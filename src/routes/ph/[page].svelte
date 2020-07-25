<script context="module">
  export async function preload({ path, params }) {
    const product = path.split("/")[1];
    const filter = path.split("/")[2];

    const page = +params.page;

    const res = await this.fetch(
      `https://api.rss2json.com/v1/api.json?rss_url=https%3A%2F%2Fwww.producthunt.com%2Ffeed%3Fcategory%3Dundefined&api_key=ib5kfi6dwpoyf28h3fovhjoehjravssmevnsurte`
    );
    const items = await res.json();

    return {
      page,
      items,
      product,
      filter,
    };
  }
</script>

<script>
  import ItemSummary from "./_ItemSummary.svelte";
  import Nav from "../../components/Nav.svelte";

  export let page;
  export let items;
  export let product;
  export let filter;

  const PAGE_SIZE = 10;

  $: start = 1 + (page - 1) * PAGE_SIZE;
  $: next = `ph/${+page + 1}`;
</script>

<style>
  .wrapper {
    padding: 2em;
  }
</style>

<svelte:head>
  <title>dev.news | ProductHunt</title>
  <meta name="description" content="Latest ProductHunt Apps" />
</svelte:head>

<Nav {filter} {product} />

<div class="wrapper">
  {#each items.items as item, i}
    {#if item}
      <!-- sometimes we get bad data? TODO investigate -->
      <ItemSummary {item} index={start + i} />
    {/if}
  {/each}
</div>

{#if next}
  <a class="more" href={next}>More...</a>
{/if}
