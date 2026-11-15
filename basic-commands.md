# دستورات پایه Git برای مبتدی‌ها

**Git** یک سیستم کنترل نسخه توزیع‌شده (Distributed Version Control System) است که تاریخچه تمام تغییرات فایل‌های پروژه را ذخیره می‌کند تا در هر لحظه بتوانید به نسخه‌های قبلی برگردید یا هم‌زمان با سایر اعضای تیم روی یک پروژه کار کنید.

## ۱. تنظیمات اولیه پس از نصب Git
پس از نصب Git، باید نام و ایمیل خود را معرفی کنید تا تمام ثبت‌ها (Commitها) به نام شما ثبت شوند:

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

برای بررسی صحت تنظیمات می‌توانید دستور زیر را اجرا کنید:
```bash
git config --list
```

## ۲. ایجاد یا دریافت مخزن (Repository)
- **ساخت مخزن جدید در سیستم خودتان:**
  ```bash
  mkdir my-project
  cd my-project
  git init
  ```
- **دریافت (Clone) یک مخزن موجود از GitHub:**
  ```bash
  git clone [https://github.com/username/repository-name.git](https://github.com/username/repository-name.git)
  ```

## ۳. چرخه ثبت تغییرات (Working Directory ← Staging Area ← Repository)
در Git تغییرات قبل از ثبت نهایی وارد فضای میانی (Staging Area) می‌شوند:

1. **بررسی وضعیت فایل‌ها:**
   ```bash
   git status
   ```
2. **افزودن فایل‌ها به Staging Area:**
   ```bash
   git add README.md
   git add .
   ```
3. **ثبت نهایی تغییرات با پیام معنادار:**
   ```bash
   git commit -m "feat: add initial project structure"
   ```