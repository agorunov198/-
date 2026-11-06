<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
    <title>КиберБезопасность СПО | Викторина</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', 'Roboto', system-ui, sans-serif;
        }
        body {
            background: linear-gradient(135deg, #0f172a 0%, #1e293b 50%, #0f172a 100%);
            min-height: 100vh;
            padding: 20px;
        }
        .container {
            max-width: 1400px;
            margin: 0 auto;
        }
        .header {
            background: rgba(255,255,255,0.98);
            border-radius: 32px;
            padding: 20px 28px;
            margin-bottom: 28px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            box-shadow: 0 20px 40px rgba(0,0,0,0.2);
        }
        h1 {
            background: linear-gradient(120deg, #1e6f5c, #2c7da0, #4a90e2);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            font-size: 1.6rem;
        }
        .mode-switch {
            display: flex;
            gap: 12px;
            background: white;
            padding: 6px;
            border-radius: 60px;
        }
        .mode-btn {
            background: transparent;
            color: #1e6f5c;
            padding: 8px 24px;
            border-radius: 50px;
            font-weight: 600;
            cursor: pointer;
            border: none;
            transition: all 0.3s ease;
        }
        .mode-btn.active {
            background: linear-gradient(120deg, #1e6f5c, #2c7da0);
            color: white;
        }
        .grid-2 {
            display: grid;
            grid-template-columns: 1fr 1.2fr;
            gap: 28px;
        }
        @media (max-width: 900px) {
            .grid-2 { grid-template-columns: 1fr; }
        }
        .card {
            background: rgba(255,255,255,0.98);
            border-radius: 32px;
            padding: 28px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.15);
        }
        .qr-box {
            background: #f8fafc;
            border-radius: 24px;
            padding: 24px;
            text-align: center;
            border: 2px solid #e2e8f0;
        }
        #qrcode {
            display: flex;
            justify-content: center;
            margin: 20px 0;
            min-height: 220px;
            background: white;
            border-radius: 16px;
            padding: 15px;
            flex-direction: column;
            align-items: center;
        }
        #qrcode canvas {
            max-width: 200px;
            border-radius: 16px;
            box-shadow: 0 4px 20px rgba(0,0,0,0.15);
        }
        button {
            background: linear-gradient(120deg, #1e6f5c, #2c7da0);
            border: none;
            color: white;
            padding: 12px 28px;
            border-radius: 60px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            display: inline-flex;
            align-items: center;
            gap: 8px;
        }
        button:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(30,111,92,0.4);
        }
        select, input, textarea {
            padding: 12px 18px;
            border-radius: 60px;
            border: 1px solid #cbd5e1;
            width: 100%;
            font-size: 0.95rem;
            margin: 8px 0;
        }
        textarea {
            border-radius: 20px;
            resize: vertical;
        }
        .stats-table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 20px;
        }
        .stats-table th, .stats-table td {
            padding: 12px 10px;
            text-align: left;
            border-bottom: 1px solid #e2e8f0;
        }
        .stats-table th {
            background: #eef2ff;
            font-weight: 700;
        }
        .live-badge {
            background: #10b981;
            color: white;
            font-size: 0.7rem;
            border-radius: 40px;
            margin-left: 10px;
            animation: pulse 1.5s infinite;
        }
        @keyframes pulse {
            0% { opacity: 0.7; }
            100% { opacity: 1; background: #059669; }
        }
        footer {
            text-align: center;
            margin-top: 40px;
            color: #94a3b8;
            font-size: 0.8rem;
        }
        .link-info {
            margin-top: 12px;
            font-size: 14px;
            word-break: break-all;
        }
        .danger-btn {
            background: #b45353;
        }
        .danger-btn:hover {
            background: #8b3a3a;
        }
        .copy-btn {
            background: #2c7da0;
            padding: 8px 16px;
            font-size: 0.8rem;
            margin-left: 10px;
        }
        .session-card {
            background: #fef3c7;
            border-left: 4px solid #f59e0b;
            margin-bottom: 16px;
            padding: 16px;
            border-radius: 16px;
        }
        .session-active {
            background: #d1fae5;
            border-left-color: #10b981;
        }
        .answers-grid {
            background: #f8fafc;
            padding: 10px;
            border-radius: 12px;
            margin-top: 10px;
            max-height: 300px;
            overflow-y: auto;
        }
        .live-sessions {
            max-height: 600px;
            overflow-y: auto;
        }
        .tab-buttons {
            display: flex;
            gap: 12px;
            margin-bottom: 16px;
            flex-wrap: wrap;
        }
        .tab-btn {
            background: #e2e8f0;
            color: #1a2a3f;
            padding: 8px 20px;
            border-radius: 40px;
            border: none;
            cursor: pointer;
            font-weight: 600;
        }
        .tab-btn.active {
            background: #1e6f5c;
            color: white;
        }
        .tab-content {
            display: none;
        }
        .tab-content.active {
            display: block;
        }
        .link-url {
            background: white;
            padding: 12px;
            border-radius: 12px;
            margin: 15px 0;
            border: 1px solid #cbd5e1;
            font-family: monospace;
            font-size: 14px;
            word-break: break-all;
        }
        .question-area {
            background: #f8fafc;
            border-radius: 28px;
            padding: 24px;
            margin: 20px 0;
        }
        .question-text {
            font-size: 1.3rem;
            font-weight: 600;
            margin-bottom: 20px;
        }
        .options-list {
            display: flex;
            flex-direction: column;
            gap: 12px;
        }
        .option-item {
            background: white;
            border: 2px solid #e2e8f0;
            border-radius: 60px;
            padding: 14px 20px;
            cursor: pointer;
            transition: 0.2s;
            display: flex;
            align-items: center;
            gap: 12px;
        }
        .option-item:hover {
            border-color: #1e6f5c;
            background: #f0fdf4;
        }
        .option-item.selected {
            background: #1e6f5c;
            color: white;
            border-color: #1e6f5c;
        }
        .option-prefix {
            font-weight: bold;
            width: 30px;
        }
        .nav-buttons {
            display: flex;
            justify-content: space-between;
            margin-top: 24px;
            gap: 12px;
        }
        .progress-bar {
            background: #e2e8f0;
            border-radius: 30px;
            height: 10px;
            margin: 20px 0;
            overflow: hidden;
        }
        .progress-fill {
            background: #1e6f5c;
            height: 100%;
            transition: width 0.3s;
        }
        .score-board {
            background: #fef3c7;
            border-radius: 28px;
            padding: 16px;
            margin-bottom: 20px;
            display: flex;
            justify-content: space-between;
        }
        .final-result {
            text-align: center;
            padding: 20px;
            animation: fadeIn 0.5s ease;
        }
        @keyframes fadeIn {
            from { opacity: 0; transform: scale(0.9); }
            to { opacity: 1; transform: scale(1); }
        }
        .info-note {
            background: #e6f7ff;
            padding: 12px;
            border-radius: 20px;
            margin-top: 20px;
            font-size: 13px;
            text-align: center;
        }
        .admin-only {
            display: block;
        }
        .student-only {
            display: none;
        }
        body.student-mode .admin-only {
            display: none;
        }
        body.student-mode .student-only {
            display: block;
        }
        body.admin-mode .student-only {
            display: none;
        }
        .question-item {
            background: #f8fafc;
            padding: 15px;
            border-radius: 16px;
            margin-bottom: 15px;
            border: 1px solid #e2e8f0;
        }
        .question-actions {
            display: flex;
            gap: 10px;
            margin-top: 10px;
        }
        .edit-btn {
            background: #2c7da0;
            padding: 6px 12px;
            font-size: 0.8rem;
        }
        .delete-btn {
            background: #b45353;
            padding: 6px 12px;
            font-size: 0.8rem;
        }
        .add-question-btn {
            background: #1e6f5c;
            margin-top: 20px;
            width: 100%;
            justify-content: center;
        }
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.5);
            justify-content: center;
            align-items: center;
            z-index: 1000;
        }
        .modal-content {
            background: white;
            padding: 30px;
            border-radius: 32px;
            max-width: 500px;
            width: 90%;
            max-height: 90vh;
            overflow-y: auto;
        }
        .modal-content h3 {
            margin-bottom: 20px;
        }
        .close-modal {
            float: right;
            cursor: pointer;
            font-size: 24px;
        }
        .update-time {
            font-size: 11px;
            color: #666;
            margin-top: 8px;
            text-align: right;
        }
        .admin-info-box {
            background: #f0fdf4;
            padding: 15px;
            border-radius: 16px;
            margin-top: 20px;
            border: 1px solid #bbf7d0;
        }
        .hint {
            background: #f1f5f9;
            border-left: 3px solid #1e6f5c;
            padding: 10px 15px;
            margin-top: 15px;
            border-radius: 12px;
            font-size: 13px;
            cursor: pointer;
        }
        .hint-text {
            display: none;
            margin-top: 8px;
            color: #1e6f5c;
        }
        .hint-text.show {
            display: block;
        }
        .result-medal {
            font-size: 64px;
            margin-bottom: 10px;
        }
        .loading {
            text-align: center;
            padding: 40px;
            font-size: 18px;
            color: #1e6f5c;
        }
        .certificate-btn {
            background: #d4af37;
            color: #1a2a3f;
            margin-top: 15px;
        }
        .optional-note {
            font-size: 11px;
            color: #64748b;
            margin: -4px 0 8px 0;
            padding-left: 10px;
        }
        .other-school-input {
            display: none;
            margin-top: 8px;
        }
        .other-school-input.visible {
            display: block;
        }
    </style>
    <script src="https://cdn.jsdelivr.net/npm/qrcodejs@1.0.0/qrcode.min.js"></script>
</head>
<body id="appBody">
<div class="container">
    <div class="header">
        <div style="display: flex; align-items: center; gap: 15px;">
            <div style="font-size: 42px;">🛡️</div>
            <h1 id="pageTitle">КиберБезопасность СПО</h1>
        </div>
        <div class="mode-switch" id="modeSwitch">
            <button id="adminModeBtn" class="mode-btn active">👑 Админ</button>
            <button id="userModeBtn" class="mode-btn">👤 Пользователь</button>
        </div>
    </div>

    <!-- АДМИНСКАЯ ПАНЕЛЬ -->
    <div class="admin-only">
        <div class="grid-2">
            <div class="card">
                <h3>📱 QR-код для пользователей</h3>
                <div class="qr-box">
                    <label>Выберите курс:</label>
                    <select id="courseForQR">
                        <option value="1 курс">📘 1 курс</option>
                        <option value="2 курс">📙 2 курс</option>
                    </select>
                    <button id="generateQRBtn">🔄 Создать QR-код</button>
                    <div id="qrcode"><div style="padding:20px;">Нажмите "Создать QR-код"</div></div>
                    <div id="qrLinkArea" class="link-info"></div>
                </div>
                
                <div class="admin-info-box">
                    <strong>🔐 Администратор</strong><br>
                    <div id="adminUrlDisplay" class="link-url"></div>
                    <button id="copyAdminUrlBtn" class="copy-btn">📋 Копировать админ-ссылку</button>
                </div>
                
                <hr style="margin: 24px 0;">
                <button id="clearStatsBtn" class="danger-btn">🗑️ Очистить историю</button>
                <button id="clearAllQuestionsBtn" class="danger-btn" style="margin-top:10px;">🗑️ Сбросить вопросы по умолчанию</button>
            </div>

            <div class="card">
                <div class="tab-buttons">
                    <button class="tab-btn active" data-tab="results">📊 Завершённые</button>
                    <button class="tab-btn" data-tab="live">🟢 LIVE-сессии</button>
                    <button class="tab-btn" data-tab="questions">📝 Управление вопросами</button>
                </div>
                
                <div id="resultsTab" class="tab-content active">
                    <div style="display: flex; justify-content: space-between;">
                        <h3>Результаты пользователей</h3>
                        <span id="resultsCount" style="background:#e2e8f0; padding: 4px 12px; border-radius: 30px;">0</span>
                    </div>
                    <div style="overflow-x: auto; max-height: 450px; overflow-y: auto;">
                        <table class="stats-table">
                            <thead><tr><th>Пользователь</th><th>Школа</th><th>Телефон</th><th>Баллы</th><th>%</th><th>Сертификат</th><th>Дата</th></tr></thead>
                            <tbody id="statsTableBody"><tr><td colspan="7">📭 Нет данных</td></tr></tbody>
                        </table>
                    </div>
                </div>
                
                <div id="liveTab" class="tab-content">
                    <h3>Активные сессии <span class="live-badge">● реальное время</span></h3>
                    <div id="liveSessionsList" class="live-sessions"><div style="padding:40px;">🟢 Нет активных сессий</div></div>
                    <div class="update-time" id="lastUpdateTime">Обновлено: только что</div>
                </div>
                
                <div id="questionsTab" class="tab-content">
                    <h3>Управление вопросами</h3>
                    <div id="questionsList"></div>
                    <button id="addQuestionBtn" class="add-question-btn">➕ Добавить вопрос</button>
                </div>
            </div>
        </div>
    </div>

    <!-- ПОЛЬЗОВАТЕЛЬСКАЯ ПАНЕЛЬ -->
    <div class="student-only">
        <div class="card" style="max-width: 800px; margin: 0 auto;">
            <h2>🛡️ Кибербезопасность: проверь свои знания!</h2>
            <div id="studentLoading" class="loading">📚 Загрузка вопросов...</div>
            
            <div id="regBlock" style="display: none;">
                <label>👤 Введите ФИО:</label>
                <input type="text" id="studentNameInput" placeholder="Иванов Иван Иванович">
                <label>🏫 Название школы:</label>
                <select id="schoolNameSelect">
                    <option value="">— Выберите школу —</option>
                    <option value="МБОУ СОШ №1">МБОУ СОШ №1</option>
                    <option value="МБОУ СОШ №2">МБОУ СОШ №2</option>
                    <option value="МБОУ СОШ №3">МБОУ СОШ №3</option>
                    <option value="МБОУ СОШ №4">МБОУ СОШ №4</option>
                    <option value="МБОУ СОШ №5">МБОУ СОШ №5</option>
                    <option value="МБОУ СОШ №7">МБОУ СОШ №7</option>
                    <option value="МБОУ СОШ №8">МБОУ СОШ №8</option>
                    <option value="МБОУ СОШ №14">МБОУ СОШ №14</option>
                    <option value="МБОУ СОШ №16">МБОУ СОШ №16</option>
                    <option value="МБОУ СОШ №20">МБОУ СОШ №20</option>
                    <option value="МБОУ СОШ №24">МБОУ СОШ №24</option>
                    <option value="МБОУ СОШ №25">МБОУ СОШ №25</option>
                    <option value="МБОУ СОШ №27">МБОУ СОШ №27</option>
                    <option value="МБОУ СОШ №28">МБОУ СОШ №28</option>
                    <option value="МБОУ СОШ №31">МБОУ СОШ №31</option>
                    <option value="МБОУ СОШ №33">МБОУ СОШ №33</option>
                    <option value="МБОУ СОШ №40">МБОУ СОШ №40</option>
                    <option value="МБОУ СОШ №43">МБОУ СОШ №43</option>
                    <option value="__other__">📝 Другая школа (ввести вручную)</option>
                </select>
                <input type="text" id="schoolNameInput" class="other-school-input" placeholder="Введите название школы вручную">
                <label>📞 Номер телефона:</label>
                <input type="tel" id="phoneInput" placeholder="+7 (___) ___-__-__" inputmode="numeric" maxlength="20">
                <div class="optional-note">Поле не является обязательным для ввода</div>
                <button id="startQuizBtn">▶ Начать викторину</button>
            </div>
            
            <div id="quizContent" style="display: none;">
                <div class="score-board">
                    <span>⭐ Счёт: <strong id="currentScore">0</strong> / <span id="totalQuestions">0</span></span>
                    <span>📊 Прогресс: <span id="progressPercent">0</span>%</span>
                </div>
                <div class="progress-bar"><div class="progress-fill" id="progressFill"></div></div>
                <div id="questionContainer"></div>
                <div class="nav-buttons">
                    <button id="prevBtn" disabled>◀ Назад</button>
                    <button id="nextBtn">Далее ▶</button>
                    <button id="submitBtn" style="background:#059669;">✅ Завершить</button>
                </div>
                <div id="hintContainer"></div>
            </div>
            <div id="finalResult" style="display: none;"></div>
        </div>
    </div>
    
    <footer><span id="footerText">КиберБезопасность СПО</span></footer>
</div>

<!-- Модальное окно для редактирования вопроса -->
<div id="questionModal" class="modal">
    <div class="modal-content">
        <span class="close-modal" onclick="closeModal()">&times;</span>
        <h3 id="modalTitle">Добавить вопрос</h3>
        <input type="text" id="questionText" placeholder="Текст вопроса">
        <input type="text" id="option0" placeholder="Вариант ответа 1">
        <input type="text" id="option1" placeholder="Вариант ответа 2">
        <input type="text" id="option2" placeholder="Вариант ответа 3">
        <input type="text" id="option3" placeholder="Вариант ответа 4">
        <select id="correctAnswer">
            <option value="0">Правильный ответ: 1</option>
            <option value="1">Правильный ответ: 2</option>
            <option value="2">Правильный ответ: 3</option>
            <option value="3">Правильный ответ: 4</option>
        </select>
        <textarea id="questionHint" rows="2" placeholder="Подсказка (необязательно)"></textarea>
        <button id="saveQuestionBtn" style="margin-top: 15px;">💾 Сохранить</button>
    </div>
</div>

<script>
    // ========== 15 ВОПРОСОВ ПО УМОЛЧАНИЮ ==========
    const DEFAULT_QUESTIONS = [
        { text: "Какой пароль считается наиболее надёжным?", options: ["qwerty123", "MyCatName2020", "F#7x!pL$9qRz", "password"], correct: 2, hint: "Надёжный пароль содержит не менее 12 символов, включая заглавные и строчные буквы, цифры и спецсимволы." },
        { text: "Что такое фишинг?", options: ["Вид антивируса", "Мошенническая попытка получить личные данные", "Сетевой протокол", "Шифрование"], correct: 1, hint: "Фишеры часто маскируются под банки, соцсети или госуслуги." },
        { text: "Что лучше всего защищает аккаунт?", options: ["Сложный пароль + 2FA", "Один пароль везде", "Записывать пароль в блокнот", "Пароль 'admin'"], correct: 0, hint: "Двухфакторная аутентификация (2FA) — это второй уровень защиты." },
        { text: "Как безопасно пользоваться публичным Wi-Fi?", options: ["Передавать данные карт", "Включить VPN и не вводить пароли", "Отключить брандмауэр", "Скачивать любые файлы"], correct: 1, hint: "VPN шифрует ваш трафик, делая его нечитаемым для злоумышленников." },
        { text: "Вам пришло SMS: 'Ваш аккаунт взломан, перейдите по ссылке'", options: ["Перейти по ссылке", "Проверить через официальный сайт", "Отправить пароль другу", "Ответить на SMS"], correct: 1, hint: "Никогда не переходите по ссылкам из подозрительных сообщений." },
        { text: "Что обозначает HTTPS?", options: ["Шифрование данных", "Опасный сайт", "Сайт госуслуг", "Сайт заблокирован"], correct: 0, hint: "Буква 'S' означает Secure — защищённое соединение." },
        { text: "Какое действие ведёт к заражению вирусом?", options: ["Установка из офиц. магазина", "Открытие подозрительного вложения", "Использование антивируса", "Обновление ОС"], correct: 1, hint: "Вложения от незнакомцев могут содержать вредоносный код." },
        { text: "Что делать при кибербуллинге?", options: ["Оскорбить в ответ", "Сохранить скрины, заблокировать и сообщить", "Ничего", "Удалить аккаунт"], correct: 1, hint: "Сохраните доказательства — скриншоты помогут при обращении в полицию." },
        { text: "Что такое VPN?", options: ["Вредоносная программа", "Технология шифрования трафика", "Антивирус", "Браузер"], correct: 1, hint: "VPN создаёт защищённый туннель между вами и интернетом." },
        { text: "Как часто нужно обновлять пароли?", options: ["Никогда", "Раз в год", "При подозрении на утечку", "Каждый день"], correct: 2, hint: "Регулярная смена паролей снижает риск взлома." },
        { text: "Что такое социальная инженерия?", options: ["Программирование", "Психологическое манипулирование", "Сетевой протокол", "Шифрование"], correct: 1, hint: "Злоумышленники используют доверие и спешку, чтобы выманить данные." },
        { text: "Что делать, если вы стали жертвой мошенников?", options: ["Ничего", "Сразу сообщить в банк и полицию", "Ответить мошенникам", "Удалить все сообщения"], correct: 1, hint: "Чем быстрее вы сообщите, тем выше шанс вернуть средства." },
        { text: "Какое ПО обязательно должно быть на компьютере?", options: ["Антивирус", "Торрент-клиент", "Взломщик паролей", "Кейген"], correct: 0, hint: "Антивирус защищает от известных и новых угроз." },
        { text: "Что такое бэкап?", options: ["Вид вируса", "Резервное копирование данных", "Антивирусная программа", "Сетевой протокол"], correct: 1, hint: "Регулярное создание копий важных файлов спасёт при атаке шифровальщика." },
        { text: "Какое расширение у безопасного сайта?", options: ["http://", "https://", "ftp://", "file://"], correct: 1, hint: "Ищите значок замка в адресной строке браузера." }
    ];

    // ========== ГЛОБАЛЬНЫЕ ПЕРЕМЕННЫЕ ==========
    let QUESTIONS = [];
    let completedResults = [];
    let activeSessions = {};
    let currentEditIndex = -1;
    let studentTimers = {};
    let syncInterval = null;

    // ========== API ==========
    const API_URL = 'save_data.php';
    const QUESTIONS_API = 'save_questions.php';

    // ========== ОГРАНИЧЕНИЕ ВВОДА ТОЛЬКО ЦИФР В ТЕЛЕФОНЕ ==========
    function setupPhoneInput() {
        const phoneInput = document.getElementById('phoneInput');
        if (!phoneInput) return;
        
        phoneInput.addEventListener('beforeinput', function(e) {
            const allowed = /[0-9+\-() ]/;
            if (e.data && !allowed.test(e.data)) {
                e.preventDefault();
            }
        });
        
        phoneInput.addEventListener('input', function(e) {
            const original = this.value;
            const cleaned = original.replace(/[^0-9+\-() ]/g, '');
            if (original !== cleaned) {
                this.value = cleaned;
            }
        });
        
        phoneInput.addEventListener('paste', function(e) {
            e.preventDefault();
            const pasted = (e.clipboardData || window.clipboardData).getData('text');
            const cleaned = pasted.replace(/[^0-9+\-() ]/g, '');
            document.execCommand('insertText', false, cleaned);
        });
        
        phoneInput.addEventListener('keydown', function(e) {
            const allowedKeys = ['Backspace', 'Delete', 'Tab', 'Escape', 'Enter', 'ArrowLeft', 'ArrowRight', 'Home', 'End'];
            if (allowedKeys.includes(e.key)) return;
            
            const allowedChars = /[0-9+\-() ]/;
            if (!allowedChars.test(e.key) && !e.ctrlKey && !e.metaKey) {
                e.preventDefault();
            }
        });
    }

    // ========== ВЫБОР ШКОЛЫ (ВЫПАДАЮЩИЙ СПИСОК + РУЧНОЙ ВВОД) ==========
    function setupSchoolSelect() {
        const schoolSelect = document.getElementById('schoolNameSelect');
        const otherInput = document.getElementById('schoolNameInput');
        if (!schoolSelect || !otherInput) return;
        
        schoolSelect.addEventListener('change', function() {
            if (this.value === '__other__') {
                otherInput.classList.add('visible');
                otherInput.focus();
            } else {
                otherInput.classList.remove('visible');
                otherInput.value = '';
            }
        });
    }

    function getSchoolValue() {
        const schoolSelect = document.getElementById('schoolNameSelect');
        const otherInput = document.getElementById('schoolNameInput');
        if (!schoolSelect) return '';
        
        if (schoolSelect.value === '__other__') {
            return otherInput.value.trim();
        }
        return schoolSelect.value.trim();
    }

    // ========== ЗАГРУЗКА ВОПРОСОВ ==========
    async function loadQuestions() {
        try {
            const response = await fetch(QUESTIONS_API);
            if (response.ok) {
                const data = await response.json();
                if (data.status === 'success' && data.questions && data.questions.length > 0) {
                    QUESTIONS = data.questions;
                } else {
                    QUESTIONS = [...DEFAULT_QUESTIONS];
                    await saveQuestions();
                }
                renderQuestionsList();
                const totalSpan = document.getElementById('totalQuestions');
                if(totalSpan) totalSpan.innerText = QUESTIONS.length;
                return true;
            }
        } catch(e) {
            console.error('Load questions error:', e);
        }
        QUESTIONS = [...DEFAULT_QUESTIONS];
        renderQuestionsList();
        const totalSpan = document.getElementById('totalQuestions');
        if(totalSpan) totalSpan.innerText = QUESTIONS.length;
        return true;
    }

    async function saveQuestions() {
        try {
            await fetch(QUESTIONS_API, {
                method: 'POST',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify({ questions: QUESTIONS })
            });
        } catch(e) { console.error('Save questions error:', e); }
    }

    function resetToDefaultQuestions() {
        if(confirm('Сбросить все вопросы к настройкам по умолчанию?')) {
            QUESTIONS = JSON.parse(JSON.stringify(DEFAULT_QUESTIONS));
            saveQuestions();
            renderQuestionsList();
            const totalSpan = document.getElementById('totalQuestions');
            if(totalSpan) totalSpan.innerText = QUESTIONS.length;
            alert('Вопросы сброшены к настройкам по умолчанию!');
        }
    }

    function renderQuestionsList() {
        const container = document.getElementById('questionsList');
        if(!container) return;
        if(!QUESTIONS.length) {
            container.innerHTML = '<div style="padding:20px; text-align:center;">📭 Нет вопросов. Добавьте первый!</div>';
            return;
        }
        container.innerHTML = QUESTIONS.map((q, idx) => `
            <div class="question-item">
                <strong>${idx+1}. ${escapeHtml(q.text)}</strong>
                <div style="font-size:13px; color:#666; margin-top:5px;">
                    ${q.options.map((opt, i) => `${String.fromCharCode(65+i)}. ${escapeHtml(opt)}`).join(' | ')}
                    ${q.hint ? `<br>💡 Подсказка: ${escapeHtml(q.hint)}` : ''}
                </div>
                <div class="question-actions">
                    <button class="edit-btn" onclick="editQuestion(${idx})">✏️ Редактировать</button>
                    <button class="delete-btn" onclick="deleteQuestion(${idx})">🗑️ Удалить</button>
                </div>
            </div>
        `).join('');
    }

    function editQuestion(index) {
        currentEditIndex = index;
        const q = QUESTIONS[index];
        document.getElementById('modalTitle').innerText = 'Редактировать вопрос';
        document.getElementById('questionText').value = q.text;
        document.getElementById('option0').value = q.options[0] || '';
        document.getElementById('option1').value = q.options[1] || '';
        document.getElementById('option2').value = q.options[2] || '';
        document.getElementById('option3').value = q.options[3] || '';
        document.getElementById('correctAnswer').value = q.correct;
        document.getElementById('questionHint').value = q.hint || '';
        document.getElementById('questionModal').style.display = 'flex';
    }

    function deleteQuestion(index) {
        if(confirm('Удалить этот вопрос?')) {
            QUESTIONS.splice(index, 1);
            saveQuestions();
            renderQuestionsList();
            const totalSpan = document.getElementById('totalQuestions');
            if(totalSpan) totalSpan.innerText = QUESTIONS.length;
        }
    }

    function openAddQuestionModal() {
        currentEditIndex = -1;
        document.getElementById('modalTitle').innerText = 'Добавить вопрос';
        document.getElementById('questionText').value = '';
        document.getElementById('option0').value = '';
        document.getElementById('option1').value = '';
        document.getElementById('option2').value = '';
        document.getElementById('option3').value = '';
        document.getElementById('correctAnswer').value = '0';
        document.getElementById('questionHint').value = '';
        document.getElementById('questionModal').style.display = 'flex';
    }

    function closeModal() {
        document.getElementById('questionModal').style.display = 'none';
    }

    async function saveCurrentQuestion() {
        const newQuestion = {
            text: document.getElementById('questionText').value,
            options: [
                document.getElementById('option0').value,
                document.getElementById('option1').value,
                document.getElementById('option2').value,
                document.getElementById('option3').value
            ],
            correct: parseInt(document.getElementById('correctAnswer').value),
            hint: document.getElementById('questionHint').value
        };
        
        if(!newQuestion.text || newQuestion.options.some(o => !o)) {
            alert('Заполните все поля!');
            return;
        }
        
        if(currentEditIndex >= 0) {
            QUESTIONS[currentEditIndex] = newQuestion;
        } else {
            QUESTIONS.push(newQuestion);
        }
        
        await saveQuestions();
        renderQuestionsList();
        closeModal();
        
        const totalSpan = document.getElementById('totalQuestions');
        if(totalSpan) totalSpan.innerText = QUESTIONS.length;
    }

    // ========== СОХРАНЕНИЕ РЕЗУЛЬТАТОВ В ОДИН ФАЙЛ ==========
    async function saveStudentResultToFile(studentName, schoolName, phone, score, total, percent, answers) {
        const resultData = {
            studentName: studentName,
            schoolName: schoolName,
            phone: phone || '',
            score: score,
            total: total,
            percent: percent,
            date: new Date().toLocaleString(),
            answers: answers.map((ans, idx) => ({
                question: QUESTIONS[idx]?.text || 'Вопрос',
                selectedAnswer: ans !== null ? QUESTIONS[idx]?.options[ans] : 'Не отвечен',
                correctAnswer: QUESTIONS[idx]?.options[QUESTIONS[idx]?.correct] || 'Неизвестно',
                isCorrect: ans !== null && ans === QUESTIONS[idx]?.correct
            }))
        };
        
        try {
            await fetch('save_result.php', {
                method: 'POST',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify({ data: resultData })
            });
        } catch(e) { console.error('Save result error:', e); }
    }

    // ========== СИНХРОНИЗАЦИЯ С СЕРВЕРОМ ==========
    async function saveToServer() {
        try {
            await fetch(API_URL, {
                method: 'POST',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify({ activeSessions: activeSessions, completedResults: completedResults })
            });
        } catch(e) {}
    }

    async function loadFromServer() {
        try {
            const response = await fetch(API_URL);
            if (response.ok) {
                const data = await response.json();
                if (data.status === 'success') {
                    if (data.activeSessions) activeSessions = data.activeSessions;
                    if (data.completedResults) completedResults = data.completedResults;
                    renderLiveSessions();
                    renderCompletedTable();
                }
            }
        } catch(e) {}
    }

    function renderCompletedTable() {
        const tbody = document.getElementById('statsTableBody');
        if(!tbody) return;
        if(!completedResults.length) {
            tbody.innerHTML = '<tr><td colspan="7">📭 Нет данных</td></tr>';
            document.getElementById('resultsCount').innerText = '0';
            return;
        }
        document.getElementById('resultsCount').innerText = completedResults.length;
        tbody.innerHTML = completedResults.map((r, idx) => `
            <tr>
                <td>👤 ${escapeHtml(r.studentName)}</td>
                <td>🏫 ${escapeHtml(r.schoolName || '—')}</td>
                <td>📞 ${escapeHtml(r.phone || '—')}</td>
                <td><strong>${r.score}/${r.total}</strong></td>
                <td style="color: ${r.percent >= 70 ? '#15803d' : '#b45309'};">${r.percent}%</td>
                <td><button class="copy-btn" onclick="downloadCertificate('${escapeHtml(r.studentName)}', ${r.score}, ${r.total}, ${r.percent}, '${escapeHtml(r.schoolName || '')}')">📜 Сертификат</button></td>
                <td style="font-size:0.8rem;">${escapeHtml(r.date)}</td>
            </tr>
        `).join('');
    }

    function clearAllHistory() {
        if(confirm('Очистить всю историю?')) {
            completedResults = [];
            renderCompletedTable();
            saveToServer();
        }
    }

    // ========== УПРАВЛЕНИЕ СЕССИЯМИ ==========
    function createSession(sessionId, studentName, schoolName, phone) {
        studentTimers[sessionId] = { startTime: Date.now(), currentQuestionStart: Date.now() };
        activeSessions[sessionId] = {
            studentName: studentName, schoolName: schoolName, phone: phone || '', currentQuestion: 0,
            answers: new Array(QUESTIONS.length).fill(null),
            startTime: new Date().toLocaleTimeString(), lastUpdate: Date.now()
        };
        renderLiveSessions();
        saveToServer();
    }

    function updateSessionAnswer(sessionId, qIndex, aIndex) {
        if(activeSessions[sessionId]) {
            if(studentTimers[sessionId]) studentTimers[sessionId].currentQuestionStart = Date.now();
            activeSessions[sessionId].answers[qIndex] = aIndex;
            activeSessions[sessionId].currentQuestion = qIndex;
            activeSessions[sessionId].lastUpdate = Date.now();
            renderLiveSessions();
            saveToServer();
        }
    }

    function completeSession(sessionId, studentName, schoolName, phone, score, total, percent, answers) {
        if(activeSessions[sessionId]) delete activeSessions[sessionId];
        completedResults.unshift({ studentName, schoolName, phone, score, total, percent, date: new Date().toLocaleString(), timestamp: Date.now() });
        renderLiveSessions();
        renderCompletedTable();
        saveToServer();
        saveStudentResultToFile(studentName, schoolName, phone, score, total, percent, answers);
        delete studentTimers[sessionId];
    }

    function renderLiveSessions() {
        const container = document.getElementById('liveSessionsList');
        if(!container) return;
        const sessions = Object.keys(activeSessions);
        if(sessions.length === 0) {
            container.innerHTML = '<div style="padding:40px;">🟢 Нет активных сессий</div>';
            return;
        }
        
        container.innerHTML = sessions.map(sid => {
            const s = activeSessions[sid];
            let score = 0;
            for(let i=0; i<s.answers.length; i++) if(s.answers[i] !== null && s.answers[i] === QUESTIONS[i]?.correct) score++;
            const currentTimer = studentTimers[sid] ? Math.floor((Date.now() - studentTimers[sid].currentQuestionStart) / 1000) : 0;
            
            const answersHtml = s.answers.map((ans, idx) => {
                const isCorrect = ans !== null && ans === QUESTIONS[idx]?.correct;
                if(ans !== null) {
                    return `<div style="margin-bottom:5px; padding:5px; background: ${isCorrect ? '#d1fae5' : '#fee2e2'}; border-radius:8px;">
                                <strong>${idx+1}.</strong> ${escapeHtml(QUESTIONS[idx]?.options[ans] || '-')} ${isCorrect ? '✓' : '✗'}
                            </div>`;
                }
                return `<div style="margin-bottom:5px; padding:5px; background:#f1f5f9; border-radius:8px;">
                            <strong>${idx+1}.</strong> ⏳ Не отвечен
                        </div>`;
            }).join('');
            
            return `<div class="session-card session-active">
                <div>👤 <strong>${escapeHtml(s.studentName)}</strong> | 🏫 ${escapeHtml(s.schoolName || 'Школа не указана')} ${s.phone ? '| 📞 ' + escapeHtml(s.phone) : ''}</div>
                <div>📊 Счёт: ${score}/${QUESTIONS.length} (${Math.round(score/QUESTIONS.length*100)}%)</div>
                <div>❓ Вопрос ${s.currentQuestion+1}: "${QUESTIONS[s.currentQuestion]?.text.substring(0,50) || '...'}"</div>
                <div>⏱️ Таймер: ${currentTimer} сек</div>
                <div class="answers-grid">${answersHtml}</div>
            </div>`;
        }).join('');
        
        const timeSpan = document.getElementById('lastUpdateTime');
        if(timeSpan) timeSpan.innerHTML = 'Обновлено: ' + new Date().toLocaleTimeString();
    }

    function escapeHtml(str) { if(!str) return ''; return str.replace(/[&<>]/g, m => ({'&':'&amp;','<':'&lt;','>':'&gt;'}[m])); }

    function getBaseCleanUrl() { return window.location.href.split('?')[0].split('#')[0]; }
    function getStudentUrl(course) { return `${getBaseCleanUrl()}?mode=student&course=${course === '1 курс' ? '1' : '2'}`; }
    function getAdminUrl() { return `${getBaseCleanUrl()}?mode=admin`; }

    function generateRealQRCode(url, containerId) {
        const container = document.getElementById(containerId);
        if(!container) return;
        container.innerHTML = '';
        const qrDiv = document.createElement('div');
        container.appendChild(qrDiv);
        if(typeof QRCode !== 'undefined') new QRCode(qrDiv, { text: url, width: 200, height: 200, colorDark: "#000000", colorLight: "#ffffff", correctLevel: QRCode.CorrectLevel.H });
        else setTimeout(() => generateRealQRCode(url, containerId), 300);
    }

    function refreshQRAndLink() {
        const course = document.getElementById('courseForQR').value;
        const studentUrl = getStudentUrl(course);
        generateRealQRCode(studentUrl, 'qrcode');
        document.getElementById('qrLinkArea').innerHTML = `🔗 <a href="${studentUrl}" target="_blank">${studentUrl}</a>`;
        document.getElementById('adminUrlDisplay').innerHTML = getAdminUrl();
    }

    // Скачивание сертификата
    function downloadCertificate(name, score, total, percent, schoolName) {
        const medalText = percent >= 90 ? 'ЗОЛОТО' : (percent >= 70 ? 'СЕРЕБРО' : (percent >= 50 ? 'БРОНЗА' : 'УЧАСТНИК'));
        const schoolDisplay = schoolName ? `<p style="font-size:16px; margin:5px 0;">Школа: <strong>${escapeHtml(schoolName)}</strong></p>` : '';
        const certHtml = `
            <!DOCTYPE html>
            <html>
            <head><meta charset="UTF-8"><title>Сертификат - ${name}</title></head>
            <body style="display:flex; justify-content:center; align-items:center; min-height:100vh; background:#e2e8f0; margin:0; padding:20px;">
                <div id="certificate" style="width:800px; padding:40px; background:linear-gradient(135deg,#fff8e7,#fff0d4); text-align:center; border:15px double #d4af37; border-radius:20px;">
                    <div style="font-size:64px;">🛡️</div>
                    <h2 style="color:#1e6f5c; margin:20px 0;">СЕРТИФИКАТ</h2>
                    <p>Настоящим подтверждается, что</p>
                    <h3 style="font-size:32px; margin:20px 0; color:#b45353;">${escapeHtml(name)}</h3>
                    ${schoolDisplay}
                    <p>успешно прошёл(ла) викторину<br><strong>«Кибербезопасность»</strong></p>
                    <div style="margin:20px 0; font-size:24px; font-weight:bold;">Результат: ${score} из ${total} (${percent}%)</div>
                    <div style="margin:20px 0;">🏆 ${medalText}</div>
                    <p style="margin-top:30px; font-size:12px;">Дата: ${new Date().toLocaleDateString()}</p>
                    <hr style="margin:20px 0;">
                    <p style="font-size:12px;">КиберБезопасность СПО</p>
                </div>
                <script>window.onload = function() { setTimeout(function() { window.print(); }, 500); }<\/script>
            </body>
            </html>
        `;
        const win = window.open('', '_blank');
        win.document.write(certHtml);
        win.document.close();
    }

    // ========== ПОЛЬЗОВАТЕЛЬСКАЯ ЛОГИКА ==========
    let studentSessionId = null, studentAnswers = null, studentCurrentIndex = 0, studentNameValue = '', studentSchoolValue = '', studentPhoneValue = '';

    async function setupStudentQuiz() {
        const loadingDiv = document.getElementById('studentLoading');
        const regBlock = document.getElementById('regBlock');
        
        await loadQuestions();
        
        if (QUESTIONS.length > 0) {
            loadingDiv.style.display = 'none';
            regBlock.style.display = 'block';
            
            setupPhoneInput();
            setupSchoolSelect();
            
            document.getElementById('totalQuestions').innerText = QUESTIONS.length;
            studentAnswers = new Array(QUESTIONS.length).fill(null);
            studentSessionId = 'session_' + Date.now() + '_' + Math.random();
            
            document.getElementById('startQuizBtn').onclick = () => {
                const nameInput = document.getElementById('studentNameInput').value.trim();
                const schoolValue = getSchoolValue();
                const phoneInput = document.getElementById('phoneInput').value.trim();
                if(!nameInput) { alert('Введите ваше ФИО!'); return; }
                if(!schoolValue) { alert('Выберите или введите название школы!'); return; }
                studentNameValue = nameInput;
                studentSchoolValue = schoolValue;
                studentPhoneValue = phoneInput;
                createSession(studentSessionId, studentNameValue, studentSchoolValue, studentPhoneValue);
                regBlock.style.display = 'none';
                document.getElementById('quizContent').style.display = 'block';
                updateStudentUI();
            };
            
            document.getElementById('prevBtn').onclick = () => { if(studentCurrentIndex > 0) { studentCurrentIndex--; updateStudentUI(); } };
            document.getElementById('nextBtn').onclick = () => { if(studentCurrentIndex < QUESTIONS.length - 1) { studentCurrentIndex++; updateStudentUI(); } };
            document.getElementById('submitBtn').onclick = () => {
                let score = 0;
                for(let i=0; i<studentAnswers.length; i++) if(studentAnswers[i] !== null && studentAnswers[i] === QUESTIONS[i].correct) score++;
                const percent = Math.round(score/QUESTIONS.length*100);
                completeSession(studentSessionId, studentNameValue, studentSchoolValue, studentPhoneValue, score, QUESTIONS.length, percent, studentAnswers);
                document.getElementById('quizContent').style.display = 'none';
                const medal = percent >= 90 ? '🏆 ЗОЛОТО!' : (percent >= 70 ? '🥈 СЕРЕБРО!' : (percent >= 50 ? '🥉 БРОНЗА!' : '📚 Учись дальше!'));
                document.getElementById('finalResult').innerHTML = `
                    <div class="final-result">
                        <div class="result-medal">${percent >= 90 ? '🏆' : (percent >= 70 ? '🥈' : (percent >= 50 ? '🥉' : '📚'))}</div>
                        <h3>Результат: ${score} из ${QUESTIONS.length} (${percent}%)</h3>
                        <p style="font-size:18px; margin:10px 0;">${medal}</p>
                        <p>${percent >= 70 ? '🎉 Отлично!' : '📖 Рекомендуем повторить'}</p>
                        <button onclick="downloadCertificate('${escapeHtml(studentNameValue)}', ${score}, ${QUESTIONS.length}, ${percent}, '${escapeHtml(studentSchoolValue)}')" class="certificate-btn" style="margin:5px;">📜 Скачать сертификат</button>
                        <button onclick="location.reload()" style="margin:5px;">🔄 Заново</button>
                    </div>
                `;
                document.getElementById('finalResult').style.display = 'block';
            };
        } else {
            loadingDiv.innerHTML = '❌ Ошибка загрузки вопросов. Обновите страницу.';
        }
    }

    function updateStudentUI() {
        if(!QUESTIONS.length) return;
        
        let score = 0;
        for(let i=0; i<studentAnswers.length; i++) if(studentAnswers[i] !== null && studentAnswers[i] === QUESTIONS[i].correct) score++;
        document.getElementById('currentScore').innerText = score;
        document.getElementById('progressPercent').innerText = Math.round(score/QUESTIONS.length*100);
        document.getElementById('progressFill').style.width = ((studentCurrentIndex + 1) / QUESTIONS.length) * 100 + '%';
        
        const q = QUESTIONS[studentCurrentIndex];
        if(!q) return;
        
        const container = document.getElementById('questionContainer');
        container.innerHTML = `<div class="question-area">
            <div class="question-text">
                <span style="background: #1e6f5c; color: white; padding: 4px 12px; border-radius: 20px; font-size: 14px; margin-right: 10px;">${studentCurrentIndex+1}/${QUESTIONS.length}</span>
                ${escapeHtml(q.text)}
            </div>
            <div class="options-list" id="optionsList"></div>
        </div>`;
        
        document.getElementById('hintContainer').innerHTML = `<div class="hint" onclick="this.querySelector('.hint-text').classList.toggle('show')">
            💡 Подсказка <span>▼</span>
            <div class="hint-text">${escapeHtml(q.hint || 'Подумайте внимательно!')}</div>
        </div>`;
        
        const optsList = document.getElementById('optionsList');
        q.options.forEach((opt, idx) => {
            const optDiv = document.createElement('div');
            optDiv.className = 'option-item' + (studentAnswers[studentCurrentIndex] === idx ? ' selected' : '');
            optDiv.innerHTML = `<span class="option-prefix">${String.fromCharCode(65+idx)}.</span><span>${escapeHtml(opt)}</span>`;
            optDiv.onclick = () => {
                studentAnswers[studentCurrentIndex] = idx;
                document.querySelectorAll('.option-item').forEach(el => el.classList.remove('selected'));
                optDiv.classList.add('selected');
                updateSessionAnswer(studentSessionId, studentCurrentIndex, idx);
                updateStudentUI();
            };
            optsList.appendChild(optDiv);
        });
        document.getElementById('prevBtn').disabled = studentCurrentIndex === 0;
    }

    // ========== АДМИНСКАЯ ЛОГИКА ==========
    async function initAdmin() {
        await loadQuestions();
        await loadFromServer();
        refreshQRAndLink();
        
        document.getElementById('generateQRBtn').onclick = refreshQRAndLink;
        document.getElementById('courseForQR').onchange = refreshQRAndLink;
        document.getElementById('clearStatsBtn').onclick = clearAllHistory;
        document.getElementById('clearAllQuestionsBtn').onclick = resetToDefaultQuestions;
        document.getElementById('copyAdminUrlBtn').onclick = () => { navigator.clipboard.writeText(getAdminUrl()); alert('Ссылка скопирована!'); };
        document.getElementById('addQuestionBtn').onclick = openAddQuestionModal;
        document.getElementById('saveQuestionBtn').onclick = saveCurrentQuestion;
        
        document.querySelectorAll('.tab-btn').forEach(btn => {
            btn.onclick = () => {
                document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
                document.querySelectorAll('.tab-content').forEach(c => c.classList.remove('active'));
                btn.classList.add('active');
                const tabId = btn.dataset.tab;
                document.getElementById(tabId === 'results' ? 'resultsTab' : (tabId === 'live' ? 'liveTab' : 'questionsTab')).classList.add('active');
            };
        });
        
        if (syncInterval) clearInterval(syncInterval);
        syncInterval = setInterval(loadFromServer, 1500);
    }

    // ========== ЗАПУСК ==========
    const urlParams = new URLSearchParams(window.location.search);
    if(urlParams.get('mode') === 'student') {
        const modeSwitch = document.getElementById('modeSwitch');
        if(modeSwitch) modeSwitch.style.display = 'none';
        
        document.body.classList.add('student-mode');
        document.body.classList.remove('admin-mode');
        setupStudentQuiz();
    } else {
        document.body.classList.add('admin-mode');
        document.body.classList.remove('student-mode');
        initAdmin();
    }
    
    window.editQuestion = editQuestion;
    window.deleteQuestion = deleteQuestion;
    window.closeModal = closeModal;
    window.downloadCertificate = downloadCertificate;
</script>
</body>
</html>
