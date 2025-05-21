<nav class="w-full flex justify-between items-center py-4 px-10 bg-gray-800/80 backdrop-blur-sm fixed top-0 z-50">
    <div class="flex items-center">
      <img src="/lums_logo.png" alt="LUMS Logo" class="h-10 w-auto mr-2">
      <span class="text-2xl font-bold text-white ml-1">LUMS CeDAR</span>
    </div>
    <ul class="flex space-x-6">
      <li><a href="#about" class="hover:text-orange-600 text-white scroll-smooth">About</a></li>
      <li><a href="#vision" class="hover:text-orange-600 text-white scroll-smooth">Vision</a></li>
      <li><a href="#team" class="hover:text-orange-600 text-white scroll-smooth">Team</a></li>
      <li><a href="#projects" class="hover:text-orange-600 text-white scroll-smooth">Projects</a></li>
    </ul>
  </nav>
  
  <script>
    import { onMount } from 'svelte';
    
    onMount(() => {
      // Smooth scroll behavior for anchor links
      document.querySelectorAll('a[href^="#"]').forEach(anchor => {
        anchor.addEventListener('click', function (e) {
          e.preventDefault();
          const targetId = this.getAttribute('href');
          const targetElement = document.querySelector(targetId);
          
          if (targetElement) {
            const navbarHeight = 64; 
            const targetPosition = targetElement.getBoundingClientRect().top + window.pageYOffset - navbarHeight;
            window.scrollTo({
              top: targetPosition,
              behavior: 'smooth'
            });
          }
        });
      });
    });
  </script>
  