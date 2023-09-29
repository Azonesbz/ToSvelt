<script>
  let taskId = 1;

  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();

  let task = {
    name: "",
    description: "",
    id: taskId
  }

</script>

<div class="flex flex-col gap-2 w-96 mt-10">
    <div class="flex flex-col text-black gap-2">
        <input class="py-2 px-4 outline-none rounded-t-3xl" type="text" bind:value={task.name} placeholder="Nom de la tâche" />
        <textarea class="h-20 py-2 px-4 outline-none" bind:value={task.description} placeholder="Description de votre tâche" />
    </div>
    <button
        class="bg-[#5C8374] py-2 px-4 rounded-b-3xl"
        on:click={() => {
            if(task.name.length && task.description.length){
                dispatch('add', task);
            };
            task.name = "";
            task.description = "";
            taskId += 1;
            return;
        }}
    >
        Ajouter une tâche
    </button>
</div>