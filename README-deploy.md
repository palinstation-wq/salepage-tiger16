# วิธี Deploy ขึ้น GitHub Pages

ไฟล์ในโฟลเดอร์นี้พร้อม deploy แล้ว: `index.html`, `assets/` (รูป+ฟอนต์), `.nojekyll`

> ⚠️ อัปโหลด **ทั้งหมด** รวมโฟลเดอร์ `assets/` ด้วย ไม่งั้นรูปจะไม่ขึ้น

---

## ขั้นที่ 1 — สร้าง Repository
1. เข้า https://github.com → กด **New repository**
2. ตั้งชื่อ เช่น `salepage-tiger16` → เลือก **Public** → **Create repository**

## ขั้นที่ 2 — อัปโหลดไฟล์
**วิธีง่าย (ผ่านเว็บ):**
1. ในหน้า repo กด **Add file → Upload files**
2. ลากไฟล์จากโฟลเดอร์ `deploy/` นี้เข้าไป: `index.html`, `.nojekyll` และ**ลากโฟลเดอร์ `assets` ทั้งโฟลเดอร์**
3. กด **Commit changes**

**หรือผ่าน Git:**
```bash
cd deploy
git init
git add .
git commit -m "salepage tiger16"
git branch -M main
git remote add origin https://github.com/<username>/salepage-tiger16.git
git push -u origin main
```

## ขั้นที่ 3 — เปิด GitHub Pages
1. ใน repo → **Settings → Pages**
2. **Source:** Deploy from a branch
3. **Branch:** `main` / โฟลเดอร์ `/ (root)` → **Save**
4. รอ 1–2 นาที → จะได้ลิงก์:
   ```
   https://<username>.github.io/salepage-tiger16/
   ```

## ขั้นที่ 4 — แก้ลิงก์รูปแชร์ (OG) ให้เป็น URL จริง ⚠️สำคัญ
พอได้ลิงก์เว็บจากขั้นที่ 3 แล้ว เปิด `index.html` ค้นหา `YOUR-DOMAIN`
มี **3 จุด** (og:url, og:image, twitter:image) → แทนด้วยลิงก์เว็บจริง เช่น:
```html
<meta property="og:url" content="https://username.github.io/salepage-tiger16/">
<meta property="og:image" content="https://username.github.io/salepage-tiger16/assets/og-image.jpg">
<meta name="twitter:image" content="https://username.github.io/salepage-tiger16/assets/og-image.jpg">
```
แล้ว upload/push ทับ index.html อีกครั้ง
> ถ้าไม่แก้ เวลาแชร์ลิงก์ใน LINE/FB รูป+หัวข้อจะไม่ขึ้น (เพราะชี้ไป YOUR-DOMAIN ที่ไม่มีจริง)

ทดสอบรูปแชร์: เอาลิงก์ไปวางใน https://developers.facebook.com/tools/debug/ กด "Scrape Again"

## ขั้นที่ 5 — ทดสอบ
เปิดลิงก์ → กรอกฟอร์ม → แนบสลิป → ติ๊กยอมรับ → กดยืนยัน
- ✅ ฟอร์มส่งเข้า Google Sheet ได้จริง (บนเว็บจริง CSP ไม่บล็อกแล้ว)
- ✅ ปุ่มโทรทำงานบนมือถือ
- ✅ แชร์ลิงก์ใน LINE/FB ขึ้นรูป OG + หัวข้อสวย

---

## (ทีหลัง) ใช้โดเมน landforloan.co.th
- Settings → Pages → **Custom domain** → ใส่ เช่น `course.landforloan.co.th` → Save
- ไปที่ผู้ดูแลโดเมน เพิ่ม DNS record **CNAME**: `course` → `<username>.github.io`
- รอ DNS อัปเดต (ไม่กี่ชม.) → เปิด "Enforce HTTPS"

## อัปเดตหน้าเว็บทีหลัง
แก้ไฟล์แล้ว push/upload ทับ index.html (+assets ถ้ารูปเปลี่ยน) → GitHub Pages อัปเดตอัตโนมัติใน 1–2 นาที
