<script>
  export let venue = '';
  export let description = '';
  export let image = null;
  export let time = '';
  export let signup = '';
  export let host = '';
  export let flip = false;
</script>

<div class="mic-card {flip ? 'flip' : ''}">
  <img src={image} alt={`${venue} open mic`} />
  <div class="mic-content">
    <h3>{venue}</h3>
    <div class="mic-details">
      {#if time}<p class="time">{time}</p>{/if}
      {#if signup}<p class="signup">{@html signup}</p>{/if}
      {#if host}<p class="host">Hosted by {host}</p>{/if}
    </div>
    <p class="description">{description}</p>
  </div>
</div>

<style>
  .mic-card {
    display: flex;
    flex-direction: row;
    background: rgba(0, 0, 0, 0.3);
    border-radius: 12px;
    overflow: hidden;
    margin: 20px 0;
    padding: 16px;
    gap: 16px;
    align-items: start;
  }

  .mic-card.flip {
    flex-direction: row-reverse;
  }

  .mic-card > img {
    width: 250px;
    height: 250px;
    object-fit: cover;
    border-radius: 8px;
    flex-shrink: 0;
  }

  .mic-content {
    flex: 1;
    display: flex;
    flex-direction: column;
    gap: 12px;
  }

  h3 {
    margin: 0;
    font-size: 1.5rem;
    color: var(--text);
  }

  .mic-details {
    display: flex;
    flex-direction: column;
    gap: 8px;
    color: var(--text);
    opacity: 0.9;
  }

  .mic-details :global(a) {
    color: #1877f2 !important;
    font-weight: bold !important;
    text-decoration: none !important;
  }

  .mic-details :global(a:hover) {
    text-decoration: underline !important;
  }

  .description {
    line-height: 1.5;
    margin-top: 8px;
  }

  @media (max-width: 768px) {
    .mic-card,
    .mic-card.flip {
      flex-direction: column;
    }

    .mic-card > img {
      width: 100%;
      height: auto;
    }
  }
</style>
