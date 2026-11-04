# VoxTrend cho Mac — hướng dẫn cài

Gói chưa ký bởi Apple, nên macOS chặn ở lần mở đầu. Làm đúng thứ tự dưới đây (một lần).

## 1. Giải nén và mở khoá

1. Nhấp đúp tệp zip → ra thư mục `VoxTrend`. Kéo thư mục ra chỗ cố định (ví dụ thư mục Home).
2. Mở **Terminal** (Cmd+Space → gõ Terminal), gõ dòng sau rồi **kéo thư mục VoxTrend** thả vào
   cửa sổ Terminal (Terminal tự điền đường dẫn), Enter:

   ```
   xattr -dr com.apple.quarantine
   ```

   (có một dấu cách cuối dòng trước khi thả thư mục). Lệnh này bỏ cờ «tải từ Internet» để macOS
   cho mở tệp trong thư mục. Không cần mật khẩu.

## 2. Cài phần đi kèm (~15–30 phút, cần mạng)

Nhấp đúp **`1. Cai dat (chay mot lan).command`**. Script cài Homebrew (nếu chưa có — hỏi mật khẩu
máy Mac), Python 3.12, ffmpeg, giọng đọc VieNeu, Whisper; cuối cùng hỏi có cài Paraformer (tiếng
Trung) + Douyin không.

## 3. Mở app

Nhấp đúp **`2. Mo VoxTrend.command`**. Cửa sổ Terminal đi kèm là nhật ký — app lỗi thì chụp màn
hình cửa sổ này. Nhật ký cũng ghi ở `logs/voxdub.log`.

## Khác bản Windows

- Mac không có CUDA: tách nhạc và nghe lời chạy CPU (chậm hơn máy Windows có card NVIDIA).
- Chưa tự cập nhật: có bản mới, dải «↑ Cập nhật» trên tên tài khoản tải gói Mac mới về.
- Cài thêm / cài lại một phần (Paraformer, Douyin…) hoặc khi lỗi: trong app vào **Trợ giúp → Cài thêm tính
  năng** → bấm **Cài** / **Cài lại**. Gửi lỗi: **Trợ giúp → Lưu nhật ký để gửi hỗ trợ**.
- Dữ liệu (`.env`, `models/`, `output/`, các `.venv-*`) nằm trong thư mục VoxTrend — bản mới
  thì chép các mục này sang thư mục mới.
