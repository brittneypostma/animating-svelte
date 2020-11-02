<script>
	import { fly } from 'svelte/transition'
	import { alert } from './alert'

	function closeAlert() {
		alert.set({
			text: $alert.text,
			isActive: false
		})
	}

	alert.subscribe((value) => {
		if (value.isActive) {
			setTimeout(closeAlert, 5000)
		}
	})
</script>

{#if $alert.isActive}
	<div transition:fly={{ y: 100 }} class="toast">
		<button class="drawer--close" on:click={closeAlert}>X</button>
		<p>{$alert.text}</p>
	</div>
{/if}

<style>
	.toast {
		color: white;
		background: var(--black);
		border-radius: var(--borderRadius);
		padding: 1.25rem;
		position: fixed;
		bottom: 10px;
		left: 10px;
		right: 10px;
	}

	.toast p {
		text-align: center;
		margin: 0;
		max-width: 100%;
	}
</style>
