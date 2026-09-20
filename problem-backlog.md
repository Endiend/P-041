# Problem backlog

Những chỗ gặp trong lúc gán nhãn mà **guideline chưa trả lời được**, cộng các pain point về công cụ.

Ghi ngay khi gặp, kể cả lúc chưa biết xử lý thế nào. Một edge case không được ghi lại thì
mỗi người sẽ tự xử lý theo một kiểu — và đó là nguồn lớn nhất của nhãn không nhất quán.

> Nguồn: nhật ký tuần 01 (15/09 – 21/09/2026), task 160 W1-BBOX-G6-T1. Mã ảnh (G06_B…, G06_S…) ghi theo nhật ký; chưa có link CVAT trực tiếp.

## Danh sách

| Mã | Tóm tắt | Loại | Mục guideline | Trạng thái | Kết quả |
|---|---|---|---|---|---|
| [P-001](#p-001) | Cây (kể cả cây trụi lá) che một phần building: tô building phủ cả cây hay tách riêng vegetation | Guideline đã rõ | §3 (Không chồng lấn, Occlusion), §4 | ✅ Đã chốt | — |
| [P-002](#p-002) | Building phía sau bị che: có cần đánh cờ "occluded" không | Guideline chưa nói tới | §3 (Occlusion) | ↗️ Hỏi BTC | — |
| [P-003](#p-003) | Semi-auto tô lẹm sang cành cây và sky, phải sửa tay nhiều | Pain point công cụ | — | ↗️ Hỏi BTC | — |
| [P-004](#p-004) | Xe ở xa, mờ, không phân biệt được truck/bus (xe thùng trắng): để trống hay chọn class | Guideline đã rõ (escalate) | §4 (car vs truck vs bus), §6 | ↗️ Hỏi BTC | — |
| [P-005](#p-005) | `area/drivable` và `area/alternative`: guideline không nêu định nghĩa | Guideline chưa nói tới | — (guideline bbox) | 🔴 Mở | — |
| [P-006](#p-006) | Polyline vạch kẻ: vạch đôi vẽ một hay hai đường, vẽ theo tim hay theo biên | Guideline chưa nói tới | — (guideline bbox) | 🔴 Mở | — |
| [P-007](#p-007) | Nắp capo và taplo chiếm 30–40% đáy ảnh, không có class "ego vehicle" | Guideline chưa nói tới | §1 (RULE 03), §6 | 🔴 Mở | — |
| [P-008](#p-008) | Tuyết phủ mặt đất: road, sidewalk hay terrain | Guideline chưa nói tới | §4 (road vs sidewalk, vegetation vs terrain) | 🔴 Mở | — |
| [P-009](#p-009) | Vật thể ngoài 19 class: biển quảng cáo (Mobil), trạm xăng, thùng phuy, vòi cứu hỏa | Guideline chưa nói tới | §1, §6 | 🔴 Mở | — |
| [P-010](#p-010) | Phản chiếu trên kính chắn gió: cấm gán reflection nhưng không nói pixel bên dưới gán class gì | Guideline mơ hồ | §3 (Reflection/Shadow) | 🔴 Mở | — |
| [P-011](#p-011) | Vegetation vs terrain: luống hoa, bụi thấp, dải phân cách có lề bê tông | Guideline mơ hồ | §4 (vegetation vs terrain) | 🔴 Mở | — |
| [P-012](#p-012) | Ảnh tối, vật nhỏ, đèn lóa: guideline nói đưa review nhưng không cho ngưỡng | Guideline mơ hồ | §3 (Object nhỏ/xa), §6 | 🔴 Mở | — |
| [P-013](#p-013) | BBox cho vật thể bị che khuất: bao phần nhìn thấy hay suy ra cả vật | Guideline chưa nói tới | — (guideline bbox) | 🔴 Mở | — |
| [P-014](#p-014) | Tên nhãn khác nhau giữa hai guideline và 9 nhãn thừa trong job segmentation | Guideline mâu thuẫn | §2 | 🔴 Mở | — |
| [P-015](#p-015) | Mask trong CVAT có thể chồng lên nhau, trong khi Rule 01 cấm | Pain point công cụ | §1 (RULE 01) | 🔴 Mở | — |
| [P-016](#p-016) | Khoảng trời nhìn xuyên qua kẽ lá: vẽ sky hay để vegetation phủ | Guideline mơ hồ | §1 (RULE 03), §3 | ✅ Đã chốt | — |

**Loại**

| Loại | Nghĩa là |
|---|---|
| Guideline đã rõ | Guideline có quy tắc trả lời được, ghi lại để tra cứu |
| Guideline chưa nói tới | Tình huống không có trong guideline |
| Guideline mơ hồ | Đọc guideline ra được hai cách hiểu trở lên |
| Guideline mâu thuẫn | Hai mục trong guideline nói ngược nhau |
| Pain point công cụ | Guideline rõ, nhưng làm trên CVAT chậm hoặc dễ sai |

**Trạng thái:** 🔴 Mở · 🗣️ Đang bàn · ↗️ Hỏi BTC · ✅ Đã chốt (trỏ sang QĐ) · 🛠️ Làm tool (trỏ sang `source-tool/`) · ⚪ Bỏ (ghi lý do)

---

## P-001

**Cây (kể cả cây trụi lá) che một phần building: tô building phủ cả cây hay tách riêng vegetation**

- **Loại:** Guideline đã rõ
- **Mục guideline:** §3 (Không chồng lấn, Occlusion), §4 (vegetation vs terrain)
- **Người phát hiện:** @NgoDuyNgoc · 20/09/2026
- **Link CVAT:** (bỏ trống)
- **Mô tả:** Mask semi-auto của building phủ luôn cả cây đứng phía trước.
- **Các cách hiểu:**
  1. Tô building bao trùm cả cây vì cây chiếm diện tích nhỏ.
  2. Tách riêng: pixel của cây là `vegetation`, building chỉ tô phần nhìn thấy.
- **Xử lý tạm trong lúc chờ:** không cần chờ. Theo cách 2, vì mỗi pixel chỉ thuộc một class và pixel nhìn thấy thuộc vật ở phía trước.
- **Kết quả:** ✅ Guideline đã rõ, không cần QĐ. Cành quá mảnh, dày đến mức không tách được thì tạo Issue `UNCERTAIN_BOUNDARY`.

## P-002

**Building phía sau bị che: có cần đánh cờ "occluded" không**

- **Loại:** Guideline chưa nói tới
- **Mục guideline:** §3 (Occlusion)
- **Người phát hiện:** @NgoDuyNgoc · 20/09/2026
- **Link CVAT:** (bỏ trống)
- **Mô tả:** Guideline chỉ nói gán các pixel nhìn thấy, không nhắc đến attribute "occluded" cho segmentation.
- **Các cách hiểu:**
  1. Không cần cờ, việc bị che đã thể hiện qua hình dạng mask.
  2. Batch có attribute occluded riêng trong label config, cần dùng.
- **Xử lý tạm trong lúc chờ:** không đánh cờ, chỉ tô phần nhìn thấy.
- **Kết quả:** ↗️ Hỏi BTC.

## P-003

**Semi-auto tô lẹm sang cành cây và sky, phải sửa tay nhiều**

- **Loại:** Pain point công cụ
- **Mục guideline:** —
- **Người phát hiện:** @NgoDuyNgoc · 20/09/2026
- **Link CVAT:** (bỏ trống)
- **Mô tả:** Mask building (semi-auto) có biên đi vòng qua cành cây và phần trời phía trên, lẹm sang `vegetation` và `sky`.
- **Hướng đang cân nhắc:**
  1. Dùng semi-auto cho vùng lớn, sau đó tô `vegetation` và `sky` đè lên để cắt bớt (đúng thứ tự vùng lớn trước, vật nhỏ sau).
  2. Chuyển sang Mask/Brush cho các khu vực nhiều cành.
- **Kết quả:** ↗️ Hỏi BTC.

## P-004

**Xe ở xa, mờ, không phân biệt được truck/bus (xe thùng trắng)**

- **Loại:** Guideline đã rõ (escalate)
- **Mục guideline:** §4 (car vs truck vs bus), §6
- **Người phát hiện:** @NgoDuyNgoc · 20/09/2026
- **Link CVAT:** (bỏ trống)
- **Mô tả:** Xe trắng ở xa, ảnh nhỏ và mờ, không nhìn ra được là xe tải hay xe buýt.
- **Các cách hiểu:**
  1. Chọn class theo cảm nhận (`truck` do mặt sau phẳng, không thấy cửa sổ).
  2. Không đoán: để trống và tạo Issue `UNCERTAIN_CLASS`.
- **Xử lý tạm trong lúc chờ:** cách 2. Không ép vào `car` cho kín ảnh.
- **Kết quả:** ↗️ Hỏi BTC.

## P-005

**`area/drivable` và `area/alternative`: guideline không nêu định nghĩa**

- **Loại:** Guideline chưa nói tới
- **Mục guideline:** guideline bbox/polyline (chưa ghi số mục), nói "theo định nghĩa mentor chốt"
- **Người phát hiện:** @VuTruongDuy (job 1492, G06_B061), @NguyenMinhTu (job 1493), @PhamNguyenTuan (job 1491) · tuần 01
- **Link CVAT:** (chưa có link; ảnh G06_B061)
- **Mô tả:** Biên giữa hai vùng không rõ ở mép đường, và guideline chỉ dẫn sang định nghĩa của mentor nhưng không có định nghĩa nào.
- **Các cách hiểu:**
  1. `drivable` chỉ là làn xe đang chạy, phần còn lại có thể đi được là `alternative`.
  2. Định nghĩa khác do mentor quyết.
- **Xử lý tạm trong lúc chờ:** chỉ dùng `area/drivable` cho phần đường xe chạy; chỉ vẽ tới phần có biên nhìn thấy rõ, không chắc thì đưa review.
- **Kết quả:** 🔴 Mở. Lead hỏi mentor một lần trong tuần 02 rồi ghi vào decision log.

## P-006

**Polyline vạch kẻ: vạch đôi vẽ một hay hai đường, vẽ theo tim hay theo biên**

- **Loại:** Guideline chưa nói tới
- **Mục guideline:** guideline bbox/polyline (chưa ghi số mục), nói "theo tim/biên theo quy ước của bài"
- **Người phát hiện:** @VuTruongDuy (job 1492, G06_B067) · tuần 01
- **Link CVAT:** (chưa có link; ảnh G06_B067)
- **Mô tả:** Guideline nhắc "quy ước của bài" nhưng không nêu quy ước. Hai vạch đôi nằm gần nhau nên dễ tạo thành hai polyline.
- **Các cách hiểu:**
  1. Vạch đôi vẽ 1 polyline ở giữa (tim), gán class `lane/double white` hoặc `lane/double yellow`.
  2. Mỗi vạch một polyline.
- **Xử lý tạm trong lúc chờ:** cách 1, chỉ vẽ 1 đường ở tim, áp dụng cho cả vạch đơn và vạch đôi.
- **Kết quả:** 🔴 Mở.

## P-007

**Nắp capo và taplo chiếm 30–40% đáy ảnh, không có class "ego vehicle"**

- **Loại:** Guideline chưa nói tới
- **Mục guideline:** §1 (RULE 03), §6
- **Người phát hiện:** @NguyenMinhTu (job 1709) · tuần 01
- **Link CVAT:** (chưa có link; nhiều frame trong job 1709)
- **Mô tả:** Phần xe quay chiếm rất nhiều diện tích đáy ảnh, nhưng 19 class không có class phù hợp.
- **Các cách hiểu:**
  1. Để trống (unlabeled) nếu batch có cấu hình ignore.
  2. Ép vào `car` hoặc `road` (trái RULE 03).
- **Xử lý tạm trong lúc chờ:** cách 1, để trống và tạo Issue hỏi mentor có label ignore không. Không tự tạo class ignore.
- **Kết quả:** 🔴 Mở.

## P-008

**Tuyết phủ mặt đất: road, sidewalk hay terrain**

- **Loại:** Guideline chưa nói tới
- **Mục guideline:** §4 (road vs sidewalk, vegetation vs terrain)
- **Người phát hiện:** @VuTruongDuy (job 1708, S084), @PhamNguyenTuan (job 1491, G06_S027, G06_S030) · tuần 01
- **Link CVAT:** (chưa có link; ảnh S084, G06_S027, G06_S030)
- **Mô tả:** Tuyết phủ làm mất ranh giới giữa mặt đường, vỉa hè và đất tự nhiên.
- **Các cách hiểu:**
  1. Gán theo loại bề mặt nằm dưới lớp tuyết (suy đoán).
  2. Chỉ gán khi thấy rõ biên, phần không rõ để review.
- **Xử lý tạm trong lúc chờ:** cách 2.
- **Kết quả:** 🔴 Mở.

## P-009

**Vật thể ngoài 19 class: biển quảng cáo (Mobil), trạm xăng, thùng phuy, vòi cứu hỏa**

- **Loại:** Guideline chưa nói tới
- **Mục guideline:** §1 (chỉ dùng 19 class), §6
- **Người phát hiện:** @VuTruongDuy (job 1708) · tuần 01
- **Link CVAT:** (bỏ trống)
- **Mô tả:** Các vật thể này không thuộc class nào. Biển quảng cáo không phải `traffic_sign`.
- **Các cách hiểu:**
  1. Để trống và tạo Issue.
  2. Batch có label ignore/unlabeled riêng để đánh dấu.
- **Xử lý tạm trong lúc chờ:** cách 1. Không ép vào class gần giống.
- **Kết quả:** 🔴 Mở. Cần mentor chốt danh sách vật thể này thành decision log vì gặp lặp lại.

## P-010

**Phản chiếu trên kính chắn gió: cấm gán reflection nhưng không nói pixel bên dưới gán class gì**

- **Loại:** Guideline mơ hồ
- **Mục guideline:** §3 (Reflection/Shadow)
- **Người phát hiện:** @VuTruongDuy (job 1708, S081, S098), @PhamNguyenTuan (job 1491) · tuần 01
- **Link CVAT:** (chưa có link; ảnh S081, S098)
- **Mô tả:** Guideline cấm gán reflection thành object thật, nhưng vùng kính có phản chiếu che mất cảnh thật phía sau.
- **Các cách hiểu:**
  1. Gán theo cảnh thật nhìn thấy dưới lớp phản chiếu.
  2. Không gán (để trống) cả vùng có phản chiếu.
- **Xử lý tạm trong lúc chờ:** cách 1; nếu không nhìn ra cảnh thật thì để trống. Không gán vật thể chỉ là ảnh phản chiếu.
- **Kết quả:** 🔴 Mở.

## P-011

**Vegetation vs terrain: luống hoa, bụi thấp, dải phân cách có lề bê tông**

- **Loại:** Guideline mơ hồ
- **Mục guideline:** §4 (vegetation vs terrain)
- **Người phát hiện:** @VuTruongDuy (job 1708, S081) · tuần 01
- **Link CVAT:** (chưa có link; ảnh S081)
- **Mô tả:** Guideline nói vegetation là cây/bụi/lá còn terrain là đất/cỏ/bề mặt tự nhiên thấp, nhưng bụi thấp và luống hoa nằm giữa hai định nghĩa.
- **Các cách hiểu:**
  1. Có thân hoặc tán thì `vegetation`, cỏ và đất thấp thì `terrain`.
  2. Bụi thấp và luống hoa gộp vào `terrain`.
- **Xử lý tạm trong lúc chờ:** cách 1, dùng cùng một quy tắc cho cả batch.
- **Kết quả:** 🔴 Mở.

## P-012

**Ảnh tối, vật nhỏ, đèn lóa: guideline nói đưa review nhưng không cho ngưỡng**

- **Loại:** Guideline mơ hồ
- **Mục guideline:** §3 (Object nhỏ/xa), §6
- **Người phát hiện:** @VuTruongDuy (job 1708, G06_S072, B076), @PhamNguyenTuan (job 1491, job 1707) · tuần 01
- **Link CVAT:** (chưa có link; ảnh G06_S072, B076)
- **Mô tả:** Ảnh ban đêm có đèn chói, vạch mờ, đèn giao thông chỉ vài pixel, xe bật đèn bị lóa. Không rõ mức nào thì đủ bằng chứng để gán.
- **Các cách hiểu:**
  1. Chỉ gán khi zoom lên vẫn thấy vật hoặc các thành phần đặc trưng của vật.
  2. Có ngưỡng định lượng do mentor quy định (kích thước, độ sáng).
- **Xử lý tạm trong lúc chờ:** cách 1. Nếu không đủ bằng chứng thì không gán và không đoán class để lấp ảnh, giữ vùng chưa chắc và đánh dấu review.
- **Kết quả:** 🔴 Mở.

## P-013

**BBox cho vật thể bị che khuất: bao phần nhìn thấy hay suy ra cả vật**

- **Loại:** Guideline chưa nói tới
- **Mục guideline:** guideline bbox (chưa ghi số mục)
- **Người phát hiện:** @VuTruongDuy (B084, B091), @PhamNguyenTuan (job 1491, B046), @VuTruongDuy (job 1492, B073, biển báo bị khuất) · tuần 01
- **Link CVAT:** (chưa có link; ảnh B084, B091, B046, B073)
- **Mô tả:** Không rõ box ôm phần nhìn thấy hay ước lượng cả vật. Với biển báo bị khuất, cũng không rõ có gộp cột biển vào box không.
- **Các cách hiểu:**
  1. Box chỉ bao phần nhìn thấy, bật `occluded`.
  2. Box ôm cả phần ước lượng bị che.
- **Xử lý tạm trong lúc chờ:** cách 1. Với `traffic sign`, không mở rộng box sang cột biển nếu cột không thuộc vật thể cần gán.
- **Kết quả:** 🔴 Mở.

## P-014

**Tên nhãn khác nhau giữa hai guideline và 9 nhãn thừa trong job segmentation**

- **Loại:** Guideline mâu thuẫn
- **Mục guideline:** §2 (danh sách class)
- **Người phát hiện:** @NguyenMinhTu (job 1709, job 1493) · tuần 01
- **Link CVAT:** (bỏ trống)
- **Mô tả:** Cả hai job cùng có 31 nhãn gộp từ hai guideline. Các cặp trùng nghĩa: `pedestrian`/`person`, `traffic light`/`traffic_light`, `traffic sign`/`traffic_sign`. Job segmentation còn thừa 9 nhãn `area/`, `lane/`.
- **Các cách hiểu:**
  1. Mỗi job dùng đúng bộ tên của guideline tương ứng, bỏ qua nhãn thừa.
  2. Chuẩn hóa lại label config của job (ẩn nhãn thừa, thống nhất tên).
- **Xử lý tạm trong lúc chờ:** job 1709 chỉ dùng tên dạng gạch dưới (`person`, `traffic_light`, `traffic_sign`); job 1493 chỉ dùng tên bbox (`pedestrian`, `traffic light`, `traffic sign`).
- **Kết quả:** 🔴 Mở. Hỏi mentor có ẩn nhãn thừa được không.

## P-015

**Mask trong CVAT có thể chồng lên nhau, trong khi Rule 01 cấm**

- **Loại:** Pain point công cụ
- **Mục guideline:** §1 (RULE 01)
- **Người phát hiện:** @VuTruongDuy (job 1708), @PhamNguyenTuan (job 1491) · tuần 01
- **Link CVAT:** (bỏ trống)
- **Mô tả:** CVAT cho phép hai mask cùng chiếm một pixel, nhưng RULE 01 quy định mỗi pixel chỉ thuộc một class.
- **Hướng đang cân nhắc:**
  1. Vẽ vùng lớn trước (road, sky, building), rồi vật thể nhỏ. Dùng Lock/Hide theo label để khỏi sửa nhầm.
  2. Dùng layer của CVAT để đặt mask nào nằm trên, mask nào nằm dưới, đúng thứ tự phía trước và phía sau trong ảnh.
- **Kết quả:** 🔴 Mở. Cần kiểm tra xem export của CVAT có giải quyết chồng lấn theo thứ tự layer hay không.

## P-016

**Khoảng trời nhìn xuyên qua kẽ lá: vẽ sky hay để vegetation phủ**

- **Loại:** Guideline mơ hồ
- **Mục guideline:** §1 (RULE 03), §3
- **Người phát hiện:** @VuTruongDuy (job 1708, G06_S066) · tuần 01
- **Link CVAT:** (chưa có link; ảnh G06_S066)
- **Mô tả:** Tán lá có nhiều khoảng nhỏ nhìn xuyên qua thấy bầu trời, không thể vẽ riêng từng khoảng.
- **Các cách hiểu:**
  1. Không cố gán các vùng không đủ bằng chứng, đưa vào review (theo RULE 03).
  2. Vẽ `vegetation` đè lên cả phần đó khi hai lớp chồng nhau.
- **Xử lý tạm trong lúc chờ:** không còn cần chờ. Theo yêu cầu của mentor thì dùng cách 2.
- **Kết quả:** ✅ Mentor đã yêu cầu cách 2. Chưa có QĐ trong `so-quyet-dinh.md`, cần ghi lại để mọi nhóm áp dụng giống nhau.

---


Nhớ thêm một dòng vào bảng **Danh sách** ở đầu file.
