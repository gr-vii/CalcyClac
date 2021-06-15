<script>
	import {derivative, evaluate} from "mathjs"
	
	let is_expanded = true
	let expr = ""
	let res = 0
	let cols = 5
	let rows = 6

	function insert(seg) {
		expr += seg
	}

	function calc() {
		res = evaluate(expr)
	}

	function deriv() {
		res = derivative(expr, 'x').toString()
	}

	function all_clear() {
		expr = ""
		res = 0
	}

	function del() {
		expr = expr.substring(0, expr.length-1)
	}

	function toggle_expanded() {
		is_expanded = !is_expanded
		cols = 5
		rows = 5
	}

	/* { val: String", func: Function, w Number, h Number } */
	let buttons = [
		{ val: "1",		func: insert	},
		{ val: "2",		func: insert	},
		{ val: "3",		func: insert	},
		{ val: "+",		func: insert	},
		{ val: "-",		func: insert	},

		{ val: "4",		func: insert	},
		{ val: "5",		func: insert	},
		{ val: "6",		func: insert	},
		{ val: "^",		func: insert	},
		{ val: "*",		func: insert	},

		{ val: "7",		func: insert	},
		{ val: "8",		func: insert	},
		{ val: "9",		func: insert	},
		{ val: "/",		func: insert	},
		{ val: "%",		func: insert	},

		{ val: "=",		func: calc,		w: 2},
		{ val: "0",		func: insert	},
		{ val: ".",		func: insert	},
		{ val: "DEL",	func: del		},
		{ val: "AC",	func: all_clear },

		{ val: "sin",	func: insert,	advanced: true},
		{ val: "cos",	func: insert,	advanced: true},
		{ val: "tan",	func: insert,	advanced: true},
		{ val: "(",		func: insert,	advanced: true},
		{ val: ")",		func: insert,	advanced: true},

		{ val: "abs",	func: insert,	advanced: true},
		{ val: "sqrt",	func: insert,	advanced: true},
		{ val: "log",	func: insert,	advanced: true},
		{ val: "x",		func: insert,	advanced: true},
		{ val: "DER",	func: deriv	,	advanced: true},

		{ val: "EXP",	func: toggle_expanded },
	]
</script>

<div class="container">
	<div class ="calc">
	<h2>{expr == "" ? ":D" : expr}</h2>
		<h1>{res}</h1>

		<div
			class="buttons"
			style="
			grid-template-columns: repeat({cols}, 1fr);
			grid-template-rows: repeat({rows}, 1fr);
			"
		>
			{#each buttons as btn}
				<button
				on:click={() => btn.func(btn.val)}
				style="
				grid-column: span {btn.w ? btn.w : 1};
				grid-row: span {btn.h ? btn.h : 1};
				display: { btn.advanced && !is_expanded ? "none" : "grid" };
				"
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
			color: white;
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
		color: white;
		margin: 20px;
	}

	h1{ font-size: 34px; }
	h2 { font-size: 24px; }
</style>
