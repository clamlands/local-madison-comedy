<script>
  let { graphic, title, date, time, place, link } = $props();
</script>

<div class="show-card">
  <a href={link} target="_blank" rel="noreferrer">
    <img
      src={graphic}
      width="1600"
      height="901"
      alt={title}
      class="show-pic"
      loading="lazy"
    />
  </a>
  <div class="card-body">
    <a href={link} target="_blank" rel="noreferrer" class="no-underline">
      <h3>{title}</h3>
    </a>

    <div class="date">
      {date} | {time}
    </div>
    <div>{place}</div>
    <a href={link} target="_blank" rel="noreferrer" class="to-eventbrite"> TICKETS </a>
  </div>
</div>

<style>
  .show-card {
    margin-bottom: 50px;
    background: rgba(0, 0, 0, 0.2);
    padding: 8px;
    border-radius: 8px;
  }

  img {
    border-radius: 8px;
  }

  h3 {
    color: var(--text);
  }

  .date {
    font-size: 15px;
  }

  .card-body {
    display: flex;
    flex-direction: column;
    gap: 5px;
    margin-top: 6px;
  }

  .to-eventbrite {
    background-color: var(--button);
    font-weight: bold;
    color: var(--dark-text);
    margin-top: 4px;
    padding: 15px 32px;
    text-decoration: none;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 16px;
    border-radius: 8px;
    width: 33%;
  }

  @media (min-width: 768px) {
    .card-body {
      line-height: 1.2;
      flex-grow: 1;
      margin-top: 0;
    }

    .show-card {
      display: flex;
      flex-direction: column;
      gap: 6px;
      margin-bottom: 0;
    }

    .to-eventbrite {
      margin-top: auto;
      text-align: center;
      display: inline-block;
      cursor: pointer;
      transition: all 0.25s ease;
    }

    .to-eventbrite:hover {
      filter: brightness(80%);
    }

    .show-pic:hover {
      filter: brightness(80%);
      transition: all 0.25s ease;
    }
  }
</style>
