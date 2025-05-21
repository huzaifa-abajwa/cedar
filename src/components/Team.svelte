<script>
  import Carousel from 'svelte-carousel';
  
  const advisoryBoard = [
    { name: "Muhammad Hamad Alizai", role: "Dept. Chair CS, Director LUMS Learning Institute", img: "hammad.jpg" },
    { name: "Jazib Zahir", role: "Director LUMS Center for Entrepreneurship", img: "jazib.jpg" },
    { name: "Ali Farid Khwaja", role: "Chairman KTrade Securities", img: "farid.jpg" },
    { name: "Murad Akhter", role: "CEO Tintash", img: "murad.jpg" },
    { name: "Amina Hassan", role: "Partner Hughes Hubbard & Reed LLP", img: "amina.jpg" },
      { name: "Fatima Tanvir Gilani", role: "PM Center for Digital Assets Research", affiliation: "Admin CeDAR", img: "fatima.jpeg" }
  ];

  const directors = [
    { name: "Dr. Zartash Afzal Uzmi", role: "Principal Investigator", affiliation: "Prof. EE & CS, LUMS", img: "zartash.jpg" },
    { name: "Dr. Basit Shafiq", role: "Co-Principal Investigator", affiliation: "Associate Prof. CS, LUMS", img: "basit.jpg" },
    { name: "Dr. Naveed ul Hassan", role: "Co-Principal Investigator", affiliation: "Associate Prof. EE, LUMS", img: "naveed.jpg" },
    { name: "Dr. Ussama Yaqub", role: "Co-Principal Investigator", affiliation: "Assistant Prof. SBASSE, LUMS", img: "usama.jpg" }
  ];

  const slides = [
    { title: 'Board of Directors', members: directors },
    { title: 'Advisory Board & Admin', members: advisoryBoard }
  ];
</script>

<div id="team" class="min-h-screen relative overflow-hidden py-12 pb-12 mt-12">
  <div class="container mx-auto px-6 md:px-20 relative z-10">
    <!-- Section Header -->
    <div class="flex flex-col items-center text-center mb-8">
      <h2 class="text-4xl md:text-5xl font-light mb-6 bg-gradient-to-r from-red-600 to-orange-600 bg-clip-text text-transparent">
        Our Team
      </h2>
      <div class="w-24 h-1 bg-gradient-to-r from-red-600 to-orange-600 rounded-full mb-4"></div>
    </div>

    <!-- Carousel Component -->
    <Carousel
      autoplay={true}
      autoplayDuration={5000}
      duration={2000}
      infinite={true}
      dots={true}
      arrows={false}
      timingFunction="cubic-bezier(0.645, 0.045, 0.355, 1)"
    >
      {#each slides as slide (slide.title)}
        <div class="px-4 py-4">
          <!-- Slide Title -->
          <div class="text-center mb-4">
            <p class="text-3xl font-medium text-white pb-4">{slide.title}</p>
          </div>
          <!-- Team Members Grid -->
          <div class={"grid grid-cols-1 md:grid-cols-2 " + (slide.members.length === 4 ? "lg:grid-cols-2" : "lg:grid-cols-3") + " gap-6 justify-center"}>
            {#each slide.members as member}
              <div class="bg-gray-800/30 backdrop-blur-sm border border-gray-700/50 rounded-lg p-4 transform hover:scale-105 transition-all duration-300 relative">
                <div class="flex flex-col items-center text-center">
                  <div class="w-32 h-32 rounded-full overflow-hidden mb-6 border-2 border-orange-600/20">
                    <img src={`/${member.img}`} alt={member.name} class="w-full h-full object-cover grayscale">
                  </div>
                  <h3 class="text-xl font-medium text-white mb-2">{member.name}</h3>
                  <p class="text-orange-600 mb-4">{member.role}</p>
                  {#if member.affiliation}
                    <p class="text-gray-400 text-sm">{member.affiliation}</p>
                  {/if}
                </div>
              </div>
            {/each}
          </div>
        </div>
      {/each}
    </Carousel>
  </div>
</div>

<style>
</style>
