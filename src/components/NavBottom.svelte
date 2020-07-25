<script>
  import ThemeToggler from "../components/ThemeToggler.svelte";

  export let product;
</script>

<style>
  nav {
    background-color: var(--bg);
    border-top: 1px solid #ff6600;
    color: var(--fg-light);
    font-weight: 300;
    position: sticky;
    height: 56px;
    bottom: 0;
    left: 0;
    width: 100%;
    display: flex;
    justify-content: center;
  }

  .icon {
    display: block;
    width: 1em;
    height: 1em;
    float: left;
    font-size: 2em;
    position: relative;
    box-sizing: border-box;
  }

  ul {
    width: 100%;
    max-width: 500px;
    height: 100%;
    display: flex;
    justify-content: space-around;
    margin: 0;
    padding: 0;
  }

  ul::after {
    content: "";
    display: block;
    clear: both;
  }

  li {
    list-style: none;
  }

  .selected {
    position: relative;
    display: inline-block;
    color: var(--fg);
  }

  .selected::after {
    position: absolute;
    content: "";
    width: calc(100% - 1em);
    height: 2px;
    background-color: #ff6600;
    display: block;
    bottom: 0;
  }

  a {
    color: inherit;
    text-decoration: none;
    display: block;
    font-weight: 500;
    width: 64px;
    height: 100%;
    display: grid;
    place-items: center;
  }

  .dt {
    margin-top: 10px;
    width: 35px;
    height: 35px;
    padding: 0 5px 0 5px;
    background: #000;
    border-radius: 5px;
  }
</style>

<nav>

  <ul>
    <li>
      <a
        rel="prefetch"
        class={product === 'hn' ? 'selected' : ''}
        href="hn/top/1">
        <img alt="HackerNews" class="icon" src="ycombinator.svg" />
      </a>
    </li>
    <li>
      <a rel="prefetch" class={product === 'ph' ? 'selected' : ''} href="ph/1">
        <img alt="ProductHunt" class="icon" src="producthunt.svg" />
      </a>
    </li>
    <li>
      <a
        rel="prefetch"
        class={product === 'dt' ? 'dt selected' : 'dt'}
        href="dt/rising/1">
        <img alt="Dev.to" class="icon" src="devto_white.svg" />
      </a>
    </li>
    <li>
      <ThemeToggler />
    </li>
  </ul>
</nav>
