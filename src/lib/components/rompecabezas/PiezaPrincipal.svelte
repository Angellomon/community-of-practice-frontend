<script>
  import { createEventDispatcher } from 'svelte';
  import { fade } from 'svelte/transition';
  import { PIEZA_LENGTH } from '../../util';

  const src = '/piezas/05.png';

  export let top = 0;
  export let left = 0;
  export let scale = 1;

  const dispatch = createEventDispatcher();

  let hover = false;
  let clicked = false;

  const handleHover = () => {
    hover = true;
  };

  const handleUnhover = () => {
    hover = false;
  };

  const handleClick = () => {
    clicked = true;
    dispatch('click');
  };
</script>

<div
  class="pieza"
  style={`width: ${PIEZA_LENGTH * scale}px; height: ${
    PIEZA_LENGTH * scale
  }px; margin-top: ${top}px; margin-left: ${left}px;`}
  on:mouseenter={handleHover}
  on:mouseleave={handleUnhover}
  on:click={handleClick}
>
  {#if hover || clicked}
    <span transition:fade />
  {/if}
  <img {src} alt="pieza 0" width={PIEZA_LENGTH * scale} height={PIEZA_LENGTH * scale} />
</div>

<style>
  div.pieza {
    position: relative;
  }
  div.pieza:hover {
    cursor: pointer;
    margin: 0;
    padding: 0;
  }
  img {
    align-self: center;
    justify-self: center;
    width: 100%;
    height: 100%;
  }
  span {
    margin-left: 50%;
    margin-top: 55%;
    z-index: 0;
    position: absolute;

    -webkit-box-shadow: 0px 0px 25px 20px rgba(195, 214, 98, 1);
    -moz-box-shadow: 0px 0px 25px 20px rgba(195, 214, 98, 1);
    box-shadow: 0px 0px 25px 20px rgba(195, 214, 98, 1);
  }
</style>
