<script>
// @ts-nocheck

import FeedbackItem from "./FeedbackItem.svelte";
export let feedback

</script>

{#each feedback as feed (feed.id)}
   <FeedbackItem item={feed} on:delete-feedback />
{/each}