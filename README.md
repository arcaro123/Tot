<html lang="ca">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Els jocs de Machacadron</title>
<meta name="description" content="Col·lecció de jocs que es poden jugar directament al navegador.">
<style>
  :root {
    --bg: #fff8e7;
    --bg2: #ffeec2;
    --card: #ffffff;
    --text: #2b2118;
    --muted: #6d5b48;
    --accent: #e0a100;
    --accent2: #b87400;
    --border: #ecd9a8;
    --shadow: rgba(120, 80, 0, .18);
    color-scheme: light;
  }
  @media (prefers-color-scheme: dark) {
    :root {
      --bg: #17120b;
      --bg2: #241b0d;
      --card: #2a2113;
      --text: #f6ead2;
      --muted: #c4b08a;
      --accent: #ffc83a;
      --accent2: #ffd978;
      --border: #4a3a1c;
      --shadow: rgba(0, 0, 0, .5);
      color-scheme: dark;
    }
  }
  * { box-sizing: border-box; }
  html, body { margin: 0; min-height: 100%; }
  body {
    font-family: system-ui, -apple-system, "Segoe UI", Roboto, sans-serif;
    color: var(--text);
    background:
      radial-gradient(circle at 20% 0%, var(--bg2), transparent 55%),
      var(--bg);
    padding: env(safe-area-inset-top, 0) 0 env(safe-area-inset-bottom, 0);
  }
  header {
    text-align: center;
    padding: 56px 20px 20px;
  }
  header h1 { margin: 0 0 8px; font-size: clamp(2rem, 6vw, 3.2rem); letter-spacing: -.02em; }
  header p { margin: 0 auto; max-width: 540px; color: var(--muted); font-size: 1.05rem; }
  main {
    max-width: 1000px;
    margin: 0 auto;
    padding: 24px 20px 64px;
    display: grid;
    gap: 22px;
    grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
  }
  a.card {
    display: flex;
    flex-direction: column;
    gap: 10px;
    padding: 26px 24px 22px;
    background: var(--card);
    border: 2px solid var(--border);
    border-radius: 18px;
    color: inherit;
    text-decoration: none;
    box-shadow: 0 6px 18px var(--shadow);
    transition: transform .15s ease, border-color .15s ease, box-shadow .15s ease;
  }
  a.card:hover, a.card:focus-visible {
    transform: translateY(-4px);
    border-color: var(--accent);
    box-shadow: 0 12px 26px var(--shadow);
    outline: none;
  }
  .icon {
    font-size: 3rem;
    line-height: 1;
    width: 72px; height: 72px;
    display: grid; place-items: center;
    border-radius: 16px;
    background: var(--bg2);
  }
  .card h2 { margin: 6px 0 0; font-size: 1.4rem; }
  .card p { margin: 0; color: var(--muted); line-height: 1.45; flex: 1; }
  .play {
    margin-top: 10px;
    align-self: flex-start;
    padding: 9px 18px;
    border-radius: 999px;
    background: var(--accent);
    color: #2b2118;
    font-weight: 700;
  }
  .url { font-size: .8rem; color: var(--muted); word-break: break-all; }
  footer { text-align: center; padding: 0 20px 36px; color: var(--muted); font-size: .9rem; }
  footer a { color: var(--accent2); }
</style>
</head>
<body>
  <header>
    <h1>Els jocs de Machacadron</h1>
    <p>Tria un joc i juga-hi directament des del navegador, sense instal·lar res.</p>
  </header>

  <main>
    <a class="card" href="https://arcaro123.github.io/BattleBees/" target="_blank" rel="noopener">
      <div class="icon" aria-hidden="true">🐝</div>
      <h2>The BattleBees</h2>
      <p>Defensa el teu rusc contra exèrcits d’insectes: genera abelles, millora-les i derrota la Vespa Reina.</p>
      <span class="url">arcaro123.github.io/BattleBees</span>
      <span class="play">Jugar</span>
    </a>

    <a class="card" href="https://arcaro123.github.io/PokemonQuest/" target="_blank" rel="noopener">
      <div class="icon" aria-hidden="true">⚡</div>
      <h2>PokemonQuest</h2>
      <p>Joc d’aventura per navegador. Obre’l i comença l’exploració.</p>
      <span class="url">arcaro123.github.io/PokemonQuest</span>
      <span class="play">Jugar</span>
    </a>

    <a class="card" href="https://arcaro123.github.io/ratlla/" target="_blank" rel="noopener">
      <div class="icon" aria-hidden="true">🎯</div>
      <h2>Ratlla</h2>
      <p>Joc de ratlles per a dos jugadors. Obre’l i prova de guanyar.</p>
      <span class="url">arcaro123.github.io/ratlla</span>
      <span class="play">Jugar</span>
    </a>
  </main>

  <footer>
    Fet per <a href="https://github.com/arcaro123" target="_blank" rel="noopener">arcaro123</a>
  </footer>
</body>
</html>
