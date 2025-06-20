<script>
  import { push } from "svelte-spa-router";

  const webinars = [
    {
      title: "'Blockchain 101,' Webinar at Stacks Hackathon",
      date: "April 8, 2021",
    },
    {
      title:
        "'Blockchain 101, Laying the Foundation' Webinar at Stacks Hackathon",
      date: "July 14, 2021",
    },
  ];

  const panels = [
    {
      title:
        'Panelist: "Web 3.0, Crypto, DeFi, Metaverse: Game Changer or Just Hype?"',
      event:
        "International Conference on Big Data and Cloud Computing (BigC), LUMS",
      date: "Dec 2022",
    },
    {
      title: "Investing in the Future of Digital Assets",
      event: "CeDAR Launch Event - LUMS",
      date: "April 24, 2025",
      description:
        "A panel of top VCs discussing global investment trends, regulation, and the finance-tech intersection.",
      link: "/launch#panel-investment",
    },
    {
      title: "Building Trust in the Digital Asset Ecosystem",
      event: "CeDAR Launch Event - LUMS",
      date: "April 24, 2025",
      description:
        "Leading infrastructure providers discuss institutional adoption, security, and compliance.",
      link: "/launch#panel-trust",
    },
  ];

  function goToPanel(link) {
    const hash = link.split("#")[1]; 
    push(link.split("#")[0]) 
      .then(() => scrollToAnchor(hash));
  }

  function scrollToAnchor(id) {
    setTimeout(() => {
      const section = document.getElementById(id);
      if (section) {
        section.scrollIntoView({ behavior: "smooth" });
      }
    }, 300); // adjust if needed
  }
</script>

<div id="webinars-panels" class="min-h-[60vh] py-16">
  <div class="container mx-auto px-6 md:px-20">
    <div class="text-center mb-12">
      <h2
        class="text-4xl md:text-5xl font-light bg-gradient-to-r from-red-600 to-orange-600 bg-clip-text text-transparent"
      >
        Webinars & Panels
      </h2>
      <div
        class="w-24 h-1 bg-gradient-to-r from-red-600 to-orange-600 rounded-full mt-4 mx-auto"
      ></div>
    </div>

    <div class="grid md:grid-cols-2 gap-8">
      <!-- Webinars Section -->
      <div
        class="bg-gray-800/30 backdrop-blur-sm border border-gray-700/50 rounded-lg p-6"
      >
        <h3 class="text-2xl text-orange-500 font-semibold mb-4">
          Webinars at Stacks Hackathon
        </h3>
        <ul class="list-disc list-inside space-y-2 text-gray-300 text-sm">
          {#each webinars as webinar}
            <li>
              <span class="text-white">{webinar.title}</span><br />
              <span class="text-gray-400 italic">{webinar.date}</span>
            </li>
          {/each}
        </ul>
      </div>

      <!-- Panels Section -->
      <!-- Panels Card -->
      <div
        class="bg-gray-800/30 backdrop-blur-sm border border-gray-700/50 rounded-lg p-6"
      >
        <h3 class="text-2xl text-orange-500 font-semibold mb-4">
          Talks & Panels
        </h3>
        <ul class="list-disc list-inside space-y-4 text-gray-300 text-sm">
          {#each panels as panel}
            <li>
              <span class="text-white">{panel.title}</span><br />
              <span class="text-gray-400 italic"
                >{panel.event} - {panel.date}</span
              >

              {#if panel.description}
                <p class="mt-1 text-gray-400">{panel.description}</p>
              {/if}

              {#if panel.link}
                <button
                  on:click={() => goToPanel(panel.link)}
                  class="mt-2 text-orange-500 hover:text-orange-400 underline text-sm"
                >
                  Watch panel →
                </button>
              {/if}
            </li>
          {/each}
        </ul>
      </div>
    </div>
  </div>
</div>
