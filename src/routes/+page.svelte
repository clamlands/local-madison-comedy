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

<div class="hero">
  <h1>Local Madison Comedy</h1>
  <p class="tagline">Your guide to Madison's comedy scene</p>
</div>
<UpcomingShows />

<style>
  /* Hero Section */
  .hero {
    text-align: center;
    padding: 2rem 0;
    margin-bottom: 2rem;
  }

  .hero .tagline {
    font-size: 1.2rem;
    color: var(--text);
    margin-top: -1rem;
  }

  /* Quick Links Section */
  .quick-links {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 1rem;
    margin-bottom: 3rem;
  }

  /* Featured Section */
  .featured {
    margin-bottom: 3rem;
  }

  /* About Scene Section */
  .about-scene {
    max-width: 800px;
    margin: 0 auto;
  }

  .venue-highlights {
    margin-top: 2rem;
  }

  .venue-highlights ul {
    list-style: none;
    padding: 0;
  }

  .venue-highlights li {
    margin: 1rem 0;
    line-height: 1.5;
  }

  /* Mobile Responsiveness */
  @media (max-width: 768px) {
    .quick-links {
      grid-template-columns: 1fr;
    }

    .hero {
      padding: 1rem 0;
    }
  }
</style>
