# BÀI LÀM – THI THỬ HACKATHON 01

- **Mã đề:** Thi thử
- **Họ tên:** 
- **Lớp:** 
- **Link repository:** 
- **Hệ điều hành (Windows/macOS):** 

## 4.2. Thao tác máy tính cơ bản bằng CLI

### Các lệnh đã chạy

```shell
get-location :  Đường dẫn tuyệt đối
get-childitem -force : Liệt kê nội dung kể cả file ẩn
move-item -Path .\nhap_hang.txt -Destination .\docs\
move-item -Path .\logo_van_phong_pham.png  -Destination .\media\
Copy-Item -Path .\media\logo_van_phong_pham.png -Destination .\backup\
rm temp_131.tmp
set-location .\logs
get-childItem -force
cd..
```

### Kết quả liệt kê toàn bộ dự án (Windows: Get-ChildItem -Recurse -Force; macOS: ls -aR)

```text
Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----        10/23/2026   9:01 AM                backup
d-----        10/23/2026   9:04 AM                data
d-----        10/23/2026   9:01 AM                docs
d-----        10/23/2026   9:05 AM                logs
d-----        10/23/2026   9:01 AM                media
-a----        10/23/2026   9:14 AM           2231 bai_lam.md
-a----        10/23/2026   9:02 AM              0 logo_van_phong_pham.png
-a----        10/23/2026   9:03 AM              0 nhap_hang.txt
-a----        10/23/2026   9:11 AM              0 tem_131.tmp


    Directory: C:\Users\admin\Desktop\van-phong-pham-website\data


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----        10/23/2026   9:03 AM              0 don_ban__thang_10.xlsx


    Directory: C:\Users\admin\Desktop\van-phong-pham-website\logs


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----        10/23/2026   9:04 AM              0 shop.log

```

## 4.3. Lọc log thủ công

### Lệnh đã chạy

```shell
Get-Content .\logs\shop.log | Select-String "ERROR" | Set-Content .\logs\daily_report.txt

```

### 2 dòng lỗi đầu tiên trong daily_report.txt

```text
Get-Content .\logs\daily_report.txt -Head 2

2025-10-28 08:24:28 [ERROR] Thanh toan bi tu choi
2025-10-28 08:30:28 [ERROR] Thanh toan bi tu choi
```

## 4.4. Thao tác với tài liệu Markdown (README.md)

> README.md được chấm trực tiếp trên file `README.md` ở gốc dự án. Đánh dấu `[x]` vào các mục đã làm để tự kiểm tra.

- [x] Heading 1: tên dự án
- [x] Mô tả ngắn có cả **in đậm** và *in nghiêng*
- [x] Bảng `Thư mục | Nội dung`, ít nhất 3 dòng dữ liệu
- [x] Code block chứa lệnh PowerShell/Terminal liệt kê nội dung dự án
- [x] Task list ít nhất 2 công việc, có ít nhất 1 mục đã hoàn thành
- [x] Blockquote nhắc không upload `.env`

## 4.5. Chạy script auto_report (.ps1 hoặc .sh)

### Lệnh chạy (Windows: nếu dùng Phụ lục 2 thì ghi cả 2 lệnh)

```shell
# Script: auto_report.ps1
# Tac gia: Pham Quang Vinh
# Ngay tao: 23/10/2026

Write-Host "Dang loc log..."

"=== BAO CAO LOI ===" > logs/auto_report.txt
Get-Content logs/shop.log | Select-String "ERROR" >> logs/auto_report.txt

Write-Host "Hoan thanh!"

```

### Nội dung file logs/auto_report.txt

```text
=== BAO CAO LOI ===

2025-10-28 08:24:28 [ERROR] Thanh toan bi tu choi
2025-10-28 08:30:28 [ERROR] Thanh toan bi tu choi
2025-10-28 08:33:28 [ERROR] Ket noi kho du lieu that bai
2025-10-28 08:39:28 [ERROR] Ket noi kho du lieu that bai
2025-10-28 08:42:28 [ERROR] Ket noi kho du lieu that bai
2025-10-28 09:12:28 [ERROR] Thanh toan bi tu choi


```

## 4.6. Đếm số dòng lỗi

### Lệnh

```shell
(Get-Content .\logs\shop.log | Select-String "ERROR").Count

```

### Kết quả đếm (Windows: giá trị Count; macOS: con số in ra)

```text
6

```

## 4.7. Báo cáo tổng hợp

### Các lệnh đã chạy

```shell
"=== TONG HOP LOG ===" > .\logs\tong_hop.txt
Get-Content .\logs\shop.log | Select-String "WARNING" >> .\logs\tong_hop.txt
(Get-Content .\logs\shop.log | Select-String "ERROR").Count >> .\logs\tong_hop.txt
Get-Content .\logs\tong_hop.txt

```

### Nội dung file logs/tong_hop.txt

```text
=== TONG HOP LOG ===

2025-10-28 08:51:28 [WARNING] Thoi gian tai trang cham
2025-10-28 08:54:28 [WARNING] Anh san pham dung luong lon
2025-10-28 08:57:28 [WARNING] Thoi gian tai trang cham


```

## 4.8. Excel

> Phần Excel được chấm trực tiếp trên file `data/don_ban_thang_10.xlsx`, không cần ghi vào đây.
