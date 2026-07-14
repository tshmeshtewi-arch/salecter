# إعداد المشروع

## 1. API المنتجات (لا يحتاج أي إعداد)
التطبيق يجيب المنتجات من:
https://fakestoreapi.com/

هذا API **مجاني وعمومي**، ماخصكش تسوي حساب ولا تجيب مفتاح، خدام أوتوماتيكياً.

## 2. Firebase (خاص بتسجيل الدخول والحساب)
صفحة اللوگان وصفحة الحساب (تعديل الاسم، الصورة، العنوان، حذف الحساب...) خاصهم Firebase. باش تخدم:

1. روح لـ https://console.firebase.google.com وسوي مشروع جديد (مجاني).
2. داخل المشروع، ضيف تطبيق Android بهاذ الـ package name بالضبط:
   `com.ahmetocak.shoppingapp`
3. فعّل من "Build" هاذ الخدمات:
   - Authentication (فعّل طريقة Email/Password)
   - Firestore Database
   - Storage
4. Firebase غادي يعطيك ملف اسمو **`google-services.json`** — حمّلو، وحطو هنا بالضبط:
   ```
   app/google-services.json
   ```
   (يعني جوج المجلد `app/`، حدا `build.gradle.kts` ديال الموديول).
5. من "Project settings" ديال Firebase، خد هاذ 3 قيم وحطهم فملف `local.properties` (فالجذر ديال المشروع، حدا `gradlew`) — كاين نموذج جاهز فملف `local.properties.example`، بدّل الاسم لـ `local.properties` وعمر القيم:
   ```
   API_KEY=...
   PROJECT_ID=...
   APPLICATION_ID=...
   ```

⚠️ ملف `local.properties` ماكايتبعتش لـ GitHub عادةً (محمي فـ `.gitignore`)، وملف `google-services.json` فيه معلومات مشروعك. إيلا الريبو ديالك **خاص/private**، تنجم تزيدهم مباشرة للريبو باش الـ GitHub Actions يبنيهم معاه. إيلا الريبو **عمومي**، الأحسن تزيدهم كـ GitHub Secrets وتكتب خطوة فـ workflow تنشئهم قبل البناء (نگولها ليك إيلا بغيتي).

## 3. البناء بدون Firebase
إيلا مازال ماحطيتيش `google-services.json`، التطبيق غادي يبني بلا مشاكل (APK كايخرج عادي)، غير صفحة اللوگان وصفحة الحساب ماغاديش تخدم حتى تزيد الملف.
