# Power Meter Simulator 1.0.4

- จำกัด Pymodbus เป็น `>=3.8,<3.10` ให้ตรงกับ datastore API ที่ backend ใช้
- แก้ backend ปิดทันทีด้วย ImportError บน Pymodbus รุ่นใหม่ที่ถอด `ModbusSlaveContext` ออก
- สร้าง installer ใหม่สำหรับ Trial และ Full
- เพิ่มปุ่มส่งคำขอเพิ่มมิเตอร์ โดยระบุยี่ห้อและรุ่นผ่านอีเมลถึงผู้พัฒนา
