<script lang="ts">
    import Feedback from './feedbackPost.svelte'
    export let feedback = [];
    console.log(feedback)
</script>

<main>
    {#each feedback as fb (fb.id)}
        <Feedback id={fb.id} rating={fb.rating} text={fb.text} on:delete-feedback/>
    {/each}
</main>