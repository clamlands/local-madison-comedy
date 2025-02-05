<script>
  import ccc from '$lib/images/shows/ccc.png';
  import cch from '$lib/images/shows/cch.png';
  import silly from '$lib/images/shows/silly.png';
  import cabaret from '$lib/images/shows/cabaret.png';
  import donttell from '$lib/images/shows/donttell.png';
  import donttellIcon from '$lib/images/icons/donttell-icon.png';
  import cccIcon from '$lib/images/icons/ccc.png';
  import insta from '$lib/images/icons/ig.png';
  import cchIcon from '$lib/images/icons/cch-icon.png';
</script>

<div class="width-container">
  <section class="hero">
    <h1 class="neon-title">Stand-up Shows</h1>
    <p>
      There are many regularly occuring comedy shows in Madison every month. Check out the
      production teams and shows below.
    </p>
  </section>
  <section>
    <div class="side-card">
      <img src={ccc} alt="Cheshire Cat Comedy logo" />
      <div class="content">
        <h2>Cheshire Cat Comedy</h2>
        <p>
          Founded by Sasha Rosser and then bringing on producers Noah Mailloux, Josh Glen,
          and Cody Lemke, Cheshire Cat Comedy brings live entertainment to venues across
          the Madison area and beyond. Their shows feature stand-up, funny educational
          lectures, live music, burlesque, drag, and more.
        </p>
        <strong>See more here:</strong>
        <div class="icon-links">
          <a href="https://cheshirecatcomedy.com/" target="_blank" rel="noreferrer">
            <img src={cccIcon} alt="Cheshire Cat Comedy icon" />
          </a>
          <a
            href="https://www.instagram.com/cheshirecatcomedyco/"
            target="_blank"
            rel="noreferrer"><img src={insta} alt="Instagram icon" /></a
          >
        </div>
      </div>
    </div>

    <hr class="narrow" />

    <div class="side-card flip">
      <div class="content">
        <h2>Capitol Comedy Hour</h2>
        <p>
          Capitol Comedy Hour is a late-night style variety show produced by Matt Jordan
          and Andrew Rynning, featuring the writing, performing, filming, and editing
          contributions of many other comics in the scene.
        </p>
        <strong>See more here:</strong>
        <div class="icon-links">
          <a href="https://www.capitolcomedyhour.com/" target="_blank" rel="noreferrer"
            ><img src={cchIcon} alt="Capitol Comedy Hour icon" /></a
          >
        </div>
      </div>
      <img src={cch} alt="Capitol Comedy Hour logo" />
    </div>

    <hr class="narrow" />

    <div class="side-card">
      <img src={silly} alt="Silly Street Comedy logo" />
      <div class="content">
        <h2>Silly Street Comedy</h2>
        <p>
          Founded by Eli Wilz, Silly Street Comedy is a cooperative effort of local
          comedians in Madison to bring great comedy to the Willy Street Neighborhood.
        </p>
        <strong>See more here:</strong>
        <div class="icon-links">
          <a
            href="https://www.instagram.com/sillystreetcomedy/"
            target="_blank"
            rel="noreferrer"><img src={insta} alt="Instagram icon" /></a
          >
        </div>
      </div>
    </div>

    <hr class="narrow" />

    <div class="side-card flip">
      <div class="content">
        <h2>Comedy at the Cabaret</h2>
        <p>
          With a tenure of 6+ years, Comedy at The Cabaret is a monthly stand-up showcase
          hosted by Allie Lindsay, with music by Jake Snell, at the wonderful North Street
          Cabaret!
        </p>
        <strong>See more here:</strong>
        <div class="icon-links">
          <a
            href="https://www.instagram.com/comedyatthecabaret/"
            target="_blank"
            rel="noreferrer"><img src={insta} alt="Instagram icon" /></a
          >
        </div>
      </div>
      <img src={cabaret} alt="Comedy at the Cabaret logo" />
    </div>

    <hr class="narrow" />

    <div class="side-card">
      <img src={donttell} alt="Don't Tell Comedy: Madison logo" />
      <div class="content">
        <h2>Don't Tell Comedy: Madison</h2>
        <p>Secret Pop-Up Comedy Shows in Madison!</p>
        <div class="icon-links">
          <a
            href="https://www.donttellcomedy.com/cities/madison/"
            target="_blank"
            rel="noreferrer"><img src={donttellIcon} alt="Don't Tell Comedy icon" /></a
          >
          <a
            href="https://www.instagram.com/donttellmadison/"
            target="_blank"
            rel="noreferrer"><img src={insta} alt="Instagram logo" /></a
          >
        </div>
      </div>
    </div>

    <hr class="narrow" />

    <h2>Antoine</h2>
    <h2>Chuky</h2>
    <h2>Justin Frisque</h2>
    <h2>Lady Laughs</h2>
    <h2>Lisa Quam</h2>
    <h2>The Merge</h2>
    <h2>Gamma Ray stuff</h2>
  </section>
</div>

<style>
  .width-container {
    max-width: 1000px;
    margin: 0 auto;
    padding: 2rem 0;
  }

  .hero {
    display: flex;
    flex-direction: column;
    max-width: 1000px;
    align-items: center;
    margin-top: -15px;
    width: 100%;
    padding-top: 30px;
    margin-bottom: 30px;
  }

  @keyframes pulsate-title {
    100% {
      text-shadow:
        0 0 3px #fff,
        0 0 5px #fff,
        0 0 7px #fff,
        0 0 40px var(--neon),
        0 0 80px var(--neon),
        0 0 90px var(--neon),
        0 0 100px var(--neon),
        0 0 150px var(--neon);
    }

    0% {
      text-shadow:
        0 0 2px #fff,
        0 0 4px #fff,
        0 0 6px #fff,
        0 0 10px var(--neon),
        0 0 45px var(--neon),
        0 0 55px var(--neon),
        0 0 70px var(--neon),
        0 0 80px var(--neon);
    }
  }

  .neon-title {
    /* font-family: Sacramento; */
    font-family: 'Vibur';
    /* font-family: 'Exo2'; */
    text-align: center;
    color: #fff;
    font-size: 5.9rem;
    font-weight: 400;
    animation: pulsate-title 1s infinite alternate;
    border: 0.2rem solid #fff;
    border-radius: 2rem;
    padding: 30px 50px;
    margin-bottom: 40px;
    box-shadow:
      0 0 0.2rem #fff,
      0 0 0.2rem #fff,
      0 0 2rem var(--neon),
      0 0 0.8rem var(--neon),
      0 0 2.8rem var(--neon),
      inset 0 0 1.3rem var(--neon);
  }

  .icon-links a img {
    width: 32px;
    height: 32px;
  }

  @media (min-width: 768px) {
    .neon-title {
      font-size: 6.2rem;
    }
  }
</style>
