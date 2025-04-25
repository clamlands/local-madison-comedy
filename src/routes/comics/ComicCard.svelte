<script>
  let { img, name, bio, clip, insta, facebook, youtube, tiktok, email, website } =
    $props();

  const imgId = img.split('?id=')[1];
  const shouldTruncate = bio.length > 400;
  let isExpanded = $state(false);

  let displayedBio = $derived(
    shouldTruncate && !isExpanded ? bio.slice(0, 400) + '...' : bio,
  );

  function toggleExpand() {
    isExpanded = !isExpanded;
  }
</script>

<div class="comic-card">
  <div class="image-container">
    <img src={`https://drive.google.com/thumbnail?id=${imgId}&sz=w1000`} alt={name} />
  </div>
  <div class="details">
    <h2>{name}</h2>
    <div class="bio-container">
      <div class="bio">{displayedBio}</div>
      {#if shouldTruncate}
        <button class="expand-button" on:click={toggleExpand}>
          {isExpanded ? 'Show less' : 'Read more'}
        </button>
      {/if}
    </div>
    <div class="links">
      {#if clip}
        <a href={clip} target="_blank" rel="noreferrer">Stand-up clip</a>
      {/if}
      {#if insta}
        <a href={insta} target="_blank" rel="noreferrer">Instagram</a>
      {/if}
      {#if tiktok}
        <a href={tiktok} target="_blank" rel="noreferrer">TikTok</a>
      {/if}
      {#if facebook}
        <a href={facebook} target="_blank" rel="noreferrer">Facebook</a>
      {/if}
      {#if youtube}
        <a href={youtube} target="_blank" rel="noreferrer">YouTube</a>
      {/if}
      {#if website}
        <a href={website} target="_blank" rel="noreferrer">Personal website</a>
      {/if}
      {#if email}
        <div class="email">Email: {email}</div>
      {/if}
    </div>
  </div>
</div>

<style>
  .comic-card {
    display: flex;
    flex-direction: column;
    height: 100%;
    background: rgba(0, 0, 0, 0.2);
    border-radius: 8px;
    overflow: hidden;
  }

  .details {
    display: flex;
    flex-direction: column;
    gap: 12px;
    padding: 16px;
    flex: 1;
  }

  h2 {
    margin: 0;
    font-size: 1.4rem;
  }

  .bio-container {
    flex: 1;
  }

  .bio {
    text-align: justify;
    hyphens: auto;
    line-height: 1.4;
    display: inline;
  }

  .expand-button {
    background: none;
    border: none;
    color: var(--neon);
    cursor: pointer;
    padding: 0 0 0 4px;
    font-size: 0.9rem;
    font-weight: bold;
    text-decoration: underline;
    display: inline;
  }

  .expand-button:hover {
    opacity: 0.8;
  }

  .links {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    margin-top: auto;
  }

  .image-container {
    width: 100%;
    aspect-ratio: 1;
    overflow: hidden;
  }

  img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  a {
    color: var(--neon);
  }

  .email {
    width: 100%;
  }
</style>
