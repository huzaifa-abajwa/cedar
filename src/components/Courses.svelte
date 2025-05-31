<script>
  const courses = [
    {
      code: "CS 3812",
      title: "Introduction to Blockchain: Technologies & Applications",
      terms: ["Spring 2022", "Spring 2023", "Spring 2024"]
    },
    {
      code: "CS 589",
      title: "Recent Developments in Blockchain Technology",
      terms: ["Fall 2022"]
    },
    {
      code: "MBA 6038A",
      title: "Blockchain and Cryptocurrency",
      terms: ["Fall 2021", "Fall 2022", "Fall 2023", "Fall 2024"]
    }
  ];
</script>

<div id="courses" class="min-h-[60vh] py-24 bg-transparent">
  <div class="container mx-auto px-6 md:px-20">
    <!-- Section Header -->
    <div class="text-center mb-12">
      <h2 class="text-4xl md:text-5xl font-light bg-gradient-to-r from-red-600 to-orange-600 bg-clip-text text-transparent">
        Courses Taught
      </h2>
      <div class="w-24 h-1 bg-gradient-to-r from-red-600 to-orange-600 rounded-full mt-4 mx-auto"></div>
    </div>

    <!-- Courses Card -->
    <div class="grid md:grid-cols-2 gap-8">
      <div class="bg-gray-800/30 backdrop-blur-sm border border-gray-700/50 rounded-lg p-6 col-span-full shadow-lg">
        <ul class="list-disc list-inside space-y-4 text-gray-300 text-base leading-relaxed">
          {#each courses as course}
            <li>
              <span class="text-white font-semibold">{course.code} – {course.title}</span><br />
              <span class="text-gray-400 italic">Offered in: {course.terms.join(", ")}</span>
            </li>
          {/each}
        </ul>
      </div>
    </div>
  </div>
</div>
