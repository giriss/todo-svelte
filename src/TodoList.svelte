<script>
  import { createEventDispatcher } from 'svelte';
  import Todo from './Todo.svelte';

  const dispatch = createEventDispatcher();

  export let items;
</script>

<ul class="list-group">
  {#each items as item}
    <Todo
      {...item}
      on:toggle={() => { dispatch('toggle', item.title); }}
      on:delete={() => { dispatch('delete', item.title); }}
    />
  {/each}
</ul>
