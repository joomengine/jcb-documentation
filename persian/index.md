# خوش آمدید به مرکز یادگیری جوملا کامپوننت بیلدر

## از اینجا شروع کنید

این آموزش‌ها درک عملی از نحوه کارکرد جوملا کامپوننت بیلدر (JCB) را به شما ارائه می‌دهند. مستندات زیر هر راهنما را با ارجاعات زمانی از ویدیوی همراه آن جفت می‌کنند تا بتوانید مستقیماً به لحظه‌ای که نیاز دارید بروید. همانطور که می‌خوانید، توجه ویژه‌ای داشته باشید به اینکه چگونه **ویوهای ادمین سفارشی** (Custom Admin Views) بخش مدیریت جوملا را گسترش می‌دهند و چگونه راهنمای به‌روزشده **پلاگین‌های جوملا** اتوماسیون پس‌زمینه را مستند می‌کند - JCB اکنون نحوه کنار هم آمدن Dynamic Getها، قالب‌ها، لایه‌ها، بلوک‌های کد قابل‌استفاده مجدد و سرویس‌های مبتنی بر پلاگین را ثبت می‌کند تا رابط کاربری کامپوننت شما و منطق رویدادها هماهنگ بمانند.

بازنگری در این پایگاه دانش در جریان است تا زمان‌بندی‌ها اضافه شده و هر متن پیاده‌سازی شود. فصل‌های اول تا هفتم قبلاً شامل رونوشت‌های خام هستند و به طور فعال در حال ویرایش هستند. به‌روزرسانی‌های پیشرفت همچنان در عنوان فصلی که در حال حاضر در حال پالایش است ظاهر می‌شوند و اطلاعیه‌های جدید پس از اتمام یک فصل در انجمن جامعه ارسال می‌شوند.

برای نگاهی اجمالی به کیفیت هدف، فصل کاملاً ویرایش‌شده [انواع فیلد](./Field-Types.md) را بررسی کنید. کار در درس‌های قبلی قبل از ادامه فصل‌های ششم تا هفتم در حال پیشرفت است. هر زمان که به بازآموزی در مورد اینکه تعاریف فیلد چگونه طرح‌واره پایگاه داده، رندرینگ، اعتبارسنجی و اشتراک‌گذاری را هدایت می‌کنند نیاز دارید، آن را با معرفی جدید [فیلدهای JCB](./JCB-Fields.md) جفت کنید.

اگر سوالی دارید یا می‌خواهید مشارکت کنید، به [بحث‌های](https://github.com/orgs/joomengine/discussions) پروژه بپیوندید. همچنین می‌توانید لیست پخش کامل [یوتیوب](https://www.youtube.com/playlist?list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE) آموزش‌های JCB را کاوش کنید.

> 🧱 **به‌روزرسانی: پایه و اساس فیلدهای JCB** – [فصل فیلدهای JCB](./JCB-Fields.md) اکنون نحوه کنترل تعاریف فیلد بر طرح‌واره پایگاه داده، رندرینگ، اعتبارسنجی، اشتراک‌گذاری و نسخه‌سازی مبتنی بر مخزن را ادغام می‌کند تا بتوانید به سرعت جریان کار را به هم تیمی‌های جدید توضیح دهید.
> 🆕 **بررسی عمیق Dynamic Gets** – راهنمای به‌روزشده [Dynamic Get](./dynamicGet.md#overview) اکنون توضیح می‌دهد که چگونه کوئری‌ساز بصری جداول، جوین‌ها، فیلترها، مرتب‌سازی و گروه‌بندی را انتخاب می‌کند، چگونه چند Get در داخل یک ویو ترکیب می‌شوند و چگونه جریان‌های کار Init/Reset/Fork کوئری‌های پیچیده را نسخه-کنترل نگه می‌دارند.
> 📌 **جدید: توضیح معماری ویوی سایت** – با راهنمای بازنگری‌شده [افزودن ویوهای سایت](./Adding-Site-Views-to-a-Component.md) شروع کنید تا ببینید چگونه Dynamic Getها، قالب‌ها، لایه‌ها، مکان‌نماهای کد سفارشی و کتابخانه‌های اختیاری JS/CSS فرانت‌اند شما را مونتاژ می‌کنند. آن را با فصل به‌روزشده [راه‌اندازی قالب](./Template-Setup.md) جفت کنید تا بفهمید این بسته‌بندی‌های ماژولار چگونه تجربه‌های سایت و ادمین را شکل می‌دهند و چگونه آن‌ها را در پروژه‌ها نگهداری کنید.
> 🧱 **جدید: بررسی اجمالی لایه‌های JCB** – [راهنمای اختصاصی لایه‌های JCB](./JCB-Layouts.md) اکنون توضیح می‌دهد که چگونه مخازن لایه را در تب Layouts مقداردهی اولیه، بازنشانی، ارسال (push) و شاخه‌گیری (fork) کنید تا نشانه‌گذاری قابل‌استفاده مجدد شما در کنار کامپوننت‌هایتان نسخه-کنترل بماند.
> 🔌 **جدید: پلاگین‌های جوملا در JCB** – [بررسی اجمالی پلاگین‌های جوملا](./Joomla-Plugins.md) را بخوانید تا یاد بگیرید چگونه منطق رویداد-محور با کامپوننت شما سفر می‌کند. این مقاله اکنون توضیح می‌دهد که چگونه پلاگین‌ها با هر ساخت بسته‌بندی، پیکربندی و ارسال می‌شوند تا بتوانید اتوماسیون را در کنار قابلیت‌های کامپوننت که به آن وابسته‌اند مستند کنید.
> 🧩 **به‌روزرسانی: جریان‌های کار کد سفارشی** – [بررسی اجمالی کدهای سفارشی JCB](./JCB-Custom-Codes.md) جدید خلاصه می‌کند که چگونه قطعه‌کدهای دستی مبتنی بر آرگومان و اتوماسیون مبتنی بر هش مکمل یکدیگرند، از جمله قوانین رمزگذاری، رفت و برگشت رشته‌های زبان و نکات همکاری.
> 📦 **جدید: ماژول‌های جوملا در JCB** – [بررسی اجمالی ماژول‌های جوملا](./Joomla-Modules.md) را کاوش کنید تا بفهمید ماژول‌ها چگونه با کامپوننت‌های شما کامپایل می‌شوند، نسخه‌سازی Reset/Fork را به ارث می‌برند و ویجت‌های قابل‌استفاده مجدد را به موقعیت‌های ماژول جوملا تحویل می‌دهند.

---

### بررسی‌های عمیق قابلیت‌ها

| قابلیت | چرا اهمیت دارد |
| --- | --- |
| [ویوهای مدیریتی JCB](./Features/JCB-Admin-Views.md) | نشان می‌دهد که چگونه JCB یک تعریف داده واحد را به یک تجربه کامل مدیریتی جوملا، کامل با ACL، روابط و صفحات CRUD تولید شده تبدیل می‌کند. |

---

### [کامپوننت‌های جوملا در JCB](./Joomla-Components.md)

| تمرکز | چرا اهمیت دارد |
| --- | --- |
| بررسی اجمالی کامپوننت | خلاصه می‌کند که چگونه ویوهای ادمین، ویوهای سایت، هلپرها، دارایی‌ها و پیکربندی در یک افزونه جوملا کامپایل می‌شوند. |
| مدیریت انتشار | توضیح می‌دهد که چگونه اهداف نسخه، گزارش‌های تغییرات (changelogs) و فراداده‌های توزیع، هر کامپوننت را لنگر می‌اندازند. |
| پیوندهای همکاری | شما را به آموزش‌های عمیق‌تری هدایت می‌کند که تنظیمات کامپوننت، پکیجینگ و جریان‌های کاری تیم را پوشش می‌دهند. |

---

### [ماژول‌های جوملا در JCB](./Joomla-Modules.md)

| تمرکز | چرا اهمیت دارد |
| --- | --- |
| مبانی ماژول | نشان می‌دهد که چگونه ماژول‌ها به کامپوننت‌ها متصل می‌شوند، ساختار جوملا را به ارث می‌برند و در موقعیت‌های ماژول رندر می‌شوند. |
| یکپارچه‌سازی جریان کار | نگهداری Reset/Fork، هدف‌گذاری نسخه و نحوه استفاده مجدد ماژول‌ها از هلپرهای کامپوننت و کد سفارشی را توضیح می‌دهد. |
| برنامه‌ریزی جای‌گذاری | نحوه طراحی پارامترهای مدیر و مستندسازی جای‌گذاری‌های پیشنهادی ماژول را برجسته می‌کند. |

---

### [ساخت کامپوننت "Hello World" با جوملا کامپوننت بیلدر](./Hello-World-with-Joomla-Component-Builder.md)

| زمان‌بندی ویدیو | بخش‌های مستندات |
| --- | --- |
| <ul><li>[ویدیوی آموزشی](https://www.youtube.com/watch?v=1KBBtQUxMTc)</li><li>[01:55](https://youtu.be/1KBBtQUxMTc?t=115)</li><li>[02:46](https://youtu.be/1KBBtQUxMTc?t=166)</li><li>[03:51](https://youtu.be/1KBBtQUxMTc?t=263)</li><li>[04:55](https://youtu.be/1KBBtQUxMTc?t=295)</li><li>[07:25](https://youtu.be/1KBBtQUxMTc?t=445)</li><li>[09:55](https://youtu.be/1KBBtQUxMTc?t=595)</li><li>[12:15](https://youtu.be/1KBBtQUxMTc?t=737)</li><li>[13:34](https://youtu.be/1KBBtQUxMTc?t=814)</li><li>[17:05](https://youtu.be/1KBBtQUxMTc?t=1025)</li><li>[20:30](https://youtu.be/1KBBtQUxMTc?t=1230)</li><li>[24:00](https://youtu.be/1KBBtQUxMTc?t=1440)</li><li>[27:40](https://youtu.be/1KBBtQUxMTc?t=1660)</li><li>[31:10](https://youtu.be/1KBBtQUxMTc?t=1870)</li><li>[34:55](https://youtu.be/1KBBtQUxMTc?t=2095)</li><li>[38:40](https://youtu.be/1KBBtQUxMTc?t=2320)</li></ul> | <ul><li><a href="./Hello-World-with-Joomla-Component-Builder.md#introduction">نمای کلی</a></li><li><a href="./Hello-World-with-Joomla-Component-Builder.md#1-create-the-greeting-field">۱. ساخت فیلد تبریک</a></li><li><a href="./Hello-World-with-Joomla-Component-Builder.md#2-create-an-admin-view">۲. ساخت یک ویوی مدیریتی</a></li><li><a href="./Hello-World-with-Joomla-Component-Builder.md#3-create-the-component-world">۳. ساخت کامپوننت "World"</a></li><li><a href="./Hello-World-with-Joomla-Component-Builder.md#4-compile-and-install-the-component">۴. کامپایل و نصب کامپوننت</a></li><li><a href="./Hello-World-with-Joomla-Component-Builder.md#5-add-frontend-site-views">۵. افزودن ویوهای فرانت‌اند (سایت)</a></li><li><a href="./Hello-World-with-Joomla-Component-Builder.md#6-verify-frontend-and-public-access">۶. بررسی فرانت‌اند و دسترسی عمومی</a></li><li><a href="./Hello-World-with-Joomla-Component-Builder.md#7-link-a-menu-item">۷. پیوند دادن یک آیتم منو</a></li><li><a href="./Hello-World-with-Joomla-Component-Builder.md#8-make-list-items-clickable-using-slug-and-route-helper">۸. قابل کلیک کردن آیتم‌های لیست ...</a></li></ul> |

---

### [راهنمای مقدماتی جوملا کامپوننت بیلدر](./Intro-to-JCB.md)

| زمان‌بندی ویدیو | بخش‌های مستندات |
| --- | --- |
| <ul><li>**مقدمه پایه**</li></ul> | <ul><li><a href="./Intro-to-JCB.md#1-prerequisites-and-mindset">نمای کلی</a></li><li><a href="./Intro-to-JCB.md#2-local-development-environment">۱. محیط توسعه محلی</a></li><li><a href="./Intro-to-JCB.md#3-security-and-offline-preference">۲. امنیت و ترجیح آفلاین</a></li><li><a href="./Intro-to-JCB.md#4-understanding-the-purpose-of-jcb">۳. درک هدف JCB</a></li><li><a href="./Intro-to-JCB.md#5-creating-your-first-component">۴. ساخت اولین کامپوننت</a></li><li><a href="./Intro-to-JCB.md#6-adding-admin-views-and-fields">۵. افزودن ویوهای ادمین و فیلدها</a></li><li><a href="./Intro-to-JCB.md#7-building-frontend-site-views">۶. ساخت ویوهای فرانت‌اند (سایت)</a></li><li><a href="./Intro-to-JCB.md#8-using-dynamic-gets">۷. استفاده از Dynamic GETs</a></li><li><a href="./Intro-to-JCB.md#9-compiling-and-installing-the-component">۸. کامپایل و نصب کامپوننت</a></li><li><a href="./Intro-to-JCB.md#10-contributing-and-feature-requests">۹. مشارکت و درخواست قابلیت</a></li><li><a href="./Intro-to-JCB.md#11-supporting-the-project">۱۰. حمایت از پروژه</a></li><li><a href="./Intro-to-JCB.md#12-summary-complete-workflow">خلاصه - جریان کار کامل</a></li></ul> |

---

### [نصب جوملا کامپوننت بیلدر](./Installation-of-JCB.md)

| زمان‌بندی ویدیو | بخش‌های مستندات |
| --- | --- |
| <ul><li>**دستورالعمل‌های نصب پایه**</li></ul> | <ul><li><a href="./Installation-of-JCB.md#introduction-how-to-build-a-component">نمای کلی</a></li><li><a href="./Installation-of-JCB.md#jcb-is-fully-open-source">۱. JCB کاملاً متن‌باز است</a></li><li><a href="./Installation-of-JCB.md#using-the-compiler">۲. استفاده از کامپایلر</a></li><li><a href="./Installation-of-JCB.md#clear-your-temporary-folder">۳. پاکسازی پوشه موقت</a></li><li><a href="./Installation-of-JCB.md#setting-up-a-blank-test-website">۴. راه‌اندازی یک وب‌سایت تستی خالی</a></li><li><a href="./Installation-of-JCB.md#understanding-the-included-sample-data">۵. درک داده‌های نمونه گنجانده شده</a></li><li><a href="./Installation-of-JCB.md#accessing-database-information-in-your-component">۶. دسترسی به اطلاعات پایگاه داده در کامپوننت</a></li><li><a href="./Installation-of-JCB.md#option-1-reinstall-jcb-to-restore-default-data">۷. گزینه ۱: نصب مجدد JCB برای بازگردانی داده‌های پیش‌فرض</a></li><li><a href="./Installation-of-JCB.md#option-2-restore-sample-data-manually-via-mysql">۸. گزینه ۲: بازگردانی دستی داده‌های نمونه از طریق MySQL</a></li><li><a href="./Installation-of-JCB.md#reinstalling-jcb-after-a-reset">۹. نصب مجدد JCB پس از بازنشانی</a></li><li><a href="./Installation-of-JCB.md#exploring-the-included-field-types">۱۰. کاوش انواع فیلد گنجانده شده</a></li><li><a href="./Installation-of-JCB.md#summary">خلاصه</a></li></ul> |

---

### [برنامه‌ریزی کلی: جوملا کامپوننت بیلدر](./General-Planning.md)

| زمان‌بندی ویدیو | بخش‌های مستندات |
| --- | --- |
| <ul><li>**برنامه‌ریزی کامپوننت**</li></ul> | <ul><li><a href="./General-Planning.md#1-be-prepared-to-build-components">نمای کلی</a></li><li><a href="./General-Planning.md#2-using-demo-components-as-learning-tools">۱. استفاده از کامپوننت‌های دمو به عنوان ابزار یادگیری</a></li><li><a href="./General-Planning.md#3-understanding-the-purpose-of-conventions">۲. درک هدف قراردادها</a></li><li><a href="./General-Planning.md#4-backend-views-and-database-connections">۳. ویوهای بک‌اند و اتصالات پایگاه داده</a></li><li><a href="./General-Planning.md#5-dynamic-get-and-data-relationships">۴. Dynamic Get و روابط داده</a></li><li><a href="./General-Planning.md#6-mapping-views-to-database-tables">۵. مپ کردن ویوها به جدول‌های پایگاه داده</a></li><li><a href="./General-Planning.md#7-using-dynamic-get-for-combined-data">۶. استفاده از Dynamic Get برای داده‌های ترکیبی</a></li><li><a href="./General-Planning.md#8-structuring-fields-and-data-mapping">۷. ساختاردهی فیلدها و مپ کردن داده‌ها</a></li><li><a href="./General-Planning.md#9-adding-compulsory-fields">۸. افزودن فیلدهای اجباری</a></li><li><a href="./General-Planning.md#10-adding-and-creating-views">۹. افزودن و ساخت ویوها</a></li><li><a href="./General-Planning.md#11-adding-fields-to-views">۱۰. افزودن فیلدها به ویوها</a></li><li><a href="./General-Planning.md#12-admin-views-and-field-creation">۱۱. ویوهای ادمین و ساخت فیلد</a></li><li><a href="./General-Planning.md#13-creating-normal-vs-custom-fields">۱۲. ساخت فیلدهای عادی در برابر سفارشی</a></li><li><a href="./General-Planning.md#14-planning-your-component">۱۳. برنامه‌ریزی کامپوننت شما</a></li><li><a href="./General-Planning.md#15-whats-next">۱۴. گام بعدی</a></li></ul> |

---

### فیلدهای JCB

| تمرکز | چرا اهمیت دارد |
| --- | --- |
| مبانی فیلد | خلاصه می‌کند که چگونه یک تعریف فیلد منفرد ذخیره‌سازی، رندرینگ، اعتبارسنجی و دسترسی‌ها را در هر زمینه JCB مدیریت می‌کند. |
| بررسی اجمالی جریان کار | یک مسیر شروع سریع از برنامه‌ریزی تا نگاشت، کامپایل و نگهداری فیلدهای قابل‌استفاده مجدد ارائه می‌دهد. |
| هم‌راستایی مخزن | توضیح می‌دهد که چگونه جریان‌های کار Reset/Fork کتابخانه‌های فیلد مشترک را نسخه-دار و هماهنگ نگه می‌دارند. |

### انواع فیلد در جوملا کامپوننت بیلدر

| زمان‌بندی ویدیو | بخش‌های مستندات |
| --- | --- |
| <ul><li>[01:05](https://youtu.be/OhLzvThDXls?list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=1m5s) **انواع فیلد**</li><li>[01:57](https://youtu.be/OhLzvThDXls?list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE&t=1m57s) **ویوی لیست**</li></ul> | <ul><li><a href="./Field-Types.md#1-overview">نمای کلی</a></li><li><a href="./Field-Types.md#2-creating-field-types">۱. ساخت انواع فیلد</a></li></ul> |

---

## چگونه مستندات را به طور کارآمد مرور کنیم

- **از Start Here + Home با هم استفاده کنید:** Start Here شما را به موضوع مناسب هدایت می‌کند؛ Home هر فصل را با ارجاعات زمانی برای اسکن سریع فهرست می‌کند.
- **نحوه تولید مستندات را درک کنید:** [توسعه با جوملا کامپوننت بیلدر](./Developing-with-Joomla-Component-Builder.md) پروژه پیاده‌سازی را خلاصه می‌کند و نکاتی را برای مطالعه در کنار ویدیوها ارائه می‌دهد.
- **جستجو در مخزن:** از جستجوی ویرایشگر یا ابزارهای خط فرمان (`rg "keyword" english/`) برای یافتن ویژگی‌های خاص، نام فیلدها یا منابع هلپر در فایل‌های Markdown استفاده کنید.
- **از نوار کناری بهره ببرید:** [`_Sidebar.md](./_Sidebar.md) ایندکس Home را منعکس می‌کند و می‌تواند در گیت‌هاب یا نماهای ویکی برای ناوبری دائمی پین شود. از بخش جدید **Features** در آنجا استفاده کنید تا مستقیماً به بررسی‌های عمیقی مانند [ویوهای مدیریتی JCB](./Features/JCB-Admin-Views.md) بپرید.
- **نشانک‌گذاری هاب قابلیت:** [فهرست Features](./Features/README.md) هر قابلیت پرچمدار را با پیوندهایی به راهنماهای تفصیلی فهرست می‌کند تا بتوانید به سرعت به هم‌تیمی‌ها briefing بدهید.
- **پیگیری وضعیت بازنگری:** عنوان‌های فصل شامل یادداشت‌های پیشرفت در طول پروژه ویرایش است. هنگام نیاز به راهنمایی صیقلی، به درس‌های کاملاً ویرایش‌شده مانند [انواع فیلد](./Field-Types.md) اولویت دهید.
- **یادداشت‌های شخصی نگه‌دارید:** یک `docs/notes.md` یا سیستم ردیابی در مخزن پروژه خود نگه دارید تا ثبت کنید چگونه آموزش‌ها را اعمال کرده‌اید - این کار چرخه بازخورد را هنگام عیب‌یابی کوتاه‌تر می‌کند.

---

## از کجا کمک بگیرید و به‌روز بمانید

- **بحث‌های جامعه:** در [انجمن بحث‌های JCB](https://github.org/orgs/joomengine/discussions) به گفتگوهای جاری بپیوندید و سوال بپرسید.
- **پلی‌لیست ویدیو:** [پلی‌لیست کامل آموزش‌های یوتیوب](https://www.youtube.com/playlist?list=PLQRGFI8XZ_wtGvPQZWBfDzzlERLQgpMRE) را در کنار فصل‌های مکتوب دنبال کنید.
- **به‌روزرسانی‌های تست بتا:** برای یادداشت‌های انتشار و فراخوان‌ها برای تست‌کنندگان، [تست بتا](./Beta-Testing.md) را زیر نظر داشته باشید.
- **مشارکت مجدد:** هنگامی که هلپرها، لایه‌ها یا قطعه‌کدها را تهیه می‌کنید، به اشتراک گذاری آن‌ها از طریق جریان کار قطعه‌کدها یا فهرست پکیج لینک‌شده در بالا فکر کنید.

---

## آماده برای گام بعدی خود؟

هر زمان که نیاز دارید جهت خود را مجدداً تنظیم کنید یا به یک هم‌تیمی آموزش دهید، به این صفحه بازگردید. اگر به بازبینی معماری نیاز دارید از گام ۱ شروع کنید، برای بررسی عمیق یک قابلیت به گام ۴ بپرید یا هنگام آماده‌سازی یک انتشار مستقیماً به گام ۶ بروید. ساختن مبارک!
