# Môn: Phát triển ứng dụng với mã nguồn mở-TEE0421
# Lớp: 58KTPM
# Bài tập 02:

# SỬ DỤNG DJANGO ĐỂ TẠO WEB QUẢN LÝ TIỆM CẦM ĐỒ
deadline : 23h59 ngày 09 tháng 5 năm 2026.

**1. TỔ CHỨC CSDL CHO HỆ THỐNG QUẢN LÝ TIỆM CẦM ĐỒ**
<img width="597" height="645" alt="image" src="https://github.com/user-attachments/assets/e4b2c0ad-51c1-4c50-9169-57d874be95b8" />


**2. SỬ DỤNG DOCKER TRÊN UBUNTU ĐỂ:**
- Tạo thư mục chứa dự án:
  <img width="675" height="43" alt="image" src="https://github.com/user-attachments/assets/05d7c65c-0508-4613-a774-edd3c78ea2f6" />
- Thêm các dịch vụ vào trong file docker-compose.yml ( sử dụng sudo nano docker-compose.yml):
a. Mariadb : chứa csdl của hệ thống này
b. Phpmyadmin: để soi được csdl (chỉ để xem, ko cần tạo bảng từ đây, django sẽ làm hết)
    <img width="1445" height="751" alt="image" src="https://github.com/user-attachments/assets/44828080-fa47-43ed-b432-c982e71fe562" />

c. Django: build 1 docker container (dùng Dockerfile): trên nền python, sử dụng django, nhớ mount thư mục để dễ edit, edit dùng: sudo nano ten_file
  - Tạo 1 thư mục riêng cho Django:
    <img width="767" height="22" alt="image" src="https://github.com/user-attachments/assets/12257926-06fb-4bd1-9883-66e72b89db04" />
  - Dùng "sudo nano django_app/requirements.txt" <bash>

sau khi có 3 service này trong file docker-compose.yml :

run nó, cấu hình để Django nhận csdl mariadb (sửa file settings.py), cấu hình user login ban đầu, mô tả các bảng trong models.py, .... (đc phép sử dụng AI để làm) => KQ được trang admin, y/c đăng nhập, vào trang admin: cho phép thêm sửa xoá dữ liệu các bảng. các trường là khoá ngoại chỉ việc chọn text (mặc dù là csdl tại trường FK đó lưu ID của PK mà nó tham chiếu : sử dụng phpmyadmin để kiểm chứng)
chú ý kết hợp ssh để chạy lệnh tác động vào django và sudo nano để edit file.
sử dụng template (file html, sử dụng cú pháp jinja2), lấy context từ 1 view home_page, để tạo trang liệt kê các con nợ đến hạn mà chưa trả tiền!
sử dụng cloudflare tunnel để public kết quả lên 1 sub-domain => chụp kết quả
Hướng dẫn:

Tạo thư mục để chứa image tự buid cho django
Vào thư mục đó tạo file tên: Dockerfile (nội dung hỏi AI xem file này cần có nội dung gì, full comment cho từng dòng lệnh trong file này => mục tiêu kép: để hiểu và để hệ thống chạy được)
AI sẽ nói cần thêm file requirements.txt để cài các thư viện cho python (cài qua lệnh pip) => tạo file requirements.txt với nội dung tưng ứng, trong file này cũng comment được => comment xem thư viện nào dùng để làm gì
Sau mỗi lần sửa đỏi có thể phải chạy lệnh dạng : docker compose exec TÊN_SERVICE_DJANGO_CỦA_BẠN python manage.py migrate để tác động vào django (còn nhiều lệnh khác chứ ko luôn như này), để django thay đổi csdl hoặc thay đổi cấu hình.
