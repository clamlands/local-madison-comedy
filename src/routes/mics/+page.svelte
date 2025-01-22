<script>
  import OpenMicCard from './OpenMicCard.svelte';
  import state from '$lib/images/mics/state.webp';
  import './mics.css';

  const micImages = {
  state: state,
  // Add other images here as needed
};

const weeklyMics = {
    sunday: [],
    monday: [],
    tuesday: [
      {
        venue: "The Argus Underground",
        description: "The Argus open mic has been a staple in the Madison comedy scene for over a decade.",
        host: "Ben O'Connell",
        time: "8:00 PM",
        signup: "7:30PM"
      }
    ],
    wednesday: [
      {
        venue: "The Mic on State",
        description: "Widely considered to be one of the best open mics in the country, The Mic on State regularly attracts crowds of over 200 people. Upwards of 60 people sign up each week in hopes of getting one of the 20 available spots.",
        image: state,
        time: "9:00 PM",
        signup: "madisoncomedy.com"
      }
    ],
    thursday: [
      {
        venue: "The Revolver at Rigby",
        description: "Every week a new host picks a theme or gimmick for the night that the comics prepare for. The theme is posted ahead of time day-of on the Facebook group. Past themes have included \"Yo mama\" jokes, Roast Mic, Random Wikipedia Article, Ohio, and tons more.",
        time: "8:00 PM",
        signup: "7:30PM"
      }
    ]
};

  const daysOfWeek = ['sunday', 'monday', 'tuesday', 'wednesday', 'thursday'];
</script>

<div class="open-mics-container">
  <h1>Weekly Open Mics</h1>
   <div class="notice">
    <p>
      Stay tuned to the Madison Area Comedy Network Facebook group, Instagram, and Discord for the most up to date information on new mics,pop-up mics, cancellations, and time changes.
    </p>
    <a href="https://www.facebook.com/groups/186265104823579/" class="fb-link">Join Facebook Group</a>
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