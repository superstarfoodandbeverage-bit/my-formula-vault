<!DOCTYPE html>
<html lang="bn">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>মাই ফর্মুলা ভল্ট (My Formula Vault)</title>
  <style>
    :root { --bg: #f4f6f9; --card: #ffffff; --text: #1e293b; --muted: #64748b; --primary: #2563eb; --success: #16a34a; --danger: #dc2626; --border: #e2e8f0; --accent-bg: #eff6ff; }
    body.dark { --bg: #0f172a; --card: #1e293b; --text: #f1f5f9; --muted: #94a3b8; --primary: #3b82f6; --success: #22c55e; --danger: #ef4444; --border: #334155; --accent-bg: #1e3a8a33; }
    * { box-sizing: border-box; font-family: 'Segoe UI', system-ui, sans-serif; }
    body { margin: 0; background: var(--bg); color: var(--text); padding-bottom: 84px; }
    header { background: var(--primary); color: #fff; padding: 12px 16px; display: flex; justify-content: space-between; align-items: center; position: sticky; top: 0; z-index: 100; box-shadow: 0 2px 8px rgba(0,0,0,0.12); }
    .brand { display: flex; align-items: center; gap: 10px; }
    .brand-logo { width: 38px; height: 38px; border-radius: 10px; background: #fff; display: flex; align-items: center; justify-content: center; box-shadow: 0 2px 6px rgba(0,0,0,0.15); flex-shrink: 0; }
    .brand-text h1 { margin: 0; font-size: 1.08rem; line-height: 1.15; }
    .brand-text span { font-size: 0.72rem; opacity: 0.9; display: block; }
    .header-actions { display: flex; gap: 8px; }
    .icon-btn { background: rgba(255,255,255,0.18); border: none; color: #fff; padding: 6px 10px; border-radius: 8px; font-size: 0.85rem; cursor: pointer; }
    .tabs { display: flex; background: var(--card); border-bottom: 1px solid var(--border); position: sticky; top: 62px; z-index: 90; }
    .tab { flex: 1; text-align: center; padding: 12px 8px; font-weight: 600; font-size: 0.92rem; cursor: pointer; border-bottom: 3px solid transparent; color: var(--muted); }
    .tab.active { color: var(--primary); border-bottom-color: var(--primary); }
    .container { max-width: 720px; margin: 0 auto; padding: 14px; }
    .search-bar { width: 100%; padding: 10px 14px; border: 1px solid var(--border); border-radius: 10px; background: var(--card); color: var(--text); font-size: 0.95rem; margin-bottom: 12px; }
    .card { background: var(--card); border: 1px solid var(--border); border-radius: 12px; padding: 14px; margin-bottom: 12px; }
    .card-header { display: flex; justify-content: space-between; align-items: flex-start; gap: 8px; }
    .badge { display: inline-block; background: var(--accent-bg); color: var(--primary); padding: 3px 8px; border-radius: 6px; font-size: 0.75rem; font-weight: 600; }
    .card-title { margin: 4px 0; font-size: 1.05rem; font-weight: 700; }
    .meta { font-size: 0.85rem; color: var(--muted); }
    .btn { padding: 8px 12px; border-radius: 8px; border: none; font-weight: 600; font-size: 0.85rem; cursor: pointer; display: inline-flex; align-items: center; justify-content: center; gap: 5px; }
    .btn-primary { background: var(--primary); color: #fff; }
    .btn-success { background: var(--success); color: #fff; }
    .btn-danger { background: var(--danger); color: #fff; }
    .btn-outline { background: transparent; border: 1px solid var(--border); color: var(--text); }
    .btn-sm { padding: 6px 10px; font-size: 0.8rem; }
    .btn-group { display: flex; gap: 8px; flex-wrap: wrap; margin-top: 10px; }
    .fab { position: fixed; bottom: 20px; right: 20px; background: var(--primary); color: #fff; border: none; border-radius: 50px; padding: 14px 20px; font-size: 0.95rem; font-weight: 700; cursor: pointer; z-index: 95; box-shadow: 0 4px 12px rgba(37,99,235,0.35); }
    .modal-backdrop { display: none; position: fixed; inset: 0; background: rgba(0,0,0,0.55); z-index: 200; overflow-y: auto; padding: 14px; }
    .modal-backdrop.open { display: block; }
    .modal { background: var(--card); max-width: 650px; margin: 20px auto; border-radius: 14px; padding: 16px; border: 1px solid var(--border); }
    .modal-header { display: flex; justify-content: space-between; align-items: center; border-bottom: 1px solid var(--border); padding-bottom: 10px; margin-bottom: 12px; }
    .form-group { margin-bottom: 10px; }
    .form-group label { display: block; font-size: 0.82rem; font-weight: 600; margin-bottom: 4px; color: var(--muted); }
    .form-control { width: 100%; padding: 9px 10px; border: 1px solid var(--border); border-radius: 8px; background: var(--bg); color: var(--text); font-size: 0.92rem; }
    .row-grid { display: grid; grid-template-columns: 2fr 1fr 0.9fr 1fr auto; gap: 6px; margin-bottom: 8px; align-items: center; }
    @media (max-width: 520px) { .row-grid { grid-template-columns: 1fr 1fr; background: var(--bg); padding: 8px; border-radius: 8px; } .row-grid input:first-child { grid-column: span 2; } }
    table { width: 100%; border-collapse: collapse; margin-top: 10px; font-size: 0.88rem; }
    th, td { padding: 8px 6px; border-bottom: 1px solid var(--border); text-align: left; }
    th { color: var(--muted); font-weight: 600; }
    .sub-unit { display: block; font-size: 0.76rem; color: var(--primary); font-weight: 600; }
    .preset-bar { display: flex; gap: 8px; flex-wrap: wrap; align-items: center; background: var(--accent-bg); padding: 10px; border-radius: 10px; margin: 10px 0; }
    .preset-input { width: 110px; padding: 7px 10px; border: 1px solid var(--primary); border-radius: 8px; font-weight: 700; font-size: 1rem; background: var(--card); color: var(--text); }
    .summary-box { display: grid; grid-template-columns: 1fr 1fr; gap: 8px; background: var(--bg); padding: 10px; border-radius: 10px; margin-top: 10px; }
    .summary-item span { display: block; font-size: 0.78rem; color: var(--muted); }
    .summary-item strong { font-size: 1.05rem; color: var(--primary); }
    .toast { position: fixed; bottom: 80px; left: 50%; transform: translateX(-50%); background: #1e293b; color: #fff; padding: 10px 18px; border-radius: 30px; font-size: 0.88rem; display: none; z-index: 300; }
  </style>
</head>
<body>
<header>
  <div class="brand">
    <div class="brand-logo" aria-label="My Formula Vault Logo">
      <svg width="26" height="26" viewBox="0 0 28 28" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M10 4H18M12 4V10.2L6.4 19.6C5.6 20.9 6.6 22.5 8.1 22.5H19.9C21.4 22.5 22.4 20.9 21.6 19.6L16 10.2V4" stroke="#2563eb" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round"/>
        <path d="M8.5 17.5C10.5 16.5 13.5 18.5 15.5 17.5C17 16.8 18.5 17.2 19.5 17.8L21.2 20.5C21.6 21.2 21.1 22 20.3 22H7.7C6.9 22 6.4 21.2 6.8 20.5L8.5 17.5Z" fill="#16a34a" fill-opacity="0.85"/>
        <circle cx="14" cy="13.5" r="1.3" fill="#2563eb"/>
      </svg>
    </div>
    <div class="brand-text">
      <h1>মাই ফর্মুলা ভল্ট</h1>
      <span>MY FORMULA VAULT</span>
    </div>
  </div>
  <div class="header-actions">
    <button class="icon-btn" onclick="openBackupModal()">💾 ব্যাকআপ</button>
    <button class="icon-btn" onclick="toggleDark()">🌓 থিম</button>
  </div>
</header>
<div class="tabs">
  <div class="tab active" id="tab-my" onclick="switchTab('my')">আমার ফর্মুলা (<span id="my-count">0</span>)</div>
  <div class="tab" id="tab-explore" onclick="switchTab('explore')">নতুন ফর্মুলা দেখুন</div>
</div>
<div class="container">
  <input type="text" id="searchInput" class="search-bar" placeholder="ফর্মুলার নাম বা ক্যাটাগরি খুঁজুন..." oninput="renderList()" />
  <div id="listContainer"></div>
</div>
<button class="fab" onclick="openFormModal()">+ নতুন ফর্মুলা</button>

<div class="modal-backdrop" id="calcModal">
  <div class="modal">
    <div class="modal-header">
      <div><span class="badge" id="viewCat"></span><h3 style="margin:4px 0 0;" id="viewTitle"></h3></div>
      <button class="btn btn-outline btn-sm" onclick="closeModal('calcModal')">✕ বন্ধ</button>
    </div>
    <div class="preset-bar">
      <div style="flex:1; min-width:140px;">
        <label style="font-size:0.78rem; font-weight:700; display:block; margin-bottom:4px;">কত কেজি/লিটার বানাবেন?</label>
        <input type="number" id="targetBatchInput" class="preset-input" step="any" oninput="recalcBatch()" />
        <span id="viewBaseUnit" style="font-weight:700; margin-left:4px;">কেজি</span>
      </div>
      <div style="display:flex; gap:6px; flex-wrap:wrap;">
        <button class="btn btn-primary btn-sm" onclick="setBatch(25)">২৫</button>
        <button class="btn btn-primary btn-sm" onclick="setBatch(50)">৫০</button>
        <button class="btn btn-primary btn-sm" onclick="setBatch(70)">৭০</button>
        <button class="btn btn-outline btn-sm" onclick="resetBatch()">মূল ব্যাচ</button>
      </div>
    </div>
    <table>
      <thead><tr><th>উপকরণ</th><th>পরিমাণ</th><th>দর</th><th>মোট টাকা</th></tr></thead>
      <tbody id="calcTableBody"></tbody>
    </table>
    <div class="summary-box">
      <div class="summary-item"><span>মোট ব্যাচ ওজন</span><strong id="sumWeight">0</strong></div>
      <div class="summary-item"><span>মোট উৎপাদন খরচ</span><strong id="sumCost">৳ 0</strong></div>
      <div class="summary-item"><span>প্রতি কেজি/লিটার খরচ</span><strong id="unitCost">৳ 0</strong></div>
      <div class="summary-item"><span>মূল বেস ব্যাচ</span><strong id="origBatchInfo">0</strong></div>
    </div>
    <p id="viewNotes" style="font-size:0.85rem; color:var(--muted); margin-top:10px; white-space:pre-line;"></p>
    <div class="btn-group">
      <button class="btn btn-success" onclick="copySlip()">📋 হিসাব কপি করুন</button>
      <button class="btn btn-primary" id="saveExploreBtn" style="display:none;" onclick="saveFromExplore()">⭐ আমার ফর্মুলায় সেভ করুন</button>
      <button class="btn btn-outline" id="editBtn" onclick="editCurrentFormula()">✏️ এডিট</button>
      <button class="btn btn-danger" id="deleteBtn" onclick="deleteCurrentFormula()">🗑️ ডিলিট</button>
    </div>
  </div>
</div>

<div class="modal-backdrop" id="formModal">
  <div class="modal">
    <div class="modal-header">
      <h3 style="margin:0;" id="formModalTitle">নতুন ফর্মুলা যোগ করুন</h3>
      <button class="btn btn-outline btn-sm" onclick="closeModal('formModal')">✕</button>
    </div>
    <input type="hidden" id="editId" />
    <div class="form-group"><label>ফর্মুলার নাম *</label><input type="text" id="fName" class="form-control" /></div>
    <div style="display:grid; grid-template-columns:1fr 1fr 1fr; gap:8px;">
      <div class="form-group"><label>ক্যাটাগরি</label><input type="text" id="fCat" class="form-control" value="হোম কেয়ার" /></div>
      <div class="form-group"><label>বেস ব্যাচ সাইজ *</label><input type="number" id="fBatch" class="form-control" step="any" /></div>
      <div class="form-group"><label>একক</label><select id="fUnit" class="form-control"><option value="কেজি">কেজি (kg)</option><option value="লিটার">লিটার (L)</option><option value="গ্রাম">গ্রাম (g)</option></select></div>
    </div>
    <div style="display:flex; justify-content:space-between; align-items:center; margin:8px 0;">
      <strong style="font-size:0.9rem;">উপকরণের তালিকা</strong>
      <button type="button" class="btn btn-outline btn-sm" onclick="autoSetBaseBatch()">⚖️ মোট ওজনকে বেস ব্যাচ ধরুন</button>
    </div>
    <div id="ingredientsEditor"></div>
    <button type="button" class="btn btn-outline btn-sm" style="width:100%; margin-top:4px;" onclick="addIngredientRow()">+ আরও উপকরণ যোগ করুন</button>
    <div class="form-group" style="margin-top:10px;"><label>প্রস্তুত প্রণালী / নোট</label><textarea id="fNotes" class="form-control" rows="2"></textarea></div>
    <div class="btn-group"><button class="btn btn-primary" style="flex:1;" onclick="saveFormula()">💾 ফর্মুলা সেভ করুন</button></div>
  </div>
</div>

<div class="modal-backdrop" id="backupModal">
  <div class="modal">
    <div class="modal-header">
      <h3 style="margin:0;">ডাটা ব্যাকআপ ও রিস্টোর</h3>
      <button class="btn btn-outline btn-sm" onclick="closeModal('backupModal')">✕</button>
    </div>
    <p style="font-size:0.88rem; color:var(--muted);">আপনার ফর্মুলা JSON ফাইল হিসেবে সেভ বা রিস্টোর করুন।</p>
    <div class="btn-group">
      <button class="btn btn-primary" onclick="exportBackup()">⬇️ ব্যাকআপ ডাউনলোড করুন</button>
      <label class="btn btn-outline" style="cursor:pointer;">⬆️ ব্যাকআপ ফাইল আপলোড<input type="file" accept=".json" style="display:none;" onchange="importBackup(event)" /></label>
    </div>
  </div>
</div>
<div class="toast" id="toast"></div>

<script>
  const EXPLORE_FORMULAS = [
    { id: 'exp_1', name: 'কমার্শিয়াল ডিটারজেন্ট পাউডার', category: 'হোম কেয়ার', batch: 100, unit: 'কেজি', notes: 'সোডা অ্যাশ ও লবণ মিশিয়ে LABSA দিন।', ingredients: [
      { name: 'সোডা অ্যাশ', qty: 42, unit: 'কেজি', rate: 52 }, { name: 'লবণ', qty: 32, unit: 'কেজি', rate: 18 },
      { name: 'ল্যাবসা', qty: 10, unit: 'কেজি', rate: 175 }, { name: 'এসএলইএস', qty: 3, unit: 'কেজি', rate: 165 },
      { name: 'এসটিপিপি', qty: 4, unit: 'কেজি', rate: 140 }, { name: 'কস্টিক সোডা', qty: 1.5, unit: 'কেজি', rate: 95 },
      { name: 'পানি', qty: 6, unit: 'কেজি', rate: 0 }, { name: 'কালার ও পারফিউম', qty: 1.5, unit: 'কেজি', rate: 650 }
    ]},
    { id: 'exp_2', name: 'লিকুইড হ্যান্ডওয়াশ', category: 'পার্সোনাল কেয়ার', batch: 100, unit: 'লিটার', notes: 'পানিতে SLES গুলিয়ে CDEA ও লবণ দিন।', ingredients: [
      { name: 'পানি', qty: 80, unit: 'লিটার', rate: 2 }, { name: 'এসএলইএস', qty: 11, unit: 'কেজি', rate: 165 },
      { name: 'কোকা ডিইএ', qty: 2.5, unit: 'কেজি', rate: 220 }, { name: 'গ্লিসারিন', qty: 2, unit: 'কেজি', rate: 180 },
      { name: 'পার্ল এজেন্ট', qty: 1.5, unit: 'কেজি', rate: 260 }, { name: 'লবণ', qty: 2.2, unit: 'কেজি', rate: 25 },
      { name: 'পারফিউম ও কালার', qty: 0.8, unit: 'কেজি', rate: 800 }
    ]}
  ];
  let myFormulas = JSON.parse(localStorage.getItem('fv_my_formulas') || '[]');
  let activeTab = 'my', currentFormula = null, isExploreCurrent = false;
  if (localStorage.getItem('fv_dark') === '1') document.body.classList.add('dark');
  function showToast(msg) { const t = document.getElementById('toast'); t.textContent = msg; t.style.display = 'block'; setTimeout(() => { t.style.display = 'none'; }, 2400); }
  function toggleDark() { document.body.classList.toggle('dark'); localStorage.setItem('fv_dark', document.body.classList.contains('dark') ? '1' : '0'); }
  function switchTab(tab) { activeTab = tab; document.getElementById('tab-my').classList.toggle('active', tab === 'my'); document.getElementById('tab-explore').classList.toggle('active', tab === 'explore'); renderList(); }
  function calcTotalCost(f) { return f.ingredients.reduce((s, i) => s + (Number(i.qty) * Number(i.rate || 0)), 0); }
  function renderList() {
    document.getElementById('my-count').textContent = myFormulas.length;
    const q = document.getElementById('searchInput').value.toLowerCase().trim();
    const list = (activeTab === 'my' ? myFormulas : EXPLORE_FORMULAS).filter(f => f.name.toLowerCase().includes(q) || (f.category || '').toLowerCase().includes(q));
    const el = document.getElementById('listContainer');
    if (!list.length) { el.innerHTML = `<div class="card" style="text-align:center;padding:25px;color:var(--muted);">কোনো ফর্মুলা নেই। "+ নতুন ফর্মুলা" চাপুন বা "নতুন ফর্মুলা দেখুন" ট্যাব দেখুন।</div>`; return; }
    el.innerHTML = list.map(f => {
      const total = calcTotalCost(f), per = f.batch > 0 ? (total / f.batch).toFixed(2) : 0;
      return `<div class="card" onclick="openCalcModal('${f.id}', ${activeTab === 'explore'})" style="cursor:pointer;"><div class="card-header"><div><span class="badge">${f.category || 'সাধারণ'}</span><div class="card-title">${f.name}</div><div class="meta">ব্যাচ: <b>${f.batch} ${f.unit}</b> • ${f.ingredients.length} আইটেম</div></div><div style="text-align:right;"><div style="font-weight:700;color:var(--primary);">৳ ${per}/${f.unit}</div><div class="meta">মোট: ৳ ${total.toFixed(0)}</div></div></div></div>`;
    }).join('');
  }
  function openCalcModal(id, isExplore) {
    isExploreCurrent = isExplore;
    currentFormula = JSON.parse(JSON.stringify((isExplore ? EXPLORE_FORMULAS : myFormulas).find(x => x.id === id)));
    if (!currentFormula) return;
    document.getElementById('viewCat').textContent = currentFormula.category || 'সাধারণ';
    document.getElementById('viewTitle').textContent = currentFormula.name;
    document.getElementById('viewBaseUnit').textContent = currentFormula.unit;
    document.getElementById('targetBatchInput').value = currentFormula.batch;
    document.getElementById('origBatchInfo').textContent = `${currentFormula.batch} ${currentFormula.unit}`;
    document.getElementById('viewNotes').textContent = currentFormula.notes ? `📝 ${currentFormula.notes}` : '';
    document.getElementById('saveExploreBtn').style.display = isExplore ? 'inline-flex' : 'none';
    document.getElementById('editBtn').style.display = isExplore ? 'none' : 'inline-flex';
    document.getElementById('deleteBtn').style.display = isExplore ? 'none' : 'inline-flex';
    recalcBatch();
    document.getElementById('calcModal').classList.add('open');
  }
  function setBatch(v) { document.getElementById('targetBatchInput').value = v; recalcBatch(); }
  function resetBatch() { if (currentFormula) { document.getElementById('targetBatchInput').value = currentFormula.batch; recalcBatch(); } }
  function formatSubUnit(qty, unit) {
    if (qty > 0 && qty < 10) {
      if (unit === 'কেজি') return `<span class="sub-unit">(${(qty * 1000).toFixed(0)} গ্রাম)</span>`;
      if (unit === 'লিটার') return `<span class="sub-unit">(${(qty * 1000).toFixed(0)} মিলি)</span>`;
    }
    return '';
  }
  function recalcBatch() {
    if (!currentFormula) return;
    const target = parseFloat(document.getElementById('targetBatchInput').value) || 0;
    const ratio = currentFormula.batch > 0 ? (target / currentFormula.batch) : 0;
    let totalCost = 0;
    document.getElementById('calcTableBody').innerHTML = currentFormula.ingredients.map(item => {
      const q = item.qty * ratio, c = q * (item.rate || 0); totalCost += c;
      const qStr = q % 1 === 0 ? q.toFixed(0) : q.toFixed(3).replace(/\.?0+$/, '');
      return `<tr><td><b>${item.name}</b></td><td><b>${qStr} ${item.unit}</b>${formatSubUnit(q, item.unit)}</td><td>৳${item.rate || 0}</td><td><b>৳${c.toFixed(1)}</b></td></tr>`;
    }).join('');
    document.getElementById('sumWeight').textContent = `${target} ${currentFormula.unit}`;
    document.getElementById('sumCost').textContent = `৳ ${totalCost.toFixed(2)}`;
    document.getElementById('unitCost').textContent = target > 0 ? `৳ ${(totalCost / target).toFixed(2)}` : '৳ 0';
  }
  function copySlip() {
    if (!currentFormula) return;
    const target = parseFloat(document.getElementById('targetBatchInput').value) || 0;
    const ratio = currentFormula.batch > 0 ? (target / currentFormula.batch) : 0;
    let lines = [`🧪 *${currentFormula.name}*`, `📦 ব্যাচ: ${target} ${currentFormula.unit}`, `---`], totalCost = 0;
    currentFormula.ingredients.forEach((item, i) => {
      const q = item.qty * ratio; totalCost += q * (item.rate || 0);
      const qStr = q % 1 === 0 ? q.toFixed(0) : q.toFixed(3).replace(/\.?0+$/, '');
      const extra = (q > 0 && q < 10 && (item.unit === 'কেজি' || item.unit === 'লিটার')) ? ` (${(q * 1000).toFixed(0)} ${item.unit === 'কেজি' ? 'গ্রাম' : 'মিলি'})` : '';
      lines.push(`${i + 1}. ${item.name}: ${qStr} ${item.unit}${extra}`);
    });
    lines.push(`---`, `💰 মোট খরচ: ৳${totalCost.toFixed(0)}`);
    navigator.clipboard.writeText(lines.join('\n')).then(() => showToast('কপি হয়েছে!'));
  }
  function saveFromExplore() {
    if (!currentFormula) return;
    const copy = JSON.parse(JSON.stringify(currentFormula)); copy.id = 'my_' + Date.now();
    myFormulas.unshift(copy); persist(); closeModal('calcModal'); switchTab('my'); showToast('সেভ হয়েছে!');
  }
  function openFormModal(f = null) {
    document.getElementById('editId').value = f ? f.id : '';
    document.getElementById('formModalTitle').textContent = f ? 'ফর্মুলা এডিট' : 'নতুন ফর্মুলা';
    document.getElementById('fName').value = f ? f.name : '';
    document.getElementById('fCat').value = f ? f.category : 'হোম কেয়ার';
    document.getElementById('fBatch').value = f ? f.batch : '';
    document.getElementById('fUnit').value = f ? f.unit : 'কেজি';
    document.getElementById('fNotes').value = f ? (f.notes || '') : '';
    const ed = document.getElementById('ingredientsEditor'); ed.innerHTML = '';
    (f ? f.ingredients : [{ name: '', qty: '', unit: 'কেজি', rate: '' }]).forEach(it => addIngredientRow(it));
    document.getElementById('formModal').classList.add('open');
  }
  function addIngredientRow(item = { name: '', qty: '', unit: 'কেজি', rate: '' }) {
    const div = document.createElement('div'); div.className = 'row-grid';
    div.innerHTML = `<input type="text" class="form-control ing-name" placeholder="উপকরণ" value="${item.name}" /><input type="number" step="any" class="form-control ing-qty" placeholder="পরিমাণ" value="${item.qty}" /><select class="form-control ing-unit"><option value="কেজি" ${item.unit==='কেজি'?'selected':''}>কেজি</option><option value="গ্রাম" ${item.unit==='গ্রাম'?'selected':''}>গ্রাম</option><option value="লিটার" ${item.unit==='লিটার'?'selected':''}>লিটার</option><option value="মিলি" ${item.unit==='মিলি'?'selected':''}>মিলি</option></select><input type="number" step="any" class="form-control ing-rate" placeholder="দর" value="${item.rate}" /><button type="button" class="btn btn-danger btn-sm" onclick="this.parentElement.remove()">✕</button>`;
    document.getElementById('ingredientsEditor').appendChild(div);
  }
  function autoSetBaseBatch() {
    const bu = document.getElementById('fUnit').value; let total = 0;
    document.querySelectorAll('#ingredientsEditor .row-grid').forEach(r => {
      const q = parseFloat(r.querySelector('.ing-qty').value) || 0, u = r.querySelector('.ing-unit').value;
      if (bu === 'কেজি' || bu === 'লিটার') total += (u === 'গ্রাম' || u === 'মিলি') ? q / 1000 : q;
      else total += (u === 'কেজি' || u === 'লিটার') ? q * 1000 : q;
    });
    if (total > 0) { document.getElementById('fBatch').value = Number(total.toFixed(3)); showToast(`বেস ব্যাচ ${Number(total.toFixed(3))} ${bu} সেট হয়েছে`); }
  }
  function saveFormula() {
    const name = document.getElementById('fName').value.trim(), category = document.getElementById('fCat').value.trim() || 'সাধারণ';
    const batch = parseFloat(document.getElementById('fBatch').value), unit = document.getElementById('fUnit').value;
    const notes = document.getElementById('fNotes').value.trim(), editId = document.getElementById('editId').value;
    if (!name || !batch || batch <= 0) { alert('নাম ও ব্যাচ সাইজ দিন।'); return; }
    const ingredients = [];
    document.querySelectorAll('#ingredientsEditor .row-grid').forEach(r => {
      const iName = r.querySelector('.ing-name').value.trim(), iQty = parseFloat(r.querySelector('.ing-qty').value), iUnit = r.querySelector('.ing-unit').value, iRate = parseFloat(r.querySelector('.ing-rate').value) || 0;
      if (iName && iQty > 0) {
        let nq = iQty, nu = iUnit;
        if ((unit === 'কেজি' && iUnit === 'গ্রাম') || (unit === 'লিটার' && iUnit === 'মিলি')) { nq = iQty / 1000; nu = unit; }
        ingredients.push({ name: iName, qty: nq, unit: nu, rate: iRate });
      }
    });
    if (!ingredients.length) { alert('কমপক্ষে একটি উপকরণ দিন।'); return; }
    if (editId) { const idx = myFormulas.findIndex(x => x.id === editId); if (idx !== -1) myFormulas[idx] = { id: editId, name, category, batch, unit, notes, ingredients }; }
    else myFormulas.unshift({ id: 'my_' + Date.now(), name, category, batch, unit, notes, ingredients });
    persist(); closeModal('formModal'); switchTab('my'); showToast('সেভ হয়েছে!');
  }
  function editCurrentFormula() { if (currentFormula) { closeModal('calcModal'); openFormModal(currentFormula); } }
  function deleteCurrentFormula() { if (currentFormula && confirm('মুছে ফেলবেন?')) { myFormulas = myFormulas.filter(x => x.id !== currentFormula.id); persist(); closeModal('calcModal'); renderList(); } }
  function persist() { localStorage.setItem('fv_my_formulas', JSON.stringify(myFormulas)); }
  function closeModal(id) { document.getElementById(id).classList.remove('open'); }
  function openBackupModal() { document.getElementById('backupModal').classList.add('open'); }
  function exportBackup() {
    const blob = new Blob([JSON.stringify(myFormulas, null, 2)], { type: 'application/json' });
    const url = URL.createObjectURL(blob), a = document.createElement('a');
    a.href = url; a.download = 'my_formula_vault_backup.json'; a.click(); URL.revokeObjectURL(url);
  }
  function importBackup(e) {
    const file = e.target.files[0]; if (!file) return;
    const reader = new FileReader();
    reader.onload = evt => { try { const imp = JSON.parse(evt.target.result); if (Array.isArray(imp)) { myFormulas = imp; persist(); renderList(); closeModal('backupModal'); showToast('রিস্টোর হয়েছে!'); } } catch { alert('সঠিক ফাইল নয়।'); } };
    reader.readAsText(file);
  }
  renderList();
</script>
</body>
</html>
