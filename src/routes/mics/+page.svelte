<script>
  import state from '$lib/images/mics/state.webp';
  import argus from '$lib/images/mics/argus.jpg';
  import rooster from '$lib/images/mics/rooster.jpg';
</script>

<div class="open-mics-container">
  <section class="hero">
    <h1 class="neon-title">Weekly Open Mics</h1>
    <div class="notice">
      <p>
        Stay tuned to the Madison Area Comedy Network Facebook group for the most up to
        date information on new mics, pop-up mics, cancellations, and time changes.
      </p>
      <a href="https://www.facebook.com/groups/186265104823579/" class="fb-link"
        >Join Facebook Group</a
      >
    </div>
  </section>

  <section class="quick-links">
    <a href="https://www.facebook.com/groups/186265104823579/" class="quick-link">
      <h3>Join Facebook Group</h3>
    </a>
    <a href="https://instagram.com/madisoncomedy" class="quick-link">
      <h3>Instagram</h3>
    </a>
  </section>

  <hr />

  <section></section>
  <section class="day-section">
    <h2>Monday</h2>
    <div class="mic-card">
      <img src={rooster} alt={`Monday Night Raw open mic`} />
      <div class="mic-content">
        <h3>Monday Night Raw</h3>
        <div class="mic-details">
          <p>Location: Red Rooster</p>
          <p>Show time: 7:30 PM</p>
          <p>Sign-up: 7:00 PM</p>
          <p>Hosted by Sammy Dice Jr.</p>
        </div>
        <p>
          Madison's newest open mic featuring the antics of comedian/faux-magician Sammy
          Dice Jr.
        </p>
      </div>
    </div>
  </section>

  <hr />

  <section class="day-section">
    <h2>Tuesday</h2>
    <div class="mic-card flip">
      <div class="mic-content">
        <h3>The Argus Underground</h3>
        <div class="mic-details">
          <p>Location: Argus BarGrille</p>
          <p>Show time: 8:00 PM</p>
          <p>Sign-up: 7:30 PM</p>
          <p>Hosted by Ben O'Connell</p>
        </div>
        <p>
          The Argus open mic has been a staple in the Madison comedy scene for over a
          decade.
        </p>
      </div>
      <img src={argus} alt={`Argus open mic`} />
    </div>
  </section>

  <hr />

  <section class="day-section">
    <h2>Wednesday</h2>
    <div class="mic-card">
      <img src={state} alt={`The Mic on State`} />
      <div class="mic-content">
        <h3>The Mic on State</h3>
        <div class="mic-details">
          <p>Location: Comedy on State</p>
          <p>Show time: 9:00 PM</p>
          <p>
            Sign-up online at <a
              href="https://www.madisoncomedy.com/open-mic/"
              target="_blank"
              rel="noreferrer">madisoncomedy.com</a
            >
            from noon to 7 PM on Wednesdays.
          </p>
        </div>
        <p>
          Widely considered to be one of the best open mics in the country, The Mic on
          State regularly attracts crowds of over 200 people. Upwards of 60 people sign up
          each week in hopes of getting one of the 20 available spots.
        </p>
      </div>
    </div>
  </section>

  <hr />

  <section class="day-section">
    <h2>Thursday</h2>
    <div class="mic-card flip">
      <div class="mic-content">
        <h3>The Revolver at Rigby</h3>
        <div class="mic-details">
          <p>Location: The Rigby Pub</p>
          <p>Show time: 8:00 PM</p>
          <p>Sign-up: 7:30 PM</p>
        </div>
        <p>
          Every week a new host picks a theme or gimmick for the comics to prepare for.
          The theme is posted ahead of time day-of on the Facebook group. Past themes have
          included "Yo mama" jokes, Roast Mic, Random Wikipedia Article, Ohio, and tons
          more.
        </p>
      </div>
      <img src={argus} alt={`The Revolver open mic`} />
    </div>
  </section>
  <hr />
  <p class="no-mics">
    There are no regularly scheduled mics on Friday, Saturday, or Sunday. Go catch a
    weekend show instead!
  </p>
</div>

<style>
  .hero {
    display: flex;
    flex-direction: column;
    max-width: 1000px;
    align-items: center;
    margin-top: -15px;
    width: 100%;
    padding-top: 30px;
    margin-bottom: 30px;
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
    font-size: 4.8rem;
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
    z-index: 0;
  }

  img {
    z-index: 1;
  }

  h2 {
    font-family: 'Vibur';
    color: #fff;
    font-size: 80px;
    font-weight: 400;
    animation: pulsate 1s infinite alternate;
    margin-bottom: 75px;
    text-align: center;
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

  a {
    color: inherit;
  }

  .open-mics-container {
    max-width: 1000px;
  }

  .quick-links {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 20px;
    margin: 40px 0;
  }

  .quick-links h3 {
    font-style: normal;
  }

  .notice {
    background-color: rgba(255, 255, 255, 0.05);
    padding: 1.5rem;
    border-radius: 8px;
  }

  .fb-link {
    display: inline-block;
    margin-top: 1rem;
    color: #1877f2;
    text-decoration: none;
  }

  .fb-link:hover {
    text-decoration: underline;
  }

  .day-section {
    margin-bottom: 100px;
  }

  .no-mics {
    color: var(--text);
    opacity: 0.7;
    font-style: italic;
    padding: 0 15px;
    margin-bottom: 50px;
  }

  h1 {
    margin-bottom: 2rem;
  }

  h3 {
    font-style: italic;
  }

  .mic-card {
    display: flex;
    flex-direction: column;
    gap: 20px;
    align-items: start;
  }

  .mic-card.flip {
    flex-direction: column-reverse;
  }

  .mic-content {
    flex: 1;
    display: flex;
    flex-direction: column;
    gap: 15px;
  }

  @media (min-width: 768px) {
    .mic-card {
      width: 100%;
      display: grid;
      grid-template-columns: 1fr 1fr;
      grid-auto-rows: max-content;
      gap: 30px;
    }

    .mic-card,
    .mic-card.flip {
      flex-direction: column;
    }

    .mic-card > img {
      width: 100%;
      height: auto;
    }

    .neon-title {
      font-size: 6.2rem;
    }
  }
</style>
