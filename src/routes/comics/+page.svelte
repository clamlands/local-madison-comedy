<script>
  import { PUBLIC_GOOGLE_SHEETS_KEY } from '$env/static/public';
  import ComicCard from './ComicCard.svelte';
  import noah from '$lib/images/noah-750.webp';
  import eli from '$lib/images/EliWilz-750.webp';
  import { onMount } from 'svelte';

  const comicObjectArray = $state([]);

  async function getComics() {
    const response = await fetch(
      `https://sheets.googleapis.com/v4/spreadsheets/1Vmy362KSY7vJa9HNiAJH1rCjUpzRUjfV_ieTeDqxjUs/values/Form%20Responses%201!A:K?key=${PUBLIC_GOOGLE_SHEETS_KEY}`,
    );
    const json = await response.json();
    const rows = json.values;
    converToObjects(rows);
  }

  function converToObjects(rows) {
    let comicObj = {};
    rows.forEach((row, i) => {
      if (i === 0) {
        return;
      }
      let comicObj = {
        headshot: row[1],
        name: row[2],
        bio: row[3],
        insta: row[4],
        email: row[5],
        facebook: row[6],
        youtube: row[7],
        website: row[8],
        clip: row[9],
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
  <section>
    <!-- DO NOT DELETE: This works. It might fail if there's too many requests though -->
    <!-- <img
      src="https://drive.google.com/thumbnail?id=1Ysshpf-4OHmpPSdjHB4kJMYYKp_fHzV_&sz=w1000"
      alt=""
    /> -->

    <div class="comic-cards">
      {#each comicObjectArray as comicObject}
        <ComicCard
          img={comicObject.headshot}
          name={comicObject.name}
          bio={comicObject.bio}
          clip={comicObject.clip}
          insta={comicObject.insta}
          facebook={comicObject.facebook}
          youtube={comicObject.youtube}
          email={comicObject.email}
          website={comicObject.website}
        />
      {/each}

      <!-- <ComicCard
        img={noah}
        name="Noah Mailloux"
        insta="https://www.instagram.com/noahmailloux/"
        email="noah.mailloux1@gmail.com"
        clip="https://www.youtube.com/watch?v=FzSgMFVobT0"
        bio="Noah Mailloux is a Madison, WI based comedian who relates to crowds using his honest and conversational style, with topics ranging from substance abuse and relationships to totally absurd takes on toothbrushes or stacking chairs. He hosts The Revolver Open Mic and produces several monthly showcases with Cheshire Cat Comedy spanning stand-up, improv, and music. He was selected to perform on the Best of the Fest showcase during Madison Comedy Week in 2024. A regular performer at Comedy on State and Comedy Cabin, Noah has opened for nationally recognized headliners including Kevin Bozeman, Chastity Washington, and Julio Diaz."
      />
      <ComicCard
        img={eli}
        name="Eli Wilz"
        insta="https://www.instagram.com/eliwilz/"
        email="eli@sillystreetcomedy.com"
        clip="https://www.youtube.com/watch?v=iqOCiv-Sn1s"
        bio="Eli Wilz is a stand-up comedian from Madison, WI. He has opened for comics you have heard of in rooms you think are interesting. He has also opened for comics you haven't heard in rooms that suck. In both scenarios, everyone thinks he did a really good job."
      /> -->
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
    font-size: 6.2rem;
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
</style>
