<script>
  // @ts-nocheck
  
	import { FeedbackStore } from './stores.js';
import FeedbackForm from './components/FeedbackForm.svelte';
  import FeedbackList from './components/FeedbackList.svelte';
  import FeedbackStats from './components/FeedbackStats.svelte';


// const DeleteFeedback = (e) => {
//  feedback = feedback.filter((item) => item.id != e.detail)
// }
const handleFeedback = (e) => {
  $FeedbackStore = [e.detail,...$FeedbackStore]
}
console.log(FeedbackStore ,$FeedbackStore)
</script>

<main class="container py-0 px-5">
  <FeedbackForm on:submit-feedback={handleFeedback}/>
  <FeedbackStats/>
 <FeedbackList />
</main>
