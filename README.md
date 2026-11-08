
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="theme-color" content="#10120f">
<title>Book Studio — Create something worth reading</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600;700;800&family=Playfair+Display:wght@500;600;700&display=swap" rel="stylesheet">
<style>
:root{
  --bg:#10120f;--panel:#181b17;--panel2:#20241e;--line:#30352d;
  --text:#f4f4ed;--muted:#a0a596;--lime:#c6f36b;--lime2:#dafa9a;
  --white:#fff;--danger:#ff8d83;--radius:18px;
}
*{box-sizing:border-box}
body{margin:0;background:var(--bg);color:var(--text);font-family:"DM Sans",sans-serif}
button,input,textarea,select{font:inherit}
button{cursor:pointer}
.app{min-height:100vh;display:flex}
.sidebar{width:250px;position:fixed;inset:0 auto 0 0;background:#141713;border-right:1px solid var(--line);padding:25px 17px;display:flex;flex-direction:column;z-index:5}
.brand{display:flex;align-items:center;gap:11px;padding:3px 8px 30px}
.brand-mark{width:35px;height:35px;border-radius:11px;background:var(--lime);color:#11150d;display:grid;place-items:center;font-weight:900;font-size:19px}
.brand-name{font-weight:800;letter-spacing:-.5px;font-size:17px}
.brand-sub{font-size:10px;color:var(--muted);letter-spacing:1.6px;margin-top:2px}
.nav-label{font-size:10px;letter-spacing:1.6px;color:#777e70;padding:12px 11px 9px}
.nav{display:flex;flex-direction:column;gap:5px}
.nav button{border:0;background:transparent;color:#b7bcae;text-align:left;padding:12px 13px;border-radius:11px;display:flex;align-items:center;gap:12px;font-size:13px}
.nav button:hover,.nav button.active{background:#282e22;color:var(--lime)}
.nav .ico{width:19px;text-align:center;font-size:16px}
.sidebar-bottom{margin-top:auto}
.plan-mini{background:#20271b;border:1px solid #3c4b2a;border-radius:14px;padding:14px;margin:12px 2px}
.plan-mini strong{font-size:12px}
.plan-mini p{font-size:11px;color:var(--muted);line-height:1.5;margin:7px 0 12px}
.plan-mini button{width:100%;background:var(--lime);border:0;border-radius:8px;padding:9px;font-weight:800;font-size:11px}
.profile{display:flex;gap:10px;align-items:center;padding:15px 7px 0;border-top:1px solid var(--line)}
.avatar{width:34px;height:34px;border-radius:50%;background:#394333;color:var(--lime);display:grid;place-items:center;font-weight:800}
.profile small{display:block;color:var(--muted);font-size:10px;margin-top:3px}
.main{margin-left:250px;width:calc(100% - 250px);min-height:100vh}
.topbar{height:72px;border-bottom:1px solid var(--line);display:flex;align-items:center;justify-content:space-between;padding:0 4.2%;position:sticky;top:0;background:#10120fef;backdrop-filter:blur(14px);z-index:4}
.topbar-left{font-size:13px;color:var(--muted)}
.topbar-right{display:flex;align-items:center;gap:12px}
.status{font-size:11px;color:var(--lime);border:1px solid #465834;border-radius:30px;padding:7px 11px}
.mobile-brand{display:none}
.content{max-width:1400px;margin:auto;padding:38px 4.2% 70px}
.page{display:none;animation:fade .2s ease}
.page.active{display:block}
@keyframes fade{from{opacity:.5;transform:translateY(4px)}to{opacity:1;transform:none}}
.eyebrow{color:var(--lime);font-size:10px;font-weight:800;letter-spacing:2px;text-transform:uppercase}
h1,h2,h3,p{margin-top:0}
h1{font-size:clamp(29px,4vw,43px);letter-spacing:-1.7px;margin:10px 0 9px}
h2{font-size:23px;letter-spacing:-.6px}
h3{font-size:15px}
.sub{color:var(--muted);font-size:13px;line-height:1.7}
.btn{border:1px solid var(--line);background:var(--panel2);color:var(--text);border-radius:10px;padding:11px 15px;font-size:12px;font-weight:700}
.btn:hover{border-color:#788d54}
.btn.primary{background:var(--lime);color:#11150d;border-color:var(--lime)}
.btn.primary:hover{background:var(--lime2)}
.btn.small{padding:8px 11px;font-size:11px}
.btn.danger{color:var(--danger)}
.hero{display:flex;justify-content:space-between;align-items:flex-end;gap:20px;margin-bottom:28px}
.hero-actions{display:flex;gap:9px;flex-wrap:wrap}
.stats{display:grid;grid-template-columns:repeat(4,1fr);gap:13px;margin-bottom:28px}
.stat{background:var(--panel);border:1px solid var(--line);border-radius:15px;padding:18px}
.stat-label{font-size:11px;color:var(--muted)}
.stat-value{font-size:27px;font-weight:800;margin:9px 0 3px;letter-spacing:-1px}
.stat-note{font-size:10px;color:#9ba58c}
.grid-two{display:grid;grid-template-columns:1.45fr 1fr;gap:17px}
.panel{background:var(--panel);border:1px solid var(--line);border-radius:var(--radius);padding:21px}
.panel-head{display:flex;align-items:center;justify-content:space-between;gap:10px;margin-bottom:18px}
.panel-head h2,.panel-head h3{margin:0}
.quick-grid{display:grid;grid-template-columns:repeat(2,1fr);gap:10px}
.quick{border:1px solid var(--line);background:#1e221c;border-radius:13px;padding:15px;text-align:left;color:var(--text)}
.quick:hover{border-color:var(--lime)}
.quick .quick-icon{font-size:22px;margin-bottom:12px}
.quick strong{display:block;font-size:12px}
.quick span{display:block;font-size:10px;color:var(--muted);margin-top:5px;line-height:1.5}
.book-list{display:flex;flex-direction:column;gap:10px}
.book-row{display:flex;align-items:center;gap:13px;padding:10px;border:1px solid var(--line);border-radius:12px}
.cover{width:52px;height:68px;flex-shrink:0;border-radius:6px;background:linear-gradient(145deg,#35452d,#11180f);display:flex;align-items:center;justify-content:center;text-align:center;padding:6px;color:#e8f6cf;font-family:"Playfair Display",serif;font-size:10px;overflow:hidden}
.book-info{min-width:0;flex:1}
.book-info strong{font-size:12px;display:block;white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
.book-info small{font-size:10px;color:var(--muted);display:block;margin-top:5px}
.book-actions{display:flex;gap:6px}
.empty{padding:32px 15px;text-align:center;color:var(--muted);border:1px dashed #454b40;border-radius:14px;font-size:12px;line-height:1.7}
.form-card{max-width:850px}
.field{margin:17px 0}
.field label{display:block;font-size:12px;font-weight:700;margin-bottom:8px}
.field input,.field textarea,.field select{width:100%;background:#11140f;border:1px solid var(--line);border-radius:10px;color:var(--text);padding:13px;outline:none;font-size:13px}
.field textarea{min-height:110px;resize:vertical;line-height:1.6}
.field input:focus,.field textarea:focus,.field select:focus{border-color:var(--lime)}
.field small{display:block;color:var(--muted);font-size:10px;margin-top:6px}
.field-row{display:grid;grid-template-columns:1fr 1fr;gap:13px}
.chips{display:flex;flex-wrap:wrap;gap:8px}
.chip{border:1px solid var(--line);background:#171a15;color:#c4c9bb;padding:9px 13px;border-radius:30px;font-size:11px}
.chip.selected{background:#29351f;border-color:var(--lime);color:var(--lime)}
.templates{display:grid;grid-template-columns:repeat(3,1fr);gap:12px}
.template{background:var(--panel);border:1px solid var(--line);border-radius:14px;padding:16px;text-align:left;color:var(--text)}
.template:hover{border-color:var(--lime);transform:translateY(-2px)}
.template-art{height:90px;border-radius:9px;margin-bottom:13px;display:grid;place-items:center;font-size:30px;background:linear-gradient(135deg,#35452d,#161c13)}
.template:nth-child(2) .template-art{background:linear-gradient(135deg,#493b32,#211b17)}
.template:nth-child(3) .template-art{background:linear-gradient(135deg,#303f50,#141d28)}
.template strong{font-size:12px;display:block}
.template small{color:var(--muted);font-size:10px;line-height:1.5;display:block;margin-top:5px}
.editor-layout{display:grid;grid-template-columns:1fr 1fr;gap:16px}
.editor-paper{background:#f4f0e7;color:#25271f;border-radius:13px;padding:clamp(20px,4vw,45px);min-height:460px;box-shadow:0 12px 35px #0004}
.editor-paper h2{font-family:"Playfair Display",serif;font-size:27px;color:#263421}
.editor-paper p{font-family:Georgia,serif;font-size:13px;line-height:1.9;color:#42453b;white-space:pre-wrap}
.editor-paper textarea{width:100%;min-height:290px;border:0;outline:0;resize:vertical;background:transparent;color:#42453b;font:13px/1.9 Georgia,serif}
.book-cover-large{min-height:340px;border-radius:13px;background:radial-gradient(circle at 70% 20%,#64764b,#253321 48%,#10170f);display:flex;flex-direction:column;align-items:center;justify-content:center;text-align:center;padding:35px;color:#f4f0e7}
.book-cover-large .cover-kicker{font-size:10px;letter-spacing:3px;text-transform:uppercase;color:#d5e7b8}
.book-cover-large h2{font:600 36px/1.15 "Playfair Display",serif;max-width:320px;margin:24px 0}
.book-cover-large p{font-size:11px;color:#d2d9c7}
.notice{border:1px solid #4b563c;background:#20271b;color:#c8d7b0;border-radius:11px;padding:12px 14px;font-size:11px;line-height:1.6;margin:15px 0}
.pricing-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:14px}
.price-card{background:var(--panel);border:1px solid var(--line);border-radius:17px;padding:22px}
.price-card.featured{border-color:var(--lime);background:#20271b}
.price{font-size:32px;font-weight:800;margin:17px 0 5px}
.price small{font-size:11px;color:var(--muted);font-weight:500}
.price-card ul{padding-left:18px;color:var(--muted);font-size:11px;line-height:2.2;min-height:130px}
.faq-item{border-bottom:1px solid var(--line);padding:15px 0}
.faq-item strong{font-size:12px}
.faq-item p{font-size:11px;color:var(--muted);line-height:1.7;margin:7px 0 0}
.toast{position:fixed;bottom:22px;left:50%;transform:translateX(-50%);background:var(--lime);color:#11150d;padding:12px 18px;border-radius:10px;font-size:12px;font-weight:800;z-index:20;display:none;box-shadow:0 8px 30px #0008}
.mobile-nav{display:none}
.footer-note{font-size:10px;color:#72796b;text-align:center;margin-top:40px;line-height:1.7}
@media(max-width:900px){
 .sidebar{width:215px}.main{margin-left:215px;width:calc(100% - 215px)}
 .stats{grid-template-columns:repeat(2,1fr)}.grid-two{grid-template-columns:1fr}
}
@media(max-width:650px){
 .sidebar{display:none}.main{margin:0;width:100%;padding-bottom:65px}
 .topbar{height:60px;padding:0 17px}.mobile-brand{display:flex;align-items:center;gap:8px;font-weight:800;font-size:14px}
 .mobile-brand .brand-mark{width:29px;height:29px;font-size:15px}
 .topbar-left{display:none}.status{font-size:9px}
 .content{padding:27px 16px 50px}
 .hero{display:block}.hero-actions{margin-top:18px}
 .stats{gap:9px}.stat{padding:14px}.stat-value{font-size:23px}
 .templates{grid-template-columns:1fr 1fr}.template:last-child{display:none}
 .editor-layout{grid-template-columns:1fr}.field-row{grid-template-columns:1fr}
 .pricing-grid{grid-template-columns:1fr}
 .book-actions .btn{padding:7px;font-size:10px}
 .mobile-nav{position:fixed;bottom:0;left:0;right:0;z-index:10;background:#151813;border-top:1px solid var(--line);display:flex;justify-content:space-around;padding:8px 3px calc(8px + env(safe-area-inset-bottom))}
 .mobile-nav button{border:0;background:transparent;color:#92998a;font-size:9px;display:flex;flex-direction:column;align-items:center;gap:4px}
 .mobile-nav button.active{color:var(--lime)}.mobile-nav b{font-size:17px}
}
</style>
</head>
<body>
<div class="app">
<aside class="sidebar">
  <div class="brand"><div class="brand-mark">B</div><div><div class="brand-name">Book Studio</div><div class="brand-sub">YOUR IDEAS, IN PRINT</div></div></div>
  <div class="nav-label">WORKSPACE</div>
  <nav class="nav">
    <button class="active" data-page="dashboard"><span class="ico">⌂</span>Overview</button>
    <button data-page="create"><span class="ico">✦</span>Create an ebook</button>
    <button data-page="library"><span class="ico">▤</span>My library</button>
    <button data-page="templates"><span class="ico">▦</span>Templates</button>
  </nav>
  <div class="nav-label">PREFERENCES</div>
  <nav class="nav">
    <button data-page="pricing"><span class="ico">◇</span>Plans & credits</button>
    <button data-page="account"><span class="ico">⚙</span>Settings</button>
    <button data-page="help"><span class="ico">?</span>Help center</button>
  </nav>
  <div class="sidebar-bottom">
    <div class="plan-mini"><strong>Free workspace</strong><p>Your workspace is in preview mode. Connect an account and plan later.</p><button onclick="go('pricing')">Explore plans</button></div>
    <div class="profile"><div class="avatar">Y</div><div><strong style="font-size:12px">Your workspace</strong><small>Preview account</small></div></div>
  </div>
</aside>

<main class="main">
<header class="topbar">
  <div class="mobile-brand"><div class="brand-mark">B</div>Book Studio</div>
  <div class="topbar-left">Workspace / <span id="crumb">Overview</span></div>
  <div class="topbar-right"><span class="status">● FRONTEND PREVIEW</span></div>
</header>

<div class="content">
<section class="page active" id="dashboard">
  <div class="hero">
    <div><div class="eyebrow">YOUR CREATIVE WORKSPACE</div><h1>Turn your ideas into <span style="color:var(--lime)">ebooks.</span></h1><p class="sub">Plan, write, shape and prepare your next great book — all in one place.</p></div>
    <div class="hero-actions"><button class="btn" onclick="go('library')">My library</button><button class="btn primary" onclick="go('create')">＋ Create new ebook</button></div>
  </div>
  <div class="stats">
    <div class="stat"><div class="stat-label">Total projects</div><div class="stat-value" id="stat-books">0</div><div class="stat-note">In your library</div></div>
    <div class="stat"><div class="stat-label">Completed drafts</div><div class="stat-value" id="stat-drafts">0</div><div class="stat-note">Ready for review</div></div>
    <div class="stat"><div class="stat-label">Words written</div><div class="stat-value" id="stat-words">0</div><div class="stat-note">Across your projects</div></div>
    <div class="stat"><div class="stat-label">Available credits</div><div class="stat-value">—</div><div class="stat-note">Credits activate later</div></div>
  </div>
  <div class="grid-two">
    <div class="panel"><div class="panel-head"><h2>Recent projects</h2><button class="btn small" onclick="go('library')">View all →</button></div><div id="recent-books" class="book-list"></div></div>
    <div class="panel"><div class="panel-head"><h2>Start creating</h2></div>
      <div class="quick-grid">
        <button class="quick" onclick="chooseType('Guide')"><div class="quick-icon">📘</div><strong>Step-by-step guide</strong><span>Teach something useful.</span></button>
        <button class="quick" onclick="chooseType('Workbook')"><div class="quick-icon">✍️</div><strong>Workbook</strong><span>Exercises and activities.</span></button>
        <button class="quick" onclick="chooseType('Lead magnet')"><div class="quick-icon">🎯</div><strong>Lead magnet</strong><span>A useful free resource.</span></button>
        <button class="quick" onclick="chooseType('Business ebook')"><div class="quick-icon">💼</div><strong>Business ebook</strong><span>Share your expertise.</span></button>
      </div>
    </div>
  </div>
  <div class="footer-note">This is an early frontend preview. AI writing, cloud accounts, exports and payments will be connected in later development stages.</div>
</section>

<section class="page" id="create">
  <div class="eyebrow">NEW PROJECT</div><h1>Let's make a book.</h1><p class="sub">Start with your idea. You can refine the details as you go.</p>
  <div class="panel form-card" style="margin-top:24px">
    <div class="field"><label for="book-title">What should we call your ebook?</label><input id="book-title" placeholder="e.g. The Beginner's Guide to Personal Finance"></div>
    <div class="field"><label for="book-idea">Describe your ebook idea</label><textarea id="book-idea" placeholder="Tell us what the book should teach, who it is for, and what readers should learn..."></textarea><small>More detail helps produce a more focused book when AI is connected.</small></div>
    <div class="field"><label>Choose a book type</label><div class="chips" id="type-chips">
      <button class="chip selected" data-type="Guide">Guide</button><button class="chip" data-type="Lead magnet">Lead magnet</button><button class="chip" data-type="Workbook">Workbook</button><button class="chip" data-type="Report">Report</button><button class="chip" data-type="Course">Course</button><button class="chip" data-type="Novel">Novel</button>
    </div></div>
    <div class="field-row">
      <div class="field"><label for="book-audience">Target audience</label><input id="book-audience" placeholder="e.g. Beginners, students"></div>
      <div class="field"><label for="book-language">Language</label><select id="book-language"><option>English</option><option>Hindi</option><option>Marathi</option><option>Gujarati</option><option>Tamil</option><option>Telugu</option><option>Bengali</option></select></div>
    </div>
    <div class="field-row">
      <div class="field"><label for="book-length">Book length</label><select id="book-length"><option value="Short">Short (5–7 chapters)</option><option value="Standard" selected>Standard (8–10 chapters)</option><option value="Detailed">Detailed (12–15 chapters)</option></select></div>
      <div class="field"><label for="book-tone">Writing tone</label><select id="book-tone"><option>Friendly and simple</option><option>Professional</option><option>Educational</option><option>Inspirational</option><option>Conversational</option></select></div>
    </div>
    <div class="notice">Preview mode: creating a project will save a sample draft in this browser. Real chapter generation will be enabled after the AI backend is connected.</div>
    <button class="btn primary" style="width:100%;padding:14px" onclick="createBook()">Create my project →</button>
  </div>
</section>

<section class="page" id="library">
  <div class="hero"><div><div class="eyebrow">YOUR WORK</div><h1>My library</h1><p class="sub">Every project you create, together in one place.</p></div><button class="btn primary" onclick="go('create')">＋ New ebook</button></div>
  <div class="panel"><div class="panel-head"><h2>All projects</h2><span class="sub" id="library-count">0 projects</span></div><div id="all-books" class="book-list"></div></div>
</section>

<section class="page" id="templates">
  <div class="eyebrow">GET STARTED FASTER</div><h1>Choose a starting point.</h1><p class="sub">Pick a format and we'll prefill your new project.</p>
  <div class="templates" style="margin-top:25px">
    <button class="template" onclick="useTemplate('Beginner’s Guide','A practical step-by-step guide for beginners, with clear explanations and examples.','Guide')"><div class="template-art">📗</div><strong>Beginner's guide</strong><small>Explain a topic clearly, one step at a time.</small></button>
    <button class="template" onclick="useTemplate('The Complete Workbook','An interactive workbook with exercises, reflection questions and practical activities.','Workbook')"><div class="template-art">📝</div><strong>Interactive workbook</strong><small>Help readers learn through practice.</small></button>
    <button class="template" onclick="useTemplate('The Essential Report','A structured report with an executive summary, key findings and recommendations.','Report')"><div class="template-art">📊</div><strong>Professional report</strong><small>Present research and useful insights.</small></button>
    <button class="template" onclick="useTemplate('A Practical Business Guide','A business-focused ebook with actionable frameworks and examples.','Business ebook')"><div class="template-art">💼</div><strong>Business ebook</strong><small>Share expertise with customers.</small></button>
    <button class="template" onclick="useTemplate('The Quick Start Checklist','A concise resource with checklists, quick wins and next steps.','Lead magnet')"><div class="template-art">☑️</div><strong>Quick-start resource</strong><small>Create a useful downloadable freebie.</small></button>
    <button class="template" onclick="useTemplate('A Learning Course','A structured learning course divided into lessons, activities and recaps.','Course')"><div class="template-art">🎓</div><strong>Mini course</strong><small>Turn your knowledge into lessons.</small></button>
  </div>
</section>

<section class="page" id="editor">
  <div class="hero"><div><div class="eyebrow">PROJECT EDITOR</div><h1 id="editor-title">Your ebook</h1><p class="sub" id="editor-meta">Draft project</p></div><div class="hero-actions"><button class="btn" onclick="go('library')">← Library</button><button class="btn primary" onclick="saveEditor()">Save changes</button></div></div>
  <div class="notice">You can edit this sample content now. AI chapter writing and PDF/EPUB/DOCX exports will be added in later stages.</div>
  <div class="editor-layout">
    <div class="panel"><div class="panel-head"><h3>Book content</h3><span class="sub">Editable draft</span></div>
      <div class="field"><label>Book title</label><input id="edit-title"></div>
      <div class="field"><label>Subtitle</label><input id="edit-subtitle"></div>
      <div class="field"><label>Chapter / introduction</label><textarea id="edit-body" style="min-height:330px"></textarea></div>
      <button class="btn primary" onclick="saveEditor()">Save draft</button>
    </div>
    <div><div class="panel" style="margin-bottom:15px"><div class="panel-head"><h3>Cover preview</h3></div><div class="book-cover-large"><div class="cover-kicker">A practical guide</div><h2 id="cover-title">Your ebook title</h2><p id="cover-subtitle">A guide to getting started</p></div></div>
      <div class="panel"><h3>Project details</h3><p class="sub" id="project-details">Your project information will appear here.</p><button class="btn danger small" onclick="deleteCurrent()">Delete this project</button></div>
    </div>
  </div>
</section>

<section class="page" id="pricing">
  <div class="eyebrow">SIMPLE, TRANSPARENT PLANS</div><h1>Choose how you create.</h1><p class="sub">These are example plan layouts for the frontend. Final INR prices and credits will be decided after AI costs are tested.</p>
  <div class="pricing-grid" style="margin-top:25px">
    <div class="price-card"><div class="eyebrow">STARTER</div><h2>Explore</h2><div class="price">Free</div><p class="sub">Try the workspace and plan your first book.</p><ul><li>Book planning</li><li>Basic templates</li><li>Draft preview</li><li>Limited AI credits — later</li></ul><button class="btn" style="width:100%" onclick="toast('You are viewing the free preview plan.')">Current preview</button></div>
    <div class="price-card featured"><div class="eyebrow">MOST POPULAR</div><h2>Creator</h2><div class="price">₹— <small>/ month</small></div><p class="sub">For regular ebook creators.</p><ul><li>More AI writing credits</li><li>Full ebook generation</li><li>Editing and regeneration</li><li>Download formats</li></ul><button class="btn primary" style="width:100%" onclick="toast('Payments will be connected after testing.')">Coming later</button></div>
    <div class="price-card"><div class="eyebrow">ADVANCED</div><h2>Studio</h2><div class="price">₹— <small>/ month</small></div><p class="sub">For creators with larger projects.</p><ul><li>Higher credit allowance</li><li>Advanced workflows</li><li>More export options</li><li>Priority project tools</li></ul><button class="btn" style="width:100%" onclick="toast('This plan is not active yet.')">Coming later</button></div>
  </div>
  <div class="notice">No real subscription or payment is active in this prototype. We will decide pricing after measuring the actual cost of generating books.</div>
</section>

<section class="page" id="account">
  <div class="eyebrow">PREFERENCES</div><h1>Workspace settings</h1><p class="sub">Account features will be connected when authentication is implemented.</p>
  <div class="panel" style="max-width:700px;margin-top:22px">
    <h3>Profile</h3><div class="field"><label>Workspace name</label><input value="My workspace" disabled></div>
    <div class="field"><label>Email address</label><input value="Not connected yet" disabled></div>
    <div class="field"><label>Sign-in method</label><input value="Phone OTP — planned" disabled></div>
    <div class="notice">This preview does not create a real user account. Your sample projects are stored only in this browser.</div>
  </div>
</section>

<section class="page" id="help">
  <div class="eyebrow">SUPPORT</div><h1>Help center</h1><p class="sub">A few answers about this early version.</p>
  <div class="panel" style="max-width:800px;margin-top:22px">
    <div class="faq-item"><strong>Can I generate a real ebook right now?</strong><p>Not yet. This version tests the interface and project workflow. Gemini will be connected in a later stage.</p></div>
    <div class="faq-item"><strong>Where are my projects saved?</strong><p>They are saved in this browser on this device. They are not synced to an online account yet.</p></div>
    <div class="faq-item"><strong>Can I download PDF, EPUB or DOCX?</strong><p>Export tools are not connected yet. We will implement and test them after the writing workflow.</p></div>
    <div class="faq-item"><strong>Will I be charged?</strong><p>No. This prototype has no payment integration and cannot charge you.</p></div>
    <div class="faq-item"><strong>What happens next?</strong><p>We will test the frontend, connect the AI backend, add database storage, file storage and then payments.</p></div>
  </div>
</section>
</div>
</main>
</div>

<nav class="mobile-nav">
  <button class="active" data-page="dashboard"><b>⌂</b>Home</button>
  <button data-page="create"><b>✦</b>Create</button>
  <button data-page="library"><b>▤</b>Library</button>
  <button data-page="templates"><b>▦</b>Templates</button>
  <button data-page="account"><b>⚙</b>Settings</button>
</nav>
<div class="toast" id="toast"></div>

<script>
const KEY="bookstudio_projects_v1";
let books=JSON.parse(localStorage.getItem(KEY)||"[]");
let currentId=null;
let selectedType="Guide";

function persist(){localStorage.setItem(KEY,JSON.stringify(books));renderBooks();updateStats()}
function toast(message){
  const el=document.getElementById("toast");el.textContent=message;el.style.display="block";
  clearTimeout(window.toastTimer);window.toastTimer=setTimeout(()=>el.style.display="none",2400);
}
function go(page){
  document.querySelectorAll(".page").forEach(p=>p.classList.toggle("active",p.id===page));
  document.querySelectorAll("[data-page]").forEach(b=>b.classList.toggle("active",b.dataset.page===page));
  const names={dashboard:"Overview",create:"Create an ebook",library:"My library",templates:"Templates",editor:"Editor",pricing:"Plans & credits",account:"Settings",help:"Help center"};
  document.getElementById("crumb").textContent=names[page]||page;
  window.scrollTo({top:0,behavior:"smooth"});
}
document.querySelectorAll("[data-page]").forEach(b=>b.addEventListener("click",()=>go(b.dataset.page)));
document.querySelectorAll("#type-chips .chip").forEach(b=>b.addEventListener("click",()=>{
  document.querySelectorAll("#type-chips .chip").forEach(x=>x.classList.remove("selected"));
  b.classList.add("selected");selectedType=b.dataset.type;
}));
function chooseType(type){
  selectedType=type;
  document.querySelectorAll("#type-chips .chip").forEach(x=>x.classList.toggle("selected",x.dataset.type===type));
  go("create");
}
function useTemplate(title,idea,type){
  document.getElementById("book-title").value=title;
  document.getElementById("book-idea").value=idea;
  chooseType(type);
}
function makeSampleBody(title,idea,audience){
  return `Introduction\n\nWelcome to ${title}.\n\n${idea}\n\nThis book is designed for ${audience||"readers who want to learn the subject"}. It will help you understand the main ideas, build a foundation and identify practical next steps.\n\nChapter 1 — Understanding the basics\n\nEvery useful learning journey begins with a clear understanding of the basics. Start by identifying what you already know, what you want to learn and why the topic matters to you.\n\nKey points to remember:\n• Understand the central idea before moving to advanced topics.\n• Break large goals into smaller steps.\n• Use examples to connect ideas with real situations.\n\nChapter 2 — Turning knowledge into action\n\nLearning becomes more valuable when you apply it. Choose one small action you can take, practise it consistently and review what you learn. Keep notes about questions that need further research.\n\nChapter 3 — Your next steps\n\nCreate a simple action plan. Decide what you will practise, how you will measure progress and when you will review your results.\n\nConclusion\n\nYou now have a starting framework. Continue learning, check important facts and adapt the ideas to your own situation.`;
}
function createBook(){
  const title=document.getElementById("book-title").value.trim();
  const idea=document.getElementById("book-idea").value.trim();
  const audience=document.getElementById("book-audience").value.trim();
  if(!title||!idea){toast("Please add a title and describe your idea.");return}
  const book={
    id:Date.now().toString(),title,idea,audience,type:selectedType,
    language:document.getElementById("book-language").value,
    length:document.getElementById("book-length").value,
    tone:document.getElementById("book-tone").value,
    subtitle:"A practical guide to getting started",
    body:makeSampleBody(title,idea,audience),
    created:new Date().toISOString()
  };
  books.unshift(book);currentId=book.id;persist();openEditor(book.id);
  toast("Sample project created!");
}
function renderBooks(){
  const recent=document.getElementById("recent-books");
  const all=document.getElementById("all-books");
  document.getElementById("library-count").textContent=books.length+" project"+(books.length===1?"":"s");
  const row=b=>`<div class="book-row"><div class="cover">${escapeHTML(b.title.slice(0,35))}</div><div class="book-info"><strong>${escapeHTML(b.title)}</strong><small>${escapeHTML(b.type)} · ${new Date(b.created).toLocaleDateString()}</small></div><div class="book-actions"><button class="btn small" onclick="openEditor('${b.id}')">Open</button></div></div>`;
  recent.innerHTML=books.length?books.slice(0,4).map(row).join(""):'<div class="empty">No projects yet.<br>Create your first ebook to see it here.</div>';
  all.innerHTML=books.length?books.map(row).join(""):'<div class="empty">Your library is empty.<br>Start with your first ebook project.</div>';
}
function updateStats(){
  document.getElementById("stat-books").textContent=books.length;
  document.getElementById("stat-drafts").textContent=books.length;
  const words=books.reduce((n,b)=>n+(b.body||"").trim().split(/\s+/).filter(Boolean).length,0);
  document.getElementById("stat-words").textContent=words.toLocaleString();
}
function escapeHTML(s){
  return String(s).replace(/[&<>"']/g,c=>({"&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;","'":"&#39;"}[c]));
}
function openEditor(id){
  const b=books.find(x=>x.id===id);if(!b)return;
  currentId=id;
  document.getElementById("editor-title").textContent=b.title;
  document.getElementById("editor-meta").textContent=b.type+" · "+b.language+" · "+b.length+" book";
  document.getElementById("edit-title").value=b.title;
  document.getElementById("edit-subtitle").value=b.subtitle||"";
  document.getElementById("edit-body").value=b.body||"";
  document.getElementById("cover-title").textContent=b.title;
  document.getElementById("cover-subtitle").textContent=b.subtitle||"";
  document.getElementById("project-details").textContent=`Type: ${b.type} · Audience: ${b.audience||"Not specified"} · Tone: ${b.tone} · Language: ${b.language}`;
  go("editor");
}
function saveEditor(){
  const b=books.find(x=>x.id===currentId);if(!b)return;
  b.title=document.getElementById("edit-title").value.trim()||"Untitled ebook";
  b.subtitle=document.getElementById("edit-subtitle").value.trim();
  b.body=document.getElementById("edit-body").value;
  persist();openEditor(currentId);toast("Your draft has been saved on this device.");
}
function deleteCurrent(){
  if(!currentId)return;
  if(!confirm("Delete this project from this browser?"))return;
  books=books.filter(x=>x.id!==currentId);currentId=null;persist();go("library");toast("Project deleted.");
}
document.getElementById("edit-title").addEventListener("input",e=>document.getElementById("cover-title").textContent=e.target.value||"Your ebook title");
document.getElementById("edit-subtitle").addEventListener("input",e=>document.getElementById("cover-subtitle").textContent=e.target.value);
renderBooks();updateStats();
</script>
</body>
</html>
