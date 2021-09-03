<script>
  import Emphasis from './Emphasis.svelte';

  export let on = false;
</script>

<h2 class:on>community<br /><Emphasis>of practice</Emphasis></h2>

<style>
  h2 {
    color: #6eceb2;
    font-size: 2.9em;
    text-align: left;
    line-height: 1em;
    /* margin-top: -100px; */
  }
  .on {
    color: #6eceb2;
  }
</style>
