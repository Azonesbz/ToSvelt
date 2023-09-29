<script>
    export let task;
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();

    let editedName = task.name;
    let editedDescription = task.description

    const confirmEdit = () => {
        let editedTask = {
            name: editedName,
            description: editedDescription,
            id: task.detail.id
        }
        dispatch("edit", editedTask)
    }

</script>

<div 
    class="absolute min-h-screen min-w-screen h-full w-full inset-0 backdrop-blur-sm flex items-center justify-center" 
>
    <div class="bg-[#183D3D] text-black p-5 w-96 flex flex-col rounded-3xl" >
        <input class="rounded-t-3xl py-2 px-4 outline-none" type="text" bind:value={editedName} />
        <textarea class="py-2 px-4 outline-none" bind:value={editedDescription} />
        <button class="bg-green-400 py-2 px-4 rounded-b-3xl" on:click={confirmEdit}>Confirmer la modification</button>
    </div>
</div>