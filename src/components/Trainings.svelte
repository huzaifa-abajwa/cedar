<script>
  import { onMount } from 'svelte';
  import * as XLSX from 'xlsx';

  let trainings = [];
  let loading = true;

  onMount(async () => {
    try {
      const res = await fetch('/trainings_descriptions.xlsx');
      const data = await res.arrayBuffer();
      console.log(data)
      const workbook = XLSX.read(data, { type: 'array' });
      console.log(workbook)
      const sheet = workbook.Sheets[workbook.SheetNames[0]];
      console.log(sheet)
      trainings = XLSX.utils.sheet_to_json(sheet);
      console.log(trainings)
    } catch (err) {
      console.error('Failed to load training data:', err);
    } finally {
      loading = false;
    }
  });
</script>

<div id="trainings" class="min-h-screen py-16">
  <div class="container mx-auto px-6 md:px-20">
    <!-- Section Heading -->
    <div class="text-center mb-12">
      <h2 class="text-4xl md:text-5xl font-light bg-gradient-to-r from-red-600 to-orange-600 bg-clip-text text-transparent">
        Training & Outreach
      </h2>
      <div class="w-24 h-1 bg-gradient-to-r from-red-600 to-orange-600 rounded-full mt-4 mx-auto"></div>
    </div>

    {#if loading}
      <p class="text-center text-gray-400">Loading training sessions...</p>
    {:else if trainings.length === 0}
      <p class="text-center text-gray-400">No training data found.</p>
    {:else}
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
        {#each trainings as training}
          <div class="bg-gray-800/30 backdrop-blur-sm border border-gray-700/50 rounded-lg p-6 transform hover:scale-105 transition-all duration-300">
            <h3 class="text-xl font-semibold text-white mb-2">{training.Session}</h3>
            <p class="text-orange-600">Presenter: {training.Presenter}</p>
          </div>
        {/each}
      </div>
    {/if}
  </div>
</div>
