<script>
	import {Router, Link, Route} from 'svelte-routing';
	import BasicOne from "./BasicOne.svelte";
	import Home from "./Home.svelte";
	import ShoppingCart from "./shop/ShoppingCart.svelte";
</script>

<main>
	<Router>
		<nav>
			<Link to="/">Home</Link> |
			<Link to="baseone">Basic One</Link> |
			<Link to="shop">Shopping Cart</Link>
		</nav>

		<div>
			<Route path="/" component="{Home}"/>
			<Route path="baseone" component="{BasicOne}" />
			<Route path="shop" component="{ShoppingCart}" /> 
		</div>
	</Router>
</main>


<style>
	main{
		padding-top:20px
	}
	nav{
		background: #fff;
		text-align: center;
		padding: 20px 0px 20px 0px;
		border-radius: 10px;
		max-width: 500px;
		margin: auto;
		box-shadow: 0px 0px 12px -5px #0000004d;
	}
</style>