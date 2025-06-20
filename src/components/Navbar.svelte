<script>
  import { onMount } from 'svelte';
  import { location, push } from 'svelte-spa-router';

  let currentRoute;
  $: currentRoute = $location;

  const navbarHeight = 64;

  onMount(() => {
    // Smooth scroll for internal anchor links
    document.querySelectorAll('a[href^="#"]').forEach(anchor => {
      anchor.addEventListener('click', function (e) {
        e.preventDefault();
        const targetId = this.getAttribute('href');
        const targetElement = document.querySelector(targetId);

        if (targetElement) {
          const targetPosition = targetElement.getBoundingClientRect().top + window.pageYOffset - navbarHeight;
          window.scrollTo({
            top: targetPosition,
            behavior: 'smooth'
          });
        }
      });
    });
  });

  function scrollToTop() {
    window.scrollTo({ top: 0, behavior: 'auto' });
  }

  function goToLaunch() {
    push('/launch').then(scrollToTop);
  }

  function goHome() {
    push('/').then(scrollToTop);
  }
</script>


<nav class="w-full flex justify-between items-center py-4 px-10 bg-gray-800/80 backdrop-blur-sm fixed top-0 z-50">
  <div class="flex items-center">
    <img src="/lums_logo.png" alt="LUMS Logo" class="h-10 w-auto mr-2" />
    <span class="text-2xl font-bold text-white ml-1">LUMS CeDAR</span>
  </div>

  {#if currentRoute === '/launch'}
    <!-- On launch page: show only back button -->
    <button
      class="bg-orange-600 hover:bg-orange-700 text-white px-4 py-2 rounded"
      on:click={goHome}
    >
      Back to homepage
    </button>
  {:else}
    <!-- Normal navbar -->
    <ul class="flex space-x-6 items-center">
      <li><a href="#about" class="hover:text-orange-600 text-white scroll-smooth">About</a></li>
      <li><a href="#vision" class="hover:text-orange-600 text-white scroll-smooth">Vision</a></li>
      <li><a href="#courses" class="hover:text-orange-600 text-white scroll-smooth">Courses</a></li>
      <li><a href="#projects" class="hover:text-orange-600 text-white scroll-smooth">Projects</a></li>
      <li><a href="#trainings" class="hover:text-orange-600 text-white scroll-smooth">Trainings</a></li>
      <li><a href="#webinars-panels" class="hover:text-orange-600 text-white scroll-smooth">Webinars</a></li>
      <li><a href="#team" class="hover:text-orange-600 text-white scroll-smooth">Team</a></li>
      <li>
        <button
          class="bg-orange-600 hover:bg-orange-700 text-white px-4 py-2 rounded"
          on:click={goToLaunch}
        >
          Launch Event
        </button>
      </li>
    </ul>
  {/if}
</nav>
