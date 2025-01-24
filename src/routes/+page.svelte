<script>
  import UpcomingShows from './UpcomingShows.svelte';
  import ComicCard from './comics/ComicCard.svelte';
  import noah from '$lib/images/noah-750.webp';
  import eli from '$lib/images/EliWilz-750.webp';

  const featuredComics = [
    {
      img: noah,
      name: 'Noah Mailloux',
      insta: 'https://www.instagram.com/noahmailloux/',
      clip: 'https://www.youtube.com/watch?v=FzSgMFVobT0',
      bio: 'Host of The Revolver Open Mic and producer with Cheshire Cat Comedy',
    },
    {
      img: eli,
      name: 'Eli Wilz',
      insta: 'https://www.instagram.com/eliwilz/',
      clip: 'https://www.youtube.com/watch?v=iqOCiv-Sn1s',
      bio: 'Madison-based comedian known for his unique perspective and sharp wit',
    },
  ];
</script>

<section class="hero">
  <h1 class="neon-title">madison comedy</h1>
  <p class="tagline">Your guide to Madison's comedy scene</p>
</section>
<div class="width-container">
  <section class="quick-links">
    <a href="/mics" class="quick-link">
      <h3>Open Mics</h3>
      <p>Try your hand at stand-up</p>
    </a>
    <a href="/shows" class="quick-link">
      <h3>Shows</h3>
      <p>Upcoming comedy events</p>
    </a>
    <a href="/comics" class="quick-link">
      <h3>Comics</h3>
      <p>Meet local performers</p>
    </a>
  </section>
  <section class="about-scene">
    <div class="venue-highlights">
      <h3>Key Venues</h3>
      <ul>
        <li><strong>Comedy on State</strong> - Madison's premier comedy club</li>
        <li><strong>The Rigby</strong> - Weekly open mic for new talent</li>
        <li><strong>The Argus</strong> - Weekly open mic for new talent</li>
      </ul>
    </div>
  </section>

  <UpcomingShows />
</div>

<style>
  .hero {
    display: flex;
    flex-direction: column;
    align-items: center;
    background-color: var(--text);
    margin-top: -15px;
    width: 100%;
    padding: 30px 0;
    margin-bottom: 30px;
  }

  .tagline {
    color: white;
  }

  @keyframes pulsate {
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
    color: #fff;
    font-size: 6.2rem;
    font-weight: 400;
    animation: pulsate 1.5s infinite alternate;
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
</style>
