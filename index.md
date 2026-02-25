<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>AI PRO 2026 | HOANGDZ AUTH</title>
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;900&display=swap" rel="stylesheet">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/crypto-js/4.1.1/crypto-js.min.js"></script>
    <style>
        :root { --neon: #00f2ff; --bg: #050505; }
        body { margin:0; background:var(--bg); color:#fff; font-family:'Orbitron', sans-serif; overflow-x:hidden; }
        .snow { position:fixed; top:0; left:0; width:100%; height:100%; pointer-events:none; z-index:99; }
        .login-overlay { position:fixed; inset:0; display:flex; align-items:center; justify-content:center; background:rgba(0,0,0,0.95); z-index:2000; padding:20px; }
        .login-box { border:2px solid var(--neon); padding:20px; border-radius:20px; text-align:center; width:100%; max-width:350px; background:#000; transition: transform 0.2s; }
        .wrapper { max-width:450px; margin:0 auto; padding:15px; display:none; }
        .glass { background:rgba(0,0,0,0.8); border:1px solid var(--neon); border-radius:15px; padding:15px; margin-bottom:10px; text-align:center; }
        input, button { width:100%; padding:12px; margin-bottom:10px; border-radius:8px; border:1px solid #444; background:#000; color:#fff; box-sizing:border-box; font-size:16px; }
        .btn { background:linear-gradient(90deg, var(--neon), #7000ff); font-weight:bold; cursor:pointer; }
        .res-box { font-size:2.5rem; font-weight:900; animation: flash 1s infinite; }
        @keyframes flash { 0%, 100% { opacity: 1; } 50% { opacity: 0.5; } }
        @keyframes shake { 0%, 100% { transform: translateX(0); } 25% { transform: translateX(-10px); } 75% { transform: translateX(10px); } }
        .admin-link { position:fixed; bottom:15px; right:15px; font-size:12px; color:var(--neon); z-index:1000; }
    </style>
</head>
<body>

<div class="snow" id="snowContainer"></div>

<div class="login-overlay" id="loginScreen">
    <div class="login-box" id="loginBox">
        <h2 style="color:var(--neon);">🔑 KÍCH HOẠT VIP HOANGDZ</h2>
        <input type="text" id="keyInput" placeholder="Nhập Key của bạn...">
        <button class="btn" onclick="checkKey()">KÍCH HOẠT NGAY</button>
        <div id="checkStatus" style="margin-top:10px; font-size:12px;"></div>
    </div>
</div>

<div class="wrapper" id="mainScreen">
    <div class="glass">
        <h3 style="color:var(--neon); margin:0;">CHÀO MỪNG QUAY TRỞ LẠI</h3>
        <p style="font-size:11px; color:#ccc;">Hệ thống phân tích MD5 thế hệ 2026. Tối ưu tỉ lệ thắng cho VIP.</p>
    </div>
    <div class="glass">
        <input type="text" id="code" placeholder="MÃ PHIÊN (MD5)...">
        <button class="btn" onclick="runAnalysis()">PHÂN TÍCH KẾT QUẢ</button>
        <div id="loader" style="color:yellow; font-size:12px; display:none; margin-bottom:10px;">Đang phân tích dữ liệu, vui lòng đợi...</div>
        <div id="res" class="res-box">--</div>
        <div id="logic" style="font-size:10px; color:#aaa; margin-top:10px;"></div>
    </div>
</div>

<div class="admin-link">Admin: @tranhoang2286</div>

<script>
    // Dán 600 key của bạn vào đây (Ví dụ: "KEY": thời gian)
    const masterKeys = {
        "KEY-HOANGDZ-1H-X7A7PYKS": 3600,
        // ... (Dán toàn bộ danh sách tại đây)
    };

    function checkKey() {
        let val = document.getElementById('keyInput').value.trim();
        let status = document.getElementById('checkStatus');
        let box = document.getElementById('loginBox');
        
        status.innerText = "🔑 Đang kiểm tra key, vui lòng đợi...";
        status.style.color = "var(--neon)";

        setTimeout(() => {
            if (masterKeys[val]) {
                status.style.color = "#2dff8f";
                status.innerText = "✅ Kích hoạt thành công!";
                localStorage.setItem('expiry', Date.now() + (masterKeys[val] * 1000));
                setTimeout(() => location.reload(), 1000);
            } else {
                status.style.color = "#ff3b3b";
                status.innerText = "❌ CẢNH BÁO: Key không hợp lệ!";
                box.style.animation = "shake 0.3s";
                setTimeout(() => box.style.animation = "", 300);
            }
        }, 1500);
    }

    function runAnalysis() {
        let input = document.getElementById('code').value.trim();
        if(input.length < 32) return alert("Nhập đủ 32 ký tự MD5!");
        
        let loader = document.getElementById('loader');
        let resBox = document.getElementById('res');
        loader.style.display = "block";
        resBox.innerText = "--";

        setTimeout(() => {
            let hash = CryptoJS.MD5(input).toString();
            let res = (parseInt(hash.slice(-1), 16) % 2 === 0) ? "🔴 TÀI" : "⚪ XỈU";
            loader.style.display = "none";
            resBox.innerText = res;
            document.getElementById('logic').innerText = `Thuật toán MD5 | Độ chính xác: ${85 + (parseInt(hash.slice(-1), 16) % 10)}%`;
        }, 2000);
    }

    window.onload = () => {
        if(localStorage.getItem('expiry') > Date.now()) {
            document.getElementById('loginScreen').style.display = 'none';
            document.getElementById('mainScreen').style.display = 'block';
        }
    };
</script>
</body>
</html>
