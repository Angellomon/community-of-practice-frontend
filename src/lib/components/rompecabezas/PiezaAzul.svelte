<script>
  import { PIEZA_LENGTH } from '../../util';

  export let src = '';
  export let scale = 1;
  export let top = 0;
  export let left = 0;
</script>

<img
  {src}
  alt="pieza"
  width={PIEZA_LENGTH * scale}
  height={PIEZA_LENGTH * scale}
  style={`margin-top: ${top}px; margin-left: ${left}px`}
/>

<style>
  img {
    padding: 0;
    /* width: 100%;
    height: 100%; */
  }
</style>
