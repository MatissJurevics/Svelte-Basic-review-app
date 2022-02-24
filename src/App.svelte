<script lang="ts">
  import FeedbackList from "./components/feedbackList.svelte";
  import StatDisplay from './components/stats.svelte';
  import FeedbackForm from './components/feedbackForm.svelte'
  
  let feedback = [
    {
      id: 1,
      rating: 8,
      text: `Quam ab eligendi aut. Animi repellendus distinctio esse. Mollitia quibusdam porro quia maxime non. Voluptatem minus a aut dignissimos aspernatur maiores quis. Consectetur molestiae et aliquam at sit laudantium voluptatem`
    },
    {
      id: 2,
      rating: 10,
      text: `Quam ab eligendi aut. Animi repellendus distinctio esse. Mollitia quibusdam porro quia maxime non. Voluptatem minus a aut dignissimos aspernatur maiores quis. Consectetur molestiae et aliquam at sit laudantium voluptatem`
    },
    {
      id: 3,
      rating: 9,
      text: `Quam ab eligendi aut. Animi repellendus distinctio esse. Mollitia quibusdam porro quia maxime non. Voluptatem minus a aut dignissimos aspernatur maiores quis. Consectetur molestiae et aliquam at sit laudantium voluptatem`
    }
  ]
  $: count = feedback.length
  $: avgRating = (Math.round((feedback.reduce((a, {rating}) => rating + a, 0) / feedback.length) * 100)) /100
  const deleteFeedback = e => {
    let itemId = e.detail
    feedback = feedback.filter((item) => item.id != itemId)
  }
  const handleSubmit = e => {
    console.log(e.detail)
    feedback= [e.detail, ...feedback]
  }
</script>

<main class="max-w-3xl">
  <FeedbackForm on:form-submit={handleSubmit}/>
  <StatDisplay {count} {avgRating} />
  <FeedbackList {feedback} on:delete-feedback={deleteFeedback}/>
</main>