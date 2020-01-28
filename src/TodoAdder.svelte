<script>
  import { createEventDispatcher } from 'svelte';

  const dispatch = createEventDispatcher();
  let todo;

  function handleAdd(event) {
    event.preventDefault();
    dispatch('todo', todo);
    todo = '';
  }
</script>

<form class="input-group mb-3" on:submit={handleAdd}>
  <input bind:value={todo} type="text" class="form-control" placeholder="New todo" />
  <div class="input-group-append">
    <button class="btn btn-primary" type="submit">Add</button>
  </div>
</form>
