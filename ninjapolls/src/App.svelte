<script>
	import Header from './components/Header.svelte';
	import Footer from './components/Footer.svelte';
  import Tabs from './shared/Tabs.svelte';
  
  // tabs
  let items = ['Current Polls', 'Add New Poll'];
  let activeItem = 'Current Polls';
  const tabChange = (e) => activeItem = e.detail;
</script>

<Header />
<main>
  <Tabs {activeItem} {items} on:tabChange={tabChange} />
  {#if activeItem === 'Current Polls'}
    <p>poll list goes here</p>
  {:else if activeItem === 'Add New Poll'}
    <p>new poll form goes here</p>
  {/if}
</main>
<Footer />

<style>
	main{
    width: 100%;
    max-width: 960px;
    margin: 40px auto;
  }
</style>