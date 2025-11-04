<!doctype html>
<html lang="ko">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>우리 초등학교 탐험하기</title>
  <style>
        body {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Pretendard', -apple-system, BlinkMacSystemFont, system-ui, Roboto, 'Helvetica Neue', 'Segoe UI', 'Apple SD Gothic Neo', 'Noto Sans KR', 'Malgun Gothic', 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol', sans-serif;
            background: linear-gradient(135deg, #FFE5B4 0%, #FFCCCB 50%, #E6E6FA 100%);
            min-height: 100%;
            overflow-x: hidden;
        }
        
        html {
            height: 100%;
        }
        
        .container {
            max-width: 800px;
            margin: 0 auto;
            padding: 20px;
            min-height: 100%;
        }
        
        .header {
            text-align: center;
            margin-bottom: 30px;
            background: white;
            border-radius: 25px;
            padding: 25px;
            box-shadow: 0 8px 25px rgba(0,0,0,0.1);
            border: 4px solid #FFB6C1;
        }
        
        .title {
            font-size: 2.5rem;
            color: #FF6B6B;
            margin: 0;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.1);
        }
        
        .subtitle {
            font-size: 1.2rem;
            color: #4ECDC4;
            margin: 10px 0 0 0;
        }
        
        .school-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 25px;
            margin-bottom: 30px;
        }
        
        .school-card {
            background: white;
            border-radius: 20px;
            padding: 25px;
            text-align: center;
            box-shadow: 0 8px 25px rgba(0,0,0,0.1);
            border: 3px solid #FFE4E1;
            transition: all 0.3s ease;
            cursor: pointer;
        }
        
        .school-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 12px 35px rgba(0,0,0,0.15);
            border-color: #FFB6C1;
        }
        
        .card-icon {
            font-size: 4rem;
            margin-bottom: 15px;
            display: block;
        }
        
        .card-title {
            font-size: 1.5rem;
            color: #FF6B6B;
            margin: 0 0 10px 0;
            font-weight: bold;
        }
        
        .card-description {
            font-size: 1rem;
            color: #666;
            line-height: 1.5;
            margin: 0;
        }
        
        .activity-section {
            background: white;
            border-radius: 20px;
            padding: 25px;
            margin-bottom: 25px;
            box-shadow: 0 8px 25px rgba(0,0,0,0.1);
            border: 3px solid #E6E6FA;
        }
        
        .section-title {
            font-size: 1.8rem;
            color: #9370DB;
            text-align: center;
            margin: 0 0 20px 0;
        }
        
        .activity-buttons {
            display: flex;
            flex-wrap: wrap;
            gap: 15px;
            justify-content: center;
        }
        
        .activity-btn {
            background: linear-gradient(45deg, #4ECDC4, #44A08D);
            color: white;
            border: none;
            border-radius: 25px;
            padding: 15px 25px;
            font-size: 1.1rem;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(0,0,0,0.2);
            font-family: inherit;
        }
        
        .activity-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 6px 20px rgba(0,0,0,0.3);
            background: linear-gradient(45deg, #44A08D, #4ECDC4);
        }
        
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.5);
            z-index: 1000;
            justify-content: center;
            align-items: center;
            padding: 20px;
            box-sizing: border-box;
        }
        
        .modal-content {
            background: white;
            border-radius: 25px;
            padding: 30px;
            max-width: 500px;
            width: 100%;
            text-align: center;
            box-shadow: 0 15px 50px rgba(0,0,0,0.3);
            border: 4px solid #FFB6C1;
            position: relative;
        }
        
        .close-btn {
            position: absolute;
            top: 15px;
            right: 20px;
            background: #FF6B6B;
            color: white;
            border: none;
            border-radius: 50%;
            width: 35px;
            height: 35px;
            font-size: 1.2rem;
            cursor: pointer;
            font-weight: bold;
        }
        
        .modal-icon {
            font-size: 3rem;
            margin-bottom: 15px;
        }
        
        .modal-title {
            font-size: 1.8rem;
            color: #FF6B6B;
            margin: 0 0 15px 0;
        }
        
        .modal-text {
            font-size: 1.1rem;
            color: #666;
            line-height: 1.6;
            margin: 0;
        }
        
        .floating-elements {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: -1;
        }
        
        .floating-star {
            position: absolute;
            font-size: 2rem;
            animation: float 6s ease-in-out infinite;
            opacity: 0.3;
        }
        
        .navigation-buttons {
            position: fixed;
            top: 20px;
            right: 20px;
            display: flex;
            gap: 10px;
            z-index: 1500;
        }
        
        .nav-btn {
            background: linear-gradient(45deg, #FF6B6B, #4ECDC4);
            color: white;
            border: none;
            border-radius: 25px;
            padding: 12px 20px;
            font-size: 1rem;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(0,0,0,0.2);
            font-family: inherit;
            pointer-events: auto;
        }
        
        .nav-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(0,0,0,0.3);
        }
        
        .nav-btn.home {
            background: linear-gradient(45deg, #4ECDC4, #44A08D);
        }
        
        .nav-btn.exit {
            background: linear-gradient(45deg, #FF6B6B, #FF8E8E);
        }
        
        @keyframes float {
            0%, 100% { transform: translateY(0px) rotate(0deg); }
            50% { transform: translateY(-20px) rotate(180deg); }
        }
        
        .school-setup {
            text-align: center;
        }
        
        .school-input-section {
            margin: 25px 0;
        }
        
        .school-name-input {
            padding: 15px 20px;
            border: 3px solid #FFB6C1;
            border-radius: 25px;
            font-size: 1.2rem;
            text-align: center;
            font-family: inherit;
            outline: none;
            transition: border-color 0.3s ease;
            width: 300px;
            max-width: 90%;
            margin-bottom: 15px;
        }
        
        .school-name-input:focus {
            border-color: #FF6B6B;
        }
        
        .school-submit-btn {
            background: linear-gradient(45deg, #FF6B6B, #FF8E8E);
            color: white;
            border: none;
            border-radius: 25px;
            padding: 15px 30px;
            font-size: 1.2rem;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(0,0,0,0.2);
            font-family: inherit;
        }
        
        .school-submit-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 6px 20px rgba(0,0,0,0.3);
        }
        
        .school-image-section {
            text-align: center;
            margin: 30px 0;
            background: white;
            border-radius: 20px;
            padding: 25px;
            box-shadow: 0 8px 25px rgba(0,0,0,0.1);
            border: 3px solid #E6E6FA;
        }
        
        .school-svg {
            width: 100%;
            max-width: 400px;
            height: 300px;
            margin-bottom: 15px;
        }
        
        .school-name-display {
            font-size: 1.8rem;
            color: #FF6B6B;
            margin: 15px 0;
            font-weight: bold;
        }
        
        .attendance-section {
            margin-top: 20px;
            padding: 20px;
            background: #F0F8FF;
            border-radius: 15px;
            border: 2px solid #87CEEB;
        }
        
        .user-info {
            display: flex;
            gap: 10px;
            margin-bottom: 15px;
            justify-content: center;
            flex-wrap: wrap;
        }
        
        .name-input {
            padding: 10px 15px;
            border: 2px solid #FFB6C1;
            border-radius: 20px;
            font-size: 1rem;
            text-align: center;
            font-family: inherit;
            outline: none;
            transition: border-color 0.3s ease;
        }
        
        .name-input:focus {
            border-color: #FF6B6B;
        }
        
        .attendance-btn {
            background: linear-gradient(45deg, #FF6B6B, #FF8E8E);
            color: white;
            border: none;
            border-radius: 25px;
            padding: 12px 25px;
            font-size: 1.1rem;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(0,0,0,0.2);
            font-family: inherit;
            margin-bottom: 15px;
        }
        
        .attendance-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(0,0,0,0.3);
        }
        
        .attendance-btn:disabled {
            background: #ccc;
            cursor: not-allowed;
            transform: none;
        }
        
        .attendance-status {
            text-align: center;
        }
        
        .attendance-count {
            font-size: 1.1rem;
            color: #4ECDC4;
            font-weight: bold;
        }
        
        .reward-status {
            margin-top: 10px;
            font-size: 1rem;
            font-weight: bold;
        }
        
        .reward-earned {
            color: #FF6B6B;
            animation: bounce 1s ease-in-out;
        }
        
        .math-problem {
            background: #FFF8DC;
            border: 3px solid #FFD700;
            border-radius: 15px;
            padding: 20px;
            margin: 15px 0;
            text-align: center;
        }
        
        .math-question {
            font-size: 1.5rem;
            color: #FF6B6B;
            margin-bottom: 15px;
        }
        
        .math-input {
            padding: 10px;
            border: 2px solid #FFD700;
            border-radius: 10px;
            font-size: 1.2rem;
            text-align: center;
            width: 80px;
            margin: 0 10px;
        }
        
        .math-submit {
            background: #32CD32;
            color: white;
            border: none;
            border-radius: 15px;
            padding: 10px 20px;
            font-size: 1rem;
            cursor: pointer;
            margin-left: 10px;
        }
        
        .stamp-collection {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            justify-content: center;
            margin-top: 15px;
        }
        
        .stamp {
            font-size: 2rem;
            animation: stampPop 0.5s ease-out;
        }
        
        .cafeteria-chair {
            text-align: center;
            margin: 20px 0;
        }
        
        .chair-svg {
            width: 200px;
            height: 200px;
            margin: 20px auto;
        }
        
        .vr-experience {
            background: linear-gradient(45deg, #9370DB, #BA55D3);
            color: white;
            border: none;
            border-radius: 20px;
            padding: 15px 25px;
            font-size: 1.1rem;
            cursor: pointer;
            margin: 15px 0;
            font-family: inherit;
        }
        
        .gallery-container {
            background: #F8F9FA;
            padding: 20px;
            border-radius: 15px;
            margin: 15px 0;
        }
        
        .gallery-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
            gap: 15px;
            margin-top: 15px;
        }
        
        .gallery-item {
            position: relative;
            border-radius: 10px;
            overflow: hidden;
            cursor: pointer;
            transition: transform 0.3s ease;
            background: white;
            box-shadow: 0 4px 15px rgba(0,0,0,0.1);
        }
        
        .gallery-item:hover {
            transform: scale(1.05);
        }
        
        .gallery-image {
            width: 100%;
            height: 120px;
            object-fit: cover;
            border-radius: 10px 10px 0 0;
        }
        
        .gallery-placeholder {
            width: 100%;
            height: 120px;
            background: linear-gradient(45deg, #E3F2FD, #BBDEFB);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 2rem;
            border-radius: 10px 10px 0 0;
        }
        
        .gallery-label {
            padding: 10px;
            text-align: center;
            font-size: 0.9rem;
            color: #666;
            font-weight: bold;
        }
        
        .upload-section {
            background: #FFF3E0;
            padding: 20px;
            border-radius: 15px;
            margin: 15px 0;
            border: 2px dashed #FF9800;
        }
        
        .upload-area {
            border: 3px dashed #FFB74D;
            border-radius: 15px;
            padding: 30px;
            text-align: center;
            background: white;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .upload-area:hover {
            border-color: #FF9800;
            background: #FFF8E1;
        }
        
        .upload-area.dragover {
            border-color: #FF5722;
            background: #FFEBEE;
        }
        
        .file-input {
            display: none;
        }
        
        .upload-btn {
            background: linear-gradient(45deg, #FF9800, #FFB74D);
            color: white;
            border: none;
            border-radius: 25px;
            padding: 12px 25px;
            font-size: 1.1rem;
            cursor: pointer;
            margin: 10px;
            font-family: inherit;
            transition: all 0.3s ease;
        }
        
        .upload-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(0,0,0,0.3);
        }
        
        .category-selector {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            justify-content: center;
            margin: 15px 0;
        }
        
        .category-btn {
            background: #E3F2FD;
            color: #1976D2;
            border: 2px solid #BBDEFB;
            border-radius: 20px;
            padding: 8px 16px;
            font-size: 0.9rem;
            cursor: pointer;
            transition: all 0.3s ease;
            font-family: inherit;
        }
        
        .category-btn.active {
            background: #1976D2;
            color: white;
            border-color: #1976D2;
        }
        
        .category-btn:hover {
            background: #BBDEFB;
        }
        
        .photo-modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.9);
            display: none;
            justify-content: center;
            align-items: center;
            z-index: 2000;
        }
        
        .photo-modal-content {
            max-width: 90%;
            max-height: 90%;
            border-radius: 15px;
            position: relative;
        }
        
        .photo-modal img {
            width: 100%;
            height: 100%;
            object-fit: contain;
            border-radius: 15px;
        }
        
        .photo-close {
            position: absolute;
            top: -40px;
            right: 0;
            background: white;
            color: #333;
            border: none;
            border-radius: 50%;
            width: 35px;
            height: 35px;
            font-size: 1.2rem;
            cursor: pointer;
            font-weight: bold;
        }
        
        @keyframes bounce {
            0%, 20%, 50%, 80%, 100% { transform: translateY(0); }
            40% { transform: translateY(-10px); }
            60% { transform: translateY(-5px); }
        }
        
        @keyframes stampPop {
            0% { transform: scale(0); }
            50% { transform: scale(1.2); }
            100% { transform: scale(1); }
        }
        
        @media (max-width: 768px) {
            .title {
                font-size: 2rem;
            }
            
            .school-grid {
                grid-template-columns: 1fr;
            }
            
            .activity-buttons {
                flex-direction: column;
                align-items: center;
            }
            
            .activity-btn {
                width: 100%;
                max-width: 250px;
            }
            
            .user-info {
                flex-direction: column;
                align-items: center;
            }
            
            .name-input {
                width: 200px;
            }
            
            .navigation-buttons {
                top: 10px;
                right: 10px;
                flex-direction: column;
                gap: 5px;
            }
            
            .nav-btn {
                padding: 8px 15px;
                font-size: 0.9rem;
            }
        }
    </style>
  <style>@view-transition { navigation: auto; }</style>
  <script src="/_sdk/data_sdk.js" type="text/javascript"></script>
  <script src="/_sdk/element_sdk.js" type="text/javascript"></script>
  <script src="https://cdn.tailwindcss.com" type="text/javascript"></script>
 </head>
 <body>
  <div class="floating-elements">
   <div class="floating-star" style="top: 10%; left: 10%;">
    ⭐
   </div>
   <div class="floating-star" style="top: 20%; right: 15%; animation-delay: -2s;">
    🌟
   </div>
   <div class="floating-star" style="top: 60%; left: 5%; animation-delay: -4s;">
    ✨
   </div>
   <div class="floating-star" style="bottom: 20%; right: 10%; animation-delay: -1s;">
    ⭐
   </div>
  </div><!-- 네비게이션 버튼들 -->
  <div class="navigation-buttons"><button class="nav-btn home" onclick="goHome()">🏠 처음으로</button> <button class="nav-btn exit" onclick="exitApp()">🚪 끝내기</button>
  </div>
  <main class="container">
   <header class="header" id="mainHeader">
    <div id="kindergartenSetup" class="school-setup">
     <h1 class="title">🌈 안녕하세요!</h1>
     <p class="subtitle">지금 다니고 있는 유치원을 알려주세요</p>
     <div class="school-input-section"><input type="text" id="kindergartenName" placeholder="유치원 이름 (예: 꿈나무유치원)" class="school-name-input"> <input type="text" id="kindergartenClass" placeholder="반 이름 (예: 사과반, 토끼반)" class="school-name-input" style="margin-top: 10px;"> <button class="school-submit-btn" onclick="setKindergarten()">✨ 다음 단계로</button>
     </div>
    </div>
    <div id="schoolSetup" class="school-setup" style="display: none;">
     <h1 class="title">🏫 이제 초등학교를 준비해 볼까요?</h1>
     <p class="subtitle" id="kindergartenGreeting">어떤 초등학교에 입학하나요?</p>
     <div class="school-input-section"><input type="text" id="schoolName" placeholder="학교 이름을 입력하세요 (예: 행복초등학교)" class="school-name-input"> <button class="school-submit-btn" onclick="setSchool()">🎒 우리 학교 만들기</button>
     </div>
    </div>
    <div id="mainContent" class="main-content" style="display: none;">
     <h1 class="title" id="schoolTitle">🏫 우리 초등학교 탐험하기</h1>
     <p class="subtitle">새로운 학교 친구들과 함께 즐거운 모험을 떠나요!</p><!-- 출석체크 섹션 -->
     <div class="attendance-section">
      <div class="user-info"><input type="text" id="userName" placeholder="이름을 입력하세요" class="name-input">
      </div><button class="attendance-btn" onclick="checkAttendance()">📅 오늘 출석하기</button>
      <div class="attendance-status"><span class="attendance-count">이번 달 출석: <span id="attendanceCount">0</span>일</span>
       <div class="reward-status" id="rewardStatus"></div><button class="attendance-btn" onclick="showStickerCollection()" style="background: linear-gradient(45deg, #9370DB, #BA55D3); margin-top: 10px;">🌟 내 스티커 모음 보기</button>
      </div>
     </div>
    </div>
   </header><!-- 학교 그림 섹션 -->
   <div id="schoolImageSection" class="school-image-section" style="display: none;">
    <div class="school-building">
     <svg id="schoolSVG" class="school-svg" viewbox="0 0 400 300"><!-- 학교 건물이 여기에 동적으로 생성됩니다 -->
     </svg>
     <h2 id="schoolNameDisplay" class="school-name-display"></h2>
    </div>
   </div>
   <section class="school-grid" id="schoolGrid" style="display: none;">
    <div class="school-card" onclick="openModal('classroom')"><span class="card-icon">📚</span>
     <h2 class="card-title">우리 교실</h2>
     <p class="card-description">책상과 의자가 있고, 선생님과 함께 공부하는 곳이에요</p>
    </div>
    <div class="school-card" onclick="openModal('playground')"><span class="card-icon">🛝</span>
     <h2 class="card-title">운동장</h2>
     <p class="card-description">친구들과 뛰어놀고 체육 시간에 운동하는 넓은 곳이에요</p>
    </div>
    <div class="school-card" onclick="openModal('library')"><span class="card-icon">📖</span>
     <h2 class="card-title">도서관</h2>
     <p class="card-description">재미있는 책들이 가득하고 조용히 읽는 곳이에요</p>
    </div>
    <div class="school-card" onclick="openModal('cafeteria')"><span class="card-icon">🍽️</span>
     <h2 class="card-title">급식실</h2>
     <p class="card-description">맛있는 급식을 먹고 친구들과 이야기하는 곳이에요</p>
    </div>
    <div class="school-card" onclick="openModal('music')"><span class="card-icon">🎵</span>
     <h2 class="card-title">음악실</h2>
     <p class="card-description">노래하고 악기를 연주하며 음악을 배우는 곳이에요</p>
    </div>
    <div class="school-card" onclick="openModal('art')"><span class="card-icon">🎨</span>
     <h2 class="card-title">미술실</h2>
     <p class="card-description">그림을 그리고 만들기를 하는 창작 공간이에요</p>
    </div>
    <div class="school-card" onclick="openModal('health')"><span class="card-icon">🏥</span>
     <h2 class="card-title">보건실</h2>
     <p class="card-description">다치거나 아플 때 보건 선생님이 돌봐주시는 곳이에요</p>
    </div>
    <div class="school-card" onclick="openModal('teachers')"><span class="card-icon">👩‍🏫</span>
     <h2 class="card-title">교무실</h2>
     <p class="card-description">선생님들이 일하시고 회의하시는 곳이에요</p>
    </div>
    <div class="school-card" onclick="openModal('principal')"><span class="card-icon">🏛️</span>
     <h2 class="card-title">교장실</h2>
     <p class="card-description">교장선생님이 계시고 학교 일을 관리하시는 곳이에요</p>
    </div>
    <div class="school-card" onclick="openModal('counseling')"><span class="card-icon">💝</span>
     <h2 class="card-title">상담실</h2>
     <p class="card-description">고민이 있을 때 따뜻하게 이야기를 들어주시는 곳이에요</p>
    </div>
    <div class="school-card" onclick="openModal('gallery')"><span class="card-icon">📸</span>
     <h2 class="card-title">학교 둘러보기</h2>
     <p class="card-description">우리 학교의 실제 모습을 사진으로 구경해보세요</p>
    </div>
    <div class="school-card" onclick="openModal('teacher-upload')"><span class="card-icon">👩‍🏫</span>
     <h2 class="card-title">선생님 전용</h2>
     <p class="card-description">선생님이 학교 사진을 업로드하는 곳이에요</p>
    </div>
   </section>
   <section class="activity-section" id="activitySection" style="display: none;">
    <h2 class="section-title">🌈 초등학교에서 하는 재미있는 활동들</h2>
    <div class="activity-buttons"><button class="activity-btn" onclick="openModal('reading')">📚 책 읽기</button> <button class="activity-btn" onclick="openModal('sports')">⚽ 체육 활동</button> <button class="activity-btn" onclick="openModal('friends')">👫 친구 사귀기</button> <button class="activity-btn" onclick="openModal('science')">🔬 과학 실험</button> <button class="activity-btn" onclick="openModal('field-trip')">🚌 현장학습</button>
    </div>
   </section>
  </main><!-- 모달 창들 -->
  <div id="modal" class="modal" onclick="closeModal(event)">
   <div class="modal-content"><button class="close-btn" onclick="closeModal()">×</button>
    <div id="modal-body"></div>
   </div>
  </div>
  <script>
        // 출석 및 도장 관리
        let attendanceData = JSON.parse(localStorage.getItem('schoolAttendance')) || {
            count: 0,
            lastDate: null,
            stamps: [],
            userName: '',
            userClass: '',
            schoolName: '',
            kindergartenName: '',
            kindergartenClass: ''
        };
        
        // 학교 사진 갤러리 관리
        let schoolPhotos = JSON.parse(localStorage.getItem('schoolPhotos')) || {
            classroom: [],
            playground: [],
            library: [],
            cafeteria: [],
            music: [],
            art: [],
            health: [],
            teachers: [],
            principal: [],
            counseling: [],
            entrance: [],
            hallway: [],
            garden: [],
            events: []
        };
        
        let selectedCategory = 'classroom';
        let currentPhotoIndex = 0;
        
        // 학교 건물 디자인 템플릿들
        const schoolDesigns = [
            {
                name: 'modern',
                colors: ['#4A90E2', '#7ED321', '#F5A623'],
                windows: 12,
                style: 'modern'
            },
            {
                name: 'classic',
                colors: ['#D0021B', '#F8E71C', '#50E3C2'],
                windows: 8,
                style: 'classic'
            },
            {
                name: 'colorful',
                colors: ['#BD10E0', '#B8E986', '#F5A623'],
                windows: 15,
                style: 'colorful'
            },
            {
                name: 'nature',
                colors: ['#7ED321', '#417505', '#F5A623'],
                windows: 10,
                style: 'nature'
            }
        ];
        
        let currentMathProblem = null;
        
        const mathProblems = [
            { question: '2 + 3 = ?', answer: 5 },
            { question: '5 - 2 = ?', answer: 3 },
            { question: '3 + 4 = ?', answer: 7 },
            { question: '6 - 1 = ?', answer: 5 },
            { question: '4 + 2 = ?', answer: 6 },
            { question: '7 - 3 = ?', answer: 4 },
            { question: '1 + 8 = ?', answer: 9 },
            { question: '10 - 2 = ?', answer: 8 }
        ];

        const principalQuizzes = [
            { question: '학교에서 가장 중요한 것은 무엇일까요?', options: ['친구와 사이좋게 지내기', '혼자 놀기', '떠들기'], answer: 0 },
            { question: '수업 시간에는 어떻게 해야 할까요?', options: ['조용히 듣기', '친구와 이야기하기', '잠자기'], answer: 0 },
            { question: '선생님께 인사할 때는?', options: ['고개 숙이고 인사', '손 흔들기만', '모른 척하기'], answer: 0 },
            { question: '책을 읽으면 어떤 좋은 점이 있을까요?', options: ['상상력이 커져요', '졸려져요', '아무것도 없어요'], answer: 0 }
        ];

        const healthQuizzes = [
            { question: '손을 언제 씻어야 할까요?', options: ['밥 먹기 전후', '놀고 난 후에만', '씻지 않아도 돼요'], answer: 0 },
            { question: '이를 하루에 몇 번 닦아야 할까요?', options: ['3번 이상', '1번', '닦지 않아도 돼요'], answer: 0 },
            { question: '몸이 아플 때는 어떻게 해야 할까요?', options: ['선생님께 말씀드리기', '참고 있기', '집에 가기'], answer: 0 },
            { question: '건강한 음식은 무엇일까요?', options: ['채소와 과일', '과자만', '탄산음료'], answer: 0 }
        ];

        const artQuizzes = [
            { question: '가위를 사용할 때 가장 중요한 것은?', options: ['친구에게 건네줄 때 손잡이 먼저', '가위로 장난치기', '아무렇게나 두기'], answer: 0 },
            { question: '물감을 사용한 후에는?', options: ['붓을 깨끗이 씻기', '그대로 두기', '다른 친구가 치우기'], answer: 0 },
            { question: '친구와 함께 작품을 만들 때는?', options: ['서로 도와주고 양보하기', '혼자만 하기', '친구 작품 망치기'], answer: 0 },
            { question: '미술 시간이 끝나면?', options: ['자리 정리하고 도구 제자리에', '그냥 나가기', '선생님이 치우기'], answer: 0 }
        ];

        let currentQuiz = null;
        let isListening = false;

        const modalContents = {
            classroom: {
                icon: '📚',
                title: '우리 교실',
                text: '지금은 수학 시간입니다! 문제를 풀어보세요.',
                showMath: true
            },
            playground: {
                icon: '🛝',
                title: '넓은 운동장',
                text: '운동장에는 재미있는 놀이기구들이 많아요! 각 놀이기구의 사용법과 안전수칙을 배워보세요.',
                showPlayground: true
            },
            library: {
                icon: '📖',
                title: '조용한 도서관',
                text: '도서관에는 초등학생을 위한 추천 도서들이 가득해요! 어떤 책을 읽어볼까요?',
                showBooks: true
            },
            cafeteria: {
                icon: '🍽️',
                title: '맛있는 급식실',
                text: '급식실에서는 영양사 선생님이 만든 맛있고 건강한 음식을 먹어요! 초등학교에는 특별한 둥근 의자가 있어요.',
                showChair: true
            },
            music: {
                icon: '🎵',
                title: '신나는 음악실',
                text: '음악실에서는 다양한 악기들을 배우고 연주해요! 각 악기의 연주법과 소리를 체험해보세요.',
                showInstruments: true
            },
            art: {
                icon: '🎨',
                title: '창작하는 미술실',
                text: '미술실에서 안전하게 작품을 만들기 위한 규칙들을 퀴즈로 배워보세요!',
                showQuiz: true,
                quizType: 'art'
            },
            reading: {
                icon: '📚',
                title: '책 읽기의 즐거움',
                text: '초등학교에서는 매일 책을 읽어요! 한글을 배우면서 점점 더 많은 책을 읽을 수 있게 돼요. 선생님이 재미있는 동화를 읽어주시기도 하고, 친구들과 책 이야기를 나눠요.'
            },
            sports: {
                icon: '⚽',
                title: '건강한 체육 활동',
                text: '체육 시간에는 달리기, 줄넘기, 공놀이를 해요! 친구들과 팀을 이뤄서 게임도 하고, 새로운 운동을 배워요. 운동을 하면 몸이 건강해지고 기분도 좋아져요!'
            },
            friends: {
                icon: '👫',
                title: '소중한 친구 사귀기',
                text: '초등학교에서 만나는 친구들은 정말 소중해요! 함께 공부하고, 놀고, 도움을 주고받으며 우정을 쌓아가요. 서로 다른 점을 이해하고 배려하는 마음을 기르게 돼요.'
            },
            science: {
                icon: '🔬',
                title: '신기한 과학 실험',
                text: '과학 시간에는 재미있는 실험을 해요! 물과 기름이 섞이지 않는 것을 보거나, 자석의 힘을 관찰해요. 주변의 자연과 사물들이 어떻게 작동하는지 알아가는 시간이에요!'
            },
            'field-trip': {
                icon: '🚌',
                title: '즐거운 현장학습',
                text: '가끔 버스를 타고 박물관, 과학관, 공원에 가요! 교실에서 배운 것들을 직접 보고 체험할 수 있어요. 친구들과 함께 가는 여행이라 더욱 즐겁고 기억에 남아요!'
            },
            health: {
                icon: '🏥',
                title: '친절한 보건선생님',
                text: '안녕하세요! 흰 가운을 입은 보건선생님이 반갑게 인사드려요. 건강한 생활을 위한 퀴즈를 준비했어요!',
                showHealthTeacher: true
            },
            teachers: {
                icon: '👩‍🏫',
                title: '웃는 교감선생님',
                text: '안녕하세요! 교감선생님이에요. 자신있게 큰 소리로 친구 이름을 말해보세요!',
                showVoice: true
            },
            principal: {
                icon: '🏛️',
                title: '친절한 교장선생님',
                text: '안녕하세요! 예쁜 교장선생님이 재미있는 퀴즈를 준비했어요. 맞히면 특별한 도장을 드려요!',
                showQuiz: true,
                quizType: 'principal'
            },
            counseling: {
                icon: '💝',
                title: '따뜻한 상담실',
                text: '상담실에는 친절한 상담 선생님이 계세요! 어떤 고민이든 편하게 이야기해보세요.',
                showCounseling: true
            },
            gallery: {
                icon: '📸',
                title: '우리 학교 둘러보기',
                text: '선생님이 올려주신 우리 학교의 실제 모습을 구경해보세요!',
                showGallery: true
            },
            'teacher-upload': {
                icon: '👩‍🏫',
                title: '선생님 전용 - 사진 업로드',
                text: '학교의 아름다운 모습을 아이들과 학부모님께 보여주세요!',
                showUpload: true
            }
        };

        // 네비게이션 함수들
        function goHome() {
            // 모든 모달 닫기
            closeModal();
            closePhotoModal();
            
            // 메인 화면으로 이동
            if (attendanceData.schoolName) {
                showMainContent();
            } else if (attendanceData.kindergartenName) {
                showSchoolSetup();
            } else {
                // 처음 상태로 리셋
                document.getElementById('kindergartenSetup').style.display = 'block';
                document.getElementById('schoolSetup').style.display = 'none';
                document.getElementById('mainContent').style.display = 'none';
                document.getElementById('schoolImageSection').style.display = 'none';
                document.getElementById('schoolGrid').style.display = 'none';
                document.getElementById('activitySection').style.display = 'none';
            }
        }
        
        function exitApp() {
            // 사용자에게 확인 메시지 표시 (커스텀 모달 사용)
            const confirmModal = document.createElement('div');
            confirmModal.className = 'modal';
            confirmModal.style.display = 'flex';
            confirmModal.innerHTML = `
                <div class="modal-content" style="max-width: 400px;">
                    <div class="modal-icon">👋</div>
                    <h3 class="modal-title">정말 나가시겠어요?</h3>
                    <p class="modal-text">지금까지 한 것들이 모두 저장되어 있어요. 언제든 다시 돌아와서 계속 탐험할 수 있어요!</p>
                    <div style="display: flex; gap: 15px; justify-content: center; margin-top: 20px;">
                        <button onclick="confirmExit()" style="background: #FF6B6B; color: white; border: none; border-radius: 20px; padding: 12px 25px; font-size: 1rem; cursor: pointer; font-family: inherit;">🚪 나가기</button>
                        <button onclick="cancelExit()" style="background: #4ECDC4; color: white; border: none; border-radius: 20px; padding: 12px 25px; font-size: 1rem; cursor: pointer; font-family: inherit;">🏠 계속하기</button>
                    </div>
                </div>
            `;
            
            document.body.appendChild(confirmModal);
        }
        
        function confirmExit() {
            // 종료 메시지 표시
            document.body.innerHTML = `
                <div style="display: flex; justify-content: center; align-items: center; height: 100vh; background: linear-gradient(135deg, #FFE5B4 0%, #FFCCCB 50%, #E6E6FA 100%); font-family: inherit;">
                    <div style="text-align: center; background: white; padding: 50px; border-radius: 25px; box-shadow: 0 15px 50px rgba(0,0,0,0.2);">
                        <div style="font-size: 4rem; margin-bottom: 20px;">👋</div>
                        <h2 style="color: #FF6B6B; margin-bottom: 15px;">안녕히 가세요!</h2>
                        <p style="color: #666; font-size: 1.1rem; margin-bottom: 20px;">초등학교 탐험을 마쳐주셔서 감사해요!</p>
                        <p style="color: #4ECDC4; font-size: 1rem;">언제든 다시 돌아와서 더 많은 것을 배워보세요! 🌈</p>
                    </div>
                </div>
            `;
        }
        
        function cancelExit() {
            // 확인 모달 제거
            const confirmModal = document.querySelector('.modal');
            if (confirmModal) {
                confirmModal.remove();
            }
        }

        // 페이지 로드 시 출석 정보 표시
        window.onload = function() {
            if (attendanceData.schoolName) {
                showMainContent();
            } else if (attendanceData.kindergartenName) {
                showSchoolSetup();
            }
            updateAttendanceDisplay();
            if (attendanceData.userName) {
                document.getElementById('userName').value = attendanceData.userName;
            }
            if (attendanceData.kindergartenName) {
                document.getElementById('kindergartenName').value = attendanceData.kindergartenName;
            }
            if (attendanceData.kindergartenClass) {
                document.getElementById('kindergartenClass').value = attendanceData.kindergartenClass;
            }
        };
        
        function setKindergarten() {
            const kindergartenName = document.getElementById('kindergartenName').value.trim();
            const kindergartenClass = document.getElementById('kindergartenClass').value.trim();
            
            if (!kindergartenName || !kindergartenClass) {
                showCustomAlert('유치원 이름과 반 이름을 모두 입력해주세요!');
                return;
            }
            
            attendanceData.kindergartenName = kindergartenName;
            attendanceData.kindergartenClass = kindergartenClass;
            localStorage.setItem('schoolAttendance', JSON.stringify(attendanceData));
            
            showSchoolSetup();
        }
        
        function showSchoolSetup() {
            // 유치원 설정 화면 숨기기
            document.getElementById('kindergartenSetup').style.display = 'none';
            
            // 초등학교 설정 화면 보이기
            document.getElementById('schoolSetup').style.display = 'block';
            
            // 개인화된 인사말 표시
            if (attendanceData.kindergartenName && attendanceData.kindergartenClass) {
                const greeting = document.getElementById('kindergartenGreeting');
                greeting.textContent = `${attendanceData.kindergartenName} ${attendanceData.kindergartenClass} 친구! 어떤 초등학교에 입학하나요?`;
            }
        }
        
        function setSchool() {
            const schoolName = document.getElementById('schoolName').value.trim();
            
            if (!schoolName) {
                showCustomAlert('학교 이름을 입력해주세요!');
                return;
            }
            
            attendanceData.schoolName = schoolName;
            localStorage.setItem('schoolAttendance', JSON.stringify(attendanceData));
            
            showMainContent();
        }
        
        function showMainContent() {
            // 모든 설정 화면 숨기기
            document.getElementById('kindergartenSetup').style.display = 'none';
            document.getElementById('schoolSetup').style.display = 'none';
            
            // 메인 콘텐츠 보이기
            document.getElementById('mainContent').style.display = 'block';
            document.getElementById('schoolImageSection').style.display = 'block';
            document.getElementById('schoolGrid').style.display = 'grid';
            document.getElementById('activitySection').style.display = 'block';
            
            // 학교 제목 업데이트
            const schoolTitle = document.getElementById('schoolTitle');
            schoolTitle.textContent = `🏫 ${attendanceData.schoolName} 탐험하기`;
            
            // 학교 건물 그리기
            generateSchoolBuilding();
        }
        
        function generateSchoolBuilding() {
            const schoolName = attendanceData.schoolName;
            const schoolSVG = document.getElementById('schoolSVG');
            const schoolNameDisplay = document.getElementById('schoolNameDisplay');
            
            // 학교 이름을 기반으로 디자인 선택 (해시 기반)
            let hash = 0;
            for (let i = 0; i < schoolName.length; i++) {
                hash = ((hash << 5) - hash + schoolName.charCodeAt(i)) & 0xffffffff;
            }
            const designIndex = Math.abs(hash) % schoolDesigns.length;
            const design = schoolDesigns[designIndex];
            
            // SVG 내용 생성
            let svgContent = `
                <!-- 하늘 배경 -->
                <rect width="400" height="300" fill="#87CEEB"/>
                
                <!-- 구름들 -->
                <ellipse cx="80" cy="50" rx="25" ry="15" fill="white" opacity="0.8"/>
                <ellipse cx="95" cy="45" rx="30" ry="18" fill="white" opacity="0.8"/>
                <ellipse cx="320" cy="40" rx="20" ry="12" fill="white" opacity="0.8"/>
                
                <!-- 땅 -->
                <rect x="0" y="220" width="400" height="80" fill="#7ED321"/>
                
                <!-- 학교 건물 메인 -->
                <rect x="50" y="120" width="300" height="100" fill="${design.colors[0]}" stroke="#333" stroke-width="2"/>
                
                <!-- 지붕 -->
                <polygon points="40,120 200,80 360,120" fill="${design.colors[1]}" stroke="#333" stroke-width="2"/>
                
                <!-- 입구 -->
                <rect x="180" y="180" width="40" height="40" fill="${design.colors[2]}" stroke="#333" stroke-width="2"/>
                <rect x="185" y="185" width="30" height="30" fill="#8B4513"/>
                
                <!-- 창문들 -->
            `;
            
            // 창문 생성
            const windowsPerRow = Math.ceil(design.windows / 2);
            for (let i = 0; i < design.windows; i++) {
                const row = Math.floor(i / windowsPerRow);
                const col = i % windowsPerRow;
                const x = 70 + (col * 40);
                const y = 135 + (row * 25);
                
                if (x < 170 || x > 210) { // 입구 부분 피하기
                    svgContent += `<rect x="${x}" y="${y}" width="20" height="15" fill="#E6F3FF" stroke="#333" stroke-width="1"/>`;
                }
            }
            
            // 학교 이름 간판
            svgContent += `
                <!-- 간판 -->
                <rect x="120" y="95" width="160" height="25" fill="white" stroke="#333" stroke-width="2" rx="5"/>
                <text x="200" y="110" text-anchor="middle" font-family="Arial" font-size="12" fill="#333">${schoolName}</text>
                
                <!-- 나무들 -->
                <circle cx="30" cy="200" r="15" fill="#228B22"/>
                <rect x="27" y="200" width="6" height="20" fill="#8B4513"/>
                
                <circle cx="370" cy="205" r="12" fill="#228B22"/>
                <rect x="367" y="205" width="6" height="15" fill="#8B4513"/>
                
                <!-- 태양 -->
                <circle cx="350" cy="60" r="20" fill="#FFD700"/>
            `;
            
            schoolSVG.innerHTML = svgContent;
            schoolNameDisplay.textContent = schoolName;
        }
        
        function updateAttendanceDisplay() {
            document.getElementById('attendanceCount').textContent = attendanceData.count;
            const rewardStatus = document.getElementById('rewardStatus');
            
            if (attendanceData.count >= 20) {
                rewardStatus.innerHTML = '🎉 축하해요! 칭찬 스티커를 받았어요! ⭐';
                rewardStatus.className = 'reward-status reward-earned';
            } else if (attendanceData.count >= 15) {
                rewardStatus.innerHTML = `🌟 ${20 - attendanceData.count}일만 더 오면 스티커를 받아요!`;
                rewardStatus.className = 'reward-status';
            } else {
                rewardStatus.innerHTML = '';
                rewardStatus.className = 'reward-status';
            }
        }
        
        function checkAttendance() {
            const userName = document.getElementById('userName').value.trim();
            
            if (!userName) {
                showCustomAlert('이름을 입력해주세요!');
                return;
            }
            
            const today = new Date().toDateString();
            
            if (attendanceData.lastDate === today) {
                showCustomAlert('오늘은 이미 출석했어요! 내일 또 만나요 😊');
                return;
            }
            
            attendanceData.count++;
            attendanceData.lastDate = today;
            attendanceData.userName = userName;
            
            localStorage.setItem('schoolAttendance', JSON.stringify(attendanceData));
            updateAttendanceDisplay();
            
            const btn = document.querySelector('.attendance-btn');
            btn.textContent = '✅ 출석 완료!';
            btn.disabled = true;
            
            setTimeout(() => {
                btn.textContent = '📅 오늘 출석하기';
                btn.disabled = false;
            }, 3000);
        }
        
        function showCustomAlert(message) {
            const alertModal = document.createElement('div');
            alertModal.className = 'modal';
            alertModal.style.display = 'flex';
            alertModal.innerHTML = `
                <div class="modal-content" style="max-width: 400px;">
                    <div class="modal-icon">💬</div>
                    <h3 class="modal-title">알림</h3>
                    <p class="modal-text">${message}</p>
                    <button onclick="this.closest('.modal').remove()" style="background: #4ECDC4; color: white; border: none; border-radius: 20px; padding: 12px 25px; font-size: 1rem; cursor: pointer; font-family: inherit;">확인</button>
                </div>
            `;
            
            document.body.appendChild(alertModal);
            
            // 3초 후 자동으로 닫기
            setTimeout(() => {
                if (alertModal.parentNode) {
                    alertModal.remove();
                }
            }, 3000);
        }
        
        function showStickerCollection() {
            const stickerModal = document.createElement('div');
            stickerModal.className = 'modal';
            stickerModal.style.display = 'flex';
            
            const totalStickers = attendanceData.stamps.length;
            const stickersByType = {};
            
            // 스티커 종류별로 분류
            attendanceData.stamps.forEach(sticker => {
                stickersByType[sticker] = (stickersByType[sticker] || 0) + 1;
            });
            
            let achievementMessage = '';
            if (totalStickers >= 50) {
                achievementMessage = '🏆 스티커 마스터! 정말 대단해요!';
            } else if (totalStickers >= 30) {
                achievementMessage = '🌟 스티커 수집가! 훌륭해요!';
            } else if (totalStickers >= 20) {
                achievementMessage = '⭐ 칭찬 스티커 달성! 축하해요!';
            } else if (totalStickers >= 10) {
                achievementMessage = '✨ 열심히 모으고 있어요!';
            } else {
                achievementMessage = '💪 더 많은 스티커를 모아보세요!';
            }
            
            stickerModal.innerHTML = `
                <div class="modal-content" style="max-width: 500px; max-height: 80vh; overflow-y: auto;">
                    <button class="close-btn" onclick="this.closest('.modal').remove()">&times;</button>
                    <div class="modal-icon">🌟</div>
                    <h3 class="modal-title">내 스티커 모음집</h3>
                    
                    <div style="background: linear-gradient(45deg, #FFE5B4, #FFCCCB); padding: 20px; border-radius: 15px; margin: 20px 0; text-align: center;">
                        <div style="font-size: 2rem; margin-bottom: 10px;">🎉</div>
                        <div style="font-size: 1.3rem; color: #FF6B6B; font-weight: bold; margin-bottom: 5px;">총 ${totalStickers}개의 스티커</div>
                        <div style="color: #4ECDC4; font-weight: bold;">${achievementMessage}</div>
                    </div>
                    
                    <div style="background: #F8F9FA; padding: 20px; border-radius: 15px; margin: 15px 0;">
                        <h4 style="color: #666; margin: 0 0 15px 0; text-align: center;">📊 스티커 종류별 현황</h4>
                        <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(80px, 1fr)); gap: 15px; text-align: center;">
                            ${Object.entries(stickersByType).map(([sticker, count]) => 
                                `<div style="background: white; padding: 10px; border-radius: 10px; box-shadow: 0 2px 8px rgba(0,0,0,0.1);">
                                    <div style="font-size: 2rem; margin-bottom: 5px;">${sticker}</div>
                                    <div style="font-size: 0.9rem; color: #666; font-weight: bold;">${count}개</div>
                                </div>`
                            ).join('')}
                        </div>
                    </div>
                    
                    <div style="background: #FFF8E1; padding: 20px; border-radius: 15px; margin: 15px 0;">
                        <h4 style="color: #FF9800; margin: 0 0 15px 0; text-align: center;">🎯 스티커 획득 방법</h4>
                        <div style="color: #666; font-size: 0.9rem; line-height: 1.6;">
                            • 📚 교실에서 수학 문제 맞히기<br>
                            • 🏛️ 교장실에서 퀴즈 맞히기<br>
                            • 🏥 보건실에서 건강 퀴즈 맞히기<br>
                            • 🎨 미술실에서 안전 퀴즈 맞히기<br>
                            • 👩‍🏫 교무실에서 큰 소리로 말하기<br>
                            • 📅 매일 출석하기
                        </div>
                    </div>
                    
                    <div style="background: #E8F5E8; padding: 15px; border-radius: 15px; margin: 15px 0; text-align: center;">
                        <div style="color: #2E7D32; font-weight: bold; margin-bottom: 5px;">🎁 다음 목표</div>
                        <div style="color: #666; font-size: 0.9rem;">
                            ${totalStickers < 20 ? `${20 - totalStickers}개 더 모으면 칭찬 스티커 달성!` :
                              totalStickers < 30 ? `${30 - totalStickers}개 더 모으면 스티커 수집가!` :
                              totalStickers < 50 ? `${50 - totalStickers}개 더 모으면 스티커 마스터!` :
                              '모든 목표를 달성했어요! 🏆'}
                        </div>
                    </div>
                    
                    <div style="text-align: center; margin-top: 20px;">
                        <button onclick="this.closest('.modal').remove()" 
                                style="background: linear-gradient(45deg, #4ECDC4, #44A08D); color: white; border: none; border-radius: 25px; padding: 12px 25px; font-size: 1rem; cursor: pointer; font-family: inherit;">
                            ✨ 더 많은 스티커 모으러 가기
                        </button>
                    </div>
                </div>
            `;
            
            document.body.appendChild(stickerModal);
            
            // 클릭으로 모달 닫기
            stickerModal.addEventListener('click', function(e) {
                if (e.target === stickerModal) {
                    stickerModal.remove();
                }
            });
        }
        
        function generateMathProblem() {
            currentMathProblem = mathProblems[Math.floor(Math.random() * mathProblems.length)];
            return `
                <div class="math-problem">
                    <div class="math-question">${currentMathProblem.question}</div>
                    <input type="number" class="math-input" id="mathAnswer" placeholder="답">
                    <button class="math-submit" onclick="checkMathAnswer()">확인</button>
                </div>
                <div class="stamp-collection">
                    ${attendanceData.stamps.map(stamp => `<span class="stamp">${stamp}</span>`).join('')}
                </div>
            `;
        }

        function generateQuiz(type) {
            let quizzes;
            if (type === 'principal') {
                quizzes = principalQuizzes;
            } else if (type === 'health') {
                quizzes = healthQuizzes;
            } else if (type === 'art') {
                quizzes = artQuizzes;
            }
            currentQuiz = quizzes[Math.floor(Math.random() * quizzes.length)];
            
            return `
                <div class="math-problem">
                    <div class="math-question">${currentQuiz.question}</div>
                    <div style="display: flex; flex-direction: column; gap: 10px; margin: 15px 0;">
                        ${currentQuiz.options.map((option, index) => 
                            `<button class="math-submit" onclick="checkQuizAnswer(${index})" style="width: 100%; padding: 10px;">${index + 1}. ${option}</button>`
                        ).join('')}
                    </div>
                </div>
                <div class="stamp-collection">
                    ${attendanceData.stamps.map(stamp => `<span class="stamp">${stamp}</span>`).join('')}
                </div>
            `;
        }

        function generateVoiceChallenge() {
            const friends = ['민수', '지영', '하늘', '도윤', '서연', '준호', '예린', '시우', '채원', '건우'];
            const randomFriend = friends[Math.floor(Math.random() * friends.length)];
            
            return `
                <div class="math-problem">
                    <div class="math-question">친구 이름을 큰 소리로 불러보세요!</div>
                    <div style="font-size: 1.8rem; color: #FF6B6B; margin: 20px 0; font-weight: bold;">"${randomFriend}"</div>
                    <button class="math-submit" onclick="startVoiceChallenge('${randomFriend}')" id="voiceBtn">🎤 큰 소리로 말하기</button>
                    <div id="voiceResult" style="margin-top: 15px;"></div>
                </div>
                <div class="stamp-collection">
                    ${attendanceData.stamps.map(stamp => `<span class="stamp">${stamp}</span>`).join('')}
                </div>
            `;
        }

        function generateCounseling() {
            const concerns = [
                '새 학교가 무서워요',
                '친구를 사귀고 싶어요',
                '공부가 어려워요',
                '선생님이 무서워요',
                '급식이 걱정돼요',
                '화장실이 어디인지 모르겠어요'
            ];
            
            return `
                <div style="background: #FFF0F5; padding: 20px; border-radius: 15px; margin: 15px 0;">
                    <div style="font-size: 1.3rem; color: #FF69B4; margin-bottom: 15px;">💕 어떤 고민이 있나요?</div>
                    <div style="display: flex; flex-direction: column; gap: 10px;">
                        ${concerns.map((concern, index) => 
                            `<button class="math-submit" onclick="showCounselingResponse('${concern}')" style="width: 100%; padding: 10px; background: #FFB6C1;">${concern}</button>`
                        ).join('')}
                    </div>
                    <div id="counselingResponse" style="margin-top: 15px;"></div>
                </div>
            `;
        }

        function generatePlaygroundGuide() {
            const equipment = [
                {
                    name: '미끄럼틀',
                    icon: '🛝',
                    usage: '계단으로 올라가서 앉아서 미끄러져 내려와요',
                    safety: '• 한 명씩 차례대로 타요\n• 거꾸로 올라가지 마세요\n• 미끄럼틀 아래 친구가 없는지 확인해요'
                },
                {
                    name: '그네',
                    icon: '🪀',
                    usage: '그네 의자에 앉아서 다리로 밀어주며 앞뒤로 움직여요',
                    safety: '• 그네 앞뒤로 지나다니지 마세요\n• 너무 높이 올라가지 마세요\n• 뛰어내리지 마세요'
                },
                {
                    name: '시소',
                    icon: '⚖️',
                    usage: '양쪽에 앉아서 번갈아가며 위아래로 움직여요',
                    safety: '• 갑자기 일어나지 마세요\n• 손잡이를 꽉 잡아요\n• 무게가 비슷한 친구와 함께 타요'
                },
                {
                    name: '정글짐',
                    icon: '🏗️',
                    usage: '손과 발을 이용해서 천천히 올라가고 내려와요',
                    safety: '• 미끄러운 날에는 타지 마세요\n• 너무 높이 올라가지 마세요\n• 친구를 밀거나 당기지 마세요'
                },
                {
                    name: '철봉',
                    icon: '🤸',
                    usage: '철봉을 잡고 매달리거나 턱걸이를 해요',
                    safety: '• 손에 땀이 나면 잘 닦아요\n• 무리하지 마세요\n• 아래 친구가 없는지 확인해요'
                }
            ];
            
            return `
                <div style="background: #E8F5E8; padding: 20px; border-radius: 15px; margin: 15px 0;">
                    <div style="font-size: 1.3rem; color: #228B22; margin-bottom: 15px; text-align: center;">🏃‍♂️ 운동장 놀이기구 안내</div>
                    <div style="display: flex; flex-direction: column; gap: 15px;">
                        ${equipment.map(item => 
                            `<div style="background: white; padding: 15px; border-radius: 10px; border-left: 4px solid #32CD32;">
                                <div style="display: flex; align-items: center; margin-bottom: 10px;">
                                    <span style="font-size: 2rem; margin-right: 10px;">${item.icon}</span>
                                    <span style="font-size: 1.2rem; font-weight: bold; color: #228B22;">${item.name}</span>
                                </div>
                                <div style="color: #666; margin-bottom: 8px;"><strong>사용법:</strong> ${item.usage}</div>
                                <div style="color: #D2691E; font-size: 0.9rem; white-space: pre-line;"><strong>⚠️ 안전수칙:</strong>\n${item.safety}</div>
                            </div>`
                        ).join('')}
                    </div>
                    <div style="background: #FFE4B5; padding: 15px; border-radius: 10px; margin-top: 15px; text-align: center;">
                        <div style="color: #FF6B6B; font-weight: bold; margin-bottom: 5px;">🚨 중요한 약속</div>
                        <div style="color: #666; font-size: 0.9rem;">놀이기구는 순서를 지켜서 사용하고, 다치면 즉시 선생님께 말씀드려요!</div>
                    </div>
                </div>
            `;
        }

        function generateBookRecommendations() {
            const books = [
                {
                    title: '아낌없이 주는 나무',
                    author: '셸 실버스타인',
                    summary: '한 소년과 나무의 아름다운 우정 이야기예요. 나무는 소년을 위해 자신의 모든 것을 내어주며 사랑의 의미를 알려줍니다.',
                    videoId: 'OTqIT5R4hrc',
                    genre: '감동'
                },
                {
                    title: '마당을 나온 암탉',
                    author: '황선미',
                    summary: '자유를 꿈꾸는 암탉 잎싹이 마당을 나와 겪는 모험 이야기예요. 꿈과 용기, 모성애에 대한 감동적인 동화입니다.',
                    videoId: 'Zn8fxHBxFxs',
                    genre: '모험'
                },
                {
                    title: '강아지똥',
                    author: '권정생',
                    summary: '작고 보잘것없어 보이는 강아지똥이 예쁜 민들레꽃을 피우는 데 도움을 주는 이야기예요. 생명의 소중함을 배울 수 있어요.',
                    videoId: 'XqZsoesa55w',
                    genre: '교훈'
                },
                {
                    title: '백설공주',
                    author: '그림형제',
                    summary: '일곱 난쟁이와 함께 살게 된 백설공주의 이야기예요. 착한 마음과 우정의 힘을 보여주는 전래동화입니다.',
                    videoId: 'TiFVWNMqYcA',
                    genre: '전래동화'
                },
                {
                    title: '신데렐라',
                    author: '샤를 페로',
                    summary: '유리구두를 신은 신데렐라가 왕자님을 만나는 마법 같은 이야기예요. 꿈을 포기하지 않는 마음을 배울 수 있어요.',
                    videoId: 'PlxTob4kGfA',
                    genre: '전래동화'
                },
                {
                    title: '빨간 모자',
                    author: '그림형제',
                    summary: '할머니께 음식을 가져다드리러 가는 빨간 모자의 이야기예요. 낯선 사람을 조심해야 한다는 교훈을 줍니다.',
                    videoId: 'NVmgWZ8VH9k',
                    genre: '전래동화'
                }
            ];
            
            return `
                <div style="background: #F0F8FF; padding: 20px; border-radius: 15px; margin: 15px 0;">
                    <div style="font-size: 1.3rem; color: #4169E1; margin-bottom: 15px; text-align: center;">📚 초등학생 추천 도서</div>
                    <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 15px;">
                        ${books.map((book, index) => 
                            `<div style="background: white; padding: 15px; border-radius: 10px; border: 2px solid #E6E6FA; cursor: pointer; transition: all 0.3s ease;" onclick="showBookDetails(${index})">
                                <div style="font-size: 1.1rem; font-weight: bold; color: #4169E1; margin-bottom: 5px;">${book.title}</div>
                                <div style="color: #666; font-size: 0.9rem; margin-bottom: 8px;">✍️ ${book.author}</div>
                                <div style="background: #E6E6FA; padding: 5px 10px; border-radius: 15px; display: inline-block; font-size: 0.8rem; color: #4169E1;">${book.genre}</div>
                            </div>`
                        ).join('')}
                    </div>
                    <div id="bookDetails" style="margin-top: 20px;"></div>
                </div>
            `;
        }

        function showBookDetails(bookIndex) {
            const books = [
                {
                    title: '아낌없이 주는 나무',
                    author: '셸 실버스타인',
                    summary: '한 소년과 나무의 아름다운 우정 이야기예요. 나무는 소년을 위해 자신의 모든 것을 내어주며 사랑의 의미를 알려줍니다.',
                    videoId: 'OTqIT5R4hrc',
                    genre: '감동'
                },
                {
                    title: '마당을 나온 암탉',
                    author: '황선미',
                    summary: '자유를 꿈꾸는 암탉 잎싹이 마당을 나와 겪는 모험 이야기예요. 꿈과 용기, 모성애에 대한 감동적인 동화입니다.',
                    videoId: 'Zn8fxHBxFxs',
                    genre: '모험'
                },
                {
                    title: '강아지똥',
                    author: '권정생',
                    summary: '작고 보잘것없어 보이는 강아지똥이 예쁜 민들레꽃을 피우는 데 도움을 주는 이야기예요. 생명의 소중함을 배울 수 있어요.',
                    videoId: 'XqZsoesa55w',
                    genre: '교훈'
                },
                {
                    title: '백설공주',
                    author: '그림형제',
                    summary: '일곱 난쟁이와 함께 살게 된 백설공주의 이야기예요. 착한 마음과 우정의 힘을 보여주는 전래동화입니다.',
                    videoId: 'TiFVWNMqYcA',
                    genre: '전래동화'
                },
                {
                    title: '신데렐라',
                    author: '샤를 페로',
                    summary: '유리구두를 신은 신데렐라가 왕자님을 만나는 마법 같은 이야기예요. 꿈을 포기하지 않는 마음을 배울 수 있어요.',
                    videoId: 'PlxTob4kGfA',
                    genre: '전래동화'
                },
                {
                    title: '빨간 모자',
                    author: '그림형제',
                    summary: '할머니께 음식을 가져다드리러 가는 빨간 모자의 이야기예요. 낯선 사람을 조심해야 한다는 교훈을 줍니다.',
                    videoId: 'NVmgWZ8VH9k',
                    genre: '전래동화'
                }
            ];
            
            const book = books[bookIndex];
            const bookDetails = document.getElementById('bookDetails');
            
            bookDetails.innerHTML = `
                <div style="background: #FFF8DC; padding: 20px; border-radius: 15px; border: 3px solid #FFD700;">
                    <div style="font-size: 1.4rem; font-weight: bold; color: #FF6B6B; margin-bottom: 10px; text-align: center;">📖 ${book.title}</div>
                    <div style="color: #666; text-align: center; margin-bottom: 15px;">✍️ ${book.author}</div>
                    <div style="color: #333; line-height: 1.6; margin-bottom: 20px; text-align: center;">${book.summary}</div>
                    <div style="text-align: center;">
                        <button onclick="window.open('https://www.youtube.com/watch?v=${book.videoId}', '_blank')" 
                                style="background: #FF0000; color: white; border: none; border-radius: 25px; padding: 12px 25px; font-size: 1rem; cursor: pointer; margin: 5px;">
                            📺 유튜브에서 보기
                        </button>
                        <button onclick="document.getElementById('bookDetails').innerHTML = ''" 
                                style="background: #666; color: white; border: none; border-radius: 25px; padding: 12px 25px; font-size: 1rem; cursor: pointer; margin: 5px;">
                            📚 다른 책 보기
                        </button>
                    </div>
                </div>
            `;
        }
        
        function checkMathAnswer() {
            const userAnswer = parseInt(document.getElementById('mathAnswer').value);
            
            if (userAnswer === currentMathProblem.answer) {
                const stamps = ['🌟', '⭐', '✨', '🎯', '🏆', '🎉'];
                const newStamp = stamps[Math.floor(Math.random() * stamps.length)];
                attendanceData.stamps.push(newStamp);
                localStorage.setItem('schoolAttendance', JSON.stringify(attendanceData));
                
                document.querySelector('.math-problem').innerHTML = `
                    <div style="color: #32CD32; font-size: 1.3rem;">🎉 정답이에요! 도장을 받았어요!</div>
                `;
                
                setTimeout(() => {
                    const stampCollection = document.querySelector('.stamp-collection');
                    if (stampCollection) {
                        stampCollection.innerHTML = attendanceData.stamps.map(stamp => `<span class="stamp">${stamp}</span>`).join('');
                    }
                }, 500);
            } else {
                document.querySelector('.math-problem').innerHTML = `
                    <div style="color: #FF6B6B; font-size: 1.2rem;">다시 한번 생각해보세요! 💪</div>
                    <button class="math-submit" onclick="openModal('classroom')" style="margin-top: 10px;">새 문제</button>
                `;
            }
        }

        function checkQuizAnswer(selectedIndex) {
            if (selectedIndex === currentQuiz.answer) {
                const stamps = ['👑', '🏅', '🎖️', '🌟', '⭐', '✨'];
                const newStamp = stamps[Math.floor(Math.random() * stamps.length)];
                attendanceData.stamps.push(newStamp);
                localStorage.setItem('schoolAttendance', JSON.stringify(attendanceData));
                
                document.querySelector('.math-problem').innerHTML = `
                    <div style="color: #32CD32; font-size: 1.3rem;">🎉 정답이에요! 특별한 도장을 받았어요!</div>
                `;
                
                setTimeout(() => {
                    const stampCollection = document.querySelector('.stamp-collection');
                    if (stampCollection) {
                        stampCollection.innerHTML = attendanceData.stamps.map(stamp => `<span class="stamp">${stamp}</span>`).join('');
                    }
                }, 500);
            } else {
                document.querySelector('.math-problem').innerHTML = `
                    <div style="color: #FF6B6B; font-size: 1.2rem;">다시 한번 생각해보세요! 💪</div>
                    <button class="math-submit" onclick="location.reload()" style="margin-top: 10px;">새 문제</button>
                `;
            }
        }

        function startVoiceChallenge(friendName) {
            const voiceBtn = document.getElementById('voiceBtn');
            const voiceResult = document.getElementById('voiceResult');
            
            voiceBtn.textContent = '🎤 듣고 있어요... 큰 소리로!';
            voiceBtn.disabled = true;
            
            // 음성 인식 시뮬레이션 (실제로는 Web Speech API 사용 불가능한 환경)
            setTimeout(() => {
                const success = Math.random() > 0.3; // 70% 성공률
                
                if (success) {
                    const stamps = ['🎤', '📢', '🔊', '👏', '🎉', '⭐'];
                    const newStamp = stamps[Math.floor(Math.random() * stamps.length)];
                    attendanceData.stamps.push(newStamp);
                    localStorage.setItem('schoolAttendance', JSON.stringify(attendanceData));
                    
                    voiceResult.innerHTML = `
                        <div style="color: #32CD32; font-size: 1.2rem;">🎉 훌륭해요! 자신있게 잘 말했어요!</div>
                        <div style="color: #666; font-size: 1rem; margin-top: 10px;">스티커를 받았어요! 👏</div>
                    `;
                    
                    setTimeout(() => {
                        const stampCollection = document.querySelector('.stamp-collection');
                        if (stampCollection) {
                            stampCollection.innerHTML = attendanceData.stamps.map(stamp => `<span class="stamp">${stamp}</span>`).join('');
                        }
                    }, 500);
                } else {
                    voiceResult.innerHTML = `
                        <div style="color: #FF6B6B; font-size: 1.1rem;">조금 더 큰 소리로 말해보세요! 💪</div>
                        <button class="math-submit" onclick="startVoiceChallenge('${friendName}')" style="margin-top: 10px;">다시 도전하기</button>
                    `;
                    voiceBtn.disabled = false;
                    voiceBtn.textContent = '🎤 큰 소리로 말하기';
                }
            }, 3000);
        }

        function showCounselingResponse(concern) {
            const responses = {
                '새 학교가 무서워요': '괜찮아요! 새로운 곳은 처음엔 누구나 무서워해요. 선생님과 친구들이 도와줄 거예요. 천천히 적응해보세요! 💕',
                '친구를 사귀고 싶어요': '좋은 마음이에요! 먼저 웃으면서 "안녕하세요"라고 인사해보세요. 함께 놀자고 말하면 친구가 될 수 있어요! 👫',
                '공부가 어려워요': '처음엔 모든 게 어려워요. 모르는 건 선생님께 물어보고, 천천히 하나씩 배워가면 돼요. 포기하지 마세요! 📚',
                '선생님이 무서워요': '선생님은 여러분을 도와주시려는 분이에요. 무서워하지 말고 궁금한 건 언제든 물어보세요. 선생님도 여러분을 좋아하세요! 👩‍🏫',
                '급식이 걱정돼요': '급식은 영양사 선생님이 맛있고 건강하게 만들어주세요. 새로운 음식도 한 번씩 맛보면 좋아하게 될 거예요! 🍽️',
                '화장실이 어디인지 모르겠어요': '화장실 위치를 모르면 언제든 선생님께 물어보세요. 급할 때는 손을 들고 말씀드리면 돼요. 부끄러워하지 마세요! 🚻'
            };
            
            const response = responses[concern];
            document.getElementById('counselingResponse').innerHTML = `
                <div style="background: #E6F3FF; padding: 15px; border-radius: 10px; border-left: 4px solid #4ECDC4;">
                    <div style="color: #4ECDC4; font-weight: bold; margin-bottom: 10px;">💝 상담선생님의 따뜻한 조언</div>
                    <div style="color: #666; line-height: 1.5;">${response}</div>
                </div>
                <button class="math-submit" onclick="generateCounseling(); document.getElementById('counselingResponse').innerHTML = '';" style="margin-top: 15px; background: #FFB6C1;">다른 고민도 이야기하기</button>
            `;
        }
        
        function createChairSVG() {
            return `
                <div class="cafeteria-chair">
                    <svg class="chair-svg" viewBox="0 0 200 200">
                        <!-- 의자 등받이 -->
                        <circle cx="100" cy="80" r="45" fill="#8B4513" stroke="#654321" stroke-width="3"/>
                        <!-- 의자 좌석 -->
                        <circle cx="100" cy="120" r="35" fill="#A0522D" stroke="#654321" stroke-width="3"/>
                        <!-- 테이블 -->
                        <ellipse cx="100" cy="140" rx="50" ry="15" fill="#DEB887" stroke="#CD853F" stroke-width="2"/>
                        <!-- 다리 -->
                        <rect x="95" y="155" width="10" height="30" fill="#654321"/>
                    </svg>
                    <p style="color: #666; margin: 10px 0;">초등학교 급식실의 특별한 둥근 의자예요!</p>
                    <div style="background: #FFF8DC; padding: 15px; border-radius: 10px; margin: 15px 0;">
                        <h4 style="color: #FF6B6B; margin: 0 0 10px 0;">안전하게 앉는 방법:</h4>
                        <p style="margin: 5px 0;">• 의자를 살짝 빼고 앉아요</p>
                        <p style="margin: 5px 0;">• 일어날 때는 의자를 밀어 넣어요</p>
                        <p style="margin: 5px 0;">• 친구들과 부딪히지 않게 조심해요</p>
                    </div>
                    <button class="vr-experience" onclick="startVRExperience()">🥽 의자 앉기 체험하기</button>
                </div>
            `;
        }
        
        function startVRExperience() {
            const vrSteps = [
                '🚶‍♀️ 의자 앞으로 걸어가요...',
                '🤏 의자를 살짝 뒤로 빼요...',
                '🪑 천천히 앉아요...',
                '🍽️ 맛있게 급식을 먹어요!',
                '🧹 다 먹고 의자를 안으로 밀어요!'
            ];
            
            let step = 0;
            const vrButton = document.querySelector('.vr-experience');
            
            function nextStep() {
                if (step < vrSteps.length) {
                    vrButton.textContent = vrSteps[step];
                    step++;
                    setTimeout(nextStep, 2000);
                } else {
                    vrButton.textContent = '🎉 체험 완료! 잘했어요!';
                    setTimeout(() => {
                        vrButton.textContent = '🥽 의자 앉기 체험하기';
                    }, 3000);
                }
            }
            
            nextStep();
        }

        function openModal(type) {
            const modal = document.getElementById('modal');
            const modalBody = document.getElementById('modal-body');
            const content = modalContents[type];
            
            let modalContent = `
                <div class="modal-icon">${content.icon}</div>
                <h3 class="modal-title">${content.title}</h3>
                <p class="modal-text">${content.text}</p>
            `;
            
            if (content.showMath) {
                modalContent += generateMathProblem();
            }
            
            if (content.showQuiz) {
                modalContent += generateQuiz(content.quizType);
            }
            
            if (content.showVoice) {
                modalContent += generateVoiceChallenge();
            }
            
            if (content.showCounseling) {
                modalContent += generateCounseling();
            }
            
            if (content.showPlayground) {
                modalContent += generatePlaygroundGuide();
            }
            
            if (content.showBooks) {
                modalContent += generateBookRecommendations();
            }
            
            if (content.showChair) {
                modalContent += createChairSVG();
            }
            
            if (content.showInstruments) {
                modalContent += generateInstrumentsGuide();
            }
            
            if (content.showHealthTeacher) {
                modalContent += generateHealthTeacher();
            }
            
            if (content.showGallery) {
                modalContent += generateGallery();
            }
            
            if (content.showUpload) {
                modalContent += generateUploadSection();
            }
            
            modalBody.innerHTML = modalContent;
            modal.style.display = 'flex';
        }

        function closeModal(event) {
            const modal = document.getElementById('modal');
            if (!event || event.target === modal || event.target.classList.contains('close-btn')) {
                modal.style.display = 'none';
            }
        }

        function generateGallery() {
            const categories = {
                classroom: '교실',
                playground: '운동장',
                library: '도서관',
                cafeteria: '급식실',
                music: '음악실',
                art: '미술실',
                health: '보건실',
                teachers: '교무실',
                principal: '교장실',
                counseling: '상담실',
                entrance: '학교 입구',
                hallway: '복도',
                garden: '학교 정원',
                events: '학교 행사'
            };
            
            return `
                <div class="gallery-container">
                    <div style="text-align: center; margin-bottom: 20px;">
                        <div style="font-size: 1.2rem; color: #1976D2; margin-bottom: 15px;">📸 카테고리별 학교 사진</div>
                        <div class="category-selector">
                            ${Object.entries(categories).map(([key, name]) => 
                                `<button class="category-btn ${key === selectedCategory ? 'active' : ''}" onclick="selectCategory('${key}')">${name}</button>`
                            ).join('')}
                        </div>
                    </div>
                    <div id="galleryGrid" class="gallery-grid">
                        ${generateGalleryItems()}
                    </div>
                    ${schoolPhotos[selectedCategory].length === 0 ? 
                        `<div style="text-align: center; color: #666; margin: 30px 0;">
                            <div style="font-size: 3rem; margin-bottom: 10px;">📷</div>
                            <div>아직 ${categories[selectedCategory]} 사진이 없어요</div>
                            <div style="font-size: 0.9rem; margin-top: 5px;">선생님이 곧 멋진 사진을 올려주실 거예요!</div>
                        </div>` : ''
                    }
                </div>
            `;
        }
        
        function generateGalleryItems() {
            const photos = schoolPhotos[selectedCategory] || [];
            
            if (photos.length === 0) {
                return '';
            }
            
            return photos.map((photo, index) => `
                <div class="gallery-item" onclick="openPhotoModal(${index})">
                    <img src="${photo.url}" alt="${photo.title}" class="gallery-image" onerror="this.parentElement.innerHTML='<div class=\\'gallery-placeholder\\'>❌</div><div class=\\'gallery-label\\'>이미지 로드 실패</div>'">
                    <div class="gallery-label">${photo.title}</div>
                </div>
            `).join('');
        }
        
        function generateUploadSection() {
            const categories = {
                classroom: '교실',
                playground: '운동장',
                library: '도서관',
                cafeteria: '급식실',
                music: '음악실',
                art: '미술실',
                health: '보건실',
                teachers: '교무실',
                principal: '교장실',
                counseling: '상담실',
                entrance: '학교 입구',
                hallway: '복도',
                garden: '학교 정원',
                events: '학교 행사'
            };
            
            return `
                <div class="upload-section">
                    <div style="text-align: center; margin-bottom: 20px;">
                        <div style="font-size: 1.2rem; color: #FF9800; margin-bottom: 15px;">📤 사진 업로드</div>
                        <div class="category-selector">
                            ${Object.entries(categories).map(([key, name]) => 
                                `<button class="category-btn ${key === selectedCategory ? 'active' : ''}" onclick="selectUploadCategory('${key}')">${name}</button>`
                            ).join('')}
                        </div>
                    </div>
                    
                    <div class="upload-area" onclick="document.getElementById('fileInput').click()" 
                         ondrop="handleDrop(event)" ondragover="handleDragOver(event)" ondragleave="handleDragLeave(event)">
                        <div style="font-size: 3rem; margin-bottom: 15px;">📁</div>
                        <div style="font-size: 1.2rem; color: #FF9800; margin-bottom: 10px;">사진을 여기에 끌어다 놓거나 클릭하세요</div>
                        <div style="font-size: 0.9rem; color: #666;">JPG, PNG, GIF 파일을 업로드할 수 있어요</div>
                        <button class="upload-btn" onclick="event.stopPropagation(); document.getElementById('fileInput').click()">📷 파일 선택</button>
                    </div>
                    
                    <input type="file" id="fileInput" class="file-input" multiple accept="image/*" onchange="handleFileSelect(event)">
                    
                    <div style="margin-top: 20px;">
                        <div style="font-size: 1rem; color: #666; margin-bottom: 10px;">📝 사진 제목:</div>
                        <input type="text" id="photoTitle" placeholder="예: 우리 반 교실, 점심시간 급식실" 
                               style="width: 100%; padding: 10px; border: 2px solid #FFB74D; border-radius: 10px; font-size: 1rem; box-sizing: border-box;">
                    </div>
                    
                    <div style="background: #E8F5E8; padding: 15px; border-radius: 10px; margin-top: 15px;">
                        <div style="color: #2E7D32; font-weight: bold; margin-bottom: 5px;">📋 업로드된 사진 (${categories[selectedCategory]})</div>
                        <div style="color: #666; font-size: 0.9rem;">총 ${schoolPhotos[selectedCategory].length}장</div>
                        ${schoolPhotos[selectedCategory].length > 0 ? 
                            `<div style="margin-top: 10px;">
                                ${schoolPhotos[selectedCategory].slice(-3).map(photo => 
                                    `<span style="background: white; padding: 5px 10px; border-radius: 15px; margin: 2px; display: inline-block; font-size: 0.8rem;">${photo.title}</span>`
                                ).join('')}
                                ${schoolPhotos[selectedCategory].length > 3 ? '<span style="color: #666;">...</span>' : ''}
                            </div>` : ''
                        }
                    </div>
                </div>
            `;
        }
        
        function selectCategory(category) {
            selectedCategory = category;
            const galleryGrid = document.getElementById('galleryGrid');
            if (galleryGrid) {
                galleryGrid.innerHTML = generateGalleryItems();
            }
            
            // 카테고리 버튼 활성화 상태 업데이트
            document.querySelectorAll('.category-btn').forEach(btn => {
                btn.classList.remove('active');
            });
            event.target.classList.add('active');
        }
        
        function selectUploadCategory(category) {
            selectedCategory = category;
            
            // 카테고리 버튼 활성화 상태 업데이트
            document.querySelectorAll('.category-btn').forEach(btn => {
                btn.classList.remove('active');
            });
            event.target.classList.add('active');
            
            // 업로드 섹션 새로고침
            openModal('teacher-upload');
        }
        
        function handleDragOver(event) {
            event.preventDefault();
            event.target.closest('.upload-area').classList.add('dragover');
        }
        
        function handleDragLeave(event) {
            event.target.closest('.upload-area').classList.remove('dragover');
        }
        
        function handleDrop(event) {
            event.preventDefault();
            event.target.closest('.upload-area').classList.remove('dragover');
            
            const files = event.dataTransfer.files;
            processFiles(files);
        }
        
        function handleFileSelect(event) {
            const files = event.target.files;
            processFiles(files);
        }
        
        function processFiles(files) {
            const photoTitle = document.getElementById('photoTitle').value.trim();
            
            if (!photoTitle) {
                showUploadMessage('사진 제목을 입력해주세요!', 'error');
                return;
            }
            
            Array.from(files).forEach((file, index) => {
                if (file.type.startsWith('image/')) {
                    const reader = new FileReader();
                    reader.onload = function(e) {
                        const photo = {
                            id: Date.now() + index,
                            title: files.length > 1 ? `${photoTitle} ${index + 1}` : photoTitle,
                            url: e.target.result,
                            category: selectedCategory,
                            uploadDate: new Date().toLocaleDateString()
                        };
                        
                        schoolPhotos[selectedCategory].push(photo);
                        localStorage.setItem('schoolPhotos', JSON.stringify(schoolPhotos));
                        
                        showUploadMessage(`"${photo.title}" 사진이 업로드되었어요! 📸`, 'success');
                        
                        // 업로드 섹션 새로고침
                        setTimeout(() => {
                            openModal('teacher-upload');
                        }, 1500);
                    };
                    reader.readAsDataURL(file);
                } else {
                    showUploadMessage('이미지 파일만 업로드할 수 있어요!', 'error');
                }
            });
            
            // 입력 필드 초기화
            document.getElementById('photoTitle').value = '';
            document.getElementById('fileInput').value = '';
        }
        
        function showUploadMessage(message, type) {
            const messageDiv = document.createElement('div');
            messageDiv.style.cssText = `
                position: fixed;
                top: 20px;
                right: 20px;
                padding: 15px 25px;
                border-radius: 25px;
                color: white;
                font-weight: bold;
                z-index: 3000;
                animation: slideIn 0.3s ease-out;
                background: ${type === 'success' ? '#4CAF50' : '#F44336'};
            `;
            messageDiv.textContent = message;
            
            document.body.appendChild(messageDiv);
            
            setTimeout(() => {
                messageDiv.remove();
            }, 3000);
        }
        
        function openPhotoModal(photoIndex) {
            currentPhotoIndex = photoIndex;
            const photos = schoolPhotos[selectedCategory];
            const photo = photos[photoIndex];
            
            const photoModal = document.createElement('div');
            photoModal.className = 'photo-modal';
            photoModal.style.display = 'flex';
            photoModal.innerHTML = `
                <div class="photo-modal-content">
                    <button class="photo-close" onclick="closePhotoModal()">&times;</button>
                    <img src="${photo.url}" alt="${photo.title}">
                    <div style="position: absolute; bottom: -50px; left: 0; right: 0; text-align: center; color: white;">
                        <div style="font-size: 1.2rem; font-weight: bold;">${photo.title}</div>
                        <div style="font-size: 0.9rem; margin-top: 5px;">업로드: ${photo.uploadDate}</div>
                        <div style="margin-top: 10px;">
                            <button onclick="prevPhoto()" style="background: rgba(255,255,255,0.2); color: white; border: none; border-radius: 50%; width: 40px; height: 40px; margin: 0 10px; cursor: pointer;">‹</button>
                            <span>${photoIndex + 1} / ${photos.length}</span>
                            <button onclick="nextPhoto()" style="background: rgba(255,255,255,0.2); color: white; border: none; border-radius: 50%; width: 40px; height: 40px; margin: 0 10px; cursor: pointer;">›</button>
                        </div>
                    </div>
                </div>
            `;
            
            document.body.appendChild(photoModal);
            
            // 클릭으로 모달 닫기
            photoModal.addEventListener('click', function(e) {
                if (e.target === photoModal) {
                    closePhotoModal();
                }
            });
        }
        
        function closePhotoModal() {
            const photoModal = document.querySelector('.photo-modal');
            if (photoModal) {
                photoModal.remove();
            }
        }
        
        function prevPhoto() {
            const photos = schoolPhotos[selectedCategory];
            currentPhotoIndex = (currentPhotoIndex - 1 + photos.length) % photos.length;
            closePhotoModal();
            openPhotoModal(currentPhotoIndex);
        }
        
        function nextPhoto() {
            const photos = schoolPhotos[selectedCategory];
            currentPhotoIndex = (currentPhotoIndex + 1) % photos.length;
            closePhotoModal();
            openPhotoModal(currentPhotoIndex);
        }

        function generateInstrumentsGuide() {
            const instruments = [
                {
                    name: '피아노',
                    icon: '🎹',
                    usage: '건반을 손가락으로 눌러서 연주해요. 오른손은 높은 음, 왼손은 낮은 음을 담당해요.',
                    tips: '• 등을 곧게 펴고 앉아요\n• 손목을 부드럽게 유지해요\n• 처음엔 한 손가락씩 연습해요',
                    sound: '도레미파솔라시도~ ♪'
                },
                {
                    name: '실로폰',
                    icon: '🎵',
                    usage: '나무나 금속 막대를 말렛(작은 망치)으로 두드려서 소리를 내요.',
                    tips: '• 말렛을 너무 세게 치지 마세요\n• 각 음판의 가운데를 쳐요\n• 리듬에 맞춰 연주해요',
                    sound: '딩동댕~ 맑은 소리! ✨'
                },
                {
                    name: '탬버린',
                    icon: '🪘',
                    usage: '손으로 치거나 흔들어서 방울 소리와 북 소리를 함께 내요.',
                    tips: '• 손바닥으로 가볍게 쳐요\n• 흔들면서 리듬을 만들어요\n• 친구들과 함께 연주하면 더 재미있어요',
                    sound: '짤랑짤랑 쨍그랑! 🎶'
                },
                {
                    name: '트라이앵글',
                    icon: '🔺',
                    usage: '삼각형 모양의 금속을 작은 막대로 쳐서 맑은 소리를 내요.',
                    tips: '• 실로 매달고 연주해요\n• 살짝만 쳐도 큰 소리가 나요\n• 조용한 부분에서 효과적이에요',
                    sound: '띵~ 맑고 긴 여운! ✨'
                },
                {
                    name: '캐스터네츠',
                    icon: '🥄',
                    usage: '두 개의 나무 조각을 손가락으로 딱딱 부딪혀서 소리를 내요.',
                    tips: '• 엄지와 중지에 끼워서 사용해요\n• 빠른 리듬 연주에 좋아요\n• 스페인 춤 음악에 많이 써요',
                    sound: '딱딱딱! 경쾌한 리듬! 💃'
                },
                {
                    name: '리코더',
                    icon: '🎶',
                    usage: '입으로 불면서 손가락으로 구멍을 막았다 열었다 하며 연주해요.',
                    tips: '• 부드럽게 불어요 (너무 세게 불면 안 돼요)\n• 손가락으로 구멍을 완전히 막아요\n• 매일 조금씩 연습하면 늘어요',
                    sound: '후우~ 아름다운 선율! 🎵'
                }
            ];
            
            return `
                <div style="background: #FFF8E7; padding: 20px; border-radius: 15px; margin: 15px 0;">
                    <div style="font-size: 1.3rem; color: #FF6B35; margin-bottom: 15px; text-align: center;">🎵 음악실 악기 체험관</div>
                    <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 15px;">
                        ${instruments.map((instrument, index) => 
                            `<div style="background: white; padding: 15px; border-radius: 10px; border: 2px solid #FFE4B5; cursor: pointer; transition: all 0.3s ease;" onclick="playInstrumentSound(${index})">
                                <div style="display: flex; align-items: center; margin-bottom: 10px;">
                                    <span style="font-size: 2rem; margin-right: 10px;">${instrument.icon}</span>
                                    <span style="font-size: 1.2rem; font-weight: bold; color: #FF6B35;">${instrument.name}</span>
                                </div>
                                <div style="color: #666; margin-bottom: 8px; font-size: 0.9rem;"><strong>연주법:</strong> ${instrument.usage}</div>
                                <div style="color: #2E7D32; font-size: 0.8rem; white-space: pre-line; margin-bottom: 10px;"><strong>🎯 연주 팁:</strong>\n${instrument.tips}</div>
                                <button onclick="event.stopPropagation(); playInstrumentSound(${index})" 
                                        style="background: linear-gradient(45deg, #FF6B35, #F7931E); color: white; border: none; border-radius: 20px; padding: 8px 15px; font-size: 0.9rem; cursor: pointer; width: 100%;">
                                    🔊 소리 들어보기
                                </button>
                                <div id="sound-${index}" style="margin-top: 10px; text-align: center; font-weight: bold; color: #FF6B35;"></div>
                            </div>`
                        ).join('')}
                    </div>
                    <div style="background: #E8F5E8; padding: 15px; border-radius: 10px; margin-top: 15px; text-align: center;">
                        <div style="color: #2E7D32; font-weight: bold; margin-bottom: 5px;">🎼 음악실에서의 약속</div>
                        <div style="color: #666; font-size: 0.9rem;">악기는 소중히 다루고, 차례를 지켜서 연주하며, 선생님 말씀을 잘 들어요!</div>
                    </div>
                </div>
            `;
        }

        function playInstrumentSound(instrumentIndex) {
            const instruments = [
                { name: '피아노', sound: '도레미파솔라시도~ ♪' },
                { name: '실로폰', sound: '딩동댕~ 맑은 소리! ✨' },
                { name: '탬버린', sound: '짤랑짤랑 쨍그랑! 🎶' },
                { name: '트라이앵글', sound: '띵~ 맑고 긴 여운! ✨' },
                { name: '캐스터네츠', sound: '딱딱딱! 경쾌한 리듬! 💃' },
                { name: '리코더', sound: '후우~ 아름다운 선율! 🎵' }
            ];
            
            const soundDiv = document.getElementById(`sound-${instrumentIndex}`);
            const instrument = instruments[instrumentIndex];
            
            soundDiv.innerHTML = `🎵 ${instrument.sound}`;
            soundDiv.style.animation = 'bounce 0.6s ease-in-out';
            
            // 3초 후 소리 표시 제거
            setTimeout(() => {
                soundDiv.innerHTML = '';
                soundDiv.style.animation = '';
            }, 3000);
        }

        function generateHealthTeacher() {
            return `
                <div style="background: #F0F8FF; padding: 20px; border-radius: 15px; margin: 15px 0;">
                    <div style="text-align: center; margin-bottom: 20px;">
                        <svg width="200" height="250" viewBox="0 0 200 250" style="margin: 0 auto;">
                            <!-- 보건선생님 캐릭터 -->
                            <!-- 머리 -->
                            <circle cx="100" cy="60" r="35" fill="#FDBCB4" stroke="#E8A598" stroke-width="2"/>
                            
                            <!-- 머리카락 -->
                            <path d="M 70 45 Q 100 25 130 45 Q 125 35 100 30 Q 75 35 70 45" fill="#8B4513"/>
                            
                            <!-- 눈 -->
                            <circle cx="90" cy="55" r="3" fill="#333"/>
                            <circle cx="110" cy="55" r="3" fill="#333"/>
                            
                            <!-- 코 -->
                            <circle cx="100" cy="65" r="1" fill="#E8A598"/>
                            
                            <!-- 입 (미소) -->
                            <path d="M 95 70 Q 100 75 105 70" stroke="#333" stroke-width="2" fill="none"/>
                            
                            <!-- 몸통 (흰 가운) -->
                            <rect x="75" y="95" width="50" height="80" fill="white" stroke="#E0E0E0" stroke-width="2" rx="5"/>
                            
                            <!-- 가운 버튼들 -->
                            <circle cx="100" cy="110" r="2" fill="#4CAF50"/>
                            <circle cx="100" cy="125" r="2" fill="#4CAF50"/>
                            <circle cx="100" cy="140" r="2" fill="#4CAF50"/>
                            
                            <!-- 가운 주머니 -->
                            <rect x="80" y="150" width="15" height="12" fill="white" stroke="#E0E0E0" stroke-width="1" rx="2"/>
                            <rect x="105" y="150" width="15" height="12" fill="white" stroke="#E0E0E0" stroke-width="1" rx="2"/>
                            
                            <!-- 팔 -->
                            <rect x="60" y="100" width="15" height="40" fill="#FDBCB4" rx="7"/>
                            <rect x="125" y="100" width="15" height="40" fill="#FDBCB4" rx="7"/>
                            
                            <!-- 청진기 -->
                            <circle cx="85" cy="105" r="8" fill="none" stroke="#2196F3" stroke-width="3"/>
                            <path d="M 85 97 Q 100 85 115 97" stroke="#2196F3" stroke-width="3" fill="none"/>
                            <circle cx="115" cy="97" r="3" fill="#2196F3"/>
                            
                            <!-- 다리 -->
                            <rect x="85" y="175" width="12" height="35" fill="#2196F3" rx="6"/>
                            <rect x="103" y="175" width="12" height="35" fill="#2196F3" rx="6"/>
                            
                            <!-- 신발 -->
                            <ellipse cx="91" cy="215" rx="8" ry="4" fill="white"/>
                            <ellipse cx="109" cy="215" rx="8" ry="4" fill="white"/>
                            
                            <!-- 십자가 마크 (가슴에) -->
                            <rect x="98" y="115" width="4" height="12" fill="#FF5722"/>
                            <rect x="94" y="119" width="12" height="4" fill="#FF5722"/>
                        </svg>
                        
                        <div style="font-size: 1.2rem; color: #2196F3; margin-top: 10px; font-weight: bold;">👩‍⚕️ 친절한 보건선생님</div>
                        <div style="color: #666; font-size: 0.9rem; margin-top: 5px;">"안녕하세요! 여러분의 건강을 지켜드릴게요!"</div>
                    </div>
                    
                    ${generateQuiz('health')}
                </div>
            `;
        }

        // 키보드 ESC로 모달 닫기
        document.addEventListener('keydown', function(event) {
            if (event.key === 'Escape') {
                closeModal();
                closePhotoModal();
            }
        });
    </script>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'99916437705cea33',t:'MTc2MjIzMDc4OC4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
