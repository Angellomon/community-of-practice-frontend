<script>
  import { createEventDispatcher } from 'svelte';
  import PiezaPrincipal from './PiezaPrincipal.svelte';
  import PiezaAzul from './PiezaAzul.svelte';

  import srcPieza1 from '../../../assets/piezas/09.png';
  import srcPieza2 from '../../../assets/piezas/08.png';
  import srcPieza3 from '../../../assets/piezas/07.png';
  import srcPieza4 from '../../../assets/piezas/06.png';
  import srcPieza6 from '../../../assets/piezas/04.png';
  import srcPieza7 from '../../../assets/piezas/03.png';
  import srcPieza8 from '../../../assets/piezas/02.png';
  import srcPieza9 from '../../../assets/piezas/01.png';
  import { onDestroy } from 'svelte';

  const dispatch = createEventDispatcher();

  let pieza1Hidden = true;
  let pieza2Hidden = true;
  let pieza3Hidden = true;
  let pieza4Hidden = true;
  let pieza6Hidden = true;
  let pieza7Hidden = true;
  let pieza8Hidden = true;
  let pieza9Hidden = true;

  let timeout1;
  let timeout2;
  let timeout3;
  let timeout4;
  let timeout6;
  let timeout7;
  let timeout8;
  let timeout9;

  const handleClick = () => {
    timeout1 = setTimeout(() => {
      pieza1Hidden = false;
    }, 750);
    timeout2 = setTimeout(() => {
      pieza2Hidden = false;
    }, 350);
    timeout3 = setTimeout(() => {
      pieza3Hidden = false;
    }, 850);
    timeout4 = setTimeout(() => {
      pieza4Hidden = false;
    }, 250);
    timeout6 = setTimeout(() => {
      pieza6Hidden = false;
    }, 150);
    timeout7 = setTimeout(() => {
      pieza7Hidden = false;
    }, 550);
    timeout8 = setTimeout(() => {
      pieza8Hidden = false;
    }, 450);
    timeout9 = setTimeout(() => {
      pieza9Hidden = false;
    }, 650);
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
    <PiezaAzul src={srcPieza3} scale={1} top={-18} left={-45} hidden={pieza3Hidden} />
  </div>
  <div class="row">
    <PiezaAzul src={srcPieza4} scale={1.0} top={-39} left={3} hidden={pieza4Hidden} />
    <PiezaPrincipal on:click={handleClick} scale={1} top={-56} left={-40} />
    <PiezaAzul src={srcPieza6} scale={1} top={-41} left={-37} hidden={pieza6Hidden} />
  </div>
  <div class="row">
    <PiezaAzul src={srcPieza7} scale={1} top={-39} left={16} hidden={pieza7Hidden} />
    <PiezaAzul src={srcPieza8} scale={1} top={-53.5} left={-37} hidden={pieza8Hidden} />
    <PiezaAzul src={srcPieza9} scale={1} top={-51.5} left={-38} hidden={pieza9Hidden} />
  </div>
</section>

<style>
  div.row {
    display: flex;
    flex-direction: row;
    flex-wrap: nowrap;
    margin-left: 30px;
    justify-content: center;
    align-items: center;
  }
</style>
