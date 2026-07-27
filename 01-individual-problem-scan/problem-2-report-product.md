# Problem 2 — Tổng hợp & phân loại report của product

- **Lăng kính:** AI hỗ trợ tốt hơn (cần đọc hiểu ngữ cảnh, tổng hợp đa nguồn)
- **Ai chịu ảnh hưởng:** Quản lý (bản thân) + team sửa lỗi; gián tiếp là người dùng cuối

## Problem (1 câu)

Hằng ngày phải viết 3 loại report từ hoạt động của product trên server (lỗi / tính năng / tracking hành vi), trong đó bước sàng lọc lỗi để tìm ra bug hệ thống thật là nghẽn chính.

## Dấu hiệu thật

- **Report lỗi:** trung bình **8 lỗi/ngày**, trong đó **3/4 là lỗi người dùng** → chỉ ~2 lỗi là bug hệ thống thật cần sửa.
- **Report tính năng:** gom từ những gì người dùng suggest.
- **Report tracking hành vi:** gom từ những thao tác của người dùng.
- **Nghẽn:** phải sàng 8 lỗi để lọc ~2 bug thật; nếu phân loại sai, đúng bug thật đó bị chôn trong nhóm "lỗi người dùng" và không được sửa.

## Hiện trạng / cách đang xử lý

Đã tạo schedule cho AI tự động chạy phân tích report hằng ngày.

## Problem Card

**Problem 1 câu:** Mỗi ngày quản lý phải đọc và phân loại ~8 lỗi (3/4 là lỗi người dùng) cùng suggestion tính năng và dữ liệu hành vi, nghẽn ở khâu sàng lọc để tìm ra ~2 bug hệ thống thật cần sửa.

**Actor:** Quản lý sản phẩm theo dõi report vận hành product hằng ngày; team dev nhận bug đã phân loại.

**Thời điểm / bối cảnh:** Hằng ngày, khi tổng hợp report từ hoạt động product trên server.

**Current workflow:**
1. Kéo log/report lỗi, suggestion và dữ liệu hành vi từ server
2. Đọc từng lỗi và phân loại: bug hệ thống / lỗi thao tác người dùng / hành vi người dùng
3. Gom suggestion thành report tính năng
4. Tổng hợp dữ liệu tracking hành vi
5. Viết 3 report
6. Ưu tiên bug hệ thống và giao dev sửa

**Bottleneck:** Bước 2 — sàng 8 lỗi/ngày để lọc ~2 bug thật; dễ nhầm bug hệ thống thành lỗi người dùng.

**Impact:** Diễn ra mỗi ngày. Phân loại sai → bug hệ thống bị bỏ sót, ảnh hưởng người dùng cuối và tích tụ nợ kỹ thuật.

**Success metric:** Giảm thời gian đọc + phân loại report mỗi ngày; không tăng (giảm được càng tốt) số bug hệ thống bị gán nhầm thành "lỗi người dùng".

**Non-AI alternative:** Rule phân loại theo mã lỗi / pattern log cố định + template 3 report. Đủ cho lỗi có signature rõ, chưa xử lý được lỗi mơ hồ cần đọc ngữ cảnh.

**AI hypothesis:** AI đọc log + mô tả lỗi, đề xuất phân loại kèm độ tin cậy và draft 3 report; người duyệt các case mơ hồ / nghiêm trọng.

**Quick gut:** Workflow.

### Draft current workflow

```text
CURRENT STATE
[1 Kéo log/report từ server]
→ [2 Đọc + phân loại 8 lỗi/ngày]  <-- nghẽn (sàng ra ~2 bug thật)
→ [3 Gom suggestion → report tính năng]
→ [4 Tổng hợp tracking hành vi]
→ [5 Viết 3 report]
→ [6 Ưu tiên + giao dev sửa]
```

### Draft future workflow

```text
FUTURE STATE
[1 Auto-pull log/report]              -- Rule/script
→ [2 AI phân loại + gắn độ tin cậy]  -- Workflow
→ [3 AI draft 3 report]              -- Workflow
→ [4 Người duyệt case mơ hồ/nghiêm trọng + chốt bug cần sửa]  <-- human boundary
→ [5 Giao dev sửa]

Fallback: AI phân loại độ tin cậy thấp hoặc sai → đẩy sang review tay.
```
