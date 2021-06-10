<script>
  import { createEventDispatcher } from "svelte";

  let content = "";

  const dispatch = createEventDispatcher();

  const createToDo = () => {
    dispatch("createToDo", {
      content: content,
    });
    content = "";
  };
</script>

<input class="todo-input" bind:value={content} />
<button class="todo-btn" on:click={createToDo}>Create</button>
