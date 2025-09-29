# 🐍 SnakeDetect RAG - Hệ thống Phát hiện và Phân tích Rắn với AI

Dự án kết hợp **Computer Vision** và **Retrieval-Augmented Generation (RAG)** để phát hiện, phân tích và cung cấp thông tin chi tiết về các loài rắn thông qua hình ảnh.

## 🎯 Tổng quan

SnakeDetect_RAG là một hệ thống AI thông minh có khả năng:
- 🔍 **Crawl dữ liệu**: Thu thập hình ảnh và thông tin về rắn từ các nguồn web
- 🧠 **Phát hiện rắn**: Sử dụng Computer Vision để nhận diện rắn trong hình ảnh
- 📚 **RAG Pipeline**: Tìm kiếm và trả lời câu hỏi về các loài rắn dựa trên dữ liệu đã thu thập
- 💬 **Phân tích thông minh**: Cung cấp thông tin chi tiết về đặc điểm, môi trường sống, mức độ nguy hiểm

## 🏗️ Cấu trúc Project

```
SnakeDetect_RAG/
├── 📓 crawl_data_image_snake.ipynb    # Notebook crawl dữ liệu hình ảnh rắn
├── 📓 truc_quan_hoa_snake.ipynb       # Notebook trực quan hóa và phân tích
├── 📁 RAG/                            # Hệ thống RAG hoàn chỉnh
│   ├── main.py                        # Entry point chính
│   ├── requirements.txt               # Dependencies
│   ├── config/                        # Cấu hình hệ thống
│   ├── data/                          # Dữ liệu và JSON loader
│   ├── src/                           # Source code chính
│   └── examples/                      # Ví dụ demo
└── README.md                          # Tài liệu này
```

## 🚀 Tính năng chính

### 1. 🕸️ Thu thập dữ liệu (Data Crawling)
- Crawl hình ảnh rắn từ các nguồn web
- Thu thập thông tin mô tả, đặc điểm sinh học
- Lưu trữ metadata chi tiết

### 2. 🔍 Hệ thống RAG
- **Vector Database**: FAISS để lưu trữ embeddings
- **LLM Integration**: Google Gemini 2.5 Flash
- **Embedding Model**: Gemini text-embedding với 3072 dimensions
- **JSON Data Loader**: Linh hoạt load dữ liệu từ nhiều định dạng

### 3. 🤖 AI Analysis
- Phân tích hình ảnh để nhận diện loài rắn
- Trả lời câu hỏi về đặc điểm, môi trường sống
- Đánh giá mức độ nguy hiểm và cách xử lý

## 🛠️ Cài đặt và Sử dụng

### Prerequisites
```bash
# Python 3.8+
pip install -r RAG/requirements.txt
```

### Cấu hình
1. Tạo file `.env` trong folder `RAG/`:
```env
GOOGLE_API_KEY=your_gemini_api_key_here
```

2. Cấu hình trong `RAG/config/config.py` nếu cần thiết

### Chạy hệ thống

#### 1. Ingest dữ liệu
```bash
cd RAG/
python main.py --ingest data/documents.json --json-fields content title category
```

#### 2. Query về rắn
```bash
# Hỏi về thông tin chung
python main.py --query "Rắn hổ mang có nguy hiểm không?"

# Hỏi về đặc điểm
python main.py --query "Đặc điểm nhận dạng rắn lục"

# Hỏi về môi trường sống
python main.py --query "Rắn cạp nong sống ở đâu?"
```

#### 3. Quản lý dữ liệu
```bash
# Xem thống kê
python main.py --stats

# Reset dữ liệu
python main.py --reset
```

## 📊 Notebooks

### 1. `crawl_data_image_snake.ipynb`
- Thu thập hình ảnh rắn từ web
- Xử lý và lọc dữ liệu
- Tạo dataset cho training

### 2. `truc_quan_hoa_snake.ipynb`
- Visualize dữ liệu đã thu thập
- Phân tích phân bố các loài
- Đánh giá chất lượng dữ liệu

## 🔧 Kiến trúc Technical

### RAG Pipeline
```
🔤 Input Text → 🧠 Gemini Embedding → 🔍 FAISS Search → 📝 Context → 🤖 Gemini LLM → 💬 Response
```

### Data Flow
```
📄 JSON Data → 🔄 Chunking → 📊 Embeddings → 💾 Vector Store (.index + .pkl)
```

### Vector Storage
- **FAISS Index**: Lưu embedding vectors
- **PKL File**: Lưu text metadata tương ứng
- **Mapping**: `vector[i] ↔ text[i]`

## 🧪 Demo & Examples

```python
# Example usage trong code
from src.rag_pipeline import RAGPipeline

rag = RAGPipeline()
result = rag.query("Cách phân biệt rắn độc và không độc?")
print(result["response"])
```

## 📋 Dependencies

Xem chi tiết trong `RAG/requirements.txt`:
- `google-generativeai` - Gemini AI
- `faiss-cpu` - Vector similarity search  
- `numpy` - Numerical computing
- `python-dotenv` - Environment variables

## 🤝 Contributing

1. Fork repository
2. Tạo feature branch: `git checkout -b feature/snake-detection`
3. Commit changes: `git commit -m "Add snake detection feature"`
4. Push branch: `git push origin feature/snake-detection`
5. Tạo Pull Request

## 📝 License

MIT License - Xem file LICENSE để biết thêm chi tiết.

## 📞 Contact

- **Author**: Anhhuhi123
- **GitHub**: [SnakeDetect_RAG](https://github.com/Anhhuhi123/SnakeDetect_RAG)
- **Issues**: [Report Bug](https://github.com/Anhhuhi123/SnakeDetect_RAG/issues)

---

⭐ **Star repository này nếu thấy hữu ích!** ⭐
