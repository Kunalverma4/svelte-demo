<script>
  // @ts-nocheck
  import RatingSelect from "./RatingSelect.svelte";
  import Card from "./Card.svelte";
  import Button from "./Button.svelte";
  import { createEventDispatcher } from "svelte";
  import { FeedbackStore } from "../stores";
  let text = "";
  let rating = 10;
  let btnDisabled = true;
  let min = 10;
  let max = 100;
  let message;
  const dispatch = createEventDispatcher();
  const handleInput = () => {
    if (text.trim().length <= min) {
      btnDisabled = true;
      message = `Text must be at least ${min} characters long`;
    } else {
      btnDisabled = false;
      message = null;
    }
  };
  const handleSelect = (e) => {
    rating = e.detail;
  };

  const handleSubmit = () => {
    if (text.trim().length > min) {
      const newFeedback = {
        id: Date.now(),
        text,
        rating: +rating,
      };

      $FeedbackStore = [newFeedback,...$FeedbackStore]
    };
      text = "";
    }
 
</script>

<Card>
  <form on:submit|preventDefault={handleSubmit}>
    <header>
      <h2>How would you rate Us?</h2>
    </header>
    <RatingSelect on:rating-select={handleSelect} />
    <div class="input-group">
      <input
        type="text"
        on:input={handleInput}
        bind:value={text}
        placeholder="Tell us something that keeps you coming back"
      />
      <Button disabled={btnDisabled} type="submit">Send</Button>
    </div>
    {#if message}
      <p class="message">{message}</p>
    {/if}
  </form>
</Card>

<style>
  header {
    max-width: 400px;
    margin: auto;
  }
  header h2 {
    font-size: 22px;
    font-weight: 600;
    text-align: center;
  }
  .input-group {
    display: flex;
    flex-direction: row;
    border: 1px solid #ccc;
    padding: 8px 10px;
    border-radius: 8px;
    margin-top: 15px;
  }
  input {
    flex-grow: 2;
    border: none;
    font-size: 16px;
  }
  input:focus {
    outline: none;
  }
  .message {
    padding-top: 10px;
    text-align: center;
    color: rebeccapurple;
  }
</style>
