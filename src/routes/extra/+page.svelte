<script>
  import dirtynerd from '$lib/images/extra/dirtynerd.jpg';
  import charlie from '$lib/images/extra/charlie.webp';
  import chuky from '$lib/images/extra/chuky.jpg';
  import youtube from '$lib/images/icons/youtube.png';
  import apple from '$lib/images/icons/apple.png';
  import spotify from '$lib/images/icons/spotify.png';
  import bandcamp from '$lib/images/icons/bandcamp.png';
  import atlasLogo from '$lib/images/extra/atlaslogo.png';
  import atlas from '$lib/images/extra/atlas.jpg';
  import mbi from '$lib/images/extra/mbi-background.webp';
  import mbiGroup from '$lib/images/extra/mbi-group.webp';
  import pitchpit from '$lib/images/extra/pitchpit.jpg';
</script>

<div class="width-container">
  <section>
    <h1>Extra</h1>
    <h2>Comedy Albums</h2>
    <div class="side-card">
      <img src={dirtynerd} alt="Dirty Nerd album cover" />
      <div class="content">
        <h3>Dirty Nerd - Sasha Rosser</h3>
        <p>
          Nothing is off limits in Sasha Rosser's blistering debut comedy album. Seasoning
          dark, dirty stand-up with her background as a synth producer and academic,
          Sasha's irreverent takes on everything from Pavlov's dog to Sapphic sex are
          bookended with original music made through her side project as exandroid.
        </p>
        <strong>Listen here:</strong>
        <div class="icon-links">
          <a
            href="https://sasharosser.bandcamp.com/album/dirty-nerd"
            target="_blank"
            rel="noreferrer"
          >
            <img src={bandcamp} alt="Bandcamp icon" width="64" height="64" /></a
          >
          <a
            href="https://open.spotify.com/album/1mWexCfq079qwnKMS1ZpeZ?si=ttC91kcOQeWAlngMJU_qEQ"
            target="_blank"
            rel="noreferrer"
          >
            <img src={spotify} alt="Spotify icon" width="64" height="64" /></a
          >
          <a
            href="https://music.apple.com/us/album/dirty-nerd/1750445026"
            target="_blank"
            rel="noreferrer"
          >
            <img src={apple} alt="Apple Music icon" width="64" height="64" /></a
          >
        </div>
      </div>
    </div>
    <div class="side-card flip">
      <div class="content">
        <h3>A Normal Amount of Pain - Charlie Kojis</h3>
        <p>
          From an antique store in Milwaukee, Wisconsin, comedian Charlie Kojis tells
          jokes about cast iron pans, funerals, and the origins of Irish dance.
        </p>
        <strong>Watch/listen here:</strong>
        <div class="icon-links">
          <a
            href="https://youtu.be/XwwRuMid150?si=P1tFLRJuOM_oNpuL"
            target="_blank"
            rel="noreferrer"
          >
            <img src={youtube} alt="YouTube icon" width="64" height="45" /></a
          >
          <a
            href="https://open.spotify.com/album/2m9tKGBrhlGiMIpz4z2UFH?si=1D1ykGJVTVuvQT-9hGgojQ"
            target="_blank"
            rel="noreferrer"
          >
            <img src={spotify} alt="Spotify icon" width="64" height="64" /></a
          >
          <a
            href="https://music.apple.com/us/album/a-normal-amount-of-pain/1750142983"
            target="_blank"
            rel="noreferrer"
          >
            <img src={apple} alt="Apple Music icon" /></a
          >
        </div>
      </div>
      <img src={charlie} alt="A Normal Amount of Pain album cover" />
    </div>
    <h2>Sketch</h2>
    <div>Capital Comedy Hour sketches</div>
    <div>Breanne, Owen, Will sketches</div>
    <h2>Podcasts</h2>
    <img src={pitchpit} alt="The Pitch Pit" />
    <h3>The Pitch Pit</h3>
    <img src={chuky} alt="Choppin' It up with Chuky" />
    <h3>Choppin' it up with Chuky</h3>
    <a
      href="https://www.youtube.com/@choppinitupwithchuky/videos"
      target="_blank"
      rel="noreferrer">Watch on YouTube</a
    >
    <h2>Madison Comedy Week</h2>
    <a href="https://madisoncomedyweek.com/" target="_blank" rel="noreferrer"
      >Festival link</a
    >
    <p>
      Madison Comedy Week is an comedy festival held each year in August. It features
      upwards of 20 shows spanning stand-up, improv, variety shows, and other special
      themed shows.
    </p>
    <h2>Improv</h2>
    <img src={atlasLogo} alt="Atlas Improv logo" class="no-shadow" />
    <img src={atlas} alt="Atlas Improv peforming" />
    <div>From left: Steve Horton, Steve Wyeth, Neil Baron & Claire Ramming</div>
    <a href="https://www.atlasimprov.com/" target="_blank" rel="noreferrer"
      >Atlas Improv</a
    >
    <img src={mbi} alt="Monkey Business Institute logo" class="no-shadow" />
    <img src={mbiGroup} alt="Monkey Business Institute group" />
    <a href="https://monkeybusinessinstitute.com/" target="_blank" rel="noreferrer"
      >Monkey Business Institute</a
    >
  </section>
</div>

<style>
  .side-card {
    display: flex;
    flex-direction: column;
    gap: 10px;
    margin-bottom: 100px;
  }

  .content {
    display: flex;
    flex-direction: column;
    gap: 10px;
  }

  .flip {
    flex-direction: column-reverse;
  }

  .icon-links {
    display: flex;
    gap: 40px;
  }

  .icon-links a img {
    box-shadow: none;
  }

  @media (min-width: 768px) {
    .side-card {
      display: grid;
      grid-template-columns: 1fr 1fr;
      align-items: center;
      gap: 50px;
      justify-items: start;
      margin-bottom: 150px;
    }

    .icon-links a:hover {
      transform: scale(1.07);
    }

    .icon-links a {
      transition: all 0.25s ease;
    }
  }
</style>
