<script lang="ts">
import Button from './formButton.svelte'
import Select from './ratingSelect.svelte'
import{createEventDispatcher} from 'svelte'
import {v4 as uuidv4} from 'uuid'
let text = ''
let message:string;
let rating = 10
let isDisabled = true
const handleInput = () => {
    if (text.trim().length <= 10) {
        message = 'Description must be at least 10 characters long'
        isDisabled = true
    }
    else {isDisabled = false};
}
const handleRating = (e) => {
    rating = e.detail
}
const dispatch = createEventDispatcher();
const handleSubmit = e => {
    if (text.trim().length >= 10) {
        const feedback = {
            id: uuidv4(),
            text,
            rating: rating
        }
        dispatch('form-submit', feedback)
    }
}

</script>

<form on:submit|preventDefault={handleSubmit} class="flex flex-col items-center bg-white rounded-xl drop-shadow-lg mx-2 my-8 py-4">
    <h1 class="text-2xl font-bold text-slate-800 text-center w-full">Feedback Form</h1>
    <div class="grid grid-cols-10 grid-rows-1 gap-2">
        
    </div>
    <Select on:change-select={handleRating} />
    <input on:input={handleInput} bind:value={text} class='w-2/3 text-center border border-slate-300 p-2 my-2 rounded-lg mb-8' type="text" placeholder="Describe your experience here">
    {#if (isDisabled)}
    <p class="mb-4 text-indigo-900 text-lg">Your description needs to be at least 10 characters long.</p>
    {/if}
    <Button type='submit' disabled={isDisabled}/>
</form>