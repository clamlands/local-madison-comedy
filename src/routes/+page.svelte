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
