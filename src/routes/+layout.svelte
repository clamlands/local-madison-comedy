<script>
  import '../app.css';
  import '../nav.css';
  import '../home.css';
  import { page } from '$app/stores';
  let { children } = $props();

  const currentPath = $derived($page.url.pathname);
</script>

<header>
  <nav>
    <a href="/" class:active={currentPath === '/'}>Home</a>
    <a href="/mics" class:active={currentPath === '/mics'}>Open Mics</a>
    <a href="/shows" class:active={currentPath === '/shows'}>Shows</a>
    <a href="/comics" class:active={currentPath === '/comics'}>Comics</a>
    <a href="/extra" class:active={currentPath === '/extra'}>Extra</a>
  </nav>
</header>

<main>
  {@render children()}
</main>

<footer>
  <div>Website by Noah Mailloux and Eli Wilz</div>
</footer>
