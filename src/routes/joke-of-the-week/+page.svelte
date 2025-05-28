<script>
  import { onMount } from 'svelte';

  // Weekly theme - to be updated manually each week
  let weeklyTheme = 'Jokes a person would write in their own Eulogy / Obituary';

  // Google Form link - update this URL when creating a new form
  let googleFormLink =
    'https://docs.google.com/forms/d/1lUMNGxp2fIZzNINMb6lqEl8z-OTwSIyWrTp5_c4Vl58/'; // Replace with your actual Google Form URL

  // Instagram hashtag to display
  let instagramHashtag = 'madisonlaughs';
</script>

<svelte:head>
  <title>Joke of the Week | Madison Laughs</title>
  <meta
    name="description"
    content="Submit your jokes for the weekly theme and vote for your favorites!"
  />
</svelte:head>

<div class="width-container" data-element="main-container">
  <section class="joke-of-week-container" data-element="joke-week-section">
    <h1 class="neon-title" data-element="main-heading">Joke of the Week</h1>

    <!-- Weekly Theme Section -->
    <div class="theme-container" data-element="theme-container">
      <div class="theme-content" data-element="theme-content">
        <h2 data-element="theme-heading">This Week's Theme:</h2>
        <div class="neon-box" data-element="theme-box">
          <p class="theme-text" data-element="theme-text">{weeklyTheme}</p>
        </div>
        <p class="theme-description" data-element="theme-description">
          Submit a joke in the above theme and have your jokes featured on the
          @madisoncomedy Instagram
        </p>

        <div class="theme-example" data-element="theme-example">
          <p data-element="example-intro">
            This is the joke of the week section for Madison Comedy. Each week, we select
            a theme, think late night style, punchy stuff. So like if the theme above was
            "Top Ten Reasons a Dog Should Be Mayor of Madison" you could write "Because
            traffic on the Isthmus is Ruff"
          </p>
        </div>
      </div>
    </div>

    <!-- Submission Form Section -->
    <div class="form-container" data-element="form-container">
      <h2 data-element="form-heading">Submit Your Joke</h2>
      <p data-element="form-description">
        Use the form below to submit jokes under this week's theme.
      </p>

      <div class="rules-container" data-element="rules-container">
        <h3 data-element="rules-heading">Rules:</h3>
        <ol data-element="rules-list">
          <li data-element="rule-1">
            Submit as many jokes as you'd like below. One joke per form submission.
          </li>
          <li data-element="rule-2">
            Include your instagram handle if you'd like to be tagged when featured
          </li>
          <li data-element="rule-3">
            Anyone can submit, you do not have be a Madison comedian to participate
          </li>
          <li data-element="rule-4">
            Join us at the Argus Open Mic Tuesday Nights to hear the best jokes performed
            live!
          </li>
        </ol>
      </div>

      <div class="google-form-placeholder" data-element="form-placeholder">
        <p data-element="form-placeholder-text">
          Click the button below to open the submission form
        </p>
        <a
          href={googleFormLink}
          class="form-button"
          data-element="submit-button"
          target="_blank"
          rel="noopener noreferrer">Submit Your Joke</a
        >
      </div>
    </div>

    <!-- Instagram Section -->
    <div class="instagram-section" data-element="instagram-section">
      <h2 data-element="instagram-heading">Check Out Previous Jokes</h2>
      <p data-element="instagram-description">
        Follow us on Instagram to see past winners and submissions with #{instagramHashtag}
      </p>
      <a
        href="https://www.instagram.com/madisoncomedy"
        class="instagram-link"
        data-element="instagram-link"
        target="_blank"
        rel="noopener noreferrer"
      >
        <div class="instagram-icon" data-element="instagram-icon">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 448 512"
            width="40"
            height="40"
          >
            <path
              fill="currentColor"
              d="M224.1 141c-63.6 0-114.9 51.3-114.9 114.9s51.3 114.9 114.9 114.9S339 319.5 339 255.9 287.7 141 224.1 141zm0 189.6c-41.1 0-74.7-33.5-74.7-74.7s33.5-74.7 74.7-74.7 74.7 33.5 74.7 74.7-33.6 74.7-74.7 74.7zm146.4-194.3c0 14.9-12 26.8-26.8 26.8-14.9 0-26.8-12-26.8-26.8s12-26.8 26.8-26.8 26.8 12 26.8 26.8zm76.1 27.2c-1.7-35.9-9.9-67.7-36.2-93.9-26.2-26.2-58-34.4-93.9-36.2-37-2.1-147.9-2.1-184.9 0-35.8 1.7-67.6 9.9-93.9 36.1s-34.4 58-36.2 93.9c-2.1 37-2.1 147.9 0 184.9 1.7 35.9 9.9 67.7 36.2 93.9s58 34.4 93.9 36.2c37 2.1 147.9 2.1 184.9 0 35.9-1.7 67.7-9.9 93.9-36.2 26.2-26.2 34.4-58 36.2-93.9 2.1-37 2.1-147.8 0-184.8zM398.8 388c-7.8 19.6-22.9 34.7-42.6 42.6-29.5 11.7-99.5 9-132.1 9s-102.7 2.6-132.1-9c-19.6-7.8-34.7-22.9-42.6-42.6-11.7-29.5-9-99.5-9-132.1s-2.6-102.7 9-132.1c7.8-19.6 22.9-34.7 42.6-42.6 29.5-11.7 99.5-9 132.1-9s102.7-2.6 132.1 9c19.6 7.8 34.7 22.9 42.6 42.6 11.7 29.5 9 99.5 9 132.1s2.7 102.7-9 132.1z"
            ></path>
          </svg>
        </div>
        <span>@madisoncomedy</span>
      </a>
    </div>
  </section>
</div>

<style>
  .joke-of-week-container {
    width: 100%;
    max-width: 1000px;
    margin: 0 auto;
    padding: 20px;
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
    /* animation: pulsate-title 1s infinite alternate; */
    border: 0.2rem solid #fff;
    border-radius: 2rem;
    padding: 25px 40px;
    margin-bottom: 30px;
    text-shadow:
      0 0 2px #fff,
      0 0 4px #fff,
      0 0 6px #fff,
      0 0 10px var(--neon),
      0 0 45px var(--neon),
      0 0 55px var(--neon),
      0 0 70px var(--neon),
      0 0 80px var(--neon);
    box-shadow:
      0 0 0.2rem #fff,
      0 0 0.2rem #fff,
      0 0 2rem var(--neon),
      0 0 0.8rem var(--neon),
      0 0 2.8rem var(--neon),
      inset 0 0 1.3rem var(--neon);
    z-index: 0;
  }

  @media (max-width: 768px) {
    .neon-title {
      font-size: 50px;
      padding: 15px 25px;
    }
  }

  /* Theme Section Styling */
  .theme-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    background-color: rgba(0, 0, 0, 0.6);
    border-radius: 10px;
    padding: 30px;
    margin-bottom: 50px;
    position: relative;
    overflow: hidden;
  }

  .theme-content {
    text-align: center;
    width: 100%;
  }

  .neon-box {
    border: 2px solid var(--neon2);
    border-radius: 8px;
    padding: 15px 30px;
    margin: 20px 0;
    box-shadow:
      0 0 10px var(--neon2),
      inset 0 0 10px var(--neon2);
    background-color: rgba(0, 0, 0, 0.7);
  }

  .theme-text {
    font-size: 2rem;
    font-weight: bold;
    color: white;
    text-shadow:
      0 0 5px #fff,
      0 0 10px var(--neon2),
      0 0 15px var(--neon2);
  }

  .theme-description {
    font-size: 1.1rem;
    margin-top: 15px;
  }

  .theme-example {
    background-color: rgba(20, 20, 20, 0.7);
    border-radius: 8px;
    padding: 15px;
    margin-top: 20px;
    border-left: 3px solid var(--neon2);
  }

  .theme-example p {
    font-size: 1rem;
    line-height: 1.5;
    margin: 0;
  }

  .rules-container {
    background-color: rgba(20, 20, 20, 0.7);
    border-radius: 8px;
    padding: 15px;
    margin: 20px 0;
    border-left: 3px solid var(--neon2);
  }

  .rules-container h3 {
    margin-top: 0;
    margin-bottom: 10px;
    color: white;
  }

  .rules-container ol {
    margin: 0 auto;
    padding: 0 0 0 30px;
    width: 80%;
    counter-reset: rule-counter;
  }

  .rules-container li {
    margin-bottom: 8px;
    line-height: 1.4;
    text-align: left;
    position: relative;
    padding-left: 5px;
  }

  .rules-container ol li::marker {
    color: var(--neon2);
    font-weight: bold;
  }

  .rules-container li:last-child {
    margin-bottom: 0;
  }

  /* Form Section Styling */
  .form-container {
    background-color: rgba(50, 50, 50, 0.7);
    border-radius: 10px;
    padding: 30px;
    margin-bottom: 50px;
    text-align: center;
  }

  .google-form-placeholder {
    background-color: rgba(30, 30, 30, 0.7);
    border-radius: 8px;
    padding: 40px;
    margin-top: 20px;
    min-height: 300px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }

  .form-button {
    display: inline-block;
    background-color: var(--neon);
    color: white;
    padding: 12px 24px;
    border-radius: 5px;
    text-decoration: none;
    margin-top: 20px;
    font-weight: bold;
    transition: all 0.3s ease;
    border: none;
    cursor: pointer;
    font-size: 1rem;
    text-align: center;
  }

  .form-button:hover {
    background-color: var(--neon2);
    transform: translateY(-2px);
    box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
    color: white;
    text-decoration: none;
  }

  /* Instagram Section Styling */
  .instagram-section {
    background-color: rgba(50, 50, 50, 0.7);
    border-radius: 10px;
    padding: 30px;
    margin-bottom: 50px;
    text-align: center;
  }

  .instagram-link {
    display: flex;
    align-items: center;
    justify-content: center;
    text-decoration: none;
    color: white;
    margin-top: 20px;
    padding: 15px 30px;
    background: linear-gradient(
      45deg,
      #405de6,
      #5851db,
      #833ab4,
      #c13584,
      #e1306c,
      #fd1d1d,
      #f56040,
      #f77737,
      #fcaf45,
      #ffdc80
    );
    border-radius: 8px;
    transition: all 0.3s ease;
  }

  .instagram-link:hover {
    transform: translateY(-3px);
    box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
  }

  .instagram-icon {
    margin-right: 10px;
  }

  /* Voting Section Styling */
  .voting-section {
    background-color: rgba(50, 50, 50, 0.7);
    border-radius: 10px;
    padding: 30px;
    margin-bottom: 50px;
  }

  .jokes-container {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    gap: 20px;
    margin-top: 30px;
  }

  .joke-card {
    background-color: rgba(30, 30, 30, 0.9);
    border-radius: 8px;
    padding: 20px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
    transition: transform 0.3s ease;
  }

  .joke-card:hover {
    transform: translateY(-5px);
  }

  .joke-text {
    font-size: 1.1rem;
    line-height: 1.5;
    margin-bottom: 15px;
  }

  .joke-author {
    font-style: italic;
    text-align: right;
    margin-bottom: 15px;
  }

  .joke-votes {
    display: flex;
    justify-content: flex-end;
  }

  .vote-button {
    display: flex;
    align-items: center;
    background-color: rgba(0, 0, 0, 0.2);
    border: 1px solid var(--neon);
    color: white;
    padding: 8px 16px;
    border-radius: 5px;
    cursor: pointer;
    transition: all 0.2s ease;
  }

  .vote-button:hover {
    background-color: var(--neon);
  }

  .vote-button svg {
    margin-right: 5px;
  }

  /* Responsive Styling */
  @media (min-width: 768px) {
    .theme-container {
      flex-direction: row;
      align-items: flex-start;
    }

    .theme-content {
      text-align: left;
    }
  }

  @media (max-width: 767px) {
    .jokes-container {
      grid-template-columns: 1fr;
    }

    .neon-text {
      font-size: 2.5rem;
    }

    .theme-text {
      font-size: 1.5rem;
    }
  }
</style>
