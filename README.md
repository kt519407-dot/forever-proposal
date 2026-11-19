# forever-proposal
A romantic proposal page with photo and video
<style>
    /* ==============================================================
       1. TWILIGHT STARLIGHT & ROSE-GOLD THEME VARIABLES
       ============================================================== */
    :root {
        --bg-night: #0f081e;
        --bg-twilight: #21113b;
        --bg-plum: #3d163b;
        --rose-gold: #f472b6;
        --rose-soft: #fbcfe8;
        --champagne: #fde68a;
        --amber-glow: #f59e0b;
        --cream-text: #fffbeb;
        --lavender-text: #f3e8ff;
        --glass-surface: rgba(28, 15, 52, 0.76);
        --glass-border: rgba(253, 230, 138, 0.32);
    }

    * {
        box-sizing: border-box;
        margin: 0;
        padding: 0;
        -webkit-tap-highlight-color: transparent;
    }

    body {
        font-family: 'Quicksand', sans-serif;
        background: radial-gradient(circle at 80% 10%, var(--bg-plum) 0%, var(--bg-twilight) 48%, var(--bg-night) 100%);
        color: var(--cream-text);
        min-height: 100vh;
        overflow-x: hidden;
        display: flex;
        align-items: center;
        justify-content: center;
        padding: 64px 16px 28px;
        position: relative;
    }

    .font-script {
        font-family: 'Great Vibes', cursive;
    }

    .font-serif {
        font-family: 'Playfair Display', serif;
    }

    /* Background Twinkling Starlight & Floating Hearts Canvas */
    #starlight-canvas {
        position: fixed;
        inset: 0;
        width: 100%;
        height: 100%;
        pointer-events: none;
        z-index: 0;
    }

    /* Top Floating Music & Sound Toggle Bar */
    .top-audio-bar {
        position: fixed;
        top: 14px;
        right: 16px;
        left: 16px;
        max-width: 450px;
        margin: 0 auto;
        display: flex;
        justify-content: space-between;
        align-items: center;
        z-index: 50;
        pointer-events: none;
    }

    .stage-pill {
        pointer-events: auto;
        background: rgba(24, 12, 46, 0.78);
        backdrop-filter: blur(12px);
        border: 1px solid rgba(253, 230, 138, 0.3);
        color: var(--champagne);
        font-size: 0.72rem;
        font-weight: 700;
        padding: 7px 13px;
        border-radius: 999px;
        letter-spacing: 0.05em;
    }

    .sound-toggle-btn {
        pointer-events: auto;
        display: inline-flex;
        align-items: center;
        gap: 6px;
        background: linear-gradient(135deg, rgba(244, 114, 182, 0.25), rgba(245, 158, 11, 0.25));
        backdrop-filter: blur(12px);
        border: 1px solid rgba(253, 230, 138, 0.45);
        color: var(--cream-text);
        font-family: 'Quicksand', sans-serif;
        font-size: 0.76rem;
        font-weight: 700;
        padding: 7px 14px;
        border-radius: 999px;
        cursor: pointer;
        box-shadow: 0 6px 20px rgba(0, 0, 0, 0.35);
        transition: all 0.25s ease;
    }

    .sound-toggle-btn:hover {
        transform: scale(1.04);
        border-color: var(--champagne);
    }

    .sound-wave {
        display: inline-flex;
        align-items: flex-end;
        gap: 2px;
        height: 12px;
    }

    .sound-wave span {
        width: 2.5px;
        height: 5px;
        background: var(--champagne);
        border-radius: 2px;
        transition: height 0.2s ease;
    }

    .sound-wave.playing span:nth-child(1) { animation: eqBar 0.6s infinite alternate; }
    .sound-wave.playing span:nth-child(2) { animation: eqBar 0.45s infinite alternate 0.15s; }
    .sound-wave.playing span:nth-child(3) { animation: eqBar 0.7s infinite alternate 0.3s; }

    @keyframes eqBar {
        from { height: 4px; }
        to { height: 12px; }
    }

    /* Main Glassmorphic App Container */
    .app-container {
        width: 100%;
        max-width: 450px;
        z-index: 10;
        position: relative;
    }

    .glass-stage {
        background: var(--glass-surface);
        backdrop-filter: blur(22px);
        -webkit-backdrop-filter: blur(22px);
        border: 1.5px solid var(--glass-border);
        border-radius: 30px;
        padding: 28px 22px;
        box-shadow: 0 28px 65px rgba(0, 0, 0, 0.6), 0 0 35px rgba(244, 114, 182, 0.18);
        text-align: center;
        animation: smoothEntrance 0.65s cubic-bezier(0.16, 1, 0.3, 1) forwards;
    }

    @keyframes smoothEntrance {
        from { opacity: 0; transform: translateY(26px) scale(0.96); }
        to { opacity: 1; transform: translateY(0) scale(1); }
    }

    .hidden {
        display: none !important;
    }

    /* Badges & Gradients */
    .royal-badge {
        display: inline-flex;
        align-items: center;
        gap: 6px;
        padding: 6px 15px;
        border-radius: 999px;
        background: linear-gradient(135deg, rgba(245, 158, 11, 0.22), rgba(244, 114, 182, 0.24));
        border: 1px solid rgba(253, 230, 138, 0.45);
        color: var(--champagne);
        font-size: 0.75rem;
        font-weight: 700;
        letter-spacing: 0.08em;
        text-transform: uppercase;
        margin-bottom: 14px;
    }

    .rose-gold-heading {
        background: linear-gradient(135deg, #fffbeb 5%, #fde68a 45%, #f472b6 92%);
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
    }

    /* Primary CTA Button */
    .btn-celestial {
        width: 100%;
        padding: 15px 22px;
        border: none;
        border-radius: 18px;
        background: linear-gradient(135deg, #f59e0b 0%, #ec4899 52%, #9333ea 100%);
        color: #ffffff;
        font-family: 'Quicksand', sans-serif;
        font-size: 1rem;
        font-weight: 700;
        cursor: pointer;
        box-shadow: 0 12px 28px rgba(236, 72, 153, 0.42);
        transition: transform 0.2s cubic-bezier(0.34, 1.56, 0.64, 1), box-shadow 0.2s ease;
    }

    .btn-celestial:hover {
        transform: translateY(-2px) scale(1.01);
        box-shadow: 0 16px 34px rgba(236, 72, 153, 0.56);
    }

    .btn-celestial:active {
        transform: scale(0.96);
    }

    /* ==============================================================
       2. STAGE 1: CELESTIAL PORTAL ENTRANCE
       ============================================================== */
    .celestial-portal {
        width: 164px;
        height: 164px;
        margin: 10px auto 18px;
        border-radius: 50%;
        background: radial-gradient(circle, rgba(244, 114, 182, 0.32) 0%, rgba(245, 158, 11, 0.14) 55%, transparent 74%);
        border: 1.5px dashed rgba(253, 230, 138, 0.6);
        display: flex;
        align-items: center;
        justify-content: center;
        position: relative;
        cursor: pointer;
        animation: orbitRotate 18s linear infinite;
    }

    .celestial-portal::before {
        content: "✨";
        position: absolute;
        top: -10px;
        font-size: 1.1rem;
    }

    .celestial-portal::after {
        content: "💖";
        position: absolute;
        bottom: -10px;
        font-size: 1rem;
    }

    .portal-emblem {
        animation: counterOrbit 18s linear infinite, hoverFloat 2.6s ease-in-out infinite;
        font-size: 4.3rem;
        filter: drop-shadow(0 10px 22px rgba(245, 158, 11, 0.5));
    }

    @keyframes orbitRotate {
        from { transform: rotate(0deg); }
        to { transform: rotate(360deg); }
    }

    @keyframes counterOrbit {
        from { transform: rotate(0deg); }
        to { transform: rotate(-360deg); }
    }

    @keyframes hoverFloat {
        0%, 100% { transform: translateY(0); }
        50% { transform: translateY(-9px); }
    }

    .nickname-ticker {
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        gap: 6px;
        margin: 14px 0 22px;
    }

    .nick-chip {
        font-size: 0.72rem;
        font-weight: 700;
        padding: 4px 10px;
        border-radius: 999px;
        background: rgba(255, 255, 255, 0.09);
        border: 1px solid rgba(244, 114, 182, 0.35);
        color: var(--rose-soft);
    }

    /* ==============================================================
       3. STAGE 2: MULTI-TIER ROSE-GOLD & CREAM 21ST CAKE
       ============================================================== */
    .cake-arena {
        position: relative;
        height: 255px;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: flex-end;
        margin: 10px 0 16px;
        padding-bottom: 10px;
    }

    .topper-21-crown {
        display: flex;
        flex-direction: column;
        align-items: center;
        margin-bottom: 2px;
        animation: crownGlow 2.2s infinite alternate;
    }

    .topper-21-num {
        font-family: 'Playfair Display', serif;
        font-size: 2.25rem;
        font-weight: 700;
        line-height: 1;
        color: #fde68a;
        text-shadow: 0 0 14px rgba(245, 158, 11, 0.95), 0 0 26px rgba(244, 114, 182, 0.8);
    }

    @keyframes crownGlow {
        from { transform: scale(1); }
        to { transform: scale(1.07); }
    }

    .candles-group {
        display: flex;
        gap: 28px;
        z-index: 6;
        margin-bottom: -4px;
    }

    .candle-item {
        display: flex;
        flex-direction: column;
        align-items: center;
        cursor: pointer;
        padding: 4px 8px;
        position: relative;
        transition: transform 0.2s ease;
    }

    .candle-item:hover {
        transform: scale(1.1);
    }

    .candle-flame {
        width: 14px;
        height: 23px;
        background: radial-gradient(circle at 50% 75%, #ffffff 12%, #fde047 48%, #f97316 86%, transparent 100%);
        border-radius: 50% 50% 35% 35%;
        box-shadow: 0 0 14px #fbbf24, 0 0 28px #f97316;
        animation: flameDance 0.32s infinite alternate ease-in-out;
        transform-origin: bottom center;
        margin-bottom: 3px;
    }

    .candle-flame.extinguished {
        opacity: 0;
        transform: scale(0.1) translateY(-14px);
        transition: all 0.35s ease-out;
    }

    /* Smoke Puff when blown out */
    .smoke-puff {
        position: absolute;
        top: -8px;
        width: 14px;
        height: 14px;
        border-radius: 50%;
        background: rgba(255, 255, 255, 0.65);
        filter: blur(3px);
        animation: smokeRise 1.1s ease-out forwards;
        pointer-events: none;
    }

    @keyframes smokeRise {
        0% { opacity: 0.85; transform: translateY(0) scale(0.7); }
        100% { opacity: 0; transform: translateY(-34px) scale(2.2); }
    }

    @keyframes flameDance {
        0% { transform: scale(1) rotate(-3deg); }
        100% { transform: scale(1.08, 0.93) rotate(3deg); }
    }

    .candle-body {
        width: 10px;
        height: 36px;
        border-radius: 4px;
        background: repeating-linear-gradient(45deg, #fffbeb, #fffbeb 5px, #f472b6 5px, #f472b6 10px);
        border: 1px solid rgba(253, 230, 138, 0.7);
    }

    /* Rose-Gold & Cream Tiers */
    .tier-top {
        width: 144px;
        height: 48px;
        background: linear-gradient(180deg, #fffbeb 0%, #fbcfe8 45%, #f472b6 100%);
        border-radius: 16px 16px 6px 6px;
        position: relative;
        box-shadow: inset 0 6px 0 rgba(255, 255, 255, 0.7), 0 5px 14px rgba(0, 0, 0, 0.28);
        transition: transform 0.65s cubic-bezier(0.34, 1.56, 0.64, 1);
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .tier-top::after {
        content: "Janu 👑";
        font-size: 0.68rem;
        font-weight: 700;
        color: #831843;
    }

    .tier-bottom {
        width: 210px;
        height: 60px;
        background: linear-gradient(180deg, #fde68a 0%, #f9a8d4 45%, #db2777 100%);
        border-radius: 16px 16px 10px 10px;
        position: relative;
        box-shadow: inset 0 7px 0 rgba(255, 255, 255, 0.65), 0 10px 22px rgba(0, 0, 0, 0.38);
        transition: transform 0.65s cubic-bezier(0.34, 1.56, 0.64, 1);
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .tier-bottom::after {
        content: "✨ Pyari Jigglu • 21 ✨";
        font-size: 0.75rem;
        font-weight: 700;
        color: #4c0519;
        letter-spacing: 0.4px;
    }

    .cake-stand {
        width: 244px;
        height: 12px;
        background: linear-gradient(90deg, #d97706, #fef3c7, #f59e0b);
        border-radius: 999px;
        box-shadow: 0 8px 18px rgba(0, 0, 0, 0.5);
    }

    .cake-cut-active .tier-top {
        transform: translateX(-10px) rotate(-2.5deg);
    }

    .cake-cut-active .tier-bottom {
        transform: translateX(10px) rotate(2deg);
    }

    /* ==============================================================
       4. STAGE 3: NICKNAME & ROMANTIC COMPLIMENT CONSTELLATION
       ============================================================== */
    .constellation-bar {
        width: 100%;
        height: 10px;
        background: rgba(255, 255, 255, 0.12);
        border-radius: 999px;
        overflow: hidden;
        margin: 10px 0 16px;
        border: 1px solid rgba(253, 230, 138, 0.3);
    }

    .constellation-fill {
        height: 100%;
        width: 0%;
        background: linear-gradient(90deg, #fde68a, #f472b6, #a855f7);
        transition: width 0.45s cubic-bezier(0.34, 1.56, 0.64, 1);
    }

    .orbs-grid {
        display: grid;
        grid-template-columns: repeat(2, 1fr);
        gap: 11px;
        margin-bottom: 16px;
    }

    .orb-card {
        min-height: 124px;
        border-radius: 22px;
        padding: 12px 10px;
        background: radial-gradient(circle at top left, rgba(244, 114, 182, 0.26), rgba(88, 28, 135, 0.32));
        border: 1.5px solid rgba(253, 230, 138, 0.38);
        box-shadow: 0 8px 20px rgba(0, 0, 0, 0.25), inset 0 0 16px rgba(244, 114, 182, 0.15);
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        cursor: pointer;
        transition: all 0.32s cubic-bezier(0.34, 1.56, 0.64, 1);
    }

    .orb-card:hover {
        transform: translateY(-4px) scale(1.03);
        border-color: var(--champagne);
        box-shadow: 0 12px 26px rgba(244, 114, 182, 0.35);
    }

    .orb-card.revealed {
        background: linear-gradient(145deg, rgba(255, 251, 235, 0.14), rgba(244, 114, 182, 0.22));
        border-color: #f472b6;
        cursor: default;
        transform: scale(1);
    }

    .orb-sphere {
        width: 46px;
        height: 46px;
        border-radius: 50%;
        background: radial-gradient(circle at 30% 30%, #ffffff, #fbcfe8 35%, #ec4899 100%);
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 1.4rem;
        margin-bottom: 7px;
        box-shadow: 0 0 18px rgba(244, 114, 182, 0.65);
        animation: orbBob 2.8s ease-in-out infinite;
    }

    .orb-card:nth-child(even) .orb-sphere {
        animation-delay: 0.9s;
    }

    @keyframes orbBob {
        0%, 100% { transform: translateY(0); }
        50% { transform: translateY(-5px); }
    }

    .orb-shayari {
        font-size: 0.76rem;
        line-height: 1.45;
        color: #fffbeb;
        font-weight: 600;
        animation: fadeScaleIn 0.4s ease forwards;
    }

    @keyframes fadeScaleIn {
        from { opacity: 0; transform: scale(0.86); }
        to { opacity: 1; transform: scale(1); }
    }

    /* ==============================================================
       5. STAGE 4: DIL KI BAATEIN (INTERACTIVE SCRATCH & DECK)
       ============================================================== */
    .scratch-container {
        position: relative;
        width: 100%;
        height: 165px;
        border-radius: 22px;
        overflow: hidden;
        margin: 14px 0 16px;
        border: 2px solid rgba(253, 230, 138, 0.55);
        box-shadow: 0 12px 30px rgba(0, 0, 0, 0.4);
        user-select: none;
        touch-action: none;
    }

    .scratch-secret-layer {
        position: absolute;
        inset: 0;
        background: linear-gradient(135deg, #4c0519 0%, #701a75 50%, #3b0764 100%);
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        padding: 16px;
        text-align: center;
    }

    #scratch-canvas {
        position: absolute;
        inset: 0;
        width: 100%;
        height: 100%;
        cursor: crosshair;
        transition: opacity 0.5s ease;
    }

    .shayari-deck-card {
        background: rgba(255, 255, 255, 0.08);
        border: 1px solid rgba(244, 114, 182, 0.38);
        border-radius: 20px;
        padding: 16px 14px;
        margin-bottom: 16px;
        min-height: 112px;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        transition: all 0.3s ease;
    }

    .btn-deck-next {
        background: rgba(253, 230, 138, 0.16);
        border: 1px solid rgba(253, 230, 138, 0.5);
        color: var(--champagne);
        font-family: 'Quicksand', sans-serif;
        font-size: 0.8rem;
        font-weight: 700;
        padding: 8px 16px;
        border-radius: 999px;
        cursor: pointer;
        margin-top: 10px;
        transition: all 0.2s ease;
    }

    .btn-deck-next:hover {
        background: rgba(253, 230, 138, 0.28);
    }

    /* ==============================================================
       6. STAGE 5: ROYAL 21ST LETTER & GOLDEN VIP PASS
       ============================================================== */
    .royal-letter-box {
        background: rgba(15, 8, 30, 0.68);
        border: 1px solid rgba(253, 230, 138, 0.32);
        border-radius: 22px;
        padding: 18px 16px;
        text-align: left;
        font-size: 0.85rem;
        line-height: 1.65;
        color: var(--lavender-text);
        margin: 12px 0 16px;
        max-height: 270px;
        overflow-y: auto;
    }

    .royal-letter-box p {
        margin-bottom: 11px;
    }

    .royal-letter-box p:last-child {
        margin-bottom: 0;
    }

    .royal-letter-box::-webkit-scrollbar {
        width: 5px;
    }
    .royal-letter-box::-webkit-scrollbar-thumb {
        background: rgba(244, 114, 182, 0.55);
        border-radius: 10px;
    }

    .golden-vip-card {
        margin-top: 14px;
        background: linear-gradient(135deg, #fef3c7 0%, #fde68a 45%, #fbcfe8 100%);
        color: #3b0764;
        border-radius: 24px;
        padding: 4px;
        box-shadow: 0 16px 38px rgba(245, 158, 11, 0.4);
        animation: smoothEntrance 0.6s ease forwards;
    }

    .golden-vip-inner {
        border: 2px dashed #b45309;
        border-radius: 20px;
        padding: 18px 14px;
        background: rgba(255, 255, 255, 0.62);
    }

    .vip-pill {
        display: inline-block;
        background: #701a75;
        color: #fde68a;
        font-size: 0.66rem;
        font-weight: 700;
        letter-spacing: 0.1em;
        text-transform: uppercase;
        padding: 4px 12px;
        border-radius: 999px;
        margin-bottom: 8px;
    }

    .btn-replay-outline {
        margin-top: 12px;
        width: 100%;
        padding: 12px 16px;
        border-radius: 16px;
        background: rgba(255, 255, 255, 0.12);
        border: 1px solid rgba(253, 230, 138, 0.45);
        color: var(--champagne);
        font-family: 'Quicksand', sans-serif;
        font-size: 0.88rem;
        font-weight: 700;
        cursor: pointer;
        transition: background 0.2s ease;
    }

    .btn-replay-outline:hover {
        background: rgba(255, 255, 255, 0.22);
    }

    /* Floating Confetti Burst DOM */
    .burst-particle {
        position: fixed;
        pointer-events: none;
        z-index: 99;
        font-size: 1.45rem;
        animation: burstOut 1.65s cubic-bezier(0.16, 1, 0.3, 1) forwards;
    }

    @keyframes burstOut {
        0% { transform: translate(0, 0) scale(0.4) rotate(0deg); opacity: 1; }
        100% { transform: translate(var(--bx), var(--by)) scale(1.35) rotate(var(--brot)); opacity: 0; }
    }
</style>
