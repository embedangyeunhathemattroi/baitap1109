# BÀI LÀM – (ĐỀ LUYỆN TẬP SỐ 02)

- **Mã đề:** 02
- **Họ tên:**Phạm Ngọc Linh
- **Lớp:**K26CNTT3
- **Link repository:**
- **Hệ điều hành (Windows/macOS):**Windows

## 4.2. Thao tác máy tính cơ bản bằng CLI

### Các lệnh đã chạy

```shell
ls -Force
mv .\bien_ban_ban_giao.txt .\docs\
mkdir backup
cp .\data\ban_ve_thang_11.xlsx .\backup\
rm -LiteralPath .\cache_991.tmp
cd .\logs
ls -Force
cd ..
Get-ChildItem -Recurse -Force


```

### Kết quả liệt kê toàn bộ dự án (Windows: Get-ChildItem -Recurse -Force; macOS: ls -aR)

```text

    Directory: C:\Users\TRONG TIN\Downloads\Luyen_Tap_11_9\starter-kit\rap-phim-website


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----         11/9/2026   8:09 PM                backup
d-----         11/9/2026   7:48 PM                data
d-----         11/9/2026   8:09 PM                docs
d-----         11/9/2026   7:47 PM                evidence
d-----         11/9/2026   7:48 PM                logs
d-----         11/9/2026   3:38 PM                web
-a----         11/9/2026   3:38 PM             82 .env
-a----         11/9/2026   8:11 PM           2828 bai_lam.md


    Directory: C:\Users\TRONG TIN\Downloads\Luyen_Tap_11_9\starter-kit\rap-phim-website\backup


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/9/2026   3:38 PM           5693 ban_ve_thang_11.xlsx


    Directory: C:\Users\TRONG TIN\Downloads\Luyen_Tap_11_9\starter-kit\rap-phim-website\data


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/9/2026   3:38 PM           5693 ban_ve_thang_11.xlsx


    Directory: C:\Users\TRONG TIN\Downloads\Luyen_Tap_11_9\starter-kit\rap-phim-website\docs


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/9/2026   3:38 PM            172 bien_ban_ban_giao.txt


    Directory: C:\Users\TRONG TIN\Downloads\Luyen_Tap_11_9\starter-kit\rap-phim-website\logs


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/9/2026   3:38 PM            893 server.log


    Directory: C:\Users\TRONG TIN\Downloads\Luyen_Tap_11_9\starter-kit\rap-phim-website\web


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----         11/9/2026   3:38 PM                images
-a----         11/9/2026   3:38 PM            618 app.js
-a----         11/9/2026   3:38 PM            545 index.html
-a----         11/9/2026   3:38 PM            460 style.css


    Directory: C:\Users\TRONG
    TIN\Downloads\Luyen_Tap_11_9\starter-kit\rap-phim-website\web\images


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/9/2026   3:38 PM            342 logo-cinebox.png


```

## 4.3. Lọc log truy cập website

### a) Lệnh lọc các dòng ERROR

```shell
Get-Content .\logs\server.log | Select-String "ERROR" > .\logs\loi_error.txt
Get-Content .\logs\loi_error.txt -TotalCount 2

```

### 2 dòng đầu tiên trong logs/loi_error.txt

```text
2026-11-01 09:25:40 ERROR POST /api/mua-ve

```

### b) Lệnh đếm số dòng WARNING và kết quả

```shell
Get-Content .\logs\server.log | Select-String "WARNING" | Measure-Object

```

```text

Count    : 5
Average  :
Sum      :
Maximum  :
Minimum  :
Property :
```

## 4.4. Chạy script tong_hop (.ps1 hoặc .sh)

### Lệnh chạy (Windows: nếu dùng Phụ lục 2 thì ghi cả 2 lệnh)

```shell
.\tong_hop.ps1

```

### Nội dung file logs/tong_hop.txt

```text
Dang tao bao cao...
Hoan thanh!

```

## 4.5. README.md và bảo vệ thông tin bí mật

> README.md, .gitignore và .env.example được chấm trực tiếp trên file ở gốc dự án. Đánh dấu `[x]` vào các mục đã làm để tự kiểm tra.

- [ ] README.md: Heading 1, mô tả có **in đậm** và _in nghiêng_, bảng, code block, task list, blockquote
- [ ] .gitignore có dòng `.env` (tên file đúng, không có đuôi .txt)
- [ ] .env.example có đủ tên biến, giá trị để trống (tên file đúng, không có đuôi .txt)

## 4.6. Kiểm tra trang web bằng DevTools (F12) và báo cáo lỗi

### Bảng lỗi

| STT | Tab DevTools phát hiện lỗi | Tên file hoặc thông báo lỗi | Cách khắc phục |
| --- | -------------------------- | --------------------------- | -------------- |
| 1   | Network                        |  images/logo.png — net::ERR_FILE_NOT_FOUND                           |   Trong web/index.html dòng 10, đổi thành src="images/logo-cinebox.png". Lưu rồi nhấn Ctrl + Shift + R.             |
| 2   |     Console                       |   hienThiBangGia is not defined tại app.js:18                          |  doi thanh hienThiBangGiaVe ở dóng số 19 file app.js              |

> Ảnh chụp màn hình lưu trong thư mục `evidence/` (network.png, console.png).

### Báo cáo lỗi gửi trưởng nhóm

- **Context:**Mở web/index.html bằng Chrome trên Windows, bật Console và tải lại trang.
- **Expected:**Bảng giá hiển thị dữ liệu vé.
- **Actual:**Bảng chỉ hiện tiêu đề cột.
- **Log:**ncaught ReferenceError: hienThiBangGia is not defined

### Câu tìm kiếm Google

```text
site:stackoverflow.com "Uncaught ReferenceError"

```

## 4.7. Excel

> Phần Excel được chấm trực tiếp trên file `data/ban_ve_thang_11.xlsx`, không cần ghi vào đây.
