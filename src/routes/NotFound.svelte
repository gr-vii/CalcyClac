<script>
	let title = "404"
	let desc = "Opps! Page not found"
	let warn = "Sorry, the page you're looking for doesn't exist. If you think something is broken, report a problem"
</script>

<div class="container">
	<div class="content">
		<h2 class="title" data-text={title}> {title} </h2>
		<h4 data-text={desc}> {desc} </h4>
		<br>
		<h4 data-text={warn}> {warn} </h4>
	</div>
</div>

<style lang="scss">
.container {
  width: 100vw;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
}

.content {
  max-width: 600px;
  text-align: center;
}

.title {
  font-size: 20vw;
}
</style>
