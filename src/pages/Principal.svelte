<script>
  import { onDestroy } from 'svelte';
  import { fade } from 'svelte/transition';
  import Titulo from '../lib/components/Titulo.svelte';
  import Rompecabezas from '../lib/components/rompecabezas/Rompecabezas.svelte';

  let on = false;
  let redirect = false;
  let timeout;
  let timeout2;

  const URL = 'https://collaboration.merck.com/sites/CoPMexico';

  $: if (on) {
    timeout = setTimeout(() => {
      redirect = true;
    }, 3000);
  } else {
    clearTimeout(timeout);
  }
  $: if (redirect) {
    clearTimeout(timeout);
    timeout2 = setTimeout(() => {
      window.location.href = URL;
      // push('/info');
    }, 400);
  }
  onDestroy(() => clearTimeout(timeout2));
</script>

<section class:on>
  {#if !redirect}
    <div class="container" transition:fade>
      <Titulo {on} />

      <Rompecabezas
        on:click={() => {
          on = true;
        }}
      />

      {#if on}
        <div class="mensaje" transition:fade>
          <p>Powered by Subsidiary</p>
          <p>of the Future</p>
        </div>
      {:else}
        <span class="helper">dale clic</span>
      {/if}
    </div>
  {/if}
</section>

<style>
  p {
    color: #75c7ae;
    text-align: center;
    margin: 0;
    font-weight: bold;
  }
  div.mensaje {
    margin-top: 5em;
  }
  div.container {
    margin: 5em;
    padding: 5em;
    display: flex;
    flex-direction: column;
    align-content: center;
  }
  section {
    display: flex;
    flex-direction: row;
    justify-content: center;
    background-color: #13213d;
    min-width: 100vw;
    min-height: 100vh;
  }
  .on {
    background-color: white;
    -webkit-transition: background-color 500ms linear;
    -ms-transition: background-color 500ms linear;
    transition: background-color 500ms linear;
  }
  .helper {
    color: white;
    text-align: center;
    margin-top: 15%;
  }
</style>
