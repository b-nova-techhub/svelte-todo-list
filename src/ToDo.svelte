<script>
  export let toDo;

  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  function deleteToDo() {
    dispatch("deleteToDo", {
      content: toDo.content,
    });
  }

  const toggleToDo = () => {
    toDo.completed = !toDo.completed;
  };
</script>

<div class="todo">
  <p class="content {toDo.completed ? 'completed' : 'open'}">
    {toDo.content}
  </p>
  <button class="todo-btn" on:click={toggleToDo}
    >{toDo.completed ? "Uncheck" : "Check"}</button
  >
  <button class="todo-btn" on:click={deleteToDo}>Delete</button>
</div>

<style>
  .completed {
    text-decoration: line-through;
  }
  .open {
    color: red;
  }

  .content {
    flex: 1 1 100%;
  }

  .todo {
    display: flex;
    padding: 10px 15px;
    background-color: #fff;
    border-bottom: 1px solid #ddd;
  }

  .todo:nth-child(even) {
    background-color: #eee;
  }

  .todo:last-of-type {
    border-bottom: 0;
  }

  .todo-btn {
    background-color: #258814 !important;
  }
</style>
