<script>
    export let onClick;
    export let disable
    export let label;
    export let side = "middle" || "left" || "right"
</script>
  
<button 
    class="px-4 py-2 text-white font-semibold rounded w-full"
    class:bg-green-800={label === "Valider"} 
    class:bg-red-800={label === "Supprimer"} 
    class:bg-yellow-800={label === "Modifier"} 
    class:rounded-l-3xl={side === "left"} 
    class:rounded-r-3xl={side === "right"} 
    on:click={onClick}
    disabled={disable}
>
    {label}
</button>