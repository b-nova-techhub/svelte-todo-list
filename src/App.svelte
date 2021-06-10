<script>
  import CreateToDo from "./CreateToDo.svelte";
  import ToDo from "./ToDo.svelte";

  let toDos = [
    {
      content: "Get tea",
      completed: true,
    },
    {
      content: "Learn Svelte",
      completed: false,
    },
    {
      content: "Write blog post",
      completed: false,
    },
  ];

  const deleteToDo = (event) => {
    toDos = toDos.filter((toDo) => toDo.content !== event.detail.content);
  };

  const createToDo = (event) => {
    toDos = [
      ...toDos,
      {
        content: event.detail.content,
        completed: false,
      },
    ];
  };
</script>

<main>
  <h1>b-nova To-Do List Svelte</h1>
  <CreateToDo on:createToDo={createToDo} />
  {#if toDos.length !== 0}
    <div class="container">
      {#each toDos as toDo}
        <ToDo {toDo} on:deleteToDo={deleteToDo} />
      {/each}
    </div>
  {:else}
    No ToDo Items
  {/if}
</main>
