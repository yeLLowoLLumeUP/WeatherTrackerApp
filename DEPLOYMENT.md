# Offline Weather App - Dağıtım Kılavuzu

Bu kılavuz, uygulamayı Android telefonunuzda çalıştırmak için gerekli adımları açıklamaktadır.

## 📱 Android Telefonda Çalıştırma Seçenekleri

### Seçenek 1: Expo Go ile Hızlı Test (Önerilen - Geliştirme)

En hızlı ve kolay yöntem. İnternet bağlantısı gerektirir.

#### Adımlar:

1. **Telefonunuza Expo Go Yükleyin**
   - Google Play Store'dan "Expo Go" uygulamasını indirin
   - iOS için App Store'dan indirin

2. **Bilgisayarda Uygulamayı Başlatın**
   ```bash
   cd offline-weather-app
   npm start
   ```

3. **QR Kodu Tarayın**
   - Terminal'de gösterilen QR kodu Expo Go ile tarayın
   - Uygulama otomatik olarak telefonunuzda açılacak

4. **Test Edin**
   - Tüm özellikleri test edin
   - Çevrimdışı modda çalıştığını doğrulayın

### Seçenek 2: APK Dosyası Oluşturma (Önerilen - Dağıtım)

Kalıcı kurulum için APK dosyası oluşturun. İnternet bağlantısı gerektirir.

#### Gereksinimler:

- EAS CLI kurulu
- Expo hesabı (ücretsiz)
- İnternet bağlantısı

#### Adımlar:

1. **EAS CLI Kurulumu**
   ```bash
   npm install -g eas-cli
   ```

2. **Expo Hesabına Giriş Yapın**
   ```bash
   eas login
   ```
   - Tarayıcıda açılacak sayfada hesap oluşturun veya giriş yapın

3. **EAS Konfigürasyonu**
   ```bash
   cd offline-weather-app
   eas build --platform android --local
   ```

4. **Derleme Başlat**
   - İlk kez çalıştırıldığında EAS konfigürasyonu yapılacak
   - "Create a new Android app" seçeneğini seçin
   - Derleme başlayacak (5-15 dakika sürebilir)

5. **APK İndirin**
   - Derleme tamamlandığında indirme bağlantısı verilecek
   - APK dosyasını telefonunuza aktarın

6. **Telefonunuza Kurun**
   - Dosya yöneticisinden APK dosyasını açın
   - "Yükle" düğmesine tıklayın
   - Kurulum tamamlanacak

### Seçenek 3: Android Studio Emülatörü (Geliştirme)

Bilgisayarınızda sanal telefon üzerinde test edin.

#### Gereksinimler:

- Android Studio kurulu
- Android SDK kurulu

#### Adımlar:

1. **Android Studio'yu Açın**
   - Android Studio'yu başlatın
   - Virtual Device Manager'ı açın

2. **Sanal Cihaz Oluşturun (İlk Kez)**
   - "Create Virtual Device" seçeneğini tıklayın
   - Telefon modeli seçin (Pixel 4 önerilen)
   - Android sürümü seçin (API 30+)
   - "Finish" tıklayın

3. **Emülatörü Başlatın**
   - Sanal cihazı seçin
   - "Play" düğmesine tıklayın
   - Emülatör açılacak (ilk kez 1-2 dakika sürebilir)

4. **Uygulamayı Çalıştırın**
   ```bash
   cd offline-weather-app
   npm run android
   ```
   - Uygulama otomatik olarak emülatörde açılacak

## 🔧 Sorun Giderme

### APK Oluşturmada Hata

**Hata**: "No credentials available"
```bash
# Çözüm: Expo hesabına giriş yapın
eas login
```

**Hata**: "Build failed"
```bash
# Çözüm: Bağımlılıkları temizle ve yeniden yükle
rm -rf node_modules package-lock.json
npm install
```

### Emülatörde Açılmıyor

**Hata**: "Unable to connect to emulator"
```bash
# Çözüm: Emülatörü yeniden başlatın
adb kill-server
adb start-server
```

### Telefonunuzda Kurulmuyor

**Hata**: "Installation failed"
- Telefonunuzda bilinmeyen kaynaklar seçeneğini etkinleştirin
- Ayarlar > Güvenlik > Bilinmeyen Kaynaklar
- APK dosyasını tekrar açmayı deneyin

## 📊 Sistem Gereksinimleri

### Minimum Gereksinimler
- **Android**: 5.0+ (API 21+)
- **RAM**: 100 MB
- **Depolama**: 50 MB

### Önerilen Gereksinimler
- **Android**: 8.0+ (API 26+)
- **RAM**: 2 GB+
- **Depolama**: 100 MB+

## 🌐 Çevrimdışı Çalışma

Uygulama tamamen çevrimdışı çalışır:

1. **İlk Kurulum**
   - Uygulamayı ilk açtığınızda tüm veriler cihazda kaydedilir
   - İnternet bağlantısı gerekli değildir

2. **Veri Depolama**
   - Tüm hava durumu verileri AsyncStorage'da saklanır
   - Favori şehirler cihazda kaydedilir
   - Ayarlar yerel olarak saklanır

3. **Çevrimdışı Modda Kullanım**
   - İnternet olmadan tüm özellikleri kullanabilirsiniz
   - Veriler güncellenmez (statik veri seti)
   - Hiçbir veri internete gönderilmez

## 📝 Uygulamayı Kaldırma

### Expo Go'dan Kaldırma
- Expo Go uygulamasını açın
- Offline Weather App'i bulun
- "Kaldır" seçeneğini tıklayın

### APK'dan Kaldırma
- Ayarlar > Uygulamalar
- Offline Weather App'i bulun
- "Kaldır" tıklayın

## 🚀 Gelişmiş Dağıtım

### Google Play Store'a Yayınlama

1. **Google Play Developer Hesabı Oluşturun**
   - https://play.google.com/console adresine gidin
   - Hesap oluşturun (25 USD ödeme gerekir)

2. **Uygulama Bilgilerini Hazırlayın**
   - Uygulama adı
   - Açıklama
   - Ekran görüntüleri (minimum 2)
   - Simge (512x512 PNG)

3. **APK Hazırlayın**
   ```bash
   eas build --platform android --release
   ```

4. **Play Store'a Yükleyin**
   - Google Play Console'da yeni uygulama oluşturun
   - APK dosyasını yükleyin
   - Bilgileri doldurun
   - Gözden geçirme için gönderin

## 📞 Destek

Sorunlar için:
- GitHub Issues: Teknik sorunlar
- Email: Genel sorular

## ✅ Kontrol Listesi

Dağıtımdan önce kontrol edin:

- [ ] Tüm özellikler test edildi
- [ ] Çevrimdışı modda çalışıyor
- [ ] Lint kontrolleri geçti
- [ ] APK dosyası oluşturuldu
- [ ] Telefonunuzda kuruldu
- [ ] Tüm ekranlar çalışıyor
- [ ] Favoriler kaydediliyor
- [ ] Ayarlar kaydediliyor

## 🎉 Tamamlandı!

Uygulamanız artık Android telefonunuzda çalışmaya hazır!

Sorularınız varsa, GitHub issues açabilirsiniz.
