# Power Meter Simulator 1.0.6

- แก้บัคบนเครื่อง Windows ที่ใช้ code page ซึ่งไม่รองรับภาษาไทย: backend อาจหยุดทันทีตอนเริ่มฉากก่อนส่งค่ามิเตอร์
- บังคับ stdout/stderr ของ backend เป็น UTF-8 และใช้ replacement สำหรับอักขระที่เขียนไม่ได้
- เพิ่ม regression test สำหรับการเริ่ม backend บน locale ที่ไม่ใช่ภาษาไทย
