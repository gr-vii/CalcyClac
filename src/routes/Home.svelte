<script>
	import {derivative, evaluate} from "mathjs"
	
	let expr = ""
	let res = 0

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

	let buttons = [
		{ val: "1", func: insert },
		{ val: "2", func: insert },
		{ val: "3", func: insert },
		{ val: "+", func: insert },
		{ val: "4", func: insert },
		{ val: "5", func: insert },
		{ val: "6", func: insert },
		{ val: "-", func: insert },
		{ val: "7", func: insert },
		{ val: "8", func: insert },
		{ val: "9", func: insert },
		{ val: "^", func: insert },
		{ val: "*", func: insert },
		{ val: "/", func: insert },
		{ val: "0", func: insert },
		{ val: "=", func: calc },
		{ val: "DER", func: deriv },
		{ val: "x", func: insert },
		{ val: "%", func: insert },
		{ val: "sin", func: insert },
		{ val: "cos", func: insert },
		{ val: "tan", func: insert },
		{ val: "DEL", func: del },
		{ val: "AC", func: all_clear },
		{ val: "(", func: insert },
		{ val: ")", func: insert },
	]
</script>

<div class ="calc">
<h2>{expr == "" ? ":D" : expr}</h2>
	<h1>{res}</h1>

	<div class="container">
		{#each buttons as btn}
			<button on:click={() => btn.func(btn.val)}>{btn.val}</button>
		{/each}
	</div>
</div>

<style lang="scss">
	* {
		font-family: monospace;
		font-weight: 400;
	}

	:global(body) {
		background: radial-gradient(circle, rgba(238,174,202,1) 0%, rgba(148,187,233,1) 100%);
	}

	.calc {
		border-radius: 20px;
		background: rgba(255, 255, 255, 0.4);
		margin: 100px auto;
		width: 480px;
		padding: 20px;
	}

	.container {
		display: grid ;
		grid-template-columns: 1fr 1fr 1fr 1fr;
		grid-template-rows: 1fr 1fr 1fr 1fr;
	}

	.container button{
		padding: 20px; 
		font-size: 34px;
		background: transparent;
		color: white;
		border: none;
		border-radius: 70px;

	&:hover {
		background: rgba(255, 255, 255, 0.5);
	}

	&:active {
		background: rgba(255, 255, 255, 0.75);
		
	}

}

	h1, h2 {
		color: white;
		margin: 20px;
	}

	h1{ font-size: 34px; }
	h2 { font-size: 24px; }
</style>
