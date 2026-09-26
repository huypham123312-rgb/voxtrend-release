# VoxTrend — lồng tiếng video sang tiếng Việt

Ứng dụng Windows: tải video (YouTube, Douyin hoặc file trên máy) → nghe-chép lời →
dịch → đọc giọng Việt → xuất video có phụ đề. Nhận dạng giọng nói và giọng đọc chạy
**ngay trên máy bạn**; bước dịch dùng khóa Gemini của chính bạn hoặc dịch thủ công.

## Tải về

Vào mục **[Releases](../../releases/latest)** → tải `VoxTrend-v4.0.1.zip` (~217 MB).

## Cài nhanh

Máy cần: Windows 10/11 64-bit, ~10 GB trống, có mạng. Card NVIDIA không bắt buộc.

1. Mở PowerShell, cài công cụ (mỗi dòng một lần), xong đóng và mở lại PowerShell:
   ```
   winget install -e --id Python.Python.3.12
   winget install -e --id Gyan.FFmpeg
   ```
2. Giải nén zip → thư mục `VoxTrend\`.
3. Đúp chuột lần lượt, mỗi file **đợi tới dòng XONG** rồi mới đóng:
   - `Cai dat giong VieNeu.bat` — **bắt buộc**
   - `Cai dat Whisper ASR.bat` — **bắt buộc**
   - `Cai dat ASR tieng Trung (Paraformer).bat` — nếu làm video tiếng Trung
   - `Cai dat tinh nang Douyin.bat` — nếu tải video Douyin
   - `Cai dat GPU NVIDIA (tuy chon).bat` — nếu máy có card NVIDIA
4. Mở `VoxTrend.exe`.

Hướng dẫn đầy đủ và xử lý lỗi: [HUONG_DAN_CAI_DAT.md](HUONG_DAN_CAI_DAT.md) (cũng có sẵn trong zip).

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
