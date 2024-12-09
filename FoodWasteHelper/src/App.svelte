<script>
  import MainPage from './components/MainPage.svelte';
</script>

<main>
  <MainPage />
</main>

<style>
  main {
    margin: 0;
    padding: 0;
    width: 100vw; /* Full viewport width */
    height: 100vh; /* Full viewport height */
    overflow: hidden; /* Prevent scrolling */
  }

  /* Global styles (optional) */
  body {
    margin: 0;
    font-family: 'Arial', sans-serif; /* Update with your preferred font */
  }
</style>
