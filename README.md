# AI-DMFT (tên tạm) – bản mô phỏng

Trang web tĩnh minh hoạ quy trình của ứng dụng AI-DMFT trong đề cương:
năm ảnh trong miệng → AI đánh số răng và phân loại → hồ sơ điền sẵn → nha sĩ kiểm tra, sửa → DMFT và nhu cầu điều trị.

**Đây là bản mô phỏng.** Phần "AI" là giả lập (sinh số theo ca mẫu), không có mô hình thật, không dùng cho chẩn đoán.
Dữ liệu chỉ lưu trong trình duyệt của máy đang dùng, không gửi đi đâu.

## Đưa lên GitHub Pages
1. Tạo repository mới (ví dụ `ai-dmft`), để Public.
2. Add file → Upload files → kéo toàn bộ nội dung thư mục này vào, gồm cả hai thư mục `fonts` và `icons` (`index.html`, `manifest.webmanifest`, `sw.js`, `README.md`) → Commit changes.
3. Settings → Pages → Source: *Deploy from a branch* → Branch: `main`, thư mục `/ (root)` → Save.
4. Chờ 1–2 phút, mở `https://<tên-tài-khoản>.github.io/ai-dmft/`.

Khi sửa file và muốn máy đã cài nhận bản mới: đổi `aidmft-sim-v2` trong `sw.js` thành `v3`.

## Cách dùng để trình bày
1. **Thông tin**: nhập mã, tuổi, hai câu hỏi đau/sưng.
2. **Năm ảnh**: chọn ca mô phỏng rồi bấm *Dùng ảnh minh hoạ*, hoặc tải ảnh thật (app kiểm tra thật độ phân giải, độ sáng, độ nét).
3. **AI phân tích**: xem 6 bước xử lý; kéo ngưỡng T để thấy kết quả thay đổi.
4. **Nha sĩ xác nhận**: sơ đồ răng điền sẵn; dấu `?` là răng AI không chắc; bấm răng rồi chọn mã (hoặc phím 0–9) để sửa; app bấm giờ.
5. **Kết quả**: D, M, F, DMFT; nhu cầu điều trị N0/N1/N2/NX; số răng đã sửa; nút *so với khám lâm sàng* minh hoạ cách tính độ nhạy, độ đặc hiệu và hành vi sửa. Tải .json/.csv hoặc in phiếu.

## Phần nào là thật, phần nào giả lập
| Phần | Trạng thái |
|---|---|
| Giao diện, quy tắc mã răng → DMFT, nhu cầu điều trị, bấm giờ, nhật ký sửa, xuất file | Thật, dùng lại được cho ứng dụng nghiên cứu |
| Kiểm tra chất lượng ảnh tải lên | Thật nhưng đơn giản (độ phân giải, độ sáng, độ nét) |
| Đánh số răng, phân loại sâu/trám/vắng, xác suất | **Giả lập** theo ca mẫu |
| "Kết quả khám lâm sàng" để so sánh | **Giả lập** (tình trạng của ca mẫu) |

Khi có mô hình thật: thay hàm `makeCase()`/`aiCodes()` trong `index.html` bằng lời gọi tới máy chủ chạy mô hình (trả về xác suất sâu/trám và răng vắng cho 28 răng).
