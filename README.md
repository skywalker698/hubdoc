# eDoc Smart Hub Farmer (PWA)

หน้าแอปสำหรับติดตั้งลงมือถือ/คอมพิวเตอร์ ครอบเว็บ Google Apps Script เดิมไว้ใน iframe

## ขึ้น GitHub Pages
1. สร้าง repository ใหม่ แล้วอัปโหลดไฟล์ทั้งหมดในโฟลเดอร์นี้ (ไว้ที่ root)
2. Settings → Pages → Source: Deploy from a branch → เลือก `main` / `/ (root)` → Save
3. เปิด `https://<ชื่อผู้ใช้>.github.io/<ชื่อ repo>/`

## เปลี่ยนลิงก์ Apps Script
แก้ที่ `src` ของ `<iframe id="frame">` ใน `index.html`

## หมายเหตุ
- Apps Script ต้อง Deploy แบบ Web app และตั้งสิทธิ์ให้เข้าถึงได้ตามผู้ใช้งาน
- ฝั่ง `doGet` ต้องใช้ `.setXFrameOptionsMode(HtmlService.XFrameOptionsMode.ALLOWALL)` จึงจะแสดงใน iframe ได้
- เมื่อแก้ไฟล์ในแอป ให้เปลี่ยนเลขเวอร์ชัน `V` ใน `sw.js` (ตอนนี้ edoc-farmer-v2) — ผู้ใช้จะเห็นแถบ "มีเวอร์ชันใหม่ กดอัปเดต" เพื่อให้เครื่องผู้ใช้อัปเดตแคช
