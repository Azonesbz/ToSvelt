<script>
  import AddTask from "./lib/AddTask.svelte";
  import EditModal from "./lib/EditModal.svelte";
  import Taskcontainer from "./lib/Taskcontainer.svelte";

  let tasks = [];
  let nextTaskId = 1;
  let editingTask = null

  const addTask = (newTask) => {
    console.log(newTask)
    tasks = [...tasks, { ...newTask.detail, id: nextTaskId }];
    nextTaskId += 1;
  };
  const deleteTask = (taskId) => {
    console.log(taskId)
    tasks = tasks.filter(task => task.id !== taskId.detail);
  };

  const openEditModal = (task) => {
    editingTask = task
  }

  const editTask = (newName) => {
    tasks = tasks.map((task) => (task.id === newName.detail.id ? { ...task, name: newName.detail.name, description: newName.detail.description } : task));
    editingTask = null;
  }
</script>

<head>
  <link rel="stylesheet" href="/app.css">
</head>

<main class="min-h-screen h-screen flex items-center justify-center">
  <nav class="fixed min-w-screen w-full h-[75px] flex items-center justify-center inset-0">
    <h1>todoapp</h1>
  </nav>
  <section class="h-[80vh] w-full flex flex-col items-center justify-between px-[200px]">
    <div class="grid grid-cols-12 w-full gap-5 overflow-scroll">
      {#each tasks as task}
        <Taskcontainer {task} on:delete={deleteTask} on:edit={openEditModal}/>
      {/each}
    </div>
    <AddTask on:add={addTask} />
    {#if editingTask}
      <EditModal bind:task={editingTask} on:edit={editTask} />
    {/if}
  </section>
</main>
