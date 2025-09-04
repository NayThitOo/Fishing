<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Fishing in Myanmar</title>
  <meta name="description" content="A simple, modern website about fishing in Myanmar: top regions, species, seasons, tips, and a photo gallery." />

  <!-- Fonts -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;600;700&display=swap" rel="stylesheet">

  <style>
    :root {
      --bg: #0f172a;           /* slate-900 */
      --panel: #0b1224;        /* deep navy */
      --muted: #94a3b8;        /* slate-400 */
      --text: #e2e8f0;         /* slate-200 */
      --brand: #08bdbd;        /* teal */
      --accent: #f59e0b;       /* amber */
      --ring: rgba(8, 189, 189, .35);
      --card: #0b1530;
      --card2: #0e1b3d;
    }
    * { box-sizing: border-box; }
    html, body { height: 100%; }
    body {
      margin: 0;
      font-family: "Outfit", system-ui, -apple-system, Segoe UI, Roboto, "Helvetica Neue", Arial, "Noto Sans", "Apple Color Emoji", "Segoe UI Emoji";
      color: var(--text);
      background: radial-gradient(1200px 800px at 80% -20%, #123 0%, transparent 60%),
                  radial-gradient(900px 600px at -20% 10%, #042 0%, transparent 60%),
                  linear-gradient(180deg, #071021 0%, #0a1226 100%);
    }
    a { color: inherit; text-decoration: none; }
    .container { width: min(1100px, 92%); margin: 0 auto; }

    /* Header */
    header {
      position: sticky; top: 0; z-index: 40;
      backdrop-filter: blur(10px);
      background: rgba(7, 16, 33, 0.6);
      border-bottom: 1px solid rgba(255,255,255,.06);
    }
    .nav { display:flex; align-items:center; justify-content:space-between; padding: 14px 0; }
    .brand { display:flex; align-items:center; gap: .65rem; font-weight:700; letter-spacing:.2px; }
    .brand .logo {
      width: 36px; height: 36px; border-radius: 14px;
      display:grid; place-items:center;
      background: linear-gradient(135deg, var(--brand), #0ea5a5 60%, #22d3ee);
      box-shadow: 0 10px 30px rgba(8, 189, 189, .25);
    }
    nav ul { display:flex; gap: 1.1rem; list-style: none; margin: 0; padding: 0; }
    nav a { opacity:.9; padding:.5rem .75rem; border-radius: 10px; transition: .2s ease; }
    nav a:hover { background: rgba(255,255,255,.06); opacity:1; }
    .cta { background: linear-gradient(135deg, var(--accent), #fbbf24); color: #0a0e1a; font-weight:700; padding:.55rem .9rem; border-radius:12px; box-shadow: 0 8px 24px rgba(245, 158, 11, .35); }

    /* Hero */
    .hero { position:relative; overflow:hidden; }
    .hero .wrap { display:grid; grid-template-columns: 1.1fr .9fr; gap: 2.2rem; align-items:center; padding: 64px 0 42px; }
    .eyebrow { font-size: .85rem; letter-spacing: .18em; text-transform: uppercase; color: var(--brand); }
    h1 { font-size: clamp(2rem, 1.2rem + 2.8vw, 3.25rem); line-height: 1.05; margin: .5rem 0 1rem; }
    .lead { color: var(--muted); font-size: clamp(1rem, .86rem + .6vw, 1.125rem); }
    .hero .actions { display:flex; gap: .8rem; margin-top: 1.2rem; flex-wrap: wrap; }
    .btn { display:inline-flex; align-items:center; gap:.5rem; padding:.8rem 1.05rem; border-radius: 12px; border:1px solid rgba(255,255,255,.08); background:#0c1834; cursor:pointer; transition:.2s; }
    .btn:hover { transform: translateY(-1px); border-color: rgba(255,255,255,.18); }
    .btn.primary { background: linear-gradient(135deg, var(--brand), #22d3ee); color:#06101d; font-weight:700; border: none; box-shadow:0 10px 30px rgba(34,211,238,.22); }

    .hero .card {
      background: radial-gradient(800px 400px at 70% -40%, rgba(34, 211, 238, .12), transparent 60%),
                  linear-gradient(180deg, var(--card) 0%, var(--card2) 100%);
      border: 1px solid rgba(255,255,255,.06);
      border-radius: 18px; overflow:hidden;
      box-shadow: 0 20px 60px rgba(0,0,0,.35);
    }
    .hero img { width: 100%; height: 100%; display:block; object-fit: cover; aspect-ratio: 4/3; }
    .hero .photo-caption { padding: .85rem 1rem; color: var(--muted); font-size:.9rem; border-top: 1px solid rgba(255,255,255,.06); }

    /* Sections */
    section { padding: 64px 0; }
    .section-title { font-size: clamp(1.4rem, 1.1rem + 1.2vw, 2rem); margin: 0 0 12px; }
    .section-lead { color: var(--muted); margin-bottom: 26px; }

    .grid { display:grid; gap: 1rem; }
    .grid.regions { grid-template-columns: repeat(auto-fit, minmax(230px, 1fr)); }
    .grid.species { grid-template-columns: repeat(auto-fit, minmax(180px, 1fr)); }
    .card2 { background: linear-gradient(180deg, rgba(255,255,255,.03), rgba(255,255,255,.01)); border:1px solid rgba(255,255,255,.06); padding: 16px; border-radius: 16px; transition:.2s; }
    .card2:hover { transform: translateY(-2px); border-color: rgba(255,255,255,.12); }
    .card2 h3 { margin: .3rem 0 .35rem; font-size: 1.05rem; }
    .tag { display:inline-flex; gap:.4rem; align-items:center; background: rgba(8,189,189,.12); border:1px solid rgba(8,189,189,.25); color:#99f6e4; font-size:.8rem; padding:.2rem .5rem; border-radius: 999px; }
    .grid .thumb { width:100%; height:150px; border-radius:12px; object-fit:cover; border:1px solid rgba(255,255,255,.06); }

    /* Seasons */
    .seasons { display:grid; grid-template-columns: repeat(auto-fit, minmax(240px, 1fr)); gap: 1rem; }
    .season { background: linear-gradient(180deg, rgba(255,255,255,.03), rgba(255,255,255,.01)); border:1px solid rgba(255,255,255,.06); padding: 16px; border-radius: 16px; }
    .season ul { margin:.4rem 0 0; padding-left: 1.1rem; color: var(--muted); }

    /* Tips */
    .tips { display:grid; grid-template-columns: repeat(auto-fit, minmax(260px, 1fr)); gap: 1rem; }
    .tip { position: relative; padding: 16px 16px 16px 46px; border-radius: 16px; border:1px solid rgba(255,255,255,.06); background: linear-gradient(180deg, rgba(255,255,255,.03), rgba(255,255,255,.01)); }
    .tip svg { position:absolute; left: 14px; top: 18px; opacity:.9; }

    /* Gallery */
    .gallery { display:grid; grid-template-columns: repeat(auto-fit, minmax(180px, 1fr)); gap: .7rem; }
    .gallery img { width:100%; height:160px; object-fit:cover; border-radius:12px; border:1px solid rgba(255,255,255,.06); transition:.2s; }
    .gallery img:hover { transform: scale(1.02); }

    /* Contact */
    form { display:grid; gap:.8rem; }
    input, textarea {
      width:100%; padding:.9rem 1rem; border-radius:12px; border:1px solid rgba(255,255,255,.1); background:#0b1530; color:var(--text);
      outline: none; box-shadow: 0 0 0 0px var(--ring);
    }
    input:focus, textarea:focus { border-color: rgba(8,189,189,.45); box-shadow: 0 0 0 6px var(--ring); }
    textarea { min-height: 130px; resize: vertical; }

    /* Footer */
    footer { padding: 42px 0; color: var(--muted); border-top: 1px solid rgba(255,255,255,.06); }

    /* Back to top */
    #toTop { position: fixed; right: 16px; bottom: 16px; z-index: 50; opacity: 0; pointer-events: none; transition:.2s; }
    #toTop.show { opacity: 1; pointer-events: auto; }

    /* Responsive */
    @media (max-width: 900px) {
      .hero .wrap { grid-template-columns: 1fr; padding-top: 40px; }
    }
  </style>
</head>
<body>
  <header>
    <div class="container nav">
      <div class="brand">
        <div class="logo" aria-hidden="true">🎣</div>
        <a href="#top" aria-label="Fishing in Myanmar home">Fishing in Myanmar</a>
      </div>
      <nav aria-label="Primary">
        <ul>
          <li><a href="#regions">Regions</a></li>
          <li><a href="#species">Species</a></li>
          <li><a href="#seasons">Seasons</a></li>
          <li><a href="#tips">Tips</a></li>
          <li><a href="#gallery">Gallery</a></li>
          <li><a class="cta" href="#contact">Plan a Trip</a></li>
        </ul>
      </nav>
    </div>
  </header>

  <main id="top" class="container">
    <!-- Hero -->
    <section class="hero" aria-label="Intro">
      <div class="wrap">
        <div>
          <p class="eyebrow">Cast, Explore, Respect</p>
          <h1>Discover the joy of fishing across Myanmar’s lakes, rivers, and coast</h1>
          <p class="lead">From serene highland lakes to the mighty Ayeyarwady River and the Andaman Sea, Myanmar offers a range of waters for casual anglers and seasoned explorers alike.</p>
          <div class="actions">
            <a class="btn primary" href="#regions">Explore Regions</a>
            <a class="btn" href="#tips">Responsible Fishing</a>
          </div>
        </div>
        <figure class="card">
          <img src="https://images.unsplash.com/photo-1478479405421-ce83c92fb2c5?q=80&w=1600&auto=format&fit=crop" alt="Angler silhouetted on calm water at sunrise" />
          <figcaption class="photo-caption">Early light over still waters—perfect time to cast.</figcaption>
        </figure>
      </div>
    </section>

    <!-- Regions -->
    <section id="regions" aria-labelledby="regions-title">
      <h2 class="section-title" id="regions-title">Top Fishing Regions</h2>
      <p class="section-lead">A few well‑known destinations to inspire your next outing.</p>
      <div class="grid regions">
        <article class="card2">
          <img class="thumb" src="https://images.unsplash.com/photo-1545239351-1141bd82e8a6?q=80&w=1600&auto=format&fit=crop" alt="Stilt houses over a lake with boats" />
          <h3>Inle Lake (Shan State)</h3>
          <p class="muted">Tranquil high‑altitude waters, floating gardens, and traditional leg‑rowing fishermen.</p>
          <span class="tag" title="Freshwater">💧 Freshwater</span>
        </article>
        <article class="card2">
          <img class="thumb" src="https://images.unsplash.com/photo-1558980664-10bc8e8a0600?q=80&w=1600&auto=format&fit=crop" alt="Wide muddy river with boats" />
          <h3>Ayeyarwady River</h3>
          <p class="muted">Myanmar’s great river system with diverse habitats, channels, and tributaries.</p>
          <span class="tag" title="River">🌊 River</span>
        </article>
        <article class="card2">
          <img class="thumb" src="https://images.unsplash.com/photo-1500375592092-40eb2168fd21?q=80&w=1600&auto=format&fit=crop" alt="Tropical coastline with islands" />
          <h3>Tanintharyi Coast</h3>
          <p class="muted">Island‑dotted Andaman coastline with access to inshore and near‑shore species.</p>
          <span class="tag" title="Saltwater">🌴 Saltwater</span>
        </article>
        <article class="card2">
          <img class="thumb" src="https://images.unsplash.com/photo-1582719478250-c89cae4dc85b?q=80&w=1600&auto=format&fit=crop" alt="Green delta channels and mangroves" />
          <h3>Delta & Mangroves</h3>
          <p class="muted">Brackish backwaters and tidal creeks—great for patient, stealthy approaches.</p>
          <span class="tag" title="Brackish">🌿 Brackish</span>
        </article>
      </div>
    </section>

    <!-- Species -->
    <section id="species" aria-labelledby="species-title">
      <h2 class="section-title" id="species-title">Popular Species</h2>
      <p class="section-lead">A general, non‑exhaustive list you might encounter across Myanmar’s waters.</p>
      <div class="grid species">
        <article class="card2">
          <h3>Rohu (Labeo rohita)</h3>
          <p class="muted">Common carp family fish in lakes and slow rivers—responds to dough baits and maize.</p>
        </article>
        <article class="card2">
          <h3>Catfish (various)</h3>
          <p class="muted">Nocturnal feeders in deep holes and undercut banks—try live or cut bait.</p>
        </article>
        <article class="card2">
          <h3>Snakehead (Channa spp.)</h3>
          <p class="muted">Aggressive surface strikes in weedy margins; topwater lures can be exciting.</p>
        </article>
        <article class="card2">
          <h3>Barramundi (Lates calcarifer)</h3>
          <p class="muted">Brackish/saltwater ambush predator near mangroves and estuaries—soft plastics work well.</p>
        </article>
      </div>
    </section>

    <!-- Seasons -->
    <section id="seasons" aria-labelledby="seasons-title">
      <h2 class="section-title" id="seasons-title">Seasons at a Glance</h2>
      <p class="section-lead">Conditions vary by region; always check local weather and water levels before you go.</p>
      <div class="seasons">
        <div class="season">
          <h3>Cool & Dry (Nov–Feb)</h3>
          <ul>
            <li>Clearer water in many lakes and rivers</li>
            <li>Comfortable mornings and evenings</li>
          </ul>
        </div>
        <div class="season">
          <h3>Hot Season (Mar–May)</h3>
          <ul>
            <li>Fish deeper pools by day; dawn/dusk surface action</li>
            <li>Hydrate and bring sun protection</li>
          </ul>
        </div>
        <div class="season">
          <h3>Monsoon (Jun–Oct)</h3>
          <ul>
            <li>Rising/falling flows can trigger feeding</li>
            <li>Be cautious of currents and debris</li>
          </ul>
        </div>
      </div>
    </section>

    <!-- Responsible Fishing Tips -->
    <section id="tips" aria-labelledby="tips-title">
      <h2 class="section-title" id="tips-title">Responsible Fishing</h2>
      <p class="section-lead">Respect local communities and ecosystems to keep waters healthy for everyone.</p>
      <div class="tips">
        <div class="tip">
          <!-- icon -->
          <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><path d="m9 11 3 3L22 4"></path><path d="M21 12v7a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V5a2 2 0 0 1 2-2h11"></path></svg>
          <strong>Know the rules.</strong> Check current local regulations, licensing, and protected areas before fishing.
        </div>
        <div class="tip">
          <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><path d="M22 2 11 13"></path><path d="M22 2s-5 1-10 6-6 10-6 10 6-1 10-6S22 2 22 2Z"></path><path d="M16 6c1.5 1.5 2 3.5 1.5 5.5"></path><path d="M2 22l3-3"></path><path d="M3 21c-.5-2 1-4 3-6 2-2 4-3.5 6-3"></path></svg>
          <strong>Handle fish carefully.</strong> Use barbless hooks where appropriate and release quickly if not keeping.
        </div>
        <div class="tip">
          <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><path d="M6 3v12"></path><path d="m6 15-2 2"></path><path d="M8 17H4"></path><path d="M18 3v12"></path><path d="m18 15 2 2"></path><path d="M20 17h-4"></path><path d="M9 7h6"></path><path d="M12 3v4"></path><path d="M12 11v4"></path></svg>
          <strong>Leave no trace.</strong> Pack out line, hooks, and trash; respect wildlife and private property.
        </div>
      </div>
      <p class="section-lead" style="margin-top:14px; font-size:.95rem;">Note: Information here is general and for inspiration only. Always confirm up‑to‑date guidance on seasons, access, and safety.</p>
    </section>

    <!-- Gallery -->
    <section id="gallery" aria-labelledby="gallery-title">
      <h2 class="section-title" id="gallery-title">Photo Gallery</h2>
      <p class="section-lead">Swap these images with your own trip photos.</p>
      <div class="gallery">
        <img src="https://images.unsplash.com/photo-1518834107812-67b5c8d8aa32?q=80&w=1600&auto=format&fit=crop" alt="Boat on a calm lake at dusk" />
        <img src="https://images.unsplash.com/photo-1512015453214-39f84f0434e3?q=80&w=1600&auto=format&fit=crop" alt="Closeup of a fishing reel" />
        <img src="https://images.unsplash.com/photo-1528154291023-a6525fabe5fb?q=80&w=1600&auto=format&fit=crop" alt="River bend with misty trees" />
        <img src="https://images.unsplash.com/photo-1505483531331-92888b7c4dd0?q=80&w=1600&auto=format&fit=crop" alt="Mangrove channel with reflections" />
        <img src="https://images.unsplash.com/photo-1512646605205-78422b742f1c?q=80&w=1600&auto=format&fit=crop" alt="Sunlit coastline and small islands" />
        <img src="https://images.unsplash.com/photo-1529107386315-e1a2ed48a620?q=80&w=1600&auto=format&fit=crop" alt="Angler with rod casting off rocks" />
      </div>
    </section>

    <!-- Plan / Contact -->
    <section id="contact" aria-labelledby="contact-title">
      <h2 class="section-title" id="contact-title">Plan Your Trip</h2>
      <p class="section-lead">Have questions or want to suggest a spot? Send a message below.</p>
      <div class="grid" style="grid-template-columns: 1.1fr .9fr; align-items: start; gap: 1.2rem;">
        <form id="msgForm" aria-label="Contact form" novalidate>
          <label>
            <span>Name</span>
            <input name="name" placeholder="Your name" required aria-required="true" />
          </label>
          <label>
            <span>Email</span>
            <input type="email" name="email" placeholder="you@example.com" required aria-required="true" />
          </label>
          <label>
            <span>Message</span>
            <textarea name="message" placeholder="Share your idea or question…" required aria-required="true"></textarea>
          </label>
          <button class="btn primary" type="submit">Send Message</button>
          <p id="formNote" class="section-lead" style="display:none; margin:.6rem 0 0;">Thanks! Your message was captured locally (demo only).</p>
        </form>

        <aside class="card2" aria-label="Map">
          <iframe title="Myanmar Map" width="100%" height="320" style="border:0; border-radius:12px;" loading="lazy" allowfullscreen
            referrerpolicy="no-referrer-when-downgrade"
            src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3894333.032675205!2d92.10946407323323!3d19.295433242760743!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x30cb7734b12bcbc1%3A0x33f7a129b3f95308!2sMyanmar%20(Burma)!5e0!3m2!1sen!2smm!4v1700000000000">
          </iframe>
          <p class="section-lead" style="margin-top:.8rem;">Use the map to explore waterways and plan access routes.</p>
        </aside>
      </div>
    </section>
  </main>

  <footer>
    <div class="container">
      <p>© <span id="year"></span> Fishing in Myanmar • Built with ❤️ for anglers. This is an informational demo—verify local rules and conditions before fishing.</p>
    </div>
  </footer>

  <button id="toTop" class="btn" aria-label="Back to top">↑ Top</button>

  <script>
    // Smooth scroll for same-page links
    document.querySelectorAll('a[href^="#"]').forEach(a => {
      a.addEventListener('click', (e) => {
        const target = document.querySelector(a.getAttribute('href'));
        if (target) { e.preventDefault(); target.scrollIntoView({ behavior: 'smooth' }); }
      });
    });

    // Back-to-top button
    const toTop = document.getElementById('toTop');
    const onScroll = () => {
      if (window.scrollY > 500) toTop.classList.add('show'); else toTop.classList.remove('show');
    };
    window.addEventListener('scroll', onScroll);
    toTop.addEventListener('click', () => window.scrollTo({ top: 0, behavior: 'smooth' }));

    // Footer year
    document.getElementById('year').textContent = new Date().getFullYear();

    // Demo form handler (no backend)
    const form = document.getElementById('msgForm');
    form.addEventListener('submit', (e) => {
      e.preventDefault();
      const data = Object.fromEntries(new FormData(form).entries());
      console.log('Contact form (demo):', data);
      localStorage.setItem('fishing-myanmar-message', JSON.stringify({ ...data, at: new Date().toISOString() }));
      document.getElementById('formNote').style.display = 'block';
      form.reset();
    });
  </script>
</body>
</html>
