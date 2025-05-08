<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>عقاراتي - TikTok للعقارات</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Tajawal:wght@400;500;700&display=swap');
        
        body {
            font-family: 'Tajawal', sans-serif;
            background-color: #000;
            color: #fff;
            margin: 0;
            padding: 0;
            overflow-x: hidden;
        }
        
        .video-container {
            height: 100vh;
            width: 100%;
            position: relative;
            overflow: hidden;
        }
        
        .video-player {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        
        .property-info {
            position: absolute;
            bottom: 80px;
            right: 15px;
            left: 15px;
            z-index: 10;
        }
        
        .property-features {
            display: flex;
            gap: 10px;
            margin-bottom: 8px;
        }
        
        .feature-icon {
            width: 24px;
            height: 24px;
            border: 1px solid white;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            background: rgba(0,0,0,0.3);
            font-size: 10px;
        }
        
        .right-sidebar {
            position: absolute;
            bottom: 120px;
            right: 10px;
            display: flex;
            flex-direction: column;
            gap: 15px;
            z-index: 10;
        }
        
        .left-sidebar {
            position: absolute;
            bottom: 120px;
            left: 10px;
            display: flex;
            flex-direction: column;
            gap: 15px;
            z-index: 10;
        }
        
        .action-btn {
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        
        .action-count {
            font-size: 10px;
            margin-top: 3px;
        }
        
        .top-tabs {
            position: absolute;
            top: 15px;
            left: 0;
            right: 0;
            display: flex;
            justify-content: center;
            gap: 15px;
            z-index: 10;
        }
        
        .tab {
            color: rgba(255,255,255,0.7);
            font-size: 12px;
            position: relative;
        }
        
        .tab.active {
            color: white;
            font-weight: 500;
        }
        
        .tab.active:after {
            content: '';
            position: absolute;
            bottom: -3px;
            left: 0;
            right: 0;
            height: 2px;
            background: white;
        }
        
        .location-filter {
            position: absolute;
            top: 15px;
            right: 15px;
            z-index: 10;
        }
        
        .dropdown {
            background: rgba(0,0,0,0.5);
            border: 1px solid rgba(255,255,255,0.2);
            border-radius: 5px;
            padding: 4px 8px;
            font-size: 10px;
            color: white;
        }
        
        .profile-verified {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            width: 14px;
            height: 14px;
            background: #000;
            border-radius: 50%;
            margin-right: 4px;
        }
        
        .profile-verified i {
            color: gold;
            font-size: 8px;
        }
        
        .phone-options {
            position: absolute;
            bottom: 40px;
            right: 40px;
            background: rgba(0,0,0,0.8);
            border-radius: 8px;
            padding: 8px;
            display: none;
            flex-direction: column;
            gap: 8px;
            font-size: 12px;
        }
        
        .phone-options.show {
            display: flex;
        }
        
        .phone-option {
            display: flex;
            align-items: center;
            gap: 8px;
            padding: 4px 8px;
            border-radius: 4px;
        }
        
        .phone-option:hover {
            background: rgba(255,255,255,0.1);
        }
        
        .recording-timer {
            position: absolute;
            top: 15px;
            right: 15px;
            background: rgba(255,0,0,0.7);
            color: white;
            padding: 4px 8px;
            border-radius: 15px;
            font-size: 10px;
            display: none;
            z-index: 100;
        }
        
        .recording-controls {
            position: absolute;
            bottom: 15px;
            left: 0;
            right: 0;
            display: flex;
            justify-content: center;
            gap: 15px;
            z-index: 100;
        }
        
        .record-btn {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background: white;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
        }
        
        .record-btn:after {
            content: '';
            position: absolute;
            width: 60px;
            height: 60px;
            border: 2px solid white;
            border-radius: 50%;
            animation: pulse 1.5s infinite;
        }
        
        @keyframes pulse {
            0% { transform: scale(0.9); opacity: 1; }
            70% { transform: scale(1.3); opacity: 0; }
            100% { transform: scale(0.9); opacity: 0; }
        }
        
        .profile-page {
            padding: 15px;
            display: none;
        }
        
        .profile-header {
            display: flex;
            align-items: center;
            gap: 15px;
            margin-bottom: 15px;
        }
        
        .profile-pic {
            width: 70px;
            height: 70px;
            border-radius: 50%;
            background: #333;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 24px;
        }
        
        .profile-actions {
            display: flex;
            gap: 8px;
            margin-top: 10px;
        }
        
        .profile-btn {
            padding: 6px 12px;
            border-radius: 4px;
            font-size: 12px;
        }
        
        /* Updated bottom navigation */
        .bottom-nav {
            position: fixed;
            bottom: 0;
            left: 0;
            right: 0;
            background: rgba(0, 0, 0, 0.9);
            border-top: 1px solid rgba(255, 255, 255, 0.2);
            display: flex;
            justify-content: space-around;
            padding: 10px 0;
            z-index: 50;
        }
        
        .nav-btn {
            color: white;
            font-size: 18px;
            position: relative;
        }
        
        .nav-btn.active {
            color: #1DA1F2;
        }
        
        .nav-badge {
            position: absolute;
            top: -5px;
            right: -5px;
            background: red;
            color: white;
            border-radius: 50%;
            width: 14px;
            height: 14px;
            font-size: 9px;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        
        /* Messages page */
        .messages-page {
            display: none;
            padding: 12px;
        }
        
        .message-item {
            display: flex;
            align-items: center;
            gap: 12px;
            padding: 10px 0;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        .message-avatar {
            width: 45px;
            height: 45px;
            border-radius: 50%;
            background: #333;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 18px;
        }
        
        .message-content {
            flex: 1;
        }
        
        .message-name {
            font-weight: 500;
            margin-bottom: 2px;
            font-size: 14px;
        }
        
        .message-text {
            color: rgba(255, 255, 255, 0.7);
            font-size: 12px;
        }
        
        .message-time {
            color: rgba(255, 255, 255, 0.5);
            font-size: 10px;
        }
        
        .unread-badge {
            background: #1DA1F2;
            width: 8px;
            height: 8px;
            border-radius: 50%;
        }
    </style>
</head>
<body>
    <!-- Main Video Feed -->
    <div class="video-feed">
        <div class="video-container">
            <video class="video-player" autoplay muted loop>
                <source src="https://sample-videos.com/video123/mp4/720/big_buck_bunny_720p_1mb.mp4" type="video/mp4">
            </video>
            
            <!-- Property Info -->
            <div class="property-info">
                <div class="property-features">
                    <div class="feature-icon">
                        <i class="fas fa-toilet"></i>
                    </div>
                    <div class="feature-icon">
                        <i class="fas fa-bed"></i>
                    </div>
                    <div class="feature-icon">
                        <i class="fas fa-couch"></i>
                    </div>
                    <div class="feature-icon">
                        <i class="fas fa-utensils"></i>
                    </div>
                    <div class="feature-icon">
                        <i class="fas fa-ruler-combined"></i>
                    </div>
                </div>
                <p class="text-white text-xs">فيلا فاخرة للبيع في حي الياسمين بالرياض مساحة 600م² تشطيب سوبر لوكس</p>
            </div>
            
            <!-- Right Sidebar Actions (Profile, Like, Comment, etc.) -->
            <div class="right-sidebar">
                <div class="action-btn">
                    <div class="w-8 h-8 rounded-full bg-gray-800 flex items-center justify-center">
                        <img src="https://randomuser.me/api/portraits/men/1.jpg" class="w-6 h-6 rounded-full" alt="Profile">
                    </div>
                    <span class="text-white text-2xs mt-1">+ متابعة</span>
                </div>
                
                <div class="action-btn">
                    <div class="w-10 h-10 rounded-full bg-gray-800 flex items-center justify-center">
                        <i class="fas fa-heart text-white text-lg"></i>
                    </div>
                    <span class="action-count">1.2K</span>
                </div>
                
                <div class="action-btn">
                    <div class="w-10 h-10 rounded-full bg-gray-800 flex items-center justify-center">
                        <i class="fas fa-comment text-white text-lg"></i>
                    </div>
                    <span class="action-count">243</span>
                </div>
                
                <div class="action-btn" id="phone-btn">
                    <div class="w-10 h-10 rounded-full bg-gray-800 flex items-center justify-center">
                        <i class="fas fa-phone text-white text-lg"></i>
                    </div>
                    <div class="phone-options" id="phone-options">
                        <div class="phone-option">
                            <i class="fab fa-whatsapp text-green-500 text-sm"></i>
                            <span>واتساب</span>
                        </div>
                        <div class="phone-option">
                            <i class="fas fa-envelope text-blue-400 text-sm"></i>
                            <span>رسالة خاصة</span>
                        </div>
                        <div class="phone-option">
                            <i class="fas fa-phone-alt text-white text-sm"></i>
                            <span>اتصال مباشر</span>
                        </div>
                    </div>
                </div>
                
                <div class="action-btn">
                    <div class="w-10 h-10 rounded-full bg-gray-800 flex items-center justify-center">
                        <i class="fas fa-share text-white text-lg"></i>
                    </div>
                    <span class="action-count">مشاركة</span>
                </div>
            </div>
            
            <!-- Top Tabs -->
            <div class="top-tabs">
                <div class="tab active">للبيع</div>
                <div class="tab">للإيجار</div>
                <div class="tab">للاستثمار</div>
            </div>
            
            <!-- Location Filter (Moved to right side) -->
            <div class="location-filter">
                <select class="dropdown mb-2">
                    <option>الرياض</option>
                    <option>جدة</option>
                    <option>الدمام</option>
                    <option>مكة</option>
                    <option>المدينة</option>
                </select>
                <select class="dropdown">
                    <option>فلل</option>
                    <option>شقق</option>
                    <option>أراضي</option>
                    <option>فنادق</option>
                    <option>شاليهات</option>
                </select>
            </div>
        </div>
        
        <!-- Add more video containers for scrolling effect -->
        <div class="video-container">
            <video class="video-player" autoplay muted loop>
                <source src="https://sample-videos.com/video123/mp4/720/big_buck_bunny_720p_1mb.mp4" type="video/mp4">
            </video>
            
            <div class="property-info">
                <div class="property-features">
                    <div class="feature-icon">
                        <i class="fas fa-toilet"></i>
                    </div>
                    <div class="feature-icon">
                        <i class="fas fa-bed"></i>
                    </div>
                    <div class="feature-icon">
                        <i class="fas fa-utensils"></i>
                    </div>
                </div>
                <p class="text-white text-xs">شقة للإيجار في حي الصحافة بالرياض 3 غرف وصالة تشطيب حديث</p>
            </div>
            
            <div class="right-sidebar">
                <div class="action-btn">
                    <div class="w-8 h-8 rounded-full bg-gray-800 flex items-center justify-center">
                        <img src="https://randomuser.me/api/portraits/women/1.jpg" class="w-6 h-6 rounded-full" alt="Profile">
                    </div>
                    <span class="text-white text-2xs mt-1">+ متابعة</span>
                </div>
                
                <div class="action-btn">
                    <div class="w-10 h-10 rounded-full bg-gray-800 flex items-center justify-center">
                        <i class="fas fa-heart text-white text-lg"></i>
                    </div>
                    <span class="action-count">876</span>
                </div>
                
                <div class="action-btn">
                    <div class="w-10 h-10 rounded-full bg-gray-800 flex items-center justify-center">
                        <i class="fas fa-comment text-white text-lg"></i>
                    </div>
                    <span class="action-count">132</span>
                </div>
                
                <div class="action-btn">
                    <div class="w-10 h-10 rounded-full bg-gray-800 flex items-center justify-center">
                        <i class="fas fa-phone text-white text-lg"></i>
                    </div>
                </div>
                
                <div class="action-btn">
                    <div class="w-10 h-10 rounded-full bg-gray-800 flex items-center justify-center">
                        <i class="fas fa-share text-white text-lg"></i>
                    </div>
                    <span class="action-count">مشاركة</span>
                </div>
            </div>
        </div>
    </div>
    
    <!-- Recording UI -->
    <div class="recording-ui" style="display: none;">
        <div class="recording-timer" id="recording-timer">00:60</div>
        
        <div class="video-container">
            <video class="video-player" id="recording-preview" muted></video>
        </div>
        
        <div class="recording-controls">
            <button class="bg-gray-800 text-white w-10 h-10 rounded-full flex items-center justify-center">
                <i class="fas fa-times text-sm"></i>
            </button>
            <button class="record-btn" id="record-btn">
                <div class="w-4 h-4 bg-red-600 rounded-full" id="record-indicator"></div>
            </button>
            <button class="bg-gray-800 text-white w-10 h-10 rounded-full flex items-center justify-center">
                <i class="fas fa-check text-sm"></i>
            </button>
        </div>
    </div>
    
    <!-- Profile Page -->
    <div class="profile-page" id="profile-page">
        <div class="profile-header">
            <div class="profile-pic">
                <i class="fas fa-home text-white"></i>
            </div>
            <div>
                <h2 class="text-white font-bold text-lg">
                    سلطان السحيمي
                    <span class="profile-verified">
                        <i class="fas fa-check"></i>
                    </span>
                </h2>
                <p class="text-gray-400 text-xs">مالك ومؤسس تطبيق "عقاراتي"</p>
                
                <div class="profile-actions">
                    <button class="profile-btn bg-white text-black">متابعة</button>
                    <button class="profile-btn bg-gray-800 text-white border border-gray-600">مراسلة</button>
                </div>
            </div>
        </div>
        
        <div class="border-t border-gray-800 pt-3">
            <h3 class="text-white font-medium mb-2 text-sm">عقاراتي</h3>
            
            <div class="grid grid-cols-3 gap-1">
                <div class="aspect-square bg-gray-800 flex items-center justify-center">
                    <i class="fas fa-play text-white text-sm"></i>
                </div>
                <div class="aspect-square bg-gray-800 flex items-center justify-center">
                    <i class="fas fa-play text-white text-sm"></i>
                </div>
                <div class="aspect-square bg-gray-800 flex items-center justify-center">
                    <i class="fas fa-play text-white text-sm"></i>
                </div>
                <div class="aspect-square bg-gray-800 flex items-center justify-center">
                    <i class="fas fa-play text-white text-sm"></i>
                </div>
                <div class="aspect-square bg-gray-800 flex items-center justify-center">
                    <i class="fas fa-play text-white text-sm"></i>
                </div>
                <div class="aspect-square bg-gray-800 flex items-center justify-center">
                    <i class="fas fa-play text-white text-sm"></i>
                </div>
            </div>
        </div>
    </div>
    
    <!-- Messages Page -->
    <div class="messages-page" id="messages-page">
        <h2 class="text-white text-lg mb-3">الرسائل</h2>
        
        <div class="message-item">
            <div class="message-avatar">
                <i class="fas fa-user text-white"></i>
            </div>
            <div class="message-content">
                <div class="message-name">أحمد السبيعي</div>
                <div class="message-text">هل الفيلا متوفرة للعرض؟</div>
            </div>
            <div class="message-time">10:30 ص</div>
            <div class="unread-badge"></div>
        </div>
        
        <div class="message-item">
            <div class="message-avatar">
                <i class="fas fa-user text-white"></i>
            </div>
            <div class="message-content">
                <div class="message-name">ناصر القحطاني</div>
                <div class="message-text">أريد معلومات أكثر عن الشقة</div>
            </div>
            <div class="message-time">أمس</div>
        </div>
        
        <div class="message-item">
            <div class="message-avatar">
                <i class="fas fa-user text-white"></i>
            </div>
            <div class="message-content">
                <div class="message-name">شركة العقارية</div>
                <div class="message-text">نود التواصل معك بخصوص عرض خاص</div>
            </div>
            <div class="message-time">٢٤ مايو</div>
        </div>
        
        <div class="message-item">
            <div class="message-avatar">
                <i class="fas fa-user text-white"></i>
            </div>
            <div class="message-content">
                <div class="message-name">محمد الغامدي</div>
                <div class="message-text">شكراً لك على المعلومات</div>
            </div>
            <div class="message-time">٢٠ مايو</div>
        </div>
    </div>
    
    <!-- Bottom Navigation -->
    <div class="bottom-nav">
        <button class="nav-btn active" onclick="showFeed()">
            <i class="fas fa-home"></i>
        </button>
        <button class="nav-btn" onclick="showMessages()">
            <i class="fas fa-envelope"></i>
            <span class="nav-badge">3</span>
        </button>
        <button class="nav-btn" onclick="startRecording()">
            <i class="fas fa-plus-square"></i>
        </button>
        <button class="nav-btn" onclick="showLikes()">
            <i class="fas fa-heart"></i>
        </button>
        <button class="nav-btn" onclick="showProfile()">
            <i class="fas fa-user"></i>
        </button>
    </div>
    
    <script>
        // Phone options toggle
        document.getElementById('phone-btn').addEventListener('click', function() {
            document.getElementById('phone-options').classList.toggle('show');
        });
        
        // Show/hide sections
        function showFeed() {
            document.querySelector('.video-feed').style.display = 'block';
            document.querySelector('.recording-ui').style.display = 'none';
            document.getElementById('profile-page').style.display = 'none';
            document.getElementById('messages-page').style.display = 'none';
            updateNavActive('home');
        }
        
        function showProfile() {
            document.querySelector('.video-feed').style.display = 'none';
            document.querySelector('.recording-ui').style.display = 'none';
            document.getElementById('profile-page').style.display = 'block';
            document.getElementById('messages-page').style.display = 'none';
            updateNavActive('profile');
        }
        
        function showMessages() {
            document.querySelector('.video-feed').style.display = 'none';
            document.querySelector('.recording-ui').style.display = 'none';
            document.getElementById('profile-page').style.display = 'none';
            document.getElementById('messages-page').style.display = 'block';
            updateNavActive('messages');
        }
        
        function showLikes() {
            // In a real app, this would show liked properties
            showFeed(); // For now just show feed
            updateNavActive('likes');
        }
        
        function updateNavActive(activeBtn) {
            const navBtns = document.querySelectorAll('.nav-btn');
            navBtns.forEach(btn => btn.classList.remove('active'));
            
            if (activeBtn === 'home') {
                document.querySelector('.nav-btn:nth-child(1)').classList.add('active');
            } else if (activeBtn === 'messages') {
                document.querySelector('.nav-btn:nth-child(2)').classList.add('active');
            } else if (activeBtn === 'likes') {
                document.querySelector('.nav-btn:nth-child(4)').classList.add('active');
            } else if (activeBtn === 'profile') {
                document.querySelector('.nav-btn:nth-child(5)').classList.add('active');
            }
        }
        
        // Recording functionality
        let mediaRecorder;
        let recordedChunks = [];
        let recordingTime = 60;
        let timerInterval;
        
        function startRecording() {
            document.querySelector('.video-feed').style.display = 'none';
            document.querySelector('.recording-ui').style.display = 'block';
            document.getElementById('profile-page').style.display = 'none';
            document.getElementById('messages-page').style.display = 'none';
            updateNavActive('');
            
            navigator.mediaDevices.getUserMedia({ video: true, audio: true })
                .then(function(stream) {
                    const preview = document.getElementById('recording-preview');
                    preview.srcObject = stream;
                    preview.play();
                    
                    mediaRecorder = new MediaRecorder(stream);
                    
                    mediaRecorder.ondataavailable = function(e) {
                        if (e.data.size > 0) {
                            recordedChunks.push(e.data);
                        }
                    };
                    
                    mediaRecorder.onstop = function() {
                        const blob = new Blob(recordedChunks, { type: 'video/mp4' });
                        recordedChunks = [];
                        // Here you would typically upload the blob to your server
                    };
                    
                    document.getElementById('record-btn').addEventListener('click', toggleRecording);
                })
                .catch(function(err) {
                    console.error("Error accessing media devices: ", err);
                });
        }
        
        function toggleRecording() {
            if (mediaRecorder.state === 'inactive') {
                mediaRecorder.start();
                document.getElementById('record-indicator').style.backgroundColor = 'red';
                startTimer();
            } else {
                mediaRecorder.stop();
                document.getElementById('record-indicator').style.backgroundColor = 'white';
                stopTimer();
            }
        }
        
        function startTimer() {
            document.getElementById('recording-timer').style.display = 'block';
            let timeLeft = recordingTime;
            updateTimerDisplay(timeLeft);
            
            timerInterval = setInterval(function() {
                timeLeft--;
                updateTimerDisplay(timeLeft);
                
                if (timeLeft <= 0) {
                    stopTimer();
                    mediaRecorder.stop();
                    document.getElementById('record-indicator').style.backgroundColor = 'white';
                }
            }, 1000);
        }
        
        function stopTimer() {
            clearInterval(timerInterval);
        }
        
        function updateTimerDisplay(seconds) {
            const mins = Math.floor(seconds / 60);
            const secs = seconds % 60;
            document.getElementById('recording-timer').textContent = 
                `${mins.toString().padStart(2, '0')}:${secs.toString().padStart(2, '0')}`;
        }
        
        // Simulate vertical scrolling between videos
        let currentVideoIndex = 0;
        const videoContainers = document.querySelectorAll('.video-container');
        
        function scrollToVideo(index) {
            if (index >= 0 && index < videoContainers.length) {
                currentVideoIndex = index;
                window.scrollTo({
                    top: videoContainers[index].offsetTop,
                    behavior: 'smooth'
                });
            }
        }
        
        let startY;
        let isScrolling = false;
        
        document.addEventListener('touchstart', function(e) {
            startY = e.touches[0].clientY;
        }, { passive: true });
        
        document.addEventListener('touchmove', function(e) {
            if (!isScrolling) {
                const y = e.touches[0].clientY;
                const diff = y - startY;
                
                if (Math.abs(diff) > 50) {
                    isScrolling = true;
                    if (diff > 0) {
                        // Swipe down - previous video
                        scrollToVideo(currentVideoIndex - 1);
                    } else {
                        // Swipe up - next video
                        scrollToVideo(currentVideoIndex + 1);
                    }
                    
                    setTimeout(() => {
                        isScrolling = false;
                    }, 1000);
                }
            }
        }, { passive: true });
        
        // Initialize with feed view
        showFeed();
    </script>
</body>
</html>
