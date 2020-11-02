<script>
	import { fly } from 'svelte/transition'
	export let toggleNav
</script>

<nav transition:fly={{ x: 1000 }}>
	<ul>
		<button on:click={toggleNav}>X</button>
		<li><a href="#">Home</a></li>
		<li><a href="#">About</a></li>
		<li><a href="#">Contact</a></li>
		<li><a href="#">Services</a></li>
	</ul>
</nav>

<style>
	nav {
		position: fixed;
		top: 0;
		right: 0;
		bottom: 0;
		left: 0;
		background: var(--black);
		box-shadow: var(--shadow-lg);
		padding: 1rem;
	}

	a {
		font-size: 5rem;
		color: white;
	}

	button {
		font-size: 3rem;
		color: white;
		outline: none;
		background: transparent;
		border: none;
		box-shadow: none;
	}
</style>
