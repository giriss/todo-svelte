<script>
  import { createEventDispatcher } from 'svelte';

  export let title;
  export let completed;

  const dispatch = createEventDispatcher();

  function handleToggle() {
    dispatch('toggle');
  }

  function handleDelete(event) {
    event.stopPropagation();
    dispatch('delete');
  }
</script>

<li
  class="list-group-item list-group-item-action"
  on:click={handleToggle}
  class:completed
>
  {title}
  <span class="float-right" on:click={handleDelete}>
    <i class="fas fa-times"></i>
  </span>
</li>

<style>
  .completed {
    text-decoration: line-through;
  }
</style>
