<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>أداة تحضير الطلاب</title>
<link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@400;700&display=swap" rel="stylesheet">
<style>
  body { font-family: 'Tajawal', sans-serif; background: #f4f4f4; padding: 20px; }
  table { width: 100%; border-collapse: collapse; margin-bottom: 20px; }
  th, td { border: 1px solid #ccc; padding: 8px; text-align: center; }
  th { background: #007bff; color: #fff; }
  td.toggle { cursor: pointer; font-size: 20px; }
  button { padding: 8px 15px; margin: 5px; cursor: pointer; }
  #adminPanel { display:none; border:1px solid #007bff; padding:10px; margin-top:20px; background:#e6f0ff; }
  h2 { margin-top: 30px; }
</style>
</head>
<body>

<h1>أداة تحضير الطلاب</h1>

<div id="weeksContainer"></div>

<hr>

<button onclick="printPage()">طباعة التحضير</button>
<button onclick="exportExcel()">تصدير Excel</button>
<button onclick="toggleAdmin()">إدارة</button>

<div id="adminPanel">
  <label>أدخل الرقم السري: <input type="password" id="adminPass"></label>
  <button onclick="loginAdmin()">دخول</button>
  <div id="adminActions" style="margin-top:10px; display:none;">
    <h3>تحضير عشوائي لكل أسبوع</h3>
    <div id="adminWeekButtons"></div>
    <button onclick="randomizeAll()">تحضير عشوائي لجميع الفصول</button>
  </div>
</div>

<script src="https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.18.5/xlsx.full.min.js"></script>
<script>
// ----- بيانات الطلاب -----
const students = {
"3-1":[
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
"2-3":[
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
"3-3":[
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
"4-3":[
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
"5-3":[
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

// ----- بيانات الأسابيع والتواريخ -----
const weeks = {
"الأسبوع 1":["2025-08-24","2025-08-25","2025-08-26","2025-08-27","2025-08-28"],
"الأسبوع 2":["2025-08-31","2025-09-01","2025-09-02","2025-09-03","2025-09-04"],
"الأسبوع 3":["2025-09-07","2025-09-08","2025-09-09","2025-09-10","2025-09-11"],
"الأسبوع 4":["2025-09-14","2025-09-15","2025-09-16","2025-09-17","2025-09-18"],
"الأسبوع 5":["2025-09-21","2025-09-22","2025-09-23","2025-09-24","2025-09-25"],
"الأسبوع 6":["2025-09-28","2025-09-29","2025-09-30","2025-10-01","2025-10-02"],
"الأسبوع 7":["2025-10-05","2025-10-06","2025-10-07","2025-10-08","2025-10-09"],
"الأسبوع 8":["2025-10-13","2025-10-14","2025-10-15","2025-10-16"],
"الأسبوع 9":["2025-10-19","2025-10-20","2025-10-21","2025-10-22","2025-10-23"],
"الأسبوع 10":["2025-10-26","2025-10-27","2025-10-28","2025-10-29","2025-10-30"],
"الأسبوع 11":["2025-11-02","2025-11-03","2025-11-04","2025-11-05","2025-11-06"],
"الأسبوع 12":["2025-11-09","2025-11-10","2025-11-11","2025-11-12","2025-11-13"],
"الأسبوع 13":["2025-11-16","2025-11-17","2025-11-18","2025-11-19","2025-11-20"],
"الأسبوع 15":["2025-11-30","2025-12-01","2025-12-02","2025-12-03"],
"الأسبوع 16":["2025-12-08","2025-12-09","2025-12-10","2025-12-11"],
"الأسبوع 17":["2025-12-14","2025-12-15","2025-12-16","2025-12-17","2025-12-18"],
"الأسبوع 18":["2025-12-21","2025-12-22","2025-12-23","2025-12-24","2025-12-25"],
"الأسبوع 19":["2025-12-28","2025-12-29","2025-12-30","2025-12-31","2026-01-01"]
};

// ----- إنشاء الجدول -----
function createTables() {
  const container = document.getElementById('weeksContainer');
  for (let week in weeks) {
    const tbl = document.createElement('table');
    tbl.id = week;
    const th = document.createElement('tr');
    th.innerHTML = `<th>الفصل</th><th>الطالب</th><th>الحضور</th><th>الواجبات</th><th>المشروعات</th><th>تطبيقات وانشطة</th><th>المشاركة</th>`;
    tbl.appendChild(th);
    for (let cls in students) {
      students[cls].forEach(name=>{
        const tr = document.createElement('tr');
        tr.innerHTML = `<td>${cls}</td><td>${name}</td>
        <td class="toggle" onclick="toggleCell(this)">❌</td>
        <td class="toggle" onclick="toggleCell(this)">❌</td>
        <td class="toggle" onclick="toggleCell(this)">❌</td>
        <td class="toggle" onclick="toggleCell(this)">❌</td>
        <td class="toggle" onclick="toggleCell(this)">❌</td>`;
        tbl.appendChild(tr);
      });
    }
    const btn = document.createElement('button');
    btn.innerText = `تحضير جميع الطلاب - ${week}`;
    btn.onclick = ()=>markAll(tbl);
    container.appendChild(document.createElement('h2')).innerText = week;
    container.appendChild(tbl);
    container.appendChild(btn);
  }
}

function toggleCell(cell){
  cell.innerText = cell.innerText==='❌' ? '✅' : '❌';
}

function markAll(table){
  table.querySelectorAll('td.toggle').forEach(cell=>cell.innerText='✅');
}

// ----- طباعة وتصدير -----
function printPage(){ window.print(); }

function exportExcel(){
  const wb = XLSX.utils.book_new();
  for(let week in weeks){
    const table = document.getElementById(week);
    const ws = XLSX.utils.table_to_sheet(table);
    XLSX.utils.book_append_sheet(wb, ws, week);
  }
  XLSX.writeFile(wb, "تحضير_الطلاب.xlsx");
}

// ----- إدارة -----
function toggleAdmin(){
  const panel = document.getElementById('adminPanel');
  panel.style.display = panel.style.display==='none' ? 'block' : 'none';
}

function loginAdmin(){
  const pass = document.getElementById('adminPass').value;
  if(pass==='1406'){
    document.getElementById('adminActions').style.display='block';
  } else alert('الرقم السري غير صحيح');
}

// ----- تحضير عشوائي -----
function randomizeAll(){
  for(let week in weeks){
    const table = document.getElementById(week);
    table.querySelectorAll('td.toggle').forEach(cell=>{
      cell.innerText = Math.random() > 0.5 ? '✅' : '❌';
    });
  }
}

window.onload = createTables;
</script>

</body>
</html>
