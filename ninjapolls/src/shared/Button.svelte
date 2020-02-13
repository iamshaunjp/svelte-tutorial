<script>
  export let type = 'primary';
  export let flat = false;
  export let inverse = false;
</script>

<button class:flat={flat} class:inverse={inverse} class={type} on:click>
  <slot></slot>
</button>

<style>
  button{
    border: 0;
    cursor: pointer;
    border-radius: 6px;
    padding: 8px 12px;
    font-weight: bold;
    box-shadow: 1px 2px 3px rgba(0,0,0,0.2);
  }
  .flat{
    box-shadow: none;
  }
  .primary{
    background: #d91b42;
    color: white;
  }
  .secondary{
    background: #45c496;
    color: white;
  }
  .primary.inverse{
    color: #d91b42;
    background: white;
    border: 2px solid #d91b42;
  }
  .secondary.inverse{
    color: #45c496;
    background: white;
    border: 2px solid #45c496;
  }
</style>