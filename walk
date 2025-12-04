<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>步履台灣 - 10週環島計畫</title>
    <style>
        :root {
            --primary: #4A90E2;
            --accent: #F5A623;
            --bg: #F0F4F8;
            --text: #333;
            --card-bg: #ffffff;
        }

        body {
            font-family: 'Helvetica Neue', Helvetica, Arial, sans-serif;
            background-color: var(--bg);
            color: var(--text);
            margin: 0;
            padding: 20px;
            line-height: 1.6;
        }

        .container {
            max-width: 600px;
            margin: 0 auto;
        }

        /* Header */
        header {
            text-align: center;
            margin-bottom: 30px;
        }
        header h1 {
            color: var(--primary);
            margin-bottom: 5px;
        }
        header p {
            color: #666;
            font-size: 0.9rem;
        }

        /* Cards */
        .card {
            background: var(--card-bg);
            border-radius: 16px;
            padding: 20px;
            box-shadow: 0 4px 12px rgba(0,0,0,0.05);
            margin-bottom: 20px;
        }

        /* Status Section */
        .status-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 10px;
        }
        .big-number {
            font-size: 2.5rem;
            font-weight: bold;
            color: var(--primary);
        }
        .sub-text {
            color: #888;
            font-size: 0.9rem;
        }

        /* Progress Bar */
        .progress-container {
            background-color: #e0e0e0;
            border-radius: 10px;
            height: 12px;
            width: 100%;
            margin: 15px 0;
            overflow: hidden;
        }
        .progress-bar {
            background: linear-gradient(90deg, var(--primary), #6DD5FA);
            height: 100%;
            width: 0%;
            transition: width 0.5s ease-in-out;
            border-radius: 10px;
        }

        /* Location Info */
        .location-badge {
            display: inline-block;
            background-color: var(--primary);
            color: white;
            padding: 5px 12px;
            border-radius: 20px;
            font-size: 0.85rem;
            font-weight: bold;
            margin-bottom: 10px;
        }
        .next-goal {
            font-size: 0.9rem;
            color: #666;
            text-align: right;
        }

        /* Message Box */
        .message-box {
            background-color: #E8F4FD;
            border-left: 5px solid var(--primary);
            padding: 15px;
            margin-top: 15px;
            border-radius: 4px;
        }
        .message-title {
            font-weight: bold;
            color: var(--primary);
            margin-bottom: 5px;
        }
        .message-content {
            font-style: italic;
            color: #555;
        }

        /* Input Form */
        .input-group {
            display: flex;
            gap: 10px;
        }
        input[type="number"] {
            flex: 1;
            padding: 12px;
            border: 1px solid #ddd;
            border-radius: 8px;
            font-size: 1rem;
        }
        button {
            background-color: var(--primary);
            color: white;
            border: none;
            padding: 12px 24px;
            border-radius: 8px;
            font-size: 1rem;
            cursor: pointer;
            font-weight: bold;
            transition: background 0.2s;
        }
        button:hover {
            background-color: #357ABD;
        }
        button.delete-btn {
            background-color: #ff6b6b;
            padding: 5px 10px;
            font-size: 0.8rem;
            margin-left: auto;
        }

        /* History List */
        .history-list {
            list-style: none;
            padding: 0;
            margin: 0;
        }
        .history-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 10px 0;
            border-bottom: 1px solid #eee;
        }
        .history-date {
            color: #888;
            font-size: 0.9rem;
        }
        .history-steps {
            font-weight: bold;
            color: #333;
        }

        /* Footer */
        .footer {
            text-align: center;
            margin-top: 40px;
            color: #aaa;
            font-size: 0.8rem;
        }
        .reset-link {
            color: #aaa;
            text-decoration: underline;
            cursor: pointer;
        }
    </style>
</head>
<body>

<div class="container">
    <header>
        <h1>🇹🇼 步履台灣</h1>
        <p>10 週｜75 萬步｜帶我一起走</p>
    </header>

    <!-- 儀表板區域 -->
    <div class="card">
        <div class="status-header">
            <div>
                <div class="sub-text">目前累積步數</div>
                <div class="big-number" id="totalStepsDisplay">0</div>
            </div>
            <div style="text-align: right;">
                <div class="sub-text">完成度</div>
                <div style="font-size: 1.2rem; font-weight: bold;" id="percentageDisplay">0%</div>
            </div>
        </div>

        <div class="progress-container">
            <div class="progress-bar" id="progressBar"></div>
        </div>

        <div style="display: flex; justify-content: space-between; align-items: flex-start;">
            <div>
                <span class="location-badge" id="currentLocationBadge">📍 準備出發：淡水</span>
                <div id="currentDateRange" style="font-size: 0.8rem; color: #999; margin-top: 4px;">12/8 - 12/14</div>
            </div>
            <div class="next-goal">
                目標：<span id="nextCityName">桃園</span><br>
                <span id="stepsToNext" style="font-size: 0.8rem; color: #e67e22;">還差 63,000 步</span>
            </div>
        </div>

        <!-- 激勵訊息區 -->
        <div class="message-box" id="messageBox">
            <div class="message-title" id="msgTitle">👋 旅程開始</div>
            <div class="message-content" id="msgContent">
                「你也曾想過背著包、迎著風，走一圈台灣嗎？不用離家，只要每天願意走一點，我們的腳，就能在地圖上環島。」
            </div>
        </div>
    </div>

    <!-- 輸入區域 -->
    <div class="card">
        <h3 style="margin-top: 0;">📝 記錄今日步數</h3>
        <div class="input-group">
            <input type="number" id="stepInput" placeholder="輸入今天走了幾步..." min="0">
            <button onclick="addSteps()">紀錄</button>
        </div>
    </div>

    <!-- 歷史紀錄 -->
    <div class="card">
        <h3 style="margin-top: 0;">📅 行走紀錄</h3>
        <ul class="history-list" id="historyList">
            <!-- JS 會插入資料 -->
            <li style="text-align: center; color: #999;">尚未有紀錄</li>
        </ul>
    </div>

    <div class="footer">
        <p>Keep Walking, Keep Dreaming.</p>
        <span class="reset-link" onclick="resetData()">重置所有資料</span>
    </div>
</div>

<script>
    // --- 1. 資料設定 (根據你的表格) ---
    const milestones = [
        { name: "淡水 (起點)", target: 0, range: "12/8-12/14", msg: "萬事起頭難，但你已經踏出了淡水河畔的第一步。", spot: "準備好感受林口台地的風了嗎？" },
        { name: "桃園", target: 63000, range: "12/15-12/21", msg: "恭喜抵達桃園！🛬 看見飛機起降了嗎？我們雙腳比飛機更踏實。", spot: "獎勵：來一塊大溪豆干犒賞自己吧！" },
        { name: "新竹", target: 154000, range: "12/22-12/28", msg: "歡迎來到新竹！💨 風會把汗水吹乾，也會把煩惱吹散。", spot: "去城隍廟求個平安，或是吃一碗熱騰騰的米粉湯。" },
        { name: "苗栗", target: 224000, range: "12/29-1/4", msg: "抵達苗栗山城！⛰️ 慢下來沒關係，這是一座適合慢活的城市。", spot: "想像你在龍騰斷橋前，拍下了一張最帥氣的自拍。" },
        { name: "台中", target: 322000, range: "1/5-1/11", msg: "台中到了！☀️ 這裡有全台灣最好的陽光。你用雙腳送給自己最棒的禮物。", spot: "經過高美濕地時，別忘了回頭看看夕陽。" },
        { name: "彰化", target: 378000, range: "1/12-1/18", msg: "恭喜抵達彰化！那些你以為過不去的坎，走著走著就跨過去了。", spot: "那是八卦山大佛嗎？他在看著你環島的決心呢。" },
        { name: "雲林", target: 455000, range: "1/19-1/25", msg: "雲林到了！🌾 這裡是台灣最樸實的角落，就像你樸實而堅定的步伐。", spot: "去北港朝天宮感受一下香火鼎盛的人情味吧。" },
        { name: "嘉義", target: 511000, range: "1/26-2/1", msg: "嘉義，雞肉飯之都！🍚 你已經走完了超過 50 萬步，這是半個百萬富翁的等級了！", spot: "聽說阿里山的小火車在呼喚，我們心已飛到雲端。" },
        { name: "台南", target: 609000, range: "2/2-2/8", msg: "台南到了！全糖的城市！🍬 空氣是甜的，勝利的果實也是甜的。", spot: "迷失在台南的小巷弄裡，是旅行最好的方式。" },
        { name: "高雄", target: 672000, range: "2/9-2/15", msg: "高雄到了！🚢 港都的遼闊讓你心胸開闊了嗎？終點就在不遠處！", spot: "看見蓮池潭的龍虎塔了嗎？走進去，把好運都帶走。" },
        { name: "墾丁 (終點)", target: 756000, range: "達成！", msg: "🏆 恭喜完成環島！你靠自己的雙腳，走完了台灣的一條路。", spot: "現在，脫下鞋子，想像你的腳踩在墾丁的白沙灘上吧！" }
    ];

    const FINAL_GOAL = 756000;
    
    // --- 2. 狀態管理 ---
    let logs = JSON.parse(localStorage.getItem('walkTaiwanLogs')) || [];
    
    // --- 3. 初始化 ---
    updateUI();

    // --- 4. 核心功能 ---

    function addSteps() {
        const input = document.getElementById('stepInput');
        const steps = parseInt(input.value);

        if (!steps || steps <= 0) {
            alert("請輸入有效的步數！");
            return;
        }

        const newLog = {
            id: Date.now(),
            date: new Date().toLocaleDateString(),
            steps: steps
        };

        logs.unshift(newLog); // 加到最前面
        saveData();
        input.value = ''; // 清空輸入框
        updateUI();
    }

    function deleteLog(id) {
        if(confirm("確定要刪除這筆紀錄嗎？")) {
            logs = logs.filter(log => log.id !== id);
            saveData();
            updateUI();
        }
    }

    function saveData() {
        localStorage.setItem('walkTaiwanLogs', JSON.stringify(logs));
    }

    function resetData() {
        if(confirm("警告：這將會清除所有步數紀錄，確定要重置嗎？")) {
            localStorage.removeItem('walkTaiwanLogs');
            logs = [];
            updateUI();
        }
    }

    function updateUI() {
        // 1. 計算總步數
        const totalSteps = logs.reduce((acc, curr) => acc + curr.steps, 0);
        
        // 2. 更新數字顯示
        document.getElementById('totalStepsDisplay').innerText = totalSteps.toLocaleString();
        
        // 3. 計算進度條
        let percentage = (totalSteps / FINAL_GOAL) * 100;
        if (percentage > 100) percentage = 100;
        document.getElementById('percentageDisplay').innerText = percentage.toFixed(1) + '%';
        document.getElementById('progressBar').style.width = percentage + '%';

        // 4. 判斷當前位置與下一站
        let currentStageIndex = -1;
        
        // 找到最後一個達成的目標 (例如總步數 16萬，大於新竹15.4萬，current就是新竹)
        for (let i = 0; i < milestones.length; i++) {
            if (totalSteps >= milestones[i].target) {
                currentStageIndex = i;
            } else {
                break;
            }
        }

        const currentStage = currentStageIndex >= 0 ? milestones[currentStageIndex] : milestones[0];
        const nextStage = milestones[currentStageIndex + 1] || null;

        // 5. 更新介面文字
        
        // 目前位置 Badge
        let locationText = "📍 準備出發：淡水";
        if (currentStageIndex >= 0) {
            locationText = `📍 目前位置：${currentStage.name}`;
        }
        document.getElementById('currentLocationBadge').innerText = locationText;

        // 下一站資訊
        if (nextStage) {
            document.getElementById('nextCityName').innerText = nextStage.name;
            const stepsNeeded = nextStage.target - totalSteps;
            document.getElementById('stepsToNext').innerText = `還差 ${stepsNeeded.toLocaleString()} 步`;
            document.getElementById('currentDateRange').innerText = `本週日期：${nextStage.range}`;
        } else {
            // 已完成所有目標
            document.getElementById('nextCityName').innerText = "已完成";
            document.getElementById('stepsToNext').innerText = "旅程圓滿結束！";
            document.getElementById('currentDateRange').innerText = "";
        }

        // 6. 更新激勵訊息 (Message Box)
        const msgTitle = document.getElementById('msgTitle');
        const msgContent = document.getElementById('msgContent');

        // 邏輯：
        // 如果剛達到某個里程碑（例如剛超過63000），顯示抵達賀詞。
        // 如果在途中（例如 80000，過了桃園但在往新竹路上），顯示途中的景點/鼓勵。
        
        if (totalSteps >= FINAL_GOAL) {
             // 完賽
             msgTitle.innerText = "🎉 環島挑戰成功！";
             msgContent.innerHTML = milestones[milestones.length-1].msg + "<br><br>" + milestones[milestones.length-1].spot;
        } else if (currentStageIndex === -1) {
            // 還沒開始或剛開始
            msgTitle.innerText = "👋 旅程開始";
            msgContent.innerText = milestones[0].msg;
        } else {
            // 判斷是「剛抵達」還是「路途中」
            // 這裡簡單判定：顯示當前已抵達城市的賀詞 + 下一站的鼓勵
            msgTitle.innerText = `🙌 抵達${currentStage.name}`;
            
            // 顯示組合訊息：抵達賀詞 + 途中景點(如果是前往下一站的路上)
            let content = `${currentStage.msg}`;
            
            // 如果還有下一站，且已經走了一點路 (超過當前目標 10%)
            if (nextStage) {
                 // 稍微加點變化，如果走到一半，顯示下一站的景點預告
                 const progressToNext = (totalSteps - currentStage.target) / (nextStage.target - currentStage.target);
                 if (progressToNext > 0.3) {
                     msgTitle.innerText = `🏃 往${nextStage.name}前進中`;
                     content = `加油！${nextStage.spot}`; // 使用下一站的景點作為途中鼓勵
                 }
            }
            msgContent.innerHTML = content;
        }

        // 7. 更新歷史列表
        const list = document.getElementById('historyList');
        list.innerHTML = '';
        if (logs.length === 0) {
            list.innerHTML = '<li style="text-align: center; color: #999;">尚未有紀錄</li>';
        } else {
            logs.forEach(log => {
                const li = document.createElement('li');
                li.className = 'history-item';
                li.innerHTML = `
                    <span class="history-date">${log.date}</span>
                    <div style="display:flex; align-items:center; gap:10px;">
                        <span class="history-steps">+${log.steps.toLocaleString()}</span>
                        <button class="delete-btn" onclick="deleteLog(${log.id})">刪除</button>
                    </div>
                `;
                list.appendChild(li);
            });
        }
    }
</script>

</body>
</html>
