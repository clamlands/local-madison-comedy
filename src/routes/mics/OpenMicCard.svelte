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