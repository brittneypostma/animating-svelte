<script>
  import { drag } from './drag'
</script>

<div class="wrapper">
<div class="box" use:drag></div>
<div class="box" use:drag={{
  direction: 'y'
}}></div>
<div class="box" use:drag={{
  direction: 'x'
}}></div>
</div>

<style>
  .wrapper {
    display: grid;
    gap: 1rem;
  }
  .box {
    background: var(--blue);
    box-shadow: var(--shadow-md);
    width: 100px;
    height: 100px;
  }
</style>