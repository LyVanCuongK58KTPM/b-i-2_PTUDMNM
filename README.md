# Môn: Phát triển ứng dụng với mã nguồn mở-TEE0421
# Lớp: 58KTPM
# Bài tập 02:

# SỬ DỤNG DJANGO ĐỂ TẠO WEB QUẢN LÝ TIỆM CẦM ĐỒ
deadline : 23h59 ngày 09 tháng 5 năm 2026.
Ngày làm: 07/05/2026

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
  - Dùng "sudo nano django_app/requirements.txt" để edit file và thêm các thư viện cần thiết
    <img width="1470" height="236" alt="image" src="https://github.com/user-attachments/assets/757e194f-2546-48ce-ad63-483eb2772741" />

  - Tạo và edit DockerFile thêm các công cụ cần thiết để Django kết tối tới Mariadb:
    <img width="1477" height="613" alt="image" src="https://github.com/user-attachments/assets/aa80428d-0d2c-458b-a88f-f08e4e134f3b" />

  - Cấu hình build django trong docker-compose.yml và mout thư mục:
    <img width="1465" height="754" alt="image" src="https://github.com/user-attachments/assets/1f8fbfa7-aa5f-4772-b3cd-2d209fddcc27" />

d. Chạy docker compose và cấu hình file setting.py để Django nhận csdl từ mariadb:
  - dùng lệnh để Django tự sinh file ra thư mục đã mount:
    <img width="1440" height="191" alt="image" src="https://github.com/user-attachments/assets/cf441b06-104c-49d3-b378-8430bcef7460" />
 - Cấu hình file setting.
<img width="1477" height="752" alt="image" src="https://github.com/user-attachments/assets/a1621dfb-3f27-4037-9574-cf489ac48f47" />
- Mô tả các bảng trong model.py
  <img width="1467" height="756" alt="image" src="https://github.com/user-attachments/assets/59cde42d-f38d-494d-b260-c3aa4d3eb160" />
- Cấu hình trang admin:
  <img width="1472" height="752" alt="image" src="https://github.com/user-attachments/assets/fdccc0ad-f7bc-4bee-8e89-125f18f912f7" />
- kết hợp ssh để chạy lệnh tác động vào django và sudo nano để edit file:
  <img width="1466" height="301" alt="image" src="https://github.com/user-attachments/assets/3d04eeac-c98e-40d8-bbc3-eaec66a363bf" />

===> KQ được:trang admin, y/c đăng nhập vào trang admin: cho phép thêm sửa xoá dữ liệu các bảng. các trường là khoá ngoại chỉ việc chọn text (mặc dù là csdl tại trường FK đó lưu ID của PK mà nó tham chiếu : sử dụng phpmyadmin để kiểm chứng)
  <img width="1830" height="845" alt="image" src="https://github.com/user-attachments/assets/3b82eace-eca4-400f-9175-d49cebe6fc7d" />
  <img width="1780" height="746" alt="image" src="https://github.com/user-attachments/assets/26c04f42-c070-45fb-b639-17a2bfb3fe06" />
  <img width="1896" height="725" alt="image" src="https://github.com/user-attachments/assets/978c0aea-913e-4379-8757-4b4bf8f834d0" />
  <img width="1518" height="556" alt="image" src="https://github.com/user-attachments/assets/a87d66d0-8a35-42ea-9534-f15810ec3394" />
  <img width="1913" height="816" alt="image" src="https://github.com/user-attachments/assets/53e12708-0cd2-4d06-93e7-7142fdde70a7" />
  <img width="1910" height="861" alt="image" src="https://github.com/user-attachments/assets/29929080-4dd0-408e-80f8-d5b98689cbbe" />


e. Sử dụng template (file html, sử dụng cú pháp jinja2), lấy context từ 1 view home_page, để tạo trang liệt kê các con nợ đến hạn mà chưa trả tiền!
 - Cấu hình file view.py để xử lí logic lấy danh sách các con nợ
   <img width="1917" height="327" alt="image" src="https://github.com/user-attachments/assets/82b3988c-6704-46bc-956d-9280d2f70b77" />

 - Tạo Template HTML (Dùng cú pháp Jinja2):
   <img width="1908" height="1011" alt="image" src="https://github.com/user-attachments/assets/aa021594-4efa-4208-affc-81e3730e0957" />

 - Dùng "sudo nano ~/quanly_camdo/django_app/core/urls.py" Sửa file để trỏ đường dẫn trống '' vào home_page:
   <img width="1919" height="1035" alt="image" src="https://github.com/user-attachments/assets/8d68dacc-eaa1-4ea6-9623-3f1f5b86da4b" />

 - Dùng "sudo nano ~/quanly_camdo/django_app/core/settings.py" Tìm mục TEMPLATES, tại dòng 'DIRS': [], sửa thành:
   <img width="1917" height="1017" alt="image" src="https://github.com/user-attachments/assets/5fa38fce-4f6a-42e9-b110-5c0c4d3deadd" />

- Kết quả ( em đã chỉnh sửa ngôn ngữ và múi giờ sang việt nam để hiển thị rõ ngày tháng năm thay vì tiếng Anh mặc định của Django)
<img width="1507" height="405" alt="image" src="https://github.com/user-attachments/assets/977bc1a9-aaf2-4fe3-b317-3a1784c6dab1" />

<img width="1882" height="630" alt="image" src="https://github.com/user-attachments/assets/86ed85a1-8b3c-46c4-bde5-ca6c76ae3f10" />

  

- Sử dụng cloudflare tunnel để public kết quả lên 1 sub-domain:
<img width="1125" height="2436" alt="image" src="https://github.com/user-attachments/assets/d7f82bd8-b898-4b25-889e-ea56cafb3a78" />
<img width="1125" height="2436" alt="image" src="https://github.com/user-attachments/assets/c484bb99-0111-4a73-866f-e286bbd662d7" />


