
<html lang="kk">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Дамир &amp; Айдайдын — Үйлену тойы</title>
<link rel="preconnect" href="https://fonts.cdnfonts.com">
<link href="https://fonts.cdnfonts.com/css/bickham-script-pro" rel="stylesheet">
<style>

  :root{
    --maroon:#7c1f2d;
    --maroon-dark:#4a1119;
    --cream:#faf5ec;
    --cream-2:#f2e9db;
    --gold:#c9a45f;
    --charcoal:#2b241f;
    --navy:#1f2a3f;
  }

  *{ margin:0; padding:0; box-sizing:border-box; }

  html{ scroll-behavior:smooth; }

  body{
    font-family:'Book Antiqua','Palatino Linotype', Georgia, 'Times New Roman', serif;
    color:var(--charcoal);
    background:var(--cream);
    overflow-x:hidden;
  }

  .scroller{
    scroll-snap-type: y proximity;
  }

  .section{
    min-height:100vh;
    width:100%;
    scroll-snap-align:start;
    display:flex;
    flex-direction:column;
    align-items:center;
    justify-content:center;
    position:relative;
    padding:8vh 6vw;
    text-align:center;
  }

  .script{
    font-family:'Bickham Script Pro','Brush Script MT', cursive;
    font-weight:400;
    line-height:1;
  }

  /* ---------- reveal-on-scroll ---------- */
  .reveal{
    opacity:0;
    transform:translateY(22px);
    transition:opacity 0.9s ease, transform 0.9s ease;
  }
  .reveal.is-visible{
    opacity:1;
    transform:translateY(0);
  }

  /* ---------- torn paper edge ---------- */
  .torn-edge{
    position:absolute;
    left:0; right:0; bottom:-1px;
    width:100%;
    height:44px;
    z-index:2;
    line-height:0;
  }
  .torn-edge svg{ width:100%; height:100%; display:block; }

  /* ---------- corner ornaments ---------- */
  .corner-orn{
    position:absolute;
    width:54px; height:54px;
    z-index:1;
    opacity:0.85;
  }
  .corner-orn.tl{ top:5.5vh; left:5.5vw; }
  .corner-orn.tr{ top:5.5vh; right:5.5vw; transform:scaleX(-1); }

  /* ---------- flourish divider ---------- */
  .flourish{
    display:flex;
    align-items:center;
    justify-content:center;
    gap:0.8rem;
    margin:2rem auto;
    color:var(--gold);
  }
  .flourish svg{ flex-shrink:0; }
  .flourish .fl-line{
    height:1px;
    width:64px;
    background:linear-gradient(90deg, transparent, var(--gold));
  }
  .flourish .fl-line.right{ background:linear-gradient(90deg, var(--gold), transparent); }

  /* ---------- line-art floral accent ---------- */
  .floral-accent{
    position:absolute;
    width:150px;
    opacity:0.9;
    z-index:0;
  }

  /* ---------- floating music control ---------- */
  #musicToggle{
    position:fixed;
    right:1.4rem;
    bottom:1.4rem;
    z-index:50;
    width:58px; height:58px;
    border-radius:50%;
    border:1.4px solid var(--gold);
    background:rgba(74,17,25,0.75);
    backdrop-filter:blur(6px);
    display:flex;
    align-items:center;
    justify-content:center;
    cursor:pointer;
    box-shadow:0 8px 24px rgba(0,0,0,0.25);
    transition:transform .2s ease, background .2s ease;
  }
  #musicToggle:hover{ transform:scale(1.06); }
  #musicToggle svg{ width:20px; height:20px; }
  #musicToggle .ring{
    position:absolute;
    inset:-6px;
    border-radius:50%;
    border:1px solid var(--gold);
    opacity:0.5;
    animation:spin 9s linear infinite;
  }
  #musicToggle.paused .ring{ animation-play-state:paused; }
  @keyframes spin{ to{ transform:rotate(360deg); } }
  .icon-pause{ display:block; }
  .icon-play{ display:none; }
  #musicToggle.paused .icon-pause{ display:none; }
  #musicToggle.paused .icon-play{ display:block; }

  @media (prefers-reduced-motion: reduce){
    #musicToggle .ring{ animation:none; }
  }

  /* ---------- watermark monogram ---------- */
  .monogram-bg{
    position:absolute;
    inset:0;
    display:flex;
    align-items:center;
    justify-content:center;
    pointer-events:none;
    opacity:0.06;
    font-size:min(60vw,60vh);
    color:var(--cream);
    font-family:'Bickham Script Pro','Brush Script MT', cursive;
    z-index:0;
    user-select:none;
  }

  /* ---------- SECTION 1 : HERO ---------- */
  #hero{
    background: radial-gradient(120% 100% at 50% 0%, var(--maroon) 0%, var(--maroon-dark) 75%);
    color:var(--cream);
  }
  #hero .eyebrow{
    letter-spacing:0.35em;
    font-size:0.72rem;
    text-transform:uppercase;
    color:var(--gold);
    margin-bottom:1.6rem;
    z-index:1;
  }
  #hero .names{
    font-size:clamp(3.5rem, 12vw, 8rem);
    color:#fff;
    z-index:1;
    text-shadow:0 2px 24px rgba(0,0,0,0.25);
  }
  #hero .amp{
    display:block;
    font-size:0.5em;
    color:var(--gold);
    margin:0.1em 0;
  }
  #hero .subtitle{
    margin-top:1.8rem;
    font-size:1rem;
    letter-spacing:0.08em;
    z-index:1;
    color:var(--cream-2);
  }
  #hero .date{
    margin-top:2.2rem;
    font-size:1.15rem;
    letter-spacing:0.15em;
    border-top:1px solid var(--gold);
    border-bottom:1px solid var(--gold);
    padding:0.6rem 1.6rem;
    z-index:1;
  }
  .scroll-cue{
    position:absolute;
    bottom:3.2rem;
    left:50%;
    transform:translateX(-50%);
    z-index:1;
    display:flex;
    flex-direction:column;
    align-items:center;
    gap:0.4rem;
    color:var(--gold);
    animation:bob 2.4s ease-in-out infinite;
  }
  .scroll-cue span{ font-size:0.65rem; letter-spacing:0.25em; text-transform:uppercase; }
  @keyframes bob{
    0%,100%{ transform:translate(-50%,0); }
    50%{ transform:translate(-50%,10px); }
  }

  /* ---------- SECTION 2 : INVITATION ---------- */
  #invite{
    background:var(--cream);
  }
  .heading-script{
    font-family:'Bickham Script Pro','Brush Script MT', cursive;
    color:var(--maroon);
    font-size:clamp(2.4rem,7vw,4rem);
    margin-bottom:1.6rem;
  }
  .addressees{
    max-width:640px;
    font-size:1.05rem;
    line-height:2;
    color:var(--charcoal);
    margin-bottom:2.4rem;
  }
  .invite-body{
    max-width:600px;
    font-size:1.15rem;
    line-height:1.95;
    color:var(--maroon-dark);
  }
  .divider{
    width:70px;
    height:2px;
    background:var(--gold);
    margin:2.2rem auto;
    position:relative;
  }
  .divider::before{
    content:"♥";
    position:absolute;
    top:50%; left:50%;
    transform:translate(-50%,-50%);
    background:var(--cream);
    padding:0 10px;
    color:var(--maroon);
    font-size:0.9rem;
  }

  /* ---------- SECTION 3 : TIMELINE ---------- */
  #timeline{
    background: linear-gradient(180deg, var(--maroon-dark), var(--maroon));
    color:var(--cream);
    padding-top:10vh;
    padding-bottom:10vh;
  }
  #timeline .heading-script{ color:var(--gold); }
  .timeline-wrap{
    position:relative;
    max-width:640px;
    width:100%;
    margin-top:2rem;
  }
  .timeline-svg{
    position:absolute;
    top:0; left:0;
    width:100%; height:100%;
    z-index:0;
  }
  .t-item{
    position:relative;
    z-index:1;
    display:flex;
    align-items:baseline;
    gap:1.4rem;
    margin:3.4rem 0;
    text-align:left;
  }
  .t-item:nth-child(even){ flex-direction:row-reverse; text-align:right; }
  .t-time{
    font-size:1.5rem;
    color:var(--gold);
    letter-spacing:0.05em;
    min-width:100px;
    flex-shrink:0;
  }
  .t-item:nth-child(even) .t-time{ text-align:right; }
  .t-text .t-title{
    font-family:'Bickham Script Pro','Brush Script MT', cursive;
    font-size:1.7rem;
    color:#fff;
    display:block;
    margin-bottom:0.2rem;
  }
  .t-text .t-desc{
    font-size:0.92rem;
    color:var(--cream-2);
    opacity:0.85;
  }

  /* ---------- SECTION 4 : LOCATION ---------- */
  #location{ background:var(--cream-2); }
  .map-card{
    max-width:480px;
    background:#fff;
    border:1px solid rgba(124,31,45,0.15);
    border-radius:4px;
    padding:2.6rem 2.4rem;
    box-shadow:0 20px 40px -20px rgba(74,17,25,0.25);
  }
  .map-card .venue{
    font-family:'Bickham Script Pro','Brush Script MT', cursive;
    font-size:2.4rem;
    color:var(--maroon);
    margin-bottom:0.4rem;
  }
  .map-card .addr{
    font-size:1.05rem;
    line-height:1.7;
    margin-bottom:1.6rem;
  }
  .map-link{
    display:inline-flex;
    align-items:center;
    gap:0.5rem;
    color:#fff;
    background:var(--maroon);
    text-decoration:none;
    padding:0.85rem 1.8rem;
    border-radius:2px;
    font-size:0.85rem;
    letter-spacing:0.08em;
    text-transform:uppercase;
    transition:background 0.25s ease;
  }
  .map-link:hover{ background:var(--maroon-dark); }

  /* ---------- SECTION 5 : HOSTS ---------- */
  #hosts{
    background: radial-gradient(120% 100% at 50% 100%, var(--maroon) 0%, var(--maroon-dark) 80%);
    color:var(--cream);
  }
  #hosts .quote{
    font-size:clamp(1.6rem,4.2vw,2.4rem);
    max-width:640px;
    line-height:1.6;
    margin-bottom:2.4rem;
    color:var(--cream-2);
  }
  #hosts .hosts-names{
    font-family:'Bickham Script Pro','Brush Script MT', cursive;
    font-size:clamp(2.6rem,8vw,4.2rem);
    color:var(--gold);
  }
  #hosts .hosts-label{
    font-size:0.7rem;
    letter-spacing:0.3em;
    text-transform:uppercase;
    color:var(--cream-2);
    opacity:0.7;
    margin-top:0.6rem;
  }

  /* ---------- SECTION 6 : RSVP ---------- */
  #rsvp{ background:var(--cream); }
  .rsvp-card{
    width:100%;
    max-width:460px;
    background:#fff;
    border-radius:4px;
    padding:3rem 2.2rem;
    box-shadow:0 30px 60px -30px rgba(74,17,25,0.3);
    border:1px solid rgba(124,31,45,0.12);
  }
  .rsvp-card p.lead{
    font-size:0.95rem;
    color:#6b6259;
    margin-bottom:1.8rem;
  }
  .field{
    width:100%;
    margin-bottom:1.4rem;
  }
  .field input[type="text"]{
    width:100%;
    padding:0.9rem 1.1rem;
    border:1px solid #d9cdbd;
    border-radius:30px;
    font-family:inherit;
    font-size:1rem;
    outline:none;
    transition:border-color .2s ease;
  }
  .field input[type="text"]:focus{ border-color:var(--maroon); }
  .options{
    text-align:left;
    margin-bottom:1.8rem;
    display:flex;
    flex-direction:column;
    gap:0.9rem;
  }
  .option{
    display:flex;
    align-items:center;
    gap:0.7rem;
    font-size:1rem;
    cursor:pointer;
  }
  .option input{
    appearance:none;
    -webkit-appearance:none;
    width:19px; height:19px;
    border:1.5px solid var(--charcoal);
    border-radius:3px;
    flex-shrink:0;
    position:relative;
    cursor:pointer;
  }
  .option input:checked{
    background:var(--maroon);
    border-color:var(--maroon);
  }
  .option input:checked::after{
    content:"";
    position:absolute;
    left:5.5px; top:1.5px;
    width:5px; height:10px;
    border:solid white;
    border-width:0 2px 2px 0;
    transform:rotate(45deg);
  }
  .submit-btn{
    width:100%;
    padding:1rem;
    background:var(--maroon);
    color:#fff;
    border:none;
    border-radius:30px;
    font-family:inherit;
    font-size:0.95rem;
    letter-spacing:0.06em;
    text-transform:uppercase;
    cursor:pointer;
    transition:background .2s ease;
  }
  .submit-btn:hover{ background:var(--maroon-dark); }
  .thanks{
    display:none;
    text-align:center;
  }
  .thanks .heading-script{ margin-bottom:1rem; }
  .thanks p{ font-size:1.05rem; color:var(--charcoal); }
  .error-msg{
    display:none;
    color:var(--maroon);
    font-size:0.85rem;
    margin-top:-0.8rem;
    margin-bottom:1.2rem;
  }

  footer{
    text-align:center;
    padding:2.4rem 1rem;
    background:var(--maroon-dark);
    color:var(--cream-2);
    font-size:0.8rem;
    letter-spacing:0.1em;
  }
  footer .script{ font-size:1.4rem; color:var(--gold); display:block; margin-bottom:0.4rem; }

  @media (max-width:600px){
    .t-item, .t-item:nth-child(even){
      flex-direction:column;
      align-items:flex-start;
      text-align:left;
      gap:0.3rem;
    }
    .t-item:nth-child(even) .t-time{ text-align:left; }
    .t-time{ font-size:1.2rem; }
  }

  @media (prefers-reduced-motion: reduce){
    .scroll-cue{ animation:none; }
    html{ scroll-behavior:auto; }
  }
</style>
</head>
<body>

<div class="scroller">

  <!-- 1. HERO -->
  <section class="section" id="hero">
    <div class="monogram-bg">Д&amp;А</div>

    <svg class="corner-orn tl" viewBox="0 0 60 60" fill="none">
      <path d="M2 40 V10 Q2 2 10 2 H40" stroke="#c9a45f" stroke-width="1.2"/>
      <circle cx="10" cy="2" r="2" fill="#c9a45f"/>
    </svg>
    <svg class="corner-orn tr" viewBox="0 0 60 60" fill="none">
      <path d="M2 40 V10 Q2 2 10 2 H40" stroke="#c9a45f" stroke-width="1.2"/>
      <circle cx="10" cy="2" r="2" fill="#c9a45f"/>
    </svg>

    <div class="eyebrow reveal">Үйлену тойы</div>
    <h1 class="names reveal">
      Дамир
      <span class="amp script">&amp;</span>
      Айдайдын
    </h1>
    <p class="subtitle reveal">Сіздерді салтанатты ақ дастарханымыздың қадірлі қонағы болуға шақырамыз</p>
    <div class="date reveal">21 ТАМЫЗ 2026 · ЖҰМА</div>
    <div class="scroll-cue">
      <span>Төмен қараңыз</span>
      <svg width="16" height="24" viewBox="0 0 16 24" fill="none"><path d="M8 0V22M8 22L1 15M8 22L15 15" stroke="currentColor" stroke-width="1.4"/></svg>
    </div>

    <div class="torn-edge">
      <svg viewBox="0 0 1200 44" preserveAspectRatio="none">
        <path d="M0,44 L0,20 L40,32 L80,8 L125,26 L170,4 L215,30 L260,12 L305,34 L350,6 L395,28 L440,14 L485,36 L530,10 L575,30 L620,4 L665,26 L710,14 L755,34 L800,8 L845,30 L890,6 L935,28 L980,12 L1025,32 L1070,4 L1115,26 L1160,14 L1200,30 L1200,44 Z" fill="#faf5ec"/>
      </svg>
    </div>
  </section>

  <!-- 2. INVITATION -->
  <section class="section" id="invite">
    <svg class="floral-accent" style="top:6vh; right:4vw;" viewBox="0 0 160 160" fill="none">
      <g stroke="#c9a45f" stroke-width="1.1" opacity="0.8">
        <path d="M80 80 C60 60 55 30 80 15 C105 30 100 60 80 80Z"/>
        <path d="M80 80 C100 60 130 55 145 80 C130 105 100 100 80 80Z"/>
        <path d="M80 80 C100 100 105 130 80 145 C55 130 60 100 80 80Z"/>
        <path d="M80 80 C60 100 30 105 15 80 C30 55 60 60 80 80Z"/>
        <circle cx="80" cy="80" r="7"/>
      </g>
    </svg>

    <p class="heading-script reveal">Құрметті қонақтар</p>
    <p class="addressees reveal">
      Құрметті ағайын-туыс, бауырлар, құда-жекжат,<br>
      нағашы-жиен, бөлелер, құрбы-құрдас,<br>
      дос-жарандар, әріптестер, көршілер!
    </p>
    <div class="flourish reveal">
      <span class="fl-line"></span>
      <svg width="22" height="14" viewBox="0 0 22 14" fill="none"><path d="M11 1 L11 13 M1 7 Q11 1 21 7 Q11 13 1 7Z" stroke="currentColor" stroke-width="1"/></svg>
      <span class="fl-line right"></span>
    </div>
    <p class="invite-body reveal">
      Сіздерді балаларымыз <strong>Дамир</strong> мен <strong>Айдайдын</strong>
      үйлену тойына арналған салтанатты ақ дастарханымыздың
      қадірлі қонағы болуға шақырамыз!
    </p>
  </section>

  <!-- 3. TIMELINE -->
  <section class="section" id="timeline">
    <p class="heading-script reveal">Той салтанаты</p>
    <div class="timeline-wrap">
      <svg class="timeline-svg" viewBox="0 0 600 900" preserveAspectRatio="none">
        <path d="M550,20 C 250,120 650,260 300,340 C -20,420 620,540 320,640 C 80,720 560,800 300,880"
              stroke="#c9a45f" stroke-width="1.4" fill="none" opacity="0.55"/>
      </svg>
      <div class="t-item reveal">
        <div class="t-time">17:30</div>
        <div class="t-text">
          <span class="t-title">Қонақтар жиналуы</span>
          <span class="t-desc">Күтуге келіңіздер, уақытында бастаймыз</span>
        </div>
      </div>
      <div class="t-item reveal">
        <div class="t-time">17:30&ndash;18:00</div>
        <div class="t-text">
          <span class="t-title">Welcome-зона</span>
          <span class="t-desc">Шай-кофе мен жеңіл дәм дайын тұрады</span>
        </div>
      </div>
      <div class="t-item reveal">
        <div class="t-time">18:00</div>
        <div class="t-text">
          <span class="t-title">Беташар</span>
          <span class="t-desc">Платоктарыңызды дайындап алыңыздар</span>
        </div>
      </div>
      <div class="t-item reveal">
        <div class="t-time">19:00</div>
        <div class="t-text">
          <span class="t-title">Той басталуы</span>
          <span class="t-desc">Дәмді ас пен қызу билер кешіне қош келдіңіздер</span>
        </div>
      </div>
    </div>
  </section>

  <!-- 4. LOCATION -->
  <section class="section" id="location">
    <p class="heading-script reveal">Мекен-жайымыз</p>
    <div class="map-card reveal">
      <p class="venue">Aisultan</p>
      <p class="addr">Алматы қаласы,<br>"Aisultan" мейрамханасы</p>
      <a class="map-link" href="https://2gis.kz/almaty/geo/70000001041712972/77.049459,43.305557" target="_blank" rel="noopener">
        Картадан көру
        <svg width="14" height="14" viewBox="0 0 24 24" fill="none"><path d="M12 2C8 2 5 5.1 5 9c0 5.3 7 13 7 13s7-7.7 7-13c0-3.9-3-7-7-7z" stroke="currentColor" stroke-width="1.6"/><circle cx="12" cy="9" r="2.3" stroke="currentColor" stroke-width="1.6"/></svg>
      </a>
    </div>
  </section>

  <!-- 5. HOSTS -->
  <section class="section" id="hosts">
    <p class="quote reveal">Куанышымызға ортақ болыңыздар!</p>
    <div class="flourish reveal">
      <span class="fl-line"></span>
      <svg width="22" height="14" viewBox="0 0 22 14" fill="none"><path d="M11 1 L11 13 M1 7 Q11 1 21 7 Q11 13 1 7Z" stroke="currentColor" stroke-width="1"/></svg>
      <span class="fl-line right"></span>
    </div>
    <p class="hosts-names reveal">Серік &middot; Гүлмира</p>
    <p class="hosts-label reveal">Той иелері</p>
  </section>

  <!-- 6. RSVP -->
  <section class="section" id="rsvp">
    <p class="heading-script reveal">Тойға келесіз бе?</p>
    <div class="rsvp-card reveal">
      <div id="formView">
        <p class="lead">Қатысу-қатыспауыңызды хабарласаңыз, біз үшін өте маңызды.</p>
        <form id="rsvpForm">
          <div class="field">
            <input type="text" id="guestName" name="name" placeholder="Есіміңіз" required>
          </div>
          <div class="options">
            <label class="option">
              <input type="radio" name="answer" value="Әрине келемін" required>
              Әрине келемін
            </label>
            <label class="option">
              <input type="radio" name="answer" value="Жұбайыммен барамын">
              Жұбайыммен барамын
            </label>
            <label class="option">
              <input type="radio" name="answer" value="Өкінішке орай, келе алмаймын">
              Өкінішке орай, келе алмаймын
            </label>
          </div>
          <p class="error-msg" id="errorMsg">Есіміңізді жазып, жауабыңызды таңдаңыз.</p>
          <button type="submit" class="submit-btn">Жауапты жіберемін</button>
        </form>
      </div>
      <div class="thanks" id="thanksView">
        <p class="heading-script">Рахмет!</p>
        <p>Жауабыңыз қабылданды. Тойда көріскенше!</p>
      </div>
    </div>
  </section>

  <footer>
    <span class="script">Дамир &amp; Айдайдын</span>
    21 тамыз 2026 &middot; Алматы
  </footer>

</div>

<!-- Фондык музыка: "Махаббатым" әнінің припев бөлігі (шамамен 1 минут), файлдың ішіне тікелей ендірілген -->
<audio id="Baqzhvn_Махаббатым_Qazaq_Edition_Радио_Hits_Beats" preload="auto" loop>
  <source src="audio/Baqzhvn_Махаббатым_Qazaq_Edition_Радио_Hits_Beats.mp3" type="audio/mpeg">
</audio>


<button id="musicToggle" aria-label="Музыканы қосу/тоқтату">
  <span class="ring"></span>
  <svg class="icon-pause" viewBox="0 0 24 24" fill="none"><rect x="6" y="5" width="4" height="14" fill="#f2e9db"/><rect x="14" y="5" width="4" height="14" fill="#f2e9db"/></svg>
  <svg class="icon-play" viewBox="0 0 24 24" fill="none"><path d="M7 4 L19 12 L7 20 Z" fill="#f2e9db"/></svg>
</button>

<script>
  // ---- reveal on scroll ----
  const revealEls = document.querySelectorAll('.reveal');
  const io = new IntersectionObserver((entries)=>{
    entries.forEach(en=>{
      if(en.isIntersecting){
        en.target.classList.add('is-visible');
        io.unobserve(en.target);
      }
    });
  }, { threshold:0.2 });
  revealEls.forEach(el=>io.observe(el));

  // ---- background music (chorus clip, ~60s, loops automatically) ----
  const music = document.getElementById('bgMusic');
  const musicBtn = document.getElementById('musicToggle');
  let userPaused = false;

  function tryPlay(){
    music.play().then(()=>{
      musicBtn.classList.remove('paused');
    }).catch(()=>{
      musicBtn.classList.add('paused');
    });
  }

  // Attempt autoplay on load; most mobile browsers will block this
  // until the guest taps the page, which the listener below handles.
  window.addEventListener('load', tryPlay);
  document.body.addEventListener('click', function firstTap(){
    if(!userPaused) tryPlay();
    document.body.removeEventListener('click', firstTap);
  }, { once:true });

  musicBtn.addEventListener('click', ()=>{
    if(music.paused){
      userPaused = false;
      tryPlay();
    } else {
      music.pause();
      userPaused = true;
      musicBtn.classList.add('paused');
    }
  });

  const form = document.getElementById('rsvpForm');
  const formView = document.getElementById('formView');
  const thanksView = document.getElementById('thanksView');
  const errorMsg = document.getElementById('errorMsg');

  // NOTE: to actually receive these RSVP submissions by email, replace
  // "YOUR_EMAIL@example.com" below with the couple's real email address.
  // The first submission to a new address requires a one-time confirmation
  // click from that inbox (FormSubmit.co sends it automatically).
  const FORM_ENDPOINT = "https://formsubmit.co/ajax/YOUR_EMAIL@example.com";

  form.addEventListener('submit', function(e){
    e.preventDefault();
    const name = document.getElementById('guestName').value.trim();
    const answer = form.querySelector('input[name="answer"]:checked');

    if(!name || !answer){
      errorMsg.style.display = 'block';
      return;
    }
    errorMsg.style.display = 'none';

    fetch(FORM_ENDPOINT, {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({
        Есім: name,
        Жауап: answer.value,
        _subject: "Той жауабы: " + name
      })
    }).catch(()=>{ /* even if the network call fails, still thank the guest locally */ });

    formView.style.display = 'none';
    thanksView.style.display = 'block';
  });
</script>

</body>
</html>
