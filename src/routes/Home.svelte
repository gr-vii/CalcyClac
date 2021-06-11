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
</script>

<div class ="calc">
<h2>{vals[0]}{op}{vals[1]}</h2> 
<h1>{res}</h1>
	<div class="container">
	<button on:click={() => insert(1)}>1</button>
	<button on:click={() => insert(2)}>2</button>
	<button on:click={() => insert(3)}>3</button>
	<button on:click={() => operator("+")}>+</button>
	<button on:click={() => insert(4)}>4</button>
	<button on:click={() => insert(5)}>5</button>
	<button on:click={() => insert(6)}>6</button>
	<button on:click={() => operator("-")}>-</button>
	<button on:click={() => insert(7)}>7</button>
	<button on:click={() => insert(8)}>8</button>
	<button on:click={() => insert(9)}>9</button>
	<button on:click={() => operator("*")}>*</button>
	<button on:click={() => insert(0)}>0</button>
	<button on:click={() => operator("/")}>/</button>
	<button on:click={() => operator("%")}>%</button>
	<button on:click={() => calc()}>=</button>
	</div>
</div>
<style>
*{font-family: monospace;}
:global(body){
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
h1{
	margin: 20px;
	font-size: 34px;
	font-weight: lighter;
}
 h2 {
	margin: 20px; 
	font-size: 24px;
	font-weight: lighter;
}
</style>