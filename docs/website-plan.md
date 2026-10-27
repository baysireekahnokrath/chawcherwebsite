# Chaw Cher Website — แผนและการตัดสินใจ

ไฟล์นี้คือ "ความจริงที่ตกลงกันแล้ว" ของเว็บ chawcher.com
ห้ามเปลี่ยนโดยไม่ถาม Bay · ระบบหลังบ้านดูที่ repo `Chawcheros/docs/decisions-log.md`

---

## A. ตัดสินใจแล้ว (2026-10-27)

| # | เรื่อง | คำตอบ |
|---|---|---|
| A1 | แพลตฟอร์ม | **WordPress + WooCommerce ต่อ** เหตุผล: ทีม marketing และคนที่ไม่เขียนโค้ดต้องแก้เองได้ และหาคนดูแลต่อได้ง่ายถ้าไม่มี Claude Code |
| A2 | บทความ | 2 ทาง: (1) Claude Code เขียนแล้วโพสต์เลย (2) คนเขียนเองทั้งหมดใน wp-admin |
| A3 | เจ้าของข้อมูลสินค้า | ChawcherOS เป็นเจ้าของ · WordPress เป็นหน้าร้าน (ตาม backlog B2 ของ ChawcherOS) |

## B. ใครเป็นเจ้าของข้อมูลช่องไหน

| ข้อมูล | เจ้าของ | แก้ที่ไหน |
|---|---|---|
| SKU · ราคา · ราคาโปร · สถานะขาย/เลิกขาย · ขนาด · ผ้าที่มี/หมด | ChawcherOS | ใน ChawcherOS เท่านั้น แล้ว sync ขึ้นเว็บทางเดียว |
| คำบรรยายสินค้า · รูป · ข้อความ SEO · บทความ · โปรโมชันหน้าเว็บ · หน้า About/Contact | WordPress | wp-admin (คน) หรือ Claude ผ่าน WordPress.com connector |
| บัญชีสมาชิกลูกค้า | WordPress (WooCommerce) | ส่งต่อเข้าโมดูลลูกค้าของ ChawcherOS เมื่อโมดูลนั้นมีแล้ว |

## C. โครงที่เสนอ (รอ Bay ยืนยัน)

- **โฮสต์:** ย้ายไป WordPress.com Business (฿9,999/ปี) เพราะมี staging site, GitHub Deployments, site preview links, real-time backup, SSH/SFTP และ Claude ต่อได้เต็มที่ผ่าน connector
- **repo นี้เก็บ:** ปลั๊กอิน `chawcher-connector` (โค้ดเฉพาะของเรา) · child theme ถ้าจำเป็น · เทส QC · เอกสาร
- **ไหลงาน:** PR → deploy ขึ้น staging → เทสอัตโนมัติ → merge → deploy ขึ้น production
- **เนื้อหา:** แก้ใน wp-admin ตรงๆ ใช้ draft/preview/revision ของ WordPress
- **สมาชิก:** WooCommerce My Account + LINE Login
- **ลิงก์เช็กออเดอร์ (ChawcherOS B1):** หน้าใน WordPress เรียก API ของ ChawcherOS ด้วยลิงก์ที่เดาไม่ได้

## D. ผลตรวจเว็บเดิม (2026-10-27 ผ่าน WordPress.com connector)

ข้อมูลรายการปลั๊กอินเป็น snapshot วันที่ 2025-08-20 (Jetpack sync) ส่วนหน้าเว็บ บทความ และสินค้าเป็นข้อมูลสด

- ธีม Eskil (Qode Interactive, ซื้อจาก Envato) + Elementor Pro + Slider Revolution · โฮสต์เดิมใช้ LiteSpeed
- สินค้า 102 ตัว ใน 12 หมวด · สีไม้ (Oak/Walnut) แยกเป็นสินค้าคนละตัว ไม่ใช่ variation
- บทความ 22 เรื่อง ใน 3 หมวด (design / lifestyle / promotion)
- หน้าเพจ 58 หน้า **ส่วนใหญ่เป็นหน้า demo ของธีมที่ import มาตั้งแต่ปี 2022** และยังเปิดสาธารณะอยู่

### ต้องเก็บกวาด (ยังไม่ได้แตะ รอ Bay อนุมัติ)

| # | เรื่อง |
|---|---|
| D1 | หน้า demo ธีมที่ยังเผยแพร่อยู่ เช่น sample-page, careers, gift-cards, typo, shop-dark, left-menu-home, coming-soon, landing และหน้า portfolio demo หลายหน้า |
| D2 | หน้าระบบซ้ำ: my-account-2, checkout-2, wishlist-2 |
| D3 | สินค้าซ้ำ: koontong-sideboard-oak / -oak-2, koontong-sideboard-walnut / -walnut-2, koontong-sofa / koontong-sofa-2 |
| D4 | slug ไม่ตรงชื่อ: `phoenix-sofa-copy-copy` = KRATA SOFA, `mininest-armchair-2` = NOKKAEW ARMCHAIR, โพสต์ล่าสุด "Chaw cher promotion" ใช้ slug ที่ copy มา |
| D5 | ข้อมูลติดต่อไม่ตรงกัน: เบอร์ 063-829-9536 กับ 095-490-3174 · เวลาเปิด จ–ส 9–18 กับ จ–ศ 10–18 |
| D6 | ความปลอดภัย: เปิดให้สมัครสมาชิกอยู่ แต่ Akismet กับ Limit Login Attempts ปิดอยู่ · Jetpack ปิดอยู่ (connector จัดการปลั๊กอินแบบสดไม่ได้) |
| D7 | มีโค้ดอยู่ในปลั๊กอิน Code Snippets ซึ่งไม่มีประวัติการแก้ ควรย้ายเข้าปลั๊กอินใน repo นี้ |

## E. ยังเปิดอยู่

| # | คำถาม |
|---|---|
| OPEN-1 | ยืนยันย้ายโฮสต์ไป WordPress.com Business ไหม · โฮสต์ปัจจุบันคือเจ้าไหน หมดอายุเมื่อไร |
| OPEN-2 | อนุมัติเก็บกวาดหัวข้อ D ไหม |
| OPEN-3 | สีไม้ควรรวมเป็น variation ของสินค้าตัวเดียว (ตรงกับ ChawcherOS ที่แยก รุ่น → ตัวที่ขายจริง) หรือแยกตัวเหมือนเดิม |
