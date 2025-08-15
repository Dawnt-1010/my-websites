< html>
<html lang="vi">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Trang Cá Nhân — Lê Đăng Tiến</title>
  <style>
    /* ===== TONE MÀU ===== */
    :root{
      --blue-50:#f0f7ff; /* trắng xanh rất nhạt */
      --blue-100:#e3f2fd;
      --blue-200:#cfe8ff;
      --blue-300:#a8d5ff;
      --blue-400:#75bdf8;
      --blue-500:#3aa0f2; /* xanh chủ đạo */
      --blue-600:#1d85d8;
      --ink:#184A6B;       /* chữ xanh đậm */
      --card:#ffffffcc;    /* glass */
      --border:#d7e9ff99;
      --shadow: 0 10px 30px rgba(24,74,107,.15);
    }

    /* ===== RESET NHẸ ===== */
    *{box-sizing:border-box}
    html,body{height:100%}
    body{
      margin:0; font-family:system-ui, -apple-system, Segoe UI, Roboto, Arial, sans-serif;
      color:var(--ink); overflow-x:hidden;
      background: var(--blue-50);
    }
    a{color:var(--blue-600); text-decoration:none}
    img{max-width:100%; display:block}

    /* ===== NỀN LỚP 1: CARO (PLAID) ===== */
    .plaid-bg{
      position:fixed; inset:0; z-index:-3; pointer-events:none;
      background:
        /* caro chéo mờ */
        repeating-linear-gradient(45deg, rgba(90,160,220,.06) 0 20px, rgba(90,160,220,.09) 20px 40px),
        repeating-linear-gradient(-45deg, rgba(90,160,220,.05) 0 22px, rgba(90,160,220,.08) 22px 44px),
        linear-gradient(#eaf5ff, #f8fbff);
    }

    /* ===== NỀN LỚP 2: SAO LẤP LÁNH ===== */
    .stars{
      position:fixed; inset:-50px; z-index:-2; pointer-events:none;
      background:
        radial-gradient(2px 2px at 20% 30%, rgba(255,255,255,.9) 50%, transparent 51%) 0 0/200px 200px,
        radial-gradient(1.5px 1.5px at 70% 60%, rgba(255,255,255,.8) 50%, transparent 51%) 0 0/180px 180px,
        radial-gradient(1.2px 1.2px at 40% 80%, rgba(255,255,255,.7) 50%, transparent 51%) 0 0/220px 220px,
        radial-gradient(1.8px 1.8px at 85% 25%, rgba(255,255,255,.85) 50%, transparent 51%) 0 0/210px 210px;
      animation: twinkle 6s infinite ease-in-out;
      opacity:.8;
      filter: drop-shadow(0 0 2px rgba(255,255,255,.4));
    }
    @keyframes twinkle{ 50%{opacity:.4} }

    /* ===== NỀN LỚP 3: MÂY BAY ===== */
    .clouds{ position:fixed; inset:0; z-index:-1; pointer-events:none; overflow:hidden; }
    .cloud{
      position:absolute; top:var(--y,10%);
      left:var(--x,-20%);
      width:var(--w,220px); height:calc(var(--w) * .55);
      background: #fff; opacity:.85; border-radius: 60px;
      box-shadow:
        30px -20px 0 10px #fff,
        90px -10px 0 25px #fff,
        160px -25px 0 15px #fff,
        70px 10px 0 20px #fff;
      filter: blur(1px);
      animation: float var(--t,65s) linear infinite;
    }
    @keyframes float{
      from{ transform: translateX(-40vw) translateZ(0) }
      to{   transform: translateX(140vw) translateZ(0) }
    }

    /* ===== LAYOUT CHÍNH ===== */
    header{
      width:min(1100px, 94%); margin: 60px auto 24px; text-align:center;
    }
    .badge{ display:inline-block; padding:6px 12px; border-radius:999px; background: #ffffffaa; border:1px solid var(--border); box-shadow: var(--shadow); font-weight:600 }
    h1{ font-size: clamp(28px, 4vw, 44px); margin:14px 0 6px }
    .subtitle{ color:#3c6e91; margin:0 0 22px; font-size:clamp(15px,2vw,18px) }

    .wrap{ width:min(1100px, 94%); margin:0 auto 80px; display:grid; gap:20px; grid-template-columns: 1fr; }
    @media (min-width:900px){
      .wrap{ grid-template-columns: 360px 1fr; align-items:start }
    }

    .card{
      background: var(--card); backdrop-filter: blur(8px);
      border: 1px solid var(--border); border-radius: 18px; box-shadow: var(--shadow);
    }
    .profile{ padding:18px }
    .avatar{
      width:180px; height:180px; border-radius:50%; margin: 6px auto 12px; overflow:hidden; border:6px solid #ffffffcc; box-shadow: 0 6px 30px rgba(31,93,133,.25);
    }
    .name{ font-size: 22px; font-weight:700; margin:4px 0 }
    .nick{ color:#2b82b7; font-weight:600; margin:0 0 6px }
    .school{ margin:0 0 4px }
    .actions{ display:flex; gap:10px; justify-content:center; flex-wrap:wrap; margin-top:10px }
    .btn{
      padding:10px 14px; border-radius:12px; border:1px solid var(--border);
      background:linear-gradient(180deg, #fff, #f5fbff); font-weight:700;
      box-shadow: var(--shadow); transition: transform .06s ease, box-shadow .2s ease;
    }
    .btn:hover{ transform: translateY(-2px) }

    /* ===== BẢNG LỊCH ===== */
    .table-card{ padding:16px 16px 4px }
    table{ width:100%; border-collapse:collapse; overflow:hidden; border-radius:14px; background:#fff }
    thead th{ background:linear-gradient(180deg, var(--blue-200), #ffffff); color:#0f4e79 }
    th,td{ padding:12px 14px; border:1px solid #e6f0fb; text-align:center }
    tbody tr:nth-child(odd){ background:#f7fbff }

    /* ===== KHỐI "GIỚI THIỆU" ===== */
    .bio{ padding:18px }
    .bio p{ margin:10px 0; font-size:16px }

    /* ===== FOOTER ===== */
    footer{ text-align:center; opacity:.8; padding:30px 0 60px; font-size:14px }
  </style>
</head>
<body>
  <!-- LỚP NỀN -->
  <div class="plaid-bg" aria-hidden="true"></div>
  <div class="stars" aria-hidden="true"></div>
  <div class="clouds" aria-hidden="true">
    <!-- Có thể thêm/bớt mây bằng cách nhân bản các div.cloud bên dưới -->
    <div class="cloud" style="--y:12%; --w:320px; --t:70s"></div>
    <div class="cloud" style="--y:22%; --w:260px; --t:60s; animation-delay:-10s"></div>
    <div class="cloud" style="--y:35%; --w:380px; --t:85s; animation-delay:-20s"></div>
    <div class="cloud" style="--y:58%; --w:300px; --t:72s; animation-delay:-35s"></div>
    <div class="cloud" style="--y:72%; --w:420px; --t:95s; animation-delay:-50s"></div>
  </div>

  <!-- HEADER -->
  <header>
    <span class="badge">💙 Xanh & Trắng — gọn gàng, mát mát</span>
    <h1>Lê Đăng Tiến</h1>
    <p class="subtitle">Sinh viên Công Nghệ Thông Tin — Đại Học Sài Gòn</p>
  </header>

  <main class="wrap">
    <!-- CỘT TRÁI: HỒ SƠ NGẮN -->
    <section class="card profile">
      <div class="avatar">
        <!-- Đổi đường dẫn ảnh tại thuộc tính src bên dưới -->
        <img src="IMG_0790.JPG" alt="Ảnh chân dung của Lê Đăng Tiến" width="180" height="180"/>
      </div>
      <p class="name">Lê Đăng Tiến</p>
      <p class="nick">Biệt danh: Đẹp trai VCL 😎</p>
      <p class="school">Trường: Đại Học Sài Gòn — Khoa CNTT</p>
      <div class="actions">
        <a class="btn" href="https://www.sgu.edu.vn/" target="_blank" rel="noopener">🌐 Trang trường SGU</a>
        <a class="btn" href="#lich">📅 Thời khoá biểu</a>
      </div>
    </section>

    <!-- CỘT PHẢI: GIỚI THIỆU & LỊCH -->
    <section class="card bio">
      <h2 style="margin:4px 0 10px">Giới thiệu nhanh</h2>
      <p>Xin chào các con vk của anh. không biết các em đã đớp gì vào mồm chưa nhỉ,chưa hay rồi thì nhắn cho anh biết nhá.
        Để anh gửi em cái thời khóa biểu hằng ngày của anh nhaa 💙.</p>

      <h2 id="lich" style="margin:20px 0 10px">Lịch hoạt động trong ngày</h2>
      <div class="table-card">
        <table>
          <thead>
            <tr>
              <th>STT</th>
              <th>Buổi</th>
              <th>Hoạt động</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td>1</td>
              <td>Sáng</td>
              <td>đớp</td>
            </tr>
            <tr>
              <td>2</td>
              <td>Trưa</td>
              <td>đớp</td>
            </tr>
            <tr>
              <td>3</td>
              <td>Chiều</td>
              <td>đớp</td>
            </tr>
            <tr>
              <td>4</td>
              <td>Tối</td>
              <td>đớp</td>
            </tr>
          </tbody>
        </table>
      </div>
    </section>
  </main>

  <footer>
    © <span id="y"></span> • Thiết kế bởi Lê Đăng Tiến • Made with 💙
  </footer>

  <script>
    // Cập nhật năm hiện tại ở footer
    document.getElementById('y').textContent = new Date().getFullYear();
  </script>
</body>
</html>
