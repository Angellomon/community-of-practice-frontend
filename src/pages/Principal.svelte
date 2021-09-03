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
    }, 3500);
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

<section class:on transition:fade>
  {#if !redirect}
    <span class="titulo">
      <Titulo {on} />
    </span>
    <span class="puzzle">
      <Rompecabezas
        on:click={() => {
          on = true;
        }}
      />
    </span>

    {#if on}
      <div class="mensaje" transition:fade={{ duration: 400, delay: 200 }}>
        <p>powered by subsidiary of the future</p>
      </div>
    {:else}
      <span class="helper" transition:fade={{ duration: 250, delay: 300 }}>dale clic</span>
    {/if}
  {/if}
</section>

<style>
  span.titulo,
  span.puzzle,
  span.helper,
  div.mensaje {
    position: absolute;
  }

  span.titulo {
    top: 5%;
  }

  span.puzzle {
    bottom: 40%;
    align-self: center;
  }

  span.helper {
    color: white;
    text-align: center;
    bottom: 25%;
    align-self: center;
  }

  div.mensaje {
    bottom: 25%;
  }

  p {
    color: #6eceb2;
    text-align: center;
    margin: 0;
    font-weight: bold;
  }

  section {
    display: flex;
    flex-direction: row;
    justify-content: center;
    background-color: #13213d;
    /* background-color: white; */
    min-width: 100vw;
    min-height: 100vh;
    position: relative;
  }
  .on {
    background-color: white;
    -webkit-transition: background-color 550ms linear;
    -ms-transition: background-color 550ms linear;
    transition: background-color 550ms linear;
  }
</style>
