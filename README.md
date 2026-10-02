# eDoc Smart Hub Farmer (PWA) — v3

หน้าแอปสำหรับติดตั้งลงมือถือ/คอมพิวเตอร์ ครอบเว็บ Google Apps Script เดิมไว้ใน iframe

## ขึ้น GitHub Pages
1. สร้าง repository ใหม่ แล้วอัปโหลดไฟล์ทั้งหมดในโฟลเดอร์นี้ (ไว้ที่ root)
2. Settings → Pages → Source: Deploy from a branch → เลือก `main` / `/ (root)` → Save
3. เปิด `https://<ชื่อผู้ใช้>.github.io/<ชื่อ repo>/`

## เปลี่ยนลิงก์ Apps Script
แก้ที่ `src` ของ `<iframe id="frame">` ใน `index.html`

## สิ่งที่ปรับใน v3
- แก้บั๊ก: หน้ารีโหลดเองตอนเปิดครั้งแรก (controllerchange)
- แก้บั๊ก: iOS กด "เข้าใจแล้ว" แล้ว sheet โผล่ซ้ำทุกครั้ง
- Service Worker: รอเครือข่ายสูงสุด 4 วินาทีแล้วใช้แคช (เหมาะกับสัญญาณอ่อน)
- ตรวจเบราว์เซอร์ในแอป (LINE/Facebook/IG): LINE เด้งไปเบราว์เซอร์ภายนอกอัตโนมัติ, แอปอื่นแสดงวิธีเปิดด้วย Safari/Chrome + ปุ่มคัดลอกลิงก์
- คำแนะนำติดตั้งบน iOS รองรับทั้ง Safari และ Chrome/Edge
- เพิ่มโฟลเดอร์ `apps-script/` (ตัวอย่าง doGet + CSS สำหรับมือถือ) — ไม่จำเป็นต้องอัปโหลดขึ้น GitHub Pages

## ข้อจำกัดของ iOS
- iOS ไม่มีปุ่มติดตั้งอัตโนมัติ ผู้ใช้ต้องกด แชร์ → เพิ่มไปยังหน้าจอโฮม เอง (แอปมีหน้าสอนให้)
- แอปที่เพิ่มลงหน้าจอโฮมมี storage แยกจาก Safari ต้องล็อกอินใหม่ในแอป

## หมายเหตุฝั่ง Apps Script
- Deploy เป็น Web app แนะนำ Execute as: Me / Who has access: Anyone (ถ้าต้องล็อกอิน Google ใน iframe บน iOS มักใช้ไม่ได้)
- `doGet` ต้องมี `.setXFrameOptionsMode(ALLOWALL)` และ `.addMetaTag('viewport', ...)` ดู `apps-script/Code.gs`
- ช่อง input ในหน้า Apps Script ควรฟอนต์ ≥ 16px ดู `apps-script/mobile-snippet.html`

## อัปเดตเวอร์ชัน
เมื่อแก้ไฟล์ในแอป ให้เปลี่ยนเลขเวอร์ชัน `V` ใน `sw.js` (ตอนนี้ edoc-farmer-v3) — ผู้ใช้จะเห็นแถบ "มีเวอร์ชันใหม่ กดอัปเดต"
