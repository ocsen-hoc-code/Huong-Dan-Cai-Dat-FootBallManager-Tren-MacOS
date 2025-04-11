```markdown
# 🐳 Hướng dẫn Cài đặt SQL Server Docker trên macOS

---

## 📋 Yêu cầu hệ thống

- macOS 11 (Big Sur) trở lên  
- CPU hỗ trợ ảo hóa (Apple Silicon M1/M2/M3 hoặc Intel)  
- Dung lượng trống: ~1GB  
- Tài khoản có quyền Admin  

---

## 🔽 Bước 1: Tải Docker Desktop

👉 Tải tại: [https://www.docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop)

![Docker Desktop Image](Images/Docker-Desktop.png)

**Chọn bản phù hợp với chip máy của bạn:**
- Intel chip: dành cho Mac đời cũ  
- Apple chip (M1/M2/M3): dành cho Mac mới hơn

![Docker Desktop OS Version Image](Images/OS-Version.png)

---

## 🧱 Bước 2: Cài đặt Docker

1. Mở file `.dmg` vừa tải về  
2. Kéo biểu tượng Docker vào thư mục **Applications**  
   ![Install Docker Image](Images/Install-Docker.png)

3. Mở ứng dụng **Docker Desktop**  
4. Làm theo hướng dẫn và cấp quyền khi được yêu cầu  
   ![Permission Image](Images/Permission.png)

5. Chờ biểu tượng 🐳 hiện trên thanh menu → Docker đã sẵn sàng

---

## ✅ Bước 3: Kiểm tra cài đặt

Mở **Terminal**, chạy lệnh sau:

```bash
docker -v
```

**Ví dụ kết quả:**
```
Docker version 28.0.1, build 068a01e
```

---

## ⚙️ Docker Compose

Docker Desktop đã bao gồm sẵn Docker Compose. Kiểm tra bằng lệnh:

```bash
docker-compose --version
```

**Ví dụ kết quả:**
```
Docker Compose version 2.32.4
```

---

## 🐘 Bước 4: Chạy và Dừng Docker SQL Server trên macOS

Di chuyển vào thư mục `Huong-Dan-Cai-Dat-FootBallManager-Tren-MacOS`, rồi chạy:

**Chạy Docker Compose:**
```bash
docker-compose up -d
```

**Dừng Docker Compose:**
```bash
docker-compose down
```

---

## 💻 Bước 5: Dùng Azure Data Studio để kết nối tới Docker SQL Server

👉 Tải Azure Data Studio:  
[https://learn.microsoft.com/en-us/azure-data-studio/download-azure-data-studio](https://learn.microsoft.com/en-us/azure-data-studio/download-azure-data-studio?view=sql-server-ver16&tabs=win-install%2Cwin-user-install%2Credhat-install%2Cwindows-uninstall%2Credhat-uninstall)

**Chọn đúng phiên bản cho chip máy:**
- Intel chip: dành cho Mac đời cũ  
- Apple chip (M1/M2/M3): dành cho Mac mới hơn  

---

### 🔌 Kết nối đến SQL Server

- Mở Azure Data Studio  
- Chọn **New → Connection**  
  ![SQL Create Connection Image](Images/Create-Connection.png)

- Điền thông tin kết nối:
  - **Server**: `127.0.0.1`  
  - **User**: `sa`  
  - **Password**: `admin@123`  
  - **Trust server certificate**: `True`  
  ![SQL Connection Setting Image](Images/Connection-Setting.png)

---

### 🗃️ Tạo database

- Chọn **Databases** → Chuột phải → **New Database (Preview)**  
  ![Create Database1 Image](Images/Create-Database1.png)

- Điền:
  - **Name**: `officialleague`  
  - **Owner**: `sa`  
  ![Create Database2 Image](Images/Create-Database2.png)

---

### 🧾 Chạy file `official.sql` để thêm dữ liệu

- Chọn database `officialleague` → Nhấp chuột phải → Chọn **New Query**  
  ![New Query Image](Images/New-Query.png)

- Sao chép nội dung từ file `official.sql`, dán vào editor → Nhấn **Run**  
  ![Run Script Image](Images/Run-Script.png)

- Mở phần **Tables** trong database `officialleague` để kiểm tra:  
  ![Tables Image](Images/Tables.png)

---

🎉 **Chúc mừng! Bạn đã cài đặt thành công SQL Server Docker trên macOS và kết nối bằng Azure Data Studio.**
```
