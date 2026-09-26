VIETNAM:
--------------------------------------

#Ghydro
Công cụ phân tích tĩnh (static analysis) file game Unity/Android: tự động phát hiện hàm tiền tệ, chữ ký, bảo vệ, chỉ số nhân vật từ `dump.cs` + `libil2cpp.so`. Hỗ trợ 13 nhóm chức năng, chấm điểm heuristic, đa luồng, cache thông minh, xuất báo cáo chi tiết.

## ✨ Tính năng chính
- Tự động trích xuất và phân tích file `dump.cs` + `libil2cpp.so` từ `GhidroZip.zip`.
- Lọc hơn 13 nhóm chức năng: Currency, Signature, Protection, Damage, Health, Mana, Level, Speed, Defense, Item, Skill, Reward, Time.
- Chấm điểm hàm theo nhiều tiêu chí: bytecode ARM64, tham chiếu chuỗi, hằng số, độ phức tạp, số lượng caller, tên hàm...
- Hỗ trợ chế độ **BASIC / FULL / CUSTOM** để chọn nhóm chức năng cần phân tích.
- Tích hợp chức năng V0.4: sắp xếp kết quả phản hồi từ AI (file `v04_AI.txt`) theo điểm số và mức độ ưu tiên.
- Xuất báo cáo chi tiết ra 5 file `.txt`: danh sách ứng viên, top 30 currency, top 30 protection, đánh giá đầy đủ và raw dump.
- Cơ chế cache thông minh giúp tăng tốc độ phân tích cho các lần chạy sau.
- Hỗ trợ đa luồng (multi-threading) giúp xử lý nhanh trên máy nhiều CPU.

## ⚙️ Yêu cầu hệ thống
- Windows 64-bit.
- Không cần cài Python (bản `.exe` đã đóng gói sẵn).
- File đầu vào: `GhidroZip.zip` (chứa `libil2cpp.so` và `dump.cs`) đặt trong thư mục `Downloads`.

## 📥 Tải về
Vào tab **Releases** để tải file `Ghydro.exe` và chạy trực tiếp.

## ⚠️ Lưu ý
- Đây là công cụ hỗ trợ phân tích, không đảm bảo tìm ra 100% hàm cần thiết.
- Nếu Windows Defender cảnh báo, hãy bấm **"More info"** → **"Run anyway"**.


English:
------------------------------
# Ghydro

A static analysis tool for Unity/Android games that automatically detects important functions related to currency, signatures, protection, and character stats from `dump.cs` + `libil2cpp.so`. Supports 13 feature categories, heuristic scoring, multi-threading, smart caching, and detailed report exports.

## ✨ Features
- Automatically extracts and analyzes `dump.cs` + `libil2cpp.so` from `GhidroZip.zip`.
- Filters over 13 categories: Currency, Signature, Protection, Damage, Health, Mana, Level, Speed, Defense, Item, Skill, Reward, Time.
- Scores functions using multiple criteria: ARM64 bytecode, string references, constants, complexity, caller count, function names...
- Supports **BASIC / FULL / CUSTOM** modes to select which categories to analyze.
- Includes V0.4: sorts AI response results (from `v04_AI.txt`) by score and priority.
- Exports detailed reports to 5 `.txt` files: candidates list, top 30 currency, top 30 protection, full evaluations, and raw dump.
- Smart caching system to speed up repeated analysis runs.
- Multi-threading support for faster processing on multi-core CPUs.

## ⚙️ Requirements
- Windows 64-bit.
- No Python installation required (pre-packaged `.exe`).
- Input file: `GhidroZip.zip` (containing `libil2cpp.so` and `dump.cs`) placed in the `Downloads` folder.

## 📥 Download
Go to the **Releases** tab to download `Ghydro.exe` and run it directly.

## ⚠️ Notes
- This is an analysis assistance tool; it does not guarantee finding 100% of the needed functions.
- If Windows Defender warns you, click **"More info"** → **"Run anyway"**.
  ------------------‐-----------
# 📖 Hướng dẫn sử dụng Ghydro

## 📋 Yêu cầu
- Windows 64-bit
- File `GhidroZip.zip` (chứa `libil2cpp.so` và `dump.cs`) đặt trong thư mục `Downloads`
- (Tùy chọn) File `blacklist.json` và `whitelist.json` cùng thư mục với `Ghydro.exe`

## 🚀 Các bước sử dụng

### Bước 1: Chuẩn bị file đầu vào
1. Đặt file `GhidroZip.zip` vào thư mục `Downloads` (`C:\Users\<TênBạn>\Downloads`).
2. File zip phải chứa 2 file:
   - `libil2cpp.so`
   - `dump.cs`

### Bước 2: Chạy tool
1. Tải `Ghydro.exe` từ tab **Releases**.
2. Double-click để chạy.
3. Nếu Windows Defender cảnh báo, bấm **"More info"** → **"Run anyway"**.

### Bước 3: Chọn chế độ phân tích
Tool sẽ hiện menu:
- **BASIC**: Phân tích nhanh 3 nhóm chính (tiền tệ, chữ ký, bảo vệ).
- **FULL**: Phân tích tất cả 13 nhóm (lâu hơn).
- **CUSTOM**: Tự chọn nhóm muốn phân tích.
- **V0.4**: Dùng khi có file `v04_AI.txt` (kết quả từ AI) để sắp xếp.

### Bước 4: Đợi tool chạy
Tool sẽ tự động:
1. Giải nén `GhidroZip.zip`.
2. Phân tích `dump.cs`.
3. Chấm điểm hàm bằng bytecode ARM64.
4. Xuất báo cáo.

### Bước 5: Xem kết quả
Tool xuất 5 file trong thư mục `Downloads`:

| File | Nội dung |
|---|---|
| `v02_bytecode_candidates.txt` | Danh sách ứng viên từ V0.2 |
| `v03_top30_currency.txt` | Top 30 hàm tiền tệ |
| `v03_top30_protection.txt` | Top 30 hàm bảo vệ |
| `v03_full_evaluations.txt` | Đánh giá đầy đủ theo category |
| `all_in_raw_dump.txt` | Raw dump tất cả hàm |

## ⚙️ Cấu hình nâng cao

Tool tự động tìm file `blacklist.json` và `whitelist.json` ở 2 vị trí:
1. Cùng thư mục với `Ghydro.exe`.
2. Trong thư mục `Downloads`.

Nếu không tìm thấy, tool dùng config mặc định (đã tích hợp sẵn trong code,nhưng không tối ưu).

**Muốn tùy chỉnh?**
- Sửa `blacklist.json` để thêm class không muốn phân tích.
- Sửa `whitelist.json` để thêm keyword muốn ưu tiên.

## ⚠️ Lưu ý
- Kết quả có thể khác nhau tùy vào game và phiên bản dump.cs.
- Tool không đảm bảo tìm ra 100% hàm cần thiết.
-Offset khi trong các file được xuất ra 'Không Chính Xác',khuyến nghị nên sao chép tên hàm rồi vào 'dump.cs'để lấy chính xác.
