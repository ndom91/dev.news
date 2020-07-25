<script>
  import ThemeToggler from "../components/ThemeToggler.svelte";

  export let segment;
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
    padding: 0 20px;
  }

  li {
    list-style: none;
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

  .dt-li {
    width: 64px;
    display: flex;
    justify-content: center;
  }
</style>

<nav>

  <ul>
    <li>
      <a
        rel="prefetch"
        class={segment === 'hn' ? 'selected' : ''}
        href="hn/top/1">
        <img alt="HackerNews" class="icon" src="ycombinator.svg" />
      </a>
    </li>
    <li>
      <a rel="prefetch" class={segment === 'ph' ? 'selected' : ''} href="ph/1">
        <img alt="ProductHunt" class="icon" src="producthunt.svg" />
      </a>
    </li>
    <li class="dt-li">
      <a
        rel="prefetch"
        class={segment === 'dt' ? 'dt selected' : 'dt'}
        href="dt/rising/1">
        <img alt="Dev.to" class="icon" src="devto_white.svg" />
      </a>
    </li>
    <li>
      <ThemeToggler />
    </li>
  </ul>
</nav>
