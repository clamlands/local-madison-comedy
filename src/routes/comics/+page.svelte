  <script>
  import { PUBLIC_GOOGLE_SHEETS_KEY } from '$env/static/public';
  import ComicCard from './ComicCard.svelte';
  import SubmitCard from './SubmitCard.svelte';
  import { onMount } from 'svelte';

  const comicObjectArray = $state([]);

  async function getComics() {
    const response = await fetch(
      `https://sheets.googleapis.com/v4/spreadsheets/1Vmy362KSY7vJa9HNiAJH1rCjUpzRUjfV_ieTeDqxjUs/values/Form%20Responses%201!A:K?key=${PUBLIC_GOOGLE_SHEETS_KEY}`,
    );
    const json = await response.json();
    const rows = json.values;
    converToObjects(rows);
    //sort alphabetically by name
    comicObjectArray.sort((a, b) => a.name.localeCompare(b.name));
  }

  function converToObjects(rows) {
    let comicObj = {};
    rows.forEach((row, i) => {
      if (i === 0) {
        return;
      }
      
      // Helper function to ensure URLs have proper protocol
      const formatUrl = (url) => {
        if (!url) return url;
        url = url.trim();
        if (!url.startsWith('http://') && !url.startsWith('https://')) {
          return `https://${url}`;
        }
        return url;
      };

      let comicObj = {
        headshot: row[1],
        name: row[2],
        bio: row[3],
        insta: formatUrl(row[4]),
        email: row[5],
        facebook: formatUrl(row[6]),
        youtube: formatUrl(row[7]),
        website: formatUrl(row[8]),
        clip: formatUrl(row[9]),
        tiktok: formatUrl(row[10]),
      };
      comicObjectArray.push(comicObj);
    });
  }

  onMount(getComics);
</script>

<div class="width-container">
  <section class="hero">
    <h1 class="neon-title">Comic Directory</h1>
    <p>
      Saw a Madison-area comedian and liked what you saw? Below is a list of all the
      stand-up comics in the scene.
    </p>
  </section>
  <section class="comic-section">
    <div class="comic-cards">
      {#each comicObjectArray as comicObject}
        <ComicCard
          img={comicObject.headshot}
          name={comicObject.name}
          bio={comicObject.bio}
          clip={comicObject.clip}
          insta={comicObject.insta}
          tiktok={comicObject.tiktok}
          facebook={comicObject.facebook}
          youtube={comicObject.youtube}
          email={comicObject.email}
          website={comicObject.website}
        />
      {/each}
    </div>
  </section>
</div>

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

  .comic-section {
    width: 100%;
    max-width: 1400px;
    margin: 0 auto;
    padding: 0 20px;
  }

  .comic-cards {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    gap: 30px;
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
  @media (min-width: 768px) {
    .neon-title {
      font-size: 6.2rem;
    }
  }
</style>
