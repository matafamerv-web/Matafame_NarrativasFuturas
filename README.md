<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="description" content="Portfolio audiovisual y musical de Matafame.">
<title>Matafame — Portfolio audiovisual</title>
<style>
:root {
  --background:#f5f4f0; --foreground:#171717; --muted:#777770;
  --line:#d9d8d1; --accent:#d5ff45; --max-width:1400px;
  --page-padding:clamp(20px,5vw,72px);
}
*{box-sizing:border-box}
html{scroll-behavior:smooth;scroll-padding-top:90px}
body{margin:0;background:var(--background);color:var(--foreground);font-family:Arial,Helvetica,sans-serif;font-size:16px;line-height:1.5;-webkit-font-smoothing:antialiased}
img,video,iframe{display:block;max-width:100%}
a{color:inherit;text-decoration:none}
a:hover{opacity:.65}
.container{width:min(100% - (var(--page-padding)*2),var(--max-width));margin-inline:auto}
.eyebrow{margin:0 0 12px;color:var(--muted);font-size:11px;font-weight:700;letter-spacing:.12em;text-transform:uppercase}
.section{padding-block:clamp(48px,7vw,92px);border-top:1px solid var(--line)}
.section-heading{display:flex;justify-content:space-between;align-items:end;gap:24px;margin-bottom:32px}
.section-heading h2{margin:0;font-size:clamp(30px,4vw,56px);font-weight:500;line-height:1;letter-spacing:-.055em}
.section-heading p{max-width:360px;margin:0;color:var(--muted);font-size:13px}
.site-header{position:sticky;top:0;z-index:10;background:rgba(245,244,240,.94);border-bottom:1px solid var(--line);backdrop-filter:blur(12px)}
.nav{min-height:68px;display:flex;align-items:center;justify-content:space-between;gap:24px}
.logo{font-size:20px;font-weight:800;letter-spacing:-.07em}
.nav-links{display:flex;flex-wrap:wrap;justify-content:flex-end;gap:clamp(12px,2.5vw,32px);font-size:12px}
.hero{min-height:min(650px,75vh);display:flex;align-items:end;padding-block:80px 64px}
.hero-content{width:100%}
.hero h1{max-width:1100px;margin:0;font-size:clamp(64px,14vw,190px);line-height:.78;letter-spacing:-.095em;font-weight:700;overflow-wrap:anywhere}
.hero-bottom{display:flex;align-items:end;justify-content:space-between;gap:30px;margin-top:40px}
.hero-description{max-width:420px;margin:0;font-size:clamp(16px,2vw,23px);line-height:1.3}
.hero-note{color:var(--muted);font-size:12px;text-align:right}
.featured-video,.video-frame{position:relative;width:100%;aspect-ratio:16/9;overflow:hidden;background:#deded7}
.featured-video iframe,.video-frame iframe{width:100%;height:100%;border:0}
.video-caption{display:flex;justify-content:space-between;gap:20px;padding-top:14px;font-size:13px}
.video-caption span:last-child{color:var(--muted);text-align:right}
.project-grid{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:42px 24px}

/* Carrusel unificado de Narrativas Futuras — integrado con el sistema visual */
.narrativas-gallery-wrap{position:relative;margin-bottom:0}
.narrativas-gallery{display:grid;grid-auto-flow:column;grid-auto-columns:100%;gap:0;overflow-x:auto;scroll-snap-type:x mandatory;scroll-behavior:smooth;scrollbar-width:none;padding:0;border:1px solid var(--line);background:#deded7}
.narrativas-gallery::-webkit-scrollbar{display:none}
.narrativas-slide{margin:0;min-width:0;overflow:hidden;background:#deded7;aspect-ratio:16/9;scroll-snap-align:start;position:relative}
.narrativas-photo-slide img{width:100%;height:100%;object-fit:contain;object-position:center;cursor:zoom-in;transition:transform .3s ease}
.narrativas-photo-slide img:hover{transform:scale(1.015)}
.narrativas-video-slide .video-frame{width:100%;height:100%;aspect-ratio:auto;background:#deded7}
.narrativas-video-slide .video-frame iframe{width:100%;height:100%;border:0}
.narrativas-gallery-caption{display:none;justify-content:space-between;align-items:baseline;gap:12px;margin:0 0 10px;color:var(--muted);font-size:11px}
.narrativas-gallery-caption span:first-child{color:var(--foreground);font-weight:600}
.narrativas-gallery-controls{display:flex;align-items:center;gap:12px;margin-top:12px;padding-bottom:2px}
.narrativas-gallery-controls button{display:grid;place-items:center;flex:0 0 32px;width:32px;height:32px;border:1px solid var(--line);border-radius:50%;background:transparent;color:var(--foreground);font-size:16px;line-height:1;cursor:pointer;transition:background .2s ease,border-color .2s ease}
.narrativas-gallery-controls button:hover{background:var(--accent);border-color:var(--foreground)}
.narrativas-gallery-controls input{flex:1;min-width:0;accent-color:var(--foreground);cursor:pointer}
.narrativas-gallery-count{min-width:34px;text-align:right;font-size:10px;color:var(--muted);white-space:nowrap}
.narrativas-gallery-wrap + .project-info{padding-top:12px}
.photo-lightbox{position:fixed;inset:0;z-index:100;display:none;align-items:center;justify-content:center;padding:24px;background:rgba(0,0,0,.9)}
.photo-lightbox.is-open{display:flex}
.photo-lightbox img{max-width:min(1100px,100%);max-height:85vh;object-fit:contain}
.photo-lightbox button{position:absolute;top:18px;right:22px;border:1px solid rgba(255,255,255,.6);border-radius:50%;width:42px;height:42px;background:transparent;color:white;font-size:25px;cursor:pointer}
@media(max-width:700px){
  .narrativas-gallery-caption{margin-bottom:8px}
  .narrativas-gallery-controls{gap:8px;margin-top:9px}
  .narrativas-gallery-controls button{flex-basis:30px;width:30px;height:30px}
  .narrativas-gallery-count{min-width:30px;font-size:9px}
}

.project-card{min-width:0}
.project-info{display:flex;justify-content:space-between;align-items:start;gap:16px;padding-top:12px}
.project-info h3{margin:0;font-size:clamp(17px,2vw,24px);font-weight:500;letter-spacing:-.035em}
.project-info p{margin:4px 0 0;color:var(--muted);font-size:12px}
.project-year{flex-shrink:0;color:var(--muted);font-size:12px}
.music-subsection+.music-subsection{margin-top:64px}
.subheading{display:flex;align-items:baseline;justify-content:space-between;gap:20px;margin-bottom:20px;padding-bottom:12px;border-bottom:1px solid var(--line)}
.subheading h3{margin:0;font-size:23px;font-weight:500;letter-spacing:-.04em}
.subheading span{color:var(--muted);font-size:12px}
.music-grid{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:14px}
.music-item{min-width:0;padding:20px;border:1px solid var(--line);background:rgba(255,255,255,.18)}
.music-item h4{margin:0;font-size:19px;font-weight:500;letter-spacing:-.035em}
.music-item .music-meta{margin:4px 0 18px;color:var(--muted);font-size:12px}
.music-item audio{display:block;width:100%;height:38px}
.music-link{display:inline-block;margin-top:14px;font-size:12px;text-decoration:underline;text-underline-offset:4px}
.bio-grid{display:grid;grid-template-columns:1fr 2fr;gap:48px}
.bio-title{margin:0;font-size:13px;font-weight:700;letter-spacing:.08em;text-transform:uppercase}
.bio-text{max-width:820px}
.bio-text p{margin:0 0 18px;font-size:clamp(18px,2.4vw,28px);line-height:1.35;letter-spacing:-.035em}
.bio-text p:last-child{margin-bottom:0}
.contact-section{padding-block:72px;background:var(--accent)}
.contact-section h2{max-width:900px;margin:0 0 28px;font-size:clamp(44px,9vw,110px);line-height:.9;letter-spacing:-.075em;font-weight:600}
.contact-links{display:flex;flex-wrap:wrap;gap:12px 28px;font-size:14px}
.contact-links a{text-decoration:underline;text-underline-offset:4px}
.site-footer{padding-block:20px;background:var(--foreground);color:var(--background)}
.footer-inner{display:flex;justify-content:space-between;gap:20px;font-size:11px}
.footer-inner p{margin:0}
/* Carpetas de álbumes */
.album-list{border-top:1px solid var(--line)}
.album-folder{border-bottom:1px solid var(--line)}
.album-folder summary{display:flex;align-items:center;gap:18px;padding:20px 4px;cursor:pointer;list-style:none}
.album-folder summary::-webkit-details-marker{display:none}
.folder-number{color:var(--muted);font-size:12px;min-width:24px}
.folder-title{display:flex;flex:1;min-width:0;flex-direction:column;gap:3px}
.folder-title strong{font-size:clamp(16px,2vw,22px);font-weight:500;letter-spacing:-.035em}
.folder-title small,.folder-count{color:var(--muted);font-size:11px}
.folder-count{white-space:nowrap}
.folder-icon{display:grid;width:28px;height:28px;place-items:center;border:1px solid var(--line);border-radius:50%;font-size:18px;transition:transform .2s ease}
.album-folder[open] .folder-icon{transform:rotate(45deg)}
.album-tracks{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:0 32px;padding:0 4px 24px 42px}
.track{display:flex;align-items:flex-start;gap:12px;min-width:0;padding:12px 0;border-top:1px solid var(--line)}
.track>span{padding-top:3px;color:var(--muted);font-size:11px}
.track-info{flex:1;min-width:0}
.track-info strong{display:block;margin-bottom:8px;font-size:13px;font-weight:500}
.track-info audio{display:block;width:100%;max-width:100%;height:34px}

/* Carrusel horizontal de bandas con deslizador */
.band-carousel { display:grid; grid-template-columns:40px minmax(0,1fr) 40px; align-items:center; gap:12px; }
.band-track { display:grid; grid-auto-flow:column; grid-auto-columns:calc((100% - 24px)/2); gap:24px; overflow-x:auto; scroll-snap-type:x mandatory; scroll-behavior:smooth; scrollbar-width:none; padding:2px 1px 12px; }
.band-track::-webkit-scrollbar { display:none; }
.band-card { scroll-snap-align:start; min-width:0; }
.band-arrow { width:40px; height:40px; border:1px solid var(--line); border-radius:50%; background:transparent; color:var(--foreground); font-size:20px; cursor:pointer; }
.band-arrow:hover { background:var(--accent); opacity:1; }
.band-slider-row { display:flex; align-items:center; gap:20px; margin-top:18px; }
.band-slider-label { color:var(--muted); font-size:11px; white-space:nowrap; }
.band-slider-row input { width:100%; accent-color:var(--foreground); cursor:pointer; }

/* Variante compacta para las carpetas y sus reproductores */
.album-folder summary { padding: 13px 4px; gap: 12px; }
.folder-title strong { font-size: 16px; }
.folder-title small, .folder-count { font-size: 10px; }
.folder-icon { width: 24px; height: 24px; font-size: 15px; }
.album-tracks { padding-bottom: 12px; gap: 0 20px; }
.track { padding: 7px 0; gap: 8px; }
.track-info strong { margin-bottom: 4px; font-size: 12px; }
.track-info audio { height: 30px; }

@media(max-width:700px){
  .band-carousel { grid-template-columns:30px minmax(0,1fr) 30px; gap:6px; }
  .band-arrow { width:30px; height:30px; font-size:16px; }
  .band-track { grid-auto-columns:100%; gap:16px; }
  .band-slider-row { gap:12px; }

  :root{--page-padding:20px}
  .nav{min-height:60px;align-items:flex-start;flex-direction:column;justify-content:center;gap:8px;padding-block:12px}
  .nav-links{justify-content:flex-start;gap:8px 16px;font-size:11px}
  .hero{min-height:55vh;padding-block:68px 42px}
  .hero h1{font-size:clamp(58px,18vw,110px)}
  .hero-bottom{align-items:flex-start;flex-direction:column;gap:16px;margin-top:28px}
  .hero-note{text-align:left}
  .section-heading{align-items:flex-start;flex-direction:column;gap:12px;margin-bottom:24px}
  .project-grid,.music-grid{grid-template-columns:1fr;gap:28px}
  .music-subsection+.music-subsection{margin-top:42px}
  .bio-grid{grid-template-columns:1fr;gap:22px}
  .contact-section{padding-block:52px}
  .footer-inner{flex-direction:column;gap:6px}
  .video-caption{flex-direction:column;gap:4px}
  .video-caption span:last-child{text-align:left}
  .album-folder summary{gap:10px;padding-block:16px}
  .folder-count{font-size:10px}
  .album-tracks{grid-template-columns:1fr;padding-left:8px;padding-right:8px}
}
</style>
</head>
<body>
<header class="site-header">
  <div class="container nav">
    <a class="logo" href="#inicio">&nbsp;</a>
    <nav class="nav-links" aria-label="Navegación principal">
      <a href="#audiovisual">&nbsp; Audiovisual</a><a href="#bandas">Bandas</a><a href="#musica">Música</a><a href="#bio">Bio</a><a href="#contacto">Contacto</a>
    </nav>
  </div>
</header>
<main>
  <section class="hero container" id="inicio">
    <div class="hero-content">
      <p class="eyebrow">Portfolio · Audiovisual · Música</p>
      <h1>MATA&nbsp; FAME</h1>
      <div class="hero-bottom">
        <p class="hero-description">Práctica artística y producción audiovisual desde una perspectiva multidisciplinar.</p>
        <div class="hero-note"><div>Galicia, España</div><div>Dirección · Imagen · Sonido</div></div>
      </div>
    </div>
  </section>

  <section class="section" id="destacado">
    <div class="container">
      <div class="section-heading"><h2>Destacado</h2><p>Una selección de trabajos audiovisuales y proyectos recientes.</p></div>
      <div class="featured-video"><iframe src="https://www.youtube.com/embed/VIDEO_ID" title="Proyecto audiovisual destacado" loading="lazy" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe></div>
      <div class="video-caption"><span>Proyecto audiovisual destacado</span><span>Vídeo · Dirección · Producción</span></div>
    </div>
  </section>

  <section class="section" id="audiovisual">
    <div class="container">
      <div class="section-heading"><h2>Arte e Audiovisual&nbsp;</h2>
      <p>Archivo de obras, piezas y proyectos desarrollados en distintos contextos.</p></div>
      <div class="project-grid">
        <article class="project-card"><div class="video-frame"><iframe src="https://www.youtube.com/embed/3QeXXPd2_Zs?si=nd-8XJZstZra4yXF" title="Lobes Salvaxes" loading="lazy" allowfullscreen></iframe></div><div class="project-info"><div><h3>Lobes Salvaxes</h3><p>Proyecto audiovisual</p></div><span class="project-year">2025</span></div></article>
        <article class="project-card">
          <div class="narrativas-gallery-wrap">
            <div class="narrativas-gallery-caption"><span>Narrativas Futuras</span><span>Fotografías · Vídeo · 2025</span></div>
            <div class="narrativas-gallery" id="narrativas-gallery" aria-label="Galería y vídeo de Narrativas Futuras">
              <!-- Para añadir fotos, duplica una slide de foto y cambia la ruta FOTO_NARRATIVAS_XX.jpg. -->
              <figure class="narrativas-slide narrativas-photo-slide"><img src="https://github.com/matafamerv-web/Matafame/blob/main/Matafame=Youtube.png?raw=true" alt="Narrativas Futuras — fotografía 1" loading="lazy" data-lightbox></figure>
              <figure class="narrativas-slide narrativas-photo-slide"><img src="FOTO_NARRATIVAS_02.jpg" alt="Narrativas Futuras — fotografía 2" loading="lazy" data-lightbox></figure>
              <figure class="narrativas-slide narrativas-photo-slide"><img src="FOTO_NARRATIVAS_03.jpg" alt="Narrativas Futuras — fotografía 3" loading="lazy" data-lightbox></figure>
              <figure class="narrativas-slide narrativas-photo-slide"><img src="FOTO_NARRATIVAS_04.jpg" alt="Narrativas Futuras — fotografía 4" loading="lazy" data-lightbox></figure>
              <div class="narrativas-slide narrativas-video-slide">
                <div class="video-frame"><iframe src="https://www.youtube.com/embed/VIDEO_NARRATIVAS" title="Narrativas Futuras" loading="lazy" allowfullscreen></iframe></div>
              </div>
            </div>
            <div class="narrativas-gallery-controls">
              <button type="button" id="narrativas-prev" aria-label="Elemento anterior">←</button>
              <input type="range" id="narrativas-slider" min="0" max="4" value="0" step="1" aria-label="Desplazarse por fotos y vídeo de Narrativas Futuras">
              <button type="button" id="narrativas-next" aria-label="Elemento siguiente">→</button>
              <span class="narrativas-gallery-count" id="narrativas-count">1 / 5</span>
            </div>
          </div>
          <div class="project-info"><div><h3>Narrativas Futuras</h3><p>Proyecto audiovisual</p></div><span class="project-year">2025</span></div>
        </article>
        <article class="project-card"><div class="video-frame"><iframe src="https://www.youtube.com/embed/VIDEO_FURADA" title="Furada" loading="lazy" allowfullscreen></iframe></div><div class="project-info"><div><h3>Furada</h3><p>Proyecto audiovisual</p></div><span class="project-year">2023</span></div></article>
        <article class="project-card"><div class="video-frame"><iframe src="https://www.youtube.com/embed/VIDEO_ADIOS_MANUEL" title="Adiós Manuel" loading="lazy" allowfullscreen></iframe></div><div class="project-info"><div><h3>Adiós Manuel</h3><p>Proyecto audiovisual</p></div><span class="project-year">2022</span></div></article>
        <article class="project-card"><div class="video-frame"><iframe src="https://www.youtube.com/embed/VIDEO_MATAFAME" title="Matafame" loading="lazy" allowfullscreen></iframe></div><div class="project-info"><div><h3>Matafame</h3><p>Proyecto audiovisual</p></div><span class="project-year">2021</span></div></article>
        <article class="project-card"><div class="video-frame"><iframe src="https://www.youtube.com/embed/VIDEO_FILEBO" title="Filebo" loading="lazy" allowfullscreen></iframe></div><div class="project-info"><div><h3>Filebo</h3><p>Proyecto audiovisual</p></div><span class="project-year">2020</span></div></article>
      </div>
    </div>
  </section>

  <section class="section" id="bandas">
    <div class="container">
      <div class="section-heading"><h2>Bandas</h2><p>Proyectos musicales colectivos, directos y colaboraciones.</p></div>
      <div class="band-carousel">
        <button class="band-arrow band-prev" type="button" aria-label="Bandas anteriores">&#8592;</button>
        <div class="band-track" id="band-track">
          <article class="project-card band-card"><div class="video-frame"><iframe src="https://www.youtube.com/embed/VIDEO_BANDA_1" title="Banda 1" loading="lazy" allowfullscreen></iframe></div><div class="project-info"><div><h3>Nombre de la banda</h3><p>Directo / Videoclip / Sesión</p></div><span class="project-year">2025</span></div></article>
          <article class="project-card band-card"><div class="video-frame"><iframe src="https://www.youtube.com/embed/VIDEO_BANDA_2" title="Banda 2" loading="lazy" allowfullscreen></iframe></div><div class="project-info"><div><h3>Nombre de la banda</h3><p>Directo / Videoclip / Sesión</p></div><span class="project-year">2024</span></div></article>
          <article class="project-card band-card"><div class="video-frame"><iframe src="https://www.youtube.com/embed/VIDEO_BANDA_3" title="Banda 3" loading="lazy" allowfullscreen></iframe></div><div class="project-info"><div><h3>Nombre de la banda</h3><p>Directo / Videoclip / Sesión</p></div><span class="project-year">2023</span></div></article>
          <article class="project-card band-card"><div class="video-frame"><iframe src="https://www.youtube.com/embed/VIDEO_BANDA_4" title="Banda 4" loading="lazy" allowfullscreen></iframe></div><div class="project-info"><div><h3>Nombre de la banda</h3><p>Directo / Videoclip / Sesión</p></div><span class="project-year">2022</span></div></article>
          <article class="project-card band-card"><div class="video-frame"><iframe src="https://www.youtube.com/embed/VIDEO_BANDA_5" title="Banda 5" loading="lazy" allowfullscreen></iframe></div><div class="project-info"><div><h3>Nombre de la banda</h3><p>Directo / Videoclip / Sesión</p></div><span class="project-year">2021</span></div></article>
        </div>
        <button class="band-arrow band-next" type="button" aria-label="Ver más bandas">&#8594;</button>
      </div>
      <div class="band-slider-row">
        <span class="band-slider-label">Desliza para ver más</span>
        <input id="band-slider" type="range" min="0" max="4" value="0" step="1" aria-label="Seleccionar banda">
      </div>
    </div>
  </section>

  <section class="section" id="musica">
    <div class="container">
      <div class="section-heading"><h2>Música</h2><p>Ediciones, composiciones, grabaciones y exploraciones sonoras.</p></div>

      <div class="music-subsection" id="albumes">
        <div class="subheading"><h3>Álbumes</h3><span>01 — Ediciones · 5 carpetas</span></div>
        <div class="album-list" id="album-list"></div>
      </div>

      <div class="music-subsection" id="proyectos-musicales">
        <div class="subheading"><h3>Proyectos</h3><span>02 — Experimentos y colaboraciones</span></div>
        <div class="music-grid">
          <article class="music-item"><h4>Nombre del proyecto</h4><p class="music-meta">Proyecto sonoro · Año</p><audio controls preload="none"><source src="URL_PROYECTO_01.mp3" type="audio/mpeg">Tu navegador no permite reproducir este audio.</audio><a class="music-link" href="URL_PROYECTO_COMPLETO_1" target="_blank" rel="noopener">Más información ↗</a></article>
          <article class="music-item"><h4>Nombre del proyecto</h4><p class="music-meta">Colaboración · Año</p><audio controls preload="none"><source src="URL_PROYECTO_02.mp3" type="audio/mpeg">Tu navegador no permite reproducir este audio.</audio><a class="music-link" href="URL_PROYECTO_COMPLETO_2" target="_blank" rel="noopener">Más información ↗</a></article>
        </div>
      </div>
    </div>
  </section>

  <section class="section" id="bio">
    <div class="container bio-grid">
      <div><p class="eyebrow">Sobre el trabajo</p><h2 class="bio-title">Bio / Enfoque</h2></div>
      <div class="bio-text">
        <p>Desarrolla una práctica artística y audiovisual de carácter multidisciplinar, vinculada a proyectos autogestionados y a la exploración de diferentes lenguajes visuales y sonoros.</p>
        <p>Su trabajo combina música, imagen y experimentación para construir propuestas con una perspectiva artística propia, atendiendo tanto al proceso de creación como a las posibilidades de interacción con el contexto contemporáneo.</p>
        <p>Entre sus proyectos se encuentran Lobes Salvaxes, Narrativas Futuras, Furada, Adiós Manuel, Matafame y Filebo.</p>
      </div>
    </div>
  </section>

  <section class="contact-section" id="contacto">
    <div class="container">
      <p class="eyebrow">Contacto y colaboraciones</p><h2>Hablemos<br>de proyectos.</h2>
      <div class="contact-links"><a href="mailto:TU_EMAIL@EJEMPLO.COM">Email ↗</a><a href="URL_INSTAGRAM" target="_blank" rel="noopener">Instagram ↗</a><a href="URL_YOUTUBE" target="_blank" rel="noopener">YouTube ↗</a><a href="URL_BANDCAMP" target="_blank" rel="noopener">Bandcamp ↗</a></div>
    </div>
  </section>
</main>
<div class="photo-lightbox" id="photo-lightbox" role="dialog" aria-modal="true" aria-label="Fotografía ampliada">
  <button type="button" id="close-lightbox" aria-label="Cerrar fotografía">×</button>
  <img id="lightbox-image" src="" alt="">
</div>
<footer class="site-footer"><div class="container footer-inner"><p>© <span id="year"></span> Matafame</p><p>Portfolio audiovisual y musical</p></div></footer>

<script>
document.getElementById("year").textContent = new Date().getFullYear();

const narrativasGallery = document.getElementById("narrativas-gallery");
const narrativasSlider = document.getElementById("narrativas-slider");
const narrativasCount = document.getElementById("narrativas-count");
const narrativasSlides = narrativasGallery ? Array.from(narrativasGallery.querySelectorAll(".narrativas-slide")) : [];
function narrativasScrollTo(index) {
  if (!narrativasGallery || !narrativasSlides.length) return;
  const safeIndex = Math.max(0, Math.min(index, narrativasSlides.length - 1));
  narrativasGallery.scrollTo({
    left: narrativasSlides[safeIndex].offsetLeft - narrativasSlides[0].offsetLeft,
    behavior: "smooth"
  });
  if (narrativasSlider) narrativasSlider.value = String(safeIndex);
  if (narrativasCount) narrativasCount.textContent = `${safeIndex + 1} / ${narrativasSlides.length}`;
}
if (narrativasSlider) {
  narrativasSlider.max = String(Math.max(0, narrativasSlides.length - 1));
  narrativasSlider.addEventListener("input", event => narrativasScrollTo(Number(event.target.value)));
}
document.getElementById("narrativas-prev").addEventListener("click", () => narrativasScrollTo(Number(narrativasSlider.value) - 1));
document.getElementById("narrativas-next").addEventListener("click", () => narrativasScrollTo(Number(narrativasSlider.value) + 1));
if (narrativasGallery) {
  narrativasGallery.addEventListener("scroll", () => {
    const nearest = narrativasSlides.reduce((best, slide, index) => {
      const distance = Math.abs((slide.offsetLeft - narrativasSlides[0].offsetLeft) - narrativasGallery.scrollLeft);
      return distance < best.distance ? {index, distance} : best;
    }, {index: 0, distance: Infinity});
    if (narrativasSlider) narrativasSlider.value = String(nearest.index);
    if (narrativasCount) narrativasCount.textContent = `${nearest.index + 1} / ${narrativasSlides.length}`;
  });
}
document.querySelectorAll("[data-lightbox]").forEach(photo => {
  photo.addEventListener("click", () => {
    const lightbox = document.getElementById("photo-lightbox");
    const largePhoto = document.getElementById("lightbox-image");
    largePhoto.src = photo.src;
    largePhoto.alt = photo.alt;
    lightbox.classList.add("is-open");
  });
});
function closePhotoLightbox() {
  document.getElementById("photo-lightbox").classList.remove("is-open");
}
document.getElementById("close-lightbox").addEventListener("click", closePhotoLightbox);
document.getElementById("photo-lightbox").addEventListener("click", event => {
  if (event.target.id === "photo-lightbox") closePhotoLightbox();
});
document.addEventListener("keydown", event => {
  if (event.key === "Escape") closePhotoLightbox();
});


/* Genera 5 carpetas compactas, cada una con 10 pistas.
   Sustituye los nombres y las rutas de audio de ejemplo por los tuyos. */
const bandTrack = document.getElementById("band-track");
const bandSlider = document.getElementById("band-slider");
const bandCards = Array.from(document.querySelectorAll(".band-card"));
const bandPrev = document.querySelector(".band-prev");
const bandNext = document.querySelector(".band-next");

function bandScrollTo(index) {
  if (!bandTrack || !bandCards.length) return;
  const safeIndex = Math.max(0, Math.min(index, bandCards.length - 1));
  bandTrack.scrollTo({
    left: bandCards[safeIndex].offsetLeft - bandCards[0].offsetLeft,
    behavior: "smooth"
  });
  if (bandSlider) bandSlider.value = String(safeIndex);
}
if (bandSlider) bandSlider.addEventListener("input", event => bandScrollTo(Number(event.target.value)));
if (bandPrev) bandPrev.addEventListener("click", () => bandScrollTo(Number(bandSlider.value) - 1));
if (bandNext) bandNext.addEventListener("click", () => bandScrollTo(Number(bandSlider.value) + 1));
if (bandTrack && bandSlider) {
  bandTrack.addEventListener("scroll", () => {
    const firstLeft = bandCards[0].offsetLeft;
    const nearest = bandCards.reduce((best, card, index) => {
      const distance = Math.abs((card.offsetLeft - firstLeft) - bandTrack.scrollLeft);
      return distance < best.distance ? { index, distance } : best;
    }, { index: 0, distance: Infinity });
    bandSlider.value = String(nearest.index);
  });
}

const albumList = document.getElementById("album-list");
for (let album = 1; album <= 5; album++) {
  const albumNumber = String(album).padStart(2, "0");
  const folder = document.createElement("details");
  folder.className = "album-folder compact-folder";
  folder.innerHTML = `
    <summary>
      <span class="folder-number">${albumNumber}</span>
      <span class="folder-title">
        <strong>Álbum ${albumNumber}</strong>
        <small>Álbum · Año</small>
      </span>
      <span class="folder-count">10 pistas</span>
      <span class="folder-icon">+</span>
    </summary>
    <div class="album-tracks compact-tracks"></div>`;
  const tracks = folder.querySelector(".album-tracks");

  for (let track = 1; track <= 10; track++) {
    const trackNumber = String(track).padStart(2, "0");
    const item = document.createElement("div");
    item.className = "track compact-track";
    item.innerHTML = `
      <span>${trackNumber}</span>
      <div class="track-info">
        <strong>Pista ${trackNumber}</strong>
        <audio controls preload="none">
          <source src="ALBUM${albumNumber}_PISTA${trackNumber}.mp3" type="audio/mpeg">
          Tu navegador no permite reproducir este audio.
        </audio>
      </div>`;
    tracks.appendChild(item);
  }
  albumList.appendChild(folder);
}
</script>
</body>
</html># Matafame_NarrativasFuturas
