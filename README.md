<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Krishnasamy | Portfolio - School Project</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      background: #f4f6f9;
      color: #333;
      line-height: 1.6;
    }

    header {
      background: #24292e;
      color: white;
      padding: 40px 20px;
      text-align: center;
    }

    nav {
      background: #0366d6;
      text-align: center;
      padding: 12px;
    }

    nav a {
      color: white;
      text-decoration: none;
      margin: 0 15px;
      font-weight: bold;
    }

    nav a:hover {
      text-decoration: underline;
    }

    .container {
      max-width: 1000px;
      margin: 40px auto;
      padding: 20px;
    }

    .content {
      display: flex;
      flex-wrap: wrap;
      gap: 20px;
    }

    main {
      flex: 3;
      background: white;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 4px 8px rgba(0,0,0,0.05);
    }

    aside {
      flex: 1;
      background: #eaeaea;
      padding: 20px;
      border-radius: 10px;
    }

    footer {
      background: #24292e;
      color: white;
      text-align: center;
      padding: 15px;
      margin-top: 40px;
    }

    footer a {
      color: white;
      text-decoration: none;
    }

    @media (max-width: 768px) {
      .content {
        flex-direction: column;
      }
    }
  </style>
</head>

<body>

<header>
  <h1>Welcome to My GitHub Page</h1>
  <p>Student Portfolio | Built with GitHub Pages</p>
</header>

<nav>
  <a href="#home">Home</a>
  <a href="#projects">Projects</a>
  <a href="#about">About</a>
  <a href="#contact">Contact</a>
</nav>

<div class="container">
  <div class="content">
    
    <main>
      <section id="home">
        <h2>Main Content</h2>
        <p>This is where you showcase your projects, achievements, and skills.</p>
      </section>
    </main>

    <aside>
      <h2>Sidebar</h2>
      <p>Add your GitHub profile link or quick info here.</p>
    </aside>

  </div>
</div>

<footer>
  © 2026 Your Name | Hosted on GitHub Pages
</footer>

</body>
</html>
