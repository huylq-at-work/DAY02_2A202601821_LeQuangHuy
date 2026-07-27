# Problem 4 — Xử lý lỗi CI/CD khi deploy

- **Lăng kính:** Tốn thời gian (hao phí ở bước tìm kiếm, chờ đợi, định dạng)
- **Ai chịu ảnh hưởng:** DevOps (bản thân); gián tiếp team dev đang chờ deploy

## Problem (1 câu)

Mỗi lần deploy đều có CI/CD xử lý, nhưng khi pipeline báo lỗi thì phải tự vào đọc log, tìm nguyên nhân và xử lý thủ công; context lỗi cũ không được lưu lại để tái dùng.

## Dấu hiệu thật

- Xảy ra **mỗi khi build/CI/CD báo lỗi** → ngắt mạch công việc.
- Cùng loại lỗi có thể phải điều tra lại từ đầu vì không có kho context.

## Hiện trạng / cách đang xử lý

Đã tích hợp AI: quản lý build, tự động xử lý lỗi khi CI/CD báo lỗi, và tự log lại context các lỗi có thể gặp để cải thiện phương án giải quyết trong tương lai.

## Problem Card

**Problem 1 câu:** Mỗi khi pipeline CI/CD báo lỗi, DevOps phải tự đọc log, tìm nguyên nhân và xử lý thủ công; cùng loại lỗi thường phải điều tra lại từ đầu vì không có kho context tích lũy.

**Actor:** DevOps engineer phụ trách pipeline deploy; team dev đang chờ build xanh để release.

**Thời điểm / bối cảnh:** Mỗi lần deploy khi CI/CD fail.

**Current workflow:**
1. CI/CD chạy khi deploy
2. Pipeline báo lỗi
3. DevOps mở log, đọc, tìm nguyên nhân
4. Nhớ lại / tra cứu cách từng xử lý lỗi tương tự
5. Sửa (config / script / retry)
6. Chạy lại pipeline và xác minh xanh

**Bottleneck:** Bước 3–4 — đọc log và tìm nguyên nhân, đặc biệt với lỗi lặp lại phải điều tra lại từ đầu.

**Impact:** Ngắt mạch công việc mỗi lần fail; block team đang chờ deploy; kiến thức xử lý lỗi không được tích lũy để tái dùng.

**Success metric:** Giảm thời gian trung bình từ lúc CI/CD báo lỗi đến khi pipeline xanh trở lại; giảm số lần phải điều tra lại cùng một loại lỗi nhờ kho context.

**Non-AI alternative:** Runbook + rule auto-retry cho lỗi đã biết (flaky test, timeout). Đủ cho lỗi có pattern cố định, chưa xử lý được lỗi mới hoặc đa nguyên nhân.

**AI hypothesis:** AI đọc log lỗi, đối chiếu kho context lỗi cũ, gợi ý nguyên nhân + cách xử lý kèm độ tin cậy; đồng thời ghi lại context để lần sau tra nhanh.

**Quick gut:** Workflow (nghiêng Agent nếu để AI tự apply fix — cần boundary rõ).

### Draft current workflow

```text
CURRENT STATE
[1 CI/CD chạy khi deploy]
→ [2 Pipeline báo lỗi]
→ [3 Đọc log, tìm nguyên nhân]        <-- nghẽn
→ [4 Nhớ/tra cách xử lý lỗi tương tự]  <-- nghẽn (lỗi lặp lại điều tra lại từ đầu)
→ [5 Sửa config/script/retry]
→ [6 Chạy lại + xác minh xanh]
```

### Draft future workflow

```text
FUTURE STATE
[1 CI/CD fail]
→ [2 AI đọc log + tra kho context lỗi]         -- Workflow
→ [3 AI gợi ý nguyên nhân + fix + độ tin cậy]  -- Workflow
→ [4 DevOps duyệt/áp dụng fix]                 <-- human boundary
        (chỉ tự apply cho lỗi an toàn đã whitelist)
→ [5 Chạy lại + AI ghi context mới vào kho]

Fallback: AI không nhận ra lỗi → DevOps điều tra tay như cũ, rồi bổ sung vào kho context.
```
