<script>
	import { scale, fly } from 'svelte/transition'
	export let toggleModal
</script>

<div class="modal">
	<div class="card" transition:fly={{ y: 100 }}>
		<button class="drawer--close" on:click={toggleModal}>X</button>
		<slot />
	</div>
	<div
		class="background"
		on:click={toggleModal}
		transition:scale={{ start: 2, duration: 1000 }} />
</div>

<style>
	.modal {
		position: fixed;
		display: flex;
		align-items: center;
		justify-content: center;
		width: 100%;
		height: 100%;
		top: 0;
		left: 0;
	}
	.card {
		position: relative;
		text-align: center;
	}
	.background {
		/* background: hsl(3, 3%, 3%, 0.75); */
		background: linear-gradient(142deg, var(--red) 3.62%, var(--green) 100%);
		opacity: 50%;
		position: absolute;
		z-index: -1;
		width: 100%;
		height: 100%;
	}
</style>
