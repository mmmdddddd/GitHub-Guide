# راهنمای کار با شاخه‌ها (Branching) در Git

**شاخه (Branch)** یک خط توسعه مستقل در پروژه است که به شما اجازه می‌دهد بدون ایجاد اختلال در کدهای اصلی و پایدار پروژه (شاخه `main`)، قابلیت‌های جدید بسازید یا باگ‌ها را رفع کنید.

## ۱. چرا نباید مستقیم روی شاخه `main` تغییرات بدهیم؟
- شاخه `main` باید همیشه نسخه سالم و قابل اجرای پروژه باشد.
- اگر چند نفر هم‌زمان روی `main` تغییر ایجاد کنند، مدیریت خطاها و بازگرداندن کد بسیار دشوار می‌شود.
- کار روی شاخه‌های مجزا امکان بررسی کد (Code Review) را قبل از ادغام فراهم می‌کند.

## ۲. دستورات ضروری مدیریت شاخه‌ها
- **مشاهده لیست شاخه‌های محلی:**
  ```bash
  git branch
  ```
- **مشاهده تمام شاخه‌ها (محلی و GitHub):**
  ```bash
  git branch -a
  ```
- **ساخت یک شاخه جدید:**
  ```bash
  git branch feature/login
  ```
- **جابه‌جایی به یک شاخه دیگر:**
  ```bash
  git checkout feature/login
  git switch feature/login
  ```
- **ساخت شاخه جدید و ورود هم‌زمان به آن:**
  ```bash
  git checkout -b docs/branching
  git switch -c docs/branching
  ```

## ۳. ارسال شاخه به GitHub و حذف شاخه‌های قدیمی
- **اولین ارسال (Push) یک شاخه جدید به GitHub:**
  ```bash
  git push -u origin docs/branching
  ```
- **حذف شاخه محلی پس از ادغام شدن در `main`:**
  ```bash
  git branch -d docs/branching
  ```
- **حذف شاخه از روی GitHub:**
  ```bash
  git push origin --delete docs/branching
  ```

## ۴. استاندارد نام‌گذاری شاخه‌ها در پروژه‌های تیمی
- `feature/...` برای افزودن قابلیت جدید (مثلاً `feature/user-auth`)
- `fix/...` یا `bugfix/...` برای رفع خطا (مثلاً `fix/navbar-alignment`)
- `docs/...` برای تغییر در مستندات (مثلاً `docs/branching`)

## ۵. مثال عملی شروع کار روی یک وظیفه جدید
```bash
git checkout main
git pull origin main
git checkout -b feature/search-bar
git add .
git commit -m "feat: implement search bar component"
git push -u origin feature/search-bar
```