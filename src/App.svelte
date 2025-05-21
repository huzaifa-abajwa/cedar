<div class="min-h-screen bg-gradient-to-b from-gray-900 to-gray-700">
  <Navbar />
  <Hero />
  <EventDetails />
  <Vision />
  <Team />
  <Projects />
  <Footer />
</div>

<script>
  import Navbar from './components/Navbar.svelte';
  import Hero from './components/Hero.svelte';
  import EventDetails from './components/EventDetails.svelte';
  import Vision from './components/Vision.svelte';
  import Team from './components/Team.svelte';
  import Projects from './components/Projects.svelte';
  import Footer from './components/Footer.svelte';
</script>

<style>
  :global(html) {
    scroll-behavior: smooth;
    scroll-padding-top: 4rem;
  }
</style>
