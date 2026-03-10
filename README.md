<!DOCTYPE html>

<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>정책 일정 달력</title>
<link href="https://fonts.googleapis.com/css2?family=Noto+Serif+KR:wght@400;600;700&family=Noto+Sans+KR:wght@300;400;500;700&display=swap" rel="stylesheet">
<style>
  :root {
    --navy: #0d1b2a;
    --navy2: #1b2d42;
    --gold: #c9a84c;
    --gold-light: #e8c97a;
    --cream: #f5f0e8;
    --cream2: #ede6d6;
    --red: #c0392b;
    --green: #1e7e5a;
    --blue: #1a5276;
    --text: #1a1a2e;
    --muted: #7f8c8d;
  }

- { margin: 0; padding: 0; box-sizing: border-box; }

body {
background: var(–cream);
font-family: ‘Noto Sans KR’, sans-serif;
color: var(–text);
min-height: 100vh;
}

/* Header */
header {
background: var(–navy);
color: white;
padding: 0;
position: relative;
overflow: hidden;
}

header::before {
content: ‘’;
position: absolute;
top: 0; left: 0; right: 0; bottom: 0;
background: repeating-linear-gradient(
90deg,
transparent,
transparent 60px,
rgba(201,168,76,0.05) 60px,
rgba(201,168,76,0.05) 61px
);
}

.header-inner {
max-width: 1100px;
margin: 0 auto;
padding: 32px 24px 28px;
position: relative;
}

.header-badge {
display: inline-block;
background: var(–gold);
color: var(–navy);
font-size: 11px;
font-weight: 700;
letter-spacing: 2px;
padding: 4px 12px;
margin-bottom: 14px;
text-transform: uppercase;
}

header h1 {
font-family: ‘Noto Serif KR’, serif;
font-size: clamp(24px, 5vw, 38px);
font-weight: 700;
letter-spacing: -0.5px;
line-height: 1.2;
}

header h1 span {
color: var(–gold-light);
}

.header-sub {
margin-top: 8px;
font-size: 13px;
color: rgba(255,255,255,0.5);
letter-spacing: 0.5px;
}

/* Nav */
.nav-bar {
background: var(–navy2);
border-bottom: 2px solid var(–gold);
}

.nav-inner {
max-width: 1100px;
margin: 0 auto;
padding: 0 24px;
display: flex;
align-items: center;
gap: 4px;
overflow-x: auto;
}

.nav-btn {
background: none;
border: none;
color: rgba(255,255,255,0.6);
font-family: ‘Noto Sans KR’, sans-serif;
font-size: 13px;
font-weight: 500;
padding: 14px 16px;
cursor: pointer;
white-space: nowrap;
transition: color 0.2s;
border-bottom: 2px solid transparent;
margin-bottom: -2px;
}

.nav-btn:hover { color: white; }
.nav-btn.active { color: var(–gold-light); border-bottom-color: var(–gold); }

/* Main layout */
.main {
max-width: 1100px;
margin: 0 auto;
padding: 32px 24px;
display: grid;
grid-template-columns: 1fr 320px;
gap: 28px;
}

@media (max-width: 768px) {
.main { grid-template-columns: 1fr; }
}

/* Calendar */
.calendar-card {
background: white;
border: 1px solid var(–cream2);
box-shadow: 0 2px 16px rgba(0,0,0,0.06);
}

.cal-header {
display: flex;
align-items: center;
justify-content: space-between;
padding: 20px 24px;
border-bottom: 1px solid var(–cream2);
}

.cal-title {
font-family: ‘Noto Serif KR’, serif;
font-size: 20px;
font-weight: 700;
color: var(–navy);
}

.cal-nav {
display: flex;
gap: 8px;
}

.cal-nav button {
background: var(–cream);
border: 1px solid var(–cream2);
width: 32px;
height: 32px;
cursor: pointer;
font-size: 14px;
color: var(–navy);
transition: background 0.15s;
}

.cal-nav button:hover { background: var(–gold); color: white; border-color: var(–gold); }

.cal-grid {
padding: 16px 24px 24px;
}

.day-labels {
display: grid;
grid-template-columns: repeat(7, 1fr);
margin-bottom: 8px;
}

.day-label {
text-align: center;
font-size: 11px;
font-weight: 700;
letter-spacing: 1px;
color: var(–muted);
padding: 4px 0;
text-transform: uppercase;
}

.day-label:first-child { color: var(–red); }
.day-label:last-child { color: var(–blue); }

.days-grid {
display: grid;
grid-template-columns: repeat(7, 1fr);
gap: 3px;
}

.day-cell {
aspect-ratio: 1;
display: flex;
flex-direction: column;
align-items: center;
justify-content: flex-start;
padding: 6px 2px 2px;
cursor: pointer;
transition: background 0.15s;
position: relative;
min-height: 48px;
}

.day-cell:hover { background: var(–cream); }

.day-cell.other-month .day-num { color: #ccc; }

.day-cell.today .day-num {
background: var(–navy);
color: white;
width: 26px;
height: 26px;
display: flex;
align-items: center;
justify-content: center;
border-radius: 50%;
}

.day-cell.selected { background: rgba(201,168,76,0.12); }
.day-cell.selected .day-num { color: var(–gold); font-weight: 700; }

.day-num {
font-size: 13px;
font-weight: 500;
line-height: 1;
width: 26px;
height: 26px;
display: flex;
align-items: center;
justify-content: center;
}

.day-cell.sunday .day-num { color: var(–red); }
.day-cell.saturday .day-num { color: var(–blue); }

.event-dots {
display: flex;
gap: 2px;
margin-top: 3px;
flex-wrap: wrap;
justify-content: center;
}

.event-dot {
width: 5px;
height: 5px;
border-radius: 50%;
}

/* Sidebar */
.sidebar {}

.sidebar-card {
background: white;
border: 1px solid var(–cream2);
box-shadow: 0 2px 16px rgba(0,0,0,0.06);
margin-bottom: 20px;
}

.sidebar-title {
padding: 16px 20px;
font-family: ‘Noto Serif KR’, serif;
font-size: 15px;
font-weight: 700;
color: var(–navy);
border-bottom: 1px solid var(–cream2);
display: flex;
align-items: center;
gap: 8px;
}

.sidebar-title::before {
content: ‘’;
width: 3px;
height: 16px;
background: var(–gold);
display: block;
}

/* Events list */
.events-list { padding: 8px 0; }

.event-item {
padding: 12px 20px;
border-bottom: 1px solid var(–cream2);
cursor: pointer;
transition: background 0.15s;
}

.event-item:last-child { border-bottom: none; }
.event-item:hover { background: var(–cream); }

.event-tag {
display: inline-block;
font-size: 10px;
font-weight: 700;
letter-spacing: 0.5px;
padding: 2px 7px;
margin-bottom: 5px;
border-radius: 2px;
}

.tag-legislation { background: rgba(192,57,43,0.1); color: var(–red); }
.tag-policy { background: rgba(30,126,90,0.1); color: var(–green); }
.tag-hearing { background: rgba(26,82,118,0.1); color: var(–blue); }
.tag-deadline { background: rgba(201,168,76,0.15); color: #8B6914; }

.event-name {
font-size: 13px;
font-weight: 500;
color: var(–text);
line-height: 1.4;
margin-bottom: 4px;
}

.event-meta {
font-size: 11px;
color: var(–muted);
}

/* Add event form */
.add-form {
padding: 16px 20px;
display: flex;
flex-direction: column;
gap: 10px;
}

.form-input {
width: 100%;
padding: 9px 12px;
border: 1px solid var(–cream2);
background: var(–cream);
font-family: ‘Noto Sans KR’, sans-serif;
font-size: 13px;
color: var(–text);
outline: none;
transition: border-color 0.2s;
}

.form-input:focus { border-color: var(–gold); background: white; }

.form-select {
width: 100%;
padding: 9px 12px;
border: 1px solid var(–cream2);
background: var(–cream);
font-family: ‘Noto Sans KR’, sans-serif;
font-size: 13px;
color: var(–text);
outline: none;
appearance: none;
cursor: pointer;
}

.btn-add {
background: var(–navy);
color: white;
border: none;
padding: 10px;
font-family: ‘Noto Sans KR’, sans-serif;
font-size: 13px;
font-weight: 700;
letter-spacing: 1px;
cursor: pointer;
transition: background 0.2s;
}

.btn-add:hover { background: var(–gold); color: var(–navy); }

/* Legend */
.legend {
padding: 14px 20px;
display: flex;
flex-wrap: wrap;
gap: 10px;
}

.legend-item {
display: flex;
align-items: center;
gap: 5px;
font-size: 11px;
color: var(–muted);
}

.legend-dot {
width: 8px;
height: 8px;
border-radius: 50%;
flex-shrink: 0;
}

/* Stats bar */
.stats-bar {
background: var(–navy);
color: white;
margin-bottom: 28px;
}

.stats-inner {
max-width: 1100px;
margin: 0 auto;
padding: 0 24px;
display: flex;
overflow-x: auto;
}

.stat-item {
padding: 16px 24px;
border-right: 1px solid rgba(255,255,255,0.08);
min-width: 120px;
}

.stat-num {
font-family: ‘Noto Serif KR’, serif;
font-size: 24px;
font-weight: 700;
color: var(–gold-light);
line-height: 1;
}

.stat-label {
font-size: 11px;
color: rgba(255,255,255,0.5);
margin-top: 4px;
letter-spacing: 0.5px;
}

/* Modal */
.modal-overlay {
display: none;
position: fixed;
inset: 0;
background: rgba(13,27,42,0.7);
z-index: 100;
align-items: center;
justify-content: center;
}

.modal-overlay.open { display: flex; }

.modal {
background: white;
width: 90%;
max-width: 440px;
max-height: 80vh;
overflow-y: auto;
animation: slideUp 0.2s ease;
}

@keyframes slideUp {
from { transform: translateY(20px); opacity: 0; }
to { transform: translateY(0); opacity: 1; }
}

.modal-header {
background: var(–navy);
color: white;
padding: 20px 24px;
display: flex;
align-items: center;
justify-content: space-between;
}

.modal-title {
font-family: ‘Noto Serif KR’, serif;
font-size: 16px;
font-weight: 700;
}

.modal-close {
background: none;
border: none;
color: white;
font-size: 20px;
cursor: pointer;
opacity: 0.6;
line-height: 1;
}

.modal-close:hover { opacity: 1; }

.modal-body { padding: 20px 24px; }

.modal-event {
padding: 14px 0;
border-bottom: 1px solid var(–cream2);
}

.modal-event:last-child { border-bottom: none; }

.modal-event-name {
font-size: 14px;
font-weight: 500;
margin: 6px 0 3px;
}

.modal-event-meta {
font-size: 12px;
color: var(–muted);
}

.empty-state {
padding: 24px;
text-align: center;
color: var(–muted);
font-size: 13px;
}
</style>

</head>
<body>

<header>
  <div class="header-inner">
    <div class="header-badge">정책 일정 관리 시스템</div>
    <h1>정책·법안 <span>일정 달력</span></h1>
    <p class="header-sub">Policy & Legislation Schedule Calendar</p>
  </div>
</header>

<nav class="nav-bar">
  <div class="nav-inner">
    <button class="nav-btn active" onclick="filterEvents('all')">전체</button>
    <button class="nav-btn" onclick="filterEvents('legislation')">법안심의</button>
    <button class="nav-btn" onclick="filterEvents('policy')">정책발표</button>
    <button class="nav-btn" onclick="filterEvents('hearing')">청문회</button>
    <button class="nav-btn" onclick="filterEvents('deadline')">마감기한</button>
  </div>
</nav>

<div class="stats-bar">
  <div class="stats-inner">
    <div class="stat-item">
      <div class="stat-num" id="stat-total">0</div>
      <div class="stat-label">이번 달 일정</div>
    </div>
    <div class="stat-item">
      <div class="stat-num" id="stat-upcoming">0</div>
      <div class="stat-label">7일 내 예정</div>
    </div>
    <div class="stat-item">
      <div class="stat-num" id="stat-legislation">0</div>
      <div class="stat-label">법안심의</div>
    </div>
    <div class="stat-item">
      <div class="stat-num" id="stat-policy">0</div>
      <div class="stat-label">정책발표</div>
    </div>
  </div>
</div>

<div class="main">
  <!-- Calendar -->
  <div>
    <div class="calendar-card">
      <div class="cal-header">
        <div class="cal-title" id="cal-title"></div>
        <div class="cal-nav">
          <button onclick="changeMonth(-1)">◀</button>
          <button onclick="goToday()">오늘</button>
          <button onclick="changeMonth(1)">▶</button>
        </div>
      </div>
      <div class="cal-grid">
        <div class="day-labels">
          <div class="day-label">일</div>
          <div class="day-label">월</div>
          <div class="day-label">화</div>
          <div class="day-label">수</div>
          <div class="day-label">목</div>
          <div class="day-label">금</div>
          <div class="day-label">토</div>
        </div>
        <div class="days-grid" id="days-grid"></div>
      </div>
    </div>

```
<!-- Legend -->
<div class="sidebar-card" style="margin-top: 20px;">
  <div class="legend">
    <div class="legend-item"><div class="legend-dot" style="background:#c0392b"></div>법안심의</div>
    <div class="legend-item"><div class="legend-dot" style="background:#1e7e5a"></div>정책발표</div>
    <div class="legend-item"><div class="legend-dot" style="background:#1a5276"></div>청문회</div>
    <div class="legend-item"><div class="legend-dot" style="background:#c9a84c"></div>마감기한</div>
  </div>
</div>
```

  </div>

  <!-- Sidebar -->

  <div class="sidebar">
    <!-- Upcoming events -->
    <div class="sidebar-card">
      <div class="sidebar-title">예정 일정</div>
      <div class="events-list" id="events-list">
        <div class="empty-state">일정을 추가해주세요</div>
      </div>
    </div>

```
<!-- Add event -->
<div class="sidebar-card">
  <div class="sidebar-title">일정 추가</div>
  <div class="add-form">
    <input class="form-input" type="text" id="new-title" placeholder="일정 제목">
    <input class="form-input" type="date" id="new-date">
    <input class="form-input" type="text" id="new-desc" placeholder="내용 (선택)">
    <select class="form-select" id="new-type">
      <option value="legislation">법안심의</option>
      <option value="policy">정책발표</option>
      <option value="hearing">청문회</option>
      <option value="deadline">마감기한</option>
    </select>
    <button class="btn-add" onclick="addEvent()">＋ 일정 추가</button>
  </div>
</div>
```

  </div>
</div>

<!-- Day modal -->

<div class="modal-overlay" id="modal" onclick="closeModal(event)">
  <div class="modal">
    <div class="modal-header">
      <div class="modal-title" id="modal-title"></div>
      <button class="modal-close" onclick="document.getElementById('modal').classList.remove('open')">✕</button>
    </div>
    <div class="modal-body" id="modal-body"></div>
  </div>
</div>

<script>
const typeColors = {
  legislation: '#c0392b',
  policy: '#1e7e5a',
  hearing: '#1a5276',
  deadline: '#c9a84c'
};
const typeLabels = {
  legislation: '법안심의',
  policy: '정책발표',
  hearing: '청문회',
  deadline: '마감기한'
};
const tagClasses = {
  legislation: 'tag-legislation',
  policy: 'tag-policy',
  hearing: 'tag-hearing',
  deadline: 'tag-deadline'
};

const today = new Date();
let currentYear = today.getFullYear();
let currentMonth = today.getMonth();
let activeFilter = 'all';

// Sample events
let events = [
  { id: 1, title: '개인정보보호법 개정안 심의', date: formatDate(today, 3), type: 'legislation', desc: '국회 법제사법위원회' },
  { id: 2, title: '2025 국가예산안 정책발표', date: formatDate(today, 7), type: 'policy', desc: '기획재정부' },
  { id: 3, title: '탄소중립 기본계획 청문회', date: formatDate(today, 12), type: 'hearing', desc: '환경노동위원회' },
  { id: 4, title: '공공기관 혁신안 제출 마감', date: formatDate(today, 5), type: 'deadline', desc: '각 부처 제출 기한' },
  { id: 5, title: '디지털혁신 촉진법 2독회', date: formatDate(today, -2), type: 'legislation', desc: '본회의' },
  { id: 6, title: '저출생 대응 정책 발표', date: formatDate(today, 15), type: 'policy', desc: '인구정책실' },
];

let nextId = 7;

function formatDate(base, offset = 0) {
  const d = new Date(base);
  d.setDate(d.getDate() + offset);
  return d.toISOString().split('T')[0];
}

function changeMonth(dir) {
  currentMonth += dir;
  if (currentMonth > 11) { currentMonth = 0; currentYear++; }
  if (currentMonth < 0) { currentMonth = 11; currentYear--; }
  render();
}

function goToday() {
  currentYear = today.getFullYear();
  currentMonth = today.getMonth();
  render();
}

function filterEvents(f) {
  activeFilter = f;
  document.querySelectorAll('.nav-btn').forEach((b, i) => {
    b.classList.toggle('active', ['all','legislation','policy','hearing','deadline'][i] === f);
  });
  render();
}

function getFilteredEvents() {
  return activeFilter === 'all' ? events : events.filter(e => e.type === activeFilter);
}

function getEventsForDate(dateStr) {
  return getFilteredEvents().filter(e => e.date === dateStr);
}

function render() {
  renderCalendar();
  renderSidebar();
  updateStats();
}

function renderCalendar() {
  const months = ['1월','2월','3월','4월','5월','6월','7월','8월','9월','10월','11월','12월'];
  document.getElementById('cal-title').textContent = `${currentYear}년 ${months[currentMonth]}`;

  const grid = document.getElementById('days-grid');
  grid.innerHTML = '';

  const firstDay = new Date(currentYear, currentMonth, 1).getDay();
  const daysInMonth = new Date(currentYear, currentMonth + 1, 0).getDate();
  const daysInPrev = new Date(currentYear, currentMonth, 0).getDate();
  const todayStr = today.toISOString().split('T')[0];

  // Prev month padding
  for (let i = firstDay - 1; i >= 0; i--) {
    const d = daysInPrev - i;
    const dateStr = `${currentYear}-${String(currentMonth === 0 ? 12 : currentMonth).padStart(2,'0')}-${String(d).padStart(2,'0')}`;
    addDayCell(grid, d, dateStr, true, (firstDay - 1 - i) % 7);
  }

  // Current month
  for (let d = 1; d <= daysInMonth; d++) {
    const dateStr = `${currentYear}-${String(currentMonth+1).padStart(2,'0')}-${String(d).padStart(2,'0')}`;
    const isToday = dateStr === todayStr;
    const dayOfWeek = (firstDay + d - 1) % 7;
    addDayCell(grid, d, dateStr, false, dayOfWeek, isToday);
  }

  // Next month padding
  const totalCells = Math.ceil((firstDay + daysInMonth) / 7) * 7;
  const remaining = totalCells - firstDay - daysInMonth;
  for (let d = 1; d <= remaining; d++) {
    const dateStr = `${currentYear}-${String(currentMonth+2 > 12 ? 1 : currentMonth+2).padStart(2,'0')}-${String(d).padStart(2,'0')}`;
    addDayCell(grid, d, dateStr, true, (firstDay + daysInMonth + d - 1) % 7);
  }
}

function addDayCell(grid, dayNum, dateStr, isOther, dow, isToday = false) {
  const cell = document.createElement('div');
  cell.className = 'day-cell' + (isOther ? ' other-month' : '') + (isToday ? ' today' : '') +
    (dow === 0 ? ' sunday' : '') + (dow === 6 ? ' saturday' : '');
  cell.onclick = () => openDayModal(dateStr);

  const num = document.createElement('div');
  num.className = 'day-num';
  num.textContent = dayNum;
  cell.appendChild(num);

  const evts = getEventsForDate(dateStr);
  if (evts.length > 0) {
    const dots = document.createElement('div');
    dots.className = 'event-dots';
    evts.slice(0, 3).forEach(e => {
      const dot = document.createElement('div');
      dot.className = 'event-dot';
      dot.style.background = typeColors[e.type];
      dots.appendChild(dot);
    });
    cell.appendChild(dots);
  }

  grid.appendChild(cell);
}

function renderSidebar() {
  const list = document.getElementById('events-list');
  const upcoming = getFilteredEvents()
    .filter(e => e.date >= today.toISOString().split('T')[0])
    .sort((a, b) => a.date.localeCompare(b.date))
    .slice(0, 8);

  if (upcoming.length === 0) {
    list.innerHTML = '<div class="empty-state">예정된 일정이 없습니다</div>';
    return;
  }

  list.innerHTML = upcoming.map(e => `
    <div class="event-item" onclick="openDayModal('${e.date}')">
      <span class="event-tag ${tagClasses[e.type]}">${typeLabels[e.type]}</span>
      <div class="event-name">${e.title}</div>
      <div class="event-meta">${formatKorDate(e.date)}${e.desc ? ' · ' + e.desc : ''}</div>
    </div>
  `).join('');
}

function formatKorDate(dateStr) {
  const d = new Date(dateStr + 'T00:00:00');
  const days = ['일','월','화','수','목','금','토'];
  return `${d.getMonth()+1}월 ${d.getDate()}일 (${days[d.getDay()]})`;
}

function updateStats() {
  const monthStr = `${currentYear}-${String(currentMonth+1).padStart(2,'0')}`;
  const monthEvents = events.filter(e => e.date.startsWith(monthStr));
  document.getElementById('stat-total').textContent = monthEvents.length;

  const sevenDays = new Date(today); sevenDays.setDate(today.getDate() + 7);
  const todayStr = today.toISOString().split('T')[0];
  const sevenStr = sevenDays.toISOString().split('T')[0];
  document.getElementById('stat-upcoming').textContent = events.filter(e => e.date >= todayStr && e.date <= sevenStr).length;
  document.getElementById('stat-legislation').textContent = events.filter(e => e.type === 'legislation').length;
  document.getElementById('stat-policy').textContent = events.filter(e => e.type === 'policy').length;
}

function addEvent() {
  const title = document.getElementById('new-title').value.trim();
  const date = document.getElementById('new-date').value;
  const desc = document.getElementById('new-desc').value.trim();
  const type = document.getElementById('new-type').value;

  if (!title || !date) { alert('제목과 날짜를 입력해주세요.'); return; }

  events.push({ id: nextId++, title, date, type, desc });
  document.getElementById('new-title').value = '';
  document.getElementById('new-date').value = '';
  document.getElementById('new-desc').value = '';
  render();
}

function openDayModal(dateStr) {
  const evts = events.filter(e => e.date === dateStr);
  document.getElementById('modal-title').textContent = formatKorDate(dateStr) + ' 일정';

  const body = document.getElementById('modal-body');
  if (evts.length === 0) {
    body.innerHTML = '<div class="empty-state" style="padding: 32px;">이 날의 일정이 없습니다</div>';
  } else {
    body.innerHTML = evts.map(e => `
      <div class="modal-event">
        <span class="event-tag ${tagClasses[e.type]}">${typeLabels[e.type]}</span>
        <div class="modal-event-name">${e.title}</div>
        ${e.desc ? `<div class="modal-event-meta">${e.desc}</div>` : ''}
        <button onclick="deleteEvent(${e.id})" style="margin-top:8px;background:none;border:1px solid #ddd;padding:4px 10px;font-size:11px;cursor:pointer;color:#999;">삭제</button>
      </div>
    `).join('');
  }

  document.getElementById('modal').classList.add('open');
}

function deleteEvent(id) {
  events = events.filter(e => e.id !== id);
  document.getElementById('modal').classList.remove('open');
  render();
}

function closeModal(e) {
  if (e.target === document.getElementById('modal')) {
    document.getElementById('modal').classList.remove('open');
  }
}

// Set today's date as default
document.getElementById('new-date').value = today.toISOString().split('T')[0];

render();
</script>

</body>
</html>
