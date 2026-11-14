# Power Meter Simulator

แอป Windows สำหรับจำลองมิเตอร์ไฟฟ้าและทดสอบการสื่อสาร Modbus TCP/RTU มีรุ่น Trial และ Full

## โครงสร้างโปรเจกต์

- `sim/power_meter_gui.py` — GUI หลัก ใช้ร่วมกันทั้งสองรุ่น
- `sim/power_meter_gui_full.py` — entry point ของรุ่น Full
- `sim/power_meter_pm5xxx_sim.py` — backend จำลองมิเตอร์ของรุ่น Trial
- `sim/power_meter_pm5xxx_sim_full.py` — backend จำลองมิเตอร์ของรุ่น Full
- `core/` — plant simulation และ trial state
- `vendors/` — register maps และโปรไฟล์มิเตอร์
- `installer/*.iss` — Inno Setup scripts; กำหนดเลขรุ่นแยกสำหรับ Trial และ Full
- `build_windows.bat`, `build_full_windows.bat` — build และสร้าง installer

## พฤติกรรมที่ควรรู้

- GUI หลักอยู่ใน `power_meter_gui.py`; ไฟล์ `_full.py` เรียก `main(full_edition=True)` ไม่ได้คัดลอก GUI
- ข้อผิดพลาดในสถานะ GUI ได้รหัสตามหมวด เช่น `PM-1001` การตั้งค่า, `PM-2001` TCP,
  `PM-2002` RTU/Serial, `PM-3001` backend และ `PM-4001` การอ่าน Modbus
- ปุ่ม “ส่งรายงานปัญหา” เปิดอีเมลฉบับร่างถึง `horenso309@gmail.com` โดยผู้ใช้ตรวจและกดส่งเอง
- Backend ถูกติดตั้งในโฟลเดอร์ข้าง GUI; อย่าย้าย executable ออกจากโฟลเดอร์ของมัน

## แนวทางสำหรับ AI ที่แก้ไขโปรเจกต์

1. อ่าน README นี้และ `BUILD_WINDOWS.md` ก่อนแก้โค้ดหรือไฟล์ release
2. แก้แหล่งโค้ดหลักเพียงจุดเดียวเมื่อรุ่น Trial/Full ใช้ entry point ร่วมกัน
3. ทุกครั้งที่เปลี่ยนโค้ด ให้อัปเดต README นี้ให้ตรงกับพฤติกรรม/โครงสร้างล่าสุด
4. เมื่อเตรียม release ให้เพิ่ม patch version ใน installer scripts ทั้งสองรุ่น
   เพิ่ม `RELEASE_NOTES-<version>.md` แล้วสร้าง installer ใหม่ทั้ง Trial และ Full
5. ใช้ `build_windows.bat` และ `build_full_windows.bat` ตามขั้นตอนใน `BUILD_WINDOWS.md`

## รุ่นปัจจุบัน

รุ่น `1.0.3` เพิ่มรหัสข้อผิดพลาดและการร่างอีเมลรายงานปัญหา ดูรายละเอียดใน
[`RELEASE_NOTES-1.0.3.md`](./RELEASE_NOTES-1.0.3.md)
