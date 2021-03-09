<script>

  import { onMount } from 'svelte';

  export let name = 'Harold';

  // fixed by calling the onMount lifecycle function
  onMount(() => {
    document.getElementById('my-name').style = 'font-size: 2rem;';
  });

</script>

<p id="my-name">My name is {name}</p>
