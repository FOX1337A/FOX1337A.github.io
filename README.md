<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Foxware - FOXS1337</title>
    <script src="https://cdn.tailwindcss.com/3.3.3"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.7.2/css/all.min.css">
    <style>
        body {
            font-family: 'Noto Sans TC', sans-serif;
            background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%);
            color: #ffffff;
            overflow-x: hidden;
        }

        .glassmorphism {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border-radius: 16px;
            border: 1px solid rgba(255, 255, 255, 0.2);
            box-shadow: 0 8px 32px 0 rgba(0, 0, 0, 0.3);
        }

        .card-hover {
            transition: all 0.3s ease;
        }

        .card-hover:hover {
            transform: translateY(-5px);
            box-shadow: 0 12px 28px 0 rgba(0, 0, 0, 0.4);
        }

        .highlight-text {
            position: relative;
            display: inline-block;
        }

        .highlight-text::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            height: 4px;
            background-color: rgba(255, 191, 0, 0.5);
            z-index: -1;
        }

        .feature-icon {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background: linear-gradient(135deg, #ffbf00 0%, #ff8c00 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            color: #1a1a2e;
            font-size: 24px;
            margin-bottom: 16px;
            transition: all 0.3s ease;
        }

        .feature-card:hover .feature-icon {
            transform: scale(1.1);
            box-shadow: 0 0 20px rgba(255, 191, 0, 0.6);
        }

        .discord-button {
            background: linear-gradient(135deg, #7289da 0%, #5b6eae 100%);
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .discord-button:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 20px rgba(114, 137, 218, 0.5);
        }

        .discord-button::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.2), transparent);
            transition: all 0.6s ease;
        }

        .discord-button:hover::before {
            left: 100%;
        }

        .game-image-container {
            position: relative;
            overflow: hidden;
            border-radius: 16px;
        }

        .game-image-container img {
            transition: transform 0.5s ease;
        }

        .game-image-container:hover img {
            transform: scale(1.05);
        }

        .bg-glow {
            position: absolute;
            background: radial-gradient(circle, rgba(255, 191, 0, 0.2) 0%, rgba(255, 191, 0, 0) 70%);
            width: 300px;
            height: 300px;
            border-radius: 50%;
            z-index: -1;
        }

        /* 移动端菜单样式 */
        .mobile-menu {
            position: absolute;
            top: 100%;
            left: 0;
            right: 0;
            padding: 1rem;
            margin: 0.5rem;
            border-radius: 0.75rem;
            background: rgba(26, 26, 46, 0.9);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            box-shadow: 0 8px 32px 0 rgba(0, 0, 0, 0.3);
            transform-origin: top;
            transform: scaleY(0);
            opacity: 0;
            transition: transform 0.3s ease, opacity 0.3s ease;
            z-index: 100;
        }

        .mobile-menu.active {
            transform: scaleY(1);
            opacity: 1;
        }

        .mobile-menu a {
            display: block;
            padding: 0.75rem 1rem;
            border-radius: 0.5rem;
            margin-bottom: 0.5rem;
            font-weight: 500;
            transition: all 0.2s ease;
        }

        .mobile-menu a:hover, .mobile-menu a:focus {
            background-color: rgba(255, 191, 0, 0.1);
            color: #ffbf00;
        }
    </style>
</head>
<body class="min-h-screen">
    <!-- 导航条 -->
    <nav class="glassmorphism sticky top-0 z-50 p-4 mb-8" id="mainNav">
        <div class="container mx-auto flex items-center justify-between">
            <div class="text-xl font-bold text-white flex items-center">
                <i class="fas fa-fox mr-2 text-yellow-400"></i>Foxware
            </div>
            <div class="hidden md:flex space-x-6">
                <a href="#about" class="text-gray-300 hover:text-yellow-400 transition-colors">關於</a>
                <a href="#features" class="text-gray-300 hover:text-yellow-400 transition-colors">功能</a>
                <a href="#discord" class="text-gray-300 hover:text-yellow-400 transition-colors">社區</a>
            </div>
            <button class="md:hidden text-gray-300 focus:outline-none" id="mobileMenuButton" aria-label="導航菜單">
                <i class="fas fa-bars"></i>
            </button>

            <!-- 移动端导航菜单 -->
            <div class="mobile-menu md:hidden" id="mobileMenu">
                <a href="#about" class="text-gray-300 hover:text-yellow-400 transition-colors flex items-center">
                    <i class="fas fa-info-circle mr-3 text-yellow-400"></i>關於
                </a>
                <a href="#features" class="text-gray-300 hover:text-yellow-400 transition-colors flex items-center">
                    <i class="fas fa-cogs mr-3 text-yellow-400"></i>功能
                </a>
                <a href="#discord" class="text-gray-300 hover:text-yellow-400 transition-colors flex items-center">
                    <i class="fab fa-discord mr-3 text-yellow-400"></i>社區
                </a>
            </div>
        </div>
    </nav>

    <!-- 头部横幅 -->
    <header class="container mx-auto py-16 px-4 md:px-8 relative">
        <div class="bg-glow top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2"></div>
        <div class="max-w-4xl mx-auto text-center relative">
            <h1 class="text-5xl md:text-6xl font-bold mb-6">
                <span class="text-yellow-400">Foxware</span>
            </h1>
            <p class="text-xl md:text-2xl text-gray-300 mb-12">為《Garena 三角洲行動》打造的頂級輔助工具</p>
            <div class="flex justify-center">
                <a href="#discord" class="discord-button text-white font-bold py-3 px-8 rounded-full flex items-center">
                    <i class="fab fa-discord mr-2"></i> 加入 Discord 社區
                </a>
            </div>
        </div>
    </header>

    <!-- 关于部分 -->
    <section id="about" class="container mx-auto py-12 px-4 md:px-8">
        <div class="glassmorphism p-8 mb-16">
            <h2 class="text-3xl font-bold mb-8 text-center">關於 <span class="text-yellow-400">Foxware</span></h2>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-8 items-center">
                <div>
                    <h3 class="text-2xl font-semibold mb-4 text-yellow-400">適用遊戲</h3>
                    <p class="text-gray-300 mb-6">Foxware 專為《Garena 三角洲行動》設計，提供安全、穩定、高效的遊戲體驗增強功能，讓您在戰場上佔據優勢地位。</p>
                    <div class="data-pill bg-yellow-400/20 text-yellow-400 px-4 py-2 rounded-full inline-block">
                        <i class="fas fa-gamepad mr-2"></i> 《Garena 三角洲行動》
                    </div>
                </div>
                <div class="game-image-container">
                    <img src="https://s.coze.cn/image/XAUoRHCf9Ec/" alt="《Garena 三角洲行動》遊戲截圖" class="w-full h-auto rounded-2xl">
                </div>
            </div>
        </div>
    </section>

    <!-- 功能特点部分 -->
    <section id="features" class="container mx-auto py-12 px-4 md:px-8">
        <h2 class="text-3xl font-bold mb-12 text-center">功能 <span class="text-yellow-400">特點</span></h2>

        <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8">
            <div class="glassmorphism p-6 card-hover feature-card">
                <div class="feature-icon">
                    <i class="fas fa-paint-brush"></i>
                </div>
                <h3 class="text-xl font-semibold mb-3">美觀UI</h3>
                <p class="text-gray-300">精心設計的用戶界面，簡潔明了，易於操作，讓您輕鬆掌握所有功能。</p>
            </div>

            <div class="glassmorphism p-6 card-hover feature-card">
                <div class="feature-icon">
                    <i class="fas fa-crosshairs"></i>
                </div>
                <h3 class="text-xl font-semibold mb-3">多種自定義ESP</h3>
                <p class="text-gray-300">提供多種敵人位置顯示模式，讓您在複雜的戰場環境中隨時掌握敵情。</p>
            </div>

            <div class="glassmorphism p-6 card-hover feature-card">
                <div class="feature-icon">
                    <i class="fas fa-lightbulb"></i>
                </div>
                <h3 class="text-xl font-semibold mb-3">簡單使用</h3>
                <p class="text-gray-300">直覺式操作，無需複雜設置，新手也能快速上手，享受最佳遊戲體驗。</p>
            </div>

            <div class="glassmorphism p-6 card-hover feature-card">
                <div class="feature-icon">
                    <i class="fas fa-tags"></i>
                </div>
                <h3 class="text-xl font-semibold mb-3">價格便宜</h3>
                <p class="text-gray-300">性價比高，提供多種套餐選擇，讓每一位玩家都能輕鬆負擔。</p>
            </div>

            <div class="glassmorphism p-6 card-hover feature-card">
                <div class="feature-icon">
                    <i class="fas fa-shield-alt"></i>
                </div>
                <h3 class="text-xl font-semibold mb-3">不動任何內存</h3>
                <p class="text-gray-300">先進的技術，無需修改遊戲內存，確保您的帳號安全，遠離封禁風險。</p>
            </div>

            <div class="glassmorphism p-6 card-hover feature-card">
                <div class="feature-icon">
                    <i class="fas fa-bolt"></i>
                </div>
                <h3 class="text-xl font-semibold mb-3">更新速度快</h3>
                <p class="text-gray-300">專業團隊全天候監控，遊戲更新後第一時間提供相容版本，不影響您的遊戲體驗。</p>
            </div>
        </div>
    </section>

    <!-- Discord社区部分 -->
    <section id="discord" class="container mx-auto py-16 px-4 md:px-8">
        <div class="glassmorphism p-8 text-center">
            <h2 class="text-3xl font-bold mb-6">加入我們的 <span class="text-yellow-400">Discord 社區</span></h2>
            <p class="text-gray-300 mb-8 max-w-2xl mx-auto">加入Foxware Discord社區，與其他玩家交流心得，獲取最新軟件更新資訊，享受專業客服支持。</p>
            <a href="https://discord.gg/RbRfnU4Gzv" target="_blank" rel="noopener noreferrer" class="discord-button text-white font-bold py-4 px-10 rounded-full text-lg inline-flex items-center">
                <i class="fab fa-discord mr-3 text-2xl"></i> 立即加入 Discord
            </a>
            <p class="text-gray-400 mt-4">Discord 邀請碼: RbRfnU4Gzv</p>
        </div>
    </section>

    <!-- 页脚 -->
    <footer class="container mx-auto py-8 px-4 md:px-8 text-center text-gray-400">
        <p>© 2025 Foxware. 版權所有。</p>
    </footer>

    <script>
        // 添加滚动动画效果
        document.addEventListener('DOMContentLoaded', function() {
            // 平滑滚动
            document.querySelectorAll('a[href^="#"]').forEach(anchor => {
                anchor.addEventListener('click', function (e) {
                    e.preventDefault();

                    document.querySelector(this.getAttribute('href')).scrollIntoView({
                        behavior: 'smooth'
                    });

                    // 点击导航链接后关闭移动端菜单
                    const mobileMenu = document.getElementById('mobileMenu');
                    if (mobileMenu.classList.contains('active')) {
                        mobileMenu.classList.remove('active');
                        // 同时切换图标回汉堡按钮
                        const menuIcon = document.querySelector('#mobileMenuButton i');
                        menuIcon.classList.remove('fa-times');
                        menuIcon.classList.add('fa-bars');
                    }
                });
            });

            // 移动端导航菜单切换
            const menuButton = document.getElementById('mobileMenuButton');
            const mobileMenu = document.getElementById('mobileMenu');

            menuButton.addEventListener('click', function() {
                mobileMenu.classList.toggle('active');

                // 切换图标
                const icon = this.querySelector('i');
                if (mobileMenu.classList.contains('active')) {
                    icon.classList.remove('fa-bars');
                    icon.classList.add('fa-times');
                } else {
                    icon.classList.remove('fa-times');
                    icon.classList.add('fa-bars');
                }
            });

            // 点击页面其他区域关闭移动端菜单
            document.addEventListener('click', function(event) {
                const isClickInsideNav = document.getElementById('mainNav').contains(event.target);

                if (!isClickInsideNav && mobileMenu.classList.contains('active')) {
                    mobileMenu.classList.remove('active');
                    const icon = menuButton.querySelector('i');
                    icon.classList.remove('fa-times');
                    icon.classList.add('fa-bars');
                }
            });
        });
    </script>
</body>
</html>
