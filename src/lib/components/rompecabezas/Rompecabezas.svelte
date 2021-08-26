<script>
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

  const SCALE = 0.65;

  const handleClick = () => {
    console.log('click');
  };
</script>

<section>
  <div class="row">
    <PiezaAzul src={srcPieza1} scale={1} top={0} left={0} />
    <PiezaAzul src={srcPieza2} scale={1} top={-15} left={-36} />
    <PiezaAzul src={srcPieza3} scale={1} top={-18} left={-45} />
  </div>
  <div class="row">
    <PiezaAzul src={srcPieza4} scale={1.0} top={-39} left={3} />
    <PiezaPrincipal on:click={handleClick} scale={1} top={-56} left={-40} />
    <PiezaAzul src={srcPieza6} scale={1} top={-41} left={-37} />
  </div>
  <div class="row">
    <PiezaAzul src={srcPieza7} scale={1} top={-39} left={16} />
    <PiezaAzul src={srcPieza8} scale={1} top={-53.5} left={-37} />
    <PiezaAzul src={srcPieza9} scale={1} top={-51.5} left={-38} />
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
