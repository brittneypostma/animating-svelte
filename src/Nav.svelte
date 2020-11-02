<script>
  import { fly } from 'svelte/transition'
</script>

<style>
  nav {
    position: fixed;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    background: var(--black);
    box-shadow: var(--shadow-lg);
    padding: 5rem;
  }

  a {
    font-size: 5rem;
    color: white;
  }
</style>

<nav transition:fly={{ x: 1000 }}>
  <ul>
    <li><a href="#">Home</a></li>
    <li><a href="#">About</a></li>
    <li><a href="#">Contact</a></li>
    <li><a href="#">Services</a></li>
  </ul>
</nav>
