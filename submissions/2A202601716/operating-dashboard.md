# Operating Dashboard - EquiScreen Recruiter Copilot

- Học viên: Nguyễn Huy Toàn
- Mã học viên: 2A202601716
- Mô hình: B2B
- Cập nhật: 2026-08-28
- North Star: L-01 - TTFV tối đa của cohort 3 pilot gần nhất ≤14 ngày; hiện chưa đo được, trạng thái XÁM.

**Phạm vi:** thiết kế vận hành trước pilot, không phải kết quả kinh doanh. Họp thứ Sáu, Product Owner Nguyễn Huy Toàn chủ trì; owner chức năng là vai trò cần bố trí, không khẳng định đã có nhân sự. USD; múi giờ Asia/Ho_Chi_Minh. D0 = 2026-08-28.

## Chẩn đoán mô hình

EquiScreen được thiết kế theo B2B: tiền dự kiến từ ngân sách HR Tech/Recruiting Operations của doanh nghiệp tuyển dụng; recruiter của chính doanh nghiệp đó trực tiếp sử dụng evidence panel/review queue. Ứng viên là người bị tác động, chưa có bề mặt sản phẩm trực tiếp. Base Hiring chỉ là kênh giới thiệu/tích hợp dự kiến, chưa xác nhận hợp tác. Không gọi B2B2C chỉ vì có partner. Chưa có giao dịch/log chứng minh mô hình đã vận hành.

| Dữ liệu đầu vào | Trạng thái | Nằm ở đâu hoặc cần gì để đo | Ngày có số |
|---|---|---|---|
| Unit economics Day 24 | ĐỌC ĐƯỢC MÔ HÌNH; KHÁC SẢN PHẨM | D24 là SaleMate AI: ARPU 1.490.000 VND/tháng, CAC 5.500.000 VND, churn 4%/tháng. Không chuyển sang EquiScreen. Cần finance model riêng EquiScreen. | 2026-09-11 |
| Value Metric và Cost/Job Day 25 | ĐỌC ĐƯỢC GIẢ ĐỊNH; CHƯA ĐO | D25: evidence pack hoàn tất; 5.000 job thử/tài khoản/tháng, completion 95%, cost/job $0,03784505, giá $0,12, GM trước kênh 68,4625%. | 2026-08-28 |
| CAC và payback EquiScreen | GIẢ ĐỊNH | D25 4_Channel_Fit!B42: CAC mục tiêu $1.500; B8: payback cho phép 12 tháng. Mục tiêu kế hoạch, không phải benchmark đã xác minh. | 2026-11-26 |
| Retention/renewal EquiScreen | CHƯA ĐO ĐƯỢC | Cần cohort hợp đồng trả phí và ngày gia hạn/hủy. Đến D90 chỉ kiểm tra retention 30 ngày nếu đủ cohort; không suy annual renewal từ churn SaleMate. | 2026-11-26 |
| Partner, buyer, quyền quan sát | TRONG 2 TUẦN - KẾ HOẠCH | D25 4_Channel_Fit!B39:B42 và 5_90Day_Plan!B5:B8. Phỏng vấn 3 buyer, xác nhận quyền ghi event; chưa có bằng chứng đã liên hệ Base. | 2026-09-11 |

**Chuyển tiếp nguồn:** ưu tiên EquiScreen vì là bài Day25 mới hơn. Day24 chỉ dùng phát hiện lệch sản phẩm, không làm nguồn số cho ngưỡng. MH truy về Day25 và kịch bản Day26 công khai. Thiếu finance model Day24 riêng cho EquiScreen là giới hạn cần người chấm xem xét, không nhận đã có đủ lịch sử tài chính.

**Bridge kinh tế:** Day25 đề xuất chia 20% doanh thu usage trong 12 tháng cho partner nhưng chưa đưa vào cost/job. Với giá $0,12, CM sau kênh = 1 - 20% - 0,03784505/0,12 = **48,4625%**, dưới mục tiêu 60%. Giá tối thiểu = 0,03784505/(1 - 20% - 60%) = **$0,18922526/job**. Day26 thử **$0,20/job hoàn tất**, bằng trần giá trị 25% tại D25 2_Pricing!B13; đây là kịch bản cần kiểm chứng, chưa phải giá được phê duyệt/khách chấp nhận. Nếu giá không được chấp nhận, đàm phán share hoặc dừng kênh; không sửa workbook Day24/25.

**Thuật ngữ:** G-01 là biên đóng góp sau kênh trên doanh thu gộp (CM), dùng như GM điều chỉnh cho vận hành; không đánh đồng với GM kế toán trên doanh thu thuần. Trừ phí partner, inference/retry, infra, QA và direct delivery COGS; không trừ R&D/OPEX/CAC. Onboarding phục vụ bán tính CAC; delivery sau bán tính COGS, không tính hai lần. Chi phí chưa có trong mô hình không mặc nhiên bằng 0.

## Kiểm kê đèn ứng viên

✅ có dữ liệu thực tế; 🔧 có cách đo, dự kiến instrument trong 2 tuần, chưa chắc đủ cohort; ❌ chưa có điều kiện đo đáng tin. Không đánh dấu ✅ cho mô phỏng.

| Đèn ứng viên từ handbook | Tầng | Trạng thái | Bằng chứng hiện có hoặc kế hoạch đo |
|---|---|---|---|
| Time-to-first-value (TTFV) | L | 🔧 | L-01; pilot_signed_at và first_value_at; schema 2026-09-11. |
| Pipeline coverage | L | 🔧 | CRM opportunities và target quý; schema 2026-09-11, chưa có pipeline thật. |
| % deal chết ở khâu security/procurement | L | 🔧 | CRM closed-lost reason được xác nhận; taxonomy 2026-09-11. |
| POC → paid | O | 🔧 | Join pilot_id với hợp đồng/hóa đơn; schema 2026-09-11, chờ cohort. |
| Sales cycle (ngày) | O | 🔧 | qualified_at → signed_at; schema 2026-09-11. |
| Usage depth trong tài khoản | O | 🔧 | Recruiter được cấp quyền và review events; schema 2026-09-11. |
| Chi phí triển khai ÷ ACV | O | 🔧 | Delivery timesheet, invoice tích hợp và ACV thực; schema 2026-09-11. |
| Tập trung doanh thu | O | 🔧 | Revenue ledger theo employer_id; schema 2026-09-11. |
| NRR | G | ❌ | Chưa có cohort trả phí/renewal; 2026-11-26 kiểm tra lại, không ngoại suy renewal năm. |
| Gross Margin | G | 🔧 | D25 chỉ là mô hình trước phí kênh; chọn G-01 điều chỉnh, ledger schema 2026-09-11. |
| CAC payback | G | 🔧 | Acquisition ledger và GP cohort; schema 2026-09-11; chọn G-02 CAC làm kết quả sớm. |

Chọn **6 đèn: 2L/2O/2G**; thêm SLA review/completion phù hợp workflow EquiScreen. Cây giả thuyết: **TTFV → adoption/POC-paid (4-8 tuần) → CAC/retention (1-3 tháng)**; **SLA review → POC-paid (4-8 tuần)**; **completion + AI/retry → CM (1-4 tuần)**. Đây là giả thuyết cần kiểm chứng, không phải nhân quả đã xác lập.

## Đèn báo sớm

| ID | Đèn | Định nghĩa và công thức | Nhịp · Owner | Hiện tại | 🟢 | 🟡 | 🔴 | Nguồn | Ngày kiểm tra | Báo trước cho | Luật |
|---|---|---|---|---|---|---|---|---|---|---|---|
| L-01 | TTFV tối đa - North Star | max((first_value_at - pilot_signed_at)/24h) trên 3 employer pilot gần nhất; first value = recruiter xác nhận 1 pack có evidence đúng, hữu ích cho review. | Tuần · Product Owner | Chưa đo; XÁM | ≤14 ngày | >14 đến ≤28 ngày | >28 ngày | [TB] TB-01: 4 kỳ tuần, ≥3 pilot; chốt 2026-09-25. Ngưỡng tạm: 14 ngày dành nửa pilot 4 tuần để kiểm chứng sử dụng, 28 ngày là hết thời gian tạo giá trị. | 2026-08-28 | POC-paid sau 4-8 tuần rồi G-02 sau 1-3 tháng; giá trị sớm giảm bỏ pilot. | R-01 |
| L-02 | Review đúng SLA 48h | 100 × pack được recruiter ký review trong 48h / tổng pack hoàn tất đã đủ 48h từ delivered_at; tính cả pack chưa mở. | Tuần · Customer Success | Chưa đo; XÁM | ≥90% | ≥80% đến <90% | <80% | [TB] TB-02: 4 kỳ tuần, ≥100 pack/kỳ; chốt 2026-10-09. 90% từ mục tiêu D25; 80% là sàn thử nghiệm khi ≥1/5 pack chậm; phân tách employer. | 2026-08-28 | POC-paid sau 4-8 tuần, retention sau 30-90 ngày; backlog cản giá trị đến người dùng. | R-02 |

TB-01 giữ cả pilot chưa có first value: tuổi hiện tại là cận dưới TTFV, không loại khỏi cohort. Nếu tuổi bất kỳ pilot chưa có giá trị >28 ngày thì đỏ; chưa xác định được màu hoặc cohort <3 thì XÁM. Không báo xanh chỉ dựa vào pilot thành công. TB-02 thiếu pack trưởng thành thì XÁM. Completion không thay human sign-off; không tự tuyển/loại ứng viên.

## Đèn vận hành

| ID | Đèn | Định nghĩa và công thức | Nhịp · Owner | Hiện tại | 🟢 | 🟡 | 🔴 | Nguồn | Ngày kiểm tra | Báo trước cho | Luật |
|---|---|---|---|---|---|---|---|---|---|---|---|
| O-01 | Completion evidence pack | 100 × job gốc có pack vượt policy checks và delivered trong 24h / tổng job gốc đủ 24h; retry cùng job_id, không tăng mẫu số; lỗi/timeout vẫn tính. | Tuần · Engineering | Chưa đo; mô hình 95% | ≥95% | ≥90% đến <95% | <90% | [MH] MH-03: sàn tính được 89,882%, chọn 90% có buffer 0,118 điểm %; mục tiêu 95% từ D25. Dưới sàn không đủ CM60% dù giá thử $0,20. | 2026-08-28 | G-01 sau 1-4 tuần; lỗi tốn tiền không tạo doanh thu. | R-03 |
| O-02 | Chi phí AI + retry / job thử | Tổng USD inference (retry, fail, cache billing) quy thuộc cohort / số job gốc; cộng cost đến ngày chốt, dự phòng invoice trễ; USD/job thử. | Ngày, tổng hợp tuần · FinOps | Chưa đo; mô hình $0,0039528 | ≤$0,004 | >$0,004 đến ≤$0,022 | >$0,022 | [MH] MH-01: tại completion sàn 90%, giá thử $0,20, share20%, non-AI $0,032/job thử; hai mốc bảo vệ CM60% và 50%. | 2026-08-28 | G-01 sau 1-4 tuần; bắt token/retry trước kỳ đóng sổ. | R-04 |

O-02 là ngân sách có điều kiện: giá thu được ≥$0,20, share ≤20%, non-AI ≤$0,032/job thử, completion ≥90%. Nếu vi phạm, không tô xanh: tính lại **AI cap = p × completion × (1 - share - CM mục tiêu) - non-AI**. Cap âm nghĩa là cấu trúc giá không khả thi. Chỉ dùng dữ liệu được phép, synthetic/khử định danh.

## Đèn kết quả

| ID | Đèn | Định nghĩa và công thức | Nhịp · Owner | Hiện tại | 🟢 | 🟡 | 🔴 | Nguồn | Ngày kiểm tra | Báo trước cho | Luật |
|---|---|---|---|---|---|---|---|---|---|---|---|
| G-01 | CM sau phí kênh | 100 × (doanh thu usage sau discount/refund, trước phí kênh - phí partner - toàn bộ direct COGS) / cùng doanh thu trước phí kênh; không gồm VAT; theo employer và tổng. | Tháng · Finance | Chưa đo; $0,12: 48,4625%; thử $0,20: 61,0775% | ≥60% | ≥50% đến <60% | <50% | [MH] MH-04: chuyển target60%/floor50% D25 sang CM sau share; dưới 50% dừng mở rộng. Không coi mô hình là kết quả đạt. | 2026-08-28 | Kết quả economics và G90, không phải chỉ báo sớm. | R-05 |
| G-02 | CAC cohort trả phí | Tổng acquisition cost quy thuộc cohort (sales time, demo, campaign, onboarding bán và deal thất bại) / employer mới trả phí; loại recurring partner share đã trừ ở CM. | Tháng · Finance | Chưa đo; mục tiêu $1.500 | ≤$1.500 | >$1.500 đến ≤$6.840 | >$6.840 | [MH] MH-02: mục tiêu kênh $1.500 D25; trần = ARPU thử $950 × CM60% × 12 tháng. Chỉ hiệu lực nếu giữ được ARPU/CM. | 2026-08-28 | Kết quả acquisition, đọc cùng payback; không gắn giả chuỗi dự báo. | R-05 |

Mẫu số 0/chưa reconcile → XÁM, không đổi thành 0. Khi ARPU/CM giảm, trần CAC = **ARPU thực × CM thực × 12**. CM ≤0 dừng mở rộng. Giá thử chưa được chấp nhận: toàn bộ đèn thực tế vẫn XÁM; G-01 đỏ ở mô hình giá cũ là cảnh báo khả thi.

## Luật quyết định

| ID | NẾU | TRONG | VÀ | THÌ | KHÔNG THÌ | Luật dừng? |
|---|---|---|---|---|---|---|
| R-01 | L-01 >28 ngày | 2 phiên họp tuần liên tiếp | ≥3 pilot đã ký; giữ pilot chưa có giá trị, timestamp xác nhận với customer | Đóng băng pilot rộng mới; PO trong 2 ngày thu hẹp còn 1 use case/1 đội, sửa onboarding trong 7 ngày; mở lại khi 3 pilot kế tiếp đều TTFV ≤14 ngày. | Không tuyển thêm sales hoặc thêm logo để che tắc onboarding. | CÓ |
| R-02 | L-02 <80% | 2 tuần liên tiếp | Mỗi tuần ≥100 pack đủ 48h và ≥2 recruiter; đối chiếu sign-off | Dừng mở review queue mới tại employer lỗi; CS trong 48h tổ chức 2 buổi xử lý backlog, giữ chronological fallback; mở lại khi 2 tuần SLA ≥90%. | Không tự ký review, auto-reject hoặc bán thêm module để che adoption yếu. | CÓ |
| R-03 | O-01 <90% | 2 tuần liên tiếp | Mỗi tuần ≥500 job trưởng thành, trace lỗi đủ ≥95% job | Cắt scope về 1 định dạng CV/1 role; Engineering trong 7 ngày sửa top-2 lỗi, replay 200 hồ sơ khử định danh được phép; rollout lại khi ≥95% trên 500 job mới. | Không đổi định nghĩa hoàn tất, bỏ job lỗi hoặc hạ policy checks để làm đẹp tỷ lệ. | KHÔNG |
| R-04 | O-02 >$0,004/job thử hoặc AI cap tính lại <0 | 7 ngày liên tiếp; cap âm xác nhận trong 1 ngày | ≥500 job có cost trong cửa sổ; cap âm cần 1 bảng giá/COGS do Finance xác nhận | Giới hạn 1 retry/job; FinOps trong 24h chặn batch mở rộng, kiểm tra routing; Engineering eval 200 hồ sơ trước đổi model. Cap âm: dừng mở rộng, tính lại giá/share trong 2 ngày. Mở lại khi trong cap 7 ngày và eval không giảm chất lượng. | Không cắt QA/human review, không tăng volume để bù biên âm. | CÓ |
| R-05 | G-01 <50% hoặc G-02 >$6.840; hoặc CAC vượt trần tính lại; hoặc CM ≤0 | 1 kỳ đóng sổ 30 ngày; CM ≤0 xác nhận trong 1 ngày | ≥3 employer trả phí, reconcile ≥95%; CM ≤0 cần 1 employer có ledger xác nhận | Đóng băng acquisition mới; Finance trong 7 ngày đàm phán giá/share với p_min = cost/job ÷ (1 - share - 60%), gửi 3 báo giá; mở khi CM ≥60% và CAC trong trần trên cohort đủ mẫu. | Không giảm giá thiếu tính lại economics, giấu phí partner, loại deal thất bại hoặc đếm signed pilot như paid. | CÓ |

Thiếu mẫu: XÁM, hoàn tất instrumentation trước 2026-09-11, không tự cho phép scale. Vàng: owner mở ticket nguyên nhân trong 2 ngày, giữ quy mô pilot hiện hữu. Sự cố auto-reject/quyết định tuyển dụng tự động xử lý ngay theo release blocker, không chờ đủ mẫu tài chính. Các hành động trên là đề xuất, chưa thực thi.

## Cổng gác 90 ngày

| Ngày | Metric gác cổng | Ngưỡng | Bằng chứng vật lý | Nếu đạt | Nếu trượt |
|---|---|---|---|---|---|
| 30 | Tỷ lệ evidence pack được recruiter xác nhận hữu ích | ≥80% trên ≥300 hồ sơ synthetic/khử định danh, ≥3 recruiter; hữu ích = evidence đúng nguồn và đủ giúp review; đếm 1 lần/pack | 2026-09-27: eval_300.csv (job_id, rubric v1, useful_label, reviewer_id giả danh) + eval_report.pdf. CHƯA TỒN TẠI, phải chạy eval thật. | GO | FIX |
| 60 | O-01 completion | ≥95% trên ≥2.000 job gốc trưởng thành trong 4 tuần gần nhất | 2026-10-27: jobs_4weeks.csv + policy_delivery_audit.csv nối job_id. CHƯA TỒN TẠI. | GO | PIVOT |
| 90 | G-01 CM sau kênh | ≥60% trên 30 ngày gần nhất, ≥3 employer trả phí; dùng hóa đơn thực, không dùng giá đề xuất | 2026-11-26: revenue_cogs_partner_ledger.csv + hóa đơn che thông tin + reconciliation_report.pdf. CHƯA TỒN TẠI. | GO | KILL |

D30 kiểm chứng giá trị, không đo doanh thu; 80% là mục tiêu thử nghiệm 4/5 pack hữu ích, không phải benchmark, rubric phải khóa trước eval. Mỗi cổng đúng 1 metric; sample chỉ là điều kiện tin cậy. **FIX 1 lần/vấn đề:** D30 trượt → sửa 14 ngày, kiểm tra lại trên 300 hồ sơ mới trước 2026-10-11; trượt lần hai → PIVOT sang evidence retrieval không xếp hạng. D60 trượt → PIVOT phạm vi đó, không tiếp tục FIX. Thiếu evidence/mẫu tại gate thì không GO, thực hiện nhánh trượt. GO chỉ cho bước tiếp theo trong shadow/sandbox; phải đóng release blockers trước sử dụng ảnh hưởng ứng viên.

## Kill criteria

Đến ngày 90 (2026-11-26), nếu CM sau kênh 30 ngày gần nhất <60% trên ≥3 employer trả phí, **KILL phương án EquiScreen qua kênh Base với cấu trúc giá/share đang thử**: dừng acquisition/triển khai mới, hoàn tất nghĩa vụ pilot hiện có. Nếu <3 employer trả phí hoặc thiếu ledger đối soát tại mốc đó, cũng đóng thử nghiệm vì không chứng minh được giả thuyết; không coi CM bằng 0, không kéo dài bằng FIX. Đóng kênh thử nghiệm không đồng nghĩa phải đóng công ty.

## Chưa đo được

| Đèn hoặc giả định | Cần gì để đo | Ai chịu trách nhiệm | Ngày có số |
|---|---|---|---|
| Finance EquiScreen, willingness-to-pay | Finance model riêng, 3 buyer interview/báo giá $0,20; xác nhận volume, discount/refund, ngân sách; không có phản hồi thì vẫn thiếu. | Product Owner + Finance | 2026-09-11 |
| L-01 TTFV | pilot_signed_at/first_value_at có sign-off; 4 snapshot tuần, ≥3 pilot. Không có khách thì báo thiếu baseline. | Product Owner | 2026-09-25 |
| L-02 SLA review | delivered_at/reviewed_at; 4 tuần ≥100 pack/tuần; pseudonymous IDs. | Customer Success | 2026-10-09 |
| O-01/O-02 | Job gốc, policy_pass, delivery, retry, cache/token cost; schema 2026-09-11, ≥2.000 job D60. | Engineering + FinOps | 2026-10-27 |
| G-01/G-02, delivery COGS | Hóa đơn, refunds, fee, cloud bills, QA/delivery timesheet và full acquisition cost; ≥3 khách. | Finance | 2026-11-26 |
| Retention/renewal, NRR | Hợp đồng/cohort; D90 chỉ kiểm retention 30 ngày nếu đủ dữ liệu; annual renewal chưa đủ thời gian. | Customer Success | 2026-11-26 |
| Rev-share, quyền quan sát Base | Điều khoản kênh, fee schedule, event permissions; 20% chỉ là đề xuất D25, chưa ký. | Partner Lead + Product Owner | 2026-09-11 |

Ngày trên là deadline thu thập/xem lại, không hứa có số. Không tạo log/hợp đồng/eval/doanh thu giả. D25 mô tả risk checklist Day22 nhưng file đó ngoài hai thư mục được cung cấp; chưa kiểm tra độc lập Day22.

## Phụ lục ngưỡng suy từ mô hình

| ID | Metric | Input Day 24–25 | Phép tính | Kết quả và ngưỡng áp dụng |
|---|---|---|---|---|
| MH-01 | O-02 AI + retry/job thử | D25 Cost B31=$0,00366; B46=8%; B43=$0,012; B50:B52: $12/h, QA5%, 2 phút. D26: p=$0,20/job hoàn tất; share20% (D25 Channel B41); completion floor90%; CM target60%, floor50%. | QA/job thử = 0,05 × 2/60 × 12 = $0,020; non-AI = 0,012 + 0,020 = $0,032; AI nền = 0,00366 × 1,08 = $0,0039528; cap60 = 0,20 × 0,90 × (1 - 0,20 - 0,60) - 0,032 = $0,004; cap50 = 0,20 × 0,90 × (1 - 0,20 - 0,50) - 0,032 = $0,022. | O-02 xanh ≤0,004; vàng (0,004;0,022]; đỏ >0,022 USD/job thử. Không chia tiếp completion vì mẫu số là job thử. |
| MH-02 | G-02 CAC và ngân sách payback | D25 Channel B42: CAC mục tiêu $1.500/khách; B8:12 tháng; Cost B11:4.750 job hoàn tất/khách/tháng; Pricing B32:60%; p thử D26=$0,20. | ARPU = 4.750 × 0,20 = $950/tháng; GP mục tiêu = 950 × 0,60 = $570/tháng; CAC trần = 570 × 12 = $6.840/khách; payback tại mục tiêu = 1.500/570 = 2,6316 tháng. | G-02 xanh ≤$1.500; vàng (1.500;6.840]; đỏ >$6.840. ARPU/CM giảm phải giảm trần. Độc lập phép tính token MH-01. |
| MH-03 | O-01 completion | D25 Pricing B29=$0,0159528/job thử, B30=$0,020; p thử=$0,20; share20%; CM60%; completion target Cost B10=95%. | Cost/job thử = 0,0159528 + 0,020 = $0,0359528; completion min = 0,0359528/(0,20 × (1 - 0,20 - 0,60)) = 0,89882 = 89,882%; sàn vận hành = 90%; buffer = 90 - 89,882 = 0,118 điểm %. | O-01 đỏ <90%; vàng [90%;95%); xanh ≥95%. AI/non-AI tăng phải tính lại sàn. |
| MH-04 | G-01 CM và cầu nối giá | D25 Cost B65=$179,764/tháng, B11=4.750; Pricing B19=$0,12, B13=$0,20; Channel B41=20%; kế thừa target60%/floor50% Pricing B23,B32 nhưng áp dụng sau share. | Cost/job = 179,764/4.750 = $0,03784505; CM cũ = 1 - 0,20 - 0,03784505/0,12 = 48,4625%; p_min60 = 0,03784505/0,20 = $0,18922526; CM thử = 1 - 0,20 - 0,03784505/0,20 = 61,0775%; GP thử = 950 - 190 - 179,764 = $580,236/tháng; payback dự phóng = 1.500/580,236 = 2,5852 tháng. | G-01 xanh ≥60%; vàng [50%;60%); đỏ <50%. Giá cũ đỏ; giá thử chỉ đạt trên mô hình. |

**Độ nhạy:** giá cũ $0,12, completion95%: cap AI để giữ CM60% = 0,12 × 0,95 × 0,20 - 0,032 = **-$0,0092/job thử**: AI miễn phí vẫn không đủ. Nếu giữ giá/cost nền, share tối đa = 1 - 60% - 0,03784505/0,12 = **8,4625%**, so với đề xuất 20%. Đây là phương án đàm phán, không phải partner đã đồng ý.

**Nguồn nội bộ, đọc 2026-08-28:**

- D24: `Track1-DAY24-2A202601716-NguyenHuyToan/Track1-DAY24-2A202601716-NguyenHuyToan/2A202601716_NguyenHuyToan_Day24.xlsx`; `1. Assumptions!D7,D18,D22,B39` xác nhận SaleMate; không dùng cho economics EquiScreen.
- D25: `Track1-DAY25-2A202601716-NguyenHuyToan/outputs/day25_submission/NguyenHuyToan_Day25_model.xlsx`; `1_Cost_Job!B5:B12,B31,B43,B46:B56,B65:B66`; `2_Pricing!B13,B19,B23,B29:B34`; `4_Channel_Fit!B5:B10,B39:B42`; `5_90Day_Plan!B12:D25`.
- PDF D25: `outputs/day25_submission/NguyenHuyToan_Day25_onepager.pdf` là tóm tắt; ưu tiên công thức workbook.
- Không dùng ngưỡng [BM]. Giá API/tỷ giá/nguồn thị trường trong D25 không được nhận là báo giá hiện hành đã xác minh lại. D26 dùng cost giả định, pilot phải thay invoice thật. TB là kế hoạch baseline, không phải số đã đo.

## Ghi nhận AI critique

| Phản biện | Chấp nhận hay bác bỏ | Thay đổi đã thực hiện | Lý do |
|---|---|---|---|
| Day24 khác sản phẩm; partner-led không tự động B2B2C. | Áp dụng trong bản soạn AI; chờ học viên duyệt. | Chọn B2B EquiScreen, loại churn/CAC SaleMate khỏi phép tính. | Không tạo lịch sử giả, giữ dòng tiền/người dùng nhất quán. |
| GM68,5% bỏ phí share khiến kênh có vẻ khả thi. | Áp dụng trong bản soạn AI; chờ học viên duyệt. | CM sau share48,4625%; p_min và kịch bản $0,20; giữ giá gốc đối chiếu. | Không che recurring fee, không nhận giá mới được khách chấp nhận. |
| Chỉ tính pilot/job thành công làm đẹp metric. | Áp dụng trong bản soạn AI; chờ học viên duyệt. | Giữ pilot mở/job lỗi/retry; thiếu mẫu XÁM; công khai evidence chưa tồn tại. | Chống survivor bias/double counting/màu xanh giả. |

AI hỗ trợ soạn và rà soát theo yêu cầu; chưa có peer review độc lập hoặc học viên phê duyệt. Không nhận học viên đã tự viết bản đầu.

## Tự kiểm theo rubric v2.0.0

| Tiêu chí | Tự rà | Điểm đề xuất để học viên duyệt |
|---|---|---|
| Tier Discipline | B2B, TTFV, 2L/2O/2G, owner/formula/delay; chuỗi dự báo chưa thực chứng. | 18/20 |
| Threshold Quality | 4 MH, 2 TB có lịch/mẫu; vùng không chồng; giá/volume/share chưa xác thực, thiếu Day24 cùng sản phẩm. | 24/30 |
| Decision Rule Quality | 5 luật đủ 5 vế, 4 luật dừng có điều kiện mở lại. | 29/30 |
| 90-Day Gates | 3 gate, mỗi gate 1 metric; FIX một lần và kill có số. | 15/15 |
| Honesty | Giả định/chưa đo có owner/deadline; không bịa log/hợp đồng. | 5/5 |

Tự rà đề xuất **91/100**, không phải điểm chính thức/semantic grader. Người chấm cần xem giới hạn lớn nhất: giá $0,20 và economics kênh chưa kiểm chứng; Day24 khác sản phẩm. PASS chỉ chứng minh cấu trúc.
