# 🦷 DentoCrown — نظام التحقق من هوية الطالب
## دليل الإعداد الكامل | Kurulum Kılavuzu

---

## 📋 ما تحتاجه قبل البدء

| المتطلب | الرابط | مجاني؟ |
|---|---|---|
| حساب Google | google.com | ✅ |
| Google AI Studio (Gemini API Key) | aistudio.google.com/app/apikey | ✅ |
| حساب GitHub (للاستضافة) | github.com | ✅ |

---

## 🚀 الخطوة 1 — رفع الملفات على GitHub Pages

### أ) إنشاء مستودع جديد
1. اذهب إلى github.com/new
2. اسم المستودع: dentocrown-verify
3. اجعله **Public** (عام) حتى تعمل GitHub Pages
4. اضغط **Create repository**

### ب) ارفع هذه الملفات:
- index.html
- LogoFinal-(1).png
- LogoFinal (1).png
- cover2 (2).png

### ج) تفعيل GitHub Pages
1. Settings → Pages
2. Source: Deploy from a branch
3. Branch: main → / (root)
4. Save
5. رابطك سيكون:
   https://[اسم_حسابك].github.io/dentocrown-verify/

---

## 🤖 الخطوة 2 — إعداد Google Apps Script

### أ) احصل على Gemini API Key (مجاني)
1. اذهب إلى: https://aistudio.google.com/app/apikey
2. اضغط Create API Key
3. انسخ المفتاح

### ب) إنشاء Apps Script
1. اذهب إلى: https://script.google.com
2. اضغط + New project
3. احذف الكود وألصق محتوى ملف Code.gs
4. عدّل هذه الإعدادات في أعلى الملف:

   GEMINI_API_KEY: 'الصق_مفتاح_Gemini_هنا',
   ADMIN_EMAIL:    'بريد_الفريق@gmail.com',
   WHATSAPP_INVITE: 'https://chat.whatsapp.com/رابط_مجموعتك',

### ج) نشر Script كـ Web App
1. Deploy → New deployment
2. ⚙️ → Web app
3. Execute as: Me
4. Who has access: Anyone
5. Deploy → اقبل الأذونات
6. انسخ رابط الـ Web App

---

## 🔗 الخطوة 3 — ربط الموقع بالخادم

في ملف index.html، ابحث عن:
   const APPS_SCRIPT_URL = 'REPLACE_WITH_YOUR_APPS_SCRIPT_URL';

استبدلها بـ:
   const APPS_SCRIPT_URL = 'https://script.google.com/macros/s/AKfyc.../exec';

ثم ارفع الملف المحدَّث إلى GitHub.

---

## ✅ الخطوة 4 — اختبار النظام

افتح رابط موقعك وجرّب النموذج.

النتائج المتوقعة:
- مستند صحيح  → إيميل للفريق + إيميل مبروك للطالب
- مستند خاطئ  → إيميل للفريق + إيميل رفض للطالب

---

## 📊 الحدود المجانية

| الخدمة              | الحد اليومي        |
|---------------------|--------------------|
| Gemini 2.0 Flash    | 1,500 طلب / يوم   |
| Google Apps Script  | 6 ساعات تشغيل     |
| Gmail               | 100 إيميل / يوم    |
| GitHub Pages        | غير محدود          |

---

## 🔒 ضمانات الخصوصية

- المستندات لا تُحفظ في أي مكان
- تُرسل مباشرة للذكاء الاصطناعي وتُحذف فور التحليل
- يُحفظ فقط: الاسم، الجامعة، رقم التحقق، ونتيجة القرار

---

## 📱 الرابط الذي ترسله للطلاب

https://[اسم_حسابك].github.io/dentocrown-verify/

---

## 🆘 مشاكل شائعة

| المشكلة                    | الحل                                            |
|----------------------------|-------------------------------------------------|
| خطأ في الاتصال             | تأكد أن Apps Script منشور كـ Anyone             |
| لا تصل إيميلات             | تأكد من صحة ADMIN_EMAIL في الإعدادات            |
| AI لم يتعرف على المستند    | الصورة ضبابية — اطلب من الطالب إعادة التصوير   |
