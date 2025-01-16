<script>
    let {img, name, insta, clip, email, bio} = $props();
</script>
<div class='comic-card'>
    <img src={img} alt="Headshot of {name}">
    <h3>{name}</h3>
    <div>{bio}</div>
    <a href={insta}>Noah's Instagrams</a>
    <div>{email}</div>
    <a href={clip}>Stand-up clip</a>
</div>
