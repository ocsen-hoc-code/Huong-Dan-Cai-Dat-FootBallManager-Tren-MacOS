# 🐳 Hướng dẫn Cài đặt SQL Server Docker trên macOS

## 📋 Yêu cầu hệ thống
- macOS 11 (Big Sur) trở lên
- CPU hỗ trợ ảo hóa (Apple Silicon M1/M2/M3 hoặc Intel)
- Dung lượng trống: ~1GB
- Tài khoản có quyền Admin

## 🔽 Bước 1: Tải Docker Desktop

Truy cập link sau để tải Docker Desktop:  
👉 [https://www.docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop)

![Docker Desktop Image](Images/Docker-Desktop.png)

Chọn bản phù hợp với chip máy của bạn:
- **Intel chip**: dành cho Mac đời cũ
- **Apple chip (M1/M2/M3)**: dành cho Mac mới hơn

![Docker Desktop OS Version Image](Images/OS-Version.png)

## 🧱 Bước 2: Cài đặt Docker

1. Mở file `.dmg` vừa tải về  
2. Kéo biểu tượng Docker vào thư mục **Applications**

![Install Docker Image](Images/Install-Docker.png)

3. Mở ứng dụng **Docker Desktop**  
4. Làm theo hướng dẫn và cấp quyền khi được yêu cầu

![Permission Image](Images/Permission.png)

5. Chờ biểu tượng 🐳 hiện trên thanh menu → Docker đã sẵn sàng

## ✅ Bước 3: Kiểm tra cài đặt

Mở **Terminal**, chạy lệnh sau:

```bash
docker -v
```

Kết quả ví dụ:
```
Docker version 28.0.1, build 068a01e
```

## ⚙️ Docker Compose

Docker Desktop đã bao gồm sẵn Docker Compose. Kiểm tra bằng lệnh:

```bash
docker-compose --version
```

Kết quả ví dụ:
```
Docker Compose version 2.32.4
```

## ✅ Bước 4: Chạy và dừng Docker SQL Server trên MacOS

Mở **Terminal**, ở thư mục **Huong-Dan-Cai-Dat-FootBallManager-Tren-MacOS** chạy lệnh sau:

Chạy Docker Compose:
```bash
docker-compose up -d
```

Dừng Docker Compose:
```bash
docker-compose down
```

## ✅ Bước 5: Chạy Azure Data Studio trên MacOS để kết nối đến Docker SQL Server

Truy cập link sau để tải Azure Data Studio:  
👉 [https://learn.microsoft.com/en-us/azure-data-studio/download-azure-data-studio](https://learn.microsoft.com/en-us/azure-data-studio/download-azure-data-studio?view=sql-server-ver16&tabs=win-install%2Cwin-user-install%2Credhat-install%2Cwindows-uninstall%2Credhat-uninstall)

Chọn bản phù hợp với chip máy của bạn:
- **Intel chip**: dành cho Mac đời cũ
- **Apple chip (M1/M2/M3)**: dành cho Mac mới hơn

Chạy Azure Data Studio và thực hiện các bước sau để tiến hành tạo database.

- Chọn New -> Connection để tạo connection tới Docker SQL Server.  
![SQL Create Connection Image](Images/Create-Connection.png)

- Điền thông tin giống trong hình:  
  + Server: ***127.0.0.1***  
  + User: ***sa***  
  + Password: ***admin@123***  
  + Trust server certificate: ***True***  
![SQL Connection Setting Image](Images/Connection-Setting.png)

- Tạo database:  
  + Chọn Database -> Nhấp chuột phải -> New Database (Preview)  
![Create Database1 Image](Images/Create-Database1.png)

  + Name: ***officialleague***  
  + Owner: ***sa***  
![Create Database2 Image](Images/Create-Database2.png)

- Chạy `official.sql` để thêm dữ liệu vào ***officialleague***

  + Chọn database ***officialleague*** -> nhấp phải chuột -> chọn New Query  
![New Query Image](Images/New-Query.png)

  + Sao chép nội dung của file `official.sql` rồi dán vào editor của New Query -> nhấn nút Run  
![Run Script Image](Images/Run-Script.png)

  + Mở Tables của database ***officialleague*** để xem các bảng giống như hình  
![Tables Image](Images/Tables.png)

## ✅ Bước 6: Cài đặt VMWare để chạy Windows 11 trên macOS với CPU M1/M2/M3/M4

### 🔗 Tải về phần mềm cần thiết

- Tải **VMWare Fusion** tại:  
👉 [VMWare Fusion Download](https://drive.google.com/file/d/1c04Cp7eOti4FhwiP7Slsu1e6JVSGhfWF/view?usp=sharing)

- Tải **Windows 11 ARM** tại:  
👉 [Windows 11 ARM Download](https://drive.google.com/file/d/12p-OUDRGajjLio3tCdOY-umm_VRHSHTX/view?usp=sharing)

---

### 🔧 Các bước cài đặt

1. Nhấp đúp vào file `VMware-Fusion-13.6.3-24585314_universal.dmg`  
   → Sau đó tiếp tục nhấp đúp vào biểu tượng **VMWare Fusion**  
   ![VMWare Step 1](VMWare-img/Step1.png)

2. Chọn **Install from disc or image**  
   ![VMWare Step 2](VMWare-img/Step2.png)

3. Chọn **Use another disc or disc image...**  
   → Dẫn đến file `Windows11_26100.2033_Professional_en-us_arm64.iso`  
   → Chọn **OK** → Chọn **Continue**  
   ![VMWare Step 3](VMWare-img/Step3.png)

4. Giữ mặc định → Chọn **Continue**  
   ![VMWare Step 4](VMWare-img/Step4.png)

5. Đặt **mật khẩu** cho máy ảo  
   ![VMWare Step 5](VMWare-img/Step5.png)

---

### ⚙️ Cấu hình máy ảo

6. Nhấp vào biểu tượng **mỏ lết** để cấu hình  
   ![VMWare Step 5-2](VMWare-img/Step5-2.png)

7. Chọn **Processor và Memory**  
   ![VMWare Step 6](VMWare-img/Step6.png)

8. Chọn số **nhân CPU** và **RAM** mong muốn  
   ![VMWare Step 7](VMWare-img/Step7.png)

9. Chọn **Hard Disk** để cấu hình ổ cứng  
   ![VMWare Step 8](VMWare-img/Step8.png)

10. Thiết lập dung lượng ổ cứng → Chọn **Apply**  
    ![VMWare Step 9](VMWare-img/Step9.png)

---

### ▶️ Khởi chạy và hoàn tất

11. Nhấp vào biểu tượng **Play** để chạy máy ảo  
    ![VMWare Run VM](VMWare-img/Run-Virtual-Machine.png)

12. Khi xuất hiện dòng `Press any key to boot from CD or DVD`  
    → Nhấn phím bất kỳ để bắt đầu cài đặt Windows 11.  
    → Lưu ý: Hãy **nhớ mã PIN** để đăng nhập sau này.  
    ![VMWare Loading](VMWare-img/Loading.png)

13. Sau khi cài đặt và đăng nhập Windows 11:  
    → Trên menu chính của VMWare Fusion, chọn:  
    **Virtual Machine** → **Install VMWare Tools**  
    ![VMWare Screen1](VMWare-img/Screen1.png)

14. Vào thư mục gốc `DVD Driver VMWare Tools`  
    → Nhấp vào `setup.exe` để cài đặt mặc định  
    → **Restart máy ảo** sau khi cài để cập nhật độ phân giải và hỗ trợ phần cứng  
    ![VMWare Screen2](VMWare-img/Screen2.png)
