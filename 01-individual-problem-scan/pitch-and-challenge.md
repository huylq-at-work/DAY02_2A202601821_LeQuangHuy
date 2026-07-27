# Pitch + Câu hỏi muốn nhóm challenge (Phase 2)

## Card muốn pitch nhất

**Problem #2 — Tổng hợp & phân loại report product.**

Vì sao chọn card này để pitch:

- Có con số cứng và dễ hình dung: 8 lỗi/ngày, 3/4 là lỗi người dùng → công việc thật là tìm ~2 bug hệ thống.
- Bottleneck nằm gọn ở một bước (phân loại), dễ vẽ before/after.
- Là bài toán phân loại kinh điển, khớp bối cảnh lớp: AI cho doanh nghiệp technical.
- So sánh Rule / Workflow / Agent rõ ràng, dễ tạo tranh luận.

## Dàn ý pitch (~60–90 giây)

1. **Mở bằng con số:** mỗi ngày report có ~8 lỗi, nhưng 6/8 là lỗi thao tác người dùng — việc thật là lọc ra ~2 bug hệ thống trước khi chúng ảnh hưởng người dùng.
2. **Actor + workflow:** quản lý sản phẩm, mỗi ngày kéo log → đọc và phân loại → viết 3 report → giao dev sửa.
3. **Bottleneck:** khâu phân loại. Nhầm 1 bug hệ thống thành "lỗi người dùng" nghĩa là bug thật bị bỏ sót.
4. **Impact:** lặp lại mỗi ngày; sai sót tích tụ thành nợ kỹ thuật và ảnh hưởng người dùng cuối.
5. **Future workflow:** AI phân loại kèm độ tin cậy + draft report, con người duyệt các case mơ hồ / nghiêm trọng và chốt bug cần sửa.
6. **Ranh giới:** AI không tự chốt bỏ qua lỗi nào; case độ tin cậy thấp đẩy về review tay.
7. **Chốt mức:** đây là Workflow, không phải Agent — các bước tuyến tính, con người vẫn là người quyết cuối.

## Câu hỏi tôi muốn nhóm challenge

Nhắm thẳng vào các điểm tôi chưa chắc:

1. Success metric "phân loại đúng" nên đo bằng gì, và lấy ground truth (nhãn đúng) ở đâu để so?
2. Nếu Rule theo mã lỗi / pattern log đã xử lý được 70–80% case, thì phần AI có còn đáng làm không?
3. Rủi ro nguy hiểm nhất: AI gán nhầm bug hệ thống thành "lỗi người dùng" với độ tin cậy cao — ai/cơ chế nào bắt được lỗi này?
4. 8 lỗi/ngày có đủ khối lượng để đáng dựng một workflow AI, hay chỉ cần checklist + template là đủ?
5. Có nên gộp cả 3 loại report (lỗi / tính năng / hành vi) vào một workflow, hay chỉ nên tự động hóa riêng report lỗi trước?

## Câu hỏi dự phòng cho #4 và #5 (nếu nhóm muốn bàn thêm)

- **#4 CI/CD:** ranh giới ở đâu giữa "AI đề xuất fix" và "AI tự apply fix"? Ai rollback nếu AI sửa sai trên môi trường thật?
- **#5 Biên bản họp:** đã có nhiều tool ghi biên bản sẵn — điểm khác biệt thật là gì, và ai chịu trách nhiệm duyệt biên bản trước khi gửi?
