<script>
  function handleClick() {
    alert('no more alerts');
  }
</script>

<button on:click|once={handleClick}> 
  Click me 
</button>

<!-- You can chain modifiers together, e.g. 
  on:click|once|capture={...}. 
-->