# Draft Workflow trước/sau — Top 3

Ký hiệu: `<-- nghẽn` = bottleneck · `<-- human boundary` = điểm con người kiểm soát · `Rule/Workflow` = mức AI ở bước đó.

---

## Problem #2 — Tổng hợp & phân loại report product

**Context:** Quản lý sản phẩm, mỗi ngày theo dõi report vận hành product trên server. Trung bình ~8 lỗi/ngày, trong đó 3/4 là lỗi thao tác người dùng → chỉ ~2 là bug hệ thống thật cần sửa. Ngoài report lỗi còn có report tính năng (từ suggestion của user) và report tracking hành vi. Nghẽn ở khâu phân loại: nhầm 1 bug thành "lỗi user" là bug thật bị bỏ sót.

```text
CURRENT STATE
[1 Kéo log/report từ server]
→ [2 Đọc + phân loại 8 lỗi/ngày]  <-- nghẽn (sàng ra ~2 bug thật)
→ [3 Gom suggestion → report tính năng]
→ [4 Tổng hợp tracking hành vi]
→ [5 Viết 3 report]
→ [6 Ưu tiên + giao dev sửa]

FUTURE STATE
[1 Auto-pull log/report]              -- Rule/script
→ [2 AI phân loại + gắn độ tin cậy]  -- Workflow
→ [3 AI draft 3 report]              -- Workflow
→ [4 Người duyệt case mơ hồ/nghiêm trọng + chốt bug cần sửa]  <-- human boundary
→ [5 Giao dev sửa]

Fallback: AI phân loại độ tin cậy thấp hoặc sai → đẩy sang review tay.
```

| Metric | Trước | Sau kỳ vọng |
|---|---|---|
| Số bước | 6 | 5 |
| Bước thủ công | 6/6 | 2/5 (duyệt + giao) |
| Bottleneck | Phân loại 8 lỗi | Duyệt case mơ hồ |
| Risk mới | — | AI phân loại sai bug ↔ lỗi user |

---

## Problem #4 — Xử lý lỗi CI/CD

**Context:** DevOps ở công ty truyền thông, mỗi lần deploy đều qua pipeline CI/CD. Khi pipeline báo lỗi, phải tự vào đọc log, tìm nguyên nhân và xử lý thủ công. Vấn đề lớn nhất: cùng một loại lỗi thường phải điều tra lại từ đầu vì kiến thức xử lý không được tích lũy vào một kho context dùng lại được.

```text
CURRENT STATE
[1 CI/CD chạy khi deploy]
→ [2 Pipeline báo lỗi]
→ [3 Đọc log, tìm nguyên nhân]         <-- nghẽn
→ [4 Nhớ/tra cách xử lý lỗi tương tự]  <-- nghẽn (lỗi lặp lại điều tra lại từ đầu)
→ [5 Sửa config/script/retry]
→ [6 Chạy lại + xác minh xanh]

FUTURE STATE
[1 CI/CD fail]
→ [2 AI đọc log + tra kho context lỗi]         -- Workflow
→ [3 AI gợi ý nguyên nhân + fix + độ tin cậy]  -- Workflow
→ [4 DevOps duyệt/áp dụng fix]                 <-- human boundary
        (chỉ tự apply cho lỗi an toàn đã whitelist)
→ [5 Chạy lại + AI ghi context mới vào kho]

Fallback: AI không nhận ra lỗi → DevOps điều tra tay như cũ, rồi bổ sung vào kho context.
```

| Metric | Trước | Sau kỳ vọng |
|---|---|---|
| Số bước | 6 | 5 |
| Bước thủ công | 4/6 | 1/5 (duyệt fix) |
| Bottleneck | Đọc log + tìm nguyên nhân | Duyệt fix do AI đề xuất |
| Risk mới | — | AI gợi ý sai / tự apply hỏng môi trường |

---

## Problem #5 — Ghi biên bản daily meeting

**Context:** Mỗi buổi daily meeting cần một người ghi lại toàn bộ nội dung. Do team thiếu nhân sự, việc này luôn rơi vào cùng một bạn nhân viên. Suốt buổi họp bạn đó bị "khóa" vào việc gõ biên bản nên không tham gia được thảo luận, và biên bản phụ thuộc vào một cá nhân nên dễ sót ý.

```text
CURRENT STATE
[1 Họp bắt đầu]
→ [2 1 nhân viên gõ biên bản realtime]  <-- nghẽn (1 người bị khóa)
→ [3 Người đó không tham gia thảo luận]
→ [4 Chỉnh lại biên bản sau họp]
→ [5 Gửi biên bản + action item]

FUTURE STATE
[1 AI ghi + transcribe buổi họp]          -- Workflow
→ [2 AI tóm tắt + trích action item]      -- Workflow
→ [3 Người chủ trì duyệt/sửa biên bản]    <-- human boundary
→ [4 Gửi team]

Fallback: AI nghe/hiểu sai (thiếu context doanh nghiệp, thuật ngữ nội bộ, nội dung họp hôm trước) → người chủ trì bổ sung.
Lưu ý dữ liệu: ghi âm cuộc họp cần được team đồng thuận.
```

| Metric | Trước | Sau kỳ vọng |
|---|---|---|
| Số bước | 5 | 4 |
| Người bị khóa vào ghi chép | 1/buổi | 0/buổi |
| Bottleneck | 1 người gõ realtime | Chủ trì duyệt biên bản |
| Risk mới | — | AI nghe/hiểu sai vì thiếu context doanh nghiệp và nội dung meeting hôm trước; dữ liệu ghi âm nhạy cảm |
