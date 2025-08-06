# 🚀 Promptitron Unified AI Education System

> **Modern AI-Powered Education Platform for YKS Students**  
> Türkiye'nin en kapsamlı yapay zeka destekli eğitim platformu

[![Python](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![Next.js](https://img.shields.io/badge/Next.js-15-black.svg)](https://nextjs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.x-blue.svg)](https://www.typescriptlang.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

---

## 📋 İçindekiler

1. [Özellikler Hiyerarşisi](#-özellikler-hiyerarşisi)
2. [Teknoloji Stack](#-teknoloji-stack)
3. [Sistem Mimarisi](#-sistem-mimarisi)
4. [Detaylı Özellikler](#-detaylı-özellikler)
5. [Kurulum](#-kurulum)
6. [API Dokümantasyonu](#-api-dokümantasyonu)
7. [Akış Diyagramları](#-akış-diyagramları)

---

## 🏗️ Özellikler Hiyerarşisi

### 1. **🤖 AI & Backend Sistemi**
   - **1.1 Yapay Zeka Modeli**
     - Google Gemini 2.5 Pro/Flash/Flash-Lite
     - Çoklu model stratejisi
     - Function Calling desteği
   - **1.2 RAG Sistemi**
     - ChromaDB vektör veritabanı
     - Hibrit arama (Semantik + Anahtar Kelime)
     - Akıllı yeniden sıralama
   - **1.3 Uzman Sistem**
     - Ders bazlı uzmanlar (Matematik, Fizik, Kimya, Biyoloji, vb.)
     - LangGraph workflow sistemi
     - Otomatik uzman seçimi
   - **1.4 Bellek Sistemi**
     - Konuşma belleği
     - Öğrenci profili yönetimi
     - Uzun dönem hafıza

### 2. **🎓 Eğitim Özellikleri**
   - **2.1 Müfredat Tabanlı**
     - YKS müfredat entegrasyonu
     - 10 ders desteği
     - Kazanım bazlı öğretim
   - **2.2 Soru Üretimi**
     - Çoktan seçmeli sorular
     - Doğru-yanlış soruları
     - Boşluk doldurma
     - Kısa cevap ve kompozisyon
   - **2.3 İçerik Analizi**
     - Metin analizi
     - Döküman analizi (PDF, Word, vb.)
     - Web sitesi analizi
     - YouTube video analizi
   - **2.4 Çalışma Yönetimi**
     - Kişiselleştirilmiş çalışma planları
     - İlerleme takibi
     - Performans analizi

### 3. **💻 Frontend & UI**
   - **3.1 Web Arayüzü**
     - Modern React/Next.js
     - TypeScript güvenliği
     - Tailwind CSS styling
     - ShadCN/UI komponenleri
   - **3.2 Sayfa Yapısı**
     - Ana sayfa ve navigasyon
     - YKS kazanımları sayfası
     - Servisler (Soru üretimi, Analiz, vb.)
     - Müfredat tabanlı sayfalar
     - 404 ve hata sayfaları
   - **3.3 Etkileşim**
     - Real-time chat sistemi
     - Dosya yükleme
     - Drag & drop desteği
     - Responsive tasarım

### 4. **🔧 Sistem & API**
   - **4.1 FastAPI Backend**
     - RESTful API
     - Otomatik dokümantasyon
     - Rate limiting
     - Error handling
   - **4.2 Veri Yönetimi**
     - PostgreSQL/SQLite
     - ChromaDB vektör DB
     - Cache sistemi
     - Dosya yönetimi
   - **4.3 Güvenlik**
     - API key koruması
     - CORS yapılandırması
     - Input validation
     - Content filtering

---

## 🛠️ Teknoloji Stack

### **Backend Teknolojileri**
| Teknoloji | Kullanım Alanı | Versiyon |
|-----------|---------------|----------|
| **Python** | Ana backend dili | 3.8+ |
| **FastAPI** | Web framework ve API | Latest |
| **Google Gemini 2.5** | LLM modeli | Pro/Flash/Flash-Lite |
| **LangChain** | LLM orkestrasyon | Latest |
| **LangGraph** | Workflow yönetimi | Latest |
| **ChromaDB** | Vektör veritabanı | Latest |
| **Pydantic** | Veri validasyon | Latest |

### **Frontend Teknolojileri**
| Teknoloji | Kullanım Alanı | Versiyon |
|-----------|---------------|----------|
| **Next.js** | React framework | 15.x |
| **React** | UI kütüphanesi | 18.x |
| **TypeScript** | Type güvenliği | 5.x |
| **Tailwind CSS** | Styling framework | Latest |
| **ShadCN/UI** | Komponent kütüphanesi | Latest |
| **Lucide React** | Icon kütüphanesi | Latest |

### **Veri & Depolama**
| Teknoloji | Kullanım Alanı | Kullanım Yeri |
|-----------|---------------|-------------|
| **ChromaDB** | Vektör arama | RAG sistemi |
| **SQLite** | İlişkisel veri | Metadata, cache |
| **JSON** | Müfredat verileri | Statik dosyalar |
| **File System** | Dosya yönetimi | Upload/download |

### **AI & ML Teknolojileri**
| Teknoloji | Kullanım Alanı | Entegrasyon |
|-----------|---------------|-------------|
| **Gemini 2.5 Pro** | Karmaşık analiz | Core/gemini_client.py |
| **Gemini 2.5 Flash** | Hızlı yanıtlar | Core/gemini_client.py |
| **Embedding API** | Vektör dönüşümü | RAG sistemi |
| **Function Calling** | Yapılandırılmış çıktı | Tüm modüller |

---

## 🏛️ Sistem Mimarisi

### **Proje Yapısı**
```
promptitron_unified/
├── 🐍 **Backend (Python)**
│   ├── api/                     # FastAPI uygulaması
│   │   ├── routers/            # API endpoint'leri
│   │   ├── models/             # Pydantic modelleri
│   │   ├── controllers/        # Business logic
│   │   └── middleware/         # Middleware'ler
│   ├── core/                   # Temel AI modülleri
│   │   ├── gemini_client.py    # LLM client
│   │   ├── rag_system.py       # RAG implementasyonu
│   │   ├── agents.py           # LangGraph agents
│   │   └── conversation_memory.py # Bellek sistemi
│   ├── models/                 # Veri modelleri
│   ├── data/                   # Müfredat verileri
│   └── config.py               # Konfigürasyon
├── 💻 **Frontend (Next.js)**
│   ├── app/                    # Next.js 13+ App Router
│   │   ├── (lessons)/          # Ders sayfaları
│   │   ├── services/           # Servis sayfaları
│   │   ├── curriculum/         # Müfredat sayfaları
│   │   └── not-found.tsx       # 404 sayfası
│   ├── components/             # React komponentleri
│   ├── lib/                    # Utility'ler
│   │   ├── api/               # API client
│   │   └── hooks/             # Custom hooks
│   └── public/                 # Statik dosyalar
├── 📦 **Veri & Cache**
│   ├── chroma_db/             # Vektör veritabanı
│   ├── uploads/               # Yüklenen dosyalar
│   └── logo/                  # Logo dosyaları
└── 📝 **Konfigürasyon**
    ├── requirements.txt        # Python deps
    ├── package.json           # Node.js deps
    └── .env                   # Environment vars
```

---

## 📚 Detaylı Özellikler

### **1. YKS Kazanımları Sistemi**
- **Kapsamlı Müfredat**: 10 farklı ders (Matematik, Fizik, Kimya, Biyoloji, vb.)
- **Hiyerarşik Yapı**: Ders → Sınıf → Konu → Kazanım
- **İnteraktif Seçim**: Checkbox tabanlı çoklu seçim
- **Görsel Organizasyon**: Genişletilebilir ağaç yapısı
- **Otomatik Parsing**: JSON verilerinin akıllı işlenmesi

### **2. Soru Üretim Sistemi**
- **Çoklu Format**: Multiple choice, True/False, Fill-in-blank, Essay
- **Zorluk Seviyeleri**: Easy, Medium, Hard
- **Sınav Tipları**: TYT, AYT, YKS, LGS
- **Müfredat Entegrasyonu**: Seçili kazanımlara dayalı
- **Otomatik Cevap Anahtarı**: Açıklamalı çözümler

### **3. İçerik Analizi**
- **Metin Analizi**: 6 farklı analiz tipi
- **Döküman Analizi**: PDF, Word, Text, Markdown desteği
- **Web Analizi**: URL tabanlı içerik çözümlemesi
- **YouTube Analizi**: Video transkript ve özet
- **AI Destekli**: Gemini 2.5 ile güçlendirilmiş

### **4. RAG (Retrieval-Augmented Generation)**
- **Hibrit Arama**: Semantic + Keyword search
- **Çoklu Koleksiyon**: Curriculum, conversations, documents
- **Akıllı Reranking**: LLM-based result optimization
- **Kişiselleştirme**: User profile based filtering
- **Cache Sistemi**: Performance optimizasyonu

### **5. Konuşma ve Bellek**
- **Context Aware**: Sohbet geçmişi takibi
- **Long-term Memory**: Öğrenci profili hafızası
- **Session Management**: Oturum bazlı konuşmalar
- **Personalization**: Öğrenme stiline göre uyarlama
- **Progress Tracking**: İlerleme ve performans analizi

### **6. Uzman Sistem**
- **Ders Uzmanları**: Her ders için özelleşmiş AI
- **Otomatik Routing**: Soru tipine göre uzman seçimi
- **LangGraph Integration**: Workflow tabanlı işlem
- **Function Calling**: Yapılandırılmış çıktılar
- **Multi-agent Collaboration**: Uzmanlar arası işbirliği

### **7. Modern Web Arayüzü**
- **Responsive Design**: Mobil-first yaklaşım
- **Component Based**: Yeniden kullanılabilir UI
- **Real-time Updates**: Live data synchronization
- **File Upload**: Drag & drop file handling
- **Error Handling**: Kullanıcı dostu hata yönetimi

### **8. API ve Entegrasyonlar**
- **RESTful API**: Standardize endpoint'ler
- **OpenAPI Docs**: Otomatik dokümantasyon
- **Rate Limiting**: API kullanım koruması
- **CORS Support**: Cross-origin request desteği
- **Type Safety**: Pydantic model validation

---

## ⚡ Kurulum

### **Ön Gereksinimler**
- Python 3.8+
- Node.js 18+
- Google Cloud API Key (Gemini)
- Git

### **1. Repository Klonlama**
```bash
git clone https://github.com/your-username/promptitron-unified.git
cd promptitron-unified
```

### **2. Backend Kurulumu**
```bash
# Virtual environment oluştur
python -m venv venv

# Windows
venv\\Scripts\\activate
# Linux/Mac
source venv/bin/activate

# Dependencies yükle
pip install -r requirements.txt
```

### **3. Frontend Kurulumu**
```bash
cd client
npm install
# veya
yarn install
```

### **4. Environment Konfigürasyonu**
```bash
# .env dosyası oluştur
cp .env.example .env

# Gerekli değerleri düzenle
GOOGLE_API_KEY=your_google_api_key_here
SECRET_KEY=your_secret_key_here
DATABASE_URL=sqlite:///./promptitron.db
```

### **5. Veritabanı Hazırlığı**
```bash
# ChromaDB otomatik oluşturulacak
# SQLite database otomatik oluşturulacak
```

### **6. Uygulamayı Çalıştırma**

**Backend:**
```bash
# Ana dizinde
python main.py
# veya
uvicorn api.main:app --reload
```

**Frontend:**
```bash
# client dizininde
npm run dev
# veya
yarn dev
```

### **7. Erişim Noktaları**
- **Frontend**: http://localhost:3000
- **Backend API**: http://localhost:8000
- **API Docs**: http://localhost:8000/docs
- **Health Check**: http://localhost:8000/health

---

## 🔌 API Dokümantasyonu

### **Authentication**
```http
Authorization: Bearer YOUR_API_KEY
Content-Type: application/json
```

### **Core Endpoints**

#### **1. Chat System**
```http
POST /chat
{
    "message": "Matematik türev konusunu açıkla",
    "student_id": "student_123",
    "session_id": "session_456",
    "use_memory": true,
    "context": {}
}
```

#### **2. Question Generation**
```http
POST /generate/questions
{
    "subject": "matematik",
    "topic": "türev",
    "difficulty": "medium",
    "question_type": "multiple_choice",
    "count": 5,
    "exam_type": "YKS"
}
```

#### **3. Curriculum Questions**
```http
POST /curriculum/questions
{
    "selected_topics": [
        {
            "ders": "matematik",
            "sinif": "11",
            "konu": "Türev",
            "kazanim": "Türev kurallarını uygular",
            "title": "Türev Kuralları"
        }
    ],
    "difficulty": "medium",
    "count": 3
}
```

#### **4. Content Analysis**
```http
POST /analyze/content
{
    "content": "Analiz edilecek metin içeriği...",
    "analysis_type": "educational",
    "include_suggestions": true
}
```

#### **5. Document Upload**
```http
POST /upload/document
Content-Type: multipart/form-data

file: [PDF/Word/Text file]
description: "Document description"
analysis_type: "general"
```

#### **6. YouTube Analysis**
```http
POST /youtube/analyze
{
    "url": "https://www.youtube.com/watch?v=...",
    "analysis_type": "educational",
    "custom_prompt": "Focus on mathematical concepts"
}
```

### **Response Format**
```json
{
    "success": true,
    "data": {
        "response": "AI generated content",
        "metadata": {
            "model_used": "gemini-2.5-flash",
            "tokens_used": 1250,
            "processing_time": 2.3
        }
    },
    "agent_used": "mathematics_expert",
    "session_id": "session_456"
}
```

---

## 📊 Akış Diyagramları

> **Not**: Detaylı akış diyagramları ayrı HTML sayfasında görüntülenebilir.  
> Diyagramlar Mermaid formatında hazırlanmış ve interaktif olarak sunulmaktadır.

### **Diyagram Kategorileri**
1. **Sistem Mimarisi**: Genel sistem yapısı ve bileşenler
2. **Veri Akışı**: Kullanıcı isteğinden yanıta kadar veri akışı
3. **Girdi-Çıktı Süreçleri**: Her özellik için detaylı akış

---

## 🧪 Test ve Geliştirme

### **Test Komutları**
```bash
# Backend testleri
pytest tests/

# Frontend testleri
npm test

# Integration testleri
python -m pytest tests/test_integration.py
```

### **Development Mode**
```bash
# Backend (hot reload)
uvicorn api.main:app --reload

# Frontend (hot reload)
npm run dev
```

### **Linting ve Formatting**
```bash
# Backend
black core/ api/
flake8 core/ api/

# Frontend
npm run lint
npm run format
```

---

## 🔧 Konfigürasyon

### **Environment Variables**
```env
# Core Settings
GOOGLE_API_KEY=your_google_api_key
SECRET_KEY=your_secret_key
DEBUG=true

# Database
DATABASE_URL=sqlite:///./promptitron.db
CHROMA_PERSIST_DIR=chroma_db

# API Settings
MAX_OUTPUT_TOKENS=8192
TEMPERATURE=0.7
TOP_P=0.95

# File Upload
MAX_UPLOAD_SIZE=104857600  # 100MB
UPLOAD_DIR=uploads

# Rate Limiting
RATE_LIMIT_REQUESTS=100
RATE_LIMIT_PERIOD=60
```

### **Model Configuration**
```python
# config.py
GEMINI_MODELS = {
    "pro": "gemini-2.5-pro",        # Complex reasoning
    "flash": "gemini-2.5-flash",    # General purpose
    "lite": "gemini-2.5-flash-lite" # Fast & economical
}
```

---

## 🚨 Troubleshooting

### **Yaygın Sorunlar**

#### **1. Google API Hatası**
```bash
# Hata: Invalid API key
# Çözüm: .env dosyasında API key kontrolü
echo $GOOGLE_API_KEY
```

#### **2. ChromaDB Hatası**
```bash
# Hata: ChromaDB connection failed
# Çözüm: ChromaDB yeniden oluştur
rm -rf chroma_db/
python main.py
```

#### **3. Port Çakışması**
```bash
# Hata: Port already in use
# Çözüm: Port değiştir
uvicorn api.main:app --port 8001
```

#### **4. Memory Hatası**
```python
# config.py içinde
MAX_OUTPUT_TOKENS = 4096  # Azalt
BATCH_SIZE = 10          # Küçült
```

### **Debug Mode**
```python
import logging
logging.basicConfig(level=logging.DEBUG)
```

---

## 🤝 Contributing

### **Development Workflow**
1. Fork repository
2. Create feature branch: `git checkout -b feature/amazing-feature`
3. Commit changes: `git commit -m 'Add amazing feature'`
4. Push to branch: `git push origin feature/amazing-feature`
5. Open Pull Request

### **Code Standards**
- **Python**: PEP 8, Type hints
- **TypeScript**: Strict mode, ESLint
- **Commits**: Conventional commits format
- **Documentation**: Inline comments + README updates

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 📞 Support & Contact

- **📧 Email**: support@promptitron.ai
- **🐛 Issues**: [GitHub Issues](https://github.com/your-username/promptitron-unified/issues)
- **📖 Docs**: http://localhost:8000/docs
- **💬 Discussions**: [GitHub Discussions](https://github.com/your-username/promptitron-unified/discussions)

---

## 🌟 Credits

- **AI Model**: Google Gemini 2.5
- **Vector DB**: ChromaDB
- **Frontend**: Next.js Team
- **UI Components**: ShadCN/UI
- **Icons**: Lucide React

---

**⚠️ Disclaimer**: Bu sistem eğitim amaçlıdır ve gerçek sınav sonuçlarını garanti etmez. Profesyonel eğitim danışmanlığı almanızı öneririz.

---

*Promptitron - Türkiye'nin AI destekli eğitim platformu* 🇹🇷