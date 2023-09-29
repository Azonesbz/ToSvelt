<script>
  import Button from "./Button.svelte";
  export let task;
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();

  let validate = false

</script>

    <div class="col-span-6 w-full max-h-72 h-full flex flex-col bg-[#5C8374] rounded-3xl justify-between duration-200" class:opacity-75={validate} key={task.id}>
      <div class="bg-[#183D3D] h-full px-10 py-5 rounded-3xl">
        <h2>{task.name}</h2>
        <p>{task.description}</p>
      </div>
      <div class="h-[75px] flex justify-around items-center gap-2 px-2">
        <Button label="Supprimer" onClick={() => dispatch("delete", task.id)} side="left" disable={validate} />
        <Button label="Modifier" onClick={() => dispatch("edit", task)} disable={validate} />
        <Button label={validate ? "Reprendre" : "Valider"} onClick={() => validate = !validate} side="right" disable={false} />
      </div>
    </div>
