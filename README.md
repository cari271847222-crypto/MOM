<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=yes, viewport-fit=cover">
    <title>母親節團隊競賽 · 手機版</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: system-ui, -apple-system, 'Segoe UI', 'Helvetica Neue', 'Noto Sans', sans-serif;
        }

        body {
            background: linear-gradient(145deg, #fff9f0 0%, #ffe6d5 100%);
            min-height: 100vh;
            padding: 16px 12px 40px;
        }

        .container {
            max-width: 600px;
            margin: 0 auto;
        }

        /* 頂部比分條 */
        .score-bar {
            background: linear-gradient(135deg, #ffe9e0, #ffd9c8);
            border-radius: 40px;
            padding: 12px 16px;
            margin-bottom: 16px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 12px;
            color: #7b4a38;
            box-shadow: 0 4px 12px rgba(0,0,0,0.05);
            border: 1px solid #ffcdb3;
        }
        .team-score-compact {
            display: flex;
            align-items: baseline;
            gap: 12px;
            background: rgba(255,245,235,0.7);
            padding: 4px 16px;
            border-radius: 40px;
        }
        .team-compact {
            text-align: center;
        }
        .team-compact .name {
            font-weight: 600;
            font-size: 0.7rem;
            color: #b45f48;
        }
        .team-compact .points {
            font-size: 1.6rem;
            font-weight: 800;
            line-height: 1;
            color: #c25b3c;
        }
        .vs {
            font-size: 0.9rem;
            font-weight: bold;
            margin: 0 4px;
            color: #cc886e;
        }
        .leader-info {
            background: #fff2e8;
            padding: 4px 12px;
            border-radius: 30px;
            color: #a35134;
            font-weight: bold;
            font-size: 0.75rem;
            box-shadow: inset 0 0 0 1px #ffe0ce;
        }

        /* 倒數計時 */
        .countdown-area {
            background: #fff3ea;
            border-radius: 40px;
            padding: 10px 16px;
            margin-bottom: 16px;
            text-align: center;
            border: 1px solid #ffd5be;
        }
        .countdown-title {
            font-size: 0.7rem;
            font-weight: 600;
            color: #c47a5e;
        }
        .countdown-number {
            font-size: 1.6rem;
            font-weight: 800;
            color: #dc6b4a;
            line-height: 1.2;
        }
        .countdown-sub {
            font-size: 0.6rem;
            color: #b28b78;
        }

        .hero {
            text-align: center;
            margin-bottom: 16px;
        }
        .hero h1 {
            font-size: 1.6rem;
            color: #b3413a;
            text-shadow: 1px 1px 0 #ffd9c5;
        }
        .sub {
            color: #b97f6e;
            background: #fff4e6;
            display: inline-block;
            padding: 4px 14px;
            border-radius: 30px;
            font-size: 0.7rem;
        }

        /* 加分工具列 */
        .action-bar {
            background: #fff8f0;
            border-radius: 40px;
            padding: 12px 16px;
            margin: 16px 0 24px;
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 10px;
            box-shadow: 0 4px 10px rgba(0,0,0,0.05);
            border: 1px solid #ffddcc;
        }
        .action-btn {
            background: #ffede3;
            border: none;
            padding: 8px 14px;
            border-radius: 40px;
            font-weight: 600;
            font-size: 0.75rem;
            color: #b14534;
            cursor: pointer;
            transition: all 0.2s;
            flex: 0 0 auto;
        }
        .action-btn.special {
            background: #ffe0cf;
            color: #c25a3e;
        }

        /* 團隊卡片 */
        .teams-grid {
            display: flex;
            flex-direction: column;
            gap: 24px;
            margin-bottom: 32px;
        }
        .team-card {
            background: white;
            border-radius: 40px;
            box-shadow: 0 8px 20px rgba(0,0,0,0.1);
            overflow: hidden;
            border: 1px solid #ffd5be;
        }
        .team-header {
            padding: 16px 18px 10px;
            background: #fff7f0;
            border-bottom: 2px solid #ffbe9f;
        }
        .team-name-input {
            font-size: 1.4rem;
            font-weight: 800;
            background: transparent;
            border: none;
            width: 100%;
            padding: 4px 0;
            color: #772e26;
        }
        .punish-area {
            margin-top: 10px;
            display: flex;
            align-items: center;
            gap: 6px;
            flex-wrap: wrap;
            background: #ffefe3;
            padding: 6px 10px;
            border-radius: 30px;
        }
        .punish-label {
            font-size: 0.6rem;
            font-weight: bold;
            background: #e7b89c;
            padding: 3px 10px;
            border-radius: 30px;
            color: white;
        }
        .punish-text {
            flex: 1;
            border: none;
            background: transparent;
            padding: 4px 0;
            font-size: 0.75rem;
            color: #8b4b3a;
        }

        .team-score {
            padding: 12px 20px;
            background: #fff3ea;
            text-align: center;
        }
        .score-number {
            font-size: 2.8rem;
            font-weight: 800;
            color: #dc6b4a;
        }
        .team-score > div:last-child {
            font-size: 0.7rem;
            color: #b27b62;
        }

        .members-section {
            padding: 14px 16px;
            background: #fffaf5;
            border-top: 1px solid #ffe2d0;
            border-bottom: 1px solid #ffe2d0;
        }
        .members-title {
            font-weight: 700;
            color: #c47a5e;
            font-size: 0.8rem;
            margin-bottom: 10px;
        }
        .member-list {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
            margin-bottom: 12px;
        }
        .member-chip {
            background: #fff1e8;
            border-radius: 30px;
            padding: 5px 12px;
            display: inline-flex;
            align-items: center;
            gap: 6px;
            font-size: 0.75rem;
            font-weight: 500;
            color: #7b3d2c;
        }
        .member-today-score {
            background: #ecc7b6;
            border-radius: 30px;
            padding: 2px 8px;
            font-size: 0.6rem;
            font-weight: bold;
        }
        .delete-member {
            background: none;
            border: none;
            cursor: pointer;
            color: #c27e64;
            font-weight: bold;
            font-size: 0.9rem;
            margin-left: 4px;
        }
        .add-member-form {
            display: flex;
            gap: 8px;
            margin-top: 8px;
            background: #fff0e6;
            padding: 8px 12px;
            border-radius: 50px;
        }
        .add-member-input {
            flex: 1;
            border: 1px solid #ffcfb5;
            border-radius: 50px;
            padding: 8px 12px;
            background: white;
            font-size: 0.8rem;
        }
        .add-member-btn {
            background: #e07a5f;
            border: none;
            border-radius: 50px;
            padding: 6px 16px;
            font-weight: bold;
            color: white;
            cursor: pointer;
            font-size: 0.75rem;
        }

        /* 表單 - 團隊按鈕直接顯示隊名 */
        .form-panel {
            background: white;
            border-radius: 40px;
            padding: 18px;
            margin-bottom: 32px;
            border: 1px solid #ffddcc;
        }
        .form-title {
            font-weight: bold;
            margin-bottom: 16px;
            color: #b54733;
            font-size: 1rem;
            text-align: center;
        }
        .team-toggle {
            display: flex;
            flex-direction: column;
            gap: 12px;
            margin-bottom: 16px;
        }
        .team-btn {
            background: #ffede3;
            border: 1px solid #ffcdb5;
            padding: 12px;
            border-radius: 60px;
            font-weight: 700;
            font-size: 1rem;
            color: #b14534;
            text-align: center;
            cursor: pointer;
            transition: 0.2s;
        }
        .team-btn.active {
            background: #e07a5f;
            color: white;
            border-color: #e07a5f;
            box-shadow: 0 2px 8px rgba(224,122,95,0.3);
        }
        .form-grid {
            display: flex;
            flex-direction: column;
            gap: 12px;
        }
        .input-group {
            width: 100%;
        }
        .input-group label {
            font-size: 0.7rem;
            font-weight: 600;
            color: #c27156;
            display: block;
            margin-bottom: 4px;
        }
        select, input {
            width: 100%;
            padding: 10px 14px;
            border-radius: 40px;
            border: 1.5px solid #ffd5be;
            background: #fffcf8;
            font-size: 0.85rem;
        }
        .btn-primary {
            background: #e07a5f;
            border: none;
            padding: 12px;
            border-radius: 40px;
            color: white;
            font-weight: bold;
            cursor: pointer;
            width: 100%;
            font-size: 0.9rem;
            margin-top: 8px;
        }
        .rule-hint {
            background: #fff2e6;
            border-radius: 28px;
            padding: 8px 12px;
            margin-top: 16px;
            font-size: 0.6rem;
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
        }

        /* 紀錄表格 */
        .log-section {
            background: #fffef7;
            border-radius: 40px;
            padding: 16px;
        }
        .log-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            margin-bottom: 12px;
        }
        .log-header h3 {
            font-size: 1rem;
            color: #b54733;
        }
        .reset-btn {
            background: #ffdad0;
            border: none;
            padding: 5px 12px;
            border-radius: 30px;
            font-size: 0.7rem;
            cursor: pointer;
        }
        .table-wrapper {
            overflow-x: auto;
            -webkit-overflow-scrolling: touch;
        }
        table {
            width: 100%;
            border-collapse: collapse;
            min-width: 500px;
        }
        th, td {
            text-align: left;
            padding: 10px 6px;
            border-bottom: 1px solid #ffdfcf;
            font-size: 0.7rem;
        }
        .delete-log {
            background: none;
            border: none;
            cursor: pointer;
            color: #e6947a;
            font-size: 1rem;
        }
        .footer-note {
            text-align: center;
            margin-top: 24px;
            font-size: 0.6rem;
            color: #b28b78;
        }
        button:active {
            transform: scale(0.97);
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

    <!-- 加分工具列 -->
    <div class="action-bar">
        <button class="action-btn" data-type="1">①限動+1</button>
        <button class="action-btn" data-type="2">②起承轉合+2</button>
        <button class="action-btn" data-type="3">③詢問+3</button>
        <button class="action-btn" data-type="4">④成交+4</button>
        <button class="action-btn" data-type="5">⑤Reels+5</button>
        <button class="action-btn special" data-type="6">⑥全組+6</button>
        <button class="action-btn" data-type="7">⑦素材+7</button>
    </div>

    <div class="teams-grid" id="teamsGrid"></div>

    <!-- 詳細加分表單 - 團隊按鈕直接顯示隊名 -->
    <div class="form-panel">
        <div class="form-title">📋 詳細加分表單</div>
        <div class="team-toggle" id="teamToggle">
            <div class="team-btn" data-team-val="A" id="teamABtn">愛心媽咪隊</div>
            <div class="team-btn" data-team-val="B" id="teamBBtn">甜心寶貝隊</div>
        </div>
        <div class="form-grid">
            <div class="input-group">
                <label>👤 成員</label>
                <select id="memberSelectForm">
                    <option value="">-- 請選擇 --</option>
                </select>
            </div>
            <div class="input-group">
                <label>🎯 加分項目</label>
                <select id="actionTypeForm">
                    <option value="1">① 發限動 (置入產品) +1 (每日限1)</option>
                    <option value="2">② 限動起承轉合 +2</option>
                    <option value="3">③ 有人詢問 +3</option>
                    <option value="4">④ 成交 +4</option>
                    <option value="5">⑤ 發Reels +5</option>
                    <option value="6">⑥ 全組每人發限動 +6</option>
                    <option value="7">⑦ 分享素材 +7</option>
                </select>
            </div>
            <button class="btn-primary" id="addRecordBtn">✨ 新增加分</button>
        </div>
        <div class="rule-hint">
            <span>📌 ①&② 每人每日擇一</span>
            <span>👥 ⑥ 全組加分</span>
            <span>📊 今日貢獻即時顯示</span>
        </div>
    </div>

    <div class="log-section">
        <div class="log-header">
            <h3>📋 近期加分紀錄</h3>
            <button class="reset-btn" id="resetAllDataBtn">🗑️ 重置全部</button>
        </div>
        <div class="table-wrapper">
            <table>
                <thead><tr><th>時間</th><th>團隊</th><th>成員</th><th>項目</th><th>分數</th><th></th></tr></thead>
                <tbody id="logBody"></tbody>
            </table>
        </div>
    </div>
    <div class="footer-note">✨ 點擊隊員✖可刪除 | 團隊名稱/懲罰可直接修改 | 資料自動儲存</div>
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

    const END_DATE = new Date(2026, 4, 11, 23, 59, 59);
    function updateCountdown() {
        const now = new Date();
        const diffMs = END_DATE - now;
        const diffDays = Math.ceil(diffMs / (1000 * 60 * 60 * 24));
        const el = document.getElementById('countdownNumber');
        if (el) el.innerText = diffMs <= 0 ? "比賽已結束" : `${diffDays} 天`;
    }
    setInterval(updateCountdown, 1000);

    function saveToLocal() { localStorage.setItem(STORAGE_KEY, JSON.stringify(appData)); }
    function loadFromLocal() {
        const raw = localStorage.getItem(STORAGE_KEY);
        if (raw) try { const p = JSON.parse(raw); if (p.teams && p.logs) appData = p; } catch(e) {}
        if (!appData.teams) appData.teams = { A: { name: "愛心媽咪隊", punish: "輸家請喝珍奶", members: ["小美","阿華","小莉"] }, B: { name: "甜心寶貝隊", punish: "輸家跳舞影片", members: ["大雄","靜香","胖虎"] } };
        if (!appData.teams.A.members) appData.teams.A.members = ["小美","阿華","小莉"];
        if (!appData.teams.B.members) appData.teams.B.members = ["大雄","靜香","胖虎"];
        if (!appData.logs) appData.logs = [];
        saveToLocal();
    }
    function getTodayStr() { const d = new Date(); return `${d.getFullYear()}-${String(d.getMonth()+1).padStart(2,'0')}-${String(d.getDate()).padStart(2,'0')}`; }
    function hasTodayLimitStory(team, member, today) {
        return appData.logs.some(l => l.team === team && l.member === member && l.date === today && (l.type === 1 || l.type === 2));
    }
    function hasTodayTeamBonus6(team, today) { return appData.logs.some(l => l.team === team && l.type === 6 && l.date === today); }
    function getMemberTodayScore(team, member, today) {
        return appData.logs.filter(l => l.team === team && l.member === member && l.date === today && l.type !== 6).reduce((s,l)=>s+l.points,0);
    }
    function computeTeamScore(team) { return appData.logs.filter(l=>l.team===team).reduce((s,l)=>s+l.points,0); }

    function addRecord(team, member, typeVal) {
        const type = parseInt(typeVal,10);
        const pointsMap = {1:1,2:2,3:3,4:4,5:5,6:6,7:7};
        const points = pointsMap[type];
        if (!points) return { success: false, msg: "錯誤項目" };
        const today = getTodayStr();
        if (type !== 6) {
            if (!member) return { success: false, msg: "請選擇成員" };
            if (!appData.teams[team].members.includes(member)) return { success: false, msg: `❌ ${member} 不是該團隊成員` };
        }
        if ((type === 1 || type === 2) && hasTodayLimitStory(team, member, today)) {
            return { success: false, msg: `⚠️ ${member} 今日已有限動加分，每人每日限一次` };
        }
        if (type === 6) {
            if (member && member !== "") return { success: false, msg: "全組加分不需選成員" };
            if (hasTodayTeamBonus6(team, today)) return { success: false, msg: "今日已用過全組加分" };
        }
        const newLog = { id: Date.now()+Math.random(), team, member: type===6?"全組行動":member, type, points, date: today, timestamp: Date.now() };
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
        const scoreA = computeTeamScore('A'), scoreB = computeTeamScore('B');
        const leader = scoreA > scoreB ? appData.teams.A.name : (scoreB > scoreA ? appData.teams.B.name : "平手");
        const diff = Math.abs(scoreA-scoreB);
        document.getElementById('scoreBar').innerHTML = `
            <div class="team-score-compact">
                <div class="team-compact"><div class="name">${escapeHtml(appData.teams.A.name)}</div><div class="points">${scoreA}</div></div>
                <span class="vs">VS</span>
                <div class="team-compact"><div class="name">${escapeHtml(appData.teams.B.name)}</div><div class="points">${scoreB}</div></div>
            </div>
            <div class="leader-info">🏆 ${leader} ${scoreA!==scoreB ? `領先 ${diff} 分` : "平手"}</div>
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
                html += `<div class="member-chip">${escapeHtml(m)}<span class="member-today-score">📅今日+${todayScore}</span><button class="delete-member" data-team="${teamLetter}" data-member="${escapeHtml(m)}">✖</button></div>`;
            });
            html += '</div>';
            html += `<div class="add-member-form"><input type="text" class="add-member-input" id="newMember${teamLetter}" placeholder="新隊員名字"><button class="add-member-btn" data-team="${teamLetter}">➕ 新增</button></div>`;
            return html;
        };
        grid.innerHTML = `
            <div class="team-card">
                <div class="team-header"><input type="text" class="team-name-input" id="teamAName" value="${escapeHtml(appData.teams.A.name)}"><div class="punish-area"><span class="punish-label">😈 懲罰</span><input type="text" class="punish-text" id="teamAPunish" value="${escapeHtml(appData.teams.A.punish)}"></div></div>
                <div class="team-score"><div class="score-number">${computeTeamScore('A')}</div><div>團隊總分</div></div>
                <div class="members-section"><div class="members-title">👥 隊員名單 (今日貢獻)</div>${renderMemberList('A','A')}</div>
            </div>
            <div class="team-card">
                <div class="team-header"><input type="text" class="team-name-input" id="teamBName" value="${escapeHtml(appData.teams.B.name)}"><div class="punish-area"><span class="punish-label">😈 懲罰</span><input type="text" class="punish-text" id="teamBPunish" value="${escapeHtml(appData.teams.B.punish)}"></div></div>
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
        // 更新表單中的團隊按鈕文字 (隊名)
        const teamABtn = document.getElementById('teamABtn');
        const teamBBtn = document.getElementById('teamBBtn');
        if (teamABtn) teamABtn.innerText = appData.teams.A.name;
        if (teamBBtn) teamBBtn.innerText = appData.teams.B.name;
    }

    function renderLogTable() {
        const tbody = document.getElementById('logBody');
        if(!tbody) return;
        if(appData.logs.length===0) { tbody.innerHTML='<tr><td colspan="6" style="text-align:center">暫無紀錄</td></tr>'; return; }
        const typeMap = {1:'①限動+1',2:'②起承轉合+2',3:'③詢問+3',4:'④成交+4',5:'⑤Reels+5',6:'⑥全組+6',7:'⑦素材+7'};
        let html='';
        for(let log of appData.logs) {
            const teamName = log.team==='A'? appData.teams.A.name : appData.teams.B.name;
            const timeStr = new Date(log.timestamp).toLocaleString('zh-TW');
            html+=`<tr><td style="white-space:nowrap">${escapeHtml(timeStr)}</td><td><span style="background:#fce5d8;padding:2px 8px;border-radius:20px;">${escapeHtml(teamName)}</span></td><td>${escapeHtml(log.member||'—')}</td><td>${typeMap[log.type]}</td><td>+${log.points}</td><td><button class="delete-log" data-id="${log.id}">🗑️</button></td></tr>`;
        }
        tbody.innerHTML = html;
        document.querySelectorAll('.delete-log').forEach(btn => {
            btn.addEventListener('click', (e) => { const id = parseInt(btn.getAttribute('data-id'),10); if(confirm('刪除此筆？')) deleteLog(id); });
        });
    }

    // 表單團隊選擇狀態 (直接以隊名按鈕切換)
    let selectedTeam = 'A';
    function updateTeamButtons() {
        const btnA = document.getElementById('teamABtn');
        const btnB = document.getElementById('teamBBtn');
        if (btnA) {
            if (selectedTeam === 'A') btnA.classList.add('active');
            else btnA.classList.remove('active');
        }
        if (btnB) {
            if (selectedTeam === 'B') btnB.classList.add('active');
            else btnB.classList.remove('active');
        }
        // 更新成員下拉選單
        const memberSelect = document.getElementById('memberSelectForm');
        const members = appData.teams[selectedTeam].members || [];
        memberSelect.innerHTML = '<option value="">-- 請選擇成員 --</option>' + members.map(m=>`<option value="${escapeHtml(m)}">${escapeHtml(m)}</option>`).join('');
    }

    function bindForm() {
        const btnA = document.getElementById('teamABtn');
        const btnB = document.getElementById('teamBBtn');
        if (btnA) {
            btnA.addEventListener('click', () => {
                selectedTeam = 'A';
                updateTeamButtons();
            });
        }
        if (btnB) {
            btnB.addEventListener('click', () => {
                selectedTeam = 'B';
                updateTeamButtons();
            });
        }
        const addBtn = document.getElementById('addRecordBtn');
        addBtn.addEventListener('click', () => {
            const member = document.getElementById('memberSelectForm').value;
            const action = document.getElementById('actionTypeForm').value;
            if (parseInt(action) !== 6 && !member) { alert("請選擇成員"); return; }
            const res = addRecord(selectedTeam, member, action);
            alert(res.msg);
        });
        document.getElementById('resetAllDataBtn')?.addEventListener('click', resetAll);
    }

    function showAddDialog(type) {
        if (type === 6) {
            const teamKey = prompt("請選擇團隊：\nA = 左隊\nB = 右隊");
            if (!teamKey) return;
            const team = teamKey.toUpperCase() === 'A' ? 'A' : (teamKey.toUpperCase() === 'B' ? 'B' : null);
            if (!team) { alert("請輸入 A 或 B"); return; }
            const res = addRecord(team, "", "6");
            alert(res.msg);
        } else {
            const teamKey = prompt("請選擇團隊：\nA = 左隊\nB = 右隊");
            if (!teamKey) return;
            const team = teamKey.toUpperCase() === 'A' ? 'A' : (teamKey.toUpperCase() === 'B' ? 'B' : null);
            if (!team) { alert("請輸入 A 或 B"); return; }
            const members = appData.teams[team].members;
            if (!members.length) { alert("請先新增隊員"); return; }
            const listStr = members.map((m,i)=>`${i+1}. ${m}`).join('\n');
            const input = prompt(`請選擇成員 (數字或名稱)\n${listStr}`);
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
        document.querySelectorAll('.action-btn').forEach(btn => {
            btn.addEventListener('click', (e) => {
                const type = parseInt(btn.getAttribute('data-type'), 10);
                showAddDialog(type);
            });
        });
    }

    function renderAll() {
        renderTopScoreBar();
        renderTeams();
        renderLogTable();
        bindQuickActions();
        bindForm();
        updateTeamButtons();
        updateCountdown();
    }

    loadFromLocal();
    renderAll();
    function escapeHtml(str) { if(!str) return ''; return str.replace(/[&<>]/g, m=> m==='&'?'&amp;': m==='<'?'&lt;':'&gt;'); }
</script>
</body>
</html>
