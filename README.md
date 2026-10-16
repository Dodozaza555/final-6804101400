# Final Exam: Software Testing with Playwright

- รหัสนักศึกษา: 6804101400
- ชื่อ-นามสกุล: นายเอกราช แซ่ว่าง
- ระบบที่ทดสอบ: https://www.saucedemo.com/
- เครื่องมือ: Playwright Test (TypeScript)

## วิธีรัน

    npm install
    npx playwright install
    npx playwright test
    npx playwright show-report

## โครงสร้างข้อสอบ

| บท | รหัส | ไฟล์ | หัวข้อ |
|---|---|---|---|
| 1 | UT-01 | tests/unit/UT-01.spec.ts | Login Form Validation |
| 1 | UT-02 | tests/unit/UT-02.spec.ts | Product Button State |
| 2 | IT-01 | tests/integration/IT-01.spec.ts | Top-Down with Stub |
| 2 | IT-02 | tests/integration/IT-02.spec.ts | Bottom-Up with Driver |
| 3 | ST-01 | tests/system/ST-01.spec.ts | Complete Purchase Flow |
| 3 | ST-02 | tests/system/ST-02.spec.ts | Checkout Validation and Recovery |

## IT-01: Top-Down Integration Testing (Stub)

- **Real:** หน้า Login ของ SauceDemo จริง (กรอก standard_user / secret_sauce
  แล้วเข้าสู่ inventory.html จริง)
- **Stub:** หน้า Inventory ที่จำลองด้วย `page.setContent()` แสดงข้อความ
  `Mock Inventory Ready` และสินค้าจำลอง `Mock Backpack`, `Mock Bike Light`
- **แนวคิด:** Top-Down ทดสอบโมดูลระดับบน (Login) ของจริง
  โดยใช้ Stub แทนโมดูลระดับล่างที่ยังไม่ถูกนำมาเชื่อมต่อ (Inventory)
- **ข้อจำกัด:** Stub นี้จำลอง DOM ระดับ Browser หลัง Login จริง
  ไม่ใช่การแทน Internal Module ของ SauceDemo เพราะเข้าถึง Source Code ภายในไม่ได้

## IT-02: Bottom-Up Integration Testing (Driver)

- **Driver:** ฟังก์ชัน `driverOpenInventory()` สร้าง BrowserContext,
  ตั้ง Cookie `session-username = standard_user` บนโดเมน `www.saucedemo.com`
  ด้วย `addCookies()` แล้วเปิด `inventory.html` โดยตรง โดยไม่ผ่าน Login Form
- **Real:** หน้า Inventory (สินค้า 6 รายการ), การเพิ่มสินค้าลง Cart,
  Cart Badge และหน้า Shopping Cart ของ SauceDemo จริง
- **แนวคิด:** Bottom-Up ทดสอบโมดูลระดับล่าง (Inventory/Cart) ของจริง
  โดยใช้ Driver เป็นตัวเรียกใช้และเตรียมสถานะแทนโมดูลระดับบน (Login)

## Reports

- HTML Report: `playwright-report/index.html`
  (เปิดดูด้วย `npx playwright show-report`)
- JSON Report: `reports/results.json`
- สรุปผล: `reports/test-summary.md`