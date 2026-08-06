# VFS Appointment Bot (نسخه‌ی فارسی)

[![GitHub License](https://img.shields.io/github/license/peymanpasbani/vfs-appointment-bot-fa)](https://github.com/peymanpasbani/vfs-appointment-bot-fa/blob/main/LICENSE)
[![GitHub Release](https://img.shields.io/github/v/release/peymanpasbani/vfs-appointment-bot-fa?logo=GitHub)](https://github.com/peymanpasbani/vfs-appointment-bot-fa/releases)
[![GitHub forks](https://img.shields.io/github/forks/peymanpasbani/vfs-appointment-bot-fa)](https://github.com/peymanpasbani/vfs-appointment-bot-fa/forks)
[![GitHub Repo stars](https://img.shields.io/github/stars/peymanpasbani/vfs-appointment-bot-fa)](https://github.com/peymanpasbani/vfs-appointment-bot-fa/stargazers)
[![GitHub Issues or Pull Requests](https://img.shields.io/github/issues/peymanpasbani/vfs-appointment-bot-fa)](https://github.com/peymanpasbani/vfs-appointment-bot-fa/issues)

> 🔀 این مخزن یک **فورک با ترجمه و مستندسازی فارسی** از پروژه‌ی متن‌باز [vfs-appointment-bot](https://github.com/ranjan-mohanty/vfs-appointment-bot) نوشته‌ی **Ranjan Mohanty** است. منطق اصلی برنامه از پروژه‌ی مرجع گرفته شده؛ برای جزئیات نگاه کنید به [NOTICE.md](./NOTICE.md).
>
> نگهدارنده‌ی این فورک: **Peyman Pasbani** — تلگرام: [@peyman_s110](https://t.me/peyman_s110) — ایکس: [@peymanpasbani](https://x.com/peymanpasbani)

این اسکریپت پایتون (**vfs-appointment-bot**) به‌صورت خودکار وجود نوبت‌های خالی در پورتال VFS Global برای کشور مشخص‌شده رو بررسی می‌کنه و در صورت پیدا شدن نوبت، از طریق کانال‌های مختلف (ایمیل، تلگرام، پیامک/تماس با Twilio) به شما اطلاع می‌ده.

## نصب

اسکریپت `vfs-appointment-bot` رو می‌شه با دو روش نصب کرد:

### ۱. نصب با pip

روش پیشنهادی برای نصب:

1. **ساخت محیط مجازی (پیشنهادی):**

   ```bash
   python3 -m venv venv
   ```

   این دستور یک محیط مجازی به اسم `venv` می‌سازه تا وابستگی‌های پروژه از نصب پایتون سیستم جدا بمونن (**پیشنهاد می‌شه**).

2. **فعال‌سازی محیط مجازی:**

   **لینوکس/مک:**

   ```bash
   source venv/bin/activate
   ```

   **ویندوز:**

   ```bash
   venv\Scripts\activate
   ```

3. **نصب با pip:**

   ```bash
   pip install vfs-appointment-bot
   ```

   این دستور پکیج `vfs-appointment-bot` و وابستگی‌هاش رو دانلود و نصب می‌کنه.

### ۲. نصب دستی

برای نصب به روش دیگه، می‌تونید سورس رو از مخزن پروژه کلون کرده و به‌صورت دستی نصب کنید.

1. **کلون کردن مخزن:**

   ```bash
   git clone https://github.com/peymanpasbani/vfs-appointment-bot-fa
   ```

2. **رفتن به پوشه‌ی پروژه:**

   ```bash
   cd vfs-appointment-bot-fa
   ```

3. **ساخت محیط مجازی (پیشنهادی):**

   ```bash
   python3 -m venv venv
   ```

4. **فعال‌سازی محیط مجازی:**

   **لینوکس/مک:**

   ```bash
   source venv/bin/activate
   ```

   **ویندوز:**

   ```bash
   venv\Scripts\activate
   ```

5. **نصب وابستگی‌ها:**

   ```bash
   pip install poetry
   poetry install
   ```

6. **نصب وابستگی‌های Playwright:**

   ```bash
   playwright install
   ```

## پیکربندی

1. فایل نمونه‌ی [`config/config.ini`](https://raw.githubusercontent.com/peymanpasbani/vfs-appointment-bot-fa/main/config/config.ini) رو دانلود کنید:

   ```bash
   curl -L https://raw.githubusercontent.com/peymanpasbani/vfs-appointment-bot-fa/main/config/config.ini -o config.ini
   ```

2. اطلاعات ورود VFS و تنظیمات کانال اطلاع‌رسانی رو به‌روزرسانی کنید. برای جزئیات به بخش [کانال‌های اطلاع‌رسانی](#کانالهای-اطلاعرسانی) مراجعه کنید.
3. مسیر فایل کانفیگ رو در متغیر محیطی `VFS_BOT_CONFIG_PATH` قرار بدید:

   ```bash
   export VFS_BOT_CONFIG_PATH=<your-config-path>/config.ini
   ```

**اگر اسکریپت رو با کلون کردن مخزن نصب کردید (نصب دستی)**، می‌تونید مستقیماً مقادیر رو در `config/config.ini` ویرایش کنید.

## استفاده

1. **آرگومان خط فرمان:**

   اسکریپت نیاز داره کد کشور مبدأ و مقصد ([بر اساس استاندارد ISO 3166-1 alpha-2](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Officially_assigned_code_elements)) با گزینه‌های `-sc` یا `--source-country-code` و `-dc` یا `--destination-country-code` داده بشه.

2. **اجرای اسکریپت:**

   دو راه برای وارد کردن مشخصات نوبت وجود داره:

   - **پاسخ به پرامپت‌های برنامه (پیشنهادی):**

     ```bash
     vfs-appointment-bot -sc IN -dc DE
     ```

     اسکریپت ازتون می‌خواد پارامترهای موردنیاز نوبت رو برای کشور مشخص‌شده وارد کنید.

   - **استفاده از `-ap` یا `--appointment-params`:**

     مشخصات نوبت رو به‌صورت کلید-مقدار و جدا‌شده با کاما (**نه فاصله**) وارد کنید:

     ```bash
     vfs-appointment-bot -sc IN -dc DE -ap visa_center=X,visa_category=Y,visa_sub_category=Z
     ```

   اسکریپت بعد از اون به سایت VFS Global برای کشور مشخص‌شده وصل می‌شه، با پارامترهای داده‌شده دنبال نوبت خالی می‌گرده و در صورت پیدا شدن (بسته به تنظیمات شما) اعلان ارسال می‌کنه.

## کانال‌های اطلاع‌رسانی

در حال حاضر سه کانال اطلاع‌رسانی پشتیبانی می‌شه:

- **ایمیل:** ارسال اعلان از طریق حساب جیمیل.
- **Twilio (پیامک و تماس صوتی):** اعلان از طریق پیامک متنی و تماس تلفنی با استفاده از سرویس Twilio.
- **تلگرام:** ارسال اعلان مستقیم به حساب تلگرام شما از طریق یک بات.

**تنظیم اعلان‌ها:**

**ایمیل:**

1. **حساب ایمیل:** به یک **حساب جیمیل** برای ارسال اعلان نیاز دارید.
2. **رمز عبور اپلیکیشن:** به‌جای رمز عبور معمولی، یک App Password برای حساب جیمیل بسازید. راهنمای گوگل برای ساخت App Password: [https://support.google.com/accounts/answer/185833?hl=en](https://support.google.com/accounts/answer/185833?hl=en)
3. **فایل پیکربندی:** موارد زیر رو در `config.ini` وارد کنید:

   - **`email` (الزامی):** آدرس جیمیل شما.
   - **`password` (الزامی):** App Password ساخته‌شده.

**Twilio:**

1. **ساخت حساب Twilio (در صورت نیاز):** در [https://www.twilio.com/en-us](https://www.twilio.com/en-us) ثبت‌نام کنید تا اطلاعات حساب و شماره تلفن بگیرید.
2. **دریافت اطلاعات حساب:** SID حساب، auth token و شماره‌های تلفن رو از داشبورد Twilio پیدا کنید.
3. **فایل پیکربندی:** موارد زیر رو وارد کنید:

   - `auth_token` (الزامی): توکن احراز هویت Twilio
   - `account_sid` (الزامی): SID حساب Twilio
   - `sms_enabled` (اختیاری): فعال‌سازی اعلان پیامکی (پیش‌فرض: True)
   - `call_enabled` (اختیاری): فعال‌سازی اعلان تماس صوتی (پیش‌فرض: False)
   - `url` (اختیاری): آدرس API توییلیو (فقط در صورت فعال بودن تماس لازمه)
   - `to_num` (الزامی): شماره تلفن گیرنده‌ی اعلان
   - `from_num` (الزامی): شماره تلفن Twilio که برای ارسال استفاده می‌شه

**تلگرام:**

1. **ساخت بات تلگرام:** به [https://telegram.me/BotFather](https://telegram.me/BotFather) برید و طبق راهنما یک بات بسازید تا توکن بات رو بگیرید.
2. **فایل پیکربندی:** موارد زیر رو وارد کنید:

   - **`bot_token` (الزامی):** توکن بات تلگرام که از BotFather گرفتید.
   - **`chat_id` (اختیاری):** شناسه‌ی چت تلگرامی که می‌خواید اعلان‌ها اونجا ارسال بشه. اگه خالی بذارید، بات به همون چتی که ازش پیام گرفته پاسخ می‌ده. برای پیدا کردن chat ID، یک گروه فقط با خودتون بسازید و از دستور `/my_id` داخل بات استفاده کنید.

## کشورها و پارامترهای نوبت پشتیبانی‌شده

جدول زیر کشورهای پشتیبانی‌شده و پارامترهای مربوط به نوبت‌شون رو نشون می‌ده:

| کشور                        | پارامترهای نوبت                                               |
| --------------------------- | -------------------------------------------------------------- |
| هند (IN) - آلمان (DE)       | visa_category, visa_sub_category, visa_center                  |
| عراق (IQ) - آلمان (DE)      | visa_category, visa_sub_category, visa_center                  |
| مراکش (MA) - ایتالیا (IT)   | visa_category, visa_sub_category, visa_center, payment_mode    |
| آذربایجان (AZ) - ایتالیا (IT) | visa_category, visa_sub_category, visa_center                |

**نکات:**

- پارامترهای نوبت ممکنه بسته به کشور و نوع ویزا فرق کنه. همیشه برای اطلاعات به‌روز به سایت VFS Global مراجعه کنید.

## مشکلات شناخته‌شده

**۱. خطای ورود بعد از درخواست‌های مکرر:**  
اگه بات با فرکانس بالا به سایت VFS درخواست ورود بفرسته، سیستم VFS ممکنه به‌خاطر شک به اتومیشن، دسترسی رو موقتاً مسدود کنه.

- **راه‌حل موقت:**
  - **کاهش فرکانس درخواست:** فاصله‌ی زمانی بین اجراهای بات رو بیشتر کنید تا مکانیزم بلاک VFS فعال نشه. این فاصله رو می‌تونید در تنظیمات یا کد تغییر بدید.
  - **تلاش مجدد بعد از ۲ ساعت:** اگه با خطای ورود مواجه شدید، حداقل ۲ ساعت صبر کنید و دوباره امتحان کنید. بلاک VFS معمولاً توی همین بازه رفع می‌شه.

**۲. تأیید کپچا:**  
سایت VFS در مرحله‌ی ورود، تأیید کپچا می‌خواد و بات در حال حاضر حل‌کننده‌ی داخلی کپچا نداره.

- **راه‌حل موقت:**
  - **صبر و تلاش مجدد:** گاهی کپچا به‌خاطر مشکلات موقت سایت ظاهر می‌شه. کمی صبر کنید و دوباره امتحان کنید.
  - **تلاش با مرورگر دیگه:** کپچا معمولاً در فایرفاکس به‌صورت خودکار حل می‌شه. اگه بازم شکست خورد، در `config.ini` مقدار `browser_type` رو به `"chromium"` یا `"webkit"` تغییر بدید.

**نکته:** به‌طور مداوم در حال بهبود عملکرد بات هستیم. آپدیت‌های بعدی ممکنه شامل حل خودکار کپچا هم بشه.

## توسعه‌ی پشتیبانی کشورهای بیشتر

این اسکریپت در حال حاضر برای سایت VFS Global مربوط به آلمان طراحی شده. با تغییر اسکریپت برای مدیریت تفاوت‌های احتمالی در ساختار سایت و پارامترهای موردنیاز، احتمالاً می‌شه پشتیبانی کشورهای دیگه رو هم اضافه کرد.

## مشارکت

از مشارکت شما برای بهتر شدن این پروژه استقبال می‌کنیم:

- **گزارش باگ:** اگه با باگ یا مشکلی مواجه شدید، توی مخزن پروژه issue بسازید.
- **پیشنهاد بهبود:** ایده‌ای برای کاربرپسندتر یا کامل‌تر شدن اسکریپت دارید؟ خوشحال می‌شیم issue یا pull request بسازید.
- **ارسال Pull Request:** اگه تغییری در کد دادید که فکر می‌کنید به پروژه کمک می‌کنه، یک pull request بفرستید.

## سپاسگزاری و منبع

این پروژه بر پایه‌ی کار متن‌باز [ranjan-mohanty/vfs-appointment-bot](https://github.com/ranjan-mohanty/vfs-appointment-bot) ساخته شده. تمام حقوق مربوط به منطق اصلی برنامه متعلق به نویسنده‌ی اصلیه. جزئیات بیشتر در [NOTICE.md](./NOTICE.md).

## سلب مسئولیت

این اسکریپت به همون شکلی که هست ارائه می‌شه و هیچ وابستگی رسمی به VFS Global نداره. مسئولیت رعایت شرایط و قوانین VFS Global هنگام استفاده از این اسکریپت بر عهده‌ی خود کاربره. ممکنه ساختار سایت و مکانیزم‌های نوبت‌دهی در طول زمان تغییر کنه.
