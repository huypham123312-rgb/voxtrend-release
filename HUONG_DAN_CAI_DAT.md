# Cài VoxTrend (Windows 10/11 64-bit)

## Cài — 3 bước

1. Giải nén zip ra một thư mục cố định, ví dụ `D:\VoxTrend` (đường dẫn có dấu tiếng Việt vẫn chạy được).
2. Đúp chuột **`VoxTrend.exe`**. Windows hiện «Windows protected your PC» → bấm **More info → Run anyway**
   (gói chưa ký số, chỉ hỏi lần đầu).
3. Trình cài mở ra → tick phần tùy chọn nếu cần → **Bắt đầu cài đặt**. App tự cài hết, không phải cài
   Python hay chạy tệp nào bằng tay:

| Phần | Bắt buộc? | Dung lượng |
|---|---|---|
| FFmpeg (ghép hình + tiếng) | có | ~100 MB |
| Python của app (cài riêng trong thư mục `python`, không đụng Python của máy) | có | ~70 MB |
| Giọng đọc VieNeu | có | ~900 MB |
| Nhận dạng Whisper | có | ~500 MB |
| Paraformer — nghe tiếng Trung chuẩn hơn | tùy chọn | ~1,2 GB |
| Tải video Douyin | tùy chọn | ~200 MB |
| Card đồ họa NVIDIA — nhanh hơn nhiều lần (tự tick nếu máy có card) | tùy chọn | ~2,5 GB |

Cần mạng và ~5 GB trống (thêm ~4 GB nếu cài GPU). Mất 15–30 phút tuỳ mạng.

## Khi cài bị lỗi

| Gặp | Làm |
|---|---|
| Mất mạng / tải đứt giữa chừng | Bấm **Thử lại** ở đúng bước đó — phần đã tải được giữ, không tải lại từ đầu |
| Báo «Ổ đĩa … còn … MB» | Dọn ổ chứa thư mục VoxTrend rồi bấm Thử lại |
| Báo «Thư mục VoxTrend nằm quá sâu» | Đóng app, chuyển cả thư mục ra chỗ ngắn (ví dụ D:\VoxTrend), mở lại rồi cài |
| Tắt app / mất điện lúc đang cài | Mở lại app → **Trợ giúp → Cài thêm tính năng** → bấm **Cài** ở dòng còn «chưa cài» |
| Bấm «Bỏ qua» một bước | Cài sau ở **Trợ giúp → Cài thêm tính năng** |
| Phần đã cài nhưng chạy sai | **Trợ giúp → Cài thêm tính năng** → **Cài lại** ở dòng đó |
| Antivirus chặn VoxTrend.exe | Thêm thư mục VoxTrend vào danh sách loại trừ (exe đóng gói PyInstaller hay bị nhận nhầm) |
| Vẫn lỗi | **Trợ giúp → Lưu nhật ký để gửi hỗ trợ** → gửi tệp zip (không chứa khoá API, video) |

Dùng video không cần cài lại gì: thiếu phần nào thì app báo NGAY trước khi chạy, kèm chỗ bấm cài.

## Chọn cách dịch

- **Khóa Gemini miễn phí (khuyên dùng):** <https://aistudio.google.com/apikey> → Create API key → VoxTrend,
  trang **Dịch thuật** → **Google Gemini** → dán khóa → **Lưu**. Khóa là của riêng bạn, không gửi ai.
- **Không dùng khóa:** trang **Dịch thuật** → **Dịch thủ công** → app dừng sau bước nghe, làm theo
  `TRANSLATE_PENDING.txt` trong thư mục dự án (dán cho ChatGPT/Gemini trên web) rồi bấm tiếp tục.

## Chọn Bộ nhận dạng theo loại video

| Loại video | Chọn |
|---|---|
| Chỉ nhạc + chữ, hoặc vlog phụ đề chạy suốt có bài hát nền | **Đọc chữ trên hình** (cần khóa Gemini) |
| Có lời + phụ đề khớp lời (Douyin có sub) | **Nghe + đọc chữ** (cần khóa Gemini) |
| Chỉ có lời tiếng Trung, nghe rõ | **Paraformer** |
| Chỉ có lời tiếng Anh/Hàn/Nhật/Thái | **Whisper** + chọn đúng Ngôn ngữ gốc |
| Lẫn nhiều thứ tiếng, hoặc phim thoại nhỏ lẫn tiếng động | **Lời nhiều thứ tiếng** (bước nghe lâu ~15 phút/phim dài — xem dòng tiến độ, đừng bấm dừng) |

## Cập nhật

Có bản mới thì app hiện hộp thoại và dải **«↑ Cập nhật v…»** trên tên tài khoản (thanh bên). Bấm là cập
nhật; giọng đọc, model, khoá API, video, dự án giữ nguyên. Dừng Hàng loạt trước khi bấm.

## Thư mục sau khi cài

```
VoxTrend/
├── VoxTrend.exe     ← mở app tại đây
├── _internal/       ← thư viện của app (không đụng vào)
├── scripts/         ← script cài của app (app tự chạy, không cần mở)
├── python/          ← Python riêng của app
├── .venv-*/         ← môi trường giọng đọc / nhận dạng
├── models/          ← model đã tải
├── .env             ← cài đặt + khoá API của bạn (không gửi ai)
└── output/          ← video kết quả
```
