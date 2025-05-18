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

## ✅ Bước 6: Cài đặt VMWare để chạy Window 11 trên Mac OS với CPU M1/M2/M3/M4

Truy cập link sau để tải VMWare:
👉 [https://drive.google.com/file/d/1c04Cp7eOti4FhwiP7Slsu1e6JVSGhfWF/view?usp=sharing](https://drive.google.com/file/d/1c04Cp7eOti4FhwiP7Slsu1e6JVSGhfWF/view?usp=sharing)

Truy cập link sau để tải Window 11 ARM:
👉 [https://drive.google.com/file/d/12p-OUDRGajjLio3tCdOY-umm_VRHSHTX/view?usp=sharing](https://drive.google.com/file/d/12p-OUDRGajjLio3tCdOY-umm_VRHSHTX/view?usp=sharing)

- Nhấp 2 lần liên tục vào file VMware-Fusion-13.6.3-24585314_universal.dmg -> Sau đó nhấp 2 lần tiên tục vào biểu tượng VMWare Fusion
![WMWare Fusion Image](VMWare-img/Step1.png)

- Nhấp vào `Install from disc or image`.
![WMWare Fusion Image](VMWare-img/Step2.png)

- Nhấp vào `Use another disc or disc image ...` sẽ hiện một của sổ cho phép tìm kiếm tập tin, hãy chọn đến thư mục chứa tập tin `Windows11_26100.2033_Professional_en-us_arm64.iso` chính là tập tin Window 11 ARM. -> Chọn Ok -> Chọn Continue.
![WMWare Fusion Image](VMWare-img/Step3.png)

- Để mặc định chọn Continue
![WMWare Fusion Image](VMWare-img/Step4.png)

- Đặt mật khẩu cho máy ảo.
![WMWare Fusion Image](VMWare-img/Step5.png)


- Nhấp vào biểu tượng Mỏ Lết
![WMWare Fusion Image](VMWare-img/Step5-2.png)

- Chọn `Processor và Memory`.
![WMWare Fusion Image](VMWare-img/Step6.png)

- Chọn lựa số nhân CPU và RAM cho máy ảo.
![WMWare Fusion Image](VMWare-img/Step7.png)

- Chọn `Hard Disk`.
![WMWare Fusion Image](VMWare-img/Step8.png)

- Chọn kích thước ổ cứng cho máy ảo. -> Chọn Apply.
![WMWare Fusion Image](VMWare-img/Step8.png)

- Nhấp vào biểu tượng Play để chạy máy ảo.
![WMWare Fusion Image](VMWare-img/Run-Virtual-Machine.png)

- Khi màng hình với thông tin `Press any key to boot from CD or DVD` để tiến hành cài đặt Window 11, bạn có thể tham khảo các bước cài đặt trên mạng. Lưu ý phải nhớ mã PIN để cho những lần đăng nhập vào Window.
![WMWare Fusion Image](VMWare-img/Loading.png)

- Chọn kích thước ổ cứng cho máy ảo. -> Chọn Apply.
![WMWare Fusion Image](VMWare-img/Step8.png)

- Sau khi cài xong và đăng nhập vào Window 11 -> Trên phần thực đơn (menu) chính của VMWare Fusion -> Chọn `Virtual Machine` -> Chọn `Install VMWare Tools`.
![WMWare Fusion Image](VMWare-img/Screen1.png)

- Tìm vào thư mục gốc tên là `DVD Driver VMWare Tools` -> Nhấp vào tập tin `setup.exe` -> Tiến hành cài đặt theo mặt định. -> Sau đó restart lại máy ảo để cập nhập thông số màn hình tương thích với phần cứng của máy tính Macbook.
![WMWare Fusion Image](VMWare-img/Screen2.png)