# Trash For Coin - ขยะแลกเหรียญ

ระบบจัดการขยะแลกเหรียญเพื่อส่งเสริมการรีไซเคิลและการจัดการขยะอย่างยั่งยืน

## ภาพรวมโครงการ

Trash For Coin เป็นระบบมัดจำบรรจุภัณฑ์ขยะที่พัฒนาขึ้นจากปัญหาการจัดการขยะมูลฝอยชุมชน โดยใช้กลไกการมัดจำ **1 บาทต่อบรรจุภัณฑ์ 1 ชิ้น** เพื่อสร้างแรงจูงใจให้ผู้บริโภคนำขยะมารีไซเคิล

### วัตถุประสงค์
- พัฒนาระบบมัดจำบรรจุภัณฑ์ที่รองรับการจัดการขยะได้อย่างครอบคลุม
- ส่งเสริมการดำเนินงานด้านการจัดการขยะให้มีประสิทธิภาพและลดต้นทุน
- ส่งเสริมการคัดแยกขยะจากแหล่งต้นทางเพื่อเพิ่มอัตราการรีไซเคิล
- สร้างแรงจูงใจเชิงบวกและสร้างจิตสำนึกด้านสิ่งแวดล้อม

## ประเภทขยะที่รองรับ

1. **PET** - ภาชนะพลาสติกประเภท PET
2. **อลูมิเนียม** - ภาชนะอลูมิเนียม
3. **แก้ว** - ภาชนะแก้วที่สามารถหลอมได้
4. **วัสดุเผา** - ขยะสำหรับเผาเพื่อผลิตพลังงาน
5. **ขยะปนเปื้อน** - ขยะที่ต้องจัดการพิเศษ

## คุณสมบัติหลัก

### ระบบผู้ใช้งาน 5 ระดับ
- **Root Admin**: สิทธิ์สูงสุดในระบบ
- **Administrator**: ผู้ดูแลระบบ
- **Moderator**: ผู้ดูแลเนื้อหา
- **Member**: สมาชิกทั่วไป
- **Viewer**: ผู้ดูข้อมูล
- **Guest**: ผู้เยี่ยมชม (ไม่ได้เข้าสู่ระบบ)
### ฟีเจอร์ครบครัน
- ✅ จัดการหมวดหมู่ขยะ
- ✅ จัดการสินค้าและบรรจุภัณฑ์
- ✅ ระบบคำสั่งซื้อพร้อมมัดจำ
- ✅ จัดการผู้ใช้งานและสิทธิ์
- ✅ ส่งออกรายงาน CSV/PDF
- ✅ API endpoints
- ✅ ระบบยืนยันตัวตน

## เทคโนโลยีที่ใช้

### Backend
- **Flask** (Python) - Web Framework
- **MySQL** - Database
- **xhtml2pdf** - PDF Generation

### Frontend
- **Bootstrap 5.3.0** - CSS Framework
- **Bootstrap Icons** - Icons
- **Google Fonts** - Typography (Inter, Sarabun)
- **Jinja2** - Template Engine

### Hardware (สำหรับตู้คืนขยะ)
- Raspberry Pi 4 (1GB)
- Automatic Scanner
- เครื่องพิมพ์ใบเสร็จ 58MM
- LCD Display Module
- เครื่องจ่ายเหรียญ 24V
- เซ็นเซอร์และ LED

## การติดตั้งและใช้งาน

### 1. ติดตั้ง Dependencies
```bash
pip install -r requirements.txt
```

### 2. ตั้งค่าฐานข้อมูล
```sql
CREATE DATABASE project_bin;
-- ดูรายละเอียดเพิ่มเติมใน developer_manual.html
```

### 3. การรันแอพพลิเคชัน
```bash
python app.py
```

แอพพลิเคชันจะทำงานที่ `http://localhost:5000`

### 4. ตั้งค่า Root Admin
```sql
ALTER TABLE tbl_users ADD COLUMN role VARCHAR(50) DEFAULT 'member';
UPDATE tbl_users SET role = 'root_admin' WHERE email = 'your_admin_email@example.com';
```

## โครงสร้างโฟลเดอร์

```
trash-for-coin/
├── app.py                    # Main Flask application
├── templates/                # HTML templates
│   ├── base.html            # Base template
│   ├── index.html           # Homepage
│   ├── login.html           # Login page
│   ├── register.html        # Registration page
│   ├── profile.html         # User profile
│   ├── about.html           # About page
│   ├── contact.html         # Contact page
│   ├── tbl_category.html    # Category management
│   ├── tbl_products.html    # Product management
│   ├── tbl_order.html       # Order management
│   ├── tbl_users.html       # User management
│   └── pdf_template.html    # PDF export template
├── user_manual.html         # User manual
├── developer_manual.html    # Developer manual
├── requirements.txt         # Python dependencies
└── README.md               # This file
```

## วิธีการใช้งาน

### สำหรับผู้ใช้งานทั่วไป
1. **สมัครสมาชิก** - ลงทะเบียนเข้าสู่ระบบ
2. **ซื้อสินค้า** - ได้รับใบเสร็จพร้อมรหัส barcode
3. **คัดแยกขยะ** - แยกตามประเภท 5 ประเภท
4. **นำไปทิ้ง** - สแกน barcode และทิ้งที่ตู้คืนขยะ
5. **รับเงินคืน** - ได้รับเงินมัดจำคืนทันที

### สำหrับผู้ดูแลระบบ
- จัดการหมวดหมู่และสินค้า
- ตรวจสอบคำสั่งซื้อ
- จัดการผู้ใช้งาน
- ดูรายงานและสถิติ

## เอกสารประกอบ

- 📖 [คู่มือการใช้งาน](user_manual.html) - สำหรับผู้ใช้งานทั่วไป
- 🔧 [คู่มือผู้พัฒนา](developer_manual.html) - สำหรับผู้พัฒนาระบบ

## ทีมพัฒนา

### ผู้จัดทำโครงการ
- **นายเพียรเลิศ พริ้งเพราะ**
- **นายปพณ คุปตะพันธ์**

### ที่ปรึกษาโครงการ
- **ครูกิจจารักษ์ หิรัญน้อย** - ครูที่ปรึกษาโครงการ
- **ครูสมเกียรติ ใจดี** - ครูที่ปรึกษาร่วม
- **คุณสุธน เจริญยุทธ** - ครูที่ปรึกษาร่วม

## สาขาวิชา
เทคโนโลยีสารสนเทศ

## งบประมาณ
**ต้นทุนรวม**: 6,023 บาท

## ลิขสิทธิ์
© 2025 Trash For Coin Project. All rights reserved.

## การสนับสนุน

หากพบปัญหาหรือต้องการความช่วยเหลือ กรุณาติดต่อผ่าน:
- Email: info@trashforcoin.com
- Tel: 02-123-4567

---

**Trash For Coin** - ขยะแลกเหรียญ เพื่อสิ่งแวดล้อมที่ยั่งยืน 🌱"# TrashForCoin" 
