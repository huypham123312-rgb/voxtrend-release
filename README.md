# VoxTrend — lồng tiếng video sang tiếng Việt

Ứng dụng Windows (và Mac chip M — thử nghiệm): tải video (YouTube, Douyin hoặc file trên máy) → nghe-chép lời →
dịch → đọc giọng Việt → xuất video có phụ đề. Nhận dạng giọng nói và giọng đọc chạy
**ngay trên máy bạn**; bước dịch dùng khóa Gemini của chính bạn hoặc dịch thủ công.

## Tải về

Vào mục **[Releases](../../releases/latest)** (bản mới nhất: **4.6.3**):

| Máy của bạn | Tải gì |
|---|---|
| **Windows, chưa cài lần nào** | `VoxTrend-v<số bản>.zip` — gói đầy đủ (~217 MB), rồi làm theo **Cài nhanh** bên dưới |
| **Windows, đã cài rồi** | Không cần tải tay: mở app → **Cập nhật ngay** (hoặc dải «↑ Cập nhật» trên tên tài khoản). App tự chọn gói vá nhỏ hoặc gói đầy đủ, giữ nguyên giọng, model, khoá API và dự án |
| **Mac chip M1–M4 (thử nghiệm)** | `VoxTrend-mac-arm64-v<số bản>.zip` → [HUONG_DAN_CAI_DAT_MAC.md](HUONG_DAN_CAI_DAT_MAC.md). Mac Intel chưa hỗ trợ |

Tệp `VoxTrend-patch-…zip` chỉ dành cho app tự cập nhật — **máy mới đừng tải tệp này**.

## Mã kích hoạt (từ bản 4.6)

App cần **mã kích hoạt** dạng `VXT-XXXXX-XXXXX-XXXXX-XXXXX`:

- **Dùng thử 3 ngày** hoặc mua tại [trendiora.com/long-tieng-video](https://trendiora.com/long-tieng-video).
- Mã của bạn nằm ở trang [Hồ sơ](https://trendiora.com/tai-khoan) (và trong email sau khi mua). Mở app → dán mã vào ô
  «Mã kích hoạt».
- Chưa có mã thì các nút xử lý bị khoá; app vẫn mở, **dự án và video đã xuất còn nguyên**.
- Đổi máy: trong app bấm **«Ngừng dùng trên máy này»**, rồi dán mã ở máy mới.

## Cài nhanh (Windows)

Máy cần: Windows 10/11 64-bit, ~5 GB trống (thêm ~4 GB nếu cài card NVIDIA), có mạng. Không cần cài Python hay
FFmpeg trước — app tự cài.

1. Giải nén zip ra **thư mục ngắn**, ví dụ `D:\VoxTrend`.
2. Đúp chuột **`VoxTrend.exe`** → Windows hỏi «Windows protected your PC» → **More info → Run anyway**.
3. Trình cài mở ra → tick phần tùy chọn nếu cần (Paraformer cho phim Trung, Douyin, card NVIDIA) →
   **Bắt đầu cài đặt**. 15–30 phút tuỳ mạng.

Lỗi giữa chừng: bấm **Thử lại** ở đúng bước đó. Cài sau / cài lại: **Trợ giúp → Cài thêm tính năng**.
Gửi lỗi: **Trợ giúp → Lưu nhật ký để gửi hỗ trợ**.

Hướng dẫn đầy đủ và bảng xử lý lỗi: [HUONG_DAN_CAI_DAT.md](HUONG_DAN_CAI_DAT.md) (cũng có sẵn trong zip).

## Không có khóa API?

- **Khóa Gemini miễn phí** (khuyên dùng): <https://aistudio.google.com/apikey> → Create API key →
  trong app vào trang **Dịch thuật**, chọn **Google Gemini**, dán khóa, Lưu. Chỉ cần tài khoản Google.
- **Không dùng API:** trang **Dịch thuật** → **Dịch thủ công**. App dừng sau bước nghe-chép và
  hướng dẫn 3 bước nhờ ChatGPT/Gemini trên web dịch giúp, rồi bấm **"Đã dịch xong, tiếp tục"**.
- Chế độ "Đọc chữ trên hình" (video không lời) bắt buộc có khóa Gemini.

Khóa API là của riêng bạn — không gửi cho người khác, không dán lên mạng.

## Máy yếu

- App tự chọn mức nhận dạng phù hợp máy (máy không card đồ họa dùng mức nhẹ).
- Máy có card NVIDIA nhưng nóng hoặc lỗi: **Cài đặt → Nâng cao → Thiết bị xử lý → Chỉ CPU**.
- Nên thử video ngắn 30–60 giây trước.
