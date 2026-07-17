
<html lang="vi">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Xưởng Nhạc — Studio soạn nhạc đa nhạc cụ</title>
  <style>
    :root{
      --bg:#120f16;
      --bg2:#1a1620;
      --panel:#211c29;
      --panel2:#2a2433;
      --line:#342d3f;
      --line2:#4b4258;
      --text:#f3ede3;
      --muted:#a49bb2;
      --accent:#e3a24b;
      --accent2:#59b7a7;
      --danger:#da6d8c;
      --good:#78c26d;
      --shadow:0 12px 35px rgba(0,0,0,.28);
      --step-w:28px;
      --row-mel:14px;
      --row-drum:36px;
      --label-w:54px;
      --radius:16px;
    }
    @media (max-width: 720px){
      :root{
        --step-w:20px;
        --row-mel:13px;
        --row-drum:30px;
        --label-w:42px;
      }
    }


*{box-sizing:border-box}
html,body{margin:0;height:100%;background:linear-gradient(180deg,#17131c, #0f0d12);color:var(--text);font-family:system-ui,-apple-system,Segoe UI,Roboto,sans-serif}
body{overflow-x:hidden}
button,input,select{font:inherit}
.hidden{display:none !important}

.screen{
  min-height:100vh;
  display:flex;
  align-items:center;
  justify-content:center;
  padding:18px;
}

.auth-wrap{
  width:min(980px,100%);
  display:grid;
  grid-template-columns:1.1fr .9fr;
  gap:18px;
  align-items:stretch;
}
@media (max-width: 900px){
  .auth-wrap{grid-template-columns:1fr}
}

.hero, .auth-card, .app-shell, .panel, .song-list, .track-card, .note-editor{
  background:linear-gradient(180deg,var(--panel),#1a1620);
  border:1px solid var(--line);
  border-radius:var(--radius);
  box-shadow:var(--shadow);
}

.hero{
  padding:26px;
  position:relative;
  overflow:hidden;
  min-height:420px;
}
.hero::before, .hero::after{
  content:"";
  position:absolute;
  border-radius:999px;
  filter:blur(8px);
  opacity:.28;
  pointer-events:none;
}
.hero::before{width:180px;height:180px;background:var(--accent);top:-30px;right:-30px}
.hero::after{width:260px;height:260px;background:var(--accent2);bottom:-90px;left:-90px}

.brand{
  display:flex;align-items:center;gap:12px;flex-wrap:wrap;margin-bottom:18px
}
.brand-badge{
  width:50px;height:50px;border-radius:16px;
  display:grid;place-items:center;
  background:linear-gradient(135deg,#f1b35e,#d87b9d);
  color:#1d1208;font-size:1.5rem;font-weight:900;
}
.brand h1{margin:0;font-size:2rem;line-height:1.05}
.brand p{margin:.2rem 0 0;color:var(--muted)}
.hero h2{margin:18px 0 10px;font-size:1.45rem}
.hero ul{margin:12px 0 0;padding-left:18px;color:#eadfce;line-height:1.7}
.hero .chips{display:flex;gap:8px;flex-wrap:wrap;margin-top:18px}
.chip{
  background:rgba(255,255,255,.05);
  border:1px solid var(--line);
  color:#f0e7d6;
  padding:8px 12px;
  border-radius:999px;
  font-size:.88rem;
}

.auth-card{
  padding:22px;
  display:flex;
  flex-direction:column;
  gap:14px;
  justify-content:center;
}
.tabs{
  display:flex;
  gap:8px;
  padding:6px;
  background:rgba(255,255,255,.03);
  border:1px solid var(--line);
  border-radius:14px;
}
.tab{
  flex:1;
  border:none;
  background:transparent;
  color:var(--muted);
  padding:12px 10px;
  border-radius:10px;
  cursor:pointer;
  font-weight:700;
}
.tab.active{background:linear-gradient(180deg,var(--accent),#efbd73);color:#1c1207}
.form{
  display:grid;
  gap:12px;
  margin-top:4px;
}
.field{
  display:grid;
  gap:6px;
}
.field label{font-size:.84rem;color:var(--muted);font-weight:700}
.field input, .field select{
  width:100%;
  border:none;
  outline:none;
  background:#15111a;
  color:var(--text);
  border:1px solid var(--line2);
  border-radius:12px;
  padding:12px 12px;
}
.field input:focus, .field select:focus{border-color:var(--accent)}
.primary, .secondary, .danger, .ghost{
  border:none;
  outline:none;
  border-radius:12px;
  padding:11px 14px;
  font-weight:800;
  cursor:pointer;
  transition:.15s transform ease,.15s opacity ease,.15s background ease,border-color .15s ease;
}
.primary{background:linear-gradient(180deg,#f1b35e,#e09b35);color:#1c1207}
.secondary{background:#2e2737;color:var(--text);border:1px solid var(--line2)}
.danger{background:#7b3048;color:#fff;border:1px solid #9f4663}
.ghost{background:transparent;color:var(--text);border:1px solid var(--line2)}
.primary:active,.secondary:active,.danger:active,.ghost:active,.tab:active,.smallbtn:active{transform:scale(.98)}
.msg{min-height:20px;color:#f3d18f;font-size:.92rem}
.msg.good{color:#a9e19f}
.msg.bad{color:#f59db1}

.app-shell{
  display:flex;
  flex-direction:column;
  min-height:100vh;
  border-radius:0;
  border-left:none;
  border-right:none;
}

.topbar{
  position:sticky;top:0;z-index:50;
  background:linear-gradient(180deg,rgba(26,22,32,.98),rgba(26,22,32,.92));
  backdrop-filter:blur(10px);
  border-bottom:1px solid var(--line);
  padding:14px 14px 12px;
}
.topbar-row{
  display:flex;
  align-items:center;
  gap:10px;
  flex-wrap:wrap;
  justify-content:space-between;
}
.app-title{
  display:flex;align-items:center;gap:10px;flex-wrap:wrap
}
.app-title h1{margin:0;font-size:1.2rem}
.app-title small{color:var(--muted)}
.account-pill{
  display:flex;
  align-items:center;
  gap:10px;
  background:rgba(255,255,255,.04);
  border:1px solid var(--line);
  padding:8px 12px;
  border-radius:999px;
  color:var(--text);
  font-size:.92rem;
}

.toolbar{
  display:flex;
  gap:8px;
  flex-wrap:wrap;
  align-items:center;
  margin-top:12px;
}
.toolbar .smallbtn,
.toolbar select,
.toolbar input[type="range"]{
  height:38px;
}
.smallbtn{
  border:none;
  background:#2b2432;
  color:var(--text);
  border:1px solid var(--line2);
  border-radius:11px;
  padding:0 12px;
  cursor:pointer;
  font-weight:800;
  white-space:nowrap;
}
.smallbtn.accent{background:#f1b35e;color:#1d1208;border-color:#f1b35e}
.smallbtn.red{background:#7b3048;color:#fff;border-color:#9f4663}
.smallbtn.green{background:#255b4e;color:#d8fff7;border-color:#3d8777}
.toolbar select{
  background:#18141d;color:var(--text);border:1px solid var(--line2);border-radius:11px;padding:0 10px;
}
.toolbar .range-wrap{
  display:flex;align-items:center;gap:8px;
  background:#18141d;border:1px solid var(--line2);border-radius:11px;padding:0 10px;
  height:38px;
}
.toolbar input[type="range"]{accent-color:var(--accent)}
.toolbar .muted{color:var(--muted);font-size:.82rem}
.toolbar .value{min-width:42px;text-align:right;font-weight:900;color:#f4cc80}

.main{
  display:grid;
  grid-template-columns:minmax(0,1fr) 330px;
  gap:14px;
  padding:14px;
  max-width:1600px;
  width:100%;
  margin:0 auto;
  flex:1;
}
@media (max-width: 1100px){
  .main{grid-template-columns:1fr}
}

.left-col{
  min-width:0;
  display:flex;
  flex-direction:column;
  gap:14px;
}
.right-col{
  min-width:0;
  display:flex;
  flex-direction:column;
  gap:14px;
}

.song-list, .panel, .track-card, .note-editor{
  padding:14px;
}
.section-title{
  display:flex;align-items:center;justify-content:space-between;gap:10px;flex-wrap:wrap;
  margin-bottom:12px;
}
.section-title h3{margin:0;font-size:1rem}
.section-title span{color:var(--muted);font-size:.85rem}
.song-grid{
  display:grid;
  grid-template-columns:1fr auto;
  gap:10px;
  align-items:center;
}
.song-grid select,.song-grid input,.song-grid button{height:40px}
.song-list .row{
  display:flex;gap:8px;flex-wrap:wrap;margin-top:10px
}

.track-creator{
  display:grid;
  grid-template-columns:1fr auto;
  gap:10px;
  align-items:center;
}
.track-creator select{height:40px}
.track-creator .smallbtn{height:40px}

.tracks{
  display:flex;
  flex-direction:column;
  gap:14px;
}

.track-card{
  overflow:hidden;
}
.track-head{
  display:flex;
  gap:8px;
  flex-wrap:wrap;
  align-items:center;
  justify-content:space-between;
  margin-bottom:12px;
}
.track-head .group{
  display:flex;
  gap:8px;
  flex-wrap:wrap;
  align-items:center;
}
.track-head select, .track-head input[type="text"]{
  height:38px;
  background:#15111a;
  color:var(--text);
  border:1px solid var(--line2);
  border-radius:11px;
  padding:0 10px;
}
.track-name{
  min-width:160px;
  max-width:240px;
}
.track-mini{
  display:flex;align-items:center;gap:6px;
  background:rgba(255,255,255,.04);
  border:1px solid var(--line);
  padding:6px 8px;
  border-radius:12px;
  color:var(--muted);
}
.track-mini input[type="range"]{accent-color:var(--accent)}
.track-mini .mini-value{min-width:38px;text-align:right;color:var(--text);font-weight:900}
.toggle{
  display:flex;align-items:center;gap:6px;
  background:rgba(255,255,255,.04);
  border:1px solid var(--line);
  border-radius:12px;
  padding:8px 10px;
  color:var(--muted);
  font-size:.9rem;
}

.roll-wrap{
  display:flex;
  min-width:0;
  overflow:hidden;
  border-radius:14px;
  border:1px solid var(--line);
  background:#15111a;
}
.labels-col{
  width:var(--label-w);
  flex:0 0 auto;
  border-right:1px solid var(--line);
  background:#19141d;
  position:sticky;
  left:0;
  z-index:2;
}
.grid-scroll{
  overflow:auto;
  -webkit-overflow-scrolling:touch;
  flex:1;
  min-width:0;
}
.grid-inner{
  position:relative;
  width:100%;
  min-height:100%;
  touch-action:none;
}
.label-row{
  height:var(--row-mel);
  border-bottom:1px solid rgba(255,255,255,.03);
  font-size:9px;
  color:var(--muted);
  display:flex;
  align-items:center;
  justify-content:flex-end;
  padding-right:6px;
  font-family:Consolas,monospace;
}
.label-row.c-note{color:var(--accent);font-weight:900}
.drum-roll .label-row{
  height:var(--row-drum);
  justify-content:flex-start;
  padding-left:10px;
  font-size:11px;
  font-weight:800;
  color:var(--text);
}

.note-block{
  position:absolute;
  border-radius:6px;
  border:1px solid rgba(0,0,0,.35);
  box-shadow:0 2px 10px rgba(0,0,0,.25);
  cursor:grab;
  user-select:none;
  overflow:hidden;
}
.note-block:active{cursor:grabbing}
.note-block.selected{outline:2px solid #fff; outline-offset:-2px}
.note-block .resize{
  position:absolute;right:0;top:0;height:100%;width:10px;cursor:ew-resize;
  background:linear-gradient(90deg,transparent,rgba(255,255,255,.22));
}
.note-block .tag{
  position:absolute;left:6px;top:50%;transform:translateY(-50%);
  font-size:10px;font-weight:900;
  color:#24160a;
  text-shadow:0 1px 0 rgba(255,255,255,.18);
  white-space:nowrap;
  pointer-events:none;
}

.note-editor .preview{
  display:grid;
  gap:10px;
}
.note-editor .empty{
  color:var(--muted);
  line-height:1.6;
  font-size:.92rem;
}
.note-editor .kv{
  display:grid;
  grid-template-columns:120px 1fr;
  gap:8px;
  align-items:center;
}
.note-editor .kv label{color:var(--muted);font-size:.86rem;font-weight:800}
.note-editor .kv input,.note-editor .kv select{
  width:100%;
  height:38px;
  background:#15111a;
  color:var(--text);
  border:1px solid var(--line2);
  border-radius:11px;
  padding:0 10px;
}
.note-editor .kv input[type="range"]{accent-color:var(--accent)}
.note-editor .actions{
  display:flex;gap:8px;flex-wrap:wrap;margin-top:6px
}

.playhead{
  position:absolute;top:0;bottom:0;width:2px;
  background:var(--accent2);
  box-shadow:0 0 10px var(--accent2);
  z-index:9;
  pointer-events:none;
}

.footer-hint{
  color:var(--muted);
  font-size:.82rem;
  padding:0 14px 12px;
  text-align:center;
}

.fx-layer{
  position:fixed;
  inset:0;
  pointer-events:none;
  overflow:hidden;
  z-index:90;
}
.fx-note{
  position:absolute;
  font-size:18px;
  opacity:0;
  transform:translate(-50%,-50%);
  animation:fxUp 900ms ease-out forwards;
  text-shadow:0 3px 14px rgba(0,0,0,.32);
}
@keyframes fxUp{
  0%{opacity:0;transform:translate(-50%,-20%) scale(.75)}
  20%{opacity:1}
  100%{opacity:0;transform:translate(-50%,-170%) scale(1.2)}
}

.toast{
  position:fixed;
  right:14px;
  bottom:14px;
  z-index:100;
  background:#17131c;
  color:var(--text);
  border:1px solid var(--line2);
  padding:12px 14px;
  border-radius:14px;
  box-shadow:var(--shadow);
  max-width:min(92vw,380px);
}

.kbd{
  border:1px solid var(--line2);
  background:#18141d;
  border-radius:8px;
  padding:2px 7px;
  font-size:.8rem;
  color:var(--text);
}


  </style>
</head>
<body>
  <div id="authScreen" class="screen">
    <div class="auth-wrap">
      <section class="hero">
        <div class="brand">
          <div class="brand-badge">♪</div>
          <div>
            <h1>Koi Music</h1>
            <p>Soạn nhạc đa nhạc cụ và kiến tạo không gian âm nhạc không giới hạn</p>
          </div>
        </div>

```
    <h2>Điểm nổi bật</h2>
    <ul>
      <li>Đăng ký, đăng nhập, đăng xuất ngay trong website.</li>
      <li>Soạn nhiều nhạc cụ cùng lúc: piano, guitar, ukulele, sáo, bass, trống, violin, trumpet.</li>
      <li>Chỉnh nốt theo cao độ, trường độ, cường độ, thăng/giáng và xóa nốt.</li>
      <li>Có preset sẵn, khuông nhạc mở rộng thêm không giới hạn theo ý bạn.</li>
    </ul>

    <div class="chips">
      <span class="chip">Responsive</span>
      <span class="chip">Mobile + PC</span>
      <span class="chip">Lưu cục bộ</span>
      <span class="chip">Piano Roll</span>
      <span class="chip">Nhiều track</span>
    </div>
  </section>

  <section class="auth-card">
    <div class="tabs">
      <button class="tab active" id="tabLogin">Đăng nhập</button>
      <button class="tab" id="tabRegister">Đăng ký</button>
    </div>

    <div class="form" id="loginForm">
      <div class="field">
        <label>Tên tài khoản</label>
        <input id="loginUser" autocomplete="username" placeholder="ví dụ: abc123" />
      </div>
      <div class="field">
        <label>Mật khẩu</label>
        <input id="loginPass" type="password" autocomplete="current-password" placeholder="Nhập mật khẩu" />
      </div>
      <button class="primary" id="btnLogin">Đăng nhập</button>
    </div>

    <div class="form hidden" id="registerForm">
      <div class="field">
        <label>Tên tài khoản mới</label>
        <input id="regUser" autocomplete="username" placeholder="ví dụ: abc123" />
      </div>
      <div class="field">
        <label>Mật khẩu mới</label>
        <input id="regPass" type="password" autocomplete="new-password" placeholder="Tạo mật khẩu" />
      </div>
      <button class="primary" id="btnRegister">Tạo tài khoản</button>
    </div>

    <div id="authMsg" class="msg"></div>
    <div style="color:var(--muted);font-size:.86rem;line-height:1.6">
      Tài khoản và bản nhạc được lưu ngay trên trình duyệt hiện tại. Mỗi tài khoản có thư viện bài riêng.
    </div>
  </section>
</div>
```

  </div>

  <div id="appScreen" class="app-shell hidden">
    <div class="topbar">
      <div class="topbar-row">
        <div class="app-title">
          <h1>🎼 Koi Music</h1>
          <small>soạn nhạc đa nhạc cụ , không giới hạn</small>
        </div>
        <div class="account-pill">
          <span>👤</span>
          <strong id="currentUserLabel">-</strong>
          <button class="smallbtn red" id="btnLogout">Đăng xuất</button>
        </div>
      </div>

```
  <div class="toolbar">
    <button class="smallbtn accent" id="btnPlay">▶ Phát</button>
    <button class="smallbtn red" id="btnStop">■ Dừng</button>

    <div class="range-wrap">
      <span class="muted">BPM</span>
      <input id="bpmRange" type="range" min="40" max="220" value="110" />
      <span class="value" id="bpmValue">110</span>
    </div>

    <label class="toggle">
      <input type="checkbox" id="flatToggle" />
      Hiển thị giáng (♭)
    </label>

    <select id="songSelect"></select>
    <input id="songName" type="text" class="song-name" placeholder="Tên bản nhạc" style="width:min(260px,100%)" />

    <button class="smallbtn green" id="btnNewSong">+ Bản nhạc mới</button>
    <button class="smallbtn" id="btnDuplicateSong">Nhân bản</button>
    <button class="smallbtn" id="btnSaveSong">Lưu</button>
    <button class="smallbtn red" id="btnDeleteSong">Xóa bản nhạc</button>
  </div>

  <div class="toolbar">
    <select id="newTrackInstrument">
      <option value="piano">🎹 Piano</option>
      <option value="guitar">🎸 Guitar</option>
      <option value="ukulele">🪕 Ukulele</option>
      <option value="flute">🎼 Sáo</option>
      <option value="bass">🎻 Bass</option>
      <option value="violin">🎻 Violin</option>
      <option value="trumpet">🎺 Trumpet</option>
      <option value="drums">🥁 Trống</option>
    </select>
    <button class="smallbtn" id="btnAddTrack">+ Thêm nhạc cụ</button>

    <button class="smallbtn" id="btnAddMeasure">+ Thêm khuông (4 nhịp)</button>

    <select id="presetSelect">
      <option value="">— Chọn bản mẫu —</option>
      <option value="twinkle">Twinkle Twinkle</option>
      <option value="ode">Ode to Joy</option>
      <option value="beat">Nhịp trống cơ bản</option>
    </select>
    <button class="smallbtn" id="btnLoadPreset">Tải bản mẫu</button>
    <button class="smallbtn red" id="btnClearAll">Xóa tất cả nốt</button>
  </div>
</div>

<div class="main">
  <div class="left-col">
    <section class="panel">
      <div class="section-title">
        <h3>Thư viện bản nhạc</h3>
        <span>lưu theo từng tài khoản</span>
      </div>
      <div class="song-grid">
        <div class="field" style="margin:0">
          <label>Chọn bản nhạc</label>
          <select id="songListSelect"></select>
        </div>
        <button class="smallbtn" id="btnOpenSong">Mở</button>
      </div>
      <div class="row">
        <button class="smallbtn" id="btnRefreshList">Làm mới danh sách</button>
      </div>
    </section>

    <section class="tracks" id="tracksContainer"></section>
  </div>

  <div class="right-col">
    <section class="note-editor">
      <div class="section-title">
        <h3>Chỉnh nốt</h3>
        <span id="selectedHint">Chọn một nốt để chỉnh</span>
      </div>
      <div id="noteEditorBody" class="preview">
        <div class="empty">
          Bấm vào một nốt để đổi <strong>cao độ</strong>, <strong>trường độ</strong>, <strong>cường độ</strong> hoặc xóa nốt.
          Với track trống, bạn có thể đổi loại tiếng trống ở bảng bên trái.
        </div>
      </div>
    </section>

    <section class="panel">
      <div class="section-title">
        <h3>Hướng dẫn nhanh</h3>
        <span>cảm ứng tốt trên điện thoại</span>
      </div>
      <div style="color:var(--muted);line-height:1.75;font-size:.92rem">
        Chạm vào ô trống để thêm nốt. Kéo nốt để di chuyển. Kéo mép phải để kéo dài. Bấm vào nốt để chọn và chỉnh chi tiết.
        Khi phát nhạc, sẽ có hiệu ứng nốt bay lên theo từng âm thanh.
      </div>
    </section>
  </div>
</div>

<div class="footer-hint">
  Mẹo: có thể thêm khuông nhiều lần để mở rộng bản nhạc. Dữ liệu lưu cục bộ trong trình duyệt của tài khoản đang đăng nhập.
</div>
```

  </div>

  <div id="fxLayer" class="fx-layer"></div>

  <script>
    (() => {
      "use strict";

      // ===== Storage =====
      const STORE_KEY = "xuongnhac_store_v3";
      const CURRENT_KEY = "xuongnhac_current_user_v3";

      const NOTE_SHARP = ["C","C#","D","D#","E","F","F#","G","G#","A","A#","B"];
      const NOTE_FLAT   = ["C","Db","D","Eb","E","F","Gb","G","Ab","A","Bb","B"];
      const DRUM_NAMES = ["Hi-Hat","Clap","Snare","Kick"];
      const INSTRUMENTS = {
        piano:   { label: "🎹 Piano", type: "melodic" },
        guitar:  { label: "🎸 Guitar", type: "melodic" },
        ukulele: { label: "🪕 Ukulele", type: "melodic" },
        flute:   { label: "🎼 Sáo", type: "melodic" },
        bass:    { label: "🎻 Bass", type: "melodic" },
        violin:  { label: "🎻 Violin", type: "melodic" },
        trumpet: { label: "🎺 Trumpet", type: "melodic" },
        drums:   { label: "🥁 Trống", type: "drum" }
      };

      const MIDI_MIN = 36; // C2
      const MIDI_MAX = 95; // B6
      const MEL_ROWS = MIDI_MAX - MIDI_MIN + 1;

      const $ = (sel) => document.querySelector(sel);
      const el = (tag, cls, txt) => {
        const n = document.createElement(tag);
        if (cls) n.className = cls;
        if (txt !== undefined) n.textContent = txt;
        return n;
      };

      const state = {
        store: loadStore(),
        user: null,
        song: null,
        selected: null, // {trackId, noteId}
        showFlat: false,
        playing: false,
        playTimer: null,
        currentStep: 0,
        noteSeq: 1,
        trackSeq: 1,
        bpm: 110,
        totalSteps: 64,
        autosaveTimer: null,
        audioReady: false
      };

      // ===== Audio =====
      const AudioCtx = window.AudioContext || window.webkitAudioContext;
      const audio = new AudioCtx();
      const master = audio.createGain();
      master.gain.value = 0.9;
      master.connect(audio.destination);

      let noiseBuffer = null;
      function getNoise() {
        if (noiseBuffer) return noiseBuffer;
        const len = audio.sampleRate;
        noiseBuffer = audio.createBuffer(1, len, audio.sampleRate);
        const data = noiseBuffer.getChannelData(0);
        for (let i = 0; i < len; i++) data[i] = Math.random() * 2 - 1;
        return noiseBuffer;
      }

      function midiToFreq(midi) {
        return 440 * Math.pow(2, (midi - 69) / 12);
      }
      function midiToName(midi, flat = false) {
        const t = flat ? NOTE_FLAT : NOTE_SHARP;
        return t[((midi % 12) + 12) % 12] + (Math.floor(midi / 12) - 1);
      }
      function rowToMidi(row) {
        return MIDI_MAX - row;
      }
      function midiToRow(midi) {
        return MIDI_MAX - midi;
      }
      function clamp(v, min, max) {
        return Math.max(min, Math.min(max, v));
      }

      function playEnvelope(gainNode, when, attack, decay, sustain, release, vel, dur) {
        const g = gainNode.gain;
        g.cancelScheduledValues(when);
        g.setValueAtTime(0.0001, when);
        g.linearRampToValueAtTime(Math.max(0.0001, vel), when + attack);
        g.linearRampToValueAtTime(Math.max(0.0001, vel * sustain), when + attack + decay);
        const relStart = Math.max(when + attack + decay, when + dur - release);
        g.setValueAtTime(Math.max(0.0001, vel * sustain), relStart);
        g.linearRampToValueAtTime(0.0001, relStart + release);
      }

      function playMelodic(inst, midi, dur, vel, when) {
        const freq = midiToFreq(midi);
        const out = audio.createGain();
        out.connect(master);

        if (inst === "piano") {
          const o1 = audio.createOscillator();
          const o2 = audio.createOscillator();
          const g2 = audio.createGain();
          o1.type = "triangle";
          o2.type = "sine";
          o1.frequency.value = freq;
          o2.frequency.value = freq * 2;
          g2.gain.value = 0.16;
          o1.connect(out);
          o2.connect(g2);
          g2.connect(out);
          playEnvelope(out, when, 0.004, 0.22, 0.36, 0.12, vel, dur);
          o1.start(when); o2.start(when);
          o1.stop(when + dur + 0.25); o2.stop(when + dur + 0.25);
          return;
        }

        if (inst === "guitar") {
          const o = audio.createOscillator();
          const f = audio.createBiquadFilter();
          o.type = "sawtooth";
          o.frequency.value = freq;
          f.type = "lowpass";
          f.frequency.value = 2400;
          f.Q.value = 1;
          o.connect(f); f.connect(out);
          playEnvelope(out, when, 0.003, 0.3, 0.18, 0.18, vel, dur);
          o.start(when); o.stop(when + dur + 0.28);
          return;
        }

        if (inst === "ukulele") {
          const o = audio.createOscillator();
          const f = audio.createBiquadFilter();
          o.type = "triangle";
          o.frequency.value = freq;
          f.type = "lowpass";
          f.frequency.value = 3700;
          o.connect(f); f.connect(out);
          playEnvelope(out, when, 0.002, 0.13, 0.22, 0.1, vel, dur);
          o.start(when); o.stop(when + dur + 0.2);
          return;
        }

        if (inst === "flute") {
          const o = audio.createOscillator();
          const lfo = audio.createOscillator();
          const lfoGain = audio.createGain();
          o.type = "sine";
          o.frequency.value = freq;
          lfo.type = "sine";
          lfo.frequency.value = 5.2;
          lfoGain.gain.value = freq * 0.008;
          lfo.connect(lfoGain);
          lfoGain.connect(o.frequency);
          o.connect(out);
          playEnvelope(out, when, 0.07, 0.12, 0.85, 0.12, vel, dur);
          o.start(when); lfo.start(when);
          o.stop(when + dur + 0.2); lfo.stop(when + dur + 0.2);
          return;
        }

        if (inst === "bass") {
          const o1 = audio.createOscillator();
          const o2 = audio.createOscillator();
          const f = audio.createBiquadFilter();
          o1.type = "sine";
          o2.type = "triangle";
          o1.frequency.value = freq;
          o2.frequency.value = freq;
          f.type = "lowpass";
          f.frequency.value = 900;
          const g2 = audio.createGain();
          g2.gain.value = 0.36;
          o1.connect(f);
          o2.connect(g2);
          g2.connect(f);
          f.connect(out);
          playEnvelope(out, when, 0.01, 0.22, 0.58, 0.15, vel, dur);
          o1.start(when); o2.start(when);
          o1.stop(when + dur + 0.18); o2.stop(when + dur + 0.18);
          return;
        }

        if (inst === "violin") {
          const o = audio.createOscillator();
          const lfo = audio.createOscillator();
          const lfoGain = audio.createGain();
          const f = audio.createBiquadFilter();
          o.type = "sawtooth";
          o.frequency.value = freq;
          lfo.type = "sine";
          lfo.frequency.value = 6.2;
          lfoGain.gain.value = freq * 0.009;
          lfo.connect(lfoGain);
          lfoGain.connect(o.frequency);
          f.type = "bandpass";
          f.frequency.value = freq * 2;
          f.Q.value = 0.8;
          o.connect(f); f.connect(out);
          playEnvelope(out, when, 0.05, 0.16, 0.7, 0.15, vel, dur);
          o.start(when); lfo.start(when);
          o.stop(when + dur + 0.2); lfo.stop(when + dur + 0.2);
          return;
        }

        if (inst === "trumpet") {
          const o = audio.createOscillator();
          const f = audio.createBiquadFilter();
          o.type = "square";
          o.frequency.value = freq;
          f.type = "bandpass";
          f.frequency.value = freq * 1.45;
          f.Q.value = 1.2;
          o.connect(f); f.connect(out);
          playEnvelope(out, when, 0.02, 0.1, 0.72, 0.12, vel, dur);
          o.start(when); o.stop(when + dur + 0.2);
          return;
        }

        const o = audio.createOscillator();
        o.type = "sine";
        o.frequency.value = freq;
        o.connect(out);
        playEnvelope(out, when, 0.02, 0.14, 0.55, 0.12, vel, dur);
        o.start(when); o.stop(when + dur + 0.2);
      }

      function playDrum(name, vel, when) {
        const noise = getNoise();

        if (name === "Kick") {
          const o = audio.createOscillator();
          const g = audio.createGain();
          o.type = "sine";
          o.frequency.setValueAtTime(150, when);
          o.frequency.exponentialRampToValueAtTime(40, when + 0.12);
          g.gain.setValueAtTime(vel, when);
          g.gain.exponentialRampToValueAtTime(0.001, when + 0.32);
          o.connect(g); g.connect(master);
          o.start(when); o.stop(when + 0.35);
          return;
        }

        if (name === "Snare") {
          const src = audio.createBufferSource();
          src.buffer = noise;
          const f = audio.createBiquadFilter();
          const g = audio.createGain();
          f.type = "bandpass";
          f.frequency.value = 1800;
          g.gain.setValueAtTime(vel * 0.8, when);
          g.gain.exponentialRampToValueAtTime(0.001, when + 0.16);
          src.connect(f); f.connect(g); g.connect(master);
          const o = audio.createOscillator();
          const g2 = audio.createGain();
          o.type = "triangle";
          o.frequency.value = 200;
          g2.gain.setValueAtTime(vel * 0.35, when);
          g2.gain.exponentialRampToValueAtTime(0.001, when + 0.12);
          o.connect(g2); g2.connect(master);
          src.start(when); src.stop(when + 0.18);
          o.start(when); o.stop(when + 0.15);
          return;
        }

        if (name === "Hi-Hat") {
          const src = audio.createBufferSource();
          src.buffer = noise;
          const f = audio.createBiquadFilter();
          const g = audio.createGain();
          f.type = "highpass";
          f.frequency.value = 7000;
          g.gain.setValueAtTime(vel * 0.6, when);
          g.gain.exponentialRampToValueAtTime(0.001, when + 0.07);
          src.connect(f); f.connect(g); g.connect(master);
          src.start(when); src.stop(when + 0.08);
          return;
        }

        if (name === "Clap") {
          for (let i = 0; i < 3; i++) {
            const t = when + i * 0.012;
            const src = audio.createBufferSource();
            src.buffer = noise;
            const f = audio.createBiquadFilter();
            const g = audio.createGain();
            f.type = "bandpass";
            f.frequency.value = 1600;
            g.gain.setValueAtTime(vel * 0.55, t);
            g.gain.exponentialRampToValueAtTime(0.001, t + 0.09);
            src.connect(f); f.connect(g); g.connect(master);
            src.start(t); src.stop(t + 0.1);
          }
        }
      }

      // ===== Data =====
      function nowISO() {
        return new Date().toISOString();
      }

      function genId(prefix = "id") {
        return prefix + "_" + Math.random().toString(36).slice(2, 10) + Date.now().toString(36);
      }

      function hashText(text) {
        return crypto.subtle.digest("SHA-256", new TextEncoder().encode(text)).then(buf => {
          return Array.from(new Uint8Array(buf)).map(v => v.toString(16).padStart(2, "0")).join("");
        });
      }

      function loadStore() {
        try {
          const raw = localStorage.getItem(STORE_KEY);
          if (!raw) return { users: {} };
          const parsed = JSON.parse(raw);
          if (!parsed.users) parsed.users = {};
          return parsed;
        } catch {
          return { users: {} };
        }
      }

      function saveStore() {
        localStorage.setItem(STORE_KEY, JSON.stringify(state.store));
      }

      function getCurrentUserName() {
        return localStorage.getItem(CURRENT_KEY) || "";
      }

      function setCurrentUserName(name) {
        if (name) localStorage.setItem(CURRENT_KEY, name);
        else localStorage.removeItem(CURRENT_KEY);
      }

      function makeTrack(instrument = "piano", name = "") {
        return {
          id: state.trackSeq++,
          instrument,
          name: name || INSTRUMENTS[instrument].label.replace(/^[^\s]+\s/, ""),
          volume: 0.85,
          octaveShift: 0,
          muted: false,
          notes: []
        };
      }

      function makeSong(name = "Bản nhạc mới") {
        return {
          id: genId("song"),
          name,
          bpm: 110,
          totalSteps: 64,
          tracks: [makeTrack("piano", "Piano 1")],
          createdAt: nowISO(),
          updatedAt: nowISO()
        };
      }

      function ensureUser(userName, passHash) {
        if (!state.store.users[userName]) {
          state.store.users[userName] = {
            passHash,
            songs: {},
            songOrder: [],
            lastSongId: ""
          };
        }
        return state.store.users[userName];
      }

      function currentUserData() {
        if (!state.user) return null;
        return state.store.users[state.user] || null;
      }

      function saveSongToUser() {
        const u = currentUserData();
        if (!u || !state.song) return;
        state.song.updatedAt = nowISO();
        u.songs[state.song.id] = JSON.parse(JSON.stringify(state.song));
        if (!u.songOrder.includes(state.song.id)) u.songOrder.unshift(state.song.id);
        u.lastSongId = state.song.id;
        saveStore();
      }

      function restoreSong(song) {
        state.song = JSON.parse(JSON.stringify(song));
        state.bpm = song.bpm || 110;
        state.totalSteps = song.totalSteps || 64;
        state.noteSeq = 1;
        state.trackSeq = 1;
        // restore next ids
        for (const t of state.song.tracks) {
          if (t.id >= state.trackSeq) state.trackSeq = t.id + 1;
          for (const n of t.notes) {
            if (n.id >= state.noteSeq) state.noteSeq = n.id + 1;
          }
        }
        state.selected = null;
        $("#bpmRange").value = state.bpm;
        $("#bpmValue").textContent = state.bpm;
        $("#songName").value = state.song.name || "";
        renderAll();
        renderSongList();
        renderNoteEditor();
      }

      function createDefaultSongForNewUser() {
        const song = makeSong("Bản nhạc đầu tiên");
        song.tracks = [
          makeTrack("piano", "Piano"),
          makeTrack("bass", "Bass"),
          makeTrack("drums", "Trống")
        ];
        song.totalSteps = 64;
        song.bpm = 110;
        // sample melody
        const melody = [
          ["C4",0,4],["C4",4,4],["G4",8,4],["G4",12,4],["A4",16,4],["A4",20,4],["G4",24,8],
          ["F4",32,4],["F4",36,4],["E4",40,4],["E4",44,4],["D4",48,4],["D4",52,4],["C4",56,8]
        ];
        melody.forEach(([note, step, len]) => {
          song.tracks[0].notes.push({
            id: state.noteSeq++,
            step, length: len,
            midi: noteToMidi(note),
            velocity: 0.85
          });
        });
        [["C2",0,16],["G2",16,16],["C2",32,16],["G2",48,16]].forEach(([note, step, len]) => {
          song.tracks[1].notes.push({
            id: state.noteSeq++,
            step, length: len,
            midi: noteToMidi(note),
            velocity: 0.7
          });
        });
        for (let s = 0; s < 64; s += 8) song.tracks[2].notes.push({ id: state.noteSeq++, step:s, length:1, drum:3, velocity:0.95 });
        for (let s = 4; s < 64; s += 8) song.tracks[2].notes.push({ id: state.noteSeq++, step:s, length:1, drum:2, velocity:0.8 });
        for (let s = 0; s < 64; s += 2) song.tracks[2].notes.push({ id: state.noteSeq++, step:s, length:1, drum:0, velocity:0.45 });
        return song;
      }

      function noteToMidi(note) {
        const m = String(note).match(/^([A-G]#?)(-?\d+)$/);
        if (!m) return 60;
        const idx = NOTE_SHARP.indexOf(m[1]);
        return (parseInt(m[2], 10) + 1) * 12 + idx;
      }

      // ===== UI refs =====
      const authScreen = $("#authScreen");
      const appScreen = $("#appScreen");
      const tracksContainer = $("#tracksContainer");
      const fxLayer = $("#fxLayer");

      // Auth widgets
      const tabLogin = $("#tabLogin");
      const tabRegister = $("#tabRegister");
      const loginForm = $("#loginForm");
      const registerForm = $("#registerForm");
      const authMsg = $("#authMsg");
      const loginUser = $("#loginUser");
      const loginPass = $("#loginPass");
      const regUser = $("#regUser");
      const regPass = $("#regPass");

      // App widgets
      const currentUserLabel = $("#currentUserLabel");
      const btnLogout = $("#btnLogout");
      const btnPlay = $("#btnPlay");
      const btnStop = $("#btnStop");
      const bpmRange = $("#bpmRange");
      const bpmValue = $("#bpmValue");
      const flatToggle = $("#flatToggle");
      const songSelect = $("#songSelect");
      const songName = $("#songName");
      const btnNewSong = $("#btnNewSong");
      const btnDuplicateSong = $("#btnDuplicateSong");
      const btnSaveSong = $("#btnSaveSong");
      const btnDeleteSong = $("#btnDeleteSong");
      const btnAddTrack = $("#btnAddTrack");
      const btnAddMeasure = $("#btnAddMeasure");
      const newTrackInstrument = $("#newTrackInstrument");
      const presetSelect = $("#presetSelect");
      const btnLoadPreset = $("#btnLoadPreset");
      const btnClearAll = $("#btnClearAll");
      const songListSelect = $("#songListSelect");
      const btnOpenSong = $("#btnOpenSong");
      const btnRefreshList = $("#btnRefreshList");
      const noteEditorBody = $("#noteEditorBody");
      const selectedHint = $("#selectedHint");

      // ===== Auth =====
      function showAuthMsg(text, type = "") {
        authMsg.textContent = text;
        authMsg.className = "msg " + (type || "");
      }

      function openApp() {
        authScreen.classList.add("hidden");
        appScreen.classList.remove("hidden");
      }

      function closeApp() {
        appScreen.classList.add("hidden");
        authScreen.classList.remove("hidden");
      }

      function fillSongSelector() {
        const u = currentUserData();
        if (!u) return;
        songSelect.innerHTML = "";
        songListSelect.innerHTML = "";

        const ids = u.songOrder.length ? u.songOrder : Object.keys(u.songs);
        if (!ids.length && state.song) ids.push(state.song.id);

        ids.forEach(id => {
          const s = u.songs[id];
          if (!s) return;
          const opt1 = new Option(s.name || "Không tên", id);
          const opt2 = new Option(s.name || "Không tên", id);
          songSelect.add(opt1);
          songListSelect.add(opt2);
        });

        if (state.song && u.songs[state.song.id]) {
          songSelect.value = state.song.id;
          songListSelect.value = state.song.id;
          songName.value = state.song.name || "";
        }
      }

      async function register() {
        const user = regUser.value.trim();
        const pass = regPass.value;
        if (user.length < 3) return showAuthMsg("Tên tài khoản cần ít nhất 3 ký tự.", "bad");
        if (pass.length < 4) return showAuthMsg("Mật khẩu cần ít nhất 4 ký tự.", "bad");
        if (state.store.users[user]) return showAuthMsg("Tài khoản này đã tồn tại.", "bad");

        const passHash = await hashText(pass);
        state.store.users[user] = {
          passHash,
          songs: {},
          songOrder: [],
          lastSongId: ""
        };
        const userData = state.store.users[user];
        const song = createDefaultSongForNewUser();
        userData.songs[song.id] = song;
        userData.songOrder = [song.id];
        userData.lastSongId = song.id;
        saveStore();
        setCurrentUserName(user);
        state.user = user;
        restoreSong(song);
        fillSongSelector();
        currentUserLabel.textContent = user;
        openApp();
      }

      async function login() {
        const user = loginUser.value.trim();
        const pass = loginPass.value;
        if (!user || !pass) return showAuthMsg("Nhập đủ tên tài khoản và mật khẩu.", "bad");
        const account = state.store.users[user];
        if (!account) return showAuthMsg("Không tìm thấy tài khoản.", "bad");

        const passHash = await hashText(pass);
        if (passHash !== account.passHash) return showAuthMsg("Sai mật khẩu.", "bad");

        state.user = user;
        setCurrentUserName(user);
        currentUserLabel.textContent = user;

        // load last song or create one
        let songId = account.lastSongId;
        if (!songId || !account.songs[songId]) {
          const ids = account.songOrder.length ? account.songOrder : Object.keys(account.songs);
          songId = ids[0];
        }
        if (!songId) {
          const song = createDefaultSongForNewUser();
          account.songs[song.id] = song;
          account.songOrder = [song.id];
          account.lastSongId = song.id;
          saveStore();
          restoreSong(song);
        } else {
          restoreSong(account.songs[songId]);
        }
        fillSongSelector();
        openApp();
      }

      function logout() {
        stopPlayback();
        state.user = null;
        state.song = null;
        setCurrentUserName("");
        closeApp();
      }

      tabLogin.onclick = () => {
        tabLogin.classList.add("active");
        tabRegister.classList.remove("active");
        loginForm.classList.remove("hidden");
        registerForm.classList.add("hidden");
        authMsg.textContent = "";
      };
      tabRegister.onclick = () => {
        tabRegister.classList.add("active");
        tabLogin.classList.remove("active");
        registerForm.classList.remove("hidden");
        loginForm.classList.add("hidden");
        authMsg.textContent = "";
      };

      $("#btnLogin").onclick = login;
      $("#btnRegister").onclick = register;
      btnLogout.onclick = logout;

      // ===== Song management =====
      function createSongFromCurrent(copyNameSuffix = "") {
        const s = makeSong((state.song?.name || "Bản nhạc") + copyNameSuffix);
        s.bpm = state.bpm;
        s.totalSteps = state.totalSteps;
        s.tracks = JSON.parse(JSON.stringify(state.song?.tracks || [makeTrack("piano", "Piano 1")]));
        s.id = genId("song");
        s.createdAt = nowISO();
        s.updatedAt = nowISO();
        return s;
      }

      function createNewSong() {
        const s = makeSong("Bản nhạc mới");
        s.tracks = [makeTrack("piano", "Piano 1")];
        state.song = s;
        state.bpm = s.bpm;
        state.totalSteps = s.totalSteps;
        state.selected = null;
        renderAll();
        fillSongSelector();
        debouncedSave();
      }

      function deleteCurrentSong() {
        const u = currentUserData();
        if (!u || !state.song) return;
        if (!confirm("Xóa bản nhạc này?")) return;
        delete u.songs[state.song.id];
        u.songOrder = u.songOrder.filter(id => id !== state.song.id);
        if (!u.songOrder.length && Object.keys(u.songs).length === 0) {
          const s = createDefaultSongForNewUser();
          u.songs[s.id] = s;
          u.songOrder = [s.id];
          u.lastSongId = s.id;
          state.song = s;
          state.user = state.user;
        } else {
          const nextId = u.songOrder[0] || Object.keys(u.songs)[0];
          u.lastSongId = nextId;
          state.song = JSON.parse(JSON.stringify(u.songs[nextId]));
        }
        saveStore();
        restoreSong(state.song);
        fillSongSelector();
      }

      function openSelectedSong(songId) {
        const u = currentUserData();
        if (!u || !u.songs[songId]) return;
        state.song = JSON.parse(JSON.stringify(u.songs[songId]));
        state.bpm = state.song.bpm || 110;
        state.totalSteps = state.song.totalSteps || 64;
        bpmRange.value = state.bpm;
        bpmValue.textContent = state.bpm;
        songName.value = state.song.name || "";
        selectedHint.textContent = "Chọn một nốt để chỉnh";
        state.selected = null;
        renderAll();
      }

      function saveSong() {
        if (!state.song) return;
        state.song.name = songName.value.trim() || "Bản nhạc";
        state.song.bpm = state.bpm;
        state.song.totalSteps = state.totalSteps;
        const u = currentUserData();
        if (!u) return;
        u.songs[state.song.id] = JSON.parse(JSON.stringify(state.song));
        if (!u.songOrder.includes(state.song.id)) u.songOrder.unshift(state.song.id);
        u.lastSongId = state.song.id;
        saveStore();
        fillSongSelector();
        toast("Đã lưu bản nhạc.");
      }

      function duplicateSong() {
        if (!state.song) return;
        const u = currentUserData();
        if (!u) return;
        const s = createSongFromCurrent(" (bản sao)");
        s.name = (state.song.name || "Bản nhạc") + " (bản sao)";
        u.songs[s.id] = JSON.parse(JSON.stringify(s));
        u.songOrder.unshift(s.id);
        u.lastSongId = s.id;
        saveStore();
        state.song = JSON.parse(JSON.stringify(s));
        state.bpm = s.bpm;
        state.totalSteps = s.totalSteps;
        state.selected = null;
        renderAll();
        fillSongSelector();
        toast("Đã nhân bản bản nhạc.");
      }

      function debouncedSave() {
        clearTimeout(state.autosaveTimer);
        state.autosaveTimer = setTimeout(() => {
          if (!state.song || !state.user) return;
          saveSong();
        }, 350);
      }

      // ===== Rendering =====
      function noteColor(inst) {
        const map = {
          piano: "#e6ac56",
          guitar: "#d77ea0",
          ukulele: "#8fd0c4",
          flute: "#79a8e2",
          bass: "#c390e4",
          violin: "#e0a9dc",
          trumpet: "#e0d070",
          drums: "#58b7a7"
        };
        return map[inst] || "#e6ac56";
      }

      function stepWidth() {
        return parseFloat(getComputedStyle(document.documentElement).getPropertyValue("--step-w"));
      }
      function rowHeight(isDrum) {
        return parseFloat(getComputedStyle(document.documentElement).getPropertyValue(isDrum ? "--row-drum" : "--row-mel"));
      }

      function renderAll() {
        if (!state.song) return;
        state.bpm = state.song.bpm || state.bpm;
        state.totalSteps = state.song.totalSteps || state.totalSteps;
        bpmRange.value = state.bpm;
        bpmValue.textContent = state.bpm;
        songName.value = state.song.name || "";
        currentUserLabel.textContent = state.user || "-";
        renderSongList();
        renderTracks();
        renderNoteEditor();
      }

      function renderSongList() {
        const u = currentUserData();
        if (!u) return;
        fillSongSelector();
        const songIds = u.songOrder.length ? u.songOrder : Object.keys(u.songs);
        songListSelect.innerHTML = "";
        songSelect.innerHTML = "";
        songIds.forEach(id => {
          const s = u.songs[id];
          if (!s) return;
          songListSelect.add(new Option(s.name || "Không tên", id));
          songSelect.add(new Option(s.name || "Không tên", id));
        });
        if (state.song && state.song.id) {
          songSelect.value = state.song.id;
          songListSelect.value = state.song.id;
        }
      }

      function renderTracks() {
        tracksContainer.innerHTML = "";
        if (!state.song) return;

        state.song.tracks.forEach(track => {
          const isDrum = INSTRUMENTS[track.instrument].type === "drum";
          const card = el("section", "track-card");

          const head = el("div", "track-head");
          const left = el("div", "group");

          const nameInput = el("input");
          nameInput.className = "track-name";
          nameInput.value = track.name || "";
          nameInput.placeholder = "Tên nhạc cụ";
          nameInput.oninput = () => {
            track.name = nameInput.value;
            debouncedSave();
          };

          const instSelect = el("select");
          Object.entries(INSTRUMENTS).forEach(([key, info]) => {
            const op = new Option(info.label, key);
            if (key === track.instrument) op.selected = true;
            instSelect.add(op);
          });
          instSelect.onchange = () => {
            const before = INSTRUMENTS[track.instrument].type;
            const after = INSTRUMENTS[instSelect.value].type;
            track.instrument = instSelect.value;
            if (before !== after) {
              // đổi loại nhạc cụ thì reset nốt để tránh lỗi dữ liệu
              track.notes = [];
              state.selected = null;
            }
            renderTracks();
            renderNoteEditor();
            debouncedSave();
          };

          const vol = el("div", "track-mini");
          vol.innerHTML = `<span>Âm lượng</span>`;
          const volRange = document.createElement("input");
          volRange.type = "range";
          volRange.min = 0;
          volRange.max = 1;
          volRange.step = 0.05;
          volRange.value = track.volume ?? 0.85;
          const volVal = el("span", "mini-value", String(track.volume ? Number(track.volume).toFixed(2) : "0.85"));
          volRange.oninput = () => {
            track.volume = parseFloat(volRange.value);
            volVal.textContent = Number(track.volume).toFixed(2);
            debouncedSave();
          };
          vol.append(volRange, volVal);

          const oct = el("div", "track-mini");
          oct.innerHTML = `<span>Cao độ</span>`;
          const btnDown = el("button", "smallbtn", "▼");
          const octVal = el("span", "mini-value", `x${track.octaveShift || 0}`);
          const btnUp = el("button", "smallbtn", "▲");
          btnDown.onclick = () => {
            track.octaveShift = clamp((track.octaveShift || 0) - 1, -3, 3);
            octVal.textContent = `x${track.octaveShift}`;
            debouncedSave();
          };
          btnUp.onclick = () => {
            track.octaveShift = clamp((track.octaveShift || 0) + 1, -3, 3);
            octVal.textContent = `x${track.octaveShift}`;
            debouncedSave();
          };
          oct.append(btnDown, octVal, btnUp);

          const mute = el("label", "toggle");
          mute.style.margin = "0";
          const muteCheck = document.createElement("input");
          muteCheck.type = "checkbox";
          muteCheck.checked = !!track.muted;
          muteCheck.onchange = () => {
            track.muted = muteCheck.checked;
            debouncedSave();
          };
          mute.append(muteCheck, document.createTextNode("Tắt tiếng"));

          left.append(instSelect, nameInput, vol, oct, mute);

          const right = el("div", "group");
          const del = el("button", "smallbtn red", "Xóa");
          del.onclick = () => {
            if (!confirm("Xóa nhạc cụ này?")) return;
            state.song.tracks = state.song.tracks.filter(t => t.id !== track.id);
            if (state.selected && state.selected.trackId === track.id) state.selected = null;
            renderTracks();
            renderNoteEditor();
            debouncedSave();
          };
          right.append(del);

          head.append(left, right);
          card.appendChild(head);

          const roll = el("div", "roll-wrap" + (isDrum ? " drum-roll" : ""));
          const labels = el("div", "labels-col");
          const rows = isDrum ? DRUM_NAMES.length : MEL_ROWS;
          for (let r = 0; r < rows; r++) {
            const row = el("div", "label-row");
            if (isDrum) {
              row.textContent = DRUM_NAMES[r];
            } else {
              const midi = rowToMidi(r);
              const name = midiToName(midi, state.showFlat);
              row.textContent = name;
              if (name.replace(/\d+/g, "").replace(/b/g, "").replace(/#/g, "") === "C") {
                row.classList.add("c-note");
              }
            }
            labels.appendChild(row);
          }

          const scroll = el("div", "grid-scroll");
          const inner = el("div", "grid-inner");
          const sw = stepWidth();
          const rh = rowHeight(isDrum);
          inner.style.height = rows * rh + "px";
          inner.style.width = state.totalSteps * sw + "px";

          const measurePx = 16 * sw;
          inner.style.backgroundImage =
            `repeating-linear-gradient(to right, var(--line2) 0, var(--line2) 1px, transparent 1px, transparent ${measurePx}px),` +
            `repeating-linear-gradient(to right, var(--line) 0, var(--line) 1px, transparent 1px, transparent ${sw}px),` +
            `repeating-linear-gradient(to bottom, var(--line) 0, var(--line) 1px, transparent 1px, transparent ${rh}px)`;

          track.notes.forEach(note => {
            const noteEl = buildNoteEl(track, note, sw, rh, isDrum);
            inner.appendChild(noteEl);
          });

          attachGridInteraction(inner, track, isDrum, sw, rh);
          scroll.appendChild(inner);
          roll.append(labels, scroll);
          card.appendChild(roll);

          tracksContainer.appendChild(card);
        });

        updatePlayheads();
      }

      function buildNoteEl(track, note, sw, rh, isDrum) {
        const n = el("div", "note-block");
        n.dataset.noteId = note.id;
        n.dataset.trackId = track.id;

        const row = isDrum ? (note.drum ?? 0) : midiToRow(note.midi);
        n.style.left = (note.step * sw) + "px";
        n.style.top = (row * rh) + "px";
        n.style.width = Math.max(1, note.length * sw - 2) + "px";
        n.style.height = (rh - 2) + "px";
        n.style.background = noteColor(track.instrument);
        n.style.opacity = 0.35 + (note.velocity ?? 0.8) * 0.65;

        const tag = el("div", "tag");
        if (isDrum) {
          tag.textContent = DRUM_NAMES[row] || "Drum";
        } else {
          tag.textContent = midiToName(note.midi, state.showFlat);
        }
        n.appendChild(tag);

        if (!isDrum) {
          const resize = el("div", "resize");
          resize.dataset.role = "resize";
          n.appendChild(resize);
        }

        if (state.selected && state.selected.trackId === track.id && state.selected.noteId === note.id) {
          n.classList.add("selected");
        }

        n.addEventListener("pointerdown", (e) => onNotePointerDown(e, track, note, n, isDrum, sw, rh));
        return n;
      }

      function onNotePointerDown(e, track, note, noteEl, isDrum, sw, rh) {
        const target = e.target;
        const isResize = target && target.dataset && target.dataset.role === "resize";
        selectNote(track.id, note.id);
        e.preventDefault();

        const grid = noteEl.parentElement;
        const rect = grid.getBoundingClientRect();
        let startX = e.clientX - rect.left;
        let startY = e.clientY - rect.top;

        let moved = false;
        let mode = isResize ? "resize" : "maybe-move";

        const startStep = note.step;
        const startRow = isDrum ? (note.drum ?? 0) : midiToRow(note.midi);
        const startLength = note.length;

        const move = (ev) => {
          const x = ev.clientX - rect.left;
          const y = ev.clientY - rect.top;
          const dx = Math.abs(x - startX);
          const dy = Math.abs(y - startY);

          if (mode === "maybe-move" && (dx > 6 || dy > 6)) mode = "move";

          if (mode === "resize") {
            const endStep = Math.floor(x / sw);
            const newLen = Math.max(1, endStep - startStep + 1);
            if (newLen !== note.length) {
              note.length = newLen;
              moved = true;
              noteEl.style.width = (note.length * sw - 2) + "px";
              debouncedSave();
            }
          } else if (mode === "move") {
            const newStep = clamp(Math.floor(x / sw), 0, Math.max(0, state.totalSteps - note.length));
            const maxRow = isDrum ? DRUM_NAMES.length - 1 : MEL_ROWS - 1;
            const newRow = clamp(Math.floor(y / rh), 0, maxRow);
            if (isDrum) {
              if (newStep !== note.step || newRow !== note.drum) {
                note.step = newStep;
                note.drum = newRow;
                moved = true;
                noteEl.style.left = (newStep * sw) + "px";
                noteEl.style.top = (newRow * rh) + "px";
                debouncedSave();
              }
            } else {
              const newMidi = rowToMidi(newRow);
              if (newStep !== note.step || newMidi !== note.midi) {
                note.step = newStep;
                note.midi = newMidi;
                moved = true;
                noteEl.style.left = (newStep * sw) + "px";
                noteEl.style.top = (newRow * rh) + "px";
                noteEl.querySelector(".tag").textContent = midiToName(newMidi, state.showFlat);
                debouncedSave();
              }
            }
          }
        };

        const up = () => {
          document.removeEventListener("pointermove", move);
          document.removeEventListener("pointerup", up);
          if (!moved && mode === "maybe-move") {
            // Chạm nhẹ vào nốt => chọn nốt, không xóa ngay.
            renderTracks();
            renderNoteEditor();
          }
        };

        document.addEventListener("pointermove", move);
        document.addEventListener("pointerup", up);
      }

      function selectNote(trackId, noteId) {
        state.selected = { trackId, noteId };
        renderTracks();
        renderNoteEditor();
      }

      function selectedObjects() {
        if (!state.song || !state.selected) return { track: null, note: null };
        const track = state.song.tracks.find(t => t.id === state.selected.trackId) || null;
        const note = track ? track.notes.find(n => n.id === state.selected.noteId) || null : null;
        return { track, note };
      }

      function renderNoteEditor() {
        const { track, note } = selectedObjects();
        noteEditorBody.innerHTML = "";

        if (!track || !note) {
          selectedHint.textContent = "Chọn một nốt để chỉnh";
          const empty = el("div", "empty");
          empty.innerHTML = `Bấm vào một nốt để chỉnh <strong>cao độ</strong>, <strong>trường độ</strong>, <strong>cường độ</strong> hoặc <strong>xóa</strong> nốt.`;
          noteEditorBody.appendChild(empty);
          return;
        }

        selectedHint.textContent = `Track: ${track.name || "Không tên"}`;

        const isDrum = INSTRUMENTS[track.instrument].type === "drum";
        const body = el("div", "preview");

        const info = el("div", "toggle");
        info.style.display = "block";
        info.innerHTML = `<strong>Đã chọn:</strong> ${isDrum ? (DRUM_NAMES[note.drum ?? 0] || "Drum") : midiToName(note.midi, state.showFlat)}<br>
          <span style="color:var(--muted)">Nhạc cụ: ${INSTRUMENTS[track.instrument].label} · Ô nhịp: ${note.step} · Dài: ${note.length}</span>`;

        body.appendChild(info);

        const kv1 = el("div", "kv");
        kv1.appendChild(el("label", "", "Vị trí"));
        const pos = document.createElement("input");
        pos.type = "number";
        pos.min = 0;
        pos.max = Math.max(0, state.totalSteps - 1);
        pos.value = note.step;
        pos.oninput = () => {
          note.step = clamp(parseInt(pos.value || "0", 10), 0, Math.max(0, state.totalSteps - note.length));
          renderTracks();
          debouncedSave();
        };
        kv1.appendChild(pos);
        body.appendChild(kv1);

        const kv2 = el("div", "kv");
        kv2.appendChild(el("label", "", "Trường độ"));
        const len = document.createElement("input");
        len.type = "range";
        len.min = 1;
        len.max = 32;
        len.value = note.length;
        const lenVal = el("span", "muted");
        lenVal.style.gridColumn = "1 / -1";
        lenVal.textContent = `Dài nốt: ${note.length}`;
        len.oninput = () => {
          note.length = parseInt(len.value, 10);
          lenVal.textContent = `Dài nốt: ${note.length}`;
          renderTracks();
          debouncedSave();
        };
        kv2.appendChild(len);
        body.appendChild(kv2);
        body.appendChild(lenVal);

        const kv3 = el("div", "kv");
        kv3.appendChild(el("label", "", "Cường độ"));
        const vel = document.createElement("input");
        vel.type = "range";
        vel.min = 0.1;
        vel.max = 1;
        vel.step = 0.01;
        vel.value = note.velocity ?? 0.8;
        const velVal = el("span", "muted");
        velVal.style.gridColumn = "1 / -1";
        velVal.textContent = `Cường độ: ${Number(vel.value).toFixed(2)}`;
        vel.oninput = () => {
          note.velocity = parseFloat(vel.value);
          velVal.textContent = `Cường độ: ${Number(note.velocity).toFixed(2)}`;
          renderTracks();
          debouncedSave();
        };
        kv3.appendChild(vel);
        body.appendChild(kv3);
        body.appendChild(velVal);

        if (!isDrum) {
          const kv4 = el("div", "kv");
          kv4.appendChild(el("label", "", "Nốt"));
          const pitch = document.createElement("input");
          pitch.type = "range";
          pitch.min = 0;
          pitch.max = 11;
          pitch.step = 1;
          pitch.value = ((note.midi % 12) + 12) % 12;
          const pitchVal = el("span", "muted");
          pitchVal.style.gridColumn = "1 / -1";
          pitchVal.textContent = `Nốt: ${midiToName(note.midi, state.showFlat).replace(/\d+/g, "")}`;
          pitch.oninput = () => {
            const pc = parseInt(pitch.value, 10);
            const oct = Math.floor(note.midi / 12) - 1;
            note.midi = clamp((oct + 1) * 12 + pc, MIDI_MIN, MIDI_MAX);
            pitchVal.textContent = `Nốt: ${midiToName(note.midi, state.showFlat).replace(/\d+/g, "")}`;
            renderTracks();
            debouncedSave();
          };
          kv4.appendChild(pitch);
          body.appendChild(kv4);
          body.appendChild(pitchVal);

          const kv5 = el("div", "kv");
          kv5.appendChild(el("label", "", "Quãng tám"));
          const oct = document.createElement("input");
          oct.type = "range";
          oct.min = 1;
          oct.max = 7;
          oct.step = 1;
          oct.value = Math.floor(note.midi / 12) - 1;
          const octVal = el("span", "muted");
          octVal.style.gridColumn = "1 / -1";
          octVal.textContent = `Quãng tám: ${oct.value}`;
          oct.oninput = () => {
            const pc = ((note.midi % 12) + 12) % 12;
            const o = parseInt(oct.value, 10);
            note.midi = clamp((o + 1) * 12 + pc, MIDI_MIN, MIDI_MAX);
            octVal.textContent = `Quãng tám: ${o}`;
            renderTracks();
            debouncedSave();
          };
          kv5.appendChild(oct);
          body.appendChild(kv5);
          body.appendChild(octVal);
        } else {
          const kv6 = el("div", "kv");
          kv6.appendChild(el("label", "", "Âm trống"));
          const drum = document.createElement("select");
          DRUM_NAMES.forEach((d, idx) => {
            const op = new Option(d, String(idx));
            if ((note.drum ?? 0) === idx) op.selected = true;
            drum.add(op);
          });
          drum.onchange = () => {
            note.drum = parseInt(drum.value, 10);
            renderTracks();
            debouncedSave();
          };
          kv6.appendChild(drum);
          body.appendChild(kv6);
        }

        const actions = el("div", "actions");
        const del = el("button", "danger", "Xóa nốt");
        del.onclick = () => {
          const { track: tr, note: nt } = selectedObjects();
          if (!tr || !nt) return;
          tr.notes = tr.notes.filter(x => x.id !== nt.id);
          state.selected = null;
          renderTracks();
          renderNoteEditor();
          debouncedSave();
        };
        const clone = el("button", "secondary", "Nhân đôi");
        clone.onclick = () => {
          const { track: tr, note: nt } = selectedObjects();
          if (!tr || !nt) return;
          const copy = JSON.parse(JSON.stringify(nt));
          copy.id = state.noteSeq++;
          copy.step = clamp(copy.step + copy.length, 0, Math.max(0, state.totalSteps - copy.length));
          tr.notes.push(copy);
          selectNote(tr.id, copy.id);
          debouncedSave();
        };
        actions.append(clone, del);
        body.appendChild(actions);

        noteEditorBody.appendChild(body);
      }

      // ===== Grid interactions =====
      function attachGridInteraction(gridInner, track, isDrum, sw, rh) {
        let drag = null;

        gridInner.onpointerdown = (e) => {
          const noteEl = e.target.closest(".note-block");
          const rect = gridInner.getBoundingClientRect();
          const x = e.clientX - rect.left;
          const y = e.clientY - rect.top;

          if (noteEl) {
            const noteId = parseInt(noteEl.dataset.noteId, 10);
            const note = track.notes.find(n => n.id === noteId);
            if (!note) return;

            const isResize = e.target && e.target.dataset && e.target.dataset.role === "resize";
            selectNote(track.id, note.id);
            drag = {
              mode: isResize ? "resize" : "maybe-move",
              note,
              noteEl,
              startX: x,
              startY: y
            };
            e.preventDefault();
          } else {
            const step = Math.floor(x / sw);
            const row = Math.floor(y / rh);
            const maxRow = isDrum ? DRUM_NAMES.length - 1 : MEL_ROWS - 1;
            if (step < 0 || row < 0 || row > maxRow || step >= state.totalSteps) return;

            const note = isDrum
              ? { id: state.noteSeq++, step, length: 1, drum: row, velocity: 0.8 }
              : { id: state.noteSeq++, step, length: 1, midi: rowToMidi(row), velocity: 0.8 };

            track.notes.push(note);
            state.selected = { trackId: track.id, noteId: note.id };
            renderTracks();
            renderNoteEditor();
            debouncedSave();
          }

          const move = (ev) => {
            if (!drag) return;
            const cx = ev.clientX - rect.left;
            const cy = ev.clientY - rect.top;
            const dx = Math.abs(cx - drag.startX);
            const dy = Math.abs(cy - drag.startY);

            if (drag.mode === "maybe-move" && (dx > 6 || dy > 6)) drag.mode = "move";

            if (drag.mode === "resize") {
              const endStep = Math.floor(cx / sw);
              const newLen = Math.max(1, endStep - drag.note.step + 1);
              if (newLen !== drag.note.length) {
                drag.note.length = newLen;
                drag.noteEl.style.width = Math.max(1, newLen * sw - 2) + "px";
                debouncedSave();
              }
            } else if (drag.mode === "move") {
              const newStep = clamp(Math.floor(cx / sw), 0, Math.max(0, state.totalSteps - drag.note.length));
              const newRow = clamp(Math.floor(cy / rh), 0, isDrum ? DRUM_NAMES.length - 1 : MEL_ROWS - 1);
              if (isDrum) {
                if (drag.note.step !== newStep || drag.note.drum !== newRow) {
                  drag.note.step = newStep;
                  drag.note.drum = newRow;
                  drag.noteEl.style.left = (newStep * sw) + "px";
                  drag.noteEl.style.top = (newRow * rh) + "px";
                  drag.noteEl.querySelector(".tag").textContent = DRUM_NAMES[newRow] || "Drum";
                  debouncedSave();
                }
              } else {
                const newMidi = rowToMidi(newRow);
                if (drag.note.step !== newStep || drag.note.midi !== newMidi) {
                  drag.note.step = newStep;
                  drag.note.midi = newMidi;
                  drag.noteEl.style.left = (newStep * sw) + "px";
                  drag.noteEl.style.top = (newRow * rh) + "px";
                  drag.noteEl.querySelector(".tag").textContent = midiToName(newMidi, state.showFlat);
                  debouncedSave();
                }
              }
            }
          };

          const up = () => {
            document.removeEventListener("pointermove", move);
            document.removeEventListener("pointerup", up);
            drag = null;
          };

          document.addEventListener("pointermove", move);
          document.addEventListener("pointerup", up);
        };
      }

      function updatePlayheads(step = state.currentStep) {
        document.querySelectorAll(".grid-inner").forEach(grid => {
          let ph = grid.querySelector(".playhead");
          if (!ph) {
            ph = el("div", "playhead");
            grid.appendChild(ph);
          }
          ph.style.left = (step * stepWidth()) + "px";
        });
      }

      function removePlayheads() {
        document.querySelectorAll(".playhead").forEach(n => n.remove());
      }

      function spawnFx(text, x, y) {
        const n = el("div", "fx-note", text);
        n.style.left = x + "px";
        n.style.top = y + "px";
        fxLayer.appendChild(n);
        setTimeout(() => n.remove(), 950);
      }

      function toast(text) {
        let t = document.querySelector(".toast");
        if (!t) {
          t = el("div", "toast");
          document.body.appendChild(t);
        }
        t.textContent = text;
        clearTimeout(t._timer);
        t._timer = setTimeout(() => t.remove(), 1600);
      }

      // ===== Playback =====
      function triggerStep(step) {
        if (!state.song) return;
        const sw = stepWidth();

        state.song.tracks.forEach(track => {
          if (track.muted) return;
          const isDrum = INSTRUMENTS[track.instrument].type === "drum";
          track.notes.forEach(note => {
            if (note.step !== step) return;
            const when = audio.currentTime + 0.02;
            const dur = Math.max(0.05, note.length * (60 / state.bpm / 4));
            const vel = (note.velocity ?? 0.8) * (track.volume ?? 0.85);

            if (isDrum) {
              playDrum(DRUM_NAMES[note.drum ?? 0], vel, when);
            } else {
              const midi = clamp((note.midi ?? 60) + (track.octaveShift || 0) * 12, MIDI_MIN, MIDI_MAX);
              playMelodic(track.instrument, midi, dur, vel, when);
            }

            const gridInner = document.querySelector(`.track-card[data-track-id="${track.id}"] .grid-inner`);
            if (gridInner) {
              const rect = gridInner.getBoundingClientRect();
              const y = rect.top + 20 + (Math.random() * 26);
              const x = Math.min(window.innerWidth - 20, rect.left + step * sw + 18);
              spawnFx(isDrum ? "🥁" : "♪", x, y);
            }
          });
        });
      }

      function play() {
        if (!state.song || state.playing) return;
        audio.resume();
        state.playing = true;
        state.currentStep = 0;
        const interval = (60 / state.bpm / 4) * 1000;

        triggerStep(0);
        updatePlayheads(0);
        state.currentStep = 1;

        state.playTimer = setInterval(() => {
          if (!state.song) return;
          if (state.currentStep >= state.totalSteps) state.currentStep = 0;
          triggerStep(state.currentStep);
          updatePlayheads(state.currentStep);
          state.currentStep++;
        }, interval);
      }

      function stopPlayback() {
        state.playing = false;
        clearInterval(state.playTimer);
        state.playTimer = null;
        state.currentStep = 0;
        removePlayheads();
      }

      // ===== Presets =====
      function clearSongTracks() {
        if (!state.song) return;
        state.song.tracks = [];
        state.selected = null;
        renderTracks();
        renderNoteEditor();
      }

      function loadPreset(name) {
        if (!state.song) return;
        stopPlayback();
        state.song.tracks = [];
        state.noteSeq = 1;
        state.trackSeq = 1;
        state.totalSteps = 64;

        if (name === "twinkle") {
          const piano = makeTrack("piano", "Giai điệu");
          const bass = makeTrack("bass", "Bass");
          const drum = makeTrack("drums", "Trống");

          [
            ["C4",0,4],["C4",4,4],["G4",8,4],["G4",12,4],["A4",16,4],["A4",20,4],["G4",24,8],
            ["F4",32,4],["F4",36,4],["E4",40,4],["E4",44,4],["D4",48,4],["D4",52,4],["C4",56,8]
          ].forEach(([n,s,l]) => piano.notes.push({ id: state.noteSeq++, step:s, length:l, midi:noteToMidi(n), velocity:0.86 }));

          [["C2",0,16],["G2",16,16],["C2",32,16],["G2",48,16]].forEach(([n,s,l]) => bass.notes.push({ id: state.noteSeq++, step:s, length:l, midi:noteToMidi(n), velocity:0.68 }));

          for (let s = 0; s < 64; s += 8) drum.notes.push({ id: state.noteSeq++, step:s, length:1, drum:3, velocity:0.95 });
          for (let s = 4; s < 64; s += 8) drum.notes.push({ id: state.noteSeq++, step:s, length:1, drum:2, velocity:0.78 });
          for (let s = 0; s < 64; s += 2) drum.notes.push({ id: state.noteSeq++, step:s, length:1, drum:0, velocity:0.42 });

          state.song.tracks.push(piano, bass, drum);
        } else if (name === "ode") {
          const piano = makeTrack("piano", "Giai điệu");
          const bass = makeTrack("bass", "Bass");
          const melody = ["E4","E4","F4","G4","G4","F4","E4","D4","C4","C4","D4","E4","E4","D4","D4","C4"];
          melody.forEach((n,i) => piano.notes.push({ id: state.noteSeq++, step:i*4, length:4, midi:noteToMidi(n), velocity:0.86 }));
          [["C2",0,32],["G2",32,32]].forEach(([n,s,l]) => bass.notes.push({ id: state.noteSeq++, step:s, length:l, midi:noteToMidi(n), velocity:0.66 }));
          state.song.tracks.push(piano, bass);
        } else if (name === "beat") {
          const drum = makeTrack("drums", "Trống");
          for (let s = 0; s < 32; s += 8) drum.notes.push({ id: state.noteSeq++, step:s, length:1, drum:3, velocity:0.95 });
          for (let s = 4; s < 32; s += 8) drum.notes.push({ id: state.noteSeq++, step:s, length:1, drum:2, velocity:0.8 });
          for (let s = 0; s < 32; s += 2) drum.notes.push({ id: state.noteSeq++, step:s, length:1, drum:0, velocity:0.5 });
          state.song.tracks.push(drum);
          state.totalSteps = 32;
        }

        state.song.bpm = 110;
        state.song.totalSteps = state.totalSteps;
        state.bpm = state.song.bpm;
        state.selected = null;
        renderAll();
        debouncedSave();
      }

      // ===== Events =====
      bpmRange.oninput = () => {
        state.bpm = parseInt(bpmRange.value, 10);
        bpmValue.textContent = state.bpm;
        if (state.song) state.song.bpm = state.bpm;
        debouncedSave();
      };

      flatToggle.onchange = () => {
        state.showFlat = flatToggle.checked;
        renderTracks();
        renderNoteEditor();
      };

      btnPlay.onclick = play;
      btnStop.onclick = stopPlayback;

      btnNewSong.onclick = () => {
        stopPlayback();
        state.song = makeSong("Bản nhạc mới");
        state.song.tracks = [makeTrack("piano", "Piano 1")];
        state.song.bpm = 110;
        state.song.totalSteps = 64;
        state.bpm = 110;
        state.totalSteps = 64;
        bpmRange.value = 110;
        bpmValue.textContent = 110;
        state.selected = null;
        renderAll();
        debouncedSave();
      };

      btnDuplicateSong.onclick = duplicateSong;
      btnSaveSong.onclick = saveSong;
      btnDeleteSong.onclick = deleteCurrentSong;
      btnAddTrack.onclick = () => {
        if (!state.song) return;
        const inst = newTrackInstrument.value;
        const tr = makeTrack(inst, INSTRUMENTS[inst].label.replace(/^[^\s]+\s/, "") + " " + (state.song.tracks.length + 1));
        state.song.tracks.push(tr);
        renderTracks();
        debouncedSave();
      };
      btnAddMeasure.onclick = () => {
        if (!state.song) return;
        state.totalSteps += 16;
        state.song.totalSteps = state.totalSteps;
        renderTracks();
        debouncedSave();
      };
      btnLoadPreset.onclick = () => {
        if (!presetSelect.value) return;
        loadPreset(presetSelect.value);
      };
      btnClearAll.onclick = () => {
        if (!state.song) return;
        if (!confirm("Xóa toàn bộ nốt trong tất cả nhạc cụ?")) return;
        state.song.tracks.forEach(t => t.notes = []);
        state.selected = null;
        renderTracks();
        renderNoteEditor();
        debouncedSave();
      };
      btnRefreshList.onclick = renderSongList;
      btnOpenSong.onclick = () => openSelectedSong(songListSelect.value);
      songSelect.onchange = () => openSelectedSong(songSelect.value);
      songListSelect.onchange = () => openSelectedSong(songListSelect.value);

      songName.oninput = () => {
        if (!state.song) return;
        state.song.name = songName.value;
        debouncedSave();
      };

      $("#btnClearAll").onclick = () => {
        if (!state.song) return;
        if (!confirm("Xóa toàn bộ nốt?")) return;
        state.song.tracks.forEach(t => t.notes = []);
        state.selected = null;
        renderTracks();
        renderNoteEditor();
        debouncedSave();
      };

      window.addEventListener("resize", () => {
        renderTracks();
        if (state.playing) updatePlayheads();
      });

      // Shortcuts
      document.addEventListener("keydown", (e) => {
        if (!state.user || !state.song) return;
        if (e.key === " " && !e.repeat) {
          e.preventDefault();
          state.playing ? stopPlayback() : play();
        }
        if (e.key === "Escape") {
          state.selected = null;
          renderTracks();
          renderNoteEditor();
        }
        if ((e.key === "Delete" || e.key === "Backspace") && state.selected) {
          const { track, note } = selectedObjects();
          if (track && note) {
            track.notes = track.notes.filter(n => n.id !== note.id);
            state.selected = null;
            renderTracks();
            renderNoteEditor();
            debouncedSave();
          }
        }
      });

      // ===== Init =====
      function init() {
        const savedUser = getCurrentUserName();
        const u = savedUser && state.store.users[savedUser] ? state.store.users[savedUser] : null;

        if (u) {
          state.user = savedUser;
          currentUserLabel.textContent = savedUser;
          let songId = u.lastSongId || u.songOrder[0] || Object.keys(u.songs)[0];
          if (!songId || !u.songs[songId]) {
            const s = createDefaultSongForNewUser();
            u.songs[s.id] = s;
            u.songOrder = [s.id];
            u.lastSongId = s.id;
            saveStore();
            songId = s.id;
          }
          restoreSong(u.songs[songId]);
          fillSongSelector();
          openApp();
        } else {
          closeApp();
        }
      }

      init();
    })();
  </script>

</body>
</html>
