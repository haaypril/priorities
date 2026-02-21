<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Texas Priorities</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Libre+Baskerville:ital,wght@0,400;0,700;1,400&family=DM+Mono:wght@300;400;500&display=swap');

  :root {
    --bg: #F5F1EB;
    --surface: #FDFAF5;
    --border: #D8CFC0;
    --border-light: #EBE5DA;
    --ink: #1A160E;
    --ink-mid: #5C5244;
    --ink-light: #9C8E7E;
    --accent: #C4450A;
    --accent-light: #F0E4DC;
    --green: #2E6B3A;
    --green-light: #D8EDD9;
    --yellow: #9B7B1A;
    --yellow-light: #F5EAC8;
    --blue: #1A4A7A;
    --blue-light: #D3E2F0;
    --shadow: 0 1px 3px rgba(26,22,14,0.08), 0 4px 12px rgba(26,22,14,0.04);
  }

  * { box-sizing: border-box; margin: 0; padding: 0; }
  body { font-family: 'DM Mono', monospace; background: var(--bg); color: var(--ink); min-height: 100vh; font-size: 13px; }

  .topbar { background: var(--ink); color: #F5F1EB; padding: 0 24px; display: flex; align-items: center; gap: 20px; height: 52px; position: sticky; top: 0; z-index: 100; }
  .topbar-logo { font-family: 'Libre Baskerville', serif; font-size: 17px; letter-spacing: -0.3px; white-space: nowrap; flex-shrink: 0; }
  .topbar-logo span { color: var(--accent); }
  .topbar-nav { display: flex; gap: 4px; flex: 1; overflow-x: auto; }
  .topbar-nav::-webkit-scrollbar { display: none; }
  .nav-btn { background: none; border: 1px solid transparent; color: rgba(245,241,235,0.6); padding: 5px 12px; border-radius: 4px; cursor: pointer; font: inherit; font-size: 12px; white-space: nowrap; transition: all 0.15s; }
  .nav-btn:hover { color: #F5F1EB; background: rgba(255,255,255,0.08); }
  .nav-btn.active { color: var(--ink); background: var(--bg); border-color: var(--bg); }
  .sync-indicator { margin-left: auto; font-size: 11px; color: rgba(245,241,235,0.5); display: flex; align-items: center; gap: 6px; flex-shrink: 0; }
  .sync-dot { width: 7px; height: 7px; border-radius: 50%; background: #5AB85C; animation: pulse 2s ease-in-out infinite; }
  .sync-dot.syncing { background: var(--yellow); animation: none; }
  .sync-dot.error { background: var(--accent); animation: none; }
  @keyframes pulse { 0%,100% { opacity: 1; } 50% { opacity: 0.4; } }

  .main { max-width: 1280px; margin: 0 auto; padding: 24px 20px; }

  .section-header { display: flex; align-items: center; justify-content: space-between; margin-bottom: 16px; flex-wrap: wrap; gap: 10px; }
  .section-title { font-family: 'Libre Baskerville', serif; font-size: 22px; font-weight: 400; letter-spacing: -0.3px; }
  .section-subtitle { font-size: 12px; color: var(--ink-light); margin-top: 2px; }

  .progress-bar-wrap { background: var(--border-light); border-radius: 2px; height: 4px; overflow: hidden; margin-bottom: 20px; }
  .progress-bar-fill { height: 100%; background: var(--green); transition: width 0.4s ease; }

  .btn { display: inline-flex; align-items: center; gap: 6px; padding: 7px 14px; border-radius: 5px; border: 1px solid var(--border); background: var(--surface); color: var(--ink); font: inherit; font-size: 12px; cursor: pointer; transition: all 0.15s; }
  .btn:hover { background: var(--bg); border-color: var(--ink-light); }
  .btn-primary { background: var(--ink); color: var(--bg); border-color: var(--ink); }
  .btn-primary:hover { background: #2E2820; }
  .btn-accent { background: var(--accent); color: white; border-color: var(--accent); }
  .btn-accent:hover { background: #A33A08; }
  .btn-sm { padding: 4px 10px; font-size: 11px; }
  .btn-icon { padding: 5px 8px; }

  .task-table-wrap { background: var(--surface); border: 1px solid var(--border); border-radius: 8px; overflow: hidden; box-shadow: var(--shadow); margin-bottom: 24px; }
  .task-table-title { padding: 12px 16px; border-bottom: 1px solid var(--border-light); display: flex; align-items: center; justify-content: space-between; gap: 8px; }
  .task-table-title h3 { font-family: 'Libre Baskerville', serif; font-size: 14px; font-weight: 700; display: flex; align-items: center; gap: 8px; }

  .deal-badge { font-family: 'DM Mono', monospace; font-size: 10px; font-weight: 500; padding: 2px 7px; border-radius: 3px; background: var(--accent-light); color: var(--accent); text-transform: uppercase; letter-spacing: 0.5px; }
  .deal-badge.construction { background: var(--yellow-light); color: var(--yellow); }
  .deal-badge.post-award { background: var(--blue-light); color: var(--blue); }
  .deal-badge.lease-up { background: var(--green-light); color: var(--green); }

  table { width: 100%; border-collapse: collapse; }
  thead th { text-align: left; padding: 8px 12px; font-size: 10px; text-transform: uppercase; letter-spacing: 0.8px; color: var(--ink-light); border-bottom: 1px solid var(--border-light); background: var(--bg); white-space: nowrap; }
  tbody tr { border-bottom: 1px solid var(--border-light); transition: background 0.1s; }
  tbody tr:last-child { border-bottom: none; }
  tbody tr:hover { background: var(--bg); }
  tbody td { padding: 10px 12px; vertical-align: top; }

  .task-check { width: 32px; text-align: center; }
  .check-box { width: 16px; height: 16px; border: 1.5px solid var(--border); border-radius: 3px; cursor: pointer; display: inline-flex; align-items: center; justify-content: center; transition: all 0.15s; flex-shrink: 0; }
  .check-box:hover { border-color: var(--green); }
  .check-box.checked { background: var(--green); border-color: var(--green); }
  .check-box.checked::after { content: '✓'; color: white; font-size: 10px; line-height: 1; }

  .task-text { font-size: 12.5px; line-height: 1.5; }
  .task-text.done { text-decoration: line-through; color: var(--ink-light); }
  .task-notes { font-size: 11.5px; color: var(--ink-mid); margin-top: 3px; }

  .responsible-chip { display: inline-block; padding: 2px 8px; border-radius: 3px; background: var(--accent-light); color: var(--accent); font-size: 11px; font-weight: 500; white-space: nowrap; }
  .responsible-chip.ae { background: var(--blue-light); color: var(--blue); }
  .responsible-chip.ch { background: var(--yellow-light); color: var(--yellow); }
  .responsible-chip.both { background: var(--green-light); color: var(--green); }

  .date-cell { white-space: nowrap; font-size: 12px; }
  .date-cell.overdue { color: var(--accent); font-weight: 500; }
  .date-cell.soon { color: var(--yellow); }
  .date-cell.done-date { color: var(--ink-light); text-decoration: line-through; }

  .add-row td { padding: 6px 12px; }
  .add-btn-inline { background: none; border: none; color: var(--ink-light); font: inherit; font-size: 12px; cursor: pointer; display: flex; align-items: center; gap: 6px; padding: 4px 0; transition: color 0.15s; }
  .add-btn-inline:hover { color: var(--accent); }

  .month-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(300px, 1fr)); gap: 16px; margin-bottom: 24px; }
  .month-card { background: var(--surface); border: 1px solid var(--border); border-radius: 8px; overflow: hidden; box-shadow: var(--shadow); }
  .month-card-header { padding: 12px 16px; background: var(--ink); color: var(--bg); display: flex; align-items: center; justify-content: space-between; cursor: pointer; user-select: none; }
  .month-card-header h3 { font-family: 'Libre Baskerville', serif; font-size: 14px; font-weight: 400; }
  .month-card-header .count { font-size: 11px; opacity: 0.6; }
  .month-card-body { padding: 8px 0; }
  .milestone-row { display: flex; align-items: flex-start; gap: 10px; padding: 8px 16px; border-bottom: 1px solid var(--border-light); transition: background 0.1s; }
  .milestone-row:last-child { border-bottom: none; }
  .milestone-row:hover { background: var(--bg); }
  .milestone-content { flex: 1; min-width: 0; }
  .milestone-title { font-size: 12px; line-height: 1.4; }
  .milestone-title.done { text-decoration: line-through; color: var(--ink-light); }
  .milestone-meta { display: flex; align-items: center; gap: 8px; margin-top: 4px; flex-wrap: wrap; }
  .milestone-dev { font-size: 10px; color: var(--ink-mid); background: var(--bg); border: 1px solid var(--border-light); padding: 1px 6px; border-radius: 3px; }
  .milestone-date { font-size: 10px; color: var(--ink-light); }

  .filter-bar { display: flex; gap: 8px; margin-bottom: 16px; flex-wrap: wrap; align-items: center; }
  .filter-chip { padding: 4px 12px; border: 1px solid var(--border); border-radius: 100px; background: var(--surface); color: var(--ink-mid); font: inherit; font-size: 11px; cursor: pointer; transition: all 0.15s; white-space: nowrap; }
  .filter-chip:hover { border-color: var(--ink-light); color: var(--ink); }
  .filter-chip.active { background: var(--ink); color: var(--bg); border-color: var(--ink); }
  .search-input { padding: 5px 12px; border: 1px solid var(--border); border-radius: 5px; background: var(--surface); font: inherit; font-size: 12px; color: var(--ink); outline: none; transition: border-color 0.15s; min-width: 200px; }
  .search-input:focus { border-color: var(--accent); }

  .stats-row { display: grid; grid-template-columns: repeat(auto-fill, minmax(160px, 1fr)); gap: 12px; margin-bottom: 24px; }
  .stat-card { background: var(--surface); border: 1px solid var(--border); border-radius: 8px; padding: 14px 16px; box-shadow: var(--shadow); }
  .stat-value { font-family: 'Libre Baskerville', serif; font-size: 28px; font-weight: 400; line-height: 1; margin-bottom: 4px; }
  .stat-label { font-size: 11px; color: var(--ink-light); text-transform: uppercase; letter-spacing: 0.5px; }

  .modal-overlay { position: fixed; inset: 0; background: rgba(26,22,14,0.5); z-index: 200; display: flex; align-items: center; justify-content: center; padding: 20px; backdrop-filter: blur(2px); }
  .modal { background: var(--surface); border-radius: 10px; width: 100%; max-width: 560px; max-height: 90vh; overflow-y: auto; box-shadow: 0 20px 60px rgba(26,22,14,0.2); }
  .modal-header { padding: 20px 24px 16px; border-bottom: 1px solid var(--border-light); display: flex; align-items: center; justify-content: space-between; }
  .modal-header h2 { font-family: 'Libre Baskerville', serif; font-size: 18px; font-weight: 400; }
  .modal-body { padding: 20px 24px; display: flex; flex-direction: column; gap: 14px; }
  .modal-footer { padding: 16px 24px; border-top: 1px solid var(--border-light); display: flex; justify-content: flex-end; gap: 8px; }
  .form-group { display: flex; flex-direction: column; gap: 4px; }
  .form-label { font-size: 11px; text-transform: uppercase; letter-spacing: 0.5px; color: var(--ink-light); }
  .form-input, .form-select, .form-textarea { padding: 8px 12px; border: 1px solid var(--border); border-radius: 5px; background: var(--bg); font: inherit; font-size: 13px; color: var(--ink); outline: none; transition: border-color 0.15s; }
  .form-input:focus, .form-select:focus, .form-textarea:focus { border-color: var(--accent); background: white; }
  .form-textarea { min-height: 80px; resize: vertical; }

  .toast-container { position: fixed; bottom: 20px; right: 20px; z-index: 300; display: flex; flex-direction: column; gap: 8px; pointer-events: none; }
  .toast { background: var(--ink); color: var(--bg); padding: 10px 16px; border-radius: 6px; font-size: 12px; box-shadow: 0 4px 16px rgba(0,0,0,0.2); animation: slideIn 0.2s ease; pointer-events: auto; }
  .toast.success { background: var(--green); }
  .toast.error { background: var(--accent); }
  @keyframes slideIn { from { transform: translateY(10px); opacity: 0; } }

  .tab-strip { display: flex; gap: 0; border-bottom: 1px solid var(--border); margin-bottom: 20px; overflow-x: auto; }
  .tab-strip::-webkit-scrollbar { display: none; }
  .tab { padding: 8px 16px; border: none; background: none; font: inherit; font-size: 12px; color: var(--ink-light); cursor: pointer; border-bottom: 2px solid transparent; margin-bottom: -1px; white-space: nowrap; transition: all 0.15s; }
  .tab:hover { color: var(--ink); }
  .tab.active { color: var(--accent); border-bottom-color: var(--accent); }

  .hidden { display: none !important; }

  .year-tabs { display: flex; gap: 4px; }
  .year-tab { padding: 4px 12px; border: 1px solid var(--border); border-radius: 4px; background: var(--surface); font: inherit; font-size: 11px; cursor: pointer; color: var(--ink-mid); transition: all 0.15s; }
  .year-tab.active { background: var(--ink); color: var(--bg); border-color: var(--ink); }

  .de-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(260px, 1fr)); gap: 16px; margin-bottom: 24px; }
  .de-card { background: var(--surface); border: 1px solid var(--border); border-radius: 8px; padding: 16px; box-shadow: var(--shadow); }
  .de-card h4 { font-family: 'Libre Baskerville', serif; font-size: 14px; font-weight: 700; margin-bottom: 10px; padding-bottom: 8px; border-bottom: 1px solid var(--border-light); }
  .de-row { display: flex; justify-content: space-between; padding: 5px 0; border-bottom: 1px solid var(--border-light); font-size: 12px; }
  .de-row:last-child { border-bottom: none; }
  .de-label { color: var(--ink-mid); }

  .empty-state { text-align: center; padding: 48px 24px; color: var(--ink-light); }
  .empty-state .icon { font-size: 36px; margin-bottom: 12px; }

  @media (max-width: 640px) {
    .topbar { padding: 0 14px; }
    .main { padding: 16px 12px; }
    .stats-row { grid-template-columns: repeat(2, 1fr); }
  }
</style>
</head>
<body>

<div class="topbar">
  <div class="topbar-logo">Texas <span>///</span> Priorities</div>
  <div class="topbar-nav" id="topNav">
    <button class="nav-btn active" onclick="showView('dashboard')">Dashboard</button>
    <button class="nav-btn" onclick="showView('priorities')">Top Priorities</button>
    <button class="nav-btn" onclick="showView('deals')">Deals</button>
    <button class="nav-btn" onclick="showView('milestones')">Milestones</button>
    <button class="nav-btn" onclick="showView('debt')">Debt &amp; Equity</button>
    <button class="nav-btn" onclick="showView('planning')">Planning</button>
  </div>
  <div class="sync-indicator">
    <div class="sync-dot" id="syncDot"></div>
    <span id="syncLabel">synced</span>
  </div>
</div>

<div class="main" id="mainContent"></div>

<div class="modal-overlay hidden" id="modalOverlay">
  <div class="modal">
    <div class="modal-header">
      <h2 id="modalTitle">Add</h2>
      <button class="btn btn-icon" onclick="closeModal()">✕</button>
    </div>
    <div class="modal-body" id="modalBody"></div>
    <div class="modal-footer">
      <button class="btn" onclick="closeModal()">Cancel</button>
      <button class="btn btn-primary" id="modalSave" onclick="saveModal()">Save</button>
    </div>
  </div>
</div>

<div class="toast-container" id="toastContainer"></div>

<script>
const SEED = {
  topPriorities: [
    {id:'tp1',complete:false,task:'Irving Lofts',notes:'Finalize underwriting',ooo:'AE - 2/23-24'},
    {id:'tp2',complete:true,task:'Landmark 601 - Equity',notes:'email Brad at Ice Miller for suggestions',ooo:'CH - 4/24'},
    {id:'tp3',complete:true,task:'Green Meadow',notes:'Completion equity - set date',ooo:'CH - 4/17 & 4/20'},
    {id:'tp4',complete:false,task:'Roosevelt Lofts - Stabilization',notes:'will review updates once Nigel sends',ooo:'AE - 4/2-3'},
    {id:'tp5',complete:true,task:'Clifton - Cost Cert Response',notes:'responded 2/17',ooo:'AE - 4/23-24'},
    {id:'tp6',complete:false,task:'Roosevelt Lofts - Award Nomination',notes:'due 3/4',ooo:''},
    {id:'tp7',complete:false,task:'Application Site Work Forms',notes:'',ooo:''},
    {id:'tp8',complete:true,task:'Centennial Park - Email councilmember',notes:'',ooo:''}
  ],
  deals: {
    'Irving Lofts': {status:'Post-Award',tasks:[
      {id:'il1',complete:false,task:'Façade Grant Opportunity',responsible:'',internalDue:'',externalDue:'',notes:'50% match up to $5,000 & eligible fee waiver',etc:'need to review timing'},
      {id:'il2',complete:true,task:'Building Permit Timing / Costs',responsible:'AE',internalDue:'',externalDue:'2025-12-29',notes:'followed up with Maggie/Andrea on 1/6',etc:''},
      {id:'il3',complete:true,task:'Underwriting Update',responsible:'AE',internalDue:'',externalDue:'2026-01-12',notes:'send over to Julie & MHEG - need appraisal updated',etc:''},
      {id:'il4',complete:false,task:'10% test',responsible:'CH',internalDue:'2026-03-31',externalDue:'',notes:'trying to work ahead of the 7/1 deadline',etc:'follow up with Cale week of 3/2'},
      {id:'il5',complete:false,task:'BR Insurance',responsible:'CH',internalDue:'2026-03-01',externalDue:'2026-03-03',notes:'we are moving forward with MCP',etc:''}
    ]},
    'Landmark 601': {status:'Post-Award',tasks:[
      {id:'l6011',complete:true,task:'Email group about solar',responsible:'AE',internalDue:'',externalDue:'',notes:'',etc:''},
      {id:'l6012',complete:true,task:'Underwriting update',responsible:'AE',internalDue:'',externalDue:'2025-12-31',notes:'sent to Drew on 1/2',etc:''},
      {id:'l6013',complete:false,task:'Design selections',responsible:'AE',internalDue:'',externalDue:'2026-01-30',notes:'',etc:''},
      {id:'l6014',complete:true,task:'Check in with Drew Foster',responsible:'AE',internalDue:'',externalDue:'2026-01-30',notes:'',etc:''},
      {id:'l6015',complete:false,task:'10% test',responsible:'CH',internalDue:'2026-03-31',externalDue:'',notes:'trying to work ahead of the 7/1 deadline',etc:'follow up with Cale week of 3/2'},
      {id:'l6016',complete:true,task:'PDL Draw',responsible:'CH',internalDue:'2026-02-10',externalDue:'',notes:'',etc:''},
      {id:'l6017',complete:true,task:'TABS registration',responsible:'AE',internalDue:'2026-02-10',externalDue:'',notes:'',etc:''}
    ]},
    'Landmark on Cypress': {status:'Post-Award',tasks:[
      {id:'loc1',complete:false,task:'Paramount Parking',responsible:'AE',internalDue:'',externalDue:'2026-05-30',notes:'will submit variance request to city post-pre apps',etc:''},
      {id:'loc2',complete:false,task:'Façade Grant Opportunity',responsible:'',internalDue:'',externalDue:'',notes:'post closing, coordinate timing with MCP once schedule received',etc:'for blade sign'},
      {id:'loc3',complete:false,task:'10% test',responsible:'CH',internalDue:'2026-03-31',externalDue:'',notes:'trying to work ahead of the 7/1 deadline',etc:'follow up with Cale week of 3/2'},
      {id:'loc4',complete:true,task:'First construction draw',responsible:'CH',internalDue:'2026-02-10',externalDue:'',notes:'need to check on signed pay app',etc:'submitted already'},
      {id:'loc5',complete:false,task:'JGR payment',responsible:'CH',internalDue:'',externalDue:'',notes:'March draw. Pay 50%',etc:''}
    ]},
    'Landmark on Pine': {status:'Post-Award',tasks:[
      {id:'lop1',complete:false,task:'Façade Grant Opportunity',responsible:'',internalDue:'',externalDue:'',notes:'',etc:''},
      {id:'lop2',complete:false,task:'Grant & Loan Programs',responsible:'',internalDue:'',externalDue:'',notes:'',etc:''},
      {id:'lop3',complete:true,task:'Updated Numbers',responsible:'AE',internalDue:'',externalDue:'2026-01-30',notes:'out to closing group',etc:''},
      {id:'lop4',complete:false,task:'EPA Grant - Phase I & II',responsible:'CH',internalDue:'',externalDue:'',notes:'requested Phase II approval from EPA on January 6th',etc:'Phase I will be updated for the reliance letter - due 2/20'},
      {id:'lop5',complete:false,task:'10% test',responsible:'CH',internalDue:'2026-03-31',externalDue:'',notes:'trying to work ahead of the 7/1 deadline',etc:'follow up with Cale week of 3/2'},
      {id:'lop6',complete:true,task:'Update lender & investor',responsible:'AE',internalDue:'',externalDue:'2026-02-09',notes:'permit submittal & plans & specs',etc:''}
    ]},
    'Landmark at Abilene': {status:'Lease-Up',tasks:[
      {id:'la1',complete:true,task:'Cost Cert',responsible:'CH',internalDue:'',externalDue:'2025-11-15',notes:'RFI responses sent to TDHCA 2/13/26',etc:''},
      {id:'la2',complete:true,task:'Gap financing / construction loan maturity date',responsible:'AE',internalDue:'',externalDue:'2025-12-17',notes:'getting a construction loan extension',etc:''},
      {id:'la3',complete:true,task:'Cost Cert RFI #2',responsible:'AE/CH',internalDue:'2026-01-16',externalDue:'',notes:'RFI response submitted on 2/13',etc:''},
      {id:'la4',complete:false,task:'Follow up with Ann @ MHEG',responsible:'AE',internalDue:'',externalDue:'2026-02-20',notes:'just checked in with Ryan (2/16)',etc:''}
    ]},
    'Clifton Riverside': {status:'Lease-Up',tasks:[
      {id:'cr1',complete:true,task:'Cost Cert - TDHCA DD',responsible:'CH',internalDue:'2026-01-08',externalDue:'2026-01-15',notes:'PIS package status sent to AE on 12/4',etc:''},
      {id:'cr2',complete:false,task:'3rd Capital Contribution',responsible:'CH',internalDue:'',externalDue:'2025-12-01',notes:'will need title update to include LURA, and final survey',etc:'only need perm loan increase waiver from JP'},
      {id:'cr3',complete:true,task:'Construction Loan Maturity',responsible:'',internalDue:'',externalDue:'2026-02-21',notes:'loan matures on 2/21/2026',etc:'extending by 3 months'},
      {id:'cr4',complete:true,task:'Cost Cert RFI',responsible:'CH/AE',internalDue:'',externalDue:'2026-02-19',notes:'sent responses back on 2/17',etc:''}
    ]},
    'Residence at Green Meadow': {status:'Construction',tasks:[
      {id:'gm1',complete:true,task:'Perm Insurance',responsible:'CH',internalDue:'',externalDue:'',notes:'just need final bound certs for owner perm insurance',etc:''},
      {id:'gm2',complete:false,task:'Cost Cert - DOZ',responsible:'CH',internalDue:'',externalDue:'2026-02-01',notes:'sent most recent dd on 1/20',etc:''},
      {id:'gm3',complete:false,task:'Completion Equity',responsible:'CH',internalDue:'',externalDue:'2026-02-20',notes:"survey to be delivered by 2/13, DDE ordered, need final CO's",etc:''}
    ]},
    'Reserves at Magnolia': {status:'Construction',tasks:[
      {id:'mag1',complete:true,task:'Projection updates on per draw basis',responsible:'CH',internalDue:'',externalDue:'2026-01-30',notes:'',etc:''},
      {id:'mag2',complete:true,task:'Interior Design',responsible:'AE',internalDue:'',externalDue:'2025-12-08',notes:'FFE reselections for Wayfair',etc:''},
      {id:'mag3',complete:true,task:'Cost Cert DD',responsible:'CH',internalDue:'',externalDue:'2025-12-15',notes:'all dd uploaded for Cale',etc:''},
      {id:'mag4',complete:false,task:'Completion Equity',responsible:'CH',internalDue:'',externalDue:'2025-12-31',notes:'final inspection report, soils report, affidavit of completion, estoppels, DDE, cost cert review',etc:''},
      {id:'mag5',complete:true,task:'Extension Request',responsible:'AE',internalDue:'',externalDue:'2025-12-01',notes:'',etc:''},
      {id:'mag6',complete:false,task:'LURA',responsible:'CH',internalDue:'',externalDue:'2026-03-16',notes:'would like to get recorded before PIS deadline of 4/30',etc:''},
      {id:'mag7',complete:true,task:'FFE install',responsible:'AE',internalDue:'',externalDue:'2026-01-19',notes:'scheduled for 1/19',etc:''}
    ]},
    'Landmark 301': {status:'Lease-Up',tasks:[
      {id:'l3011',complete:true,task:'Cost Cert - RFI',responsible:'CH',internalDue:'',externalDue:'2026-01-15',notes:'we should have update by EOW 2/27',etc:''}
    ]},
    'Residence at Red Cedar': {status:'Post-Award',tasks:[
      {id:'rc1',complete:true,task:'10% Test - Due Date Extension',responsible:'CH',internalDue:'',externalDue:'2025-10-31',notes:'Extension approved through 12/19/2025',etc:''},
      {id:'rc2',complete:true,task:'Force majeure request documentation',responsible:'AE/CH',internalDue:'',externalDue:'2025-12-01',notes:'',etc:''},
      {id:'rc3',complete:false,task:'AHP Grant Application',responsible:'AE',internalDue:'',externalDue:'2026-04-30',notes:'get email out to group',etc:''}
    ]},
    'Roosevelt Lofts': {status:'Construction',tasks:[
      {id:'rl1',complete:false,task:'Vending Machines',responsible:'AE/CH',internalDue:'',externalDue:'2025-10-31',notes:'',etc:''},
      {id:'rl2',complete:true,task:'Soft Cost draw',responsible:'AE',internalDue:'',externalDue:'2026-01-15',notes:'property taxes, MN',etc:''},
      {id:'rl3',complete:true,task:'Part III',responsible:'AE',internalDue:'',externalDue:'2025-12-01',notes:'check in on timing or latest from Ellis',etc:''},
      {id:'rl4',complete:true,task:'Cost Cert - PIS Package',responsible:'CH',internalDue:'',externalDue:'2026-01-15',notes:'down to a short list of 3 items as of 12/22',etc:'budget, $500 fee waiver, LBP abatement documentation'},
      {id:'rl5',complete:false,task:'Stabilization due diligence',responsible:'AE/CH',internalDue:'',externalDue:'2026-01-12',notes:'DCR report and DDE',etc:''},
      {id:'rl6',complete:false,task:'Equity Gap solve',responsible:'AE',internalDue:'',externalDue:'',notes:'Pending comments from TDHCA RFI',etc:''}
    ]},
    'Santa Fe Place': {status:'Post-Award',tasks:[]}
  },
  milestones: {
    '2024': {
      'September':[{id:'ms24s1',complete:true,development:'Clifton Riverside',milestone:"Builder's Risk",dueDate:'2024-09-27',responsible:'CH',notes:"Lydia sending us invoices 9/19"},{id:'ms24s2',complete:true,development:'Green Meadow',milestone:'Commitment Notice Due Diligence',dueDate:'2024-09-25',responsible:'AE',notes:'PDL draw submitted and sent to TDHCA'},{id:'ms24s3',complete:true,development:'Red Cedar',milestone:'Commitment Notice Due Diligence',dueDate:'2024-09-25',responsible:'CH',notes:''}],
      'October':[{id:'ms24o1',complete:true,development:'Landmark at Abilene',milestone:'FFE',dueDate:'2024-10-08',responsible:'AE',notes:''},{id:'ms24o2',complete:true,development:'Santa Fe Place',milestone:'Amendment Submission to TDHCA',dueDate:'2024-10-28',responsible:'AE',notes:''},{id:'ms24o3',complete:true,development:'Red Cedar',milestone:'Amendment Submission to TDHCA',dueDate:'2024-10-28',responsible:'CH',notes:''}],
      'November':[{id:'ms24n1',complete:true,development:'Clifton Riverside',milestone:'Cost Cert',dueDate:'2024-11-29',responsible:'CH',notes:'Need docs 2 weeks prior to release date'},{id:'ms24n2',complete:true,development:'Ridgehill',milestone:'RFI #1 Responses due to TDHCA',dueDate:'2024-11-11',responsible:'AE',notes:''},{id:'ms24n3',complete:true,development:'Landmark 601',milestone:'City Council Meeting',dueDate:'2024-11-13',responsible:'AE',notes:'Council meeting to see if they list.'}],
      'December':[{id:'ms24d1',complete:true,development:'Ridgehill',milestone:'Recorded LURA',dueDate:'2024-12-31',responsible:'CH',notes:''},{id:'ms24d2',complete:true,development:'Landmark 301',milestone:'Recorded LURA',dueDate:'2024-12-31',responsible:'CH',notes:''},{id:'ms24d3',complete:true,development:'Clifton Riverside',milestone:'Construction completion due diligence',dueDate:'2024-12-31',responsible:'AE/CH',notes:'In Progress'}]
    },
    '2025': {
      'January':[{id:'ms25j1',complete:true,development:'Ridgehill',milestone:'Cost Cert due to TDHCA',dueDate:'2025-01-15',responsible:'AE',notes:''},{id:'ms25j2',complete:true,development:'Holdsworth',milestone:'Cost Cert due to TDHCA',dueDate:'2025-01-15',responsible:'AE',notes:'followed up with Novo 12/13'},{id:'ms25j3',complete:false,development:'Clifton Riverside',milestone:'Completion Equity',dueDate:'2025-01-01',responsible:'AE/CH',notes:''}],
      'February':[{id:'ms25f1',complete:true,development:'TX 2025',milestone:'Applications due',dueDate:'2025-02-28',responsible:'AE/CH',notes:''},{id:'ms25f2',complete:true,development:'Clifton Riverside',milestone:'Construction Loan Maturity & Extension',dueDate:'2025-02-21',responsible:'AE/CH',notes:'Paying down $6,877,223 - requested on 2/21'},{id:'ms25f3',complete:true,development:'Ridgehill',milestone:'Conversion',dueDate:'2025-02-28',responsible:'AE',notes:''}],
      'March':[{id:'ms25mr1',complete:false,development:'Clifton Riverside',milestone:'Finalize Cost Cert with Novo',dueDate:'2025-03-31',responsible:'CH',notes:'will push because of LURA'},{id:'ms25mr2',complete:true,development:'Landmark 301',milestone:'Novo Award Nomination',dueDate:'2025-03-05',responsible:'CH',notes:'submitted 3/5'},{id:'ms25mr3',complete:true,development:'Landmark 301',milestone:'Part III/Part C',dueDate:'2025-03-15',responsible:'AE',notes:'received part C cert 3/11'}],
      'April':[{id:'ms25a1',complete:true,development:'Clifton Riverside',milestone:'N/A - DCR Report Engagement',dueDate:'2025-04-30',responsible:'AE/CH',notes:'May, June, July. Engage Novo and AM for stabilization workbook'},{id:'ms25a2',complete:true,development:'Landmark 301',milestone:'State Historic Equity',dueDate:'2025-04-30',responsible:'AE',notes:'Submitted to comptroller on 4/8'},{id:'ms25a3',complete:false,development:'Santa Fe Place',milestone:'Executed debt & equity LOIs',dueDate:'2025-04-30',responsible:'AE',notes:''}],
      'May':[{id:'ms25my1',complete:false,development:'Clifton Riverside',milestone:'Submit Cost Cert App to TDHCA',dueDate:'2025-05-30',responsible:'CH',notes:'*Need LURA'},{id:'ms25my2',complete:false,development:'Landmark 301',milestone:'Submit Cost Cert App to TDHCA',dueDate:'2025-05-30',responsible:'CH',notes:'pending as-built survey timing'},{id:'ms25my3',complete:false,development:'Red Cedar',milestone:'Executed debt & equity LOIs',dueDate:'2025-05-30',responsible:'AE',notes:'may by May - TBD'}],
      'June':[{id:'ms25jn1',complete:true,development:'TX 2025',milestone:'PDL Sizing to Tish',dueDate:'2025-06-09',responsible:'AE/CH',notes:'Land costs, reservation fees, S. Anderson fees, JGR billing'},{id:'ms25jn2',complete:true,development:'Roosevelt Lofts',milestone:'LURA Origination Submission',dueDate:'2025-06-30',responsible:'CH',notes:''},{id:'ms25jn3',complete:true,development:'Landmark at Abilene',milestone:'Charles L. Edson Award Nomination',dueDate:'2025-06-10',responsible:'CH',notes:'Working with MHEG'}],
      'July':[{id:'ms25jl1',complete:true,development:'Roosevelt Lofts',milestone:'Construction Completion Equity',dueDate:'2025-07-15',responsible:'AE/CH',notes:''},{id:'ms25jl2',complete:true,development:'TX 2025',milestone:'Award Notification',dueDate:'2025-07-24',responsible:'AE/CH',notes:'FYI only'},{id:'ms25jl3',complete:true,development:'TX 2025',milestone:'Entity formations',dueDate:'2025-07-15',responsible:'CH',notes:'With Amanda and Winthrop'}],
      'August':[{id:'ms25au1',complete:true,development:'Magnolia',milestone:'BR/GL Extension',dueDate:'2025-08-01',responsible:'AE',notes:'Current expires on 8/6'},{id:'ms25au2',complete:true,development:'Landmark at Abilene',milestone:'THC Awards',dueDate:'2025-08-15',responsible:'CH',notes:''},{id:'ms25au3',complete:true,development:'Landmark 301',milestone:'THC Awards',dueDate:'2025-08-15',responsible:'CH',notes:''}],
      'September':[{id:'ms25se1',complete:true,development:'TX 2025',milestone:'Commitment Notice Due Diligence',dueDate:'2025-09-25',responsible:'CH',notes:'Due 9/26'},{id:'ms25se2',complete:true,development:'Landmark 601',milestone:'Land Closing',dueDate:'2025-09-30',responsible:'AE/CH',notes:'Final, after all extensions'},{id:'ms25se3',complete:true,development:'Landmark on Cypress',milestone:'Land Closing',dueDate:'2025-09-30',responsible:'',notes:''}],
      'October':[{id:'ms25oc1',complete:true,development:'Landmark 301',milestone:'TDHCA Cost Cert',dueDate:'2025-10-15',responsible:'AE/CH',notes:'Submitted to TDHCA on 10/14'},{id:'ms25oc2',complete:true,development:'TX 2025',milestone:'Carryovers from TDHCA',dueDate:'2025-10-30',responsible:'AE/CH',notes:'FYI only'}],
      'November':[{id:'ms25no1',complete:false,development:'Roosevelt Lofts',milestone:'Cost Cert Application Submission',dueDate:'2025-11-30',responsible:'CH',notes:'Meredith is working on our documents now'},{id:'ms25no2',complete:true,development:'Landmark at Abilene',milestone:'TDHCA Cost Cert',dueDate:'2025-11-15',responsible:'CH',notes:'Submitted on 11/25!!'}],
      'December':[{id:'ms25de1',complete:true,development:'Clifton Riverside',milestone:'Final LURA due',dueDate:'2025-12-31',responsible:'CH',notes:''},{id:'ms25de2',complete:true,development:'Landmark at Abilene',milestone:'Final LURA due',dueDate:'2025-12-31',responsible:'CH',notes:''},{id:'ms25de3',complete:true,development:'Landmark at Abilene',milestone:'Construction loan maturity date',dueDate:'2025-12-15',responsible:'AE',notes:''}]
    },
    '2026': {
      'January':[{id:'ms26j1',complete:true,development:'TX 2026',milestone:'Pre-Applications Due',dueDate:'2026-01-09',responsible:'AE/CH',notes:''},{id:'ms26j2',complete:true,development:'Green Meadow',milestone:'TDHCA Quarterly Reporting',dueDate:'2026-01-10',responsible:'CH',notes:''},{id:'ms26j3',complete:true,development:'Magnolia',milestone:'TDHCA Quarterly Reporting',dueDate:'2026-01-10',responsible:'CH',notes:''}],
      'February':[{id:'ms26f1',complete:false,development:'TX 2026',milestone:'Applications Due',dueDate:'2026-02-27',responsible:'AE/CH',notes:''},{id:'ms26f2',complete:false,development:'TX 2026',milestone:'Centennial Park Lofts - City Council Meeting',dueDate:'2026-02-24',responsible:'AE/CH',notes:'Midland'},{id:'ms26f3',complete:true,development:'Green Meadow',milestone:'Completion Equity',dueDate:'2026-02-20',responsible:'AE/CH',notes:''}],
      'March':[{id:'ms26mr1',complete:false,development:'Irving Lofts',milestone:'Closing',dueDate:'2026-03-03',responsible:'AE/CH',notes:''},{id:'ms26mr2',complete:false,development:'Magnolia',milestone:'Record LURA',dueDate:'2026-03-31',responsible:'',notes:''},{id:'ms26mr3',complete:false,development:'Green Meadow',milestone:'Record LURA',dueDate:'2026-03-31',responsible:'',notes:''}],
      'April':[{id:'ms26a1',complete:false,development:'Landmark 301',milestone:'Construction loan maturity date',dueDate:'2026-04-01',responsible:'AE',notes:''},{id:'ms26a2',complete:false,development:'Other',milestone:'Quarterly construction monitoring report',dueDate:'2026-04-10',responsible:'CH',notes:''},{id:'ms26a3',complete:false,development:'Red Cedar',milestone:'AHP application',dueDate:'2026-04-30',responsible:'',notes:''}],
      'May':[{id:'ms26my1',complete:false,development:'Red Cedar',milestone:'Pre-dev loan matures',dueDate:'2026-05-31',responsible:'',notes:''},{id:'ms26my2',complete:false,development:'Landmark on Pine',milestone:'Closing',dueDate:'2026-05-15',responsible:'',notes:''},{id:'ms26my3',complete:false,development:'TX 2026',milestone:'The Lenora - RHDA application due',dueDate:'2026-05-01',responsible:'',notes:''}],
      'June':[{id:'ms26jn1',complete:false,development:'Landmark at Abilene',milestone:'Construction loan matures',dueDate:'2026-06-15',responsible:'',notes:''},{id:'ms26jn2',complete:false,development:'Irving Lofts',milestone:'10% test',dueDate:'2026-07-01',responsible:'',notes:''},{id:'ms26jn3',complete:false,development:'Landmark on Cypress',milestone:'10% test',dueDate:'2026-07-01',responsible:'',notes:''}],
      'July':[{id:'ms26jl1',complete:false,development:'Landmark 601',milestone:'Closing',dueDate:'2026-07-31',responsible:'',notes:''},{id:'ms26jl2',complete:false,development:'Green Meadow',milestone:'Stabilization',dueDate:'2026-07-15',responsible:'',notes:'per LPA'},{id:'ms26jl3',complete:false,development:'Irving Lofts',milestone:'10% test',dueDate:'2026-07-01',responsible:'',notes:''}],
      'August':[{id:'ms26au1',complete:false,development:'TX 2026',milestone:'Contract extensions',dueDate:'',responsible:'',notes:''},{id:'ms26au2',complete:false,development:'TX 2026',milestone:'Acquisition Loan',dueDate:'',responsible:'',notes:''},{id:'ms26au3',complete:false,development:'TX 2026',milestone:'PDL originations',dueDate:'',responsible:'',notes:''}],
      'September':[{id:'ms26se1',complete:false,development:'TX 2026',milestone:'Commitment Notices',dueDate:'',responsible:'',notes:''},{id:'ms26se2',complete:false,development:'TX 2026',milestone:'Lucas Lofts - Rezoning Approval',dueDate:'',responsible:'',notes:''},{id:'ms26se3',complete:false,development:'TX 2026',milestone:'The Lenora - Rezoning Approval',dueDate:'',responsible:'',notes:''}],
      'October':[{id:'ms26oc1',complete:false,development:'Other',milestone:'Quarterly construction monitoring report',dueDate:'2026-10-10',responsible:'',notes:''}],
      'December':[{id:'ms26de1',complete:false,development:'TX 2026',milestone:'Lucas Lofts - Closing',dueDate:'2026-12-31',responsible:'',notes:''},{id:'ms26de2',complete:false,development:'Green Meadow',milestone:'LURA due',dueDate:'2026-12-31',responsible:'',notes:''},{id:'ms26de3',complete:false,development:'Magnolia',milestone:'LURA due',dueDate:'2026-12-31',responsible:'',notes:''}]
    }
  },
  debtEquity: {
    equity:[
      {deal:'Landmark on Cypress',investor:'MHEG',pricing:'0.83',notes:'LOI Executed'},
      {deal:'Landmark on Pine',investor:'RJ',pricing:'0.8275',notes:'LOI executed, dd underway'},
      {deal:'Irving Lofts',investor:'MHEG',pricing:'0.83',notes:'LOI executed, dd underway'},
      {deal:'Landmark 601',investor:'Berkadia',pricing:'TBD',notes:'sent 8/28'},
      {deal:'Landmark 601',investor:'Wells',pricing:'0.88',notes:'being squirrly'},
      {deal:'Landmark 601',investor:'RJ',pricing:'0.83',notes:'pricing too low'},
      {deal:'Landmark 601',investor:'US Bank',pricing:'0.83',notes:'pricing too low'}
    ],
    preDev:[
      {deal:'Landmark on Cypress',acqLender:'TSAHC',pdlLender:'MHDF',pdlClosing:'2025-09-30',acqClosing:'2025-09-30'},
      {deal:'Landmark 601',acqLender:'Horizon',pdlLender:'Horizon',pdlClosing:'2025-09-11',acqClosing:'2025-09-30'},
      {deal:'Irving Lofts',acqLender:'TSAHC',pdlLender:'Legacy',pdlClosing:'',acqClosing:'2025-09-22'},
      {deal:'Landmark on Pine',acqLender:'TSAHC',pdlLender:'Horizon',pdlClosing:'2025-09-30',acqClosing:'2025-12-17'}
    ]
  },
  planning: [
    {id:'pl1',complete:false,task:'Application Season - Debrief',category:'To Do',notes:'Any changes / tweaks to workflow or due diligence'},
    {id:'pl2',complete:true,task:'AE - arch plans, proformas, feasibility reports, site plans, surveys (filing)',category:'To Do',notes:'Clean up/filing'},
    {id:'pl3',complete:true,task:'CM - appraisals, PMAs, phase 1s (filing)',category:'To Do',notes:''},
    {id:'pl4',complete:false,task:'Talk to Matt/Tish about a set amount for JGR application work ($50k?)',category:'Ahead of Next Round',notes:''},
    {id:'pl5',complete:false,task:'Talk to Matt about Sarah / Wayne billing & timing',category:'Ahead of Next Round',notes:''},
    {id:'pl6',complete:false,task:'Pre-dev budget prep ahead of season start',category:'Ahead of Next Round',notes:'AE to find old email/draw workbook she sent for app planning'},
    {id:'pl7',complete:false,task:'Work on an OPG pitch deck/resume (tailor to land owners)',category:'Ahead of Next Round',notes:'timeline, awards, articles, reference letters'},
    {id:'pl8',complete:false,task:'Feasibility Report review / synopsis for MCP',category:'2025 Planning',notes:'either synopsis or group meeting'},
    {id:'pl9',complete:false,task:'Preservation memo review / synopsis for MCP',category:'2025 Planning',notes:'either synopsis or group meeting'},
    {id:'pl10',complete:false,task:'Phase Engineering Scope of Work - review',category:'2025 Planning',notes:'probably something to run by MCP, too'},
    {id:'pl11',complete:true,task:'Annual awards schedule (THC, Novo, HUD) - map out all',category:'2025 Planning',notes:'THC Award Homepage (spring 2025)'},
    {id:'pl12',complete:false,task:'Red Cedar Closing - assign due diligence',category:'2025 Planning',notes:"We'll review due diligence responsibilities before starting"},
    {id:'pl13',complete:false,task:'Santa Fe Place Closing - assign due diligence',category:'2025 Planning',notes:''},
    {id:'pl14',complete:true,task:'Next steps with new deals',category:'2025 Planning',notes:'Meeting scheduled 3/26'},
    {id:'pl15',complete:false,task:'Cost Cert Applications - make assignments',category:'2025 Planning',notes:'Caroline to go through and make assignments, April to update notification settings'},
    {id:'pl16',complete:true,task:'Commitment Notice due diligence checklist',category:'2025 Planning',notes:'Checklist on DP'},
    {id:'pl17',complete:false,task:'Map out remaining year on priorities checklists',category:'2025 Planning',notes:'Maturity dates, commitment notice due diligence/carryovers, 10% tests, cost certs, LURAs, AHP application, etc.'},
    {id:'pl18',complete:false,task:'Any/all historic or local grants/funding',category:'2025 Planning',notes:'Texas Preservation Grant, AHP Grant, downtown Abilene facade grant, Texarkana partial tax abatement, EPA low interest loans'},
    {id:'pl19',complete:true,task:'All final land closing dates after extensions',category:'2025 Planning',notes:'Added to monthly tabs'},
    {id:'pl20',complete:true,task:'Any applicable conferences - mapped on monthly tabs',category:'2025 Planning',notes:'Novo historic tax credit conference, Texas Municipality League conference in October, THC Real Places conference in April, Texas Downtown Conference'},
    {id:'pl21',complete:true,task:'Lucas Lofts - Wichita Falls',category:'TX 2026',notes:'ISD Bids - due 8/5/2025'}
  ]
};

// STATE
let data = null;
let view = 'dashboard';
let milestoneYear = '2026';
let dealFilter = 'All';
let dealSearch = '';
let modalCtx = {};
let syncTimer = null;

const KEY = 'tx-priorities-v3';

async function loadData() {
  setSyncStatus('syncing');
  try {
    const r = await window.storage.get(KEY, true);
    data = r && r.value ? JSON.parse(r.value) : JSON.parse(JSON.stringify(SEED));
    if (!r || !r.value) await saveData();
    setSyncStatus('synced');
  } catch(e) {
    data = JSON.parse(JSON.stringify(SEED));
    setSyncStatus('error');
  }
}

async function saveData() {
  setSyncStatus('syncing');
  clearTimeout(syncTimer);
  syncTimer = setTimeout(async () => {
    try {
      await window.storage.set(KEY, JSON.stringify(data), true);
      setSyncStatus('synced');
    } catch(e) {
      setSyncStatus('error');
      toast('Sync error', 'error');
    }
  }, 500);
}

function setSyncStatus(s) {
  const d = document.getElementById('syncDot');
  const l = document.getElementById('syncLabel');
  if (!d) return;
  d.className = 'sync-dot' + (s !== 'synced' ? ' ' + s : '');
  l.textContent = s === 'syncing' ? 'saving…' : s === 'error' ? 'error' : 'synced';
}

function uid() { return '_' + Math.random().toString(36).slice(2,9); }

function fmtDate(d) {
  if (!d) return '';
  const dt = new Date(d + 'T12:00:00');
  return dt.toLocaleDateString('en-US',{month:'short',day:'numeric',year:'2-digit'});
}

function dcls(d, done) {
  if (!d) return 'date-cell';
  if (done) return 'date-cell done-date';
  const diff = (new Date(d+'T12:00:00') - new Date()) / 86400000;
  if (diff < 0) return 'date-cell overdue';
  if (diff < 14) return 'date-cell soon';
  return 'date-cell';
}

function rcls(r) {
  if (!r) return 'responsible-chip';
  const u = r.toUpperCase();
  if (u.includes('AE') && u.includes('CH')) return 'responsible-chip both';
  if (u.includes('AE')) return 'responsible-chip ae';
  if (u.includes('CH')) return 'responsible-chip ch';
  return 'responsible-chip';
}

function sbadge(status) {
  const m = {Construction:'construction','Post-Award':'post-award','Lease-Up':'lease-up'};
  return `<span class="deal-badge ${m[status]||''}">${status||''}</span>`;
}

function toast(msg, type='') {
  const c = document.getElementById('toastContainer');
  const t = document.createElement('div');
  t.className = 'toast '+type; t.textContent = msg; c.appendChild(t);
  setTimeout(() => t.remove(), 3000);
}

function e(id) { return document.getElementById(id); }

function showView(v) {
  view = v;
  const btns = document.querySelectorAll('.nav-btn');
  btns.forEach(b => b.classList.remove('active'));
  const idx = {dashboard:0,priorities:1,deals:2,milestones:3,debt:4,planning:5};
  btns[idx[v] ?? 0]?.classList.add('active');
  render();
}

function render() {
  const c = e('mainContent');
  if (!data) { c.innerHTML = '<div class="empty-state"><div class="icon">⏳</div><p>Loading…</p></div>'; return; }
  const r = {dashboard:rDashboard,priorities:rPriorities,deals:rDeals,milestones:rMilestones,debt:rDebt,planning:rPlanning};
  c.innerHTML = (r[view]||rDashboard)();
  document.onkeydown = ev => { if (ev.key==='Escape') closeModal(); };
}

// DASHBOARD
function rDashboard() {
  const allT = Object.values(data.deals).flatMap(d => d.tasks);
  const allM = Object.values(data.milestones).flatMap(yr => Object.values(yr)).flat();
  const tot = allT.length + data.topPriorities.length + data.planning.length;
  const done = allT.filter(t=>t.complete).length + data.topPriorities.filter(t=>t.complete).length + data.planning.filter(t=>t.complete).length;
  const pct = tot ? Math.round(done/tot*100) : 0;
  const now = new Date();
  const upcoming = allM.filter(m=>!m.complete && m.dueDate && new Date(m.dueDate+'T12:00:00')>now).sort((a,b)=>new Date(a.dueDate)-new Date(b.dueDate)).slice(0,8);
  const overdue = allM.filter(m=>!m.complete && m.dueDate && new Date(m.dueDate+'T12:00:00')<now).length;
  const openDeals = Object.values(data.deals).filter(d=>d.tasks.some(t=>!t.complete)).length;
  return `
  <div class="section-header">
    <div><div class="section-title">Good morning ✦</div><div class="section-subtitle">${new Date().toLocaleDateString('en-US',{weekday:'long',month:'long',day:'numeric',year:'numeric'})}</div></div>
    <button class="btn btn-accent" onclick="openAddModal('milestone')">+ Add Milestone</button>
  </div>
  <div class="progress-bar-wrap"><div class="progress-bar-fill" style="width:${pct}%"></div></div>
  <div class="stats-row">
    <div class="stat-card"><div class="stat-value">${pct}%</div><div class="stat-label">Overall Complete</div></div>
    <div class="stat-card"><div class="stat-value" style="color:var(--accent)">${overdue}</div><div class="stat-label">Overdue Milestones</div></div>
    <div class="stat-card"><div class="stat-value">${upcoming.length}</div><div class="stat-label">Upcoming</div></div>
    <div class="stat-card"><div class="stat-value">${openDeals}</div><div class="stat-label">Active Deals</div></div>
    <div class="stat-card"><div class="stat-value">${done}</div><div class="stat-label">Tasks Done</div></div>
  </div>
  <div class="section-header" style="margin-bottom:12px"><div><strong>Upcoming Milestones</strong></div><button class="btn btn-sm" onclick="showView('milestones')">View all →</button></div>
  <div class="task-table-wrap" style="margin-bottom:24px">
    <table><thead><tr><th class="task-check"></th><th>Development</th><th>Milestone</th><th>Due Date</th><th>Responsible</th></tr></thead><tbody>
    ${upcoming.length ? upcoming.map(m=>`<tr>
      <td class="task-check"><div class="check-box ${m.complete?'checked':''}" onclick="toggleMs('${m.id}')"></div></td>
      <td><span class="milestone-dev">${m.development}</span></td>
      <td class="task-text">${m.milestone}</td>
      <td class="${dcls(m.dueDate,m.complete)}">${fmtDate(m.dueDate)}</td>
      <td>${m.responsible?`<span class="${rcls(m.responsible)}">${m.responsible}</span>`:''}</td>
    </tr>`).join('') : '<tr><td colspan="5" style="text-align:center;padding:24px;color:var(--ink-light)">No upcoming milestones</td></tr>'}
    </tbody></table>
  </div>
  <div class="section-header" style="margin-bottom:12px"><div><strong>Top Priorities</strong></div><button class="btn btn-sm" onclick="showView('priorities')">View all →</button></div>
  ${rTopPrioritiesTable(data.topPriorities.slice(0,6))}`;
}

// TOP PRIORITIES
function rPriorities() {
  const done = data.topPriorities.filter(t=>t.complete).length;
  const pct = data.topPriorities.length ? Math.round(done/data.topPriorities.length*100) : 0;
  return `
  <div class="section-header">
    <div><div class="section-title">Top Priorities</div><div class="section-subtitle">${done}/${data.topPriorities.length} complete • ${pct}%</div></div>
    <button class="btn btn-accent" onclick="openAddModal('topPriority')">+ Add Priority</button>
  </div>
  <div class="progress-bar-wrap"><div class="progress-bar-fill" style="width:${pct}%"></div></div>
  ${rTopPrioritiesTable(data.topPriorities)}`;
}

function rTopPrioritiesTable(items) {
  return `<div class="task-table-wrap"><table>
  <thead><tr><th class="task-check"></th><th>Task / Deal</th><th>Notes</th><th>Out of Office</th><th></th></tr></thead>
  <tbody>
  ${items.map(t=>`<tr>
    <td class="task-check"><div class="check-box ${t.complete?'checked':''}" onclick="toggleTP('${t.id}')"></div></td>
    <td><span class="task-text ${t.complete?'done':''}" contenteditable="true" onblur="editTP('${t.id}','task',this.textContent.trim())">${t.task}</span></td>
    <td><span class="task-notes" contenteditable="true" onblur="editTP('${t.id}','notes',this.textContent.trim())">${t.notes}</span></td>
    <td><span class="task-notes" contenteditable="true" onblur="editTP('${t.id}','ooo',this.textContent.trim())">${t.ooo||''}</span></td>
    <td><button class="btn btn-sm btn-icon" style="color:var(--ink-light)" onclick="delTP('${t.id}')">✕</button></td>
  </tr>`).join('')}
  <tr class="add-row"><td colspan="5"><button class="add-btn-inline" onclick="openAddModal('topPriority')">+ Add priority</button></td></tr>
  </tbody></table></div>`;
}

// DEALS
function rDeals() {
  const deals = Object.entries(data.deals);
  const statuses = ['All',...new Set(deals.map(([,d])=>d.status).filter(Boolean))];
  const filtered = deals.filter(([name,d]) => {
    if (dealFilter !== 'All' && d.status !== dealFilter) return false;
    if (dealSearch && !name.toLowerCase().includes(dealSearch.toLowerCase())) return false;
    return true;
  });
  return `
  <div class="section-header">
    <div><div class="section-title">Deals</div><div class="section-subtitle">${deals.length} deals tracked</div></div>
    <button class="btn btn-accent" onclick="openAddModal('deal')">+ Add Deal</button>
  </div>
  <div class="filter-bar">
    ${statuses.map(s=>`<button class="filter-chip ${s===dealFilter?'active':''}" onclick="setDF('${s}')">${s}</button>`).join('')}
    <input class="search-input" type="text" placeholder="Search deals…" value="${dealSearch}" oninput="setDS(this.value)">
  </div>
  ${filtered.map(([n,d])=>rDealTable(n,d)).join('')}
  ${!filtered.length?'<div class="empty-state"><div class="icon">🔍</div><p>No deals match filter.</p></div>':''}`;
}

function rDealTable(name, d) {
  const done = d.tasks.filter(t=>t.complete).length;
  const pct = d.tasks.length ? Math.round(done/d.tasks.length*100) : 0;
  return `<div class="task-table-wrap">
  <div class="task-table-title">
    <h3>${name} ${sbadge(d.status)}</h3>
    <div style="display:flex;gap:8px;align-items:center">
      <span style="font-size:11px;color:var(--ink-light)">${done}/${d.tasks.length} • ${pct}%</span>
      <button class="btn btn-sm btn-accent" onclick="openAddModal('dealTask','${name}')">+ Task</button>
    </div>
  </div>
  <div class="progress-bar-wrap" style="margin:0;border-radius:0"><div class="progress-bar-fill" style="width:${pct}%"></div></div>
  <table><thead><tr>
    <th class="task-check"></th><th>Task</th><th>Responsible</th>
    <th>Internal Due</th><th>External Due</th><th>Notes</th><th></th>
  </tr></thead><tbody>
  ${d.tasks.map(t=>`<tr>
    <td class="task-check"><div class="check-box ${t.complete?'checked':''}" onclick="toggleDT('${name}','${t.id}')"></div></td>
    <td>
      <span class="task-text ${t.complete?'done':''}" contenteditable="true" onblur="editDT('${name}','${t.id}','task',this.textContent.trim())">${t.task}</span>
      ${t.etc?`<div class="task-notes">${t.etc}</div>`:''}
    </td>
    <td>${t.responsible?`<span class="${rcls(t.responsible)}">${t.responsible}</span>`:'<span class="task-notes">—</span>'}</td>
    <td class="${dcls(t.internalDue,t.complete)}">${fmtDate(t.internalDue)||'—'}</td>
    <td class="${dcls(t.externalDue,t.complete)}">${fmtDate(t.externalDue)||'—'}</td>
    <td><span class="task-notes" contenteditable="true" onblur="editDT('${name}','${t.id}','notes',this.textContent.trim())">${t.notes||''}</span></td>
    <td><button class="btn btn-sm btn-icon" style="color:var(--ink-light)" onclick="delDT('${name}','${t.id}')">✕</button></td>
  </tr>`).join('')}
  <tr class="add-row"><td colspan="7"><button class="add-btn-inline" onclick="openAddModal('dealTask','${name}')">+ Add task</button></td></tr>
  </tbody></table></div>`;
}

function setDF(f) { dealFilter=f; render(); }
function setDS(v) { dealSearch=v; render(); }

// MILESTONES
function rMilestones() {
  const months = ['January','February','March','April','May','June','July','August','September','October','November','December'];
  const yrData = data.milestones[milestoneYear] || {};
  return `
  <div class="section-header">
    <div><div class="section-title">Monthly Milestones</div><div class="section-subtitle">Track deal milestones by month</div></div>
    <div style="display:flex;gap:8px">
      <div class="year-tabs">
        ${['2024','2025','2026'].map(y=>`<button class="year-tab ${y===milestoneYear?'active':''}" onclick="setMY('${y}')">${y}</button>`).join('')}
      </div>
      <button class="btn btn-accent" onclick="openAddModal('milestone')">+ Add</button>
    </div>
  </div>
  <div class="month-grid">
  ${months.map(m => {
    const items = yrData[m] || [];
    if (!items.length) return '';
    const done = items.filter(i=>i.complete).length;
    return `<div class="month-card">
      <div class="month-card-header" onclick="toggleMC('${m}${milestoneYear}')">
        <h3>${m}</h3>
        <span class="count">${done}/${items.length} <span id="ci_${m}${milestoneYear}">▶</span></span>
      </div>
      <div class="month-card-body" id="mb_${m}${milestoneYear}">
        ${items.map(item=>`<div class="milestone-row">
          <div class="check-box ${item.complete?'checked':''}" style="flex-shrink:0;margin-top:2px" onclick="toggleMs('${item.id}')"></div>
          <div class="milestone-content">
            <div class="milestone-title ${item.complete?'done':''}" contenteditable="true" onblur="editMs('${item.id}','milestone',this.textContent.trim())">${item.milestone}</div>
            <div class="milestone-meta">
              <span class="milestone-dev">${item.development}</span>
              ${item.dueDate?`<span class="${dcls(item.dueDate,item.complete)}" style="font-size:10px">${fmtDate(item.dueDate)}</span>`:''}
              ${item.responsible?`<span class="${rcls(item.responsible)}" style="font-size:10px">${item.responsible}</span>`:''}
            </div>
            ${item.notes?`<div class="task-notes" style="margin-top:3px">${item.notes}</div>`:''}
          </div>
          <button class="btn btn-sm btn-icon" style="color:var(--ink-light);flex-shrink:0" onclick="delMs('${item.id}')">✕</button>
        </div>`).join('')}
        <div style="padding:6px 16px"><button class="add-btn-inline" onclick="openAddModal('msMonth','${m}','${milestoneYear}')">+ Add milestone</button></div>
      </div>
    </div>`;
  }).filter(Boolean).join('')}
  </div>`;
}

function setMY(y) { milestoneYear=y; render(); }
function toggleMC(id) {
  const b = e('mb_'+id), ci = e('ci_'+id);
  if (!b) return;
  b.style.display = b.style.display==='none' ? '' : 'none';
}

// DEBT & EQUITY
function rDebt() {
  const de = data.debtEquity;
  const byDeal = {};
  de.equity.forEach(eq => { if (!byDeal[eq.deal]) byDeal[eq.deal]=[]; byDeal[eq.deal].push(eq); });
  return `
  <div class="section-header">
    <div><div class="section-title">Debt &amp; Equity Tracking</div><div class="section-subtitle">Capital stack overview by deal</div></div>
  </div>
  <div class="tab-strip">
    <button class="tab active" onclick="showDETab('equity',this)">Equity</button>
    <button class="tab" onclick="showDETab('predev',this)">Pre-Dev Debt</button>
  </div>
  <div id="deTab_equity">
    <div class="de-grid">
    ${Object.entries(byDeal).map(([deal,invs])=>`
      <div class="de-card"><h4>${deal}</h4>
      <div class="de-row" style="font-size:10px;text-transform:uppercase;letter-spacing:0.5px;color:var(--ink-light)"><span>Investor</span><span>Pricing</span></div>
      ${invs.map(inv=>`<div class="de-row"><span class="de-label">${inv.investor}</span><span>${inv.pricing}</span></div>${inv.notes?`<div style="font-size:11px;color:var(--ink-light);padding:2px 0 4px">${inv.notes}</div>`:''}`).join('')}
      </div>
    `).join('')}
    </div>
  </div>
  <div id="deTab_predev" class="hidden">
    <div class="task-table-wrap">
      <table><thead><tr><th>Deal</th><th>Acq. Lender</th><th>PDL Lender</th><th>PDL Closing</th><th>Acq. Closing</th></tr></thead>
      <tbody>
      ${de.preDev.map(r=>`<tr>
        <td class="task-text">${r.deal}</td>
        <td class="task-notes">${r.acqLender}</td>
        <td class="task-notes">${r.pdlLender}</td>
        <td class="${dcls(r.pdlClosing,false)}">${fmtDate(r.pdlClosing)||'—'}</td>
        <td class="${dcls(r.acqClosing,false)}">${fmtDate(r.acqClosing)||'—'}</td>
      </tr>`).join('')}
      </tbody></table>
    </div>
  </div>`;
}

function showDETab(tab, btn) {
  ['equity','predev'].forEach(t=>{ const el2=e('deTab_'+t); if(el2) el2.classList.toggle('hidden',t!==tab); });
  document.querySelectorAll('.tab-strip .tab').forEach(b=>b.classList.remove('active'));
  btn.classList.add('active');
}

// PLANNING
function rPlanning() {
  const cats = [...new Set(data.planning.map(p=>p.category))];
  return `
  <div class="section-header">
    <div><div class="section-title">Planning</div><div class="section-subtitle">Strategy, workflow, and future initiatives</div></div>
    <button class="btn btn-accent" onclick="openAddModal('planningItem')">+ Add Item</button>
  </div>
  ${cats.map(cat => {
    const items = data.planning.filter(p=>p.category===cat);
    const done = items.filter(p=>p.complete).length;
    return `<div class="task-table-wrap" style="margin-bottom:16px">
    <div class="task-table-title"><h3>${cat}</h3><span style="font-size:11px;color:var(--ink-light)">${done}/${items.length}</span></div>
    <table><thead><tr><th class="task-check"></th><th>Task</th><th>Notes</th><th></th></tr></thead>
    <tbody>
    ${items.map(p=>`<tr>
      <td class="task-check"><div class="check-box ${p.complete?'checked':''}" onclick="togglePL('${p.id}')"></div></td>
      <td><span class="task-text ${p.complete?'done':''}" contenteditable="true" onblur="editPL('${p.id}','task',this.textContent.trim())">${p.task}</span></td>
      <td><span class="task-notes" contenteditable="true" onblur="editPL('${p.id}','notes',this.textContent.trim())">${p.notes||''}</span></td>
      <td><button class="btn btn-sm btn-icon" style="color:var(--ink-light)" onclick="delPL('${p.id}')">✕</button></td>
    </tr>`).join('')}
    <tr class="add-row"><td colspan="4"><button class="add-btn-inline" onclick="openAddModal('planningItem','${cat}')">+ Add item</button></td></tr>
    </tbody></table></div>`;
  }).join('')}`;
}

// TOGGLE / EDIT
function toggleTP(id) { const t=data.topPriorities.find(t=>t.id===id); if(t){t.complete=!t.complete;saveData();render();} }
function toggleDT(dn,id) { const t=data.deals[dn]?.tasks.find(t=>t.id===id); if(t){t.complete=!t.complete;saveData();render();} }
function toggleMs(id) { for(const yr of Object.values(data.milestones)) for(const items of Object.values(yr)){const m=items.find(m=>m.id===id);if(m){m.complete=!m.complete;saveData();render();return;}} }
function togglePL(id) { const p=data.planning.find(p=>p.id===id); if(p){p.complete=!p.complete;saveData();render();} }

function editTP(id,f,v) { const t=data.topPriorities.find(t=>t.id===id); if(t&&t[f]!==v){t[f]=v;saveData();} }
function editDT(dn,id,f,v) { const t=data.deals[dn]?.tasks.find(t=>t.id===id); if(t&&t[f]!==v){t[f]=v;saveData();} }
function editMs(id,f,v) { for(const yr of Object.values(data.milestones)) for(const items of Object.values(yr)){const m=items.find(m=>m.id===id);if(m&&m[f]!==v){m[f]=v;saveData();return;}} }
function editPL(id,f,v) { const p=data.planning.find(p=>p.id===id); if(p&&p[f]!==v){p[f]=v;saveData();} }

function delTP(id) { data.topPriorities=data.topPriorities.filter(t=>t.id!==id); saveData(); render(); }
function delDT(dn,id) { const d=data.deals[dn]; if(d){d.tasks=d.tasks.filter(t=>t.id!==id);saveData();render();} }
function delMs(id) { for(const yr of Object.values(data.milestones)) for(const [,items] of Object.entries(yr)){const i=items.findIndex(m=>m.id===id);if(i>=0){items.splice(i,1);saveData();render();return;}} }
function delPL(id) { data.planning=data.planning.filter(p=>p.id!==id); saveData(); render(); }

// MODAL
function openAddModal(type, ...args) {
  modalCtx = {type, args};
  e('modalOverlay').classList.remove('hidden');
  const titles = {topPriority:'Add Priority',dealTask:`Add Task — ${args[0]||''}`,milestone:'Add Milestone',msMonth:`Add Milestone — ${args[0]} ${args[1]}`,deal:'Add Deal',planningItem:'Add Planning Item'};
  e('modalTitle').textContent = titles[type]||'Add';
  const forms = {
    topPriority:`
      <div class="form-group"><label class="form-label">Task / Deal Name</label><input class="form-input" id="mf_task" placeholder="Task description"></div>
      <div class="form-group"><label class="form-label">Notes</label><input class="form-input" id="mf_notes" placeholder="Notes"></div>
      <div class="form-group"><label class="form-label">Out of Office</label><input class="form-input" id="mf_ooo" placeholder="e.g. AE - 2/23-24"></div>`,
    dealTask:`
      <div class="form-group"><label class="form-label">Task</label><input class="form-input" id="mf_task" placeholder="Task description"></div>
      <div class="form-group"><label class="form-label">Responsible</label><select class="form-select" id="mf_resp"><option value="">—</option><option>AE</option><option>CH</option><option>AE/CH</option></select></div>
      <div style="display:grid;grid-template-columns:1fr 1fr;gap:12px">
        <div class="form-group"><label class="form-label">Internal Due</label><input class="form-input" id="mf_intDue" type="date"></div>
        <div class="form-group"><label class="form-label">External Due</label><input class="form-input" id="mf_extDue" type="date"></div>
      </div>
      <div class="form-group"><label class="form-label">Notes</label><textarea class="form-textarea" id="mf_notes"></textarea></div>
      <div class="form-group"><label class="form-label">Etc</label><input class="form-input" id="mf_etc" placeholder="Additional info"></div>`,
    milestone:`
      <div class="form-group"><label class="form-label">Development</label><input class="form-input" id="mf_dev" placeholder="Deal name"></div>
      <div class="form-group"><label class="form-label">Milestone</label><input class="form-input" id="mf_ms" placeholder="Milestone description"></div>
      <div style="display:grid;grid-template-columns:1fr 1fr;gap:12px">
        <div class="form-group"><label class="form-label">Year</label><select class="form-select" id="mf_year"><option>2024</option><option>2025</option><option selected>2026</option></select></div>
        <div class="form-group"><label class="form-label">Month</label><select class="form-select" id="mf_month">${['January','February','March','April','May','June','July','August','September','October','November','December'].map(m=>`<option>${m}</option>`).join('')}</select></div>
      </div>
      <div class="form-group"><label class="form-label">Due Date</label><input class="form-input" id="mf_due" type="date"></div>
      <div class="form-group"><label class="form-label">Responsible</label><select class="form-select" id="mf_resp"><option value="">—</option><option>AE</option><option>CH</option><option>AE/CH</option></select></div>
      <div class="form-group"><label class="form-label">Notes</label><textarea class="form-textarea" id="mf_notes"></textarea></div>`,
    msMonth:`
      <div class="form-group"><label class="form-label">Development</label><input class="form-input" id="mf_dev" placeholder="Deal name"></div>
      <div class="form-group"><label class="form-label">Milestone</label><input class="form-input" id="mf_ms" placeholder="Milestone description"></div>
      <div class="form-group"><label class="form-label">Due Date</label><input class="form-input" id="mf_due" type="date"></div>
      <div class="form-group"><label class="form-label">Responsible</label><select class="form-select" id="mf_resp"><option value="">—</option><option>AE</option><option>CH</option><option>AE/CH</option></select></div>
      <div class="form-group"><label class="form-label">Notes</label><textarea class="form-textarea" id="mf_notes"></textarea></div>`,
    deal:`
      <div class="form-group"><label class="form-label">Deal Name</label><input class="form-input" id="mf_name" placeholder="e.g. Landmark on Oak"></div>
      <div class="form-group"><label class="form-label">Status</label><select class="form-select" id="mf_status"><option>Post-Award</option><option>Construction</option><option>Lease-Up</option><option>Planning</option></select></div>`,
    planningItem:`
      <div class="form-group"><label class="form-label">Task</label><input class="form-input" id="mf_task" placeholder="Task description"></div>
      <div class="form-group"><label class="form-label">Category</label><select class="form-select" id="mf_cat"><option>To Do</option><option>Ahead of Next Round</option><option>2025 Planning</option><option>TX 2026</option><option>Other</option></select></div>
      <div class="form-group"><label class="form-label">Notes</label><textarea class="form-textarea" id="mf_notes"></textarea></div>`
  };
  e('modalBody').innerHTML = forms[type]||'';
  if (type==='planningItem' && args[0] && e('mf_cat')) e('mf_cat').value = args[0];
}

function closeModal() { e('modalOverlay').classList.add('hidden'); }

function saveModal() {
  const {type,args} = modalCtx;
  const g = id => { const el2=e(id); return el2 ? el2.value.trim() : ''; };
  if (type==='topPriority') {
    const task=g('mf_task'); if(!task) return;
    data.topPriorities.push({id:uid(),complete:false,task,notes:g('mf_notes'),ooo:g('mf_ooo')});
  } else if (type==='dealTask') {
    const dn=args[0], task=g('mf_task'); if(!task||!dn) return;
    data.deals[dn].tasks.push({id:uid(),complete:false,task,responsible:g('mf_resp'),internalDue:g('mf_intDue'),externalDue:g('mf_extDue'),notes:g('mf_notes'),etc:g('mf_etc')});
  } else if (type==='milestone'||type==='msMonth') {
    const ms=g('mf_ms'); if(!ms) return;
    const yr=type==='milestone'?g('mf_year'):(args[1]||'2026');
    const mo=type==='milestone'?g('mf_month'):(args[0]||'January');
    if(!data.milestones[yr]) data.milestones[yr]={};
    if(!data.milestones[yr][mo]) data.milestones[yr][mo]=[];
    data.milestones[yr][mo].push({id:uid(),complete:false,development:g('mf_dev'),milestone:ms,dueDate:g('mf_due'),responsible:g('mf_resp'),notes:g('mf_notes')});
  } else if (type==='deal') {
    const name=g('mf_name'); if(!name||data.deals[name]) return;
    data.deals[name]={status:g('mf_status')||'Post-Award',tasks:[]};
  } else if (type==='planningItem') {
    const task=g('mf_task'); if(!task) return;
    data.planning.push({id:uid(),complete:false,task,category:g('mf_cat')||'To Do',notes:g('mf_notes')});
  }
  saveData(); closeModal(); render();
  toast('Saved ✓','success');
}

// INIT
(async function() {
  e('mainContent').innerHTML='<div class="empty-state"><div class="icon">⏳</div><p>Loading your data…</p></div>';
  await loadData();
  render();
})();
</script>
</body>
</html>
