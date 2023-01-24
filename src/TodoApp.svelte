<script>
  import TodoList from './TodoList.svelte';
  import TodoAdder from './TodoAdder.svelte';

  let todos = [];

  function addTodo({ detail: title }) {
    todos = [...todos, { title, completed: false }];
  }

  function toggleTodo({ detail }) {
    const index = todos.findIndex(({ title }) => title === detail);
    todos[index].completed = !todos[index].completed;
    todos = [...todos];
  }

  function deleteTodo({ detail }) {
    todos = todos.filter(({ title }) => title !== detail);
  }
</script>

<main class="container">
  <a target="_blank" rel="noopener noreferrer" href="https://github.com/giriss/todo-svelte">→ View code on GitHub</a>
  <h1>Svelte Todo App</h1>
  <TodoAdder on:todo={addTodo} />
  <TodoList items={todos} on:toggle={toggleTodo} on:delete={deleteTodo} />
</main>
