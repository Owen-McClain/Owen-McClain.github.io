# Owen-McClain.github.io

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Engineering Portfolio</title>
  <style>
    :root {
      --bg: #0d0d0d;
      --card: #1a1a1a;
      --accent: #4f7cff;
      --text: #e6e6e6;
      --text-light: #b3b3b3;
      --radius: 14px;
    }

    body {
      margin: 0;
      font-family: "Segoe UI", Arial, sans-serif;
      background: var(--bg);
      color: var(--text);
      line-height: 1.6;
    }

    header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 20px 40px;
      position: sticky;
      top: 0;
      background: rgba(13, 13, 13, 0.9);
      backdrop-filter: blur(8px);
      z-index: 100;
    }

    nav a {
      margin-left: 24px;
      text-decoration: none;
      color: var(--text);
      transition: 0.2s;
    }

    nav a:hover {
      color: var(--accent);
    }

    .hero {
      padding: 120px 40px 100px;
      max-width: 900px;
    }

    .hero h1 {
      font-size: 3.4rem;
      margin-bottom: 10px;
    }

    .hero p {
      font-size: 1.2rem;
      color: var(--text-light);
      max-width: 600px;
    }

    section {
      padding: 60px 40px;
      max-width: 1100px;
    }

    h2 {
      font-size: 2.4rem;
      margin-bottom: 20px;
    }

    .projects {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
      gap: 20px;
    }

    .card {
      background: var(--card);
      padding: 24px;
      border-radius: var(--radius);
      transition: 0.25s;
      border: 1px solid #242424;
      cursor: pointer;
    }

    .card:hover {
      transform: translateY(-4px);
      border-color: var(--accent);
    }

    .card h3 {
      margin-top: 0;
    }

    .card p {
      color: var(--text-light);
      font-size: 0.95rem;
    }

    footer {
      padding: 40px;
      text-align: center;
      color: var(--text-light);
    }

    .contact a {
      color: var(--accent);
      text-decoration: none;
    }

    /* Modal Carousel */
    .modal {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0, 0, 0, 0.8);
      display: none;
      justify-content: center;
      align-items: center;
      z-index: 200;
    }

    .modal-content {
      position: relative;
      max-width: 80%;
      max-height: 80%;
    }

    .modal img {
      width: 100%;
      border-radius: var(--radius);
    }

    .close-btn {
      position: absolute;
      top: -40px;
      right: 0;
      font-size: 2rem;
      cursor: pointer;
      color: var(--text);
    }

    .arrow {
      position: absolute;
      top: 50%;
      transform: translateY(-50%);
      font-size: 3rem;
      cursor: pointer;
      color: var(--text);
      user-select: none;
    }

    .left { left: -60px; }
    .right { right: -60px; }
  </style>
</head>
<body>
  <header>
    <div class="logo">Owen McClain - Engineering Portfolio</div>
    <nav>
      <a href="#about">About</a>
      <a href="#projects">Projects</a>
      <a href="#contact">Contact</a>
    </nav>
  </header>

  <section class="hero" id="about">
    <h1>Hi, I'm Owen McClain</h1>
    <p>
      I'm a Mechanical Engineering student at the University of Colorado Boulder, with experience in Solidworks parts and assemblies. I aim to apply engineering principles to create efficient and elegant solutions to design challenges.
    </p>
  </section>

  <section id="projects">
    <h2>Projects</h2>
    <div class="projects">

     <a href="aircraft.html" class="project-card">
    <img src="images/plane1.jpg" alt="Aircraft Project">
    <h3>Aircraft CAD Model</h3>
</a>

<a href="truck.html" class="project-card">
    <img src="images/truck1.jpg" alt="Truck Project">
    <h3>Skateboard Truck Assembly</h3>
</a>

<a href="vise.html" class="project-card">
    <img src="images/vise1.jpg" alt="Vise Project">
    <h3>Precision Machined Fractal Vise</h3>
</a>
    </div>
  </section>

  <section id="contact">
    <h2>Contact</h2>
    <p class="contact">Email: <a href="mailto:owen.mcclain04@gmail.com">owen.mcclain04@gmail.com</a></p>
    <p class="contact">LinkedIn: <a href="#">linkedin.com/in/owen-mcclain-71a253310</a></p>
  </section>

  <footer>
    © 2025 Owen McClain — Engineering Portfolio
  </footer>

  <!-- Modal -->
  <div class="modal" id="modal">
    <div class="modal-content">
      <span class="close-btn" id="close">×</span>
      <span class="arrow left" id="left">❮</span>
      <img id="modal-img" src="">
      <span class="arrow right" id="right">❯</span>
    </div>
  </div>

  <script>
    const modal = document.getElementById("modal");
    const modalImg = document.getElementById("modal-img");
    const closeBtn = document.getElementById("close");
    const leftArrow = document.getElementById("left");
    const rightArrow = document.getElementById("right");

    let images = [];
    let index = 0;

    document.querySelectorAll(".card").forEach(card => {
      card.addEventListener("click", () => {
        images = card.dataset.images.split(",").map(img => "images/" + img.trim());
        index = 0;
        modalImg.src = images[index];
        modal.style.display = "flex";
      });
    });

    closeBtn.onclick = () => modal.style.display = "none";

    leftArrow.onclick = () => {
      index = (index - 1 + images.length) % images.length;
      modalImg.src = images[index];
    };

    rightArrow.onclick = () => {
      index = (index + 1) % images.length;
      modalImg.src = images[index];
    };

    window.onclick = e => {
      if (e.target === modal) modal.style.display = "none";
    };
  </script>
</body>
</html>
