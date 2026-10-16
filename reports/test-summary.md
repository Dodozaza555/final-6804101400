# Test Summary

รันด้วย `npx playwright test` (Chromium, workers: 1) บนระบบ https://www.saucedemo.com/

| ข้อ | Test | ผล |
|---|---|---|
| UT-01 | UT-01.1: empty username and password | Passed |
| UT-01 | UT-01.2: missing password | Passed |
| UT-01 | UT-01.3: invalid login details | Passed |
| UT-02 | UT-02: product button state Add to cart -> Remove -> Add to cart | Passed |
| IT-01 | IT-01: top-down REAL Login -> browser-level Inventory STUB | Passed |
| IT-02 | IT-02: DRIVER login state -> REAL Inventory and Cart | Passed |
| ST-01 | ST-01: complete purchase of two products | Passed |
| ST-02 | ST-02: checkout validation and recovery | Passed |

**รวม:** 8 Passed / 0 Failed

**ข้อผิดพลาดที่พบ:** ไม่มี
