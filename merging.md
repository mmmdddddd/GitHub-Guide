# راهنمای ادغام تغییرات (Merging) و حل Merge Conflict

فرآیند **Merge** یعنی ترکیب کردن تغییرات یک شاخه با شاخه دیگر (معمولاً `main`).

## ۱. انواع اصلی Merge در Git
1. **Fast-Forward Merge:** زمانی رخ می‌دهد که از لحظه ساخت شاخه جدید، هیچ کامیت جدیدی روی شاخه `main` ثبت نشده باشد.
2. **Three-Way Merge:** زمانی رخ می‌دهد که هم روی `main` و هم روی شاخه فرعی کامیت‌های جدیدی ثبت شده باشد و Git یک Merge Commit جدید می‌سازد.

## ۲. دستور ادغام در ترمینال
```bash
git checkout main
git pull origin main
git merge feature/login
```

## ۳. تعارض در ادغام (Merge Conflict) چیست؟
وقتی دو توسعه‌دهنده روی دو شاخه جداگانه، **دقیقاً یک خط مشخص از یک فایل مشترک** را به دو شکل متفاوت تغییر دهند، Git اعلام **Merge Conflict** می‌کند:

```text
<<<<<<< HEAD
Project Status: Under Review
=======
Project Status: Completed
>>>>>>> origin/main
```

## ۴. مراحل گام‌به‌گام حل دستی Merge Conflict
1. دریافت آخرین تغییرات مخزن و تلاش برای ادغام:
   ```bash
   git fetch origin
   git merge origin/main
   ```
2. باز کردن فایل دارای تعارض در ویرایشگر کد و بررسی هر دو تغییر.
3. حذف خطوط نشانگر (`<<<<<<<`، `=======`، `>>>>>>>`) و نگه داشتن متن نهایی مورد توافق.
4. ثبت نهایی حل تعارض:
   ```bash
   git add README.md
   git commit -m "fix: resolve merge conflict in README.md"
   git push
   ```