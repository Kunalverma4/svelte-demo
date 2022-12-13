<script>
    import { FeedbackStore } from "../stores";
    
    $: count = $FeedbackStore.length
    $:average = $FeedbackStore.reduce((acc, item) => acc + item.rating, 0) / count 
</script>


<div class='flex justify-between items-center'>
    <h4>{count} Reviews</h4>
     <h4>ratings average:{average.toFixed()}</h4>
</div>