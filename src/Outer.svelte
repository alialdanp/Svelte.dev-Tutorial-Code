<script>
  import Inner from './Inner.svelte';
</script>

<Inner on:message />

<!-- au lieu de 

<script>
  import Inner from './Inner.svelte';
  import { createEventDispatcher } from 'svelte';

  const dispatch = createEventDispatcher();

  function forward(event) {
    dispatch('message', event.detail);
  }
</script>

<Inner on:message={forward} /> 

-->
