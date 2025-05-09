<script>
  import OpenMicCard from './OpenMicCard.svelte';
  import state from '$lib/images/mics/state.webp';
  import argus from '$lib/images/mics/argus.jpg';

  const micImages = {
    state: state,
    argus: argus,
    // Add other images here as needed
  };

  const weeklyMics = {
    sunday: [],
    monday: [],
    tuesday: [
      {
        venue: 'The Argus Underground',
        description:
          'The Argus open mic has been a staple in the Madison comedy scene for over a decade.',
        host: "Ben O'Connell",
        image: argus,
        time: '8:00 PM',
        signup: '7:30PM',
      },
    ],
    wednesday: [
      {
        venue: 'The Mic on State',
        description:
          'Widely considered to be one of the best open mics in the country, The Mic on State regularly attracts crowds of over 200 people. Upwards of 60 people sign up each week in hopes of getting one of the 20 available spots.',
        image: state,
        time: '8:00 PM',
        signup: 'madisoncomedy.com',
        flip: true,
      },
    ],
    thursday: [
      {
        venue: 'The Revolver at Rigby',
        description:
          'Every week a new host picks a theme or gimmick for the comics to prepare for. The theme is posted ahead of time day-of on the Facebook group. Past themes have included "Yo mama" jokes, Roast Mic, Random Wikipedia Article, Ohio, and tons more.',
        image: argus,
        time: '8:00 PM',
        signup: '7:30PM',
      },
    ],
  };

  const daysOfWeek = ['sunday', 'monday', 'tuesday', 'wednesday', 'thursday'];
</script>

<div class="open-mics-container">
  <h1>Weekly Open Mics</h1>
  <div class="notice">
    <p>
      Stay tuned to the Madison Area Comedy Network Facebook group, Instagram, and Discord
      for the most up to date information on new mics,pop-up mics, cancellations, and time
      changes.
    </p>
    <a href="https://www.facebook.com/groups/186265104823579/" class="fb-link"
      >Join Facebook Group</a
    >
  </div>

  <section class="quick-links">
    <a href="https://www.facebook.com/groups/186265104823579/" class="quick-link">
      <h3>Join Facebook Group</h3>
      <p>test test test</p>
    </a>
    <a href="https://instagram.com/madisoncomedy" class="quick-link">
      <h3>Instagram</h3>
      <p>test test test</p>
    </a>
    <a href="/*" class="quick-link">
      <h3>Discord</h3>
      <p>test test test</p>
    </a>
  </section>

  {#each daysOfWeek as day}
    <section class="day-section">
      <h2>{day.charAt(0).toUpperCase() + day.slice(1)}</h2>
      {#if weeklyMics[day].length > 0}
        {#each weeklyMics[day] as mic}
          <OpenMicCard {...mic} />
        {/each}
      {:else}
        <p class="no-mics">No regularly scheduled mics</p>
      {/if}
    </section>
  {/each}
</div>

<style>
  .open-mics-container {
    max-width: 1000px;
    margin: 0 auto;
    padding: 2rem 0;
  }

  .quick-links {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 20px;
    margin: 40px 0;
  }

  .notice {
    background-color: rgba(255, 255, 255, 0.05);
    padding: 1.5rem;
    border-radius: 8px;
    margin-bottom: 2rem;
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
    margin-bottom: 3rem;
  }

  .no-mics {
    color: var(--text);
    opacity: 0.7;
    font-style: italic;
  }

  h1 {
    margin-bottom: 2rem;
  }

  h2 {
    margin-bottom: 1.5rem;
    color: var(--text);
  }

  @media (max-width: 768px) {
    .open-mics-container {
      padding: 1rem 0;
    }
  }
</style>
