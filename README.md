<!doctype html>
<html lang="es">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Feliz Cumpleaños Vaquero 🎉</title>
  <style>
    :root{
      --bg:#0f172a;
      --card:#0b1220;
      --accent:#ffd166;
      --text:#e6eef8;
    }
    html,body{height:100%;margin:0;font-family:Inter,ui-sans-serif,system-ui,Segoe UI,Roboto,'Helvetica Neue',Arial}
    body{display:flex;align-items:center;justify-content:center;background:radial-gradient(circle at 20% 20%, #10243a 0%, var(--bg) 40%), linear-gradient(180deg,#071428 0%, #07121b 100%);color:var(--text)}
    .card{width:min(920px,94vw);background:linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));border-radius:18px;padding:36px;box-shadow:0 10px 30px rgba(2,6,23,0.7);display:flex;gap:28px;align-items:center}
    .left{flex:1}
    h1{margin:0;font-size:clamp(28px,4vw,44px);line-height:1.02;color:var(--accent);text-shadow:0 6px 20px rgba(255,209,102,0.06)}
    p{margin:12px 0 0;font-size:18px;color:rgba(230,238,248,0.92)}
    .btns{margin-top:20px;display:flex;gap:12px}
    .btn{background:linear-gradient(90deg,#ffd166,#ff9a66);padding:10px 16px;border-radius:12px;color:#08233a;font-weight:700;border:none;cursor:pointer;box-shadow:0 6px 18px rgba(255,150,60,0.12)}

    /* bear area */
    .bear-wrap{width:360px;height:360px;display:grid;place-items:center;position:relative}
    .bear-card{width:300px;height:300px;background:linear-gradient(180deg,#fff7ea,#ffe9c7);border-radius:28px;display:grid;place-items:center;position:relative;overflow:visible;transform:translateY(60px) scale(.9);opacity:0;animation:bearIn 900ms cubic-bezier(.2,.9,.22,1) forwards 400ms}

    @keyframes bearIn{
      to{transform:translateY(0) scale(1);opacity:1}
    }

    /* simple cute bear with hat using SVG scaling */
    .confetti{position:absolute;inset:0;pointer-events:none}
    .pulse{position:absolute;inset:0;border-radius:28px;box-shadow:0 40px 80px rgba(0,0,0,0.35);filter:blur(10px);opacity:.25}

    .caption{position:absolute;bottom:14px;left:50%;transform:translateX(-50%);font-size:14px;color:rgba(10,10,10,0.6)}

    /* small fireworks animation */
    .spark{position:absolute;width:6px;height:6px;border-radius:50%;opacity:0;transform:scale(.3)}
    .s1{left:12%;top:12%;animation:pop 1200ms infinite linear}
    .s2{left:85%;top:18%;animation:pop 1100ms .12s infinite linear}
    .s3{left:70%;top:78%;animation:pop 1150ms .22s infinite linear}
    .s4{left:32%;top:80%;animation:pop 1250ms .06s infinite linear}

    @keyframes pop{
      0%{opacity:0;transform:scale(.2)}
      10%{opacity:1}
      50%{transform:scale(1.8)}
      100%{opacity:0;transform:scale(.2)}
    }

    /* Responsive */
    @media (max-width:760px){.card{flex-direction:column;align-items:center}.bear-wrap{width:260px;height:260px}}
  </style>
</head>
<body>
  <div class="card" role="main">
    <div class="left">
      <h1>¡Feliz cumpleaños, vaquero! 🤠</h1>
      <p>Que el éxito y la felicidad colmen tu vida hoy y siempre. 🎉</p>
      <div class="btns">
        <button class="btn" id="revealBtn">Desplegar oso con sombrero</button>
        <button class="btn" id="downloadBtn">Descargar imagen</button>
      </div>
      <p style="margin-top:14px;font-size:13px;color:rgba(230,238,248,0.7)">Toca «Desplegar oso con sombrero» para ver la sorpresa.</p>
    </div>

    <div class="bear-wrap" aria-hidden="false">
      <div class="bear-card" id="bearCard" aria-hidden="true">
        <!-- Inline SVG bear with hat -->
        <svg id="bearSVG" width="220" height="220" viewBox="0 0 220 220" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="Oso con sombrero">
          <defs>
            <linearGradient id="fur" x1="0" x2="1"><stop offset="0" stop-color="#a56c3a"/><stop offset="1" stop-color="#8b4f2b"/></linearGradient>
            <linearGradient id="hatg" x1="0" x2="1"><stop offset="0" stop-color="#2b3a67"/><stop offset="1" stop-color="#1b263f"/></linearGradient>
          </defs>

          <!-- ears -->
          <g id="ears">
            <ellipse cx="60" cy="60" rx="26" ry="26" fill="url(#fur)" />
            <ellipse cx="160" cy="60" rx="26" ry="26" fill="url(#fur)" />
            <ellipse cx="60" cy="60" rx="12" ry="12" fill="#f2d3ab" transform="translate(0,4)" />
            <ellipse cx="160" cy="60" rx="12" ry="12" fill="#f2d3ab" transform="translate(0,4)" />
          </g>

          <!-- head -->
          <circle cx="110" cy="110" r="70" fill="url(#fur)" />
          <ellipse cx="110" cy="130" rx="42" ry="36" fill="#f2d3ab" />

          <!-- eyes & nose -->
          <g id="face">
            <circle cx="92" cy="100" r="8" fill="#28140b" />
            <circle cx="128" cy="100" r="8" fill="#28140b" />
            <ellipse cx="110" cy="124" rx="10" ry="8" fill="#28140b" />
          </g>

          <!-- hat (initially hidden, will drop in) -->
          <g id="hat" transform="translate(0,-60)" opacity="0">
            <ellipse cx="110" cy="56" rx="64" ry="18" fill="url(#hatg)" />
            <path d="M52 64c14-18 110-22 116 0 2 8-6 14-12 16-22 8-82 12-104-4-7-5-12-12-0-12z" fill="#163055"/>
            <rect x="78" y="38" width="64" height="22" rx="8" fill="#1f355a" transform="rotate(-6 110 49)"/>
          </g>

          <!-- body hat shadow -->
          <g id="body" transform="translate(0,60)">
            <ellipse cx="110" cy="118" rx="82" ry="40" fill="#fff" opacity="0.03" />
          </g>
        </svg>
        <div class="caption">¡Sorpresa! 🐻</div>
      </div>

      <!-- confetti and sparks -->
      <div class="confetti" id="confetti"></div>
      <div class="pulse"></div>
      <div class="spark s1"></div>
      <div class="spark s2"></div>
      <div class="spark s3"></div>
      <div class="spark s4"></div>

    </div>
  </div>

  <script>
    const revealBtn = document.getElementById('revealBtn');
    const bearCard = document.getElementById('bearCard');
    const hat = document.getElementById('hat');
    const confettiArea = document.getElementById('confetti');
    const downloadBtn = document.getElementById('downloadBtn');

    function makeConfetti(){
      confettiArea.innerHTML = '';
      const colors = ['#ffd166','#06d6a0','#118ab2','#ef476f','#ff9a66'];
      for(let i=0;i<30;i++){
        const el = document.createElement('div');
        el.style.position='absolute';
        el.style.left = Math.random()*100 + '%';
        el.style.top = Math.random()*20 + '%';
        el.style.width = (6+Math.random()*8)+'px';
        el.style.height = (10+Math.random()*12)+'px';
        el.style.background = colors[Math.floor(Math.random()*colors.length)];
        el.style.transform = 'rotate('+Math.random()*360+'deg)';
        el.style.opacity = '0';
        el.style.borderRadius='2px';
        el.style.pointerEvents='none';
        confettiArea.appendChild(el);

        // animate
        const fall = el.animate([
          {transform: 'translateY(0) rotate(0deg)', opacity:0},
          {transform: 'translateY(' + (160+Math.random()*160) + 'px) rotate(' + (360+Math.random()*720) + 'deg)', opacity:1},
          {transform: 'translateY(' + (320+Math.random()*240) + 'px) rotate(' + (720+Math.random()*1080) + 'deg)', opacity:0}
        ],{duration:1600+Math.random()*1200,delay:Math.random()*200,iterations:1,easing:'cubic-bezier(.2,.7,.2,1)'});
        fall.onfinish = ()=> el.remove();
      }
    }

    function dropHat(){
      hat.animate([{transform:'translateY(-60px)'},{transform:'translateY(0)'}],{duration:700,easing:'cubic-bezier(.2,.8,.2,1)'});
      hat.animate([{opacity:0},{opacity:1}],{duration:400, easing:'linear', fill:'forwards'});
      // also add a little tilt
      const rect = hat.querySelector('rect');
      if(rect) rect.animate([{transform:'rotate(-6deg)'},{transform:'rotate(6deg)'},{transform:'rotate(0deg)'}],{duration:900, easing:'ease-out'});
    }

    revealBtn.addEventListener('click', ()=>{
      // reveal card
      bearCard.setAttribute('aria-hidden','false');
      // show hat
      hat.setAttribute('opacity','1');
      dropHat();
      makeConfetti();
      // small bounce for the bear
      bearCard.animate([
        {transform:'translateY(0) scale(1)'},
        {transform:'translateY(-12px) scale(1.03)'},
        {transform:'translateY(0) scale(1)'}
      ],{duration:700,easing:'cubic-bezier(.2,.9,.22,1)'});
    });

    // Download the bear as PNG (simple approach: draw SVG to canvas)
    downloadBtn.addEventListener('click', async ()=>{
      const svg = document.getElementById('bearSVG');
      const svgData = new XMLSerializer().serializeToString(svg);
      const blob = new Blob([svgData], {type: 'image/svg+xml;charset=utf-8'});
      const url = URL.createObjectURL(blob);
      const img = new Image();
      img.onload = ()=>{
        const canvas = document.createElement('canvas');
        canvas.width = img.width;
        canvas.height = img.height;
        const ctx = canvas.getContext('2d');
        ctx.fillStyle = '#fff2e6';
        ctx.fillRect(0,0,canvas.width,canvas.height);
        ctx.drawImage(img,0,0);
        canvas.toBlob((b)=>{
          const a = document.createElement('a');
          a.href = URL.createObjectURL(b);
          a.download = 'oso_con_sombrero.png';
          a.click();
          URL.revokeObjectURL(url);
        });
      };
      img.src = url;
    });

    // Auto reveal on load for small surprise on first view
    window.addEventListener('load', ()=>{
      setTimeout(()=>{
        // only auto reveal on wide screens
        if(window.innerWidth>720) revealBtn.click();
      },700);
    });
  </script>
</body>
</html>
