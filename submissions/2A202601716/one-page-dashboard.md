Nguyễn Huy Toàn · 2A202601716 &nbsp; | &nbsp; B2B · 2026-08-28 · Họp tuần: Product Owner (PO)



# EquiScreen | Operating Dashboard



Chẩn đoán: doanh nghiệp tuyển dụng trả tiền; recruiter sử dụng evidence panel. Ứng viên là bên bị tác động, không sử dụng giao diện trực tiếp. Kênh phân phối lựa chọn trong kịch bản: Base Hiring.

North Star: L-01 TTFV tối đa ≤14 ngày trên 3 pilot gần nhất. Thông số vận hành: giá $0,20/job hoàn tất, chia sẻ doanh thu 20%; mục tiêu CM sau kênh ≥60%.

01 / Cây tín hiệu - 2 Leading · 2 Operating · 2 Lagging

| ID | Metric / công thức ngắn | Xanh (X) · Vàng (V) · Đỏ (Đ) | Nhịp · Owner · Downstream |

| --- | --- | --- | --- |

| L-01 | TTFV tối đa (ngày) · max(ký pilot → recruiter xác nhận pack hữu ích); giữ pilot mở. | X ≤14 · V (14;28] · Đ >28 · [TB] TB-01 | Tuần · PO · POC-paid 4-8 tuần → CAC 1-3 tháng · R-01 |

| L-02 | Review đúng SLA48h · review trong 48h / pack đã đủ 48h; gồm pack chưa mở. | X ≥90% · V [80%;90%) · Đ <80% · [TB] TB-02 | Tuần · Customer Success (CS) · POC-paid 4-8 tuần; retention 30-90 ngày · R-02 |

| O-01 | Completion · job pass policy + delivered ≤24h / job gốc đủ 24h. | X ≥95% · V [90%;95%) · Đ <90% · [MH] MH-03 | Tuần · Engineering (ENG) · CM sau 1-4 tuần · R-03 |

| O-02 | AI + retry / job thử · tổng USD inference, gồm fail/cache/retry / job gốc. | X ≤$0,004 · V (0,004;0,022] · Đ >$0,022 · [MH] MH-01 | Ngày → tuần · FinOps · CM sau 1-4 tuần · R-04 |

| G-01 | CM sau kênh · (doanh thu - partner fee - direct COGS) / doanh thu. | X ≥60% · V [50%;60%) · Đ <50% · [MH] MH-04 | Tháng · Finance (FIN) · Kết quả economics → G90 · R-05 |

| G-02 | CAC cohort trả phí · full acquisition cost, gồm deal thất bại / khách mới trả phí. | X ≤$1.500 · V (1.500;6.840] · Đ >$6.840 · [MH] MH-02 | Tháng · FIN · Kết quả acquisition, đọc cùng payback · R-05 |

Quy ước: tỷ lệ ×100%; job lỗi vẫn tính, retry không tăng mẫu số. Mẫu số 0/thiếu mẫu → XÁM. O-02/G-02 chỉ dùng khi điều kiện kinh tế trang 2 còn đúng; sai điều kiện phải tính lại cap. Chuỗi downstream là giả thuyết cần kiểm chứng.

02 / Năm luật quyết định - NẾU / TRONG / VÀ → THÌ / CẤM

R-01 · DỪNG. TTFV >28 ngày / 2 kỳ tuần / ≥3 pilot, gồm pilot mở → PO đóng băng pilot rộng; trong 2 ngày thu về 1 use case/1 đội, sửa onboarding trong 7 ngày. Cấm thêm sales/logo để che tắc.

R-02 · DỪNG. SLA <80% / 2 tuần / mỗi tuần ≥100 pack đủ48h, ≥2 recruiter → CS dừng mở queue mới; trong 48h tổ chức 2 buổi xử lý backlog, giữ chronological fallback. Cấm tự ký review/auto-reject/upsell.

R-03. Completion <90% / 2 tuần / ≥500 job mỗi tuần, trace≥95% → ENG cắt scope 1 CV format/1 role; sửa top-2 lỗi trong 7 ngày, replay 200 hồ sơ được phép. Cấm bỏ job lỗi/hạ policy checks.

R-04 · DỪNG. AI >$0,004 / 7 ngày / ≥500 job có cost; hoặc cap âm được FIN xác nhận trong 1 ngày → FinOps chặn batch mở rộng trong 24h, giới hạn 1 retry; ENG eval 200 hồ sơ trước đổi model. Cap âm: tính lại giá/share trong 2 ngày. Cấm cắt QA hoặc bù lỗ bằng volume.

R-05 · DỪNG. CM<50% hoặc CAC>$6.840/trần tính lại / 30 ngày / ≥3 khách trả phí, reconcile≥95% → FIN đóng băng acquisition; đàm phán giá/share và gửi 3 báo giá trong 7 ngày. CM≤0: dừng trong 1 ngày khi 1 ledger xác nhận. Cấm giảm giá mù/giấu fee/đếm pilot như paid.

Mở lại: R01: 3 pilot kế tiếp TTFV≤14d; R02: 2 tuần SLA≥90%; R03: 500 job mới completion≥95%; R04: trong cap7d, eval không giảm; R05: CM≥60%, CAC trong trần, đủ mẫu. Vàng: ticket nguyên nhân ≤2 ngày, giữ quy mô. Auto-reject: xử lý ngay, không chờ mẫu.

03 / Cổng 90 ngày - mỗi cổng một metric

| Ngày / 2026 | Ngưỡng / mẫu | Hồ sơ đối soát yêu cầu | Đạt / Trượt |

| --- | --- | --- | --- |

| 30 · 27/09 | Pack hữu ích ≥80% · ≥300 hồ sơ, ≥3 recruiter | eval_300.csv + eval_report.pdf | GO / FIX |

| 60 · 27/10 | Completion ≥95% · ≥2.000 job / 4 tuần | jobs_4weeks.csv + policy_delivery_audit.csv | GO / PIVOT |

| 90 · 26/11 | CM≥60% / 30 ngày · ≥3 employer trả phí | revenue_cogs_partner_ledger.csv + đối soát/hóa đơn | GO / KILL |

FIX chỉ 1 lần: D30 sửa14d, thử 300 hồ sơ mới trước 11/10; trượt lại → PIVOT. KILL 26/11: CM<60%, hoặc <3 khách trả phí, hoặc thiếu ledger → đóng thử nghiệm kênh, dừng chi mới, hoàn tất nghĩa vụ cũ; không kéo dài bằng FIX. GO không thay release sign-off.

Đọc nguồn: 2026-08-28 · D25 = NguyenHuyToan_Day25_model.xlsx · Không dùng ngưỡng benchmark [BM]



# Ngưỡng có thể tính lại



A / Đối chiếu Day 24-25 và kịch bản Day 26

Số liệu theo mô hình Day 25

Đối chiếu Day24: SaleMate AI có ARPU1.490.000 VND/tháng; CAC5.500.000 VND; churn4%/tháng tại 1. Assumptions!D7,D22,D18; tên sản phẩm B39. Dashboard này sử dụng EquiScreen từ Day25, không trộn số liệu hai sản phẩm.

Đầu vào D25 EquiScreen: 5.000 job thử/tháng; completion95% → 4.750 pack hoàn tất; cost/job=$0,03784505; giá gốc=$0,12; ARPU=$570; GM trước kênh=68,4625%; CAC mục tiêu=$1.500; payback cho phép12 tháng. Share20% áp dụng cho 12 tháng đầu trong kịch bản.

Điều chỉnh giá: trừ share20%, CM giá gốc là 48,4625%. Để giữ CM60%, p_min=$0,18922526/job. Chọn $0,20 (trần25% giá trị trong D25 Pricing!B13), cho CM=61,0775%; nếu giữ $0,12 thì share phải ≤8,4625% với cost nền. Rà soát với 3 buyer trước 11/09.

B / Bốn phép tính [MH] - đơn vị USD, số học dùng giá trị chưa làm tròn

| ID / áp dụng | Input → phép tính → kết quả / nguồn |

| --- | --- |

| MH-01 · AI/job thử | Input: LLM0,00366; retry8%; infra0,012; QA5% × 2 phút × $12/h. p thử0,20; q sàn90%; share20%; CM60%/50%. · QA = 0,05 × 2/60 × 12 = 0,020; non-AI = 0,012 + 0,020 = 0,032. · AI nền = 0,00366 × 1,08 = 0,0039528/job thử. · Cap60 = 0,20 × 0,90 × (1 - 0,20 - 0,60) - 0,032 = 0,004. · Cap50 = 0,20 × 0,90 × (1 - 0,20 - 0,50) - 0,032 = 0,022. · Nguồn: D25 1_Cost_Job!B31,B43,B46,B50:B52; Channel!B41. |

| MH-02 · CAC | Input: 4.750 pack/khách/tháng; p thử0,20; CM60%; payback12 tháng; CAC mục tiêu1.500. · ARPU = 4.750 × 0,20 = 950/tháng; GP mục tiêu = 950 × 0,60 = 570/tháng. · CAC trần = 570 × 12 = 6.840/khách; payback mục tiêu = 1.500/570 = 2,6316 tháng. · Nguồn: D25 1_Cost_Job!B11; 4_Channel_Fit!B8,B42; 2_Pricing!B32. |

| MH-03 · Completion | Input: variable0,0159528 + QA0,020/job thử; p0,20; share20%; CM60%. · q_min = (0,0159528 + 0,020)/(0,20 × 0,20) = 89,882%. · Chọn sàn90%: buffer = 90 - 89,882 = 0,118 điểm %; target95% từ D25. · Nguồn: D25 2_Pricing!B29:B32; 1_Cost_Job!B10. |

| MH-04 · CM / giá | Input: COGS179,764/tháng; 4.750 pack; giá gốc0,12; share20%; p thử0,20. · Cost/job = 179,764/4.750 = 0,03784505; CM gốc = 1 - 0,20 - cost/0,12 = 48,4625%. · p_min60 = cost/(1 - 0,20 - 0,60) = 0,18922526; CM thử = 1 - 0,20 - cost/0,20 = 61,0775%. · GP thử = 950 - 190 - 179,764 = 580,236/tháng; payback = 1.500/580,236 = 2,5852 tháng. · Nguồn: D25 Cost!B65:B66; Pricing!B13,B19,B23,B32; Channel!B41. |

Điều kiện ngân sách: O-02 giả định p≥0,20; q≥90%; share≤20%; non-AI≤0,032/job thử. Nếu đổi: AI cap = p×q×(1-share-CM mục tiêu)-non-AI. Ở p0,12, q95%: cap60=-0,0092 (bất khả thi). CAC cap = ARPU thực×CM thực×12. CM≤0: dừng. CM dùng doanh thu trước fee, sau discount/refund; direct delivery phải vào COGS; recurring share không tính lại CAC.

C / Kế hoạch đo và lịch rà soát

| Hạng mục | Cách đo / owner / deadline |

| --- | --- |

| TB-01 / L-01 | 4 kỳ tuần, ≥3 pilot; ký → sign-off giá trị. Mở quá28d: đỏ; chưa rõ/thiếu cohort: XÁM. 14d dành nửa pilot4 tuần để học. PO · 25/09/2026. |

| TB-02 / L-02 | 4 kỳ tuần, ≥100 pack/kỳ; delivered/reviewed events, gồm pack chưa mở. 90% là mục tiêu D25; sàn thử80% bắt ≥1/5 pack chậm. CS · 09/10/2026. |

| Kinh tế / event / renewal | Finance EquiScreen, 3 buyer và điều khoản Base: PO/FIN · 11/09. Job/cost ledger: ENG/FinOps · 27/10. CM/CAC và retention30d: FIN/CS · 26/11. Renewal năm đánh giá khi cohort đủ12 tháng. |

Inventory B2B: kiểm kê11 đèn trong worksheet: TTFV, pipeline, procurement loss, POC-paid, sales cycle, usage, implementation/ACV, concentration, NRR, GM, payback. Ưu tiên instrument10 đèn; NRR đánh giá khi có cohort gia hạn phù hợp.

AI critique (3 sửa đổi): tách SaleMate/EquiScreen; đưa share vào CM và trình bày kịch bản giá; giữ pilot mở/job lỗi, thiếu mẫu XÁM. Tự rà đề xuất: 18/20 + 24/30 + 29/30 + 15/15 + 5/5 = 91/100, không phải điểm chính thức. Trọng tâm rà soát: giá/fee/volume và tính nhất quán nguồn.

Truy nguồn: D25 ở thư mục outputs/day25_submission; Cost = 1_Cost_Job, Pricing = 2_Pricing, Channel = 4_Channel_Fit. Đường dẫn và định nghĩa mở rộng trong submissions/2A202601716/operating-dashboard.md. Đơn giá API lấy theo đầu vào D25; cập nhật theo invoice ở mỗi kỳ đối soát.