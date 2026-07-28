<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 800 200" width="100%" height="auto">
  <defs>
    <!-- Efek Cahaya (Glow) untuk Petir -->
    <filter id="cahaya-petir" x="-50%" y="-50%" width="200%" height="200%">
      <feGaussianBlur stdDeviation="4" result="blur" />
      <feMerge>
        <feMergeNode in="blur" />
        <feMergeNode in="SourceGraphic" />
      </feMerge>
    </filter>

    <style>
      /* === ANIMASI AWAN BADAI (BERGERAK LAMBAT) === */
      .awan {
        animation: melayang 12s ease-in-out infinite alternate;
      }
      .awan-bawah {
        animation: melayang 15s ease-in-out infinite alternate-reverse;
      }
      @keyframes melayang {
        0% { transform: translateX(0px); }
        100% { transform: translateX(-40px); }
      }

      /* === ANIMASI HUJAN (GARIS TURUN) === */
      .hujan {
        stroke: #7a9cce;
        stroke-width: 1.5;
        stroke-linecap: round;
        animation: jatuh 0.6s linear infinite;
      }
      @keyframes jatuh {
        0% { transform: translateY(-30px); opacity: 0; }
        10% { opacity: 0.7; }
        90% { opacity: 0.7; }
        100% { transform: translateY(200px); opacity: 0; }
      }

      /* === ANIMASI PETIR (KILAT BERKEDIP) === */
      .petir-utama {
        stroke: #fff7a8;
        stroke-width: 3;
        fill: none;
        filter: url(#cahaya-petir);
        animation: kilat 3.5s infinite;
      }
      .petir-cabang {
        stroke: #ffe066;
        stroke-width: 1.5;
        fill: none;
        filter: url(#cahaya-petir);
        animation: kilat 3.5s infinite 0.1s; /* delay sedikit agar efek lebih alami */
      }
      @keyframes kilat {
        0%, 83%, 85%, 87%, 89%, 91%, 93%, 95%, 100% { opacity: 0; }
        84% { opacity: 1; }
        86% { opacity: 0.3; }
        88% { opacity: 1; }
        90% { opacity: 0; }
        92% { opacity: 0.8; }
        94% { opacity: 0; }
      }

      /* === ANIMASI KEDIPAN CAHAYA LATAR (Efek NUTUP) === */
      .latar-belakang {
        animation: redup 3.5s infinite;
      }
      @keyframes redup {
        0%, 83%, 85%, 87%, 89%, 91%, 93%, 95%, 100% { fill: #0b0e1a; }
        84% { fill: #1c2640; }
        88% { fill: #1c2640; }
        92% { fill: #1c2640; }
      }
    </style>
  </defs>

  <!-- BACKGROUND LANGIT MALAM -->
  <rect class="latar-belakang" width="800" height="200" fill="#0b0e1a" />

  <!-- AWAN BADAI (LAPISAN ATAS) -->
  <g class="awan">
    <ellipse cx="200" cy="50" rx="100" ry="40" fill="#1a1f2e" />
    <ellipse cx="320" cy="40" rx="80" ry="35" fill="#151a28" />
    <ellipse cx="480" cy="55" rx="90" ry="38" fill="#1a1f2e" />
    <ellipse cx="600" cy="45" rx="70" ry="30" fill="#131826" />
  </g>

  <!-- AWAN BADAI (LAPISAN BAWAH - LEBIH GELAP) -->
  <g class="awan-bawah">
    <ellipse cx="150" cy="70" rx="110" ry="30" fill="#0f131f" />
    <ellipse cx="400" cy="75" rx="130" ry="35" fill="#0d111c" />
    <ellipse cx="650" cy="70" rx="100" ry="28" fill="#0f131f" />
  </g>

  <!-- EFEK HUJAN (TETESAN) -->
  <g>
    <!-- Baris 1 -->
    <line class="hujan" x1="50" y1="20" x2="40" y2="60" style="animation-delay: 0s;" />
    <line class="hujan" x1="150" y1="0" x2="140" y2="40" style="animation-delay: 0.15s;" />
    <line class="hujan" x1="250" y1="30" x2="240" y2="70" style="animation-delay: 0.3s;" />
    <line class="hujan" x1="350" y1="10" x2="340" y2="50" style="animation-delay: 0.45s;" />
    <line class="hujan" x1="450" y1="40" x2="440" y2="80" style="animation-delay: 0.1s;" />
    <line class="hujan" x1="550" y1="5" x2="540" y2="45" style="animation-delay: 0.25s;" />
    <line class="hujan" x1="650" y1="25" x2="640" y2="65" style="animation-delay: 0.4s;" />
    <line class="hujan" x1="750" y1="15" x2="740" y2="55" style="animation-delay: 0.55s;" />
    
    <!-- Baris 2 (lebih ke bawah) -->
    <line class="hujan" x1="100" y1="80" x2="90" y2="120" style="animation-delay: 0.2s;" />
    <line class="hujan" x1="200" y1="100" x2="190" y2="140" style="animation-delay: 0.35s;" />
    <line class="hujan" x1="300" y1="70" x2="290" y2="110" style="animation-delay: 0.05s;" />
    <line class="hujan" x1="500" y1="90" x2="490" y2="130" style="animation-delay: 0.5s;" />
    <line class="hujan" x1="700" y1="85" x2="690" y2="125" style="animation-delay: 0.15s;" />
  </g>

  <!-- SUTRA PETIR UTAMA (BERBENTUK ZIGZAG) -->
  <!-- Dari kiri-atas ke kanan-bawah, lalu bercabang -->
  <polyline class="petir-utama" points="380,20 360,80 395,85 340,160" />
  
  <!-- SUTRA PETIR CABANG (Efek percabangan kecil) -->
  <polyline class="petir-cabang" points="360,80 385,100 375,120" />
  <polyline class="petir-cabang" points="395,85 415,105 405,135" />

  <!-- TEKS (Opsional - Letakkan di atas agar terbaca) -->
  <text x="400" y="160" font-family="Arial, sans-serif" font-size="24" font-weight="bold" fill="#ffffff" text-anchor="middle" opacity="0.9" letter-spacing="3">
    ⚡ FULL-STACK DEVELOPER ⚡
  </text>
  <text x="400" y="185" font-family="Arial, sans-serif" font-size="12" fill="#a0b4d6" text-anchor="middle" opacity="0.7" letter-spacing="2">
    Building Apps Like Thunder
  </text>
</svg>
