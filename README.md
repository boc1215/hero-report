[index.html.html](https://github.com/user-attachments/files/26770135/index.html.html)
# hero-report<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ヒーロー科レポート（店舗）</title>
<style>
* { box-sizing: border-box; margin: 0; padding: 0; }
body { font-family: -apple-system, BlinkMacSystemFont, 'Hiragino Sans', sans-serif; background: #f5f5f0; color: #1a1a1a; min-height: 100vh; }
.app { max-width: 480px; margin: 0 auto; padding: 1rem; }
.header { text-align: center; padding: 1.5rem 0 0.5rem; margin-bottom: 1rem; }
.header h1 { font-size: 18px; font-weight: 500; color: #1a1a1a; }
.tab-bar { display: flex; background: #fff; border-radius: 12px; padding: 4px; gap: 4px; margin-bottom: 1.5rem; box-shadow: 0 1px 3px rgba(0,0,0,0.08); }
.tab { flex: 1; padding: 10px 0; font-size: 11px; font-weight: 500; text-align: center; background: none; border: none; color: #888; cursor: pointer; border-radius: 8px; transition: all 0.2s; font-family: inherit; line-height: 1.3; }
.tab.active { background: #1a1a1a; color: #fff; }
.section { margin-bottom: 1.25rem; }
.label { font-size: 13px; color: #666; margin-bottom: 6px; display: block; }
.required { color: #c0392b; margin-left: 2px; }
input[type="date"], input[type="text"], input[type="password"], select, textarea {
  width: 100%; padding: 12px 14px; font-size: 15px;
  border: 1px solid #e0e0e0; border-radius: 10px;
  background: #fff; color: #1a1a1a;
  font-family: inherit; outline: none; transition: border-color 0.2s;
  -webkit-appearance: none; appearance: none;
}
input:focus, select:focus, textarea:focus { border-color: #888; }
textarea { resize: vertical; min-height: 100px; line-height: 1.7; }
.btn-primary { width: 100%; padding: 15px; background: #1a1a1a; color: #fff; border: none; border-radius: 12px; font-size: 16px; font-weight: 500; cursor: pointer; font-family: inherit; transition: opacity 0.2s; }
.btn-primary:active { opacity: 0.8; }
.btn-secondary { padding: 9px 16px; background: #fff; border: 1px solid #ddd; border-radius: 8px; font-size: 13px; color: #1a1a1a; cursor: pointer; font-family: inherit; }
.btn-danger { padding: 7px 13px; background: none; border: 1px solid #f0c0c0; border-radius: 8px; font-size: 12px; color: #c0392b; cursor: pointer; font-family: inherit; }
.success-msg { background: #eafaf1; color: #1e8449; padding: 12px 16px; border-radius: 10px; font-size: 14px; margin-bottom: 1rem; display: none; }
.error-msg { background: #fdf2f2; color: #c0392b; padding: 12px 16px; border-radius: 10px; font-size: 14px; margin-bottom: 1rem; display: none; }
.report-card { background: #fff; border: 1px solid #ebebeb; border-radius: 14px; padding: 1rem 1.25rem; cursor: pointer; margin-bottom: 12px; transition: box-shadow 0.15s; }
.report-card:active { box-shadow: 0 2px 8px rgba(0,0,0,0.08); }
.report-header { display: flex; justify-content: space-between; align-items: flex-start; margin-bottom: 5px; }
.report-store { font-size: 15px; font-weight: 500; }
.report-date { font-size: 12px; color: #999; }
.report-author { font-size: 12px; color: #999; margin-bottom: 7px; }
.report-preview { font-size: 13px; color: #666; line-height: 1.5; display: -webkit-box; -webkit-line-clamp: 2; -webkit-box-orient: vertical; overflow: hidden; }
.badge { display: inline-block; font-size: 11px; padding: 3px 9px; border-radius: 99px; background: #fff3f3; color: #c0392b; margin-top: 8px; border: 1px solid #f0c0c0; }
.badge-green { background: #eafaf1; color: #1e8449; border: 1px solid #a9dfbf; }
.empty-state { text-align: center; padding: 3rem 1rem; color: #aaa; font-size: 14px; line-height: 1.8; }
.modal-bg { position: fixed; inset: 0; background: rgba(0,0,0,0.4); display: flex; align-items: flex-end; justify-content: center; z-index: 100; }
.modal { background: #fff; border-radius: 20px 20px 0 0; width: 100%; max-width: 480px; padding: 1.5rem; max-height: 85vh; overflow-y: auto; }
.modal-handle { width: 36px; height: 4px; background: #ddd; border-radius: 2px; margin: 0 auto 1.25rem; }
.modal-title { font-size: 16px; font-weight: 500; margin-bottom: 1.25rem; }
.modal-close-btn { float: right; background: none; border: none; font-size: 22px; color: #aaa; cursor: pointer; margin-top: -4px; }
.detail-row { margin-bottom: 1.1rem; }
.detail-label { font-size: 12px; color: #999; margin-bottom: 4px; }
.detail-value { font-size: 14px; color: #1a1a1a; line-height: 1.7; white-space: pre-wrap; }
.store-item { display: flex; align-items: center; justify-content: space-between; padding: 12px 0; border-bottom: 1px solid #f0f0f0; font-size: 14px; }
.store-add-row { display: flex; gap: 8px; margin-top: 1.25rem; }
.store-add-row input { flex: 1; }
.admin-login-box { background: #fff; border-radius: 14px; padding: 1.5rem; margin-top: 1rem; }
.admin-login-box p { font-size: 14px; color: #666; margin-bottom: 1.25rem; text-align: center; }
.section-title { font-size: 12px; color: #999; margin-bottom: 0.75rem; letter-spacing: 0.5px; }
.divider { border: none; border-top: 1px solid #f0f0f0; margin: 1.25rem 0; }
.list-switcher { display: flex; gap: 8px; margin-bottom: 1rem; }
.list-switcher button { flex: 1; }
</style>
</head>
<body>
<div class="app">
  <div class="header"><h1>ヒーロー科レポート（店舗）</h1></div>

  <div class="tab-bar">
    <button class="tab active" onclick="switchTab('input')">店舗<br>レポート</button>
    <button class="tab" onclick="switchTab('training')">育成<br>レポート</button>
    <button class="tab" onclick="switchTab('list')">一覧</button>
    <button class="tab" onclick="switchTab('admin')">管理者</button>
  </div>

  <!-- 店舗レポート入力タブ -->
  <div id="tab-input">
    <div class="success-msg" id="success-msg">保存しました。</div>
    <div class="section">
      <label class="label">日付<span class="required">*</span></label>
      <input type="date" id="input-date" />
    </div>
    <div class="section">
      <label class="label">記入者名<span class="required">*</span></label>
      <input type="text" id="input-author" placeholder="例：佐藤" />
    </div>
    <div class="section">
      <label class="label">訪問店舗<span class="required">*</span></label>
      <select id="input-store"><option value="">選択してください</option></select>
    </div>
    <div class="section">
      <label class="label">出勤スタッフ名</label>
      <input type="text" id="input-members" placeholder="例：田中、鈴木、山田" />
    </div>
    <div class="section">
      <label class="label">スタッフの様子・コメント</label>
      <textarea id="input-staff" placeholder="スタッフの状態、モチベーション、気になること等"></textarea>
    </div>
    <div class="section">
      <label class="label">店舗の様子、課題</label>
      <textarea id="input-issue" placeholder="接客面、設備面、オペレーション上の課題等"></textarea>
    </div>
    <button class="btn-primary" onclick="submitReport()">保存する</button>
  </div>

  <!-- 育成レポート入力タブ -->
  <div id="tab-training" style="display:none;">
    <div class="success-msg" id="training-success-msg">保存しました。</div>
    <div class="section">
      <label class="label">日付<span class="required">*</span></label>
      <input type="date" id="tr-date" />
    </div>
    <div class="section">
      <label class="label">記入者名<span class="required">*</span></label>
      <input type="text" id="tr-author" placeholder="例：佐藤" />
    </div>
    <div class="section">
      <label class="label">新人名<span class="required">*</span></label>
      <select id="tr-trainee"><option value="">選択してください</option></select>
    </div>
    <div class="section">
      <label class="label">内容<span class="required">*</span></label>
      <textarea id="tr-content" placeholder="育成の内容、気づき、課題等" style="min-height:140px;"></textarea>
    </div>
    <button class="btn-primary" onclick="submitTraining()">保存する</button>
  </div>

  <!-- 一覧タブ -->
  <div id="tab-list" style="display:none;">
    <div class="list-switcher">
      <button id="list-btn-store" class="btn-secondary" style="background:#1a1a1a;color:#fff;border-color:#1a1a1a;" onclick="switchListView('store')">店舗レポート</button>
      <button id="list-btn-training" class="btn-secondary" onclick="switchListView('training')">育成レポート</button>
    </div>
    <div id="reports-list"><div class="empty-state">まだ記録がありません。</div></div>
  </div>

  <!-- 管理者タブ -->
  <div id="tab-admin" style="display:none;">
    <div id="admin-lock">
      <div class="admin-login-box">
        <p>管理者パスワードを入力してください</p>
        <div class="section">
          <input type="password" id="admin-pw-input" placeholder="パスワード" />
        </div>
        <div class="error-msg" id="pw-error">パスワードが違います。</div>
        <button class="btn-primary" onclick="checkPassword()" style="margin-top:0.75rem;">ログイン</button>
      </div>
    </div>
    <div id="admin-panel" style="display:none;">
      <div class="section-title">店舗リスト管理</div>
      <div id="store-list-manage"></div>
      <div class="store-add-row">
        <input type="text" id="new-store-input" placeholder="新しい店舗名を入力" />
        <button class="btn-secondary" onclick="addStore()">追加</button>
      </div>
      <hr class="divider">
      <div class="section-title">新人リスト管理</div>
      <div id="trainee-list-manage"></div>
      <div class="store-add-row">
        <input type="text" id="new-trainee-input" placeholder="新人名を入力" />
        <button class="btn-secondary" onclick="addTrainee()">追加</button>
      </div>
      <hr class="divider">
      <button class="btn-secondary" onclick="lockAdmin()">ログアウト</button>
    </div>
  </div>
</div>

<!-- 詳細モーダル -->
<div class="modal-bg" id="modal-bg" style="display:none;" onclick="closeModal(event)">
  <div class="modal">
    <div class="modal-handle"></div>
    <button class="modal-close-btn" onclick="closeModalDirect()">×</button>
    <div class="modal-title" id="modal-title"></div>
    <div id="modal-body"></div>
  </div>
</div>

<script>
const GAS_URL = 'https://script.google.com/macros/s/AKfycbywVX0SG6I4deGItEUrIpcoiu1UZDSd0SV6PRXMZP1h5cVv53c9AjtogvAsh8N32MCaSg/exec';
const ADMIN_PASSWORD = '0723';
const DEFAULT_STORES = [
  'flower 平井店','Riz hair 稲毛店','coast-R 稲毛店',
  'globe 船橋店','Roi 西千葉店','STROKE 八街店',
  'STROKE 宇都宮店','B-8 宇都宮店'
];
const LS_REPORTS   = 'patrol_reports';
const LS_STORES    = 'patrol_stores';
const LS_TRAININGS = 'patrol_trainings';
const LS_TRAINEES  = 'patrol_trainees';

function loadReports()    { try { return JSON.parse(localStorage.getItem(LS_REPORTS))   || []; } catch(e) { return []; } }
function saveReports(d)   { localStorage.setItem(LS_REPORTS,   JSON.stringify(d)); }
function loadTrainings()  { try { return JSON.parse(localStorage.getItem(LS_TRAININGS)) || []; } catch(e) { return []; } }
function saveTrainings(d) { localStorage.setItem(LS_TRAININGS, JSON.stringify(d)); }
function loadStores() {
  try { const s = JSON.parse(localStorage.getItem(LS_STORES)); return Array.isArray(s) && s.length ? s : [...DEFAULT_STORES]; } catch(e) { return [...DEFAULT_STORES]; }
}
function saveStores(d)    { localStorage.setItem(LS_STORES,    JSON.stringify(d)); }
function loadTrainees() {
  try { const s = JSON.parse(localStorage.getItem(LS_TRAINEES)); return Array.isArray(s) ? s : []; } catch(e) { return []; }
}
function saveTrainees(d)  { localStorage.setItem(LS_TRAINEES,  JSON.stringify(d)); }

let reports   = loadReports();
let trainings = loadTrainings();
let stores    = loadStores();
let trainees  = loadTrainees();
let currentListView = 'store';

function today() { return new Date().toISOString().split('T')[0]; }
document.getElementById('input-date').value = today();
document.getElementById('tr-date').value    = today();
renderStoreSelect();
renderTraineeSelect();

function renderStoreSelect() {
  const sel = document.getElementById('input-store');
  const cur = sel.value;
  sel.innerHTML = '<option value="">選択してください</option>';
  stores.forEach(s => {
    const o = document.createElement('option');
    o.value = s; o.textContent = s;
    if (s === cur) o.selected = true;
    sel.appendChild(o);
  });
}

function renderTraineeSelect() {
  const sel = document.getElementById('tr-trainee');
  const cur = sel.value;
  sel.innerHTML = '<option value="">選択してください</option>';
  trainees.forEach(t => {
    const o = document.createElement('option');
    o.value = t; o.textContent = t;
    if (t === cur) o.selected = true;
    sel.appendChild(o);
  });
}

function switchTab(tab) {
  ['input','training','list','admin'].forEach(t => {
    document.getElementById('tab-' + t).style.display = t === tab ? 'block' : 'none';
  });
  document.querySelectorAll('.tab').forEach((el, i) => {
    el.classList.toggle('active', ['input','training','list','admin'][i] === tab);
  });
  if (tab === 'list') renderList();
}

function switchListView(view) {
  currentListView = view;
  const sBtn = document.getElementById('list-btn-store');
  const tBtn = document.getElementById('list-btn-training');
  sBtn.style.background   = view === 'store'    ? '#1a1a1a' : '#fff';
  sBtn.style.color        = view === 'store'    ? '#fff'    : '#1a1a1a';
  sBtn.style.borderColor  = view === 'store'    ? '#1a1a1a' : '#ddd';
  tBtn.style.background   = view === 'training' ? '#1a1a1a' : '#fff';
  tBtn.style.color        = view === 'training' ? '#fff'    : '#1a1a1a';
  tBtn.style.borderColor  = view === 'training' ? '#1a1a1a' : '#ddd';
  renderList();
}

function submitReport() {
  const date    = document.getElementById('input-date').value;
  const author  = document.getElementById('input-author').value.trim();
  const store   = document.getElementById('input-store').value;
  const members = document.getElementById('input-members').value.trim();
  const staff   = document.getElementById('input-staff').value.trim();
  const issue   = document.getElementById('input-issue').value.trim();
  if (!date || !author || !store) { alert('日付・記入者名・訪問店舗は必須です。'); return; }
  const report = { type: 'store', date, author, store, members, staff, issue, id: Date.now() };
  reports.unshift(report);
  saveReports(reports);
  sendToSheet(report);
  const msg = document.getElementById('success-msg');
  msg.style.display = 'block';
  setTimeout(() => msg.style.display = 'none', 3000);
  document.getElementById('input-members').value = '';
  document.getElementById('input-staff').value   = '';
  document.getElementById('input-issue').value   = '';
  document.getElementById('input-store').value   = '';
  document.getElementById('input-date').value    = today();
}

function submitTraining() {
  const date    = document.getElementById('tr-date').value;
  const author  = document.getElementById('tr-author').value.trim();
  const trainee = document.getElementById('tr-trainee').value;
  const content = document.getElementById('tr-content').value.trim();
  if (!date || !author || !trainee || !content) { alert('すべての必須項目を入力してください。'); return; }
  const record = { type: 'training', date, author, trainee, content, id: Date.now() };
  trainings.unshift(record);
  saveTrainings(trainings);
  sendToSheet(record);
  const msg = document.getElementById('training-success-msg');
  msg.style.display = 'block';
  setTimeout(() => msg.style.display = 'none', 3000);
  document.getElementById('tr-content').value  = '';
  document.getElementById('tr-trainee').value  = '';
  document.getElementById('tr-date').value     = today();
}

function sendToSheet(data) {
  fetch(GAS_URL, {
    method: 'POST',
    mode: 'no-cors',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify(data)
  }).catch(err => console.error('送信エラー:', err));
}

function renderList() {
  const el = document.getElementById('reports-list');
  if (currentListView === 'store') {
    if (!reports.length) { el.innerHTML = '<div class="empty-state">まだ店舗レポートがありません。</div>'; return; }
    el.innerHTML = reports.map(r => `
      <div class="report-card" onclick="showStoreDetail(${r.id})">
        <div class="report-header">
          <span class="report-store">${r.store}</span>
          <span class="report-date">${r.date}</span>
        </div>
        <div class="report-author">${r.author}</div>
        <div class="report-preview">${r.staff || r.issue || '（本文なし）'}</div>
        ${r.issue ? '<span class="badge">課題あり</span>' : ''}
      </div>
    `).join('');
  } else {
    if (!trainings.length) { el.innerHTML = '<div class="empty-state">まだ育成レポートがありません。</div>'; return; }
    el.innerHTML = trainings.map(r => `
      <div class="report-card" onclick="showTrainingDetail(${r.id})">
        <div class="report-header">
          <span class="report-store">${r.trainee}</span>
          <span class="report-date">${r.date}</span>
        </div>
        <div class="report-author">${r.author}</div>
        <div class="report-preview">${r.content || '（本文なし）'}</div>
        <span class="badge badge-green">育成</span>
      </div>
    `).join('');
  }
}

function showStoreDetail(id) {
  const r = reports.find(x => x.id === id);
  if (!r) return;
  document.getElementById('modal-title').textContent = r.store + '　' + r.date;
  document.getElementById('modal-body').innerHTML = `
    <div class="detail-row"><div class="detail-label">記入者</div><div class="detail-value">${r.author}</div></div>
    <div class="detail-row"><div class="detail-label">出勤スタッフ名</div><div class="detail-value">${r.members || '—'}</div></div>
    <div class="detail-row"><div class="detail-label">スタッフの様子</div><div class="detail-value">${r.staff || '—'}</div></div>
    <div class="detail-row"><div class="detail-label">店舗の様子、課題</div><div class="detail-value">${r.issue || '—'}</div></div>
  `;
  document.getElementById('modal-bg').style.display = 'flex';
}

function showTrainingDetail(id) {
  const r = trainings.find(x => x.id === id);
  if (!r) return;
  document.getElementById('modal-title').textContent = r.trainee + '　' + r.date;
  document.getElementById('modal-body').innerHTML = `
    <div class="detail-row"><div class="detail-label">記入者</div><div class="detail-value">${r.author}</div></div>
    <div class="detail-row"><div class="detail-label">新人名</div><div class="detail-value">${r.trainee}</div></div>
    <div class="detail-row"><div class="detail-label">内容</div><div class="detail-value">${r.content}</div></div>
  `;
  document.getElementById('modal-bg').style.display = 'flex';
}

function closeModal(e) { if (e.target === document.getElementById('modal-bg')) closeModalDirect(); }
function closeModalDirect() { document.getElementById('modal-bg').style.display = 'none'; }

function checkPassword() {
  const pw  = document.getElementById('admin-pw-input').value;
  const err = document.getElementById('pw-error');
  if (pw === ADMIN_PASSWORD) {
    document.getElementById('admin-lock').style.display  = 'none';
    document.getElementById('admin-panel').style.display = 'block';
    err.style.display = 'none';
    renderStoreManage();
    renderTraineeManage();
  } else {
    err.style.display = 'block';
  }
}

function lockAdmin() {
  document.getElementById('admin-lock').style.display  = 'block';
  document.getElementById('admin-panel').style.display = 'none';
  document.getElementById('admin-pw-input').value = '';
}

function renderStoreManage() {
  const el = document.getElementById('store-list-manage');
  if (!el) return;
  el.innerHTML = stores.length ? stores.map((s, i) => `
    <div class="store-item"><span>${s}</span><button class="btn-danger" onclick="removeStore(${i})">削除</button></div>
  `).join('') : '<div style="font-size:13px;color:#aaa;padding:8px 0;">店舗がありません。</div>';
}

function renderTraineeManage() {
  const el = document.getElementById('trainee-list-manage');
  if (!el) return;
  el.innerHTML = trainees.length ? trainees.map((t, i) => `
    <div class="store-item"><span>${t}</span><button class="btn-danger" onclick="removeTrainee(${i})">削除</button></div>
  `).join('') : '<div style="font-size:13px;color:#aaa;padding:8px 0;">まだ新人が登録されていません。</div>';
}

function addStore() {
  const input = document.getElementById('new-store-input');
  const name  = input.value.trim();
  if (!name) return;
  if (stores.includes(name)) { alert('同じ名前の店舗がすでにあります。'); return; }
  stores.push(name); saveStores(stores); input.value = '';
  renderStoreSelect(); renderStoreManage();
}

function removeStore(i) {
  if (!confirm('「' + stores[i] + '」を削除しますか？')) return;
  stores.splice(i, 1); saveStores(stores);
  renderStoreSelect(); renderStoreManage();
}

function addTrainee() {
  const input = document.getElementById('new-trainee-input');
  const name  = input.value.trim();
  if (!name) return;
  if (trainees.includes(name)) { alert('同じ名前がすでにあります。'); return; }
  trainees.push(name); saveTrainees(trainees); input.value = '';
  renderTraineeSelect(); renderTraineeManage();
}

function removeTrainee(i) {
  if (!confirm('「' + trainees[i] + '」を削除しますか？')) return;
  trainees.splice(i, 1); saveTrainees(trainees);
  renderTraineeSelect(); renderTraineeManage();
}
</script>
</body>
</html>
