<script>
  import '../app.css';
  import '../nav.css';
  let { children } = $props();
</script>

<header>
  <nav>
    <a href="/">Home</a>
    <a href="/mics">Open Mics</a>
    <a href="/shows">Shows</a>
    <a href="/comics">Comics</a>
    <a href="/extra">Extra</a>
  </nav>
</header>

<main>
  {@render children()}
</main>

<footer>
  <div>Website by Noah Mailloux</div>
</footer>
