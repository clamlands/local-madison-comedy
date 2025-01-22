<script>
  import UpcomingShows from './UpcomingShows.svelte';
  import ComicCard from './comics/ComicCard.svelte';
  import noah from '$lib/images/noah-750.webp';
  import eli from '$lib/images/EliWilz-750.webp';
  import '../home.css';

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
<div>List of all shows from eventbrite sources</div>
<UpcomingShows />
