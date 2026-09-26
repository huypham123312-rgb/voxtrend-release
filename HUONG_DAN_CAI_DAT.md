# Hướng dẫn cài đặt VoxTrend

VoxTrend lồng tiếng video tự động sang tiếng Việt: tải video → nhận dạng
giọng nói → dịch → đọc giọng Việt (clone giọng) → ghép lại thành video.

Nhận dạng giọng nói, đọc giọng Việt, Project state và ghép video đều chạy
**trên máy của bạn**. Bước dịch có thể làm thủ công hoặc gọi trực tiếp
Gemini/OpenRouter/DeepSeek bằng API key của chính bạn. Bạn cần cài vài công
cụ trước khi dùng — làm đúng thứ tự dưới đây, mỗi bước chỉ làm **một lần**.

> **Cài tối thiểu để chạy được ngay:** Bước 1 (FFmpeg) + Bước 2 (Python) +
> Bước 3 (giọng đọc VieNeu **và** nhận dạng Whisper). Dịch thủ công không cần API key.

> **Máy cần có:** Windows 10/11 64-bit, card đồ họa NVIDIA (khuyến nghị,
> để chạy nhanh), ~10 GB dung lượng trống, kết nối mạng để tải model.

---

## Bước 1 — Cài FFmpeg (xử lý âm thanh/video)

Mở **PowerShell** (bấm phím Windows, gõ `powershell`, Enter) rồi chạy:

```
winget install Gyan.FFmpeg
```

Xong **đóng PowerShell và mở lại**, gõ `ffmpeg -version` — thấy số phiên
bản là được.

*Không dùng được winget?* Tải bản "release full" tại
<https://www.gyan.dev/ffmpeg/builds/>, giải nén, rồi chép 2 file
`ffmpeg.exe` và `ffprobe.exe` trong thư mục `bin` vào **cùng thư mục với
VoxTrend.exe** — app sẽ tự nhận, không cần chỉnh PATH.

## Bước 2 — Cài Python (để cài giọng đọc VieNeu)

Trong PowerShell:

```
winget install Python.Python.3.12
```

Đóng và mở lại PowerShell, gõ `py --version` — thấy `Python 3.12.x` là được.

> Cần đúng **Python 3.12** (tính năng tải Douyin kiểm tra đúng phiên bản này).

## Bước 3 — Cài giọng đọc VieNeu và nhận dạng Whisper (bắt buộc)

Đúp chuột lần lượt 2 file trong thư mục VoxTrend, mỗi file đợi tới dòng
**XONG** rồi mới đóng cửa sổ:

1. **`Cai dat giong VieNeu.bat`** — giọng đọc tiếng Việt (~300 MB).
2. **`Cai dat Whisper ASR.bat`** — nghe-chép lời video (~500 MB). Thiếu bước
   này thì video có lời không nhận dạng được.

Script tự tạo môi trường riêng (`.venv-vieneu`), tải model (~300 MB) và
chạy thử. Chỉ mất vài phút, **không cần card đồ họa** — đây là bộ giọng
đọc của app với hàng chục giọng nam/nữ.

## Bước 4 — Chọn cách dịch

### Cách A — Khóa Gemini MIỄN PHÍ (khuyên dùng, app tự dịch)

1. Vào <https://aistudio.google.com/apikey>, đăng nhập tài khoản Google.
2. Bấm **Create API key** → copy chuỗi khóa.
3. Mở VoxTrend → trang **Dịch thuật** → nhà cung cấp **Google Gemini** →
   dán khóa → **Lưu**.

- Gói miễn phí đủ cho dùng cá nhân; hết lượt trong ngày thì đợi hôm sau.
- Khóa là của riêng bạn: không gửi cho ai, không dán lên mạng.

### Cách B — Không dùng API: dịch thủ công bằng AI miễn phí trên web

1. Trang **Dịch thuật** → nhà cung cấp **Dịch thủ công** → **Lưu**.
2. Tạo dự án như bình thường. Nghe-chép xong, app **dừng lại** và mở hướng dẫn
   3 bước (file `TRANSLATE_PENDING.txt` trong thư mục dự án):
   - copy file `transcript_original.json`;
   - dán vào ChatGPT / gemini.google.com cùng đoạn "LỜI NHẮN GỬI AI" có sẵn;
   - lưu kết quả thành `transcript_vi.json` đúng thư mục đó.
3. Bấm **"Đã dịch xong, tiếp tục"** → app đọc giọng và xuất video.

- Mất thêm 2–3 phút mỗi video, không tốn phí.
- **"Đọc chữ trên hình"** (video không lời) BẮT BUỘC có khóa Gemini — dùng Cách A.

## Bước 5 — Mở VoxTrend và kiểm tra

1. Đúp chuột **VoxTrend.exe**.
2. Kiểm tra nhanh:
   - Trang **Dự án**: kiểm tra Project đã lưu và có thể Resume.
   - Trang **Giọng đọc AI**: chọn giọng bạn thích, bấm **Nghe thử**.
   - Trang **Dịch thuật**: điền ngữ cảnh video nếu muốn bản dịch bám đúng
     chủ đề và xưng hô của kênh bạn (không bắt buộc).
3. Vào trang **Tạo dự án**, chọn video trên máy hoặc dán link YouTube/Douyin,
   bấm chạy. Nên thử trước một video ngắn 30–60 giây.

Video kết quả nằm trong thư mục `output` cạnh VoxTrend.exe.

## Tùy chọn

- **Máy có card NVIDIA:** đúp chuột **`Cai dat GPU NVIDIA (tuy chon).bat`** (~2,5 GB, một
  lần) — tách nhạc và nghe-chép nhanh hơn nhiều. Máy nóng hoặc card lỗi: **Cài đặt →
  Nâng cao → Thiết bị xử lý → Chỉ CPU**.
- **Tải video Douyin:** đúp chuột **`Cai dat tinh nang Douyin.bat`** (cài
  thư viện + Chromium, ~210 MB, một lần). YouTube và link trực tiếp không
  cần bước này.
- **Nhận dạng tiếng Trung chính xác hơn:** đúp chuột
  **`Cai dat ASR tieng Trung (Paraformer).bat`** (~520 MB, chạy CPU). Video
  tiếng Trung sẽ được nghe-chép bằng Paraformer thay vì Whisper — chính xác
  hơn rõ rệt; ngôn ngữ khác tự dùng Whisper như cũ.
- **Tiêu đề, mô tả và hashtag tự động:** bật/tắt ở trang **Dịch thuật**,
  mục "Nội dung đăng bài"; dùng cùng provider AI đã cấu hình.
- **Giọng đọc riêng:** thu một file WAV 5–10 giây giọng bạn muốn clone
  (rõ, không nhạc nền) + file `.txt` cùng tên chứa đúng nội dung câu nói,
  rồi chọn nó trong tab Cài đặt.
- **Dịch đúng ngữ cảnh hơn:** vào trang **Dịch thuật**, mục **"Ngữ cảnh
  video"** — điền chủ đề, xưng hô và thuật ngữ cố định; bản dịch sẽ bám đúng
  văn phong kênh của bạn.

---

## Xử lý lỗi thường gặp

| Hiện tượng | Cách xử lý |
|---|---|
| `ffmpeg` không nhận sau khi cài | Đóng mở lại PowerShell/app; hoặc chép `ffmpeg.exe`+`ffprobe.exe` vào cạnh `VoxTrend.exe` |
| `py` không nhận | Cài lại Python bằng winget (Bước 2), nhớ mở PowerShell mới |
| Provider dịch báo lỗi mạng/API | Kiểm tra API key, endpoint, quota/rate limit; Project giữ checkpoint để Retry/Resume |
| App báo chưa cài bộ giọng VieNeu | Chạy `Cai dat giong VieNeu.bat` (Bước 3) |
| Chạy chậm, GPU không dùng | Cần card NVIDIA + driver mới (`nvidia-smi` trong PowerShell phải chạy được) |
| Antivirus chặn VoxTrend.exe | Thêm thư mục VoxTrend vào danh sách loại trừ — app không có mã độc, exe đóng gói bằng PyInstaller hay bị nhận nhầm |

## Cấu trúc thư mục sau khi cài đủ

```
VoxTrend/
├── VoxTrend.exe             ← mở app tại đây
├── _internal/             ← thư viện của app (không đụng vào)
├── Cai dat giong VieNeu.bat            ← Bước 3 (giọng đọc, bắt buộc)
├── Cai dat Whisper ASR.bat             ← nhận dạng giọng nói, chạy sidecar
├── Cai dat ASR tieng Trung (Paraformer).bat ← tùy chọn, nghe tiếng Trung chuẩn hơn
├── Cai dat tinh nang Douyin.bat        ← tùy chọn, tải video Douyin
├── scripts/
├── libs/                  ← thư viện Douyin (sau khi cài, nếu dùng)
├── models/vieneu/         ← model VieNeu (sau Bước 3)
├── models/paraformer-zh/  ← model Paraformer (nếu cài)
├── .venv-vieneu/          ← môi trường VieNeu (sau Bước 3)
├── .venv-asr/             ← môi trường Paraformer (nếu cài)
├── pw-browsers/           ← Chromium (nếu dùng Douyin)
├── .env                   ← app tự tạo khi bạn Lưu cài đặt
└── output/                ← video kết quả
```
