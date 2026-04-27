<div align="center">
  <h1>Dịch Sách bằng LLM</h1>
</div>

Dịch **sách**, **phụ đề**, và **tài liệu** bằng AI - chạy cục bộ hoặc trên đám mây.

**Không giới hạn kích thước.** Xử lý tài liệu có độ dài bất kỳ - từ một trang đến tiểu thuyết dài hàng nghìn trang. Hệ thống phân đoạn thông minh xử lý nội dung không giới hạn trong khi vẫn duy trì ngữ cảnh giữa các đoạn.

**Bảo toàn hoàn hảo.** Tài liệu đầu ra giữ nguyên định dạng như khi nhập vào: định dạng EPUB, kiểu chữ và cấu trúc được giữ nguyên. Mã thời gian SRT vẫn đồng bộ hoàn hảo. Mọi thẻ, mọi dấu thời gian, mọi chi tiết định dạng đều được bảo toàn.

**Tiếp tục bất cứ lúc nào.** Dịch bị gián đoạn? Tiếp tục ngay từ chỗ dừng. Hệ thống checkpoint tự động lưu tiến trình.

Định dạng hỗ trợ: **EPUB**, **SRT**, **DOCX**, **TXT**

<img width="1240" height="1945" alt="image" src="https://github.com/user-attachments/assets/7b9769df-6833-410d-ae38-a5894ca415dd" />

Nhà cung cấp:

<p align="left">
<img src="src/web/static/img/providers/ollama.png" alt="Ollama" height="32">&nbsp;&nbsp;
<img src="src/web/static/img/providers/poe.png" alt="Poe" height="32">&nbsp;&nbsp;
<img src="src/web/static/img/providers/openrouter.png" alt="OpenRouter" height="32">&nbsp;&nbsp;
<img src="src/web/static/img/providers/openai.png" alt="OpenAI" height="32">&nbsp;&nbsp;
<img src="src/web/static/img/providers/mistral.png" alt="Mistral" height="32">&nbsp;&nbsp;
<img src="src/web/static/img/providers/deepseek.png" alt="DeepSeek" height="32">&nbsp;&nbsp;
<img src="src/web/static/img/providers/gemini.png" alt="Gemini" height="32">
</p>

- [**Ollama**](https://ollama.com/download) (cục bộ / đám mây)
- [**Poe**](https://poe.com/api_key) ⭐ Khuyến nghị - Cài đặt dễ dàng, nhiều mô hình AI
- [**OpenRouter**](https://openrouter.ai/keys) (200+ mô hình)
- [**OpenAI**](https://platform.openai.com/api-keys) (**tương thích với LM Studio**)
- [**Mistral**](https://console.mistral.ai/api-keys)
- [**DeepSeek**](https://platform.deepseek.com/api_keys)
- [**Gemini**](https://aistudio.google.com/apikey)

> **[Đánh giá chất lượng dịch thuật](https://github.com/chuong1224/llmgamingtranslate/wiki)** — Tìm mô hình tốt nhất cho ngôn ngữ đích của bạn.

---

## Bắt đầu nhanh

### Tải file thực thi (Không cần Python!)

[![Tải Windows](https://img.shields.io/badge/Tải-Windows-blue?style=for-the-badge&logo=windows)](https://github.com/chuong1224/llmgamingtranslate/releases/latest/download/TranslateBook-Windows.zip)

1. Tải và giải nén file zip
2. Cài đặt [Ollama](https://ollama.com/) (nếu muốn chạy mô hình AI cục bộ; bỏ qua nếu chỉ dùng API đám mây)
3. Chạy `TranslateBook.exe`
4. Mở http://localhost:5000 trên trình duyệt

> **Lưu ý:** Lần chạy đầu tiên sẽ tạo thư mục `TranslateBook_Data` chứa các file cấu hình.

---

### Dành cho người dùng nâng cao - Cài đặt từ mã nguồn

**Yêu cầu:** [Python 3.8+](https://www.python.org/downloads/), [Ollama](https://ollama.com/), [Git](https://git-scm.com/)

```bash
git clone https://github.com/chuong1224/llmgamingtranslate.git
cd llmgamingtranslate
ollama pull qwen3:14b    # Tải mô hình

# Windows
start.bat

# Mac/Linux
chmod +x start.sh && ./start.sh
```

Giao diện web mở tại **http://localhost:5000**

---

## Nhà cung cấp LLM

| Nhà cung cấp | Loại | Cài đặt |
|----------|------|-------|
| **Ollama** | Cục bộ | [ollama.com](https://ollama.com/) |
| **Poe** ⭐ | Đám mây (Khuyến nghị) | [poe.com/api_key](https://poe.com/api_key) |
| **OpenAI-Compatible** | Cục bộ | llama.cpp, LM Studio, vLLM, LocalAI... |
| **OpenRouter** | Đám mây (200+ mô hình) | [openrouter.ai/keys](https://openrouter.ai/keys) |
| **OpenAI** | Đám mây | [platform.openai.com](https://platform.openai.com/api-keys) |
| **Mistral** | Đám mây | [console.mistral.ai](https://console.mistral.ai/api-keys) |
| **DeepSeek** | Đám mây | [platform.deepseek.com](https://platform.deepseek.com/api_keys) |
| **Gemini** | Đám mây | [Google AI Studio](https://makersuite.google.com/app/apikey) |

> **Máy chủ tương thích OpenAI:** Dùng `--provider openai` với endpoint của máy chủ (ví dụ: llama.cpp: `http://localhost:8080/v1/chat/completions`, LM Studio: `http://localhost:1234/v1/chat/completions`)

Xem [docs/PROVIDERS.md](docs/PROVIDERS.md) để biết hướng dẫn cài đặt chi tiết.

---

## Dòng lệnh (CLI)

```bash
# Cơ bản (tự động tạo "book (Vietnamese).epub")
python translate.py -i book.epub -sl English -tl Vietnamese

# Với OpenRouter
python translate.py -i book.txt --provider openrouter \
    --openrouter_api_key YOUR_KEY -m anthropic/claude-sonnet-4 -tl Vietnamese

# Với OpenAI
python translate.py -i book.txt --provider openai \
    --openai_api_key YOUR_KEY -m gpt-4o -tl Vietnamese

# Với Gemini
python translate.py -i book.txt --provider gemini \
    --gemini_api_key YOUR_KEY -m gemini-2.0-flash -tl Vietnamese

# Với máy chủ tương thích OpenAI cục bộ (llama.cpp, LM Studio, vLLM, v.v.)
python translate.py -i book.txt --provider openai \
    --api_endpoint http://localhost:8080/v1/chat/completions -m your-model -tl Vietnamese
```

### Các tùy chọn chính

| Tùy chọn | Mô tả | Mặc định |
|--------|-------------|---------|
| `-i, --input` | File đầu vào | Bắt buộc |
| `-o, --output` | File đầu ra | Tự động: `{tên} ({ngôn ngữ}).{ext}` |
| `-sl, --source_lang` | Ngôn ngữ nguồn | English |
| `-tl, --target_lang` | Ngôn ngữ đích | Chinese |
| `-m, --model` | Tên mô hình | mistral-small:24b |
| `--provider` | ollama/openrouter/openai/gemini | ollama |
| `--text-cleanup` | Làm sạch OCR/ký tự in | tắt |
| `--refine` | Lượt thứ hai để đánh bóng văn học | tắt |
| `--tts` | Tạo âm thanh (Edge-TTS) | tắt |

Xem [docs/CLI.md](docs/CLI.md) để biết tất cả tùy chọn (giọng TTS, tốc độ, định dạng, v.v.).

---

## Cấu hình (.env)

Sao chép `.env.example` thành `.env` và chỉnh sửa:

```bash
# Nhà cung cấp
LLM_PROVIDER=ollama

# Ollama
API_ENDPOINT=http://localhost:11434/api/generate
DEFAULT_MODEL=mistral-small:24b

# API Keys (nếu dùng nhà cung cấp đám mây)
OPENROUTER_API_KEY=sk-or-v1-...
OPENAI_API_KEY=sk-...
GEMINI_API_KEY=...

# Hiệu suất
REQUEST_TIMEOUT=900
MAX_TOKENS_PER_CHUNK=400  # Phân đoạn theo token (mặc định: 400 tokens)
```

---

## Docker

```bash
docker build -t translatebook .
docker run -p 5000:5000 -v $(pwd)/translated_files:/app/translated_files translatebook
```

Xem [DOCKER.md](DOCKER.md) để biết thêm tùy chọn.

---

## Xử lý sự cố

| Vấn đề | Giải pháp |
|---------|----------|
| Ollama không kết nối được | Kiểm tra Ollama đang chạy, thử `curl http://localhost:11434/api/tags` |
| Không tìm thấy mô hình | Chạy `ollama list`, sau đó `ollama pull model-name` |

Xem [docs/TROUBLESHOOTING.md](docs/TROUBLESHOOTING.md) để biết thêm giải pháp.

---

## Tài liệu

| Hướng dẫn | Mô tả |
|-------|-------------|
| [docs/PROVIDERS.md](docs/PROVIDERS.md) | Cài đặt chi tiết nhà cung cấp (Ollama, LM Studio, OpenRouter, OpenAI, Gemini) |
| [docs/CLI.md](docs/CLI.md) | Tham khảo CLI đầy đủ |
| [docs/TROUBLESHOOTING.md](docs/TROUBLESHOOTING.md) | Giải pháp xử lý sự cố |
| [DOCKER.md](DOCKER.md) | Hướng dẫn triển khai Docker |

---

## Liên kết

- [Báo cáo sự cố](https://github.com/chuong1224/llmgamingtranslate/issues)
- [Các mô hình OpenRouter](https://openrouter.ai/models)

---

**Giấy phép:** AGPL-3.0

---
---

<div align="center">
  <h1>Translate Books with LLMs</h1>
</div>

Translate **books**, **subtitles**, and **documents** using AI - locally or in the cloud.

**No size limit.** Process documents of any length - from a single page to thousand-page novels. The intelligent chunking system handles unlimited content while preserving context between segments.

**Perfect preservation.** Your documents come out exactly as they went in: EPUB formatting, styles, and structure remain intact. SRT timecodes stay perfectly synchronized. Every tag, every timestamp, every formatting detail is preserved.

**Resume anytime.** Interrupted translation? Pick up exactly where you left off. The checkpoint system saves progress automatically.

Formats: **EPUB**, **SRT**, **DOCX**, **TXT**

<img width="1240" height="1945" alt="image" src="https://github.com/user-attachments/assets/7b9769df-6833-410d-ae38-a5894ca415dd" />

Providers:

<p align="left">
<img src="src/web/static/img/providers/ollama.png" alt="Ollama" height="32">&nbsp;&nbsp;
<img src="src/web/static/img/providers/poe.png" alt="Poe" height="32">&nbsp;&nbsp;
<img src="src/web/static/img/providers/openrouter.png" alt="OpenRouter" height="32">&nbsp;&nbsp;
<img src="src/web/static/img/providers/openai.png" alt="OpenAI" height="32">&nbsp;&nbsp;
<img src="src/web/static/img/providers/mistral.png" alt="Mistral" height="32">&nbsp;&nbsp;
<img src="src/web/static/img/providers/deepseek.png" alt="DeepSeek" height="32">&nbsp;&nbsp;
<img src="src/web/static/img/providers/gemini.png" alt="Gemini" height="32">
</p>

- [**Ollama**](https://ollama.com/download) (local / cloud)
- [**Poe**](https://poe.com/api_key) ⭐ Recommended - Easy setup, multiple AI models
- [**OpenRouter**](https://openrouter.ai/keys) (200+ models)
- [**OpenAI**](https://platform.openai.com/api-keys) (**compatible like LM Studio**)
- [**Mistral**](https://console.mistral.ai/api-keys)
- [**DeepSeek**](https://platform.deepseek.com/api_keys)
- [**Gemini**](https://aistudio.google.com/apikey)

> **[Translation Quality Benchmarks](https://github.com/chuong1224/llmgamingtranslate/wiki)** — Find the best model for your target language.

---

## Quick Start

### Download Executable (No Python Required!)

[![Download Windows](https://img.shields.io/badge/Download-Windows-blue?style=for-the-badge&logo=windows)](https://github.com/chuong1224/llmgamingtranslate/releases/latest/download/TranslateBook-Windows.zip)

1. Download and extract the zip
2. Install [Ollama](https://ollama.com/) (only if you want to run local AI models; skip if you only use cloud APIs)
3. Run `TranslateBook.exe`
4. Open http://localhost:5000 in your browser

> **Note:** First run creates a `TranslateBook_Data` folder with configuration files.

---

### For the Bearded Ones - Install from Source

**Prerequisites:** [Python 3.8+](https://www.python.org/downloads/), [Ollama](https://ollama.com/), [Git](https://git-scm.com/)

```bash
git clone https://github.com/chuong1224/llmgamingtranslate.git
cd llmgamingtranslate
ollama pull qwen3:14b    # Download a model

# Windows
start.bat

# Mac/Linux
chmod +x start.sh && ./start.sh
```

The web interface opens at **http://localhost:5000**

---

## LLM Providers

| Provider | Type | Setup |
|----------|------|-------|
| **Ollama** | Local | [ollama.com](https://ollama.com/) |
| **Poe** ⭐ | Cloud (Recommended) | [poe.com/api_key](https://poe.com/api_key) |
| **OpenAI-Compatible** | Local | llama.cpp, LM Studio, vLLM, LocalAI... |
| **OpenRouter** | Cloud (200+ models) | [openrouter.ai/keys](https://openrouter.ai/keys) |
| **OpenAI** | Cloud | [platform.openai.com](https://platform.openai.com/api-keys) |
| **Mistral** | Cloud | [console.mistral.ai](https://console.mistral.ai/api-keys) |
| **DeepSeek** | Cloud | [platform.deepseek.com](https://platform.deepseek.com/api_keys) |
| **Gemini** | Cloud | [Google AI Studio](https://makersuite.google.com/app/apikey) |

> **OpenAI-Compatible servers:** Use `--provider openai` with your server's endpoint (e.g., llama.cpp: `http://localhost:8080/v1/chat/completions`, LM Studio: `http://localhost:1234/v1/chat/completions`)

See [docs/PROVIDERS.md](docs/PROVIDERS.md) for detailed setup instructions.

---

## Command Line

```bash
# Basic (auto-generates "book (Chinese).epub")
python translate.py -i book.epub -sl English -tl Chinese

# With OpenRouter
python translate.py -i book.txt --provider openrouter \
    --openrouter_api_key YOUR_KEY -m anthropic/claude-sonnet-4 -tl French

# With OpenAI
python translate.py -i book.txt --provider openai \
    --openai_api_key YOUR_KEY -m gpt-4o -tl French

# With Gemini
python translate.py -i book.txt --provider gemini \
    --gemini_api_key YOUR_KEY -m gemini-2.0-flash -tl French

# With local OpenAI-compatible server (llama.cpp, LM Studio, vLLM, etc.)
python translate.py -i book.txt --provider openai \
    --api_endpoint http://localhost:8080/v1/chat/completions -m your-model -tl French
```

### Main Options

| Option | Description | Default |
|--------|-------------|---------|
| `-i, --input` | Input file | Required |
| `-o, --output` | Output file | Auto: `{name} ({lang}).{ext}` |
| `-sl, --source_lang` | Source language | English |
| `-tl, --target_lang` | Target language | Chinese |
| `-m, --model` | Model name | mistral-small:24b |
| `--provider` | ollama/openrouter/openai/gemini | ollama |
| `--text-cleanup` | OCR/typographic cleanup | disabled |
| `--refine` | Second pass for literary polish | disabled |
| `--tts` | Generate audio (Edge-TTS) | disabled |

See [docs/CLI.md](docs/CLI.md) for all options (TTS voices, rates, formats, etc.).

---

## Configuration (.env)

Copy `.env.example` to `.env` and edit:

```bash
# Provider
LLM_PROVIDER=ollama

# Ollama
API_ENDPOINT=http://localhost:11434/api/generate
DEFAULT_MODEL=mistral-small:24b

# API Keys (if using cloud providers)
OPENROUTER_API_KEY=sk-or-v1-...
OPENAI_API_KEY=sk-...
GEMINI_API_KEY=...

# Performance
REQUEST_TIMEOUT=900
MAX_TOKENS_PER_CHUNK=400  # Token-based chunking (default: 400 tokens)
```

---

## Docker

```bash
docker build -t translatebook .
docker run -p 5000:5000 -v $(pwd)/translated_files:/app/translated_files translatebook
```

See [DOCKER.md](DOCKER.md) for more options.

---

## Troubleshooting

| Problem | Solution |
|---------|----------|
| Ollama won't connect | Check Ollama is running, test `curl http://localhost:11434/api/tags` |
| Model not found | Run `ollama list`, then `ollama pull model-name` |

See [docs/TROUBLESHOOTING.md](docs/TROUBLESHOOTING.md) for more solutions.

---

## Documentation

| Guide | Description |
|-------|-------------|
| [docs/PROVIDERS.md](docs/PROVIDERS.md) | Detailed provider setup (Ollama, LM Studio, OpenRouter, OpenAI, Gemini) |
| [docs/CLI.md](docs/CLI.md) | Complete CLI reference |
| [docs/TROUBLESHOOTING.md](docs/TROUBLESHOOTING.md) | Problem solutions |
| [DOCKER.md](DOCKER.md) | Docker deployment guide |

---

## Links

- [Report Issues](https://github.com/chuong1224/llmgamingtranslate/issues)
- [OpenRouter Models](https://openrouter.ai/models)

---

**License:** AGPL-3.0
