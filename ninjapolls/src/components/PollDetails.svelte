<script>
  import Card from '../shared/Card.svelte';
  import { createEventDispatcher } from 'svelte';

  export let poll;
  const dispatch = createEventDispatcher();

  // reactive values
  $: totalVotes = poll.votesA + poll.votesB;

  // handling votes
  const handleVote = (option, id) => {
    dispatch('vote', {option, id});
  };
</script>

<Card>
  <div class="poll">
    <h3>{ poll.question }</h3>
    <p>Total votes: { totalVotes }</p>
    <div class="answer" on:click={() => handleVote('a', poll.id)}>
      <div class="percent percent-a"></div>
      <span>{ poll.answerA } ({ poll.votesA } votes)</span>
    </div>
    <div class="answer" on:click={() => handleVote('b', poll.id)}>
      <div class="percent percent-b"></div>
      <span>{ poll.answerB } ({ poll.votesB } votes)</span>
    </div>
  </div>
</Card>

<style>
  h3{
    margin: 0 auto;
    color: #555;
  }
  p{
    margin-top: 6px;
    font-size: 14px;
    color: #aaa;
    margin-bottom: 30px;
  }
  .answer{
    background: #fafafa;
    cursor: pointer;
    margin: 10px auto;
    position: relative;
  }
  .answer:hover{
    opacity: 0.6;
  }
  span{
    display: inline-block;
    padding: 10px 20px;
  }
</style>