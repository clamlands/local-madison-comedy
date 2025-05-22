<script>
  import '../app.css';
  import '../nav.css';
  import '../home.css';
  import { page } from '$app/stores';
  let { children } = $props();

  const currentPath = $derived($page.url.pathname);

  let mobileNavOpen = $state(false);

  function toggleMobileNav() {
    mobileNavOpen = !mobileNavOpen;
  }
</script>

<svelte:head>
  <meta name="description" content="Your guide to the Madison, WI comedy scene." />
  <title>Madison Laughs</title>
  <link rel="stylesheet preload" href="fonts.css" as="style" />
</svelte:head>

<header>
  <h1 class="desktop-hide">Madison Laughs</h1>
  <button
    class="burger"
    aria-label="Toggle mobile navigation"
    onclick={() => {
      toggleMobileNav();
    }}
  >
    <div class={`burger-bar ${mobileNavOpen ? 'open' : 'closed'}`}></div>
    <div class={`burger-bar ${mobileNavOpen ? 'open' : 'closed'}`}></div>
    <div class={`burger-bar ${mobileNavOpen ? 'open' : 'closed'}`}></div>
  </button>
  <nav class={`${mobileNavOpen ? 'open' : 'closed'}`}>
    <a
      href="/"
      class:active={currentPath === '/'}
      onclick={() => {
        toggleMobileNav();
      }}>Home</a
    >
    <a
      href="/mics"
      class:active={currentPath === '/mics'}
      onclick={() => {
        toggleMobileNav();
      }}>Open Mics</a
    >
    <a
      href="/shows"
      class:active={currentPath === '/shows'}
      onclick={() => {
        toggleMobileNav();
      }}>Shows</a
    >
    <a
      href="/comics"
      class:active={currentPath === '/comics'}
      onclick={() => {
        toggleMobileNav();
      }}>Comics</a
    >
    <a
      href="/joke-of-the-week"
      class:active={currentPath === '/joke-of-the-week'}
      onclick={() => {
        toggleMobileNav();
      }}>Joke of the Week</a
    >
    <a
      href="/extra"
      class:active={currentPath === '/extra'}
      onclick={() => {
        toggleMobileNav();
      }}>Extra</a
    >
  </nav>
</header>

<main>
  {@render children()}
</main>

<footer>
  <div>Website by Noah Mailloux and Eli Wilz</div>
</footer>
