<script>
  import { onMount } from 'svelte';
  import * as XLSX from 'xlsx';

  let projects = [];
  let loading = true;

  onMount(async () => {
    try {
      const res = await fetch('/project_descriptions.xlsx');
      const data = await res.arrayBuffer();
      const workbook = XLSX.read(data, { type: 'array' });
      const sheet = workbook.Sheets[workbook.SheetNames[0]];
      const json = XLSX.utils.sheet_to_json(sheet);
      projects = json;
    } catch (err) {
      console.error('Error loading projects:', err);
    } finally {
      loading = false;
    }
  });
</script>

<div id="projects" class="min-h-screen py-16">
  <div class="container mx-auto px-6 md:px-20">
    <div class="text-center mb-12">
      <h2 class="text-4xl md:text-5xl font-light bg-gradient-to-r from-red-600 to-orange-600 bg-clip-text text-transparent">
        Projects
      </h2>
      <div class="w-24 h-1 bg-gradient-to-r from-red-600 to-orange-600 rounded-full mt-4 mx-auto"></div>
    </div>

    {#if loading}
      <p class="text-center text-gray-400 text-lg">Loading projects...</p>
    {:else if projects.length === 0}
      <p class="text-center text-gray-400 text-lg">No projects available.</p>
    {:else}
      <div class="grid gap-8 md:grid-cols-2">
        {#each projects as project}
          <div class="bg-gray-800/30 backdrop-blur-sm border border-gray-700/50 rounded-lg p-6 shadow-md hover:shadow-lg transition-shadow duration-300">
            <h3 class="text-2xl text-orange-500 font-semibold mb-2">{project.Title}</h3>
            <p class="text-gray-300 mb-4 text-sm">{project.Description}</p>

            <div class="text-sm text-gray-400 space-y-1">
              {#if project.Authors}<p><strong class="text-white">Authors:</strong> {project.Authors}</p>{/if}
              {#if project.Year}<p><strong class="text-white">Year:</strong> {project.Year}</p>{/if}
              {#if project.Venue}<p><strong class="text-white">Venue:</strong> {project.Venue}</p>{/if}
              {#if project.Type}<p><strong class="text-white">Type:</strong> {project.Type}</p>{/if}
              {#if project["Funding Body"]}<p><strong class="text-white">Funding:</strong> {project["Funding Body"]}</p>{/if}
              {#if project.Amount}<p><strong class="text-white">Amount:</strong> {project.Amount}</p>{/if}
              {#if project.Students}<p><strong class="text-white">Students:</strong> {project.Students}</p>{/if}
              {#if project.Advisors}<p><strong class="text-white">Advisors:</strong> {project.Advisors}</p>{/if}
              {#if project.Link}
                <p>
                  <a href={project.Link} target="_blank" rel="noopener noreferrer" class="text-orange-500 hover:underline">
                    View Publication
                  </a>
                </p>
              {/if}
            </div>
          </div>
        {/each}
      </div>
    {/if}
  </div>
</div>
