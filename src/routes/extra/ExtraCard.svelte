<script>
  let { img, title, description, description2, description3, links = [], imgAlt = '', flip = false } = $props();
</script>

<div class="extra-card {flip ? 'flip' : ''}">
  <img src={img} alt={imgAlt} />
  <div class="content">
    <h3>{title}</h3>
    <p>{description}</p>
    {#if description2}
      <p>{description2}</p>
    {/if}
    {#if description3}
      <p>{description3}</p>
    {/if}
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
  .extra-card {
    display: flex;
    flex-direction: row;
    background: rgba(0, 0, 0, 0.3);
    gap: 16px;
    margin: 20px 0;
    padding: 16px;
    border-radius: 12px;
    overflow: hidden;
  }

  .extra-card.flip {
    flex-direction: row-reverse;
  }

  .extra-card > img {
    width: 250px;
    height: 250px;
    object-fit: cover;
    border-radius: 8px;
    flex-shrink: 0;
  }

  .content {
    flex: 1;
    display: flex;
    flex-direction: column;
    min-height: 250px;
    position: relative;
    gap: 12px;
    padding-bottom: 60px; /* Space for links */
  }

  h3 {
    margin: 0;
    font-size: 1.5rem;
    color: var(--text);
  }

  .content p {
    margin: 0;
    line-height: 1.5;
  }

  .icon-links {
    display: flex;
    gap: 20px;
    position: absolute;
    bottom: 0;
    left: 0;
    padding-top: 16px;
    background: linear-gradient(to top, rgba(0, 0, 0, 0.3), transparent);
    width: 100%;
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
    .extra-card,
    .extra-card.flip {
      flex-direction: column;
    }

    .extra-card > img {
      width: 100%;
      height: auto;
    }

    .content {
      min-height: auto;
      padding-top: 16px;
      padding-bottom: 0;
    }

    .icon-links {
      position: relative;
      margin-top: 16px;
      padding-top: 0;
      background: none;
    }
  }
</style>