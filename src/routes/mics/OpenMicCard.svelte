<script>
  export let name = '';
  export let venue = '';
  export let description = '';
  export let image = null;
  export let time = '';
  export let signup = '';
  export let host = '';
</script>

<div class="mic-card">
  <div class="image-container">
    {#if image}
      <img src={image} alt={`${venue} open mic`} class="venue-image" />
    {/if}
  </div>
  <div class="mic-content">
    <h3>{venue}</h3>
    <div class="mic-details">
      {#if time}<p class="time">{time}</p>{/if}
      {#if host}<p class="host">Hosted by {host}</p>{/if}
      {#if signup}<p class="signup">Sign-up: {signup}</p>{/if}
    </div>
    <p class="description">{description}</p>
  </div>
</div>

<style>
  .mic-card {
    border: 1px solid var(--border);
    border-radius: 8px;
    overflow: hidden;
    margin-bottom: 1.5rem;
    background-color: rgba(255, 255, 255, 0.02);
    transition: transform 0.2s ease;
    display: block;
    width: 100%;
  }

  .mic-card:hover {
    transform: translateY(-2px);
  }

  .image-container {
    width: 100%;
    height: 200px;
    overflow: hidden;
    position: relative;
    background-color: rgba(0, 0, 0, 0.1);
    display: block;
  }

  .venue-image {
    width: 100%;
    height: 100%;
    object-fit: cover;
    object-position: center;
    display: block;
    border: none;
  }

  .mic-content {
    padding: 1.5rem;
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
  }

  .mic-details {
    display: flex;
    gap: 1rem;
    font-size: 0.9rem;
    color: var(--text);
    opacity: 0.8;
  }

  h3 {
    margin-bottom: 0.5rem;
  }

  .description {
    line-height: 1.5;
  }

  @media (max-width: 768px) {
    .mic-details {
      flex-direction: column;
      gap: 0.5rem;
    }

    .image-container {
      height: 150px;
    }
  }
</style>