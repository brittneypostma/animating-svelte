<script>
  import { fade, blur, slide, fly } from 'svelte/transition'
  import { custom } from './custom'
  import Nav from './Nav.svelte'
  export let name
  let isReady = false
  let isNavOpen = false
  function toggleNav() {
    isNavOpen = !isNavOpen
  }
</script>

<style>
  /* .hidden {
    opacity: 0;
    transition: 0.3s ease opacity;
  } */

  h1 {
    color: rgb(14, 92, 102);
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>

<!-- Fade - opacity 0 -1 -->
<!-- Blue - opacity and blur -->
<!-- Fly - x and y along with opacity -->
<!-- Slide - height -->
<!-- Scale - start: scale, opacity -->
<!-- Draw - draw svgs -->

<main>
  <!-- <button on:click={() => (isReady = !isReady)}>Fade</button> -->
  <button on:click={toggleNav}>Menu</button>
  <!-- Mounting and unmounting animation -->
  <!-- {#if isReady}{/if} -->
  {#if isNavOpen}
    <Nav />
  {/if}
  <!-- Initial load animation -->
  <h1 transition:fade={{ delay: 100, duration: 1000 }}>Hello {name}!</h1>
  <!-- <h1 transition:blur={{ delay: 100, duration: 1000, opacity: 1, amount: 20 }}> Hello {name}!</h1> -->

  <!-- <h1 in:fly={{ y: 100 }} out:fade>Hello {name}!</h1> -->
  <!-- <h1 transition:slide>Hello {name}!</h1> -->
  <!-- <h1 transition:fly={{ y: 100 }}>Hello {name}!</h1> -->
  <!-- css transition animation -->
  <!-- <h1 class:hidden={!isReady}>Hello {name}!</h1> -->
  <!-- <h1 transition:custom={{ delay: 100, duration: 1000 }}>Hello {name}!</h1> -->
</main>
