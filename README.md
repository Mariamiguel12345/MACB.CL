[index.html.html](https://github.com/user-attachments/files/33013458/index.html.html)
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Gente Grande — Ayuda a personas mayores</title>
<link href="https://fonts.googleapis.com/css2?family=Lora:wght@400;600&family=Inter:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
  :root {
    --verde:      #2D6A4F;
    --verde-claro:#52B788;
    --crema:      #FDF6EC;
    --dorado:     #C68642;
    --gris-texto: #3A3A3A;
    --gris-suave: #F0EBE3;
  }
  html { scroll-behavior: smooth; }
  body { font-family: 'Inter', sans-serif; background: var(--crema); color: var(--gris-texto); font-size: 18px; line-height: 1.7; }

  /* HEADER */
  header { background: var(--verde); padding: 18px 40px; display: flex; align-items: center; justify-content: space-between; position: sticky; top: 0; z-index: 100; }
  .logo { font-family: 'Lora', serif; font-size: 1.5rem; font-weight: 600; color: #fff; }
  .logo span { color: var(--verde-claro); }
  nav a { color: rgba(255,255,255,0.85); text-decoration: none; font-size: 0.95rem; margin-left: 28px; transition: color .2s; }
  nav a:hover { color: #fff; }

  /* HERO con VIDEO */
  .hero {
    position: relative;
    min-height: 92vh;
    display: flex;
    align-items: center;
    justify-content: center;
    text-align: center;
    overflow: hidden;
    color: #fff;
  }
  .hero-video {
    position: absolute; inset: 0;
    width: 100%; height: 100%;
    object-fit: cover;
    z-index: 0;
  }
  .hero-overlay {
    position: absolute; inset: 0;
    background: linear-gradient(to bottom, rgba(20,60,40,0.72) 0%, rgba(20,60,40,0.55) 60%, rgba(20,60,40,0.8) 100%);
    z-index: 1;
  }
  .hero-content { position: relative; z-index: 2; padding: 60px 24px; max-width: 760px; }
  .hero-badge {
    display: inline-block;
    background: rgba(82,183,136,0.25);
    border: 1px solid rgba(82,183,136,0.5);
    color: #A8EDCA;
    font-size: 0.82rem;
    font-weight: 500;
    letter-spacing: 0.08em;
    padding: 6px 18px;
    border-radius: 50px;
    margin-bottom: 24px;
    text-transform: uppercase;
  }
  .hero h1 { font-family: 'Lora', serif; font-size: clamp(2.2rem, 5vw, 3.6rem); font-weight: 600; line-height: 1.2; margin-bottom: 22px; }
  .hero h1 em { font-style: normal; color: var(--verde-claro); }
  .hero p { font-size: 1.15rem; font-weight: 300; color: rgba(255,255,255,0.9); max-width: 560px; margin: 0 auto 36px; }
  .btn-hero { display: inline-block; background: var(--dorado); color: #fff; font-size: 1.05rem; font-weight: 500; padding: 16px 44px; border-radius: 50px; text-decoration: none; transition: background .2s, transform .15s; }
  .btn-hero:hover { background: #b07530; transform: translateY(-2px); }

  /* SECCIÓN FOTOS - galería */
  .galeria {
    padding: 72px 40px;
    background: #fff;
  }
  .galeria h2 { font-family: 'Lora', serif; font-size: clamp(1.6rem, 3vw, 2.2rem); font-weight: 600; color: var(--verde); text-align: center; margin-bottom: 10px; }
  .galeria .subtitulo { text-align: center; color: #666; font-size: 1rem; margin-bottom: 40px; }
  .fotos-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 16px;
    max-width: 1000px;
    margin: 0 auto;
  }
  .foto-card { position: relative; border-radius: 16px; overflow: hidden; aspect-ratio: 4/3; }
  .foto-card img { width: 100%; height: 100%; object-fit: cover; display: block; transition: transform .4s ease; }
  .foto-card:hover img { transform: scale(1.04); }
  .foto-card .foto-caption {
    position: absolute; bottom: 0; left: 0; right: 0;
    background: linear-gradient(to top, rgba(20,60,40,0.85), transparent);
    color: #fff;
    padding: 24px 16px 14px;
    font-size: 0.85rem;
    font-weight: 500;
  }
  /* foto grande a la izquierda */
  .foto-card.grande { grid-row: span 2; aspect-ratio: auto; }
  .foto-card.grande img { height: 100%; }

  /* QUÉ HACEMOS */
  .que-hacemos { padding: 80px 40px; max-width: 960px; margin: 0 auto; }
  .que-hacemos h2 { font-family: 'Lora', serif; font-size: clamp(1.6rem, 3vw, 2.2rem); font-weight: 600; color: var(--verde); text-align: center; margin-bottom: 10px; }
  .que-hacemos .subtitulo { text-align: center; color: #666; font-size: 1rem; margin-bottom: 44px; }
  .servicios { display: grid; grid-template-columns: repeat(auto-fit, minmax(210px, 1fr)); gap: 24px; }
  .servicio-card { background: #fff; border-radius: 16px; padding: 30px 24px; border-top: 4px solid var(--verde-claro); box-shadow: 0 2px 12px rgba(0,0,0,0.06); }
  .servicio-card .icono { font-size: 2.2rem; margin-bottom: 14px; display: block; }
  .servicio-card h3 { font-family: 'Lora', serif; font-size: 1.05rem; font-weight: 600; color: var(--verde); margin-bottom: 8px; }
  .servicio-card p { font-size: 0.92rem; color: #666; line-height: 1.6; }

  /* SEPARADOR */
  .sep { height: 1px; background: linear-gradient(to right, transparent, var(--verde-claro), transparent); max-width: 600px; margin: 0 auto; }

  /* FRASE INSPIRADORA */
  .frase {
    background: var(--verde);
    padding: 60px 40px;
    text-align: center;
    color: #fff;
  }
  .frase blockquote {
    font-family: 'Lora', serif;
    font-size: clamp(1.3rem, 3vw, 1.9rem);
    font-weight: 400;
    font-style: italic;
    max-width: 700px;
    margin: 0 auto;
    line-height: 1.5;
    color: rgba(255,255,255,0.95);
  }
  .frase cite { display: block; margin-top: 18px; font-size: 0.9rem; font-style: normal; color: var(--verde-claro); font-weight: 500; }

  /* CONTACTO */
  .contacto { padding: 80px 40px; text-align: center; background: var(--gris-suave); }
  .contacto h2 { font-family: 'Lora', serif; font-size: clamp(1.6rem, 3vw, 2.2rem); font-weight: 600; color: var(--verde); margin-bottom: 14px; }
  .contacto p { color: #555; max-width: 520px; margin: 0 auto 36px; }
  .contacto-caja { display: inline-flex; align-items: center; gap: 16px; background: #fff; border: 2px solid var(--verde-claro); border-radius: 16px; padding: 28px 40px; flex-wrap: wrap; justify-content: center; }
  .contacto-caja .mail-icono { font-size: 2.5rem; }
  .contacto-caja .mail-info h3 { font-family: 'Lora', serif; font-size: 1rem; color: #888; font-weight: 400; margin-bottom: 4px; }
  .contacto-caja .mail-info a { font-size: 1.25rem; font-weight: 500; color: var(--verde); text-decoration: none; word-break: break-all; }
  .contacto-caja .mail-info a:hover { color: var(--dorado); text-decoration: underline; }
  .btn-mail { display: inline-block; margin-top: 28px; background: var(--verde); color: #fff; font-size: 1rem; font-weight: 500; padding: 14px 36px; border-radius: 50px; text-decoration: none; transition: background .2s; }
  .btn-mail:hover { background: #1e4d38; }

  /* FOOTER */
  footer { background: var(--verde); color: rgba(255,255,255,0.7); text-align: center; padding: 28px 20px; font-size: 0.88rem; }
  footer strong { color: #fff; }
  footer a { color: var(--verde-claro); text-decoration: none; }

  /* RESPONSIVE */
  @media (max-width: 700px) {
    header { padding: 14px 20px; }
    .galeria, .que-hacemos, .contacto { padding: 52px 20px; }
    .fotos-grid { grid-template-columns: 1fr 1fr; }
    .foto-card.grande { grid-row: span 1; aspect-ratio: 4/3; }
    .servicios { grid-template-columns: 1fr; }
    .contacto-caja { padding: 20px; }
    nav { display: none; }
  }
</style>
</head>
<body>

<!-- HEADER -->
<header>
  <div class="logo">Gente <span>Grande</span></div>
  <nav>
    <a href="#nosotros">Nosotros</a>
    <a href="#servicios">Servicios</a>
    <a href="#contacto">Contacto</a>
  </nav>
</header>

<!-- HERO CON VIDEO -->
<section class="hero">
  <!-- Video de Pexels (libre de derechos) — adultos mayores activos y felices -->
  <video class="hero-video" autoplay muted loop playsinline
    poster="https://images.unsplash.com/photo-1573496359142-b8d87734a5a2?w=1400&q=80">
    <source src="https://videos.pexels.com/video-files/3121459/3121459-uhd_2560_1440_25fps.mp4" type="video/mp4">
  </video>
  <div class="hero-overlay"></div>
  <div class="hero-content">
    <div class="hero-badge">🌿 Cuidamos a quienes más queremos</div>
    <h1>Acompañamos y cuidamos a la <em>Gente Grande</em></h1>
    <p>Porque envejecer con dignidad, alegría y compañía es un derecho de todas las personas.</p>
    <a href="#contacto" class="btn-hero">Contáctanos hoy</a>
  </div>
</section>

<!-- GALERÍA DE FOTOS -->
<section class="galeria" id="nosotros">
  <h2>Una vida plena a cualquier edad</h2>
  <p class="subtitulo">Creemos que la etapa de la vida más rica merece el mejor acompañamiento.</p>

  <div class="fotos-grid">

    <!-- Foto grande izquierda -->
    <div class="foto-card grande">
      <img src="https://images.unsplash.com/photo-1576765608622-067973a79f53?w=800&q=80"
           alt="Adulta mayor sonriendo feliz con su familia" loading="lazy">
      <div class="foto-caption">Momentos que importan</div>
    </div>

    <!-- Fila derecha, foto arriba -->
    <div class="foto-card">
      <img src="https://images.unsplash.com/photo-1543342384-1f1350e27861?w=700&q=80"
           alt="Abuela abrazando a su nieto con amor" loading="lazy">
      <div class="foto-caption">Vínculos que permanecen</div>
    </div>

    <!-- Fila derecha, foto abajo -->
    <div class="foto-card">
      <img src="https://images.unsplash.com/photo-1498503182468-3b51cbb6cb24?w=700&q=80"
           alt="Personas mayores caminando y disfrutando al aire libre" loading="lazy">
      <div class="foto-caption">Actividad y bienestar</div>
    </div>

    <!-- Fila inferior completa - 3 fotos -->
    <div class="foto-card">
      <img src="https://images.unsplash.com/photo-1556742031-c6961e8560b0?w=700&q=80"
           alt="Persona mayor recibiendo apoyo y compañía" loading="lazy">
      <div class="foto-caption">Apoyo presente</div>
    </div>

    <div class="foto-card">
      <img src="https://images.unsplash.com/photo-1516307365426-bea591f05011?w=700&q=80"
           alt="Adulto mayor leyendo tranquilo en casa" loading="lazy">
      <div class="foto-caption">Tranquilidad en el hogar</div>
    </div>

    <div class="foto-card">
      <img src="https://images.unsplash.com/photo-1559839734-2b71ea197ec2?w=700&q=80"
           alt="Familia reunida con abuelos en un almuerzo" loading="lazy">
      <div class="foto-caption">Familia unida</div>
    </div>

  </div>
</section>

<!-- QUÉ HACEMOS -->
<section class="que-hacemos" id="servicios">
  <h2>¿En qué ayudamos?</h2>
  <p class="subtitulo">Acompañamos a personas mayores y a sus familias en los momentos que más importan.</p>
  <div class="servicios">
    <div class="servicio-card">
      <span class="icono">🏠</span>
      <h3>Acompañamiento en el hogar</h3>
      <p>Presencia, compañía y ayuda cotidiana para que cada día sea mejor.</p>
    </div>
    <div class="servicio-card">
      <span class="icono">📋</span>
      <h3>Orientación y trámites</h3>
      <p>Ayudamos con gestiones, documentos y trámites para facilitar la vida diaria.</p>
    </div>
    <div class="servicio-card">
      <span class="icono">💬</span>
      <h3>Escucha y apoyo</h3>
      <p>A veces lo más importante es tener con quién hablar. Aquí estamos.</p>
    </div>
    <div class="servicio-card">
      <span class="icono">👨‍👩‍👧</span>
      <h3>Apoyo a las familias</h3>
      <p>Orientamos a quienes cuidan de un adulto mayor para que no estén solos.</p>
    </div>
  </div>
</section>

<div class="sep"></div>

<!-- FRASE -->
<section class="frase">
  <blockquote>
    "Cuidar a quien nos cuidó es el acto de amor más grande que podemos dar."
    <cite>— Gente Grande</cite>
  </blockquote>
</section>

<!-- CONTACTO -->
<section class="contacto" id="contacto">
  <h2>¿Quieres comunicarte con nosotros?</h2>
  <p>Si necesitas ayuda o quieres saber más sobre lo que hacemos, escríbenos y te respondemos a la brevedad.</p>
  <div class="contacto-caja">
    <span class="mail-icono">✉️</span>
    <div class="mail-info">
      <h3>Correo de contacto</h3>
      <a href="mailto:miguel.collio@gmail.com">miguel.collio@gmail.com</a>
    </div>
  </div>
  <br>
  <a href="mailto:miguel.collio@gmail.com" class="btn-mail">Enviar un correo</a>
</section>

<!-- FOOTER -->
<footer>
  <p><strong>Gente Grande</strong> — Ayuda a personas de la tercera edad · Chile</p>
  <p style="margin-top:6px;">Contacto: <a href="mailto:miguel.collio@gmail.com">miguel.collio@gmail.com</a></p>
  <p style="margin-top:10px; font-size:0.78rem; opacity:0.6;">Fotos: Unsplash · Video: Pexels · Uso libre sin atribución comercial requerida</p>
</footer>

</body>
</html>
