<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PRESS START - Game Store</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;500;600;700;800;900&family=Rajdhani:wght@300;400;500;600;700&family=Share+Tech+Mono&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary-cyan: #00FFFF;
            --primary-magenta: #FF00FF;
            --primary-gradient: linear-gradient(135deg, #00FFFF 0%, #FF00FF 100%);
            --bg-dark: #000000;
            --bg-card: #0a0a12;
            --text-primary: #ffffff;
            --text-secondary: #8a8a9a;
            --accent-red: #ff4444;
            --glow-cyan: rgba(0, 255, 255, 0.4);
            --glow-magenta: rgba(255, 0, 255, 0.4);
        }
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body { font-family: 'Rajdhani', sans-serif; background: var(--bg-dark); color: var(--text-primary); min-height: 100vh; overflow-x: hidden; }
        .bg-grid { position: fixed; top: 0; left: 0; width: 100%; height: 100%; background-image: linear-gradient(rgba(0, 255, 255, 0.02) 1px, transparent 1px), linear-gradient(90deg, rgba(255, 0, 255, 0.02) 1px, transparent 1px); background-size: 50px 50px; pointer-events: none; z-index: 0; }
        .circuit-lines { position: fixed; top: 0; left: 0; width: 100%; height: 100%; pointer-events: none; z-index: 0; overflow: hidden; }
        .circuit-line { position: absolute; height: 1px; animation: circuit-flow 8s linear infinite; opacity: 0.3; }
        .circuit-line:nth-child(odd) { background: linear-gradient(90deg, transparent, var(--primary-cyan), transparent); }
        .circuit-line:nth-child(even) { background: linear-gradient(90deg, transparent, var(--primary-magenta), transparent); }
        .circuit-line:nth-child(1) { top: 10%; width: 200px; animation-delay: 0s; }
        .circuit-line:nth-child(2) { top: 25%; width: 150px; animation-delay: 2s; }
        .circuit-line:nth-child(3) { top: 45%; width: 250px; animation-delay: 4s; }
        .circuit-line:nth-child(4) { top: 70%; width: 180px; animation-delay: 1s; }
        .circuit-line:nth-child(5) { top: 85%; width: 220px; animation-delay: 3s; }
        @keyframes circuit-flow { 0% { left: -300px; } 100% { left: 100%; } }
        header { position: relative; z-index: 10; padding: 15px 40px; display: flex; align-items: center; justify-content: space-between; border-bottom: 1px solid rgba(0, 255, 255, 0.1); background: linear-gradient(180deg, rgba(0, 0, 0, 0.95) 0%, transparent 100%); }
        .logo-container { display: flex; align-items: center; gap: 15px; }
        .logo-img { height: 60px; width: auto; }
        .logo-text { font-family: 'Orbitron', sans-serif; font-size: 1.3rem; font-weight: 800; letter-spacing: 0.3em; background: var(--primary-gradient); -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text; }
        .nav-links a { display: inline-flex; align-items: center; gap: 8px; font-family: 'Share Tech Mono', monospace; color: var(--primary-cyan); text-decoration: none; font-size: 0.9rem; letter-spacing: 0.1em; transition: all 0.3s ease; padding: 10px 20px; border: 1px solid var(--primary-cyan); border-radius: 4px; }
        .nav-links a:hover { background: var(--primary-gradient); color: var(--bg-dark); box-shadow: 0 0 20px var(--glow-cyan), 0 0 20px var(--glow-magenta); }
        .nav-links a svg { width: 18px; height: 18px; }
        .hero { position: relative; z-index: 5; text-align: center; padding: 50px 20px 30px; }
        .hero-tagline { font-family: 'Orbitron', sans-serif; font-size: 0.9rem; letter-spacing: 0.5em; background: var(--primary-gradient); -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text; margin-bottom: 15px; opacity: 0; animation: fadeInUp 0.8s ease forwards; }
        .hero-title { font-family: 'Orbitron', sans-serif; font-size: clamp(1.5rem, 4vw, 2.5rem); font-weight: 300; color: var(--text-primary); margin-bottom: 10px; opacity: 0; animation: fadeInUp 0.8s ease 0.2s forwards; }
        .hero-subtitle { font-size: 1.1rem; color: var(--text-secondary); opacity: 0; animation: fadeInUp 0.8s ease 0.4s forwards; }
        @keyframes fadeInUp { from { opacity: 0; transform: translateY(20px); } to { opacity: 1; transform: translateY(0); } }
        main { position: relative; z-index: 5; max-width: 1000px; margin: 0 auto; padding: 40px 20px 80px; }
        .section-header { display: flex; align-items: center; gap: 15px; margin-bottom: 30px; }
        .section-line { flex: 1; height: 1px; background: linear-gradient(90deg, var(--primary-cyan), transparent); }
        .section-line:last-child { background: linear-gradient(90deg, transparent, var(--primary-magenta)); }
        .section-title { font-family: 'Orbitron', sans-serif; font-size: 0.85rem; letter-spacing: 0.3em; background: var(--primary-gradient); -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text; }
        .bundles-grid { display: flex; flex-direction: column; gap: 20px; }
        .bundle-card { background: var(--bg-card); border: 1px solid rgba(0, 255, 255, 0.1); border-radius: 12px; overflow: hidden; transition: all 0.3s ease; }
        .bundle-card:hover { border-color: rgba(0, 255, 255, 0.3); box-shadow: 0 0 30px rgba(0, 255, 255, 0.1), 0 0 30px rgba(255, 0, 255, 0.1); }
        .bundle-preview { display: flex; gap: 20px; padding: 20px; cursor: pointer; align-items: center; }
        .bundle-images { display: flex; gap: 8px; flex-shrink: 0; }
        .bundle-images img { width: 120px; height: 56px; object-fit: cover; border-radius: 6px; border: 1px solid rgba(255, 255, 255, 0.1); transition: transform 0.3s ease; }
        .bundle-card:hover .bundle-images img { transform: scale(1.02); }
        .bundle-info { flex: 1; min-width: 0; }
        .bundle-header { display: flex; align-items: center; gap: 12px; margin-bottom: 8px; flex-wrap: wrap; }
        .bundle-title { font-family: 'Orbitron', sans-serif; font-size: 1.1rem; font-weight: 700; color: var(--text-primary); letter-spacing: 0.05em; }
        .bundle-badge { font-family: 'Share Tech Mono', monospace; font-size: 0.7rem; padding: 3px 8px; background: var(--primary-gradient); color: var(--bg-dark); border-radius: 3px; font-weight: 600; }
        .bundle-desc { font-size: 0.85rem; color: var(--text-secondary); line-height: 1.4; margin-bottom: 10px; display: -webkit-box; -webkit-line-clamp: 2; -webkit-box-orient: vertical; overflow: hidden; }
        .bundle-meta { display: flex; align-items: center; gap: 15px; flex-wrap: wrap; }
        .bundle-price { font-family: 'Orbitron', sans-serif; font-size: 1.3rem; font-weight: 700; background: var(--primary-gradient); -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text; }
        .expand-btn { display: inline-flex; align-items: center; gap: 6px; font-family: 'Share Tech Mono', monospace; font-size: 0.75rem; color: var(--primary-cyan); background: transparent; border: 1px solid rgba(0, 255, 255, 0.3); padding: 6px 12px; border-radius: 4px; cursor: pointer; transition: all 0.3s ease; letter-spacing: 0.05em; }
        .expand-btn:hover { background: rgba(0, 255, 255, 0.1); border-color: var(--primary-cyan); }
        .expand-btn svg { transition: transform 0.3s ease; }
        .bundle-card.expanded .expand-btn svg { transform: rotate(180deg); }
        .bundle-details { max-height: 0; overflow: hidden; transition: max-height 0.5s ease; background: rgba(0, 0, 0, 0.3); }
        .bundle-card.expanded .bundle-details { max-height: 1000px; }
        .details-content { padding: 20px; border-top: 1px solid rgba(0, 255, 255, 0.1); }
        .bundle-contents { margin-bottom: 20px; }
        .bundle-label { font-family: 'Share Tech Mono', monospace; font-size: 0.7rem; color: var(--primary-cyan); letter-spacing: 0.1em; margin-bottom: 10px; }
        .bundle-games { display: flex; flex-wrap: wrap; gap: 10px; }
        .bundle-game-item { display: flex; align-items: center; gap: 8px; padding: 8px 12px; background: rgba(0, 255, 255, 0.05); border: 1px solid rgba(0, 255, 255, 0.1); border-radius: 6px; font-size: 0.85rem; }
        .info-tabs { display: flex; gap: 10px; margin-bottom: 15px; flex-wrap: wrap; }
        .info-tab { font-family: 'Share Tech Mono', monospace; font-size: 0.7rem; padding: 8px 16px; background: transparent; border: 1px solid rgba(255, 255, 255, 0.1); color: var(--text-secondary); cursor: pointer; transition: all 0.3s ease; border-radius: 4px; letter-spacing: 0.05em; }
        .info-tab:hover { border-color: rgba(0, 255, 255, 0.3); color: var(--primary-cyan); }
        .info-tab.active { background: var(--primary-gradient); border-color: transparent; color: var(--bg-dark); }
        .info-content { display: none; background: rgba(0, 0, 0, 0.3); border-radius: 8px; padding: 15px; margin-bottom: 20px; }
        .info-content.active { display: block; }
        .game-specs-title { font-family: 'Orbitron', sans-serif; font-size: 0.85rem; background: var(--primary-gradient); -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text; margin-bottom: 10px; margin-top: 15px; }
        .game-specs-title:first-child { margin-top: 0; }
        .spec-row { display: flex; justify-content: space-between; padding: 8px 0; border-bottom: 1px solid rgba(255, 255, 255, 0.05); font-size: 0.85rem; }
        .spec-label { color: var(--text-secondary); font-family: 'Share Tech Mono', monospace; font-size: 0.75rem; }
        .spec-value { color: var(--text-primary); text-align: right; }
        .age-rating { display: flex; align-items: center; gap: 15px; flex-wrap: wrap; }
        .age-badge { font-family: 'Orbitron', sans-serif; font-size: 1.2rem; font-weight: 700; padding: 10px 15px; background: var(--accent-red); color: white; border-radius: 6px; }
        .age-text { font-size: 0.85rem; color: var(--text-secondary); line-height: 1.4; }
        .buy-section { display: flex; justify-content: flex-end; }
        .buy-btn { display: inline-flex; align-items: center; gap: 10px; font-family: 'Orbitron', sans-serif; font-size: 0.9rem; font-weight: 600; padding: 12px 24px; background: var(--primary-gradient); color: var(--bg-dark); text-decoration: none; border-radius: 6px; transition: all 0.3s ease; letter-spacing: 0.05em; }
        .buy-btn:hover { transform: translateY(-2px); box-shadow: 0 10px 30px var(--glow-cyan), 0 10px 30px var(--glow-magenta); }
        footer { position: relative; z-index: 5; text-align: center; padding: 40px 20px; border-top: 1px solid rgba(0, 255, 255, 0.1); background: linear-gradient(0deg, rgba(0, 0, 0, 0.95) 0%, transparent 100%); }
        .footer-logo { font-family: 'Orbitron', sans-serif; font-size: 1rem; letter-spacing: 0.3em; background: var(--primary-gradient); -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text; margin-bottom: 10px; }
        .footer-tagline { font-size: 0.9rem; color: var(--text-secondary); font-style: italic; margin-bottom: 15px; }
        .footer-mission { font-size: 0.8rem; color: var(--text-secondary); opacity: 0.6; }
        @media (max-width: 768px) {
            header { padding: 15px 20px; flex-direction: column; gap: 15px; }
            .logo-img { height: 50px; }
            .logo-text { font-size: 1rem; }
            .bundle-preview { flex-direction: column; align-items: flex-start; }
            .bundle-images { width: 100%; justify-content: center; flex-wrap: wrap; }
            .bundle-images img { width: calc(33% - 6px); max-width: 120px; }
        }
        ::-webkit-scrollbar { width: 8px; }
        ::-webkit-scrollbar-track { background: var(--bg-dark); }
        ::-webkit-scrollbar-thumb { background: linear-gradient(180deg, var(--primary-cyan), var(--primary-magenta)); border-radius: 4px; }
    </style>
</head>
<body>
    <div class="bg-grid"></div>
    <div class="circuit-lines">
        <div class="circuit-line"></div>
        <div class="circuit-line"></div>
        <div class="circuit-line"></div>
        <div class="circuit-line"></div>
        <div class="circuit-line"></div>
    </div>

    <header>
        <div class="logo-container">
            <span class="logo-text">PRESS START</span>
        </div>
        <nav class="nav-links">
            <a href="https://www.facebook.com/profile.php?id=61587333490339" target="_blank">
                <svg viewBox="0 0 24 24" fill="currentColor"><path d="M22 12c0-5.52-4.48-10-10-10S2 6.48 2 12c0 4.84 3.44 8.87 8 9.8V15H8v-3h2V9.5C10 7.57 11.57 6 13.5 6H16v3h-2c-.55 0-1 .45-1 1v2h3v3h-3v6.95c5.05-.5 9-4.76 9-9.95z"/></svg>
                VISIT OUR PAGE
            </a>
        </nav>
    </header>

    <section class="hero">
        <p class="hero-tagline">GAME STORE</p>
        <h1 class="hero-title">Premium Game Bundles for Everyone</h1>
    </section>

    <main>
        <div class="section-header">
            <div class="section-line"></div>
            <h2 class="section-title">AVAILABLE BUNDLES</h2>
            <div class="section-line"></div>
        </div>

        <div class="bundles-grid">
            <!-- The Last of Us Bundle -->
            <article class="bundle-card" id="tlou-bundle">
                <div class="bundle-preview" onclick="toggleBundle('tlou-bundle')">
                    <div class="bundle-images">
                        <img src="https://cdn.cloudflare.steamstatic.com/steam/apps/1888930/header.jpg" alt="The Last of Us Part I">
                        <img src="https://cdn.cloudflare.steamstatic.com/steam/apps/2531310/header.jpg" alt="The Last of Us Part II">
                    </div>
                    <div class="bundle-info">
                        <div class="bundle-header">
                            <h3 class="bundle-title">THE LAST OF US BUNDLE</h3>
                            <span class="bundle-badge">2 GAMES</span>
                        </div>
                        <p class="bundle-desc">Experience the complete story of Joel and Ellie. Two critically acclaimed masterpieces that redefined narrative gaming.</p>
                        <div class="bundle-meta">
                            <span class="bundle-price">₱50</span>
                            <button class="expand-btn">VIEW DETAILS <svg width="12" height="12" viewBox="0 0 24 24" fill="currentColor"><path d="M7.41 8.59L12 13.17l4.59-4.58L18 10l-6 6-6-6 1.41-1.41z"/></svg></button>
                        </div>
                    </div>
                </div>
                <div class="bundle-details">
                    <div class="details-content">
                        <div class="bundle-contents">
                            <p class="bundle-label">INCLUDED IN BUNDLE</p>
                            <div class="bundle-games">
                                <div class="bundle-game-item"><span>📀 The Last of Us Part I (PC)</span></div>
                                <div class="bundle-game-item"><span>📀 The Last of Us Part II Remastered (PC)</span></div>
                            </div>
                        </div>
                        <div class="info-tabs">
                            <button class="info-tab active" onclick="switchTab(event, 'tlou-specs')">SYSTEM REQUIREMENTS</button>
                            <button class="info-tab" onclick="switchTab(event, 'tlou-age')">AGE RATING</button>
                        </div>
                        <div id="tlou-specs" class="info-content active">
                            <p class="game-specs-title">The Last of Us Part I:</p>
                            <div class="spec-row"><span class="spec-label">CPU</span><span class="spec-value">Ryzen 5 1500X / i7-4770K</span></div>
                            <div class="spec-row"><span class="spec-label">RAM</span><span class="spec-value">16 GB</span></div>
                            <div class="spec-row"><span class="spec-label">GPU</span><span class="spec-value">RX 470 / GTX 970 (4GB)</span></div>
                            <div class="spec-row"><span class="spec-label">Storage</span><span class="spec-value">100 GB</span></div>
                            <div class="spec-row"><span class="spec-label">OS</span><span class="spec-value">Windows 10</span></div>
                            <p class="game-specs-title">The Last of Us Part II Remastered:</p>
                            <div class="spec-row"><span class="spec-label">CPU</span><span class="spec-value">i5-8600 / Ryzen 5 3600</span></div>
                            <div class="spec-row"><span class="spec-label">RAM</span><span class="spec-value">16 GB</span></div>
                            <div class="spec-row"><span class="spec-label">GPU</span><span class="spec-value">RTX 3060 / RX 5700</span></div>
                            <div class="spec-row"><span class="spec-label">Storage</span><span class="spec-value">150 GB (SSD)</span></div>
                            <div class="spec-row"><span class="spec-label">OS</span><span class="spec-value">Windows 10 / 11</span></div>
                        </div>
                        <div id="tlou-age" class="info-content">
                            <div class="age-rating">
                                <span class="age-badge">18+</span>
                                <span class="age-text">Mature Content: Intense Violence, Blood and Gore, Strong Language, Sexual Content</span>
                            </div>
                        </div>
                        <div class="buy-section">
                            <a href="https://www.facebook.com/profile.php?id=61587333490339" target="_blank" class="buy-btn">
                                <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor"><path d="M7 18c-1.1 0-1.99.9-1.99 2S5.9 22 7 22s2-.9 2-2-.9-2-2-2zM1 2v2h2l3.6 7.59-1.35 2.45c-.16.28-.25.61-.25.96 0 1.1.9 2 2 2h12v-2H7.42c-.14 0-.25-.11-.25-.25l.03-.12.9-1.63h7.45c.75 0 1.41-.41 1.75-1.03l3.58-6.49c.08-.14.12-.31.12-.48 0-.55-.45-1-1-1H5.21l-.94-2H1zm16 16c-1.1 0-1.99.9-1.99 2s.89 2 1.99 2 2-.9 2-2-.9-2-2-2z"/></svg>
                                BUY NOW - ₱50
                            </a>
                        </div>
                    </div>
                </div>
            </article>

            <!-- Silent Hill Bundle -->
            <article class="bundle-card" id="sh-bundle">
                <div class="bundle-preview" onclick="toggleBundle('sh-bundle')">
                    <div class="bundle-images">
                        <img src="https://cdn.cloudflare.steamstatic.com/steam/apps/2124490/header.jpg" alt="Silent Hill 2 Remake">
                        <img src="https://media.rawg.io/media/screenshots/8b2/8b243945a439d181d8736e785064e01d.jpg" alt="Silent Hill f">
                    </div>
                    <div class="bundle-info">
                        <div class="bundle-header">
                            <h3 class="bundle-title">SILENT HILL BUNDLE</h3>
                            <span class="bundle-badge">2 GAMES</span>
                        </div>
                        <p class="bundle-desc">Two nightmares. One bundle. Silent Hill 2 Remake and Silent Hill f. Written by Ryukishi07, music by Akira Yamaoka.</p>
                        <div class="bundle-meta">
                            <span class="bundle-price">₱50</span>
                            <button class="expand-btn">VIEW DETAILS <svg width="12" height="12" viewBox="0 0 24 24" fill="currentColor"><path d="M7.41 8.59L12 13.17l4.59-4.58L18 10l-6 6-6-6 1.41-1.41z"/></svg></button>
                        </div>
                    </div>
                </div>
                <div class="bundle-details">
                    <div class="details-content">
                        <div class="bundle-contents">
                            <p class="bundle-label">INCLUDED IN BUNDLE</p>
                            <div class="bundle-games">
                                <div class="bundle-game-item"><span>📀 Silent Hill 2 Remake</span></div>
                                <div class="bundle-game-item"><span>📀 Silent Hill f</span></div>
                            </div>
                        </div>
                        <div class="info-tabs">
                            <button class="info-tab active" onclick="switchTab(event, 'sh-specs')">SYSTEM REQUIREMENTS</button>
                            <button class="info-tab" onclick="switchTab(event, 'sh-age')">AGE RATING</button>
                        </div>
                        <div id="sh-specs" class="info-content active">
                            <p class="game-specs-title">Silent Hill 2 Remake:</p>
                            <div class="spec-row"><span class="spec-label">CPU</span><span class="spec-value">i7-6700K / Ryzen 5 3600</span></div>
                            <div class="spec-row"><span class="spec-label">RAM</span><span class="spec-value">16 GB</span></div>
                            <div class="spec-row"><span class="spec-label">GPU</span><span class="spec-value">GTX 1070 Ti / RX 5700</span></div>
                            <div class="spec-row"><span class="spec-label">Storage</span><span class="spec-value">50 GB</span></div>
                            <div class="spec-row"><span class="spec-label">OS</span><span class="spec-value">Windows 10</span></div>
                            <p class="game-specs-title">Silent Hill f:</p>
                            <div class="spec-row"><span class="spec-label">CPU</span><span class="spec-value">i5-8400 / Ryzen 5 2600</span></div>
                            <div class="spec-row"><span class="spec-label">RAM</span><span class="spec-value">16 GB</span></div>
                            <div class="spec-row"><span class="spec-label">GPU</span><span class="spec-value">GTX 1070 Ti / RX 5700</span></div>
                            <div class="spec-row"><span class="spec-label">Storage</span><span class="spec-value">50 GB (SSD)</span></div>
                            <div class="spec-row"><span class="spec-label">OS</span><span class="spec-value">Windows 11</span></div>
                        </div>
                        <div id="sh-age" class="info-content">
                            <div class="age-rating">
                                <span class="age-badge">18+</span>
                                <span class="age-text">Mature Content: Psychological Horror, Violence, Disturbing Imagery, Blood and Gore</span>
                            </div>
                        </div>
                        <div class="buy-section">
                            <a href="https://www.facebook.com/profile.php?id=61587333490339" target="_blank" class="buy-btn">
                                <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor"><path d="M7 18c-1.1 0-1.99.9-1.99 2S5.9 22 7 22s2-.9 2-2-.9-2-2-2zM1 2v2h2l3.6 7.59-1.35 2.45c-.16.28-.25.61-.25.96 0 1.1.9 2 2 2h12v-2H7.42c-.14 0-.25-.11-.25-.25l.03-.12.9-1.63h7.45c.75 0 1.41-.41 1.75-1.03l3.58-6.49c.08-.14.12-.31.12-.48 0-.55-.45-1-1-1H5.21l-.94-2H1zm16 16c-1.1 0-1.99.9-1.99 2s.89 2 1.99 2 2-.9 2-2-.9-2-2-2z"/></svg>
                                BUY NOW - ₱50
                            </a>
                        </div>
                    </div>
                </div>
            </article>

            <!-- Resident Evil Remake Bundle -->
            <article class="bundle-card" id="re-bundle">
                <div class="bundle-preview" onclick="toggleBundle('re-bundle')">
                    <div class="bundle-images">
                        <img src="https://cdn.cloudflare.steamstatic.com/steam/apps/883710/header.jpg" alt="Resident Evil 2 Remake">
                        <img src="https://cdn.cloudflare.steamstatic.com/steam/apps/952060/header.jpg" alt="Resident Evil 3 Remake">
                        <img src="https://cdn.cloudflare.steamstatic.com/steam/apps/2050650/header.jpg" alt="Resident Evil 4 Remake">
                    </div>
                    <div class="bundle-info">
                        <div class="bundle-header">
                            <h3 class="bundle-title">RESIDENT EVIL REMAKE BUNDLE</h3>
                            <span class="bundle-badge">3 GAMES</span>
                        </div>
                        <p class="bundle-desc">The ultimate survival horror collection. Three legendary remakes featuring Leon, Claire, Jill, and Carlos. Fight through Raccoon City and beyond.</p>
                        <div class="bundle-meta">
                            <span class="bundle-price">₱50</span>
                            <button class="expand-btn">VIEW DETAILS <svg width="12" height="12" viewBox="0 0 24 24" fill="currentColor"><path d="M7.41 8.59L12 13.17l4.59-4.58L18 10l-6 6-6-6 1.41-1.41z"/></svg></button>
                        </div>
                    </div>
                </div>
                <div class="bundle-details">
                    <div class="details-content">
                        <div class="bundle-contents">
                            <p class="bundle-label">INCLUDED IN BUNDLE</p>
                            <div class="bundle-games">
                                <div class="bundle-game-item"><span>📀 Resident Evil 2 Remake</span></div>
                                <div class="bundle-game-item"><span>📀 Resident Evil 3 Remake</span></div>
                                <div class="bundle-game-item"><span>📀 Resident Evil 4 Remake</span></div>
                            </div>
                        </div>
                        <div class="info-tabs">
                            <button class="info-tab active" onclick="switchTab(event, 're-specs')">SYSTEM REQUIREMENTS</button>
                            <button class="info-tab" onclick="switchTab(event, 're-age')">AGE RATING</button>
                        </div>
                        <div id="re-specs" class="info-content active">
                            <p class="game-specs-title">Resident Evil 2 Remake:</p>
                            <div class="spec-row"><span class="spec-label">CPU</span><span class="spec-value">i5-4460 / AMD FX-6300</span></div>
                            <div class="spec-row"><span class="spec-label">RAM</span><span class="spec-value">8 GB</span></div>
                            <div class="spec-row"><span class="spec-label">GPU</span><span class="spec-value">GTX 960 / RX 460</span></div>
                            <div class="spec-row"><span class="spec-label">Storage</span><span class="spec-value">26 GB</span></div>
                            <div class="spec-row"><span class="spec-label">OS</span><span class="spec-value">Windows 10 / 11</span></div>
                            <p class="game-specs-title">Resident Evil 3 Remake:</p>
                            <div class="spec-row"><span class="spec-label">CPU</span><span class="spec-value">i5-4460 / AMD FX-6300</span></div>
                            <div class="spec-row"><span class="spec-label">RAM</span><span class="spec-value">8 GB</span></div>
                            <div class="spec-row"><span class="spec-label">GPU</span><span class="spec-value">GTX 960 / RX 460</span></div>
                            <div class="spec-row"><span class="spec-label">Storage</span><span class="spec-value">45 GB</span></div>
                            <div class="spec-row"><span class="spec-label">OS</span><span class="spec-value">Windows 10 / 11</span></div>
                            <p class="game-specs-title">Resident Evil 4 Remake:</p>
                            <div class="spec-row"><span class="spec-label">CPU</span><span class="spec-value">i5-7500 / Ryzen 3 1200</span></div>
                            <div class="spec-row"><span class="spec-label">RAM</span><span class="spec-value">8 GB</span></div>
                            <div class="spec-row"><span class="spec-label">GPU</span><span class="spec-value">GTX 1050 Ti / RX 560 (4GB)</span></div>
                            <div class="spec-row"><span class="spec-label">Storage</span><span class="spec-value">68 GB (SSD Recommended)</span></div>
                            <div class="spec-row"><span class="spec-label">OS</span><span class="spec-value">Windows 10 / 11</span></div>
                        </div>
                        <div id="re-age" class="info-content">
                            <div class="age-rating">
                                <span class="age-badge">18+</span>
                                <span class="age-text">Mature Content: Intense Violence, Blood and Gore, Strong Language</span>
                            </div>
                        </div>
                        <div class="buy-section">
                            <a href="https://www.facebook.com/profile.php?id=61587333490339" target="_blank" class="buy-btn">
                                <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor"><path d="M7 18c-1.1 0-1.99.9-1.99 2S5.9 22 7 22s2-.9 2-2-.9-2-2-2zM1 2v2h2l3.6 7.59-1.35 2.45c-.16.28-.25.61-.25.96 0 1.1.9 2 2 2h12v-2H7.42c-.14 0-.25-.11-.25-.25l.03-.12.9-1.63h7.45c.75 0 1.41-.41 1.75-1.03l3.58-6.49c.08-.14.12-.31.12-.48 0-.55-.45-1-1-1H5.21l-.94-2H1zm16 16c-1.1 0-1.99.9-1.99 2s.89 2 1.99 2 2-.9 2-2-.9-2-2-2z"/></svg>
                                BUY NOW - ₱50
                            </a>
                        </div>
                    </div>
                </div>
            </article>
        </div>
    </main>

    <footer>
        <p class="footer-logo">▶ P R E S S  S T A R T</p>
        <p class="footer-tagline">Because everyone deserves to press start.</p>
        <div class="footer-mission"><p>Gaming changed our lives. Now we're making sure everyone gets the chance to play.</p></div>
    </footer>

    <script>
        function toggleBundle(bundleId) { document.getElementById(bundleId).classList.toggle('expanded'); }
        function switchTab(event, contentId) {
            event.stopPropagation();
            const card = event.target.closest('.bundle-card');
            card.querySelectorAll('.info-tab').forEach(tab => tab.classList.remove('active'));
            card.querySelectorAll('.info-content').forEach(content => content.classList.remove('active'));
            event.target.classList.add('active');
            document.getElementById(contentId).classList.add('active');
        }
        document.addEventListener('DOMContentLoaded', () => {
            document.querySelectorAll('.bundle-card').forEach((card, index) => {
                card.style.opacity = '0';
                card.style.transform = 'translateY(20px)';
                setTimeout(() => {
                    card.style.transition = 'all 0.5s ease';
                    card.style.opacity = '1';
                    card.style.transform = 'translateY(0)';
                }, 400 + (index * 150));
            });
        });
    </script>
</body>
</html>
