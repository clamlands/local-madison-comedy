<script>
  let { img, name, bio, clip, insta, facebook, youtube, email, website } = $props();

  const imgId = img.split('?id=')[1];
</script>

<div class="comic-card">
  <!-- <img src={img} alt="Headshot of {name}" /> -->
  <img
    src={`https://drive.google.com/thumbnail?id=${imgId}&sz=w1000`}
    alt={name}
    height="500"
    width="500"
  />
  <div class="details">
    <h3>{name}</h3>
    <div>{bio}</div>
    {#if clip}
      <a href={clip} target="_blank" rel="noreferrer">Stand-up clip</a>
    {/if}
    {#if insta}
      <a href={insta} target="_blank" rel="noreferrer">Instagram</a>
    {/if}
    {#if facebook}
      <a href={facebook} target="_blank" rel="noreferrer">Facebook</a>
    {/if}
    {#if youtube}
      <a href={youtube} target="_blank" rel="noreferrer">YouTube</a>
    {/if}
    {#if website}
      <a href={website} target="_blank" rel="noreferrer">{website}</a>
    {/if}
    {#if email}
      <div>Email: {email}</div>
    {/if}
  </div>
</div>

<style>
  .details {
    display: flex;
    flex-direction: column;
    gap: 5px;
  }

  a {
    color: var(--neon);
  }

  img {
    border-radius: 8px;
  }
</style>
