<script lang="ts">
    export let count:number;
    export let avgRating:number;
</script>

<div class="flex justify-between px-8 py-2">
    <p class="text-xl text-white font-bold">Posts: {count}</p>
    <p class="text-xl text-white font-bold">Avg. Rating: {avgRating}</p>
</div>