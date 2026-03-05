[Uploading baddy-buddies.html…]()
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0">
<title>Baddy Buddies</title>
<link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@300;400;500;600;700&display=swap" rel="stylesheet">
<style>
  :root {
    --bg:       #0e0e12;
    --surface:  #17171d;
    --surface2: #1f1f27;
    --surface3: #27272f;
    --border:   rgba(255,255,255,0.07);
    --text:     #f2f2f4;
    --muted:    #6b6b78;
    --dim:      #3a3a45;

    --sage:     #a8c5a0;
    --peach:    #e8b89a;
    --lavender: #b8a8d8;
    --sky:      #90c0d8;
    --rose:     #d8a0a8;
    --gold:     #d4b896;

    --r:        20px;
    --r-sm:     14px;
  }

  * { box-sizing: border-box; margin: 0; padding: 0; -webkit-tap-highlight-color: transparent; }

  html, body {
    height: 100%;
    background: var(--bg);
    color: var(--text);
    font-family: 'Plus Jakarta Sans', sans-serif;
    font-size: 15px;
    max-width: 430px;
    margin: 0 auto;
    -webkit-font-smoothing: antialiased;
  }

  body { padding-bottom: 76px; }

  /* ── Header ── */
  .header {
    padding: 16px 20px 14px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    position: sticky;
    top: 0;
    z-index: 100;
    background: var(--bg);
    border-bottom: 1px solid var(--border);
  }

  .logo {
    display: flex;
    align-items: center;
    gap: 10px;
  }

  .logo-icon {
    width: 34px;
    height: 34px;
    flex-shrink: 0;
  }

  .logo-text {
    font-size: 17px;
    font-weight: 700;
    letter-spacing: -0.3px;
    color: var(--text);
  }

  .match-count {
    font-size: 12px;
    font-weight: 500;
    color: var(--muted);
    background: var(--surface2);
    padding: 5px 12px;
    border-radius: 20px;
  }

  /* ── Nav ── */
  .nav {
    position: fixed;
    bottom: 0;
    left: 50%;
    transform: translateX(-50%);
    width: 100%;
    max-width: 430px;
    background: var(--surface);
    border-top: 1px solid var(--border);
    display: flex;
    z-index: 100;
  }

  .nav-btn {
    flex: 1;
    padding: 12px 4px 10px;
    background: none;
    border: none;
    color: var(--muted);
    font-family: 'Plus Jakarta Sans', sans-serif;
    font-size: 10px;
    font-weight: 600;
    cursor: pointer;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 5px;
    transition: color 0.2s;
    letter-spacing: 0.3px;
    text-transform: uppercase;
  }

  .nav-btn svg { width: 18px; height: 18px; transition: all 0.2s; }
  .nav-btn.active { color: var(--text); }
  .nav-btn.active svg { stroke: var(--sage); }

  /* ── Screens ── */
  .screen { display: none; padding: 20px; }
  .screen.active { display: block; animation: rise 0.2s ease; }

  @keyframes rise {
    from { opacity: 0; transform: translateY(6px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  .section-title {
    font-size: 11px;
    font-weight: 700;
    color: var(--muted);
    text-transform: uppercase;
    letter-spacing: 1.2px;
    margin-bottom: 14px;
  }

  .card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: var(--r);
    padding: 16px;
    margin-bottom: 10px;
  }

  /* ── Leaderboard ── */
  .lb-hero {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: var(--r);
    padding: 20px;
    margin-bottom: 16px;
    display: flex;
    align-items: center;
    gap: 16px;
  }

  .lb-hero-avatar {
    width: 56px; height: 56px;
    border-radius: 18px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 15px;
    font-weight: 700;
    flex-shrink: 0;
  }

  .lb-hero-label { font-size: 11px; font-weight: 600; color: var(--muted); text-transform: uppercase; letter-spacing: 1px; margin-bottom: 4px; }
  .lb-hero-name { font-size: 22px; font-weight: 700; letter-spacing: -0.5px; }
  .lb-hero-sub { font-size: 13px; color: var(--muted); margin-top: 3px; font-weight: 500; }
  .lb-hero-rate { font-size: 28px; font-weight: 700; letter-spacing: -1px; color: var(--sage); }

  .lb-list { display: flex; flex-direction: column; gap: 2px; }

  .lb-item {
    display: flex;
    align-items: center;
    gap: 12px;
    padding: 12px 14px;
    border-radius: var(--r-sm);
    transition: background 0.15s;
  }

  .lb-item:hover { background: var(--surface2); }

  .lb-rank { font-size: 13px; font-weight: 600; color: var(--muted); width: 20px; text-align: center; flex-shrink: 0; }

  .lb-avatar {
    width: 36px; height: 36px;
    border-radius: 11px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 12px;
    font-weight: 700;
    flex-shrink: 0;
  }

  .lb-info { flex: 1; min-width: 0; }
  .lb-name { font-size: 14px; font-weight: 600; }
  .lb-sub { font-size: 12px; color: var(--muted); font-weight: 500; margin-top: 1px; }

  .lb-right { text-align: right; flex-shrink: 0; width: 50px; }
  .lb-pct { font-size: 13px; font-weight: 600; color: var(--muted); margin-bottom: 4px; }
  .lb-bar-bg { height: 4px; background: var(--surface3); border-radius: 2px; overflow: hidden; }
  .lb-bar { height: 100%; border-radius: 2px; transition: width 0.7s cubic-bezier(.16,1,.3,1); }

  /* ── Log ── */
  .form-label {
    font-size: 11px;
    font-weight: 700;
    color: var(--muted);
    text-transform: uppercase;
    letter-spacing: 1px;
    margin-bottom: 10px;
    display: block;
  }

  .player-grid {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    gap: 6px;
    margin-bottom: 16px;
  }

  .player-chip {
    padding: 9px 6px;
    border-radius: 10px;
    border: 1px solid var(--border);
    background: var(--surface2);
    color: var(--muted);
    font-family: 'Plus Jakarta Sans', sans-serif;
    font-weight: 600;
    font-size: 12px;
    cursor: pointer;
    text-align: center;
    transition: all 0.15s;
    user-select: none;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }

  .player-chip:active { transform: scale(0.97); }

  .player-chip.selected-t1 {
    border-color: rgba(232,184,154,0.5);
    background: rgba(232,184,154,0.1);
    color: var(--peach);
  }

  .player-chip.selected-t2 {
    border-color: rgba(144,192,216,0.5);
    background: rgba(144,192,216,0.1);
    color: var(--sky);
  }

  .score-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: var(--r);
    padding: 20px;
    margin-bottom: 10px;
  }

  .score-teams {
    display: flex;
    justify-content: space-between;
    margin-bottom: 14px;
  }

  .score-team-label {
    font-size: 11px;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 1px;
  }

  .score-team-label.t1 { color: var(--peach); }
  .score-team-label.t2 { color: var(--sky); text-align: right; }

  .score-row {
    display: grid;
    grid-template-columns: 1fr 32px 1fr;
    gap: 8px;
    align-items: center;
  }

  .score-input {
    background: var(--surface2);
    border: 1px solid var(--border);
    border-radius: var(--r-sm);
    color: var(--text);
    font-family: 'Plus Jakarta Sans', sans-serif;
    font-size: 40px;
    font-weight: 700;
    letter-spacing: -1px;
    text-align: center;
    padding: 14px 8px;
    width: 100%;
    outline: none;
    transition: border-color 0.2s;
    -webkit-appearance: none;
  }

  .score-input:focus { border-color: var(--dim); }

  .score-vs {
    text-align: center;
    font-size: 11px;
    font-weight: 700;
    color: var(--muted);
    text-transform: uppercase;
    letter-spacing: 1px;
  }

  .btn-primary {
    width: 100%;
    padding: 15px;
    background: rgba(168,197,160,0.12);
    border: 1px solid rgba(168,197,160,0.25);
    border-radius: var(--r-sm);
    color: var(--sage);
    font-family: 'Plus Jakarta Sans', sans-serif;
    font-size: 14px;
    font-weight: 700;
    cursor: pointer;
    transition: all 0.15s;
    letter-spacing: 0.3px;
    margin-bottom: 8px;
  }

  .btn-primary:hover { background: rgba(168,197,160,0.18); }
  .btn-primary:active { transform: scale(0.99); }

  .btn-ghost {
    width: 100%;
    padding: 12px;
    background: none;
    border: none;
    color: var(--muted);
    font-family: 'Plus Jakarta Sans', sans-serif;
    font-size: 13px;
    font-weight: 600;
    cursor: pointer;
    transition: color 0.15s;
  }
  .btn-ghost:hover { color: var(--text); }

  /* ── History ── */
  .match-item {
    display: flex;
    align-items: center;
    gap: 12px;
    padding: 14px;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: var(--r-sm);
    margin-bottom: 8px;
  }

  .match-indicator { width: 3px; height: 40px; border-radius: 2px; flex-shrink: 0; }
  .match-teams { flex: 1; min-width: 0; }

  .match-team {
    font-size: 13px;
    font-weight: 500;
    color: var(--muted);
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
    padding: 2px 0;
  }

  .match-team.won { font-weight: 700; color: var(--text); }

  .match-right { text-align: right; flex-shrink: 0; }

  .match-score-display {
    font-size: 20px;
    font-weight: 700;
    letter-spacing: -0.5px;
    line-height: 1;
  }

  .match-score-display .w { color: var(--text); }
  .match-score-display .l { color: var(--dim); }
  .match-date { font-size: 11px; color: var(--muted); font-weight: 500; margin-top: 4px; }

  /* ── H2H ── */
  .player-pills {
    display: flex;
    gap: 6px;
    overflow-x: auto;
    padding-bottom: 2px;
    scrollbar-width: none;
    margin-bottom: 16px;
  }
  .player-pills::-webkit-scrollbar { display: none; }

  .player-pill {
    padding: 7px 14px;
    border-radius: 20px;
    border: 1px solid var(--border);
    background: var(--surface2);
    color: var(--muted);
    font-size: 13px;
    font-weight: 600;
    cursor: pointer;
    white-space: nowrap;
    transition: all 0.15s;
    flex-shrink: 0;
  }

  .player-pill.active {
    background: var(--surface3);
    border-color: var(--dim);
    color: var(--text);
  }

  .h2h-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 8px; }

  .h2h-cell {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: var(--r-sm);
    padding: 14px 12px;
    display: flex;
    align-items: center;
    gap: 10px;
  }

  .h2h-av {
    width: 32px; height: 32px;
    border-radius: 10px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 11px;
    font-weight: 700;
    flex-shrink: 0;
  }

  .h2h-info { flex: 1; min-width: 0; }
  .h2h-name { font-size: 12px; font-weight: 600; color: var(--muted); margin-bottom: 2px; white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }
  .h2h-record { font-size: 17px; font-weight: 700; letter-spacing: -0.3px; }
  .h2h-record.pos { color: var(--sage); }
  .h2h-record.neg { color: var(--rose); }
  .h2h-record.neu { color: var(--muted); }

  /* ── Stats ── */
  .stat-highlight {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: var(--r);
    padding: 16px;
    margin-bottom: 8px;
    display: flex;
    align-items: center;
    gap: 14px;
  }

  .stat-icon {
    width: 44px; height: 44px;
    border-radius: 14px;
    background: var(--surface2);
    border: 1px solid var(--border);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 20px;
    flex-shrink: 0;
  }

  .stat-eyebrow { font-size: 11px; font-weight: 700; color: var(--muted); text-transform: uppercase; letter-spacing: 1px; margin-bottom: 3px; }
  .stat-val { font-size: 16px; font-weight: 700; }
  .stat-sub { font-size: 12px; color: var(--muted); font-weight: 500; margin-top: 1px; }

  .overview-grid {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    gap: 8px;
    margin-bottom: 8px;
  }

  .overview-cell {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: var(--r-sm);
    padding: 14px 12px;
    text-align: center;
  }

  .overview-num { font-size: 24px; font-weight: 700; letter-spacing: -1px; }
  .overview-label { font-size: 11px; color: var(--muted); font-weight: 600; margin-top: 2px; }

  .pair-row {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 12px 0;
    border-bottom: 1px solid var(--border);
  }
  .pair-row:last-child { border-bottom: none; }
  .pair-names { font-size: 13px; font-weight: 600; }
  .pair-sub { font-size: 12px; color: var(--muted); font-weight: 500; margin-top: 1px; }
  .pair-pct { font-size: 16px; font-weight: 700; color: var(--sage); }

  /* ── Toast ── */
  .toast {
    position: fixed;
    bottom: 96px;
    left: 50%;
    transform: translateX(-50%) translateY(8px);
    background: var(--surface3);
    border: 1px solid var(--border);
    color: var(--text);
    padding: 11px 20px;
    border-radius: 30px;
    font-size: 13px;
    font-weight: 600;
    opacity: 0;
    transition: all 0.25s cubic-bezier(.16,1,.3,1);
    z-index: 999;
    white-space: nowrap;
    pointer-events: none;
  }
  .toast.show { opacity: 1; transform: translateX(-50%) translateY(0); }

  /* ── Avatar palette ── */
  .av-0 { background: rgba(168,197,160,0.18); color: var(--sage); }
  .av-1 { background: rgba(232,184,154,0.18); color: var(--peach); }
  .av-2 { background: rgba(184,168,216,0.18); color: var(--lavender); }
  .av-3 { background: rgba(144,192,216,0.18); color: var(--sky); }
  .av-4 { background: rgba(216,160,168,0.18); color: var(--rose); }
  .av-5 { background: rgba(212,184,150,0.18); color: var(--gold); }

  .bar-0 { background: var(--sage); }
  .bar-1 { background: var(--peach); }
  .bar-2 { background: var(--lavender); }
  .bar-3 { background: var(--sky); }
  .bar-4 { background: var(--rose); }
  .bar-5 { background: var(--gold); }

  .empty {
    padding: 48px 20px;
    text-align: center;
    color: var(--muted);
    font-size: 14px;
    font-weight: 500;
    line-height: 1.8;
  }

  .empty svg { margin-bottom: 16px; opacity: 0.25; }

  input[type=number]::-webkit-inner-spin-button,
  input[type=number]::-webkit-outer-spin-button { -webkit-appearance: none; }
  input[type=number] { -moz-appearance: textfield; }
</style>
</head>
<body>

<header class="header">
  <div class="logo">
    <!-- SVG Badminton Racket + Shuttlecock -->
    <svg class="logo-icon" viewBox="0 0 34 34" fill="none" xmlns="http://www.w3.org/2000/svg">
      <!-- Racket head (oval frame) -->
      <ellipse cx="13" cy="12" rx="9" ry="10.5" stroke="#a8c5a0" stroke-width="1.6" fill="none"/>
      <!-- Strings horizontal -->
      <line x1="4.2" y1="9"  x2="21.8" y2="9"  stroke="#a8c5a0" stroke-width="0.7" opacity="0.5"/>
      <line x1="4.0" y1="12" x2="22.0" y2="12" stroke="#a8c5a0" stroke-width="0.7" opacity="0.5"/>
      <line x1="4.2" y1="15" x2="21.8" y2="15" stroke="#a8c5a0" stroke-width="0.7" opacity="0.5"/>
      <!-- Strings vertical -->
      <line x1="9"  y1="1.8" x2="9"  y2="22.2" stroke="#a8c5a0" stroke-width="0.7" opacity="0.5"/>
      <line x1="13" y1="1.5" x2="13" y2="22.5" stroke="#a8c5a0" stroke-width="0.7" opacity="0.5"/>
      <line x1="17" y1="1.8" x2="17" y2="22.2" stroke="#a8c5a0" stroke-width="0.7" opacity="0.5"/>
      <!-- Throat + handle -->
      <path d="M9 22 L11 25 L15 25 L17 22" stroke="#a8c5a0" stroke-width="1.6" fill="none" stroke-linejoin="round"/>
      <rect x="11" y="25" width="4" height="8" rx="2" fill="#a8c5a0" opacity="0.9"/>
      <!-- Shuttlecock -->
      <circle cx="27" cy="8" r="2.2" fill="#d4b896" opacity="0.9"/>
      <line x1="27" y1="10.2" x2="24" y2="16" stroke="#d4b896" stroke-width="0.9" opacity="0.7"/>
      <line x1="27" y1="10.2" x2="27" y2="16.5" stroke="#d4b896" stroke-width="0.9" opacity="0.7"/>
      <line x1="27" y1="10.2" x2="30" y2="16" stroke="#d4b896" stroke-width="0.9" opacity="0.7"/>
      <line x1="24" y1="16" x2="30" y2="16" stroke="#d4b896" stroke-width="0.9" opacity="0.7"/>
    </svg>
    <span class="logo-text">Baddy Buddies</span>
  </div>
  <div class="match-count" id="matchCount">0 matches</div>
</header>

<div class="toast" id="toast"></div>

<!-- LEADERBOARD -->
<div class="screen active" id="screen-lb">
  <div id="lbHero"></div>
  <div class="section-title">All Players</div>
  <div class="lb-list" id="lbList"></div>
</div>

<!-- LOG -->
<div class="screen" id="screen-log">
  <div class="section-title">Select Teams</div>
  <div class="card">
    <span class="form-label" style="color:var(--peach);">Team 1</span>
    <div class="player-grid" id="t1Grid"></div>
    <span class="form-label" style="color:var(--sky);">Team 2</span>
    <div class="player-grid" id="t2Grid"></div>
  </div>
  <div class="score-card">
    <div class="score-teams">
      <span class="score-team-label t1" id="t1Label">Team 1</span>
      <span class="score-team-label t2" id="t2Label">Team 2</span>
    </div>
    <div class="score-row">
      <input class="score-input" type="number" id="score1" placeholder="21" min="0" max="99">
      <div class="score-vs">vs</div>
      <input class="score-input" type="number" id="score2" placeholder="18" min="0" max="99">
    </div>
  </div>
  <button class="btn-primary" onclick="submitMatch()">Save Match</button>
  <button class="btn-ghost" onclick="clearForm()">Clear</button>
</div>

<!-- HISTORY -->
<div class="screen" id="screen-history">
  <div class="section-title">Recent Matches</div>
  <div id="historyList"></div>
</div>

<!-- H2H -->
<div class="screen" id="screen-h2h">
  <div class="section-title">Head to Head</div>
  <div class="player-pills" id="h2hPills"></div>
  <div id="h2hContent"></div>
</div>

<!-- STATS -->
<div class="screen" id="screen-stats">
  <div id="statsContent"></div>
</div>

<!-- NAV -->
<nav class="nav">
  <button class="nav-btn active" onclick="showScreen('lb',this)">
    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><polyline points="22 12 18 12 15 21 9 3 6 12 2 12"/></svg>
    Ranks
  </button>
  <button class="nav-btn" onclick="showScreen('log',this)">
    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><line x1="12" y1="8" x2="12" y2="16"/><line x1="8" y1="12" x2="16" y2="12"/></svg>
    Log
  </button>
  <button class="nav-btn" onclick="showScreen('history',this)">
    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="4" width="18" height="18" rx="2"/><line x1="16" y1="2" x2="16" y2="6"/><line x1="8" y1="2" x2="8" y2="6"/><line x1="3" y1="10" x2="21" y2="10"/></svg>
    History
  </button>
  <button class="nav-btn" onclick="showScreen('h2h',this)">
    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M23 21v-2a4 4 0 0 0-3-3.87"/><path d="M16 3.13a4 4 0 0 1 0 7.75"/></svg>
    H2H
  </button>
  <button class="nav-btn" onclick="showScreen('stats',this)">
    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><line x1="18" y1="20" x2="18" y2="10"/><line x1="12" y1="20" x2="12" y2="4"/><line x1="6" y1="20" x2="6" y2="14"/></svg>
    Stats
  </button>
</nav>

<script>
const PLAYERS = [
  { id:'p1', name:'Anishaa' },
  { id:'p2', name:'Kuhan' },
  { id:'p3', name:'Chandra' },
  { id:'p4', name:'Armaan' },
  { id:'p5', name:'Mithiran' },
  { id:'p6', name:'Joon Lok' },
];

const SUPABASE_URL = 'https://cufnpmlljcqthiaguvbq.supabase.co';
const SUPABASE_KEY = 'sb_publishable_hEhmbzkmJwo9g2eRVxO_GQ_jW4B0oOf';

let matches = [];
let t1 = [], t2 = [];
let h2hPick = null;

const pidx = id => PLAYERS.findIndex(p => p.id === id);
const pname = id => PLAYERS.find(p => p.id === id)?.name || id;
const initials = name => name.split(' ').map(w => w[0]).join('').toUpperCase();

async function loadMatches() {
  try {
    const res = await fetch(`${SUPABASE_URL}/rest/v1/matches?order=id.desc`, {
      headers: {
        'apikey': SUPABASE_KEY,
        'Authorization': `Bearer ${SUPABASE_KEY}`
      }
    });
    if (!res.ok) throw new Error(await res.text());
    matches = await res.json();
    renderLB();
    updateCount();
  } catch(e) {
    console.error('Load error:', e);
    showToast('Could not load matches');
  }
}

async function save(match) {
  try {
    const res = await fetch(`${SUPABASE_URL}/rest/v1/matches`, {
      method: 'POST',
      headers: {
        'apikey': SUPABASE_KEY,
        'Authorization': `Bearer ${SUPABASE_KEY}`,
        'Content-Type': 'application/json',
        'Prefer': 'return=representation'
      },
      body: JSON.stringify(match)
    });
    if (!res.ok) throw new Error(await res.text());
    const saved = await res.json();
    matches.unshift(saved[0]);
    return true;
  } catch(e) {
    console.error('Save error:', e);
    showToast('Could not save match');
    return false;
  }
}

function updateCount() {
  const n = matches.length;
  document.getElementById('matchCount').textContent = n + (n === 1 ? ' match' : ' matches');
}

function showScreen(name, btn) {
  document.querySelectorAll('.screen').forEach(s => s.classList.remove('active'));
  document.querySelectorAll('.nav-btn').forEach(b => b.classList.remove('active'));
  document.getElementById('screen-' + name).classList.add('active');
  if (btn) btn.classList.add('active');
  if (name === 'lb')      renderLB();
  if (name === 'history') renderHistory();
  if (name === 'h2h')     renderH2H();
  if (name === 'stats')   renderStats();
  updateCount();
}

function calcStats() {
  return PLAYERS.map(p => {
    let wins = 0, total = 0, streak = 0;
    for (const m of matches) {
      const inT1 = m.t1.includes(p.id), inT2 = m.t2.includes(p.id);
      if (!inT1 && !inT2) continue;
      total++;
      const t1w = m.s1 > m.s2;
      if ((inT1 && t1w) || (inT2 && !t1w)) wins++;
    }
    for (const m of matches) {
      const inT1 = m.t1.includes(p.id), inT2 = m.t2.includes(p.id);
      if (!inT1 && !inT2) continue;
      const t1w = m.s1 > m.s2;
      const won = (inT1 && t1w) || (inT2 && !t1w);
      if (won) streak++; else break;
    }
    return { ...p, wins, losses: total - wins, total, rate: total > 0 ? wins / total : 0, streak };
  });
}

function renderLB() {
  const stats = calcStats().sort((a, b) => {
    if (!a.total && !b.total) return 0;
    if (!a.total) return 1;
    if (!b.total) return -1;
    return b.rate - a.rate || b.wins - a.wins;
  });

  const hero = stats[0];
  const hi = pidx(hero.id);
  const heroPct = Math.round(hero.rate * 100);

  document.getElementById('lbHero').innerHTML = matches.length === 0 ? '' : `
    <div class="lb-hero">
      <div class="lb-hero-avatar av-${hi}">${initials(hero.name)}</div>
      <div style="flex:1;">
        <div class="lb-hero-label">Leading</div>
        <div class="lb-hero-name">${hero.name}</div>
        <div class="lb-hero-sub">${hero.wins}W · ${hero.losses}L${hero.streak >= 3 ? ` · ${hero.streak} streak` : ''}</div>
      </div>
      <div class="lb-hero-rate">${heroPct}%</div>
    </div>
  `;

  if (matches.length === 0) {
    document.getElementById('lbList').innerHTML = `<div class="empty">
      <svg width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><polyline points="22 12 18 12 15 21 9 3 6 12 2 12"/></svg>
      <div>No matches yet.<br>Log your first game to see rankings.</div>
    </div>`;
    return;
  }

  document.getElementById('lbList').innerHTML = stats.map((p, i) => {
    const idx = pidx(p.id);
    const pct = Math.round(p.rate * 100);
    return `
      <div class="lb-item">
        <div class="lb-rank">${i + 1}</div>
        <div class="lb-avatar av-${idx}">${initials(p.name)}</div>
        <div class="lb-info">
          <div class="lb-name">${p.name}</div>
          <div class="lb-sub">${p.total > 0 ? `${p.wins}W · ${p.losses}L` : 'No games yet'}</div>
        </div>
        <div class="lb-right">
          <div class="lb-pct">${p.total > 0 ? pct + '%' : '—'}</div>
          <div class="lb-bar-bg"><div class="lb-bar bar-${idx}" style="width:${pct}%"></div></div>
        </div>
      </div>
    `;
  }).join('');
}

function buildGrids() {
  ['t1Grid','t2Grid'].forEach((id, ti) => {
    document.getElementById(id).innerHTML = PLAYERS.map(p =>
      `<div class="player-chip" id="chip-t${ti+1}-${p.id}" onclick="pick(${ti+1},'${p.id}')">${p.name}</div>`
    ).join('');
  });
  updateTeamLabels();
}

function pick(team, pid) {
  const other = team === 1 ? t2 : t1;
  if (other.includes(pid)) { showToast('Already on the other team'); return; }
  const arr = team === 1 ? t1 : t2;
  const cls = team === 1 ? 'selected-t1' : 'selected-t2';
  if (arr.includes(pid)) {
    arr.splice(arr.indexOf(pid), 1);
    document.getElementById(`chip-t${team}-${pid}`)?.classList.remove(cls);
  } else {
    if (arr.length >= 2) {
      const old = arr.shift();
      document.getElementById(`chip-t${team}-${old}`)?.classList.remove(cls);
    }
    arr.push(pid);
    document.getElementById(`chip-t${team}-${pid}`)?.classList.add(cls);
  }
  updateTeamLabels();
}

function updateTeamLabels() {
  document.getElementById('t1Label').textContent = t1.length ? t1.map(pname).map(n => n.split(' ')[0]).join(' & ') : 'Team 1';
  document.getElementById('t2Label').textContent = t2.length ? t2.map(pname).map(n => n.split(' ')[0]).join(' & ') : 'Team 2';
}

function clearForm() {
  t1 = []; t2 = [];
  document.getElementById('score1').value = '';
  document.getElementById('score2').value = '';
  buildGrids();
}

async function submitMatch() {
  if (t1.length !== 2 || t2.length !== 2) { showToast('Pick 2 players per team'); return; }
  const s1 = parseInt(document.getElementById('score1').value);
  const s2 = parseInt(document.getElementById('score2').value);
  if (isNaN(s1) || isNaN(s2)) { showToast('Enter both scores'); return; }
  if (s1 === s2) { showToast('Scores must differ'); return; }
  const match = { id: Date.now(), date: new Date().toISOString().split('T')[0], t1:[...t1], t2:[...t2], s1, s2 };
  const winner = s1 > s2 ? t1.map(pname).join(' & ') : t2.map(pname).join(' & ');
  showToast('Saving...');
  const ok = await save(match);
  if (ok) {
    clearForm();
    showToast(`${winner} wins`);
    updateCount();
    renderLB();
  }
}

function renderHistory() {
  const el = document.getElementById('historyList');
  if (!matches.length) {
    el.innerHTML = `<div class="empty"><svg width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><rect x="3" y="4" width="18" height="18" rx="2"/><line x1="3" y1="10" x2="21" y2="10"/></svg><div>No matches yet.</div></div>`;
    return;
  }
  const colours = ['var(--sage)','var(--peach)','var(--lavender)','var(--sky)','var(--rose)','var(--gold)'];
  el.innerHTML = matches.map(m => {
    const t1w = m.s1 > m.s2;
    const c = colours[pidx(m.t1[0])];
    return `
      <div class="match-item">
        <div class="match-indicator" style="background:${c}"></div>
        <div class="match-teams">
          <div class="match-team ${t1w?'won':''}">${m.t1.map(pname).join(' & ')}</div>
          <div class="match-team ${!t1w?'won':''}">${m.t2.map(pname).join(' & ')}</div>
        </div>
        <div class="match-right">
          <div class="match-score-display"><span class="${t1w?'w':'l'}">${m.s1}</span><span style="color:var(--surface3)"> · </span><span class="${!t1w?'w':'l'}">${m.s2}</span></div>
          <div class="match-date">${fmtDate(m.date)}</div>
        </div>
      </div>
    `;
  }).join('');
}

function fmtDate(d) {
  return new Date(d + 'T00:00:00').toLocaleDateString('en-GB', { day:'numeric', month:'short' });
}

function renderH2H() {
  document.getElementById('h2hPills').innerHTML = PLAYERS.map(p =>
    `<div class="player-pill ${h2hPick===p.id?'active':''}" onclick="pickH2H('${p.id}')">${p.name}</div>`
  ).join('');
  renderH2HGrid();
}

function pickH2H(pid) { h2hPick = pid; renderH2H(); }

function renderH2HGrid() {
  const el = document.getElementById('h2hContent');
  if (!h2hPick) {
    el.innerHTML = `<div class="empty" style="padding:24px 0;">Select a player above</div>`;
    return;
  }
  const others = PLAYERS.filter(p => p.id !== h2hPick);
  const cells = others.map(opp => {
    let w = 0, l = 0;
    matches.forEach(m => {
      const mt = m.t1.includes(h2hPick)?'t1':m.t2.includes(h2hPick)?'t2':null;
      if (!mt) return;
      const ot = m.t1.includes(opp.id)?'t1':m.t2.includes(opp.id)?'t2':null;
      if (!ot || mt===ot) return;
      const t1w = m.s1 > m.s2;
      ((mt==='t1'&&t1w)||(mt==='t2'&&!t1w)) ? w++ : l++;
    });
    const cls = w>l?'pos':l>w?'neg':'neu';
    const oi = pidx(opp.id);
    return `
      <div class="h2h-cell">
        <div class="h2h-av av-${oi}">${initials(opp.name)}</div>
        <div class="h2h-info">
          <div class="h2h-name">${opp.name}</div>
          <div class="h2h-record ${cls}">${w}–${l}</div>
        </div>
      </div>
    `;
  }).join('');
  el.innerHTML = `<div class="h2h-grid">${cells}</div>`;
}

function renderStats() {
  const el = document.getElementById('statsContent');
  if (!matches.length) {
    el.innerHTML = `<div class="empty"><svg width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><line x1="18" y1="20" x2="18" y2="10"/><line x1="12" y1="20" x2="12" y2="4"/><line x1="6" y1="20" x2="6" y2="14"/></svg><div>Log some matches to see insights.</div></div>`;
    return;
  }

  const stats = calcStats();
  const pm = {};
  matches.forEach(m => {
    [m.t1, m.t2].forEach((team, ti) => {
      if (team.length < 2) return;
      const key = [...team].sort().join('-');
      if (!pm[key]) pm[key] = { wins:0, total:0, players:team };
      const won = (ti===0&&m.s1>m.s2)||(ti===1&&m.s2>m.s1);
      pm[key].total++;
      if (won) pm[key].wins++;
    });
  });

  const pairs = Object.values(pm).sort((a,b)=>(b.wins/b.total)-(a.wins/a.total));
  const bestPair = pairs[0];
  const top = [...stats].filter(p=>p.total>0).sort((a,b)=>b.rate-a.rate)[0];
  const closest = [...matches].sort((a,b)=>Math.abs(a.s1-a.s2)-Math.abs(b.s1-b.s2))[0];
  const avgGap = (matches.reduce((s,m)=>s+Math.abs(m.s1-m.s2),0)/matches.length).toFixed(1);
  const mostActive = [...stats].sort((a,b)=>b.total-a.total)[0];

  let html = `<div class="section-title">Highlights</div>`;

  if (top) html += `<div class="stat-highlight"><div class="stat-icon">👑</div><div class="stat-body"><div class="stat-eyebrow">Top Player</div><div class="stat-val">${top.name}</div><div class="stat-sub">${Math.round(top.rate*100)}% win rate · ${top.wins}W ${top.losses}L</div></div></div>`;
  if (bestPair) html += `<div class="stat-highlight"><div class="stat-icon">🤝</div><div class="stat-body"><div class="stat-eyebrow">Best Partnership</div><div class="stat-val">${bestPair.players.map(pname).join(' & ')}</div><div class="stat-sub">${bestPair.wins}W ${bestPair.total-bestPair.wins}L · ${Math.round(bestPair.wins/bestPair.total*100)}%</div></div></div>`;
  if (closest) html += `<div class="stat-highlight"><div class="stat-icon">⚡</div><div class="stat-body"><div class="stat-eyebrow">Closest Match</div><div class="stat-val">${closest.s1}–${closest.s2}</div><div class="stat-sub">${closest.t1.map(pname).join(' & ')} vs ${closest.t2.map(pname).join(' & ')}</div></div></div>`;

  html += `<div class="section-title" style="margin-top:16px;">Overview</div>
  <div class="overview-grid">
    <div class="overview-cell"><div class="overview-num">${matches.length}</div><div class="overview-label">Matches</div></div>
    <div class="overview-cell"><div class="overview-num">${avgGap}</div><div class="overview-label">Avg gap</div></div>
    <div class="overview-cell"><div class="overview-num">${mostActive.name.split(' ')[0]}</div><div class="overview-label">Most active</div></div>
  </div>`;

  if (pairs.length) {
    html += `<div class="section-title" style="margin-top:16px;">Partnerships</div><div class="card">`;
    html += pairs.slice(0,6).map(p=>`
      <div class="pair-row">
        <div><div class="pair-names">${p.players.map(pname).join(' & ')}</div><div class="pair-sub">${p.wins}W · ${p.total-p.wins}L · ${p.total} games</div></div>
        <div class="pair-pct">${Math.round(p.wins/p.total*100)}%</div>
      </div>`).join('');
    html += `</div>`;
  }

  el.innerHTML = html;
}

function showToast(msg) {
  const el = document.getElementById('toast');
  el.textContent = msg;
  el.classList.add('show');
  setTimeout(() => el.classList.remove('show'), 2400);
}

buildGrids();
loadMatches();
</script>
</body>
</html>
