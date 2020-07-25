<script>
  export let item;
  export let index;
</script>

<style>
  article {
    position: relative;
    display: flex;
    padding: 0 0 0 4em;
    margin: 0 0 1.5em 0;
  }

  h2 {
    font-size: 1em;
    font-weight: 500;
    margin: 0 0 0.5em 0;
    color: var(--fg);
  }

  h2 a {
    text-decoration: none;
  }

  p {
    font-size: 0.8em;
    color: var(--fg-light);
    margin: 0;
    font-weight: 300;
  }

  .index {
    position: absolute;
    font-size: 1.6em;
    font-weight: 200;
    color: var(--fg-light);
    left: 0.2em;
    top: 0;
    text-align: right;
    width: 0.75em;
    line-height: 1;
  }

  @media all and (max-width: 600px) {
    article {
      flex-direction: column;
    }
  }
</style>

<article>
  <div class="item-details">
    <h2>
      <a href={item.link}>{item.title}</a>
    </h2>

    <p>
      <a
        target="_blank"
        alt="Dev.to User Profile for {item.author}"
        href="https://dev.to/{item.author}">
        {item.author}
      </a>
      {new Date(item.pubDate).toLocaleString('de-DE')}
    </p>

    <span class="index">{index}</span>

  </div>
</article>
