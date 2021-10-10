
1) убираем из проекта все лишнее, осталяем только
	/public/
	App.svelte
	index.js
	package.json
	rollup.config.js

	а) App.svelte
		<script>
		</script>

		<style>
		  h1 {
		    text-align: center;
		  }
		</style>

		<main>
			<h1>Todo Svelte</h1>
		</main>	

2) подготовим скрипт

<script>
  let todos = [];
  function addTodo() {}
  function removeTodo() {}
</script>

3) подготовм разметку

<main>
	<h1>Todo Svelte</h1>
  {#each todos as todo, index}
    <input bind:value={todos[index]}><br>
  {/each}
  <button on:click={addTodo}>Add New Todo</button>
</main>

4) напишем функции

  function addTodo() {
    todos = [...todos, ""];
  }

5) добавим кнопку удалить

<main>
	<h1>Todo Svelte</h1>
  {#each todos as todo, index}
    <input bind:value={todos[index]}>
    <button on:click={()=> removeTodo(index)}>delete</button>
    <br>
  {/each}
  <button on:click={addTodo}>Add New Todo</button>
</main>

6) обработаем удалить

  function removeTodo(index) {
    todos = [...todos.slice(0, index), ...todos.slice(index + 1)];
  }

7) весь код внутри App.svelte

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