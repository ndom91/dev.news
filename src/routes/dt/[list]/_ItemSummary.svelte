<script>
  import About from "../../about.svelte";

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

  small {
    color: var(--fg-light);
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

  .cover-image {
    height: 3rem;
  }

  .item-details {
    padding: 0 1em;
  }

  @media all and (max-width: 600px) {
    article {
      flex-direction: column;
    }
    .cover-image {
      height: auto;
      width: 100%;
    }
    .item-details {
      padding: 1em;
    }
  }
</style>

<article>
  <img src={item.social_image} alt="Cover" class="cover-image" />
  <div class="item-details">
    <h2>
      <a href={item.domain ? item.url : `/item/${item.id}`}>
        {item.title}
        {#if item.domain}
          <small>({item.domain})</small>
        {/if}
      </a>
    </h2>

    {#if item.type === 'job'}
      <p>{item.time_ago}</p>
    {:else}
      <p>
        {item.public_reactions_count} reactions by
        <a
          target="_blank"
          alt="Dev.to User Profile for {item.user.username}"
          href="https://dev.to/{item.user.username}">
          {item.user.username}
        </a>
        {item.readable_publish_date} |
        <a alt="Comments Link" rel="prefetch" href="item/{item.id}">
          {item.comments_count}
          {item.comments_count === 1 ? 'comment' : 'comments'}
        </a>
      </p>
    {/if}

    <span class="index">{index}</span>

  </div>
</article>
