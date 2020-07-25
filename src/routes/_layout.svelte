<script>
  import { stores } from "@sapper/app";
  import NavBottom from "../components/NavBottom.svelte";
  import PreloadingIndicator from "../components/PreloadingIndicator.svelte";

  const { preloading } = stores();
  export let segment;
</script>

<style>
  main {
    position: relative;
    max-width: 56em;
    margin: 0 auto;
    box-sizing: border-box;
  }
</style>

{#if $preloading}
  <PreloadingIndicator />
{/if}

<main>
  <slot />
</main>

<NavBottom {segment} />
