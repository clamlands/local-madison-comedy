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
  <section>
    <h1>Comic Directory</h1>

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
</style>
