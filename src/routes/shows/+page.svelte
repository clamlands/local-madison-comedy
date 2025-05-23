<script>
  import ShowCard from './ShowCard.svelte';
  import ccc from '$lib/images/shows/ccc-750.webp';
  import cch from '$lib/images/shows/cch-750.webp';
  import silly from '$lib/images/shows/silly-750.webp';
  import cabaret from '$lib/images/shows/cabaret.webp';
  import donttell from '$lib/images/shows/donttell-750.webp';
  import oneMotion from '$lib/images/shows/1motion-750.webp';

  import cccIcon from '$lib/images/icons/ccc.png';
  import insta from '$lib/images/icons/ig.png';
  import donttellIcon from '$lib/images/icons/donttell-icon.png';
  import cchIcon from '$lib/images/icons/cch-icon.png';
</script>

<section class="hero">
  <h1 class="neon-title">Comedy Shows</h1>
  <p>
    Madison’s comedy scene is packed with recurring shows every month, featuring stand-up,
    improv, and variety acts. Whether you're looking for a polished showcase or a
    laid-back open mic, there's something for everyone. Explore the production teams and
    shows below to find your next night of laughs!
  </p>
</section>

<hr class="section-divider" />

<section>
  <div class="width-container">
    <ShowCard
      img={ccc}
      title="Cheshire Cat Comedy"
      description="Founded by Sasha Rosser and then bringing on producers Noah Mailloux, Josh Glen, and Cody Lemke, Cheshire Cat Comedy brings live entertainment to venues across the Madison area and beyond. Their shows feature stand-up, funny educational lectures, live music, burlesque, drag, and more."
      links={[
        {
          icon: cccIcon,
          url: 'https://cheshirecatcomedy.com/',
          alt: 'Cheshire Cat Comedy website',
        },
        {
          icon: insta,
          url: 'https://www.instagram.com/cheshirecatcomedyco/',
          alt: 'Instagram',
        },
      ]}
    />

    <ShowCard
      img={cch}
      title="Capitol Comedy Hour"
      description="Capitol Comedy Hour is a late-night style variety show produced by Matt Jordan and Andrew Rynning, featuring the writing, performing, filming, and editing contributions of many other comics in the scene."
      links={[
        {
          icon: cchIcon,
          url: 'https://www.capitolcomedyhour.com/',
          alt: 'Capitol Comedy Hour website',
        },
      ]}
      flip={true}
    />

    <ShowCard
      img={silly}
      title="Silly Street Comedy"
      description="Founded by Eli Wilz, Silly Street Comedy is a cooperative effort of local comedians in Madison to bring great comedy to the Willy Street Neighborhood."
      links={[
        {
          icon: insta,
          url: 'https://www.instagram.com/sillystreetcomedy/',
          alt: 'Instagram',
        },
      ]}
    />
    <ShowCard
      img={cabaret}
      title="Comedy at the Cabaret"
      description="With a tenure of 7 years, Comedy at The Cabaret is a monthly stand-up showcase hosted by Allie Lindsay, with music by Jake Snell, at the wonderful North Street Cabaret!"
      links={[
        {
          icon: insta,
          url: 'https://www.instagram.com/comedyatthecabaret/',
          alt: 'Instagram',
        },
      ]}
      flip={true}
    />
    <ShowCard
      img={donttell}
      title="Don't Tell Madison"
      description="Don't Tell Comedy hosts secret pop-up comedy shows in unique, unexpected venues. The lineup is a surprise, featuring top-tier comedians, and the location is revealed on the day of the show. It’s an intimate, one-of-a-kind comedy experience that brings laughter to unconventional spaces."
      links={[
        {
          icon: donttellIcon,
          url: 'https://www.donttellcomedy.com/cities/madison/',
          alt: 'Website',
        },
        {
          icon: insta,
          url: 'https://www.instagram.com/donttellmadison/',
          alt: 'Instagram',
        },
      ]}
    />
    <ShowCard
      img={oneMotion}
      title="Comedy Poetry Jam"
      description="Madison's most diverse comedy & poetry showcase occurs on the 4th Saturday of every month—hosted by comedian Antoine McNeail through his production company 1Motion Out Reach Enterprise."
      links={[
        {
          icon: insta,
          url: 'https://www.instagram.com/comedyandpoetryjam',
          alt: 'Instagram',
        },
      ]}
      flip={true}
    />
  </div>
</section>

<style>
  .hero {
    display: flex;
    flex-direction: column;
    max-width: 1000px;
    align-items: center;
    margin-top: -15px;
    width: 100%;
    padding: 30px;
    margin-bottom: 30px;
    text-align: center;
  }

  .width-container {
    max-width: 1000px;
    margin: 0 auto;
    padding: 2rem 0;
  }

  .section-divider {
    border: none;
    border-bottom: 1px solid rgba(255, 255, 255, 0.2);
    margin: 2rem 0;
    width: 100%;
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
    font-family: 'Vibur';
    text-align: center;
    color: #fff;
    font-size: 75px;
    font-weight: 400;
    /* animation: pulsate-title 1s infinite alternate; */
    border: 0.2rem solid #fff;
    border-radius: 2rem;
    padding: 30px 50px;
    margin-bottom: 40px;
    text-shadow:
      0 0 2px #fff,
      0 0 4px #fff,
      0 0 6px #fff,
      0 0 10px var(--neon),
      0 0 45px var(--neon),
      0 0 55px var(--neon),
      0 0 70px var(--neon),
      0 0 80px var(--neon);
    box-shadow:
      0 0 0.2rem #fff,
      0 0 0.2rem #fff,
      0 0 2rem var(--neon),
      0 0 0.8rem var(--neon),
      0 0 2.8rem var(--neon),
      inset 0 0 1.3rem var(--neon);
  }

  @media (min-width: 768px) {
    .neon-title {
      font-size: 6.2rem;
    }
  }
</style>
