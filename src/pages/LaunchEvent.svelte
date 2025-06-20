<script>
  import Navbar from "../components/Navbar.svelte";
  import Footer from "../components/Footer.svelte";
  import { onMount } from "svelte";

  let images = [];
  let loading = true;
  let selectedImage = null;

  const totalImages = 20;

  onMount(() => {
    images = Array.from(
      { length: totalImages },
      (_, i) => `/launch/img${i + 1}.jpg`
    );
    loading = false;
  });

  function openModal(img) {
    selectedImage = img;
  }

  function closeModal() {
    selectedImage = null;
  }
</script>

<div
  class="min-h-screen bg-gradient-to-b from-gray-900 to-gray-700 text-white flex flex-col pt-20"
>
  <Navbar />

  <!-- Launch Event Section -->
  <section class="p-8 max-w-5xl mx-auto flex-grow">
    <div class="container mx-auto px-6 md:px-20">
      <div class="text-center mb-12">
        <h2
          class="text-4xl md:text-5xl font-light bg-gradient-to-r from-red-600 to-orange-600 bg-clip-text text-transparent"
        >
          Launch Event Highlights
        </h2>
        <div
          class="w-24 h-1 bg-gradient-to-r from-red-600 to-orange-600 rounded-full mt-4 mx-auto"
        ></div>
      </div>

      <!-- Embedded YouTube Video -->
      <div
        class="mb-12 aspect-video w-full rounded-lg overflow-hidden shadow-lg border border-gray-700"
      >
        <iframe
          src="https://www.youtube.com/embed/emhkpYFuWGk"
          title="Launch Event Video"
          frameborder="0"
          allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
          allowfullscreen
          class="w-full h-full"
        ></iframe>
      </div>

      <!-- Gallery Section -->
      <div class="container mx-auto px-6 md:px-20">
        <div class="text-center mb-12">
          <h2
            class="text-4xl md:text-5xl font-light bg-gradient-to-r from-red-600 to-orange-600 bg-clip-text text-transparent"
          >
            Gallery
          </h2>
          <div
            class="w-24 h-1 bg-gradient-to-r from-red-600 to-orange-600 rounded-full mt-4 mx-auto"
          ></div>
        </div>

        {#if loading}
          <p class="text-gray-400 text-center">Loading images...</p>
        {:else if images.length === 0}
          <p class="text-gray-400 text-center">No images found.</p>
        {:else}
          <div
            class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-5 gap-4"
          >
            {#each images as img}
              <div
                class="rounded-lg overflow-hidden border border-gray-700 shadow hover:shadow-lg transition duration-300 transform hover:scale-105 cursor-pointer"
                on:click={() => openModal(img)}
              >
                <img
                  src={img}
                  alt="Gallery image"
                  class="w-full h-32 object-cover"
                  loading="lazy"
                />
              </div>
            {/each}
          </div>
        {/if}

        <!-- Modal Overlay -->
        {#if selectedImage}
          <div class="modal" on:click={closeModal}>
            <img
              src={selectedImage}
              alt="Enlarged image"
              class="max-w-full max-h-full rounded-lg shadow-lg"
            />
          </div>
        {/if}
      </div>
    </div>
  </section>

  <section class="p-8 max-w-5xl mx-auto text-white">
    <div class="container mx-auto px-6 md:px-20">
      <div class="text-center mb-12">
        <h2
          class="text-4xl md:text-5xl font-light bg-gradient-to-r from-red-600 to-orange-600 bg-clip-text text-transparent"
        >
          Press Release
        </h2>
        <div
          class="w-24 h-1 bg-gradient-to-r from-red-600 to-orange-600 rounded-full mt-4 mx-auto"
        ></div>
      </div>

      <div
        class="bg-gray-800/40 border border-gray-700 backdrop-blur-md p-8 rounded-lg shadow-md space-y-6 text-gray-300 leading-relaxed"
      >
        <p>
          <strong class="text-white"
            >Center for Digital Asset Research (CeDAR) launched at LUMS</strong
          >
        </p>

        <p>
          <em>Lahore, Pakistan — [April 25, 2025]</em> — The Center for Digital Assets
          Research (CeDAR) at LUMS was officially launched on April 24, 2025, marking
          a transformative step for Pakistan's blockchain and digital assets ecosystem.
          CeDAR is supported by a generous grant from the Stacks Foundation and aims
          to be a center of excellence in research, training, development and innovation
          in the areas of decentralized internet, web3.0 and digital asset technologies.
        </p>

        <p>
          Stacks is a web3.0 platform which enables smart contracts on Bitcoin,
          the largest digital asset globally. It was co-founded by a
          distinguished LUMS alumnus, <strong class="text-white"
            >Dr. Muneeb Ali</strong
          > (BSc Computer Science, Class of 2003) who is recognized as one of the
          global pioneers in such technologies.
        </p>

        <p>
          Pakistan is one of the top ten countries which has the highest
          adoption of digital assets but lacked a regulatory framework. The
          Government of Pakistan has recently announced an intention to regulate
          the technology to support the ecosystem and has set up a Pakistan
          Crypto Council. This has further increased the importance for CeDAR,
          as an institution which can provide a place for policy research and
          training, incubation and testing of technologies, and collaboration
          and partnership, for technology students, entrepreneurs, industry and
          the government.
        </p>

        <p>
          As a launch event, CeDAR hosted an international conference to enable
          connection, knowledge transfer and collaboration between global
          experts in web3.0 ecosystem and the regulatory and government
          organizations in Pakistan. The management and CEOs of leading global
          companies such as <strong class="text-white">Zodia Markets</strong>
          (UK/UAE), <strong class="text-white">Haruko</strong> (UK/Singapore),
          <strong class="text-white">Scope Markets</strong>
          (UK), <strong class="text-white">Klickl</strong> (UAE),
          <strong class="text-white">Dragonstone Capital</strong>
          (China), <strong class="text-white">Binance</strong>,
          <strong class="text-white">Fasset</strong>
          (UAE) attended the event, along with local fintech and VC firms like
          <strong class="text-white">Abhi Bank</strong>,
          <strong class="text-white">KTrade</strong>,
          <strong class="text-white">TPL</strong>,
          <strong class="text-white">Brillianz Group</strong>,
          <strong class="text-white">Alfalah Investments</strong>,
          <strong class="text-white">Zayn VC</strong>, and
          <strong class="text-white">Nayapay</strong>.
        </p>

        <p>
          The conference facilitated roundtable conversations with leaders from
          key domestic stakeholders such as the <strong class="text-white"
            >State Bank of Pakistan (SBP)</strong
          >,
          <strong class="text-white"
            >Securities and Exchange Commission of Pakistan (SECP)</strong
          >, and <strong class="text-white">Pakistan Banking Council</strong>.
        </p>

        <p>
          Key topics included compliance and regulation, utilizing excess
          national energy for mining, investment allocation involving digital
          assets, and workforce development for emerging technologies.
        </p>

        <blockquote
          class="italic border-l-4 border-orange-500 pl-4 text-gray-400"
        >
          “LUMS has always been a hub of cutting-edge research and innovations
          and I am proud to have a long association with the Syed Babar Ali
          School of Science and Engineering... This new collaboration on crypto
          not just strengthens my association with LUMS but can prepare the next
          generation of engineers and entrepreneurs to architect the next
          generation of the internet by leveraging blockchain technology.” — <strong
            class="text-white">Dr. Muneeb Ali</strong
          >
        </blockquote>

        <p>
          With CeDAR now operational, LUMS is positioned as a leading hub for
          blockchain education and research, offering immense opportunities for
          innovation and development in Pakistan's tech sector.
        </p>
      </div>
    </div>
  </section>

  <section id="panel-investment" class="p-8 max-w-5xl mx-auto">
    <!-- Panel 1: Investing in the Future of Digital Assets -->
    <div class="mb-16">
      <div class="text-center mb-8">
        <h3
          class="text-3xl md:text-4xl font-light bg-gradient-to-r from-red-600 to-orange-600 bg-clip-text text-transparent"
        >
          Investing in the Future of Digital Assets
        </h3>
        <div
          class="w-24 h-1 bg-gradient-to-r from-red-600 to-orange-600 rounded-full mt-4 mx-auto"
        ></div>
      </div>
      <div
        class="aspect-video w-full rounded-lg overflow-hidden shadow-lg border border-gray-700 mb-6"
      >
        <iframe
          src="https://www.youtube.com/embed/ei1uEC4TKz4"
          title="Investing in the Future of Digital Assets | CeDAR Panel"
          frameborder="0"
          allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
          allowfullscreen
          class="w-full h-full"
        ></iframe>
      </div>
      <p
        class="text-gray-300 leading-relaxed text-justify bg-gray-800/40 border border-gray-700 backdrop-blur-md p-6 rounded-lg shadow"
      >
        Join CeDAR at LUMS for a compelling panel with
        <strong class="text-white">Dr. Najam Kidwai</strong> (C1 Fund),
        <strong class="text-white">Mohammad Yesilhark</strong> (NOIA Capital),
        and
        <strong class="text-white">Faisal Aftab</strong> (Zayn VC), moderated by
        <strong class="text-white">Ali Farid Khwaja</strong> (Stacks Foundation /
        KTrade). Explore global investment trends, regulatory dynamics, and the intersection
        of technology and finance shaping the digital assets landscape.
      </p>
    </div>
  </section>

  <section id="panel-trust" class="p-8 max-w-5xl mx-auto">
    <!-- Video Panel 2 -->
    <div class="mb-12">
      <div class="text-center mb-8">
        <h3
          class="text-3xl md:text-4xl font-light bg-gradient-to-r from-red-600 to-orange-600 bg-clip-text text-transparent"
        >
          Building Trust in the Digital Asset Ecosystem
        </h3>
        <div
          class="w-24 h-1 bg-gradient-to-r from-red-600 to-orange-600 rounded-full mt-4 mx-auto"
        ></div>
      </div>
      <div
        class="aspect-video w-full rounded-lg overflow-hidden shadow-lg border border-gray-700 mb-6"
      >
        <iframe
          src="https://www.youtube.com/embed/to11WTGmAJs"
          title="Building Trust in the Digital Asset Ecosystem | CeDAR Panel"
          frameborder="0"
          allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
          allowfullscreen
          class="w-full h-full"
        ></iframe>
      </div>
      <p
        class="text-gray-300 leading-relaxed text-justify bg-gray-800/40 border border-gray-700 backdrop-blur-md p-6 rounded-lg shadow"
      >
        Delve into the future of crypto infrastructure, institutional adoption,
        and compliance frameworks in this powerful panel. Featuring
        <strong class="text-white">Sardar Ahmed Durrani</strong> (Genesis
        Digital),
        <strong class="text-white">Daniel Ahmed</strong> (Fasset),
        <strong class="text-white">Daniel Holmes</strong> (Haruko), and
        <strong class="text-white">Ayad Butt</strong> (Zodia Markets), this session
        explores how infrastructure providers are forging secure, scalable paths
        for digital assets globally.
      </p>
    </div>
  </section>

  <section class="p-8 max-w-5xl mx-auto">
    <div class="text-center mb-12">
      <h2
        class="text-4xl md:text-5xl font-light bg-gradient-to-r from-red-600 to-orange-600 bg-clip-text text-transparent"
      >
        Dr. Muneeb Ali's Keynote
      </h2>
      <div
        class="w-24 h-1 bg-gradient-to-r from-red-600 to-orange-600 rounded-full mt-4 mx-auto"
      ></div>
    </div>

    <!-- Embedded YouTube Video -->
    <div
      class="mb-12 aspect-video w-full rounded-lg overflow-hidden shadow-lg border border-gray-700"
    >
      <iframe
        src="https://www.youtube.com/embed/kw8h9K4g2dc"
        title="Dr. Muneeb Ali's Keynote"
        frameborder="0"
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
        allowfullscreen
        class="w-full h-full"
      ></iframe>
    </div>
  </section>

  <!-- About Dr. Muneeb Ali Section -->
  <section class="p-8 max-w-5xl mx-auto text-white">
    <div class="container mx-auto px-6 md:px-20">
      <div class="text-center mb-12">
        <h2
          class="text-4xl md:text-5xl font-light bg-gradient-to-r from-red-600 to-orange-600 bg-clip-text text-transparent"
        >
          About Dr. Muneeb Ali
        </h2>
        <div
          class="w-24 h-1 bg-gradient-to-r from-red-600 to-orange-600 rounded-full mt-4 mx-auto"
        ></div>
      </div>

      <div class="flex flex-col lg:flex-row gap-8">
        <!-- Image -->
        <div class="w-full lg:w-1/2 relative">
          <div
            class="absolute -top-6 -left-6 w-full h-full border-2 border-red-600/40 rounded-lg"
          ></div>
          <img
            src="/muneeb_ali.svg"
            alt="Dr. Muneeb Ali"
            class="w-full h-full object-cover relative z-10 rounded-lg shadow-2xl"
          />
        </div>

        <!-- Biography -->
        <div class="w-full lg:w-2/3 space-y-4 text-gray-300">
          <p>
            <strong class="text-white">Dr. Muneeb Ali</strong> is a
            Pakistani-American computer scientist and entrepreneur. He is the
            co-founder of
            <a
              href="https://www.stacks.co"
              target="_blank"
              rel="noopener noreferrer"
              class="text-orange-500 hover:underline">Stacks</a
            >, a Bitcoin layer for smart contracts, and serves as the CEO of
            <a
              href="https://trustmachines.co"
              target="_blank"
              rel="noopener noreferrer"
              class="text-orange-500 hover:underline">Trust Machines</a
            >, a company building the largest ecosystem of Bitcoin applications.
          </p>
          <p>
            Dr. Ali earned his Ph.D. and Master's in Computer Science from
            Princeton University, where his doctoral thesis was nominated for
            the ACM SIGCOMM Dissertation Award. His research has garnered over
            1,900 citations, and he frequently delivers guest lectures on
            Bitcoin and decentralized systems at Princeton.
          </p>
          <p>
            Under his leadership, Stacks achieved a significant milestone by
            securing the first SEC-qualified token offering under the Reg A+
            exemption in 2019. He has successfully raised over $200 million from
            prominent investors, including Union Square Ventures, Y Combinator,
            and Breyer Capital.
          </p>
          <p>
            Dr. Ali's work has been featured in the book <em
              >Life After Google</em
            >, and he has served as a technical advisor for HBO's
            <em>Silicon Valley</em>. His contributions continue to shape the
            future of decentralized technology and Bitcoin innovation.
          </p>
        </div>
      </div>
    </div>
  </section>

  <Footer />
</div>

<style>
  .modal {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: rgba(0, 0, 0, 0.8);
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 50;
  }
</style>
