<script>
	import {all, derivative, evaluate} from "mathjs"
	
	let is_expanded = false
	let expr = ""
	let res = 0

	function insert(seg) { expr += seg }

	function calc() { res = evaluate(expr) }

	function deriv() { res = derivative(expr, 'x').toString() }

	function all_clear() { expr = ""; res = 0 }

	function del() { expr = expr.substring(0, expr.length-1) }

	function toggle_expanded() {
		is_expanded = !is_expanded
		selected_layout = is_expanded ? layouts.expanded : layouts.normal
	}

	class Btn {
		constructor(val, func, advanced, w, h) {
			this.val = val
			this.func = func
			this.w = w ?? 1
			this.h = h ?? 1
			this.advanced = advanced ?? false
		}
	}

	let b		= new Btn("",		() => {})
	let b_1		= new Btn("1",		insert)
	let b_2		= new Btn("2",		insert)
	let b_3		= new Btn("3",		insert)
	let b_4		= new Btn("4",		insert)
	let b_plus	= new Btn("+",		insert)
	let b_sub	= new Btn("-",		insert)
	let b_5		= new Btn("5",		insert)
	let b_6		= new Btn("6",		insert)
	let b_div	= new Btn("/",		insert)
	let b_7		= new Btn("7",		insert)
	let b_8		= new Btn("8",		insert)
	let b_9		= new Btn("9",		insert)
	let b_mul	= new Btn("*",		insert)
	let b_dot	= new Btn(".",		insert)
	let b_0		= new Btn("0",		insert)
	let b_ac	= new Btn("AC",		all_clear,			null, 2)
	let b_del	= new Btn("DEL",	del,				null, 1)
	let b_expand= new Btn("EXPAND", toggle_expanded,	null, 4)
	let b_eq	= new Btn("=",		calc,				null, 2)
	let b_pow	= new Btn("^",		insert,	true)
	let b_mod	= new Btn("%",		insert,	true)
	let b_sin	= new Btn("sin",	insert,	true)
	let b_cos	= new Btn("cos",	insert,	true)
	let b_tan	= new Btn("tan",	insert,	true)
	let b_lb	= new Btn("(",		insert,	true)
	let b_rb	= new Btn(")",		insert,	true)
	let b_lm	= new Btn("[",		insert,	true)
	let b_rm	= new Btn("]",		insert,	true)
	let b_abs	= new Btn("abs",	insert,	true)
	let b_sqrt	= new Btn("sqrt",	insert,	true)
	let b_log	= new Btn("log",	insert,	true)
	let b_x		= new Btn("x",		insert,	true)
	let b_i		= new Btn("i",		insert,	true)
	let b_der	= new Btn("DER",	deriv,	true)

	let layouts = {
		normal: {
			sizes: {cols: 4, rows: 6},
			grid: [
			b_ac,	b_del,	b_plus,
			b_1,	b_2,	b_3,	b_sub,
			b_4,	b_5,	b_6,	b_mul,
			b_7,	b_8,	b_9,	b_div,
			b_dot,	b_0,	b_eq,
			b_expand,
			]
		},
		expanded: {
			sizes: {cols: 5, rows: 7},
			grid: [
			b_ac,	b_del,	b_plus,	b_pow,
			b_1,	b_2,	b_3,	b_sub,		b_mod,
			b_4,	b_5,	b_6,	b_mul,		b_x,
			b_7,	b_8,	b_9,	b_div,		b_i,
			b_dot,	b_0,	b_eq,
			b_expand,
			]
		}
	}
	
	let selected_layout = layouts.normal
</script>

<div class="container">
	<div class ="calc">
	<h2>{expr == "" ? ":D" : expr}</h2>
		<h1>{res}</h1>

		<div
			class="buttons"
			style="
			grid-template-columns: repeat({selected_layout.sizes.cols}, 1fr);
			grid-template-rows: repeat({selected_layout.sizes.rows}, 1fr);
			"
		>
			{#each selected_layout.grid as btn}
					<button
					on:click={() => btn.func(btn.val)}
					style="grid-column: span {btn.w ? btn.w : 1}; grid-row: span {btn.h ? btn.h : 1};"
					>{btn.val}</button>
			{/each}
		</div>
	</div>
</div>

<style lang="scss">
	* {
		font-family: monospace;
		font-weight: 400;
	}

	.container {
		width: 100vw;
		height: 100vh;
		background: radial-gradient(circle, rgba(238,174,202,1) 0%, rgba(148,187,233,1) 100%);
		display: flex;
	}

	.calc {
		border-radius: 20px;
		background: rgba(255, 255, 255, 0.4);
		margin: auto;
		padding: 20px;
	}

	.buttons {
		display: grid;

		button {
			background: rgba(255, 255, 255, 0.4);
			padding: 10px; 
			font-size: 28px;
			background: transparent;
			color: black;
			border: none;
			border-radius: 5px;

			&:hover {
				background: rgba(255, 255, 255, 0.5);
			}

			&:active {
				background: rgba(255, 255, 255, 0.75);
			}
		}
	}


	h1, h2 {
		color: black;
		margin: 20px;
	}

	h1{ font-size: 34px; }
	h2 { font-size: 24px; }
</style>
