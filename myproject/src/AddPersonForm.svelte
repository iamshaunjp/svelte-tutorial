<script>
  let name;
  let beltColour;
  let age;

  const handleSubmit = () => {
    console.log(name, beltColour, age);
  };
</script>

<form on:submit|preventDefault={handleSubmit}>
  <input type="text" placeholder='name' bind:value={name}>
  <input type="text" placeholder='belt colour' bind:value={beltColour}>
  <input type="number" placeholder='age' bind:value={age}>
  <button>Add Ninja</button>
</form>