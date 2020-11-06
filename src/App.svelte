<script>
	import { onMount } from 'svelte'
	import { fade, blur, slide, fly } from 'svelte/transition'
	// import {bounceOut} from 'svelte/easing'
	import {quintInOut} from 'svelte/easing'

	import { alert } from './alert'
	import { custom } from './custom'

	import Box from './Box.svelte'
	import Card from './Card.svelte'
	import Cross from './Cross.svelte'
	import Modal from './Modal.svelte'
	import Nav from './Nav.svelte'
	import Toast from './Toast.svelte'

	export let name

	let isReady = false
	let isNavOpen = false
	let isModalOpen = false
	let isCardActive = false
	let y
	let cubes = [...Array(10).keys()]

	function toggleNav() {
		isNavOpen = !isNavOpen
	}
	export function toggleModal() {
		isModalOpen = !isModalOpen
	}
	function toggleAlert() {
		alert.set({
			isActive: !$alert.isActive,
			text: 'Our new alert'
		})
	}

	// onMount(() => {
	// 	// registers scroll events
	// 	addScrollEvent()
	// })

	// function addScrollEvent() {
	// 	window.addEventListener("scroll", onScroll, { passive: true})
	// }

	// function onScroll() {
	// 	console.log(window.pageYOffset)
	// 	const scrollPosition = window.pageYOffset

	// 	if (scrollPosition > 150) {
	// 		isCardActive = true
	// 	}
	// }

	// reactive scroll event attached to window with bind:
	$: if (y > 100) {
		isCardActive = true
	}
</script>

<svelte:window bind:scrollY={y} />

<!-- Fade - opacity 0 -1 -->
<!-- Blue - opacity and blur -->
<!-- Fly - x and y along with opacity -->
<!-- Slide - height -->
<!-- Scale - start: scale, opacity -->
<!-- Draw - draw svgs -->

<main>
	<!-- <button on:click={() => (isReady = !isReady)}>Fade</button> -->
	<div class="buttons">
		<button on:click={toggleNav}>Menu</button>
		<button on:click={toggleAlert}>Alert</button>
		<button on:click={toggleModal}>Modal</button>
	</div>
	<!-- Mounting and unmounting animation -->
	<!-- {#if isReady}{/if} -->
	{#if isNavOpen}
		<Nav {toggleNav} />
	{/if}
	<!-- Initial load animation -->
	<h1 transition:fade={{ delay: 100, duration: 1000 }}>Hello {name}!</h1>
	
	<div class="grid">
		{#each cubes as cube, i}
			<div 
			class="box" 
			transition:fly={{
				duration:1000, 
				delay: i * 100,
				easing: quintInOut,
				y: 80
			}} 
			/>
		{/each}
	</div>

	<Cross />

	<Box />

	<div class="cards">
		<Card />
		<Card />
		<Card />
		{#if isCardActive}
			<Card />
		{/if}
	</div>
	<!-- <h1 transition:blur={{ delay: 100, duration: 1000, opacity: 1, amount: 20 }}> Hello {name}!</h1> -->

	<!-- <h1 in:fly={{ y: 100 }} out:fade>Hello {name}!</h1> -->
	<!-- <h1 transition:slide>Hello {name}!</h1> -->
	<!-- <h1 transition:fly={{ y: 100 }}>Hello {name}!</h1> -->
	<!-- css transition animation -->
	<!-- <h1 class:hidden={!isReady}>Hello {name}!</h1> -->
	<!-- <h1 transition:custom={{ delay: 100, duration: 1000 }}>Hello {name}!</h1> -->
</main>

<Toast />

{#if isModalOpen}
	<Modal {toggleModal}>
		<p>This is in the modal.</p>
		<button>Do something!</button>
	</Modal>
{/if}

<style>
	/* .hidden {
    opacity: 0;
    transition: 0.3s ease opacity;
  } */

	main {
		margin: 0 auto;
		padding: 1rem;
		display: grid;
		justify-content: center;
		gap: 2.5rem;
		max-width: 1440px;
	}

	h1 {
		color: rgb(14, 92, 102);
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	.cards {
		display: grid;
		gap: 1rem;
		grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
	}

	.grid {
		--gridCols: 1;
		grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
		justify-items: center;
	}
</style>
