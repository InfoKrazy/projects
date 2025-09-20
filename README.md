<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>InfoKrazy — Projects</title>
  <style>
    :root {
      --bg-dark: #0e0e1a;
      --bg-light: #f4f6fa;
      --text-dark: #f0f4ff;
      --text-light: #1a1a1a;
      --accent: #6c63ff;
      --card-dark: #1a1a2e;
      --card-light: #ffffff;
      --radius: 14px;
      --transition: all 0.4s ease;
    }

    body {
      margin: 0;
      font-family: "Inter", system-ui, sans-serif;
      background: var(--bg-dark);
      color: var(--text-dark);
      transition: var(--transition);
      overflow-x: hidden;
    }

    body.light {
      background: var(--bg-light);
      color: var(--text-light);
    }

    .wrap {
      max-width: 1000px;
      margin: 60px auto;
      padding: 20px;
      opacity: 0;
      transform: translateY(30px);
      animation: fadeUp 1s ease forwards;
      animation-delay: 3s;
    }

    @keyframes fadeUp {
      to { opacity: 1; transform: translateY(0); }
    }

    .grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 20px;
    }

    .card {
      padding: 20px;
      border-radius: var(--radius);
      background: var(--card-dark);
      transition: var(--transition);
      box-shadow: 0 6px 18px rgba(0,0,0,0.3);
      cursor: pointer;
      opacity: 0;
      transform: scale(0.9);
      animation: popIn 0.6s ease forwards;
    }

    .card:nth-child(odd) { animation-delay: 3.2s; }
    .card:nth-child(even) { animation-delay: 3.4s; }

    body.light .card { background: var(--card-light); box-shadow: 0 6px 18px rgba(0,0,0,0.08); }

    .card:hover {
      transform: translateY(-6px) scale(1.03);
      box-shadow: 0 12px 32px rgba(0,0,0,0.4);
    }

    @keyframes popIn {
      to { opacity: 1; transform: scale(1); }
    }

    h3 {
      margin: 0 0 6px;
      font-size: 1.1rem;
    }

    p {
      margin: 0;
      font-size: 0.9rem;
      opacity: 0.8;
    }

    a {
      color: var(--accent);
      text-decoration: none;
      font-weight: 600;
      margin-top: 8px;
      display: inline-block;
      transition: var(--transition);
    }

    a:hover { opacity: 0.7; }

    .theme-toggle {
      position: fixed;
      top: 20px;
      right: 20px;
      background: var(--accent);
      border: none;
      color: white;
      padding: 10px 14px;
      border-radius: 10px;
      cursor: pointer;
      font-weight: 600;
      z-index: 100;
      transition: var(--transition);
    }

    .startup {
      position: fixed;
      inset: 0;
      display: flex;
      align-items: center;
      justify-content: center;
      background: var(--bg-dark);
      color: var(--text-dark);
      font-size: 1.6rem;
      font-weight: 700;
      z-index: 200;
      animation: fadeOut 1s ease forwards;
      animation-delay: 2.5s;
    }

    body.light .startup { background: var(--bg-light); color: var(--text-light); }

    @keyframes fadeOut {
      to { opacity: 0; visibility: hidden; }
    }
  </style>
</head>
<body>
  <div class="startup">InfoKrazys Projects</div>

  <button class="theme-toggle" id="themeBtn">Switch Theme</button>

  <div class="wrap">
    <section class="grid" id="InfoKrazy"></section>
  </div>

  <script>
    const projects = [
      { title: "In Progress Project", url: "https://github.com/InfoKrazy/in-progress", desc: "A short note about what I'm building." },
      { title: "Tweaks & Polishing", url: "https://github.com/InfoKrazy/refining", desc: "Small improvements, docs, and tests." },
      { title: "Released Project", url: "https://github.com/InfoKrazy/released", desc: "A project that's finished and available." }
    ];

    const container = document.getElementById('projects');
    projects.forEach(p => {
      const card = document.createElement('div');
      card.className = 'card';
      card.innerHTML = `
        <h3>${p.title}</h3>
        <p>${p.desc || ''}</p>
        <a href="${p.url}" target="_blank">View Project</a>
      `;
      container.appendChild(card);
    });

    const themeBtn = document.getElementById('themeBtn');
    themeBtn.addEventListener('click', () => {
      document.body.classList.toggle('light');
    });
  </script>
</body>
</html>
