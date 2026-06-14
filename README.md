<p align="center">
  <img src="appfood/assets/img/banner.png" alt="Flashfood Banner" width="100%">
</p>

<h1 align="center">⚡ FLASHFOOD - FASTBITE APP 🍔</h1>

<p align="center">
  <i>Hệ thống đặt món và giao đồ ăn thông minh thời gian thực phát triển bằng Flutter và Node.js Express.</i>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Flutter-3.10.1-blue?style=for-the-badge&logo=flutter" alt="Flutter Badge">
  <img src="https://img.shields.io/badge/Node.js-16%2B-green?style=for-the-badge&logo=node.js" alt="Node.js Badge">
  <img src="https://img.shields.io/badge/PostgreSQL-14%2B-blue?style=for-the-badge&logo=postgresql" alt="PostgreSQL Badge">
  <img src="https://img.shields.io/badge/JWT-Secure-orange?style=for-the-badge&logo=json-web-tokens" alt="JWT Badge">
  <img src="https://img.shields.io/badge/License-ISC-red?style=for-the-badge" alt="License Badge">
</p>

---
---
### 📊 GitHub Analytics
[![GitHub Stats](https://github-readme-stats.vercel.app/api?username=Hungho09&show_icons=true&theme=radical)](https://github.com/Hungho09)

---
## 📖 Tổng quan dự án

**Flashfood (FastBite)** là một hệ thống đặt đồ ăn toàn diện (Full-Stack Food Delivery Application). Dự án kết hợp sức mạnh của **Flutter** (ở phía Client/Admin) giúp mang lại giao diện mượt mà, trực quan với **Node.js Express & PostgreSQL** ở phía Backend nhằm đảm bảo hiệu năng cao, bảo mật chặt chẽ và xử lý giao dịch đáng tin cậy. 

Hệ thống được thiết kế tối ưu cho trải nghiệm người dùng từ bước đăng ký, tìm kiếm món ăn, tính toán khoảng cách thông minh dựa trên GPS thực tế, áp dụng mã giảm giá linh hoạt, cho tới quy trình thanh toán an toàn và quản lý đơn hàng chuyên nghiệp cho quản trị viên.

---

## 1. Tính năng nổi bật (Features)

### 📱 Phía Khách hàng (Customer App)
* **Xác thực an toàn & Đa dạng:** Đăng ký/Đăng nhập tài khoản cá nhân, hỗ trợ xác thực mạng xã hội (Google, Facebook) và xác thực mã OTP điện tử bảo mật (`otp_pin_field`).
* **Định vị GPS thông minh:** Tự động định vị vị trí hiện tại thông qua GPS để tính toán khoảng cách chính xác đến từng nhà hàng (sử dụng OpenStreetMap và thuật toán Haversine), từ đó sắp xếp danh sách nhà hàng gần nhất.
* **Tìm kiếm & Phân loại thông minh:** Duyệt qua các danh mục món ăn trực quan (Burger, Pizza, Cơm tấm, Phở, Tráng miệng...), tìm kiếm nhanh món ăn theo từ khóa.
* **Quản lý Giỏ hàng linh hoạt:** Thêm/sửa/xóa số lượng món ăn trực tiếp. Hệ thống tự động kiểm tra và đảm bảo người dùng chỉ đặt đồ ăn từ cùng một nhà hàng trong mỗi đơn hàng để tối ưu vận chuyển.
* **Ưu đãi & Voucher:** Nhập mã giảm giá và tự động tính toán lại chi phí đơn hàng với các rule thông minh (`FREESHIP`, `GIAM20K`, `MONKEY10`).
* **Thanh toán đa phương thức:** Hỗ trợ thanh toán khi nhận hàng (COD), Ví điện tử (E-Wallet) hoặc chuyển khoản Ngân hàng (Bank).
* **Lịch sử đơn hàng:** Theo dõi trạng thái đơn hàng chi tiết theo thời gian thực.

### 💼 Phía Quản trị viên (Admin Portal)
* **Quản lý Cửa hàng:** Thêm mới, chỉnh sửa thông tin nhà hàng (tên, ảnh, xếp hạng, tọa độ địa lý GPS).
* **Thiết lập Voucher:** Tạo và quản lý trạng thái kích hoạt của các chương trình khuyến mãi.
* **Quản trị Người dùng:** Kích hoạt hoặc vô hiệu hóa tài khoản người dùng trực tiếp để đảm bảo an ninh hệ thống.
* **Giám sát Đơn hàng:** Xem toàn bộ lịch sử giao dịch và thống kê doanh thu tổng quát.

### ⚙️ Phía Hệ thống Backend
* **RESTful API chuẩn chỉnh:** Thiết kế API mạch lạc, phân tách rõ ràng các nhóm chức năng (`auth`, `food`, `admin`).
* **Bảo mật tối đa:** Băm mật khẩu người dùng với `bcrypt` (salt rounds = 10) và quản lý phiên làm việc thông qua JWT (JSON Web Token).
* **Tính toàn vẹn dữ liệu (ACID):** Sử dụng các giao dịch SQL Transactions (`BEGIN` - `COMMIT` - `ROLLBACK`) khi tiến hành thanh toán nhằm đảm bảo không bao giờ xảy ra lỗi mất mát dữ liệu hoặc đơn hàng ảo.

---

## 2. Cấu trúc Dự án (Project Structure)

Dự án được tổ chức cấu trúc thư mục rõ ràng, phân định rạch ròi giữa ứng dụng di động (Frontend Client) và máy chủ dịch vụ (Backend API):

```text
Flashfood-app/
├── appfood/                 # Mã nguồn ứng dụng di động Flutter
│   ├── android/             # Cấu hình xây dựng ứng dụng cho Android
│   ├── ios/                 # Cấu hình xây dựng ứng dụng cho iOS
│   ├── assets/              # Tài nguyên tĩnh của ứng dụng
│   │   ├── font/            # Bộ font chữ hiện đại Satoshi (Regular, Medium, Bold, Black)
│   │   └── img/             # Các tệp hình ảnh, icon và banner minh họa
│   ├── lib/                 # Mã nguồn Dart chính điều khiển ứng dụng
│   │   ├── common/          # Các biến toàn cục, hằng số màu sắc, cấu hình mạng (globs.dart)
│   │   ├── common_widget/   # Các thành phần giao diện tái sử dụng (Buttons, TextFields, v.v.)
│   │   ├── model/           # Khai báo cấu trúc dữ liệu ánh xạ từ database (User, Restaurant, Food)
│   │   └── view/            # Giao diện người dùng phân chia theo các mô-đun chức năng cụ thể
│   └── pubspec.yaml         # Quản lý thư viện phụ thuộc và tài nguyên của Flutter
│
├── backend/                 # Mã nguồn máy chủ RESTful API Node.js Express
│   ├── config/              # Kết nối cơ sở dữ liệu và nạp dữ liệu mẫu (db.js, seed.js)
│   ├── controllers/         # Logic xử lý các luồng nghiệp vụ chính của hệ thống
│   ├── middleware/          # Tầng kiểm soát xác thực người dùng và quyền hạn Admin (JWT, Auth)
│   ├── routes/              # Định tuyến điều phối các yêu cầu URL (Endpoints) từ Client
│   ├── server.js            # Điểm khởi chạy máy chủ Express
│   ├── package.json         # Danh mục thư viện và các script chạy của Node.js
│   └── .env.example         # Định nghĩa các biến môi trường mẫu (Database, Port, JWT Secret)
│
└── README.md                # Tài liệu hướng dẫn sử dụng và thuyết minh dự án
```

---

## 3. 🚀 Hướng dẫn Chạy & Kiểm thử (Setup & Testing)

### 📋 Yêu cầu hệ thống (Prerequisites)
* **Node.js** (Phiên bản v16 trở lên)
* **PostgreSQL** (Phiên bản v14 trở lên)
* **Flutter SDK** (Phiên bản v3.10.1 trở lên) & Dart
* Thiết bị giả lập (**Android Emulator / iOS Simulator**) hoặc máy thật chạy hệ điều hành di động.

---

### 🗄️ Bước 1: Thiết lập Cơ sở dữ liệu PostgreSQL
Khởi chạy PostgreSQL trên máy tính của bạn và tạo một database trống để liên kết với ứng dụng:
```sql
CREATE DATABASE appfood_db;
```

---

### 💻 Bước 2: Thiết lập & Chạy Backend Server
1. Di chuyển vào thư mục backend:
   ```bash
   cd backend
   ```
2. Sao chép tệp cấu hình môi trường mẫu thành tệp chạy chính thức:
   ```bash
   cp .env.example .env
   ```
3. Mở tệp `.env` vừa tạo và chỉnh sửa thông tin cấu hình kết nối database của bạn:
   ```env
   PORT=5050
   DB_USER=postgres
   DB_HOST=127.0.0.1
   DB_NAME=appfood_db
   DB_PASSWORD=YOUR_POSTGRES_PASSWORD_HERE
   DB_PORT=5432
   JWT_SECRET=YOUR_SUPER_SECRET_KEY_HERE
   ```
4. Cài đặt các thư viện cần thiết:
   ```bash
   npm install
   ```
5. Khởi chạy máy chủ:
   ```bash
   npm start
   ```
   > [!NOTE]
   > Ngay khi máy chủ chạy lần đầu tiên, hệ thống sẽ tự động gọi hàm khởi tạo bảng (`createTables()`) trong [db.js](file:///Users/hohung/Downloads/Flashfood-app/backend/config/db.js) để dựng cấu trúc bảng và tự động chèn dữ liệu chạy thử (Seed Data) như tài khoản Demo, cửa hàng, món ăn mẫu...

6. Kiểm tra trạng thái máy chủ bằng cách mở trình duyệt hoặc dùng cURL:
   ```bash
   curl -s http://127.0.0.1:5050/api/health
   ```
   Kỳ vọng trả về: `{"ok":true,"service":"appfood-api"}`.

---

### 📱 Bước 3: Cấu hình & Khởi chạy Ứng dụng Flutter
1. Di chuyển vào thư mục appfood:
   ```bash
   cd ../appfood
   ```
2. Cài đặt các gói thư viện Flutter:
   ```bash
   flutter pub get
   ```
3. Cấu hình IP máy chủ API trong tệp [globs.dart](file:///Users/hohung/Downloads/Flashfood-app/appfood/lib/common/globs.dart):
   * **iOS Simulator:** Kết nối thẳng qua địa chỉ IP Loopback `http://127.0.0.1:5050`.
   * **Android Emulator:** Sử dụng địa chỉ IP Gateway mặc định của Google `http://10.0.2.2:5050` để kết nối ra máy chủ host bên ngoài.
   * **Thiết bị máy thật:** Chạy ứng dụng kèm tham số truyền IP máy tính qua lệnh:
     ```bash
     flutter run --dart-define=API_HOST=<IP_MÁY_TÍNH_CỦA_BẠN>
     ```
4. Khởi chạy dự án trên thiết bị kiểm thử:
   ```bash
   flutter run
   ```

---

### 📑 Hướng dẫn Kiểm thử (Testing)
* **Kiểm thử API:** Nhập tài khoản Demo có sẵn (đã được tạo tự động bởi seed):
  * **Tài khoản người dùng (User):** `user@example.com` / Mật khẩu: `123456`
  * **Tài khoản quản trị viên (Admin):** `admin@example.com` / Mật khẩu: `admin123`
* **Kiểm thử Unit Test trong Flutter:**
  ```bash
  flutter test
  ```

---

## 4. 📑 Các khái niệm khoa học chủ chốt (Key Concepts)

### 📐 1. Thuật toán Haversine (Haversine Formula)
Để giải quyết bài toán tính khoảng cách địa lý giữa thiết bị của người dùng và các nhà hàng trên mặt cầu Trái Đất (không phẳng hoàn toàn), hệ thống áp dụng công thức lượng giác toán học **Haversine**:

$$\operatorname{haversin}\left(\frac{d}{R}\right) = \sin^2\left(\frac{\Delta \varphi}{2}\right) + \cos(\varphi_1)\cos(\varphi_2)\sin^2\left(\frac{\Delta \lambda}{2}\right)$$

Trong đó:
* $d$ là khoảng cách cần tính giữa hai điểm.
* $R$ là bán kính trung bình của Trái Đất ($6371\text{ km}$).
* $\varphi_1, \varphi_2$ là vĩ độ (latitude) của hai địa điểm (tính bằng radian).
* $\lambda_1, \lambda_2$ là kinh độ (longitude) của hai địa điểm (tính bằng radian).

Hàm tính toán được triển khai trực tiếp bằng Javascript tại [foodController.js](file:///Users/hohung/Downloads/Flashfood-app/backend/controllers/foodController.js#L5-L18) nhằm tối ưu tốc độ phản hồi danh sách nhà hàng sắp xếp theo cự ly gần nhất của người dùng.

### 🌐 2. Kiến trúc Client-Server & RESTful API
Hệ thống tuân thủ mô hình phân lớp kiến trúc Client-Server:
* **Frontend (Client):** Xử lý luồng giao diện trực quan, thu nhận tương tác người dùng, quản lý State cục bộ và gửi yêu cầu bất đồng bộ (Asynchronous HTTP Requests) qua thư viện `http` của Dart.
* **Backend (Server):** Máy chủ phi trạng thái (Stateless Server) tiếp nhận các yêu cầu HTTP Methods chuẩn (`GET`, `POST`, `PUT`, `DELETE`), thực hiện logic nghiệp vụ và tương tác với cơ sở dữ liệu PostgreSQL.

### 🔒 3. Bảo mật & Mã hóa dữ liệu (Security & Cryptography)
* **Băm mật khẩu (Password Hashing):** Sử dụng thuật toán băm khóa đối xứng **BCrypt** để biến đổi mật khẩu thành chuỗi hash ngẫu nhiên dài 60 ký tự trước khi lưu vào PostgreSQL. Thuật toán tích hợp cơ chế Salt ngẫu nhiên giúp ngăn chặn hoàn toàn tấn công bảng Rainbow Table.
* **Xác thực phi trạng thái (Token-based Authentication):** JWT được tạo bằng chữ ký bí mật phía server (`JWT_SECRET`). Sau khi khách hàng đăng nhập thành công, token này được gửi về lưu tại bộ nhớ cục bộ `shared_preferences` của thiết bị và đính kèm vào tiêu đề HTTP Header (`Authorization: Bearer <Token>`) trong mọi yêu cầu cần xác thực quyền kế tiếp.

### 🤝 4. Giao dịch toàn vẹn dữ liệu (PostgreSQL Transactions)
Khi khách hàng gửi yêu cầu thanh toán (`checkout`), hệ thống cần thực hiện nhiều hành động thay đổi dữ liệu liên quan:
1. Tạo một đơn hàng mới trong bảng `orders`.
2. Duyệt qua danh sách món trong giỏ hàng và chèn các dòng dữ liệu chi tiết vào bảng `order_items`.

Để tránh tình trạng mất đồng bộ dữ liệu (ví dụ: tạo thành công đơn hàng nhưng không lưu được chi tiết món do mất kết nối giữa chừng), toàn bộ quá trình được đóng gói trong một **Transaction (ACID)**. Lệnh `BEGIN` được gọi đầu tiên, nếu có bất kỳ lỗi nào xuất hiện trong các câu truy vấn con, lệnh `ROLLBACK` sẽ được kích hoạt để khôi phục cơ sở dữ liệu về trạng thái nguyên bản, đảm bảo dữ liệu không bao giờ bị sai lệch.

---

## 5. ✍️ Tác giả & Tham khảo (Authors & References)

### ✍️ Nhóm phát triển dự án
* **Đại diện tác giả:** [Hungho09](https://github.com/Hungho09)
* **Nhiệm vụ:** Phát triển ứng dụng Flutter Full-Stack và thiết kế cơ sở dữ liệu.

### 📑 Tài liệu tham khảo & Công nghệ sử dụng
* **Tài liệu Flutter chính thức:** [Flutter Dev Docs](https://docs.flutter.dev/)
* **Xây dựng API với Express:** [ExpressJS Guide](https://expressjs.com/)
* **Hệ quản trị CSDL PostgreSQL:** [PostgreSQL Documentation](https://www.postgresql.org/docs/)
* **Công thức toán học tính khoảng cách địa lý:** [Haversine Formula - Wikipedia](https://en.wikipedia.org/wiki/Haversine_formula)
* **Phông chữ Satoshi hiện đại:** [Fontshare.com](https://www.fontshare.com/)
