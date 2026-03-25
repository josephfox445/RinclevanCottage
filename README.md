# RinclevanCottage
Fox Family calendar 
[rinclevan (4).html](https://github.com/user-attachments/files/26254985/rinclevan.4.html)
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Rinclevan Cottage Bookings</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,600;0,700;1,400&family=Lato:wght@300;400;700&display=swap" rel="stylesheet">
<style>
  :root {
    --cream: #f5f0e8;
    --dark-green: #2c4a3e;
    --mid-green: #3d6b5c;
    --light-green: #7aab98;
    --warm-tan: #c8a96e;
    --rust: #b05b3b;
    --white: #fdfaf4;
    --text-dark: #1e2d28;
    --text-mid: #4a5e57;
    --border: #d4c9b0;
    --shadow: rgba(44,74,62,0.15);
  }

  * { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    font-family: 'Lato', sans-serif;
    background: var(--cream);
    color: var(--text-dark);
    min-height: 100vh;
  }

  /* ── HERO HEADER ── */
  header {
    background: var(--dark-green);
    color: var(--white);
    padding: 0;
    position: relative;
    overflow: hidden;
  }
  .header-texture {
    position: absolute; inset: 0;
    background-image:
      radial-gradient(ellipse at 20% 50%, rgba(122,171,152,0.18) 0%, transparent 60%),
      radial-gradient(ellipse at 80% 20%, rgba(200,169,110,0.12) 0%, transparent 50%);
    pointer-events: none;
  }
  .header-inner {
    position: relative;
    max-width: 1100px;
    margin: 0 auto;
    padding: 48px 24px 36px;
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
  }
  .cottage-icon {
    font-size: 3rem;
    margin-bottom: 12px;
    filter: drop-shadow(0 2px 8px rgba(0,0,0,0.3));
    animation: float 4s ease-in-out infinite;
  }
  @keyframes float {
    0%,100% { transform: translateY(0); }
    50% { transform: translateY(-6px); }
  }
  header h1 {
    font-family: 'Playfair Display', serif;
    font-size: clamp(1.9rem, 5vw, 3rem);
    font-weight: 700;
    letter-spacing: 0.01em;
    color: var(--white);
    line-height: 1.15;
  }
  header h1 span { color: var(--warm-tan); }
  .tagline {
    font-size: 0.95rem;
    color: var(--light-green);
    letter-spacing: 0.08em;
    text-transform: uppercase;
    margin-top: 10px;
    font-weight: 300;
  }
  .donegal-badge {
    margin-top: 16px;
    background: rgba(255,255,255,0.08);
    border: 1px solid rgba(200,169,110,0.4);
    color: var(--warm-tan);
    font-size: 0.8rem;
    padding: 5px 16px;
    border-radius: 20px;
    letter-spacing: 0.06em;
    text-transform: uppercase;
  }

  /* ── NAV TABS ── */
  nav {
    background: var(--mid-green);
    border-bottom: 3px solid var(--warm-tan);
  }
  .nav-inner {
    max-width: 1100px;
    margin: 0 auto;
    display: flex;
    gap: 0;
    overflow-x: auto;
  }
  .nav-btn {
    flex: 1;
    min-width: 130px;
    background: none;
    border: none;
    color: rgba(255,255,255,0.7);
    font-family: 'Lato', sans-serif;
    font-size: 0.88rem;
    font-weight: 700;
    letter-spacing: 0.06em;
    text-transform: uppercase;
    padding: 15px 12px;
    cursor: pointer;
    transition: all 0.25s;
    border-bottom: 3px solid transparent;
    margin-bottom: -3px;
    white-space: nowrap;
  }
  .nav-btn:hover { color: var(--white); background: rgba(255,255,255,0.07); }
  .nav-btn.active { color: var(--white); border-bottom-color: var(--warm-tan); background: rgba(255,255,255,0.1); }

  /* ── MAIN LAYOUT ── */
  main { max-width: 1100px; margin: 0 auto; padding: 32px 16px 64px; }

  .section { display: none; }
  .section.active { display: block; animation: fadeIn 0.3s ease; }
  @keyframes fadeIn { from { opacity: 0; transform: translateY(8px); } to { opacity: 1; transform: none; } }

  /* ── CARDS ── */
  .card {
    background: var(--white);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 28px;
    box-shadow: 0 4px 20px var(--shadow);
    margin-bottom: 24px;
  }
  .card-title {
    font-family: 'Playfair Display', serif;
    font-size: 1.35rem;
    color: var(--dark-green);
    margin-bottom: 18px;
    display: flex;
    align-items: center;
    gap: 10px;
  }
  .card-title::after {
    content: '';
    flex: 1;
    height: 1px;
    background: var(--border);
    margin-left: 8px;
  }

  /* ── CALENDAR ── */
  .cal-controls {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 20px;
    flex-wrap: wrap;
    gap: 10px;
  }
  .cal-controls h2 {
    font-family: 'Playfair Display', serif;
    font-size: 1.5rem;
    color: var(--dark-green);
  }
  .cal-nav-btn {
    background: var(--dark-green);
    color: var(--white);
    border: none;
    border-radius: 8px;
    width: 38px; height: 38px;
    font-size: 1.1rem;
    cursor: pointer;
    transition: background 0.2s;
  }
  .cal-nav-btn:hover { background: var(--mid-green); }

  .calendar-grid {
    display: grid;
    grid-template-columns: repeat(7, 1fr);
    gap: 3px;
  }
  .cal-header {
    text-align: center;
    font-size: 0.75rem;
    font-weight: 700;
    letter-spacing: 0.07em;
    text-transform: uppercase;
    color: var(--text-mid);
    padding: 8px 2px;
  }
  .cal-day {
    min-height: 72px;
    border-radius: 8px;
    padding: 6px;
    border: 1.5px solid transparent;
    cursor: pointer;
    transition: all 0.18s;
    background: var(--cream);
    position: relative;
    overflow: hidden;
  }
  .cal-day:hover:not(.empty):not(.past) { border-color: var(--light-green); background: #edf5f1; }
  .cal-day.empty { background: transparent; cursor: default; }
  .cal-day.past { opacity: 0.45; cursor: default; }
  .cal-day.today { border-color: var(--warm-tan); background: #fef9f0; }
  .cal-day.booked { background: #e8f4ef; border-color: var(--light-green); }
  .cal-day.multi-booked { background: #d4eae2; }
  .day-num {
    font-size: 0.82rem;
    font-weight: 700;
    color: var(--text-mid);
    display: block;
    margin-bottom: 3px;
  }
  .cal-day.today .day-num { color: var(--rust); }
  .booking-pip {
    font-size: 0.65rem;
    font-weight: 700;
    color: var(--dark-green);
    background: rgba(61,107,92,0.15);
    border-radius: 4px;
    padding: 1px 4px;
    margin-top: 2px;
    display: block;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
    line-height: 1.4;
  }
  .booking-pip.unit-2 { background: rgba(200,169,110,0.25); color: #7a5c1a; }
  .booking-pip.unit-3 { background: rgba(176,91,59,0.18); color: #8b3820; }
  .booking-pip.unit-4 { background: rgba(44,74,62,0.25); color: var(--dark-green); }

  /* ── BOOKING FORM ── */
  .form-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 16px; }
  @media(max-width:600px) { .form-grid { grid-template-columns: 1fr; } }

  .form-group { display: flex; flex-direction: column; gap: 6px; }
  .form-group.full { grid-column: 1 / -1; }
  label {
    font-size: 0.82rem;
    font-weight: 700;
    letter-spacing: 0.05em;
    text-transform: uppercase;
    color: var(--text-mid);
  }
  input, select, textarea {
    font-family: 'Lato', sans-serif;
    font-size: 0.95rem;
    padding: 10px 14px;
    border: 1.5px solid var(--border);
    border-radius: 8px;
    background: var(--cream);
    color: var(--text-dark);
    transition: border-color 0.2s;
    outline: none;
  }
  input:focus, select:focus, textarea:focus { border-color: var(--mid-green); }
  textarea { resize: vertical; min-height: 70px; }

  .btn {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    padding: 12px 28px;
    border-radius: 8px;
    border: none;
    font-family: 'Lato', sans-serif;
    font-weight: 700;
    font-size: 0.9rem;
    letter-spacing: 0.05em;
    text-transform: uppercase;
    cursor: pointer;
    transition: all 0.2s;
  }
  .btn-primary { background: var(--dark-green); color: var(--white); }
  .btn-primary:hover { background: var(--mid-green); transform: translateY(-1px); box-shadow: 0 4px 12px var(--shadow); }
  .btn-danger { background: var(--rust); color: var(--white); font-size: 0.8rem; padding: 7px 14px; }
  .btn-danger:hover { background: #8b3820; }
  .btn-sm { padding: 7px 14px; font-size: 0.8rem; }

  /* ── BOOKINGS LIST ── */
  .booking-item {
    background: var(--cream);
    border-left: 4px solid var(--mid-green);
    border-radius: 0 8px 8px 0;
    padding: 14px 16px;
    margin-bottom: 10px;
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    gap: 12px;
    flex-wrap: wrap;
    animation: slideIn 0.3s ease;
  }
  @keyframes slideIn { from { opacity:0; transform: translateX(-8px); } to { opacity:1; transform: none; } }
  .booking-item.past-booking { border-left-color: var(--border); opacity: 0.6; }
  .booking-name {
    font-family: 'Playfair Display', serif;
    font-size: 1.05rem;
    color: var(--dark-green);
    font-weight: 600;
  }
  .booking-meta {
    font-size: 0.84rem;
    color: var(--text-mid);
    margin-top: 3px;
    line-height: 1.5;
  }
  .booking-meta strong { color: var(--text-dark); }
  .cost-badge {
    background: var(--dark-green);
    color: var(--white);
    font-size: 0.8rem;
    font-weight: 700;
    padding: 3px 10px;
    border-radius: 20px;
    white-space: nowrap;
  }

  /* ── FEES ── */
  .fee-box {
    background: var(--dark-green);
    color: var(--white);
    border-radius: 12px;
    padding: 24px;
    margin-bottom: 20px;
  }
  .fee-box h3 {
    font-family: 'Playfair Display', serif;
    font-size: 1.2rem;
    color: var(--warm-tan);
    margin-bottom: 14px;
  }
  .unit-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(220px, 1fr)); gap: 12px; margin-top: 14px; }
  .unit-card {
    background: rgba(255,255,255,0.08);
    border: 1px solid rgba(200,169,110,0.3);
    border-radius: 10px;
    padding: 14px;
  }
  .unit-card .unit-label {
    font-weight: 700;
    color: var(--warm-tan);
    font-size: 0.85rem;
    letter-spacing: 0.05em;
    text-transform: uppercase;
    margin-bottom: 6px;
  }
  .unit-card p { font-size: 0.88rem; color: rgba(255,255,255,0.85); line-height: 1.5; }
  .fee-price {
    font-family: 'Playfair Display', serif;
    font-size: 2rem;
    color: var(--warm-tan);
    font-weight: 700;
  }
  .info-note {
    background: rgba(200,169,110,0.12);
    border: 1px solid rgba(200,169,110,0.35);
    border-radius: 8px;
    padding: 12px 16px;
    font-size: 0.88rem;
    color: rgba(255,255,255,0.85);
    margin-top: 14px;
    line-height: 1.6;
  }
  .info-note strong { color: var(--warm-tan); }

  /* ── OWNERS ── */
  .owners-box {
    background: var(--mid-green);
    color: var(--white);
    border-radius: 10px;
    padding: 18px 20px;
    font-size: 0.9rem;
    line-height: 1.7;
  }
  .owners-box strong { color: var(--warm-tan); }

  /* ── MODAL ── */
  .modal-overlay {
    display: none;
    position: fixed; inset: 0;
    background: rgba(20,40,30,0.65);
    z-index: 100;
    align-items: center;
    justify-content: center;
    padding: 16px;
  }
  .modal-overlay.open { display: flex; }
  .modal {
    background: var(--white);
    border-radius: 14px;
    padding: 28px;
    max-width: 480px;
    width: 100%;
    box-shadow: 0 20px 60px rgba(0,0,0,0.25);
    animation: popIn 0.25s ease;
  }
  @keyframes popIn { from { transform: scale(0.93); opacity: 0; } to { transform: none; opacity: 1; } }
  .modal h3 {
    font-family: 'Playfair Display', serif;
    font-size: 1.25rem;
    color: var(--dark-green);
    margin-bottom: 14px;
  }
  .modal-booking-list { margin: 10px 0; }
  .modal-booking-entry {
    background: var(--cream);
    border-left: 3px solid var(--mid-green);
    border-radius: 0 6px 6px 0;
    padding: 10px 12px;
    margin-bottom: 8px;
  }
  .modal-booking-entry p { font-size: 0.88rem; color: var(--text-mid); margin-top: 3px; }
  .modal-actions { display: flex; gap: 10px; margin-top: 16px; flex-wrap: wrap; }
  .modal-close { background: none; border: none; cursor: pointer; font-size: 1.4rem; color: var(--text-mid); float: right; }

  /* ── TOAST ── */
  .toast {
    position: fixed; bottom: 24px; left: 50%; transform: translateX(-50%) translateY(80px);
    background: var(--dark-green); color: var(--white);
    padding: 12px 24px; border-radius: 30px;
    font-size: 0.9rem; font-weight: 700;
    box-shadow: 0 8px 24px rgba(0,0,0,0.25);
    z-index: 200;
    transition: transform 0.35s cubic-bezier(.34,1.56,.64,1);
    white-space: nowrap;
  }
  .toast.show { transform: translateX(-50%) translateY(0); }

  /* ── LEGEND ── */
  .legend { display: flex; gap: 14px; flex-wrap: wrap; margin-bottom: 14px; }
  .legend-item { display: flex; align-items: center; gap: 5px; font-size: 0.8rem; color: var(--text-mid); }
  .legend-dot { width: 12px; height: 12px; border-radius: 3px; }

  /* ── UPCOMING STRIP ── */
  .upcoming-strip {
    background: var(--dark-green);
    color: var(--white);
    border-radius: 10px;
    padding: 14px 18px;
    margin-bottom: 20px;
    display: flex;
    align-items: center;
    gap: 14px;
    flex-wrap: wrap;
  }
  .upcoming-strip .label {
    font-size: 0.75rem;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    color: var(--light-green);
    font-weight: 700;
  }
  .upcoming-chip {
    background: rgba(255,255,255,0.1);
    border-radius: 20px;
    padding: 4px 12px;
    font-size: 0.82rem;
  }
  .upcoming-chip strong { color: var(--warm-tan); }

  /* ── COST CALCULATOR ── */
  .calc-result {
    background: var(--dark-green);
    color: var(--white);
    border-radius: 10px;
    padding: 18px;
    margin-top: 16px;
    display: none;
  }
  .calc-result.visible { display: block; animation: fadeIn 0.3s ease; }
  .calc-result h4 { font-family: 'Playfair Display', serif; font-size: 1.1rem; color: var(--warm-tan); margin-bottom: 10px; }
  .calc-line { display: flex; justify-content: space-between; font-size: 0.9rem; padding: 5px 0; border-bottom: 1px solid rgba(255,255,255,0.1); }
  .calc-total { display: flex; justify-content: space-between; font-size: 1.1rem; font-weight: 700; padding: 10px 0 0; color: var(--warm-tan); }

  @keyframes pulse {
    0%,100% { opacity: 1; transform: scale(1); }
    50% { opacity: 0.5; transform: scale(1.3); }
  }

  @media(max-width:480px) {
    .cal-day { min-height: 54px; padding: 4px; }
    .booking-pip { font-size: 0.58rem; }
    .day-num { font-size: 0.75rem; }
  }
</style>
</head>
<body>

<header>
  <div class="header-texture"></div>
  <div class="header-inner">
    <div class="cottage-icon">🏡</div>
    <h1>Rinclevan <span>Cottage</span> Bookings</h1>
    <p class="tagline">The Fox Family — Donegal</p>
    <div class="donegal-badge">📍 County Donegal, Ireland</div>
    <div style="margin-top:10px;font-size:0.75rem;color:rgba(122,171,152,0.8);display:flex;align-items:center;gap:6px">
      <span style="width:7px;height:7px;background:#7aab98;border-radius:50%;display:inline-block;animation:pulse 2s infinite"></span>
      Live — syncs across all family devices
    </div>
  </div>
</header>

<nav>
  <div class="nav-inner">
    <button class="nav-btn active" onclick="showSection('calendar')">📅 Calendar</button>
    <button class="nav-btn" onclick="showSection('book')">✏️ Book Dates</button>
    <button class="nav-btn" onclick="showSection('bookings')">📋 All Bookings</button>
    <button class="nav-btn" onclick="showSection('fees')">💷 Fees</button>
  </div>
</nav>

<main>

  <!-- ═══ CALENDAR SECTION ═══ -->
  <div id="section-calendar" class="section active">

    <div id="upcoming-strip" class="upcoming-strip" style="display:none">
      <span class="label">🔔 Coming up</span>
      <span id="upcoming-chips"></span>
    </div>

    <div class="card">
      <div class="cal-controls">
        <button class="cal-nav-btn" onclick="changeMonth(-1)">‹</button>
        <h2 id="cal-month-label">Month Year</h2>
        <button class="cal-nav-btn" onclick="changeMonth(1)">›</button>
      </div>
      <div class="legend">
        <div class="legend-item"><div class="legend-dot" style="background:#e8f4ef;border:1.5px solid var(--light-green)"></div> Booked</div>
        <div class="legend-item"><div class="legend-dot" style="background:#fef9f0;border:1.5px solid var(--warm-tan)"></div> Today</div>
        <div class="legend-item"><div class="legend-dot" style="background:var(--cream);border:1.5px solid transparent"></div> Available</div>
      </div>
      <div class="calendar-grid" id="calendar-grid"></div>
    </div>
  </div>

  <!-- ═══ BOOK SECTION ═══ -->
  <div id="section-book" class="section">
    <div class="card">
      <div class="card-title">✏️ Make a Booking</div>
      <div class="form-grid">
        <div class="form-group">
          <label>Your Name</label>
          <input type="text" id="f-name" placeholder="e.g. Joe Fox">
        </div>
        <div class="form-group">
          <label>Unit Type</label>
          <select id="f-unit">
            <option value="na">N/A — Calculate when leaving</option>
            <option value="">— Select unit type —</option>
            <option value="solo">Solo (1 person)</option>
            <option value="solo-friends">1 Person + Friends</option>
            <option value="couple">Couple / 2 siblings</option>
            <option value="couple-friends">Couple + Friends (2 units)</option>
            <option value="family">Family (parents + kids)</option>
          </select>
        </div>
        <div class="form-group">
          <label>Check-in Date</label>
          <input type="date" id="f-start">
        </div>
        <div class="form-group">
          <label>Check-out Date</label>
          <input type="date" id="f-end">
        </div>
        <div class="form-group">
          <label>Number of Units</label>
          <select id="f-units-count">
            <option value="na">N/A — Calculate when leaving</option>
            <option value="1">1 Unit</option>
            <option value="2">2 Units</option>
            <option value="3">3 Units</option>
            <option value="4">4 Units</option>
          </select>
        </div>
        <div class="form-group full">
          <label>Notes (guests, occasion, etc.)</label>
          <textarea id="f-notes" placeholder="e.g. Bringing 2 friends, long weekend, kids in tow..."></textarea>
        </div>
      </div>

      <div id="calc-result" class="calc-result">
        <h4>💷 Estimated Cost</h4>
        <div id="calc-lines"></div>
        <div class="calc-total" id="calc-total"></div>
        <div id="calc-ev-note" style="font-size:0.8rem;margin-top:10px;color:rgba(255,255,255,0.65);display:none">⚡ EV charger surcharge to be confirmed and added to oil costs.</div>
      </div>

      <div style="margin-top:20px;display:flex;gap:12px;flex-wrap:wrap">
        <button class="btn btn-primary" onclick="calculateCost()">💷 Estimate Cost</button>
        <button class="btn btn-primary" onclick="submitBooking()" style="background:var(--rust)">✅ Confirm Booking</button>
      </div>
    </div>
  </div>

  <!-- ═══ ALL BOOKINGS SECTION ═══ -->
  <div id="section-bookings" class="section">
    <div class="card">
      <div class="card-title">📋 All Bookings</div>
      <div style="display:flex;gap:10px;margin-bottom:18px;flex-wrap:wrap">
        <button class="btn btn-sm btn-primary" onclick="filterBookings('all')" id="filter-all">All</button>
        <button class="btn btn-sm" onclick="filterBookings('upcoming')" id="filter-upcoming" style="background:var(--cream);color:var(--dark-green);border:1.5px solid var(--border)">Upcoming</button>
        <button class="btn btn-sm" onclick="filterBookings('past')" id="filter-past" style="background:var(--cream);color:var(--dark-green);border:1.5px solid var(--border)">Past</button>
      </div>
      <div id="bookings-list">
        <p style="color:var(--text-mid);font-style:italic">No bookings yet. Be the first to book! 🏡</p>
      </div>
    </div>
  </div>

  <!-- ═══ FEES SECTION ═══ -->
  <div id="section-fees" class="section">

    <div class="fee-box">
      <h3>💷 Daily Charge — Per Unit</h3>
      <p style="font-size:0.9rem;color:rgba(255,255,255,0.8);margin-bottom:12px">Each unit pays <strong style="color:var(--warm-tan)">£20 per day</strong>, regardless of how many other units are staying at the same time. Oil costs are calculated separately and added on top.</p>
      <div style="margin-bottom:16px">
        <div class="fee-price">£20 <span style="font-size:1rem;font-weight:400;color:rgba(255,255,255,0.6)">/ unit / day</span></div>
        <div style="font-size:0.82rem;color:rgba(255,255,255,0.5);margin-top:4px">+ Oil costs + EV charger (if applicable)</div>
      </div>

      <h3 style="margin-top:20px">What is a "Unit"?</h3>
      <div class="unit-grid">
        <div class="unit-card">
          <div class="unit-label">Unit 1 — Solo</div>
          <p>One person going on their own. <em>e.g. Joe.</em><br>→ £20/day + oil</p>
        </div>
        <div class="unit-card">
          <div class="unit-label">Unit 2 — Solo + Friends</div>
          <p>One person and their friends count as <strong>one unit</strong> together. <em>e.g. Liam + 2 friends.</em><br>→ £20/day + oil</p>
        </div>
        <div class="unit-card">
          <div class="unit-label">Unit 3 — Couple / Siblings</div>
          <p>Two people together (couple or two siblings) = 1 unit.<br>→ £20/day + oil</p>
        </div>
        <div class="unit-card">
          <div class="unit-label">Unit 4 — Family</div>
          <p>Parents + their children = 1 unit. <em>e.g. Joe, Aimee & kids.</em><br>→ £20/day + oil</p>
        </div>
        <div class="unit-card" style="grid-column:1/-1;background:rgba(200,169,110,0.18)">
          <div class="unit-label">⚠️ Couple + Friends</div>
          <p>If a couple brings friends, that is <strong>2 units</strong>: the couple (1 unit) and the friends (1 unit). <em>e.g. a couple + 2 friends for a weekend = £120 + oil.</em></p>
        </div>
      </div>

      <div class="info-note">
        <strong>🛢️ Oil:</strong> Worked out in the usual way and added on top of the daily charge.<br>
        <strong>⚡ EV Car Charger:</strong> Use of the car charger is likely to be added on to the daily contribution for those with electric cars.<br>
        <strong>📅 Example — Weekend (Fri–Sun = 2 nights):</strong> A couple + 2 friends = 2 units × £20 × 2 days = £80 + oil.
      </div>
    </div>

    <div class="card">
      <div class="card-title">🏠 What the Daily Charge Covers</div>
      <div style="display:grid;grid-template-columns:repeat(auto-fill,minmax(180px,1fr));gap:12px">
        <div style="background:var(--cream);border-radius:8px;padding:12px;text-align:center;font-size:0.88rem">⚡<br>Electricity</div>
        <div style="background:var(--cream);border-radius:8px;padding:12px;text-align:center;font-size:0.88rem">📺<br>TV Licence</div>
        <div style="background:var(--cream);border-radius:8px;padding:12px;text-align:center;font-size:0.88rem">📶<br>Wi-Fi</div>
        <div style="background:var(--cream);border-radius:8px;padding:12px;text-align:center;font-size:0.88rem">🌿<br>Grass Cutting</div>
        <div style="background:var(--cream);border-radius:8px;padding:12px;text-align:center;font-size:0.88rem">🏡<br>Use of Cottage</div>
      </div>
    </div>

    <div class="owners-box">
      <strong>🏦 Owners' Monthly Contributions (Direct Debit)</strong><br>
      The owners' monthly payments continue to cover: <strong>house insurance</strong>, <strong>property tax</strong>, <strong>bank fees</strong>, <strong>maintenance & repairs</strong>, <strong>furnishings</strong>, and <strong>replacement of white goods</strong> or other items. This is separate from the daily usage charge above.
    </div>
  </div>

</main>

<!-- ═══ DAY MODAL ═══ -->
<div class="modal-overlay" id="day-modal">
  <div class="modal">
    <button class="modal-close" onclick="closeModal()">✕</button>
    <h3 id="modal-date-title">Date</h3>
    <div id="modal-content"></div>
    <div class="modal-actions">
      <button class="btn btn-primary btn-sm" onclick="bookThisDate()">✏️ Book This Date</button>
      <button class="btn btn-sm" onclick="closeModal()" style="background:var(--cream);border:1.5px solid var(--border);color:var(--text-dark)">Close</button>
    </div>
  </div>
</div>

<div class="toast" id="toast"></div>

<script>
// ── STATE ──────────────────────────────────────────
let bookings = [];
let currentYear, currentMonth;
let selectedDateForModal = null;
let activeFilter = 'all';

const COLORS = ['unit-1','unit-2','unit-3','unit-4'];

// ── SHARED STORAGE (real-time sync) ────────────────
let lastKnownVersion = null;

async function saveBookings() {
  try {
    const payload = { bookings, version: Date.now() };
    await window.storage.set('rinclevan-bookings', JSON.stringify(payload), true);
    lastKnownVersion = payload.version;
  } catch(e) { console.error('Save failed', e); }
}

async function loadBookings() {
  try {
    const r = await window.storage.get('rinclevan-bookings', true);
    if (r) {
      const payload = JSON.parse(r.value);
      bookings = payload.bookings || [];
      lastKnownVersion = payload.version || null;
    }
  } catch(e) { bookings = []; }
}

// Poll every 15 seconds for updates from other family members
async function pollForUpdates() {
  try {
    const r = await window.storage.get('rinclevan-bookings', true);
    if (r) {
      const payload = JSON.parse(r.value);
      if (payload.version && payload.version !== lastKnownVersion) {
        bookings = payload.bookings || [];
        lastKnownVersion = payload.version;
        renderCalendar();
        if (document.getElementById('section-bookings').classList.contains('active')) {
          renderBookingsList();
        }
        showSyncBadge();
      }
    }
  } catch(e) {}
}

function showSyncBadge() {
  const t = document.getElementById('toast');
  t.textContent = '🔄 Calendar updated by another family member!';
  t.classList.add('show');
  setTimeout(() => t.classList.remove('show'), 3200);
}

// ── NAV ────────────────────────────────────────────
function showSection(id) {
  document.querySelectorAll('.section').forEach(s => s.classList.remove('active'));
  document.querySelectorAll('.nav-btn').forEach(b => b.classList.remove('active'));
  document.getElementById('section-' + id).classList.add('active');
  event.currentTarget.classList.add('active');
  if (id === 'bookings') renderBookingsList();
  if (id === 'calendar') renderCalendar();
}

// ── CALENDAR ───────────────────────────────────────
const MONTHS = ['January','February','March','April','May','June','July','August','September','October','November','December'];
const DAYS = ['Sun','Mon','Tue','Wed','Thu','Fri','Sat'];

function changeMonth(dir) {
  currentMonth += dir;
  if (currentMonth > 11) { currentMonth = 0; currentYear++; }
  if (currentMonth < 0) { currentMonth = 11; currentYear--; }
  renderCalendar();
}

function renderCalendar() {
  document.getElementById('cal-month-label').textContent = MONTHS[currentMonth] + ' ' + currentYear;
  const grid = document.getElementById('calendar-grid');
  grid.innerHTML = '';

  DAYS.forEach(d => {
    const el = document.createElement('div');
    el.className = 'cal-header';
    el.textContent = d;
    grid.appendChild(el);
  });

  const firstDay = new Date(currentYear, currentMonth, 1).getDay();
  const daysInMonth = new Date(currentYear, currentMonth + 1, 0).getDate();
  const today = new Date(); today.setHours(0,0,0,0);

  for (let i = 0; i < firstDay; i++) {
    const el = document.createElement('div');
    el.className = 'cal-day empty';
    grid.appendChild(el);
  }

  for (let d = 1; d <= daysInMonth; d++) {
    const date = new Date(currentYear, currentMonth, d);
    const dateStr = toDateStr(date);
    const dayBookings = bookings.filter(b => dateStr >= b.start && dateStr <= b.endStr);

    const el = document.createElement('div');
    el.className = 'cal-day';
    if (date < today) el.classList.add('past');
    if (date.toDateString() === today.toDateString()) el.classList.add('today');
    if (dayBookings.length > 0) el.classList.add('booked');
    if (dayBookings.length > 1) el.classList.add('multi-booked');

    const numEl = document.createElement('span');
    numEl.className = 'day-num';
    numEl.textContent = d;
    el.appendChild(numEl);

    dayBookings.slice(0, 3).forEach((b, i) => {
      const pip = document.createElement('span');
      pip.className = 'booking-pip ' + (COLORS[i % COLORS.length]);
      pip.textContent = b.name;
      el.appendChild(pip);
    });
    if (dayBookings.length > 3) {
      const pip = document.createElement('span');
      pip.className = 'booking-pip';
      pip.textContent = '+' + (dayBookings.length - 3) + ' more';
      el.appendChild(pip);
    }

    if (!el.classList.contains('past') || dayBookings.length > 0) {
      el.addEventListener('click', () => openDayModal(dateStr, dayBookings));
    }
    grid.appendChild(el);
  }

  renderUpcoming();
}

function renderUpcoming() {
  const strip = document.getElementById('upcoming-strip');
  const chips = document.getElementById('upcoming-chips');
  const today = new Date(); today.setHours(0,0,0,0);
  const soon = bookings
    .filter(b => new Date(b.start) >= today)
    .sort((a,b) => a.start.localeCompare(b.start))
    .slice(0, 4);

  if (soon.length === 0) { strip.style.display = 'none'; return; }
  strip.style.display = 'flex';
  chips.innerHTML = soon.map(b =>
    `<span class="upcoming-chip"><strong>${b.name}</strong>: ${formatDate(b.start)}</span>`
  ).join('');
}

function openDayModal(dateStr, dayBookings) {
  selectedDateForModal = dateStr;
  document.getElementById('modal-date-title').textContent = '📅 ' + formatDateFull(dateStr);
  const content = document.getElementById('modal-content');

  if (dayBookings.length === 0) {
    content.innerHTML = '<p style="color:var(--text-mid);font-style:italic;margin:10px 0">No bookings on this date — it\'s free! 🎉</p>';
  } else {
    content.innerHTML = '<div class="modal-booking-list">' +
      dayBookings.map(b => `
        <div class="modal-booking-entry">
          <strong style="font-family:Playfair Display,serif;color:var(--dark-green)">${b.name}</strong>
          <p>📅 ${formatDate(b.start)} → ${formatDate(b.endStr)}</p>
          <p>👥 ${b.unitType === 'na' ? 'Unit type TBC' : (unitTypeLabels[b.unitType] || b.unitType)} · ${b.unitsCount === 'na' ? 'Units TBC' : b.unitsCount + ' unit(s)'}</p>
          ${b.notes ? `<p>💬 ${b.notes}</p>` : ''}
        </div>
      `).join('') +
      '</div>';
  }
  document.getElementById('day-modal').classList.add('open');
}

function closeModal() {
  document.getElementById('day-modal').classList.remove('open');
}

function bookThisDate() {
  closeModal();
  if (selectedDateForModal) {
    document.getElementById('f-start').value = selectedDateForModal;
  }
  showSection('book');
  document.querySelectorAll('.nav-btn')[1].click();
}

// ── BOOKING FORM ───────────────────────────────────
function calculateCost() {
  const start = document.getElementById('f-start').value;
  const end = document.getElementById('f-end').value;
  const unitsVal = document.getElementById('f-units-count').value;
  const units = unitsVal === 'na' ? null : parseInt(unitsVal) || 1;
  const ev = 'no';

  if (!start || !end) { showToast('Please select check-in and check-out dates'); return; }
  const s = new Date(start), e = new Date(end);
  if (e <= s) { showToast('Check-out must be after check-in'); return; }

  const days = Math.round((e - s) / 86400000);
  const total = units !== null ? days * 20 * units : null;
  const linesEl = document.getElementById('calc-lines');
  linesEl.innerHTML = `
    <div class="calc-line"><span>${days} day(s)</span><span>${days} nights</span></div>
    <div class="calc-line"><span>${units !== null ? units + ' unit(s) × £20/day × ' + days + ' day(s)' : 'Units TBC — calculate when leaving'}</span><span>${total !== null ? '£' + total : 'TBC'}</span></div>
    <div class="calc-line"><span>Oil</span><span>To be calculated</span></div>
  `;
  document.getElementById('calc-total').innerHTML = `<span>Estimated Total (excl. oil)</span><span>${total !== null ? '£' + total : 'TBC'}</span>`;
  document.getElementById('calc-ev-note').style.display = 'none';
  document.getElementById('calc-result').classList.add('visible');
}

function submitBooking() {
  const name = document.getElementById('f-name').value.trim();
  const unitType = document.getElementById('f-unit').value;
  const start = document.getElementById('f-start').value;
  const end = document.getElementById('f-end').value;
  const unitsCount = document.getElementById('f-units-count').value;
  const ev = 'no';
  const notes = document.getElementById('f-notes').value.trim();

  if (!name || !start || !end) {
    showToast('⚠️ Please fill in all required fields'); return;
  }
  const s = new Date(start), e = new Date(end);
  if (e <= s) { showToast('Check-out must be after check-in'); return; }

  const endStr = new Date(e - 86400000).toISOString().split('T')[0];
  const days = Math.round((e - s) / 86400000);
  const cost = unitsCount === 'na' ? 'TBC' : days * 20 * parseInt(unitsCount);

  const booking = { id: Date.now(), name, unitType, start, endStr, unitsCount, ev, notes, cost, days };
  bookings.push(booking);
  saveBookings();

  showToast('✅ Booking confirmed for ' + name + '!');
  ['f-name','f-unit','f-start','f-end','f-notes'].forEach(id => {
    const el = document.getElementById(id);
    if (el.tagName === 'SELECT') el.selectedIndex = 0;
    else el.value = '';
  });
  document.getElementById('f-units-count').selectedIndex = 0;
  document.getElementById('calc-result').classList.remove('visible');
  renderCalendar();
}

// ── BOOKINGS LIST ──────────────────────────────────
const unitTypeLabels = {
  solo: 'Solo', 'solo-friends': 'Solo + Friends', couple: 'Couple / Siblings',
  'couple-friends': 'Couple + Friends (2 units)', family: 'Family'
};

function filterBookings(f) {
  activeFilter = f;
  ['all','upcoming','past'].forEach(id => {
    const btn = document.getElementById('filter-' + id);
    btn.style.background = id === f ? 'var(--dark-green)' : 'var(--cream)';
    btn.style.color = id === f ? 'var(--white)' : 'var(--dark-green)';
  });
  renderBookingsList();
}

function renderBookingsList() {
  const list = document.getElementById('bookings-list');
  const today = new Date().toISOString().split('T')[0];

  let filtered = [...bookings].sort((a,b) => a.start.localeCompare(b.start));
  if (activeFilter === 'upcoming') filtered = filtered.filter(b => b.endStr >= today);
  if (activeFilter === 'past') filtered = filtered.filter(b => b.endStr < today);

  if (filtered.length === 0) {
    list.innerHTML = '<p style="color:var(--text-mid);font-style:italic">No bookings found.</p>';
    return;
  }

  list.innerHTML = filtered.map(b => {
    const isPast = b.endStr < today;
    return `<div class="booking-item ${isPast ? 'past-booking' : ''}">
      <div>
        <div class="booking-name">${b.name}</div>
        <div class="booking-meta">
          📅 <strong>${formatDate(b.start)}</strong> → <strong>${formatDate(b.endStr)}</strong> (${b.days} night${b.days>1?'s':''})<br>
          👥 ${b.unitType === 'na' ? 'Unit type TBC' : (unitTypeLabels[b.unitType] || b.unitType)} · ${b.unitsCount === 'na' ? 'Units TBC' : b.unitsCount + ' unit(s)'}<br>
          ${b.notes ? '💬 ' + b.notes : ''}
        </div>
      </div>
      <div style="display:flex;flex-direction:column;align-items:flex-end;gap:6px">
        <span class="cost-badge">${b.cost === 'TBC' ? 'Cost TBC' : '£' + b.cost + ' + oil'}</span>
        <button class="btn btn-danger" onclick="deleteBooking(${b.id})">🗑 Remove</button>
      </div>
    </div>`;
  }).join('');
}

function deleteBooking(id) {
  if (!confirm('Remove this booking?')) return;
  bookings = bookings.filter(b => b.id !== id);
  saveBookings();
  renderBookingsList();
  renderCalendar();
  showToast('Booking removed');
}

// ── HELPERS ────────────────────────────────────────
function toDateStr(date) { return date.toISOString().split('T')[0]; }

function formatDate(str) {
  const d = new Date(str + 'T12:00:00');
  return d.toLocaleDateString('en-GB', { day:'numeric', month:'short', year:'numeric' });
}

function formatDateFull(str) {
  const d = new Date(str + 'T12:00:00');
  return d.toLocaleDateString('en-GB', { weekday:'long', day:'numeric', month:'long', year:'numeric' });
}

function showToast(msg) {
  const t = document.getElementById('toast');
  t.textContent = msg;
  t.classList.add('show');
  setTimeout(() => t.classList.remove('show'), 3200);
}

// ── INIT ───────────────────────────────────────────
(async function init() {
  const now = new Date();
  currentYear = now.getFullYear();
  currentMonth = now.getMonth();
  await loadBookings();
  renderCalendar();

  // Set today as default check-in
  document.getElementById('f-start').value = now.toISOString().split('T')[0];
  const tomorrow = new Date(now); tomorrow.setDate(now.getDate() + 1);
  document.getElementById('f-end').value = tomorrow.toISOString().split('T')[0];

  // Poll for updates from other family members every 15 seconds
  setInterval(pollForUpdates, 15000);
})();
</script>
</body>
</html>
