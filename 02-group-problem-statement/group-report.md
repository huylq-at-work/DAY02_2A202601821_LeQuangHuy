# Group Report — Day 02

## Thành viên nhóm

| STT | Họ và tên | Mã học viên | Vai trò trong nhóm |
|-----|-----------|-------------|--------------------|
| 1   | Lê Quang Huy |  2A202601821  |                    |
| 2   | Vũ Đức Anh   |               |                    |
| 3   | Phạm Thị Liên |              |                    |
| 4   | Đào Đức Mạnh |               |                    |

---

# Phase 3 — Group Convergence

## Bước 3.1 — Trình bày top candidate của từng người

| # | Người đưa ra | Candidate problem | Người gặp vấn đề | Điểm nghẽn | Cảm nhận nhanh |
|---|---|---|---|---|---|
| 1 | Đức Anh | Daily report phải nộp ở 2 nơi (Discord và repo GitHub), nội dung 2 nơi không khớp nhau | Học viên trong khóa học | Làm cùng một việc 2 lần, ở 2 định dạng khác nhau | Mạnh, Liên, Huy suggest không dùng AI — chi phí bỏ ra không đáng so với vấn đề (fix bằng process/rule) |
| 2 | Mạnh | Assignment classification — tổng hợp tài liệu từ nhiều nguồn, dùng OCR AI chuyển thành text rồi phân loại dạng đề | Học viên cần tổng hợp bài tập từ nhiều nguồn | Đọc + phân loại thủ công tài liệu từ nhiều nguồn | Giảm chi phí từ 200 phút/10 bài xuống 60 phút/10 bài. Mọi người đều đồng ý đây là candidate tốt |
| 3 | Huy | Problem #2 — Tổng hợp & phân loại report product (report lỗi/tính năng/hành vi) | Quản lý sản phẩm | Khâu phân loại 8 lỗi/ngày để lọc ra bug hệ thống thật | Mọi người chốt hết là candidate hợp lý. Đức Anh đánh giá quy trình tích hợp nhiều bước classification + suggest phương án xử lý, và muốn nêu rõ quy trình kiểm soát đầu ra (human review) |
| 4 | Liên | Thẩm định hồ sơ cho vay — chuyên viên tốn nhiều thời gian xử lý giấy tờ hồ sơ vay; quy trình hiện tại: tiếp nhận hồ sơ → xử lý hồ sơ → phê duyệt; dùng LLM xử lý thông tin | Chuyên viên thẩm định tín dụng | Xử lý giấy tờ/hồ sơ thủ công trước khi phê duyệt | Đang là hướng nhóm nghiêng về chọn |

## Bước 3.2 — Gom trùng / cluster

| Cluster | Candidates included | Pattern chung | Ghi chú |
|---|---|---|---|
| A — Report/nộp trùng lặp | Daily report (Đức Anh) | Cùng một thông tin phải nhập ở nhiều nơi | Nhóm nghiêng về xử lý bằng rule/process, không cần AI |
| B — Đọc tài liệu + phân loại | Assignment classification (Mạnh), Report product (Huy), Thẩm định hồ sơ vay (Liên) | Tổng hợp thông tin từ nhiều nguồn/định dạng rồi phân loại để ra quyết định tiếp theo | Cả 3 candidate đều là bài toán classification + AI hỗ trợ; khác nhau ở mức độ rủi ro khi AI sai |

## Bước 3.3 — Shortlist

| Candidate | Vì sao vào shortlist | Rủi ro / điều chưa rõ |
|---|---|---|
| Assignment classification (Mạnh) | Có baseline thời gian rõ (200 phút → 60 phút/10 bài), workflow đơn giản, cả nhóm đồng thuận | Quy mô nhỏ (bối cảnh học tập), impact với doanh nghiệp thấp hơn |
| Report product (Huy) | Workflow rõ, có số liệu (8 lỗi/ngày, 3/4 lỗi user), cần kiểm soát đầu ra rõ ràng | Cần định nghĩa ground truth để đo "phân loại đúng" |
| Thẩm định hồ sơ cho vay (Liên) | Bối cảnh doanh nghiệp rõ (tài chính/ngân hàng), rủi ro cao nên đáng phân tích boundary kỹ, quy trình 3 bước dễ vẽ workflow | Dữ liệu hồ sơ vay nhạy cảm; sai sót AI có hậu quả tài chính/pháp lý; cần validate thêm với người trong ngành |

Daily report (Đức Anh) không vào shortlist: cả nhóm (Mạnh, Liên, Huy) đã đồng thuận đây là vấn đề nên xử lý bằng process/rule, chi phí làm AI không đáng.

## Bước 3.4 — Score để đồng thuận

| Candidate | Actor rõ | Workflow rõ | Pain có evidence | Impact đo được | Làm trong lab | So sánh R/W/A được | Nhóm hiểu domain | Tổng |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| Assignment classification (Mạnh) | 5 | 5 | 5 | 5 | 5 | 3 | 5 | 33 |
| Report product (Huy) | 4 | 4 | 4 | 4 | 4 | 4 | 4 | 28 |
| Thẩm định hồ sơ cho vay (Liên) | 5 | 5 | 3 | 4 | 3 | 5 | 3 | 28 |

Candidate nhóm chọn:

```text
Thẩm định hồ sơ cho vay (Liên)
```

Vì sao chọn:

- Bối cảnh doanh nghiệp rõ và rủi ro cao — phù hợp để phân tích boundary, human-in-the-loop và so sánh Rule/Workflow/Agent sâu (điểm cao nhất ở tiêu chí này trong 3 candidate).
- Quy trình 3 bước (tiếp nhận → xử lý → phê duyệt) dễ vẽ workflow trước/sau và dễ chỉ ra AI intervention point.
- Đúng chủ đề lớp học (AI xử lý vấn đề cho doanh nghiệp), dễ tạo tranh luận khi thuyết trình.

Vì sao không chọn các candidate còn lại:

- **Assignment classification (Mạnh):** điểm tổng cao nhất và có baseline thời gian rõ nhất (200 phút → 60 phút/10 bài), nhưng bối cảnh học tập nên impact với doanh nghiệp thấp hơn, ít đất để so sánh Rule/Workflow/Agent.
- **Report product (Huy):** workflow và số liệu rõ, nhưng đo "phân loại đúng" khó có ground truth ngay trong lab; rủi ro khi AI sai thấp hơn candidate của Liên nên ít kịch tính hơn khi phân tích boundary.

Nếu có disagreement, nhóm xử lý thế nào:

```text
Chưa phát sinh bất đồng — cả 4 thành viên đồng thuận chọn Thẩm định hồ sơ cho vay sau khi thảo luận.
```

---

# Phase 4 — Quick Validation + Research giải pháp

## Bước 4.1 — Quick validation

> Phần này cần nhóm thực hiện phỏng vấn/khảo sát thật (2–3 người hoặc mini poll) trước khi điền. Chưa điền số liệu vì nhóm chưa thực hiện — không tự bịa số liệu chưa kiểm chứng.

| Nguồn | Số người / số mẫu | Tín hiệu xác nhận | Tín hiệu phản bác | Nhóm sửa problem thế nào |
|---|---:|---|---|---|
| Interview |  |  |  |  |
| Survey / poll |  |  |  |  |
| Log / review / ticket |  |  |  |  |

## Bước 4.2 — Research giải pháp đã có

> Cần tìm 2–3 tool/case thật kèm link nguồn kiểm được. Chưa điền vì nhóm chưa research — tránh dùng claim không có nguồn.

| Nguồn / tool / case | Link | Họ giải quyết phần nào? | Điểm mạnh | Khoảng trống / rủi ro | Bài học cho nhóm |
|---|---|---|---|---|---|
|  |  |  |  |  |  |
|  |  |  |  |  |  |
|  |  |  |  |  |  |

---

# Phase 5 — Workflow + Problem Statement

## Bước 5.1 — Current workflow bản nhóm

| Bước | Actor | Input | Output | Thời gian/tần suất | Ghi chú |
|---|---|---|---|---|---|
| 1 | Chuyên viên thẩm định | Hồ sơ vay (giấy tờ, sao kê, hợp đồng...) | Dữ liệu đã nhập | Mỗi hồ sơ | Nhập tay |
| 2 | Chuyên viên thẩm định | Sao kê, giấy tờ thu nhập | Số liệu đã đọc/trích | ~1–2 giờ/hồ sơ | Đọc thủ công, mỗi loại giấy tờ một định dạng |
| 3 | Chuyên viên thẩm định | Thông tin khách hàng | Kết quả tra CIC | Mỗi hồ sơ | Tra cứu ngoài hệ thống |
| 4 | Chuyên viên thẩm định | Dữ liệu đã trích + CIC | Bảng đối chiếu | ~30–60 phút/hồ sơ | Đối chiếu tay, dễ sai sót khi khối lượng lớn |
| 5 | Chuyên viên thẩm định | Bảng đối chiếu | Đề xuất phê duyệt | Mỗi hồ sơ | Handoff sang cấp phê duyệt |
| 6 | Cấp phê duyệt | Đề xuất | Quyết định duyệt/từ chối | 3–5 ngày kể từ khi tiếp nhận | Bottleneck tổng thể của khách hàng |

Bottleneck chính:

```text
Đọc/trích thủ công giấy tờ (bước 2) và đối chiếu chéo tay (bước 4) — chiếm phần lớn trong 2–4 giờ xử lý/hồ sơ,
đồng thời là nơi dễ phát sinh sai sót khi khối lượng hồ sơ lớn.
```

## Bước 5.2 — Future workflow bản nhóm

```text
Hồ sơ
→ OCR + LLM trích xuất dữ liệu (thu nhập, hợp đồng, sao kê...)     -- Workflow (AI)
→ Đối chiếu chéo tự động + gắn cờ mâu thuẫn (LLM + rule kiểm tra)  -- Workflow (AI + Rule)
→ Mô hình scoring chuyên dụng tính điểm tín dụng                   -- Rule/mô hình đã kiểm toán, không dùng LLM
→ LLM diễn giải điểm số bằng ngôn ngữ tự nhiên                     -- Workflow (AI)
→ Chuyên viên review hồ sơ bị gắn cờ nghi vấn                      <-- human boundary
→ Chuyên viên đề xuất
→ Cấp phê duyệt ra quyết định cuối                                 <-- human boundary

Fallback: AI trích xuất/gắn cờ sai → chuyên viên phát hiện qua review hồ sơ nghi vấn (cần thêm cơ chế
random sampling để audit các hồ sơ không bị gắn cờ, tránh bỏ sót sai sót trích xuất).
```

Before/after impact:

| Metric | Trước | Sau kỳ vọng | Ghi chú |
|---|---:|---:|---|
| Thời gian xử lý/hồ sơ | 2–4 giờ | 30–45 phút | Target chính |
| Thời gian khách hàng chờ | 3–5 ngày | Cần đo lại sau pilot | Phụ thuộc cả tốc độ phê duyệt |
| Số bước thủ công | 6/6 | 2/7 (review nghi vấn + duyệt) | Chuyên viên chuyển từ xử lý toàn bộ sang xử lý ngoại lệ |
| Bottleneck chính | Đọc/trích + đối chiếu tay | Review hồ sơ nghi vấn | Human boundary — điểm kiểm soát chất lượng |
| Risk mới | Không có AI hallucination | Trích xuất sai không bị gắn cờ → bỏ sót; thiên lệch mô hình scoring | Cần audit ngẫu nhiên + kiểm toán mô hình scoring |

## Bước 5.3 — Problem Statement v0

| Field | Nội dung |
|---|---|
| **Actor** | Chuyên viên thẩm định tín dụng xử lý hồ sơ vay cá nhân; cấp phê duyệt ra quyết định cuối. |
| **Workflow** | Tiếp nhận hồ sơ → nhập tay → đọc/trích giấy tờ thủ công → tra CIC → đối chiếu tay → đề xuất → phê duyệt. |
| **Bottleneck** | Đọc/trích dữ liệu từ giấy tờ đa định dạng và đối chiếu chéo thủ công — chiếm phần lớn 2–4 giờ xử lý mỗi hồ sơ. |
| **Impact** | Khách hàng chờ 3–5 ngày mới có kết quả; rủi ro sai sót tăng khi khối lượng hồ sơ lớn. |
| **Success Metric** | Giảm thời gian xử lý/hồ sơ từ 2–4 giờ xuống ~30–45 phút; giảm tỷ lệ hồ sơ phải làm lại; không tăng tỷ lệ nợ xấu so với quy trình cũ (đo dài hạn sau triển khai). |
| **Boundary** | AI không tự phê duyệt/từ chối; chỉ trích xuất, gắn cờ, tính điểm tham khảo. Điểm tín dụng dùng mô hình scoring truyền thống, không dùng LLM tự luận ra điểm. Người luôn quyết định cuối cùng. |

---

# Phase 6 — Rule / Workflow / Agent + Decision

## Bước 6.0 — Ma trận độ phù hợp với AI

Bài toán của nhóm nằm ở ô nào?

```text
Độ phức tạp cao, độ mơ hồ cao (Agent có thể phù hợp, nhưng cần boundary, người thật kiểm tra và phương án quay về rất rõ)
```

Vì sao:

```text
- Nhiều bước nối tiếp, nhiều nguồn dữ liệu (giấy tờ, sao kê, CIC) — độ phức tạp cao.
- Đọc hiểu giấy tờ với định dạng đa dạng và đối chiếu chéo là việc có nhiều cách "đúng" chấp nhận được — độ mơ hồ cao.
- Tuy vậy nhóm KHÔNG chọn Agent: các bước có thể cố định thành pipeline tuyến tính (trích xuất → đối chiếu → scoring →
  diễn giải → review), AI không cần tự quyết định bước tiếp theo. Vì vậy Workflow là đủ.
```

## Bước 6.1 — So sánh Rule / Workflow / Agent

| Mức | Phương án cho bài toán nhóm | Khi nào đủ | Rủi ro | Chọn? |
|---|---|---|---|---|
| **Rule** | OCR thuần + regex trích số liệu cho giấy tờ mẫu cố định; rule đối chiếu cho case đơn giản | Đủ cho giấy tờ chuẩn hóa cao (VD: mẫu sao kê ngân hàng lớn) | Không xử lý được giấy tờ đa định dạng, không đọc hiểu ngữ nghĩa | Dùng cho một phần trích xuất, không đủ toàn bộ |
| **Workflow** | OCR+LLM trích xuất → LLM+rule đối chiếu/gắn cờ → mô hình scoring → LLM diễn giải → chuyên viên review | Hợp vì các bước tuyến tính, rõ input/output, AI chỉ hỗ trợ từng bước cụ thể | Trích xuất sai không bị gắn cờ → bỏ sót; cần audit ngẫu nhiên | **Chọn** |
| **Agent** | Agent tự quyết định thu thập thêm giấy tờ, tự điều chỉnh quy trình thẩm định theo từng hồ sơ | Chỉ cần nếu quy trình có nhiều nhánh động, AI phải tự lập kế hoạch xử lý | Rủi ro cao trong domain tài chính: khó kiểm toán, khó giải thích, hậu quả pháp lý/compliance nếu sai | Chưa chọn |

Mức chọn:

```text
Workflow.
```

Vì sao:

- Trích xuất và đối chiếu cần AI hỗ trợ ngôn ngữ/ngữ nghĩa, nhưng chuỗi bước cố định, không cần AI tự lập kế hoạch.
- Mô hình scoring dùng công cụ chuyên dụng (không phải LLM) để đảm bảo có thể kiểm toán — phù hợp domain tài chính.
- Chuyên viên vẫn review hồ sơ nghi vấn và cấp phê duyệt vẫn quyết định cuối cùng, nên rủi ro được kiểm soát.

Vì sao không chọn mức đơn giản hơn:

```text
Rule thuần không xử lý được việc đọc hiểu giấy tờ đa định dạng và đối chiếu ngữ nghĩa — đây là lý do
bài toán cần AI (LLM), không chỉ dừng ở rule/regex.
```

## Bước 6.2 — Problem Statement v1

| Field | Nội dung |
|---|---|
| **Actor** | Chuyên viên thẩm định tín dụng xử lý hồ sơ vay cá nhân; cấp phê duyệt ra quyết định cuối. |
| **Workflow** | Tiếp nhận hồ sơ → OCR+LLM trích xuất → đối chiếu tự động + gắn cờ → mô hình scoring tính điểm → LLM diễn giải → chuyên viên review hồ sơ nghi vấn → đề xuất → phê duyệt. |
| **Bottleneck** | Đọc/trích dữ liệu từ giấy tờ đa định dạng và đối chiếu chéo thủ công. |
| **Impact** | Khách hàng chờ 3–5 ngày; rủi ro sai sót tăng khi khối lượng lớn. |
| **Success Metric** | Giảm thời gian xử lý/hồ sơ xuống ~30–45 phút; giảm tỷ lệ làm lại; không tăng tỷ lệ nợ xấu (đo dài hạn). |
| **Boundary** | AI không tự phê duyệt/từ chối; điểm tín dụng dùng mô hình scoring truyền thống có thể kiểm toán, không dùng LLM tự luận điểm. |
| **AI intervention point** | Từ sau khi tiếp nhận hồ sơ đến trước khi chuyên viên đề xuất — AI hỗ trợ trích xuất, đối chiếu, tính điểm tham khảo và diễn giải. |
| **Mức chọn** | Workflow: OCR+LLM trích xuất, LLM+rule đối chiếu/gắn cờ, mô hình scoring riêng, LLM diễn giải; chuyên viên review case nghi vấn. |
| **Rủi ro & người thật kiểm tra** | Risk: trích xuất sai không bị gắn cờ (bỏ sót), thiên lệch mô hình scoring, rủi ro compliance với dữ liệu tài chính nhạy cảm. Người thật kiểm tra: chuyên viên review hồ sơ nghi vấn + cần bổ sung audit ngẫu nhiên; cấp phê duyệt quyết định cuối cùng. |

## Bước 6.3 — Final decision

| Câu hỏi | Yes / Not Yet / No | Ghi chú |
|---|---|---|
| Actor và workflow đã rõ chưa? | Yes | Actor và 8 bước workflow (trước/sau) đã rõ |
| Baseline và success metric đã đo được chưa? | Not Yet | Baseline 2–4 giờ/hồ sơ dựa trên mô tả của Liên, chưa được nhóm validate với chuyên viên thật (Phase 4 chưa thực hiện) |
| Có data/input đủ dùng chưa? | Not Yet | Cần mẫu hồ sơ vay (đã ẩn danh) để thử pipeline trích xuất/đối chiếu |
| Nếu AI sai, hậu quả có chấp nhận được không? | Not Yet | Domain tài chính — sai sót có thể ảnh hưởng phê duyệt khoản vay; cần cơ chế audit ngẫu nhiên trước khi mở rộng |
| Có người review/owner vận hành không? | Yes | Chuyên viên thẩm định + cấp phê duyệt |
| Có cách non-AI đơn giản hơn không? | Not Yet | Rule/OCR thuần chỉ đủ cho một phần giấy tờ chuẩn hóa, chưa được nhóm định lượng tỷ lệ % |

Decision:

```text
Not Yet.
```

Lý do:

```text
Problem, actor và workflow đã rõ, và hướng Workflow (không phải Agent) đã có lập luận vững. Tuy nhiên nhóm
chưa thực hiện Phase 4 (validation với chuyên viên thật, research giải pháp đã có) và chưa định lượng được
Rule/OCR thuần xử lý được bao nhiêu % hồ sơ. Domain tài chính có rủi ro compliance cao nên cần validate
kỹ hơn trước khi Go.
```

Nếu Go, pilot nhỏ nhất là:

```text
Không áp dụng — quyết định hiện tại là Not Yet.
```

Nếu Not Yet, cần validate gì trước:

```text
- Phỏng vấn 2-3 chuyên viên thẩm định thật để xác nhận baseline 2-4 giờ/hồ sơ và bottleneck đúng như mô tả.
- Research 2-3 giải pháp/tool đã có trong ngành (VD: các nền tảng OCR tài liệu tài chính, credit scoring engine)
  kèm link nguồn kiểm được.
- Định lượng tỷ lệ % hồ sơ mà OCR/rule thuần đã xử lý đủ, để biết phần AI cần bù vào thực sự lớn bao nhiêu.
- Làm rõ yêu cầu compliance/bảo mật dữ liệu hồ sơ vay trước khi thử nghiệm với dữ liệu thật.
```

Nếu No-Go, nên làm gì thay AI:

```text
Không áp dụng ở bước này.
```
