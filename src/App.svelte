<script>
	import Router from 'svelte-spa-router'
	/* import {wrap} from 'svelte-spa-router/wrap' */

	import Home from './routes/Home.svelte'
	import NotFound from './routes/NotFound.svelte'

	const routes = {
    '/': Home,
    /* '/book': wrap({ asyncComponent: () => import('./routes/Book.svelte') }), */
    '*': NotFound,
	}
</script>

<Router {routes}/>

<style lang="scss" global>
$bg: #CAD5DB;
$mg: #F6FAF9;
$fg: #9DA1AF;
$acc: #2E9690;

$tr: #00000000;
$bl: #16232E;
$wh: #FFFFFF;

* {
margin: 0;
padding: 0;
box-sizing: border-box;
font-family: sans-serif;
}
</style>
