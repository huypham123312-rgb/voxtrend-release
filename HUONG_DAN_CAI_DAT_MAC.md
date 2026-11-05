# VoxTrend cho Mac — hướng dẫn cài

Gói chưa ký bởi Apple, nên macOS chặn ở lần mở đầu. Làm đúng thứ tự dưới đây (một lần).

## 1. Giải nén và mở khoá

1. Nhấp đúp tệp zip → ra thư mục `VoxTrend`. Kéo thư mục vào **thư mục nhà** (`~/VoxTrend`).
   **Đừng để trong Desktop hay Documents**: máy bật iCloud cho hai thư mục này sẽ đồng bộ cả model (vài GB),
   có thể xoá bản trên máy và làm macOS chặn app lại.
2. Mở **Terminal** (Cmd+Space → gõ Terminal), gõ dòng sau rồi **kéo thư mục VoxTrend** thả vào
   cửa sổ Terminal (Terminal tự điền đường dẫn), Enter:

   ```
   xattr -dr com.apple.quarantine
   ```

   (có một dấu cách cuối dòng trước khi thả thư mục). Lệnh này bỏ cờ «tải từ Internet» để macOS
   cho mở tệp trong thư mục. Không cần mật khẩu.

## 2. Mở app — lần đầu app tự cài (~15–30 phút, cần mạng)

Nhấp đúp **`Mo VoxTrend.command`**. Trình cài mở ra → tick phần tùy chọn nếu cần (Paraformer cho phim Trung,
Douyin) → **Bắt đầu cài đặt**. App tự tải FFmpeg, Python riêng (trong thư mục `python`, không đụng Python của máy),
giọng đọc VieNeu, Whisper — **không cần Homebrew, không hỏi mật khẩu**.

Lỗi giữa chừng (mất mạng, ổ đầy): bấm **Thử lại** ở đúng bước đó. Cài sau / cài lại: **Trợ giúp → Cài thêm tính
năng**. Cửa sổ Terminal đi kèm là nhật ký — app lỗi thì chụp màn hình cửa sổ này (nhật ký cũng ở `logs/voxdub.log`).

## Khác bản Windows

- Tách nhạc chạy bằng GPU của chip Apple (nhanh hơn CPU ~2,7 lần); GPU lỗi thì app tự chạy lại bằng CPU.
  Nghe lời (Whisper) và giọng đọc chạy CPU. Muốn tắt GPU: Cài đặt → Nâng cao → Thiết bị xử lý → Chỉ CPU.
- Nếu macOS báo «Apple không thể xác minh…»: bấm Xong (không bấm «Chuyển vào Thùng rác»), chạy lại lệnh `xattr`
  ở bước 1 cho thư mục VoxTrend, rồi mở bằng `Mo VoxTrend.command`.
- Chưa tự cập nhật: có bản mới, dải «↑ Cập nhật» trên tên tài khoản tải gói Mac mới về.
- Cài thêm / cài lại một phần (Paraformer, Douyin…) hoặc khi lỗi: trong app vào **Trợ giúp → Cài thêm tính
  năng** → bấm **Cài** / **Cài lại**. Gửi lỗi: **Trợ giúp → Lưu nhật ký để gửi hỗ trợ**.
- Dữ liệu (`.env`, `models/`, `output/`, các `.venv-*`) nằm trong thư mục VoxTrend — bản mới
  thì chép các mục này sang thư mục mới.
