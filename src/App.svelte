<script>
  async function getRandomNumber() {
    const res = await fetch(`https://svelte.dev/tutorial/random-number`);
    const text = await res.text();

    if (res.ok) {
      return text;
    } else {
      throw new Error(text);
    }
  }

  let promise = getRandomNumber();

  function handleClick() {
    promise = getRandomNumber();
  }
</script>

<button on:click={handleClick}> generate random number </button>

{#await promise}
  <p>...waiting</p>
{:then number}
  <p>The number is {number}</p>
{:catch error}
  <p style="color: red">{error.message}</p>
{/await}

<!-- 
If you know that your promise can't reject, you can omit the catch block. 
You can also omit the first block if you don't want to show anything 
until the promise resolves:

  {#await promise then value}
    <p>the value is {value}</p>
  {/await} 
-->
