<script>
  import { PUBLIC_CCC_API_KEY } from '$env/static/public';
  import ShowCard from './ShowCard.svelte';
  import { onMount } from 'svelte';

  let curatedEventsArray = $state([]);

  async function getEvents() {
    const response = await fetch(
      `https://www.eventbriteapi.com/v3/organizations/863190459903/events/?status=live&expand=venue&token=${PUBLIC_CCC_API_KEY}`,
    );
    const json = await response.json();
    const events = json.events;
    console.log(events);
    curateEventsArray(events);
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

<h1>Upcoming Shows</h1>
{#if curatedEventsArray.length === 0}
  <h2>Loading upcoming shows</h2>
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

<style>
  @media (min-width: 768px) {
    .show-cards {
      width: 100%;
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
      grid-auto-rows: max-content;
      column-gap: 30px;
      row-gap: 75px;
    }
  }
</style>
