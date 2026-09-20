# Sổ quyết định

Ghi lại những gì đội đã chốt, và **vì sao**. Ba tuần sau không ai còn nhớ vì sao box lại vẽ
kiểu này — người mới vào đội lại càng không.

**Quyết định đã ghi thì không sửa nội dung.** Đổi ý thì ghi một quyết định mới, và chuyển
trạng thái quyết định cũ thành *Bị thay bởi QĐ-xxx*. Nhờ vậy vẫn truy được vì sao các job
cũ được gán theo cách cũ.

> Nguồn: nhật ký tuần 01 và [problem-backlog.md](problem-backlog.md). Chỉ ghi các ca đã chốt; các ca còn 🔴 Mở hoặc ↗️ Hỏi BTC trong backlog chưa có QĐ.

## Danh sách

| Mã | Quyết định | Ngày | Xuất phát từ | Trạng thái |
|---|---|---|---|---|
| [QĐ-001](#qđ-001) | Cây đứng trước building gán `vegetation`, building chỉ tô phần nhìn thấy | — | [P-001](problem-backlog.md#p-001) | Hiệu lực |
| [QĐ-002](#qđ-002) | Khoảng trời nhìn xuyên qua kẽ lá: vẽ `vegetation` phủ lên, không vẽ `sky` từng khoảng nhỏ | — | [P-016](problem-backlog.md#p-016) | Hiệu lực |

**Trạng thái:** Hiệu lực · Bị thay bởi QĐ-xxx · Huỷ (ghi lý do)

---

## QĐ-001

**Cây đứng trước building gán `vegetation`, building chỉ tô phần nhìn thấy**

- **Ngày:** —
- **Người tham gia:** @NgoDuyNgoc (chốt)
- **Xuất phát từ:** [P-001](problem-backlog.md#p-001)
- **Bối cảnh:** Mask semi-auto của building phủ luôn cả cây (kể cả cây trụi lá) đứng phía trước. Cây chỉ chiếm phần nhỏ so với building nên dễ bị bỏ qua.
- **Các phương án đã cân nhắc:**
  1. *Tô building bao trùm cả cây* — nhanh hơn. Nhưng trái RULE 01 (mỗi pixel một class), quy tắc "Không chồng lấn" (pixel nhìn thấy thuộc vật ở phía trước) và làm sai IoU của `vegetation` vì mIoU tính theo từng class chứ không theo diện tích. Loại.
  2. *Tách riêng: pixel cây là `vegetation`, building chỉ tô phần nhìn thấy* — đúng guideline (§3 Occlusion, §4). **Chọn.**
- **Quyết định:** Pixel của cây, thân và cành nhìn thấy được gán `vegetation`, không gộp vào `building`. Building chỉ tô ở phần thực sự hiện ra trên ảnh. Vùng cành quá mảnh và dày đến mức không tách được thì không ép class, tạo Issue `UNCERTAIN_BOUNDARY`.
- **Việc phải làm theo:**
  - [ ] Rà lại các mask building tạo bằng semi-auto, cắt phần lẹm sang cây (tô `vegetation` đè lên theo thứ tự vùng lớn trước, vật nhỏ sau)
- **Trạng thái:** Hiệu lực

## QĐ-002

**Khoảng trời nhìn xuyên qua kẽ lá: vẽ `vegetation` phủ lên, không vẽ `sky` từng khoảng nhỏ**

- **Ngày:** —
- **Người tham gia:** Mentor (chốt), @NgoDuyNgoc, @VuTruongDuy
- **Xuất phát từ:** [P-016](problem-backlog.md#p-016)
- **Bối cảnh:** Tán lá có rất nhiều khoảng nhỏ nhìn xuyên qua thấy bầu trời (job 1708, G06_S066). Không thể vẽ riêng từng khoảng, và RULE 03 chỉ nói đưa các vùng không chắc đi review chứ không nói cách xử lý riêng cho trường hợp này.
- **Các phương án đã cân nhắc:**
  1. *Không gán các khoảng nhỏ, để trống và đưa review* — đúng tinh thần RULE 03, nhưng làm ảnh cây nào cũng đầy lỗ trống và tốn công review. Loại.
  2. *Vẽ `vegetation` phủ lên cả phần đó* — nhất quán, nhanh, cho phép chồng lớp khi vẽ rồi xử lý bằng thứ tự layer. **Chọn**, theo yêu cầu của mentor.
- **Quyết định:** Với các khoảng trời nhỏ nhìn xuyên qua kẽ lá mà không thể vẽ riêng, vẽ `vegetation` phủ lên phần đó. Khoảng trời lớn, nhìn rõ biên thì vẫn tô `sky` như bình thường.
- **Việc phải làm theo:**
  - [ ] Rà lại các ảnh đã gán theo cách "đưa review" hoặc để trống ở tán lá, kể cả G06_S066 (@VuTruongDuy)
  - [ ] Áp dụng cho các job segmentation còn lại: 1706, 1707, 1709 (@NgoDuyNgoc, @PhamNguyenTuan, @NguyenMinhTu)
  - [ ] Báo cả đội, ghim trong kênh chat của đội
- **Trạng thái:** Hiệu lực

---


