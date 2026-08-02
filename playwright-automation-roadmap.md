# Checklist Lộ Trình Đào Tạo Automation Tester (Playwright) & Career Path

> Mục tiêu: đưa một Manual Tester lên được Automation Tester chạy job trong CI trong ~12 tuần, có tiêu chí "đạt" rõ ràng cho từng bước thay vì học theo cảm tính.

---

## Giai đoạn 0 — Nền tảng (Tuần 1–2)

- [ ] JavaScript/TypeScript cơ bản: biến, hàm, array method, `async/await`, Promise
- [ ] Node.js & npm: `package.json`, script, cài package, quản lý version
- [ ] Git: branch, commit, pull request, resolve conflict
- [ ] HTML/DOM & CSS selector: `id`, `class`, attribute, quan hệ cha–con
- [ ] DevTools: tab Network, Console, Elements, copy selector
- [ ] HTTP cơ bản: method, status code, header, cookie, request/response body

**Tiêu chí đạt:** tự viết được một script Node đọc file JSON, gọi một REST API và in kết quả ra console.

---

## Giai đoạn 1 — Playwright cơ bản (Tuần 3–4)

- [ ] Cài đặt `@playwright/test`, hiểu cấu trúc project và `playwright.config.ts`
- [ ] Chạy test trên Chromium / Firefox / WebKit
- [ ] Locator: `getByRole`, `getByText`, `getByLabel`, `getByTestId` (ưu tiên hơn CSS/XPath)
- [ ] Action: `click`, `fill`, `press`, `selectOption`, `setInputFiles`
- [ ] Assertion: `expect(locator).toBeVisible()`, `toHaveText`, `toHaveURL`, `toHaveCount`
- [ ] Auto-waiting: hiểu vì sao **không** dùng `waitForTimeout` cố định
- [ ] Codegen (`npx playwright codegen`) — dùng để học, không dùng để giao nộp
- [ ] Trace Viewer & HTML report: đọc được trace của một test fail

**Tiêu chí đạt:** viết 5 test cho luồng đăng nhập (thành công, sai mật khẩu, bỏ trống, khóa tài khoản, đăng xuất) chạy xanh 3 lần liên tiếp.

---

## Giai đoạn 2 — Viết test bền, không flaky (Tuần 5–6)

- [ ] Page Object Model / Fixture pattern: tách locator ra khỏi test case
- [ ] Fixture tùy biến của Playwright (`test.extend`)
- [ ] Test data: tách data ra khỏi logic, tránh hard-code
- [ ] Độc lập giữa các test: mỗi test tự dựng và tự dọn state
- [ ] `storageState` để tái dùng phiên đăng nhập, không login lại mỗi test
- [ ] Xử lý iframe, tab mới, dialog, upload/download
- [ ] Network: `page.route` để mock/stub, `waitForResponse` cho luồng bất đồng bộ
- [ ] Nhận diện và xử lý nguyên nhân flaky: race condition, animation, dữ liệu dùng chung

**Tiêu chí đạt:** bộ 20 test chạy song song (`workers > 1`), 10 lần liên tiếp không có test nào flaky.

---

## Giai đoạn 3 — Mở rộng phạm vi (Tuần 7–9)

- [ ] API testing bằng `request` fixture; kết hợp API để setup dữ liệu cho UI test
- [ ] Visual regression: `toHaveScreenshot`, quản lý baseline
- [ ] Test theo nhiều viewport / thiết bị mobile emulation
- [ ] Phân loại test bằng tag/project: `@smoke`, `@regression`, `@critical`
- [ ] Kiểm thử đa vai trò người dùng (admin / user / guest)
- [ ] Accessibility check cơ bản (`@axe-core/playwright`)
- [ ] Quản lý môi trường: dev / staging / prod qua biến môi trường

**Tiêu chí đạt:** có bộ smoke test < 5 phút và bộ regression đầy đủ, chạy được trên cả staging và dev chỉ bằng đổi biến môi trường.

---

## Giai đoạn 4 — Đưa vào CI/CD (Tuần 10–12)

- [ ] Chạy Playwright trong Docker image chính thức
- [ ] Pipeline CI: trigger theo PR và theo lịch (nightly)
- [ ] Sharding để chia test chạy song song nhiều máy
- [ ] Publish report + trace + video của test fail thành artifact
- [ ] Retry có kiểm soát (`retries: 1`) và theo dõi danh sách test flaky
- [ ] Quality gate: PR không merge được nếu smoke test đỏ
- [ ] Cảnh báo kết quả về kênh chat của team

**Tiêu chí đạt:** mỗi PR tự chạy smoke test và chặn merge khi fail; nightly regression gửi báo cáo tự động.

---

## Giai đoạn 5 — Nâng cao (sau tuần 12)

- [ ] Component testing cho React/Vue
- [ ] Kiểm thử hiệu năng nhẹ: đo thời gian tải, số request, kích thước bundle
- [ ] Contract testing giữa frontend và backend
- [ ] Test data management: seeding, cleanup job, dữ liệu ẩn danh
- [ ] Tự viết reporter / dashboard theo dõi độ ổn định của bộ test
- [ ] Ứng dụng AI hỗ trợ: sinh test case từ mô tả nghiệp vụ, phân tích log fail, gợi ý locator ổn định hơn

---

## Career Path

| Cấp độ | Vai trò | Làm được gì | Tín hiệu sẵn sàng lên cấp |
|---|---|---|---|
| L1 | Manual Tester | Viết & thực thi test case thủ công, report bug rõ ràng | Tự động hóa được luồng hồi quy mình đang test tay |
| L2 | Automation Tester | Viết test Playwright ổn định, chạy trong CI | Bộ test của mình không flaky, người khác đọc hiểu và sửa được |
| L3 | Senior Automation Tester | Thiết kế framework, chuẩn hóa pattern, review code test | Người mới onboard vào framework trong 1 tuần |
| L4 | SDET | Viết cả tool nội bộ, test data service, API/component/perf test | Đội dev chủ động dùng tool do mình xây |
| L5 | QA Lead / Test Architect | Chiến lược kiểm thử, quality gate, đo lường chất lượng, đào tạo | Tỷ lệ lỗi lọt production giảm và duy trì được theo quý |

### Chỉ số theo dõi hiệu quả của lộ trình

- Tỷ lệ test case hồi quy đã tự động hóa (%)
- Thời gian chạy bộ smoke test (phút)
- Tỷ lệ test flaky trên tổng số test (%)
- Số lỗi lọt production mỗi kỳ release
- Thời gian từ commit đến khi biết kết quả kiểm thử

---

## Nguyên tắc khi đào tạo

1. **Không dạy công cụ trước khi dạy tư duy** — hiểu vì sao test đó tồn tại trước khi viết nó.
2. **Mỗi bước phải có tiêu chí đạt đo được**, tránh học xong không biết mình đã đủ chưa.
3. **Ưu tiên test bền hơn test nhiều** — 20 test tin cậy tốt hơn 100 test hay đỏ vặt.
4. **Vào CI càng sớm càng tốt** — test không chạy tự động thì sớm muộn cũng bị bỏ.
5. **Người học phải tự sửa test hỏng của chính mình**, đó mới là lúc kiến thức đọng lại.
