# phone-customizer
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
    <meta name="mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-capable" content="yes">
    <title>💎 Phone Customization Pro</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            -webkit-tap-highlight-color: transparent;
        }

        body {
            font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            overflow-x: hidden;
            color: #fff;
            padding-bottom: 80px;
        }

        /* Header */
        .header {
            background: rgba(0, 0, 0, 0.3);
            backdrop-filter: blur(20px);
            padding: 20px;
            text-align: center;
            position: sticky;
            top: 0;
            z-index: 1000;
            border-bottom: 2px solid rgba(255, 255, 255, 0.1);
            box-shadow: 0 4px 30px rgba(0, 0, 0, 0.3);
        }

        .header h1 {
            font-size: 24px;
            font-weight: bold;
            background: linear-gradient(45deg, #ff6ec7, #7873f5, #4facfe);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            animation: gradient 3s ease infinite;
            background-size: 200% 200%;
        }

        @keyframes gradient {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        /* Stats Bar */
        .stats-bar {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 10px;
            padding: 15px;
            margin: 15px;
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border-radius: 15px;
            border: 1px solid rgba(255, 255, 255, 0.2);
        }

        .stat-item {
            text-align: center;
            padding: 10px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 10px;
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.05); }
        }

        .stat-value {
            font-size: 24px;
            font-weight: bold;
            color: #00f0ff;
            text-shadow: 0 0 10px rgba(0, 240, 255, 0.5);
        }

        .stat-label {
            font-size: 12px;
            opacity: 0.8;
            margin-top: 5px;
        }

        /* Theme Selector */
        .theme-selector {
            margin: 20px;
            padding: 20px;
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border-radius: 15px;
            border: 1px solid rgba(255, 255, 255, 0.2);
        }

        .theme-title {
            font-size: 18px;
            font-weight: bold;
            margin-bottom: 15px;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .theme-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 10px;
        }

        .theme-btn {
            padding: 15px;
            border: none;
            border-radius: 12px;
            font-weight: bold;
            font-size: 14px;
            color: #fff;
            cursor: pointer;
            transition: all 0.3s;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.3);
            position: relative;
            overflow: hidden;
        }

        .theme-btn:active {
            transform: scale(0.95);
        }

        .theme-btn::before {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            width: 0;
            height: 0;
            border-radius: 50%;
            background: rgba(255, 255, 255, 0.3);
            transform: translate(-50%, -50%);
            transition: width 0.6s, height 0.6s;
        }

        .theme-btn:active::before {
            width: 300px;
            height: 300px;
        }

        /* Feature Cards */
        .features {
            margin: 20px;
        }

        .feature-card {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border-radius: 15px;
            padding: 20px;
            margin-bottom: 15px;
            border: 1px solid rgba(255, 255, 255, 0.2);
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
        }

        .feature-header {
            display: flex;
            align-items: center;
            gap: 12px;
            margin-bottom: 15px;
            font-size: 18px;
            font-weight: bold;
        }

        .icon {
            font-size: 28px;
            filter: drop-shadow(0 0 10px rgba(255, 255, 255, 0.5));
        }

        .action-btn {
            width: 100%;
            padding: 15px;
            margin-top: 10px;
            border: none;
            border-radius: 12px;
            font-size: 16px;
            font-weight: bold;
            color: #fff;
            background: linear-gradient(135deg, #667eea, #764ba2);
            box-shadow: 0 4px 15px rgba(102, 126, 234, 0.4);
            cursor: pointer;
            transition: all 0.3s;
            position: relative;
            overflow: hidden;
        }

        .action-btn:active {
            transform: scale(0.98);
            box-shadow: 0 2px 10px rgba(102, 126, 234, 0.4);
        }

        /* Toggle Switch */
        .toggle-container {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 12px 0;
        }

        .toggle {
            position: relative;
            width: 60px;
            height: 30px;
            background: rgba(255, 255, 255, 0.2);
            border-radius: 30px;
            cursor: pointer;
            transition: background 0.3s;
        }

        .toggle.active {
            background: linear-gradient(135deg, #667eea, #764ba2);
        }

        .toggle-circle {
            position: absolute;
            top: 3px;
            left: 3px;
            width: 24px;
            height: 24px;
            background: #fff;
            border-radius: 50%;
            transition: transform 0.3s;
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.3);
        }

        .toggle.active .toggle-circle {
            transform: translateX(30px);
        }

        /* Slider */
        .slider-container {
            padding: 15px 0;
        }

        .slider-label {
            display: flex;
            justify-content: space-between;
            margin-bottom: 10px;
            font-size: 14px;
        }

        .slider {
            width: 100%;
            height: 8px;
            border-radius: 5px;
            background: rgba(255, 255, 255, 0.2);
            outline: none;
            -webkit-appearance: none;
        }

        .slider::-webkit-slider-thumb {
            -webkit-appearance: none;
            width: 24px;
            height: 24px;
            border-radius: 50%;
            background: linear-gradient(135deg, #667eea, #764ba2);
            cursor: pointer;
            box-shadow: 0 2px 10px rgba(102, 126, 234, 0.5);
        }

        /* Bottom Navigation */
        .bottom-nav {
            position: fixed;
            bottom: 0;
            left: 0;
            right: 0;
            background: rgba(0, 0, 0, 0.5);
            backdrop-filter: blur(20px);
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            padding: 10px 0;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            z-index: 1000;
        }

        .nav-item {
            text-align: center;
            padding: 10px;
            cursor: pointer;
            transition: all 0.3s;
            border: none;
            background: none;
            color: rgba(255, 255, 255, 0.6);
        }

        .nav-item.active {
            color: #fff;
            transform: translateY(-5px);
        }

        .nav-icon {
            font-size: 24px;
            margin-bottom: 5px;
        }

        .nav-label {
            font-size: 12px;
        }

        /* Notification */
        .notification {
            position: fixed;
            top: -100px;
            left: 50%;
            transform: translateX(-50%);
            background: rgba(0, 0, 0, 0.9);
            backdrop-filter: blur(10px);
            padding: 15px 30px;
            border-radius: 50px;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.5);
            transition: top 0.5s;
            z-index: 2000;
            font-weight: bold;
        }

        .notification.show {
            top: 20px;
        }

        /* Animations */
        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .feature-card {
            animation: fadeInUp 0.5s ease-out;
        }

        .feature-card:nth-child(1) { animation-delay: 0.1s; }
        .feature-card:nth-child(2) { animation-delay: 0.2s; }
        .feature-card:nth-child(3) { animation-delay: 0.3s; }
        .feature-card:nth-child(4) { animation-delay: 0.4s; }

        /* Loading Spinner */
        .spinner {
            display: inline-block;
            width: 20px;
            height: 20px;
            border: 3px solid rgba(255, 255, 255, 0.3);
            border-top-color: #fff;
            border-radius: 50%;
            animation: spin 0.8s linear infinite;
        }

        @keyframes spin {
            to { transform: rotate(360deg); }
        }
    </style>
</head>
<body>
    <!-- Header -->
    <div class="header">
        <h1>💎 Phone Customization Pro</h1>
    </div>

    <!-- Stats Bar -->
    <div class="stats-bar">
        <div class="stat-item">
            <div class="stat-value" id="cpu">0%</div>
            <div class="stat-label">CPU</div>
        </div>
        <div class="stat-item">
            <div class="stat-value" id="ram">0%</div>
            <div class="stat-label">RAM</div>
        </div>
        <div class="stat-item">
            <div class="stat-value" id="battery">100%</div>
            <div class="stat-label">Battery</div>
        </div>
    </div>

    <!-- Theme Selector -->
    <div class="theme-selector">
        <div class="theme-title">
            <span>🎨</span>
            <span>Choose Theme</span>
        </div>
        <div class="theme-grid">
            <button class="theme-btn" style="background: linear-gradient(135deg, #667eea, #764ba2);" onclick="changeTheme('purple')">Purple</button>
            <button class="theme-btn" style="background: linear-gradient(135deg, #f093fb, #f5576c);" onclick="changeTheme('pink')">Pink</button>
            <button class="theme-btn" style="background: linear-gradient(135deg, #4facfe, #00f2fe);" onclick="changeTheme('blue')">Blue</button>
            <button class="theme-btn" style="background: linear-gradient(135deg, #43e97b, #38f9d7);" onclick="changeTheme('green')">Green</button>
            <button class="theme-btn" style="background: linear-gradient(135deg, #fa709a, #fee140);" onclick="changeTheme('sunset')">Sunset</button>
            <button class="theme-btn" style="background: linear-gradient(135deg, #30cfd0, #330867);" onclick="changeTheme('ocean')">Ocean</button>
        </div>
    </div>

    <!-- Features Container -->
    <div class="features" id="featuresContainer">
        <!-- Dashboard Tab -->
        <div class="tab-content" id="dashboard">
            <div class="feature-card">
                <div class="feature-header">
                    <span class="icon">⚡</span>
                    <span>Performance Boost</span>
                </div>
                <button class="action-btn" onclick="performAction('boost')">
                    🚀 Boost Performance
                </button>
                <button class="action-btn" onclick="performAction('clean')">
                    🧹 Clean Cache
                </button>
                <button class="action-btn" onclick="performAction('memory')">
                    💾 Free Memory
                </button>
            </div>

            <div class="feature-card">
                <div class="feature-header">
                    <span class="icon">🔋</span>
                    <span>Battery Saver</span>
                </div>
                <div class="toggle-container">
                    <span>Power Saving Mode</span>
                    <div class="toggle" onclick="toggleFeature(this)">
                        <div class="toggle-circle"></div>
                    </div>
                </div>
                <div class="toggle-container">
                    <span>Low Power Mode</span>
                    <div class="toggle" onclick="toggleFeature(this)">
                        <div class="toggle-circle"></div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Customize Tab -->
        <div class="tab-content hidden" id="customize">
            <div class="feature-card">
                <div class="feature-header">
                    <span class="icon">🎨</span>
                    <span>Visual Effects</span>
                </div>
                <div class="slider-container">
                    <div class="slider-label">
                        <span>Transparency</span>
                        <span id="transparencyValue">50%</span>
                    </div>
                    <input type="range" class="slider" min="0" max="100" value="50" oninput="updateSlider('transparency', this.value)">
                </div>
                <div class="slider-container">
                    <div class="slider-label">
                        <span>Blur Effect</span>
                        <span id="blurValue">10px</span>
                    </div>
                    <input type="range" class="slider" min="0" max="30" value="10" oninput="updateSlider('blur', this.value)">
                </div>
            </div>

            <div class="feature-card">
                <div class="feature-header">
                    <span class="icon">✨</span>
                    <span>Animations</span>
                </div>
                <div class="toggle-container">
                    <span>Enable Animations</span>
                    <div class="toggle active" onclick="toggleFeature(this)">
                        <div class="toggle-circle"></div>
                    </div>
                </div>
                <div class="toggle-container">
                    <span>Smooth Scrolling</span>
                    <div class="toggle active" onclick="toggleFeature(this)">
                        <div class="toggle-circle"></div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Apps Tab -->
        <div class="tab-content hidden" id="apps">
            <div class="feature-card">
                <div class="feature-header">
                    <span class="icon">📱</span>
                    <span>App Manager</span>
                </div>
                <button class="action-btn" onclick="performAction('listapps')">
                    📋 View All Apps
                </button>
                <button class="action-btn" onclick="performAction('cleardata')">
                    🗑️ Clear App Data
                </button>
                <button class="action-btn" onclick="performAction('permissions')">
                    🔐 Manage Permissions
                </button>
            </div>
        </div>

        <!-- Settings Tab -->
        <div class="tab-content hidden" id="settings">
            <div class="feature-card">
                <div class="feature-header">
                    <span class="icon">⚙️</span>
                    <span>Advanced Settings</span>
                </div>
                <div class="toggle-container">
                    <span>Developer Mode</span>
                    <div class="toggle" onclick="toggleFeature(this)">
                        <div class="toggle-circle"></div>
                    </div>
                </div>
                <div class="toggle-container">
                    <span>Auto Optimization</span>
                    <div class="toggle" onclick="toggleFeature(this)">
                        <div class="toggle-circle"></div>
                    </div>
                </div>
                <button class="action-btn" onclick="performAction('backup')">
                    💾 Backup Settings
                </button>
                <button class="action-btn" onclick="performAction('restore')">
                    🔄 Restore Defaults
                </button>
            </div>
        </div>
    </div>

    <!-- Bottom Navigation -->
    <div class="bottom-nav">
        <button class="nav-item active" onclick="switchTab('dashboard', this)">
            <div class="nav-icon">🏠</div>
            <div class="nav-label">Home</div>
        </button>
        <button class="nav-item" onclick="switchTab('customize', this)">
            <div class="nav-icon">🎨</div>
            <div class="nav-label">Customize</div>
        </button>
        <button class="nav-item" onclick="switchTab('apps', this)">
            <div class="nav-icon">📱</div>
            <div class="nav-label">Apps</div>
        </button>
        <button class="nav-item" onclick="switchTab('settings', this)">
            <div class="nav-icon">⚙️</div>
            <div class="nav-label">Settings</div>
        </button>
    </div>

    <!-- Notification -->
    <div class="notification" id="notification"></div>

    <script>
        // Theme Configuration
        const themes = {
            purple: 'linear-gradient(135deg, #667eea 0%, #764ba2 100%)',
            pink: 'linear-gradient(135deg, #f093fb 0%, #f5576c 100%)',
            blue: 'linear-gradient(135deg, #4facfe 0%, #00f2fe 100%)',
            green: 'linear-gradient(135deg, #43e97b 0%, #38f9d7 100%)',
            sunset: 'linear-gradient(135deg, #fa709a 0%, #fee140 100%)',
            ocean: 'linear-gradient(135deg, #30cfd0 0%, #330867 100%)'
        };

        // Change Theme
        function changeTheme(theme) {
            document.body.style.background = themes[theme];
            showNotification('✅ Theme Changed!');
        }

        // Switch Tabs
        function switchTab(tabId, button) {
            // Hide all tabs
            document.querySelectorAll('.tab-content').forEach(tab => {
                tab.classList.add('hidden');
            });
            
            // Remove active from all nav items
            document.querySelectorAll('.nav-item').forEach(item => {
                item.classList.remove('active');
            });
            
            // Show selected tab
            document.getElementById(tabId).classList.remove('hidden');
            button.classList.add('active');
        }

        // Toggle Features
        function toggleFeature(element) {
            element.classList.toggle('active');
            const isActive = element.classList.contains('active');
            showNotification(isActive ? '✅ Enabled' : '❌ Disabled');
        }

        // Update Sliders
        function updateSlider(type, value) {
            if (type === 'transparency') {
                document.getElementById('transparencyValue').textContent = value + '%';
            } else if (type === 'blur') {
                document.getElementById('blurValue').textContent = value + 'px';
            }
        }

        // Perform Actions
        
