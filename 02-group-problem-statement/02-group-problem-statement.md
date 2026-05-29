## Group convergence

Nhóm 5 người, mỗi người share top 3. Tổng cộng 14 candidates.

| Cluster | Candidate examples | Pattern chung |
|---|---|---|
| Báo cáo / Phân tích dữ liệu | Check đánh giá Shopee thành checklist (Minh), Tổng hợp tiến độ học sinh (Văn Minh), Tổng hợp bài viết (Phúc), Highlight trận đấu (Nam) | Đọc, gom nhóm, tóm tắt khối lượng lớn dữ liệu text/thông tin rời rạc thành báo cáo/insight. |
| Y tế / Sức khỏe | Tư vấn lịch khám (Văn Minh), Lịch phục hồi chấn thương (Nam), Gợi ý thuốc cho bác sĩ (Điệp), Nhắc lịch tiêm ngừa (Điệp) | Matching thông tin y tế, lên lịch và cảnh báo rủi ro (tương tác thuốc). |
| Trợ lý cá nhân / Đời sống | Sắp xếp lịch trình (Minh), Gợi ý nấu ăn/đi chợ (Phúc), Gợi ý phối đồ (Phúc), Quản lý quỹ đội bóng (Nam) | Tối ưu hóa thời gian và nguồn lực cá nhân dựa trên context hiện tại. |
| Tìm kiếm / Quản lý tri thức | Search bài DSA (Minh), Note tài liệu từ keyword ra file .md (Điệp) | Tìm kiếm ngữ nghĩa và tự động cấu trúc hóa kiến thức. |

## Shortlist và score

Nhóm chọn 3 bài toán tiềm năng nhất để chấm điểm.

| Candidate | Actor rõ | Workflow rõ | Pain có evidence | Impact đo được | Làm trong lab | So sánh R/W/A được | Nhóm hiểu domain | Tổng |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| Phân tích review Shopee (Minh) | 5 | 5 | 5 | 5 | 5 | 5 | 4 | 34 |
| Gợi ý thuốc cho bác sĩ (Điệp) | 4 | 4 | 5 | 3 | 2 | 4 | 2 | 24 |
| Tổng hợp tiến độ học sinh (Văn Minh) | 4 | 4 | 4 | 4 | 4 | 4 | 5 | 29 |

Nhóm chọn: **Phân tích đánh giá đơn hàng (Sentiment Analysis).**

Vì sao chọn:
- Có workflow và data rõ ràng (export được file Excel/CSV từ sàn).
- Impact đo được ngay bằng số giờ tiết kiệm được của nhân viên Quality Analytics (QA) và độ chính xác phân loại.
- Dễ dàng so sánh ranh giới giữa Rule-based (tìm keyword) và LLM Workflow (hiểu ngữ cảnh).
- Không vướng rủi ro lớn về đạo đức/pháp lý như bài toán Y tế (Gợi ý thuốc).

Vì sao không chọn các bài khác:
- Gợi ý thuốc: Domain quá chuyên sâu, rủi ro fatal error cao (chết người), không thể test an toàn trong lab.
- Tổng hợp tiến độ học sinh: Gom data từ nhiều nguồn (điểm số, thái độ, bài tập) khá phân mảnh, khó xin data thật của học sinh để làm lab.

## Quick validation

Nhóm hỏi nhanh 3 người đang kinh doanh online / Store Manager / QA.

| Nguồn | Số người | Tín hiệu xác nhận | Tín hiệu phản bác | Nhóm sửa problem thế nào |
|---|---:|---|---|---|
| Phỏng vấn chủ shop / QA | 3 | 2/3 shop tốn rất nhiều thời gian đọc review 1-3 sao để tìm lỗi vận chuyển hay lỗi sản phẩm. | 1 shop nhỏ bảo lượng đơn ít, tự đọc ngày 15p là xong, không cần AI. | Thu hẹp problem: Nhắm tới các Store Manager/QA quản lý gian hàng lớn (Mall) hoặc dùng trong đợt Mega Sale khi data bị quá tải. |
| Quan sát công cụ hiện tại | N/A | Các sàn chỉ có biểu đồ chung (tổng số sao), không có tóm tắt lý do. | Các công cụ social listening (như Buzzmetrics) thì quá đắt cho 1 shop bán lẻ. | Xác định khoảng trống: Cần một tool xử lý text giá rẻ, tập trung vào trích xuất lý do (aspect-based sentiment) thay vì chỉ đếm positive/negative. |

Insight sau validation:
> Pain thật không nằm ở việc biết hôm nay có bao nhiêu review 1 sao. Pain nằm ở việc "Tại sao khách cho 1 sao?" (Giao chậm? Vỡ hộp? Thái độ shipper? Hàng lỗi?) để Manager có Actionable Insight ngay lập tức.

## Research giải pháp

| Nguồn / tool / case | Link | Họ giải quyết phần nào? | Điểm mạnh | Khoảng trống / rủi ro | Bài học cho nhóm |
|---|---|---|---|---|---|
| Dashboard Analytics của Sàn TMĐT | Giao diện Seller Center | Thống kê số lượng sao, tỷ lệ phản hồi. | Số liệu real-time, có sẵn. | Không đọc hiểu được text. Không biết lý do đằng sau con số. | Rule/dashboard không đủ để giải quyết phần chữ (text). |
| Social Listening Tools (Brandwatch, v.v.) | Các nền tảng SaaS | Phân tích sentiment diện rộng. | Rất mạnh, dashboard đẹp. | Setup phức tạp, chi phí đắt đỏ, không tối ưu cho workflow nhỏ của 1 QA. | Không cần build cả 1 platform lớn, chỉ cần focus vào bước "Gán nhãn & Tóm tắt". |
| Bơm file Excel vào ChatGPT | OpenAI | Gán nhãn và tóm tắt theo prompt. | Nhanh, linh hoạt. | QA phải copy/paste thủ công, dễ đứt gãy nếu file quá dài, không có tính lặp lại (pipeline). | Cần đóng gói thành 1 Workflow cố định (Data In -> Xử lý -> Data Out). |

Research takeaway:
> Không cần Agent (không cần AI tự dạo quanh Shopee đọc comment và tự nhắn tin xin lỗi khách). Hợp lý nhất là một Data Pipeline (Workflow): AI tự động gán nhãn hàng loạt dựa trên file Excel tải về, sau đó draft báo cáo nguyên nhân, QA review và gửi cho Manager.

## Workflow before/after

Nội dung workflow:

**CURRENT STATE — 7 bước, 240 phút (với lượng review lớn)**
1. Export Excel từ Seller Center: 5'
2. Filter review 1-4 sao: 5'
3. Đọc thủ công hàng ngàn comment: 150' <-- bottleneck
4. Gán nhãn thủ công (Lý do lỗi): 45' <-- bottleneck
5. Thống kê, vẽ biểu đồ: 15'
6. Viết narrative báo cáo: 15'
7. Gửi Store Manager: 5'

**FUTURE STATE — 5 bước, 45 phút**
1. Export/Ingest Data: 5'
2. Rule-based tự lọc rác/spam: 2' *(Rule step)*
3. LLM tự động gán nhãn & trích xuất lý do: 15' *(Workflow step - Chạy ngầm)*
4. LLM draft báo cáo tổng quan: 3' *(Workflow step)*
5. QA review data, chỉnh sửa báo cáo & Gửi: 20' *(Human boundary)*

**Fallback:**
* Gặp comment lóng/quá phức tạp mà LLM gán nhãn "Unknown" → QA tự đọc lại những dòng đó.
* LLM viết báo cáo chung chung → QA tự viết lại từ biểu đồ đã được gán nhãn.

**Bottleneck mới:**
QA review lại nhãn (spot-check) và tinh chỉnh báo cáo. Đây là điểm kiểm soát bắt buộc để tránh AI đánh giá sai tình hình vận hành.

Before/after impact:

| Metric | Trước | Sau kỳ vọng | Ghi chú |
|---|---:|---:|---|
| Tổng thời gian | 240 phút | Dưới 45 phút | Target chính |
| Năng lực xử lý (Scale) | 500 reviews/buổi | 10,000+ reviews | Không bị nghẽn dịp Mega Sale |
| Bottleneck chính | Đọc & Gán nhãn | Spot-check & Chỉnh báo cáo | Giải phóng sức lao động chân tay |
| Risk mới | Sai sót do QA mệt mỏi | AI hiểu sai mỉa mai (sarcasm) | Human-in-the-loop để review |

## Problem Statement v0

| Field | Nội dung |
|---|---|
| **Actor** | Nhân viên Quality Analytics (QA) làm báo cáo cho Store Manager. |
| **Workflow** | Export dữ liệu đánh giá → Lọc 1-4 sao → Đọc từng comment → Gán nhãn nguyên nhân → Vẽ chart → Viết tóm tắt → Gửi Manager. |
| **Bottleneck** | Bước đọc thủ công và gán nhãn tốn hàng giờ đồng hồ, dễ sai sót do cảm tính và quá tải trong dịp Mega Sale. |
| **Impact** | Tốn nửa ngày làm việc; báo cáo trễ khiến Store Manager không có insight kịp thời để sửa lỗi vận hành; giới hạn scale. |
| **Success Metric** | Giảm thời gian xử lý từ 4 tiếng xuống <45 phút; Độ chính xác gán nhãn >85% so với người. |
| **Boundary** | AI chỉ gán nhãn và draft báo cáo. Không tự động thay đổi quy trình vận hành, không tự động chat trả lời khách hàng. |

## Rule / Workflow / Agent

| Mức | Phương án | Khi nào đủ | Rủi ro | Chọn? |
|---|---|---|---|---|
| **Rule** | Dùng filter keyword ("rách", "chậm", "tệ") để gán nhãn | Đủ nếu khách comment chuẩn mực, rập khuôn. | Bỏ sót context phức tạp, viết sai chính tả, không phân biệt được lỗi nào là chính. Không viết được báo cáo. | Dùng làm bước lọc rác ban đầu. |
| **Workflow** | Pipeline: Xử lý file → AI gán nhãn hàng loạt → AI draft report → QA review. | Bài toán xử lý data 1 chiều, bước xử lý ngôn ngữ lặp lại liên tục. | AI bịa nhãn (hallucinate) hoặc không hiểu từ lóng. QA phải check lại. | **Chọn** |
| **Agent** | Agent tự động lấy data qua API, tự đọc, tự phân tích, tự rep comment xin lỗi khách và gửi report cho sếp. | Khi muốn auto 100% quy trình CSKH. | Quá nguy hiểm. Agent rep sai sẽ gây khủng hoảng truyền thông. Vượt quá scope báo cáo. | Không chọn |

**Mức chọn:** Workflow (Data Pipeline).

**Vì sao:**
* Bài toán thiên về Xử lý ngôn ngữ tự nhiên (NLP/Sentiment Analysis) lô lớn, rất phù hợp với LLM pipeline.
* Cần output có cấu trúc rõ ràng (bảng data có nhãn + text báo cáo).
* Human in the loop (QA) là bắt buộc để đảm bảo chất lượng trước khi báo cáo lên cấp quản lý.

## Problem Statement v1

| Field | Nội dung |
|---|---|
| **Actor** | Nhân viên Quality Analytics (QA) làm báo cáo cho Store Manager. |
| **Workflow** | Export data → Rule lọc rác → LLM gán nhãn lý do (chậm, lỗi hàng, thái độ...) → LLM draft báo cáo → QA review → Gửi Manager. |
| **Bottleneck** | Đọc và phân loại thủ công hàng ngàn comment không thể scale khi đơn hàng tăng vọt. |
| **Impact** | Tốn 4h/tuần; trễ báo cáo sau Mega Sale làm sếp thiếu insight sửa quy trình; mệt mỏi cho QA. |
| **Success Metric** | Giảm thời gian làm report xuống <45 phút; Accuracy gán nhãn >85%. |
| **Boundary** | AI chỉ xử lý text thành insight. Không quyết định thay người, không tương tác với end-user (khách hàng). |
| **AI intervention point** | Khâu đọc hiểu text (biến unstructured data thành structured data) và khâu tổng hợp (draft narrative report). |
| **Mức chọn** | Workflow (Batch Processing Pipeline). |
| **Rủi ro & người thật kiểm tra** | Risk: AI hiểu sai ý khách hàng (đặc biệt câu mỉa mai). Người thật review: QA spot-check các nhãn lạ và tự chốt báo cáo cuối. |

## Final decision

**Decision:** Go với Pilot nhỏ (Batch processing thay vì Real-time).

**Pilot nhỏ nhất:**
* Chuẩn bị tập data mẫu (CSV) khoảng 200 review từ đợt sale gần nhất.
* Chạy qua 1 prompt chuẩn hóa: `<Yêu cầu LLM đọc review, trả về JSON gồm: Sentiment (Tích cực/Tiêu cực) và Aspect (Vận chuyển/Đóng gói/Chất lượng)>`.
* Cho QA tự chấm điểm Accuracy của tập dữ liệu AI vừa làm ra so với cách làm bằng cơm.

**Exit / rollback:**
* Nếu Accuracy của LLM < 70%, quay lại phương pháp Rule-based (Search keyword) + Đọc tay.
* Nếu LLM không thể trả về đúng format (JSON/Bảng) để phân tích số liệu, dừng dự án vì tốn công sửa lỗi format.

**Decision rationale:**
* Problem có Pain rất thực tế, Business Value lớn.
* Data input (review sàn) rất phổ biến và dễ lấy.
* Cắt bỏ hoàn toàn ý tưởng Agent (tự rep tin nhắn), giữ scope ở mức "Công cụ hỗ trợ phân tích" giúp dự án khả thi làm trong lab.
