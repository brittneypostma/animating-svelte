<script>
  import { crossfade, fade } from 'svelte/transition'
  import { flip } from 'svelte/animate'
// flip: first, last, inver, play
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
    text: "Turn on news",
  },
  {
    id: 4,
    isDone: false,
    text: "Stress out",
  },
  {
    id: 5,
    isDone: false,
    text: "Wait for votes",
  }
]

const [ send, receive ] = crossfade({
  fallback: fade
})
</script>

<div class="flex">
  <div class="card">
    <h3>Not Done</h3>
    <ul>
      {#each todo.filter(item => !item.isDone) as item (item.id)}
          <li 
            animate:flip
            in:receive={{ key: item.id}} 
            out:send={{key:item.id}}
          >
            <input bind:checked={item.isDone} id="todo" type="checkbox">
            <label for="todo">
              {item.text}
            </label>
          </li>
      {/each}
    </ul>  
  </div>

  <div class="card">
    <h3>Done</h3>
    <ul>
      {#each todo.filter(item => item.isDone) as item (item.id)}
          <li 
            animate:flip
            in:receive={{ key: item.id}} 
            out:send={{key:item.id}}
          >
            <input bind:checked={item.isDone} id="todo" type="checkbox">
            <label for="todo">
              {item.text}
            </label>
          </li>
      {/each}
    </ul>  
  </div>
</div>
<style>
  .flex {
    justify-content: center;
    flex-wrap: wrap;
    gap: 1rem;
  }
  .card {
    flex: 1 1 0;
    min-width: 200px;
    min-height: 200px;
  }
  h3 {
    margin-bottom: 1rem;
  }
  li {
    padding: 0;
    display: flex;
    gap: 1rem;
    margin-bottom: 0.5rem;
  }
</style>