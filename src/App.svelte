<script>
// @ts-nocheck


  import FeedbackList from './components/FeedbackList.svelte';
let feedback = [{
  id:1,
  rating:10,
  text:'lorean ipsum dolor sit amet lorean ipsum dolor sit amet lorean ipsum dolor sit amet lorean ipsum dolor sit amet lorean ipsum dolor sit amet', 
},{
  id:2,
  rating:7,
  text:'lorean ipsum dolor sit amet lorean ipsum dolor sit amet lorean ipsum dolor sit amet lorean ipsum dolor sit amet lorean ipsum dolor sit amet',
},
{
  id:3,
  rating:8,
  text:'lorean ipsum dolor sit amet lorean ipsum dolor sit amet lorean ipsum dolor sit amet lorean ipsum dolor sit amet lorean ipsum dolor sit amet',
}]

const DeleteFeedback = (e) => {
 feedback = feedback.filter((item) => item.id != e.detail)
}
</script>

<main class="container py-0 px-5">
 <FeedbackList feedback={feedback} on:delete-feedback={DeleteFeedback}/>
</main>
