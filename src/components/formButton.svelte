<script lang="ts">
export let disabled:boolean;
export let type:string;

</script>

<button 
{type}
{disabled}
class="py-2 px-4 font-semibold absolute inset-x-1/2 -translate-x-1/2 bottom-0 translate-y-1/2 text-white rounded-xl bg-pink-600 hover:bg-pink-500 "
>
Submit
</button>

<style>
    button:disabled {
        background-color: darkgray;
    }
    button:disabled:hover {
        background-color: lightgrey;
    }
</style>