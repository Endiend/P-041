# Nhật ký tuần 01 · 15/09 – 21/09/2026


**Lead tuần này:** Ngô Duy Ngọc
**Dữ liệu / task CVAT:** Ảnh giao thông đô thị — task 160 W1-BBOX-G6-T1

## Thành viên và phân công

| Thành viên | Vị trí | Phân công tuần này |
|---|---|---|
| Ngô Duy Ngọc (@NgoDuyNgoc) | Lead | Chia job, chốt edge case, review xác suất 10% mọi job, gán job 1706, review 1490-1493 |
| Nguyễn Minh Tú (@NguyenMinhTu) | Annotator | Job 1493,1709 |
| Vũ Trường Duy (@VuTruongDuy) | Annotator | Job 1492, 1708 |
| Phạm Nguyên Tuân (@PhamNguyenTuan) | Annotator | Job 1491, 1707 |
| Đinh Công Minh (@DinhCongMinh) | Reviewer · Annotator | Review job 1706-1709; gán job 1490 |

Đinh Công Minh vừa review vừa gán, nên job 1490 do Lead review.

## Công việc

| # | Nội dung công việc | Annotator | Reviewer | Hoàn thành | Ghi chú |
|---|---|---|---|---|---|
| 1 | Job 1493 — 25 ảnh, bbox `xe_may` / `o_to` / `nguoi` | @NguyenMinhTu | @NgoDuyNgoc | ✅ 100% | đã qua review |
| 2 | Job 1709 — 25 ảnh, segmentation | @NguyenMinhTu | @DinhCongMinh | ✅ 100% | đã hoàn thành 100% segmentation, đã qua review |
| 3 | Job 1492 — 25 ảnh, cùng nhãn | @VuTruongDuy | @NgoDuyNgoc | 🟡 90% | đang hoàn thiện nốt |
| 4 | Job 1708 — 25 ảnh, segmentation | @VuTruongDuy | @DinhCongMinh | 🟡 90% | hoàn thành 70% tiến độ, đang tiếp tục hoàn thiện |
| 5 | Job 1491 — 25 ảnh, cùng nhãn | @PhamNguyenTuan | @NgoDuyNgoc | ✅ 100% | đã qua review |
| 6 | Job 1707 — 25 ảnh, segmentation | @PhamNguyenTuan | @DinhCongMinh | ✅ 100% | đã hoàn thành 100% tiến độ, đã qua review |
| 7 | Job 1490 — 25 ảnh, bbox / polygon / polyline | @DinhCongMinh | @NgoDuyNgoc | ✅ 100% | đã qua review |
| 8 | Job 1706 — 25 ảnh, segmentation | @NgoDuyNgoc| @DinhCongMinh | ✅ 100% | đã hoàn thành 100% tiến độ, đã qua review |

Mức hoàn thành: ✅ xong **và đã qua review** · 🟡 đang làm (ghi %) · ⛔ bị chặn (ghi lý do) · ⬜ chưa bắt đầu

## Tổng kết

- Đã gán: 190 / 200 ảnh (95%)
- Qua review lần đầu: 170 / 200 ảnh (85%)
- Edge case mới: Các trường hợp xe ở xa sát nhau, màu vạch kẻ ban đêm, biển báo mờ vs biển quảng cáo, ranh giới polygon đường mờ và hiện tượng đèn giao thông phản chiếu trên gương kính tòa nhà (Job 1490).

## Vướng mắc

## Job 1490 – Bounding Box, Polygon & Polyline

| Khó khăn thấy trong job | Cách xử lý |
|---|---|
| **Các xe ở xa và gần sát sau:** khó phân biệt để đánh từng object riêng. | Zoom tối đa, căn cứ vào cụm đèn/nóc xe hoặc khoảng sáng giữa các xe để tách riêng từng bounding box; chỉ bao phần nhìn thấy rõ của từng xe, không vẽ gộp chung box. Trường hợp quá mờ dính chùm không đủ bằng chứng tách vật thể thì đánh dấu review/hỏi mentor, không tự đoán. |
| **Buổi tối khó phân biệt được màu của vạch kẻ đường:** ánh sáng yếu và đèn xe làm lóa khiến vạch trắng và vàng dễ lẫn lộn. | Zoom lớn và đối chiếu ngữ cảnh làn đường (tim đường phân 2 chiều thường là vàng, vạch chia làn cùng chiều là trắng) hoặc quan sát frame liền kề. Nếu vẫn không thể xác định chắc chắn màu sắc thì để nhãn review xin ý kiến mentor, không tự đoán màu. |
| **Một số biển báo mờ:** không rõ là biển quảng cáo hay là biển báo giao thông. | Không gán nhãn, đợi xin ý kiến guideline chính thức từ mentor. |
| **Các ảnh mờ khó phân biệt vùng đi polygon shape đường:** mép đường lẫn vào vỉa hè hoặc viền thân xe. | Chỉ đánh phần nhìn rõ bằng mắt, phần không phân biệt được là viền xe hay đường thì bỏ qua, tuân thủ nguyên tắc không suy đoán ranh giới. |
| **Các đèn giao thông ở xa mờ:** không rõ là đèn hay là phản chiếu vào gương tòa nhà. | Không đánh nhãn, đợi xin guideline cụ thể từ mentor. |

## Job 1492 – Bounding Box, Polygon & Polyline

|  Khó khăn thấy trong job | Cách xử lý |
|---|---|
| **Xe ở xa, kích thước nhỏ và khó xác định rõ biên (G06_B052):** một số xe nằm sát nhau nên dễ vẽ box rộng quá. | Chỉ bao phần nhìn thấy của từng xe, zoom ảnh và giữ box sát biên vật thể. |
| **Xe bị che bởi xe khác (G06_B058):** phần thân xe phía sau không nhìn thấy đầy đủ. | Chỉ annotate phần có bằng chứng trong ảnh, không suy đoán phần bị che khuất. |
| **Vùng `area/drivable` và `area/alternative` khó phân biệt ở mép đường (G06_B061):** biên giữa hai vùng không rõ. | Ưu tiên theo ngữ nghĩa của guideline; chỉ vẽ tới phần có biên nhìn thấy rõ, trường hợp không chắc thì đưa review. |
| **Vạch đường đôi ở xa (G06_B067):** hai vạch nằm gần nhau nên dễ tạo thành hai polyline. | Chỉ tạo **1 polyline ở giữa/tim vạch**, chọn đúng class `lane/double white` hoặc `lane/double yellow`. |
| **Biển báo nhỏ hoặc bị khuất một phần (G06_B073):** khó xác định kích thước chính xác của biển. | Dùng BBox cho `traffic sign`, chỉ bao phần biển nhìn thấy; không mở rộng box sang cột biển nếu không thuộc vật thể cần gán. |
## Job 1708 – Semantic Segmentation

|  Khó khăn thấy trong job | Cách xử lý |
|---|---|
| **Nhiều xe cùng xuất hiện trong một frame (G06_S053):** dễ nhầm giữa semantic segmentation và instance segmentation. | Tất cả xe được gán cùng class `car`; không tạo identity riêng cho từng chiếc xe. |
| **Xe bị che khuất bởi xe khác (G06_S058):** không nhìn thấy toàn bộ thân xe. | Chỉ tô mask phần pixel nhìn thấy, không suy đoán phần bị che. |
| **Ranh giới `road` và `sidewalk` ở mép đường khó nhìn rõ (G06_S061):** dễ tô lấn sang hai vùng. | Zoom để bám theo biên nhìn thấy; mỗi pixel chỉ thuộc tối đa một class. |
| **Vùng cây có các khoảng nhỏ nhìn xuyên qua (G06_S066):** khó xác định các khoảng nhỏ phía sau tán lá. | Không cố gán các vùng không đủ bằng chứng; ưu tiên xử lý theo class nhìn thấy rõ và đưa case không chắc vào review. |
| **Frame tối, một số vật thể nhỏ gần như không nhận diện được (G06_S072):** không đủ bằng chứng để xác định class. | Không đoán class chỉ để lấp ảnh; giữ vùng chưa chắc và đánh dấu review theo SOP. |
| **Nắp capo và taplo xe (job 1709):** chiếm khoảng 30–40% đáy ảnh ở nhiều frame, nhưng 19 class không có "ego vehicle". | Để trống (unlabeled), không ép vào `car` hay `road` (đúng Rule 03). Tạo Issue hỏi mentor có cấu hình nhãn ignore không. |
| **Tuyết phủ mặt đất (S084):** không rõ là road, sidewalk hay terrain. | Chỉ gán khi thấy rõ biên |
|**Vật thể ngoài 19 class:** biển Mobil, trạm xăng, thùng phuy, vòi cứu hỏa. | Biển quảng cáo không phải `traffic_sign`. Để trống hoặc xin quyết định của mentor. |
|**`area/drivable` và `area/alternative` (job 1493):** guideline nói "theo định nghĩa mentor chốt" nhưng không nêu định nghĩa. | Hỏi mentor một lần rồi ghi vào decision log. Trước khi có câu trả lời, chỉ dùng `area/drivable` cho làn xe  chạy. |
| **Phản chiếu kính chắn gió (S081, S098):** guideline cấm gán reflection, nhưng không nói pixel bên dưới gán class gì. | Gán theo cảnh thật nhìn thấy dưới lớp phản chiếu. Nếu không nhìn ra thì để trống |
| **Vegetation và terrain (S081):** luống hoa, bụi thấp, dải phân cách có lề bê tông. | Có thân hoặc tán thì gán `vegetation`, cỏ và đất thấp thì `terrain`. Dùng cùng một quy tắc cho cả batch. |
| **Ảnh ban đêm (B076):** đèn chói, vạch mờ, đèn giao thông chỉ vài pixel. Guideline nói "quá nhỏ/mờ thì đưa review" nhưng không cho ngưỡng. | Chỉ gán nhãn khi zoom lên vẫn thấy được vật, hoặc thấy các thành phần đặc trưng của vật. Không đoán. Nếu không đủ bằng chứng thì không gán. |
| **BBox cho vật thể bị che (B084, B091):** guideline không nói box bao phần nhìn thấy hay suy ra cả vật. | Đề xuất bao phần nhìn thấy, bật `occluded` |
| **Polyline vạch kẻ:** guideline nói "theo tim/biên theo quy ước của bài" nhưng không nêu quy ước. Vạch đôi vẽ một hay hai đường? | Chỉ vẽ **1 đường ở giữa (tim)** vạch kẻ. Vạch đôi cũng chỉ vẽ 1 polyline, gán đúng class như `lane/double yellow`. |
| **Tên nhãn khác nhau giữa hai tài liệu:** cả hai job cùng có 31 nhãn gộp từ 2 guideline. `pedestrian` / `person`, `traffic light` / `traffic_light` và `traffic sign` / `traffic_sign` là các cặp trùng nghĩa. Job segmentation còn thừa 9 nhãn `area/`, `lane/`. | Job 1709 chỉ dùng tên dạng gạch dưới (`person`, `traffic_light`, `traffic_sign`). Job 1493 chỉ dùng tên bbox (`pedestrian`, `traffic light`, `traffic sign`). Hỏi mentor có cần ẩn nhãn thừa không. |
| **Mask trong CVAT có thể chồng lên nhau,** trong khi Rule 01 cấm. |  Vẽ vùng lớn trước (road, sky, building), rồi vật thể nhỏ. Dùng Lock/Hide theo label để khỏi sửa nhầm. Vẽ xong thì dùng layer của CVAT để đặt mask nào nằm trên, mask nào nằm dưới, đúng thứ tự phía trước và phía sau trong ảnh. |
|**Các xe bật đèn ở ảnh tối bị đèn lóa, tối quá không nhìn thấy(Job 1491)** | Chỉ thực hiện gán nếu nhìn thấy rõ viền của vật thể.
| **Tuyết phủ mặt đất (G06_S027,S030):** không rõ là road, sidewalk hay terrain. |Chỉ gán khi thấy rõ biên
|**`area/drivable` và `area/alternative` (job 1491):** guideline nói theo định nghĩa mentor chốt nhưng không nêu định nghĩa. |Dùng `area/drivable` cho phần đường xe chạy. |
| **Phản chiếu kính chắn gió(Job1491):** guideline cấm gán reflection, nhưng không nói pixel bên dưới gán class gì. | Không gán các vật thể phản chiếu |
| **BBox cho vật thể bị che(VD:B046-Job1491):** guideline không nói box bao phần nhìn thấy hay suy ra cả vật. | Đề xuất bao phần nhìn thấy, bật `occluded` |
| **Polyline vạch kẻ:** guideline nói "theo tim/biên theo quy ước của bài" nhưng không nêu quy ước. Vạch đôi vẽ một hay hai đường? | Chỉ vẽ **1 đường ở giữa (tim)** vạch kẻ. Vạch đôi cũng chỉ vẽ 1 polyline, gán đúng class như `lane/double yellow`. |
| **Mask trong CVAT có thể chồng lên nhau,** trong khi Rule 01 cấm. |  Vẽ vùng lớn trước (road, sky, building), rồi vật thể nhỏ. Dùng Lock/Hide theo label để khỏi sửa nhầm. Vẽ xong thì dùng layer của CVAT để đặt mask nào nằm trên, mask nào nằm dưới, đúng thứ tự phía trước và phía sau trong ảnh. |
| **Các khoảng vùng nhỏ thuộc bầu trời nhìn xuyên qua kẽ lá(job segmentation)** | Theo yêu cầu của mentor, không vẽ được các khoảng nhỏ đó do lớp lá cây, vẽ lớp `vegetation` đè lên phần đó khi 2 lớp chồng nhau |
| **Các khoảng vùng trong frame quá tối không thể nhìn rõ vật thể hay loại lớp(G06-Job1707)** | Không thực hiện vẽ segmentation những phần vùng đó. |

## Kế hoạch tuần 02

### Việc cần mentor chốt (Lead gom và hỏi một lần trong tuần)

Các case dưới đây guideline chưa nói rõ hoặc mơ hồ. Cần mentor quyết định để ghi vào decision log (QD-xxx), tránh mỗi người làm một kiểu:

- Nắp capo, taplo (ego vehicle): có label ignore/unlabeled trong cấu hình batch không.
- `area/drivable` và `area/alternative`: định nghĩa cụ thể.
- Vạch kẻ đường: trong segmentation gán road hay không tô. Trong bbox/polyline, xác nhận quy ước 1 polyline ở tim vạch, kể cả vạch đôi.
- Vật thể ngoài 19 class: biển quảng cáo, guardrail, trụ cứu hỏa, thùng phuy, trạm xăng.
- Xe SUV, pickup, van: gán car hay truck.
- Núi và đồi xa: terrain hay vegetation. Tuyết phủ mặt đất: gán class nào.
- Cột đỡ biển/đèn và dây cáp mảnh: gán pole hay không tô.
- BBox cho vật bị che: xác nhận bao phần nhìn thấy và bật occluded.
- Nhãn trùng nghĩa giữa hai guideline: có ẩn 9 nhãn thừa `area/` và `lane/` trong job segmentation không.
- Ngưỡng ảnh tối hoặc vật quá nhỏ: có ngưỡng cụ thể để đưa review không.
- Quy tắc phân biệt biển quảng cáo vs biển báo mờ, và đèn tín hiệu vs ánh sáng phản chiếu gương kính tòa nhà (Job 1490).

### Quy tắc làm việc chung trong tuần

- Áp dụng thống nhất các cách xử lý tạm ghi trong bảng "Vướng mắc" cho đến khi có QD chính thức. Khi có quyết định, cả nhóm sửa lại các ảnh đã gán theo đúng quyết định đó.
- Vẽ vùng lớn trước (road, sky, building, vegetation), sau đó tới vật thể nhỏ, dùng Lock/Hide theo label để tránh mask chồng nhau (Rule 01).
- Ca không chắc thì tạo Issue (UNCERTAIN_CLASS, UNCERTAIN_BOUNDARY, UNCERTAIN_SMALL_OBJECT), không đoán để lấp kín ảnh (Rule 03).
- Tự review toàn ảnh và kiểm tra checklist mục 7 trước khi chuyển job sang completed.

### Rủi ro

- Lead đồng thời gán job 1706 và review job 1490–1493 cùng review xác suất 10%, dễ dồn việc vào cuối tuần. Nên review theo từng job ngay khi annotator báo xong.
- Job 1708 và 1709 (segmentation) tốn thời gian hơn bbox do ảnh tối, tuyết và nhiều vùng cây. Hiện Job 1708 mới đạt 50%, cần theo dõi sát để hoàn thành sớm.
- Nếu mentor chốt chậm, các quyết định tạm thời có thể phải sửa hàng loạt. Nên gửi câu hỏi sớm, đầu tuần.