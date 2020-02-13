<script>
  import Modal from './Modal.svelte';

  let showModal = false;

  let toggleModal = () => {
    showModal = !showModal;
  };

	let people = [
    { name: 'yoshi', beltColour: 'black', age: 25, id: 1 },
    { name: 'mario', beltColour: 'orange', age: 45, id: 2 },
    { name: 'luigi', beltColour: 'brown', age: 35, id: 3 }
  ];

  const handleClick = (e, id) => {
    people = people.filter(person => person.id != id);
    console.log(e);
  };
</script>

<Modal {showModal} on:click={toggleModal}>
  <!-- <h3>Add a New Ninja</h3> -->
  <form>
    <input type="text" placeholder='name'>
    <input type="text" placeholder='belt colour'>
    <button>Add Ninja</button>
  </form>
  <div slot="title">
    <h3>Add a New Ninja</h3>
  </div>
</Modal>
<main>
  <button on:click={toggleModal}>Open Modal</button>
  {#each people as person (person.id)}
    <div>
      <h4>{person.name}</h4>
      {#if person.beltColour === 'black'}
        <p><strong>MASTER NINJA</strong></p>
      {/if}
      <p>{person.age} years old, {person.beltColour} belt.</p>
      <button on:click={(e) => handleClick(e, person.id)}>delete</button>
    </div>
  {:else}
    <p>There are no people to show...</p>
  {/each}
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>