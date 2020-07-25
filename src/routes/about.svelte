<style>
  .wrapper {
    padding: 1em;
    height: calc(100vh - 90px);
  }
  .header {
    display: flex;
    align-items: center;
    justify-content: start;
  }
  .header > h1 {
    margin: 0;
    margin-left: 10px;
    line-height: 0;
  }
</style>

<svelte:head>
  <title>About • dev.news</title>
</svelte:head>

<div class="wrapper">
  <div class="header">
    <img src="favicon.png" alt="logo" height="54" />
    <h1>About this app</h1>
  </div>

  <p>
    This is a simple Hacker News clone, built with
    <a href="https://sapper.svelte.dev">Sapper</a>
    an application framework for
    <a href="https://svelte.dev">Svelte</a>
    .
  </p>
  <p>
    It is based upon the sample HackerNews client published by Svelte themselves
    available
    <a href="https://github.com/sveltejs/hn.svelte.dev">here</a>
    with the addition of some Navigation as well as ProductHunt and dev.to News
    Feeds.
  </p>
  <p>
    Built with ❤ by
    <a href="https://github.com/ndom91">ndom91</a>
  </p>
</div>
