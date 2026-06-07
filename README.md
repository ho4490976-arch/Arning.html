<!DOCTYPE html>
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover, user-scalable=yes">
    <meta name="theme-color" content="#4CAF50">
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
    <title>Gaon Gyan Quiz - Learn & Earn</title>
    
    <!-- Google AdMob -->
    <script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-7709786685996364"
        crossorigin="anonymous"></script>
    
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            -webkit-tap-highlight-color: transparent;
        }

        :root {
            --primary: #4CAF50;
            --primary-dark: #388E3C;
            --primary-light: #81C784;
            --secondary: #FF9800;
            --danger: #f44336;
            --dark: #333;
            --light: #f5f5f5;
            --white: #ffffff;
            --shadow: 0 2px 10px rgba(0,0,0,0.1);
            --border-radius: 12px;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            color: var(--dark);
        }

        body.dark-mode {
            background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%);
            color: #eee;
        }

        body.dark-mode .card {
            background: #2d2d44;
            color: #eee;
        }

        body.dark-mode input, 
        body.dark-mode .option-btn {
            background: #3d3d5c;
            color: #fff;
            border-color: #5d5d7c;
        }

        .app-container {
            max-width: 500px;
            margin: 0 auto;
            padding: 15px;
            min-height: 100vh;
            padding-bottom: 75px;
        }

        /* Header */
        .header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 12px 0;
            margin-bottom: 15px;
        }

        .logo {
            font-size: 22px;
            font-weight: bold;
            color: var(--white);
        }

        .logo span {
            color: var(--secondary);
        }

        .user-info {
            display: flex;
            align-items: center;
            gap: 12px;
            background: rgba(255,255,255,0.2);
            padding: 6px 12px;
            border-radius: 30px;
        }

        .coins {
            display: flex;
            align-items: center;
            gap: 4px;
            background: var(--secondary);
            padding: 4px 10px;
            border-radius: 20px;
            color: white;
            font-weight: bold;
            font-size: 14px;
        }

        /* Cards */
        .card {
            background: var(--white);
            border-radius: var(--border-radius);
            padding: 18px;
            margin-bottom: 15px;
            box-shadow: var(--shadow);
        }

        /* Buttons */
        .btn {
            padding: 12px 20px;
            border: none;
            border-radius: 10px;
            font-size: 16px;
            font-weight: bold;
            cursor: pointer;
            transition: transform 0.2s, opacity 0.2s;
            width: 100%;
        }

        .btn:active {
            transform: scale(0.98);
        }

        .btn-primary {
            background: var(--primary);
            color: white;
        }

        .btn-secondary {
            background: var(--secondary);
            color: white;
        }

        /* Quiz Options */
        .option-btn {
            width: 100%;
            padding: 14px;
            margin: 8px 0;
            background: var(--light);
            border: 2px solid #e0e0e0;
            border-radius: 10px;
            text-align: left;
            font-size: 15px;
            cursor: pointer;
            transition: all 0.3s;
        }

        .option-btn:active {
            transform: scale(0.98);
        }

        .option-btn.correct {
            background: #4caf50;
            color: white;
            border-color: #2e7d32;
        }

        .option-btn.wrong {
            background: #f44336;
            color: white;
            border-color: #c62828;
        }

        .option-btn.disabled {
            pointer-events: none;
            opacity: 0.7;
        }

        /* Timer */
        .timer {
            width: 55px;
            height: 55px;
            border-radius: 50%;
            background: var(--primary);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 22px;
            font-weight: bold;
            color: white;
        }

        .timer.warning {
            background: var(--danger);
            animation: pulse 1s infinite;
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.05); }
        }

        /* Grid */
        .categories-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 12px;
        }

        .category-card {
            background: linear-gradient(135deg, var(--primary), var(--primary-dark));
            color: white;
            padding: 18px;
            border-radius: var(--border-radius);
            text-align: center;
            cursor: pointer;
            transition: transform 0.2s;
        }

        .category-card:active {
            transform: scale(0.96);
        }

        .category-icon {
            font-size: 36px;
            margin-bottom: 8px;
        }

        /* Leaderboard */
        .leaderboard-item {
            display: flex;
            align-items: center;
            padding: 12px;
            border-bottom: 1px solid #eee;
        }

        body.dark-mode .leaderboard-item {
            border-bottom-color: #444;
        }

        .rank {
            width: 45px;
            font-weight: bold;
            font-size: 18px;
        }

        .rank-1 { color: #FFD700; }
        .rank-2 { color: #C0C0C0; }
        .rank-3 { color: #CD7F32; }

        /* Bottom Navigation */
        .bottom-nav {
            position: fixed;
            bottom: 0;
            left: 0;
            right: 0;
            max-width: 500px;
            margin: 0 auto;
            background: var(--white);
            display: flex;
            justify-content: space-around;
            padding: 10px;
            box-shadow: 0 -2px 15px rgba(0,0,0,0.1);
            border-radius: 20px 20px 0 0;
            z-index: 100;
        }

        body.dark-mode .bottom-nav {
            background: #2d2d44;
        }

        .nav-item {
            text-align: center;
            padding: 8px;
            cursor: pointer;
            border-radius: 10px;
            flex: 1;
        }

        .nav-item.active {
            background: var(--primary-light);
            color: white;
        }

        .nav-icon {
            font-size: 24px;
        }

        .nav-label {
            font-size: 11px;
            margin-top: 3px;
        }

        /* Ad Container */
        .ad-container {
            margin: 15px 0;
            text-align: center;
            min-height: 90px;
        }

        /* Loading */
        .spinner {
            border: 3px solid #f3f3f3;
            border-top: 3px solid var(--primary);
            border-radius: 50%;
            width: 40px;
            height: 40px;
            animation: spin 1s linear infinite;
            margin: 20px auto;
        }

        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        /* Modal */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: rgba(0,0,0,0.8);
            z-index: 1000;
            justify-content: center;
            align-items: center;
        }

        .modal-content {
            background: var(--white);
            border-radius: var(--border-radius);
            padding: 25px;
            max-width: 85%;
            text-align: center;
        }

        body.dark-mode .modal-content {
            background: #2d2d44;
        }

        /* Screens */
        .screen {
            display: none;
        }

        .screen.active {
            display: block;
        }

        /* Inputs */
        input, select {
            width: 100%;
            padding: 14px;
            border: 2px solid #e0e0e0;
            border-radius: 10px;
            font-size: 16px;
            margin-bottom: 12px;
            font-family: inherit;
        }

        /* Stats Row */
        .stats-row {
            display: flex;
            justify-content: space-around;
            text-align: center;
        }

        .stat-item {
            flex: 1;
        }

        .stat-value {
            font-size: 20px;
            font-weight: bold;
            color: var(--primary);
        }

        /* Transaction List */
        .transaction-item {
            display: flex;
            justify-content: space-between;
            padding: 12px 0;
            border-bottom: 1px solid #eee;
        }

        body.dark-mode .transaction-item {
            border-bottom-color: #444;
        }

        /* Responsive */
        @media (max-width: 480px) {
            .app-container {
                padding: 12px;
            }
            
            .categories-grid {
                gap: 10px;
            }
            
            .category-card {
                padding: 14px;
            }
            
            .category-icon {
                font-size: 28px;
            }
        }
    </style>
</head>
<body>
    <div class="app-container">
        <!-- Header -->
        <div class="header">
            <div class="logo">Gaon Gyan <span>Quiz</span></div>
            <div class="user-info" id="userInfo" style="display: none;">
                <div class="coins">
                    <span>🪙</span>
                    <span id="coinBalance">0</span>
                </div>
                <div id="userNameDisplay" style="cursor: pointer; font-size: 20px;">👤</div>
            </div>
        </div>

        <!-- ==================== LOGIN SCREEN ==================== -->
        <div id="loginScreen" class="screen active">
            <div class="card" style="text-align: center;">
                <div style="font-size: 55px; margin-bottom: 15px;">📚</div>
                <h2>Gaon Gyan Quiz</h2>
                <p style="color: #666; margin: 12px 0;">Learn, Play & Earn Rewards!</p>
                
                <div style="background: linear-gradient(135deg, #FF9800, #FF5722); padding: 12px; border-radius: 10px; margin: 15px 0; color: white;">
                    <div>🎁 Get 50 bonus coins on signup!</div>
                    <div>💰 20 coins for every referral!</div>
                </div>

                <input type="tel" id="phoneInput" placeholder="📱 Enter 10-digit mobile number" maxlength="10" pattern="[0-9]{10}">
                <input type="text" id="referralCodeInput" placeholder="🎫 Referral Code (Optional)">
                
                <button class="btn btn-primary" onclick="sendOTP()" style="margin-bottom: 10px;" id="sendOtpBtn">
                    Send OTP
                </button>
                
                <div id="otpSection" style="display: none;">
                    <input type="text" id="otpInput" placeholder="🔢 Enter 6-digit OTP" maxlength="6">
                    <button class="btn btn-secondary" onclick="verifyOTP()">
                        Verify & Login
                    </button>
                </div>
                
                <p style="font-size: 12px; color: #999; margin-top: 15px;">Demo OTP: 123456 (for testing)</p>
            </div>
        </div>

        <!-- ==================== HOME SCREEN ==================== -->
        <div id="homeScreen" class="screen">
            <!-- Daily Quiz Banner -->
            <div class="card" style="background: linear-gradient(135deg, #FF9800, #FF5722); color: white; padding: 15px;">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <div>
                        <div style="font-size: 18px; font-weight: bold;">🎯 Daily Quiz Challenge</div>
                        <div style="font-size: 13px; opacity: 0.9;">10 Questions | 50 Coins</div>
                    </div>
                    <button class="btn" style="background: white; color: #FF5722; width: auto; padding: 10px 20px;" onclick="startDailyQuiz()">
                        Play Now →
                    </button>
                </div>
            </div>

            <!-- Categories -->
            <h3 style="color: white; margin: 12px 0;">📚 Quiz Categories</h3>
            <div class="categories-grid" id="categoriesGrid"></div>

            <!-- User Stats -->
            <div class="card">
                <h3 style="margin-bottom: 12px;">📊 Your Stats</h3>
                <div class="stats-row">
                    <div class="stat-item">
                        <div>🏆</div>
                        <div class="stat-value" id="totalScore">0</div>
                        <div style="font-size: 12px;">Total Score</div>
                    </div>
                    <div class="stat-item">
                        <div>🎮</div>
                        <div class="stat-value" id="gamesPlayed">0</div>
                        <div style="font-size: 12px;">Games Played</div>
                    </div>
                    <div class="stat-item">
                        <div>📊</div>
                        <div class="stat-value" id="correctRate">0%</div>
                        <div style="font-size: 12px;">Accuracy</div>
                    </div>
                </div>
            </div>

            <!-- Ad Banner -->
            <div class="ad-container">
                <ins class="adsbygoogle"
                    style="display:block"
                    data-ad-client="ca-pub-7709786685996364"
                    data-ad-slot="4892806004"
                    data-ad-format="auto"
                    data-full-width-responsive="true"></ins>
            </div>
        </div>

        <!-- ==================== QUIZ SCREEN ==================== -->
        <div id="quizScreen" class="screen">
            <div class="card">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <div>
                        <div id="quizCategory" style="font-size: 13px; color: #666;">Category</div>
                        <div id="questionNumber" style="font-weight: bold;">Question 1/10</div>
                    </div>
                    <div id="quizTimer" class="timer">30</div>
                </div>
                <div id="questionText" style="font-size: 18px; margin: 18px 0; font-weight: bold; line-height: 1.4;"></div>
                <div id="optionsContainer"></div>
            </div>
        </div>

        <!-- ==================== RESULT SCREEN ==================== -->
        <div id="resultScreen" class="screen">
            <div class="card" style="text-align: center;">
                <div id="resultIcon" style="font-size: 70px;">🏆</div>
                <h2 id="resultTitle">Quiz Completed!</h2>
                <div id="resultScore" style="font-size: 22px; margin: 15px 0; font-weight: bold;"></div>
                <div id="resultDetails" style="margin: 15px 0; line-height: 1.8;"></div>
                <button class="btn btn-primary" onclick="goHome()">🏠 Back to Home</button>
                <button class="btn" style="background: #666; margin-top: 8px;" onclick="showScreen('home')">Play Again</button>
            </div>
        </div>

        <!-- ==================== LEADERBOARD SCREEN ==================== -->
        <div id="leaderboardScreen" class="screen">
            <div class="card">
                <div style="display: flex; gap: 8px; margin-bottom: 15px;">
                    <button class="btn" style="flex: 1; padding: 10px;" onclick="loadLeaderboard('weekly')">📅 Weekly</button>
                    <button class="btn" style="flex: 1; padding: 10px;" onclick="loadLeaderboard('monthly')">📆 Monthly</button>
                    <button class="btn" style="flex: 1; padding: 10px;" onclick="loadLeaderboard('all')">🏆 All Time</button>
                </div>
                <div id="leaderboardList"></div>
            </div>
        </div>

        <!-- ==================== WALLET SCREEN ==================== -->
        <div id="walletScreen" class="screen">
            <div class="card" style="text-align: center;">
                <div style="font-size: 45px;">💰</div>
                <h2 id="walletBalance">0 Coins</h2>
                <div style="margin: 15px 0;">
                    <button class="btn btn-secondary" onclick="showReferralModal()">📱 Invite Friends & Earn 20 Coins</button>
                </div>
            </div>
            <div class="card">
                <h3>📜 Transaction History</h3>
                <div id="transactionList"></div>
            </div>
        </div>

        <!-- ==================== PROFILE SCREEN ==================== -->
        <div id="profileScreen" class="screen">
            <div class="card" style="text-align: center;">
                <div style="font-size: 50px;">👤</div>
                <input type="text" id="profileName" placeholder="Enter your name">
                <div id="profilePhone" style="margin: 8px 0; font-size: 14px; color: #666;"></div>
                <div id="profileJoinDate" style="margin: 8px 0; font-size: 12px; color: #999;"></div>
                <button class="btn btn-primary" onclick="updateProfile()">💾 Save Profile</button>
                <button class="btn" style="background: #f44336; color: white; margin-top: 8px;" onclick="logout()">🚪 Logout</button>
                <button class="btn" style="background: #666; margin-top: 8px;" onclick="toggleDarkMode()">🌙 Dark Mode</button>
            </div>
        </div>

        <!-- Bottom Navigation -->
        <div class="bottom-nav">
            <div class="nav-item" onclick="showScreen('home')">
                <div class="nav-icon">🏠</div>
                <div class="nav-label">Home</div>
            </div>
            <div class="nav-item" onclick="showScreen('leaderboard')">
                <div class="nav-icon">🏆</div>
                <div class="nav-label">Rank</div>
            </div>
            <div class="nav-item" onclick="showScreen('wallet')">
                <div class="nav-icon">💰</div>
                <div class="nav-label">Wallet</div>
            </div>
            <div class="nav-item" onclick="showScreen('profile')">
                <div class="nav-icon">👤</div>
                <div class="nav-label">Profile</div>
            </div>
        </div>
    </div>

    <!-- Referral Modal -->
    <div id="referralModal" class="modal" onclick="closeModal()">
        <div class="modal-content" onclick="event.stopPropagation()">
            <h3>🎁 Invite Friends</h3>
            <p style="margin: 15px 0;">Share your referral code and earn <strong>20 coins</strong> for each friend who joins!</p>
            <div id="referralCodeDisplay" style="background: #f0f0f0; padding: 12px; border-radius: 10px; font-size: 20px; letter-spacing: 2px; font-weight: bold;"></div>
            <button class="btn btn-primary" style="margin-top: 15px;" onclick="copyReferralCode()">📋 Copy Code</button>
            <button class="btn" style="margin-top: 8px;" onclick="closeModal()">Close</button>
        </div>
    </div>

    <script>
        // ==================== LOCAL STORAGE DATA (No Firebase Required) ====================
        // This version uses localStorage so you can test immediately without Firebase setup
        
        let currentUser = null;
        let currentQuizzes = [];
        let currentQuestionIndex = 0;
        let currentScore = 0;
        let currentCorrectAnswers = 0;
        let timerInterval = null;
        let timeLeft = 30;
        let isAnswered = false;
        let currentCategory = '';
        let isDailyQuizMode = false;

        // Categories Data
        const categories = [
            { name: 'GK', icon: '🌍', color: '#4CAF50' },
            { name: 'India GK', icon: '🇮🇳', color: '#FF9800' },
            { name: 'Science', icon: '🔬', color: '#2196F3' },
            { name: 'History', icon: '📜', color: '#795548' },
            { name: 'Geography', icon: '🗺️', color: '#009688' },
            { name: 'Computer', icon: '💻', color: '#9C27B0' },
            { name: 'Agriculture', icon: '🌾', color: '#8BC34A' },
            { name: 'Current Affairs', icon: '📰', color: '#F44336' }
        ];

        // Complete Quiz Database
        const quizDatabase = {
            'GK': [
                { question: 'What is the capital of India?', options: ['Mumbai', 'New Delhi', 'Kolkata', 'Chennai'], correct: 1, points: 10 },
                { question: 'Who wrote the National Anthem of India?', options: ['Bankim Chandra', 'Rabindranath Tagore', 'Sarojini Naidu', 'Mahatma Gandhi'], correct: 1, points: 10 },
                { question: 'Which is the largest planet in our solar system?', options: ['Earth', 'Mars', 'Jupiter', 'Saturn'], correct: 2, points: 10 },
                { question: 'Who is known as the Father of Indian Constitution?', options: ['Mahatma Gandhi', 'Jawaharlal Nehru', 'Dr. B.R. Ambedkar', 'Sardar Patel'], correct: 2, points: 10 },
                { question: 'What is the national flower of India?', options: ['Rose', 'Marigold', 'Lotus', 'Sunflower'], correct: 2, points: 10 },
                { question: 'Which color is the national flag top band?', options: ['White', 'Green', 'Saffron', 'Blue'], correct: 2, points: 10 },
                { question: 'Who was the first Prime Minister of India?', options: ['Mahatma Gandhi', 'Jawaharlal Nehru', 'Sardar Patel', 'Rajendra Prasad'], correct: 1, points: 10 },
                { question: 'What is the national bird of India?', options: ['Eagle', 'Peacock', 'Sparrow', 'Crow'], correct: 1, points: 10 },
                { question: 'Which is the highest mountain peak in India?', options: ['K2', 'Kangchenjunga', 'Nanda Devi', 'Mount Everest'], correct: 1, points: 10 },
                { question: 'Who invented the light bulb?', options: ['Newton', 'Einstein', 'Edison', 'Tesla'], correct: 2, points: 10 }
            ],
            'India GK': [
                { question: 'Which is the longest river in India?', options: ['Yamuna', 'Godavari', 'Ganga', 'Brahmaputra'], correct: 2, points: 10 },
                { question: 'What is the national animal of India?', options: ['Lion', 'Elephant', 'Tiger', 'Peacock'], correct: 2, points: 10 },
                { question: 'Which state is known as "God\'s Own Country"?', options: ['Goa', 'Kerala', 'Karnataka', 'Tamil Nadu'], correct: 1, points: 10 },
                { question: 'What is the national sport of India?', options: ['Cricket', 'Hockey', 'Football', 'Kabaddi'], correct: 1, points: 10 },
                { question: 'Who built the Taj Mahal?', options: ['Akbar', 'Shah Jahan', 'Aurangzeb', 'Babur'], correct: 1, points: 10 }
            ],
            'Science': [
                { question: 'What is the chemical symbol for Gold?', options: ['Go', 'Gd', 'Au', 'Ag'], correct: 2, points: 10 },
                { question: 'Which planet is known as the Red Planet?', options: ['Mars', 'Venus', 'Jupiter', 'Saturn'], correct: 0, points: 10 },
                { question: 'What is the hardest natural substance?', options: ['Iron', 'Gold', 'Diamond', 'Platinum'], correct: 2, points: 10 },
                { question: 'Which gas is most abundant in Earth\'s atmosphere?', options: ['Oxygen', 'Carbon Dioxide', 'Nitrogen', 'Argon'], correct: 2, points: 10 },
                { question: 'What is the boiling point of water?', options: ['80°C', '90°C', '100°C', '110°C'], correct: 2, points: 10 }
            ],
            'History': [
                { question: 'Who was the first Emperor of the Maurya Empire?', options: ['Ashoka', 'Bindusara', 'Chandragupta Maurya', 'Samudragupta'], correct: 2, points: 10 },
                { question: 'When did India gain independence?', options: ['1945', '1946', '1947', '1948'], correct: 2, points: 10 },
                { question: 'Who was known as the Iron Man of India?', options: ['Jawaharlal Nehru', 'Mahatma Gandhi', 'Sardar Patel', 'Subhash Bose'], correct: 2, points: 10 }
            ],
            'Geography': [
                { question: 'Which is the largest desert in the world?', options: ['Gobi', 'Sahara', 'Thar', 'Kalahari'], correct: 1, points: 10 },
                { question: 'Which is the longest river in the world?', options: ['Amazon', 'Nile', 'Yangtze', 'Mississippi'], correct: 1, points: 10 },
                { question: 'Which is the smallest continent?', options: ['Europe', 'Australia', 'Antarctica', 'South America'], correct: 1, points: 10 }
            ],
            'Computer': [
                { question: 'What does CPU stand for?', options: ['Central Processing Unit', 'Computer Personal Unit', 'Central Program Unit', 'Core Processing Unit'], correct: 0, points: 10 },
                { question: 'Who is the founder of Microsoft?', options: ['Steve Jobs', 'Bill Gates', 'Mark Zuckerberg', 'Elon Musk'], correct: 1, points: 10 },
                { question: 'What does RAM stand for?', options: ['Read Access Memory', 'Random Access Memory', 'Run Access Memory', 'Rapid Access Memory'], correct: 1, points: 10 }
            ],
            'Agriculture': [
                { question: 'Which crop is known as the "Golden Fiber"?', options: ['Cotton', 'Jute', 'Silk', 'Wool'], correct: 1, points: 10 },
                { question: 'Which is the main kharif crop in India?', options: ['Wheat', 'Rice', 'Barley', 'Mustard'], correct: 1, points: 10 },
                { question: 'What is the scientific name of rice?', options: ['Triticum', 'Oryza', 'Zea', 'Saccharum'], correct: 1, points: 10 }
            ],
            'Current Affairs': [
                { question: 'Who is the current Prime Minister of India?', options: ['Rahul Gandhi', 'Narendra Modi', 'Amit Shah', 'Manmohan Singh'], correct: 1, points: 10 },
                { question: 'Who is the current President of India?', options: ['Ram Nath Kovind', 'Droupadi Murmu', 'Pranab Mukherjee', 'Venkaiah Naidu'], correct: 1, points: 10 },
                { question: 'Where was G20 Summit 2023 held?', options: ['New Delhi', 'Mumbai', 'Bengaluru', 'Hyderabad'], correct: 0, points: 10 }
            ]
        };

        // ==================== LOCAL STORAGE FUNCTIONS ====================
        function saveUserToLocal(user) {
            localStorage.setItem('currentUser', JSON.stringify(user));
        }

        function getUserFromLocal() {
            const user = localStorage.getItem('currentUser');
            return user ? JSON.parse(user) : null;
        }

        function saveUsers(users) {
            localStorage.setItem('allUsers', JSON.stringify(users));
        }

        function getUsers() {
            const users = localStorage.getItem('allUsers');
            return users ? JSON.parse(users) : {};
        }

        function saveTransactions(transactions) {
            localStorage.setItem('transactions', JSON.stringify(transactions));
        }

        function getTransactions() {
            const txn = localStorage.getItem('transactions');
            return txn ? JSON.parse(txn) : [];
        }

        function saveResults(results) {
            localStorage.setItem('quizResults', JSON.stringify(results));
        }

        function getResults() {
            const results = localStorage.getItem('quizResults');
            return results ? JSON.parse(results) : [];
        }

        // ==================== AUTHENTICATION ====================
        function sendOTP() {
            const phone = document.getElementById('phoneInput').value;
            if (phone.length !== 10) {
                alert('Please enter a valid 10-digit phone number');
                return;
            }

            // For demo, show OTP section
            document.getElementById('otpSection').style.display = 'block';
            document.getElementById('sendOtpBtn').style.display = 'none';
            alert('Demo OTP sent! Use OTP: 123456');
        }

        function verifyOTP() {
            const otp = document.getElementById('otpInput').value;
            const phone = document.getElementById('phoneInput').value;
            const referralCode = document.getElementById('referralCodeInput').value;

            // For demo, accept any 6-digit OTP or default 123456
            if (otp === '123456' || (otp.length === 6 && /^\d+$/.test(otp))) {
                handleUserSignIn(phone, referralCode);
            } else {
                alert('Invalid OTP. Use 123456 for testing.');
            }
        }

        function handleUserSignIn(phone, referralCode) {
            const users = getUsers();
            let user = users[phone];

            if (!user) {
                // Create new user
                const generatedReferralCode = 'GYAN' + Math.random().toString(36).substring(2, 6).toUpperCase();
                user = {
                    phone: phone,
                    name: '',
                    coins: 50,
                    totalScore: 0,
                    totalGames: 0,
                    correctAnswers: 0,
                    joinDate: new Date().toISOString(),
                    referralCode: generatedReferralCode,
                    referredBy: referralCode || ''
                };
                users[phone] = user;
                saveUsers(users);

                // Handle referral bonus
                if (referralCode) {
                    for (let p in users) {
                        if (users[p].referralCode === referralCode) {
                            users[p].coins += 20;
                            saveTransactions([...getTransactions(), {
                                userId: p,
                                amount: 20,
                                type: 'referral',
                                description: 'Referral bonus',
                                timestamp: new Date().toISOString()
                            }]);
                            break;
                        }
                    }
                    user.coins += 30; // Welcome + referral bonus
                    users[phone] = user;
                    saveUsers(users);
                }
            }

            currentUser = user;
            saveUserToLocal(currentUser);
            loadUserData();
            showScreen('home');
            loadCategories();
            loadLeaderboard('weekly');
            initializeAds();
        }

        async function loadUserData() {
            if (currentUser) {
                document.getElementById('coinBalance').innerText = currentUser.coins || 0;
                document.getElementById('totalScore').innerText = currentUser.totalScore || 0;
                document.getElementById('gamesPlayed').innerText = currentUser.totalGames || 0;
                document.getElementById('walletBalance').innerHTML = (currentUser.coins || 0) + ' Coins';
                
                const correctRate = currentUser.totalGames > 0 ? 
                    Math.round((currentUser.correctAnswers || 0) / (currentUser.totalGames * 10) * 100) : 0;
                document.getElementById('correctRate').innerText = correctRate + '%';
                
                document.getElementById('profileName').value = currentUser.name || '';
                document.getElementById('profilePhone').innerHTML = '📱 ' + (currentUser.phone || '');
                document.getElementById('profileJoinDate').innerHTML = '📅 Joined: ' + new Date(currentUser.joinDate).toLocaleDateString();
                
                document.getElementById('referralCodeDisplay').innerHTML = currentUser.referralCode || '';
                document.getElementById('userNameDisplay').innerHTML = currentUser.name ? currentUser.name.substring(0, 2).toUpperCase() : '👤';
                document.getElementById('userInfo').style.display = 'flex';
                
                loadTransactions();
            }
        }

        function updateProfile() {
            const name = document.getElementById('profileName').value;
            if (name) {
                const users = getUsers();
                users[currentUser.phone].name = name;
                saveUsers(users);
                currentUser.name = name;
                saveUserToLocal(currentUser);
                document.getElementById('userNameDisplay').innerHTML = name.substring(0, 2).toUpperCase();
                alert('Profile updated successfully!');
            }
        }

        function logout() {
            localStorage.removeItem('currentUser');
            currentUser = null;
            showScreen('login');
            document.getElementById('phoneInput').value = '';
            document.getElementById('referralCodeInput').value = '';
            document.getElementById('otpSection').style.display = 'none';
            document.getElementById('sendOtpBtn').style.display = 'block';
            document.getElementById('otpInput').value = '';
        }

        // ==================== QUIZ FUNCTIONS ====================
        function loadCategories() {
            const grid = document.getElementById('categoriesGrid');
            grid.innerHTML = categories.map(cat => `
                <div class="category-card" style="background: linear-gradient(135deg, ${cat.color}, ${cat.color}dd)" 
                     onclick="startQuiz('${cat.name}')">
                    <div class="category-icon">${cat.icon}</div>
                    <div>${cat.name}</div>
                </div>
            `).join('');
        }

        function startQuiz(category) {
            isDailyQuizMode = false;
            currentCategory = category;
            const quizzes = quizDatabase[category];
            if (!quizzes || quizzes.length === 0) {
                alert('No questions available for this category yet.');
                return;
            }
            currentQuizzes = [...quizzes];
            currentQuestionIndex = 0;
            currentScore = 0;
            currentCorrectAnswers = 0;
            startQuestion();
            showScreen('quiz');
        }

        function startDailyQuiz() {
            isDailyQuizMode = true;
            currentCategory = 'Daily Quiz';
            let allQuestions = [];
            Object.keys(quizDatabase).forEach(cat => {
                allQuestions = [...allQuestions, ...quizDatabase[cat]];
            });
            currentQuizzes = allQuestions.slice(0, 10);
            if (currentQuizzes.length < 10) {
                currentQuizzes = allQuestions;
            }
            currentQuestionIndex = 0;
            currentScore = 0;
            currentCorrectAnswers = 0;
            startQuestion();
            showScreen('quiz');
        }

        function startQuestion() {
            if (currentQuestionIndex >= currentQuizzes.length) {
                finishQuiz();
                return;
            }

            isAnswered = false;
            timeLeft = 30;
            const question = currentQuizzes[currentQuestionIndex];
            
            document.getElementById('quizCategory').innerText = isDailyQuizMode ? 'Daily Quiz Challenge' : currentCategory;
            document.getElementById('questionNumber').innerHTML = `Question ${currentQuestionIndex + 1}/${currentQuizzes.length}`;
            document.getElementById('questionText').innerHTML = question.question;
            
            const optionsHtml = question.options.map((opt, idx) => `
                <button class="option-btn" onclick="checkAnswer(${idx})">
                    ${String.fromCharCode(65 + idx)}. ${opt}
                </button>
            `).join('');
            
            document.getElementById('optionsContainer').innerHTML = optionsHtml;
            
            startTimer();
        }

        function startTimer() {
            if (timerInterval) clearInterval(timerInterval);
            
            const timerElement = document.getElementById('quizTimer');
            timerElement.innerText = timeLeft;
            timerElement.classList.remove('warning');
            
            timerInterval = setInterval(() => {
                if (!isAnswered && timeLeft > 0) {
                    timeLeft--;
                    timerElement.innerText = timeLeft;
                    
                    if (timeLeft <= 5) {
                        timerElement.classList.add('warning');
                    }
                    
                    if (timeLeft === 0) {
                        clearInterval(timerInterval);
                        handleTimeout();
                    }
                }
            }, 1000);
        }

        function checkAnswer(selectedIndex) {
            if (isAnswered) return;
            
            isAnswered = true;
            clearInterval(timerInterval);
            
            const question = currentQuizzes[currentQuestionIndex];
            const isCorrect = selectedIndex === question.correct;
            
            const buttons = document.querySelectorAll('.option-btn');
            buttons[question.correct].classList.add('correct');
            
            if (isCorrect) {
                buttons[selectedIndex].classList.add('correct');
                currentScore += question.points;
                currentCorrectAnswers++;
            } else {
                buttons[selectedIndex].classList.add('wrong');
            }
            
            buttons.forEach(btn => btn.classList.add('disabled'));
            
            setTimeout(() => {
                currentQuestionIndex++;
                startQuestion();
            }, 1200);
        }

        function handleTimeout() {
            if (isAnswered) return;
            
            isAnswered = true;
            const question = currentQuizzes[currentQuestionIndex];
            const buttons = document.querySelectorAll('.option-btn');
            buttons[question.correct].classList.add('correct');
            buttons.forEach(btn => btn.classList.add('disabled'));
            
            setTimeout(() => {
                currentQuestionIndex++;
                startQuestion();
            }, 1200);
        }

        function finishQuiz() {
            const coinsEarned = Math.floor(currentScore / 2);
            const percentage = Math.round((currentCorrectAnswers / currentQuizzes.length) * 100);
            
            // Update user stats
            const users = getUsers();
            users[currentUser.phone].totalScore = (users[currentUser.phone].totalScore || 0) + currentScore;
            users[currentUser.phone].coins = (users[currentUser.phone].coins || 0) + coinsEarned;
            users[currentUser.phone].totalGames = (users[currentUser.phone].totalGames || 0) + 1;
            users[currentUser.phone].correctAnswers = (users[currentUser.phone].correctAnswers || 0) + currentCorrectAnswers;
            saveUsers(users);
            
            // Update current user
            currentUser = users[currentUser.phone];
            saveUserToLocal(currentUser);
            
            // Save result
            const results = getResults();
            results.push({
                userId: currentUser.phone,
                category: currentCategory,
                score: currentScore,
                totalQuestions: currentQuizzes.length,
                correctAnswers: currentCorrectAnswers,
                coinsEarned: coinsEarned,
                completedAt: new Date().toISOString()
            });
            saveResults(results);
            
            // Save transaction
            const transactions = getTransactions();
            transactions.push({
                userId: currentUser.phone,
                amount: coinsEarned,
                type: 'earn',
                description: `Earned from ${currentCategory} quiz`,
                timestamp: new Date().toISOString()
            });
            saveTransactions(transactions);
            
            // Show result
            document.getElementById('resultIcon').innerHTML = percentage >= 70 ? '🏆🎉' : '📚👍';
            document.getElementById('resultTitle').innerHTML = percentage >= 70 ? 'Excellent Performance!' : 'Good Try!';
            document.getElementById('resultScore').innerHTML = `Score: ${currentScore} points`;
            document.getElementById('resultDetails').innerHTML = `
                ✅ Correct: ${currentCorrectAnswers}/${currentQuizzes.length}<br>
                🪙 Coins Earned: +${coinsEarned}<br>
                📊 Accuracy: ${percentage}%<br>
                💰 Total Coins: ${currentUser.coins}
            `;
            
            showScreen('result');
            loadUserData();
        }

        // ==================== LEADERBOARD ====================
        async function loadLeaderboard(period) {
            const users = getUsers();
            const results = getResults();
            
            let startDate = new Date();
            if (period === 'weekly') startDate.setDate(startDate.getDate() - 7);
            else if (period === 'monthly') startDate.setMonth(startDate.getMonth() - 1);
            else startDate = new Date(2020, 0, 1);
            
            const userScores = {};
            results.forEach(result => {
                const resultDate = new Date(result.completedAt);
                if (resultDate >= startDate) {
                    if (!userScores[result.userId]) {
                        userScores[result.userId] = { score: 0, games: 0 };
                    }
                    userScores[result.userId].score += result.score;
                    userScores[result.userId].games++;
                }
            });
            
            const leaderboard = [];
            for (const [userId, data] of Object.entries(userScores)) {
                const userName = users[userId]?.name || userId.substring(0, 6);
                leaderboard.push({
                    name: userName,
                    score: data.score,
                    games: data.games
                });
            }
            
            leaderboard.sort((a, b) => b.score - a.score);
            
            const container = document.getElementById('leaderboardList');
            if (leaderboard.length === 0) {
                container.innerHTML = '<div style="text-align: center; padding: 20px;">No data available. Play some quizzes first!</div>';
                return;
            }
            
            container.innerHTML = leaderboard.slice(0, 50).map((user, index) => `
                <div class="leaderboard-item">
                    <div class="rank ${index < 3 ? 'rank-' + (index + 1) : ''}">
                        ${index === 0 ? '🥇' : index === 1 ? '🥈' : index === 2 ? '🥉' : `${index + 1}`}
                    </div>
                    <div style="flex: 1;">${user.name}</div>
                    <div><strong>${user.score}</strong> pts</div>
                    <div style="font-size: 11px; color: #888;">${user.games} games</div>
                </div>
            `).join('');
        }

        // ==================== WALLET ====================
        function loadTransactions() {
            const transactions = getTransactions();
            const userTxns = transactions.filter(t => t.userId === currentUser.phone).reverse().slice(0, 20);
            
            const container = document.getElementById('transactionList');
            if (userTxns.length === 0) {
                container.innerHTML = '<div style="text-align: center; padding: 20px;">No transactions yet. Play quizzes to earn coins!</div>';
                return;
            }
            
            container.innerHTML = userTxns.map(txn => {
                const icon = txn.type === 'earn' ? '➕' : txn.type === 'referral' ? '🎁' : '💰';
                const date = new Date(txn.timestamp).toLocaleDateString();
                return `
                    <div class="transaction-item">
                        <div>
                            <span style="font-size: 18px;">${icon}</span>
                            <span style="margin-left: 8px;">${txn.description}</span>
                            <div style="font-size: 10px; color: #888; margin-top: 2px;">${date}</div>
                        </div>
                        <div style="color: ${txn.amount > 0 ? '#4CAF50' : '#f44336'}; font-weight: bold;">
                            ${txn.amount > 0 ? '+' : ''}${txn.amount} coins
                        </div>
                    </div>
                `;
            }).join('');
        }

        // ==================== UI FUNCTIONS ====================
        function showScreen(screenName) {
            const screens = ['login', 'home', 'quiz', 'result', 'leaderboard', 'wallet', 'profile'];
            screens.forEach(screen => {
                const element = document.getElementById(screen + 'Screen');
                if (element) element.classList.remove('active');
            });
            
            const activeScreen = document.getElementById(screenName + 'Screen');
            if (activeScreen) activeScreen.classList.add('active');
            
            // Update bottom nav
            const navItems = document.querySelectorAll('.nav-item');
            navItems.forEach(item => item.classList.remove('active'));
            
            const navMap = { home: 0, leaderboard: 1, wallet: 2, profile: 3 };
            if (navMap[screenName] !== undefined && navItems[navMap[screenName]]) {
                navItems[navMap[screenName]].classList.add('active');
            }
            
            if (screenName === 'wallet' && currentUser) loadTransactions();
            if (screenName === 'leaderboard') loadLeaderboard('weekly');
        }

        function goHome() {
            showScreen('home');
            loadUserData();
        }

        function showReferralModal() {
            document.getElementById('referralModal').style.display = 'flex';
        }

        function closeModal() {
            document.getElementById('referralModal').style.display = 'none';
        }

        function copyReferralCode() {
            const code = document.getElementById('referralCodeDisplay').innerHTML;
            navigator.clipboard.writeText(code);
            alert('Referral code copied! Share with friends to earn 20 coins each!');
        }

        function toggleDarkMode() {
            document.body.classList.toggle('dark-mode');
            localStorage.setItem('darkMode', document.body.classList.contains('dark-mode'));
        }

        function initializeAds() {
            try {
                if (typeof adsbygoogle !== 'undefined') {
                    (adsbygoogle = window.adsbygoogle || []).push({});
                }
            } catch(e) {
                console.log('AdMob loading...');
            }
        }

        // ==================== INITIALIZATION ====================
        // Check for existing user
        const savedUser = getUserFromLocal();
        if (savedUser) {
            currentUser = savedUser;
            loadUserData();
            showScreen('home');
            loadCategories();
            loadLeaderboard('weekly');
        } else {
            showScreen('login');
        }

        // Check for saved dark mode
        if (localStorage.getItem('darkMode') === 'true') {
            document.body.classList.add('dark-mode');
        }

        // Initialize ads after page load
        window.addEventListener('load', () => {
            setTimeout(initializeAds, 1000);
        });
    </script>
</body>
</html>
