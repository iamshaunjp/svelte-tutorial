<script>
  import { onMount, onDestroy } from 'svelte';
  import PollStore from '../stores/pollStore.js';
  import PollDetails from './PollDetails.svelte';

  let polls = [];

  const unsub = PollStore.subscribe(data => {
    console.log(data);
    polls = data;
  });

  onMount(() => {
    // maybe get data from a db
    console.log('poll list component mounted');
  });

  onDestroy(() => {
    // unsub from store
    console.log('poll list component destroyed');
    unsub();
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