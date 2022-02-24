<script lang="ts">
    import { createEventDispatcher } from "svelte";
    export let id:string;
    export let rating:number;
    export let text:string;

    const dispatch = createEventDispatcher()
    const handleDelete = id => {
        dispatch('delete-feedback', id)
    }
</script>

<div class="py-8 px-4 m-8 bg-white drop-shadow-md border rounded-xl border-slate-200">
    <h1 class="text-lg text-white text-center font-semibold absolute -left-6 -top-6 p-3 w-12 h-12 bg-pink-600 rounded-full">{rating}</h1>
    <button id="close" class="absolute right-4 top-4 font-bold hover:text-pink-600" on:click={() => handleDelete(id)}>X</button>
    <p class="text-md  text-slate-700">{text}</p>
</div>