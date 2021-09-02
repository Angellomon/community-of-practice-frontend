<script>
  import Emphasis from './Emphasis.svelte';

  export let on = false;
</script>

<h2 class:on><Emphasis>community</Emphasis><br />of practice</h2>

<style>
  h2 {
    color: white;
    font-size: 2.9em;
    text-align: right;
    line-height: 1em;
    /* margin-top: -100px; */
  }
  .on {
    color: #3b726c;
  }
</style>
