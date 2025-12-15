<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ella's Blog | Life, Tech & Design</title>
    
    <!-- Google Fonts: 햅번 스타일의 우아함(Playfair)과 가독성(Noto Sans) -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+KR:wght@300;400;500;700&family=Playfair+Display:ital,wght@0,400;0,700;1,400&display=swap" rel="stylesheet">
    
    <!-- FontAwesome for Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

    <style>
        /* * =========================================
         * CSS VARIABLES & RESET
         * =========================================
         */
        :root {
            --bg-color: #FAFAFA;
            --text-main: #2C2C2C;
            --text-light: #666666;
            --accent-color: #2C3E50; /* 딥 네이비 */
            --point-color: #D4A5A5;  /* 앤틱 로즈 (햅번 스타일 포인트) */
            --card-bg: #FFFFFF;
            --border-color: #EAEAEA;
            --shadow-sm: 0 4px 6px rgba(0,0,0,0.02);
            --shadow-md: 0 10px 15px rgba(0,0,0,0.05);
            --font-serif: 'Playfair Display', serif;
            --font-sans: 'Noto Sans KR', sans-serif;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: var(--font-sans);
            background-color: var(--bg-color);
            color: var(--text-main);
            line-height: 1.6;
            transition: background-color 0.3s ease;
        }

        a { text-decoration: none; color: inherit; transition: color 0.3s; }
        ul { list-style: none; }
        img { max-width: 100%; display: block; }
        button { border: none; background: none; cursor: pointer; font-family: inherit; }

        /* * =========================================
         * LAYOUT & HEADER
         * =========================================
         */
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        header {
            position: sticky;
            top: 0;
            z-index: 1000;
            background-color: rgba(250, 250, 250, 0.95);
            backdrop-filter: blur(10px);
            border-bottom: 1px solid var(--border-color);
            padding: 1rem 0;
        }

        .nav-wrapper {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-family: var(--font-serif);
            font-size: 1.8rem;
            font-weight: 700;
            letter-spacing: -0.5px;
            color: var(--text-main);
        }

        .logo span { color: var(--point-color); }

        /* Desktop Navigation */
        .gnb {
            display: flex;
            gap: 2rem;
        }

        .gnb button {
            font-size: 0.95rem;
            font-weight: 500;
            color: var(--text-light);
            position: relative;
        }

        .gnb button:hover, .gnb button.active {
            color: var(--text-main);
        }

        .gnb button.active::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 100%;
            height: 2px;
            background-color: var(--point-color);
        }

        /* Mobile Menu Button */
        .mobile-menu-btn {
            display: none;
            font-size: 1.5rem;
            color: var(--text-main);
        }

        /* * =========================================
         * HERO / FEATURED SECTION
         * =========================================
         */
        .hero-section {
            padding: 4rem 0;
            animation: fadeIn 0.8s ease-out;
        }

        .featured-post {
            display: grid;
            grid-template-columns: 1.2fr 0.8fr;
            gap: 3rem;
            align-items: center;
            background: var(--card-bg);
            border-radius: 12px;
            overflow: hidden;
            box-shadow: var(--shadow-md);
        }

        .featured-img-container {
            height: 400px;
            overflow: hidden;
        }

        .featured-img-container img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.5s ease;
        }

        .featured-post:hover .featured-img-container img {
            transform: scale(1.05);
        }

        .featured-content {
            padding: 2.5rem;
            padding-left: 0;
        }

        .tag {
            display: inline-block;
            padding: 4px 12px;
            background-color: var(--text-main);
            color: white;
            font-size: 0.75rem;
            border-radius: 20px;
            margin-bottom: 1rem;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .featured-title {
            font-family: var(--font-serif);
            font-size: 2.5rem;
            margin-bottom: 1rem;
            line-height: 1.2;
        }

        .featured-excerpt {
            color: var(--text-light);
            margin-bottom: 1.5rem;
            font-size: 1rem;
        }

        .read-more {
            display: inline-flex;
            align-items: center;
            font-weight: 600;
            color: var(--accent-color);
            border-bottom: 1px solid transparent;
        }

        .read-more:hover {
            border-bottom-color: var(--accent-color);
        }

        /* * =========================================
         * GRID SECTION (Posts)
         * =========================================
         */
        .grid-section {
            padding: 2rem 0 5rem;
        }

        .section-title {
            font-family: var(--font-serif);
            font-size: 2rem;
            margin-bottom: 2rem;
            text-align: center;
            position: relative;
        }

        .section-title::after {
            content: '';
            display: block;
            width: 40px;
            height: 3px;
            background-color: var(--point-color);
            margin: 10px auto 0;
        }

        .post-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr); /* Desktop: 3 columns */
            gap: 2rem;
        }

        .post-card {
            background: var(--card-bg);
            border-radius: 8px;
            overflow: hidden;
            box-shadow: var(--shadow-sm);
            transition: transform 0.3s, box-shadow 0.3s;
            cursor: pointer;
        }

        .post-card:hover {
            transform: translateY(-5px);
            box-shadow: var(--shadow-md);
        }

        .card-img {
            height: 200px;
            background-color: #eee;
            position: relative;
            overflow: hidden;
        }
        
        .card-img img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .card-body {
            padding: 1.5rem;
        }

        .card-category {
            font-size: 0.8rem;
            color: var(--point-color);
            font-weight: 600;
            margin-bottom: 0.5rem;
            text-transform: uppercase;
        }

        .card-title {
            font-family: var(--font-serif);
            font-size: 1.25rem;
            margin-bottom: 0.8rem;
            line-height: 1.3;
        }

        .card-desc {
            font-size: 0.9rem;
            color: var(--text-light);
            display: -webkit-box;
            -webkit-line-clamp: 2;
            -webkit-box-orient: vertical;
            overflow: hidden;
            margin-bottom: 1rem;
        }

        .card-meta {
            font-size: 0.8rem;
            color: #999;
            border-top: 1px solid #f0f0f0;
            padding-top: 1rem;
            display: flex;
            justify-content: space-between;
        }

        /* * =========================================
         * ABOUT SECTION (Hidden by default)
         * =========================================
         */
        #about-view {
            display: none;
            padding: 4rem 0;
            animation: fadeIn 0.5s;
            text-align: center;
        }

        .about-card {
            max-width: 800px;
            margin: 0 auto;
            background: white;
            padding: 4rem 2rem;
            border-radius: 12px;
            box-shadow: var(--shadow-md);
        }

        .profile-img {
            width: 180px;
            height: 180px;
            border-radius: 50%;
            object-fit: cover;
            margin: 0 auto 2rem;
            border: 4px solid var(--bg-color);
            box-shadow: 0 8px 16px rgba(0,0,0,0.1);
        }

        .about-name {
            font-family: var(--font-serif);
            font-size: 2.5rem;
            margin-bottom: 1rem;
        }

        .about-bio {
            font-size: 1.1rem;
            color: var(--text-light);
            max-width: 600px;
            margin: 0 auto 2rem;
            line-height: 1.8;
        }

        .social-links a {
            font-size: 1.5rem;
            margin: 0 10px;
            color: var(--text-main);
        }
        
        .social-links a:hover {
            color: var(--point-color);
        }

        /* * =========================================
         * FOOTER
         * =========================================
         */
        footer {
            background-color: #222;
            color: #fff;
            padding: 3rem 0;
            margin-top: auto;
        }

        .footer-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .footer-logo {
            font-family: var(--font-serif);
            font-size: 1.5rem;
        }

        .footer-info p {
            font-size: 0.9rem;
            color: #aaa;
            margin-bottom: 0.5rem;
        }

        /* * =========================================
         * RESPONSIVE BREAKPOINTS
         * =========================================
         */
        
        /* Tablet & Mobile (Max 1024px) */
        @media (max-width: 1024px) {
            .featured-post {
                gap: 1rem;
            }
            .featured-title {
                font-size: 2rem;
            }
        }

        /* Mobile (Max 768px) */
        @media (max-width: 768px) {
            .nav-wrapper {
                padding: 0 10px;
            }

            .gnb {
                display: none; /* Hide default nav */
                position: absolute;
                top: 100%;
                left: 0;
                width: 100%;
                background: white;
                flex-direction: column;
                padding: 1rem;
                box-shadow: var(--shadow-md);
                border-bottom: 1px solid var(--border-color);
            }

            .gnb.active {
                display: flex;
            }

            .mobile-menu-btn {
                display: block;
            }

            .featured-post {
                grid-template-columns: 1fr; /* Stack vertically */
                border-radius: 0;
            }

            .featured-img-container {
                height: 250px;
            }
            
            .featured-content {
                padding: 1.5rem;
            }

            .post-grid {
                grid-template-columns: 1fr; /* 1 Column */
            }

            .about-card {
                padding: 2rem 1rem;
                box-shadow: none;
            }
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        /* Utility for hiding elements */
        .hidden {
            display: none !important;
        }
    </style>
</head>
<body>

    <!-- Header -->
    <header>
        <div class="container nav-wrapper">
            <a href="#" class="logo" onclick="app.navigate('home')">Ella<span>.</span></a>
            
            <button class="mobile-menu-btn" onclick="app.toggleMenu()">
                <i class="fas fa-bars"></i>
            </button>

            <nav class="gnb" id="gnb">
                <button onclick="app.navigate('home')" class="active" data-target="home">Home</button>
                <button onclick="app.navigate('tech')" data-target="tech">Tech</button>
                <button onclick="app.navigate('design')" data-target="design">Design</button>
                <button onclick="app.navigate('about')" data-target="about">About</button>
            </nav>
        </div>
    </header>

    <!-- Main Content Area -->
    <main id="main-view">
        <div class="container">
            <!-- Hero / Featured Post -->
            <section class="hero-section" id="hero-section">
                <div class="featured-post">
                    <div class="featured-img-container">
                        <!-- Placeholder Image for Featured Post -->
                        <img src="https://images.unsplash.com/photo-1498050108023-c5249f4df085?auto=format&fit=crop&w=1200&q=80" alt="Featured Post Image">
                    </div>
                    <div class="featured-content">
                        <span class="tag">Featured / AI 활용</span>
                        <h2 class="featured-title">Github에 나만의 홈페이지 만들기</h2>
                        <p class="featured-excerpt">
                            코딩을 몰라도 괜찮아요. AI를 활용해 Github Pages에 정적 웹사이트를 배포하는 과정을 단계별로 알아봅니다. 나만의 공간을 만드는 즐거움.
                        </p>
                        <a href="#" class="read-more">Read Article <i class="fas fa-arrow-right" style="margin-left:5px; font-size: 0.8em;"></i></a>
                    </div>
                </div>
            </section>

            <!-- Post Grid -->
            <section class="grid-section">
                <h3 class="section-title" id="grid-title">Latest Stories</h3>
                <div class="post-grid" id="post-grid">
                    <!-- Javascript will inject cards here -->
                </div>
            </section>
        </div>
    </main>

    <!-- About View (Hidden by default) -->
    <section id="about-view" class="container">
        <div class="about-card">
            <!-- 
               [중요] 사용자 가이드: 
               1. '홍미숙 사진-1.jpg' 파일명을 'ella_profile.jpg'로 변경해주세요.
               2. 변경한 이미지 파일을 이 index.html 파일과 같은 폴더에 넣어주세요.
            -->
            <img src="ella_profile.jpg" onerror="this.src='https://images.unsplash.com/photo-1515621061946-b2742f34f539?auto=format&fit=crop&w=400&h=400&q=80'" alt="Ella Profile" class="profile-img">
            
            <h2 class="about-name">Ella</h2>
            <p class="about-bio">
                안녕하세요, Ella입니다.<br>
                일상 속의 작은 반짝임을 기록합니다. 독서와 글쓰기를 사랑하며, 
                때로는 코딩을 통해 새로운 세상을 배웁니다. <br>
                따뜻한 커피 한 잔과 함께 저의 이야기를 들어보세요.
            </p>
            <div class="social-links">
                <a href="https://github.com/hmsuk21" target="_blank" title="GitHub"><i class="fab fa-github"></i></a>
                <a href="mailto:hmsuk21@gmail.com" title="Email"><i class="fas fa-envelope"></i></a>
                <a href="#" title="Instagram"><i class="fab fa-instagram"></i></a>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <div class="container footer-content">
            <div class="footer-info">
                <div class="footer-logo">Ella.</div>
                <p>&copy; 2025 Ella's Blog. All rights reserved.</p>
                <p>Designed with minimal elegance.</p>
            </div>
            <div class="social-links" style="font-size: 1rem;">
                <a href="https://github.com/hmsuk21" target="_blank"><i class="fab fa-github" style="color:#fff"></i></a>
            </div>
        </div>
    </footer>

    <!-- JavaScript logic -->
    <script>
        /**
         * BLOG DATA 
         * (Based on uploaded item.csv)
         */
        const blogData = [
            {
                category: "독서, 글쓰기",
                title: "마음독립만세를 읽고",
                content: "독서 후기: 온전한 나로 서기 위한 마음의 여정을 책을 통해 비추어 봅니다.",
                date: "2025-12-15",
                img: "https://images.unsplash.com/photo-1512820790803-83ca734da794?auto=format&fit=crop&w=600&q=80",
                type: "home" // general
            },
            {
                category: "철학 / 삶",
                title: "삶이란 무엇인가",
                content: "인생 에세이: 흐르는 강물처럼 변화하는 삶 속에서 변하지 않는 가치는 무엇일까요?",
                date: "2025-12-15",
                img: "https://images.unsplash.com/photo-1444703686981-a3abbc4d4fe3?auto=format&fit=crop&w=600&q=80",
                type: "design" // Conceptual/Thinking
            },
            {
                category: "여행 기록",
                title: "남프랑스 여행",
                content: "따스한 햇살과 보랏빛 라벤더 향기가 가득했던 남프랑스 여행기.",
                date: "2025-12-15",
                img: "https://images.unsplash.com/photo-1499002238440-d264edd596ec?auto=format&fit=crop&w=600&q=80",
                type: "design" // Aesthetic
            },
            {
                category: "요리",
                title: "부드러운 수육 만들기",
                content: "집밥 레시피: 가족들과 함께 즐기는 따뜻하고 부드러운 수육 황금 레시피.",
                date: "2025-12-15",
                img: "https://images.unsplash.com/photo-1546069901-ba9599a7e63c?auto=format&fit=crop&w=600&q=80",
                type: "design" // Lifestyle/Design
            },
            {
                category: "건강 정보",
                title: "영양제 섭취 방법",
                content: "중년 건강 정보: 나에게 맞는 영양제를 올바르게 섭취하는 가이드.",
                date: "2025-12-15",
                img: "https://images.unsplash.com/photo-1505751172876-fa1923c5c528?auto=format&fit=crop&w=600&q=80",
                type: "home"
            },
            {
                category: "배움, 자기 계발",
                title: "하얗게 내린 눈의 풍경 은유",
                content: "창작 노트: 겨울 아침 창밖을 보며 떠오른 단상들을 시적인 언어로 풀어봅니다.",
                date: "2025-12-15",
                // Updated: Snow covered landscape image
                img: "https://images.unsplash.com/photo-1480497490787-505ec076689f?auto=format&fit=crop&w=600&q=80",
                type: "design"
            },
            {
                category: "AI 활용",
                title: "GitHub 홈페이지 만들기",
                content: "개발자가 아니어도 할 수 있는 정적 웹사이트 배포 가이드.",
                date: "2025-12-15",
                img: "https://images.unsplash.com/photo-1555099962-4199c345e5dd?auto=format&fit=crop&w=600&q=80",
                type: "tech"
            }
        ];

        /**
         * APPLICATION LOGIC (SPA)
         */
        const app = {
            currentTab: 'home',

            init: () => {
                app.renderPosts('home');
            },

            // Navigation Handler
            navigate: (tabName) => {
                app.currentTab = tabName;
                
                // 1. Update Active State in Nav
                document.querySelectorAll('.gnb button').forEach(btn => {
                    btn.classList.remove('active');
                    if(btn.dataset.target === tabName) btn.classList.add('active');
                });

                // 2. Mobile Menu close automatically
                document.getElementById('gnb').classList.remove('active');
                
                // 3. View Logic
                const mainView = document.getElementById('main-view');
                const aboutView = document.getElementById('about-view');
                const heroSection = document.getElementById('hero-section');
                const gridTitle = document.getElementById('grid-title');

                window.scrollTo({ top: 0, behavior: 'smooth' });

                if (tabName === 'about') {
                    // Show About, Hide Main
                    mainView.classList.add('hidden');
                    aboutView.style.display = 'block';
                } else {
                    // Show Main, Hide About
                    mainView.classList.remove('hidden');
                    aboutView.style.display = 'none';

                    // Hero Section Visibility: Only show on Home
                    if (tabName === 'home') {
                        heroSection.classList.remove('hidden');
                        gridTitle.innerText = "Latest Stories";
                    } else {
                        heroSection.classList.add('hidden');
                        gridTitle.innerText = tabName.charAt(0).toUpperCase() + tabName.slice(1) + " Posts";
                    }

                    // Render Grid based on Filter
                    app.renderPosts(tabName);
                }
            },

            // Render Posts Grid
            renderPosts: (filter) => {
                const grid = document.getElementById('post-grid');
                grid.innerHTML = ''; // Clear existing

                let filteredData = [];

                if (filter === 'home') {
                    // Show all (except maybe the featured one if we wanted to exclude it, but let's show items)
                    filteredData = blogData; 
                } else if (filter === 'tech') {
                    // Filter for Tech/AI/Learning
                    filteredData = blogData.filter(item => 
                        item.category.includes('AI') || item.category.includes('배움') || item.type === 'tech'
                    );
                } else if (filter === 'design') {
                    // Filter for Design/Art/Life/Travel
                    filteredData = blogData.filter(item => 
                        ['철학', '여행', '요리', '독서', '시쓰기'].some(k => item.category.includes(k)) || item.type === 'design'
                    );
                }

                if (filteredData.length === 0) {
                    grid.innerHTML = '<p style="grid-column: 1/-1; text-align:center; padding: 2rem;">No posts found in this category.</p>';
                    return;
                }

                filteredData.forEach(post => {
                    const card = document.createElement('article');
                    card.className = 'post-card';
                    card.innerHTML = `
                        <div class="card-img">
                            <img src="${post.img}" alt="${post.title}" loading="lazy">
                        </div>
                        <div class="card-body">
                            <div class="card-category">${post.category}</div>
                            <h3 class="card-title">${post.title}</h3>
                            <p class="card-desc">${post.content}</p>
                            <div class="card-meta">
                                <span>Ella</span>
                                <span>${post.date}</span>
                            </div>
                        </div>
                    `;
                    grid.appendChild(card);
                });
            },

            // Mobile Menu Toggle
            toggleMenu: () => {
                const gnb = document.getElementById('gnb');
                gnb.classList.toggle('active');
            }
        };

        // Initialize App
        document.addEventListener('DOMContentLoaded', app.init);

    </script>
</body>
</html>
