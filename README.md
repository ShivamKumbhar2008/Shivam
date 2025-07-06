<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Shivam Blog</title>
  <style>
    body { margin: 0; font-family: sans-serif; background: #fff; color: #000; }
    header, footer { background: #222; color: #fff; padding: 10px 20px; }
    header nav a { margin: 0 10px; color: white; text-decoration: none; }
    .search-toggle { float: right; }
    .container { display: grid; grid-template-columns: repeat(auto-fill, minmax(280px, 1fr)); gap: 20px; padding: 20px; }
    .card { background: #f5f5f5; padding: 15px; border-radius: 8px; }
    .tags { padding: 10px 20px; }
    .tag { background: #ddd; padding: 5px 10px; border-radius: 10px; margin-right: 5px; cursor: pointer; }
    .dark { background: #111; color: #fff; }
  </style>
</head>
<body>
  <header>
    <h1>Shivam Blog</h1>
    <nav>
      <a href="#">Home</a>
      <a href="#">Entertainment</a>
      <a href="#">Education</a>
      <a href="#">Social</a>
      <a href="#">Lifestyle</a>
      <a href="#">Motivation</a>
      <a href="#">News</a>
      <a href="#">About</a>
      <a href="#">Contact</a>
    </nav>
    <div class="search-toggle">
      <input type="search" id="searchInput" placeholder="Search..." />
      <button onclick="toggleDark()">🌗</button>
    </div>
  </header>

  <div class="tags">
    <span class="tag" onclick="filter('all')">All</span>
    <span class="tag" onclick="filter('education')">Education</span>
    <span class="tag" onclick="filter('lifestyle')">Lifestyle</span>
    <span class="tag" onclick="filter('entertainment')">Entertainment</span>
  </div>

  <div class="container" id="posts"></div>

  <footer>
    <p>&copy; 2025 Shivam Blog. All rights reserved.</p>
  </footer>

  <script>
    fetch("https://shivam-backend.onrender.com/api/posts")
      .then(res => res.json())
      .then(posts => {
        document.getElementById('posts').innerHTML = '';
        posts.forEach(post => {
          const div = document.createElement('div');
          div.className = 'card';
          div.innerHTML = `<h3>${post.title}</h3><p>${post.content}</p><p><em>${post.tag}</em></p>`;
          document.getElementById('posts').appendChild(div);
        });
      });

    function toggleDark() {
      document.body.classList.toggle("dark");
    }

    document.getElementById("searchInput").addEventListener("input", function () {
      const val = this.value.toLowerCase();
      const cards = document.querySelectorAll(".card");
      cards.forEach(c => {
        c.style.display = c.innerText.toLowerCase().includes(val) ? 'block' : 'none';
      });
    });
  </script>
</body>
</html>
