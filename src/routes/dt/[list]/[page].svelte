<script context="module">
  const valid_lists = new Set(["fresh", "rising", "all"]);

  export async function preload({ path, params }) {
    const product = path.split("/")[1];
    const filter = path.split("/")[2];

    const list =
      params.list === "fresh"
        ? "fresh"
        : params.list === "rising"
        ? "rising"
        : params.list;

    if (!valid_lists.has(list)) {
      console.log("invalid");
      this.error(404, "Not found");
      return;
    }

    const page = +params.page;

    const res = await this.fetch(
      `https://dev.to/api/articles?state=${
        filter === "all" ? "" : filter
      }&top=10`
    );
    const items = await res.json();

    return {
      page,
      list,
      items,
      product,
      filter,
    };
  }
</script>

<script>
  import ItemSummary from "./_ItemSummary.svelte";
  import Nav from "../../../components/Nav.svelte";

  export let page;
  export let list;
  export let items;
  export let product;
  export let filter;

  const PAGE_SIZE = 30;

  $: start = 1 + (page - 1) * PAGE_SIZE;
  $: next = `/dt/${list}/${+page + 1}`;
</script>

<style>
  .wrapper {
    padding: 2em;
  }
</style>

<svelte:head>
  <title>dev.news | Dev.to</title>
  <meta name="description" content="Latest Dev.to stories" />
</svelte:head>

<Nav {filter} {product} />

<div class="wrapper">
  {#each items as item, i}
    {#if item}
      <!-- sometimes we get bad data? TODO investigate -->
      <ItemSummary {item} index={start + i} />
    {/if}
  {/each}
</div>
