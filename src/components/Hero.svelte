<div id="hero" class="min-h-screen flex items-center justify-start pl-20 pr-20 pt-16">
  <div class="flex flex-col items-start">
    <div class="flex items-center gap-8">
      <div class="flex-shrink-0">
        <img src="/cedar_logo.png" alt="Launch Event" class="w-40 md:w-48 h-auto">
      </div>
      <div>
        <h1 class="text-4xl md:text-8xl font-medium bg-gradient-to-r from-red-600 to-orange-600 bg-clip-text text-transparent">
          LUMS CeDAR <span class="hidden md:inline"><br></span>Launch Event
        </h1>
        <p class="mt-4 text-xl md:text-2xl font-light text-white">
          The Center for Digital Assets Research
        </p>
      </div>
    </div>

    <div class="mt-20 w-full">
      <div class="grid grid-cols-7 items-center gap-4">
        <div class="text-center">
          <div class="text-6xl md:text-8xl text-white font-light">{days}</div>
          <div class="text-sm text-white">Days</div>
        </div>
        <div class="text-6xl md:text-8xl text-white self-center">:</div>
        <div class="text-center">
          <div class="text-6xl md:text-8xl text-white font-light">{hours}</div>
          <div class="text-sm text-white">Hours</div>
        </div>
        <div class="text-6xl md:text-8xl text-white self-center">:</div>
        <div class="text-center">
          <div class="text-6xl md:text-8xl text-white font-light">{minutes}</div>
          <div class="text-sm text-white">Mins</div>
        </div>
        <div class="text-6xl md:text-8xl text-white self-center">:</div>
        <div class="text-center">
          <div class="text-6xl md:text-8xl text-white font-light">{seconds}</div>
          <div class="text-sm text-white">Secs</div>
        </div>
      </div>
    </div>
  </div>
</div>

<script>
  import { onMount } from 'svelte';

  let days = 0;
  let hours = 0;
  let minutes = 0;
  let seconds = 0;

  const eventDate = new Date(2025, 3, 24, 1, 0, 0);

  function updateCountdown() {
    const now = new Date();
    const diff = Number(eventDate) - Number(now);

    if (diff <= 0) {
      days = hours = minutes = seconds = 0;
      return;
    }

    days = Math.floor(diff / (1000 * 60 * 60 * 24));
    hours = Math.floor((diff % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
    minutes = Math.floor((diff % (1000 * 60 * 60)) / (1000 * 60));
    seconds = Math.floor((diff % (1000 * 60)) / 1000);
  }

  onMount(() => {
    updateCountdown();
    const interval = setInterval(updateCountdown, 1000);
    return () => clearInterval(interval);
  });
</script> 