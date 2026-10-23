# Git & GitHub — Practical Guide
## راهنمای کاربردی Git و GitHub

این فایل خلاصه دستورات و مفاهیمی است که در بخش ۵ یاد گرفتیم.

---

# 1. تفاوت Git و GitHub

Git:
ابزاری برای مدیریت نسخه‌ها و تاریخچه تغییرات پروژه روی کامپیوتر.

GitHub:
سرویسی آنلاین برای نگهداری Repository و همکاری روی پروژه‌ها.

Repository:
مخزن پروژه که تاریخچه Commitها را نگهداری می‌کند.

Commit:
ثبت یک نسخه از تغییرات در تاریخچه پروژه.

Branch:
شاخه‌ای جدا برای توسعه یا آزمایش تغییرات.

Remote:
آدرس مخزن آنلاین متصل به پروژه محلی.

---

# 2. تنظیم اولیه Git

## بررسی نصب Git

git --version

کاربرد:
نمایش نسخه Git نصب‌شده روی سیستم.

## تنظیم نام کاربر

git config --global user.name "Your Name"

کاربرد:
تعیین نامی که در Commitها ثبت می‌شود.

## تنظیم ایمیل

git config --global user.email "you@example.com"

کاربرد:
تعیین ایمیلی که در مشخصات Commitها ثبت می‌شود.

## مشاهده تنظیمات

git config --global --list

کاربرد:
نمایش تنظیمات سراسری Git.

نکته:
گزینه --global باعث می‌شود تنظیمات برای تمام Repositoryهای کاربر
در همان سیستم اعمال شوند.

---

# 3. ساخت Repository

## ساخت Repository جدید

git init

کاربرد:
فعال کردن Git برای پروژه فعلی و ایجاد تاریخچه محلی.

## بررسی وضعیت پروژه

git status

کاربرد:
نمایش فایل‌های تغییرکرده، فایل‌های جدید و وضعیت Stage.

## نمایش خلاصه وضعیت

git status --short

کاربرد:
نمایش خلاصه و کوتاه وضعیت فایل‌ها.

نمونه:
M main.py

یعنی فایل main.py تغییر کرده است.

---

# 4. چرخه اصلی کار با Git

روند معمول:

ویرایش فایل
    ↓
git status
    ↓
git add
    ↓
git commit

## آماده‌سازی یک فایل

git add main.py

کاربرد:
قرار دادن تغییرات فایل main.py در Stage.

## آماده‌سازی تمام تغییرات

git add -A

کاربرد:
آماده‌سازی تمام تغییرات، از جمله فایل‌های جدید،
تغییرات فایل‌ها و حذف فایل‌ها.

## ثبت Commit

git commit -m "Add new feature"

کاربرد:
ثبت تغییرات Stage‌شده در تاریخچه Git.

گزینه -m برای نوشتن پیام Commit است.

نکته:
git add تغییرات را آماده ثبت می‌کند.
git commit تغییرات Stage‌شده را در تاریخچه ثبت می‌کند.

---

# 5. فایل .gitignore

فایل .gitignore مشخص می‌کند چه فایل‌ها و پوشه‌هایی
معمولاً نباید توسط Git ردیابی شوند.

محتوای نمونه:

.idea/
.venv/
__pycache__/
*.pyc

معنی:

.idea/
نادیده گرفتن تنظیمات محلی PyCharm.

.venv/
نادیده گرفتن محیط مجازی Python.

__pycache__/
نادیده گرفتن پوشه‌های کش Python.

*.pyc
نادیده گرفتن فایل‌های کامپایل‌شده Python.

نکته:
.gitignore به‌طور خودکار فایل‌هایی را که قبلاً تحت ردیابی Git
قرار گرفته‌اند از ردیابی خارج نمی‌کند.

---

# 6. مشاهده تغییرات و تاریخچه

## مشاهده تفاوت فایل‌ها

git diff

کاربرد:
نمایش تغییرات ثبت‌نشده در Stage.

## مشاهده تغییرات Stage‌شده

git diff --staged

کاربرد:
نمایش تفاوت‌هایی که برای Commit آماده شده‌اند.

## مشاهده تاریخچه

git log

کاربرد:
نمایش تاریخچه Commitها.

## تاریخچه خلاصه

git log --oneline

کاربرد:
نمایش هر Commit در یک خط.

## نمایش پنج Commit آخر

git log --oneline -5

## نمایش جزئیات یک Commit

git show

کاربرد:
نمایش اطلاعات و تغییرات یک Commit مشخص؛ بدون شناسه،
معمولاً آخرین Commit نمایش داده می‌شود.

## نمایش بدون Pager

git --no-pager show

کاربرد:
نمایش مستقیم خروجی در ترمینال، بدون باز کردن نمایشگر متنی.

نکته:
در خروجی git log یا git show اگر وارد Pager شدی،
معمولاً با کلید q از آن خارج می‌شوی.

---

# 7. لغو تغییرات

## برگرداندن تغییرات ثبت‌نشده فایل

git restore main.py

کاربرد:
برگرداندن فایل به وضعیت نسخه Stage‌شده؛
اگر تغییرات Stage نشده باشند، معمولاً به آخرین نسخه ثبت‌شده برمی‌گردد.

هشدار:
تغییرات حذف‌شده ممکن است قابل بازیابی نباشند.

## خارج کردن فایل از Stage

git restore --staged main.py

کاربرد:
خارج کردن تغییرات فایل از Stage، بدون پاک کردن خود تغییرات.

تفاوت:

git restore main.py
تغییرات ثبت‌نشده فایل را برمی‌گرداند.

git restore --staged main.py
تغییرات را از Stage خارج می‌کند.

---

# 8. Branch

Branch یعنی شاخه‌ای جدا برای توسعه تغییرات.

## مشاهده شاخه‌های محلی

git branch

کاربرد:
نمایش Branchهای محلی.

علامت * شاخه فعلی را مشخص می‌کند.

## مشاهده تعداد شاخه‌های محلی در PowerShell

git branch --list | Measure-Object

## مشاهده شاخه فعلی

git branch --show-current

## ساخت شاخه و ورود به آن

git switch -c feature-test

کاربرد:
ساخت Branch جدید به نام feature-test
و جابه‌جایی به آن.

گزینه -c مخفف create است.

## جابه‌جایی به شاخه موجود

git switch main

کاربرد:
رفتن به شاخه main.

## حذف شاخه محلی ادغام‌شده

git branch -d feature-test

کاربرد:
حذف شاخه محلی، در صورتی که Git اجازه دهد
و تغییرات آن از دست نروند.

## بررسی شاخه‌های ادغام‌شده

git branch --merged main

---

# 9. Merge

Merge یعنی ادغام تغییرات یک شاخه در شاخه فعلی.

مثلاً:

git switch main
git merge feature-test

معنی:

1. رفتن به شاخه main.
2. ادغام تغییرات feature-test در main.

نکته مهم:
Merge را در شاخه‌ای اجرا می‌کنیم که می‌خواهیم
تغییرات شاخه دیگر وارد آن شود.

---

# 10. Merge Conflict

Conflict وقتی رخ می‌دهد که Git نتواند تغییرات دو شاخه
را به‌صورت خودکار با هم ادغام کند.

نمونه متن Conflict:

<<<<<<< HEAD
print("Hello from main")
=======
print("Hello from feature")
>>>>>>> feature-test

معنی:

<<<<<<< HEAD
شروع نسخه شاخه فعلی.

=======
جداکننده دو نسخه.

>>>>>>> feature-test
پایان نسخه شاخه دیگر.

مراحل حل Conflict:

1. فایل را در ویرایشگر باز کن.
2. متن نهایی صحیح را انتخاب یا ترکیب کن.
3. تمام نشانه‌های Conflict را حذف کن.
4. فایل را ذخیره کن.
5. تغییرات حل‌شده را Stage کن.
6. Commit ادغام را کامل کن.

دستورات معمول:

git add main.py
git commit -m "Resolve merge conflict"

نکته:
قبل از ثبت، مطمئن شو خطوط نشانه‌گذاری Conflict
از کد حذف شده‌اند.

---

# 11. اتصال پروژه به GitHub

## اضافه کردن مخزن آنلاین

git remote add origin https://github.com/USERNAME/PROJECT.git

کاربرد:
اتصال پروژه محلی به Repository آنلاین.

به‌جای آدرس نمونه، آدرس واقعی Repository خودت را قرار بده.

origin نام رایج برای Remote اصلی پروژه است.

## مشاهده Remoteها

git remote -v

کاربرد:
نمایش آدرس‌های دریافت و ارسال مخزن آنلاین.

---

# 12. Push و Pull

## ارسال Commitها به GitHub

git push -u origin main

کاربرد:
ارسال Commitهای شاخه main به GitHub.

گزینه -u ارتباط شاخه محلی با شاخه آنلاین را
برای دستورات بعدی تنظیم می‌کند.

پس از تنظیم این ارتباط، معمولاً کافی است بنویسی:

git push

## دریافت تغییرات از GitHub

git pull

کاربرد:
دریافت تغییرات Remote و ادغام آن‌ها در شاخه فعلی،
مطابق تنظیمات Pull.

## دریافت تغییرات از یک Remote و Branch مشخص

git pull origin main

کاربرد:
دریافت و ادغام تغییرات شاخه main از Remote به نام origin.

---

# 13. Clone

Clone یعنی دریافت یک Repository از GitHub یا Remote دیگر،
همراه با تاریخچه Git آن.

دستور نمونه:

git clone https://github.com/USERNAME/PROJECT.git

با تعیین نام پوشه:

git clone https://github.com/USERNAME/PROJECT.git PROJECT-copy

نکته:
Clone یک کپی جدید از پروژه ایجاد می‌کند و Repository
اصلی روی GitHub را حذف یا تغییر نمی‌دهد.

برای مخزن دیگران، بدون اجازه تغییرات را به Remote آن‌ها Push نکن.

---

# 14. Fetch و Prune

## دریافت اطلاعات جدید Remote

git fetch

کاربرد:
دریافت اطلاعات جدید از Remote بدون ادغام خودکار
آن تغییرات در شاخه فعلی.

## پاک‌سازی ارجاع شاخه‌های حذف‌شده Remote

git fetch --prune

کاربرد:
به‌روزرسانی اطلاعات Remote و پاک‌کردن ارجاع محلی
به شاخه‌های آنلاینی که دیگر وجود ندارند.

---

# 15. کار با Pull Request در GitHub

Pull Request یا PR یعنی درخواست بررسی تغییرات یک شاخه
و پیشنهاد ادغام آن در شاخه دیگر.

روند معمول:

1. ساخت Branch جدید.
2. انجام تغییرات.
3. Commit کردن تغییرات.
4. Push کردن Branch به GitHub.
5. ساخت Pull Request.
6. بررسی تغییرات.
7. Merge کردن Pull Request.

نمونه دستورات محلی:

git switch -c docs-practice

git add notes.md
git commit -m "Add practice notes"

git push -u origin docs-practice

سپس در GitHub یک Pull Request بساز:

base: main
compare: docs-practice

بعد از بررسی و Merge در GitHub، نسخه محلی را به‌روز کن:

git switch main
git pull

حذف شاخه محلی ادغام‌شده:

git branch -d docs-practice

اگر شاخه Remote دیگر لازم نیست و کارش تمام شده:

git push origin --delete docs-practice

سپس:

git fetch --prune

---

# 16. آخرین بررسی پروژه

## وضعیت فایل‌ها

git status

اگر نوشته شود:

nothing to commit, working tree clean

یعنی تغییر ثبت‌نشده یا Stage‌شده‌ای باقی نمانده است.

## مشاهده شاخه‌ها

git branch -a

کاربرد:
نمایش شاخه‌های محلی و شاخه‌های Remote شناخته‌شده.

## بررسی تاریخچه

git log --oneline

کاربرد:
نمایش Commitهای ثبت‌شده.

---

# 17. روند پیشنهادی روزمره

برای تغییر ساده روی شاخه اصلی:

git status
git pull
# Edit files
git diff
git add -A
git diff --staged
git commit -m "Describe the change"
git push
git status

برای توسعه یک قابلیت جدید:

git switch main
git pull
git switch -c feature-name

# Edit files

git status
git add -A
git commit -m "Add feature"
git push -u origin feature-name

سپس در GitHub یک Pull Request بساز و پس از بررسی،
تغییرات را Merge کن.

---

# 18. نکات مهم

- Git محلی است؛ GitHub مخزن آنلاین است.
- هر Commit فقط تغییراتی را ثبت می‌کند که Stage شده‌اند.
- پیش از Commit، git diff --staged را بررسی کن.
- پیش از دستورهای حذف یا برگرداندن تغییرات، وضعیت را بررسی کن.
- تغییرات مهم را بدون دلیل حذف نکن.
- اطلاعات حساس مانند رمز، Token و کلیدهای API را Commit نکن.
- فایل‌های محیط مجازی معمولاً نباید وارد Repository شوند.
- نام Commit باید کوتاه و توصیفی باشد.
- برای هر قابلیت مستقل، ساخت Branch جدا می‌تواند مفید باشد.
- قبل از تحویل پروژه، کد را اجرا و نتیجه را بررسی کن.

پایان راهنمای Git و GitHub