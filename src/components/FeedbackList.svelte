<script>
  // @ts-nocheck
  import { onMount, onDestroy } from 'svelte';
import { fade, scale} from 'svelte/transition';
  import FeedbackItem from "./FeedbackItem.svelte";
 import { FeedbackStore } from '../stores';

//   let feedback 
//  const unSubscribe = FeedbackStore.subscribe((value)=>{
//     feedback = value
//  })
//  onMount(()=>{
//    console.log('mounted')
//  })
//  onDestroy(()=>{
//   unSubscribe()
//  })

</script>

{#each $FeedbackStore as feed (feed.id)}
  <div in:scale out:fade='{{duration : 500}}'>
    <FeedbackItem item={feed} />
  </div>
{/each}
