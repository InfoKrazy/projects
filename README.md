<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Your GitHub Homepage — Projects & Creations</title>
  <!--
    Instructions:
    1. Save this file as `index.html` in the root of a GitHub repository (or in a `docs/` folder).
    2. Enable GitHub Pages for that repo (Settings → Pages) and choose the branch/folder where this index.html lives.
    3. To add links permanently, open this file and edit the PROJECTS object near the top, or use the "Add Link" form in-page to generate a JSON snippet you can paste into the PROJECTS object (the Add Link form does NOT write to your repo automatically).
    4. You can personalize colors, fonts, and the `author` variable below.

    This is a single-file, responsive, accessible HTML page with three main sections:
      - Working On
      - Refining
      - Finished
    Each section displays cards for projects and provides an easy way to add new links (copy-paste-ready JSON snippet).
  -->
  <style>
    :root{--bg:#0f1724;--card:#0b1220;--muted:#9aa7bf;--accent:#7c5cff;--glass:rgba(255,255,255,0.04);--radius:14px}
    *{box-sizing:border-box}
    html,body{height:100%}
    body{margin:0;font-family:Inter, ui-sans-serif, system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;color:#e6eef8;background:linear-gradient(180deg,#071028 0%, #081426 60%);-webkit-font-smoothing:antialiased;line-height:1.4}
    .wrap{max-width:1100px;margin:36px auto;padding:28px}
    header{display:flex;align-items:center;justify-content:space-between;gap:16px}
    .brand{display:flex;align-items:center;gap:14px}
    .logo{width:64px;height:64px;border-radius:12px;background:linear-gradient(135deg,var(--accent),#00c2ff);display:flex;align-items:center;justify-content:center;font-weight:700;color:#021027;font-size:20px;box-shadow:0 6px 20px rgba(124,92,255,0.18)}
    h1{margin:0;font-size:1.4rem}
    p.lead{margin:4px 0 0;color:var(--muted);font-size:0.95rem}

    nav.controls{display:flex;gap:10px;align-items:center}
    .btn{background:var(--glass);border:1px solid rgba(255,255,255,0.04);padding:10px 14px;border-radius:10px;color:var(--muted);cursor:pointer;font-weight:600}
    .btn.primary{background:linear-gradient(90deg,var(--accent),#00c2ff);color:#021027;border:none;box-shadow:0 8px 30px rgba(124,92,255,0.12)}

    .grid{display:grid;grid-template-columns:1fr 1fr 1fr;gap:18px;margin-top:26px}
    .section{background:linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));border-radius:var(--radius);padding:16px}
    .section h2{display:flex;align-items:center;justify-content:space-between;margin:0 0 10px}
    .section .count{color:var(--muted);font-size:0.85rem}

    .cards{display:grid;gap:12px}
    .card{display:flex;gap:12px;align-items:flex-start;padding:12px;border-radius:12px;background:linear-gradient(180deg,rgba(255,255,255,0.01), rgba(255,255,255,0.00));border:1px solid rgba(255,255,255,0.03)}
    .card .thumb{width:56px;height:56px;border-radius:10px;flex-shrink:0;background:linear-gradient(135deg, rgba(255,255,255,0.02), rgba(255,255,255,0.00));display:flex;align-items:center;justify-content:center;font-weight:700;color:var(--accent)}
    .card h3{margin:0;font-size:1rem}
    .card p{margin:6px 0 0;color:var(--muted);font-size:0.92rem}
    .card .meta{margin-left:auto;display:flex;flex-direction:column;align-items:flex-end;gap:8px}
    .link{display:inline-block;padding:8px 10px;border-radius:8px;background:rgba(255,255,255,0.03);font-weight:700;text-decoration:none;color:inherit;border:1px solid rgba(255,255,255,0.02)}

    footer{margin-top:22px;color:var(--muted);font-size:0.9rem;text-align:center}

    /* modal */
    .modal-backdrop{position:fixed;inset:0;background:rgba(2,6,23,0.65);display:none;align-items:center;justify-content:center;padding:24px;z-index:60}
    .modal{width:100%;max-width:720px;background:linear-gradient(180deg,#07102a,#071124);border-radius:16px;padding:18px;border:1px solid rgba(255,255,255,0.04)}
    .form-row{display:flex;gap:10px}
    .field{display:block;width:100%;padding:10px;border-radius:10px;background:transparent;border:1px solid rgba(255,255,255,0.03);color:inherit}
    label{font-size:0.8rem;color:var(--muted);margin-bottom:6px;display:block}
    .muted{color:var(--muted);font-size:0.9rem}

    @media (max-width:900px){.grid{grid-template-columns:1fr;}}

    /* small helpers */
    .pill{padding:6px 8px;border-radius:999px;background:rgba(255,255,255,0.02);font-weight:700;border:1px solid rgba(255,255,255,0.03)}
    .actions{display:flex;gap:8px}
    .small{font-size:0.86rem}

    /* subtle animations */
    .card{transition:transform .18s ease, box-shadow .18s ease}
    .card:hover{transform:translateY(-6px);box-shadow:0 12px 40px rgba(2,6,23,0.6)}
  </style>
</head>
<body>
  <div class="wrap" role="main">
    <header>
      <div class="brand">
        <div class="logo">GH</div>
        <div>
          <h1 id="siteTitle">Your Name — Projects & Creations</h1>
          <p class="lead">A single place for everything you're working on, refining, and finished. Deploy to GitHub Pages by saving as <code>index.html</code>.</p>
        </div>
      </div>
      <nav class="controls" aria-label="Page controls">
        <button class="btn" id="exportJSON">Export JSON</button>
        <button class="btn" id="openAdd">Add Link</button>
        <a class="btn primary" id="githubBtn" href="#" target="_blank" rel="noopener">Open Repo</a>
      </nav>
    </header>

    <section class="grid" aria-label="Project sections">
      <div class="section" id="working">
        <h2>Working On <span class="count" id="workingCount">0</span></h2>
        <div class="cards" id="workingCards"></div>
      </div>

      <div class="section" id="refining">
        <h2>Refining <span class="count" id="refiningCount">0</span></h2>
        <div class="cards" id="refiningCards"></div>
      </div>

      <div class="section" id="finished">
        <h2>Finished <span class="count" id="finishedCount">0</span></h2>
        <div class="cards" id="finishedCards"></div>
      </div>
    </section>

    <footer>
      <div class="muted">Made with ❤️ — Edit the <code>PROJECTS</code> array in this file to add permanent items.</div>
    </footer>
  </div>

  <!-- Modal: Add Link / Quick edit (does NOT persist to GitHub) -->
  <div class="modal-backdrop" id="modal">
    <div class="modal" role="dialog" aria-modal="true" aria-labelledby="modalTitle">
      <h3 id="modalTitle">Add a link</h3>
      <p class="muted">Fill the form and either insert the snippet into the file's <code>PROJECTS</code> object, or copy the link to use elsewhere.</p>
      <div style="height:12px"></div>
      <div>
        <label>Section</label>
        <select id="fieldSection" class="field">
          <option value="working">Working On</option>
          <option value="refining">Refining</option>
          <option value="finished">Finished</option>
        </select>
      </div>

      <div style="height:8px"></div>
      <div>
        <label>Title</label>
        <input id="fieldTitle" class="field" placeholder="Project title — e.g. My Cool Library" />
      </div>
      <div style="height:8px"></div>
      <div>
        <label>URL</label>
        <input id="fieldURL" class="field" placeholder="https://github.com/you/repo" />
      </div>
      <div style="height:8px"></div>
      <div>
        <label>Description (optional)</label>
        <input id="fieldDesc" class="field" placeholder="Short description" />
      </div>

      <div style="height:12px"></div>
      <div style="display:flex;gap:8px;justify-content:flex-end">
        <button class="btn" id="cancelBtn">Cancel</button>
        <button class="btn primary" id="addBtn">Create snippet & add locally</button>
      </div>

      <div style="height:12px"></div>
      <div id="generated" style="display:none">
        <label>Generated JSON (copy this into the <code>PROJECTS</code> variable in this file to persist)</label>
        <textarea id="generatedArea" class="field" style="height:120px;font-family:monospace;white-space:pre-wrap;overflow:auto"></textarea>
        <div style="height:8px"></div>
        <div style="display:flex;gap:8px;justify-content:flex-end">
          <button class="btn" id="copyBtn">Copy to clipboard</button>
          <button class="btn primary" id="closeGen">Done</button>
        </div>
      </div>
    </div>
  </div>

  <script>
    /*
      PROJECTS structure: edit this block to add persistent links.
      Each item: { title, url, desc }
    */
    const author = { name: "Your Name", github: "https://github.com/yourusername" };

    const PROJECTS = {
      working: [
        { title: "Example In-Progress Project", url: "https://github.com/yourusername/in-progress", desc: "A short note about what I'm building." }
      ],
      refining: [
        { title: "Tweaks & Polishing", url: "https://github.com/yourusername/refining", desc: "Small improvements, docs, and tests." }
      ],
      finished: [
        { title: "Released Project", url: "https://github.com/yourusername/released", desc: "A project that's finished and available." }
      ]
    };

    // ----- Rendering logic -----
    function el(tag, attrs = {}, children = []){
      const node = document.createElement(tag);
      for(const k in attrs){
        if(k === 'class') node.className = attrs[k];
        else if(k === 'html') node.innerHTML = attrs[k];
        else node.setAttribute(k, attrs[k]);
      }
      (Array.isArray(children) ? children : [children]).forEach(c => { if(typeof c === 'string') node.appendChild(document.createTextNode(c)); else if(c) node.appendChild(c); });
      return node;
    }

    function makeCard(item){
      const thumb = el('div',{class:'thumb'}, [ (item.title && item.title[0]) || '?' ]);
      const title = el('h3',{}, [item.title]);
      const desc = el('p',{}, [item.desc || '']);
      const link = el('a',{class:'link',href:item.url || '#',target:'_blank',rel:'noopener'}, [ 'Open' ]);
      const meta = el('div',{class:'meta'}, [ link ]);
      const card = el('div',{class:'card'}, [thumb, el('div',{}, [title, desc]), meta]);
      return card;
    }

    function render(){
      const wk = document.getElementById('workingCards');
      const rf = document.getElementById('refiningCards');
      const fn = document.getElementById('finishedCards');
      wk.innerHTML = '';
      rf.innerHTML = '';
      fn.innerHTML = '';

      PROJECTS.working.forEach(i => wk.appendChild(makeCard(i)));
      PROJECTS.refining.forEach(i => rf.appendChild(makeCard(i)));
      PROJECTS.finished.forEach(i => fn.appendChild(makeCard(i)));

      document.getElementById('workingCount').textContent = PROJECTS.working.length;
      document.getElementById('refiningCount').textContent = PROJECTS.refining.length;
      document.getElementById('finishedCount').textContent = PROJECTS.finished.length;

      // fill some header info
      document.getElementById('siteTitle').textContent = `${author.name} — Projects & Creations`;
      const ghbtn = document.getElementById('githubBtn');
      ghbtn.href = author.github;
      ghbtn.textContent = 'Visit GitHub';
    }

    // initial render
    render();

    // ----- Modal behavior -----
    const modal = document.getElementById('modal');
    document.getElementById('openAdd').addEventListener('click', () => {
      modal.style.display = 'flex';
      document.getElementById('fieldTitle').focus();
    });
    document.getElementById('cancelBtn').addEventListener('click', () => { modal.style.display = 'none'; document.getElementById('generated').style.display='none'; });

    document.getElementById('addBtn').addEventListener('click', () => {
      const section = document.getElementById('fieldSection').value;
      const title = document.getElementById('fieldTitle').value.trim();
      const url = document.getElementById('fieldURL').value.trim();
      const desc = document.getElementById('fieldDesc').value.trim();
      if(!title || !url){
        alert('Please enter at least a title and url.');
        return;
      }
      const item = { title, url, desc };
      // add locally (this will not persist unless you edit the file)
      PROJECTS[section].unshift(item);
      render();

      // show generated JSON for copy/paste
      const generated = { [section]: PROJECTS[section].slice(0, 50) }; // show that section only
      document.getElementById('generatedArea').value = JSON.stringify(generated, null, 2);
      document.getElementById('generated').style.display = 'block';
    });

    document.getElementById('copyBtn').addEventListener('click', async () => {
      const txt = document.getElementById('generatedArea').value;
      try{ await navigator.clipboard.writeText(txt); alert('Copied to clipboard — paste into the PROJECTS variable in this file to persist.'); }
      catch(e){ prompt('Copy the JSON below:', txt); }
    });

    document.getElementById('closeGen').addEventListener('click', () => { document.getElementById('generated').style.display = 'none'; modal.style.display = 'none'; });

    // export full JSON of all projects
    document.getElementById('exportJSON').addEventListener('click', () => {
      const blob = new Blob([JSON.stringify(PROJECTS, null, 2)], { type: 'application/json' });
      const url = URL.createObjectURL(blob);
      const a = document.createElement('a');
      a.href = url; a.download = 'projects.json'; document.body.appendChild(a); a.click(); a.remove(); URL.revokeObjectURL(url);
    });

    // keyboard: escape to close modal
    document.addEventListener('keydown', (e) => { if(e.key === 'Escape'){ modal.style.display='none'; document.getElementById('generated').style.display='none'; } });

    // if you want to fetch a projects.json instead of editing file, uncomment the fetch block below and put a projects.json in the same folder.
    /*
    fetch('projects.json').then(r => r.json()).then(data => { Object.assign(PROJECTS, data); render(); }).catch(()=>{});
    */

    // small safety: sanitize URL when writing link (basic)
    function sanitize(u){ try{ const parsed=new URL(u); return parsed.href; }catch(e){ return '#'; } }

  </script>
</body>
</html>
