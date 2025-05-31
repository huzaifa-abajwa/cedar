<script>
  import Router from 'svelte-spa-router';
  import routes from './routes.js';
</script>

<style>
  :global(html, body) {
    scroll-behavior: smooth;
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
</style>

<Router {routes}/>

