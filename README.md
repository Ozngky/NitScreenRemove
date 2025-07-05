# NitScreenRemover - Velocity Eklentisi

## Açıklama
NitScreenRemover, Velocity proxy sunucularında **TÜM YÜKLEME EKRANLARINI** kaldıran gelişmiş bir eklentidir. Sunucular arası geçiş, login bekleme, ItemsAdder texture pack yükleme ve Mojang loading screen'lerini tamamen bypass eder. Oyuncular **ANLIK** olarak sunucuya bağlanır ve hiçbir yükleme ekranı görmez!

## Özellikler

### 🚀 Ana Özellikler
- **Loading Screen Kaldırma**: Sunucular arası geçişlerde yükleme ekranını hızlıca kaldırır
- **🔥 Siyah Ekran Kaldırma**: 1 saniyelik siyah ekranı da tamamen kaldırır
- **⚡ Ultra Fast Mode**: Maximum hızda geçiş, anında world rendering
- **🎯 Aggressive Rendering**: Agresif world rendering ve chunk preloading
- **🚪 LOGIN HİZLANDIRMA**: Sunucuya giriş bekleme süresini kaldırır
- **📦 ITEMSADDER ANLIK YÜKLEME**: Texture pack anlık yüklenir, yükleme ekranı yok
- **🛑 MOJANG BYPASS**: Mojang loading screen tamamen bypass edilir
- **⚡ Anlık Bağlantı**: Tıkladığı gibi sunucuya direkt bağlanır
- **Smooth Transition**: Yumuşak geçiş efektleri ile daha iyi UX
- **Server Preloading**: Sunucuları önceden yükleme sistemi
- **Custom Messages**: Özelleştirilebilir geçiş mesajları
- **Debug Mode**: Gelişmiş hata ayıklama ve loglama

### ⚙️ Konfigürasyon
- **Yeniden Yüklenebilir**: Sunucuyu yeniden başlatmadan ayarları değiştirebilirsiniz
- **Flexible Settings**: Her özellik ayrı ayrı açılıp kapatılabilir
- **Performance Tuning**: Gecikme süreleri özelleştirilebilir

## Kurulum

### Gereksinimler
- **Velocity**: 3.2.0 veya üzeri
- **Java**: 11 veya üzeri
- **Maven**: 3.6.0 veya üzeri (derleme için)

### Adımlar
1. **Derleme**:
   ```bash
   mvn clean package
   ```

2. **Kurulum**:
   - `target/nitscreen-remover-1.0-SNAPSHOT.jar` dosyasını Velocity'nin `plugins` klasörüne kopyalayın
   - Velocity'yi yeniden başlatın

3. **Konfigürasyon**:
   - `plugins/nitscreen-remover/config.properties` dosyası otomatik olarak oluşturulur
   - Gerekli ayarları yapın

## Kullanım

### Komutlar
| Komut | Açıklama | Yetki |
|-------|----------|-------|
| `/nitscreen help` | Yardım menüsü | `nitscreen.use` |
| `/nitscreen status` | Plugin durumu | `nitscreen.use` |
| `/nitscreen reload` | Konfigürasyon yenile | `nitscreen.admin` |
| `/nitscreen toggle <özellik>` | Özellik aç/kapat | `nitscreen.admin` |
| `/nitscreen test` | Loading screen test | `nitscreen.admin` |

### Kısayollar
- `/nsr` - `/nitscreen` komutunun kısayolu

### Yetkiler
```yaml
permissions:
  nitscreen.use: true      # Temel komutlar
  nitscreen.admin: false   # Admin komutları
```

## Konfigürasyon

### config.properties
```properties
# Smooth transition özelliği
enable-smooth-transition=true

# Sunucu preloading özelliği
enable-preloading=true

# Özel mesajlar
enable-custom-messages=true

# Transition gecikmesi (milisaniye)
transition-delay-ms=50

# Mesaj temizleme gecikmesi (milisaniye)
message-cleanup-delay-ms=2000

# Debug modu
enable-debug-mode=false

# 🔥 SIYAH EKRAN KALDIRMA - Ultra Fast Mode
enable-ultra-fast-mode=true

# 🎯 Agresif world rendering
enable-aggressive-rendering=true

# World render gecikmesi (milisaniye) - Düşük = Daha hızlı
world-render-delay-ms=5

# 🚪 LOGIN HİZLANDIRMA - Sunucu giriş beklemesini kaldır
enable-login-optimization=true

# 📦 ITEMSADDER TEXTURE PACK - Anlık yükleme
enable-resource-pack-optimization=true

# Resource pack yükleme gecikmesi (milisaniye) - 0 = Anında
resource-pack-delay-ms=1

# 🛑 MOJANG LOADING SCREEN BYPASS - Mojang ekranını atla
enable-mojang-bypass=true
```

### Özellik Açıklamaları

#### 🎯 Smooth Transition
- Sunucular arası geçişleri yumuşak hale getirir
- Ani kesintileri önler
- Oyuncu deneyimini iyileştirir

#### ⚡ Preloading
- Sunucuları önceden yükleme sistemi
- Geçiş süresini azaltır
- Performans optimizasyonu

#### 💬 Custom Messages
- Özelleştirilebilir geçiş mesajları
- Görsel feedback sistemi
- Oyuncu bilgilendirmesi

#### 🐛 Debug Mode
- Detaylı loglama
- Hata ayıklama bilgileri
- Gelişmiş monitoring

#### 🔥 Ultra Fast Mode
- Maximum hızda sunucu geçişi
- Siyah ekran tamamen kaldırılır
- 1 saniye > 0.05 saniye geçiş
- Anında world rendering

#### 🎯 Aggressive Rendering
- Agresif world rendering paketleri
- Chunk preloading optimization
- Camera unlock system
- Force world visible

#### 🚪 Login Hızlandırma
- Sunucuya giriş bekleme süresi kaldırıldı
- Mojang loading screen bypass
- Anında login process
- Direkt sunucuya bağlantı

#### 📦 ItemsAdder Anlık Yükleme
- Texture pack loading screen yok
- Resource pack anında yüklenir
- ItemsAdder optimizasyonu
- Progress bar bypass

#### 🛑 Mojang Bypass
- Mojang loading screen tamamen atlanır
- Client state force
- Immediate login signal
- Skip all Mojang delays

## Teknik Detaylar

### Çalışma Prensibi
1. **Event Detection**: `PostLoginEvent`, `ServerPreConnectEvent` ve `ServerConnectedEvent` eventleri dinlenir
2. **🚪 Login Optimization**: Oyuncu login olurken immediate bypass
3. **🛑 Mojang Bypass**: Mojang loading screen tamamen atlanır
4. **📦 Resource Pack Instant**: ItemsAdder texture pack anında yüklenir
5. **Loading Screen Removal**: Minecraft client'ına özel paketler gönderilir
6. **🔥 Black Screen Elimination**: Agresif world rendering ve camera unlock
7. **⚡ Ultra Fast Processing**: 1ms gecikme ile immediate world show
8. **🎯 Aggressive Rendering**: Force render, chunk preload, world state force
9. **Smooth Transition**: Experience bar temizleme ve visual feedback
10. **Custom Channels**: `nitscreen:loading` kanalı ile client iletişimi

### Performans
- **Minimal Overhead**: Sadece geçiş anında çalışır
- **Async Processing**: Blocking olmayan işlemler
- **Memory Efficient**: Minimal memory kullanımı
- **Configurable Delays**: Performans ayarları

## Sorun Giderme

### Yaygın Sorunlar

#### Loading Screen Hala Görünüyor
- Konfigürasyonu kontrol edin: `enable-smooth-transition=true`
- Client mod'ları çakışıyor olabilir
- Debug mode açıp logları kontrol edin

#### 🔥 Siyah Ekran Hala Görünüyor
- `enable-ultra-fast-mode=true` yapın
- `enable-aggressive-rendering=true` kontrol edin
- `world-render-delay-ms=5` veya daha düşük değer deneyin
- `world-render-delay-ms=1` yaparak test edin

#### 🚪 Login Bekleme Hala Var
- `enable-login-optimization=true` yapın
- `enable-mojang-bypass=true` kontrol edin
- Debug mode açıp login eventlerini kontrol edin

#### 📦 ItemsAdder Texture Pack Yavaş Yükleniyor
- `enable-resource-pack-optimization=true` yapın
- `resource-pack-delay-ms=1` veya `resource-pack-delay-ms=0` deneyin
- ItemsAdder config'inde `instant-load` ayarını kontrol edin

#### Komutlar Çalışmıyor
- Yetkileri kontrol edin: `nitscreen.use` ve `nitscreen.admin`
- Plugin yüklenmiş mi kontrol edin: `/velocity plugins`

#### Performans Sorunları
- `transition-delay-ms` değerini artırın
- `enable-preloading=false` yapın
- Debug mode'u kapatın

### Debug Mode
```properties
enable-debug-mode=true
```
Bu ayar ile detaylı loglar görüntülenir:
- Oyuncu geçişleri
- Paket gönderim durumları
- Hata mesajları

## Geliştirme

### Proje Yapısı
```
src/main/java/com/nitscreen/
├── NitScreenRemover.java      # Ana plugin sınıfı
├── LoadingScreenHandler.java  # Loading screen yönetimi
├── Configuration.java         # Konfigürasyon yönetimi
└── NitScreenCommand.java      # Komut sistemi
```

### Katkıda Bulunma
1. Fork yapın
2. Feature branch oluşturun
3. Commit yapın
4. Pull request gönderin

## Lisans
MIT License - Detaylar için `LICENSE` dosyasını inceleyin.

## Changelog

### v1.0-SNAPSHOT
- ✨ İlk release
- 🚀 Loading screen kaldırma özelliği
- 🔥 **YENİ**: Siyah ekran tamamen kaldırıldı
- ⚡ **YENİ**: Ultra Fast Mode - 0.05 saniye geçiş
- 🎯 **YENİ**: Aggressive Rendering sistemi
- 💫 **YENİ**: Camera unlock ve world state force
- 🚪 **YENİ**: LOGIN HİZLANDIRMA - Sunucu giriş bekleme süresi kaldırıldı
- 📦 **YENİ**: ITEMSADDER ANLIK YÜKLEME - Texture pack anlık yüklenir
- 🛑 **YENİ**: MOJANG BYPASS - Mojang loading screen atlanır
- ⚡ **YENİ**: ANLIK BAĞLANTI - Tıkladığı gibi sunucuya bağlanır
- ⚙️ Konfigürasyon sistemi
- 💬 Komut sistemi
- 🐛 Debug mode
- 📦 Velocity 3.2.0 desteği

## Destek
- **Issues**: GitHub Issues kullanın
- **Discord**: [Discord Linki]
- **Email**: [Email Adresi]

---

**Made with ❤️ for Minecraft Community** 