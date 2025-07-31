<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Driveway Detailing</title>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&family=Montserrat:wght@400;600&display=swap" rel="stylesheet" />
  <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css" rel="stylesheet"/>
  <link href="https://cdn.jsdelivr.net/npm/aos@2.3.4/dist/aos.css" rel="stylesheet"/>
  <style>
    /* Base */
    * { box-sizing: border-box; margin: 0; padding: 0; }
    body { font-family: 'Poppins', sans-serif; line-height: 1.6; color: #222; background: #f6f6f6; }
    a { text-decoration: none; color: inherit; }

    /* Navbar */
    nav { position: fixed; width: 100%; top: 0; left: 0; display: flex; justify-content: space-between; align-items: center; padding: 1rem 2rem; z-index: 999; font-family: 'Montserrat', sans-serif; font-weight: 600; transition: background 0.3s; }
    nav.transparent { background: transparent; color: #fff; }
    nav.scrolled { background: rgba(0,0,0,0.85); color: #fff; box-shadow: 0 2px 8px rgba(0,0,0,0.3); }
    nav .logo { font-size: 1.8rem; color: inherit; cursor: pointer; }
    nav ul { list-style: none; display: flex; gap: 2rem; }
    nav ul li a { position: relative; padding: 0.5rem 0; color: inherit; transition: color 0.3s; }
    nav ul li a::after { content: ''; position: absolute; bottom: -2px; left: 0; width: 0; height: 2px; background: #4CAF50; transition: width 0.3s; }
    nav ul li a:hover::after, nav ul li a.active::after { width: 100%; }
    nav ul li a:hover, nav ul li a.active { color: #4CAF50; }

    /* Hero */
    header { display: flex; align-items: center; justify-content: center; height: 100vh; background: url('assets/car-wash.gif') center/cover no-repeat; position: relative; text-align: center; }
    header::before { content: ''; position: absolute; inset: 0; background: rgba(0,0,0,0.5); }
    header .hero-content { position: relative; z-index: 2; max-width: 800px; padding: 1rem; }
    header h1 { font-family: 'Montserrat', sans-serif; font-size: 3.8rem; margin-bottom: 0.8rem; color: #fff; text-shadow: 0 4px 10px rgba(0,0,0,0.7); }
    header p { font-size: 1.3rem; margin-bottom: 1.5rem; color: #fff; text-shadow: 0 2px 8px rgba(0,0,0,0.6); }
    .btn-book { background: #4CAF50; color: #fff; padding: 0.8rem 2.5rem; font-size: 1.1rem; font-weight: 700; border: none; border-radius: 40px; cursor: pointer; box-shadow: 0 4px 15px rgba(76, 175, 80, 0.4); transition: background 0.3s, transform 0.3s; }
    .btn-book:hover { background: #45a047; transform: translateY(-2px); }

    /* Sections */
    section { padding: 4rem 2rem; max-width: 1100px; margin: 0 auto; }
    section h2 { font-family: 'Montserrat', sans-serif; font-size: 2.8rem; margin-bottom: 1.5rem; text-align: center; }

    /* Packages */
    #packages .package-list { display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 2rem; }
    #packages .package { background: #fff; padding: 2rem; border-radius: 12px; box-shadow: 0 6px 18px rgba(0,0,0,0.1); transition: transform 0.3s; }
    #packages .package:hover { transform: translateY(-5px); }
    #packages .package h3 { font-size: 1.5rem; color: #4CAF50; font-weight: 600; margin-bottom: 0.8rem; }
    #packages .price { font-size: 1.5rem; font-weight: 700; margin-bottom: 1rem; }
    #packages .package ul { list-style: none; color: #555; }
    #packages .package ul li { margin-bottom: 0.6rem; }

    /* Gallery */
    #gallery .grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 15px; }
    #gallery img { width: 100%; border-radius: 12px; height: 180px; object-fit: cover; box-shadow: 0 4px 10px rgba(0,0,0,0.1); transition: transform 0.3s, box-shadow 0.3s; cursor: pointer;}
    #gallery img:hover { transform: scale(1.05); box-shadow: 0 8px 25px rgba(0,0,0,0.15); }

    /* Testimonials */
    #testimonials { background: #fff; border-radius: 12px; padding: 3rem 2rem; box-shadow: 0 6px 18px rgba(0,0,0,0.1); max-width: 800px; margin: 0 auto; }
    #testimonials .testimonial { margin-bottom: 2rem; font-style: italic; color: #333; font-size: 1.1rem; }
    #testimonials .author { margin-top: 1rem; text-align: right; font-weight: 600; color: #4CAF50; }

    /* Contact */
    #contact { background: #222; color: #fff; text-align: center; border-radius: 12px; padding: 3.5rem 2rem; margin-bottom: 3rem; }
    #contact h2 { color: #4CAF50; margin-bottom: 1.5rem; }
    #contact p { font-size: 1.1rem; margin: 0.8rem 0; }
    #contact a { color: #4CAF50; font-weight: 600; }
    #contact a:hover { text-decoration: underline; }

    /* Footer */
    footer { text-align: center; padding: 1.5rem 1rem; font-size: 0.9rem; color: #888; background: #f6f6f6; }

    /* Floating Buttons */
    .floating-contact { position: fixed; bottom: 20px; right: 20px; display: flex; flex-direction: column; gap: 15px; z-index: 1000; }
    .floating-contact a { display: flex; align-items: center; justify-content: center; width: 55px; height: 55px; border-radius: 50%; color: #fff; font-size: 28px; box-shadow: 0 4px 12px rgba(0,0,0,0.3); transition: transform 0.3s; }
    .whatsapp-btn { background: #25D366; }
    .instagram-btn { background: radial-gradient(circle at 30% 107%, #fdf497 0%, #fd5949 45%, #d6249f 60%, #285AEB 90%); }
    .floating-contact a:hover { transform: scale(1.1); }

    /* Responsive */
    @media(max-width:768px) { header h1 { font-size: 2.5rem; } header p { font-size: 1.1rem; } nav ul { display: none; } nav.active ul { display: flex; flex-direction: column; background: rgba(0,0,0,0.9); padding: 1rem; position: fixed; top: 60px; right: 0; width: 200px; border-radius: 0 0 0 12px; } }
  </style>
</head>
<body>

  <nav id="navbar" class="transparent">
    <div class="logo">Driveway Detailing</div>
    <ul>
      <li><a href="#packages" class="active">Packages</a></li>
      <li><a href="#gallery">Gallery</a></li>
      <li><a href="#testimonials">Testimonials</a></li>
      <li><a href="#contact">Contact</a></li>
    </ul>
    <div class="menu-toggle" onclick="toggleMenu()"><i class="fas fa-bars" style="color:#fff; font-size:1.5rem;"></i></div>
  </nav>

  <header>
    <div class="hero-content" data-aos="fade-up">
      <h1>Driveway Detailing</h1>
      <p>Mobile Car Wash &amp; Detailing in Paarl / Wellington</p>
      <a href="#contact" class="btn-book">Book Now</a>
    </div>
  </header>

  <section id="packages">
    <h2>Our Packages</h2>
    <div class="package-list">
      <div class="package" data-aos="fade-up" data-aos-delay="100">
        <h3>The Mountain Top</h3><div class="price">R 300,00</div>
        <ul><li>Complete Wash</li><li>Full Interior Detailing</li><li>Tire Shine</li><li>Leather Conditioning</li><li>Paint / Wax Protection</li></ul>
      </div>
      <div class="package" data-aos="fade-up" data-aos-delay="200">
        <h3>The Ark</h3><div class="price">R 250,00</div>
        <ul><li>Basic Exterior Wash</li><li>Interior Vacuuming</li><li>Window Cleaning</li><li>Paint Protection</li><li>Tire Shine</li></ul>
      </div>
      <div class="package" data-aos="fade-up" data-aos-delay="300">
        <h3>Engine Detailing</h3><div class="price">R 150,00</div>
        <ul><li>Removes Dirt and Grease Build‑up</li><li>Enhances Performance and Aesthetics</li></ul>
      </div>
      <div class="package" data-aos="fade-up" data-aos-delay="400">
        <h3>Washes</h3><div class="price">R 150,00</div>
        <ul><li>Wash / Dry Exterior</li><li>Interior Cleaning</li></ul>
      </div>
    </div>
  </section>

  <section id="gallery">
    <h2>Gallery</h2>
    <div class="grid">
      <img src="https://via.placeholder.com/400x300?text=Image+1" alt="Car 1" data-aos="zoom-in" />
      <img src="https://via.placeholder.com/400x300?text=Image+2" alt="Car 2" data-aos="zoom-in" />
      <img src="https://via.placeholder.com/400x300?text=Image+3" alt="Car 3" data-aos="zoom-in" />
      <img src="https://via.placeholder.com/400x300?text=Image+4" alt="Car 4" data-aos="zoom-in" />
    </div>
  </section>

  <section id="testimonials">
    <h2>Testimonials</h2>
    <div class="testimonial" data-aos="fade-up" data-aos-delay="100">
      "Driveway Detailing gave my car the ultimate shine! Highly professional and trustworthy service."
      <div class="author">– Sarah M.</div>
    </div>
    <div class="testimonial" data-aos="fade-up" data-aos-delay="200">
      "Quick, affordable, and the results exceeded my expectations. My car looks brand new!"
      <div class="author">– Johan P.</div>
    </div>
  </section>

  <section id="contact">
    <h2>Contact Us</h2>
    <p><strong>Phone:</strong> <a href="tel:+27660642112">+27 66 064 2112</a></p>
    <p><strong>Email:</strong> <a href="mailto:ddmobilecarwash24@gmail.com">ddmobilecarwash24@gmail.com</a></p>
    <p><strong>Instagram:</strong> <a href="https://www.instagram.com/driveway_detailing/" target="blank">@_driveway_detailing</a></p>
    <p><strong>Operating Area:</strong> Paarl / Wellington, South Africa</p>
  </section>

  <footer>&copy; 2025 Driveway Detailing — All rights reserved.</footer>

  <div class="floating-contact">
    <a href="https://wa.me/27660642112" target="_blank" class="whatsapp-btn"><i class="fab fa-whatsapp"></i></a>
    <a href="https://www.instagram.com/driveway_detailing/" target="_blank" class="instagram-btn"><i class="fab fa-instagram"></i></a>
  </div>

  <script src="https://cdn.jsdelivr.net/npm/aos@2.3.4/dist/aos.js"></script>
  <script>
    AOS.init({ duration: 800, once: true });
    const nav = document.getElementById('navbar'), anchors = nav.querySelectorAll('ul li a');
    window.addEventListener('scroll', () => {
      nav.classList.toggle('scrolled', window.scrollY > 50);
      let current = '';
      document.querySelectorAll('section, header').forEach(s => {
        if (window.scrollY >= s.offsetTop - 80) current = s.id || 'hero';
      });
      anchors.forEach(a => {
        a.classList.toggle('active', a.getAttribute('href').slice(1) === current);
      });
    });
    function toggleMenu(){ nav.classList.toggle('active'); }
    anchors.forEach(a => a.addEventListener('click', e => {
      e.preventDefault();
      document.getElementById(a.getAttribute('href').slice(1)).scrollIntoView({ behavior: 'smooth' });
      nav.classList.remove('active');
    }));
  </script>
</body>
</html>
