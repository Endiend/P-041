# Nhật ký tuần 03 · 28/09 – 04/10/2026


**Lead tuần này:** Nguyễn Minh Tú
**Dữ liệu / task CVAT:**  — W3-CUBOID-G6-T1 —

## Thành viên và phân công

| Thành viên | Vị trí | Phân công tuần này |
|---|---|---|
| Nguyễn Minh Tú (@NguyenMinhTu) — 2A202602217 | Lead | Chia job, chốt edge case, review job 4067–4070 |
| Phạm Nguyên Tuân (@PhamNguyenTuan) — 2A202602091 | Annotator | Job 4067 |
| Vũ Trường Duy (@VuTruongDuy) — 2A202602291 | Annotator | Job 4068 |
| Ngô Duy Ngọc (@NgoDuyNgoc) — 2A202602050 | Annotator | Job 4069 |
| Đinh Công Minh (@DinhCongMinh) — 2A202602135 | Annotator | Job 4070 |



## Công việc

| # | Nội dung công việc | Annotator | Reviewer | Hoàn thành | Ghi chú |
|---|---|---|---|---|---|
| 1 | Job 4067 — Cuboid (annotation) | @PhamNguyenTuan | @NguyenMinhTu | 🟡 đang làm - đã hoàn thành 40% |  |
| 2 | Job 4068 — Cuboid (annotation) | @VuTruongDuy | @NguyenMinhTu | 🟡 đang làm - đã hoàn thành 20% |  |
| 3 | Job 4069 — Cuboid (annotation) | @NgoDuyNgoc | @NguyenMinhTu | 🟡 đang làm - đã hoàn thành 30% |  |
| 4 | Job 4070 — Cuboid (annotation) | @DinhCongMinh | @NguyenMinhTu | 🟡 đang làm - đã hoàn thành 40% |  |



Mức hoàn thành: ✅ xong **và đã qua review** · 🟡 đang làm (ghi %) · ⛔ bị chặn (ghi lý do) · ⬜ chưa bắt đầu

## Tổng kết
- Tổng task W3-CUBOID-G6-T1: 40 ảnh, chia 4 job (10 ảnh/job)
- Đã gán: 13 / 40 ảnh (32.5%)
  - Job 4067 (@PhamNguyenTuan): 4 / 10 ảnh (40%)
  - Job 4068 (@VuTruongDuy): 2 / 10 ảnh (20%)
  - Job 4069 (@NgoDuyNgoc): 3 / 10 ảnh (30%)
  - Job 4070 (@DinhCongMinh): 4 / 10 ảnh (40%)
- Qua review lần đầu: 0 / 40 ảnh (0%), chưa có job nào chuyển sang review
- Còn lại: 27 / 40 ảnh (67.5%)
## Kế hoạch tuần 03

**Mục tiêu:** Gán xong 40/40 ảnh Cuboid, review xong 100% và chuyển task W3-CUBOID-G6-T1 sang completed trước **Chủ nhật 04/10**.

### Việc cần mentor chốt (Lead gom và hỏi một lần trong tuần)
- Mục 4.4 quy định không tạo cuboid khi point cloud không có cơ sở 3D hợp lý. Vì vậy, khi một vật thể thấy được trên camera nhưng không có point (ngoài phạm vi quét của LiDAR hoặc bị vật thể khác che hoàn toàn), nhóm em đang không gán và ghi lại case theo mục 9.
Có trường hợp vật thể bị che hoàn toàn ở một frame nhưng có point rõ ở frame trước hoặc sau. Nhóm em có được dựa vào các frame đó để gán vật thể ở frame bị che không, hay vẫn bỏ qua theo mục 4.4 ạ? shape (mỗi frame độc lập) hay track (theo dõi vật thể qua các frame)?
- Hệ tọa độ của point cloud: lý thuyết đã học dùng hệ ego (x/đỏ hướng đầu xe, y/xanh lá nằm ngang, z/xanh dương hướng lên), nhưng trong job trục x và y đổi chỗ (y hướng về phía trước ego vehicle, x nằm ngang). Guideline không quy định hệ tọa độ. Hệ trục tọa độ các xe gán nhãn sẽ lấy hệ trục nào,lấy theo xe lấy dữ liệu, hay hiện tại hệ trục của xe lấy dữ liệu đang sai và lấy hệ trục như trong buổi học lý thuyết
- Chiều yaw của barrier: barrier có hai đầu đối xứng, guideline (mục 4.3) chỉ quy định trục dài theo chiều kéo dài của rào chắn, chưa quy định chiều cụ thể. Nhóm cần chốt: xuôi theo hướng đi của ego vehicle, ngược lại, hay chiều nào cũng được (lệch 180° không tính lỗi)?

### Quy tắc làm việc chung trong tuần

- Áp dụng thống nhất các cách xử lý tạm ghi trong bảng "Vướng mắc" cho đến khi có QD chính thức. Khi có quyết định, cả nhóm sửa lại các ảnh đã gán theo đúng quyết định đó.
- Tự review toàn ảnh và kiểm tra checklist trước khi chuyển job sang completed.

### Rủi ro

- Nếu mentor chốt chậm, các quyết định tạm thời có thể phải sửa hàng loạt. Nên gửi câu hỏi sớm, đầu tuần.