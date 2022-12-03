<script>
  let todo = { title: "", isCompleted: false };
  let todos = [];

  function addToList() {
    // todoListにtodoを追加する
    todos = [
      ...todos,
      {
        title: todo.title,
        isCompleted: false
      }
    ];
    // todoを初期化する
    todo = { title: "", isCompleted: false };
  }

  function removeFromList(index) {
    // todoListからtodoを削除する
    todos = todos.filter((_, i) => i !== index);
  }
</script>

<main>
  <div class="container">
    <div class="title">
      <h1>Todos</h1>
    </div>

    <div class="todo-list-container">
      {#if todos.length > 0}
      <ul>
        {#each todos as { title, isCompleted }, index}
          <li>
            <p>{index + 1 }：{title}</p> 
            <input type="checkbox" bind:checked={isCompleted} />
            <button on:click={() => removeFromList(index)}>Delete</button>
          </li>
        {/each}
      </ul>
      {/if}
    </div>

    <div class="form-container">
      <form>
        <label for="todo">New ToDo</label>
        <input type="title" bind:value={todo.title} />
        <button type="submit" on:click|preventDefault={addToList}>Submit</button>
      </form>
    </div>
  </div>
</main>

<style>
  main {
    font-family: sans-serif;
    text-align: center;
  }

  body {
    margin: 0;
    padding: 0;
    min-height: 100vh;
  }

  .container {
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
  }

  .title {
    width: 100%;
    display: flex;
    justify-content: center;
  }

  .todo-list-container {
    width: 100%;
    display: flex;
    justify-content: center;
  }

  li {
    list-style: none;
  }

  .form-container {
    width: 100%;
    display: flex;
    justify-content: center;
  }
</style>
