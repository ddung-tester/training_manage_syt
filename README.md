# Hệ thống Quản lý Trung tâm Đào tạo


# Training Management System

## Overview
Training Management System là hệ thống quản lý hoạt động đào tạo cho một trung tâm. Hệ thống hỗ trợ quản lý học viên, giảng viên, khóa học, lớp học, đăng ký và kết quả học tập.  
Dự án được xây dựng với mục tiêu mô phỏng quy trình phân tích nghiệp vụ và thiết kế hệ thống từ góc nhìn Business Analyst.

---

## My Role – Business Analyst (End-to-End)

- Thu thập và phân tích yêu cầu nghiệp vụ.
- Xác định stakeholder và phạm vi hệ thống.
- Phân tích quy trình hiện tại (AS-IS) và đề xuất quy trình cải tiến (TO-BE).
- Xây dựng tài liệu BRD và SRS (bản rút gọn).
- Viết Use Case, User Story và Acceptance Criteria.
- Thiết kế mô hình dữ liệu (ERD) dựa trên nghiệp vụ.
- Xác định business rules và ràng buộc hệ thống.
- Hỗ trợ kiểm thử logic hệ thống bằng SQL.
- Đảm bảo traceability giữa yêu cầu và thiết kế dữ liệu.

---

## Business Scope

Hệ thống bao gồm các module chính:

### 1. User Management
- Quản lý thông tin học viên
- Quản lý thông tin giảng viên
- Phân quyền theo vai trò

### 2. Course & Class Management
- Tạo và quản lý khóa học
- Mở lớp theo kỳ học
- Phân công giảng viên giảng dạy

### 3. Enrollment Management
- Học viên đăng ký lớp học
- Kiểm tra điều kiện đăng ký
- Theo dõi danh sách lớp

### 4. Grade Management
- Giảng viên nhập và cập nhật điểm
- Lưu trữ kết quả học tập
- Hỗ trợ tổng hợp báo cáo

---

## Sample Use Case – Course Registration

**Actor:** Student  

**Main Flow:**
1. Student đăng nhập hệ thống  
2. Xem danh sách lớp đang mở  
3. Chọn lớp cần đăng ký  
4. Hệ thống kiểm tra điều kiện (sĩ số, trùng lịch, điều kiện tiên quyết)  
5. Đăng ký thành công và lưu vào hệ thống  

**Alternative Flow:**
- Nếu lớp đầy → hiển thị thông báo  
- Nếu trùng lịch → không cho đăng ký  

---

## Key Business Rules

- Một học viên không thể đăng ký hai lớp trùng thời gian.
- Mỗi lớp có giới hạn số lượng học viên.
- Chỉ giảng viên được phân công mới có quyền nhập điểm.
- Điểm hợp lệ trong khoảng từ 0 đến 10.
- Học viên phải hoàn thành học phần tiên quyết (nếu có).

---

## Data Model (High-level)

### Core Entities
- Student  
- Instructor  
- Course  
- Class  
- Enrollment  
- Grade  

### Relationship Overview
- Một Course có thể mở nhiều Class.
- Student đăng ký Class thông qua Enrollment.
- Instructor được phân công giảng dạy Class.
- Grade gắn với Enrollment.

Thiết kế dữ liệu đảm bảo:
- Tính toàn vẹn (Primary Key, Foreign Key).
- Giảm dư thừa dữ liệu.
- Chuẩn hóa đến mức BCNF.

---

## Functional Requirements (Summary)

- Admin có thể tạo/sửa/xóa khóa học.
- Học viên có thể đăng ký lớp.
- Giảng viên có thể nhập điểm.
- Hệ thống kiểm tra điều kiện đăng ký tự động.
- Người dùng có thể tra cứu thông tin lớp học.

---

## Non-Functional Requirements

- Thời gian phản hồi < 3 giây.
- Phân quyền rõ ràng theo vai trò.
- Đảm bảo tính nhất quán và toàn vẹn dữ liệu.
- Hệ thống có thể mở rộng thêm module trong tương lai.

---

## Tech Stack

- PostgreSQL  
- SQL  
- pgAdmin  

---

## Learning Outcome

- Hiểu quy trình phân tích yêu cầu trong phát triển phần mềm.
- Thực hành chuyển đổi nghiệp vụ thành mô hình dữ liệu.
- Rèn luyện kỹ năng viết tài liệu BA.
- Làm quen với cách đảm bảo traceability trong dự án.


## Tech Stack
PostgreSQL, SQL, pgAdmin.


Ứng dụng web full-stack quản lý trung tâm đào tạo với React + Vite + Tailwind CSS (Frontend) và Node.js + Express + PostgreSQL (Backend).
## Công nghệ sử dụng

### Frontend
- **React** 18 với **Vite**
- **Tailwind CSS** cho styling
- **React Router** cho routing
- **Axios** cho HTTP requests

### Backend
- **Node.js** với **Express**
- **PostgreSQL** database
- **pg** library để kết nối database
- **CORS** và **dotenv**

## Cấu trúc thư mục

```
qlydaotao/
├── backend/
│   ├── src/
│   │   ├── db.js              # Kết nối PostgreSQL
│   │   ├── server.js          # Express server
│   │   └── routes/            # API routes (CRUD + Reports)
│   ├── package.json
│   └── .env.example
├── frontend/
│   ├── src/
│   │   ├── components/        # Layout, Header, Sidebar, DataTable
│   │   ├── pages/             # CRUD pages và Reports
│   │   ├── App.jsx
│   │   └── main.jsx
│   ├── package.json
│   ├── vite.config.js
│   └── tailwind.config.js
└── database/
    ├── schema.sql             # DDL tạo bảng
    └── seed.sql               # Dữ liệu mẫu
```

3. Tạo file `.env` từ `.env.example` và cập nhật thông tin:
```env
DB_HOST=localhost
DB_PORT=5432
DB_USER=postgres
DB_PASSWORD=your_password_here
DB_NAME=training_center
PORT=5000
```

4. Chạy backend server:
```bash
npm start
```

Server sẽ chạy tại: `http://localhost:5000`

### Bước 3: Cấu hình Frontend

1. Mở terminal mới, di chuyển vào thư mục frontend:
```bash
cd frontend
```

2. Cài đặt dependencies:
```bash
npm install
```

3. Chạy development server:
```bash
npm run dev
```

Frontend sẽ chạy tại: `http://localhost:3000`

## Chức năng chính

### CRUD Operations
- ✅ **Học viên** - Quản lý thông tin học viên (có nhiều số điện thoại)
- ✅ **Giảng viên** - Quản lý giảng viên với chuyên môn
- ✅ **Nhân viên** - Quản lý nhân viên (hỗ trợ quản lý phân cấp)
- ✅ **Chương trình đào tạo** - CRUD chương trình
- ✅ **Môn học** - Quản lý môn học thuộc chương trình
- ✅ **Kỳ học** - Quản lý kỳ học theo năm
- 📋 **Khóa đào tạo** - Kết hợp chương trình + kỳ học
- 📋 **Lớp môn học** - Lớp của từng môn trong khóa
- 📋 **Đăng ký khóa** - Học viên đăng ký khóa đào tạo
- 📋 **Điểm thi** - Quản lý điểm thi (cho phép thi lại)
- 📋 **Phân công giảng dạy** - Phân công giảng viên/trợ giảng
- 📋 **Buổi học** - Quản lý thời gian buổi học
- 📋 **Phòng học** - Quản lý phòng học
- 📋 **Xếp lịch** - Xếp lịch buổi học vào phòng

**Chú thích:**
- ✅ Đã implement CRUD đầy đủ với form
- 📋 Có API backend đầy đủ, frontend dùng stub placeholder (theo pattern tương tự)

### Reports (Báo cáo)
Tất cả report đều có API backend sẵn sàng tại `/api/reports/*`:

1. **Kết quả học tập học viên**
   - Endpoint: `GET /api/reports/student-results`
   - Hiển thị kết quả học tập của học viên trong các môn học đã đạt (điểm cao nhất > 4)

2. **Học viên chưa hoàn thành khóa**
   - Endpoint: `GET /api/reports/incomplete-students?kdt_id={id}`
   - Danh sách HV còn môn chưa đạt (điểm <= 5)

3. **Tính lương giảng viên theo tháng**
   - Endpoint: `GET /api/reports/teacher-payroll?month={M}&year={Y}&rate_ta={rate}`
   - Công thức: TROGIANG = giờ × rate, GIANGVIEN = giờ × rate × 2

4. **Tính lương nhân viên**
   - Endpoint: `GET /api/reports/staff-payroll?luong_ql_moi_hoc_vien={amount}`
   - Lương cứng + lương quản lý CT + phụ cấp quản lý NV

## Nguyên tắc nghiệp vụ quan trọng

1. **KHÔNG cho CRUD trực tiếp bảng User** - Frontend chỉ thao tác qua Học viên/Giảng viên/Nhân viên
2. **Transaction khi thêm/sửa/xóa** người dùng - Backend tự động xử lý bảng User + bảng con + user_sdt
3. **Nhân viên đầu tiên** có thể tự quản lý (quanly_id = user_id)
4. **Database schema** - Chỉ bảng `"User"` viết hoa và dùng dấu ngoặc kép, tất cả bảng khác lowercase

## API Endpoints

### Người dùng
- `GET/POST /api/hocvien` - Danh sách / Thêm học viên
- `GET/PUT/DELETE /api/hocvien/:id` - Chi tiết / Sửa / Xóa
- `GET/POST /api/giangvien` - Danh sách / Thêm giảng viên
- `GET/PUT/DELETE /api/giangvien/:id` - Chi tiết / Sửa / Xóa
- `GET/POST /api/nhanvien` - Danh sách / Thêm nhân viên
- `GET/PUT/DELETE /api/nhanvien/:id` - Chi tiết / Sửa / Xóa

### Chương trình học
- `GET/POST /api/chuongtrinh`
- `GET/PUT/DELETE /api/chuongtrinh/:id`
- `GET/POST /api/monhoc`
- `GET/PUT/DELETE /api/monhoc/:ma`
- `GET/POST /api/kyhoc`
- `GET/PUT/DELETE /api/kyhoc/:id`
- `GET/POST /api/khoadaotao`
- `GET/PUT/DELETE /api/khoadaotao/:id`
- `GET/POST /api/lopmonhoc`
- `GET/PUT/DELETE /api/lopmonhoc/:id`

### Học vụ
- `GET/POST /api/dangkykhoa`
- `PUT/DELETE /api/dangkykhoa/:hv_id/:kdt_id`
- `GET/POST /api/diemthi`
- `PUT/DELETE /api/diemthi/:hv_id/:lopmh_id/:lanthi`
- `GET/POST /api/phancong`
- `GET/PUT/DELETE /api/phancong/:id`

### Lịch học
- `GET/POST /api/buoihoc`
- `GET/PUT/DELETE /api/buoihoc/:id`
- `GET/POST /api/phonghoc`
- `GET/PUT/DELETE /api/phonghoc/:id`
- `GET/POST /api/xeplich`
- `PUT/DELETE /api/xeplich/:buoihoc_id`

### Reports
- `GET /api/reports/student-results?hv_id={id}`
- `GET /api/reports/incomplete-students?kdt_id={id}`
- `GET /api/reports/teacher-payroll?month={M}&year={Y}&rate_ta={rate}`
- `GET /api/reports/staff-payroll?luong_ql_moi_hoc_vien={amount}`

## Giao diện

- **Header**: Thanh tiêu đề màu xanh phía trên
- **Sidebar**: Menu điều hướng bên trái với nhóm chức năng
- **Main Content**: Nội dung chính bên phải
- **DataTable**: Component table với hover effect, action buttons (Sửa/Xóa)
- **Form**: Card trắng với shadow, form validation, nút Lưu/Hủy rõ ràng

