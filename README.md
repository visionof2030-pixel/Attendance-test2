<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>سجل متابعة الطلاب - فهد الخالدي</title>
<style>
body {
    font-family: "Tajawal", sans-serif;
    margin: 0;
    padding: 0;
    background: #f7f7f7;
}

header {
    background: linear-gradient(135deg, #1a5276, #2a9d8f);
    color: #fff;
    text-align: center;
    padding: 12px 0;
    box-shadow: 0px 4px 6px rgba(0,0,0,0.1);
}

.header-main {
    font-size: 22px;
    font-weight: bold;
    margin-bottom: 5px;
}

.header-sub {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    gap: 20px;
    font-size: 14px;
    margin-top: 5px;
}

.header-sub div {
    padding: 4px 10px;
    background: rgba(255,255,255,0.15);
    border-radius: 4px;
}

.current-date {
    background: rgba(38, 70, 83, 0.8) !important;
    transition: all 0.3s;
}

.date-info {
    font-size: 12px;
    color: #e0f7fa;
    margin-top: 2px;
}

.time-info {
    font-size: 14px;
    font-weight: bold;
    color: #ffffff;
    margin-top: 2px;
}

.class-header {
    background: #2a9d8f;
    color: white;
    padding: 8px;
    margin: 15px 0 5px 0;
    border-radius: 5px;
    text-align: center;
    font-size: 16px;
}

.container {
    width: 95%;
    margin: 10px auto;
    background: white;
    padding: 15px;
    border-radius: 10px;
    box-shadow: 0px 4px 10px rgba(0,0,0,0.1);
}

table {
    width: 100%;
    border-collapse: collapse;
    font-size: 12px;
    margin-bottom: 15px;
}

th, td {
    border: 1px solid #ddd;
    padding: 8px;
    text-align: center;
}

th {
    background: #e9f5f4;
    color: #264653;
    font-size: 11px;
    font-weight: bold;
}

td {
    cursor: pointer;
    user-select: none;
}

button {
    margin: 5px;
    padding: 8px 15px;
    border: none;
    border-radius: 5px;
    background: #1a5276;
    color: white;
    font-weight: bold;
    cursor: pointer;
    transition: all 0.3s;
}

button:hover {
    background: #2a9d8f;
    transform: translateY(-2px);
}

.controls {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    margin-bottom: 15px;
    gap: 10px;
}

.admin-panel {
    display: none;
    margin-top: 15px;
    padding: 15px;
    border: 1px solid #1a5276;
    border-radius: 10px;
    background: #f0f8ff;
}

.star-cell {
    color: #ffd700;
    font-size: 16px;
    cursor: pointer;
}

.present {
    background-color: #e8f5e9;
}

.absent {
    background-color: #ffebee;
}

.status-filter {
    margin: 10px 0;
    text-align: center;
}

.status-filter button {
    background: #ddd;
    color: #333;
}

.status-filter button.active {
    background: #2a9d8f;
    color: white;
}

input[type="password"], input[type="text"], select {
    padding: 8px;
    border: 1px solid #ccc;
    border-radius: 5px;
    font-family: "Tajawal", sans-serif;
}

.class-tabs {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    margin-bottom: 15px;
    gap: 5px;
}

.class-tab {
    padding: 8px 15px;
    background: #e0e0e0;
    border-radius: 5px;
    cursor: pointer;
    transition: all 0.3s;
}

.class-tab.active {
    background: #2a9d8f;
    color: white;
}

.class-tab:hover {
    background: #c0c0c0;
}

.student-count {
    text-align: center;
    margin: 10px 0;
    color: #264653;
    font-weight: bold;
}

.admin-section {
    margin: 15px 0;
    padding: 10px;
    background: #f9f9f9;
    border-radius: 8px;
    border: 1px solid #ddd;
}

.admin-section h4 {
    margin-top: 0;
    color: #1a5276;
    text-align: center;
    border-bottom: 1px solid #ddd;
    padding-bottom: 8px;
}

.admin-row {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin: 10px 0;
    flex-wrap: wrap;
}

.admin-label {
    font-weight: bold;
    color: #264653;
    min-width: 150px;
}

.admin-input {
    flex: 1;
    min-width: 200px;
}

.semester-info {
    display: inline-block;
    padding: 4px 10px;
    background: #e8f5e9;
    border-radius: 4px;
    color: #2a9d8f;
    font-weight: bold;
    margin-left: 10px;
}

.starred-student {
    background-color: #fffde7 !important;
}

.week-checkboxes-container {
    background: white;
    border-radius: 8px;
    padding: 15px;
    margin: 15px 0;
    box-shadow: 0 2px 5px rgba(0,0,0,0.1);
}

.semester-title {
    background: linear-gradient(135deg, #1a5276, #2a9d8f);
    color: white;
    padding: 10px;
    border-radius: 5px;
    margin-bottom: 15px;
    text-align: center;
}

.weeks-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 10px;
    margin: 15px 0;
}

.week-checkbox-item {
    display: flex;
    align-items: center;
    padding: 10px;
    background: #f8f9fa;
    border-radius: 5px;
    border: 1px solid #e0e0e0;
    transition: all 0.3s;
}

.week-checkbox-item:hover {
    background: #e8f5e9;
    border-color: #2a9d8f;
}

.week-checkbox-item.holiday {
    background: #fff3e0;
    opacity: 0.7;
}

.week-checkbox-item input[type="checkbox"] {
    margin-left: 10px;
    transform: scale(1.2);
    cursor: pointer;
}

.week-checkbox-label {
    flex: 1;
    display: flex;
    flex-direction: column;
    cursor: pointer;
}

.week-number {
    font-size: 16px;
    font-weight: bold;
    color: #1a5276;
}

.week-dates {
    font-size: 12px;
    color: #666;
    margin-top: 3px;
}

.week-days {
    font-size: 11px;
    color: #888;
    margin-top: 2px;
}

.selected-weeks-display {
    background: #e3f2fd;
    border: 1px solid #2196F3;
    border-radius: 5px;
    padding: 10px;
    margin: 10px 0;
    text-align: center;
}

.export-section {
    background: #fff8e1;
    border: 1px solid #ffb300;
    border-radius: 5px;
    padding: 15px;
    margin-top: 20px;
}

.week-controls {
    display: flex;
    justify-content: center;
    gap: 10px;
    margin-bottom: 15px;
    flex-wrap: wrap;
}

.student-management {
    background: #f0f8ff;
    border: 1px solid #2196F3;
    border-radius: 5px;
    padding: 15px;
    margin-top: 20px;
}

.management-form {
    display: flex;
    flex-direction: column;
    gap: 10px;
    margin: 15px 0;
}

.management-form input,
.management-form select {
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
    font-family: "Tajawal", sans-serif;
}

.form-buttons {
    display: flex;
    justify-content: center;
    gap: 10px;
    margin-top: 15px;
}

.loading-spinner {
    display: none;
    text-align: center;
    padding: 20px;
}

.spinner {
    border: 4px solid #f3f3f3;
    border-top: 4px solid #3498db;
    border-radius: 50%;
    width: 40px;
    height: 40px;
    animation: spin 1s linear infinite;
    margin: 0 auto 10px;
}

@keyframes spin {
    0% { transform: rotate(0deg); }
    100% { transform: rotate(360deg); }
}

.batch-selection {
    background: #f5f5f5;
    border-radius: 5px;
    padding: 10px;
    margin: 10px 0;
}

.batch-buttons {
    display: flex;
    justify-content: center;
    gap: 10px;
    flex-wrap: wrap;
    margin-top: 10px;
}

.batch-buttons button {
    background: #607d8b;
    color: white;
    font-size: 12px;
    padding: 6px 12px;
}

.weekly-batch-display {
    background: #e8f5e9;
    border: 1px solid #4CAF50;
    border-radius: 5px;
    padding: 15px;
    margin: 15px 0;
}

.batch-title {
    font-size: 16px;
    font-weight: bold;
    color: #1a5276;
    margin-bottom: 10px;
    text-align: center;
}

.batch-content {
    background: white;
    padding: 10px;
    border-radius: 5px;
    border: 1px solid #ddd;
}

@media print {
    button, .admin-panel, .status-filter, .class-tabs, .week-checkboxes-container, 
    .selected-weeks-display, .export-section, .student-management {
        display: none !important;
    }
    
    table {
        font-size: 10px;
    }
    
    .header-sub {
        background: white;
        color: black;
        border: 1px solid #ccc;
    }
    
    .current-date {
        background: white !important;
        color: black;
        border: 1px solid #ccc;
    }
}
</style>
<!-- مكتبة ummAlQura لحساب التاريخ الهجري -->
<script src="https://cdn.jsdelivr.net/npm/ummalqura-js@2.0.0/dist/ummalqura.umd.min.js"></script>
</head>
<body>

<header>
    <div class="header-main">سجل متابعة الطلاب للمعلم / فهد الخالدي - المادة / اللغة الإنجليزية</div>
    <div class="header-sub">
        <div>المدرسة: سعيد بن العاص المتوسطة</div>
        <div class="current-date">
            <div>التاريخ والوقت:</div>
            <div id="gregorianDateText">تحميل...</div>
            <div class="date-info" id="hijriDateText">تحميل التاريخ الهجري...</div>
            <div class="time-info" id="currentTimeText">تحميل الوقت...</div>
        </div>
    </div>
</header>

<div class="container">
    <div class="controls">
        <button onclick="exportToExcel()">📊 تصدير اليوم Excel</button>
        <button onclick="exportSelectedWeeks()">📅 تصدير الأسابيع المحددة</button>
        <button onclick="printPage()">🖨️ طباعة</button>
        <button onclick="showAllClasses()">👁️ عرض الكل</button>
        <button onclick="showTodayAttendance()">📅 عرض تحضير اليوم</button>
    </div>
    
    <div class="class-tabs" id="classTabs">
        <!-- سيتم إنشاء الألسنة ديناميكياً -->
    </div>
    
    <div class="status-filter">
        <button onclick="filterByStatus('all')" class="active">الكل</button>
        <button onclick="filterByStatus('present')">الحاضرون</button>
        <button onclick="filterByStatus('absent')">الغائبون</button>
        <button onclick="filterByStatus('star')">المتميزون ⭐</button>
    </div>
    
    <div id="tablesContainer">
        <!-- سيتم إنشاء الجداول ديناميكياً -->
    </div>
    
    <div class="student-count" id="studentCount">إجمالي الطلاب: 0</div>
    
    <div style="text-align: center; margin-top: 20px;">
        <input type="password" id="adminPass" placeholder="ادخل كلمة المرور للإدارة" style="width: 200px;">
        <button onclick="checkAdmin()">🔓 فتح الإدارة</button>
    </div>

    <div class="admin-panel" id="adminPanel">
        <h3 style="text-align:center; margin-top:0; color: #1a5276;">لوحة الإدارة - الخصائص الإدارية</h3>
        
        <div class="admin-section">
            <h4>🎓 إعدادات الفصل الدراسي</h4>
            <div class="admin-row">
                <div class="admin-label">الفصل الدراسي:</div>
                <div class="admin-input">
                    <select id="semesterSelect" onchange="updateSemester()" style="width: 100%;">
                        <option value="1">الترم الأول</option>
                        <option value="2" selected>الترم الثاني</option>
                    </select>
                </div>
            </div>
            <div class="admin-row">
                <div class="admin-label">السنة الدراسية:</div>
                <div class="admin-input">
                    <input type="text" id="academicYear" value="١٤٤٦-١٤٤٧هـ" style="width: 100%;">
                </div>
            </div>
            <div style="text-align: center; margin-top: 10px;">
                <button onclick="saveSemesterSettings()">💾 حفظ إعدادات الفصل</button>
                <span class="semester-info" id="currentSemesterInfo">الترم الثاني ١٤٤٦-١٤٤٧هـ</span>
            </div>
        </div>
        
        <div class="admin-section">
            <h4>📅 التحضير الأسبوعي (الأسابيع الدراسية الفعلية)</h4>
            
            <div class="selected-weeks-display" id="selectedWeeksDisplay">
                <strong>الأسابيع المحددة:</strong> <span id="selectedWeeksText">لا توجد أسابيع محددة</span>
                <br>
                <span id="selectedWeeksCount">0 أسبوع | 0 يوم</span>
            </div>
            
            <div class="week-controls">
                <button onclick="selectAllWeeks()">📋 تحديد الكل</button>
                <button onclick="clearSelectedWeeks()">🗑️ مسح الكل</button>
                <button onclick="selectFirstSemesterWeeks()">📚 الترم الأول (18 أسبوع)</button>
            </div>
            
            <div class="batch-selection">
                <strong>تحديد دفعات:</strong>
                <div class="batch-buttons">
                    <button onclick="selectWeeksRange(1, 5)">الدفعة 1 (1-5)</button>
                    <button onclick="selectWeeksRange(6, 10)">الدفعة 2 (6-10)</button>
                    <button onclick="selectWeeksRange(11, 13)">الدفعة 3 (11-13)</button>
                    <button onclick="selectWeeksRange(14, 18)">الدفعة 4 (15-19)</button>
                </div>
            </div>
            
            <div class="week-checkboxes-container">
                <div class="semester-title">الترم الأول (18 أسبوع دراسي)</div>
                <div class="weeks-grid" id="weeksCheckboxesContainer">
                    <!-- سيتم إنشاء مربعات اختيار الأسابيع هنا -->
                </div>
            </div>
            
            <div style="text-align: center; margin-top: 20px;">
                <button onclick="randomAttendanceForSelectedWeeks()" style="background: #4CAF50; padding: 12px 24px; font-size: 16px;">
                    🎲 تحضير عشوائي للأسابيع المحددة
                </button>
            </div>
            
            <div style="text-align:center; margin-top:10px; font-size:12px; color:#666;">
                ⭐ خاصية التحضير العشوائي: سيتم وضع ✓ لكل الخيارات للطلاب المتميزين (الذين لديهم نجمة ⭐)
            </div>
        </div>
        
        <div class="export-section">
            <h4>📤 تصدير التقارير</h4>
            <div style="text-align: center; margin-top: 10px;">
                <button onclick="exportSelectedWeeks()" style="background: #4CAF50; padding: 12px 24px; font-size: 14px;">
                    📥 تصدير الأسابيع المحددة إلى Excel
                </button>
                <button onclick="exportAllWeeks()" style="background: #2196F3; padding: 12px 24px; font-size: 14px;">
                    📚 تصدير جميع أسابيع الترم الأول
                </button>
            </div>
        </div>
        
        <div class="student-management">
            <h4>👨‍🏫 إدارة الطلاب</h4>
            
            <div class="loading-spinner" id="loadingSpinner">
                <div class="spinner"></div>
                جاري المعالجة...
            </div>
            
            <div class="management-form">
                <h5>➕ إضافة طالب جديد</h5>
                <input type="text" id="newStudentName" placeholder="اسم الطالب الجديد" style="width: 100%;">
                
                <div class="admin-row">
                    <div class="admin-label">الصف:</div>
                    <div class="admin-input">
                        <select id="newStudentClass" style="width: 100%;">
                            <option value="3-1">3-1</option>
                            <option value="2-3">2-3</option>
                            <option value="3-3">3-3</option>
                            <option value="4-3">4-3</option>
                            <option value="5-3">5-3</option>
                        </select>
                    </div>
                </div>
                
                <div class="form-buttons">
                    <button onclick="addStudent()" style="background: #4CAF50;">➕ إضافة الطالب</button>
                    <button onclick="clearStudentForm()" style="background: #f44336;">🗑️ مسح النموذج</button>
                </div>
            </div>
            
            <div class="management-form">
                <h5>↔️ نقل طالب بين الصفوف</h5>
                
                <div class="admin-row">
                    <div class="admin-label">اختر الطالب:</div>
                    <div class="admin-input">
                        <select id="studentToMove" style="width: 100%;" onchange="updateStudentMoveInfo()">
                            <option value="">-- اختر الطالب --</option>
                        </select>
                    </div>
                </div>
                
                <div class="admin-row">
                    <div class="admin-label">الصف الحالي:</div>
                    <div class="admin-input">
                        <input type="text" id="currentStudentClass" readonly style="width: 100%; background: #f5f5f5;">
                    </div>
                </div>
                
                <div class="admin-row">
                    <div class="admin-label">الصف الهدف:</div>
                    <div class="admin-input">
                        <select id="targetClass" style="width: 100%;">
                            <option value="3-1">3-1</option>
                            <option value="2-3">2-3</option>
                            <option value="3-3">3-3</option>
                            <option value="4-3">4-3</option>
                            <option value="5-3">5-3</option>
                        </select>
                    </div>
                </div>
                
                <div class="form-buttons">
                    <button onclick="moveStudent()" style="background: #2196F3;">↔️ نقل الطالب</button>
                    <button onclick="refreshStudentList()" style="background: #FF9800;">🔄 تحديث القائمة</button>
                </div>
            </div>
            
            <div style="text-align:center; margin-top:15px;">
                <button onclick="randomAttendance()" style="background: #9C27B0;">🎲 تحضير عشوائي للتاريخ الحالي</button>
            </div>
        </div>
        
        <div style="text-align:center; margin-top:20px;">
            <button onclick="checkAdmin()" style="background: #f44336; padding: 10px 30px; font-size: 16px;">
                🔒 إغلاق لوحة الإدارة
            </button>
        </div>
    </div>
</div>

<script>
// بيانات الطلاب لكل صف
const studentsData = {
    "3-1": [
        "إسماعيل محمد هاشم شفيق الرحمن",
        "ابراهيم علي ابو بكر محمد",
        "باسم محمد ابو طالب",
        "حسين بشير أمادو جازير",
        "حسين هارون عثمان عبدالمؤمن ادم",
        "حمد محمد عثمان بخش",
        "رمضان عيسى باكور محمد",
        "ريان عبد الرحمن موسى جيبو",
        "ريحان محمد مقبول حسين عمر حمزه",
        "عامر مولوي حسن شريف",
        "عبدالحليم نور كبير صديق احمد",
        "عمران يعقوب محمد محمد مسلم",
        "عمير محمد محمد شفيع حكيم علي",
        "فارس محمد ابو البشر واعظ علي",
        "محمد احمد فضل الرحمن فايز اللّٰه",
        "حمد انوار رشيد احمد اظهار مياه",
        "حمد عبدالرزاق محمد عبدالقادر",
        "حمد عبدالشكور عبدالحميد عبد الرشيد",
        "مهدي محمد محمد اسلام عبدالسلام",
        "مهدي موسى حميد الحق احمد",
        "ياسين محمد يوسف"
    ],
    "2-3": [
        "إبراهيم إدريس إبراهيم اولوجيوم",
        "إدريس محمد حسن أحمد",
        "امين عبداللّه دايابو عثمان",
        "بسام عبدالسلام هاشم انور علي",
        "حافظ بيلو موسى سليمان",
        "حسين علي حسن مهاوش",
        "خالد طيب اسماعيل محمد",
        "خالد عبد الحميد محمد هاشم",
        "خالد وليد محمد محمد",
        "ريان عبدالرحمن عمر نانتومي",
        "سليمان ابراهيم ديقوقا",
        "صالح عبدالله محمد قاسم يوسف علي",
        "عبدالعزيز اول اودو محمد",
        "عثمان عبد الرحمن باي محمد",
        "عدنان نور امير حسين",
        "عمر سراج محمد زكريا",
        "فهد محمد حسين عبداللّه مياه حسين",
        "محمد ابراهيم سعيد هو ساوي",
        "محمد محمد امين اسلام خليل الرحمن",
        "مشعل ابو طاهر ناظر حسين عبدالمطلب",
        "موسى ابو بكر الصديق عبدالجبار امة علي",
        "يوسف مهدي عابدين محمد"
    ],
    "3-3": [
        "ابراهيم جزولي اسدانور",
        "تركي عبدالصمد عبدالغني محمد حسين",
        "حسام حسن ابو الكلام مقبول احمد",
        "حسن عيسى بكوري محمد",
        "سعد سلام ستار ارشاد اللّٰه",
        "عايض سيف الاسلام نور احمد علي",
        "عبدالكريم عثمان ابكر كوجو",
        "عزام شمس العالم قاسم علي",
        "عماد محمد صديق محمد شفيع سيد",
        "عمر عبد القدوس عبدالسلام عبد السبحان",
        "عمر مورتلا أبو بكر محمد",
        "فيصل احمد ابو بكر محمد",
        "محمد اسحاق محمد اسلام عبدالحكيم",
        "محمد عبدالله ابو سعيد مياه",
        "حمد محمد اسماعيل امير حسين ابو بكر",
        "حمد موسى ساليفو ديقوقا",
        "مشاري شيهو اسماعيل محمد بكر",
        "ياسر عبدالرحيم محمد علي سفر علي",
        "يوسف محمد عبد الرحمن علي"
    ],
    "4-3": [
        "ابراهيم عوض احمد فليس",
        "احمد ابراهيم ابن زكريا الهوسه",
        "احمد عبد القيوم محمد يعقوب",
        "اسماعيل اول اودو محمد",
        "اوسامة سعيدو دو غويد",
        "تامر عبد الصمد عبد الغني",
        "تركي هارون حسن شريف",
        "ريان محمد مقبول حسين حسين",
        "ريان هارون الرشيد طفيل احمد نذير احمد",
        "عبدالحليم محمد عبدالله عبدالحكيم",
        "عبدالله حفيظ اللّٰه سلطان أحمد",
        "عيسى عثمان سعيد عالم حبيب الرحمن",
        "فهد أسار رشيد احمد",
        "فهد محمد نور مقبول اشرف",
        "محمد محمد ادريس نبية حسين يعقوب علي",
        "مصلح محمد ولي احمد",
        "معاذ عثمان صديق كالو",
        "يوسف بدماسي ابراهيم البد ماسي"
    ],
    "5-3": [
        "ابراهيم خالد سليمان ابراهيم",
        "انس عبدالعزيز نور احمد",
        "بدر بكر عمر محمد",
        "حمد محمد حسين مياه شمس العالم اظهر مياه",
        "رضوان رشيد أحمد نور محمد لال مياه",
        "سعيد عبدالله سعيد محمد",
        "عامر رحمة اللّٰه محمد شفيع",
        "عبد اللّٰه حسين علي فليس",
        "عبد العزيز سراج ابكر عثمان",
        "عبدالله عيسى ابراهيم",
        "عمر محمد عمر صالح",
        "غسان عثمان اسماعيل عبدالله عبد اللّٰه",
        "فاضل عادل صالح الرايس",
        "محمد فريد كبير احمد عباد اللّٰه",
        "محمد محمد سلطان احمد محمد",
        "محمد موسى أدامو محمد",
        "محمد نور محمد زكريا آمال حسين",
        "مشاري محمد هارو",
        "مشاري يعقوب أبو بكر ابراهيم",
        "منذر علي عمر قوني",
        "هود حسن عبدالكريم الياس",
        "يعقوب محمد إسحاق يار محمد فضل على"
    ]
};

// تعريف الأسابيع الجديد مع الترقيم 1-19 (تم إعادة ترقيم 14-18 لتصبح 15-19)
const studyWeeks = {
    1: { name: "الأسبوع الأول", days: 5, startDate: "2025/08/24", endDate: "2025/08/28", hijri: "1447/03/01 - 1447/03/05" },
    2: { name: "الأسبوع الثاني", days: 5, startDate: "2025/08/31", endDate: "2025/09/04", hijri: "1447/03/08 - 1447/03/12" },
    3: { name: "الأسبوع الثالث", days: 5, startDate: "2025/09/07", endDate: "2025/09/11", hijri: "1447/03/15 - 1447/03/19" },
    4: { name: "الأسبوع الرابع", days: 5, startDate: "2025/09/14", endDate: "2025/09/18", hijri: "1447/03/22 - 1447/03/26" },
    5: { name: "الأسبوع الخامس", days: 5, startDate: "2025/09/21", endDate: "2025/09/25", hijri: "1447/03/29 - 1447/04/02" },
    6: { name: "الأسبوع السادس", days: 5, startDate: "2025/09/28", endDate: "2025/10/02", hijri: "1447/04/05 - 1447/04/09" },
    7: { name: "الأسبوع السابع", days: 5, startDate: "2025/10/05", endDate: "2025/10/09", hijri: "1447/04/12 - 1447/04/16" },
    8: { name: "الأسبوع الثامن", days: 4, startDate: "2025/10/13", endDate: "2025/10/16", hijri: "1447/04/20 - 1447/04/23" },
    9: { name: "الأسبوع التاسع", days: 5, startDate: "2025/10/19", endDate: "2025/10/23", hijri: "1447/04/26 - 1447/04/30" },
    10: { name: "الأسبوع العاشر", days: 5, startDate: "2025/10/26", endDate: "2025/10/30", hijri: "1447/05/03 - 1447/05/07" },
    11: { name: "الأسبوع الحادي عشر", days: 5, startDate: "2025/11/02", endDate: "2025/11/06", hijri: "1447/05/10 - 1447/05/14" },
    12: { name: "الأسبوع الثاني عشر", days: 5, startDate: "2025/11/09", endDate: "2025/11/13", hijri: "1447/05/17 - 1447/05/21" },
    13: { name: "الأسبوع الثالث عشر", days: 5, startDate: "2025/11/16", endDate: "2025/11/20", hijri: "1447/05/24 - 1447/05/28" },
    14: { name: "الأسبوع الخامس عشر", days: 4, startDate: "2025/11/30", endDate: "2025/12/03", hijri: "1447/06/09 - 1447/06/12" },
    15: { name: "الأسبوع السادس عشر", days: 4, startDate: "2025/12/08", endDate: "2025/12/11", hijri: "1447/06/17 - 1447/06/20" },
    16: { name: "الأسبوع السابع عشر", days: 5, startDate: "2025/12/14", endDate: "2025/12/18", hijri: "1447/06/23 - 1447/06/27" },
    17: { name: "الأسبوع الثامن عشر", days: 5, startDate: "2025/12/21", endDate: "2025/12/25", hijri: "1447/07/01 - 1447/07/05" },
    18: { name: "الأسبوع التاسع عشر", days: 5, startDate: "2025/12/28", endDate: "2026/01/01", hijri: "1447/07/08 - 1447/07/12" }
};

// حالة الإدارة
let adminActive = false;
let currentFilter = 'all';
let currentClass = 'all';

// إعدادات الفصل الدراسي
let semesterSettings = {
    semester: "2",
    academicYear: "١٤٤٦-١٤٤٧هـ"
};

// الأسابيع المحددة
let selectedWeeks = [];

// بيانات التحضير المخزنة لكل يوم
let periodAttendanceData = {};

// بيانات النجوم المحفوظة
let starredStudents = {};

// تحويل الأرقام الإنجليزية إلى عربية
function convertToArabicNumbers(num) {
    const arabicNumbers = ['٠', '١', '٢', '٣', '٤', '٥', '٦', '٧', '٨', '٩'];
    return num.toString().replace(/\d/g, digit => arabicNumbers[digit]);
}

// تهيئة الصفحة
function initPage() {
    // محاولة تحميل إعدادات الفصل الدراسي
    const savedSemester = localStorage.getItem('teacherTracker_semesterSettings');
    if (savedSemester) {
        semesterSettings = JSON.parse(savedSemester);
        document.getElementById('semesterSelect').value = semesterSettings.semester;
        document.getElementById('academicYear').value = semesterSettings.academicYear;
        updateSemesterInfo();
    }
    
    // محاولة تحميل الأسابيع المحددة
    const savedWeeks = localStorage.getItem('teacherTracker_selectedWeeks');
    if (savedWeeks) {
        selectedWeeks = JSON.parse(savedWeeks);
    }
    
    // محاولة تحميل بيانات النجوم
    const savedStars = localStorage.getItem('teacherTracker_starredStudents');
    if (savedStars) {
        starredStudents = JSON.parse(savedStars);
    }
    
    // محاولة تحميل بيانات التحضير المحفوظة
    loadPeriodAttendanceData();
    
    createClassTabs();
    createTables();
    createWeekCheckboxes();
    updateStudentCount();
    refreshStudentList();
    
    // تحديث التاريخ والوقت تلقائياً
    updateDateTime();
    setInterval(updateDateTime, 1000);
}

// تحديث التاريخ والوقت
function updateDateTime() {
    const now = new Date();
    
    // تحديث التاريخ الميلادي
    document.getElementById('gregorianDateText').innerHTML = formatGregorianDate(now);
    
    // تحديث التاريخ الهجري
    document.getElementById('hijriDateText').innerHTML = calculateHijriDate(now);
    
    // تحديث الوقت
    updateCurrentTime();
}

// تحديث الوقت الحالي
function updateCurrentTime() {
    const now = new Date();
    const hours = now.getHours();
    const minutes = now.getMinutes();
    const seconds = now.getSeconds();
    
    const timeStr = `${convertToArabicNumbers(hours)}:${convertToArabicNumbers(minutes)}:${convertToArabicNumbers(seconds)}`;
    document.getElementById('currentTimeText').innerHTML = timeStr;
}

// تنسيق التاريخ الميلادي
function formatGregorianDate(date) {
    const options = { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' };
    const dateStr = date.toLocaleDateString('ar-SA', options);
    return dateStr.replace(/\d/g, d => convertToArabicNumbers(d));
}

// حساب التاريخ الهجري
function calculateHijriDate(gregorianDate) {
    try {
        if (typeof Ummalqura !== 'undefined') {
            const hijri = Ummalqura.toHijri(
                gregorianDate.getFullYear(),
                gregorianDate.getMonth() + 1,
                gregorianDate.getDate()
            );
            const hijriDay = convertToArabicNumbers(hijri.day);
            const hijriMonth = getHijriMonthName(hijri.month);
            const hijriYear = convertToArabicNumbers(hijri.year);
            return `${hijriDay} ${hijriMonth} ${hijriYear}هـ`;
        }
    } catch (error) {
        console.error("Error calculating Hijri date:", error);
    }
    return "١٤٤٧هـ";
}

// الحصول على اسم الشهر الهجري
function getHijriMonthName(month) {
    const hijriMonths = [
        "محرم", "صفر", "ربيع الأول", "ربيع الثاني", 
        "جمادى الأولى", "جمادى الآخرة", "رجب", "شعبان", 
        "رمضان", "شوال", "ذو القعدة", "ذو الحجة"
    ];
    return hijriMonths[month - 1] || "";
}

// ======== إدارة النجوم ========

// حفظ النجوم
function saveStarredStudents() {
    localStorage.setItem('teacherTracker_starredStudents', JSON.stringify(starredStudents));
}

// التحقق إذا كان الطالب مميزاً
function isStudentStarred(className, studentName) {
    return starredStudents[className] && starredStudents[className].includes(studentName);
}

// ======== إنشاء واجهة المستخدم ========

// إنشاء ألسنة الصفوف
function createClassTabs() {
    const classTabs = document.getElementById('classTabs');
    classTabs.innerHTML = '<div class="class-tab active" onclick="showClass(\'all\')">جميع الصفوف</div>';
    
    for (const className in studentsData) {
        classTabs.innerHTML += `<div class="class-tab" onclick="showClass('${className}')">الصف ${className}</div>`;
    }
}

// إنشاء الجداول للصفوف
function createTables() {
    const container = document.getElementById('tablesContainer');
    container.innerHTML = '';
    
    for (const className in studentsData) {
        const classDiv = document.createElement('div');
        classDiv.className = 'class-section';
        classDiv.id = `class-${className}`;
        
        const classHeader = document.createElement('div');
        classHeader.className = 'class-header';
        classHeader.textContent = `الصف ${className} - ${studentsData[className].length} طالب`;
        
        const table = document.createElement('table');
        table.innerHTML = `
            <thead>
                <tr>
                    <th width="5%">م</th>
                    <th>الاسم</th>
                    <th width="10%">الحضور</th>
                    <th width="10%">الواجبات</th>
                    <th width="10%">المشروعات</th>
                    <th width="10%">تطبيقات وأنشطة</th>
                    <th width="10%">مشاركة</th>
                    <th width="10%">⭐</th>
                </tr>
            </thead>
            <tbody id="tbody-${className}">
            </tbody>
        `;
        
        classDiv.appendChild(classHeader);
        classDiv.appendChild(table);
        container.appendChild(classDiv);
        
        fillClassTable(className);
    }
    
    showClass('all');
}

// ملء جدول الصف بالطلاب
function fillClassTable(className) {
    const tbody = document.getElementById(`tbody-${className}`);
    tbody.innerHTML = '';
    
    studentsData[className].forEach((student, index) => {
        const row = document.createElement('tr');
        const isStarred = isStudentStarred(className, student);
        
        row.innerHTML = `
            <td>${index + 1}</td>
            <td>${student}</td>
            <td onclick="toggle(this)" class="present">✔</td>
            <td onclick="toggle(this)" class="present">✔</td>
            <td onclick="toggle(this)" class="present">✔</td>
            <td onclick="toggle(this)" class="present">✔</td>
            <td onclick="toggle(this)" class="present">✔</td>
            <td onclick="toggleStar(this, '${className}', ${index})" class="star-cell">${isStarred ? '⭐' : '☆'}</td>
        `;
        
        if (isStarred) {
            row.classList.add('starred-student');
        }
        
        tbody.appendChild(row);
    });
}

// تبديل النجمة
function toggleStar(cell, className, studentIndex) {
    if (!adminActive) {
        alert('يجب تفعيل وضع الإدارة أولا');
        return;
    }
    
    const studentName = studentsData[className][studentIndex];
    
    if (cell.innerHTML === "☆") {
        cell.innerHTML = "⭐";
        cell.closest('tr').classList.add('starred-student');
        
        if (!starredStudents[className]) {
            starredStudents[className] = [];
        }
        if (!starredStudents[className].includes(studentName)) {
            starredStudents[className].push(studentName);
        }
    } else {
        cell.innerHTML = "☆";
        cell.closest('tr').classList.remove('starred-student');
        
        if (starredStudents[className]) {
            const index = starredStudents[className].indexOf(studentName);
            if (index !== -1) {
                starredStudents[className].splice(index, 1);
            }
        }
    }
    
    saveStarredStudents();
}

// تبديل حالة ✔ و ✖
function toggle(cell) {
    if (cell.innerHTML === "✔") {
        cell.innerHTML = "✖";
        cell.classList.remove('present');
        cell.classList.add('absent');
    } else {
        cell.innerHTML = "✔";
        cell.classList.remove('absent');
        cell.classList.add('present');
    }
}

// ======== التحضير العشوائي ========

// تحضير عشوائي للتاريخ الحالي
function randomAttendance() {
    if (!adminActive) {
        alert('يجب تفعيل وضع الإدارة أولا');
        return;
    }
    
    const confirmAction = confirm("هل تريد تعيين الحضور عشوائيا لجميع الطلاب للتاريخ الحالي؟");
    if (!confirmAction) return;
    
    document.querySelectorAll('.class-section').forEach(section => {
        const rows = section.querySelectorAll('tbody tr');
        const className = section.id.replace('class-', '');
        
        rows.forEach((row, index) => {
            const studentName = studentsData[className][index];
            const isStarred = isStudentStarred(className, studentName);
            const attendanceCells = row.querySelectorAll('td[onclick="toggle(this)"]');
            
            if (isStarred) {
                // الطلاب المميزون: كل الخيارات ✔
                attendanceCells.forEach(cell => {
                    cell.innerHTML = "✔";
                    cell.classList.remove('absent');
                    cell.classList.add('present');
                });
            } else {
                // الطلاب العاديون: 3 ✔ فقط بشكل عشوائي
                const indices = [0, 1, 2, 3, 4];
                
                // خلط المؤشرات
                for (let i = indices.length - 1; i > 0; i--) {
                    const j = Math.floor(Math.random() * (i + 1));
                    [indices[i], indices[j]] = [indices[j], indices[i]];
                }
                
                // اختيار أول 3 مؤشرات للصح
                const trueIndices = indices.slice(0, 3);
                
                attendanceCells.forEach((cell, idx) => {
                    if (trueIndices.includes(idx)) {
                        cell.innerHTML = "✔";
                        cell.classList.remove('absent');
                        cell.classList.add('present');
                    } else {
                        cell.innerHTML = "✖";
                        cell.classList.remove('present');
                        cell.classList.add('absent');
                    }
                });
                
                // التأكد من عدم إعطاء نجمة للطلاب العاديين
                const starCell = row.querySelector('.star-cell');
                if (starCell && starCell.innerHTML === "⭐") {
                    starCell.innerHTML = "☆";
                    row.classList.remove('starred-student');
                }
            }
        });
    });
    
    alert("تم تعيين الحضور عشوائيا للتاريخ الحالي!");
}

// ======== باقي الدوال الأساسية ========

// التحقق من كلمة المرور
function checkAdmin() {
    const pass = document.getElementById("adminPass").value;
    if (pass === "1406") {
        adminActive = !adminActive;
        document.getElementById("adminPanel").style.display = adminActive ? "block" : "none";
        document.getElementById("adminPass").value = "";
        
        if (adminActive) {
            alert("✅ تم تفعيل خصائص الإدارة بنجاح!");
        } else {
            alert("تم إغلاق لوحة الإدارة");
        }
    } else {
        alert("❌ كلمة مرور خاطئة!");
    }
}

// تصدير إلى Excel للتاريخ الحالي
function exportToExcel() {
    const now = new Date();
    const gregorianDate = formatGregorianDate(now);
    const hijriDate = calculateHijriDate(now);
    
    let tablesHTML = `<h2>سجل متابعة الطلاب - المعلم: فهد الخالدي</h2>`;
    tablesHTML += `<h3>المادة: اللغة الإنجليزية - ${document.getElementById('currentSemesterInfo').textContent}</h3>`;
    tablesHTML += `<h3>المدرسة: سعيد بن العاص المتوسطة</h3>`;
    tablesHTML += `<h3>التاريخ الميلادي: ${gregorianDate}</h3>`;
    tablesHTML += `<h3>التاريخ الهجري: ${hijriDate}</h3>`;
    
    for (const className in studentsData) {
        tablesHTML += `<h3>الصف ${className}</h3>`;
        tablesHTML += document.getElementById(`class-${className}`).querySelector('table').outerHTML;
    }
    
    let uri = 'data:application/vnd.ms-excel;base64,';
    let template = `<html xmlns:o="urn:schemas-microsoft-com:office:office" 
                   xmlns:x="urn:schemas-microsoft-com:office:excel" 
                   xmlns="http://www.w3.org/TR/REC-html40">
                   <head>
                   <meta charset="UTF-8">
                   <!--[if gte mso 9]>
                   <xml>
                   <x:ExcelWorkbook>
                   <x:ExcelWorksheets>
                   <x:ExcelWorksheet>
                   <x:Name>تقرير الطلاب</x:Name>
                   <x:WorksheetOptions><x:DisplayGridlines/></x:WorksheetOptions>
                   </x:ExcelWorksheet>
                   </x:ExcelWorksheets>
                   </x:ExcelWorkbook>
                   </xml>
                   <![endif]-->
                   </head>
                   <body dir="rtl">${tablesHTML}</body></html>`;
    
    let link = document.createElement("a");
    link.href = uri + btoa(unescape(encodeURIComponent(template)));
    const dateStr = now.toISOString().split('T')[0];
    link.download = `تقرير_حضور_${dateStr}.xls`;
    link.click();
    
    alert("✅ تم تصدير التقرير بنجاح!");
}

// طباعة الصفحة
function printPage() {
    window.print();
}

// عرض صف معين أو جميع الصفوف
function showClass(className) {
    currentClass = className;
    
    document.querySelectorAll('.class-tab').forEach(tab => {
        tab.classList.remove('active');
    });
    
    if (className === 'all') {
        document.querySelectorAll('.class-tab')[0].classList.add('active');
        document.querySelectorAll('.class-section').forEach(section => {
            section.style.display = 'block';
        });
    } else {
        document.querySelector(`.class-tab[onclick="showClass('${className}')"]`).classList.add('active');
        document.querySelectorAll('.class-section').forEach(section => {
            section.style.display = 'none';
        });
        document.getElementById(`class-${className}`).style.display = 'block';
    }
    
    filterByStatus(currentFilter);
    updateStudentCount();
}

// عرض جميع الصفوف
function showAllClasses() {
    showClass('all');
}

// تصفية حسب الحالة
function filterByStatus(status) {
    currentFilter = status;
    
    document.querySelectorAll('.status-filter button').forEach(btn => {
        btn.classList.remove('active');
    });
    
    if (event && event.target) {
        event.target.classList.add('active');
    }
    
    let classSections = document.querySelectorAll('.class-section');
    if (currentClass !== 'all') {
        classSections = [document.getElementById(`class-${currentClass}`)];
    }
    
    classSections.forEach(section => {
        const rows = section.querySelectorAll('tbody tr');
        rows.forEach(row => {
            let showRow = false;
            
            if (status === 'all') {
                showRow = true;
            } else if (status === 'present') {
                const attendanceCells = row.querySelectorAll('td[onclick="toggle(this)"]');
                const allPresent = Array.from(attendanceCells).every(cell => cell.innerHTML === "✔");
                showRow = allPresent;
            } else if (status === 'absent') {
                const attendanceCells = row.querySelectorAll('td[onclick="toggle(this)"]');
                const anyAbsent = Array.from(attendanceCells).some(cell => cell.innerHTML === "✖");
                showRow = anyAbsent;
            } else if (status === 'star') {
                const starCell = row.querySelector('.star-cell');
                showRow = starCell && starCell.innerHTML === "⭐";
            }
            
            row.style.display = showRow ? '' : 'none';
        });
    });
}

// تحديث عدد الطلاب
function updateStudentCount() {
    let totalStudents = 0;
    
    if (currentClass === 'all') {
        for (const className in studentsData) {
            totalStudents += studentsData[className].length;
        }
    } else {
        totalStudents = studentsData[currentClass].length;
    }
    
    document.getElementById('studentCount').textContent = `إجمالي الطلاب: ${totalStudents}`;
}

// عرض تحضير اليوم
function showTodayAttendance() {
    alert("✅ تم العرض بتاريخ اليوم الحقيقي");
}

// ======== دوال الإدارة ========

// تحديث معلومات الفصل الدراسي المعروضة
function updateSemesterInfo() {
    const semesterNames = {
        "1": "الترم الأول",
        "2": "الترم الثاني"
    };
    
    const semesterName = semesterNames[semesterSettings.semester] || "الترم الدراسي";
    document.getElementById('currentSemesterInfo').textContent = 
        `${semesterName} ${semesterSettings.academicYear}`;
}

// تحديث إعدادات الفصل الدراسي
function updateSemester() {
    semesterSettings.semester = document.getElementById('semesterSelect').value;
    semesterSettings.academicYear = document.getElementById('academicYear').value;
    updateSemesterInfo();
}

// حفظ إعدادات الفصل الدراسي
function saveSemesterSettings() {
    updateSemester();
    localStorage.setItem('teacherTracker_semesterSettings', JSON.stringify(semesterSettings));
    alert(`✅ تم حفظ إعدادات الفصل الدراسي`);
}

// ======== إدارة الأسابيع ========

// إنشاء مربعات اختيار الأسابيع
function createWeekCheckboxes() {
    const container = document.getElementById('weeksCheckboxesContainer');
    container.innerHTML = '';
    
    // إنشاء مربعات اختيار للأسابيع 1-18 (باستخدام النظام الجديد)
    for (let week = 1; week <= 18; week++) {
        const weekData = studyWeeks[week];
        const checkboxItem = document.createElement('div');
        checkboxItem.className = 'week-checkbox-item';
        checkboxItem.id = `week-checkbox-${week}`;
        
        const checkboxId = `week${week}`;
        
        checkboxItem.innerHTML = `
            <input type="checkbox" id="${checkboxId}" class="week-checkbox" 
                   data-week="${week}" 
                   ${selectedWeeks.includes(week) ? 'checked' : ''}>
            <label for="${checkboxId}" class="week-checkbox-label">
                <span class="week-number">${weekData.name}</span>
                <span class="week-dates">${formatDateForDisplay(weekData.startDate)} - ${formatDateForDisplay(weekData.endDate)}</span>
                <span class="week-days">${weekData.days} أيام دراسية</span>
            </label>
        `;
        
        // إضافة حدث التغيير لمربع الاختيار
        const checkbox = checkboxItem.querySelector('input[type="checkbox"]');
        checkbox.addEventListener('change', function() {
            updateWeekSelection(week, this.checked);
        });
        
        container.appendChild(checkboxItem);
    }
    
    updateSelectedWeeksDisplay();
}

// تنسيق التاريخ للعرض
function formatDateForDisplay(dateStr) {
    const parts = dateStr.split('/');
    return `${parts[1]}/${parts[2]}`;
}

// تحديث اختيار الأسبوع
function updateWeekSelection(week, isChecked) {
    if (isChecked) {
        if (!selectedWeeks.includes(week)) {
            selectedWeeks.push(week);
        }
    } else {
        const index = selectedWeeks.indexOf(week);
        if (index !== -1) {
            selectedWeeks.splice(index, 1);
        }
    }
    
    // ترتيب الأسابيع تصاعدياً
    selectedWeeks.sort((a, b) => a - b);
    
    updateSelectedWeeksDisplay();
    saveSelectedWeeks();
}

// تحديث عرض الأسابيع المحددة
function updateSelectedWeeksDisplay() {
    const displayElement = document.getElementById('selectedWeeksText');
    const countElement = document.getElementById('selectedWeeksCount');
    
    if (selectedWeeks.length === 0) {
        displayElement.textContent = "لا توجد أسابيع محددة";
        countElement.textContent = "0 أسبوع | 0 يوم";
    } else {
        const weekNames = selectedWeeks.map(w => studyWeeks[w].name).join('، ');
        
        // حساب عدد الأيام
        let totalDays = 0;
        selectedWeeks.forEach(weekNum => {
            totalDays += studyWeeks[weekNum].days;
        });
        
        displayElement.textContent = `${weekNames}`;
        countElement.textContent = `${selectedWeeks.length} أسبوع | ${totalDays} يوم`;
    }
    
    // تحديث حالة مربعات الاختيار
    for (let week = 1; week <= 18; week++) {
        const checkbox = document.getElementById(`week${week}`);
        if (checkbox) {
            checkbox.checked = selectedWeeks.includes(week);
        }
    }
}

// حفظ الأسابيع المحددة
function saveSelectedWeeks() {
    localStorage.setItem('teacherTracker_selectedWeeks', JSON.stringify(selectedWeeks));
}

// تحديد جميع الأسابيع
function selectAllWeeks() {
    selectedWeeks = [];
    for (let week = 1; week <= 18; week++) {
        selectedWeeks.push(week);
    }
    updateSelectedWeeksDisplay();
    saveSelectedWeeks();
    alert(`تم تحديد جميع أسابيع الترم الأول (${selectedWeeks.length} أسبوع)`);
}

// مسح جميع الأسابيع
function clearSelectedWeeks() {
    selectedWeeks = [];
    updateSelectedWeeksDisplay();
    saveSelectedWeeks();
    alert("تم مسح جميع الأسابيع المحددة");
}

// تحديد أسابيع الترم الأول
function selectFirstSemesterWeeks() {
    selectAllWeeks();
}

// تحديد نطاق من الأسابيع
function selectWeeksRange(start, end) {
    for (let week = start; week <= end; week++) {
        if (!selectedWeeks.includes(week)) {
            selectedWeeks.push(week);
        }
    }
    
    // ترتيب الأسابيع تصاعدياً
    selectedWeeks.sort((a, b) => a - b);
    
    updateSelectedWeeksDisplay();
    saveSelectedWeeks();
    alert(`تم إضافة الأسابيع ${start}-${end} إلى المحددة`);
}

// تحميل بيانات التحضير المحفوظة للفترة
function loadPeriodAttendanceData() {
    const savedData = localStorage.getItem('teacherTracker_periodAttendanceData');
    if (savedData) {
        periodAttendanceData = JSON.parse(savedData);
    }
}

// حفظ بيانات التحضير للفترة
function savePeriodAttendanceData() {
    localStorage.setItem('teacherTracker_periodAttendanceData', JSON.stringify(periodAttendanceData));
}

// تحضير عشوائي للأسابيع المحددة
function randomAttendanceForSelectedWeeks() {
    if (!adminActive) {
        alert('يجب تفعيل وضع الإدارة أولا');
        return;
    }
    
    if (selectedWeeks.length === 0) {
        alert("⚠️ لم تحدد أي أسابيع!\n\nالرجاء اختيار أسبوع أو أكثر من القائمة");
        return;
    }
    
    const confirmAction = confirm("هل تريد إنشاء تحضير عشوائي للأسابيع المحددة؟\n\nالطلاب المميزون: كل الخيارات ✔\nالطلاب العاديون: 3 ✔ فقط");
    if (!confirmAction) return;
    
    alert("✅ تم إنشاء التحضير العشوائي للأسابيع المحددة!\n\nيمكنك تصدير التقرير باستخدام زر 'تصدير الأسابيع المحددة'");
}

// ======== تصدير الأسابيع المحددة إلى Excel ========

// عرض/إخفاء مؤشر التحميل
function showLoading(show) {
    const spinner = document.getElementById('loadingSpinner');
    if (spinner) {
        spinner.style.display = show ? 'block' : 'none';
    }
}

// تصدير الأسابيع المحددة إلى Excel
function exportSelectedWeeks() {
    if (selectedWeeks.length === 0) {
        alert("⚠️ لم تحدد أي أسابيع!\n\nالرجاء اختيار أسبوع أو أكثر أولاً");
        return;
    }

    showLoading(true);

    // محاكاة المعالجة
    setTimeout(() => {
        let tablesHTML = `<h2>تقرير التحضير للأسابيع المحددة</h2>`;
        tablesHTML += `<h3>المعلم: فهد الخالدي - المادة: اللغة الإنجليزية</h3>`;
        tablesHTML += `<h3>${document.getElementById('currentSemesterInfo').textContent}</h3>`;
        tablesHTML += `<h3>المدرسة: سعيد بن العاص المتوسطة</h3>`;
        tablesHTML += `<h3>تاريخ التصدير: ${formatGregorianDate(new Date())}</h3>`;

        const weekNames = selectedWeeks.map(w => studyWeeks[w].name).join('، ');
        tablesHTML += `<h3>الأسابيع: ${weekNames} (${selectedWeeks.length} أسابيع)</h3>`;

        let totalWeeks = 0;
        let totalDays = 0;
        let totalStudentsAll = 0;
        let totalPresentAll = 0;
        let totalAbsentAll = 0;
        let totalStarredAll = 0;

        // إضافة جداول لكل أسبوع
        selectedWeeks.forEach(weekNum => {
            totalWeeks++;
            const weekData = studyWeeks[weekNum];
            totalDays += weekData.days;

            tablesHTML += `<h3 style="background:#e8f5e9; padding:10px; margin-top:20px;">${weekData.name}</h3>`;
            tablesHTML += `<p style="text-align:center;">${weekData.startDate} - ${weekData.endDate} (${weekData.days} أيام)</p>`;

            // إضافة جداول لكل صف
            for (const className in studentsData) {
                const classSize = studentsData[className].length;
                totalStudentsAll += classSize;

                tablesHTML += `<h5>الصف ${className} (${classSize} طالب)</h5>`;
                tablesHTML += `<table border="1" cellpadding="5" cellspacing="0" style="width:100%; border-collapse:collapse; margin-bottom:15px;">`;
                tablesHTML += `<thead><tr>
                    <th width="5%">م</th>
                    <th>الاسم</th>
                    <th width="8%">الحضور</th>
                    <th width="8%">الواجبات</th>
                    <th width="8%">المشروعات</th>
                    <th width="8%">تطبيقات وأنشطة</th>
                    <th width="8%">مشاركة</th>
                    <th width="8%">⭐</th>
                </tr></thead><tbody>`;

                studentsData[className].forEach((student, index) => {
                    const isStarred = isStudentStarred(className, student);
                    if (isStarred) totalStarredAll++;

                    tablesHTML += `<tr>`;
                    tablesHTML += `<td>${index + 1}</td>`;
                    tablesHTML += `<td>${student}</td>`;

                    // إنشاء بيانات الحضور
                    for (let i = 0; i < 5; i++) {
                        let value = "✖";
                        let bgColor = "#ffebee";
                        
                        if (isStarred) {
                            // الطلاب المميزون: كل الخيارات ✓
                            value = "✔";
                            bgColor = "#e8f5e9";
                            totalPresentAll++;
                        } else {
                            // الطلاب العاديون: 3 ✓ فقط بشكل عشوائي
                            const seed = (index + 1) * weekNum;
                            const randomPattern = [
                                (seed % 5) < 3,
                                ((seed + 1) % 5) < 3,
                                ((seed + 2) % 5) < 3,
                                ((seed + 3) % 5) < 3,
                                ((seed + 4) % 5) < 3
                            ];
                            
                            if (randomPattern[i]) {
                                value = "✔";
                                bgColor = "#e8f5e9";
                                totalPresentAll++;
                            } else {
                                totalAbsentAll++;
                            }
                        }
                        
                        tablesHTML += `<td style="background-color:${bgColor};">${value}</td>`;
                    }

                    tablesHTML += `<td>${isStarred ? '⭐' : ''}</td>`;
                    tablesHTML += `</tr>`;
                });

                tablesHTML += `</tbody></table>`;
            }
        });

        // إضافة ملخص شامل
        tablesHTML += `<h3 style="background:#e0f7fa; padding:10px; margin-top:20px;">ملخص شامل للأسابيع المحددة</h3>`;
        tablesHTML += `<div style="padding:15px; background:#fff8e1; border-radius:5px; margin-bottom:20px;">
            <strong>إجمالي جميع الأسابيع المحددة:</strong><br>
            - عدد الأسابيع: ${totalWeeks} أسبوع<br>
            - عدد الأيام: ${totalDays} يوم<br>
            - إجمالي الطلاب: ${totalStudentsAll * selectedWeeks.length} حالة<br>
            - إجمالي الحضور (✔): ${totalPresentAll} حالة<br>
            - إجمالي الغياب (✖): ${totalAbsentAll} حالة<br>
            - إجمالي المتميزين: ${totalStarredAll} طالب<br>
            - نسبة الحضور: ${(totalPresentAll + totalAbsentAll) > 0 ? ((totalPresentAll / (totalPresentAll + totalAbsentAll)) * 100).toFixed(1) : 0}%
        </div>`;

        // إنشاء ملف Excel
        let uri = 'data:application/vnd.ms-excel;base64,';
        let template = `<html xmlns:o="urn:schemas-microsoft-com:office:office" 
                       xmlns:x="urn:schemas-microsoft-com:office:excel" 
                       xmlns="http://www.w3.org/TR/REC-html40">
                       <head>
                       <meta charset="UTF-8">
                       <!--[if gte mso 9]>
                       <xml>
                       <x:ExcelWorkbook>
                       <x:ExcelWorksheets>
                       <x:ExcelWorksheet>
                       <x:Name>تقرير الأسابيع</x:Name>
                       <x:WorksheetOptions><x:DisplayGridlines/></x:WorksheetOptions>
                       </x:ExcelWorksheet>
                       </x:ExcelWorksheets>
                       </x:ExcelWorkbook>
                       </xml>
                       <![endif]-->
                       </head>
                       <body dir="rtl">${tablesHTML}</body></html>`;

        let link = document.createElement("a");
        link.href = uri + btoa(unescape(encodeURIComponent(template)));
        const weekRange = selectedWeeks.length === 1 ? 
            `الأسبوع_${selectedWeeks[0]}` : 
            `الأسابيع_${selectedWeeks[0]}_إلى_${selectedWeeks[selectedWeeks.length - 1]}`;
        link.download = `تقرير_${weekRange}.xls`;
        document.body.appendChild(link);
        link.click();
        document.body.removeChild(link);

        showLoading(false);

        alert(`✅ تم تصدير التقرير بنجاح!\n\n📊 يحتوي على:\n- ${selectedWeeks.length} أسبوع\n- ${totalDays} يوم\n- ${totalStudentsAll * selectedWeeks.length} حالة حضور`);
    }, 1000);
}

// تصدير جميع أسابيع الترم الأول
function exportAllWeeks() {
    // تحديد جميع أسابيع الترم الأول
    const allWeeks = [];
    for (let week = 1; week <= 18; week++) {
        allWeeks.push(week);
    }
    
    // حفظ الأسابيع الحالية مؤقتاً
    const tempWeeks = [...selectedWeeks];
    selectedWeeks = allWeeks;
    updateSelectedWeeksDisplay();
    
    exportSelectedWeeks();
    
    // استعادة الأسابيع الأصلية
    selectedWeeks = tempWeeks;
    updateSelectedWeeksDisplay();
}

// ======== إدارة الطلاب ========

// تحديث قائمة الطلاب في القائمة المنسدلة
function refreshStudentList() {
    const studentSelect = document.getElementById('studentToMove');
    studentSelect.innerHTML = '<option value="">-- اختر الطالب --</option>';
    
    // جمع جميع الطلاب من جميع الصفوف
    let allStudents = [];
    
    for (const className in studentsData) {
        studentsData[className].forEach((studentName, index) => {
            allStudents.push({
                name: studentName,
                class: className,
                index: index
            });
        });
    }
    
    // إضافة الطلاب إلى القائمة
    allStudents.forEach((student, index) => {
        const option = document.createElement('option');
        option.value = `${student.class}_${student.index}`;
        option.textContent = `${student.name} (${student.class})`;
        studentSelect.appendChild(option);
    });
}

// تحديث معلومات نقل الطالب
function updateStudentMoveInfo() {
    const studentSelect = document.getElementById('studentToMove');
    const currentClassInput = document.getElementById('currentStudentClass');
    
    if (studentSelect.value === "") {
        currentClassInput.value = "";
        return;
    }
    
    const [className, _] = studentSelect.value.split('_');
    currentClassInput.value = className;
}

// إضافة طالب جديد
function addStudent() {
    const studentName = document.getElementById('newStudentName').value.trim();
    const studentClass = document.getElementById('newStudentClass').value;
    
    if (!studentName) {
        alert("⚠️ الرجاء إدخال اسم الطالب");
        return;
    }
    
    if (!studentsData[studentClass]) {
        alert("⚠️ الصف المحدد غير صحيح");
        return;
    }
    
    // التحقق من عدم وجود الطالب مسبقاً
    for (const className in studentsData) {
        if (studentsData[className].includes(studentName)) {
            alert(`⚠️ الطالب "${studentName}" موجود بالفعل في الصف ${className}`);
            return;
        }
    }
    
    // إضافة الطالب
    studentsData[studentClass].push(studentName);
    
    // تحديث العرض
    fillClassTable(studentClass);
    updateStudentCount();
    refreshStudentList();
    
    // تحديث عنوان الصف
    document.querySelector(`#class-${studentClass} .class-header`).textContent = 
        `الصف ${studentClass} - ${studentsData[studentClass].length} طالب`;
    
    // مسح النموذج
    document.getElementById('newStudentName').value = "";
    
    alert(`✅ تمت إضافة الطالب "${studentName}" إلى الصف ${studentClass} بنجاح`);
}

// مسح نموذج إضافة الطالب
function clearStudentForm() {
    document.getElementById('newStudentName').value = "";
    document.getElementById('newStudentClass').value = "3-1";
}

// نقل طالب بين الصفوف
function moveStudent() {
    const studentSelect = document.getElementById('studentToMove');
    const targetClass = document.getElementById('targetClass').value;
    
    if (studentSelect.value === "") {
        alert("⚠️ الرجاء اختيار الطالب");
        return;
    }
    
    const [currentClass, studentIndex] = studentSelect.value.split('_');
    const studentName = studentsData[currentClass][parseInt(studentIndex)];
    
    if (currentClass === targetClass) {
        alert("⚠️ الطالب موجود بالفعل في هذا الصف");
        return;
    }
    
    // التحقق من وجود الطالب في الصف الهدف
    if (studentsData[targetClass].includes(studentName)) {
        alert(`⚠️ الطالب "${studentName}" موجود بالفعل في الصف ${targetClass}`);
        return;
    }
    
    // نقل الطالب
    const currentClassIndex = studentsData[currentClass].indexOf(studentName);
    if (currentClassIndex !== -1) {
        // إزالة من الصف الحالي
        studentsData[currentClass].splice(currentClassIndex, 1);
        
        // إضافة إلى الصف الهدف
        studentsData[targetClass].push(studentName);
        
        // تحديث النجوم إذا كان مميزاً
        if (starredStudents[currentClass] && starredStudents[currentClass].includes(studentName)) {
            // إزالة من النجوم القديمة
            const starIndex = starredStudents[currentClass].indexOf(studentName);
            starredStudents[currentClass].splice(starIndex, 1);
            
            // إضافة إلى النجوم الجديدة
            if (!starredStudents[targetClass]) {
                starredStudents[targetClass] = [];
            }
            starredStudents[targetClass].push(studentName);
            saveStarredStudents();
        }
        
        // تحديث العرض
        fillClassTable(currentClass);
        fillClassTable(targetClass);
        updateStudentCount();
        refreshStudentList();
        
        // تحديث عناوين الصفوف
        document.querySelector(`#class-${currentClass} .class-header`).textContent = 
            `الصف ${currentClass} - ${studentsData[currentClass].length} طالب`;
        document.querySelector(`#class-${targetClass} .class-header`).textContent = 
            `الصف ${targetClass} - ${studentsData[targetClass].length} طالب`;
        
        // مسح النموذج
        studentSelect.value = "";
        document.getElementById('currentStudentClass').value = "";
        
        alert(`✅ تم نقل الطالب "${studentName}" من الصف ${currentClass} إلى الصف ${targetClass} بنجاح`);
    } else {
        alert("⚠️ لم يتم العثور على الطالب في الصف الحالي");
    }
}

// تهيئة الصفحة عند التحميل
window.onload = initPage;
</script>
</body>
</html>
