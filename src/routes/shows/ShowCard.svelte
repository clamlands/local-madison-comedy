<script>
  let { img, title, description, links = [], imgAlt = '', flip = false } = $props();
</script>

<div class="show-card {flip ? 'flip' : ''}">
  <img src={img} alt={imgAlt || title} />
  <div class="content">
    <h2>{title}</h2>
    <p>{description}</p>
    {#if links.length > 0}
      <div class="icon-links">
        {#each links as { icon, url, alt }}
          <a href={url} target="_blank" rel="noreferrer">
            <img src={icon} {alt} />
          </a>
        {/each}
      </div>
    {/if}
  </div>
</div>

<style>
  .show-card {
    display: flex;
    gap: 20px;
    margin-bottom: 0;
    padding-bottom: 30px;
    border-bottom: 1px solid rgba(255, 255, 255, 0.2);
    margin-top: 30px;
    align-items: start;
  }

  .show-card.flip {
    flex-direction: row-reverse;
  }

  .show-card > img {
    width: 300px;
    height: 300px;
    object-fit: cover;
    border-radius: 8px;
  }

  .content {
    flex: 1;
    display: flex;
    flex-direction: column;
    gap: 15px;
  }

  h2 {
    margin: 0;
    font-size: 2rem;
    color: #fff;
  }

  .content p {
    margin: 0;
  }

  .icon-links {
    display: flex;
    gap: 20px;
    margin-top: 10px;
  }

  .icon-links a img {
    width: 32px;
    height: 32px;
    transition: transform 0.2s ease;
  }

  .icon-links a:hover img {
    transform: scale(1.1);
  }

  @media (max-width: 768px) {
    .show-card,
    .show-card.flip {
      flex-direction: column;
    }

    .show-card > img {
      width: 100%;
      height: auto;
    }
  }
</style>