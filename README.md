<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Emergency Nursing Reference</title>
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <style>
    :root {
      --bg: #020617;
      --bg-alt: #0b1220;
      --card: #020617;
      --card-alt: #020617;
      --accent: #38bdf8;
      --accent-soft: rgba(56, 189, 248, 0.1);
      --danger: #f97373;
      --text: #e5e7eb;
      --muted: #9ca3af;
      --border: #1f2937;
      --radius-lg: 14px;
      --radius-md: 10px;
      --shadow-soft: 0 18px 40px rgba(15, 23, 42, 0.7);
      --shadow-tag: 0 4px 12px rgba(15, 23, 42, 0.8);
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      font-family: system-ui, -apple-system, BlinkMacSystemFont, "SF Pro Text",
        "Segoe UI", sans-serif;
      background: radial-gradient(circle at top, #0b1120 0, #020617 55%);
      color: var(--text);
      min-height: 100vh;
    }

    .page-shell {
      max-width: 1200px;
      margin: 0 auto;
      padding: 20px 16px 40px;
    }

    header {
      margin-bottom: 24px;
    }

    .title-row {
      display: flex;
      flex-wrap: wrap;
      justify-content: space-between;
      gap: 16px;
      align-items: flex-end;
    }

    h1 {
      font-size: clamp(1.9rem, 2.4vw + 1rem, 2.6rem);
      font-weight: 750;
      letter-spacing: 0.03em;
      display: flex;
      align-items: center;
      gap: 10px;
    }

    h1 span.logo-dot {
      width: 12px;
      height: 12px;
      border-radius: 999px;
      background: radial-gradient(circle at 30% 30%, #e0f2fe, #38bdf8);
      box-shadow: 0 0 18px rgba(56, 189, 248, 0.7);
    }

    .subtitle {
      font-size: 0.95rem;
      color: var(--muted);
      max-width: 520px;
      line-height: 1.5;
      margin-top: 4px;
    }

    .view-toggle {
      display: inline-flex;
      border-radius: 999px;
      padding: 4px;
      background: rgba(15, 23, 42, 0.9);
      border: 1px solid rgba(148, 163, 184, 0.25);
      box-shadow: var(--shadow-soft);
    }

    .view-toggle button {
      border: none;
      cursor: pointer;
      padding: 6px 14px;
      border-radius: 999px;
      font-size: 0.85rem;
      font-weight: 600;
      color: var(--muted);
      background: transparent;
      display: inline-flex;
      align-items: center;
      gap: 6px;
      transition: all 0.16s ease-out;
    }

    .view-toggle button.active {
      background: radial-gradient(circle at top left, #22d3ee, #0ea5e9);
      color: #0b1120;
      box-shadow: 0 0 0 1px rgba(15, 23, 42, 0.6),
        0 14px 30px rgba(37, 99, 235, 0.6);
    }

    .view-toggle button .pill-dot {
      width: 8px;
      height: 8px;
      border-radius: 999px;
      background: rgba(15, 23, 42, 0.7);
    }

    .view-toggle button.active .pill-dot {
      background: #e0f2fe;
    }

    .meta-row {
      display: flex;
      flex-wrap: wrap;
      justify-content: space-between;
      gap: 12px;
      align-items: center;
      margin-top: 18px;
    }

    .search-box {
      position: relative;
      flex: 1 1 260px;
      max-width: 420px;
    }

    .search-box input {
      width: 100%;
      padding: 10px 11px 10px 30px;
      border-radius: 999px;
      border: 1px solid rgba(148, 163, 184, 0.4);
      background: rgba(15, 23, 42, 0.85);
      color: var(--text);
      font-size: 0.9rem;
      outline: none;
      box-shadow: 0 14px 26px rgba(15, 23, 42, 0.8);
    }

    .search-box input::placeholder {
      color: #6b7280;
    }

    .search-box span.icon {
      position: absolute;
      left: 10px;
      top: 50%;
      transform: translateY(-50%);
      font-size: 0.8rem;
      color: var(--muted);
      pointer-events: none;
    }

    .badge-row {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      font-size: 0.78rem;
      color: var(--muted);
    }

    .pill-badge {
      padding: 5px 10px;
      border-radius: 999px;
      border: 1px solid rgba(148, 163, 184, 0.35);
      background: rgba(15, 23, 42, 0.7);
      display: inline-flex;
      align-items: center;
      gap: 6px;
    }

    .pill-dot-small {
      width: 6px;
      height: 6px;
      border-radius: 999px;
      background: linear-gradient(to right, #22c55e, #a3e635);
    }

    main {
      margin-top: 24px;
    }

    .content-section {
      display: none;
      animation: fadeIn 0.3s ease-out;
    }

    .content-section.active {
      display: block;
    }

    @keyframes fadeIn {
      from {
        opacity: 0;
        transform: translateY(4px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    .category-grid {
      display: grid;
      grid-template-columns: minmax(0, 1.5fr) minmax(0, 1.5fr);
      gap: 18px;
    }

    @media (max-width: 900px) {
      .category-grid {
        grid-template-columns: minmax(0, 1fr);
      }
    }

    .category-card {
      background: radial-gradient(circle at top left, #020617, #020617);
      border-radius: var(--radius-lg);
      border: 1px solid var(--border);
      box-shadow: var(--shadow-soft);
      padding: 14px 14px 10px;
      display: flex;
      flex-direction: column;
      gap: 10px;
    }

    .category-header {
      display: flex;
      flex-direction: column;
      gap: 4px;
      padding-bottom: 6px;
      border-bottom: 1px solid rgba(31, 41, 55, 0.9);
    }

    .category-title-row {
      display: flex;
      justify-content: space-between;
      gap: 6px;
      align-items: baseline;
    }

    .category-title-row h2 {
      font-size: 0.98rem;
      text-transform: uppercase;
      letter-spacing: 0.12em;
      color: #e5e7eb;
    }

    .category-title-row span.category-tagline {
      font-size: 0.7rem;
      text-transform: uppercase;
      color: var(--muted);
      opacity: 0.9;
    }

    .category-desc {
      font-size: 0.82rem;
      color: var(--muted);
      line-height: 1.4;
    }

    .tag-row {
      display: flex;
      flex-wrap: wrap;
      gap: 6px;
      margin-top: 4px;
    }

    .tag {
      font-size: 0.68rem;
      text-transform: uppercase;
      letter-spacing: 0.12em;
      padding: 2px 8px;
      border-radius: 999px;
      background: rgba(15, 23, 42, 0.9);
      border: 1px solid rgba(148, 163, 184, 0.5);
      color: var(--muted);
      box-shadow: var(--shadow-tag);
      white-space: nowrap;
    }

    .tag-high {
      border-color: rgba(248, 113, 113, 0.8);
      color: #fecaca;
      background: rgba(127, 29, 29, 0.85);
    }

    .tag-peds {
      border-color: rgba(250, 204, 21, 0.85);
      color: #fef9c3;
      background: rgba(113, 63, 18, 0.8);
    }

    .tag-protocol {
      border-color: rgba(56, 189, 248, 0.9);
      color: #e0f2fe;
      background: rgba(8, 47, 73, 0.9);
    }

    .condition-table {
      width: 100%;
      border-collapse: collapse;
      margin-top: 4px;
      font-size: 0.78rem;
    }

    .condition-table thead {
      background: rgba(15, 23, 42, 0.9);
    }

    .condition-table th,
    .condition-table td {
      border: 1px solid rgba(31, 41, 55, 0.9);
      padding: 6px 7px;
      vertical-align: top;
    }

    .condition-table th {
      font-weight: 600;
      text-align: left;
      color: #e5e7eb;
      white-space: nowrap;
    }

    .condition-table td {
      color: #d1d5db;
      line-height: 1.4;
    }

    .condition-name {
      font-weight: 600;
      color: #e5e7eb;
    }

    .chip-row {
      margin-top: 4px;
      display: flex;
      flex-wrap: wrap;
      gap: 4px;
    }

    .chip {
      font-size: 0.63rem;
      text-transform: uppercase;
      letter-spacing: 0.16em;
      padding: 2px 6px;
      border-radius: 999px;
      border: 1px solid rgba(148, 163, 184, 0.65);
      color: #cbd5f5;
      background: rgba(15, 23, 42, 0.95);
    }

    .chip-red {
      border-color: rgba(248, 113, 113, 0.8);
      color: #fecaca;
    }

    .chip-blue {
      border-color: rgba(56, 189, 248, 0.85);
      color: #bae6fd;
    }

    .chip-amber {
      border-color: rgba(251, 191, 36, 0.9);
      color: #fef3c7;
    }

    .footnote {
      font-size: 0.7rem;
      color: var(--muted);
      margin-top: 14px;
      padding: 8px 10px;
      border-radius: var(--radius-md);
      background: linear-gradient(
        to right,
        rgba(15, 23, 42, 0.95),
        rgba(15, 23, 42, 0.9)
      );
      border: 1px dashed rgba(148, 163, 184, 0.5);
    }

    code.inline {
      font-family: ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas,
        "Liberation Mono", "Courier New", monospace;
      font-size: 0.7rem;
      background: rgba(15, 23, 42, 0.9);
      padding: 1px 4px;
      border-radius: 999px;
      border: 1px solid rgba(31, 41, 55, 0.9);
      color: #e5e7eb;
    }

    .hidden-row {
      display: none;
    }
  </style>
</head>
<body>
  <div class="page-shell">
    <header>
      <div class="title-row">
        <div>
          <h1>
            <span class="logo-dot" aria-hidden="true"></span>
            Emergency Nursing Reference
          </h1>
          <p class="subtitle">
            Quick‑access diseases, meds, and nursing actions for adult and pediatric
            emergencies. Built as a teaching + shift tool — not a replacement for
            local policies or provider orders.
          </p>
        </div>
        <div class="view-toggle" aria-label="Switch between adult and pediatric content">
          <button type="button" data-view-btn="adult" class="active">
            <span class="pill-dot"></span>
            Adult
          </button>
          <button type="button" data-view-btn="peds">
            <span class="pill-dot"></span>
            Pediatrics
          </button>
        </div>
      </div>

      <div class="meta-row">
        <div class="search-box">
          <span class="icon">🔍</span>
          <input
            id="searchInput"
            type="text"
            placeholder="Search by condition, drug, or keyword (e.g. sepsis, norepi, asthma)…"
          />
        </div>
        <div class="badge-row">
          <div class="pill-badge">
            <span class="pill-dot-small"></span>
            <span>Educational reference only – verify doses with local guidelines.</span>
          </div>
        </div>
      </div>
    </header>

    <main>
      <!-- ================= ADULT SECTION ================= -->
      <section id="adult-section" class="content-section active">
        <div class="category-grid">
          <!-- AIRWAY & BREATHING (ADULT) -->
          <article class="category-card">
            <div class="category-header">
              <div class="category-title-row">
                <h2>Airway &amp; Breathing</h2>
                <span class="category-tagline">Respiratory emergencies</span>
              </div>
              <p class="category-desc">
                First five minutes stuff: airway protection, oxygenation, ventilation, and
                recognizing who needs NIV vs tube.
              </p>
              <div class="tag-row">
                <span class="tag tag-high">High acuity</span>
                <span class="tag">Adult</span>
              </div>
            </div>

            <table class="condition-table">
              <thead>
                <tr>
                  <th style="width: 20%">Condition</th>
                  <th style="width: 35%">Key Meds</th>
                  <th style="width: 45%">Nursing Treatments / Notes</th>
                </tr>
              </thead>
              <tbody>
                <tr data-condition="status asthmaticus severe asthma bronchospasm">
                  <td>
                    <div class="condition-name">Status Asthmaticus</div>
                    <div class="chip-row">
                      <span class="chip chip-red">Airway risk</span>
                      <span class="chip chip-blue">NIV first if able</span>
                    </div>
                  </td>
                  <td>
                    • Neb <strong>salbutamol</strong> + <strong>ipratropium</strong> q20min early<br />
                    • IV <strong>methylprednisolone</strong> (e.g. 125&nbsp;mg)<br />
                    • IV <strong>magnesium sulfate</strong> (e.g. 2&nbsp;g over 20–30&nbsp;min)<br />
                    • Consider ketamine for intubation &amp; post‑intubation sedation
                  </td>
                  <td>
                    • Sit upright, continuous pulse ox, tight wheeze &amp; fatigue = red flag<br />
                    • Prepare BiPAP if tolerated; watch for rising CO₂, tiring, ↓LOC<br />
                    • If they crash: small VT, long expiratory time, watch auto‑PEEP<br />
                    • Reassess work of breathing and speaking ability q5–10&nbsp;min
                  </td>
                </tr>

                <tr data-condition="pulmonary edema flash acute heart failure">
                  <td>
                    <div class="condition-name">Acute Pulmonary Edema</div>
                    <div class="chip-row">
                      <span class="chip chip-red">Air hunger</span>
                      <span class="chip chip-blue">Positive pressure</span>
                    </div>
                  </td>
                  <td>
                    • High‑dose IV <strong>furosemide</strong> (e.g. 40–80&nbsp;mg, or 2.5× home dose)<br />
                    • Consider IV <strong>nitroglycerin</strong> if hypertensive and not RV/AS<br />
                    • Morphine only if severe distress and team agrees (resp risk)
                  </td>
                  <td>
                    • HFNC or BiPAP early (good for preload + afterload reduction)<br />
                    • Strict I/O, daily weights, monitor BP closely with IV nitro<br />
                    • Watch for pink frothy sputum, orthopnea, inability to lay flat<br />
                    • Get ECG, quickly screen for ACS driver
                  </td>
                </tr>

                <tr data-condition="respiratory failure pneumonia ards hypoxemia">
                  <td>
                    <div class="condition-name">Severe Hypoxemic Resp Failure / ARDS</div>
                    <div class="chip-row">
                      <span class="chip chip-red">Prone candidate</span>
                      <span class="chip chip-blue">Low VT</span>
                    </div>
                  </td>
                  <td>
                    • Sedation: <strong>propofol</strong> ± opioid infusion<br />
                    • <strong>Paralytic</strong> if vent asynchrony (e.g. cisatracurium or roc boluses)<br />
                    • Early <strong>steroids</strong> in moderate–severe ARDS per unit protocol
                  </td>
                  <td>
                    • Use low VT (≈6&nbsp;mL/kg predicted), PEEP per ARDSnet<br />
                    • Accept permissive hypercapnia unless neuro contraindication<br />
                    • Prone if P/F &lt;150 on high FiO₂; protect tubes/lines while flipping<br />
                    • Suction gently, oral care, inline suction if intubated
                  </td>
                </tr>
              </tbody>
            </table>
          </article>

          <!-- CIRCULATION & SHOCK (ADULT) -->
          <article class="category-card">
            <div class="category-header">
              <div class="category-title-row">
                <h2>Shock &amp; Circulation</h2>
                <span class="category-tagline">Sepsis, PE, cardiogenic</span>
              </div>
              <p class="category-desc">
                Map out the “why” (septic, obstructive, cardiogenic) and then match
                fluids, vasopressors, and inotropes to the physiology.
              </p>
              <div class="tag-row">
                <span class="tag tag-high">Resus bay</span>
                <span class="tag tag-protocol">Pressor quick reference</span>
              </div>
            </div>

            <table class="condition-table">
              <thead>
                <tr>
                  <th>Condition</th>
                  <th>Key Meds</th>
                  <th>Nursing Treatments / Notes</th>
                </tr>
              </thead>
              <tbody>
                <tr data-condition="septic shock sepsis norepinephrine vasopressin antibiotics">
                  <td>
                    <div class="condition-name">Septic Shock</div>
                    <div class="chip-row">
                      <span class="chip chip-red">Time‑critical</span>
                      <span class="chip chip-blue">MAP ≥ 65</span>
                    </div>
                  </td>
                  <td>
                    • Broad‑spectrum IV antibiotics (e.g. piperacillin‑tazobactam ± vanco)<br />
                    • <strong>Norepinephrine</strong> first‑line pressor<br />
                    • Add <strong>vasopressin</strong> if NE dose climbing<br />
                    • <strong>Hydrocortisone</strong> for refractory shock per protocol
                  </td>
                  <td>
                    • Draw lactate, blood cultures before abx if doable without delay<br />
                    • Start with ~30&nbsp;mL/kg crystalloid, then reassess fluid responsiveness<br />
                    • Titrate NE via smart pump; use central line ASAP, art line if ordered<br />
                    • Strict I/O, hourly UO, mental status, skin temp, cap refill
                  </td>
                </tr>

                <tr data-condition="pulmonary embolism pe massive submassive heparin alteplase">
                  <td>
                    <div class="condition-name">Massive / Submassive PE</div>
                    <div class="chip-row">
                      <span class="chip chip-red">RV failure risk</span>
                      <span class="chip chip-blue">Heparin</span>
                    </div>
                  </td>
                  <td>
                    • IV <strong>UFH</strong> infusion (or LMWH if stable, per orders)<br />
                    • Consider systemic <strong>alteplase</strong> per PE protocol in massive PE<br />
                    • Inotropes (dobutamine/milrinone) and vasopressors as ordered
                  </td>
                  <td>
                    • High‑flow O₂, watch for sudden hypotension, JVD, syncope<br />
                    • Avoid fluid overload; small boluses only if preload suspect low<br />
                    • Intubation is high‑risk — call for help early, prepare push‑dose pressors<br />
                    • Monitor for bleeding if lytics given (neuro checks, hematuria, etc.)
                  </td>
                </tr>

                <tr data-condition="cardiogenic shock acute coronary syndrome low output heart failure">
                  <td>
                    <div class="condition-name">Cardiogenic Shock</div>
                    <div class="chip-row">
                      <span class="chip chip-red">Low output</span>
                      <span class="chip chip-blue">Diuresis + inotrope</span>
                    </div>
                  </td>
                  <td>
                    • IV <strong>furosemide</strong> if volume overloaded<br />
                    • <strong>Dobutamine</strong> or <strong>milrinone</strong> inotrope<br />
                    • Low‑dose <strong>norepinephrine</strong> to support MAP if needed<br />
                    • <strong>Amiodarone</strong> for unstable AF/VT per ACLS
                  </td>
                  <td>
                    • Cardiac monitor, frequent BP, watch for arrhythmias &amp; chest pain<br />
                    • MAP goal often 55–60 if end organs perfusing; don’t over‑squeeze<br />
                    • Check daily weights, JVP/IVC, lung sounds to guide volume<br />
                    • Coordinate with cardiology on cath, devices (IABP, Impella, ECMO)
                  </td>
                </tr>
              </tbody>
            </table>
          </article>

          <!-- NEURO EMERGENCIES (ADULT) -->
          <article class="category-card">
            <div class="category-header">
              <div class="category-title-row">
                <h2>Neuro Emergencies</h2>
                <span class="category-tagline">TBI, SAH, seizures</span>
              </div>
              <p class="category-desc">
                BP, CO₂, and sedation are meds too. Protect the brain while team sorts the
                CT/EEG/OR plan.
              </p>
              <div class="tag-row">
                <span class="tag tag-high">Neuro watch</span>
              </div>
            </div>

            <table class="condition-table">
              <thead>
                <tr>
                  <th>Condition</th>
                  <th>Key Meds</th>
                  <th>Nursing Treatments / Notes</th>
                </tr>
              </thead>
              <tbody>
                <tr data-condition="status epilepticus seizure lorazepam levetiracetam propofol">
                  <td>
                    <div class="condition-name">Status Epilepticus</div>
                    <div class="chip-row">
                      <span class="chip chip-red">Airway risk</span>
                      <span class="chip chip-blue">EEG</span>
                    </div>
                  </td>
                  <td>
                    • IV <strong>lorazepam</strong> (first‑line) or IM <strong>midazolam</strong> if no IV<br />
                    • Load <strong>levetiracetam</strong> or <strong>phenytoin/fosphenytoin</strong><br />
                    • If refractory: <strong>propofol</strong> ± <strong>midazolam</strong> ± <strong>ketamine</strong> infusion
                  </td>
                  <td>
                    • Protect airway, suction, side‑lying if not intubated<br />
                    • Get glucose, lytes, temp, tox history (DIMS approach)<br />
                    • Once intubated, target burst suppression per EEG orders<br />
                    • Watch BP — sedative drips can tank pressure quickly
                  </td>
                </tr>

                <tr data-condition="subarachnoid hemorrhage sah nimodipine labetalol nicardipine">
                  <td>
                    <div class="condition-name">Aneurysmal SAH (Unsecured)</div>
                    <div class="chip-row">
                      <span class="chip chip-red">Re‑bleed risk</span>
                      <span class="chip chip-amber">SBP control</span>
                    </div>
                  </td>
                  <td>
                    • IV <strong>labetalol</strong>, <strong>hydralazine</strong>, or <strong>nicardipine</strong> infusion for SBP<br />
                    • Start oral/NG <strong>nimodipine</strong> once ordered (q4h x 21&nbsp;days)<br />
                    • Reverse anticoagulants per neuro protocol
                  </td>
                  <td>
                    • SBP typically 140–160 unless told otherwise; arterial line helpful<br />
                    • Neuro checks as ordered, watch for vasospasm (new deficit, ↓LOC)<br />
                    • Strict I/O, avoid hypotension — maintain euvolemia<br />
                    • Keep analgesia/anti‑emetics on board to prevent BP spikes
                  </td>
                </tr>

                <tr data-condition="traumatic brain injury tbi icp mannitol hypertonic saline">
                  <td>
                    <div class="condition-name">Moderate–Severe TBI</div>
                    <div class="chip-row">
                      <span class="chip chip-red">Avoid hypotension</span>
                      <span class="chip chip-blue">ICP control</span>
                    </div>
                  </td>
                  <td>
                    • Sedation: <strong>propofol</strong> ± opioid; avoid hypotension<br />
                    • Hyperosmolar therapy: <strong>mannitol</strong> or <strong>3% NaCl</strong> IV when ordered<br />
                    • 7‑day <strong>phenytoin</strong> prophylaxis in selected patients per neurosurg
                  </td>
                  <td>
                    • Neuroprotective intubation: no hypoxia, no hypotension, no big CO₂ swings<br />
                    • HOB up, neutral neck, avoid tight C‑collar if cleared<br />
                    • Keep Na in goal range; watch for DI/CSW vs SIADH<br />
                    • If EVD present: know level, clamp/open orders, and how to read ICP
                  </td>
                </tr>
              </tbody>
            </table>
          </article>

          <!-- ED MED QUICK REFERENCE (ADULT) -->
          <article class="category-card">
            <div class="category-header">
              <div class="category-title-row">
                <h2>ED Med Quick Reference</h2>
                <span class="category-tagline">Common resus meds</span>
              </div>
              <p class="category-desc">
                Not a dose book — just a reminder of “what &amp; why” for typical emergency
                meds. Always check local dosing guides.
              </p>
              <div class="tag-row">
                <span class="tag tag-protocol">Cross‑check doses</span>
              </div>
            </div>

            <table class="condition-table">
              <thead>
                <tr>
                  <th>Drug</th>
                  <th>Typical ED Use</th>
                  <th>Why this drug / Key cautions</th>
                </tr>
              </thead>
              <tbody>
                <tr data-condition="norepinephrine levophed septic shock pressor first line">
                  <td>
                    <div class="condition-name">Norepinephrine (Levophed)</div>
                  </td>
                  <td>
                    • First‑line vasopressor in septic/undifferentiated shock<br />
                    • Titrated to MAP (often ≥65&nbsp;mmHg)
                  </td>
                  <td>
                    • Strong α with some β1 — good squeeze + modest inotropy<br />
                    • Less tachycardia than dopamine/epinephrine<br />
                    • Prefer central line; monitor extremities for ischemia, extravasation
                  </td>
                </tr>

                <tr data-condition="vasopressin septic shock add on pressor">
                  <td>
                    <div class="condition-name">Vasopressin</div>
                  </td>
                  <td>
                    • Add‑on pressor in refractory septic shock<br />
                    • Fixed dose (e.g. 0.03 units/min per protocol)
                  </td>
                  <td>
                    • V1‑mediated vasoconstriction, minimal effect on pulmonary vessels<br />
                    • Reduces NE requirements; may help renal perfusion<br />
                    • Do <em>not</em> titrate like NE — it’s usually ordered as a fixed low dose
                  </td>
                </tr>

                <tr data-condition="ketamine induction analgesia sedation asthma agitation">
                  <td>
                    <div class="condition-name">Ketamine</div>
                  </td>
                  <td>
                    • RSI induction (hemodynamically fragile patients)<br />
                    • Low‑dose analgesia; severe agitation (IM/IV)
                  </td>
                  <td>
                    • Preserves airway reflexes and BP more than propofol<br />
                    • Bronchodilatory in asthma; good for pain + dissociation combo<br />
                    • Watch for emergence reactions; consider benzodiazepine if needed
                  </td>
                </tr>

                <tr data-condition="tranexamic acid txa trauma postpartum hemorrhage gi bleed">
                  <td>
                    <div class="condition-name">Tranexamic Acid (TXA)</div>
                  </td>
                  <td>
                    • Trauma/postpartum hemorrhage early in course<br />
                    • <em>Not</em> routinely for GI bleed per HALT‑IT
                  </td>
                  <td>
                    • Antifibrinolytic — stabilizes clot; best if given early<br />
                    • Monitor for thrombotic risk; follow local protocol tightly<br />
                    • Double‑check indication before giving in non‑trauma bleeds
                  </td>
                </tr>
              </tbody>
            </table>
          </article>
        </div>
      </section>

      <!-- ================= PEDIATRIC SECTION ================= -->
      <section id="peds-section" class="content-section">
        <div class="category-grid">
          <!-- PEDS AIRWAY & BREATHING -->
          <article class="category-card">
            <div class="category-header">
              <div class="category-title-row">
                <h2>Peds Airway &amp; Breathing</h2>
                <span class="category-tagline">Kids breathe weird</span>
              </div>
              <p class="category-desc">
                Smaller pipes, big reactions. Look at work of breathing and behavior first,
                then decide O₂, nebs, or advanced airway.
              </p>
              <div class="tag-row">
                <span class="tag tag-peds">Pediatrics</span>
                <span class="tag tag-high">High acuity</span>
              </div>
            </div>

            <table class="condition-table">
              <thead>
                <tr>
                  <th>Condition</th>
                  <th>Key Meds (weight‑based)</th>
                  <th>Nursing Treatments / Notes</th>
                </tr>
              </thead>
              <tbody>
                <tr data-condition="croup upper airway obstruction dexamethasone racemic epinephrine">
                  <td>
                    <div class="condition-name">Croup</div>
                    <div class="chip-row">
                      <span class="chip chip-amber">Upper airway</span>
                    </div>
                  </td>
                  <td>
                    • PO/NG/IV <strong>dexamethasone</strong> (per kg dosing)<br />
                    • Nebulized <strong>epinephrine</strong> (racemic/l‑epi) for moderate–severe distress
                  </td>
                  <td>
                    • Classic barking cough, stridor; keep child calm, parent present<br />
                    • Continuous sat and resp assessment after racemic epi (watch for rebound)<br />
                    • Prepare for potential deterioration and airway backup
                  </td>
                </tr>

                <tr data-condition="bronchiolitis rsv high flow nasal cannula">
                  <td>
                    <div class="condition-name">Bronchiolitis</div>
                    <div class="chip-row">
                      <span class="chip chip-blue">HFNC friendly</span>
                    </div>
                  </td>
                  <td>
                    • Usually supportive only (O₂, feeds, suction)<br />
                    • Bronchodilators/steroids typically limited role — follow local protocol
                  </td>
                  <td>
                    • Suction nose frequently; monitor feeding tolerance &amp; hydration<br />
                    • HFNC if ↑ work of breathing or persistent hypoxia<br />
                    • Watch for apnea in young infants; continuous cardioresp monitoring
                  </td>
                </tr>

                <tr data-condition="pediatric asthma acute exacerbation salbutamol ipratropium steroids magnesium">
                  <td>
                    <div class="condition-name">Acute Peds Asthma</div>
                    <div class="chip-row">
                      <span class="chip chip-red">Airway risk</span>
                    </div>
                  </td>
                  <td>
                    • Neb <strong>salbutamol</strong> ± <strong>ipratropium</strong> (per kg dosing)<br />
                    • PO/IV <strong>steroids</strong> (prednisone / methylpred)<br />
                    • IV <strong>magnesium sulfate</strong> for severe cases per protocol
                  </td>
                  <td>
                    • Monitor work of breathing, ability to speak, mental status<br />
                    • Spacers + masks for MDI if able; don’t forget coaching and reassurance<br />
                    • Prepare for possible escalation to NIV or intubation in ICU‑level cases
                  </td>
                </tr>
              </tbody>
            </table>
          </article>

          <!-- PEDS CIRCULATION / SHOCK -->
          <article class="category-card">
            <div class="category-header">
              <div class="category-title-row">
                <h2>Peds Shock &amp; Resus</h2>
                <span class="category-tagline">Tiny humans, tight margins</span>
              </div>
              <p class="category-desc">
                Kids compensate until they suddenly don’t. Weight‑based dosing, early
                fluids, and escalate to pressors/PALS meds.
              </p>
              <div class="tag-row">
                <span class="tag tag-peds">Pediatrics</span>
                <span class="tag tag-high">Resus bay</span>
              </div>
            </div>

            <table class="condition-table">
              <thead>
                <tr>
                  <th>Condition</th>
                  <th>Key Meds</th>
                  <th>Nursing Treatments / Notes</th>
                </tr>
              </thead>
              <tbody>
                <tr data-condition="pediatric septic shock fluid bolus norepinephrine epinephrine antibiotics">
                  <td>
                    <div class="condition-name">Pediatric Septic Shock</div>
                    <div class="chip-row">
                      <span class="chip chip-red">Time‑critical</span>
                    </div>
                  </td>
                  <td>
                    • 10–20&nbsp;mL/kg crystalloid boluses (careful, reassess each)<br />
                    • Early IV antibiotics (per local guideline and source)<br />
                    • Pressors (weight‑based <strong>epinephrine</strong> or <strong>norepinephrine</strong>) if hypotensive
                  </td>
                  <td>
                    • Use length/weight‑based tools (Broselow, etc.)<br />
                    • Frequent reassessment: cap refill, mental status, UO<br />
                    • Early escalation to ICU/PICU; involve Peds early<br />
                    • Watch for cold vs warm shock patterns for provider
                  </td>
                </tr>

                <tr data-condition="anaphylaxis pedi epinephrine im antihistamine steroid">
                  <td>
                    <div class="condition-name">Anaphylaxis (Peds)</div>
                    <div class="chip-row">
                      <span class="chip chip-red">Give epi IM</span>
                    </div>
                  </td>
                  <td>
                    • IM <strong>epinephrine</strong> in mid‑thigh (per kg dosing, max adult dose)<br />
                    • PO/IV <strong>antihistamines</strong> + <strong>steroids</strong> as adjuncts<br />
                    • Nebulized bronchodilators if wheezing
                  </td>
                  <td>
                    • Secure airway positioning, high‑flow O₂, continuous monitoring<br />
                    • Have second IM epi ready; observe for biphasic reaction<br />
                    • Educate family on triggers, autoinjector before discharge
                  </td>
                </tr>

                <tr data-condition="pals cardiac arrest epinephrine amiodarone">
                  <td>
                    <div class="condition-name">PALS Arrest Algorithms</div>
                    <div class="chip-row">
                      <span class="chip chip-blue">Follow PALS</span>
                    </div>
                  </td>
                  <td>
                    • IV/IO <strong>epinephrine</strong> every 3–5&nbsp;min per PALS<br />
                    • <strong>Amiodarone</strong> per PALS for refractory VT/VF<br />
                    • Weight‑based shock energy (J/kg) for defibrillation
                  </td>
                  <td>
                    • High‑quality CPR with minimal pauses<br />
                    • Ensure correct dose conversions; double‑check with second RN<br />
                    • Family presence can be offered if team supports and safe
                  </td>
                </tr>
              </tbody>
            </table>
          </article>

          <!-- PEDS COMMON ED CONDITIONS -->
          <article class="category-card">
            <div class="category-header">
              <div class="category-title-row">
                <h2>Common Peds ED Presentations</h2>
                <span class="category-tagline">Bread &amp; butter + scary stuff</span>
              </div>
              <p class="category-desc">
                Febrile kids, seizures, and dehydration — plus which meds to consider
                and what to watch like a hawk.
              </p>
              <div class="tag-row">
                <span class="tag tag-peds">Pediatrics</span>
              </div>
            </div>

            <table class="condition-table">
              <thead>
                <tr>
                  <th>Condition</th>
                  <th>Key Meds</th>
                  <th>Nursing Treatments / Notes</th>
                </tr>
              </thead>
              <tbody>
                <tr data-condition="febrile seizure diazepam midazolam acetaminophen">
                  <td>
                    <div class="condition-name">Febrile Seizure</div>
                  </td>
                  <td>
                    • PR/IV/IN <strong>benzodiazepine</strong> if seizure ongoing<br />
                    • <strong>Acetaminophen</strong> / <strong>ibuprofen</strong> for comfort (doesn’t prevent recurrence)
                  </td>
                  <td>
                    • Most simple febrile seizures self‑resolve &lt;5&nbsp;min<br />
                    • Protect airway, recovery position, reassure parents<br />
                    • Screen for serious infection (meningitis red flags, sepsis signs)
                  </td>
                </tr>

                <tr data-condition="dehydration gastroenteritis oral rehydration iv fluids ondansetron">
                  <td>
                    <div class="condition-name">Moderate Dehydration / Gastro</div>
                  </td>
                  <td>
                    • Oral rehydration solutions if able to drink<br />
                    • IV <strong>crystalloids</strong> (per kg) if unable to tolerate PO<br />
                    • <strong>Ondansetron</strong> for vomiting per protocol
                  </td>
                  <td>
                    • Weight‑based fluid boluses; watch for over‑resuscitation in neonates<br />
                    • Strict I/O, daily weight, monitor for decreased UO and lethargy<br />
                    • Parent education on small frequent sips, warning signs to return
                  </td>
                </tr>

                <tr data-condition="meningitis suspected ceftriaxone vancomycin acyclovir">
                  <td>
                    <div class="condition-name">Suspected Meningitis</div>
                  </td>
                  <td>
                    • IV <strong>ceftriaxone</strong> (meningitic dosing) ± <strong>vancomycin</strong><br />
                    • ± <strong>acyclovir</strong> if HSV risk; per orders<br />
                    • Consider <strong>dexamethasone</strong> in some age groups per protocol
                  </td>
                  <td>
                    • Droplet isolation; rapid IV access, blood cultures as ordered<br />
                    • Neuro checks, fontanel assessment in infants, photophobia/neck pain<br />
                    • Family support — explain LP, monitoring, need for admission
                  </td>
                </tr>
              </tbody>
            </table>
          </article>

          <!-- PEDS MED QUICK REF -->
          <article class="category-card">
            <div class="category-header">
              <div class="category-title-row">
                <h2>Peds Med Quick Reference</h2>
                <span class="category-tagline">Weight‑based mindset</span>
              </div>
              <p class="category-desc">
                Core pediatric emergency meds and why we reach for them. Always
                confirm dosing with a Peds reference/PALS card.
              </p>
              <div class="tag-row">
                <span class="tag tag-peds">Pediatrics</span>
                <span class="tag tag-protocol">Check doses</span>
              </div>
            </div>

            <table class="condition-table">
              <thead>
                <tr>
                  <th>Drug</th>
                  <th>Use</th>
                  <th>Key pearls</th>
                </tr>
              </thead>
              <tbody>
                <tr data-condition="acetaminophen ibuprofen antipyretic analgesic peds">
                  <td>
                    <div class="condition-name">Acetaminophen / Ibuprofen</div>
                  </td>
                  <td>
                    • Pain and fever management in kids<br />
                    • Often given as combo staggered over day
                  </td>
                  <td>
                    • Dose strictly by weight and max daily dose<br />
                    • Check liver/kidney status, other OTC meds at home<br />
                    • Teach caregivers how to measure doses accurately
                  </td>
                </tr>

                <tr data-condition="ondansetron zofran nausea vomiting pediatric">
                  <td>
                    <div class="condition-name">Ondansetron</div>
                  </td>
                  <td>
                    • Nausea/vomiting, help tolerate oral rehydration
                  </td>
                  <td>
                    • Weight‑based; avoid high QT‑prolonging doses<br />
                    • Reassess after dose: able to keep fluids down? Any abdo red flags?
                  </td>
                </tr>

                <tr data-condition="midazolam intranasal im iv sedation seizure control">
                  <td>
                    <div class="condition-name">Midazolam</div>
                  </td>
                  <td>
                    • Seizure control (IN/IM/IV)<br />
                    • Procedural sedation in combo with analgesia
                  </td>
                  <td>
                    • Monitor airway closely, especially with opioids<br />
                    • Document time/route clearly, note any paradoxical agitation
                  </td>
                </tr>
              </tbody>
            </table>
          </article>
        </div>
      </section>

      <p class="footnote">
        This page is a <strong>teaching/quick‑reference tool</strong> for emergency nurses and
        learners. It doesn’t replace clinical judgment, PALS/ACLS, or local protocols.
        Always double‑check <code class="inline">weight‑based dosing</code>, allergies, and
        contraindications before giving meds.
      </p>
    </main>
  </div>

  <script>
    // ===== Toggle Adult vs Peds view =====
    const viewButtons = document.querySelectorAll("[data-view-btn]");
    const sections = {
      adult: document.getElementById("adult-section"),
      peds: document.getElementById("peds-section")
    };

    viewButtons.forEach((btn) => {
      btn.addEventListener("click", () => {
        const target = btn.getAttribute("data-view-btn");

        viewButtons.forEach((b) => b.classList.remove("active"));
        btn.classList.add("active");

        Object.keys(sections).forEach((key) => {
          sections[key].classList.toggle("active", key === target);
        });

        // Clear search when switching views so rows are visible again
        const searchInput = document.getElementById("searchInput");
        if (searchInput.value.trim() !== "") {
          searchInput.value = "";
          filterRows("");
        }
      });
    });

    // ===== Search across visible section =====
    const searchInput = document.getElementById("searchInput");

    function filterRows(query) {
      const activeSection = document.querySelector(".content-section.active");
      if (!activeSection) return;
      const rows = activeSection.querySelectorAll(
        ".condition-table tbody tr"
      );
      const q = query.toLowerCase();

      rows.forEach((row) => {
        const text = row.textContent.toLowerCase();
        const extra = (row.getAttribute("data-condition") || "").toLowerCase();
        const match = text.includes(q) || extra.includes(q);
        row.classList.toggle("hidden-row", !match && q.length > 0);
        if (!q.length) {
          row.classList.remove("hidden-row");
        }
      });
    }

    searchInput.addEventListener("input", (e) => {
      filterRows(e.target.value);
    });
  </script>
</body>
</html>
