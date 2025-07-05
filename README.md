[//]: # (Language Switcher)
<p align="right">
  <b>Language / Dil:</b>
  <a href="#english">English</a> |
  <a href="#turkce">Türkçe</a>
</p>

---

<a name="english"></a>
# NitScreenRemover - Velocity Plugin

## Description
NitScreenRemover is an advanced plugin for Velocity proxy servers that **REMOVES ALL LOADING SCREENS**. It completely bypasses server switching, login waiting, ItemsAdder texture pack loading, and Mojang loading screens. Players connect **INSTANTLY** to the server and see no loading screens!

## Features

### 🚀 Main Features
- **Loading Screen Removal**: Instantly removes loading screens during server switches
- **🔥 Black Screen Removal**: Completely removes the 1-second black screen
- **⚡ Ultra Fast Mode**: Maximum speed switching, instant world rendering
- **🎯 Aggressive Rendering**: Aggressive world rendering and chunk preloading
- **🚪 LOGIN ACCELERATION**: Removes login waiting time
- **📦 INSTANT ITEMSADDER LOADING**: Texture pack loads instantly, no loading screen
- **🛑 MOJANG BYPASS**: Completely bypasses Mojang loading screen
- **⚡ Instant Connection**: Connects directly to the server as soon as clicked
- **Smooth Transition**: Better UX with smooth transition effects
- **Server Preloading**: Preloads servers in advance
- **Custom Messages**: Customizable transition messages
- **Debug Mode**: Advanced debugging and logging

### ⚙️ Configuration
- **Reloadable**: Change settings without restarting the server
- **Flexible Settings**: Enable/disable each feature individually
- **Performance Tuning**: Adjustable delay times

## Installation

### Requirements
- **Velocity**: 3.2.0 or higher
- **Java**: 11 or higher
- **Maven**: 3.6.0 or higher (for building)

### Steps
1. **Build**:
   ```bash
   mvn clean package
   ```
2. **Install**:
   - Copy `target/nitscreen-remover-1.0-SNAPSHOT.jar` to Velocity's `plugins` folder
   - Restart Velocity
3. **Configure**:
   - `plugins/nitscreen-remover/config.properties` will be created automatically
   - Adjust settings as needed

## Usage

### Commands
| Command | Description | Permission |
|---------|-------------|------------|
| `/nitscreen help` | Help menu | `nitscreen.use` |
| `/nitscreen status` | Plugin status | `nitscreen.use` |
| `/nitscreen reload` | Reload configuration | `nitscreen.admin` |
| `/nitscreen toggle <feature>` | Toggle feature | `nitscreen.admin` |
| `/nitscreen test` | Loading screen test | `nitscreen.admin` |

### Shortcuts
- `/nsr` - Shortcut for `/nitscreen`

### Permissions
```yaml
permissions:
  nitscreen.use: true      # Basic commands
  nitscreen.admin: false   # Admin commands
```

## Configuration

### config.properties
```properties
# Smooth transition feature
enable-smooth-transition=true
# Server preloading feature
enable-preloading=true
# Custom messages
enable-custom-messages=true
# Transition delay (ms)
transition-delay-ms=50
# Message cleanup delay (ms)
message-cleanup-delay-ms=2000
# Debug mode
enable-debug-mode=false
# 🔥 BLACK SCREEN REMOVAL - Ultra Fast Mode
enable-ultra-fast-mode=true
# 🎯 Aggressive world rendering
enable-aggressive-rendering=true
# World render delay (ms) - Lower = Faster
world-render-delay-ms=5
# 🚪 LOGIN ACCELERATION - Remove login waiting
enable-login-optimization=true
# 📦 ITEMSADDER TEXTURE PACK - Instant loading
enable-resource-pack-optimization=true
# Resource pack loading delay (ms) - 0 = Instant
resource-pack-delay-ms=1
# 🛑 MOJANG LOADING SCREEN BYPASS - Skip Mojang screen
enable-mojang-bypass=true
```

### Feature Descriptions

#### 🎯 Smooth Transition
- Makes server switches smooth
- Prevents abrupt interruptions
- Improves player experience

#### ⚡ Preloading
- Preloads servers in advance
- Reduces transition time
- Performance optimization

#### 💬 Custom Messages
- Customizable transition messages
- Visual feedback system
- Player notification

#### 🐛 Debug Mode
- Detailed logging
- Debugging information
- Advanced monitoring

#### 🔥 Ultra Fast Mode
- Maximum speed server switching
- Black screen completely removed
- 1 second > 0.05 second transition
- Instant world rendering

#### 🎯 Aggressive Rendering
- Aggressive world rendering packages
- Chunk preloading optimization
- Camera unlock system
- Force world visible

#### 🚪 Login Acceleration
- Login waiting time removed
- Mojang loading screen bypass
- Instant login process
- Direct server connection

#### 📦 Instant ItemsAdder Loading
- No texture pack loading screen
- Resource pack loads instantly
- ItemsAdder optimization
- Progress bar bypass

#### 🛑 Mojang Bypass
- Mojang loading screen completely skipped
- Client state force
- Immediate login signal
- Skip all Mojang delays

## Technical Details

### How It Works
1. **Event Detection**: Listens to `PostLoginEvent`, `ServerPreConnectEvent`, and `ServerConnectedEvent`
2. **🚪 Login Optimization**: Immediate bypass during player login
3. **🛑 Mojang Bypass**: Completely skips Mojang loading screen
4. **📦 Resource Pack Instant**: ItemsAdder texture pack loads instantly
5. **Loading Screen Removal**: Sends special packets to Minecraft client
6. **🔥 Black Screen Elimination**: Aggressive world rendering and camera unlock
7. **⚡ Ultra Fast Processing**: Immediate world show with 1ms delay
8. **🎯 Aggressive Rendering**: Force render, chunk preload, world state force
9. **Smooth Transition**: Cleans experience bar and visual feedback
10. **Custom Channels**: Communication with client via `nitscreen:loading` channel

### Performance
- **Minimal Overhead**: Only works during transitions
- **Async Processing**: Non-blocking operations
- **Memory Efficient**: Minimal memory usage
- **Configurable Delays**: Performance settings

## Troubleshooting

### Common Issues

#### Loading Screen Still Appears
- Check config: `enable-smooth-transition=true`
- Client mods may conflict
- Enable debug mode and check logs

#### 🔥 Black Screen Still Appears
- Set `enable-ultra-fast-mode=true`
- Check `enable-aggressive-rendering=true`
- Try `world-render-delay-ms=5` or lower
- Test with `world-render-delay-ms=1`

#### 🚪 Login Waiting Still Exists
- Set `enable-login-optimization=true`
- Check `enable-mojang-bypass=true`
- Enable debug mode and check login events

#### 📦 ItemsAdder Texture Pack Loads Slowly
- Set `enable-resource-pack-optimization=true`
- Try `resource-pack-delay-ms=1` or `resource-pack-delay-ms=0`
- Check `instant-load` setting in ItemsAdder config

#### Commands Not Working
- Check permissions: `nitscreen.use` and `nitscreen.admin`
- Make sure plugin is loaded: `/velocity plugins`

#### Performance Issues
- Increase `transition-delay-ms`
- Set `enable-preloading=false`
- Disable debug mode

### Debug Mode
```properties
enable-debug-mode=true
```
This setting enables detailed logs:
- Player transitions
- Packet sending status
- Error messages

## Development

### Project Structure
```
src/main/java/com/nitscreen/
├── NitScreenRemover.java      # Main plugin class
├── LoadingScreenHandler.java  # Loading screen management
├── Configuration.java         # Configuration management
└── NitScreenCommand.java      # Command system
```

### Contributing
1. Fork the repo
2. Create a feature branch
3. Commit your changes
4. Submit a pull request

## License
MIT License - See `LICENSE` file for details.

## Changelog

### v1.0-SNAPSHOT
- ✨ First release
- 🚀 Loading screen removal feature
- 🔥 **NEW**: Black screen completely removed
- ⚡ **NEW**: Ultra Fast Mode - 0.05s transition
- 🎯 **NEW**: Aggressive Rendering system
- 💫 **NEW**: Camera unlock and world state force
- 🚪 **NEW**: LOGIN ACCELERATION - Login waiting removed
- 📦 **NEW**: INSTANT ITEMSADDER LOADING
- 🛑 **NEW**: MOJANG BYPASS
- ⚡ **NEW**: INSTANT CONNECTION
- ⚙️ Configuration system
- 💬 Command system
- 🐛 Debug mode
- 📦 Velocity 3.2.0 support

## Support
- **Issues**: Use GitHub Issues
- **Discord**: [Discord Link]
- **Email**: [Email Address]

---

<a name="turkce"></a>
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