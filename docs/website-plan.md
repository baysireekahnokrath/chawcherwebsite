# Chaw Cher Website — แผนและการตัดสินใจ

ไฟล์นี้คือ "ความจริงที่ตกลงกันแล้ว" ของเว็บ chawcher.com
ห้ามเปลี่ยนโดยไม่ถาม Bay · ระบบหลังบ้านดูที่ repo `Chawcheros/docs/decisions-log.md`

---

## A. ตัดสินใจแล้ว (2026-10-27)

| # | เรื่อง | คำตอบ |
|---|---|---|
| A1 | แพลตฟอร์ม | **เปิดใหม่อีกครั้ง (2026-10-27)** · Bay พร้อมทำใหม่ทั้งหมด ไม่ยึดธีม/ปลั๊กอินเดิม · เกณฑ์หลัก: คนที่ไม่เขียนโค้ดแก้เองได้ และหาคนดูแลต่อได้ถ้าไม่มี Claude Code · ดูหัวข้อ F |
| A4 | สีไม้ Oak/Walnut | **รวมเป็นสินค้าตัวเดียว มีตัวเลือกสี** ให้ตรงกับ ChawcherOS (รุ่น → ตัวที่ขายจริง) |
| A5 | โฮสต์ปัจจุบัน | HostNeverDie · WordPress Hosting WH-Supersonic · ฿2,999/ปี · จ่ายถึง 20/08/2027 |
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

### เก็บกวาด

| # | เรื่อง |
|---|---|
| D1 | ✅ 2026-10-27 · เปลี่ยนหน้า demo ธีม 45 หน้าเป็น Draft (กู้คืนได้ใน wp-admin → Pages → Drafts) · หน้าที่ยังเผยแพร่เหลือ 10 หน้า: home, shop, cart, checkout, my-account, wishlist, blog, about-us, contact-us, returns-refunds · ไม่ได้ลบหรือแก้เนื้อหาใดๆ |
| D2 | ✅ 2026-10-27 · my-account-2, checkout-2, wishlist-2 เป็น Draft แล้ว |
| D1b | เมนูที่ไม่ได้ผูกตำแหน่ง (Footer 1–4, Fs menu) ยังลิงก์ไป eskil.qodeinteractive.com และโซเชียลของ Qode · ยังไม่แตะ |
| D1c | หน้า returns-refunds มีเนื้อหาจริง แต่แถบข้างยังเป็น demo (support@example.com) · หน้า Terms & Conditions ที่ตั้ง Draft ไปเป็น lorem ipsum ต้องเขียนจริงก่อนเปิดขายออนไลน์ |
| D3 | สินค้าซ้ำ: koontong-sideboard-oak / -oak-2, koontong-sideboard-walnut / -walnut-2, koontong-sofa / koontong-sofa-2 |
| D4 | slug ไม่ตรงชื่อ: `phoenix-sofa-copy-copy` = KRATA SOFA, `mininest-armchair-2` = NOKKAEW ARMCHAIR, โพสต์ล่าสุด "Chaw cher promotion" ใช้ slug ที่ copy มา |
| D5 | หน้า Contact (แก้ล่าสุด 2026-09-17) ถูกแล้ว: 063-829-9536 · จ–ศ 10–18 เสาร์–อาทิตย์นัดล่วงหน้า · แต่หน้าสินค้าบางหน้าและบทความเก่ายังเขียน จ–ส 9–18 และมีเบอร์ 095-490-3174 ในบทความภายนอก |
| D6 | ความปลอดภัย: เปิดให้สมัครสมาชิกอยู่ แต่ Akismet กับ Limit Login Attempts ปิดอยู่ · Jetpack ปิดอยู่ (connector จัดการปลั๊กอินแบบสดไม่ได้) |
| D7 | มีโค้ดอยู่ในปลั๊กอิน Code Snippets ซึ่งไม่มีประวัติการแก้ ควรย้ายเข้าปลั๊กอินใน repo นี้ |

## F. ถ้าทำใหม่ทั้งหมด · เทียบแพลตฟอร์ม (2026-10-27)

ต้นเหตุ "hard code เพียบ" ในเว็บเดิม: import demo ธีมทั้งชุด + จัดหน้าด้วย Elementor + โค้ดใน Code Snippets
ไม่ใช่ตัว WordPress เอง · ถ้าเลือก WordPress อีก ต้องตั้งกฎกันไม่ให้ซ้ำ (ดูข้อ F2)

| | WordPress ใหม่ (block theme) | Shopify | Webflow | Next.js + Headless CMS |
|---|---|---|---|---|
| คนไม่เขียนโค้ดแก้เอง | ✅ | ✅ | ✅ ดีที่สุดสำหรับดีไซเนอร์ | ⚠️ แก้เนื้อหาได้ แก้โครงหน้าต้องใช้นักพัฒนา |
| หาคนดูแลต่อในไทย | ✅ มากที่สุด | ✅ | ⚠️ น้อย | ⚠️ ต้องเป็นนักพัฒนา |
| Preview / Production | ⚠️ ต้องใช้ staging | ⚠️ preview ธีมได้ เนื้อหาขึ้นจริงทันที | ✅ staging ในตัว | ✅ ทุก PR |
| สมาชิก + LINE Login | ✅ ปลั๊กอิน | ✅ แอป | ❌ User Accounts ปิดไป ม.ค. 2026 ต้องใช้ third-party | ✅ เขียนเอง |
| ต่อ ChawcherOS | ⚠️ sync ผ่าน Woo REST | ⚠️ sync ผ่าน Admin API | ⚠️ sync ผ่าน CMS API | ✅ อ่านตรง |
| จ่ายเงินไทย (PromptPay, ผ่อน) | ✅ ปลั๊กอิน 2C2P/Omise | ⚠️ gateway ไทย + ค่าธรรมเนียมเพิ่ม (ต้องเช็กอัตรา) | ❌ จำกัด | ✅ ต่อ API เอง |
| ค่าใช้จ่ายประจำ | ต่ำ | กลาง (รายเดือน + ค่าธรรมเนียม) | กลาง | ต่ำ–กลาง |

### F1. ค่าโฮสต์ ถ้าเลือก WordPress (เช็กราคา 2026-10-27)

| ทางเลือก | ต่อเดือน | หมายเหตุ |
|---|---|---|
| **HostNeverDie เดิม + ทำ staging/Git เอง** | ~฿250 (จ่ายแล้วถึง ส.ค. 2027) | 2 โดเมน · 20 ฐานข้อมูล → ตั้ง staging.chawcher.com ได้ · deploy โค้ดด้วย GitHub Actions ผ่าน FTP/SSH · ต้องถาม support เรื่อง SSH/backup |
| WordPress.com Business 3 ปี | ~฿583 (฿20,988 จ่ายครั้งเดียว) | staging กดปุ่มเดียว · GitHub Deployments · backup real-time |
| WordPress.com Business 1 ปี | ~฿833 (฿9,999/ปี) | เหมือนข้างบน |
| WordPress.com Personal/Premium | ฿130–279 | ไม่มี staging, GitHub, SFTP · ไม่แนะนำ |

### F2. กฎ ถ้าเลือก WordPress
1. ไม่ใช้ page builder (Elementor) · ใช้ block editor + patterns ของธีมเท่านั้น
2. ไม่ import demo ธีม
3. ข้อมูลสินค้า/ราคามาจาก sync เท่านั้น ห้ามพิมพ์ในหน้าเพจ
4. โค้ดเฉพาะของเราอยู่ในปลั๊กอินเดียวใน repo นี้ · ห้ามใช้ Code Snippets
5. ปลั๊กอินไม่เกิน ~10 ตัว ทุกตัวต้องมีเหตุผลบันทึกไว้

## E. ยังเปิดอยู่

| # | คำถาม |
|---|---|
| OPEN-1 | เลือกแพลตฟอร์มสำหรับเว็บใหม่ (หัวข้อ F) แล้วค่อยเลือกโฮสต์ |
| OPEN-2 | สินค้าซ้ำและ slug ผิด (D3, D4) จะเก็บในเว็บเดิม หรือรอทำใหม่ทีเดียวตอน sync |
