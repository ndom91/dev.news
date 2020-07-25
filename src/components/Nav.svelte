<script>
  export let product;
  export let filter;
</script>

<style>
  .wrapper {
    position: sticky;
    width: 100%;
    top: 0;
    left: 0;
    background-color: var(--bg);
    z-index: 99;
  }
  nav {
    /* background-color: rgba(255, 102, 0, 0.05); */
    border-bottom: 1px solid #ff6600;
    color: var(--fg-light);
    font-weight: 300;
    padding: 0 1em;
  }

  .icon {
    display: block;
    width: 1em;
    height: 1em;
    float: left;
    font-size: 2em;
    position: relative;
    top: 0.4em;
    box-sizing: border-box;
    margin: 0 0.5em 0 0;
  }

  ul {
    margin: 0;
    padding: 0;
  }

  ul::after {
    content: "";
    display: block;
    clear: both;
  }

  li {
    display: block;
    float: left;
  }

  .about {
    float: right;
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
    padding: 1em 0.5em;
    display: block;
    font-weight: 500;
  }

  .dt {
    width: 35px;
    height: 30px;
    padding: 0 5px 0 5px;
    background: #000;
    border-radius: 5px;
  }

  @media (min-width: 400px) {
    .icon {
      margin: 0 0.5em 0 0;
    }

    li {
      display: inline-block;
    }
  }
  @media all and (max-width: 600px) {
    .wrapper {
      width: 100vw;
    }
  }
</style>

<div class="wrapper">
  {#if product === 'hn'}
    <nav>
      <img alt="Svelte Hacker News logo" class="icon" src="ycombinator.svg" />

      <ul>
        <li>
          <a
            rel="prefetch"
            class={filter === 'top' ? 'selected' : ''}
            href="hn/top/1">
            top
          </a>
        </li>
        <li>
          <a
            rel="prefetch"
            class={filter === 'new' ? 'selected' : ''}
            href="hn/new/1">
            new
          </a>
        </li>
        <li>
          <a
            rel="prefetch"
            class={filter === 'show' ? 'selected' : ''}
            href="hn/show/1">
            show
          </a>
        </li>
        <li>
          <a
            rel="prefetch"
            class={filter === 'ask' ? 'selected' : ''}
            href="hn/ask/1">
            ask
          </a>
        </li>
        <li>
          <a
            rel="prefetch"
            class={filter === 'jobs' ? 'selected' : ''}
            href="hn/jobs/1">
            jobs
          </a>
        </li>

        <li class="about">
          <a
            rel="prefetch"
            class={filter === 'about' ? 'selected' : ''}
            href="about">
            about
          </a>
        </li>
      </ul>
    </nav>
  {:else if product === 'dt'}
    <nav>
      <img alt="Dev.to Logo" class="dt icon" src="devto_white.svg" />
      <ul>
        <li class="rising">
          <a
            rel="prefetch"
            class={filter === 'rising' ? 'selected' : ''}
            href="dt/rising/1">
            rising
          </a>
        </li>
        <li class="fresh">
          <a
            rel="prefetch"
            class={filter === 'fresh' ? 'selected' : ''}
            href="dt/fresh/1">
            fresh
          </a>
        </li>
        <li class="all">
          <a
            rel="prefetch"
            class={filter === 'all' ? 'selected' : ''}
            href="dt/all/1">
            top
          </a>
        </li>

        <li class="about">
          <a
            rel="prefetch"
            class={filter === 'about' ? 'selected' : ''}
            href="about">
            about
          </a>
        </li>
      </ul>
    </nav>
  {:else if product === 'ph'}
    <nav>
      <img alt="Dev.to Logo" class="icon" src="producthunt.svg" />
      <ul>
        <li class="all">
          <a rel="prefetch" class="selected" href="ph/1">all</a>
        </li>

        <li class="about">
          <a
            rel="prefetch"
            class={filter === 'about' ? 'selected' : ''}
            href="about">
            about
          </a>
        </li>
      </ul>
    </nav>
  {/if}

</div>
