HƯỚNG DẪN TRIỂN KHAI SAVEVID – BẢN NÂNG CẤP GIAO DIỆN BÀI VIẾT
================================================================

1. MỤC ĐÍCH
Bản cập nhật bổ sung hình minh họa, các thẻ liên kết tới bài viết riêng và cải thiện trình bày nội dung. Đây là bản sao thử nghiệm; chưa được triển khai lên website đang hoạt động.

2. CẤU TRÚC GÓI
- index.html: trang chủ SaveVid.
- articles/: các trang hướng dẫn và bài viết.
- assets/: ảnh JPG và SVG dùng trên trang chủ và bài viết.
- robots.txt: chỉ dẫn dành cho công cụ tìm kiếm.
- sitemap.xml: danh sách URL để công cụ tìm kiếm thu thập.
- worker.js: bản Worker đi kèm để tham khảo; không cần triển khai lại khi chỉ cập nhật giao diện.

3. CÁCH ĐƯA LÊN GITHUB PAGES
Bước 1: Sao lưu index.html hiện đang hoạt động và toàn bộ tệp có liên quan.
Bước 2: Giải nén gói ZIP.
Bước 3: Tải index.html, thư mục articles, thư mục assets, robots.txt và sitemap.xml lên thư mục gốc của nhánh/thư mục GitHub Pages đang xuất bản website.
Bước 4: Giữ nguyên tên tệp và cấu trúc thư mục. Không tải riêng index.html mà bỏ qua assets và articles.
Bước 5: Chờ GitHub Pages xuất bản, sau đó mở https://savevid.cloud/ để kiểm tra ảnh, liên kết bài viết và giao diện trên điện thoại.
Bước 6: Kiểm tra Google Search Console và gửi lại https://savevid.cloud/sitemap.xml nếu cần.

4. LƯU Ý KHI XEM THỬ TRÊN MÁY TÍNH
Trang chủ đang dùng đường dẫn bắt đầu bằng dấu /, ví dụ /assets/savevid-guide.jpg và /articles/how-to-download.html. Đây là đường dẫn tính từ gốc tên miền khi website được xuất bản. Khi mở index.html bằng đường dẫn file:///C:/... trên máy tính, trình duyệt có thể không tìm thấy ảnh và bài viết dù các tệp đã có đầy đủ.
Để xem thử đúng hơn, chạy một máy chủ HTTP cục bộ tại thư mục đã giải nén. Ví dụ, nếu đã cài Python, mở Terminal trong thư mục SaveVid_editorial_upgrade và chạy:
    python -m http.server 8000
Sau đó truy cập http://localhost:8000/ bằng trình duyệt.

5. CÁC MỤC CẦN KIỂM TRA
- Ảnh hướng dẫn tải video và bốn ảnh thẻ bài viết hiển thị đầy đủ.
- Mỗi thẻ mở đúng trang nội dung trong thư mục articles.
- Bố cục trên máy tính và điện thoại không tràn lề.
- Nút chuyển đổi VI/EN trên trang chủ vẫn hoạt động.
- Các chức năng tải video cũ không bị thay đổi do cập nhật giao diện.
- Mã Google Analytics và AdSense vẫn được giữ nguyên.

6. CLOUDFLARE WORKER
Không thay thế Worker đang chạy chỉ vì cập nhật bài viết và ảnh. Các chức năng tải Instagram/Douyin và các nền tảng khác cần được kiểm thử thực tế riêng trước khi thay Worker production. Không đưa khóa RapidAPI vào HTML hoặc mã công khai; lưu khóa trong Cloudflare Worker Secrets.

7. LIÊN HỆ
Email công khai: savevid.cloud@gmail.com

8. GIỚI HẠN XÁC MINH
Việc kiểm tra cấu trúc tệp không đồng nghĩa với xác nhận tải video thành công trên API thật hoặc được Google AdSense phê duyệt. Hãy kiểm thử trên môi trường staging trước khi thay mã nguồn chính thức.
