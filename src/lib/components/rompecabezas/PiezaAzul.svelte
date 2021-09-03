<script>
  import { fade } from 'svelte/transition';
  import { PIEZA_LENGTH } from '../../util';

  export let src = '';
  export let scale = 1;
  export let top = 0;
  export let left = 0;

  export let hidden = true;
</script>

<span
  style={`width: ${PIEZA_LENGTH * scale}px; height: ${
    PIEZA_LENGTH * scale
  }px; margin-top: ${top}px; margin-left: ${left}px;`}
>
  {#if !hidden}
    <img
      {src}
      in:fade
      alt=""
      width={PIEZA_LENGTH * scale}
      height={PIEZA_LENGTH * scale}
      class:hidden
    />
  {/if}
</span>

<style>
  img {
    padding: 0;
    /* width: 100%;
    height: 100%; */
  }
  .hidden {
    visibility: hidden;
  }
</style>
