<!DOCTYPE html>
<html lang="ca">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Els jocs de Machacadron</title>
<meta name="description" content="Col·lecció de jocs que es poden jugar directament al navegador, sense instal·lar res.">
<meta name="theme-color" content="#17120b">
<style>
  :root {
    --bg: #fbf7ee;
    --surface: #ffffff;
    --surface-2: #f3ecdb;
    --text: #231b11;
    --muted: #6b5d4a;
    --line: #e6dbc2;
    --brand: #c98a00;
    --brand-ink: #231b11;
    --shadow: 0 1px 2px rgba(60, 40, 0, .06), 0 8px 24px rgba(60, 40, 0, .08);
    --shadow-hover: 0 2px 4px rgba(60, 40, 0, .08), 0 16px 36px rgba(60, 40, 0, .14);
    --c-bees: #e0a100;
    --c-quest: #e8622c;
    --c-ratlla: #d6336c;
    color-scheme: light;
  }
  @media (prefers-color-scheme: dark) {
    :root {
      --bg: #120e08;
      --surface: #1e1710;
      --surface-2: #2a2014;
      --text: #f5ead4;
      --muted: #b9a785;
      --line: #3a2d18;
      --brand: #ffc83a;
      --brand-ink: #231b11;
      --shadow: 0 1px 2px rgba(0, 0, 0, .4), 0 8px 24px rgba(0, 0, 0, .35);
      --shadow-hover: 0 2px 4px rgba(0, 0, 0, .5), 0 16px 36px rgba(0, 0, 0, .55);
      --c-bees: #ffc83a;
      --c-quest: #ff8a57;
      --c-ratlla: #ff6b9a;
      color-scheme: dark;
    }
  }

  *, *::before, *::after { box-sizing: border-box; }
  html { -webkit-text-size-adjust: 100%; }
  body {
    margin: 0;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    font-family: system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
    font-size: 1rem;
    line-height: 1.6;
    color: var(--text);
    background: var(--bg);
    -webkit-font-smoothing: antialiased;
  }
  /* Reinicia estils heretats d'altres fulls d'estil (línies sota els títols) */
  h1, h2, p { border: 0; padding-block: 0; }

  .wrap { width: min(1080px, 100% - 40px); margin-inline: auto; }

  /* Capçalera */
  .hero { padding: clamp(56px, 10vw, 104px) 0 clamp(32px, 5vw, 56px); }
  .hero h1 {
    margin: 0 0 14px;
    font-size: clamp(2.2rem, 6.5vw, 3.8rem);
    line-height: 1.05;
    font-weight: 800;
    letter-spacing: -.03em;
  }
  .hero p {
    margin: 0;
    max-width: 46ch;
    font-size: clamp(1.05rem, 2.2vw, 1.2rem);
    color: var(--muted);
  }
  .count {
    display: inline-block;
    margin-top: 22px;
    padding: 5px 12px;
    border: 1px solid var(--line);
    border-radius: 999px;
    background: var(--surface);
    font-size: .875rem;
    color: var(--muted);
  }

  /* Graella */
  main { flex: 1; }
  .grid {
    display: grid;
    gap: 20px;
    grid-template-columns: repeat(auto-fill, minmax(290px, 1fr));
    padding: 0 0 clamp(48px, 8vw, 88px);
    margin: 0;
    list-style: none;
  }

  .card {
    --accent: var(--brand);
    position: relative;
    display: flex;
    flex-direction: column;
    height: 100%;
    padding: 24px;
    background: var(--surface);
    border: 1px solid var(--line);
    border-top: 4px solid var(--accent);
    border-radius: 14px;
    color: inherit;
    text-decoration: none;
    box-shadow: var(--shadow);
    transition: transform .2s ease, box-shadow .2s ease;
  }
  .card:hover { transform: translateY(-3px); box-shadow: var(--shadow-hover); }
  .card:focus-visible { outline: 3px solid var(--accent); outline-offset: 3px; }

  .card-bees { --accent: var(--c-bees); }
  .card-quest { --accent: var(--c-quest); }
  .card-ratlla { --accent: var(--c-ratlla); }

  .icon {
    width: 56px; height: 56px;
    display: grid; place-items: center;
    border-radius: 12px;
    background: var(--surface-2);
    font-size: 1.9rem;
    line-height: 1;
  }
  .card h2 {
    margin: 20px 0 8px;
    font-size: 1.3rem;
    line-height: 1.25;
    letter-spacing: -.01em;
  }
  .card .desc { margin: 0 0 18px; color: var(--muted); font-size: .975rem; flex: 1; }

  .tags { display: flex; flex-wrap: wrap; gap: 6px; margin-bottom: 20px; }
  .tag {
    padding: 2px 10px;
    border-radius: 6px;
    background: var(--surface-2);
    font-size: .8rem;
    color: var(--muted);
  }

  .foot {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 12px;
    padding-top: 16px;
    border-top: 1px solid var(--line);
  }
  .url {
    min-width: 0;
    font-size: .8rem;
    color: var(--muted);
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
  }
  .play {
    flex: none;
    padding: 8px 20px;
    border-radius: 8px;
    background: var(--brand);
    color: var(--brand-ink);
    font-weight: 700;
    font-size: .95rem;
    transition: filter .15s ease;
  }
  .card:hover .play { filter: brightness(1.08); }

  /* Peu */
  footer { border-top: 1px solid var(--line); padding: 24px 0 32px; font-size: .9rem; color: var(--muted); }
  footer .wrap { display: flex; flex-wrap: wrap; gap: 8px 24px; justify-content: space-between; }
  footer a { color: var(--text); text-underline-offset: 3px; }
  footer a:hover { color: var(--brand); }

  @media (max-width: 480px) {
    .card { padding: 20px; }
    .foot { flex-direction: column; align-items: stretch; }
    .play { text-align: center; }
    .url { text-align: center; }
  }
  @media (prefers-reduced-motion: reduce) {
    .card, .play { transition: none; }
    .card:hover { transform: none; }
  }
</style>
</head>
<body>
  <header class="hero">
    <div class="wrap">
      <h1>Els jocs de Machacadron</h1>
      <p>Tria un joc i juga-hi directament des del navegador, sense instal·lar res.</p>
      <span class="count">3 jocs disponibles</span>
    </div>
  </header>

  <main>
    <div class="wrap">
      <ul class="grid">
        <li>
          <a class="card card-bees" href="https://arcaro123.github.io/BattleBees/" target="_blank" rel="noopener" aria-label="Jugar a The BattleBees (s'obre en una pestanya nova)">
            <div class="icon" aria-hidden="true">🐝</div>
            <h2>The BattleBees</h2>
            <p class="desc">Defensa el teu rusc contra exèrcits d’insectes: genera abelles, millora-les i derrota la Vespa Reina.</p>
            <div class="tags"><span class="tag">Estratègia</span><span class="tag">Defensa</span></div>
            <div class="foot">
              <span class="url">arcaro123.github.io/BattleBees</span>
              <span class="play">Jugar</span>
            </div>
          </a>
        </li>

        <li>
          <a class="card card-quest" href="https://arcaro123.github.io/PokemonQuest/" target="_blank" rel="noopener" aria-label="Jugar a PokemonQuest (s'obre en una pestanya nova)">
            <div class="icon" aria-hidden="true">⚡</div>
            <h2>PokemonQuest</h2>
            <p class="desc">Joc d’aventura per navegador. Obre’l i comença l’exploració.</p>
            <div class="tags"><span class="tag">Aventura</span><span class="tag">Exploració</span></div>
            <div class="foot">
              <span class="url">arcaro123.github.io/PokemonQuest</span>
              <span class="play">Jugar</span>
            </div>
          </a>
        </li>

        <li>
          <a class="card card-ratlla" href="https://arcaro123.github.io/ratlla/" target="_blank" rel="noopener" aria-label="Jugar a Ratlla (s'obre en una pestanya nova)">
            <div class="icon" aria-hidden="true">🎯</div>
            <h2>Ratlla</h2>
            <p class="desc">Joc de ratlles per a dos jugadors. Obre’l i prova de guanyar.</p>
            <div class="tags"><span class="tag">2 jugadors</span><span class="tag">Tauler</span></div>
            <div class="foot">
              <span class="url">arcaro123.github.io/ratlla</span>
              <span class="play">Jugar</span>
            </div>
          </a>
        </li>
      </ul>
    </div>
  </main>

  <footer>
    <div class="wrap">
      <span>Fet per <a href="https://github.com/arcaro123" target="_blank" rel="noopener">Machacadron</a></span>
      <span>Jocs gratuïts, directament al navegador</span>
    </div>
  </footer>
</body>
</html>
