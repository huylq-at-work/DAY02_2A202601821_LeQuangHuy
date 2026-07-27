# Problem 5 — Ghi biên bản daily meeting

- **Lăng kính:** Khó khăn từ người khác (ai đang tắc nghẽn, phàn nàn liên tục)
- **Ai chịu ảnh hưởng:** Nhân viên bị giao ghi chép (người khác); cả team

## Problem (1 câu)

Mỗi daily meeting một nhân viên phải ngồi ghi lại toàn bộ nội dung buổi họp nên không còn thời gian tham gia việc khác; do thiếu nhân sự nên việc này luôn rơi vào một bạn nhân viên.

## Dấu hiệu thật

- Mỗi buổi họp có **1 người bị "khóa"** hoàn toàn vào việc ghi chép → mất năng suất trong họp.
- Lặp lại **hằng ngày** (daily meeting).
- Nguyên nhân cấu trúc: thiếu nhân sự nên luôn là cùng một bạn.

## Hiện trạng / cách đang xử lý

Đã dùng AI để tự động ghi lại những gì xảy ra trong buổi họp.

## Problem Card

**Problem 1 câu:** Mỗi daily meeting một nhân viên phải ghi lại toàn bộ nội dung nên không tham gia được thảo luận; do thiếu nhân sự việc này luôn rơi vào cùng một bạn.

**Actor:** Nhân viên bị giao ghi biên bản; cả team dự họp; người chủ trì cần biên bản + action item.

**Thời điểm / bối cảnh:** Mỗi buổi daily meeting.

**Current workflow:**
1. Buổi họp bắt đầu
2. Một nhân viên gõ lại nội dung realtime
3. Người đó ít tham gia thảo luận vì bận ghi
4. Sau họp chỉnh lại biên bản
5. Gửi biên bản + action item cho team

**Bottleneck:** Bước 2–3 — một người bị "khóa" hoàn toàn vào việc ghi chép suốt buổi.

**Impact:** Mỗi buổi mất năng suất của 1 người; biên bản phụ thuộc 1 cá nhân nên dễ sót ý.

**Success metric:** Không còn ai bị khóa vào việc ghi (người ghi tham gia thảo luận đầy đủ); biên bản + action item sẵn ngay sau họp thay vì phải gõ lại toàn bộ.

**Non-AI alternative:** Luân phiên người ghi + template biên bản. Giảm gánh cho một người nhưng vẫn tốn một người mỗi buổi.

**AI hypothesis:** AI ghi âm / nhận dạng giọng nói → tạo biên bản + trích action item; người chủ trì duyệt lại trước khi gửi.

**Quick gut:** Workflow.

### Draft current workflow

```text
CURRENT STATE
[1 Họp bắt đầu]
→ [2 1 nhân viên gõ biên bản realtime]  <-- nghẽn (1 người bị khóa)
→ [3 Người đó không tham gia thảo luận]
→ [4 Chỉnh lại biên bản sau họp]
→ [5 Gửi biên bản + action item]
```

### Draft future workflow

```text
FUTURE STATE
[1 AI ghi + transcribe buổi họp]          -- Workflow
→ [2 AI tóm tắt + trích action item]      -- Workflow
→ [3 Người chủ trì duyệt/sửa biên bản]    <-- human boundary
→ [4 Gửi team]

Fallback: AI nghe/hiểu sai (thiếu context doanh nghiệp, thuật ngữ nội bộ, nội dung họp hôm trước) → người chủ trì bổ sung.
Lưu ý dữ liệu: ghi âm cuộc họp cần được team đồng thuận.
```
