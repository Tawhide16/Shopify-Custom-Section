# Shopify Custom Section

## 🛍 Custom Product Section

### 📌 Product Size Selection → Auto Add to Cart

When a user clicks on a product size inside the product tabs, the corresponding product variant is automatically added to the cart automatically.

### 🔗 Live Website
👉 https://your-website-link-here.com
![Image Alt](https://github.com/Tawhide16/Shopify-Custom-Section/blob/a2548db71a635942b5c3bdaf15ee88efdecd7ef2/Screenshot%202026-03-26%20174421.png)

### 🖼 Demo Preview
![Product Size Auto Add to Cart](https://i.ibb.co/YOUR-IMAGE-LINK-HERE.png)





















# 🟩 GitHub Contribution Graph Fix Guide

> **সমস্যা:** Code push হচ্ছে কিন্তু GitHub profile-এ সবুজ বক্স fill হচ্ছে না।

---

## ❓ সমস্যা কী ছিল?

GitHub-এ `custom-product-section` branch-এ push হচ্ছিল, কিন্তু GitHub শুধুমাত্র **default branch** (`main` বা `master`) এর commit গুলোকে contribution graph-এ count করে।

### মূল কারণ ২টি:
| # | কারণ | বিবরণ |
|---|------|--------|
| ১ | **ভুল Branch** | `custom-product-section` branch-এ push হচ্ছিল, `main`-এ নয় |
| ২ | **Merge সমস্যা** | Vim editor খুলে merge অসম্পূর্ণ থেকে যাচ্ছিল |

---

## ⚠️ যেসব Error এসেছিল

### Error 1: Uncommitted Changes
```
error: Your local changes to the following files would be overwritten by checkout:
Please commit your changes or stash them before you switch branches.
```
**কারণ:** Branch switch করার আগে uncommitted changes ছিল।

---

### Error 2: Merge Incomplete (MERGE_HEAD exists)
```
error: You have not concluded your merge (MERGE_HEAD exists).
hint: Please, commit your changes before merging.
```
**কারণ:** Vim editor থেকে সঠিকভাবে বের না হওয়ায় merge pending ছিল।

---

### Error 3: Push Rejected
```
! [rejected] main -> main (fetch first)
error: failed to push some refs to '...'
hint: Updates were rejected because the remote contains work that you do not have locally.
```
**কারণ:** Remote-এ নতুন commit ছিল যা locally ছিল না।

---

### Error 4: Vim Editor খুলে যাওয়া
```
Merge branch 'custom-product-section'
# Please enter a commit message...
~
~
.git/MERGE_MSG [unix]
```
**সমাধান:** `Esc` চাপো → `:wq!` টাইপ করো → `Enter` চাপো

---

## ✅ সমাধান — Step by Step

### Step 1: সব changes save করো
```bash
git add .
git commit -m "save changes before switching to main"
```

### Step 2: main branch-এ যাও
```bash
git checkout main
```

### Step 3: merge করো
```bash
git merge custom-product-section
```

### Step 4: Merge অসম্পূর্ণ থাকলে
```bash
git commit --no-edit
```

### Step 5: Remote conflict হলে
```bash
git pull origin main --no-rebase
```

### Step 6: Final push
```bash
git push origin main
```

---

## 🚀 Quick Fix Commands (সব একসাথে)

```bash
git add .
git commit -m "save changes"
git checkout main
git merge custom-product-section
git commit --no-edit
git pull origin main --no-rebase
git push origin main
```

---

## 📋 GitHub Contribution Count হওয়ার শর্ত

- ✅ Commit অবশ্যই **`main`** বা **`master`** branch-এ থাকতে হবে
- ✅ Git config-এর **email** এবং GitHub account-এর **email** একই হতে হবে
- ✅ Pull Request করলে সেটা **merge** হতে হবে
- ✅ Commit যে account থেকে করা হচ্ছে সেটা GitHub-এর সাথে **connected** থাকতে হবে

### Email চেক করো:
```bash
git config user.email
```

### Email ঠিক করো:
```bash
git config --global user.email "তোমার_github_email@example.com"
```

---

## 💡 Best Practices

1. **সবসময় `main` branch-এ কাজ করো** অথবা নিয়মিত merge করো
2. **VS Code কে default editor বানাও** (Vim এড়াতে):
   ```bash
   git config --global core.editor "code --wait"
   ```
3. **প্রতিদিন কাজ শেষে push করো** যাতে contribution graph সবুজ থাকে
4. **`git status`** দিয়ে সবসময় current branch চেক করো

---

## 📅 তৈরির তারিখ
০৪ জুন ২০২৬ | Tawhide16 এর GitHub সমস্যা সমাধানের উপর ভিত্তি করে তৈরি
