<script>
  import UpcomingShows from './UpcomingShows.svelte';
  import ComicCard from './comics/ComicCard.svelte';
  import BenDan from '$lib/images/homepage/DanBen.jpg';
  import Dick11 from '$lib/images/homepage/Dick11.png';
  import Kayla from '$lib/images/homepage/Kayla.png';
  import SitDown from '$lib/images/homepage/SitDown.png';
  import craig from '$lib/images/homepage/t5.webp';
  import noahV from '$lib/images/homepage/t15.webp';
  import kaylaWWN from '$lib/images/homepage/t10.webp';
  import ARJ from '$lib/images/homepage/t0.webp';
  import noahM from '$lib/images/homepage/t1.webp';
  import david from '$lib/images/homepage/t6.webp';
  import sasha from '$lib/images/homepage/t8.webp';
  import josh from '$lib/images/homepage/t11.webp';

  import { fade } from 'svelte/transition';
  import { onDestroy, onMount } from 'svelte';

  const allScenePhotos = [
    {
      src: BenDan,
      alt: "Ben O'Connell and Dan Gantman at The Rigby",
      caption: "Ben O'Connell and Dan Gantman at The Rigby",
      order: 1, // Add fixed order
    },
    {
      src: Dick11,
      alt: 'Owen Joyner and Rory Rusch at Madisons',
      caption: 'Owen Joyner and Rory Rusch at Madisons',
      order: 2,
    },
    {
      src: Kayla,
      alt: 'Kayla Ruth at Atlas Improv',
      caption: 'Kayla Ruth at Atlas Improv',
      order: 3,
    },
    {
      src: SitDown,
      alt: 'Eli Wilz at The Rigby',
      caption: 'Eli Wilz at The Rigby',
      order: 4,
    },
    {
      src: craig,
      alt: 'Craig Smith at Crucible',
      caption: 'Craig Smith at Crucible',
      order: 5,
    },
    {
      src: noahV,
      alt: 'Noah Van Der Weide at Forward Club',
      caption: 'Noah Van Der Weide at Forward Club',
      order: 6,
    },
    {
      src: kaylaWWN,
      alt: 'Kayla Ruth at Crucible',
      caption: 'Kayla Ruth at Crucible',
      order: 7,
    },
    {
      src: ARJ,
      alt: 'ARJ at Crucible',
      caption: 'ARJ at Crucible',
      order: 8,
    },
    {
      src: noahM,
      alt: 'Noah Mailloux at Crucible',
      caption: 'Noah Mailloux at Crucible',
      order: 9,
    },
    {
      src: david,
      alt: 'David Schendlinger at Crucible',
      caption: 'David Schendlinger at Crucible',
      order: 10,
    },
    {
      src: sasha,
      alt: 'Sasha Rosser at Crucible',
      caption: 'Sasha Rosser at Crucible',
      order: 11,
    },
    {
      src: josh,
      alt: 'Josh Glen at Cardinal Bar',
      caption: 'Josh Glen at Cardinal Bar',
      order: 12,
    },
  ];

  // function getRandomPhotos() {
  //   const currentTime = Date.now();
  //   const rotationPeriod = Math.floor(currentTime / 5000) % (allScenePhotos.length - 2);

  //   return allScenePhotos.slice(rotationPeriod, rotationPeriod + 3);
  // }

  // let displayedPhotos = getRandomPhotos();

  // function shufflePhotos() {
  //   displayedPhotos = getRandomPhotos();
  // }

  // const interval = setInterval(shufflePhotos, 15000);
  // onDestroy(() => clearInterval(interval));

  let displayedPhotos = $state([]);

  //waits for browser execution to avoid hydration issues
  import { browser } from '$app/environment';
  if (browser) {
    shufflePhotos();
  }

  let interval = setInterval(shufflePhotos, 10000);

  function shufflePhotos() {
    let copy = [...allScenePhotos];
    let selected = [];
    for (let i = 0; i < 3; i++) {
      let index = Math.floor(Math.random() * copy.length);
      selected.push(copy.splice(index, 1)[0]); // Remove and store item
    }
    displayedPhotos = [...selected];
  }
</script>

<section class="hero">
  <h1 class="neon-title">Madison Laughs</h1>
  <p class="tagline">Your Guide to the Madison, WI Comedy Scene</p>
</section>

<section class="quick-links-container">
  <nav class="quick-links">
    <a href="/mics" class="quick-link">
      <span class="icon">🎤</span>
      <h3>Open Mics</h3>
    </a>
    <a href="/shows" class="quick-link">
      <span class="icon">🏟️</span>
      <h3>Shows</h3>
    </a>
    <a href="/comics" class="quick-link">
      <span class="icon">🤡</span>
      <h3>Comics</h3>
    </a>
    <a href="/extra" class="quick-link">
      <span class="icon">✳️</span>
      <h3>Extra</h3>
    </a>
  </nav>
</section>

<section class="photo-gallery">
  <div class="gallery-grid">
    {#each displayedPhotos as photo}
      <div class="photo-frame" in:fade>
        <img src={photo.src} alt={photo.alt} />
        <div class="caption">{photo.caption}</div>
      </div>
    {/each}
  </div>
</section>

<hr class="section-divider" />

<UpcomingShows />

<style>
  .neon-title {
    font-family: 'Vibur';
    color: #fff;
    font-size: 6.2rem;
    font-weight: 400;
    /* animation: pulsate 1s infinite alternate; */
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

  @keyframes pulsate {
    100% {
      text-shadow:
        0 0 4px #fff,
        0 0 11px #fff,
        0 0 19px #fff,
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

  .quick-links {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    justify-content: center;
    gap: 10px;
    width: 100%;
  }

  .quick-link {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    height: 100%;
  }

  .icon {
    font-size: 1.5em;
    margin-bottom: 5px;
  }

  .photo-gallery {
    width: 100%;
    max-width: 1400px; /* Increased from 1200px to allow for larger screens */
    margin: 0 auto;
    padding: 2rem;
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;
    overflow: hidden; /* Prevent vertical scrolling */
  }

  .section-divider {
    border: none;
    border-bottom: 1px solid rgba(255, 255, 255, 0.2);
    margin: 2rem auto;
    width: 100%;
    max-width: 1200px;
  }

  .gallery-grid {
    display: grid;
    grid-template-columns: repeat(3, minmax(0, 1fr)); /* Use minmax for better sizing */
    grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
    gap: 40px;
    margin-bottom: 3rem;
    overflow: hidden;
    position: relative;
    width: 100%; /* Ensure full width usage */
  }

  .photo-frame {
    position: relative;
    aspect-ratio: 2/3;
    border: 1px solid rgba(255, 255, 255, 0.8);
    border-radius: 8px;
    overflow: hidden;
    height: auto; /* Allow natural height */
    /* max-height: 500px; Prevent excessive height */
  }

  .photo-frame img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transform: scale(1.01); /* Prevent potential gap at edges */
  }

  .caption {
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    background: rgba(0, 0, 0, 0.7);
    color: white;
    padding: 0.5rem;
    text-align: center;
    font-size: 0.9rem;
  }

  .nav-button {
    background: rgba(0, 0, 0, 0.5);
    border: 2px solid rgba(255, 255, 255, 0.8);
    color: white;
    font-size: 1.5rem;
    padding: 1rem;
    cursor: pointer;
    border-radius: 50%;
    width: 3rem;
    height: 3rem;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: all 0.3s ease;
    z-index: 2;
  }

  .nav-button:hover {
    background: rgba(0, 0, 0, 0.8);
    transform: scale(1.1);
  }

  @media (min-width: 768px) {
    .quick-links-container {
      max-width: 1400px;
      padding: 2rem;
    }

    .quick-links {
      grid-template-columns: repeat(4, 1fr);
    }
  }

  @media (max-width: 1024px) {
    .photo-gallery {
      max-width: 100%;
      padding: 1rem;
    }

    .gallery-grid {
      gap: 1rem;
    }

    .hero {
      padding: 20px;
      margin-bottom: 20px;
    }
  }

  @media (max-width: 768px) {
    .gallery-grid {
      grid-template-columns: repeat(2, 1fr);
    }

    .nav-button {
      display: none;
    }

    .hero {
      margin-top: -10px;
    }

    /* .photo-frame {
      max-height: 450px;
    } */
  }

  @media (max-width: 480px) {
    .gallery-grid {
      grid-template-columns: 1fr;
    }

    /* .photo-frame {
      max-height: 400px;
    } */

    .hero {
      padding: 15px;
      margin-bottom: 15px;
    }
  }

  .hero {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-top: -15px;
    width: 100%;
    padding: 30px;
    margin-bottom: 30px;
    text-align: center;
  }

  .tagline {
    color: white;
  }
</style>
