<script>
	let vals = [0, ""]
	let val_i = 0
	let res = 0
	let op = ""

	function insert(n){
		let active = vals[val_i].toString()
		active += n
		vals[val_i] = Number(active)
	}

	function operator(o) {
		op = o
		val_i++
	}

	function calc() {
		switch (op) {
			case "+": res = vals[0] + vals[1]; break;
			case "-": res = vals[0] - vals[1]; break;
			case "*": res = vals[0] * vals[1]; break;
			case "/": res = vals[0] / vals[1]; break;
			case "%": res = vals[0] % vals[1]; break;
		}
	}

	let buttons = [
		{ val: "1", func: insert },
		{ val: "2", func: insert },
		{ val: "3", func: insert },
		{ val: "+", func: operator },
		{ val: "4", func: insert },
		{ val: "5", func: insert },
		{ val: "6", func: insert },
		{ val: "-", func: operator },
		{ val: "7", func: insert },
		{ val: "8", func: insert },
		{ val: "9", func: insert },
		{ val: "*", func: operator },
		{ val: "0", func: insert },
		{ val: "/", func: operator },
		{ val: "%", func: operator },
		{ val: "=", func: calc },
	]
</script>

<div class ="calc">
	<h2>{vals[0]}{op}{vals[1]}</h2> 
	<h1>{res}</h1>

	<div class="container">
		{#each buttons as btn}
			<button on:click={() => btn.func(btn.val)}>{btn.val}</button>
		{/each}
	</div>
</div>

<style>
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
		border: none;
	}

	h1, h2 {
		color: white;
		margin: 20px;
	}

	h1{ font-size: 34px; }
	h2 { font-size: 24px; }
</style>
