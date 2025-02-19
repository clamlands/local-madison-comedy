<!--
extra
-->
<script>
  import ExtraCard from './ExtraCard.svelte';
  import dirtynerd from '$lib/images/extra/dirtynerd.jpg';
  import charlie from '$lib/images/extra/charlie.webp';
  import chuky from '$lib/images/extra/chuky.jpg';
  import youtube from '$lib/images/icons/youtube.png';
  import apple from '$lib/images/icons/apple.png';
  import applePod from '$lib/images/icons/applepod.png';
  import insta from '$lib/images/icons/ig.png';
  import spotify from '$lib/images/icons/spotify.png';
  import bandcamp from '$lib/images/icons/bandcamp.png';
  import atlasLogo from '$lib/images/extra/atlaslogo-white.png';
  import atlas from '$lib/images/extra/atlas.jpg';
  import atlasIcon from '$lib/images/icons/atlas-icon.png';
  import web from '$lib/images/icons/www.webp';
  import mbi from '$lib/images/extra/mbi-background.webp';
  import mbiLogo from '$lib/images/icons/mbi.png';
  import mbiGroup from '$lib/images/extra/mbi-group.webp';
  import pitchpit from '$lib/images/extra/pitchpit.jpg';
  import cch from '$lib/images/extra/cch.png';
  import mcw from '$lib/images/extra/mcw.jpg';

  const sections = [
    {
      id: 'albums',
      title: 'Comedy Albums',
      icon: '💽',
    },
    {
      id: 'podcasts',
      title: 'Podcasts',
      icon: '🎙️',
    },
    {
      id: 'sketch',
      title: 'Sketch Comedy',
      icon: '🎭',
    },
    {
      id: 'improv',
      title: 'Improv',
      icon: '🌎',
    },
    {
      id: 'comedy-week',
      title: 'Comedy Week',
      icon: '🎪',
    },
  ];
</script>

<section class="hero">
  <h1 class="neon-title">Extra Content</h1>
  <p>
    Discover additional content from Madison's comedy scene—including comedy albums,
    podcasts, sketches, improv performances, and more.
  </p>

  <nav class="quick-links">
    {#each sections as { id, title, icon }}
      <a href="#{id}" class="quick-link">
        <span class="icon">{icon}</span>
        <h3>{title}</h3>
      </a>
    {/each}
  </nav>
</section>

<hr class="section-divider" />

<div class="width-container">
  {#each sections as { id, title }, i}
    <section {id}>
      {#if i !== 0}
        <hr class="section-divider" />
      {/if}
      <h2>{title}</h2>
      {#if id === 'albums'}
        <ExtraCard
          img={dirtynerd}
          title="Dirty Nerd - Sasha Rosser"
          description="Nothing is off limits in Sasha Rosser's blistering debut comedy album. Seasoning dark, dirty stand-up with her background as a synth producer and academic, Sasha's irreverent takes on everything from Pavlov's dog to Sapphic sex are bookended with original music made through her side project as exandroid."
          links={[
            {
              icon: bandcamp,
              url: 'https://sasharosser.bandcamp.com/album/dirty-nerd',
              alt: 'Bandcamp',
            },
            {
              icon: spotify,
              url: 'https://open.spotify.com/album/1mWexCfq079qwnKMS1ZpeZ',
              alt: 'Spotify',
            },
            {
              icon: apple,
              url: 'https://music.apple.com/us/album/dirty-nerd/1750445026',
              alt: 'Apple Music',
            },
          ]}
        />

        <ExtraCard
          img={charlie}
          title="A Normal Amount of Pain - Charlie Kojis"
          description="From an antique store in Milwaukee, Wisconsin, comedian Charlie Kojis tells jokes about cast iron pans, funerals, and the origins of Irish dance."
          links={[
            { icon: youtube, url: 'https://youtu.be/XwwRuMid150', alt: 'YouTube' },
            {
              icon: spotify,
              url: 'https://open.spotify.com/album/2m9tKGBrhlGiMIpz4z2UFH',
              alt: 'Spotify',
            },
            {
              icon: apple,
              url: 'https://music.apple.com/us/album/a-normal-amount-of-pain/1750142983',
              alt: 'Apple Music',
            },
          ]}
          flip={true}
        />
      {/if}

      {#if id === 'podcasts'}
        <ExtraCard
          img={pitchpit}
          title="The Pitch Pit Podcast"
          description="Hosts Craig Smith, Amos Atkinson, and Alec White are joined by guests to pitch ideas for jokes, sketches, movies, music, products, etc. They also take pitches from our followers (Pitchers) who can submit pitches to possibly bounce their ideas off working comedians."
          links={[
            {
              icon: spotify,
              url: 'https://open.spotify.com/show/06iLXtz4pY0cnwgpc7ZdFP',
              alt: 'Spotify',
            },
            {
              icon: applePod,
              url: 'https://podcasts.apple.com/us/podcast/the-pitch-pit/id1677869963',
              alt: 'Apple Podcasts',
            },
            {
              icon: insta,
              url: 'https://www.instagram.com/pitchpitpodcast/',
              alt: 'Instagram',
            },
          ]}
        />

        <ExtraCard
          img={chuky}
          title="Choppin' it up with Chuky"
          description="A homegrown podcast hosted by Chuky Razo. Follow him throughout his journey as he showcases his natural comedic abilities, along with amazing interviews consisting of some of Madison's very own!"
          links={[
            {
              icon: youtube,
              url: 'https://www.youtube.com/@choppinitupwithchuky/videos',
              alt: 'YouTube',
            },
            {
              icon: insta,
              url: 'https://www.instagram.com/choppinitupwithchuky/',
              alt: 'Instagram',
            },
          ]}
          flip={true}
        />
      {/if}

      {#if id === 'sketch'}
        <ExtraCard
          img={cch}
          imgAlt="Capitol Comedy Hour Logo"
          title="Capitol Comedy Hour"
          description="The sketches you’ve seen at Capitol Comedy Hour—now available on your computer. Capitol Comedy Hour is a comedy variety show inspired by late-night TV. These sketches were performed live at the show and are now posted here for you to enjoy."
          links={[
          
          {
              icon: cch,
              url: 'https://www.capitolcomedyhour.com/',
              alt: 'Website',
            },
            {
              icon: youtube,
              url: 'https://www.youtube.com/@CapitolComedyHour',
              alt: 'YouTube',
            },
            {
              icon: insta,
              url: 'https://www.instagram.com/amnrynning/',
              alt: 'Instagram',
            },
          ]}
        />
      {/if}

      {#if id === 'improv'}
        <ExtraCard
          img={atlas}
          imgAlt="Atlas Improv performing"
          title={`Atlas Improv Co.`}
          description={`Atlas Improv has been a cornerstone of Madison's comedy scene for over 20 years, offering high-energy shows every Friday and Saturday at 7 PM (family-friendly) and 9 PM.`}
          description2={`They provide a range of classes for all skill levels and host The Cut, an intense competition where aspiring improvisers vie for a spot among the esteemed Atlas performers. Whether you're looking to laugh, learn, or compete, Atlas Improv has something for everyone.`}
          links={[
            {
              icon: atlasIcon,
              url: 'https://atlasimprov.com/',
              alt: 'Atlas Improv website',
            },
            {
              icon: insta,
              url: 'https://www.instagram.com/atlasimprov/',
              alt: 'Instagram',
            },
          ]}
        />

        <ExtraCard
          img={mbiGroup}
          imgAlt="Monkey Business Institute group"
          title="Monkey Business Institute"
          description={`Monkey Business Institute features over 35 talented performers with decades of experience in improv, acting, music, and film.`}
          description2={`Many members honed their craft with Madison’s ComedySportz before 2002 and have been performing together for over a decade. With a mix of seasoned pros and fresh talent, their shows guarantee smart, hilarious entertainment—served with pizza`}
          links={[
            {
              icon: mbiLogo,
              url: 'https://monkeybusinessinstitute.com/',
              alt: 'MBI website',
            },
            {
              icon: insta,
              url: 'https://www.instagram.com/monkeybusinessinstitute',
              alt: 'Instagram',
            },
          ]}
          flip={true}
        />
      {/if}

      {#if id === 'comedy-week'}
        <ExtraCard
          img={mcw}
          imgAlt="Madison Comedy Week Logo"
          title={`Madison Comedy Week`}
          description={`Our festival centers around the infrastructure that makes up the Madison comedy scene - a scene that stacks up to scenes in cities many times its size.`}

          description2={`Our festival is held for 7 days in the summer, and features over 25 standup, improv, music and themed variety shows. This festival is a breeding ground for hilarious ideas. We are genuinely committed to making this experience ideal for all participants, performers and audience members, and we put our comics first.`}

          description3={`Madison Comedy Week is an event that is diverse, accessible, and inclusive—showcasing the unique nature of comedy in Madison, Wisconsin and the various reasons why comedians from all over the country love to perform here.`}


          links={[
            {
              icon: mcw,
              url: 'https://madisoncomedyweek.com/',
              alt: 'Madison Comedy Week website',
            },
            {
              icon: insta,
              url: 'https://www.instagram.com/madisoncomedyweek/',
              alt: 'Instagram',
            },
          ]}
        />
      {/if}
    </section>
  {/each}
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
    margin-bottom: 0;
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
    margin: 3rem 0 2rem;
    width: 100%;
  }

  .quick-links {
    display: grid;
    grid-template-columns: repeat(5, 1fr);
    gap: 10px;
    margin: 40px 0 0;
    width: 100%;
  }

  section {
    margin-bottom: 0;
  }

  h2 {
    font-family: 'Vibur';
    color: #fff;
    font-size: 80px;
    font-weight: 400;
    animation: pulsate 1s infinite alternate;
    margin: 50px 0 2rem;
    text-align: center;
  }

  .neon-title {
    font-family: 'Vibur';
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

  .icon {
    font-size: 1.5em;
    margin-bottom: 5px;
  }

  :global(.quick-link h3) {
    font-size: 0.9em;
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

  @keyframes pulsate {
    100% {
      text-shadow:
        0 0 3px #fff,
        0 0 5px #fff,
        0 0 7px #fff,
        0 0 40px var(--neon2),
        0 0 80px var(--neon2),
        0 0 90px var(--neon2),
        0 0 100px var(--neon2),
        0 0 150px var(--neon2);
    }

    0% {
      text-shadow:
        0 0 2px #fff,
        0 0 4px #fff,
        0 0 6px #fff,
        0 0 10px var(--neon2),
        0 0 45px var(--neon2),
        0 0 55px var(--neon2),
        0 0 70px var(--neon2),
        0 0 80px var(--neon2);
    }
  }
</style>
