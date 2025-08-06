# 🚀 Dokploy ile Promptitron Deployment

Bu rehber, Promptitron sisteminin Dokploy platformunda nasıl deploy edileceğini açıklar.

## 📋 Ön Koşullar

1. **Dokploy hesabı** - [dokploy.com](https://dokploy.com) üzerinden kayıt olun
2. **Git repository** - Kodunuzun GitHub/GitLab'da olması gerekli
3. **Google API Key** - Gemini AI için gerekli
4. **Domain** (opsiyonel) - Özel alan adı için

## 🎯 Adım Adım Deployment

### 1. Dokploy'da Yeni Proje Oluşturma

1. Dokploy dashboard'una giriş yapın
2. **"New Application"** butonuna tıklayın
3. **"Docker Compose"** seçeneğini seçin
4. Proje bilgilerini doldurun:
   ```
   Name: promptitron-unified
   Description: AI-powered educational assistant
   ```

### 2. Git Repository Bağlama

1. **Repository** sekmesinde:
   ```
   Repository URL: https://github.com/your-username/promptitron_unified.git
   Branch: main
   ```

2. **Build Configuration**:
   ```
   Docker Compose File: docker-compose.yml
   ```

### 3. Environment Variables Ayarlama

**Gerekli Değişkenler:**
```bash
GOOGLE_API_KEY=your_google_api_key_here
GEMINI_MODEL=gemini-2.5-flash
TEMPERATURE=0.7
ENVIRONMENT=production
HOST=0.0.0.0
PORT=8000
```

**Opsiyonel Değişkenler:**
```bash
DEBUG=false
LOG_LEVEL=INFO
CHROMA_HOST=chroma-db
CHROMA_PORT=8000
MONITOR_PORT=8002
```

### 4. Domain Configuration

#### Otomatik Subdomain
Dokploy otomatik olarak şu URL'leri oluşturacak:
- `https://your-app.dokploy.app` - Ana API
- `https://your-app-monitor.dokploy.app` - Monitoring

#### Özel Domain (Opsiyonel)
1. **Domains** sekmesine gidin
2. Domain'inizi ekleyin: `api.yourdomain.com`
3. DNS ayarlarınızı yapın:
   ```
   Type: CNAME
   Name: api
   Value: your-app.dokploy.app
   ```

### 5. SSL Certificate

Dokploy otomatik olarak Let's Encrypt SSL sertifikası oluşturacak.

### 6. Deploy Etme

1. **Deploy** butonuna tıklayın
2. Build logs'unu izleyin
3. Deploy tamamlandığında URL'ler aktif olacak

## 🔧 Servis Yapılandırması

### Ana API Servisi
- **URL**: `https://your-app.dokploy.app`
- **Health Check**: `/health`
- **Documentation**: `/docs`
- **Port**: 8000

### Monitoring Servisi
- **URL**: `https://your-app-monitor.dokploy.app`
- **Health Check**: `/health`
- **System Stats**: `/system/stats`
- **Port**: 8002

### ChromaDB (Internal)
- **Internal URL**: `chroma-db:8000`
- **Health Check**: `/api/v1/heartbeat`
- **Sadece internal erişim**

## 📊 İzleme ve Yönetim

### Dokploy Dashboard'dan
1. **Logs** sekmesi - Tüm servislerin logları
2. **Metrics** sekmesi - CPU, Memory, Network kullanımı
3. **Terminal** sekmesi - Container içine erişim

### API Endpoints
```bash
# Sistem durumu
curl https://your-app.dokploy.app/health

# Monitoring dashboard
curl https://your-app-monitor.dokploy.app/health

# Sistem metrikleri
curl https://your-app-monitor.dokploy.app/system/stats
```

## 🔄 Güncelleme ve Redeploy

### Otomatik Deploy
1. **Webhooks** sekmesinde otomatik deploy'u aktifleştirin
2. Git'e push yaptığınızda otomatik deploy olur

### Manuel Deploy
1. Dokploy dashboard'una gidin
2. **Redeploy** butonuna tıklayın
3. Yeni build başlayacak

### Rolling Update
```bash
# Dokploy otomatik rolling update yapar
# Zero-downtime deployment
```

## 🛠️ Debugging

### Container Logları
```bash
# Dokploy terminal'den
docker-compose logs -f promptitron-api
docker-compose logs -f chroma-db
docker-compose logs -f promptitron-monitor
```

### Container İçine Erişim
```bash
# Dokploy terminal'den
docker-compose exec promptitron-api bash
```

### Database İnceleme
```bash
# ChromaDB durumu
curl http://chroma-db:8000/api/v1/collections
```

## 🔐 Güvenlik

### API Key Güvenliği
1. Environment variables'da API key'i saklayın
2. Dashboard'da **"Hide in logs"** seçeneğini işaretleyin

### Network Security
- ChromaDB sadece internal network'te erişilebilir
- API ve Monitor servisleri public
- HTTPS zorunlu

### Access Control
```bash
# API endpoint'lerinde auth middleware kullanın
# Monitoring endpoint'ini IP restrict edin
```

## 🚨 Sorun Giderme

### Yaygın Sorunlar

#### 1. Build Hatası
```bash
# Dockerfile'ları kontrol edin
# requirements.txt eksik dependency'leri ekleyin
```

#### 2. ChromaDB Bağlantı Sorunu
```bash
# Environment variables kontrol edin
CHROMA_HOST=chroma-db
CHROMA_PORT=8000
```

#### 3. Memory Limit
```bash
# docker-compose.yml'de memory limit artırın
deploy:
  resources:
    limits:
      memory: 2G
```

#### 4. Port Conflict
```bash
# Dokploy otomatik port assignment kullanır
# Manuel port belirtmeyin
```

### Log Analizi
```bash
# Dokploy'da Logs sekmesinden:
# - Build logs
# - Runtime logs  
# - Error logs
```

## 📈 Scaling

### Horizontal Scaling
```yaml
# docker-compose.yml'de replicas ayarlayın
deploy:
  replicas: 2
```

### Resource Allocation
```yaml
deploy:
  resources:
    limits:
      cpus: '2.0'
      memory: 4G
    reservations:
      cpus: '0.5'
      memory: 1G
```

## 💾 Backup

### Database Backup
```bash
# Dokploy terminal'den
docker-compose exec chroma-db tar -czf /tmp/chroma_backup.tar.gz /chroma/chroma
```

### Configuration Backup
- Environment variables'ı kaydedin
- `dokploy.json` dosyasını version control'de tutun

## 📞 Destek

### Dokploy Destek
- **Documentation**: [docs.dokploy.com](https://docs.dokploy.com)
- **Discord**: Dokploy community
- **Email**: support@dokploy.com

### Promptitron Özgü Sorunlar
- GitHub issues'da sorun bildirin
- Logs'ları ve error mesajlarını paylaşın

## ✅ Deployment Checklist

- [ ] Git repository hazır
- [ ] Google API Key alındı
- [ ] Environment variables set edildi
- [ ] Docker Compose file kontrol edildi
- [ ] Domain/subdomain ayarları yapıldı
- [ ] SSL sertifikası aktif
- [ ] Health check'ler çalışıyor
- [ ] Monitoring dashboard erişilebilir
- [ ] Backup stratejisi belirlendi