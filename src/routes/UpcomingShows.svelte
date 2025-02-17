<script>
  import { PUBLIC_CCC_API_KEY } from '$env/static/public';
  import { PUBLIC_SILLY_STREET_API_KEY } from '$env/static/public';
  import ShowCard from './ShowCard.svelte';
  import { onMount } from 'svelte';

  let curatedEventsArray = $state([]);

  // async function getEvents() {
  //   const response = await fetch(
  //     // `https://www.eventbriteapi.com/v3/organizations/{ORGANIZATION_ID}/events/?status=live&expand=venue&token=${PUBLIC_CCC_API_KEY}`,
  //     // `https://www.eventbriteapi.com/v3/organizations/863190459903/events/?status=live&expand=venue&token=${PUBLIC_CCC_API_KEY}`,
  //     `https://www.eventbriteapi.com/v3/organizations/2359569882963/events/?status=live&expand=venue&token=${PUBLIC_SILLY_STREET_API_KEY}`,
  //   );
  //   const json = await response.json();
  //   const events = json.events;
  //   curateEventsArray(events);
  // }

  const eventbriteURLs = [
    `https://www.eventbriteapi.com/v3/organizations/863190459903/events/?status=live&expand=venue&token=${PUBLIC_CCC_API_KEY}`,
    `https://www.eventbriteapi.com/v3/organizations/2359569882963/events/?status=live&expand=venue&token=${PUBLIC_SILLY_STREET_API_KEY}`,
  ];

  async function getEvents() {
    const responses = await Promise.all(eventbriteURLs.map((url) => fetch(url)));
    const dataPromises = await responses.map((response) => {
      if (!response.ok) {
        throw new Error('Network response was not ok');
      }
      return response.json();
    });
    const data = await Promise.all(dataPromises);
    const eventsArray = [];
    data.forEach((dataPoint) => {
      eventsArray.push(...dataPoint.events);
    });
    //sort events by date
    eventsArray.sort((a, b) => new Date(a.start.utc) - new Date(b.start.utc));
    curateEventsArray(eventsArray);
  }

  onMount(getEvents);

  function curateEventsArray(eventsArray) {
    eventsArray.forEach((item) => {
      const date = convertDate(item.start.local);
      if (item.venue.name === 'Crucible') {
        item.venue.name = 'Crucible Madison';
      }
      if (item.venue.name === 'the Cardinal Bar') {
        item.venue.name = 'The Cardinal Bar';
      }
      if (item.venue.name === `Madison's`) {
        item.venue.name = `Madison's Restaurant & Bar`;
      }
      if (item.venue.name === `Forward Madison FC`) {
        item.venue.name = `The Forward Club`;
      }
      //makes sure the image exists before trying to grab it. Otherwise homepage goes to black screen
      let showImg;
      if (item.logo === null) {
        showImg = null;
      } else {
        showImg = item.logo.original.url;
      }
      curatedEventsArray.push({
        graphic: showImg,
        title: item.name.text.toUpperCase().replace('CHESHIRE CAT COMEDY PRESENTS: ', ''),
        date: date[0],
        time: date[1],
        place: item.venue.name,
        link: item.url,
      });
    });
  }

  function convertDate(date) {
    const newDate = new Date(date);
    const monthNames = [
      'January',
      'February',
      'March',
      'April',
      'May',
      'June',
      'July',
      'August',
      'September',
      'October',
      'November',
      'December',
    ];
    let showTime = newDate.toLocaleString('en-US', {
      hour: 'numeric',
      minute: 'numeric',
      hour12: true,
    });

    //convert date to milliseconds to subtract 30 minutes for door time
    //currently not used, but keeping it in case
    let milliseconds = Date.parse(newDate);
    let doorTime = new Date(milliseconds - 1800000);
    doorTime = doorTime.toLocaleString('en-US', {
      hour: 'numeric',
      minute: 'numeric',
      hour12: true,
    });

    //remove the space between "PM" and the time and make it lowercase
    doorTime = doorTime.replace(/\s/g, '');
    doorTime = doorTime.toLowerCase();
    showTime = showTime.replace(/\s/g, '');
    showTime = showTime.toLowerCase();

    const day = newDate.getDate();
    const month = monthNames[newDate.getMonth()];
    const year = newDate.getFullYear();

    return [`${month} ${day}, ${year}`, `${showTime}`];
  }
</script>

<section>
  <h2 class="upcoming">Upcoming Shows</h2>
  <p class="other-shows">
    Here are SOME of the upcoming shows for which tickets can be bought on Eventbrite.
    Also check out shows run by entities such as 1Motion Out Reach Enterprise, Don't Tell:
    Madison, and
    <a href="/shows">more</a>.
  </p>
  {#if curatedEventsArray.length === 0}
    <h2>Loading upcoming shows...</h2>
  {/if}

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
</section>

<style>
  a {
    color: inherit;
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
