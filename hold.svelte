hold.svelte
<script>
  import { PUBLIC_EVENTBRITE_PRIVATE_TOKEN } from '$env/static/public';
  import ShowCard from './ShowCard.svelte';
  import { onMount } from 'svelte';

  let curatedEventsArray = $state([]);
  let isLoading = $state(true);
  let error = $state(null);

  // Define organization configurations
  const organizationConfigs = [
    {
      id: '863190459903',  // Cheshire Cat Comedy
      venueMap: {
        'Crucible': 'Crucible Madison',
        'the Cardinal Bar': 'The Cardinal Bar',
        "Madison's": "Madison's Restaurant & Bar",
        'Forward Madison FC': 'The Forward Club'
      }
    },
    // Add more organizations here with their IDs and venue mappings
    // Example:
    // {
    //   id: 'OTHER_ORG_ID',
    //   venueMap: {
    //     'VenueName': 'Mapped Venue Name'
    //   }
    // }
  ];

  async function getEventsForOrganization(orgConfig) {
    try {
      const response = await fetch(
        `https://www.eventbriteapi.com/v3/organizations/${orgConfig.id}/events/?status=live&expand=venue&token=${PUBLIC_EVENTBRITE_PRIVATE_TOKEN}`
      );
      
      if (!response.ok) {
        throw new Error(`HTTP error! status: ${response.status}`);
      }
      
      const json = await response.json();
      return json.events;
    } catch (err) {
      console.error(`Error fetching events for organization ${orgConfig.id}:`, err);
      return [];
    }
  }

  async function getAllEvents() {
    isLoading = true;
    error = null;
    
    try {
      const allEventsPromises = organizationConfigs.map(config => 
        getEventsForOrganization(config)
      );
      
      const eventsArrays = await Promise.all(allEventsPromises);
      const allEvents = eventsArrays.flat();
      
      // Sort all events by date
      allEvents.sort((a, b) => new Date(a.start.local) - new Date(b.start.local));
      
      curateEventsArray(allEvents);
    } catch (err) {
      error = 'Failed to load events. Please try again later.';
      console.error('Error fetching events:', err);
    } finally {
      isLoading = false;
    }
  }

  onMount(getAllEvents);

  function curateEventsArray(eventsArray) {
    curatedEventsArray = [];
    
    eventsArray.forEach((item) => {
      const date = convertDate(item.start.local);
      
      // Find the organization config that matches this event
      const orgConfig = organizationConfigs.find(config => 
        item.organization_id === config.id
      );
      
      // Apply venue name mapping if available
      let venueName = item.venue?.name || 'TBA';
      if (orgConfig?.venueMap[venueName]) {
        venueName = orgConfig.venueMap[venueName];
      }

      // Handle image safely
      const showImg = item.logo?.original?.url || null;

      curatedEventsArray.push({
        graphic: showImg,
        title: item.name.text.toUpperCase().replace('CHESHIRE CAT COMEDY PRESENTS: ', ''),
        date: date[0],
        time: date[1],
        place: venueName,
        link: item.url,
        organizationId: item.organization_id
      });
    });
  }

  function convertDate(date) {
    const newDate = new Date(date);
    const monthNames = [
      'January', 'February', 'March', 'April', 'May', 'June',
      'July', 'August', 'September', 'October', 'November', 'December'
    ];

    let showTime = newDate.toLocaleString('en-US', {
      hour: 'numeric',
      minute: 'numeric',
      hour12: true
    });

    // Convert to lowercase and remove spaces from time
    showTime = showTime.replace(/\s/g, '').toLowerCase();

    const day = newDate.getDate();
    const month = monthNames[newDate.getMonth()];
    const year = newDate.getFullYear();

    return [`${month} ${day}, ${year}`, showTime];
  }
</script>

<section>
  <h2 class="upcoming">Upcoming Shows</h2>
  <p class="other-shows">
    Here are upcoming shows from various comedy organizations in Madison.
    Check out shows run by entities such as 1Motion Out Reach Enterprise,
    Don't Tell: Madison, and <a href="/shows">more</a>.
  </p>

  {#if isLoading}
    <h2>Loading upcoming shows...</h2>
  {:else if error}
    <p class="error">{error}</p>
  {:else if curatedEventsArray.length === 0}
    <p>No upcoming shows found.</p>
  {:else}
    <div class="show-cards">
      {#each curatedEventsArray as event}
        <ShowCard
          graphic={event.graphic}
          title={event.title}
          date={event.date}
          time={event.time}
          place={event.place}
          link={event.link}
        />
      {/each}
    </div>
  {/if}
</section>

<style>
  a {
    color: inherit;
  }

  .error {
    color: #ff5555;
    text-align: center;
    margin: 20px 0;
  }

  .other-shows {
    margin-bottom: 40px;
    text-align: center;
  }

  .upcoming {
    font-family: 'Vibur';
    color: #fff;
    font-size: 80px;
    font-weight: 400;
    animation: pulsate 1s infinite alternate;
    margin: 50px 0 60px;
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
    .show-cards {
      width: 100%;
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
      grid-auto-rows: max-content;
      column-gap: 30px;
      row-gap: 75px;
    }

    .other-shows {
      margin-left: 300px;
      margin-right: 300px;
    }
  }
</style>