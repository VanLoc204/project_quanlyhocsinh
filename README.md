# Student Management System (Hệ Thống Quản Lý Học Sinh)

## Giới thiệu dự án (Project Overview)
Hệ Thống Quản Lý Học Sinh là một ứng dụng web được xây dựng trên nền tảng **PHP thuần (Vanilla PHP)** kết hợp với cơ sở dữ liệu **MySQL**, ứng dụng mô hình kiến trúc **MVC (Model - View - Controller)**. Dự án nhằm mục đích số hóa và tối ưu hóa quy trình quản lý học tập tại trường học, cung cấp các tính năng chuyên biệt cho từng nhóm người dùng: Ban Giám Hiệu, Quản trị viên, Giáo viên và Học sinh.

## Công nghệ sử dụng (Tech Stack)
- **Backend:** PHP (Native), PDO/MySQLi
- **Frontend:** HTML5, CSS3, JavaScript
- **Cơ sở dữ liệu:** MySQL (Database: `quan_ly_hoc_sinh_cleannew`)
- **Kiến trúc phần mềm:** MVC (Model - View - Controller)

## Phân quyền & Tính năng chính (Features & Roles)

Hệ thống cung cấp 4 vai trò (Roles) với các chức năng tương ứng thông qua bộ định tuyến (Router) tập trung tại `index.php`:

### 1. Admin (Quản trị viên - Role 1)
- **Quản lý dữ liệu cốt lõi:** Năm học, Danh mục môn học, Danh mục lớp học.
- **Quản lý người dùng:** Tài khoản hệ thống, Hồ sơ giáo viên, Hồ sơ học sinh.
- **Nghiệp vụ:** Phân lớp học sinh, Sắp xếp thời khóa biểu.

### 2. BGH - Ban Giám Hiệu (Role 2)
- Theo dõi tình hình toàn trường.
- Xem thống kê, báo cáo học tập và công tác giảng dạy.
- Phối hợp cùng Admin phân công giáo viên chủ nhiệm và giảng dạy.

### 3. Giáo viên (Teacher - Role 3)
- **Giáo viên bộ môn:** Nhập điểm, xem lịch dạy, xem danh sách lớp đang dạy, xem bảng điểm chi tiết, quản lý hồ sơ cá nhân.
- **Giáo viên chủ nhiệm:** Duyệt đơn xin nghỉ phép của học sinh, tổng kết điểm, xem thông tin lớp chủ nhiệm.

### 4. Học sinh (Student - Role 4)
- Xem thời khóa biểu cá nhân.
- Tra cứu điểm số các môn học.
- Tạo và gửi đơn xin nghỉ phép trực tuyến.
- Quản lý hồ sơ cá nhân.

## Cấu trúc thư mục (Folder Structure)
Dự án áp dụng chặt chẽ mô hình kiến trúc MVC thông qua một Front Controller:

```text
Project_quan_ly_hoc_sinh/
├── app/
│   ├── Controllers/   # Nơi chứa các class điều khiển logic (VD: cDangNhap.php, cHocSinh.php,...)
│   ├── Models/        # Tương tác trực tiếp với cơ sở dữ liệu (Database CRUD)
│   └── Views/         # Chứa giao diện hiển thị cho người dùng (HTML/CSS/JS)
├── config/            # Chứa các file cấu hình hệ thống như ketnoi.php (Database connection)
├── public/            # Thư mục chứa các tệp tĩnh (CSS, uploads, vendor)
├── db/                # Chứa file schema cơ sở dữ liệu (schema.sql - nếu có)
├── index.php          # Front Controller: Điểm vào duy nhất, nhận Request và điều hướng (Router act)
└── README.md          # Tài liệu dự án hiện tại
```

## Hướng dẫn cài đặt (Installation)

1. **Clone repository:**
   ```bash
   git clone <repository_url>
   ```
2. **Cài đặt môi trường:**
   - Cài đặt phần mềm tạo Web Server cục bộ như XAMPP, WAMP, hoặc Laragon.
   - Di chuyển thư mục dự án vào thư mục gốc của Web Server (vd: `htdocs` đối với XAMPP).
3. **Cấu hình Database:**
   - Truy cập trang quản trị CSDL (thường là `http://localhost/phpmyadmin`).
   - Tạo một cơ sở dữ liệu mới với tên `quan_ly_hoc_sinh_cleannew` (Encoding: utf8mb4_general_ci).
   - Import file cơ sở dữ liệu (`.sql`) đính kèm trong source code vào database vừa tạo.
4. **Cấu hình kết nối:**
   - Mở file `config/ketnoi.php`.
   - Đảm bảo các thông tin `$local`, `$user`, `$pass`, và `$db` khớp với môi trường Localhost của bạn.
5. **Khởi chạy ứng dụng:**
   - Mở trình duyệt và truy cập đường dẫn: `http://localhost/Project_quan_ly_hoc_sinh/index.php`

---
*Dự án này là minh chứng thực tế cho việc áp dụng kiến trúc MVC nguyên bản vào hệ sinh thái PHP nhằm xây dựng một ứng dụng quản lý chuẩn mực với hệ thống phân quyền phức tạp. Phù hợp làm đồ án môn học nâng cao hoặc tài liệu tham khảo dự án thực tế trong Portfolio cá nhân.*