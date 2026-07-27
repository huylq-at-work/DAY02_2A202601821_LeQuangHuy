# 01 — Individual Problem Scan

**Học viên:** Lê Quang Huy — 2A202601821
**Bối cảnh:** Hà Nội — vừa đi làm (quản lý sản phẩm / DevOps / truyền thông) vừa đi học, thu nhập không đều.

## Scan rộng theo 4 lăng kính

### 1. Lặp lại — việc diễn ra thường xuyên, cần chuẩn hóa

| # | Problem quan sát được | Ai chịu ảnh hưởng? | Dấu hiệu thật |
|---|---|---|---|
| 1 | Người thu nhập không đều, mỗi ngày phải quyết định chi cho ăn uống nhưng không tính được dư địa thật còn lại đến các mốc nghĩa vụ cố định (trả nợ, tiền nhà) | Bản thân (thu nhập không đều ở HN) | Chi ~200k/ngày cho ăn uống ở công ty. Chi/nghĩa vụ cố định hàng tháng ~16tr (trả nợ 2tr, chi phí AI ~5tr [$200], sinh hoạt 5tr, ăn chơi với bạn bè 2tr, tích lũy 2tr), chưa gồm ~4–6tr ăn uống. Hậu quả thật: **thường xuyên bị trừ vượt / charge thêm trên thẻ ghi nợ**. |

### 2. Tốn thời gian — hao phí ở bước tìm kiếm, chờ đợi, định dạng

| # | Problem quan sát được | Ai chịu ảnh hưởng? | Dấu hiệu thật |
|---|---|---|---|
| 4 | Mỗi khi pipeline CI/CD báo lỗi phải tự vào đọc log, tìm nguyên nhân và xử lý thủ công; context lỗi cũ không được lưu để tái dùng | DevOps (bản thân); gián tiếp team dev đang chờ deploy | Ngắt mạch công việc mỗi lần build fail; cùng loại lỗi phải điều tra lại từ đầu |

### 3. AI hỗ trợ tốt hơn — cần đọc hiểu ngữ cảnh, tổng hợp đa nguồn

| # | Problem quan sát được | Ai chịu ảnh hưởng? | Dấu hiệu thật |
|---|---|---|---|
| 2 | Hằng ngày viết 3 loại report từ hoạt động product trên server: report lỗi (phân loại bug hệ thống vs lỗi người dùng), report tính năng (từ suggestion của user), report tracking hành vi user — rồi ưu tiên và sửa | Quản lý (bản thân) + team sửa lỗi; gián tiếp là người dùng cuối | Report lỗi: TB **8 lỗi/ngày, 3/4 là lỗi người dùng** → chỉ ~2 bug hệ thống thật cần sửa. Report tính năng: gom từ suggestion user. Report tracking: gom từ thao tác user. Nghẽn: sàng 8 lỗi để lọc ~2 bug thật; nếu phân loại sai, bug thật bị chôn trong nhóm "lỗi user". |
| 3 | Mỗi tối sau giờ học phải tổng hợp kiến thức từ trang thông tin trường, hoàn thiện bài tập và xử lý công việc với đồng nghiệp | Bản thân (vừa học vừa làm) | Lặp lại mỗi tối, phải gom nhiều nguồn rời rạc (trang trường + bài tập + trao đổi công việc) |

### 4. Khó khăn từ người khác — ai đang tắc nghẽn, phàn nàn liên tục

| # | Problem quan sát được | Ai chịu ảnh hưởng? | Dấu hiệu thật |
|---|---|---|---|
| 5 | Mỗi daily meeting một nhân viên phải ngồi ghi lại toàn bộ nội dung buổi họp nên không còn thời gian tham gia việc khác; do thiếu nhân sự nên luôn rơi vào một bạn nhân viên | Nhân viên bị giao ghi chép (người khác); cả team | Mỗi buổi họp 1 người bị "khóa" vào việc ghi chép, mất năng suất; lặp lại hằng ngày |

## Top 3 (Phase 2)

Bối cảnh pitch: lớp thiên công nghệ, các công ty technical, chủ đề xử lý vấn đề bằng AI cho doanh nghiệp. Chọn 3 problem đa dạng mảng và dễ tiếp cận với nhiều người.

| Rank | Problem | Vì sao chọn | Điều còn chưa chắc |
|---|---|---|---|
| 1 | #2 — Tổng hợp & phân loại report product | Có số cứng rõ nhất (8 lỗi/ngày, 3/4 lỗi người dùng); workflow rõ; phân loại là bài toán AI kinh điển trong doanh nghiệp | Định nghĩa "phân loại đúng" cần ground truth để đo |
| 2 | #4 — Xử lý lỗi CI/CD | Rất quen thuộc với dân kỹ thuật; đúng chủ đề AI cho doanh nghiệp; ranh giới Workflow ↔ Agent rõ để thảo luận | Chưa có baseline thời gian; ranh giới AI tự apply fix hay chỉ đề xuất |
| 3 | #5 — Ghi biên bản daily meeting | Ai trong doanh nghiệp cũng hiểu; dễ tiếp cận cả lớp; AI note-taking đang phổ biến | Nhiều tool sẵn có; đo lợi ích thật hơi khó |

Problem Card đầy đủ + workflow trước/sau của từng bài nằm trong file problem tương ứng bên dưới.

## Chi tiết từng problem (file riêng)

Mỗi problem được note riêng biệt trong một file:

1. [Problem 1 — Quyết định chi tiêu khi thu nhập không đều](problem-1-chi-tieu-thu-nhap.md)
2. [Problem 2 — Tổng hợp & phân loại report của product](problem-2-report-product.md)
3. [Problem 3 — Tổng hợp kiến thức & việc buổi tối](problem-3-tong-hop-kien-thuc.md)
4. [Problem 4 — Xử lý lỗi CI/CD khi deploy](problem-4-devops-cicd.md)
5. [Problem 5 — Ghi biên bản daily meeting](problem-5-bien-ban-hop.md)

## Phase 2 — Tài liệu kèm theo

- [Draft workflow trước/sau — Top 3](top-3-workflows.md)
- [Pitch + câu hỏi muốn nhóm challenge](pitch-and-challenge.md)
