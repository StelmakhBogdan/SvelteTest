<script>
  import TodoItem from './TodoItem.svelte';

  let newTodo = '';
  let todos = [];

  const addTodo = () => {
    if (newTodo) {
      todos = [...todos, newTodo];
      newTodo = '';
    }
  };

  const removeHandler = (id) => {
    todos = [...todos.filter((item, index) => index !== id)]
  };

  const handlerKeyEnter = (e) => {
    if (e.code === 'Enter') {
      addTodo();
    }
  };

  const handleRemoveAll = () => {
    todos = [];
  };

  $: totalCount = todos.length;

</script>

<div>
  <h5 class="list_counter">Total todos: {totalCount}</h5>
  <div class="tl">
    <label for="input_msg">Todo name</label>
    <input bind:value={newTodo} on:keydown={handlerKeyEnter} id="input_msg" type="text" placeholder="Text your message..." class="input_msg"/>
    <button class="add_task_btn" on:click={addTodo}>Add new task</button>
  </div>

  {#if todos.length}
    <ul class="list">
    {#each todos as message, i}
      <TodoItem message={message} index={i} removeHandler={removeHandler} />
    {/each}
  </ul>
  {/if}

  <div>
    {#if todos.length}
      <button class="remove_all_tasks_btn"  on:click={handleRemoveAll}>Remove all</button>
    {/if}
  </div>

  {#if !todos.length}
    <span>List are empty!</span>
  {/if}


</div>


<style>
  .list_counter {
    text-align: left;
    font-size: 18px;
    font-weight: bold;
  }

  .tl {
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 400px;
    margin: 0 auto;
  }

  .add_task_btn {
    padding: 8px;
    display: flex;
    align-items: center;
    justify-content: center;
    color: #ffffff;
    background-color: green;
    font-size: 14px;
  }

  .remove_all_tasks_btn {
    padding: 8px;
    display: flex;
    align-items: center;
    justify-content: center;
    color: #ffffff;
    background-color: firebrick;
    font-size: 14px;
  }

  .list {
    padding: 5px;
    margin-left: 51px;
    border: 1px solid mediumpurple;

  }

  .input_msg, .input_msg:focus-visible {
    padding: 5px;
    border-radius: 5px;
    border: none;
    outline: none;
  }
</style>
