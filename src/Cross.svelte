<script>
let todo =[
  {
    id: 1,
    isDone: false,
    text: "Wake Up",
  },
  {
    id: 2,
    isDone: false,
    text: "Brush Teeth",
  },
  {
    id: 3,
    isDone: false,
    text: "Get Breakfast",
  }
]
</script>
<div class="card">
  <h3>Not Done</h3>
  <ul>
    {#each todo as item (item.id)}
        <li>
          <input bind:checked={item.isDone} id="todo" type="checkbox">
          <label for="todo">
            {item.text}
          </label>
        </li>
    {/each}
  </ul>  
</div>

<style>
  h3 {
    margin-bottom: 1rem;
  }
  li {
    padding: 0;
    display: flex;
    gap: 1rem;
  }
</style>