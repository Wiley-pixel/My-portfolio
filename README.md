<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Mutunga Willy- Portfolio</title>
  <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-gray-100 text-gray-900">

  <!-- Header -->
  <header class="bg-gray-900 text-white py-10">
    <div class="max-w-4xl mx-auto text-center">
      <h1 class="text-4xl font-bold">Mutunga Willy</h1>
      <p class="text-lg mt-2">Computer Science & Cybersecurity Student | Aspiring Data Analyst</p>
    </div>
  </header>

  <!-- Navigation -->
  <nav class="bg-gray-800">
    <div class="max-w-4xl mx-auto flex justify-center space-x-6 py-3">
      <a href="#about" class="text-white hover:text-yellow-400">About</a>
      <a href="#projects" class="text-white hover:text-yellow-400">Projects</a>
      <a href="#skills" class="text-white hover:text-yellow-400">Skills</a>
      <a href="#contact" class="text-white hover:text-yellow-400">Contact</a>
    </div>
  </nav>

  <!-- About Section -->
  <section id="about" class="max-w-4xl mx-auto my-12 p-6 bg-white rounded-xl shadow">
    <h2 class="text-2xl font-semibold mb-4">About Me</h2>
    <p>Hello! I'm <b>Mutunga Willy</b>, a Diploma student in Computer Science & Cybersecurity. 
       Passionate about technology, data, and security. I'm currently seeking an 
       attachment opportunity to apply my skills and grow professionally.</p>
  </section>

<!-- Projects Section -->
<section id="projects" class="max-w-5xl mx-auto my-12 p-6 bg-white rounded-xl shadow">
  <h2 class="text-3xl font-semibold mb-6 text-center">Projects</h2>
  
  <div class="grid md:grid-cols-3 gap-6">
    
    <!-- Project 1 -->
    <div class="bg-gray-50 rounded-lg shadow hover:shadow-xl transition p-4">
      <img src="images/cyberlab.jpg" alt="Cyber Security Lab" class="rounded-lg mb-3">
      <h3 class="font-bold text-lg">Cyber Security Lab Simulation</h3>
      <p class="text-sm text-gray-600">Penetration testing on virtual machines using Kali Linux & Wireshark.</p>
      <a href="https://github.com/yourusername/cyberlab" target="_blank" 
         class="inline-block mt-3 px-4 py-2 bg-blue-600 text-white rounded-lg hover:bg-blue-700">
         🔗 View Project
      </a>
    </div>

    <!-- Project 2 -->
    <div class="bg-gray-50 rounded-lg shadow hover:shadow-xl transition p-4">
      <img src="images/database.jpg" alt="Database Project" class="rounded-lg mb-3">
      <h3 class="font-bold text-lg">Database Management System</h3>
      <p class="text-sm text-gray-600">Designed a MySQL database for a retail shop to manage sales & inventory.</p>
      <a href="https://github.com/yourusername/database-project" target="_blank" 
         class="inline-block mt-3 px-4 py-2 bg-blue-600 text-white rounded-lg hover:bg-blue-700">
         🔗 View Project
      </a>
    </div>

    <!-- Project 3 -->
    <div class="bg-gray-50 rounded-lg shadow hover:shadow-xl transition p-4">
      <img src="images/portfolio.jpg" alt="Portfolio Website" class="rounded-lg mb-3">
      <h3 class="font-bold text-lg">Portfolio Website</h3>
      <p class="text-sm text-gray-600">This website built using HTML, CSS, JavaScript & Tailwind.</p>
      <a href="https://mutungawillyportfolio.com" target="_blank" 
         class="inline-block mt-3 px-4 py-2 bg-blue-600 text-white rounded-lg hover:bg-blue-700">
         🔗 Live Demo
      </a>
    </div>

  </div>
</section>


  <!-- Skills Section -->
  <section id="skills" class="max-w-4xl mx-auto my-12 p-6 bg-white rounded-xl shadow">
    <h2 class="text-2xl font-semibold mb-4">Technical Skills</h2>
    <ul class="grid grid-cols-2 gap-3">
      <li>✅ Python, Java, C basics</li>
      <li>✅ MySQL, SQL queries</li>
      <li>✅ Ethical Hacking Basics</li>
      <li>✅ Wireshark, Kali Linux</li>
      <li>✅ PowerBI, Excel</li>
      <li>✅ Troubleshooting & Networking</li>
    </ul>
  </section>

  <!-- Contact Section -->
  <section id="contact" class="max-w-4xl mx-auto my-12 p-6 bg-white rounded-xl shadow text-center">
    <h2 class="text-2xl font-semibold mb-4">Contact Me</h2>
    <p>Email: <a href="mailto:mutungawilly38@gmail.com" class="text-blue-600">mutungawilly38@gmail.com</a></p>
    <p>LinkedIn: <a href="www.linkedin.com/in/willy-musyoka-a1bba7334" target="_blank" class="text-blue-600">www.linkedin.com/in/willy-musyoka-a1bba7334</a></p>
    <p>GitHub: <a href="https://github.com/wiley-pixel" target="_blank" class="text-blue-600">github.com/wiley-pixel</a></p>
  </section>

  <!-- Footer -->
  <footer class="bg-gray-900 text-white py-4 text-center">
    <p>© 2025 Mutunga Willy | Portfolio Website</p>
  </footer>

</body>
</html>
