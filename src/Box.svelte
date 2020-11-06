<script>
  import { drag } from './drag'
  import { fade } from 'svelte/transition'

  let isVisible = true

  function handleDragStop(e) {
    if(e.detail.x > 300) {
      isVisible = false
    }
  }


</script>

<div class="wrapper">
  <!-- <div class="box" use:drag></div>
  <div class="box" use:drag={{
    direction: 'y'
  }}></div> -->
  {#if isVisible}
  <div 
    transition:fade
    class="box" 
    on:dragStop={handleDragStop}
    use:drag={{
      direction: 'x'
    }}
  ></div>
  {/if}
</div>

<style>
  .wrapper {
    display: grid;
    gap: 1rem;
  }
</style>