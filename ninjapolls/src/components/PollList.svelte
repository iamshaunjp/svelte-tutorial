<script>
  import PollStore from '../stores/pollStore.js';
  import PollDetails from './PollDetails.svelte';

  let polls = [];

  PollStore.subscribe(data => {
    console.log(data);
    polls = data;
  });

</script>

<div class="poll-list">
  {#each polls as poll (poll.id)}
    <div>
      <PollDetails {poll} on:vote />
    </div>
  {/each}
</div>

<style>
  .poll-list{
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-gap: 20px;
  }
</style>