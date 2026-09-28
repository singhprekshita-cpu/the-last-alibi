# the-last-alibiYes — if you want a **copy-paste-ready GitHub repository**, the easiest version is a single `index.html` containing the complete game.

 Create a GitHub repository, create `index.html`, and paste this entire file into it:

```
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>The Last Alibi — Noir Detective</title>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

:root {
  --bg: #090a0d;
  --panel: #111318;
  --panel2: #181a20;
  --red: #9d2b32;
  --red-light: #d04b52;
  --gold: #c8a96b;
  --text: #eee9df;
  --muted: #898781;
  --border: #292b31;
  --green: #568c68;
}

body {
  font-family: Georgia, "Times New Roman", serif;
  background:
    radial-gradient(circle at 50% 0%, #242027 0%, transparent 35%),
    #090a0d;
  color: var(--text);
  min-height: 100vh;
}

button {
  font: inherit;
}

.hidden {
  display: none !important;
}

/* =========================
   HOME
========================= */

.home {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  padding: 30px;
  position: relative;
  overflow: hidden;
}

.home::before {
  content: "";
  position: absolute;
  inset: 0;
  background:
    linear-gradient(rgba(0,0,0,.55), rgba(0,0,0,.85)),
    repeating-linear-gradient(
      90deg,
      transparent 0,
      transparent 80px,
      rgba(255,255,255,.015) 81px
    );
  pointer-events: none;
}

.home-content {
  position: relative;
  max-width: 800px;
  z-index: 2;
}

.classified {
  display: inline-block;
  color: var(--red-light);
  border: 1px solid var(--red);
  padding: 7px 15px;
  letter-spacing: 4px;
  font-size: 11px;
  margin-bottom: 28px;
}

.logo {
  font-size: clamp(48px, 9vw, 100px);
  letter-spacing: 8px;
  line-height: .95;
  text-transform: uppercase;
  text-shadow: 0 5px 30px #000;
}

.logo span {
  color: var(--red-light);
}

.tagline {
  color: #aaa7a0;
  margin: 25px auto 40px;
  font-size: 18px;
  font-style: italic;
}

.home-buttons {
  display: flex;
  gap: 15px;
  justify-content: center;
  flex-wrap: wrap;
}

.btn {
  border: 1px solid var(--border);
  background: #15161b;
  color: var(--text);
  padding: 14px 28px;
  cursor: pointer;
  letter-spacing: 2px;
  text-transform: uppercase;
  transition: .2s;
}

.btn:hover {
  border-color: var(--red-light);
  background: #21171a;
  transform: translateY(-2px);
}

.btn.primary {
  background: var(--red);
  border-color: var(--red);
}

.btn.primary:hover {
  background: #b5363e;
}

/* =========================
   MODAL
========================= */

.modal {
  position: fixed;
  inset: 0;
  background: rgba(0,0,0,.82);
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 20px;
  z-index: 20;
}

.modal-box {
  width: min(600px, 100%);
  background: var(--panel);
  border: 1px solid var(--border);
  padding: 35px;
  box-shadow: 0 20px 80px #000;
}

.modal-box h2 {
  color: var(--gold);
  margin-bottom: 20px;
}

.modal-box p {
  color: var(--muted);
  line-height: 1.7;
  margin-bottom: 20px;
}

.input {
  width: 100%;
  padding: 14px;
  background: #090a0d;
  border: 1px solid var(--border);
  color: white;
  margin-bottom: 20px;
  outline: none;
}

.input:focus {
  border-color: var(--red-light);
}

/* =========================
   DIFFICULTY
========================= */

.difficulty-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 12px;
}

.difficulty {
  padding: 20px;
  background: #0c0d10;
  border: 1px solid var(--border);
  cursor: pointer;
  text-align: left;
  transition: .2s;
}

.difficulty:hover,
.difficulty.active {
  border-color: var(--red-light);
  background: #1b1114;
}

.difficulty strong {
  display: block;
  margin-bottom: 8px;
  color: var(--gold);
}

.difficulty small {
  color: var(--muted);
  line-height: 1.5;
}

/* =========================
   GAME
========================= */

.game {
  min-height: 100vh;
}

.topbar {
  height: 70px;
  border-bottom: 1px solid var(--border);
  background: #0c0d10;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 25px;
  position: sticky;
  top: 0;
  z-index: 10;
}

.top-title {
  letter-spacing: 3px;
}

.case-number {
  color: var(--red-light);
  font-size: 12px;
}

.game-layout {
  display: grid;
  grid-template-columns: 230px 1fr;
  min-height: calc(100vh - 70px);
}

.sidebar {
  border-right: 1px solid var(--border);
  background: #0c0d10;
  padding: 20px 12px;
}

.nav-title {
  color: var(--muted);
  font-size: 10px;
  letter-spacing: 3px;
  margin: 15px 12px;
}

.nav-btn {
  display: block;
  width: 100%;
  text-align: left;
  padding: 14px 15px;
  background: transparent;
  border: 0;
  color: #aaa;
  cursor: pointer;
  margin-bottom: 4px;
  border-left: 2px solid transparent;
}

.nav-btn:hover,
.nav-btn.active {
  background: #17181d;
  color: white;
  border-left-color: var(--red-light);
}

.main {
  padding: 35px;
  max-width: 1200px;
  width: 100%;
  margin: auto;
}

.section-title {
  font-size: 32px;
  margin-bottom: 8px;
}

.section-subtitle {
  color: var(--muted);
  margin-bottom: 30px;
}

/* =========================
   CARDS
========================= */

.card-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(230px, 1fr));
  gap: 16px;
}

.card {
  background: var(--panel);
  border: 1px solid var(--border);
  padding: 22px;
  transition: .2s;
}

.card:hover {
  border-color: #45464c;
  transform: translateY(-2px);
}

.card h3 {
  margin-bottom: 10px;
}

.card p {
  color: var(--muted);
  line-height: 1.6;
}

.tag {
  display: inline-block;
  font-size: 10px;
  letter-spacing: 1px;
  padding: 5px 8px;
  margin-bottom: 14px;
  border: 1px solid #55453a;
  color: var(--gold);
}

/* =========================
   CASE
========================= */

.case-header {
  background:
    linear-gradient(120deg, #161318, #101115);
  border: 1px solid var(--border);
  padding: 30px;
  margin-bottom: 20px;
}

.case-header .stamp {
  color: var(--red-light);
  letter-spacing: 4px;
  font-size: 11px;
  margin-bottom: 15px;
}

.case-header h2 {
  font-size: 36px;
  margin-bottom: 10px;
}

.case-details {
  display: flex;
  flex-wrap: wrap;
  gap: 25px;
  margin-top: 20px;
  color: var(--muted);
}

.case-details strong {
  color: var(--text);
}

/* =========================
   EVIDENCE
========================= */

.evidence {
  cursor: pointer;
  min-height: 170px;
}

.evidence-id {
  color: var(--red-light);
  font-size: 11px;
  letter-spacing: 2px;
}

.evidence-icon {
  font-size: 35px;
  margin: 18px 0;
}

/* =========================
   TIMELINE
========================= */

.timeline {
  border-left: 2px solid var(--red);
  margin-left: 20px;
  padding-left: 30px;
}

.timeline-item {
  position: relative;
  margin-bottom: 30px;
  background: var(--panel);
  border: 1px solid var(--border);
  padding: 18px;
}

.timeline-item::before {
  content: "";
  position: absolute;
  left: -40px;
  top: 20px;
  width: 16px;
  height: 16px;
  background: var(--red);
  border-radius: 50%;
  border: 3px solid var(--bg);
}

.time {
  color: var(--gold);
  font-size: 13px;
  margin-bottom: 8px;
}

/* =========================
   ACCUSATION
========================= */

.accusation-box {
  max-width: 700px;
  margin: auto;
  background: var(--panel);
  border: 1px solid var(--border);
  padding: 35px;
}

.accusation-box label {
  display: block;
  color: var(--muted);
  margin: 20px 0 8px;
}

select,
textarea {
  width: 100%;
  background: #090a0d;
  border: 1px solid var(--border);
  color: white;
  padding: 13px;
  outline: none;
}

textarea {
  min-height: 120px;
  resize: vertical;
}

/* =========================
   RESULT
========================= */

.result {
  text-align: center;
  max-width: 800px;
  margin: auto;
}

.result-icon {
  font-size: 70px;
  margin-bottom: 20px;
}

.result h1 {
  font-size: 50px;
  color: var(--gold);
  margin-bottom: 15px;
}

.solution {
  text-align: left;
  background: var(--panel);
  border: 1px solid var(--border);
  padding: 25px;
  margin-top: 30px;
}

.solution h3 {
  color: var(--red-light);
  margin-bottom: 10px;
}

.solution p {
  color: #aaa;
  line-height: 1.7;
  margin-bottom: 18px;
}

/* =========================
   RESPONSIVE
========================= */

@media (max-width: 750px) {

  .game-layout {
    grid-template-columns: 1fr;
  }

  .sidebar {
    display: flex;
    overflow-x: auto;
    border-right: 0;
    border-bottom: 1px solid var(--border);
    padding: 8px;
  }

  .nav-title {
    display: none;
  }

  .nav-btn {
    min-width: 130px;
    margin: 0;
    border-left: 0;
    border-bottom: 2px solid transparent;
  }

  .nav-btn.active {
    border-left: 0;
    border-bottom-color: var(--red-light);
  }

  .main {
    padding: 20px;
  }

  .topbar {
    padding: 0 15px;
  }

  .difficulty-grid {
    grid-template-columns: 1fr;
  }

  .logo {
    letter-spacing: 3px;
  }

  .case-header h2 {
    font-size: 28px;
  }
}
</style>
</head>

<body>

<!-- HOME -->
<section class="home" id="home">

  <div class="home-content">

    <div class="classified">
      CLASSIFIED • DETECTIVE DIVISION
    </div>

    <h1 class="logo">
      THE LAST <span>ALIBI</span>
    </h1>

    <p class="tagline">
      Everyone has a story. One of them is a lie.
    </p>

    <div class="home-buttons">
      <button class="btn primary" onclick="openStart()">
        Start Investigation
      </button>

      <button class="btn" onclick="showHowToPlay()">
        How To Play
      </button>
    </div>

  </div>

</section>

<!-- START MODAL -->
<div class="modal hidden" id="startModal">

  <div class="modal-box">

    <h2>OPEN CASE FILE</h2>

    <p>
      Detective, enter your name before beginning the investigation.
    </p>

    <input
      id="detectiveName"
      class="input"
      placeholder="Detective name..."
      maxlength="30"
    >

    <h3 style="margin-bottom:15px;color:#c8a96b;">
      SELECT DIFFICULTY
    </h3>

    <div class="difficulty-grid">

      <div class="difficulty active" data-difficulty="easy"
           onclick="selectDifficulty(this)">
        <strong>EASY</strong>
        <small>
          4 suspects<br>
          6 clues<br>
          3 hints
        </small>
      </div>

      <div class="difficulty" data-difficulty="medium"
           onclick="selectDifficulty(this)">
        <strong>MEDIUM</strong>
        <small>
          5 suspects<br>
          9 clues<br>
          2 hints
        </small>
      </div>

      <div class="difficulty" data-difficulty="hard"
           onclick="selectDifficulty(this)">
        <strong>HARD</strong>
        <small>
          6 suspects<br>
          12 clues<br>
          1 hint
        </small>
      </div>

    </div>

    <br>

    <button class="btn primary" onclick="startGame()">
      Open Case
    </button>

    <button class="btn" onclick="closeStart()">
      Cancel
    </button>

  </div>

</div>

<!-- GAME -->
<section class="game hidden" id="game">

  <header class="topbar">

    <div>
      <div class="top-title">THE LAST ALIBI</div>
      <div class="case-number">CASE #001 — MIDNIGHT MANOR</div>
    </div>

    <div id="playerDisplay">
      DETECTIVE
    </div>

  </header>

  <div class="game-layout">

    <aside class="sidebar">

      <div class="nav-title">INVESTIGATION</div>

      <button class="nav-btn active" onclick="showSection('case', this)">
        📁 Case File
      </button>

      <button class="nav-btn" onclick="showSection('suspects', this)">
        👤 Suspects
      </button>

      <button class="nav-btn" onclick="showSection('evidence', this)">
        🔎 Evidence
      </button>

      <button class="nav-btn" onclick="showSection('timeline', this)">
        🕐 Timeline
      </button>

      <button class="nav-btn" onclick="showSection('accusation', this)">
        ⚖ Accusation
      </button>

    </aside>

    <main class="main">

      <!-- CASE -->
      <div id="section-case">

        <div class="case-header">

          <div class="stamp">
            CONFIDENTIAL CASE FILE
          </div>

          <h2>The Midnight Manor</h2>

          <p style="color:#aaa;">
            A wealthy businessman has been found dead inside
            his private study. The doors were locked from the inside.
          </p>

          <div class="case-details">

            <div>
              <strong>Victim</strong><br>
              Victor Ashcroft
            </div>

            <div>
              <strong>Location</strong><br>
              Ashcroft Manor
            </div>

            <div>
              <strong>Time Found</strong><br>
              11:30 PM
            </div>

            <div>
              <strong>Cause</strong><br>
              Poisoning
            </div>

          </div>

        </div>

        <div class="card">

          <span class="tag">DETECTIVE BRIEFING</span>

          <p>
            Victor Ashcroft hosted a private dinner at his manor.
            At approximately 11:30 PM, his body was discovered in
            the locked study.
          </p>

          <br>

          <p>
            Five people were inside the manor that night.
            Every one of them claims they had nothing to do with
            Victor's death.
          </p>

          <br>

          <p style="color:#c8a96b;">
            Your task: determine who is lying.
          </p>

        </div>

      </div>

      <!-- SUSPECTS -->
      <div id="section-suspects" class="hidden">

        <h1 class="section-title">Suspects</h1>

        <p class="section-subtitle">
          Everyone had a reason to want Victor Ashcroft gone.
        </p>

        <div class="card-grid">

          <div class="card">
            <span class="tag">SUSPECT 01</span>
            <h3>Clara Ashcroft</h3>
            <p>
              Victor's wife. Claims she was in the library
              reading between 10:45 and 11:30 PM.
            </p>
            <br>
            <small style="color:#9d2b32;">
              MOTIVE: Inheritance
            </small>
          </div>

          <div class="card">
            <span class="tag">SUSPECT 02</span>
            <h3>Marcus Vale</h3>
            <p>
              Victor's business partner. Claims he left the
              dining room at 10:50 PM.
            </p>
            <br>
            <small style="color:#9d2b32;">
              MOTIVE: Financial dispute
            </small>
          </div>

          <div class="card">
            <span class="tag">SUSPECT 03</span>
            <h3>Evelyn Hart</h3>
            <p>
              The manor's housekeeper. Says she was preparing
              tea in the kitchen.
            </p>
            <br>
            <small style="color:#9d2b32;">
              MOTIVE: Unknown
            </small>
          </div>

          <div class="card">
            <span class="tag">SUSPECT 04</span>
            <h3>Daniel Cross</h3>
            <p>
              Victor's nephew. Claims he spent the evening
              outside making a phone call.
            </p>
            <br>
            <small style="color:#9d2b32;">
              MOTIVE: Debt
            </small>
          </div>

          <div class="card medium-only">

            <span class="tag">SUSPECT 05</span>

            <h3>Arthur Bell</h3>

            <p>
              Victor's old friend. Says he was asleep in
              the guest room.
            </p>

            <br>

            <small style="color:#9d2b32;">
              MOTIVE: Personal grudge
            </small>

          </div>

          <div class="card hard-only">

            <span class="tag">SUSPECT 06</span>

            <h3>James Reed</h3>

            <p>
              Victor's private accountant. Claims he was
              reviewing financial documents.
            </p>

            <br>

            <small style="color:#9d2b32;">
              MOTIVE: Fraud
            </small>

          </div>

        </div>

      </div>

      <!-- EVIDENCE -->
      <div id="section-evidence" class="hidden">

        <h1 class="section-title">Evidence</h1>

        <p class="section-subtitle">
          Examine everything. Not every clue tells the truth.
        </p>

        <div class="card-grid">

          <div class="card evidence"
               onclick="inspectEvidence('A-01')">

            <div class="evidence-id">EVIDENCE A-01</div>

            <div class="evidence-icon">⌚</div>

            <h3>Broken Watch</h3>

            <p>
              Found beside the victim's desk.
            </p>

          </div>

          <div class="card evidence"
               onclick="inspectEvidence('A-02')">

            <div class="evidence-id">EVIDENCE A-02</div>

            <div class="evidence-icon">📱</div>

            <h3>Phone Record</h3>

            <p>
              A 17-minute call was made at 11:02 PM.
            </p>

          </div>

          <div class="card evidence"
               onclick="inspectEvidence('A-03')">

            <div class="evidence-id">EVIDENCE A-03</div>

            <div class="evidence-icon">🔑</div>

            <h3>Study Key</h3>

            <p>
              A spare key was found in the hallway.
            </p>

          </div>

          <div class="card evidence"
               onclick="inspectEvidence('A-04')">

            <div class="evidence-id">EVIDENCE A-04</div>

            <div class="evidence-icon">📹</div>

            <h3>Security Record</h3>

            <p>
              Camera detected movement near the study.
            </p>

          </div>

          <div class="card evidence medium-only"
               onclick="inspectEvidence('A-05')">

            <div class="evidence-id">EVIDENCE A-05</div>

            <div class="evidence-icon">✉️</div>

            <h3>Anonymous Letter</h3>

            <p>
              A threatening letter addressed to Victor.
            </p>

          </div>

          <div class="card evidence hard-only"
               onclick="inspectEvidence('A-06')">

            <div class="evidence-id">EVIDENCE A-06</div>

            <div class="evidence-icon">☕</div>

            <h3>Tea Cup</h3>

            <p>
              Chemical traces were discovered inside.
            </p>

          </div>

        </div>

        <br>

        <button class="btn primary" onclick="giveHint()">
          🔎 Request Hint
        </button>

        <p id="hintText" style="margin-top:20px;color:#c8a96b;"></p>

      </div>

      <!-- TIMELINE -->
      <div id="section-timeline" class="hidden">

        <h1 class="section-title">Timeline</h1>

        <p class="section-subtitle">
          Reconstruct what happened on the night of the murder.
        </p>

        <div class="timeline">

          <div class="timeline-item">
            <div class="time">10:15 PM</div>
            Dinner ends.
          </div>

          <div class="timeline-item">
            <div class="time">10:42 PM</div>
            Victor enters his private study.
          </div>

          <div class="timeline-item">
            <div class="time">10:58 PM</div>
            Someone is seen near the study corridor.
          </div>

          <div class="timeline-item">
            <div class="time">11:02 PM</div>
            A phone call begins.
          </div>

          <div class="timeline-item">
            <div class="time">11:19 PM</div>
            The security camera briefly loses power.
          </div>

          <div class="timeline-item">
            <div class="time">11:30 PM</div>
            Victor is discovered inside the study.
          </div>

        </div>

      </div>

      <!-- ACCUSATION -->
      <div id="section-accusation" class="hidden">

        <h1 class="section-title">
          Make Your Accusation
        </h1>

        <p class="section-subtitle">
          Detective, commit to your theory.
        </p>

        <div class="accusation-box">

          <label>Who is the murderer?</label>

          <select id="suspectChoice">

            <option value="">Select suspect...</option>
            <option value="Clara Ashcroft">Clara Ashcroft</option>
            <option value="Marcus Vale">Marcus Vale</option>
            <option value="Evelyn Hart">Evelyn Hart</option>
            <option value="Daniel Cross">Daniel Cross</option>
            <option value="Arthur Bell">Arthur Bell</option>
            <option value="James Reed">James Reed</option>

          </select>

          <label>
            Explain your theory
          </label>

          <textarea
            id="theory"
            placeholder="Explain the evidence that convinced you..."
          ></textarea>

          <br><br>

          <button
            class="btn primary"
            onclick="makeAccusation()"
          >
            Submit Accusation
          </button>

        </div>

      </div>

      <!-- RESULT -->
      <div id="section-result" class="hidden">

        <div class="result">

          <div class="result-icon" id="resultIcon">
            🕵️
          </div>

          <h1 id="resultTitle">
            CASE SOLVED
          </h1>

          <p id="resultMessage"></p>

          <div class="solution">

            <h3>THE TRUTH</h3>

            <p>
              The murderer was <strong>Marcus Vale</strong>.
            </p>

            <p>
              Marcus had access to the study and a strong financial
              motive. His statement placed him in the dining room,
              but the security record contradicts his alibi.
            </p>

            <p>
              The critical evidence was the timeline surrounding
              the 11:02 PM phone call and the movement detected
              near the study.
            </p>

            <p style="color:#c8a96b;">
              The case was solved by connecting the timeline,
              security record, and suspect testimony.
            </p>

          </div>

          <br>

          <button class="btn primary" onclick="location.reload()">
            New Investigation
          </button>

        </div>

      </div>

    </main>

  </div>

</section>

<!-- EVIDENCE MODAL -->
<div class="modal hidden" id="evidenceModal">

  <div class="modal-box">

    <h2 id="evidenceTitle"></h2>

    <p id="evidenceDescription"></p>

    <button class="btn primary"
            onclick="closeEvidence()">
      Close Evidence
    </button>

  </div>

</div>

<script>

let difficulty = "easy";
let hintsLeft = 3;

const evidenceData = {

  "A-01": {
    title: "EVIDENCE A-01 — BROKEN WATCH",
    description:
      "A broken watch was found beside Victor's desk. The hands stopped at 10:58 PM. This initially appears important, but investigators later determine the watch had been damaged earlier."
  },

  "A-02": {
    title: "EVIDENCE A-02 — PHONE RECORD",
    description:
      "Victor received a 17-minute phone call beginning at 11:02 PM. The call came from an unknown number."
  },

  "A-03": {
    title: "EVIDENCE A-03 — STUDY KEY",
    description:
      "A spare study key was found in the hallway. Only Victor, Clara and Marcus were known to have access to spare keys."
  },

  "A-04": {
    title: "EVIDENCE A-04 — SECURITY RECORD",
    description:
      "Security footage shows movement near the study at approximately 10:58 PM. Marcus claimed he was still in the dining room at that time."
  },

  "A-05": {
    title: "EVIDENCE A-05 — ANONYMOUS LETTER",
    description:
      "A threatening letter was found inside Victor's desk. The handwriting does not match the primary suspects."
  },

  "A-06": {
    title: "EVIDENCE A-06 — TEA CUP",
    description:
      "Chemical traces were found inside Victor's tea cup. The tea was prepared shortly before he entered the study."
  }

};

/* =========================
   START
========================= */

function openStart() {
  document
    .getElementById("startModal")
    .classList.remove("hidden");
}

function closeStart() {
  document
    .getElementById("startModal")
    .classList.add("hidden");
}

function selectDifficulty(element) {

  document
    .querySelectorAll(".difficulty")
    .forEach(x => x.classList.remove("active"));

  element.classList.add("active");

  difficulty = element.dataset.difficulty;

  if (difficulty === "easy") hintsLeft = 3;
  if (difficulty === "medium") hintsLeft = 2;
  if (difficulty === "hard") hintsLeft = 1;
}

/* =========================
   START GAME
========================= */

function startGame() {

  const name =
    document.getElementById("detectiveName").value.trim();

  if (!name) {
    alert("Please enter your detective name.");
    return;
  }

  document
    .getElementById("home")
    .classList.add("hidden");

  document
    .getElementById("startModal")
    .classList.add("hidden");

  document
    .getElementById("game")
    .classList.remove("hidden");

  document.getElementById("playerDisplay").textContent =
    "DETECTIVE " + name.toUpperCase();

  document
    .querySelectorAll(".medium-only")
    .forEach(el => {
      el.style.display =
        difficulty === "easy" ? "none" : "";
    });

  document
    .querySelectorAll(".hard-only")
    .forEach(el => {
      el.style.display =
        difficulty === "hard" ? "" : "none";
    });
}

/* =========================
   NAVIGATION
========================= */

function showSection(section, button) {

  document
    .querySelectorAll('[id^="section-"]')
    .forEach(el => el.classList.add("hidden"));

  document
    .getElementById("section-" + section)
    .classList.remove("hidden");

  document
    .querySelectorAll(".nav-btn")
    .forEach(el => el.classList.remove("active"));

  button.classList.add("active");
}

/* =========================
   EVIDENCE
========================= */

function inspectEvidence(id) {

  const evidence = evidenceData[id];

  if (!evidence) return;

  document.getElementById("evidenceTitle").textContent =
    evidence.title;

  document.getElementById("evidenceDescription").textContent =
    evidence.description;

  document
    .getElementById("evidenceModal")
    .classList.remove("hidden");
}

function closeEvidence() {

  document
    .getElementById("evidenceModal")
    .classList.add("hidden");
}

/* =========================
   HINTS
========================= */

function giveHint() {

  if (hintsLeft <= 0) {

    document.getElementById("hintText").textContent =
      "No hints remain.";

    return;
  }

  const hints = {

    easy:
      "Compare the security record with the suspects' alibis.",

    medium:
      "Marcus's timeline deserves closer examination.",

    hard:
      "The important clue is not the broken watch. Look at who could access the study."
  };

  document.getElementById("hintText").textContent =
    "HINT: " + hints[difficulty];

  hintsLeft--;

}

/* =========================
   ACCUSATION
========================= */

function makeAccusation() {

  const suspect =
    document.getElementById("suspectChoice").value;

  if (!suspect) {

    alert("Select a suspect before submitting.");

    return;
  }

  document
    .querySelectorAll('[id^="section-"]')
    .forEach(el => el.classList.add("hidden"));

  document
    .getElementById("section-result")
    .classList.remove("hidden");

  const correct = suspect === "Marcus Vale";

  if (correct) {

    document.getElementById("resultIcon").textContent =
      "🔎";

    document.getElementById("resultTitle").textContent =
      "CASE SOLVED";

    document.getElementById("resultMessage").textContent =
      "Your accusation matches the evidence.";

  } else {

    document.getElementById("resultIcon").textContent =
      "❌";

    document.getElementById("resultTitle").textContent =
      "THE THEORY FAILED";

    document.getElementById("resultMessage").textContent =
      "Your suspect was not responsible. Review the evidence and timeline.";

  }

}

/* =========================
   HOW TO PLAY
========================= */

function showHowToPlay() {

  alert(
`HOW TO PLAY

1. Choose a difficulty.
2. Read the case file.
3. Investigate the suspects.
4. Examine the evidence.
5. Compare the timeline with the alibis.
6. Use hints carefully.
7. Make your final accusation.

The goal is not simply to guess the murderer.

Build a theory using the evidence.`
  );

}

</script>

</body>
</html>
```

 
9. GitHub will give you a public website URL.

 This version is deliberately **single-file and dependency-free**, so you can literally copy/paste it into a repository and publish it without installing anything.
