
<html lang="th">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>เส้นทางการเรียนรู้ E-Health / E-Health Learning Pathway Game</title>
  <style>
    :root{
      --bg:#f3f7fb; --card:#fff; --accent:#2d87f0; --muted:#6b7280; --success:#16a34a;
      font-family: Inter, ui-sans-serif, system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;
    }
    body{ margin:0; background:var(--bg); color:#0f172a; }
    header{ background:linear-gradient(90deg,#0ea5e9, #2d87f0); color:white; padding:18px 20px; display:flex; align-items:center; justify-content:space-between;}
    header h1{ margin:0; font-size:18px; }
    header p{ margin:0; font-size:13px; opacity:0.95;}
    .container{ max-width:1100px; margin:20px auto; padding:0 16px; }
    .grid{ display:grid; gap:16px; }
    .home-grid{ grid-template-columns: 1fr 320px; }
    .card{ background:var(--card); border-radius:10px; padding:16px; box-shadow:0 6px 18px rgba(15,23,42,0.06);}
    .levels{ display:flex; gap:12px; flex-wrap:wrap; }
    .level-btn{ background:linear-gradient(180deg,#fff,#f8fafc); border:1px solid #e6eefc; padding:12px 14px; border-radius:8px; cursor:pointer; min-width:140px; text-align:left;}
    .level-btn.locked{ opacity:0.5; filter:grayscale(30%); }
    .muted{ color:var(--muted); }
    .center{ text-align:center; }
    .hidden{ display:none; }
    nav .nav-btn{ background:transparent; border:1px solid rgba(255,255,255,0.15); padding:8px 10px; color:white; border-radius:8px; cursor:pointer;}
    .progress{ height:12px; background:#e6eefc; border-radius:999px; overflow:hidden; }
    .progress > i{ display:block; height:100%; background:linear-gradient(90deg,var(--accent),#06b6d4); width:0%; transition:width .6s ease; }
    .stars{ display:flex; gap:6px; align-items:center; justify-content:center; }
    .star{ color:gold; font-size:18px; opacity:0.2; }
    .star.on{ opacity:1; }
    .badge-list{ display:flex; gap:8px; flex-wrap:wrap; }
    .badge{ padding:8px 10px; border-radius:8px; background:#fff; border:1px dashed #e6eefc; display:flex; gap:8px; align-items:center; font-size:13px;}
    .btn{ background:var(--accent); color:white; padding:10px 12px; border-radius:8px; border:0; cursor:pointer;}
    .btn.ghost{ background:transparent; border:1px solid #e6eefc; color:var(--accent); }
    .small{ font-size:13px; padding:6px 8px; }
    .level-banner{ padding:12px; border-radius:10px; }
    footer{ text-align:center; color:var(--muted); font-size:13px; margin:24px 0;}
    /* Simple responsive */
    @media (max-width:900px){
      .home-grid{ grid-template-columns: 1fr; }
      .levels{ justify-content:center; }
    }
    /* Game area */
    .game-area{ min-height:260px; display:flex; flex-direction:column; gap:12px; }
    .question{ font-weight:600; }
    .answers{ display:flex; flex-direction:column; gap:8px; }
    .answer{ padding:10px; border-radius:8px; border:1px solid #e6eefc; background:#fff; cursor:pointer; }
    .answer.correct{ background:#dcfce7; border-color:#a7f3d0; }
    .answer.wrong{ background:#fff1f2; border-color:#fecaca; }
    .meta{ display:flex; gap:12px; align-items:center; flex-wrap:wrap; }
    .notif{ background: linear-gradient(90deg,#fef3c7,#fde68a); padding:10px; border-radius:8px; }
    .topbar{ display:flex; gap:12px; align-items:center; }
    /* small helper */
    .kbd{ font-family:monospace; background:#0f172a; color:white; padding:4px 8px; border-radius:6px; font-size:12px;}
  </style>
</head>
<body>
  <header>
    <div>
      <h1>เส้นทางการเรียนรู้ E-Health • E-Health Learning Pathway</h1>
      <p>เกมการเรียนรู้เชิงเส้น (Pathway Game) เพื่อพัฒนาทักษะการใช้ข้อมูลสุขภาพดิจิทัล</p>
    </div>
    <div class="topbar">
      <button class="nav-btn" onclick="showPage('home')">Home</button>
      <button class="nav-btn" onclick="showPage('levels')">Levels</button>
      <button class="nav-btn" onclick="showPage('dashboard')">Dashboard</button>
      <button class="nav-btn" onclick="showPage('profile')">Profile</button>
    </div>
  </header>

  <main class="container">
    <!-- Page: Home -->
    <section id="page-home" class="grid home-grid">
      <div class="card">
        <h2>แนะนำเกม / Game Overview</h2>
        <p><strong>ชื่อเกม (ไทย / อังกฤษ):</strong> เส้นทางการเรียนรู้ E-Health (E-Health Learning Pathway)</p>

        <!-- 2) แนวคิด (Concept / Core Mechanic) -->
        <h3>แนวคิด (Concept / Core Mechanic)</h3>
        <p class="muted">
          เกมนี้ออกแบบมาเป็น Pathway — ผู้เล่นจะเดินผ่าน 6 ด่าน โดยแต่ละด่านเป็นชุดกิจกรรมย่อย
          ที่ผสมผสานการตอบคำถาม, เกมจับผิด, การเรียงลำดับการตรวจสอบข้อมูล และการจำลองการตัดสินใจ
          ผู้เล่นสะสมคะแนน รับเหรียญตรา และเลื่อนความก้าวหน้าจากด่าน 1 → 6
        </p>

        <!-- 3) โครงสร้างเกมแบบ Pathway (Level 1 → Level 6) -->
        <h3>โครงสร้างเกมแบบ Pathway (Levels)</h3>
        <div class="levels" id="level-list">
          <!-- Levels will be rendered by JS -->
        </div>

        <hr />
        <div class="meta" style="margin-top:8px;">
          <div style="flex:1;">
            <h4>ระบบคะแนน (Point System)</h4>
            <p class="muted">ตอบถูกได้คะแนน (เช่น +10), ทำกิจกรรมสำเร็จได้คะแนนโบนัส, ให้ดาวสำหรับคะแนนต่อด่าน</p>
          </div>
          <div style="width:220px;">
            <h4>ระบบเหรียญตรา (Badges)</h4>
            <div class="badge-list" id="badges-brief"></div>
          </div>
        </div>
      </div>

      <aside class="card">
        <h3>แผงแจ้งเตือน / Weekly Missions</h3>
        <div id="notifications" class="notif">
          <!-- Weekly notifications injected here -->
        </div>
        <hr />
        <h4>Progress</h4>
        <div class="progress" style="margin:8px 0;">
          <i id="global-progress" style="width:0%"></i>
        </div>
        <div class="stars" id="global-stars">
          <!-- stars -->
        </div>
        <hr />
        <h4>เมนูด่วน</h4>
        <button class="btn small" onclick="showPage('levels')">ไปเลือกด่าน / Choose Level</button>
        <button class="btn small ghost" onclick="showPage('dashboard')">ไปดูแดชบอร์ด / Dashboard</button>
      </aside>
    </section>

    <!-- Page: Level Selection -->
    <section id="page-levels" class="hidden">
      <div class="card">
        <h2>เลือกด่าน / Level Selection</h2>
        <p class="muted">เดินตามเส้นทางจาก ด่าน 1 → ด่าน 6. ด่านถัดไปจะปลดล็อกเมื่อทำเงื่อนไขสำเร็จ</p>
        <div class="levels" id="levels-panel"></div>
      </div>
    </section>

    <!-- Page: Game Play -->
    <section id="page-game" class="hidden">
      <div class="card">
        <button class="btn small ghost" onclick="backToLevels()">← กลับ / Back</button>
        <div id="game-header" class="level-banner">
          <!-- dynamic -->
        </div>
        <div class="game-area card" id="game-area">
          <!-- dynamic game content -->
        </div>
        <div style="display:flex; gap:8px; justify-content:flex-end; margin-top:8px;">
          <button class="btn" id="finish-btn" onclick="finishLevel()">ส่งผลลัพธ์ / Finish</button>
        </div>
      </div>
    </section>

    <!-- Page: Profile -->
    <section id="page-profile" class="hidden">
      <div class="card">
        <h2>Profile • โปรไฟล์</h2>
        <p><strong>ผู้เล่น:</strong> <span id="player-name">นักเรียน</span></p>
        <p><strong>คะแนนรวม / Points:</strong> <span id="player-points">0</span></p>
        <h4>เหรียญตราที่ได้รับ</h4>
        <div class="badge-list" id="badges-panel"></div>
      </div>
    </section>

    <!-- Page: Dashboard -->
    <section id="page-dashboard" class="hidden">
      <div class="card">
        <h2>แดชบอร์ดความก้าวหน้า / Progress Dashboard</h2>
        <p class="muted">ภาพรวมการเรียนรู้, ความก้าวหน้า, ดาว และเป้าหมายประจำสัปดาห์</p>

        <div style="display:flex; gap:12px; flex-wrap:wrap; margin-top:12px;">
          <div style="flex:1; min-width:260px;" class="card">
            <h4>ความก้าวหน้าโดยรวม</h4>
            <div class="progress" style="margin:8px 0;"><i id="dash-progress" style="width:0%"></i></div>
            <p class="muted">Completed levels: <span id="completed-levels">0</span>/6</p>
            <div class="stars" id="dash-stars"></div>
          </div>

          <div style="width:320px;" class="card">
            <h4>ภารกิจประจำสัปดาห์</h4>
            <ul id="weekly-missions">
              <!-- list -->
            </ul>
            <button class="btn small" onclick="claimWeekly()">กดทำภารกิจนี้ / Start Weekly Mission</button>
          </div>
        </div>
      </div>
    </section>
  </main>

  <footer>
    © E-Health Learning Pathway • ตัวอย่างต้นแบบ (Prototype)
  </footer>

  <script>
    /*
      This single-file prototype includes:
      1) Game name (Thai + English) - displayed at top
      2) Concept/core mechanic - described on Home
      3) Pathway 6 levels - see levelsData
      4) Details of each level (titles + descriptions)
      5) Missions per level
      6) Example mini-activities per level (simple interactive demos)
      7) Point system (points stored in localStorage)
      8) Badge system (unlock on milestones)
      9) Progress bar & stars
      10) Weekly notifications (localStorage-based demo)
      11) Basic UX pages: Home, Levels, Game, Profile, Dashboard
    */

    // --- Game Definitions (levels, missions, activities) ---
    const levelsData = [
      {
        id:1,
        titleTh:"พื้นฐานทักษะสุขภาพดิจิทัล",
        titleEn:"Basic Digital Health Literacy",
        mission:"เรียนรู้คำศัพท์พื้นฐานและเลือกคำตอบที่ถูกต้อง",
        activity:"MCQ Quiz: คำถามพื้นฐาน",
        description:"เก็บคะแนนจากการตอบคำถามเกี่ยวกับทักษะดิจิทัลด้านสุขภาพ",
        gameType:"mcq",
        questions:[
          { q:"คำว่า 'eHealth' หมายถึงอะไร?", choices:["การดูแลสุขภาพผ่านเทคโนโลยีดิจิทัล","การออกกำลังกายแบบเฉพาะ","โภชนาการแผนที่"], a:0 },
          { q:"ข้อมูลสุขภาพที่เป็นความลับต้องทำอย่างไร?", choices:["เผยแพร่บนโซเชียล","เก็บเป็นส่วนตัวและปฏิบัติตามนโยบายความเป็นส่วนตัว","ส่งต่อให้ทุกคน"], a:1 }
        ],
      },
      {
        id:2,
        titleTh:"ค้นหาและประเมินข้อมูล",
        titleEn:"Information Search & Evaluation",
        mission:"เรียงลำดับขั้นตอนการตรวจสอบแหล่งข้อมูล",
        activity:"Ordering Steps Game",
        description:"ผู้เล่นต้องนำขั้นตอนการตรวจสอบคำข่าวมาวางในลำดับที่ถูกต้อง",
        gameType:"ordering",
        steps:["หาแหล่งที่มาของข้อมูล","ตรวจสอบความเชื่อถือได้ของแหล่ง","เปรียบเทียบกับแหล่งอื่น","สรุปและจัดเก็บ"]
      },
      {
        id:3,
        titleTh:"การระบุข่าวลวงสุขภาพ",
        titleEn:"Identifying Fake Health News",
        mission:"จับผิดข่าวลวง: เลือกว่าข่าวจริง/ข่าวปลอม",
        activity:"Spot the Fake News",
        description:"เกมจับผิดข่าวลวงสุขภาพ เลือกว่าประกาศเป็นจริงหรือปลอม",
        gameType:"truefalse",
        items:[
          { t:"ผลิตภัณฑ์นี้รักษาโรค X ได้ 100%", v:false },
          { t:"การฉีดวัคซีนสามารถลดความเสี่ยงได้", v:true }
        ]
      },
      {
        id:4,
        titleTh:"การอ่านฉลากโภชนาการ",
        titleEn:"Nutrition & Health Data Interpretation",
        mission:"อ่านฉลากแล้วตอบคำถามเชิงตัวเลข",
        activity:"Nutrition Label Quiz",
        description:"ฝึกอ่านฉลากโภชนาการและตีความค่าต่าง ๆ",
        gameType:"nutrition",
        items:[
          { q:"ถ้าขนาดต่อหน่วยรับประทาน 100g และพลังงาน 250 kcal per serving, ถ้าทาน 200g จะได้พลังงานกี่ kcal?", a:"500" }
        ]
      },
      {
        id:5,
        titleTh:"การจัดการสุขภาวะดิจิทัลตนเอง",
        titleEn:"Digital Well-being Self-Management",
        mission:"จัดการเวลาหน้าจอและตั้งเป้าการใช้ข้อมูลสุขภาพ",
        activity:"Checklist & Goal Setting",
        description:"เกมแบบ checklist และตั้งเป้าการใช้แอปสุขภาพ",
        gameType:"checklist",
        items:["จำกัดเวลาแอปสุขภาพ 30 นาที/วัน","ตั้งการแจ้งเตือนเพื่อตรวจสอบอาการ","บันทึกอาการอย่างสม่ำเสมอ"]
      },
      {
        id:6,
        titleTh:"จำลองการตัดสินใจด้านสุขภาพ",
        titleEn:"Health Decision-Making Simulation",
        mission:"ตัดสินใจเลือกแหล่งข้อมูลที่เหมาะสมผ่าน Decision Tree",
        activity:"Decision Tree Game",
        description:"จำลองสถานการณ์และเลือกเส้นทางเพื่อผลลัพธ์ที่ดีที่สุด",
        gameType:"decision",
        tree:{
          q:"อาการ X ปรากฏ คุณจะทำอย่างไรเป็นอันดับแรก?",
          options:[
            { t:"ค้นหาในโซเชียลมีเดีย", good:false },
            { t:"เช็คแหล่งข้อมูลจากหน่วยงานสาธารณสุข", good:true },
            { t:"ถามเพื่อนในกลุ่ม", good:false }
          ]
        }
      }
    ];

    // --- State and Storage Utilities ---
    const STORAGE = {
      pointsKey: "ehl_points",
      badgesKey: "ehl_badges",
      progressKey: "ehl_progress", // {levelId: {completed:true, stars: n}}
      lastNotifyKey: "ehl_lastNotify",
      playerNameKey: "ehl_playerName"
    };

    function loadPoints(){ return parseInt(localStorage.getItem(STORAGE.pointsKey) || "0",10); }
    function savePoints(v){ localStorage.setItem(STORAGE.pointsKey, String(v)); updateUI(); }
    function addPoints(n){ savePoints(loadPoints()+n); }
    function loadBadges(){ return JSON.parse(localStorage.getItem(STORAGE.badgesKey) || "[]"); }
    function saveBadges(arr){ localStorage.setItem(STORAGE.badgesKey, JSON.stringify(arr)); updateUI(); }
    function addBadge(b){ const bs=loadBadges(); if(!bs.includes(b)){ bs.push(b); saveBadges(bs); } }
    function loadProgress(){ return JSON.parse(localStorage.getItem(STORAGE.progressKey) || "{}"); }
    function saveProgress(p){ localStorage.setItem(STORAGE.progressKey, JSON.stringify(p)); updateUI(); }
    function setLevelCompleted(id,stars){
      const p=loadProgress(); p[id]= { completed:true, stars:stars }; saveProgress(p);
      // award badges for milestones
      const completedCount = Object.values(p).filter(x=>x.completed).length;
      if(completedCount===1) addBadge("Beginner");
      if(completedCount>=3) addBadge("Explorer");
      if(completedCount===6) addBadge("Master");
    }

    // init player name
    if(!localStorage.getItem(STORAGE.playerNameKey)) localStorage.setItem(STORAGE.playerNameKey,"นักเรียน");

    // --- UI rendering ---
    function renderLevelButtons(){
      const container = document.getElementById("level-list");
      const panel = document.getElementById("levels-panel");
      container.innerHTML=""; panel.innerHTML="";
      const progress = loadProgress();

      levelsData.forEach(l=>{
        const completed = progress[l.id] && progress[l.id].completed;
        const unlocked = isLevelUnlocked(l.id);
        const starCount = (progress[l.id] && progress[l.id].stars) || 0;
        const el = document.createElement("div");
        el.className = "level-btn " + (unlocked ? "" : "locked");
        el.innerHTML = `<strong>ด่าน ${l.id}: ${l.titleTh}</strong>
                        <div class="muted">${l.titleEn}</div>
                        <div style="margin-top:8px;display:flex;justify-content:space-between;align-items:center;">
                          <small class="muted">${l.activity}</small>
                          <div class="stars">${renderStarsInline(starCount)}</div>
                        </div>`;
        if(unlocked) el.onclick = ()=>startLevel(l.id);
        container.appendChild(el);

        // levels panel (selection)
        const el2 = el.cloneNode(true);
        if(unlocked) el2.onclick = ()=>startLevel(l.id);
        panel.appendChild(el2);
      });
    }

    function renderStarsInline(n){
      let html="";
      for(let i=0;i<3;i++){
        html += `<span class="star ${i<n?"on":""}">★</span>`;
      }
      return html;
    }

    function updateUI(){
      document.getElementById("player-points").innerText = loadPoints();
      const badges = loadBadges();
      const badgesBrief = document.getElementById("badges-brief");
      const badgesPanel = document.getElementById("badges-panel");
      badgesBrief.innerHTML = ""; badgesPanel.innerHTML="";
      badges.forEach(b=>{
        const node = document.createElement("div"); node.className="badge"; node.innerText=b;
        badgesBrief.appendChild(node);
        badgesPanel.appendChild(node.cloneNode(true));
      });

      // progress
      const p = loadProgress();
      const completed = Object.values(p).filter(x=>x.completed).length;
      const total = levelsData.length;
      const percent = Math.round((completed/total)*100);
      document.getElementById("global-progress").style.width = percent + "%";
      document.getElementById("dash-progress").style.width = percent + "%";
      document.getElementById("completed-levels").innerText = completed;
      // stars: sum stars
      const sumStars = Object.values(p).reduce((s,x)=> s + (x ? x.stars || 0 : 0), 0);
      renderGlobalStars(sumStars);
      renderDashboardStars(sumStars);
      renderLevelButtons();
    }

    function renderGlobalStars(n){
      const el = document.getElementById("global-stars");
      el.innerHTML="";
      for(let i=0;i<3;i++){
        const s = document.createElement("div"); s.className="star " + (i<n?"on":""); s.innerText="★";
        el.appendChild(s);
      }
    }
    function renderDashboardStars(n){
      const el = document.getElementById("dash-stars");
      el.innerHTML="";
      for(let i=0;i<5;i++){
        const s = document.createElement("div"); s.className="star " + (i<n?"on":""); s.innerText="★";
        el.appendChild(s);
      }
    }

    // Level unlock logic: linear pathway
    function isLevelUnlocked(id){
      if(id===1) return true;
      const p = loadProgress();
      return p[id-1] && p[id-1].completed;
    }

    // --- Page management ---
    function showPage(page){
      document.querySelectorAll("main > section").forEach(s=>s.classList.add("hidden"));
      const element = document.getElementById("page-"+page);
      if(element) element.classList.remove("hidden");
      // special actions
      if(page==="home") updateUI();
      if(page==="levels") renderLevelButtons();
      if(page==="dashboard") renderWeeklyList();
      if(page==="profile") updateUI();
    }

    function backToLevels(){ showPage('levels'); }

    // --- Game logic for different types ---
    let currentLevel = null;
    let currentState = {}; // temp per-level

    function startLevel(id){
      const level = levelsData.find(x=>x.id===id);
      if(!level) return;
      currentLevel = level;
      currentState = { score:0, attempts:0, maxScore:0 };
      document.getElementById("game-header").innerHTML = `<h3>ด่าน ${level.id}: ${level.titleTh} <small class="muted">(${level.titleEn})</small></h3>
        <p class="muted">${level.description}</p>
        <p><strong>ภารกิจ:</strong> ${level.mission}</p>`;
      renderGameArea(level);
      showPage('game');
    }

    function renderGameArea(level){
      const area = document.getElementById("game-area");
      area.innerHTML = "";
      const meta = document.createElement("div"); meta.className="meta";
      meta.innerHTML = `<div class="muted">Activity: ${level.activity}</div><div class="muted">Type: ${level.gameType}</div>`;
      area.appendChild(meta);

      if(level.gameType === "mcq"){
        // show first question and iterate
        currentState.qIndex = 0;
        currentState.maxScore = level.questions.length * 10;
        showMCQ(level);
      } else if(level.gameType === "ordering"){
        showOrdering(level);
      } else if(level.gameType === "truefalse"){
        showTrueFalse(level);
      } else if(level.gameType === "nutrition"){
        showNutrition(level);
      } else if(level.gameType === "checklist"){
        showChecklist(level);
      } else if(level.gameType === "decision"){
        showDecision(level);
      }
    }

    // MCQ
    function showMCQ(level){
      const area = document.getElementById("game-area");
      const qObj = level.questions[currentState.qIndex];
      area.querySelectorAll(".qblock")?.forEach(n=>n.remove());
      const qblock = document.createElement("div"); qblock.className="qblock";
      qblock.innerHTML = `<div class="question">${qObj.q}</div>`;
      const answers = document.createElement("div"); answers.className="answers";
      qObj.choices.forEach((c, idx)=>{
        const a = document.createElement("div"); a.className="answer"; a.innerText = c;
        a.onclick = ()=>{
          if(idx === qObj.a){
            a.classList.add("correct"); addPoints(10); currentState.score += 10;
          } else {
            a.classList.add("wrong");
          }
          // disable siblings
          answers.querySelectorAll(".answer").forEach(s=>s.onclick=null);
          setTimeout(()=>{
            currentState.qIndex++;
            if(currentState.qIndex < level.questions.length) showMCQ(level);
            else {
              // finish MCQ
              alert("จบชุดคำถาม! คุณได้คะแนน " + currentState.score);
            }
          },700);
        };
        answers.appendChild(a);
      });
      qblock.appendChild(answers);
      area.appendChild(qblock);
    }

    // Ordering game (simple)
    function showOrdering(level){
      const area = document.getElementById("game-area");
      const shuffled = shuffle([...level.steps]);
      currentState.shuffled = shuffled;
      const list = document.createElement("ol"); list.style.paddingLeft="18px";
      shuffled.forEach((s,idx)=>{
        const li = document.createElement("li");
        li.innerHTML = `<div style="display:flex;gap:8px;align-items:center;">
                          <span class="kbd">${idx+1}</span>
                          <span>${s}</span>
                        </div>`;
        li.style.cursor="pointer";
        li.onclick = ()=>{
          // cycle number: move to end
          shuffled.push(shuffled.splice(idx,1)[0]);
          renderOrderingList(list, shuffled);
        };
        list.appendChild(li);
      });
      area.appendChild(list);
      const hint = document.createElement("div"); hint.className="muted"; hint.innerText = "กดที่รายการเพื่อเปลี่ยนลำดับ (ตัวอย่างอินเทอร์แอคชันแบบง่าย)";
      area.appendChild(hint);
      const checkBtn = document.createElement("button"); checkBtn.className="btn small"; checkBtn.innerText="ตรวจสอบคำตอบ";
      checkBtn.onclick = ()=>{
        const correct = arraysEqual(shuffled, level.steps);
        if(correct){ addPoints(20); alert("ยินดีด้วย! เรียงลำดับถูกต้อง +20 คะแนน"); currentState.score+=20; }
        else { alert("ยังไม่ถูกต้อง ลองใหม่"); }
      };
      area.appendChild(checkBtn);
    }
    function renderOrderingList(list, arr){
      list.innerHTML="";
      arr.forEach((s,idx)=>{
        const li = document.createElement("li"); li.innerHTML = `<div style="display:flex;gap:8px;align-items:center;">
                          <span class="kbd">${idx+1}</span><span>${s}</span></div>`;
        li.onclick = ()=>{
          arr.push(arr.splice(idx,1)[0];
          )};
        list.appendChild(li);
      });
    }

    // True / False game
    function showTrueFalse(level){
      const area = document.getElementById("game-area");
      level.items.forEach((it, idx)=>{
        const card = document.createElement("div"); card.className="card";
        card.style.marginBottom="8px";
        card.innerHTML = `<div class="question">${it.t}</div>`;
        const answers = document.createElement("div"); answers.className="answers";
        ["จริง / True","ปลอม / False"].forEach((label, i)=>{
          const a = document.createElement("div"); a.className="answer"; a.innerText=label;
          a.onclick = ()=>{
            const chosen = (i===0);
            if(chosen === it.v){ a.classList.add("correct"); addPoints(10); currentState.score+=10; }
            else { a.classList.add("wrong"); }
            answers.querySelectorAll(".answer").forEach(s=>s.onclick=null);
          };
          answers.appendChild(a);
        });
        card.appendChild(answers);
        area.appendChild(card);
      });
    }

    // Nutrition numeric question
    function showNutrition(level){
      const area = document.getElementById("game-area");
      level.items.forEach(it=>{
        const card = document.createElement("div"); card.className="card";
        card.innerHTML = `<div class="question">${it.q}</div>
                          <input id="nutri-input" placeholder="พิมพ์คำตอบเป็นตัวเลข" style="padding:8px;border-radius:8px;border:1px solid #e6eefc;width:120px;" />
                          <div style="margin-top:8px;"><button class="btn small" id="nutri-check">ตรวจ</button></div>`;
        area.appendChild(card);
        card.querySelector('#nutri-check').onclick = ()=>{
          const v = document.getElementById('nutri-input').value.trim();
          if(v===it.a){ addPoints(15); currentState.score+=15; alert("ถูกต้อง +15 คะแนน"); }
          else { alert("คำตอบไม่ถูกต้อง ลองใหม่"); }
        };
      });
    }

    // Checklist
    function showChecklist(level){
      const area = document.getElementById("game-area");
      const ul = document.createElement("ul");
      level.items.forEach(item=>{
        const li = document.createElement("li");
        li.innerHTML = `<label><input type="checkbox" class="chk"> ${item}</label>`;
        ul.appendChild(li);
      });
      area.appendChild(ul);
      const btn = document.createElement("button"); btn.className="btn small"; btn.innerText="บันทึกเป้าหมาย";
      btn.onclick = ()=>{
        const checks = Array.from(document.querySelectorAll('.chk')).filter(c=>c.checked).length;
        addPoints(checks*5);
        alert("บันทึกแล้ว ได้แต้ม " + (checks*5));
      };
      area.appendChild(btn);
    }

    // Decision tree
    function showDecision(level){
      const area = document.getElementById("game-area");
      const q = level.tree.q;
      const el = document.createElement("div"); el.className="card";
      el.innerHTML = `<div class="question">${q}</div>`;
      const answers = document.createElement("div"); answers.className="answers";
      level.tree.options.forEach(opt=>{
        const a = document.createElement("div"); a.className="answer"; a.innerText=opt.t;
        a.onclick = ()=>{
          if(opt.good){ a.classList.add("correct"); addPoints(25); currentState.score+=25; alert("เลือกถูก! ได้ +25 คะแนน"); }
          else { a.classList.add("wrong"); alert("การตัดสินใจนี้ไม่ดีที่สุด ลองคิดใหม่"); }
          answers.querySelectorAll(".answer").forEach(s=>s.onclick=null);
        };
        answers.appendChild(a);
      });
      el.appendChild(answers);
      area.appendChild(el);
    }

    // Helper: finish level
    function finishLevel(){
      if(!currentLevel) return;
      // assign stars based on score / max thresholds (simple heuristic)
      const score = currentState.score || 0;
      let stars = 0;
      if(score >= 25) stars = 3;
      else if(score >= 10) stars = 2;
      else if(score > 0) stars = 1;
      setLevelCompleted(currentLevel.id, stars);
      alert(`ด่าน ${currentLevel.id} เสร็จสิ้น! คะแนนที่ได้: ${score}, ดาว: ${stars}`);
      currentLevel = null;
      showPage('levels');
    }

    // --- Weekly Notifications / Missions ---
    function checkWeeklyNotifications(){
      const last = localStorage.getItem(STORAGE.lastNotifyKey);
      const now = Date.now();
      if(!last || now - parseInt(last,10) > 7*24*60*60*1000){
        // prepare weekly missions (simple example)
        const mission = generateWeeklyMission();
        localStorage.setItem(STORAGE.lastNotifyKey, String(now));
        // store missions for dashboard
        localStorage.setItem("ehl_weekly_mission", JSON.stringify(mission));
      }
      updateNotificationsPanel();
    }

    function generateWeeklyMission(){
      // choose random level to promote
      const idx = Math.floor(Math.random()*levelsData.length);
      const lv = levelsData[idx];
      const mission = {
        title:`ภารกิจสัปดาห์: ทำด่าน ${lv.id} - ${lv.titleTh}`,
        desc:`ทำให้เสร็จเพื่อรับโบนัสคะแนน +30`,
        levelId: lv.id,
        reward:30
      };
      return mission;
    }

    function updateNotificationsPanel(){
      const note = document.getElementById("notifications");
      const mission = JSON.parse(localStorage.getItem("ehl_weekly_mission") || "{}");
      if(mission && mission.title){
        note.innerHTML = `<strong>${mission.title}</strong><div class="muted" style="margin-top:6px;">${mission.desc}</div>
                          <div style="margin-top:8px;"><button class="btn small" onclick="startWeeklyMission()">เริ่มภารกิจ</button></div>`;
      } else {
        note.innerHTML = `<div class="muted">ไม่มีภารกิจประจำสัปดาห์ในขณะนี้</div>`;
      }
    }

    function startWeeklyMission(){
      const mission = JSON.parse(localStorage.getItem("ehl_weekly_mission") || "{}");
      if(mission && mission.levelId) startLevel(mission.levelId);
    }

    function claimWeekly(){
      const mission = JSON.parse(localStorage.getItem("ehl_weekly_mission") || "{}");
      if(!mission || !mission.levelId){ alert("ไม่มีภารกิจให้ทำ"); return; }
      // since this is a prototype, reward claiming happens if level completed
      const p = loadProgress();
      if(p[mission.levelId] && p[mission.levelId].completed){
        addPoints(mission.reward || 0);
        alert("ได้รับโบนัสจากภารกิจสัปดาห์ +"+(mission.reward||0)+" คะแนน");
        localStorage.removeItem("ehl_weekly_mission");
        updateNotificationsPanel();
      } else {
        alert("กรุณาทำด่านที่ภารกิจระบุให้สำเร็จก่อนจะรับโบนัส");
      }
    }

    function renderWeeklyList(){
      const ul = document.getElementById("weekly-missions"); ul.innerHTML="";
      const mission = JSON.parse(localStorage.getItem("ehl_weekly_mission") || "{}");
      if(mission && mission.title){
        const li = document.createElement("li"); li.innerHTML = `<strong>${mission.title}</strong><div class="muted">${mission.desc}</div>`;
        ul.appendChild(li);
      } else {
        const li = document.createElement("li"); li.innerHTML = `<div class="muted">ไม่มีภารกิจประจำสัปดาห์</div>`;
        ul.appendChild(li);
      }
    }

    // --- Utility functions ---
    function shuffle(a){ for(let i=a.length-1;i>0;i--){ const j=Math.floor(Math.random()*(i+1)); [a[i],a[j]]=[a[j],a[i]]; } return a; }
    function arraysEqual(a,b){ if(a.length!==b.length) return false; for(let i=0;i<a.length;i++) if(a[i]!==b[i]) return false; return true; }

    // --- Init ---
    function init(){
      renderLevelButtons();
      updateUI();
      checkWeeklyNotifications();
      // greet
      document.getElementById('player-name').innerText = localStorage.getItem(STORAGE.playerNameKey) || "นักเรียน";
      // set navigation defaults
      showPage('home');
      // small periodic UI update (for demo)
      setInterval(()=>{ updateUI(); }, 2000);
    }

    // run init
    init();

    // Expose some debugging functions to global for testers
    window.startLevel = startLevel;
    window.finishLevel = finishLevel;
    window.showPage = showPage;

    // Note: This is a prototype intended as a starting HTML that demonstrates:
    // - Game name bilingual, concept, structure (6 levels)
    // - Missions & example mini-games
    // - Point system, badges, progress bar & stars
    // - Weekly notifications mockup
    // - Basic UX pages (Home, Levels, Game, Profile, Dashboard)
    //
    // Next steps (for developer):
    // - Replace alert() with a nicer modal UI
    // - Expand content & questions, add media and illustrations
    // - Persist user profiles on backend, add authentication
    // - Add animations, drag-and-drop ordering, and detailed decision tree tracking
    // - Localize/translate strings and polish UX for mobile

  </script>
</body>
</html># Health-Me
