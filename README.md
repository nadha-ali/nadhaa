<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />

  <title>Feast — Food Photography</title>

  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link
    href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600;700&family=Playfair+Display:wght@500;600;700&display=swap"
    rel="stylesheet"
  />

  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    html {
      scroll-behavior: smooth;
    }

    body {
      font-family: "DM Sans", sans-serif;
      background: #faf7f2;
      color: #241c17;
    }

    /* NAVBAR */

    nav {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      z-index: 100;
      padding: 22px 6%;
      display: flex;
      align-items: center;
      justify-content: space-between;
      background: rgba(250, 247, 242, 0.9);
      backdrop-filter: blur(12px);
      border-bottom: 1px solid rgba(36, 28, 23, 0.08);
    }

    .logo {
      font-family: "Playfair Display", serif;
      font-size: 28px;
      font-weight: 700;
      color: #241c17;
    }

    .logo span {
      color: #c75b32;
    }

    nav ul {
      display: flex;
      list-style: none;
      gap: 35px;
    }

    nav a {
      color: #241c17;
      text-decoration: none;
      font-size: 14px;
      font-weight: 600;
      transition: 0.3s;
    }

    nav a:hover {
      color: #c75b32;
    }

    .menu-btn {
      display: none;
      border: none;
      background: none;
      font-size: 26px;
      cursor: pointer;
    }

    /* HERO */

    .hero {
      min-height: 100vh;
      padding: 130px 6% 70px;
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 70px;
      align-items: center;
    }

    .hero-text {
      max-width: 600px;
    }

    .eyebrow {
      color: #c75b32;
      font-size: 13px;
      font-weight: 700;
      text-transform: uppercase;
      letter-spacing: 2px;
      margin-bottom: 20px;
    }

    .hero h1 {
      font-family: "Playfair Display", serif;
      font-size: clamp(55px, 7vw, 100px);
      line-height: 0.95;
      margin-bottom: 28px;
    }

    .hero h1 em {
      color: #c75b32;
      font-weight: 500;
    }

    .hero p {
      color: #71675f;
      max-width: 500px;
      font-size: 17px;
      line-height: 1.8;
      margin-bottom: 35px;
    }

    .hero-button {
      display: inline-block;
      padding: 15px 28px;
      background: #241c17;
      color: white;
      text-decoration: none;
      border-radius: 50px;
      font-size: 14px;
      font-weight: 600;
      transition: 0.3s;
    }

    .hero-button:hover {
      background: #c75b32;
      transform: translateY(-3px);
    }

    .hero-image {
      position: relative;
      height: 650px;
    }

    .hero-image img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      border-radius: 180px 180px 20px 20px;
      box-shadow: 0 30px 70px rgba(40, 25, 15, 0.18);
    }

    .image-tag {
      position: absolute;
      bottom: 25px;
      left: -25px;
      background: white;
      padding: 18px 25px;
      border-radius: 15px;
      box-shadow: 0 15px 35px rgba(0, 0, 0, 0.12);
    }

    .image-tag strong {
      display: block;
      font-family: "Playfair Display", serif;
      font-size: 18px;
    }

    .image-tag span {
      font-size: 12px;
      color: #8b8179;
    }

    /* SECTION */

    section {
      padding: 110px 6%;
    }

    .section-header {
      display: flex;
      justify-content: space-between;
      align-items: end;
      margin-bottom: 45px;
    }

    .section-header h2 {
      font-family: "Playfair Display", serif;
      font-size: clamp(40px, 5vw, 65px);
    }

    .section-header p {
      max-width: 400px;
      color: #776e67;
      line-height: 1.7;
    }

    /* FILTERS */

    .filters {
      display: flex;
      gap: 10px;
      flex-wrap: wrap;
      margin-bottom: 40px;
    }

    .filter {
      border: 1px solid #ddd4cb;
      background: transparent;
      padding: 11px 20px;
      border-radius: 50px;
      cursor: pointer;
      color: #5c5149;
      transition: 0.3s;
    }

    .filter:hover,
    .filter.active {
      background: #241c17;
      color: white;
      border-color: #241c17;
    }

    /* GALLERY */

    .gallery {
      columns: 3 300px;
      column-gap: 22px;
    }

    .card {
      position: relative;
      break-inside: avoid;
      margin-bottom: 22px;
      overflow: hidden;
      border-radius: 16px;
      cursor: pointer;
    }

    .card img {
      display: block;
      width: 100%;
      transition: transform 0.6s ease;
    }

    .card:hover img {
      transform: scale(1.05);
    }

    .card-overlay {
      position: absolute;
      inset: 0;
      display: flex;
      align-items: end;
      padding: 25px;
      background: linear-gradient(
        transparent 45%,
        rgba(20, 12, 8, 0.85)
      );
      opacity: 0;
      transition: 0.3s;
    }

    .card:hover .card-overlay {
      opacity: 1;
    }

    .card-overlay h3 {
      color: white;
      font-family: "Playfair Display", serif;
      font-size: 25px;
    }

    .card-overlay span {
      display: block;
      color: #ddd;
      font-size: 12px;
      margin-top: 4px;
    }

    /* FEATURE */

    .feature {
      background: #241c17;
      color: white;
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 70px;
      align-items: center;
    }

    .feature-image img {
      width: 100%;
      height: 600px;
      object-fit: cover;
      border-radius: 20px;
    }

    .feature-text .eyebrow {
      color: #e88559;
    }

    .feature-text h2 {
      font-family: "Playfair Display", serif;
      font-size: clamp(45px, 5vw, 70px);
      line-height: 1;
      margin-bottom: 25px;
    }

    .feature-text p {
      color: #c2b8b0;
      line-height: 1.8;
      margin-bottom: 30px;
      max-width: 500px;
    }

    .light-button {
      display: inline-block;
      padding: 14px 25px;
      border: 1px solid #8c8178;
      color: white;
      text-decoration: none;
      border-radius: 50px;
      transition: 0.3s;
    }

    .light-button:hover {
      background: white;
      color: #241c17;
    }

    /* ABOUT */

    .about {
      text-align: center;
      max-width: 900px;
      margin: auto;
    }

    .about h2 {
      font-family: "Playfair Display", serif;
      font-size: clamp(45px, 6vw, 75px);
      line-height: 1.05;
      margin-bottom: 25px;
    }

    .about h2 span {
      color: #c75b32;
    }

    .about p {
      color: #71675f;
      line-height: 1.9;
      font-size: 17px;
    }

    /* FOOTER */

    footer {
      padding: 60px 6%;
      background: #17110e;
      color: white;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    footer .logo {
      color: white;
    }

    footer p {
      color: #958a82;
      font-size: 13px;
    }

    .socials {
      display: flex;
      gap: 20px;
    }

    .socials a {
      color: #ddd;
      text-decoration: none;
      font-size: 13px;
    }

    .socials a:hover {
      color: #e88559;
    }

    /* RESPONSIVE */

    @media (max-width: 800px) {

      nav {
        padding: 18px 5%;
      }

      nav ul {
        position: absolute;
        top: 70px;
        left: 0;
        width: 100%;
        background: #faf7f2;
        flex-direction: column;
        padding: 25px 6%;
        gap: 20px;
        display: none;
      }

      nav ul.show {
        display: flex;
      }

      .menu-btn {
        display: block;
      }

      .hero {
        grid-template-columns: 1fr;
        padding-top: 120px;
      }

      .hero-image {
        height: 500px;
      }

      .image-tag {
        left: 15px;
      }

      .section-header {
        display: block;
      }

      .section-header p {
        margin-top: 15px;
      }

      .feature {
        grid-template-columns: 1fr;
      }

      .feature-image img {
        height: 450px;
      }

      footer {
        flex-direction: column;
        gap: 25px;
        text-align: center;
      }
    }
  </style>
</head>

<body>

  <!-- NAVIGATION -->

  <nav>
    <div class="logo">Feast<span>.</span></div>

    <button class="menu-btn" onclick="toggleMenu()">☰</button>

    <ul id="navLinks">
      <li><a href="#home">Home</a></li>
      <li><a href="#gallery">Gallery</a></li>
      <li><a href="#story">Our Story</a></li>
      <li><a href="#contact">Contact</a></li>
    </ul>
  </nav>


  <!-- HERO -->

  <main id="home">

    <section class="hero">

      <div class="hero-text">

        <div class="eyebrow">
          Food Photography
        </div>

        <h1>
          Food worth
          <em>remembering.</em>
        </h1>

        <p>
          A visual collection celebrating beautiful food,
          unforgettable flavors, and the stories behind every plate.
        </p>

        <a href="#gallery" class="hero-button">
          Explore the gallery →
        </a>

      </div>

      <div class="hero-image">

        <img
          src="https://images.unsplash.com/photo-1547592180-85f173990554?auto=format&fit=crop&w=1000&q=90"
          alt="Beautiful food photography"
        >

        <div class="image-tag">
          <strong>Fresh & Delicious</strong>
          <span>Captured with love</span>
        </div>

      </div>

    </section>


    <!-- GALLERY -->

    <section id="gallery">

      <div class="section-header">

        <div>
          <div class="eyebrow">The Collection</div>
          <h2>From the table.</h2>
        </div>

        <p>
          Explore a collection of dishes, ingredients and moments
          captured through the lens.
        </p>

      </div>

      <div class="filters">

        <button class="filter active" data-filter="all">
          All
        </button>

        <button class="filter" data-filter="main">
          Main Course
        </button>

        <button class="filter" data-filter="dessert">
          Desserts
        </button>

        <button class="filter" data-filter="drink">
          Drinks
        </button>

        <button class="filter" data-filter="breakfast">
          Breakfast
        </button>

      </div>


      <div class="gallery">

        <div class="card" data-category="main">
          <img
            src="https://images.unsplash.com/photo-1547592180-85f173990554?auto=format&fit=crop&w=900&q=85"
            alt="Vegetable dish"
          >
          <div class="card-overlay">
            <div>
              <h3>Garden Bowl</h3>
              <span>Main Course</span>
            </div>
          </div>
        </div>


        <div class="card" data-category="dessert">
          <img
            src="https://images.unsplash.com/photo-1551024506-0bccd828d307?auto=format&fit=crop&w=900&q=85"
            alt="Donuts"
          >
          <div class="card-overlay">
            <div>
              <h3>Sweet Moments</h3>
              <span>Dessert</span>
            </div>
          </div>
        </div>


        <div class="card" data-category="drink">
          <img
            src="https://images.unsplash.com/photo-1513558161293-cdaf765ed2fd?auto=format&fit=crop&w=900&q=85"
            alt="Fresh drink"
          >
          <div class="card-overlay">
            <div>
              <h3>Summer Sip</h3>
              <span>Drinks</span>
            </div>
          </div>
        </div>


        <div class="card" data-category="breakfast">
          <img
            src="https://images.unsplash.com/photo-1533089860892-a7c6f0a88666?auto=format&fit=crop&w=900&q=85"
            alt="Pancakes"
          >
          <div class="card-overlay">
            <div>
              <h3>Slow Morning</h3>
              <span>Breakfast</span>
            </div>
          </div>
        </div>


        <div class="card" data-category="main">
          <img
            src="https://images.unsplash.com/photo-1473093295043-cdd812d0e601?auto=format&fit=crop&w=900&q=85"
            alt="Pasta"
          >
          <div class="card-overlay">
            <div>
              <h3>Italian Night</h3>
              <span>Main Course</span>
            </div>
          </div>
        </div>


        <div class="card" data-category="dessert">
          <img
            src="https://images.unsplash.com/photo-1565958011703-44f9829ba187?auto=format&fit=crop&w=900&q=85"
            alt="Cake"
          >
          <div class="card-overlay">
            <div>
              <h3>Berry Cake</h3>
              <span>Dessert</span>
            </div>
          </div>
        </div>


        <div class="card" data-category="main">
          <img
            src="https://images.unsplash.com/photo-1515003197210-e0cd71810b5f?auto=format&fit=crop&w=900&q=85"
            alt="Food plate"
          >
          <div class="card-overlay">
            <div>
              <h3>Rustic Plate</h3>
              <span>Main Course</span>
            </div>
          </div>
        </div>


        <div class="card" data-category="drink">
          <img
            src="https://images.unsplash.com/photo-1551024709-8f23befc6f87?auto=format&fit=crop&w=900&q=85"
            alt="Drink"
          >
          <div class="card-overlay">
            <div>
              <h3>Evening Pour</h3>
              <span>Drinks</span>
            </div>
          </div>
        </div>

      </div>

    </section>


    <!-- FEATURE -->

    <section class="feature">

      <div class="feature-image">

        <img
          src="https://images.unsplash.com/photo-1540189549336-e6e99c3679fe?auto=format&fit=crop&w=1200&q=90"
          alt="Fresh colorful food"
        >

      </div>

      <div class="feature-text">

        <div class="eyebrow">
          Today's Feature
        </div>

        <h2>
          Simple food.
          Beautifully captured.
        </h2>

        <p>
          Great food photography isn't just about making food
          look delicious. It's about capturing the atmosphere,
          texture, color and emotion that makes us want to sit
          down and take a bite.
        </p>

        <a href="#gallery" class="light-button">
          View more photos
        </a>

      </div>

    </section>


    <!-- ABOUT -->

    <section id="story">

      <div class="about">

        <div class="eyebrow">
          Our Story
        </div>

        <h2>
          We believe every dish
          has a <span>story.</span>
        </h2>

        <p>
          Feast is a visual journal dedicated to the art of food.
          From the first ingredient to the final plate, we capture
          the details that make eating such a beautiful experience.
        </p>

      </div>

    </section>

  </main>


  <!-- FOOTER -->

  <footer id="contact">

    <div>
      <div class="logo">
        Feast<span>.</span>
      </div>

      <p>
        Food photography for food lovers.
      </p>
    </div>

    <div class="socials">
      <a href="#">Instagram</a>
      <a href="#">Pinterest</a>
      <a href="#">Email</a>
    </div>

  </footer>


  <!-- JAVASCRIPT -->

  <script>

    // Mobile menu

    function toggleMenu() {
      document
        .getElementById("navLinks")
        .classList
        .toggle("show");
    }


    // Gallery filtering

    const filters = document.querySelectorAll(".filter");
    const cards = document.querySelectorAll(".card");

    filters.forEach(filter => {

      filter.addEventListener("click", () => {

        filters.forEach(btn => {
          btn.classList.remove("active");
        });

        filter.classList.add("active");

        const category = filter.dataset.filter;

        cards.forEach(card => {

          if (
            category === "all" ||
            card.dataset.category === category
          ) {
            card.style.display = "block";
          } else {
            card.style.display = "none";
          }

        });

      });

    });

  </script>

</body>
</html>
