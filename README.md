# ORDER BY TURA V5 — Website đặt hộ Taobao (Frontend Demo)

Bản demo tương tác gồm **website khách hàng** và **admin quản lý đơn hàng**, chưa có backend, thanh toán thật hay kết nối Taobao API.

## Chạy website

- Giải nén tất cả file vào cùng một thư mục.
- Mở `index.html` trên Chrome/Edge/Safari hoặc chạy `python -m http.server 8000` rồi truy cập `http://localhost:8000`.
- Không cần cài Node.js, không cần build, không cần máy chủ dữ liệu.

## Responsive V5 & giá quy đổi

- `responsive-v5.css` là lớp responsive áp dụng cho **toàn bộ web**: landing, giỏ hàng, đơn hàng, chi tiết, hướng dẫn, form, popup, dashboard, danh sách đơn, khách hàng, cấu hình admin.
- Layout tự thích ứng ở các nhóm 320–479, 480–767, 768–1099, 1100–1599, 1600–2399 và từ 2400px. Trên desktop rộng, `.shell` tăng từ 1200px lên 1760px (tới 2000px trên ultrawide).
- Admin trên điện thoại hiển thị danh sách đơn dạng thẻ, 4 menu luôn có thể bấm, không bắt buộc kéo ngang bảng.
- **Mỗi giá sản phẩm theo ¥** đi kèm số tiền **≈ VND**, sử dụng `settings.rate` (mặc định 3.700đ/¥), cập nhật khi Admin thay tỷ giá. Hiển thị tại sản phẩm mẫu, popup nhập sản phẩm, giỏ hàng, chi tiết đơn của khách và Admin.
- Trong popup thêm sản phẩm, số tiền VND thay đổi ngay khi chỉnh giá ¥ hoặc số lượng.
- Giá đổi ≈ VND chỉ là **tiền hàng ước tính**, không phải giá cuối cùng; phí vận chuyển và dịch vụ được tính riêng trong giỏ hàng, báo giá cuối do Admin xác nhận.

## Nhận diện thương hiệu

- **Logo ngang**: `logo.svg`, dùng ở header, thanh điều hướng admin và footer.
- **Mascot chủ đạo**: `tura-mascot.webp` (logo mascot) và `tura-mascot-logo.png` (PNG trong suốt), gấu trúc áo/mũ cam TURA **đẩy xe hàng Taobao**. Dùng cho banner, trang đăng nhập, màn hình giới thiệu.
- **Nền banner dài**: `tura-market-scene.svg` là hình minh họa độc lập không chứa chữ/nút giả; tiêu đề, ô dán link, nút đặt hàng là phần tử HTML thật.
- **Logo mascot V4**: không có nền đen/hào quang, vùng mắt nháy được chỉnh thành lông trắng, bóng đổ nhẹ do CSS.
- **Favicon**: `tura-mascot-icon.png`, cùng mẫu gấu trúc Tura.
- Xem `BRAND-GUIDE.md` để giữ đúng nhân vật trong các hình minh họa, sticker và hoạt ảnh về sau.

## Flow khách hàng và admin (mô phỏng)

1. Trang chủ: dán link Taobao/Tmall/1688 hoặc chọn một trong ba sản phẩm mẫu.
2. Nhập thông tin sản phẩm, phân loại, số lượng, thêm vào giỏ.
3. Nhập địa chỉ demo, xem chi phí ước tính, gửi yêu cầu mua hộ.
4. Vào **Quản trị** hoặc `#admin`. Đăng nhập demo bằng `admin` / `tura2026`.
5. Admin mở đơn mới, bấm **Bắt đầu kiểm tra** rồi sửa các khoản phí và **Gửi báo giá**.
6. Khách vào **Đơn hàng**, mở đơn để **Đồng ý báo giá**, bấm **Tôi đã chuyển khoản (demo)**. **Không chuyển tiền thật.**
7. Admin xác nhận thanh toán mô phỏng, sau đó cập nhật các trạng thái mua hàng, vận chuyển Trung Quốc, về Việt Nam, giao và hoàn tất.
8. Khách xem lại lịch sử cập nhật ở chi tiết đơn.

Mọi thay đổi lưu bằng `localStorage`. Trình duyệt sẽ giữ dữ liệu khi tải lại; tab khác cùng trình duyệt/nguồn trang có thể cập nhật thông qua `storage` event. **Không đồng bộ giữa các thiết bị**, không có tài khoản khách hàng hay bảo mật thực tế.

## Link Facebook / Instagram

Mục hỗ trợ trong landing page hiển thị hai kênh:
- **Chưa thiết lập**: nút hiển thị **Sắp cập nhật**; nhấp sẽ nhận thông báo, không điều hướng tới trang giả.
- **Sau khi có kênh chính thức**: Admin → **Cấu hình demo** → **Liên hệ & mạng xã hội**. Dán địa chỉ HTTPS thuộc `facebook.com`, `fb.com`, `fb.me`, `instagram.com` rồi nhấn **Lưu kênh hỗ trợ**. Trang chủ sẽ lập tức có liên kết mở trong tab mới.

Tất cả liên kết chỉ lưu trong trình duyệt demo hiện tại. Không có username social hoặc số hotline giả định.

## Phạm vi và an toàn

- Không có dữ liệu sản phẩm Taobao thật, API kiểm giá, tài khoản khách thật, giao nhận hay thông báo qua mạng.
- Thanh toán chỉ được mô phỏng bằng trạng thái, hoàn toàn không xử lý tiền.
- Đăng nhập admin demo **không an toàn để triển khai thật**; không nhập thông tin riêng tư thật.
- Phí, tỷ giá và đơn hàng mẫu chỉ là ví dụ.
- Website trình diễn frontend, không phải dịch vụ nhận đơn thực.

## Kiểm thử

V5 đã kiểm tra trên Chromium tại 12 viewport (320, 375, 390, 480, 768, 820, 1024, 1280, 1440, 1920, 2048, 2560px): tổng cộng **96 kiểm tra bố cục** qua 8 màn hình chính, không phát hiện tràn ngang. Kiểm tra thêm trang chi tiết đơn và modal ở 7 độ rộng không thấy tràn ngang. Kiểm tra thao tác xem sản phẩm mẫu → quy đổi VND → sửa số ¥ → thêm vào giỏ → Admin đổi tỷ giá → quy đổi trang chủ được cập nhật, không có lỗi JavaScript trong kịch bản này.

### Kết quả tham chiếu

- `v5-home-2048.png`: desktop rộng.
- `v5-home-390.png`: điện thoại.
- `v5-admin-2048.png` và `v5-admin-390.png`: Admin trên hai loại màn hình.
- `tura-v5-responsive-review.gif`: slideshow ảnh chụp giao diện mới để duyệt thiết kế, không phải bản ghi thao tác người dùng.



Đã test qua trình duyệt headless Chromium với các màn hình desktop, tablet, mobile (không tràn ngang). Đã thực hiện flow end-to-end từ gửi yêu cầu tới **Hoàn tất**, gồm Admin gửi báo giá, khách đồng ý, cập nhật thanh toán và các mốc vận chuyển; không có lỗi JavaScript trong luồng đã chạy. GIF `tura-v4-flow-review.gif` có 10 cảnh từ ảnh chụp màn hình trình duyệt. Chưa test tích hợp hệ thống thật vì chưa có backend.
