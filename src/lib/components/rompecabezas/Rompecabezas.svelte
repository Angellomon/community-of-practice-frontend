<script>
  import { createEventDispatcher } from 'svelte';
  import PiezaPrincipal from './PiezaPrincipal.svelte';
  import PiezaAzul from './PiezaAzul.svelte';
  import { onDestroy } from 'svelte';

  const srcPieza1 = '/piezas/09.png';
  const srcPieza2 = '/piezas/08.png';
  const srcPieza3 = '/piezas/07.png';
  const srcPieza4 = '/piezas/06.png';
  const srcPieza6 = '/piezas/04.png';
  const srcPieza7 = '/piezas/03.png';
  const srcPieza8 = '/piezas/02.png';
  const srcPieza9 = '/piezas/01.png';

  const dispatch = createEventDispatcher();

  const DEFAULT_HIDDEN = true;

  let pieza1Hidden = DEFAULT_HIDDEN;
  let pieza2Hidden = DEFAULT_HIDDEN;
  let pieza3Hidden = DEFAULT_HIDDEN;
  let pieza4Hidden = DEFAULT_HIDDEN;
  let pieza6Hidden = DEFAULT_HIDDEN;
  let pieza7Hidden = DEFAULT_HIDDEN;
  let pieza8Hidden = DEFAULT_HIDDEN;
  let pieza9Hidden = DEFAULT_HIDDEN;

  let timeout1;
  let timeout2;
  let timeout3;
  let timeout4;
  let timeout6;
  let timeout7;
  let timeout8;
  let timeout9;

  const TIMEOUT_BASE = 200;

  const handleClick = () => {
    timeout1 = setTimeout(() => {
      pieza1Hidden = false;
    }, TIMEOUT_BASE * 7);
    timeout2 = setTimeout(() => {
      pieza2Hidden = false;
    }, TIMEOUT_BASE * 3);
    timeout3 = setTimeout(() => {
      pieza3Hidden = false;
    }, TIMEOUT_BASE * 8);
    timeout4 = setTimeout(() => {
      pieza4Hidden = false;
    }, TIMEOUT_BASE * 2);
    timeout6 = setTimeout(() => {
      pieza6Hidden = false;
    }, TIMEOUT_BASE * 1);
    timeout7 = setTimeout(() => {
      pieza7Hidden = false;
    }, TIMEOUT_BASE * 5);
    timeout8 = setTimeout(() => {
      pieza8Hidden = false;
    }, TIMEOUT_BASE * 4);
    timeout9 = setTimeout(() => {
      pieza9Hidden = false;
    }, TIMEOUT_BASE * 6);
    dispatch('click');
  };

  onDestroy(() => {
    clearTimeout(timeout1);
    clearTimeout(timeout2);
    clearTimeout(timeout3);
    clearTimeout(timeout4);
    clearTimeout(timeout6);
    clearTimeout(timeout7);
    clearTimeout(timeout8);
    clearTimeout(timeout9);
  });
</script>

<section>
  <div class="row">
    <PiezaAzul src={srcPieza1} scale={1} top={0} left={0} hidden={pieza1Hidden} />
    <PiezaAzul src={srcPieza2} scale={1} top={-15} left={-36} hidden={pieza2Hidden} />
    <PiezaAzul src={srcPieza3} scale={1} top={-19} left={-45} hidden={pieza3Hidden} />
  </div>
  <div class="row">
    <PiezaAzul src={srcPieza4} scale={1.0} top={-40} left={4} hidden={pieza4Hidden} />
    <PiezaPrincipal on:click={handleClick} scale={1} top={-58.5} left={-39.5} />
    <PiezaAzul src={srcPieza6} scale={1} top={-44} left={-37.5} hidden={pieza6Hidden} />
  </div>
  <div class="row">
    <PiezaAzul src={srcPieza7} scale={1} top={-39.5} left={18} hidden={pieza7Hidden} />
    <PiezaAzul src={srcPieza8} scale={1} top={-53.5} left={-37.5} hidden={pieza8Hidden} />
    <PiezaAzul src={srcPieza9} scale={1.04} top={-52.5} left={-39} hidden={pieza9Hidden} />
  </div>
</section>

<style>
  div.row {
    display: flex;
    flex-direction: row;
    flex-wrap: nowrap;
    /* margin-left: 30px; */
    justify-content: center;
    align-items: center;
  }
</style>
