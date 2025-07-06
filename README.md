<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Shivam Blog</title>
  <link rel="stylesheet" href="https://fonts.googleapis.com/css?family=Roboto:400,700&display=swap" />
  <style>
    body {
      margin: 0;
      font-family: 'Roboto', sans-serif;
      background-color: #fff;
      color: #333;
      transition: background-color 0.3s, color 0.3s;
    }
    header {
      position: sticky;
      top: 0;
      background-color: #222;
      color: white;
      padding: 10px 20px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      z-index: 1000;
    }
    header h1 {
      font-size: 20px;
    }
    nav a {
      color: white;
      text-decoration: none;
      margin: 0 10px;
      font-weight: 500;
    }
    nav a:hover {
      text-decoration: underline;
    }
    .search-toggle {
      display: flex;
      gap: 10px;
    }
    input[type="search"] {
      padding: 5px;
      font-size: 14px;
    }
    .toggle-btn {
      padding: 5px 10px;
      cursor: pointer;
      background: #444;
      color: white;
      border: none;
    }
    .container {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
      gap: 20px;
      padding: 20px;
    }
    .card {
      background: #f5f5f5;
      padding: 15px;
      border-radius: 8px;
      transition: transform 0.3s, background-color 0.3s;
    }
    .card:hover {
      transform: scale(1.02);
    }
    .card img {
      width: 100%;
      height: 150px;
      object-fit: cover;
      border-radius: 6px;
    }
    .card h3 {
      margin: 10px 0 5px;
    }
    .card p {
      font-size: 14px;
    }
    .read-more {
      color: #0066cc;
      text-decoration: none;
      font-weight: bold;
    }
    .tags {
      display: flex;
      gap: 10px;
      flex-wrap: wrap;
      padding: 10px 20px;
    }
    .tag {
      background: #ddd;
      padding: 5px 10px;
      border-radius: 20px;
      cursor: pointer;
      font-size: 13px;
    }
    footer {
      background: #222;
      color: white;
      text-align: center;
      padding: 10px;
    }
    .dark {
      background-color: #111;
      color: white;
    }
    .dark .card {
      background: #222;
    }
    .dark header {
      background-color: #000;
    }
    .dark footer {
      background: #000;
    }
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
      <button class="toggle-btn" onclick="toggleDark()">🌓</button>
    </div>
  </header>

  <div class="tags">
    <span class="tag" onclick="filterByTag('all')">All</span>
    <span class="tag" onclick="filterByTag('education')">Education</span>
    <span class="tag" onclick="filterByTag('entertainment')">Entertainment</span>
    <span class="tag" onclick="filterByTag('lifestyle')">Lifestyle</span>
    <span class="tag" onclick="filterByTag('motivation')">Motivation</span>
  </div>

  <div class="container" id="postContainer">
    <div class="card" data-tags="education motivation">
      <img src="https://source.unsplash.com/300x200/?education" />
      <h3>Learn Anything Faster</h3>
      <p>Smart techniques to master topics quickly and retain knowledge.</p>
      <a href="#" class="read-more">Read More →</a>
    </div>
    <div class="card" data-tags="entertainment">
      <img src="https://source.unsplash.com/300x200/?movie" />
      <h3>Top 5 Netflix Shows</h3>
      <p>Discover the latest trending web series you shouldn't miss.</p>
      <a href="#" class="read-more">Read More →</a>
    </div>
    <div class="card" data-tags="lifestyle">
      <img src="https://source.unsplash.com/300x200/?lifestyle" />
      <h3>Healthy Daily Habits</h3>
      <p>Upgrade your lifestyle with these easy and effective tips.</p>
      <a href="#" class="read-more">Read More →</a>
    </div>
    <div class="card" data-tags="motivation">
      <img src="https://source.unsplash.com/300x200/?success" />
      <h3>5 Habits of Successful People</h3>
      <p>Motivate yourself with proven success habits you can adopt now.</p>
      <a href="#" class="read-more">Read More →</a>
    </div>
  </div>

  <footer>
    <p>&copy; 2025 Shivam Blog. All rights reserved.</p>
  </footer>

  <script>
    function toggleDark() {
      document.body.classList.toggle("dark");
    }

    document.getElementById("searchInput").addEventListener("input", function () {
      const value = this.value.toLowerCase();
      document.querySelectorAll(".card").forEach(card => {
        const text = card.innerText.toLowerCase();
        card.style.display = text.includes(value) ? "block" : "none";
      });
    });

    function filterByTag(tag) {
      document.querySelectorAll(".card").forEach(card => {
        const tags = card.dataset.tags.split(" ");
        if (tag === "all" || tags.includes(tag)) {
          card.style.display = "block";
        } else {
          card.style.display = "none";
        }
      });
    }
  </script>
</body>
</html>
