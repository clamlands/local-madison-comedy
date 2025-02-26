<script>
  import state from '$lib/images/mics/state.webp';
  import argus from '$lib/images/mics/argus.jpg';
  import rooster from '$lib/images/mics/rooster.jpg';
  import OpenMicCard from './OpenMicCard.svelte';
</script>

<div class="open-mics-container">
  <section class="hero">
    <h1 class="neon-title">Weekly Open Mics</h1>
    <div class="notice">
      <p>
        Stay tuned to the Madison Area Comedy Network Facebook group for the most up to
        date information on new mics, pop-up mics, cancellations, and time changes.
      </p>
    </div>
  </section>

  <section class="quick-reference">
    <table>
      <thead>
        <tr>
          <th>Day</th>
          <th>Venue</th>
          <th>Time</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>Monday</td>
          <td>Red Rooster</td>
          <td>7:30 PM</td>
        </tr>
        <tr>
          <td>Tuesday</td>
          <td>Argus BarGrille</td>
          <td>8:00 PM</td>
        </tr>
        <tr>
          <td>Wednesday</td>
          <td>Comedy onState</td>
          <td>9:00 PM</td>
        </tr>
        <tr>
          <td>Thursday</td>
          <td>The Rigby</td>
          <td>8:00 PM</td>
        </tr>
      </tbody>
    </table>
  </section>

  <section class="quick-links">
    <a href="https://www.facebook.com/groups/186265104823579/" class="quick-link">
      <h3>Join Facebook Group</h3>
    </a>
    <a href="https://instagram.com/madisoncomedy" class="quick-link">
      <h3>Instagram</h3>
    </a>
    <a href="https://instagram.com/madisoncomedy" class="quick-link">
      <h3>Discord</h3>
    </a>
  </section>

  <hr />
  <section class="day-section">
    <h2>Monday</h2>
    <OpenMicCard
      venue="Monday Night Raw"
      time="Show time: 7:30 PM"
      signup="7:00 PM"
      host="Sammy Dice Jr."
      description="Madison's newest open mic featuring the antics of comedian/faux-magician Sammy Dice Jr."
      image={rooster}
    />
  </section>

  <hr />

  <section class="day-section">
    <h2>Tuesday</h2>
    <OpenMicCard
      venue="The Argus Underground"
      time="Show time: 8:00 PM"
      signup="7:30 PM"
      host="Ben O'Connell"
      description="The Argus open mic has been a staple in the Madison comedy scene for over a decade."
      image={argus}
    />
  </section>

  <hr />

  <section class="day-section">
    <h2>Wednesday</h2>
    <OpenMicCard
      venue="The Mic on State"
      time="Show time: 9:00 PM"
      signup="Sign-up online at <a href='https://www.madisoncomedy.com/open-mic/' target='_blank' rel='noreferrer'>madisoncomedy.com</a> from noon to 7 PM on Wednesdays."
      host=""
      description="Widely considered to be one of the best open mics in the country, The Mic on State regularly attracts crowds of over 200 people. Upwards of 60 people sign up each week in hopes of getting one of the 20 available spots."
      image={state}
    />
  </section>

  <hr />

  <section class="day-section">
    <h2>Thursday</h2>
    <OpenMicCard
      venue="The Revolver at Rigby"
      time="Show time: 8:00 PM"
      signup="7:30 PM"
      host=""
      description="Every week a new host picks a theme or gimmick for the comics to prepare for. The theme is posted ahead of time day-of on the Facebook group. Past themes have included 'Yo mama' jokes, Roast Mic, Random Wikipedia Article, Ohio, and tons more."
      image={argus}
    />
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
    margin-bottom: 20px;
  }

  .quick-reference {
    width: 100%;
    max-width: 600px;
    margin: 40px auto;
  }

  table {
    width: 100%;
    border-collapse: collapse;
    background: rgba(0, 0, 0, 0.3);
    border-radius: 8px;
    overflow: hidden;
  }

  th,
  td {
    padding: 12px 16px;
    text-align: left;
    border-bottom: 1px solid var(--border);
  }

  th {
    background: rgba(0, 0, 0, 0.2);
    font-weight: bold;
    color: var(--text);
  }

  td {
    color: var(--text);
  }

  tr:last-child td {
    border-bottom: none;
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
    padding: 25px 40px;
    margin-bottom: 30px;
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

  .notice {
    background-color: rgba(255, 255, 255, 0.05);
    padding: 1.2rem;
    border-radius: 8px;
  }

  .open-mics-container {
    max-width: 1000px;
  }

  .quick-links {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 20px;
    margin: 30px 0;
  }

  .quick-links h3 {
    font-style: normal;
  }

  .day-section {
    margin-bottom: 50px;
  }

  .no-mics {
    color: var(--text);
    opacity: 0.7;
    font-style: italic;
    padding: 0 15px;
    margin-bottom: 30px;
  }

  h2 {
    font-family: 'Vibur';
    color: #fff;
    font-size: 80px;
    font-weight: 400;
    animation: pulsate 1s infinite alternate;
    margin-bottom: 35px;
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

  @media (min-width: 768px) {
    .neon-title {
      font-size: 6.2rem;
    }
  }
</style>
