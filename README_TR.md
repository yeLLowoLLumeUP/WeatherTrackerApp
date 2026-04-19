# Offline Weather App - Çevrimdışı Hava Durumu Uygulaması

Tamamen çevrimdışı çalışan, React Native ve Expo tabanlı modern bir hava durumu tahmin uygulaması.

## 🌟 Özellikler

### Temel Özellikler
- **Çevrimdışı Çalışma**: İnternet bağlantısı olmadan tamamen çalışır
- **5 Günlük Tahmin**: Detaylı hava durumu tahmini
- **Şehir Arama**: Hızlı şehir arama ve filtreleme
- **Favori Şehirler**: Favori şehirlerinizi kaydedin ve hızlı erişim
- **Birim Dönüştürme**: Celsius/Fahrenheit, km/h/knots seçenekleri
- **Yerel Depolama**: AsyncStorage ile veri cihazda saklanır

### Ekranlar
1. **Ana Sayfa (Home)**
   - Seçili şehrin güncel hava durumu
   - 5 günlük tahmin kartları
   - Diğer şehirleri hızlı görüntüleme
   - Arama ve filtreleme

2. **Favoriler (Favorites)**
   - Kaydedilen favori şehirler
   - Hızlı erişim ve yönetim
   - Favorilerden çıkarma seçeneği

3. **Ayarlar (Settings)**
   - Sıcaklık birimi seçimi (°C / °F)
   - Rüzgar hızı birimi seçimi (km/h / knots)
   - Cache temizleme
   - Favorileri temizleme
   - Uygulama bilgileri

## 📱 Teknoloji Stack

- **React Native 0.81.5**: Mobil uygulama geliştirme
- **Expo 54.0.33**: Geliştirme ve derleme platformu
- **TypeScript**: Tip güvenliği
- **Expo Router**: Navigasyon
- **AsyncStorage**: Yerel veri depolama
- **React Navigation**: Tab navigasyonu

## 📦 Kurulum

### Gereksinimler
- Node.js 18+
- npm veya yarn
- Expo CLI (opsiyonel)

### Adımlar

1. **Proje Klonla**
```bash
cd offline-weather-app
```

2. **Bağımlılıkları Yükle**
```bash
npm install
```

3. **Uygulamayı Başlat**
```bash
# Web'de çalıştır
npm run web

# Android emülatörde çalıştır
npm run android

# iOS simülatörde çalıştır
npm run ios

# Expo Go ile canlı preview
npm start
```

## 🏗️ Proje Yapısı

```
offline-weather-app/
├── app/                          # Uygulama rotaları (Expo Router)
│   ├── (tabs)/                   # Tab navigasyonu
│   │   ├── index.tsx             # Ana sayfa
│   │   ├── favorites.tsx         # Favoriler sayfası
│   │   ├── settings.tsx          # Ayarlar sayfası
│   │   └── _layout.tsx           # Tab layout
│   ├── _layout.tsx               # Root layout
│   └── modal.tsx                 # Modal ekran
├── components/                   # Yeniden kullanılabilir bileşenler
│   ├── WeatherCard.tsx           # Hava durumu kartı
│   ├── ForecastCard.tsx          # Tahmin kartı
│   └── SearchBar.tsx             # Arama çubuğu
├── context/                      # React Context
│   └── WeatherContext.tsx        # Hava durumu context ve provider
├── data/                         # Statik veri
│   └── weatherData.ts            # Offline hava durumu verileri
├── services/                     # İş mantığı servisleri
│   └── weatherService.ts         # Hava durumu servisi
├── constants/                    # Sabitler
├── hooks/                        # Custom React hooks
├── assets/                       # Görseller ve ikonlar
├── package.json                  # Proje konfigürasyonu
├── tsconfig.json                 # TypeScript konfigürasyonu
└── app.json                      # Expo konfigürasyonu
```

## 🔧 Veri Yapısı

### WeatherData Interface
```typescript
interface WeatherData {
  id: string;
  city: string;
  country: string;
  latitude: number;
  longitude: number;
  current: {
    temperature: number;
    feelsLike: number;
    humidity: number;
    windSpeed: number;
    windDirection: string;
    description: string;
    icon: string;
    pressure: number;
    visibility: number;
    uvIndex: number;
  };
  forecast: Array<{
    date: string;
    day: string;
    maxTemp: number;
    minTemp: number;
    description: string;
    icon: string;
    humidity: number;
    windSpeed: number;
    precipitation: number;
  }>;
}
```

## 💾 Yerel Depolama

Uygulama AsyncStorage kullanarak aşağıdaki verileri cihazda saklar:

- **WEATHER_DATA_CACHE**: Hava durumu verileri
- **FAVORITE_CITIES**: Favori şehir ID'leri
- **TEMP_UNIT**: Sıcaklık birimi tercihi
- **SPEED_UNIT**: Rüzgar hızı birimi tercihi

## 📊 Dahil Edilen Şehirler

Uygulama aşağıdaki Türk şehirlerinin verilerini içerir:

1. **İstanbul** - Marmara Bölgesi
2. **Ankara** - İç Anadolu Bölgesi
3. **İzmir** - Ege Bölgesi
4. **Antalya** - Akdeniz Bölgesi
5. **Bursa** - Marmara Bölgesi

Her şehir için:
- Güncel hava durumu
- 5 günlük tahmin
- Sıcaklık, nem, rüzgar, basınç gibi detaylar

## 🎨 Tasarım

- **Modern UI**: Temiz ve kullanıcı dostu arayüz
- **Responsive Design**: Tüm ekran boyutlarına uyum
- **Emoji İkonlar**: Hava durumunu görsel olarak temsil eden emojiler
- **Renk Şeması**: Mavi tonları ile profesyonel görünüm

## 🚀 APK Oluşturma

Android telefonda çalıştırmak için APK dosyası oluşturmak:

```bash
# EAS CLI kurulumu (ilk kez)
npm install -g eas-cli

# EAS konfigürasyonu
eas build --platform android --local

# Veya Expo Go ile test
npm start
# Telefonunuzda Expo Go uygulamasını açıp QR kodu tarayın
```

## 🔐 Çevrimdışı Güvenlik

- Hiçbir veri internete gönderilmez
- Tüm veriler cihazda yerel olarak saklanır
- Gizlilik ve güvenlik garantili

## 📝 Lisans

MIT License - Özgürce kullanabilirsiniz

## 👨‍💻 Geliştirici Notları

### Yeni Şehir Ekleme

`data/weatherData.ts` dosyasında `WEATHER_CITIES` dizisine yeni şehir ekleyin:

```typescript
{
  id: '6',
  city: 'Adana',
  country: 'Turkey',
  latitude: 37.0,
  longitude: 35.3,
  current: { /* ... */ },
  forecast: [ /* ... */ ]
}
```

### Hava Durumu Simgeleri

`WEATHER_ICONS` nesnesi OpenWeatherMap API simgelerini emojilere dönüştürür:

```typescript
export const WEATHER_ICONS: { [key: string]: string } = {
  '01d': '☀️',  // Sunny day
  '02d': '⛅',  // Partly cloudy
  // ...
};
```

## 📞 Destek

Sorular veya sorunlar için GitHub issues açabilirsiniz.

## 🎯 Gelecek Özellikler

- [ ] Harita görünümü
- [ ] Saatlik tahmin
- [ ] Hava uyarıları
- [ ] Tema seçeneği (Koyu/Açık)
- [ ] Daha fazla şehir
- [ ] Saat dilimi desteği
- [ ] Ses bildirimleri
