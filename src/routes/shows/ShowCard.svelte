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
    flex-direction: row;
    background: rgba(0, 0, 0, 0.3);
    gap: 16px;
    margin: 20px 0;
    padding: 16px;
    border-radius: 12px;
    overflow: hidden;
  }
  
  .show-card.flip {
    flex-direction: row-reverse;
  }

 .show-card > img {
     width: 200px;
     height: 200px;
     object-fit: cover;
     border-radius: 8px;
     flex-shrink: 0;
 }
 
 .content {
     flex: 1;
     display: flex;
     flex-direction: column;
     min-height: 200px;
     max-height: 200px;
     position: relative;
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
    position: absolute;
    bottom: 0;
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

    .content {
      min-height: auto;
      max-height: auto;
      padding-top: 16px;
    }

    .icon-links {
      position: relative;
      margin-top: 16px;
    }
  }
</style>