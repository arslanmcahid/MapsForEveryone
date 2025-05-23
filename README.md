# MapsForEveryone

MapsForEveryone, kullanıcıların harita üzerinde konum paylaşımı yapabildiği, rotalar oluşturabildiği ve diğer kullanıcılarla etkileşime girebildiği bir mobil uygulama projesidir.

## Proje Bileşenleri

### Backend (Spring Boot)

- RESTful API servisleri
- Kullanıcı kimlik doğrulama ve yetkilendirme (JWT)
- Konum ve rota verilerinin yönetimi
- Gerçek zamanlı iletişim için SSE (Server-Sent Events) desteği
- MSSQL veritabanı entegrasyonu
- Google Maps ve Text-to-Speech API entegrasyonu

### Mobil Uygulamalar

- iOS uygulaması (Swift)
- Android uygulaması (Kotlin)
- Harita entegrasyonu
- Konum takibi ve paylaşımı
- Rota oluşturma ve yönetimi
- Kullanıcı profili ve ayarlar

## Özellikler

- 📍 Gerçek zamanlı konum paylaşımı
- 🗺️ Özel rota oluşturma
- 🔔 Konum bazlı bildirimler
- 📱 iOS ve Android platformları için native uygulamalar
- 🔒 Güvenli kullanıcı kimlik doğrulama

## Kurulum

### Backend Kurulumu

```bash
# Projeyi klonlayın
git clone https://github.com/arslanmcahid/MapsForEveryone
cd MapsForEveryone

# Backend klasörüne gidin
cd demo

# Maven ile projeyi derleyin
mvn clean install

# Uygulamayı başlatın
mvn spring-boot:run
```

### Gerekli API Anahtarları

Projeyi çalıştırmak için aşağıdaki API anahtarlarını yapılandırmanız gerekmektedir:

1. Google Maps API Key (Android için)
2. Apple Maps API Key (iOS için)
3. MSSQL Bağlantı Bilgileri
4. Firebase Cloud Messaging (Bildirimler için)

Bu anahtarları ilgili yapılandırma dosyalarında ayarlayın:

- Backend: `application.properties` dosyası
- iOS: `mobile/ios/MapsForEveryone/Config.xcconfig`
- Android: `mobile/android/app/src/main/res/values/secrets.xml`

## Katkıda Bulunma

1. Bu depoyu fork edin
2. Yeni bir özellik dalı oluşturun (`git checkout -b feature/amazing-feature`)
3. Değişikliklerinizi commit edin (`git commit -m 'Add some amazing feature'`)
4. Dalınıza push edin (`git push origin feature/amazing-feature`)
5. Bir Pull Request oluşturun

## Lisans

Bu proje MIT lisansı altında lisanslanmıştır. Detaylar için [LICENSE](LICENSE) dosyasına bakın.

## Güvenlik ve Yapılandırma

### Hassas Bilgilerin Yönetimi

Projede kullanılan hassas bilgiler (API anahtarları, veritabanı kimlik bilgileri vb.) güvenli bir şekilde yönetilmektedir. Bu bilgileri yönetmek için:

1. `application.properties` dosyasını asla doğrudan commit etmeyin
2. Bunun yerine `application-example.properties` dosyasını kullanın
3. Gerçek değerleri şu yöntemlerden biriyle sağlayın:
   - Ortam değişkenleri
   - Docker secrets
   - Kubernetes secrets
   - Azure Key Vault (önerilen)

### Yapılandırma Adımları

1. `application-example.properties` dosyasını `application.properties` olarak kopyalayın:

   ```bash
   cp demo/src/main/resources/application-example.properties demo/src/main/resources/application.properties
   ```

2. `application.properties` dosyasındaki placeholder değerleri gerçek değerlerle değiştirin:

   - Google Maps API Key
   - Google TTS API Key
   - Veritabanı bağlantı bilgileri
   - JWT secret key

3. Geliştirme ortamında test edin:
   ```bash
   ./mvnw spring-boot:run
   ```

### Güvenlik Önerileri

- API anahtarlarını düzenli olarak rotate edin
- Veritabanı şifrelerini güçlü ve benzersiz tutun
- JWT secret key'i yeterince uzun ve karmaşık seçin
- Üretim ortamında hassas bilgileri Azure Key Vault gibi güvenli bir serviste saklayın
