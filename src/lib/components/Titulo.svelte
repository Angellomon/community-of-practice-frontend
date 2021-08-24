<script>
  import Emphasis from "./Emphasis.svelte";

  export let on = false;
</script>

<h2 class:on>community <br /><Emphasis>of</Emphasis> practice</h2>

<style>
  h2 {
    color: white;
    font-size: 3em;
    text-align: right;
    line-height: 1em;
    /* margin-top: -100px; */
  }
  .on {
    color: #3b726c;
  }
</style>
