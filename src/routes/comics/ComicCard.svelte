<script>
  let { img, name, bio, clip, insta, facebook, youtube, email, website } = $props();

  const imgId = img.split('?id=')[1];
  console.log(img);
  console.log(imgId);
</script>

<div class="comic-card">
  <!-- <img src={img} alt="Headshot of {name}" /> -->
  <img src={`https://drive.google.com/thumbnail?id=${imgId}&sz=w1000`} alt="" />
  <div class="details">
    <h3>{name}</h3>
    <div>{bio}</div>
    {#if clip}
      <a href={clip}>Stand-up clip</a>
    {/if}
    {#if insta}
      <a href={insta}>Instagram</a>
    {/if}
    {#if facebook}
      <a href={facebook}>Facebook</a>
    {/if}
    {#if youtube}
      <a href={youtube}>YouTube</a>
    {/if}
    {#if email}
      <div>Email: {email}</div>
    {/if}
    {#if website}
      <a href={website}>Website</a>
    {/if}
  </div>
</div>

<style>
  .details {
    display: flex;
    flex-direction: column;
    gap: 5px;
  }
</style>
