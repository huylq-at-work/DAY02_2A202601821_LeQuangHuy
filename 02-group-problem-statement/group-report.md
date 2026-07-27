# 02 — Group Problem Statement

## Thành viên nhóm

| STT | Họ và tên | Mã học viên | Vai trò trong nhóm |
|---:|---|---|---|
| 1 | Vũ Đức Anh | 2A202601191 | Thành viên |
| 2 | Lê Quang Huy | 2A202601821 | Thành viên |
| 3 | Đào Đức Mạnh | 2A202601833 | Thành viên |
| 4 | Phạm Liên | 2A202601795 | Thành viên |

## 1. Group convergence

Sau khi nghe các Problem Card, nhóm gom 12 candidates thành bốn cluster:

| Cluster | Candidate examples | Pattern chung |
|---|---|---|
| Hỗ trợ khách hàng và ngân hàng | Hỗ trợ ngân hàng; phân loại yêu cầu của khách hàng; tra cứu và chuyển trạng thái hồ sơ ngân hàng | Nhận yêu cầu từ khách hàng → đọc hiểu nội dung → xác định intent/ưu tiên → lấy thông tin còn thiếu → chuyển đúng bộ phận hoặc phản hồi |
| Phân loại báo cáo và số hóa | Phân loại báo cáo của khách hàng và số hóa; số hóa biểu mẫu/PDF; trích xuất thông tin từ hồ sơ đính kèm | Nhận email/ảnh/PDF → đọc tài liệu → xác định loại tài liệu → trích xuất metadata → lưu hoặc chuyển vào hệ thống |
| Tìm kiếm và quản lý tài liệu | Tìm lại quyết định cũ trong tài liệu; tìm FAQ/quy trình nội bộ; gắn nhãn và sắp xếp tài liệu | Người dùng có nhiều nguồn rời rạc → tìm kiếm/đọc thủ công → chọn thông tin phù hợp → lưu hoặc chia sẻ lại |
| Học tập và tài nguyên giáo dục | Phân loại tài nguyên học tập; tìm bài tập theo chủ đề/độ khó; tạo phiên bản bài tương tự cho nhiều lớp | Thu thập học liệu → đọc và phân loại → gắn chủ đề/cấp độ → tìm lại hoặc điều chỉnh cho đối tượng phù hợp |

### Shortlist và chấm điểm

Thang điểm 1–5: 1 là yếu, 5 là mạnh. Điểm “bằng chứng” dưới đây là đánh giá sơ bộ trong phase hội tụ, chưa phải kết quả validation cuối cùng.

| Candidate | Actor rõ | Workflow rõ | Pain có thể kiểm chứng | Impact đo được | Làm được trong lab | So sánh R/W/A được | Nhóm hiểu domain | Tổng |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| Hỗ trợ ngân hàng | 5 | 5 | 4 | 5 | 4 | 5 | 4 | **32** |
| Phân loại báo cáo khách hàng và số hóa | 5 | 5 | 4 | 4 | 5 | 5 | 4 | **32** |
| Phân loại tài nguyên học tập | 4 | 4 | 4 | 3 | 5 | 4 | 5 | **29** |

### Candidate được chọn

Nhóm chọn **hỗ trợ ngân hàng**, nhưng không giữ cách hiểu quá rộng như “xây chatbot ngân hàng”. Nhóm thu hẹp candidate thành:

> Hỗ trợ nhân viên tuyến đầu phân loại yêu cầu của khách hàng và chuyển đúng bộ phận, kèm trích xuất các thông tin còn thiếu để nhân viên kiểm tra và xử lý tiếp.

### Vì sao chọn candidate này

- Actor và workflow khá rõ: nhân viên tuyến đầu nhận yêu cầu, phân loại và chuyển queue.
- Có thể đo thời gian triage, tỷ lệ chuyển đúng queue và số lần khách hàng phải bổ sung thông tin.
- Có thể bắt đầu bằng Rule/Workflow có AI hỗ trợ, không cần xây Agent tự hành.
- Có thể thử nghiệm bằng dữ liệu đã ẩn danh hoặc dữ liệu mẫu, không cần truy cập hệ thống giao dịch thật.
- Rủi ro có thể giới hạn nếu AI chỉ đề xuất intent, mức ưu tiên và queue; nhân viên vẫn là người xác nhận.

### Vì sao chưa chọn hai candidate còn lại

- **Phân loại báo cáo khách hàng và số hóa:** cũng có workflow tốt, nhưng “báo cáo” có thể bao gồm quá nhiều loại tài liệu; cần xác định schema và nguồn dữ liệu trước. Một phần bài toán này có thể trở thành một module trong bài hỗ trợ ngân hàng.
- **Phân loại tài nguyên học tập:** dễ làm prototype, nhưng impact và baseline hiện chưa rõ bằng bài hỗ trợ ngân hàng; độ khó phân loại tài liệu cũng dễ phụ thuộc cảm nhận.

## 2. Validation plan và bằng chứng hiện có

> Phần này không tự ghi số liệu phỏng vấn khi nhóm chưa thực hiện. Các ô `[CẦN ĐIỀN]` phải được thay bằng dữ liệu thật sau khi hỏi người có kinh nghiệm hỗ trợ khách hàng hoặc vận hành ngân hàng.

### Quick validation

| Nguồn | Số người / mẫu | Tín hiệu xác nhận cần tìm | Tín hiệu phản bác cần ghi | Nhóm sẽ sửa problem thế nào? |
|---|---:|---|---|---|
| Phỏng vấn nhân viên chăm sóc khách hàng | [CẦN ĐIỀN: 2–3 người] | Có yêu cầu lặp lại; mất thời gian đọc và phân loại; chuyển sai queue hoặc phải hỏi lại | Hệ thống hiện tại đã tự phân loại chính xác; bottleneck thực tế nằm ở bước khác | Thu hẹp intent và queue, không gọi chung là “hỗ trợ ngân hàng” |
| Mini survey / hỏi nhanh | [CẦN ĐIỀN: 5–10 người] | Nhiều người gặp cùng một loại yêu cầu; thời gian triage có thể đo | Pain xảy ra ít hoặc chỉ do một người | Đổi candidate hoặc chọn một intent có tần suất cao hơn |
| Dữ liệu mẫu đã ẩn danh | [CẦN ĐIỀN: số ticket/email] | Có đủ nội dung để gắn nhãn intent và queue | Dữ liệu thiếu context hoặc chứa thông tin nhạy cảm không thể dùng | Dùng dữ liệu giả lập/ẩn danh và giảm scope |

### Câu hỏi validation

1. Lần gần nhất bạn phải phân loại một yêu cầu khách hàng là khi nào?
2. Bạn mất bao lâu từ lúc nhận yêu cầu đến lúc chuyển đúng queue?
3. Những loại yêu cầu nào hay bị chuyển nhầm nhất?
4. Thông tin nào khách hàng thường bỏ thiếu khiến bạn phải hỏi lại?
5. Nếu hệ thống chỉ đề xuất intent và queue, bạn muốn kiểm tra gì trước khi bấm xác nhận?

## 3. Research giải pháp đã có

| Nguồn / tool / case | Link | Họ giải quyết phần nào? | Điểm mạnh | Khoảng trống / rủi ro | Bài học cho nhóm |
|---|---|---|---|---|---|
| Microsoft Dynamics 365 Unified Routing | [Microsoft Learn](https://learn.microsoft.com/en-us/dynamics365/customer-service/administer/overview-unified-routing) | Định tuyến work item đến queue/nhân viên phù hợp dựa trên yêu cầu và năng lực | Kết hợp routing, queue và nhiều kênh; có thể dùng AI cùng rule | Đây là nền tảng doanh nghiệp; không chứng minh dữ liệu của nhóm sẽ đạt độ chính xác tương tự | Bài toán nên tách thành intent/priority/queue và có rule fallback |
| Microsoft basic routing rulesets | [Microsoft Learn](https://learn.microsoft.com/en-us/dynamics365/customer-service/administer/create-rules-automatically-route-cases) | Route case bằng các luật cố định | Dễ giải thích, dễ kiểm tra, phù hợp với intent có tiêu chí rõ | Rule không đủ tốt khi câu khách hàng tự do hoặc thiếu context | Rule nên xử lý các trường hợp chắc chắn; AI chỉ hỗ trợ phần ngôn ngữ mơ hồ |
| Microsoft AI Builder case routing | [Microsoft Learn](https://learn.microsoft.com/en-us/dynamics365/guidance/resources/cs-ai-case-deflection) | Tạo case từ inquiry và hỗ trợ phân loại/routing | Cho thấy pattern kết hợp email-to-case, AI Builder và routing | Cần dữ liệu gắn nhãn, kiểm thử và quyền truy cập hệ thống | Prototype nên bắt đầu bằng dữ liệu mẫu, không tích hợp trực tiếp hệ thống ngân hàng |
| Amazon Textract | [AWS Documentation](https://docs.aws.amazon.com/textract/latest/dg/how-it-works-analyzing.html) | Trích xuất text, form, table và key-value từ tài liệu | Hữu ích nếu yêu cầu có ảnh/PDF hoặc biểu mẫu đính kèm | OCR có thể sai; không tự quyết định nghiệp vụ ngân hàng | “Số hóa” chỉ là bước trích xuất input; vẫn cần người kiểm tra trước khi lưu/dùng |

### Research takeaway

Các giải pháp hiện có đều gợi ý mô hình kết hợp: **Rule cho trường hợp chắc chắn, AI để đọc hiểu/phân loại phần ngôn ngữ hoặc tài liệu, và nhân viên xác nhận trước khi routing hoặc trả lời**. Vì vậy, nhóm không chọn Agent tự xử lý toàn bộ yêu cầu.

## 4. Current workflow của candidate đã chọn

### Phạm vi workflow

Chỉ xét yêu cầu không thực hiện giao dịch trực tiếp, ví dụ: hỏi trạng thái hồ sơ, phí/dịch vụ, lỗi ứng dụng, yêu cầu hỗ trợ thẻ hoặc cần chuyển bộ phận. Không xét quyết định tín dụng, tư vấn đầu tư, xác thực danh tính hay thao tác chuyển tiền.

| Bước | Actor | Input | Output | Thời gian / tần suất | Ghi chú |
|---:|---|---|---|---|---|
| 1 | Khách hàng | Tin nhắn/email/cuộc gọi | Yêu cầu hỗ trợ tự do | Phát sinh theo từng yêu cầu; không tính thời gian xử lý của nhân viên | Có thể kèm ảnh/PDF; không dùng dữ liệu thật trong prototype |
| 2 | Nhân viên tuyến đầu | Yêu cầu của khách hàng | Nội dung được đọc và hiểu sơ bộ | Khoảng **2 phút/yêu cầu** | Baseline ước tính; cần đo lại bằng log/phỏng vấn. Đây là bottleneck tiềm năng |
| 3 | Nhân viên tuyến đầu | Nội dung yêu cầu | Intent, mức ưu tiên, thông tin cần bổ sung | Khoảng **3 phút/yêu cầu** | Baseline ước tính; dễ không nhất quán giữa nhân viên |
| 4 | Nhân viên tuyến đầu | Intent và thông tin khách hàng | Queue/bộ phận đích | Khoảng **1 phút/yêu cầu** | Baseline ước tính; có thể chuyển sai queue |
| 5 | Nhân viên tuyến đầu | Case đã phân loại | Phản hồi ban đầu hoặc câu hỏi bổ sung | Khoảng **2 phút/yêu cầu** | Baseline ước tính; không tự hứa thời hạn nếu chưa xác minh |
| 6 | Bộ phận chuyên môn | Case đã chuyển | Xử lý tiếp và cập nhật trạng thái | Khoảng **10–30 phút/case**, tùy loại yêu cầu; thường xảy ra sau bước 4–5 | Ngoài scope prototype; không tính vào thời gian triage |

**Bottleneck chính:** Bước 2–4: đọc yêu cầu tự do, xác định intent và chọn queue phù hợp.

## 5. Future workflow đề xuất

```text
1. Khách hàng gửi yêu cầu — phát sinh theo từng yêu cầu
   ↓
2. Hệ thống chuẩn hóa text / trích xuất file đính kèm nếu có — Rule/OCR, khoảng 30 giây
   ↓
3. AI đề xuất intent + mức ưu tiên + queue + thông tin còn thiếu — khoảng 30 giây
   ↓
4. Nhân viên kiểm tra nội dung, dữ liệu nhạy cảm và độ tin cậy — khoảng 1–2 phút
   ├─ Đúng và đủ → xác nhận queue, soạn/gửi phản hồi theo mẫu — 1–2 phút
   ├─ Thiếu thông tin → gửi câu hỏi bổ sung — khoảng 1 phút
   └─ Không chắc / rủi ro cao → chuyển chuyên viên/xử lý thủ công — khoảng 2 phút
   ↓
5. Ghi nhận kết quả để đo chất lượng và cải thiện bộ rule/intent — khoảng 30 giây
```

### Thời gian dự kiến của future workflow

| Bước | Actor | Thời gian / tần suất | Ghi chú |
|---:|---|---|---|
| 1 | Hệ thống tiếp nhận | Tự động, theo từng yêu cầu | Không tính là thời gian thao tác của nhân viên |
| 2 | Rule/OCR | Khoảng **30 giây/yêu cầu** | Chỉ trích xuất text/file; không kết luận nghiệp vụ |
| 3 | AI phân loại | Khoảng **30 giây/yêu cầu** | Tạo đề xuất intent/priority/queue và confidence |
| 4 | Nhân viên review | Khoảng **1–2 phút/yêu cầu** | Human boundary; kiểm tra nội dung và dữ liệu nhạy cảm |
| 5a | Nhân viên xác nhận và phản hồi theo mẫu | Khoảng **1–2 phút/yêu cầu** | Chỉ áp dụng khi yêu cầu đủ thông tin và thuộc scope |
| 5b | Nhân viên hỏi bổ sung | Khoảng **1 phút/yêu cầu** | Áp dụng khi thiếu trường bắt buộc |
| 5c | Nhân viên chuyển chuyên viên | Khoảng **2 phút/yêu cầu** | Áp dụng khi confidence thấp hoặc rủi ro cao |
| 6 | Hệ thống ghi nhận kết quả | Khoảng **30 giây/yêu cầu** | Lưu intent dự đoán, intent được sửa và queue cuối |

Với case thông thường, thời gian từ lúc nhận yêu cầu đến lúc xác định queue dự kiến giảm từ khoảng **6 phút** ở current workflow xuống khoảng **2–3 phút** ở future workflow. Nếu tính cả bước phản hồi và ghi nhận kết quả, tổng thời gian dự kiến là khoảng **4–6 phút/case**. Các con số này là giả định để thiết kế pilot, không phải kết quả đã được kiểm chứng.

### Bảng before/after

| Metric | Trước | Sau kỳ vọng | Cách đo / lưu ý |
|---|---:|---:|---|
| Thời gian từ lúc nhận đến lúc xác định queue | Khoảng **6 phút/yêu cầu** (ước tính từ bước 2–4) | **≤4,2 phút/yêu cầu**; kỳ vọng pilot 2–3 phút | Đo timestamp của case; thay baseline ước tính bằng log/phỏng vấn thật |
| Tỷ lệ route đúng queue | [CẦN ĐIỀN] | ≥90% trên bộ test đã gắn nhãn | Chỉ đo trên các intent thuộc scope |
| Số lần khách phải bổ sung thông tin do case thiếu trường | [CẦN ĐIỀN] | Giảm 20% | So sánh cùng loại yêu cầu |
| Tỷ lệ output AI được nhân viên chấp nhận không sửa lớn | Chưa có | ≥80% trong pilot | Không dùng làm tiêu chí duy nhất về chất lượng |
| Giao dịch/tư vấn sai do AI | Không chấp nhận | 0 trường hợp trong pilot | AI không được tự thực hiện giao dịch hoặc gửi câu trả lời nhạy cảm |

**Human boundary:** Nhân viên phải kiểm tra intent, queue, mức ưu tiên, thông tin nhạy cảm và nội dung phản hồi trước khi xác nhận. AI không được tự truy cập số dư, tự xác thực danh tính, tự chuyển tiền, tự phê duyệt hồ sơ hoặc tự gửi tư vấn tài chính.

**Fallback:** Nếu confidence thấp, intent ngoài danh mục, có dấu hiệu gian lận/khiếu nại nghiêm trọng hoặc yêu cầu liên quan giao dịch, hệ thống không tự xử lý; chuyển sang nhân viên/chuyên gia theo quy trình hiện tại.

## 6. Problem Statement v0

Nhân viên chăm sóc khách hàng ngân hàng phải đọc và phân loại các yêu cầu gửi qua nhiều kênh, xác định thông tin còn thiếu rồi chuyển case đến đúng bộ phận. Việc này mất thời gian, có thể không nhất quán và làm khách hàng phải chờ hoặc bổ sung thông tin nhiều lần. Nhóm muốn dùng AI để hỗ trợ đọc hiểu và đề xuất phân loại, nhưng chưa xác định được baseline, danh mục intent và ngưỡng an toàn phù hợp.

## 7. Problem Statement v1 — bản nhóm chọn

Nhân viên chăm sóc khách hàng tuyến đầu cần giảm thời gian phân loại các yêu cầu hỗ trợ không giao dịch từ khách hàng thành intent và queue phù hợp. Hiện tại họ phải đọc nội dung tự do, tự xác định loại yêu cầu, kiểm tra thông tin còn thiếu và chuyển case bằng tay; bước này có nguy cơ chuyển sai queue hoặc phải hỏi lại khách hàng. Trong phạm vi pilot, nhóm sẽ kiểm tra liệu một workflow kết hợp rule và AI có thể đề xuất intent, mức ưu tiên, queue và trường thông tin còn thiếu để nhân viên xác nhận hay không.

**Actor:** Nhân viên chăm sóc khách hàng tuyến đầu.

**Workflow:** Nhận yêu cầu → đọc hiểu → xác định intent/priority → kiểm tra thông tin thiếu → chọn queue → phản hồi hoặc chuyển chuyên môn.

**Bottleneck:** Đọc và phân loại yêu cầu tự do ở bước triage.

**Impact:** Tăng thời gian xử lý ban đầu, tăng khả năng chuyển sai queue và làm khách hàng phải chờ/bổ sung thông tin.

**Success metric:** Trong pilot, giảm ít nhất 30% thời gian xác định queue so với baseline thật; đạt tối thiểu 90% route đúng queue trên bộ test đã được người có chuyên môn gắn nhãn; không có trường hợp AI tự gửi hoặc tự thực hiện hành động nghiệp vụ nhạy cảm.

**Boundary:** Chỉ dùng yêu cầu hỗ trợ không giao dịch và dữ liệu đã ẩn danh/giả lập. Không tự xác thực danh tính, truy vấn số dư, chuyển tiền, phê duyệt tín dụng, tư vấn đầu tư, xử lý khiếu nại nghiêm trọng hoặc gửi phản hồi cuối nếu chưa có người kiểm tra.

**AI intervention point:** Sau khi yêu cầu được tiếp nhận và chuẩn hóa, trước bước nhân viên chọn intent/queue.

## 8. So sánh No AI / Rule / Workflow / Agent

| Phương án | Làm được gì | Ưu điểm | Hạn chế / rủi ro | Kết luận |
|---|---|---|---|---|
| No AI / process fix | Chuẩn hóa danh mục intent, form bắt buộc, FAQ và checklist triage | Rẻ, dễ kiểm soát, giảm input thiếu | Không xử lý tốt câu tự do; vẫn phải đọc và gắn nhãn thủ công | Bắt buộc làm nền, nhưng chưa đủ |
| Rule | Dùng keyword, form field và điều kiện rõ để route | Dễ giải thích, dễ audit, phù hợp case đơn giản | Nhạy với cách diễn đạt; dễ fail khi nội dung thiếu context | Dùng cho intent chắc chắn và fallback |
| Workflow | Chuẩn hóa input → AI đề xuất intent/priority/queue → nhân viên review → route → ghi kết quả | Phù hợp workflow tuyến tính; có human boundary và đo được | Cần bộ intent, dữ liệu test và cơ chế review | **Chọn** |
| Agent | Tự đọc nhiều nguồn, hỏi bổ sung, quyết định bước tiếp theo và xử lý case | Có thể bao phủ quy trình dài, nhiều nhánh | Permission/rủi ro cao; khó audit; không cần thiết cho pilot | Chưa chọn |

### Mức chọn

**Workflow có Rule và AI hỗ trợ, không chọn Agent.** Rule xử lý các trường hợp rõ; AI chỉ tạo đề xuất có cấu trúc; nhân viên là người quyết định cuối.

## 9. Final decision

| Câu hỏi | Yes / Not Yet / No | Ghi chú |
|---|---|---|
| Actor và workflow đã rõ chưa? | **Yes** | Đã thu hẹp vào nhân viên tuyến đầu và bước triage |
| Baseline và success metric đã đo được chưa? | **Not Yet** | Metric đã định nghĩa nhưng cần đo baseline thật |
| Có data/input đủ dùng chưa? | **Not Yet** | Cần dữ liệu ẩn danh hoặc bộ dữ liệu giả lập có nhãn |
| Nếu AI sai, hậu quả có chấp nhận được không? | **Yes, có điều kiện** | Chỉ pilot ở triage không giao dịch, luôn có người review |
| Có người review/owner vận hành không? | **Not Yet** | Cần xác định nhân viên/mentor chịu trách nhiệm kiểm tra |
| Có cách non-AI đơn giản hơn không? | **Yes** | Form, taxonomy, checklist và rule là nền tảng bắt buộc |

### Quyết định: **Not Yet cho production; Go cho pilot nhỏ có kiểm soát**

Nhóm chưa đủ bằng chứng để triển khai trong môi trường ngân hàng thật vì chưa có baseline, dữ liệu đã ẩn danh và owner vận hành. Tuy nhiên, nhóm có thể **Go với pilot offline** trên bộ case giả lập/ẩn danh để đo chất lượng phân loại, thời gian review và tỷ lệ route đúng.

### Pilot đề xuất

1. Chọn 5–8 intent không giao dịch, ví dụ: lỗi ứng dụng, hỏi phí/dịch vụ, hỗ trợ thẻ, trạng thái hồ sơ, yêu cầu bổ sung giấy tờ.
2. Tạo hoặc xin một bộ 30–50 case đã ẩn danh và gắn nhãn queue bởi người hiểu nghiệp vụ.
3. Chạy hai cách: checklist/rule thủ công và workflow AI đề xuất.
4. Đo thời gian triage, route đúng/sai, thông tin bị bỏ sót và số lần nhân viên sửa output.
5. Không kết nối tài khoản thật, không dùng số tài khoản/số dư/CCCD thật và không tự gửi phản hồi cho khách hàng.

### Điều kiện dừng / rollback

- Nếu route đúng thấp hơn 90% hoặc thấp hơn quy trình thủ công, quay về rule/checklist.
- Nếu AI tạo đề xuất liên quan giao dịch, tư vấn tài chính hoặc xác thực danh tính, loại case khỏi workflow và chuyển người thật.
- Nếu không có dữ liệu đủ sạch/ẩn danh, chỉ trình diễn trên dữ liệu giả lập; không tuyên bố đã chứng minh hiệu quả thực tế.
- Nếu nhân viên phải sửa phần lớn output, giữ lại taxonomy và form chuẩn, chưa dùng AI.

## 10. Việc cần bổ sung trước khi nộp chính thức

- [ ] Điền danh sách thành viên nhóm và vai trò.
- [ ] Thay các `[CẦN ĐIỀN]` bằng số liệu phỏng vấn/survey/log thật.
- [ ] Ghi ngày, đối tượng và câu hỏi validation.
- [ ] Bổ sung workflow dưới dạng ảnh/Mermaid nếu giảng viên yêu cầu.
- [ ] Kiểm tra lại các intent/queue cùng người có hiểu biết nghiệp vụ ngân hàng.
- [ ] Ghi rõ dữ liệu nào là giả lập, dữ liệu nào đã ẩn danh.
