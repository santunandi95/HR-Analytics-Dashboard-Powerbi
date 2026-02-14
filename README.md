<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>HR Analytics Dashboard · README</title>
    <style>
        /* Dark theme, dashboard-like styling – works inside GitHub README */
        .hr-dashboard-card {
            font-family: system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', sans-serif;
            background: #0b0f17;
            color: #e6edf3;
            max-width: 1100px;
            margin: 0 auto;
            padding: 2rem 1.8rem;
            border-radius: 32px;
            border: 1px solid #2a3346;
            box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.8);
            line-height: 1.5;
        }

        /* typography */
        .hr-title {
            font-size: 2.8rem;
            font-weight: 600;
            margin: 0 0 0.25rem 0;
            background: linear-gradient(135deg, #b2bfff, #85a0ff);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            letter-spacing: -0.02em;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .hr-subhead {
            font-size: 1.1rem;
            color: #9aa7c4;
            margin-top: 0.25rem;
            border-left: 4px solid #3b6eff;
            padding-left: 1rem;
            background: rgba(59, 110, 255, 0.05);
            border-radius: 0 12px 12px 0;
        }

        /* kpi row */
        .kpi-grid {
            display: flex;
            flex-wrap: wrap;
            gap: 16px;
            margin: 30px 0 25px;
        }

        .kpi-item {
            background: #161e2c;
            border-radius: 28px;
            padding: 1.2rem 1.8rem;
            flex: 1 1 140px;
            border: 1px solid #28344a;
            box-shadow: 0 8px 0 #0d121d;
            transition: all 0.15s ease;
        }

        .kpi-item:hover {
            transform: translateY(-3px);
            border-color: #4c6ef5;
            box-shadow: 0 12px 0 #0d121d;
        }

        .kpi-label {
            font-size: 0.9rem;
            text-transform: uppercase;
            letter-spacing: 1px;
            color: #8191b0;
        }

        .kpi-value {
            font-size: 2.5rem;
            font-weight: 600;
            line-height: 1.1;
            color: white;
        }

        .kpi-value small {
            font-size: 1rem;
            font-weight: 400;
            color: #a0b3d9;
            margin-left: 5px;
        }

        /* section headers */
        .section-header {
            display: flex;
            align-items: center;
            gap: 8px;
            font-size: 1.6rem;
            font-weight: 600;
            margin: 2.2rem 0 1.2rem 0;
            border-bottom: 2px solid #28344a;
            padding-bottom: 0.5rem;
            color: #ccd9f0;
        }

        .section-header span {
            background: #1f2a3c;
            padding: 4px 12px;
            border-radius: 40px;
            font-size: 0.9rem;
            color: #9bb1e0;
            margin-left: 10px;
        }

        /* tech stack chips */
        .tech-stack {
            display: flex;
            flex-wrap: wrap;
            gap: 12px;
            margin: 20px 0 10px;
        }

        .tech-badge {
            background: #1f2c3f;
            border: 1px solid #314b6b;
            color: #c3d2ff;
            padding: 8px 22px;
            border-radius: 60px;
            font-weight: 500;
            font-size: 0.95rem;
            backdrop-filter: blur(4px);
            box-shadow: 0 2px 0 #0f172a;
        }

        /* feature list (two columns) */
        .feature-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
            gap: 14px;
            margin: 15px 0 5px;
        }

        .feature-item {
            background: #151e2b;
            border-radius: 20px;
            padding: 0.9rem 1.3rem;
            border-left: 6px solid #3f6aff;
            display: flex;
            align-items: center;
            gap: 10px;
            color: #d5e0f5;
            font-weight: 450;
        }

        .feature-item::before {
            content: "▹";
            color: #6d8aff;
            font-size: 1.5rem;
            line-height: 1;
        }

        /* image / screenshot */
        .dashboard-screenshot {
            margin: 30px 0 20px;
            border-radius: 28px;
            overflow: hidden;
            border: 2px solid #2b3b57;
            background: #0e1623;
            box-shadow: 0 20px 30px -10px black;
        }

        .dashboard-screenshot img {
            width: 100%;
            height: auto;
            display: block;
            transition: transform 0.2s;
        }

        .dashboard-screenshot img:hover {
            transform: scale(1.01);
        }

        .img-caption {
            text-align: center;
            padding: 12px;
            color: #9eb1d0;
            font-size: 0.95rem;
            border-top: 1px solid #253040;
            background: #101826;
        }

        /* insights grid */
        .insights-list {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 14px;
            margin: 20px 0 25px;
        }

        .insight-bullet {
            background: #131c2b;
            border-radius: 18px;
            padding: 0.9rem 1.5rem;
            border: 1px solid #2a3850;
            display: flex;
            align-items: center;
            gap: 12px;
            font-size: 1rem;
        }

        .insight-bullet::before {
            content: "📌";
            filter: drop-shadow(0 2px 2px black);
            font-size: 1.2rem;
        }

        /* author footer */
        .author-footer {
            margin-top: 40px;
            background: linear-gradient(145deg, #121b29, #0d1420);
            padding: 1.8rem 2rem;
            border-radius: 40px;
            display: flex;
            flex-wrap: wrap;
            align-items: center;
            justify-content: space-between;
            border: 1px solid #2e3d5b;
        }

        .author-info {
            display: flex;
            align-items: center;
            gap: 20px;
        }

        .author-avatar {
            width: 58px;
            height: 58px;
            background: #22303f;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 2rem;
            border: 2px solid #5b7eff;
        }

        .author-details h4 {
            margin: 0 0 4px;
            font-size: 1.4rem;
            font-weight: 500;
            color: white;
        }

        .author-details p {
            margin: 0;
            color: #98abcf;
        }

        .author-links a {
            color: #b7c7ff;
            text-decoration: none;
            font-weight: 500;
            padding: 10px 18px;
            border-radius: 40px;
            background: #1f2c40;
            border: 1px solid #3c4e72;
            margin-left: 10px;
            transition: 0.15s;
            display: inline-block;
        }

        .author-links a:hover {
            background: #2a3b58;
            border-color: #6d8eff;
            color: white;
        }

        /* data source box */
        .data-source {
            background: #111b28;
            border-radius: 20px;
            padding: 1rem 1.8rem;
            border: 1px dashed #486291;
            display: inline-block;
            font-family: monospace;
            font-size: 1rem;
            color: #bbd0ff;
            margin: 15px 0 5px;
        }

        hr {
            border: 1px solid #253040;
            margin: 30px 0 10px;
        }

        /* emoji icons inline */
        .emoji-large {
            font-size: 2rem;
            filter: drop-shadow(2px 4px 4px #00000060);
        }

        @media (max-width: 600px) {
            .hr-title { font-size: 2rem; }
            .kpi-item { padding: 0.8rem 1rem; }
            .insights-list { grid-template-columns: 1fr; }
            .author-footer { flex-direction: column; align-items: start; gap: 20px; }
        }
    </style>
</head>
<body>
<!-- #################################################################### -->
<!-- This HTML snippet is designed for your GitHub README – dark, unique, -->
<!-- dashboard style. Replace placeholder links if needed.               -->
<!-- #################################################################### -->

<div class="hr-dashboard-card">

    <!-- main title with icon -->
    <div class="hr-title">
        <span class="emoji-large">📊</span> HR ANALYTICS DASHBOARD
    </div>
    <div class="hr-subhead">
        🧠 interactive attrition & workforce intelligence · Power BI
    </div>

    <!-- KPI cards (summary numbers) -->
    <div class="kpi-grid">
        <div class="kpi-item">
            <div class="kpi-label">👥 total employees</div>
            <div class="kpi-value">1,470</div>
        </div>
        <div class="kpi-item">
            <div class="kpi-label">🚪 attrition</div>
            <div class="kpi-value">237 <small>exits</small></div>
        </div>
        <div class="kpi-item">
            <div class="kpi-label">📉 attrition rate</div>
            <div class="kpi-value">16.1%</div>
        </div>
        <div class="kpi-item">
            <div class="kpi-label">⚖️ avg age</div>
            <div class="kpi-value">37</div>
        </div>
        <div class="kpi-item">
            <div class="kpi-label">💰 avg salary</div>
            <div class="kpi-value">6.5k <small>USD</small></div>
        </div>
        <div class="kpi-item">
            <div class="kpi-label">⏳ avg tenure</div>
            <div class="kpi-value">7.0 <small>yrs</small></div>
        </div>
    </div>

    <!-- tech stack (like badges) -->
    <div class="tech-stack">
        <span class="tech-badge">⚡ Power BI Desktop</span>
        <span class="tech-badge">📁 Excel / CSV</span>
        <span class="tech-badge">📐 DAX measures</span>
        <span class="tech-badge">🔄 Power Query</span>
        <span class="tech-badge">🧹 data cleaning</span>
        <span class="tech-badge">🎛️ interactive filters</span>
    </div>

    <!-- data source -->
    <div class="data-source">
        📂 HR_Analytics.csv · 1470 records · 35+ attributes
    </div>

    <!-- section: features -->
    <div class="section-header">
        ✨ features & highlights <span>dynamic</span>
    </div>
    <div class="feature-grid">
        <div class="feature-item">KPI cards (total employees, attrition, rate, age, salary)</div>
        <div class="feature-item">attrition by age group (26‑35 spike)</div>
        <div class="feature-item">department filter — HR, R&D, Sales</div>
        <div class="feature-item">job role & salary slab breakdown</div>
        <div class="feature-item">education & gender attrition</div>
        <div class="feature-item">job satisfaction by role</div>
        <div class="feature-item">attrition trend by years at company</div>
        <div class="feature-item">dark‑theme professional layout</div>
    </div>

    <!-- screenshot / demo area -->
    <div class="section-header">
        🖼️ dashboard preview <span>live view</span>
    </div>
    <div class="dashboard-screenshot">
        <!-- update the raw image url if needed (use your actual raw link) -->
        <img src="https://raw.githubusercontent.com/santunandi95/HR-Analytics-Dashboard-Powerbi/main/HR_Analysis_Dashboard.png"
             alt="HR Analytics Dashboard Screenshot"
             onerror="this.onerror=null; this.src='https://via.placeholder.com/1000x500?text=Dashboard+Preview+Image'; this.style.opacity='0.8'">
        <div class="img-caption">
            ⚡ interactive dashboard — attrition overview, slicers, demographic insights
        </div>
    </div>

    <!-- insights gained (core findings) -->
    <div class="section-header">
        📈 key insights <span>data driven</span>
    </div>
    <div class="insights-list">
        <div class="insight-bullet">Highest attrition in <strong>26–35 age group</strong></div>
        <div class="insight-bullet">Salary ≤5K → max turnover risk</div>
        <div class="insight-bullet">Lab technicians & sales executives lead attrition</div>
        <div class="insight-bullet">Early‑tenure employees (<2 yrs) more likely to leave</div>
        <div class="insight-bullet">Life Sciences education shows notable attrition share</div>
        <div class="insight-bullet">Job satisfaction lower among frequent attrition roles</div>
    </div>

    <!-- extra bullet: department filter hint -->
    <div style="display: flex; gap: 10px; flex-wrap: wrap; margin-top: 5px; color: #afc1e3;">
        <span style="background: #1f2d40; border-radius: 30px; padding: 6px 20px;">🔵 HR dept filter</span>
        <span style="background: #1f2d40; border-radius: 30px; padding: 6px 20px;">🟢 R&D</span>
        <span style="background: #1f2d40; border-radius: 30px; padding: 6px 20px;">🟠 Sales</span>
        <span style="background: #1f2d40; border-radius: 30px; padding: 6px 20px;">📅 years with company</span>
    </div>

    <!-- horizontal rule for separation -->
    <hr>

    <!-- author section (santu nandi) with links -->
    <div class="author-footer">
        <div class="author-info">
            <div class="author-avatar">🧑‍💻</div>
            <div class="author-details">
                <h4>Santu Nandi</h4>
                <p>Data Analytics & AI · Generative AI explorer</p>
            </div>
        </div>
        <div class="author-links">
            <a href="https://github.com/santunandi95" target="_blank">🐙 GitHub Profile</a>
            <a href="#" target="_blank">📊 Power BI Projects</a>
            <!-- ^ update '#' with your actual portfolio/powerbi link -->
        </div>
    </div>

    <!-- tiny footer note -->
    <div style="text-align: right; margin-top: 20px; color: #485b7e; font-size: 0.8rem; border-top: 1px dashed #1b2537; padding-top: 12px;">
        HR Analytics Dashboard · built with Power BI · dark theme
    </div>

</div>

<!-- additional note: image fallback if raw url doesn't work, replace with your own raw.githubusercontent path -->
</body>
</html>
