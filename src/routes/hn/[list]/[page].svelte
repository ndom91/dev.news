<script context="module">
  const valid_lists = new Set(["news", "newest", "show", "ask", "jobs"]);

  export async function preload({ path, params }) {
    const product = path.split("/")[1];
    const filter = path.split("/")[2];

    const list =
      params.list === "top"
        ? "news"
        : params.list === "new"
        ? "newest"
        : params.list;

    if (!valid_lists.has(list)) {
      console.log("invalid");
      this.error(404, "Not found");
      return;
    }

    const page = +params.page;

    const res = await this.fetch(
      `https://api.hnpwa.com/v0/${list}/${page}.json`
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
  $: next = `/hn/${list}/${+page + 1}`;
</script>

<style>
  .wrapper {
    padding: 2em;
  }
  .more {
    padding: 5px 10px;
    border-radius: 5px;
    width: auto;
    max-width: 300px;
    display: block;
    margin: 0 auto;
    border: 1px solid var(--fg-light);
    text-align: center;
    text-decoration: none;
  }
</style>

<svelte:head>
  <title>dev.news | HackerNews</title>
  <meta
    name="description"
    content="Latest Hacker News stories in the {list} category" />
</svelte:head>

<Nav {filter} {product} />

<div class="wrapper">
  {#each items as item, i}
    {#if item}
      <!-- sometimes we get bad data? TODO investigate -->
      <ItemSummary {item} index={start + i} />
    {/if}
  {/each}

  {#if next}
    <a class="more" href={next}>More</a>
  {/if}
</div>
