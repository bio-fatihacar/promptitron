# 🐳 Promptitron Docker Deployment

Bu dosya, Promptitron sisteminin Docker ile nasıl çalıştırılacağını açıklar.

## 🚀 Hızlı Başlangıç

### 1. Ortam Değişkenlerini Ayarlayın

```bash
cp .env.docker .env
# .env dosyasını düzenleyin ve Google API anahtarınızı ekleyin
```

### 2. Docker Compose ile Çalıştırın

```bash
# Tüm servisleri başlat
docker-compose up -d

# Logları görüntüle
docker-compose logs -f

# Servislerin durumunu kontrol et
docker-compose ps
```

## 📦 Servisler

### 🔧 Ana Servisler
- **promptitron-api** (Port 8000) - Ana FastAPI uygulaması
- **chroma-db** (Port 8001) - ChromaDB vektör veritabanı
- **promptitron-worker** - Arka plan doküman işleme servisi
- **promptitron-monitor** (Port 8002) - Sistem izleme servisi

### 🔗 Erişim URL'leri
- API Dokümantasyonu: http://localhost:8000/docs
- Sistem Durumu: http://localhost:8000/health
- ChromaDB: http://localhost:8001
- Monitor Dashboard: http://localhost:8002/health

## 🎛️ Servis Yönetimi

### Belirli Servisleri Çalıştırma
```bash
# Sadece API ve veritabanını çalıştır
docker-compose up -d promptitron-api chroma-db

# Worker'ı yeniden başlat
docker-compose restart promptitron-worker

# Monitor servisini durdur
docker-compose stop promptitron-monitor
```

### Log İzleme
```bash
# Tüm servislerin logları
docker-compose logs -f

# Belirli servisin logları
docker-compose logs -f promptitron-api

# Son 100 satır
docker-compose logs --tail=100 promptitron-api
```

## 🔧 Yapılandırma

### Ortam Değişkenleri
```bash
# Google AI
GOOGLE_API_KEY=your_api_key_here
GEMINI_MODEL=gemini-2.5-flash
TEMPERATURE=0.7

# Uygulama
ENVIRONMENT=production
HOST=0.0.0.0
PORT=8000

# ChromaDB
CHROMA_HOST=chroma-db
CHROMA_PORT=8000
```

### Volume Yönetimi
```bash
# Volume'ları listele
docker volume ls

# ChromaDB verisini yedekle
docker run --rm -v promptitron_chroma_data:/data -v $(pwd):/backup ubuntu tar czf /backup/chroma_backup.tar.gz -C /data .

# Yedekten geri yükle
docker run --rm -v promptitron_chroma_data:/data -v $(pwd):/backup ubuntu tar xzf /backup/chroma_backup.tar.gz -C /data
```

## 🐛 Sorun Giderme

### Sistem Durumu Kontrolü
```bash
# Tüm servislerin durumu
curl http://localhost:8002/health

# API servisi durumu
curl http://localhost:8000/health

# ChromaDB durumu
curl http://localhost:8001/api/v1/heartbeat
```

### Yaygın Sorunlar

#### Port Çakışması
```bash
# Kullanılan portları kontrol et
netstat -tlnp | grep :8000

# Farklı port kullan
docker-compose up -d --scale promptitron-api=0
docker-compose run -p 8080:8000 promptitron-api
```

#### Bellek Sorunu
```bash
# Kullanılmayan container'ları temizle
docker system prune

# Image'leri yeniden oluştur
docker-compose build --no-cache
```

#### ChromaDB Bağlantı Sorunu
```bash
# ChromaDB container'ını yeniden başlat
docker-compose restart chroma-db

# Bağlantıyı test et
docker-compose exec promptitron-api curl http://chroma-db:8000/api/v1/heartbeat
```

## 🔄 Güncelleme

```bash
# Yeni kodu çek
git pull origin main

# Image'leri yeniden oluştur
docker-compose build

# Servisleri yeniden başlat
docker-compose up -d
```

## 📊 İzleme

### Performans İzleme
```bash
# Container kaynak kullanımı
docker stats

# Sistem metrikleri
curl http://localhost:8002/system/stats

# Log dosyaları
curl http://localhost:8002/system/logs
```

### Health Check
```bash
# Otomatik health check
while true; do
  curl -f http://localhost:8000/health || echo "API Down"
  sleep 30
done
```

## 🚚 Production Deployment

### Resource Limits
```yaml
# docker-compose.override.yml
version: '3.8'
services:
  promptitron-api:
    deploy:
      resources:
        limits:
          memory: 2G
          cpus: "1.0"
        reservations:
          memory: 1G
          cpus: "0.5"
```

### Auto-Restart
```bash
# Restart policy'yi güncelle
docker-compose up -d --force-recreate
```

## 🗑️ Temizleme

```bash
# Tüm servisleri durdur ve kaldır
docker-compose down

# Volume'ları da sil (DİKKAT: Veri kaybı!)
docker-compose down -v

# Kullanılmayan her şeyi temizle
docker system prune -a
```