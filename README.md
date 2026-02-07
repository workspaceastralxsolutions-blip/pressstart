<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>▶ P R E S S  S T A R T - Game Store</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;500;600;700;800;900&family=Rajdhani:wght@300;400;500;600;700&family=Share+Tech+Mono&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary: #FFD700;
            --primary-dark: #B8860B;
            --bg-dark: #0a0a0f;
            --bg-card: #12121a;
            --bg-card-hover: #1a1a25;
            --text-primary: #ffffff;
            --text-secondary: #8a8a9a;
            --accent-red: #ff4444;
            --accent-green: #44ff88;
            --glow: rgba(255, 215, 0, 0.3);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Rajdhani', sans-serif;
            background: var(--bg-dark);
            color: var(--text-primary);
            min-height: 100vh;
            overflow-x: hidden;
        }

        /* Animated background */
        .bg-grid {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: 
                linear-gradient(rgba(255, 215, 0, 0.03) 1px, transparent 1px),
                linear-gradient(90deg, rgba(255, 215, 0, 0.03) 1px, transparent 1px);
            background-size: 50px 50px;
            pointer-events: none;
            z-index: 0;
        }

        .circuit-lines {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 0;
            overflow: hidden;
        }

        .circuit-line {
            position: absolute;
            background: linear-gradient(90deg, transparent, var(--primary), transparent);
            height: 1px;
            animation: circuit-flow 8s linear infinite;
            opacity: 0.2;
        }

        .circuit-line:nth-child(1) { top: 10%; width: 200px; animation-delay: 0s; }
        .circuit-line:nth-child(2) { top: 25%; width: 150px; animation-delay: 2s; }
        .circuit-line:nth-child(3) { top: 45%; width: 250px; animation-delay: 4s; }
        .circuit-line:nth-child(4) { top: 70%; width: 180px; animation-delay: 1s; }
        .circuit-line:nth-child(5) { top: 85%; width: 220px; animation-delay: 3s; }

        @keyframes circuit-flow {
            0% { left: -300px; }
            100% { left: 100%; }
        }

        /* Header */
        header {
            position: relative;
            z-index: 10;
            padding: 20px 40px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            border-bottom: 1px solid rgba(255, 215, 0, 0.1);
            background: linear-gradient(180deg, rgba(10, 10, 15, 0.95) 0%, transparent 100%);
        }

        .logo-text {
            font-family: 'Orbitron', sans-serif;
            font-size: 1.5rem;
            font-weight: 800;
            letter-spacing: 0.3em;
            color: var(--primary);
            text-shadow: 0 0 20px var(--glow);
        }

        .nav-links a {
            display: inline-flex;
            align-items: center;
            gap: 8px;
            font-family: 'Share Tech Mono', monospace;
            color: var(--primary);
            text-decoration: none;
            font-size: 0.9rem;
            letter-spacing: 0.1em;
            transition: all 0.3s ease;
            padding: 10px 20px;
            border: 1px solid var(--primary);
            border-radius: 4px;
        }

        .nav-links a:hover {
            background: var(--primary);
            color: var(--bg-dark);
            box-shadow: 0 0 20px var(--glow);
        }

        .nav-links a svg {
            width: 18px;
            height: 18px;
        }

        /* Hero Section */
        .hero {
            position: relative;
            z-index: 5;
            text-align: center;
            padding: 60px 20px 40px;
        }

        .hero-tagline {
            font-family: 'Orbitron', sans-serif;
            font-size: 0.9rem;
            letter-spacing: 0.5em;
            color: var(--primary);
            margin-bottom: 15px;
            opacity: 0;
            animation: fadeInUp 0.8s ease forwards;
        }

        .hero-title {
            font-family: 'Orbitron', sans-serif;
            font-size: clamp(1.5rem, 4vw, 2.5rem);
            font-weight: 300;
            color: var(--text-primary);
            margin-bottom: 10px;
            opacity: 0;
            animation: fadeInUp 0.8s ease 0.2s forwards;
        }

        .hero-subtitle {
            font-size: 1.1rem;
            color: var(--text-secondary);
            opacity: 0;
            animation: fadeInUp 0.8s ease 0.4s forwards;
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* Main Content */
        main {
            position: relative;
            z-index: 5;
            max-width: 1000px;
            margin: 0 auto;
            padding: 40px 20px 80px;
        }

        .section-header {
            display: flex;
            align-items: center;
            gap: 15px;
            margin-bottom: 30px;
        }

        .section-title {
            font-family: 'Orbitron', sans-serif;
            font-size: 1.3rem;
            font-weight: 600;
            letter-spacing: 0.2em;
            color: var(--primary);
        }

        .section-line {
            flex: 1;
            height: 1px;
            background: linear-gradient(90deg, var(--primary), transparent);
        }

        /* Compact Bundle Cards */
        .bundles-container {
            display: flex;
            flex-direction: column;
            gap: 20px;
        }

        .bundle-card {
            background: var(--bg-card);
            border: 1px solid rgba(255, 215, 0, 0.1);
            border-radius: 8px;
            overflow: hidden;
            transition: all 0.4s ease;
        }

        .bundle-card:hover {
            border-color: rgba(255, 215, 0, 0.3);
        }

        .bundle-card.expanded {
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.5), 0 0 40px var(--glow);
        }

        /* Bundle Preview (Always Visible) */
        .bundle-preview {
            display: flex;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .bundle-preview:hover {
            background: var(--bg-card-hover);
        }

        .bundle-images {
            display: flex;
            flex-shrink: 0;
            width: 200px;
            height: 120px;
            overflow: hidden;
        }

        .bundle-images img {
            width: 50%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.4s ease;
        }

        .bundle-images.single img {
            width: 100%;
        }

        .bundle-preview:hover .bundle-images img {
            transform: scale(1.05);
        }

        .bundle-info {
            flex: 1;
            padding: 15px 20px;
            display: flex;
            flex-direction: column;
            justify-content: center;
        }

        .bundle-header {
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin-bottom: 8px;
        }

        .bundle-title {
            font-family: 'Orbitron', sans-serif;
            font-size: 1.1rem;
            font-weight: 700;
            color: var(--text-primary);
        }

        .bundle-badge {
            background: var(--primary);
            color: var(--bg-dark);
            font-family: 'Orbitron', sans-serif;
            font-size: 0.65rem;
            font-weight: 700;
            padding: 4px 10px;
            border-radius: 3px;
            letter-spacing: 0.1em;
        }

        .bundle-desc {
            color: var(--text-secondary);
            font-size: 0.85rem;
            line-height: 1.5;
            display: -webkit-box;
            -webkit-line-clamp: 2;
            -webkit-box-orient: vertical;
            overflow: hidden;
        }

        .bundle-meta {
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin-top: 10px;
        }

        .bundle-price {
            font-family: 'Orbitron', sans-serif;
            font-size: 1.3rem;
            font-weight: 800;
            color: var(--accent-green);
        }

        .expand-btn {
            display: flex;
            align-items: center;
            gap: 5px;
            font-family: 'Share Tech Mono', monospace;
            font-size: 0.75rem;
            color: var(--primary);
            background: none;
            border: none;
            cursor: pointer;
            letter-spacing: 0.1em;
        }

        .expand-btn svg {
            transition: transform 0.3s ease;
        }

        .bundle-card.expanded .expand-btn svg {
            transform: rotate(180deg);
        }

        /* Bundle Details (Expandable) */
        .bundle-details {
            max-height: 0;
            overflow: hidden;
            transition: max-height 0.5s ease;
            border-top: 1px solid rgba(255, 215, 0, 0);
        }

        .bundle-card.expanded .bundle-details {
            max-height: 1000px;
            border-top-color: rgba(255, 215, 0, 0.1);
        }

        .details-content {
            padding: 25px;
        }

        /* Games in Bundle */
        .bundle-contents {
            background: rgba(0, 0, 0, 0.3);
            border-radius: 6px;
            padding: 15px;
            margin-bottom: 20px;
        }

        .bundle-label {
            font-family: 'Share Tech Mono', monospace;
            font-size: 0.75rem;
            color: var(--primary);
            letter-spacing: 0.2em;
            margin-bottom: 10px;
        }

        .bundle-games {
            display: flex;
            flex-direction: column;
            gap: 8px;
        }

        .bundle-game-item {
            display: flex;
            align-items: center;
            gap: 10px;
            padding: 8px;
            background: rgba(255, 215, 0, 0.05);
            border-radius: 4px;
            border-left: 2px solid var(--primary);
        }

        .bundle-game-item span {
            font-size: 0.9rem;
        }

        /* Info Tabs */
        .info-tabs {
            display: flex;
            gap: 5px;
            margin-bottom: 15px;
            border-bottom: 1px solid rgba(255, 215, 0, 0.1);
        }

        .info-tab {
            padding: 10px 15px;
            background: transparent;
            border: none;
            color: var(--text-secondary);
            font-family: 'Share Tech Mono', monospace;
            font-size: 0.8rem;
            cursor: pointer;
            transition: all 0.3s ease;
            position: relative;
        }

        .info-tab.active {
            color: var(--primary);
        }

        .info-tab::after {
            content: '';
            position: absolute;
            bottom: -1px;
            left: 0;
            width: 100%;
            height: 2px;
            background: var(--primary);
            transform: scaleX(0);
            transition: transform 0.3s ease;
        }

        .info-tab.active::after {
            transform: scaleX(1);
        }

        .info-content {
            display: none;
            padding: 15px;
            background: rgba(0, 0, 0, 0.2);
            border-radius: 6px;
            font-size: 0.85rem;
            line-height: 1.8;
        }

        .info-content.active {
            display: block;
        }

        .spec-row {
            display: flex;
            justify-content: space-between;
            padding: 8px 0;
            border-bottom: 1px solid rgba(255, 255, 255, 0.05);
        }

        .spec-label {
            color: var(--text-secondary);
        }

        .spec-value {
            color: var(--text-primary);
            text-align: right;
        }

        .game-specs-title {
            color: var(--primary);
            margin: 15px 0 10px;
            font-weight: 600;
        }

        .game-specs-title:first-child {
            margin-top: 0;
        }

        .age-rating {
            display: inline-flex;
            align-items: center;
            gap: 10px;
            padding: 10px 15px;
            background: rgba(255, 68, 68, 0.1);
            border: 1px solid var(--accent-red);
            border-radius: 4px;
            margin-top: 10px;
        }

        .age-badge {
            font-family: 'Orbitron', sans-serif;
            font-size: 1.2rem;
            font-weight: 700;
            color: var(--accent-red);
        }

        .age-text {
            font-size: 0.8rem;
            color: var(--text-secondary);
        }

        /* Buy Button */
        .buy-section {
            display: flex;
            align-items: center;
            justify-content: flex-end;
            padding-top: 20px;
            border-top: 1px solid rgba(255, 215, 0, 0.1);
            margin-top: 20px;
        }

        .buy-btn {
            display: inline-flex;
            align-items: center;
            gap: 10px;
            padding: 15px 35px;
            background: linear-gradient(135deg, var(--primary) 0%, var(--primary-dark) 100%);
            color: var(--bg-dark);
            font-family: 'Orbitron', sans-serif;
            font-size: 0.9rem;
            font-weight: 700;
            letter-spacing: 0.1em;
            text-decoration: none;
            border-radius: 4px;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .buy-btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.3), transparent);
            transition: left 0.5s ease;
        }

        .buy-btn:hover {
            transform: scale(1.05);
            box-shadow: 0 0 30px var(--glow);
        }

        .buy-btn:hover::before {
            left: 100%;
        }

        /* Footer */
        footer {
            position: relative;
            z-index: 5;
            text-align: center;
            padding: 40px 20px;
            border-top: 1px solid rgba(255, 215, 0, 0.1);
            background: linear-gradient(180deg, transparent 0%, rgba(10, 10, 15, 0.95) 100%);
        }

        .footer-logo {
            font-family: 'Orbitron', sans-serif;
            font-size: 1rem;
            letter-spacing: 0.3em;
            color: var(--primary);
            margin-bottom: 10px;
        }

        .footer-tagline {
            color: var(--text-secondary);
            font-size: 0.9rem;
            font-style: italic;
        }

        .footer-mission {
            margin-top: 15px;
            padding: 15px 25px;
            background: rgba(255, 215, 0, 0.05);
            border-radius: 6px;
            display: inline-block;
        }

        .footer-mission p {
            font-size: 0.85rem;
            color: var(--text-secondary);
        }

        /* Scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
        }

        ::-webkit-scrollbar-track {
            background: var(--bg-dark);
        }

        ::-webkit-scrollbar-thumb {
            background: var(--primary-dark);
            border-radius: 4px;
        }

        ::-webkit-scrollbar-thumb:hover {
            background: var(--primary);
        }

        /* Responsive */
        @media (max-width: 768px) {
            header {
                flex-direction: column;
                gap: 20px;
                padding: 20px;
            }

            .bundle-preview {
                flex-direction: column;
            }

            .bundle-images {
                width: 100%;
                height: 150px;
            }

            .bundle-info {
                padding: 15px;
            }

            .bundle-title {
                font-size: 1rem;
            }

            .logo-text {
                font-size: 1.2rem;
                letter-spacing: 0.2em;
            }
        }
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
        <span class="logo-text">▶ P R E S S  S T A R T</span>
        <nav class="nav-links">
            <a href="https://www.facebook.com/profile.php?id=61587333490339" target="_blank">
                <svg viewBox="0 0 24 24" fill="currentColor">
                    <path d="M24 12.073c0-6.627-5.373-12-12-12s-12 5.373-12 12c0 5.99 4.388 10.954 10.125 11.854v-8.385H7.078v-3.47h3.047V9.43c0-3.007 1.792-4.669 4.533-4.669 1.312 0 2.686.235 2.686.235v2.953H15.83c-1.491 0-1.956.925-1.956 1.874v2.25h3.328l-.532 3.47h-2.796v8.385C19.612 23.027 24 18.062 24 12.073z"/>
                </svg>
                VISIT OUR PAGE
            </a>
        </nav>
    </header>

    <section class="hero">
        <p class="hero-tagline">FREE GAMES FOR THOSE WHO NEED THEM</p>
        <h1 class="hero-title">Not everyone can afford to play.</h1>
        <p class="hero-subtitle">We're here to change that. 🎮</p>
    </section>

    <main>
        <div class="section-header">
            <h2 class="section-title">AVAILABLE BUNDLES</h2>
            <div class="section-line"></div>
        </div>

        <div class="bundles-container">
            <!-- The Last of Us Bundle -->
            <article class="bundle-card" id="tlou-bundle">
                <div class="bundle-preview" onclick="toggleBundle('tlou-bundle')">
                    <div class="bundle-images">
                        <img src="https://image.api.playstation.com/vulcan/ap/rnd/202206/0720/eEczyEMDd2BLa3dtkGJVE9Id.png" alt="The Last of Us Part I">
                        <img src="https://image.api.playstation.com/vulcan/ap/rnd/202311/1717/4d7d199a6abee400cdfd7925f59661a37fbc3083bc44f0f4.png" alt="The Last of Us Part II">
                    </div>
                    <div class="bundle-info">
                        <div class="bundle-header">
                            <h3 class="bundle-title">THE LAST OF US BUNDLE</h3>
                            <span class="bundle-badge">2 GAMES</span>
                        </div>
                        <p class="bundle-desc">Experience the complete post-apocalyptic saga. Follow Joel and Ellie's emotional journey through a fungal-infected America, then continue with Ellie's harrowing tale of survival and revenge in the critically acclaimed sequel.</p>
                        <div class="bundle-meta">
                            <span class="bundle-price">₱50</span>
                            <button class="expand-btn">
                                VIEW DETAILS
                                <svg width="12" height="12" viewBox="0 0 24 24" fill="currentColor">
                                    <path d="M7.41 8.59L12 13.17l4.59-4.58L18 10l-6 6-6-6 1.41-1.41z"/>
                                </svg>
                            </button>
                        </div>
                    </div>
                </div>

                <div class="bundle-details">
                    <div class="details-content">
                        <div class="bundle-contents">
                            <p class="bundle-label">INCLUDED IN BUNDLE</p>
                            <div class="bundle-games">
                                <div class="bundle-game-item">
                                    <span>📀 The Last of Us Part I (PC)</span>
                                </div>
                                <div class="bundle-game-item">
                                    <span>📀 The Last of Us Part II Remastered (PC)</span>
                                </div>
                            </div>
                        </div>

                        <div class="info-tabs">
                            <button class="info-tab active" onclick="switchTab(event, 'tlou-specs')">SYSTEM REQUIREMENTS</button>
                            <button class="info-tab" onclick="switchTab(event, 'tlou-age')">AGE RATING</button>
                        </div>

                        <div id="tlou-specs" class="info-content active">
                            <p class="game-specs-title">The Last of Us Part I:</p>
                            <div class="spec-row">
                                <span class="spec-label">CPU</span>
                                <span class="spec-value">Ryzen 5 1500X / i7-4770K</span>
                            </div>
                            <div class="spec-row">
                                <span class="spec-label">RAM</span>
                                <span class="spec-value">16 GB</span>
                            </div>
                            <div class="spec-row">
                                <span class="spec-label">GPU</span>
                                <span class="spec-value">RX 470 / GTX 970 (4GB)</span>
                            </div>
                            <div class="spec-row">
                                <span class="spec-label">Storage</span>
                                <span class="spec-value">100 GB</span>
                            </div>
                            <div class="spec-row" style="border-bottom: none;">
                                <span class="spec-label">OS</span>
                                <span class="spec-value">Windows 10</span>
                            </div>

                            <p class="game-specs-title">The Last of Us Part II Remastered:</p>
                            <div class="spec-row">
                                <span class="spec-label">CPU</span>
                                <span class="spec-value">i5-8600 / Ryzen 5 3600</span>
                            </div>
                            <div class="spec-row">
                                <span class="spec-label">RAM</span>
                                <span class="spec-value">16 GB</span>
                            </div>
                            <div class="spec-row">
                                <span class="spec-label">GPU</span>
                                <span class="spec-value">RTX 3060 / RX 5700</span>
                            </div>
                            <div class="spec-row">
                                <span class="spec-label">Storage</span>
                                <span class="spec-value">150 GB (SSD)</span>
                            </div>
                            <div class="spec-row">
                                <span class="spec-label">OS</span>
                                <span class="spec-value">Windows 10 / 11</span>
                            </div>
                        </div>

                        <div id="tlou-age" class="info-content">
                            <div class="age-rating">
                                <span class="age-badge">18+</span>
                                <span class="age-text">Mature Content: Intense Violence, Blood and Gore, Strong Language, Sexual Content</span>
                            </div>
                        </div>

                        <div class="buy-section">
                            <a href="https://www.facebook.com/profile.php?id=61587333490339" target="_blank" class="buy-btn">
                                <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
                                    <path d="M7 18c-1.1 0-1.99.9-1.99 2S5.9 22 7 22s2-.9 2-2-.9-2-2-2zM1 2v2h2l3.6 7.59-1.35 2.45c-.16.28-.25.61-.25.96 0 1.1.9 2 2 2h12v-2H7.42c-.14 0-.25-.11-.25-.25l.03-.12.9-1.63h7.45c.75 0 1.41-.41 1.75-1.03l3.58-6.49c.08-.14.12-.31.12-.48 0-.55-.45-1-1-1H5.21l-.94-2H1zm16 16c-1.1 0-1.99.9-1.99 2s.89 2 1.99 2 2-.9 2-2-.9-2-2-2z"/>
                                </svg>
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
                        <img src="https://image.api.playstation.com/vulcan/ap/rnd/202408/2010/b448dd24da1ec4cd67c9f51ec718b93eaff3b2d103f9c687.jpg" alt="Silent Hill 2 Remake">
                        <img src="https://assets-prd.ignimgs.com/2022/10/19/silent-hill-f-blogroll-1666210193498.jpg" alt="Silent Hill f">
                    </div>
                    <div class="bundle-info">
                        <div class="bundle-header">
                            <h3 class="bundle-title">SILENT HILL BUNDLE</h3>
                            <span class="bundle-badge">2 GAMES</span>
                        </div>
                        <p class="bundle-desc">Two nightmares. One bundle. Experience the legendary psychological horror with Silent Hill 2 Remake and the brand new Silent Hill f set in 1960s Japan. Written by Ryukishi07, with music by Akira Yamaoka.</p>
                        <div class="bundle-meta">
                            <span class="bundle-price">₱50</span>
                            <button class="expand-btn">
                                VIEW DETAILS
                                <svg width="12" height="12" viewBox="0 0 24 24" fill="currentColor">
                                    <path d="M7.41 8.59L12 13.17l4.59-4.58L18 10l-6 6-6-6 1.41-1.41z"/>
                                </svg>
                            </button>
                        </div>
                    </div>
                </div>

                <div class="bundle-details">
                    <div class="details-content">
                        <div class="bundle-contents">
                            <p class="bundle-label">INCLUDED IN BUNDLE</p>
                            <div class="bundle-games">
                                <div class="bundle-game-item">
                                    <span>📀 Silent Hill 2 Remake</span>
                                </div>
                                <div class="bundle-game-item">
                                    <span>📀 Silent Hill f</span>
                                </div>
                            </div>
                        </div>

                        <div class="info-tabs">
                            <button class="info-tab active" onclick="switchTab(event, 'sh-specs')">SYSTEM REQUIREMENTS</button>
                            <button class="info-tab" onclick="switchTab(event, 'sh-age')">AGE RATING</button>
                        </div>

                        <div id="sh-specs" class="info-content active">
                            <p class="game-specs-title">Silent Hill 2 Remake:</p>
                            <div class="spec-row">
                                <span class="spec-label">CPU</span>
                                <span class="spec-value">i7-6700K / Ryzen 5 3600</span>
                            </div>
                            <div class="spec-row">
                                <span class="spec-label">RAM</span>
                                <span class="spec-value">16 GB</span>
                            </div>
                            <div class="spec-row">
                                <span class="spec-label">GPU</span>
                                <span class="spec-value">GTX 1070 Ti / RX 5700</span>
                            </div>
                            <div class="spec-row">
                                <span class="spec-label">Storage</span>
                                <span class="spec-value">50 GB</span>
                            </div>
                            <div class="spec-row" style="border-bottom: none;">
                                <span class="spec-label">OS</span>
                                <span class="spec-value">Windows 10</span>
                            </div>

                            <p class="game-specs-title">Silent Hill f:</p>
                            <div class="spec-row">
                                <span class="spec-label">CPU</span>
                                <span class="spec-value">i5-8400 / Ryzen 5 2600</span>
                            </div>
                            <div class="spec-row">
                                <span class="spec-label">RAM</span>
                                <span class="spec-value">16 GB</span>
                            </div>
                            <div class="spec-row">
                                <span class="spec-label">GPU</span>
                                <span class="spec-value">GTX 1070 Ti / RX 5700</span>
                            </div>
                            <div class="spec-row">
                                <span class="spec-label">Storage</span>
                                <span class="spec-value">50 GB (SSD Recommended)</span>
                            </div>
                            <div class="spec-row">
                                <span class="spec-label">OS</span>
                                <span class="spec-value">Windows 11</span>
                            </div>
                        </div>

                        <div id="sh-age" class="info-content">
                            <div class="age-rating">
                                <span class="age-badge">18+</span>
                                <span class="age-text">Mature Content: Psychological Horror, Violence, Disturbing Imagery, Blood and Gore</span>
                            </div>
                        </div>

                        <div class="buy-section">
                            <a href="https://www.facebook.com/profile.php?id=61587333490339" target="_blank" class="buy-btn">
                                <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
                                    <path d="M7 18c-1.1 0-1.99.9-1.99 2S5.9 22 7 22s2-.9 2-2-.9-2-2-2zM1 2v2h2l3.6 7.59-1.35 2.45c-.16.28-.25.61-.25.96 0 1.1.9 2 2 2h12v-2H7.42c-.14 0-.25-.11-.25-.25l.03-.12.9-1.63h7.45c.75 0 1.41-.41 1.75-1.03l3.58-6.49c.08-.14.12-.31.12-.48 0-.55-.45-1-1-1H5.21l-.94-2H1zm16 16c-1.1 0-1.99.9-1.99 2s.89 2 1.99 2 2-.9 2-2-.9-2-2-2z"/>
                                </svg>
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
        <div class="footer-mission">
            <p>Gaming changed our lives. Now we're making sure everyone gets the chance to play.</p>
        </div>
    </footer>

    <script>
        function toggleBundle(bundleId) {
            const bundle = document.getElementById(bundleId);
            bundle.classList.toggle('expanded');
        }

        function switchTab(event, contentId) {
            event.stopPropagation();
            
            // Get the parent card
            const card = event.target.closest('.bundle-card');
            
            // Remove active class from all tabs in this card
            const tabs = card.querySelectorAll('.info-tab');
            tabs.forEach(tab => tab.classList.remove('active'));
            
            // Hide all content in this card
            const contents = card.querySelectorAll('.info-content');
            contents.forEach(content => content.classList.remove('active'));
            
            // Add active class to clicked tab
            event.target.classList.add('active');
            
            // Show corresponding content
            document.getElementById(contentId).classList.add('active');
        }

        // Add staggered animation to cards on load
        document.addEventListener('DOMContentLoaded', () => {
            const cards = document.querySelectorAll('.bundle-card');
            cards.forEach((card, index) => {
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
