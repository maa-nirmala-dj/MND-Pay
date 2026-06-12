<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no, viewport-fit=cover">
    <meta name="theme-color" content="#050608">
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
    <title>MND Pay | Premium FinTech Hub</title>

    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;500;600;700;800;900&family=Space+Grotesk:wght@500;700;900&family=Cinzel:wght@700;900&family=Orbitron:wght@500;700;900&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">

    <!-- Firebase SDKs -->
    <script src="https://www.gstatic.com/firebasejs/10.10.0/firebase-app-compat.js"></script>
    <script src="https://www.gstatic.com/firebasejs/10.10.0/firebase-database-compat.js"></script>

    <!-- Google Translate API -->
    <script type="text/javascript" src="https://translate.google.com/translate_a/element.js?cb=googleTranslateElementInit"></script>

    <style>
        /* =========================================================================
           ADVANCED PREMIUM FINTECH STYLES (MND HUB THEME)
           ========================================================================= */
        :root {
            --primary: #4f46e5;
            --primary-glow: rgba(79, 70, 229, 0.4);
            --accent: #00E5FF;
            --success: #00FA9A;
            --danger: #ff3333;
            --gold: #D4AF37;
            --gold-glow: rgba(212, 175, 55, 0.4);
            --gold-bright: #FDE047;
            --bg-base: #050608;
            --bg-nav: rgba(5, 6, 8, 0.85);
            --bg-card: rgba(15, 18, 25, 0.85);
            --text-main: #f8fafc;
            --text-muted: #94a3b8;
            --border-light: rgba(255, 255, 255, 0.08);
            
            --nav-height: 65px; 
            --bottom-nav-height: 80px;
        }

        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Outfit', sans-serif; -webkit-tap-highlight-color: transparent; outline: none; }
        
        /* * PERFECT SCROLLING ARCHITECTURE FIX
         * Body is strictly locked. Scrolling happens INSIDE the wrapper.
         */
        body, html { 
            width: 100%; height: 100%; 
            background: var(--bg-base); color: var(--text-main); 
            overflow: hidden; /* Prevent native body scroll to stop bounce effect */
            position: fixed; top: 0; left: 0; right: 0; bottom: 0;
        }

        /* Abstract Animated Background */
        .bg-mesh {
            position: absolute; inset: 0; z-index: -2; opacity: 0.3;
            background-image: 
                radial-gradient(circle at 15% 25%, var(--gold-glow) 0%, transparent 45%),
                radial-gradient(circle at 85% 75%, rgba(0, 229, 255, 0.1) 0%, transparent 45%);
            animation: pulseBg 12s infinite alternate ease-in-out;
            pointer-events: none;
        }
        .grid-overlay {
            position: absolute; inset: 0; z-index: -1; opacity: 0.03;
            background-image: linear-gradient(var(--gold) 1px, transparent 1px), linear-gradient(90deg, var(--gold) 1px, transparent 1px);
            background-size: 35px 35px;
            mask-image: radial-gradient(circle at center, black 40%, transparent 100%);
            -webkit-mask-image: radial-gradient(circle at center, black 40%, transparent 100%);
            pointer-events: none;
        }
        @keyframes pulseBg { 0% { transform: scale(1); opacity: 0.2; } 100% { transform: scale(1.1); opacity: 0.5; } }

        /* Hide Google Translate Banner & Fix Body Top */
        .goog-te-banner-frame.skiptranslate { display: none !important; } 
        body { top: 0px !important; }
        #google_translate_element select {
            background: rgba(0,0,0,0.6); color: var(--gold-bright); border: 1px solid var(--gold);
            padding: 12px 15px; border-radius: 12px; width: 100%; font-family: 'Outfit'; font-size: 16px; outline: none;
            box-shadow: inset 0 0 10px rgba(212,175,55,0.1); appearance: none;
        }
        #google_translate_element .goog-te-gadget { font-family: 'Outfit', sans-serif !important; }
        .goog-logo-link { display:none !important; } 
        .goog-te-gadget { color: transparent !important; }

        /* =========================================================================
           TOP NAVIGATION BAR
           ========================================================================= */
        .top-nav {
            position: fixed; top: 0; left: 0; width: 100%; height: var(--nav-height);
            background: var(--bg-nav); backdrop-filter: blur(20px); -webkit-backdrop-filter: blur(20px);
            border-bottom: 1px solid var(--border-light); z-index: 1000;
            display: flex; justify-content: space-between; align-items: center; padding: 0 20px;
            padding-top: env(safe-area-inset-top);
            transform: translateY(-100%); transition: transform 0.4s cubic-bezier(0.4, 0, 0.2, 1);
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
        }
        .top-nav.visible { transform: translateY(0); }

        .nav-left { display: flex; align-items: center; gap: 15px; }
        .menu-icon { font-size: 24px; color: #fff; cursor: pointer; transition: 0.3s; padding: 5px; }
        .menu-icon:hover { color: var(--gold); transform: scale(1.1); }
        
        /* Stacked Logo matching user specification */
        .brand-logo { 
            display: flex; align-items: center; gap: 8px; color: var(--gold); 
            text-shadow: 0 0 15px var(--gold-glow); cursor: pointer;
        }
        .brand-logo i { font-size: 28px; }
        .brand-text { display: flex; flex-direction: column; align-items: flex-start; line-height: 1; }
        .brand-text span:first-child { font-family: 'Cinzel', serif; font-size: 18px; font-weight: 900; letter-spacing: 1px; }
        .brand-text span:last-child { font-family: 'Outfit', sans-serif; font-size: 13px; font-weight: 800; color: var(--gold-bright); letter-spacing: 2px; }
        
        .nav-right { display: flex; align-items: center; gap: 10px; }
        .nav-box-btn {
            width: 38px; height: 38px; border-radius: 12px; background: rgba(255,255,255,0.03);
            border: 1px solid var(--border-light); color: #fff; font-size: 16px;
            display: flex; justify-content: center; align-items: center; cursor: pointer;
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        }
        .nav-box-btn:hover, .nav-box-btn.active {
            background: rgba(212, 175, 55, 0.15); box-shadow: 0 0 15px var(--gold-glow), inset 0 0 10px rgba(212, 175, 55, 0.3);
            transform: translateY(-2px); color: var(--gold-bright); border-color: var(--gold-bright);
        }

        /* SIDE MENU (Hamburger Drawer) */
        .side-menu-overlay {
            position: fixed; inset: 0; background: rgba(0,0,0,0.8); backdrop-filter: blur(8px);
            z-index: 10000; opacity: 0; pointer-events: none; transition: 0.3s ease;
        }
        .side-menu-overlay.active { opacity: 1; pointer-events: auto; }
        .side-drawer {
            position: fixed; top: 0; left: -320px; width: 300px; height: 100dvh;
            background: linear-gradient(180deg, rgba(15,18,25,0.98) 0%, rgba(5,6,8,0.98) 100%);
            border-right: 1px solid var(--gold); z-index: 10001; transition: 0.4s cubic-bezier(0.2, 0.8, 0.2, 1);
            display: flex; flex-direction: column; padding: 40px 20px; box-shadow: 20px 0 50px rgba(0,0,0,0.9);
        }
        .side-menu-overlay.active .side-drawer { left: 0; }
        .drawer-header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 30px; border-bottom: 1px dashed rgba(255,255,255,0.1); padding-bottom: 20px; }
        .drawer-link {
            display: flex; align-items: center; gap: 15px; padding: 16px; border-radius: 14px;
            color: #fff; text-decoration: none; font-size: 15px; font-weight: 500;
            transition: 0.3s; margin-bottom: 12px; background: rgba(255,255,255,0.03); border: 1px solid transparent;
        }
        .drawer-link:hover { background: rgba(212,175,55,0.1); border-color: var(--gold); color: var(--gold-bright); transform: translateX(8px); }

        /* =========================================================================
           BOTTOM NAVIGATION BAR
           ========================================================================= */
        .bottom-nav {
            position: fixed; bottom: 0; left: 0; width: 100%; height: var(--bottom-nav-height);
            background: var(--bg-nav); backdrop-filter: blur(20px); -webkit-backdrop-filter: blur(20px);
            border-top: 1px solid var(--border-light); z-index: 1000;
            display: flex; justify-content: space-around; align-items: center; padding: 0 10px;
            padding-bottom: env(safe-area-inset-bottom);
            transform: translateY(100%); transition: transform 0.4s cubic-bezier(0.4, 0, 0.2, 1);
            box-shadow: 0 -10px 30px rgba(0,0,0,0.5);
        }
        .bottom-nav.visible { transform: translateY(0); }

        .b-nav-item {
            display: flex; flex-direction: column; align-items: center; justify-content: center; gap: 6px;
            color: var(--text-muted); cursor: pointer; transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            width: 75px; height: 100%; position: relative;
        }
        .b-nav-item i { font-size: 22px; transition: 0.3s; z-index: 2; }
        .b-nav-item span { font-size: 11px; font-weight: 600; z-index: 2; text-transform: uppercase; letter-spacing: 0.5px; }
        
        .b-nav-item.active { color: var(--gold-bright); }
        .b-nav-item.active i { text-shadow: 0 0 20px var(--gold-bright); transform: translateY(-4px); font-size: 24px; }
        .b-nav-item.active::before {
            content: ''; position: absolute; top: 10px; left: 50%; transform: translateX(-50%);
            width: 50px; height: 50px; background: radial-gradient(circle, rgba(253, 224, 71, 0.2) 0%, transparent 60%);
            border-radius: 50%; z-index: 1; pointer-events: none;
        }

        /* =========================================================================
           VIEW MANAGEMENT (PERFECT SCROLL)
           ========================================================================= */
        .view-wrapper { 
            position: absolute; top: 0; left: 0; right: 0; bottom: 0; 
            overflow: hidden; 
        }
        
        .view-container { 
            display: none; width: 100%; height: 100%; 
            overflow-y: auto; overflow-x: hidden; 
            -webkit-overflow-scrolling: touch; /* Smooth iOS scrolling */
            scroll-behavior: smooth;
        }
        
        /* The inner wrapper guarantees items center properly and don't clip at the top */
        .view-inner {
            display: flex; flex-direction: column; 
            width: 100%; max-width: 650px; 
            margin: 0 auto; 
            min-height: 100%; /* Ensures flex-grow works */
            padding: calc(var(--nav-height) + 20px) 20px calc(var(--bottom-nav-height) + 40px);
            animation: fadeSlideUp 0.5s cubic-bezier(0.2, 0.8, 0.2, 1) forwards; 
        }

        @keyframes fadeSlideUp {
            from { opacity: 0; transform: translateY(30px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .active-view { display: block !important; }

        #view-auth .view-inner { padding: 40px 20px; justify-content: center; }
        #view-payment-gateway .view-inner { padding: 40px 20px 40px 20px; }
        #view-payment-gateway { background: var(--bg-base); z-index: 2000; position: relative; }

        /* Premium Glass Cards */
        .glass-card {
            width: 100%; background: var(--bg-card); backdrop-filter: blur(25px); -webkit-backdrop-filter: blur(25px);
            border: 1px solid var(--border-light); border-radius: 20px; padding: 25px;
            box-shadow: 0 15px 40px rgba(0, 0, 0, 0.6), inset 0 1px 0 rgba(255,255,255,0.1);
            margin-bottom: 20px; flex-shrink: 0; position: relative; overflow: hidden;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }
        .flex-grow { flex-grow: 1; }
        
        .card-header { display: flex; justify-content: space-between; align-items: center; border-bottom: 1px dashed rgba(255,255,255,0.15); padding-bottom: 15px; margin-bottom: 18px; }
        .section-title { font-family: 'Space Grotesk'; font-size: 17px; color: #fff; display: flex; align-items: center; gap: 12px; margin: 0; }
        
        /* Form & Inputs */
        .input-group { position: relative; margin-bottom: 18px; width: 100%; }
        .input-icon { position: absolute; left: 18px; top: 50%; transform: translateY(-50%); color: var(--gold); font-size: 16px; opacity: 0.9; }
        .mn-input {
            width: 100%; padding: 16px 16px 16px 50px; background: rgba(0,0,0,0.5);
            border: 1px solid rgba(212,175,55,0.3); border-radius: 14px;
            color: #fff; font-size: 15px; transition: all 0.3s ease; box-shadow: inset 0 4px 15px rgba(0,0,0,0.3);
        }
        .mn-input:focus { border-color: var(--gold); box-shadow: 0 0 20px var(--gold-glow), inset 0 2px 10px rgba(0,0,0,0.5); background: rgba(212,175,55,0.05); }
        .mn-input::placeholder { color: #777; font-weight: 400; }
        
        .pin-input { font-family: 'Orbitron'; letter-spacing: 12px; font-size: 22px; font-weight: 700; text-align: center; padding-left: 15px; color: var(--gold-bright); }
        .pin-input + .input-icon { display: none; }
        .pin-input::placeholder { font-size: 14px; letter-spacing: 4px; font-family: 'Outfit'; font-weight: 400; color: #555; }

        /* Buttons */
        .mn-btn {
            width: 100%; padding: 16px; border-radius: 14px; font-weight: 800; font-size: 14px; cursor: pointer;
            display: flex; justify-content: center; align-items: center; gap: 10px; border: none;
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1); text-transform: uppercase; letter-spacing: 1.5px; flex-shrink: 0;
        }
        .mn-btn:active { transform: scale(0.95); }
        .btn-gold { background: linear-gradient(135deg, var(--gold) 0%, #FFD700 100%); color: #000; box-shadow: 0 8px 25px var(--gold-glow); }
        .btn-outline { background: rgba(212,175,55,0.05); border: 1px solid var(--gold); color: var(--gold); backdrop-filter: blur(5px); }
        .btn-outline:hover { background: rgba(212,175,55,0.15); box-shadow: 0 5px 20px var(--gold-glow); }
        .btn-danger { background: rgba(255, 51, 51, 0.1); border: 1px solid var(--danger); color: var(--danger); }
        .btn-danger:hover { background: var(--danger); color: #fff; box-shadow: 0 8px 25px rgba(255, 51, 51, 0.4); }
        .btn-success { background: linear-gradient(135deg, var(--success) 0%, #059669 100%); color: #000; box-shadow: 0 8px 25px rgba(0, 250, 154, 0.3); }

        /* Custom Payment Gateway (Advanced Transaction UI) */
        .gateway-header { display: flex; align-items: center; gap: 15px; margin-bottom: 25px; width: 100%; }
        .gateway-amount-box {
            background: linear-gradient(135deg, #ffffff 0%, #f0f0f0 100%); border-radius: 20px; padding: 25px; 
            display: flex; flex-direction: column; gap: 8px;
            box-shadow: 0 15px 40px rgba(0,0,0,0.6); width: 100%; margin-bottom: 25px;
            position: relative; overflow: hidden;
        }
        .gateway-amount-box::before { content: ''; position: absolute; top:0; left:0; width:100%; height:4px; background: var(--success); }
        .gateway-amount-row { display: flex; justify-content: space-between; align-items: center; }
        .gateway-amount-row h2 { font-family: 'Space Grotesk'; font-size: 42px; color: #000; margin: 0; font-weight: 900; letter-spacing: -1px; }
        
        .gw-section-title { font-size: 15px; color: #fff; font-weight: 700; margin-bottom: 15px; display:flex; align-items:center; gap:10px; width:100%; }
        .gw-red-dot { width: 10px; height: 10px; background: var(--danger); border-radius: 50%; box-shadow: 0 0 12px var(--danger); }
        
        /* Fixed & Corrected Transaction Buttons Grid */
        .gateway-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 12px; margin-bottom: 25px; width: 100%; }
        .gw-btn {
            border-radius: 14px; padding: 15px 10px; display: flex; flex-direction: column; align-items: center; justify-content: center; gap: 10px;
            cursor: pointer; transition: all 0.3s ease; border: 1px solid rgba(255,255,255,0.15);
            background: rgba(255,255,255,0.03); backdrop-filter: blur(10px);
        }
        .gw-btn:hover { transform: translateY(-3px); border-color: rgba(255,255,255,0.4); box-shadow: 0 10px 20px rgba(0,0,0,0.4); }
        .gw-btn:active { transform: scale(0.95); }
        .gw-logo-svg { width: 36px; height: 36px; }
        .gw-btn span { font-size: 11px; font-weight: 700; color: #fff; text-align: center; letter-spacing: 0.5px; }
        
        /* Brand Colors for Hover */
        .gw-btn.paytm:hover { border-color: #00B9F5; background: rgba(0, 185, 245, 0.1); }
        .gw-btn.phonepe:hover { border-color: #5F259F; background: rgba(95, 37, 159, 0.1); }
        .gw-btn.gpay:hover { border-color: #4285F4; background: rgba(66, 133, 244, 0.1); }

        .qr-wrapper {
            background: #fff; padding: 25px; border-radius: 20px; text-align: center; width: 100%; margin-bottom: 25px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.4); border: 2px solid var(--border-light);
        }
        .qr-wrapper img { width: 200px; height: 200px; display: inline-block; border-radius: 10px; box-shadow: 0 5px 15px rgba(0,0,0,0.1); }
        .qr-wrapper p { font-size: 12px; color: #444; line-height: 1.6; margin-top: 15px; text-align: left; font-weight: 500; }

        .utr-paste-group { 
            width: 100%; background: #fff; border-radius: 14px; padding: 6px; 
            border: 2px solid var(--danger); display: flex; margin-bottom: 25px; box-shadow: 0 0 20px rgba(255,51,51,0.25);
        }
        .utr-input {
            flex-grow: 1; border: none; background: transparent; color: #000; font-family: 'Space Grotesk'; font-size: 15px; font-weight: 700; padding: 12px 15px; outline: none; letter-spacing: 1px;
        }
        .btn-paste {
            background: var(--danger); color: #fff; border: none; border-radius: 10px; padding: 0 20px; font-weight: 800; cursor: pointer; text-transform: uppercase; font-size: 13px; transition: 0.3s;
        }
        .btn-paste:active { transform: scale(0.95); }

        .gw-bottom-bar {
            display: flex; gap: 15px; width: 100%; margin-top: auto; padding-top: 25px;
        }
        .btn-gw-cancel { background: rgba(255,255,255,0.1); color: #fff; flex: 1; border-radius: 14px; font-weight: bold; border: 1px solid rgba(255,255,255,0.2); cursor:pointer; font-size: 14px; }
        .btn-gw-submit { background: #555; color: #aaa; flex: 2; border-radius: 14px; font-weight: 800; border: none; cursor:not-allowed; transition: 0.3s; font-size: 14px; text-transform: uppercase; }
        .btn-gw-submit.active { background: var(--primary); color: #fff; cursor: pointer; box-shadow: 0 8px 25px var(--primary-glow); }

        /* Beautiful UPI Items */
        .direct-upi-list { display: flex; flex-direction: column; gap: 12px; margin-top: 5px; }
        .upi-item {
            background: linear-gradient(90deg, rgba(0,0,0,0.6) 0%, rgba(212,175,55,0.08) 100%); 
            border: 1px solid rgba(212,175,55,0.3); padding: 16px 20px;
            border-radius: 14px; display: flex; justify-content: space-between; align-items: center; transition: 0.3s; cursor: pointer;
        }
        .upi-item:hover { border-color: var(--gold-bright); box-shadow: 0 8px 20px rgba(212,175,55,0.2); transform: translateX(5px); }
        .upi-id-text { font-family: 'Space Grotesk'; font-size: 15px; color: var(--gold-bright); letter-spacing: 0.5px; font-weight: 700; }
        .upi-copy-icon { width: 36px; height: 36px; border-radius: 10px; background: rgba(212,175,55,0.15); display: flex; justify-content: center; align-items: center; color: var(--gold); transition: 0.3s; }
        .upi-item:hover .upi-copy-icon { background: var(--gold); color: #000; }

        /* Team Grid (Help Section) */
        .team-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 18px; margin-top: 15px; }
        .team-card {
            background: rgba(0,0,0,0.6); border: 1px solid var(--border-light); border-radius: 16px;
            overflow: hidden; text-align: center; transition: 0.3s; box-shadow: 0 10px 30px rgba(0,0,0,0.5);
        }
        .team-card:hover { transform: translateY(-5px); border-color: var(--accent); box-shadow: 0 15px 40px rgba(0,229,255,0.25); }
        .team-img { width: 100%; height: 160px; object-fit: cover; border-bottom: 3px solid var(--accent); }
        .team-info { padding: 15px 12px; }
        .team-name { font-family: 'Space Grotesk'; font-size: 15px; color: #fff; font-weight: bold; margin-bottom: 12px; letter-spacing: 0.5px;}
        .team-actions { display: flex; justify-content: center; gap: 12px; }
        .team-btn {
            width: 40px; height: 40px; border-radius: 50%; display: flex; justify-content: center; align-items: center;
            color: #fff; text-decoration: none; font-size: 18px; transition: 0.2s;
        }
        .btn-call { background: linear-gradient(135deg, var(--primary), #3b82f6); box-shadow: 0 5px 15px rgba(79, 70, 229, 0.4); }
        .btn-wa { background: linear-gradient(135deg, #25D366, #128C7E); box-shadow: 0 5px 15px rgba(37, 211, 102, 0.4); }
        .team-btn:active { transform: scale(0.9); }

        /* Donate Portfolio Styles */
        .donate-hero {
            position: relative; width: 100%; height: 240px; border-radius: 20px; overflow: hidden;
            display: flex; flex-direction: column; justify-content: center; align-items: center; text-align: center;
            background: linear-gradient(rgba(0,0,0,0.4), rgba(0,0,0,0.9)), url('https://images.unsplash.com/photo-1488521787991-ed7bbaae773c?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80') center/cover;
            margin-bottom: 25px; border: 1px solid var(--gold); box-shadow: 0 20px 50px rgba(212,175,55,0.25);
        }
        .donate-title { font-family: 'Cinzel'; font-size: 38px; color: var(--gold-bright); text-shadow: 0 5px 20px #000; margin-bottom: 8px; font-weight: 900; }
        .donate-sub { font-size: 14px; color: #eee; text-shadow: 0 2px 5px #000; padding: 0 25px; font-weight: 400; line-height: 1.5; }
        .heart-beat { animation: heartBeat 1.5s infinite; color: var(--danger); display: inline-block; filter: drop-shadow(0 0 15px var(--danger)); }
        @keyframes heartBeat { 0%, 100% { transform: scale(1); } 50% { transform: scale(1.2); } }

        /* File Upload */
        .upload-area {
            border: 2px dashed rgba(0, 250, 154, 0.5); border-radius: 18px; padding: 35px 20px;
            text-align: center; cursor: pointer; transition: 0.3s; background: rgba(0,0,0,0.4);
            position: relative; overflow: hidden;
        }
        .upload-area:hover { border-color: var(--success); background: rgba(0, 250, 154, 0.05); }
        #preview-img { max-width: 100%; max-height: 280px; border-radius: 12px; margin-top: 18px; display: none; box-shadow: 0 15px 40px rgba(0,0,0,0.8); object-fit: contain; border: 1px solid rgba(255,255,255,0.1); }
        .file-icon-preview { display:none; font-size: 55px; color: var(--success); margin-top: 15px; }

        /* Data Lists (Directory & History) */
        .data-list { display: flex; flex-direction: column; gap: 14px; width: 100%; }
        .dir-item {
            background: rgba(0,0,0,0.6); border: 1px solid var(--border-light); border-left: 4px solid var(--accent);
            border-radius: 14px; padding: 18px; display: flex; justify-content: space-between; align-items: center; 
            transition: 0.3s; box-shadow: 0 8px 20px rgba(0,0,0,0.3); cursor: pointer;
        }
        .dir-item:hover { background: rgba(0, 229, 255, 0.08); border-left-color: var(--gold); transform: translateY(-3px); }
        .dir-item.suspended { border-left-color: var(--danger); opacity: 0.7; }

        .timeline-item {
            background: rgba(0,0,0,0.5); border: 1px solid var(--border-light); border-radius: 16px;
            padding: 20px; margin-bottom: 15px; display: flex; flex-direction: column; gap: 12px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
        }
        
        .action-icon-btn { background: transparent; border: none; color: #888; font-size: 20px; cursor: pointer; transition: 0.3s; padding: 5px; }
        .action-icon-btn:hover { color: var(--accent); transform: scale(1.15); }
        .action-icon-btn.trash { color: rgba(255,51,51,0.8); }
        .action-icon-btn.trash:hover { color: var(--danger); }

        /* Settings Toggles */
        .setting-row { display: flex; justify-content: space-between; align-items: center; padding: 18px 0; border-bottom: 1px solid rgba(255,255,255,0.05); }
        .setting-row:last-child { border-bottom: none; }
        .setting-info { display: flex; align-items: center; gap: 14px; font-size: 15px; font-weight: 500; color: #fff;}
        .setting-info i { color: var(--gold); font-size: 18px; width: 20px; text-align: center; }
        .switch { position: relative; display: inline-block; width: 50px; height: 26px; }
        .switch input { opacity: 0; width: 0; height: 0; }
        .slider { position: absolute; cursor: pointer; inset: 0; background-color: rgba(255,255,255,0.2); transition: .4s; border-radius: 26px; }
        .slider:before { position: absolute; content: ""; height: 20px; width: 20px; left: 3px; bottom: 3px; background-color: white; transition: .4s; border-radius: 50%; }
        input:checked + .slider { background-color: var(--success); box-shadow: 0 0 15px rgba(0,250,154,0.4); }
        input:checked + .slider:before { transform: translateX(24px); }

        /* Toasts & Modals */
        #toast-container { position: fixed; top: 85px; left: 50%; transform: translateX(-50%); z-index: 99999; display: flex; flex-direction: column; gap: 12px; pointer-events: none; width: 100%; align-items: center; }
        .toast {
            background: rgba(15, 18, 25, 0.98); border-left: 4px solid var(--gold);
            color: #fff; padding: 14px 20px; border-radius: 12px; font-weight: 600; font-size: 14px;
            box-shadow: 0 15px 40px rgba(0,0,0,0.8); display: flex; align-items: center; gap: 14px; max-width: 90%;
            animation: dropDown 0.5s cubic-bezier(0.2, 0.8, 0.2, 1) forwards, fadeUp 0.5s 4s forwards;
            backdrop-filter: blur(10px);
        }
        .toast.error { border-color: var(--danger); }
        .toast.success { border-color: var(--success); }
        @keyframes dropDown { from { opacity: 0; transform: translateY(-40px); } to { opacity: 1; transform: translateY(0); } }
        @keyframes fadeUp { from { opacity: 1; transform: translateY(0); } to { opacity: 0; transform: translateY(-40px); } }

        .modal-overlay {
            display: none; position: fixed; inset: 0; background: rgba(0,0,0,0.85); backdrop-filter: blur(10px);
            z-index: 999999; justify-content: center; align-items: center; padding: 20px;
        }
        .modal-overlay.active { display: flex; animation: fadeInModal 0.3s ease forwards; }
        @keyframes fadeInModal { from{opacity:0;} to{opacity:1;} }
        
        .modal-content {
            background: var(--bg-card); border: 1px solid var(--gold); border-radius: 20px;
            width: 100%; max-width: 420px; padding: 30px; box-shadow: 0 30px 60px rgba(0,0,0,0.9);
            max-height: 90vh; overflow-y: auto;
        }

        .footer-brand { text-align: center; font-size: 11px; color: rgba(255,255,255,0.25); margin-top: auto; padding: 25px 0 10px; font-family: 'Space Grotesk'; letter-spacing: 2px; text-transform: uppercase; font-weight: 700; }
        .status-tag { font-size: 10px; padding: 5px 10px; border-radius: 8px; font-weight: 800; text-transform: uppercase; display: inline-flex; align-items: center; gap: 5px; letter-spacing: 0.5px; }
        .tag-success { background: rgba(0, 250, 154, 0.15); color: var(--success); border: 1px solid rgba(0, 250, 154, 0.3); }
        .tag-pending { background: rgba(212, 175, 55, 0.15); color: var(--gold); border: 1px solid rgba(212, 175, 55, 0.3); }
        .tag-danger { background: rgba(255, 51, 51, 0.15); color: var(--danger); border: 1px solid rgba(255, 51, 51, 0.3); }
    </style>
</head>
<body>

    <div class="bg-mesh"></div>
    <div class="grid-overlay"></div>
    <div id="toast-container"></div>

    <!-- ==========================================
         TOP NAVIGATION BAR & SIDE MENU
         ========================================== -->
    <header class="top-nav" id="main-top-nav">
        <div class="nav-left">
            <i class="fas fa-bars menu-icon" onclick="toggleMenu()"></i>
            <div class="brand-logo" onclick="handleNavClick('home')">
                <i class="fas fa-wallet" style="margin-right: -2px;"></i> 
                <div class="brand-text">
                    <span>MND</span>
                    <span style="margin-top: -2px;">PAY</span>
                </div>
            </div>
        </div>
        <div class="nav-right">
            <button class="nav-box-btn" title="Translate Language" onclick="openModal('modal-language')">
                <i class="fas fa-language" style="font-size: 18px;"></i>
            </button>
            <button class="nav-box-btn" title="Theme" onclick="showToast('Theme Switcher active')"><i class="fas fa-sun"></i></button>
            <button class="nav-box-btn active" title="Settings" onclick="openModal('modal-settings')"><i class="fas fa-cog"></i></button>
        </div>
    </header>

    <!-- Side Menu Drawer -->
    <div class="side-menu-overlay" id="side-menu" onclick="toggleMenu()">
        <div class="side-drawer" onclick="event.stopPropagation()">
            <div class="drawer-header">
                <div class="brand-logo" style="font-size: 22px;">
                    <i class="fas fa-crown"></i> <span>MND HUB</span>
                </div>
                <i class="fas fa-times" style="color: #fff; font-size: 22px; cursor: pointer; padding:5px;" onclick="toggleMenu()"></i>
            </div>
            <a href="https://maa-nirmala-dj.github.io/WELCOME-TO-MND-HUB/" target="_blank" class="drawer-link">
                <i class="fas fa-network-wired" style="color: var(--accent); width:20px; text-align:center;"></i> MND Hub Portal
            </a>
            <a href="https://maa-nirmala-dj.github.io/-tent-house./" target="_blank" class="drawer-link">
                <i class="fas fa-globe" style="color: var(--success); width:20px; text-align:center;"></i> Official Website
            </a>
            <div style="margin-top: auto; text-align: center; color: var(--text-muted); font-size: 12px; line-height:1.6;">
                MND Pay System<br><strong style="color:var(--gold);">Version 4.0.0 (Build 2026)</strong>
            </div>
        </div>
    </div>

    <!-- ==========================================
         MAIN CONTENT WRAPPER
         ========================================== -->
    <div class="view-wrapper">
        
        <!-- VIEW 1: GATEKEEPER / AUTH -->
        <div id="view-auth" class="view-container active-view">
            <div class="view-inner" style="justify-content: center; height: 100vh; padding: 20px;">
                <div class="glass-card" style="border-color: var(--gold); box-shadow: 0 25px 70px rgba(0,0,0,0.9); padding: 40px 30px; margin: 0;">
                    <div style="text-align: center; margin-bottom: 30px;">
                        <div style="width: 80px; height: 80px; background: rgba(212, 175, 55, 0.08); border-radius: 24px; display: inline-flex; justify-content: center; align-items: center; margin-bottom: 18px; border: 1px solid rgba(212, 175, 55, 0.3); box-shadow: inset 0 0 20px rgba(212,175,55,0.1);">
                            <i class="fas fa-shield-alt" style="font-size: 38px; color: var(--gold); filter: drop-shadow(0 0 10px var(--gold-glow));"></i>
                        </div>
                        <h2 style="font-family: 'Space Grotesk'; font-size: 26px; color: #fff; font-weight: 900; letter-spacing: -0.5px;">Secure Portal</h2>
                        <p style="font-size: 13px; color: var(--text-muted); margin-top: 5px;">MND Logistics & MND Pay Unified Access</p>
                    </div>

                    <div id="form-login">
                        <div class="input-group">
                            <i class="fas fa-phone-alt input-icon"></i>
                            <input type="tel" id="login-phone" class="mn-input" placeholder="Registered Mobile Number" autocomplete="off">
                        </div>
                        <div class="input-group">
                            <input type="password" id="login-pin" class="mn-input pin-input" placeholder="6 DIGIT PIN" maxlength="6" autocomplete="off">
                        </div>
                        <button class="mn-btn btn-gold" onclick="processAuth()" id="btn-login" style="margin-top: 15px;">
                            <i class="fas fa-fingerprint"></i> INITIATE HANDSHAKE
                        </button>
                        <div style="text-align: center; margin-top: 25px;">
                            <a href="#" onclick="toggleAuthForm('register')" style="color: var(--accent); font-size: 14px; text-decoration: none; font-weight: 600; letter-spacing: 0.5px;">New User? Create Account</a>
                        </div>
                    </div>

                    <div id="form-register" style="display: none;">
                        <div class="input-group">
                            <i class="fas fa-user input-icon"></i>
                            <input type="text" id="reg-name" class="mn-input" placeholder="Full Name" autocomplete="off">
                        </div>
                        <div class="input-group">
                            <i class="fas fa-phone-alt input-icon"></i>
                            <input type="tel" id="reg-phone" class="mn-input" placeholder="Mobile Number" autocomplete="off">
                        </div>
                        <div class="input-group">
                            <input type="password" id="reg-pin" class="mn-input pin-input" placeholder="CREATE 6 DIGIT PIN" maxlength="6" autocomplete="off">
                        </div>
                        <button class="mn-btn btn-outline" onclick="selfRegisterUser()" style="margin-top: 15px;">
                            <i class="fas fa-user-plus"></i> REGISTER SECURELY
                        </button>
                        <div style="text-align: center; margin-top: 25px;">
                            <a href="#" onclick="toggleAuthForm('login')" style="color: var(--text-muted); font-size: 14px; text-decoration: none; font-weight: 500;">Back to Login</a>
                        </div>
                    </div>
                </div>
                <div class="footer-brand">POWERED BY MAA NIRMALA DJ</div>
            </div>
        </div>

        <!-- VIEW 2: ADMIN COMMAND CENTER -->
        <div id="view-admin" class="view-container">
            <div class="view-inner">
                <div style="width: 100%; display: flex; justify-content: space-between; align-items: center; margin-bottom: 25px; background: rgba(239, 68, 68, 0.08); padding: 18px 20px; border-radius: 18px; border: 1px solid rgba(239, 68, 68, 0.3);">
                    <div>
                        <h2 style="font-family: 'Cinzel'; font-size: 20px; color: var(--danger); margin-bottom: 4px; font-weight:900;">Command Center</h2>
                        <span style="font-size: 12px; color: #aaa; font-weight:500;">Admin Unified Directory</span>
                    </div>
                    <div class="status-badge status-tag tag-success" style="border-color: var(--accent); color: var(--accent); background: rgba(0, 229, 255, 0.1);"><i class="fas fa-database"></i> DUAL-SYNC</div>
                </div>

                <!-- Admin Registration Panel -->
                <div class="glass-card" style="border-color: rgba(6, 182, 212, 0.3);">
                    <div class="card-header" style="border-bottom: none; margin-bottom: 5px;">
                        <div class="section-title" style="color: var(--accent);"><i class="fas fa-user-plus"></i> Register New User</div>
                    </div>
                    <p style="font-size: 12px; color: var(--text-muted); margin-bottom: 18px;">Manually provision users to grant them portal access.</p>
                    <div style="display: flex; gap: 12px; margin-bottom: 12px;">
                        <input type="text" id="admin-reg-name" class="mn-input" style="padding: 14px 18px;" placeholder="Full Name">
                        <input type="tel" id="admin-reg-phone" class="mn-input" style="padding: 14px 18px;" placeholder="Mobile Number">
                    </div>
                    <div class="input-group" style="margin-bottom: 15px;">
                        <input type="text" id="admin-reg-pin" class="mn-input pin-input" style="padding: 14px; font-size: 20px; letter-spacing: 10px;" placeholder="ASSIGN 6 DIGIT PIN" maxlength="6">
                    </div>
                    <button class="mn-btn btn-outline" style="border-color: var(--accent); color: var(--accent); padding: 14px; font-size: 13px;" onclick="adminRegisterUser()">
                        <i class="fas fa-server"></i> REGISTER USER TO CLOUD
                    </button>
                </div>

                <!-- Help Requests Feed -->
                <div class="glass-card" style="border-color: rgba(255, 51, 51, 0.3);">
                    <div class="card-header">
                        <div class="section-title" style="color: var(--danger);"><i class="fas fa-ambulance"></i> Urgent Help Requests</div>
                    </div>
                    <div class="data-list" id="admin-help-list">
                        <div style="text-align:center; padding: 20px; color: #555; font-size: 13px;">No active requests.</div>
                    </div>
                </div>

                <!-- Unified Directory -->
                <div class="glass-card flex-grow" style="border-color: rgba(79, 70, 229, 0.3);">
                    <div class="card-header">
                        <div class="section-title" style="color: #fff;"><i class="fas fa-users"></i> Unified Network Directory</div>
                    </div>
                    <div class="data-list" id="admin-users-list">
                        <div style="text-align:center; padding: 20px; color: #555; font-size: 13px;"><i class="fas fa-circle-notch fa-spin"></i> Merging records...</div>
                    </div>
                </div>
            </div>
        </div>

        <!-- VIEW 3: ADMIN TARGET SESSION (User Details & UTR) -->
        <div id="view-admin-user" class="view-container">
            <div class="view-inner">
                <div style="width: 100%; display: flex; justify-content: space-between; align-items: center; margin-bottom: 25px; background: rgba(0, 229, 255, 0.05); padding: 18px 20px; border-radius: 18px; border: 1px solid rgba(0, 229, 255, 0.3);">
                    <div>
                        <h2 style="font-family: 'Space Grotesk'; font-size: 20px; color: var(--accent); margin-bottom: 4px; font-weight:900;" id="target-name">Target Name</h2>
                        <span style="font-size: 12px; color: var(--gold); font-weight:600;" id="target-phone">Phone</span>
                    </div>
                    <button class="action-icon-btn" onclick="closeAdminUserSession()" style="color:var(--accent); border:1px solid var(--accent); border-radius:12px; width:40px; height:40px; background:rgba(0, 229, 255, 0.1); display:flex; justify-content:center; align-items:center;"><i class="fas fa-arrow-left"></i></button>
                </div>

                <div class="glass-card flex-grow">
                    <div class="card-header">
                        <div class="section-title" style="color: var(--success);"><i class="fas fa-receipt"></i> User Transactions & Uploads</div>
                    </div>
                    <div class="data-list" id="admin-target-receipts-list">
                        <div style="text-align:center; padding: 20px; color: #555; font-size: 13px;"><i class="fas fa-circle-notch fa-spin"></i> Retrieving files...</div>
                    </div>
                </div>
            </div>
        </div>

        <!-- VIEW 4: CLIENT DASHBOARD (MND PAY HOME) -->
        <div id="view-client-home" class="view-container">
            <div class="view-inner">
                <div style="width: 100%; display: flex; justify-content: space-between; align-items: center; margin-bottom: 25px; background: rgba(212, 175, 55, 0.08); padding: 18px 20px; border-radius: 18px; border: 1px solid rgba(212, 175, 55, 0.25);">
                    <div style="overflow: hidden;">
                        <h2 style="font-family: 'Space Grotesk'; font-size: 18px; color: var(--gold); margin-bottom: 4px;">Hi, <span id="client-name-display" style="color: #fff;">User</span></h2>
                        <span style="font-size: 12px; color: var(--text-muted); font-weight:500;">ID: <strong id="client-phone-display" style="color: var(--accent);">--</strong></span>
                    </div>
                    <span id="client-access-badge" style="font-size:10px; padding:6px 10px; border-radius:8px; background:rgba(255,255,255,0.1); border:1px solid rgba(255,255,255,0.2); font-weight:800; letter-spacing:0.5px;">MND PAY</span>
                </div>

                <!-- Initiate Custom MND Secure Gateway -->
                <div class="glass-card" style="border-top: 3px solid var(--gold);">
                    <div class="card-header" style="border-bottom: none; margin-bottom: 5px; padding-bottom: 0;">
                        <div class="section-title"><i class="fas fa-bolt" style="color: var(--gold);"></i> MND Secure Pay</div>
                    </div>
                    <p style="font-size: 12px; color: var(--text-muted); margin-bottom: 20px;">Enter amount to launch our dedicated secure payment gateway.</p>
                    
                    <div class="input-group" style="margin-bottom: 15px;">
                        <i class="fas fa-rupee-sign input-icon" style="color: var(--success); font-size:20px;"></i>
                        <input type="number" id="pay-amount-init" class="mn-input" style="font-size: 26px; font-weight: 800; color: #fff; padding-left: 50px; font-family: 'Space Grotesk';" placeholder="0">
                    </div>
                    <button class="mn-btn btn-gold" onclick="openPaymentGateway()">
                        <i class="fas fa-lock"></i> PROCEED TO SECURE CHECKOUT
                    </button>
                </div>

                <!-- Official Beautiful UPI Cards -->
                <div class="glass-card">
                    <div class="section-title" style="margin-bottom: 18px;"><i class="fas fa-address-card"></i> Official MND UPI Handles</div>
                    <div class="direct-upi-list">
                        <div class="upi-item" onclick="copyText('9771617808@ybl')">
                            <span class="upi-id-text">9771617808@ybl</span>
                            <div class="upi-copy-icon"><i class="far fa-copy"></i></div>
                        </div>
                        <div class="upi-item" onclick="copyText('9771617808-4@ybl')">
                            <span class="upi-id-text">9771617808-4@ybl</span>
                            <div class="upi-copy-icon"><i class="far fa-copy"></i></div>
                        </div>
                        <div class="upi-item" onclick="copyText('lalukumartanti75-1@okaxis')">
                            <span class="upi-id-text">lalukumartanti75-1@okaxis</span>
                            <div class="upi-copy-icon"><i class="far fa-copy"></i></div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- ==========================================
             VIEW 4.1: CUSTOM PAYMENT GATEWAY (Advanced UI)
             ========================================== -->
        <div id="view-payment-gateway" class="view-container">
            <div class="view-inner" style="padding-top: env(safe-area-inset-top); padding-bottom: 40px;">
                <div class="gateway-header">
                    <button class="action-icon-btn" onclick="closePaymentGateway()" style="background:rgba(255,255,255,0.1); border-radius:12px; width:45px; height:45px; color:#fff; display:flex; justify-content:center; align-items:center; border: 1px solid rgba(255,255,255,0.2);"><i class="fas fa-arrow-left"></i></button>
                    <div style="font-family:'Space Grotesk'; font-size:20px; color:#fff; font-weight:800;">MND Secure Gateway</div>
                </div>

                <div class="gateway-amount-box">
                    <div class="gateway-amount-row">
                        <h2 id="gw-amount-display">₹ 0.00</h2>
                        <div style="width:40px; height:40px; background:rgba(0,0,0,0.05); border-radius:10px; display:flex; justify-content:center; align-items:center; cursor:pointer;" onclick="copyText(document.getElementById('gw-amount-display').innerText.replace('₹ ', ''))">
                            <i class="far fa-copy" style="color: #444; font-size: 20px;"></i>
                        </div>
                    </div>
                    <div style="font-size: 13px; color: var(--danger); font-weight:800; display:flex; align-items:center; gap:5px;"><i class="fas fa-stopwatch"></i> Timer: <span id="gw-timer">14:59</span></div>
                </div>

                <div class="gw-section-title"><div class="gw-red-dot"></div> Choose a payment app</div>
                
                <!-- ADVANCED FIXED SVG LOGOS FOR APPS -->
                <div class="gateway-grid">
                    <!-- Google Pay -->
                    <div class="gw-btn gpay" onclick="executeAppIntent('gpay')">
                        <svg class="gw-logo-svg" viewBox="0 0 48 48" xmlns="http://www.w3.org/2000/svg">
                            <path fill="#4285F4" d="M24 9.5c3.1 0 5.8 1.1 8 2.9l6-6C34.3 3.1 29.5 1 24 1 14.8 1 7 6.6 3.1 14.1l7.1 5.5c1.8-5.3 6.7-9.1 13.8-9.1z"/>
                            <path fill="#34A853" d="M46.1 24.5c0-1.5-.1-3-.4-4.5H24v9h12.5c-.5 2.8-2.2 5.2-4.6 6.8l7.3 5.7c4.3-4 6.9-9.9 6.9-17z"/>
                            <path fill="#FBBC05" d="M10.2 28.4c-.5-1.4-.7-2.9-.7-4.4s.3-3 .7-4.4l-7.1-5.5C1.5 17.6 1 20.7 1 24s.5 6.4 1.5 9.3l7.7-4.9z"/>
                            <path fill="#EA4335" d="M24 47c5.9 0 10.9-2 14.5-5.3l-7.3-5.7c-2 1.3-4.5 2.1-7.2 2.1-7.1 0-12-3.8-13.8-9.1l-7.7 4.9C7 41.4 14.8 47 24 47z"/>
                        </svg>
                        <span>Google Pay</span>
                    </div>
                    <!-- PhonePe -->
                    <div class="gw-btn phonepe" onclick="executeAppIntent('phonepe')">
                        <svg class="gw-logo-svg" viewBox="0 0 256 256" xmlns="http://www.w3.org/2000/svg">
                            <rect width="256" height="256" rx="50" fill="#5F259F"/>
                            <path fill="#FFF" d="M164.5 96.5h-50.8v-20.3c0-4.5 3.7-8.2 8.2-8.2h34.4c4.5 0 8.2-3.7 8.2-8.2V43.5c0-4.5-3.7-8.2-8.2-8.2H92.2c-15.8 0-28.7 12.9-28.7 28.7v101.4c0 4.5 3.7 8.2 8.2 8.2h21v35c0 4.5 3.7 8.2 8.2 8.2h16.4c4.5 0 8.2-3.7 8.2-8.2v-35h39.1c11.6 0 21-9.4 21-21v-42.1c0-11.6-9.5-21-21.1-21zm-4.7 42.1H92.7V113h67.1v25.6z"/>
                        </svg>
                        <span>PhonePe</span>
                    </div>
                    <!-- Paytm -->
                    <div class="gw-btn paytm" onclick="executeAppIntent('paytm')">
                        <svg class="gw-logo-svg" viewBox="0 0 256 256" xmlns="http://www.w3.org/2000/svg">
                            <path fill="#00B9F5" d="M128 0C57.3 0 0 57.3 0 128s57.3 128 128 128 128-57.3 128-128S198.7 0 128 0z"/>
                            <path fill="#002E6E" d="M83.5 149.2h-12V107h17.6c11.7 0 18.6 6.8 18.6 17.5 0 11-7.1 17.6-18.6 17.6h-5.6v7.1zm0-15.2h4.5c4.7 0 7.3-2.9 7.3-7.5 0-4.4-2.5-7.3-7.3-7.3h-4.5v14.8z"/>
                            <path fill="#002E6E" d="M127.1 149.2h-5.6V107h12c11.7 0 18.6 6.8 18.6 17.5 0 11-7.1 17.6-18.6 17.6h-6.4v7.1zm0-15.2h5.3c4.7 0 7.3-2.9 7.3-7.5 0-4.4-2.5-7.3-7.3-7.3h-5.3v14.8z"/>
                            <path fill="#002E6E" d="M165.7 124.6l-8.5-17.6h6.4l4.9 10.9 4.9-10.9h6.4l-8.5 17.6v24.6h-5.6v-24.6z"/>
                        </svg>
                        <span>Paytm</span>
                    </div>
                </div>

                <div class="gw-section-title" style="margin-top:10px;"><div class="gw-red-dot"></div> Scan Code Option</div>

                <div class="qr-wrapper">
                    <img id="gw-qr-code" src="" alt="Dynamic QR Code">
                    <p>1. Use another phone to scan this QR code.</p>
                    <p>2. If you scan from gallery, amount might be limited to ₹2000 per transaction.</p>
                </div>

                <div class="gw-section-title"><div class="gw-red-dot"></div> Input UTR / Reference No.</div>
                
                <p style="color: var(--danger); font-size: 13px; font-weight: 800; width: 100%; text-align: left; margin-bottom: 12px; line-height:1.4;">If you do not paste the exact 12-digit UTR, the transaction will 100% fail.</p>
                
                <div class="utr-paste-group">
                    <input type="number" id="gw-utr-input" class="utr-input" placeholder="Input 12 digits here" oninput="checkUtrLength()">
                    <button class="btn-paste" onclick="pasteUTR()">Paste</button>
                </div>
                
                <div style="font-size: 12px; color: var(--text-muted); width: 100%; text-align: left; background:rgba(255,255,255,0.05); padding:15px; border-radius:12px; border:1px solid rgba(255,255,255,0.1);">
                    <strong style="color:#fff;">Important Rules:</strong><br><br>
                    1. Do not reuse the same UTR number twice.<br>
                    2. Take a screenshot of payment success for safety.
                </div>

                <div class="gw-bottom-bar">
                    <button class="btn-gw-cancel" onclick="closePaymentGateway()">CANCEL</button>
                    <button class="btn-gw-submit" id="btn-gw-submit" disabled onclick="submitGatewayUTR()">Submit (Need UTR)</button>
                </div>
            </div>
        </div>

        <!-- VIEW 5: CLIENT UPLOAD (Upload Payment receipt) -->
        <div id="view-client-upload" class="view-container">
            <div class="view-inner">
                <!-- Payment Proof Upload -->
                <div class="glass-card" style="border-color: rgba(16, 185, 129, 0.4); background: rgba(16, 185, 129, 0.05);">
                    <div class="section-title" style="color: var(--success); margin-bottom: 10px;"><i class="fas fa-cloud-upload-alt"></i> Upload Receipt</div>
                    <p style="font-size: 12px; color: #aaa; margin-bottom: 20px;">Upload screenshot, PDF, or video proof for admin verification.</p>
                    
                    <input type="file" id="receipt-file" accept="image/*, application/pdf, video/*, .doc, .docx" style="display: none;" onchange="processFileUpload(event)">
                    <div class="upload-area" style="border-color: rgba(16, 185, 129, 0.5);" onclick="document.getElementById('receipt-file').click()">
                        <i class="fas fa-file-upload upload-icon" style="color: var(--success); font-size:40px; margin-bottom:10px; filter: drop-shadow(0 0 15px rgba(16, 185, 129, 0.5));"></i>
                        <div style="font-size: 16px; font-weight: 700; color: #fff;">Tap to Select File</div>
                        <div style="font-size: 11px; color: #999; margin-top:8px;">Supports: Images, PDF, Video, Word</div>
                        <img id="preview-img" src="" alt="Preview">
                        <i id="preview-file-icon" class="fas fa-file-alt file-icon-preview"></i>
                        <div id="preview-filename" style="font-size:13px; font-weight:600; color:var(--success); margin-top:15px; display:none; word-wrap: break-word;"></div>
                    </div>
                    
                    <div class="input-group" style="margin-top: 18px; margin-bottom: 15px;">
                        <input type="number" id="proof-amount" class="mn-input" placeholder="Amount Paid (₹)" style="font-family: 'Space Grotesk'; font-weight: bold; border-color: rgba(16, 185, 129, 0.5);">
                    </div>
                    <button class="mn-btn btn-success" id="btn-submit-proof" onclick="submitReceiptToCloud()" style="display: none;">
                        <i class="fas fa-check-circle"></i> TRANSMIT TO ADMIN
                    </button>
                </div>

                <!-- Personal Payment History -->
                <div class="glass-card flex-grow">
                    <div class="section-title" style="margin-bottom: 20px;"><i class="fas fa-history"></i> My Transaction Logs</div>
                    <div class="data-list" id="client-history-list">
                        <div style="text-align:center; padding: 20px; color: #555; font-size: 13px;"><i class="fas fa-circle-notch fa-spin"></i> Retrieving logs...</div>
                    </div>
                </div>
            </div>
        </div>

        <!-- VIEW 6: CLIENT HELP (Contact/Support) -->
        <div id="view-client-help" class="view-container">
            <div class="view-inner">
                <div class="glass-card" style="border-top: 4px solid var(--accent); padding: 35px 25px;">
                    <div style="text-align: center; margin-bottom: 30px;">
                        <i class="fas fa-headset" style="font-size: 42px; color: var(--accent); margin-bottom: 15px; filter: drop-shadow(0 0 20px var(--accent-glow));"></i>
                        <h2 style="font-family: 'Space Grotesk'; font-size: 24px; color: #fff; font-weight:900;">Support Center</h2>
                        <p style="font-size: 13px; color: var(--text-muted); margin-top: 8px;">Maa Nirmala DJ Beltikri Service Team</p>
                    </div>

                    <div style="background: rgba(0, 0, 0, 0.6); border: 1px dashed var(--accent); border-radius: 16px; padding: 20px; text-align: center; margin-bottom: 30px;">
                        <i class="fas fa-envelope" style="color: #fff; font-size: 20px; margin-bottom: 12px;"></i>
                        <div style="font-size: 14px; font-weight: 700; color: var(--accent); word-break: break-all;">maa.nirmala.dj.beltikri@gmail.com</div>
                        <p style="font-size: 11px; color: #aaa; margin-top: 8px;">For queries, payments, or issues, email us.</p>
                    </div>

                    <h3 class="section-title" style="font-size: 16px; margin-bottom: 15px; color: var(--gold);"><i class="fas fa-users"></i> Core Executives</h3>
                    <div class="team-grid">
                        <!-- Member 1 -->
                        <div class="team-card">
                            <img src="https://i.postimg.cc/6qbJj3hQ/Screenshot-2026-01-14-15-25-06-57-1c337646f29875672b5a61192b9010f9-2.jpg" class="team-img" alt="Anil Kumar">
                            <div class="team-info">
                                <div class="team-name">Anil Kumar</div>
                                <div class="team-actions">
                                    <a href="tel:+918544341240" class="team-btn btn-call"><i class="fas fa-phone-alt"></i></a>
                                    <a href="https://wa.me/918544341240" target="_blank" class="team-btn btn-wa"><i class="fab fa-whatsapp"></i></a>
                                </div>
                            </div>
                        </div>
                        <!-- Member 2 -->
                        <div class="team-card">
                            <img src="https://i.postimg.cc/7Y7rMx2y/Screenshot-2026-01-14-15-33-01-78-965bbf4d18d205f782c6b8409c5773a4-2.jpg" class="team-img" alt="Sildhar kumar">
                            <div class="team-info">
                                <div class="team-name">Sildhar Kumar</div>
                                <div class="team-actions">
                                    <a href="tel:+917294969938" class="team-btn btn-call"><i class="fas fa-phone-alt"></i></a>
                                    <a href="https://wa.me/917294969938" target="_blank" class="team-btn btn-wa"><i class="fab fa-whatsapp"></i></a>
                                </div>
                            </div>
                        </div>
                        <!-- Member 3 -->
                        <div class="team-card">
                            <img src="https://i.postimg.cc/qMWWzWbF/Screenshot-2026-01-14-15-29-44-90-965bbf4d18d205f782c6b8409c5773a4.jpg" class="team-img" alt="Sanjay kumar">
                            <div class="team-info">
                                <div class="team-name">Sanjay Kumar</div>
                                <div class="team-actions">
                                    <a href="tel:+919153635378" class="team-btn btn-call"><i class="fas fa-phone-alt"></i></a>
                                    <a href="https://wa.me/919153635378" target="_blank" class="team-btn btn-wa"><i class="fab fa-whatsapp"></i></a>
                                </div>
                            </div>
                        </div>
                        <!-- Member 4 -->
                        <div class="team-card">
                            <img src="https://i.postimg.cc/Y0jPr7Vy/20251205-103059-IMG-STYLE.jpg" class="team-img" alt="Lalu kumar">
                            <div class="team-info">
                                <div class="team-name">Lalu Kumar</div>
                                <div class="team-actions">
                                    <a href="tel:+919771617808" class="team-btn btn-call"><i class="fas fa-phone-alt"></i></a>
                                    <a href="https://wa.me/919771617808" target="_blank" class="team-btn btn-wa"><i class="fab fa-whatsapp"></i></a>
                                </div>
                            </div>
                        </div>
                    </div>

                    <button class="mn-btn btn-danger" style="margin-top: 25px; font-size:15px; padding:18px;" onclick="requestUrgentHelp()">
                        <i class="fas fa-ambulance" style="font-size:18px;"></i> URGENT HELP REQUEST
                    </button>
                </div>
            </div>
        </div>

        <!-- VIEW 7: DONATE (Animated Portfolio) -->
        <div id="view-client-donate" class="view-container">
            <div class="view-inner">
                <div class="donate-hero">
                    <i class="fas fa-heart heart-beat" style="font-size: 36px; margin-bottom: 12px;"></i>
                    <h1 class="donate-title">Give Hope</h1>
                    <p class="donate-sub">Your small contribution provides immense support and helps poor families thrive.</p>
                </div>

                <div class="glass-card" style="text-align: center; border-color: rgba(251, 191, 36, 0.4); background: rgba(251, 191, 36, 0.05);">
                    <h2 style="font-family: 'Space Grotesk'; font-size: 20px; color: var(--gold); margin-bottom: 12px; font-weight:800;">Make a Difference</h2>
                    <p style="font-size: 13px; color: var(--text-muted); margin-bottom: 25px; line-height: 1.6;">Every rupee donated directly goes into empowering those who need it most. Join the MND Foundation today.</p>
                    
                    <div class="input-group" style="margin-bottom: 20px;">
                        <i class="fas fa-rupee-sign input-icon" style="color: var(--success); font-size: 20px;"></i>
                        <input type="number" id="donate-amount" class="mn-input" style="font-size: 24px; font-weight: 800; color: #fff; padding-left: 55px; border-color: var(--success);" placeholder="Donation Amount">
                    </div>
                    <button class="mn-btn btn-success" style="font-size: 15px; padding: 18px;" onclick="initiateDonation()">
                        <i class="fas fa-gift" style="font-size: 18px;"></i> DONATE SECURELY
                    </button>
                </div>
                <div style="font-size: 12px; color: #666; text-align: center; margin-top: 15px; padding: 0 20px; line-height:1.5;">
                    <i class="fas fa-shield-check"></i> Transactions are 100% secure. Supported via standard UPI channels.
                </div>
            </div>
        </div>

    </div>

    <!-- ==========================================
         BOTTOM NAVIGATION BAR
         ========================================== -->
    <nav class="bottom-nav" id="main-bottom-nav">
        <div class="b-nav-item active" id="bnav-home" onclick="handleNavClick('home')">
            <i class="fas fa-home"></i>
            <span>Home</span>
        </div>
        <div class="b-nav-item" id="bnav-upload" onclick="handleNavClick('upload')">
            <i class="fas fa-file-upload"></i>
            <span>Upload</span>
        </div>
        <div class="b-nav-item" id="bnav-help" onclick="handleNavClick('help')">
            <i class="fas fa-headset"></i>
            <span>Help</span>
        </div>
        <div class="b-nav-item" id="bnav-donate" onclick="handleNavClick('donate')">
            <i class="fas fa-heart"></i>
            <span>Donate</span>
        </div>
    </nav>

    <!-- ==========================================
         MODALS
         ========================================== -->

    <!-- Image Viewer Modal -->
    <div id="modal-viewer" class="modal-overlay" onclick="closeModal('modal-viewer')">
        <div style="max-width: 95%; max-height: 90vh; position: relative;" onclick="event.stopPropagation()">
            <i class="fas fa-times-circle" style="position: absolute; top: -45px; right: 0; color: #fff; font-size: 32px; cursor: pointer; filter:drop-shadow(0 0 5px rgba(0,0,0,0.8));" onclick="closeModal('modal-viewer')"></i>
            <img id="full-viewer-img" src="" style="width: 100%; height: auto; max-height: 80vh; border-radius: 16px; box-shadow: 0 20px 60px rgba(0,0,0,0.9); border: 2px solid var(--border-light);">
        </div>
    </div>

    <!-- Language Translation Modal -->
    <div id="modal-language" class="modal-overlay" onclick="closeModal('modal-language')">
        <div class="modal-content" style="max-width: 380px;" onclick="event.stopPropagation()">
            <div class="card-header">
                <h3 class="section-title" style="margin:0; color: var(--gold);"><i class="fas fa-language"></i> Select Language</h3>
                <i class="fas fa-times" style="cursor: pointer; color: #888; font-size: 20px; padding:5px;" onclick="closeModal('modal-language')"></i>
            </div>
            <p style="font-size:13px; color:var(--text-muted); text-align:center; margin-bottom:20px;">Translate application to your preferred language.</p>
            
            <div id="google_translate_element"></div>

            <button class="mn-btn btn-outline" style="margin-top: 25px;" onclick="closeModal('modal-language')">DONE</button>
        </div>
    </div>

    <!-- Settings Modal -->
    <div id="modal-settings" class="modal-overlay" onclick="closeModal('modal-settings')">
        <div class="modal-content" onclick="event.stopPropagation()">
            <div class="card-header">
                <h3 class="section-title" style="margin:0; color: #fff;"><i class="fas fa-cog"></i> Settings</h3>
                <i class="fas fa-times" style="cursor: pointer; color: #888; font-size: 20px; padding:5px;" onclick="closeModal('modal-settings')"></i>
            </div>
            
            <div class="setting-row">
                <div class="setting-info"><i class="fas fa-bell"></i> Notifications</div>
                <label class="switch">
                    <input type="checkbox" id="set-notif" checked onchange="togglePref('notif')">
                    <span class="slider"></span>
                </label>
            </div>
            <div class="setting-row">
                <div class="setting-info"><i class="fas fa-volume-up"></i> Sound Effects</div>
                <label class="switch">
                    <input type="checkbox" id="set-sound" checked onchange="togglePref('sound')">
                    <span class="slider"></span>
                </label>
            </div>
            <div class="setting-row" style="margin-bottom: 25px;">
                <div class="setting-info"><i class="fas fa-map-marker-alt"></i> Location Services</div>
                <label class="switch">
                    <input type="checkbox" id="set-loc" checked onchange="togglePref('loc')">
                    <span class="slider"></span>
                </label>
            </div>

            <button class="mn-btn btn-danger" style="font-size:14px; padding: 18px;" onclick="systemLogout()">
                <i class="fas fa-power-off"></i> SECURE LOGOUT
            </button>
        </div>
    </div>

    <!-- ==========================================
         JAVASCRIPT LOGIC
         ========================================== -->
    <script>
        // --- Google Translate Init ---
        function googleTranslateElementInit() {
            new google.translate.TranslateElement({
                pageLanguage: 'en',
                includedLanguages: 'hi,en,bn,te,ta,mr,gu,ur,kn,ml,pa,or',
                layout: google.translate.TranslateElement.InlineLayout.SIMPLE
            }, 'google_translate_element');
        }

        // --- 1. Firebase Initialization ---
        const firebaseConfig = {
            apiKey: "AIzaSyCZP-zuJNDW9S4sD_d4R_-nrTMjf0HD4MM",
            authDomain: "mnd-tracking.firebaseapp.com",
            databaseURL: "https://mnd-tracking-default-rtdb.asia-southeast1.firebasedatabase.app",
            projectId: "mnd-tracking",
            storageBucket: "mnd-tracking.firebasestorage.app"
        };
        if (!firebase.apps.length) { firebase.initializeApp(firebaseConfig); }
        const db = firebase.database();

        // --- 2. Core Config & State ---
        const ADMIN_NUMBERS = ["9771617808", "7294969938", "9153635378", "8544341240"];
        const MASTER_PIN = "121120";
        const MAIN_UPI = "9771617808@ybl";
        
        let sessionUser = null; 
        let currentRole = null; 
        let compressedBase64File = null;
        let uploadFileType = 'image'; // image, pdf, video, doc
        let globalUsersMap = {};
        let currentAdminTargetPhone = "";
        let gatewayAmount = 0;

        // Preferences logic
        function togglePref(pref) {
            const val = document.getElementById(`set-${pref}`).checked;
            localStorage.setItem(`mnd_pref_${pref}`, val);
            showToast(`${pref.toUpperCase()} updated.`);
        }

        // Auto-Login
        window.addEventListener('DOMContentLoaded', () => {
            const savedPhone = localStorage.getItem('mnd_pay_phone');
            const savedPin = localStorage.getItem('mnd_pay_pin');
            if(savedPhone && savedPin) {
                document.getElementById('login-phone').value = savedPhone;
                document.getElementById('login-pin').value = savedPin;
                setTimeout(processAuth, 300);
            }
            // Load prefs
            ['notif', 'sound', 'loc'].forEach(p => {
                const v = localStorage.getItem(`mnd_pref_${p}`);
                if(v !== null) document.getElementById(`set-${p}`).checked = (v === 'true');
            });
        });

        // --- 3. UI & Utility Functions ---
        function showToast(msg, type = 'success') {
            const container = document.getElementById('toast-container');
            const toast = document.createElement('div'); toast.className = `toast ${type}`;
            const icon = type === 'success' ? 'fa-check-circle' : 'fa-exclamation-triangle';
            toast.innerHTML = `<i class="fas ${icon}"></i> <span style="flex-grow:1;">${msg}</span>`;
            container.prepend(toast);
            setTimeout(() => toast.remove(), 4000);
        }

        function toggleMenu() {
            document.getElementById('side-menu').classList.toggle('active');
        }

        function switchView(id) {
            // Hide all
            document.querySelectorAll('.view-container').forEach(el => el.classList.remove('active-view'));
            // Show requested
            const target = document.getElementById(id);
            target.classList.add('active-view');
            target.scrollTop = 0; // Reset scroll position perfectly
            
            const topNav = document.getElementById('main-top-nav');
            const bottomNav = document.getElementById('main-bottom-nav');
            
            if(id === 'view-auth' || id === 'view-payment-gateway') {
                topNav.classList.remove('visible'); bottomNav.classList.remove('visible');
            } else {
                topNav.classList.add('visible'); bottomNav.classList.add('visible');
            }
        }

        function toggleAuthForm(mode) {
            if(mode === 'register') {
                document.getElementById('form-login').style.display = 'none';
                document.getElementById('form-register').style.display = 'block';
            } else {
                document.getElementById('form-register').style.display = 'none';
                document.getElementById('form-login').style.display = 'block';
            }
        }

        function openModal(id) { document.getElementById(id).classList.add('active'); }
        function closeModal(id) { document.getElementById(id).classList.remove('active'); }
        
        function viewFullImage(src) {
            if(src.startsWith('data:application/pdf') || src.startsWith('data:video') || src.startsWith('data:application/msword')) {
                showToast("File preview handled via direct download normally.", "success");
                return;
            }
            document.getElementById('full-viewer-img').src = src;
            openModal('modal-viewer');
        }

        function copyText(txt) {
            const el = document.createElement('textarea');
            el.value = txt;
            document.body.appendChild(el);
            el.select();
            document.execCommand('copy');
            document.body.removeChild(el);
            showToast(`Copied: ${txt}`);
        }

        function escapeHTML(str) {
            if(!str) return '';
            return String(str).replace(/[&<>'"]/g, tag => ({
                '&': '&amp;', '<': '&lt;', '>': '&gt;', "'": '&#39;', '"': '&quot;'
            }[tag] || tag));
        }

        // --- 4. Bottom Navigation Routing ---
        function handleNavClick(tab) {
            document.querySelectorAll('.b-nav-item').forEach(el => el.classList.remove('active'));
            document.getElementById(`bnav-${tab}`).classList.add('active');

            if(currentRole === 'admin') {
                if(tab === 'home') { closeAdminUserSession(); switchView('view-admin'); }
                else { showToast("Global logs visible on Admin Home.", "success"); }
            } else if(currentRole === 'client') {
                if(tab === 'home') switchView('view-client-home');
                else if(tab === 'upload') switchView('view-client-upload');
                else if(tab === 'help') switchView('view-client-help');
                else if(tab === 'donate') switchView('view-client-donate');
            }
        }

        // --- 5. Dual-DB Auth & Self-Reg System ---
        function selfRegisterUser() {
            const name = document.getElementById('reg-name').value.trim();
            const phone = document.getElementById('reg-phone').value.trim();
            const pin = document.getElementById('reg-pin').value.trim();

            if(!name || !phone || !pin) return showToast("All fields required.", "error");
            if(pin.length !== 6) return showToast("PIN must be 6 digits.", "error");

            const userData = {
                name: name, phone: phone, pin: pin,
                registeredAt: Date.now(),
                dateStr: new Date().toLocaleString('en-US', { day:'numeric', month:'short', year:'numeric'}),
                status: 'active'
            };

            db.ref(`mnd_pay_users/${phone}`).once('value').then(snap => {
                if(snap.exists()) return showToast("Number already registered on MND Pay.", "error");
                db.ref(`trackings/${phone}`).once('value').then(snap2 => {
                    if(snap2.exists()) return showToast("Number found in Logistics DB. Just Login.", "error");
                    
                    db.ref(`mnd_pay_users/${phone}`).set(userData).then(() => {
                        showToast("Account Created Successfully!");
                        toggleAuthForm('login');
                        document.getElementById('login-phone').value = phone;
                        document.getElementById('login-pin').value = pin;
                    });
                });
            }).catch(e => showToast("Network Error", "error"));
        }

        function processAuth() {
            const phone = document.getElementById('login-phone').value.trim();
            const pin = document.getElementById('login-pin').value.trim();
            const btn = document.getElementById('btn-login');

            if(!phone || !pin) return showToast("Phone and PIN required.", "error");

            btn.innerHTML = '<i class="fas fa-spinner fa-spin"></i> DECRYPTING...'; btn.disabled = true;

            if(ADMIN_NUMBERS.includes(phone) && pin === MASTER_PIN) {
                localStorage.setItem('mnd_pay_phone', phone); localStorage.setItem('mnd_pay_pin', pin);
                currentRole = 'admin'; sessionUser = { name: "System Admin", phone: phone };
                
                showToast("Admin Protocol Engaged", "success");
                btn.innerHTML = '<i class="fas fa-fingerprint"></i> INITIATE HANDSHAKE'; btn.disabled = false;
                
                handleNavClick('home'); 
                startAdminListeners();
                return;
            }

            const handleSuccess = (userData, source) => {
                if(userData.status === 'suspended') {
                    btn.innerHTML = '<i class="fas fa-fingerprint"></i> INITIATE HANDSHAKE'; btn.disabled = false;
                    throw new Error("ACCOUNT SUSPENDED BY ADMIN.");
                }
                
                localStorage.setItem('mnd_pay_phone', phone); localStorage.setItem('mnd_pay_pin', pin);
                currentRole = 'client'; sessionUser = userData;
                
                document.getElementById('client-name-display').innerText = escapeHTML(userData.name);
                document.getElementById('client-phone-display').innerText = escapeHTML(userData.phone);
                document.getElementById('client-access-badge').innerText = source === 'logistics' ? 'GLOBAL ACCESS' : 'MND PAY ONLY';
                
                showToast(`Welcome back, ${userData.name}`);
                handleNavClick('home');
                startClientListeners();
                btn.innerHTML = '<i class="fas fa-fingerprint"></i> INITIATE HANDSHAKE'; btn.disabled = false;
            };

            db.ref(`mnd_pay_users/${phone}`).once('value').then(snap => {
                if(snap.exists()) {
                    const userData = snap.val();
                    if(userData.pin === pin) handleSuccess(userData, 'pay');
                    else throw new Error("Invalid Security PIN.");
                } else {
                    return db.ref(`trackings/${phone}`).once('value').then(snap2 => {
                        if(snap2.exists()) {
                            const logisticsData = snap2.val();
                            if(logisticsData.pin === pin) handleSuccess(logisticsData, 'logistics');
                            else throw new Error("Invalid Security PIN.");
                        } else {
                            throw new Error("Access Denied. Record not found.");
                        }
                    });
                }
            }).catch(e => {
                showToast(e.message || "Network Error.", "error");
                btn.innerHTML = '<i class="fas fa-fingerprint"></i> INITIATE HANDSHAKE'; btn.disabled = false;
            });
        }

        function systemLogout() {
            localStorage.removeItem('mnd_pay_phone'); localStorage.removeItem('mnd_pay_pin');
            sessionUser = null; currentRole = null;
            db.ref().off(); globalUsersMap = {}; currentAdminTargetPhone = "";
            
            document.getElementById('login-phone').value = ''; document.getElementById('login-pin').value = '';
            
            closeModal('modal-settings');
            switchView('view-auth');
            showToast("Session Terminated Securely.");
        }

        // --- 6. Admin Logic ---
        function adminRegisterUser() {
            const name = document.getElementById('admin-reg-name').value.trim();
            const phone = document.getElementById('admin-reg-phone').value.trim();
            const pin = document.getElementById('admin-reg-pin').value.trim();

            if(!name || !phone || !pin || pin.length !== 6) return showToast("Valid Name, Phone & 6-digit PIN required.", "error");

            const userData = {
                name: name, phone: phone, pin: pin, status: 'active',
                registeredAt: Date.now(), dateStr: new Date().toLocaleString('en-US', { day:'numeric', month:'short', year:'numeric'})
            };

            db.ref(`mnd_pay_users/${phone}`).set(userData).then(() => {
                showToast(`User provisioned to cloud!`);
                document.getElementById('admin-reg-name').value = ''; document.getElementById('admin-reg-phone').value = ''; document.getElementById('admin-reg-pin').value = '';
            }).catch(e => showToast("Permission denied.", "error"));
        }

        function renderAdminDirectory() {
            const list = document.getElementById('admin-users-list');
            const users = Object.values(globalUsersMap);
            
            users.sort((a, b) => {
                const timeA = a.registeredAt || a.timestamp || 0; const timeB = b.registeredAt || b.timestamp || 0;
                return timeB - timeA;
            });

            if(users.length === 0) { list.innerHTML = '<div style="text-align:center; padding: 20px; color: #555;">No users found.</div>'; return; }

            let html = '';
            users.forEach(u => {
                const sourceColor = u._source === 'Logistics DB' ? 'var(--accent)' : 'var(--primary)';
                const isSuspended = u.status === 'suspended';
                const suspendedClass = isSuspended ? 'suspended' : '';
                const suspendedBadge = isSuspended ? `<span class="status-tag tag-danger" style="color:var(--danger); background:rgba(255,51,51,0.1); border:1px solid rgba(255,51,51,0.3);">SUSPENDED</span>` : `<span class="status-tag" style="color: ${sourceColor}; background: ${sourceColor}22; border: 1px solid ${sourceColor}55;">${u._source}</span>`;
                
                html += `
                    <div class="dir-item ${suspendedClass}" style="border-left-color: ${isSuspended ? 'var(--danger)' : sourceColor};" onclick="openAdminUserSession('${u.phone}', '${escapeHTML(u.name)}', '${u._source}')">
                        <div class="dir-info" style="flex-grow:1;">
                            <h4 style="font-family:'Space Grotesk'; font-size:16px; color:#fff; margin-bottom:4px; font-weight:800;">${escapeHTML(u.name)}</h4>
                            <p style="font-size:12px; color:#aaa; font-weight:500;">${escapeHTML(u.phone)} • PIN: <strong style="color:var(--gold); font-family:'Orbitron'; letter-spacing:1px;">${escapeHTML(u.pin)}</strong></p>
                        </div>
                        <div style="display: flex; flex-direction: column; align-items: flex-end; gap: 8px;">
                            ${suspendedBadge}
                        </div>
                    </div>
                `;
            });
            list.innerHTML = html;
        }

        function startAdminListeners() {
            db.ref('mnd_pay_users').on('value', snap => {
                if(snap.exists()) {
                    snap.forEach(child => { globalUsersMap[child.key] = { ...child.val(), _source: 'Pay DB' }; });
                }
                renderAdminDirectory();
            });
            db.ref('trackings').on('value', snap => {
                if(snap.exists()) {
                    snap.forEach(child => {
                        const data = child.val();
                        if(data.phone && data.name && !globalUsersMap[data.phone]) {
                            globalUsersMap[data.phone] = { ...data, _source: 'Logistics DB' };
                        } else if(data.phone && globalUsersMap[data.phone] && data.status === 'suspended') {
                            globalUsersMap[data.phone].status = 'suspended'; 
                        }
                    });
                }
                renderAdminDirectory();
            });

            // Help Requests Listener
            db.ref('mnd_pay_help').on('value', snap => {
                const list = document.getElementById('admin-help-list');
                if(snap.exists()) {
                    let html = ''; const helps = [];
                    snap.forEach(uNode => { const pKey = uNode.key; uNode.forEach(hNode => { helps.push({ phoneKey: pKey, helpKey: hNode.key, ...hNode.val() }); }); });
                    helps.sort((a,b) => b.timestamp - a.timestamp);
                    helps.forEach(h => {
                        html += `
                            <div class="dir-item" style="border-left-color: var(--danger);">
                                <div>
                                    <h4 style="color:var(--danger); font-size:15px; margin-bottom:4px; font-weight:800;"><i class="fas fa-ambulance"></i> URGENT HELP</h4>
                                    <p style="font-size: 12px; color: #ccc; font-weight:500;">${escapeHTML(h.name)} • ${h.phoneKey}</p>
                                </div>
                                <button class="action-icon-btn trash" onclick="adminDeleteHelp('${h.phoneKey}', '${h.helpKey}')"><i class="fas fa-check-circle" style="color:var(--success); font-size:24px;"></i></button>
                            </div>
                        `;
                    });
                    list.innerHTML = html;
                } else { list.innerHTML = '<div style="text-align:center; padding: 20px; color: #555;">No active requests.</div>'; }
            });
        }

        // Admin Target Session
        function openAdminUserSession(phone, name, source) {
            currentAdminTargetPhone = phone;
            document.getElementById('target-name').innerText = escapeHTML(name);
            document.getElementById('target-phone').innerText = phone;
            switchView('view-admin-user');
            
            db.ref(`mnd_pay_receipts/${phone}`).orderByChild('timestamp').on('value', snap => {
                const list = document.getElementById('admin-target-receipts-list');
                if(snap.exists()) {
                    let html = ''; const receipts = [];
                    snap.forEach(child => receipts.push({ key: child.key, ...child.val() }));
                    receipts.reverse().forEach(r => {
                        let statusBadge = ''; let actionArea = '';
                        if(r.status === 'successful') {
                            statusBadge = `<span class="status-tag tag-success"><i class="fas fa-check-circle"></i> SUCCESSFUL</span>`;
                            actionArea = `
                                <div style="margin-top:15px; font-size:13px; color:#fff; background:rgba(0,250,154,0.1); padding:12px 15px; border-radius:12px; border:1px solid rgba(0,250,154,0.3); display:flex; justify-content:space-between; align-items:center;">
                                    <span>UTR: <strong style="font-family:'Space Grotesk'; letter-spacing:1px; font-size:15px;">${escapeHTML(r.utr)}</strong></span>
                                    <i class="fas fa-check" style="color:var(--success); font-size:18px;"></i>
                                </div>
                            `;
                        } else if(r.status === 'rejected') {
                            statusBadge = `<span class="status-tag tag-danger"><i class="fas fa-times-circle"></i> REJECTED</span>`;
                        } else {
                            statusBadge = `<span class="status-tag tag-pending"><i class="fas fa-clock"></i> PENDING</span>`;
                            actionArea = `
                                <div style="display:flex; gap:10px; margin-top:15px;">
                                    <input type="text" id="utr-${r.key}" class="mn-input" style="padding:12px 15px; font-size:14px; font-family:'Space Grotesk';" placeholder="Enter UTR No." value="${r.utr ? r.utr : ''}">
                                    <button class="mn-btn btn-success" style="width:auto; padding:12px 18px; font-size:12px;" onclick="adminApproveReceipt('${phone}', '${r.key}')">APPROVE</button>
                                    <button class="mn-btn btn-danger" style="width:auto; padding:12px 18px; font-size:12px;" onclick="adminRejectReceipt('${phone}', '${r.key}')">REJECT</button>
                                </div>
                            `;
                        }

                        let mediaView = ``;
                        if(r.photo === 'UTR_ONLY') {
                            mediaView = `<div style="width:100%; padding: 25px; background:rgba(0,229,255,0.05); border-radius:14px; border:1px dashed var(--accent); text-align:center; color:var(--accent);">
                                <i class="fas fa-hashtag" style="font-size:32px; margin-bottom:12px; filter:drop-shadow(0 0 10px rgba(0,229,255,0.4));"></i>
                                <div style="font-size:14px; font-weight:700;">Submitted via Fast Gateway</div>
                            </div>`;
                        } else if(r.fileType && r.fileType !== 'image') {
                            mediaView = `<div style="width:100%; height:140px; background:rgba(0,0,0,0.5); border-radius:14px; border:1px dashed var(--gold); display:flex; flex-direction:column; justify-content:center; align-items:center; color:var(--gold);">
                                <i class="fas fa-file-alt" style="font-size:42px; margin-bottom:12px;"></i>
                                <span style="font-size:14px; font-weight:700;">Document/Video File</span>
                                <span style="font-size:11px; color:#888; margin-top:5px; padding:0 10px; text-align:center;">${escapeHTML(r.fileName)}</span>
                            </div>`;
                        } else {
                            mediaView = `<img src="${r.photo}" style="width:100%; height:220px; object-fit:cover; border-radius:14px; border:1px solid rgba(255,255,255,0.15); cursor:pointer;" onclick="viewFullImage('${r.photo}')">`;
                        }

                        html += `
                            <div class="timeline-item">
                                <div style="display:flex; justify-content:space-between; align-items:flex-start; width:100%; margin-bottom:15px;">
                                    <div style="flex-grow:1;">
                                        <div style="display:flex; align-items:center; gap:12px; margin-bottom:6px;">
                                            <h4 style="font-family:'Space Grotesk'; font-size:26px; font-weight:900; color:var(--gold); margin:0;">₹${r.amount}</h4>
                                            ${statusBadge}
                                        </div>
                                        <p style="font-size:12px; color:#aaa; font-weight:500;">Submitted: ${r.dateStr}</p>
                                    </div>
                                    <button class="action-icon-btn trash" style="background:rgba(255,51,51,0.1); border-radius:10px; width:40px; height:40px;" onclick="adminDeleteReceipt('${phone}', '${r.key}')"><i class="fas fa-trash-alt"></i></button>
                                </div>
                                ${mediaView}
                                ${actionArea}
                            </div>
                        `;
                    });
                    list.innerHTML = html;
                } else { list.innerHTML = '<div style="text-align:center; padding: 20px; color: #555;">No uploads found for this user.</div>'; }
            });
        }

        function adminApproveReceipt(phoneKey, receiptKey) {
            const utrInput = document.getElementById(`utr-${receiptKey}`);
            const utrValue = utrInput ? utrInput.value.trim() : '';
            if(!utrValue) return showToast("Please provide the correct UTR number.", "error");

            if(confirm("Verify payment and mark as Successful with UTR: " + utrValue + "?")) {
                db.ref(`mnd_pay_receipts/${phoneKey}/${receiptKey}`).update({
                    status: 'successful', utr: utrValue
                }).then(() => showToast("Payment Approved & UTR Saved!"));
            }
        }
        function adminRejectReceipt(phoneKey, receiptKey) {
            if(confirm("Mark this payment as Rejected?")) {
                db.ref(`mnd_pay_receipts/${phoneKey}/${receiptKey}`).update({
                    status: 'rejected'
                }).then(() => showToast("Payment Rejected."));
            }
        }

        function adminDeleteReceipt(phoneKey, receiptKey) {
            if(confirm("Permanently delete this payment receipt from the system?")) {
                db.ref(`mnd_pay_receipts/${phoneKey}/${receiptKey}`).remove().then(() => showToast("Receipt Deleted."));
            }
        }
        function adminDeleteHelp(phoneKey, helpKey) {
            db.ref(`mnd_pay_help/${phoneKey}/${helpKey}`).remove().then(() => showToast("Help request marked resolved."));
        }

        function closeAdminUserSession() {
            if(currentAdminTargetPhone) db.ref(`mnd_pay_receipts/${currentAdminTargetPhone}`).off();
            currentAdminTargetPhone = ""; switchView('view-admin');
        }

        // --- 7. Client Gateway & Standard Logic ---

        function checkUtrLength() {
            const input = document.getElementById('gw-utr-input');
            const btn = document.getElementById('btn-gw-submit');
            if(input.value.trim().length >= 10) {
                btn.disabled = false; btn.classList.add('active'); btn.innerText = "SUBMIT UTR SECURELY";
            } else {
                btn.disabled = true; btn.classList.remove('active'); btn.innerText = "Submit (Need UTR)";
            }
        }

        function openPaymentGateway() {
            const amount = document.getElementById('pay-amount-init').value;
            if(!amount || amount <= 0) return showToast("Enter a valid payment amount.", "error");
            
            gatewayAmount = amount;
            document.getElementById('gw-amount-display').innerText = `${amount}`;
            
            const upiString = encodeURI(`upi://pay?pa=${MAIN_UPI}&pn=MND Pay&am=${amount}&cu=INR`);
            document.getElementById('gw-qr-code').src = `https://api.qrserver.com/v1/create-qr-code/?size=250x250&data=${upiString}&margin=10`;
            
            document.getElementById('gw-utr-input').value = ''; checkUtrLength();
            
            switchView('view-payment-gateway');
            document.getElementById('pay-amount-init').value = ''; 
        }

        function closePaymentGateway() {
            switchView('view-client-home');
        }

        function executeAppIntent(app) {
            let intentUrl = `upi://pay?pa=${MAIN_UPI}&pn=MND%20Pay&am=${gatewayAmount}&cu=INR`;
            if(app === 'phonepe') intentUrl = `phonepe://pay?pa=${MAIN_UPI}&pn=MND%20Pay&am=${gatewayAmount}&cu=INR`;
            else if(app === 'paytm') intentUrl = `paytmmp://pay?pa=${MAIN_UPI}&pn=MND%20Pay&am=${gatewayAmount}&cu=INR`;
            else if(app === 'gpay') intentUrl = `tez://upi/pay?pa=${MAIN_UPI}&pn=MND%20Pay&am=${gatewayAmount}&cu=INR`;
            
            window.location.href = intentUrl;
        }

        async function pasteUTR() {
            try {
                const text = await navigator.clipboard.readText();
                document.getElementById('gw-utr-input').value = text.trim();
                checkUtrLength();
                showToast("UTR Pasted successfully");
            } catch (err) {
                showToast("Failed to read clipboard. Please type it.", "error");
            }
        }

        function submitGatewayUTR() {
            if(!sessionUser) return;
            const utr = document.getElementById('gw-utr-input').value.trim();
            if(!utr || utr.length < 10) return showToast("Please enter a valid 12-digit UTR number.", "error");

            const btn = document.getElementById('btn-gw-submit');
            btn.innerHTML = '<i class="fas fa-spinner fa-spin"></i>'; btn.disabled = true;

            const payload = {
                name: sessionUser.name, phone: sessionUser.phone, amount: gatewayAmount, 
                photo: 'UTR_ONLY', fileType: 'none', fileName: 'Direct Gateway Submission',
                timestamp: Date.now(), dateStr: new Date().toLocaleString('en-US', { day:'numeric', month:'short', hour:'2-digit', minute:'2-digit'}),
                status: 'pending', utr: utr
            };

            db.ref(`mnd_pay_receipts/${sessionUser.phone}`).push(payload).then(() => {
                showToast("UTR Transmitted! Admin will verify soon.");
                btn.innerHTML = 'SUBMIT UTR SECURELY'; btn.disabled = false;
                handleNavClick('upload'); 
            }).catch(e => {
                showToast("Transmission Failed.", "error");
                btn.innerHTML = 'SUBMIT UTR SECURELY'; btn.disabled = false;
            });
        }

        function initiateDonation() {
            const amount = document.getElementById('donate-amount').value;
            if(!amount || amount <= 0) return showToast("Enter a valid donation amount.", "error");
            window.location.href = `upi://pay?pa=${MAIN_UPI}&pn=Maa%20Nirmala%20DJ&am=${amount}&cu=INR&tn=Maa%20Nirmala%20DJ%20for%20donations`;
            
            if(sessionUser) {
                db.ref(`mnd_pay_donations/${sessionUser.phone}`).push({
                    name: sessionUser.name, phone: sessionUser.phone, amount: amount, timestamp: Date.now(),
                    dateStr: new Date().toLocaleString('en-US', { day:'numeric', month:'short', hour:'2-digit', minute:'2-digit'})
                });
            }
            setTimeout(() => { document.getElementById('donate-amount').value = ''; }, 1000);
        }

        function requestUrgentHelp() {
            if(!sessionUser) return;
            db.ref(`mnd_pay_help/${sessionUser.phone}`).push({
                name: sessionUser.name, phone: sessionUser.phone, timestamp: Date.now(),
                dateStr: new Date().toLocaleString('en-US', { day:'numeric', month:'short', hour:'2-digit', minute:'2-digit'}), status: 'pending'
            }).then(() => showToast('Urgent Help Requested! Admin notified.'));
        }

        function processFileUpload(e) {
            const file = e.target.files[0];
            if(!file) return;

            if(file.size > 5 * 1024 * 1024) {
                showToast("File is too large! Please select under 5MB.", "error");
                e.target.value = ''; return;
            }

            const previewImg = document.getElementById('preview-img');
            const previewIcon = document.getElementById('preview-file-icon');
            const previewName = document.getElementById('preview-filename');
            const reader = new FileReader();
            
            if(file.type.startsWith('image/')) {
                uploadFileType = 'image';
                reader.onload = function(event) {
                    const img = new Image(); img.src = event.target.result;
                    img.onload = function() {
                        const canvas = document.createElement('canvas'); const MAX_WIDTH = 500; let scale = 1;
                        if(img.width > MAX_WIDTH) scale = MAX_WIDTH / img.width;
                        canvas.width = img.width * scale; canvas.height = img.height * scale;
                        const ctx = canvas.getContext('2d'); ctx.drawImage(img, 0, 0, canvas.width, canvas.height);
                        compressedBase64File = canvas.toDataURL('image/jpeg', 0.6);
                        
                        previewIcon.style.display = 'none'; previewName.style.display = 'none';
                        previewImg.src = compressedBase64File; previewImg.style.display = 'block';
                        document.getElementById('btn-submit-proof').style.display = 'flex';
                    }
                };
            } else {
                uploadFileType = 'document';
                if(file.type.startsWith('video/')) uploadFileType = 'video';
                if(file.type === 'application/pdf') uploadFileType = 'pdf';

                reader.onloadend = () => {
                    compressedBase64File = reader.result; 
                    previewImg.style.display = 'none';
                    previewIcon.className = uploadFileType === 'pdf' ? 'fas fa-file-pdf file-icon-preview' : (uploadFileType === 'video' ? 'fas fa-file-video file-icon-preview' : 'fas fa-file-alt file-icon-preview');
                    previewIcon.style.display = 'block';
                    previewName.innerText = file.name; previewName.style.display = 'block';
                    document.getElementById('btn-submit-proof').style.display = 'flex';
                };
            }
            reader.readAsDataURL(file);
        }

        function submitReceiptToCloud() {
            if(!sessionUser) return;
            const amount = document.getElementById('proof-amount').value;
            if(!amount || amount <= 0) return showToast("Enter the amount you paid.", "error");
            if(!compressedBase64File) return showToast("Attach a file first.", "error");

            const btn = document.getElementById('btn-submit-proof');
            btn.innerHTML = '<i class="fas fa-spinner fa-spin"></i> TRANSMITTING...'; btn.disabled = true;

            const payload = {
                name: sessionUser.name, phone: sessionUser.phone, amount: amount, 
                photo: compressedBase64File, fileType: uploadFileType, fileName: document.getElementById('preview-filename').innerText || 'image.jpg',
                timestamp: Date.now(), dateStr: new Date().toLocaleString('en-US', { day:'numeric', month:'short', hour:'2-digit', minute:'2-digit'}),
                status: 'pending', utr: '' 
            };

            db.ref(`mnd_pay_receipts/${sessionUser.phone}`).push(payload).then(() => {
                showToast("Proof Transmitted for Admin Verification!");
                
                document.getElementById('preview-img').style.display = 'none'; document.getElementById('preview-img').src = '';
                document.getElementById('preview-file-icon').style.display = 'none'; document.getElementById('preview-filename').style.display = 'none';
                document.getElementById('proof-amount').value = ''; document.getElementById('receipt-file').value = '';
                
                compressedBase64File = null; uploadFileType = 'image';
                btn.innerHTML = '<i class="fas fa-check-circle"></i> TRANSMIT TO ADMIN'; btn.style.display = 'none'; btn.disabled = false;
            }).catch(e => {
                showToast("Transmission Failed.", "error");
                btn.innerHTML = '<i class="fas fa-check-circle"></i> TRANSMIT TO ADMIN'; btn.disabled = false;
            });
        }

        function startClientListeners() {
            if(!sessionUser) return;
            const list = document.getElementById('client-history-list');
            db.ref(`mnd_pay_receipts/${sessionUser.phone}`).orderByChild('timestamp').on('value', snap => {
                if(snap.exists()) {
                    let html = ''; const myReceipts = [];
                    snap.forEach(child => myReceipts.push(child.val()));
                    myReceipts.reverse().forEach(r => {
                        let statusUI = '';
                        if(r.status === 'successful') {
                            statusUI = `
                                <div style="display:flex; flex-direction:column; align-items:flex-end;">
                                    <span class="status-tag tag-success" style="margin-bottom:6px;"><i class="fas fa-check-circle"></i> VERIFIED</span>
                                    <span style="font-size:11px; color:var(--text-muted); font-weight:600;">UTR: <strong style="color:#fff; font-family:'Space Grotesk'; letter-spacing:1px; font-size:12px;">${escapeHTML(r.utr)}</strong></span>
                                </div>
                            `;
                        } else if(r.status === 'rejected') {
                            statusUI = `<span class="status-tag tag-danger"><i class="fas fa-times-circle"></i> REJECTED</span>`;
                        } else {
                            statusUI = `<span class="status-tag tag-pending"><i class="fas fa-clock"></i> PENDING</span>`;
                        }

                        let mediaIcon = `<i class="fas fa-file-invoice-dollar" style="font-size: 24px;"></i>`;
                        if(r.photo === 'UTR_ONLY') mediaIcon = `<i class="fas fa-hashtag" style="font-size: 24px; color:var(--accent);"></i>`;
                        else if(r.fileType && r.fileType !== 'image') mediaIcon = `<i class="fas fa-file-alt" style="font-size: 24px; color:var(--gold);"></i>`;

                        html += `
                            <div class="timeline-item" style="align-items:center; flex-direction:row; padding: 20px 18px;">
                                <div style="display:flex; gap: 18px; align-items:center;">
                                    <div style="width: 55px; height: 55px; border-radius: 14px; background: rgba(255, 255, 255, 0.05); display: flex; justify-content: center; align-items: center; color: #fff; border: 1px solid rgba(255,255,255,0.15); box-shadow: inset 0 0 10px rgba(255,255,255,0.05);">
                                        ${mediaIcon}
                                    </div>
                                    <div>
                                        <h4 style="margin:0 0 6px 0; font-family:'Space Grotesk'; font-size:22px; font-weight:900; color:var(--gold);">₹${r.amount}</h4>
                                        <p style="margin:0; font-size:11px; font-weight:600; color:#aaa;">${r.dateStr}</p>
                                    </div>
                                </div>
                                ${statusUI}
                            </div>
                        `;
                    });
                    list.innerHTML = html;
                } else { list.innerHTML = '<div style="text-align:center; padding: 20px; color: #555;">No transaction logs found.</div>'; }
            });
        }
    </script>
</body>
</html>
