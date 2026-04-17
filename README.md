<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
    <title>母親節團隊競賽 · 限動起承轉合+2</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: system-ui, 'Segoe UI', 'Helvetica Neue', 'Noto Sans', sans-serif;
        }

        body {
            background: linear-gradient(145deg, #fff9f0 0%, #ffe6d5 100%);
            min-height: 100vh;
            padding: 20px 16px 60px;
        }

        .container {
            max-width: 1500px;
            margin: 0 auto;
        }

        /* 頂部比分條 - 柔和淺色 */
        .score-bar {
            background: linear-gradient(135deg, #ffe9e0, #ffd9c8);
            border-radius: 60px;
            padding: 14px 24px;
            margin-bottom: 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 16px;
            color: #7b4a38;
            box-shadow: 0 4px 12px rgba(0,0,0,0.05);
            border: 1px solid #ffcdb3;
        }
        .team-score-compact {
            display: flex;
            align-items: baseline;
            gap: 20px;
            background: rgba(255,245,235,0.7);
            padding: 6px 20px;
            border-radius: 48px;
        }
        .team-compact {
            text-align: center;
        }
        .team-compact .name {
            font-weight: 600;
            font-size: 0.85rem;
            color: #b45f48;
        }
        .team-compact .points {
            font-size: 2rem;
            font-weight: 800;
            line-height: 1;
            color: #c25b3c;
        }
        .vs {
            font-size: 1.1rem;
            font-weight: bold;
            margin: 0 6px;
            color: #cc886e;
        }
        .leader-info {
            background: #fff2e8;
            padding: 6px 18px;
            border-radius: 40px;
            color: #a35134;
            font-weight: bold;
            font-size: 0.9rem;
            box-shadow: inset 0 0 0 1px #ffe0ce;
        }

        /* 倒數計時區 */
        .countdown-area {
            background: #fff3ea;
            border-radius: 60px;
            padding: 12px 24px;
            margin-bottom: 20px;
            text-align: center;
            border: 1px solid #ffd5be;
            box-shadow: 0 2px 8px rgba(0,0,0,0.03);
        }
        .countdown-title {
            font-size: 0.85rem;
            font-weight: 600;
            color: #c47a5e;
            letter-spacing: 1px;
        }
        .countdown-number {
            font-size: 2rem;
            font-weight: 800;
            color: #dc6b4a;
            line-height: 1.2;
        }
        .countdown-sub {
            font-size: 0.7rem;
            color: #b28b78;
        }

        .hero {
            text-align: center;
            margin-bottom: 20px;
        }
        .hero h1 {
            font-size: 2rem;
            color: #b3413a;
            text-shadow: 2px 2px 0 #ffd9c5;
        }
        .sub {
            color: #b97f6e;
            background: #fff4e6;
            display: inline-block;
            padding: 5px 18px;
            border-radius: 40px;
            font-size: 0.85rem;
        }

        /* 加分工具列 */
        .action-bar {
            background: #fff8f0;
            border-radius: 60px;
            padding: 16px 24px;
            margin: 20px 0 32px;
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 12px;
            box-shadow: 0 6px 14px rgba(0,0,0,0.05);
            border: 1px solid #ffddcc;
        }
        .action-btn {
            background: #ffede3;
            border: none;
            padding: 10px 20px;
            border-radius: 48px;
            font-weight: 700;
            font-size: 0.9rem;
            color: #b14534;
            cursor: pointer;
            transition: all 0.2s;
            box-shadow: 0 1px 3px rgba(0,0,0,0.05);
        }
        .action-btn:hover {
            background: #ffd5be;
            transform: translateY(-2px);
        }
        .action-btn.special {
            background: #ffe0cf;
            color: #c25a3e;
        }

        .teams-grid {
            display: flex;
            flex-wrap: wrap;
            gap: 28px;
            margin-bottom: 48px;
        }
        .team-card {
            flex: 1;
            min-width: 340px;
            background: white;
            border-radius: 48px;
            box-shadow: 0 20px 35px -12px rgba(0,0,0,0.2);
            overflow: hidden;
            border: 1px solid #ffd5be;
        }
        .team-header {
            padding: 20px 24px 12px;
            background: #fff7f0;
            border-bottom: 3px solid #ffbe9f;
        }
        .team-name-input {
            font-size: 1.7rem;
            font-weight: 800;
            background: transparent;
            border: none;
            width: 100%;
            padding: 4px 0;
            color: #772e26;
        }
        .team-name-input:focus {
            outline: none;
            border-bottom: 2px dashed #ff8a5c;
        }
        .punish-area {
            margin-top: 12px;
            display: flex;
            align-items: center;
            gap: 8px;
            flex-wrap: wrap;
            background: #ffefe3;
            padding: 8px 12px;
            border-radius: 32px;
        }
        .punish-label {
            font-size: 0.7rem;
            font-weight: bold;
            background: #e7b89c;
            padding: 4px 12px;
            border-radius: 30px;
            color: white;
        }
        .punish-text {
            flex: 1;
            border: none;
            background: transparent;
            padding: 6px 0;
            font-size: 0.85rem;
            color: #8b4b3a;
        }

        .team-score {
            padding: 16px 24px;
            background: #fff3ea;
            text-align: center;
        }
        .score-number {
            font-size: 3.5rem;
            font-weight: 800;
            color: #dc6b4a;
        }

        .members-section {
            padding: 18px 20px;
            background: #fffaf5;
            border-top: 1px solid #ffe2d0;
            border-bottom: 1px solid #ffe2d0;
        }
        .members-title {
            font-weight: 700;
            color: #c47a5e;
            font-size: 0.9rem;
            margin-bottom: 12px;
            display: flex;
            justify-content: space-between;
            align-items: baseline;
        }
        .member-list {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            margin-bottom: 16px;
        }
        .member-chip {
            background: #fff1e8;
            border-radius: 40px;
            padding: 6px 14px;
            display: inline-flex;
            align-items: center;
            gap: 8px;
            font-size: 0.85rem;
            font-weight: 500;
            color: #7b3d2c;
            box-shadow: 0 1px 2px rgba(0,0,0,0.05);
        }
        .member-today-score {
            background: #ecc7b6;
            border-radius: 30px;
            padding: 2px 10px;
            font-size: 0.7rem;
            font-weight: bold;
        }
        .delete-member {
            background: none;
            border: none;
            cursor: pointer;
            color: #c27e64;
            font-weight: bold;
            font-size: 1rem;
            margin-left: 4px;
        }
        .add-member-form {
            display: flex;
            gap: 8px;
            margin-top: 12px;
            background: #fff0e6;
            padding: 12px 12px;
            border-radius: 60px;
        }
        .add-member-input {
            flex: 1;
            border: 1px solid #ffcfb5;
            border-radius: 60px;
            padding: 10px 16px;
            background: white;
            font-size: 0.9rem;
        }
        .add-member-btn {
            background: #e07a5f;
            border: none;
            border-radius: 60px;
            padding: 8px 20px;
            font-weight: bold;
            color: white;
            cursor: pointer;
            transition: 0.2s;
        }
        .add-member-btn:hover {
            background: #c05e44;
        }

        /* 備用表單 */
        .form-panel {
            background: white;
            border-radius: 48px;
            padding: 24px;
            margin-bottom: 48px;
            border: 1px solid #ffddcc;
        }
        .form-title {
            font-weight: bold;
            margin-bottom: 16px;
            color: #b54733;
        }
        .form-grid {
            display: flex;
            flex-wrap: wrap;
            gap: 16px;
            align-items: flex-end;
        }
        .input-group {
            flex: 1;
            min-width: 150px;
        }
        .input-group label {
            font-size: 0.7rem;
            font-weight: 600;
            color: #c27156;
        }
        select, input {
            width: 100%;
            padding: 10px 14px;
            border-radius: 48px;
            border: 1.5px solid #ffd5be;
            background: #fffcf8;
        }
        .btn-primary {
            background: #e07a5f;
            border: none;
            padding: 10px 24px;
            border-radius: 48px;
            color: white;
            font-weight: bold;
            cursor: pointer;
        }
        .rule-hint {
            background: #fff2e6;
            border-radius: 28px;
            padding: 10px 16px;
            margin-top: 16px;
            font-size: 0.7rem;
            display: flex;
            flex-wrap: wrap;
            gap: 12px;
        }
        .log-section {
            background: #fffef7;
            border-radius: 48px;
            padding: 20px;
        }
        .log-header {
            display: flex;
            justify-content: space-between;
            flex-wrap: wrap;
            margin-bottom: 16px;
        }
        table {
            width: 100%;
            border-collapse: collapse;
        }
        th, td {
            text-align: left;
            padding: 10px 6px;
            border-bottom: 1px solid #ffdfcf;
            font-size: 0.85rem;
        }
        .delete-log {
            background: none;
            border: none;
            cursor: pointer;
            color: #e6947a;
        }
        .footer-note {
            text-align: center;
            margin-top: 28px;
            font-size: 0.7rem;
            color: #b28b78;
        }
        @media (max-width: 780px) {
            .teams-grid { flex-direction: column; }
            .score-bar { flex-direction: column; align-items: stretch; text-align: center; }
            .action-bar { justify-content: center; }
            .countdown-number { font-size: 1.5rem; }
        }
    </style>
</head>
<body>
<div class="container">
    <!-- 頂部即時比分條 -->
    <div class="score-bar" id="scoreBar"></div>

    <!-- 倒數計時區 -->
    <div class="countdown-area" id="countdownArea">
        <div class="countdown-title">⏳ 比賽衝刺倒數</div>
        <div class="countdown-number" id="countdownNumber">-- 天</div>
        <div class="countdown-sub">活動期間：2026/4/18 ～ 2026/5/11</div>
    </div>

    <div class="hero">
        <h1>🌸 母親節團隊激戰 🌸</h1>
        <div class="sub">🏆 贏家3000元 · 輸家自我懲罰</div>
    </div>

    <!-- 加分工具列（新增「起承轉合+2」） -->
    <div class="action-bar">
        <button class="action-btn" data-type="1">① 發限動 (置入產品) +1</button>
        <button class="action-btn" data-type="2">② 限動起承轉合 +2</button>
        <button class="action-btn" data-type="3">③ 有人詢問 +3</button>
        <button class="action-btn" data-type="4">④ 成交 +4</button>
        <button class="action-btn" data-type="5">⑤ 發Reels +5</button>
        <button class="action-btn special" data-type="6">⑥ 全組都有發 +6</button>
        <button class="action-btn" data-type="7">⑦ 提供素材 +7</button>
    </div>

    <div class="teams-grid" id="teamsGrid"></div>

    <!-- 備用管理員表單 -->
    <div class="form-panel">
        <div class="form-title">📋 詳細加分表單 (備用)</div>
        <div class="form-grid">
            <div class="input-group">
                <label>團隊</label>
                <select id="teamSelectForm">
                    <option value="A">左隊</option>
                    <option value="B">右隊</option>
                </select>
            </div>
            <div class="input-group">
                <label>成員</label>
                <select id="memberSelectForm">
                    <option value="">-- 請選擇 --</option>
                </select>
            </div>
            <div class="input-group">
                <label>加分項目</label>
                <select id="actionTypeForm">
                    <option value="1">① 發限動 (置入產品) +1 (每日限1次)</option>
                    <option value="2">② 限動起承轉合 +2 (每日限1次，與①擇一)</option>
                    <option value="3">③ 有人詢問 +3</option>
                    <option value="4">④ 成交 +4</option>
                    <option value="5">⑤ 發Reels +5</option>
                    <option value="6">⑥ 全組每人發限動 +6</option>
                    <option value="7">⑦ 分享素材 +7</option>
                </select>
            </div>
            <div class="input-group">
                <button class="btn-primary" id="addRecordBtn">✨ 新增加分</button>
            </div>
        </div>
        <div class="rule-hint">
            <span>📌 ① & ② 每人每日僅能擇一獲得 (限動相關)</span>
            <span>👥 ⑥ 全組加分不需選成員</span>
            <span>📊 隊員今日貢獻顯示在名字旁</span>
        </div>
    </div>

    <div class="log-section">
        <div class="log-header">
            <h3>📋 近期加分紀錄</h3>
            <button class="btn-sm" id="resetAllDataBtn" style="background:#ffdad0; border:none; padding:6px 16px; border-radius:40px;">🗑️ 重置全部</button>
        </div>
        <div style="overflow-x: auto;">
            <table>
                <thead><tr><th>時間</th><th>團隊</th><th>成員</th><th>項目</th><th>分數</th><th></th></thead>
                <tbody id="logBody"></tbody>
            </table>
        </div>
    </div>
    <div class="footer-note">✨ 點擊隊員旁的「✖」可刪除隊員 | 團隊名稱/懲罰可直接點擊修改 | 所有資料自動儲存</div>
</div>

<script>
    const STORAGE_KEY = "mother_day_contest_v5";
    let appData = {
        teams: {
            A: { name: "愛心媽咪隊", punish: "輸家請喝珍奶", members: ["小美", "阿華", "小莉"] },
            B: { name: "甜心寶貝隊", punish: "輸家跳舞影片", members: ["大雄", "靜香", "胖虎"] }
        },
        logs: []
    };

    // 倒數計時目標日期 (2026/5/11 23:59:59)
    const END_DATE = new Date(2026, 4, 11, 23, 59, 59);

    function updateCountdown() {
        const now = new Date();
        const diffMs = END_DATE - now;
        const diffDays = Math.ceil(diffMs / (1000 * 60 * 60 * 24));
        const countdownEl = document.getElementById('countdownNumber');
        if (!countdownEl) return;
        if (diffMs <= 0) {
            countdownEl.innerText = "比賽已結束";
        } else {
            countdownEl.innerText = `${diffDays} 天`;
        }
    }
    setInterval(updateCountdown, 1000);

    function saveToLocal() { localStorage.setItem(STORAGE_KEY, JSON.stringify(appData)); }
    function loadFromLocal() {
        const raw = localStorage.getItem(STORAGE_KEY);
        if (raw) {
            try { const p = JSON.parse(raw); if (p.teams && p.logs) appData = p; } catch(e) {}
        }
        if (!appData.teams) appData.teams = { A: { name: "愛心媽咪隊", punish: "輸家請喝珍奶", members: ["小美","阿華","小莉"] }, B: { name: "甜心寶貝隊", punish: "輸家跳舞影片", members: ["大雄","靜香","胖虎"] } };
        if (!appData.teams.A.members) appData.teams.A.members = ["小美","阿華","小莉"];
        if (!appData.teams.B.members) appData.teams.B.members = ["大雄","靜香","胖虎"];
        if (!appData.logs) appData.logs = [];
        saveToLocal();
    }
    function getTodayStr() { const d = new Date(); return `${d.getFullYear()}-${String(d.getMonth()+1).padStart(2,'0')}-${String(d.getDate()).padStart(2,'0')}`; }

    // 檢查同一人今天是否已經有過限動相關加分 (type 1 或 2)
    function hasTodayLimitStory(team, member, today) {
        return appData.logs.some(l => l.team === team && l.member === member && l.date === today && (l.type === 1 || l.type === 2));
    }

    function hasTodayTeamBonus6(team, today) { // 原 type 5 變成 type 6 (全組)
        return appData.logs.some(l => l.team === team && l.type === 6 && l.date === today);
    }

    function getMemberTodayScore(team, member, today) {
        return appData.logs.filter(l => l.team === team && l.member === member && l.date === today && l.type !== 6).reduce((s,l)=>s+l.points,0);
    }
    function computeTeamScore(team) { return appData.logs.filter(l=>l.team===team).reduce((s,l)=>s+l.points,0); }

    function addRecord(team, member, typeVal) {
        const type = parseInt(typeVal,10);
        // 分數對應: type 1:+1, 2:+2, 3:+3, 4:+4, 5:+5, 6:+6, 7:+7
        const pointsMap = {1:1, 2:2, 3:3, 4:4, 5:5, 6:6, 7:7};
        const points = pointsMap[type];
        if (!points) return { success: false, msg: "錯誤項目" };
        const today = getTodayStr();

        // 個人加分需選擇成員
        if (type !== 6) {
            if (!member) return { success: false, msg: "請選擇成員" };
            const membersList = appData.teams[team].members;
            if (!membersList.includes(member)) return { success: false, msg: `❌ ${member} 不是該團隊成員` };
        }

        // 限動相關 (type 1 或 2) 互斥，一天只能擇一
        if (type === 1 || type === 2) {
            if (hasTodayLimitStory(team, member, today)) {
                return { success: false, msg: `⚠️ ${member} 今日已有限動加分 (一般或起承轉合)，每人每日限一次` };
            }
        }

        // 全組加分 (type 6)
        if (type === 6) {
            if (member && member !== "") return { success: false, msg: "全組加分不需選成員" };
            if (hasTodayTeamBonus6(team, today)) return { success: false, msg: "今日已用過全組加分" };
        }

        const newLog = {
            id: Date.now() + Math.random(),
            team: team,
            member: (type === 6) ? "全組行動" : member,
            type: type,
            points: points,
            date: today,
            timestamp: Date.now()
        };
        appData.logs.unshift(newLog);
        saveToLocal();
        renderAll();
        return { success: true, msg: `✅ +${points}分 (${type===6?'團隊':member})` };
    }

    function deleteLog(id) { appData.logs = appData.logs.filter(l=>l.id!==id); saveToLocal(); renderAll(); }
    function resetAll() { if(confirm("⚠️ 重置所有數據？")) { appData = { teams: { A: { name:"愛心媽咪隊", punish:"輸家請喝珍奶", members:["小美","阿華","小莉"] }, B: { name:"甜心寶貝隊", punish:"輸家跳舞影片", members:["大雄","靜香","胖虎"] } }, logs: [] }; saveToLocal(); renderAll(); } }
    function addMember(team, name) { name = name.trim(); if(!name) return false; if(appData.teams[team].members.includes(name)) return false; appData.teams[team].members.push(name); saveToLocal(); renderAll(); return true; }
    function removeMember(team, name) { if(appData.teams[team].members.length<=1) { alert("至少保留一名隊員"); return false; } appData.teams[team].members = appData.teams[team].members.filter(m=>m!==name); saveToLocal(); renderAll(); return true; }
    function updateTeamName(team, newName) { appData.teams[team].name = newName; saveToLocal(); renderAll(); }
    function updateTeamPunish(team, newPunish) { appData.teams[team].punish = newPunish; saveToLocal(); renderAll(); }

    function renderTopScoreBar() {
        const scoreA = computeTeamScore('A');
        const scoreB = computeTeamScore('B');
        const leader = scoreA > scoreB ? appData.teams.A.name : (scoreB > scoreA ? appData.teams.B.name : "平手");
        const diff = Math.abs(scoreA-scoreB);
        const bar = document.getElementById('scoreBar');
        bar.innerHTML = `
            <div class="team-score-compact">
                <div class="team-compact"><div class="name">${escapeHtml(appData.teams.A.name)}</div><div class="points">${scoreA}</div></div>
                <span class="vs">VS</span>
                <div class="team-compact"><div class="name">${escapeHtml(appData.teams.B.name)}</div><div class="points">${scoreB}</div></div>
            </div>
            <div class="leader-info">🏆 ${leader} ${scoreA!==scoreB ? `領先 ${diff} 分` : "雙方平手"}</div>
        `;
    }

    function renderTeams() {
        const grid = document.getElementById('teamsGrid');
        const today = getTodayStr();
        const renderMemberList = (teamLetter, teamKey) => {
            const members = appData.teams[teamKey].members;
            let html = '<div class="member-list">';
            members.forEach(m => {
                const todayScore = getMemberTodayScore(teamLetter, m, today);
                html += `<div class="member-chip">
                            ${escapeHtml(m)}
                            <span class="member-today-score">📅 今日 +${todayScore}</span>
                            <button class="delete-member" data-team="${teamLetter}" data-member="${escapeHtml(m)}">✖</button>
                         </div>`;
            });
            html += '</div>';
            html += `<div class="add-member-form">
                        <input type="text" class="add-member-input" id="newMember${teamLetter}" placeholder="新隊員名字" autocomplete="off">
                        <button class="add-member-btn" data-team="${teamLetter}">➕ 新增隊員</button>
                     </div>`;
            return html;
        };

        grid.innerHTML = `
            <div class="team-card">
                <div class="team-header">
                    <input type="text" class="team-name-input" id="teamAName" value="${escapeHtml(appData.teams.A.name)}">
                    <div class="punish-area"><span class="punish-label">😈 自我懲罰</span><input type="text" class="punish-text" id="teamAPunish" value="${escapeHtml(appData.teams.A.punish)}"></div>
                </div>
                <div class="team-score"><div class="score-number">${computeTeamScore('A')}</div><div>團隊總分</div></div>
                <div class="members-section"><div class="members-title">👥 隊員名單 (今日貢獻)</div>${renderMemberList('A','A')}</div>
            </div>
            <div class="team-card">
                <div class="team-header">
                    <input type="text" class="team-name-input" id="teamBName" value="${escapeHtml(appData.teams.B.name)}">
                    <div class="punish-area"><span class="punish-label">😈 自我懲罰</span><input type="text" class="punish-text" id="teamBPunish" value="${escapeHtml(appData.teams.B.punish)}"></div>
                </div>
                <div class="team-score"><div class="score-number">${computeTeamScore('B')}</div><div>團隊總分</div></div>
                <div class="members-section"><div class="members-title">👥 隊員名單 (今日貢獻)</div>${renderMemberList('B','B')}</div>
            </div>
        `;

        document.getElementById('teamAName')?.addEventListener('change', e=>updateTeamName('A', e.target.value));
        document.getElementById('teamAPunish')?.addEventListener('change', e=>updateTeamPunish('A', e.target.value));
        document.getElementById('teamBName')?.addEventListener('change', e=>updateTeamName('B', e.target.value));
        document.getElementById('teamBPunish')?.addEventListener('change', e=>updateTeamPunish('B', e.target.value));

        document.querySelectorAll('.add-member-btn').forEach(btn => {
            btn.addEventListener('click', (e) => {
                const team = btn.getAttribute('data-team');
                const input = document.getElementById(`newMember${team}`);
                const newName = input.value.trim();
                if(newName) { if(addMember(team, newName)) input.value=''; else alert('隊員已存在'); }
                else alert('請輸入名稱');
            });
        });
        document.querySelectorAll('.delete-member').forEach(btn => {
            btn.addEventListener('click', (e) => {
                const team = btn.getAttribute('data-team');
                const member = btn.getAttribute('data-member');
                if(confirm(`刪除隊員「${member}」？`)) removeMember(team, member);
            });
        });
    }

    function renderLogTable() {
        const tbody = document.getElementById('logBody');
        if(!tbody) return;
        if(appData.logs.length===0) { tbody.innerHTML='<tr><td colspan="6" style="text-align:center">暫無紀錄</td></tr>'; return; }
        let html='';
        const typeMap = {1:'①限動+1',2:'②起承轉合+2',3:'③詢問+3',4:'④成交+4',5:'⑤Reels+5',6:'⑥全組+6',7:'⑦素材+7'};
        for(let log of appData.logs) {
            const teamName = log.team==='A'? appData.teams.A.name : appData.teams.B.name;
            const timeStr = new Date(log.timestamp).toLocaleString('zh-TW');
            html+=`<tr><td style="white-space:nowrap">${escapeHtml(timeStr)}</td><td><span class="badge" style="background:#fce5d8;padding:2px 10px;">${escapeHtml(teamName)}</span></td><td>${escapeHtml(log.member||'—')}</td><td>${typeMap[log.type]}</td><td>+${log.points}</td><td><button class="delete-log" data-id="${log.id}">🗑️</button></td></tr>`;
        }
        tbody.innerHTML = html;
        document.querySelectorAll('.delete-log').forEach(btn => {
            btn.addEventListener('click', (e) => { const id = parseInt(btn.getAttribute('data-id'),10); if(confirm('刪除此筆？')) deleteLog(id); });
        });
    }

    function showAddDialog(type) {
        if (type === 6) { // 全組加分
            const teamKey = prompt("請選擇團隊：\n輸入 A 或 B\nA = 左隊\nB = 右隊");
            if (!teamKey) return;
            const team = teamKey.toUpperCase() === 'A' ? 'A' : (teamKey.toUpperCase() === 'B' ? 'B' : null);
            if (!team) { alert("請輸入 A 或 B"); return; }
            const res = addRecord(team, "", "6");
            alert(res.msg);
        } else {
            const teamKey = prompt("請選擇團隊：\n輸入 A 或 B\nA = 左隊\nB = 右隊");
            if (!teamKey) return;
            const team = teamKey.toUpperCase() === 'A' ? 'A' : (teamKey.toUpperCase() === 'B' ? 'B' : null);
            if (!team) { alert("請輸入 A 或 B"); return; }
            const members = appData.teams[team].members;
            if (!members.length) { alert("此團隊尚無隊員，請先新增隊員"); return; }
            const listStr = members.map((m,i)=>`${i+1}. ${m}`).join('\n');
            const input = prompt(`請選擇成員 (輸入數字或名稱)\n${listStr}`);
            if (!input) return;
            let selected = null;
            if (!isNaN(parseInt(input))) { let idx=parseInt(input)-1; if(idx>=0 && idx<members.length) selected=members[idx]; }
            else { if(members.includes(input.trim())) selected=input.trim(); }
            if (!selected) { alert(`請從: ${members.join(', ')} 中選擇`); return; }
            const res = addRecord(team, selected, type.toString());
            alert(res.msg);
        }
    }

    function bindQuickActions() {
        const btns = document.querySelectorAll('.action-btn');
        btns.forEach(btn => {
            btn.addEventListener('click', (e) => {
                const type = parseInt(btn.getAttribute('data-type'), 10);
                showAddDialog(type);
            });
        });
    }

    function updateMemberSelectForm() {
        const teamSelect = document.getElementById('teamSelectForm');
        const memberSelect = document.getElementById('memberSelectForm');
        const members = appData.teams[teamSelect.value].members || [];
        memberSelect.innerHTML = '<option value="">-- 請選擇成員 --</option>' + members.map(m=>`<option value="${escapeHtml(m)}">${escapeHtml(m)}</option>`).join('');
    }

    function bindForm() {
        const teamSelect = document.getElementById('teamSelectForm');
        const addBtn = document.getElementById('addRecordBtn');
        const memberSelect = document.getElementById('memberSelectForm');
        const actionSelect = document.getElementById('actionTypeForm');
        teamSelect.addEventListener('change', ()=>updateMemberSelectForm());
        updateMemberSelectForm();
        addBtn.addEventListener('click', ()=>{
            const team = teamSelect.value;
            let member = memberSelect.value;
            const action = actionSelect.value;
            if(parseInt(action)!==6 && !member) { alert("請選擇成員"); return; }
            const res = addRecord(team, member, action);
            alert(res.msg);
        });
        document.getElementById('resetAllDataBtn')?.addEventListener('click', resetAll);
    }

    function renderAll() {
        renderTopScoreBar();
        renderTeams();
        renderLogTable();
        bindQuickActions();
        bindForm();
        updateCountdown();
    }

    loadFromLocal();
    renderAll();
    function escapeHtml(str) { if(!str) return ''; return str.replace(/[&<>]/g, function(m){ if(m==='&') return '&amp;'; if(m==='<') return '&lt;'; if(m==='>') return '&gt;'; return m;}); }
</script>
</body>
</html>
