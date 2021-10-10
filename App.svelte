<script>
  let todos = [];
  function addTodo() {
    todos = [...todos, ""];
  }
  function removeTodo(index) {
    todos = [...todos.slice(0, index), ...todos.slice(index + 1)];
  }
</script>

<style>
  h1 {
    text-align: center;
  }
</style>

<main>
	<h1>Todo Svelte</h1>
  {#each todos as todo, index}
    <input bind:value={todos[index]}>
    <button on:click={()=> removeTodo(index)}>delete</button>
    <br>
  {/each}
  <button on:click={addTodo}>Add New Todo</button>
</main>