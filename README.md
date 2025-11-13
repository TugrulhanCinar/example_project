# 🏗️ Flutter Project Structure & Roadmap

Bu proje, **Clean Architecture** ve **MVVM (Model–View–ViewModel)** prensiplerine göre yapılandırılmıştır.  
Amaç, kodun **okunabilir**, **test edilebilir** ve **ölçeklenebilir** olmasını sağlamaktır.

---

## 📂 Project Tree

```
lib/
├── core/                          # Uygulamanın temel altyapı bileşenleri
│   ├── config/                    # Genel yapılandırma dosyaları
│   ├── services/                  # Servisler (API, local storage vb.)
│   ├── utils/                     # Genel yardımcı fonksiyonlar
│   └── localization/              # Çoklu dil desteği (çeviri dosyaları)
│
├── features/                      # Her ekran veya modül burada tanımlanır
│   └── home/                      # Örnek modül: Ana sayfa
│       ├── model/                 # Home ekranına özel veri modelleri
│       ├── cubit/                 # Durum yönetimi (Cubit veya Bloc)
│       └── view/                  # UI katmanı
│           └── widget/            # Home ekranına özel bileşenler
│
├── product/                       # Ortak kullanılan proje bileşenleri
│   ├── constants/                 # Sabit değerler
│   │   ├── color_constants.dart   # Renk paleti
│   │   ├── padding_constants.dart # Boşluk ve margin sabitleri
│   │   └── text_constants.dart    # Yazı tipleri ve metin sabitleri
│   │
│   ├── widgets/                   # Ortak kullanılan UI bileşenleri
│   │   ├── custom_button.dart
│   │   └── loading_indicator.dart
│   │
│   ├── utils/                     # Genel yardımcı fonksiyonlar
│   │   ├── validators.dart        # Form doğrulama fonksiyonları
│   │   └── date_formatter.dart    # Tarih formatlama yardımcıları
│   │
│   ├── extensions/                # Extension metodlar
│   │   ├── context_extension.dart # BuildContext yardımcıları
│   │   └── string_extension.dart  # String işlemleri yardımcıları
│   │
│   └── theme/                     # Tema yönetimi
│       ├── app_theme.dart         # Tema yapılandırması
│       └── light_theme.dart       # Aydınlık tema ayarları
│
├── app.dart                       # MaterialApp ve genel yapılandırma
└── main.dart                      # Uygulama giriş noktası

```

---

## 🧭 Development Roadmap

### 1️⃣ Core Katmanını Oluştur
- **constants/** → Renk paleti, tipografi, spacing değerleri.
- **utils/** → StringFormatter, DateHelper gibi yardımcı sınıflar.
- **network/** → Dio base setup + Interceptor.

### 2️⃣ Data Katmanını Kur
- API’den veri çekmek için **datasource** oluştur.
- JSON parsing için **model** ve **dto** dosyalarını yaz.
- Veriyi domain’e aktarmak için **repository implementation** oluştur.

### 3️⃣ Domain Katmanını Geliştir
- **entities/**: İş kurallarına uygun sade modeller.
- **repositories/**: Interface (örnek: `abstract class UserRepository`).
- **usecases/**: Tek bir işi yapan sınıflar (örnek: `GetUserProfile`).

### 4️⃣ Presentation Katmanı
- Her ekran için ayrı klasör: `presentation/screens/[screen_name]/`
- Ekran + ViewModel + Widgets olarak 3’e böl.
- `homepage.dart` → `presentation/screens/home/homepage.dart`
- State yönetimi: **Provider**, **Riverpod** veya **MobX** (tercihe göre).

### 5️⃣ Config Katmanı
- Uygulama rotalarını (`config/routes/`) düzenle.
- Dependency Injection setup (örnek: `GetIt.instance.registerLazySingleton()`).
- Tema ve environment yapılarını oluştur.

---

## 💡 Best Practices

- ViewModel içinde **iş mantığı**, Widget içinde **UI mantığı** olsun.
- Repository interface’leri domain katmanında, implementasyonları data katmanında olsun.
- Her şey test edilebilir olmalı: UseCase, Repository, ViewModel.
- Ortak componentleri `core/widgets` içinde tut.
- Ekran bazlı özel componentleri `presentation/screens/.../widgets` içine koy.

---

## 🚀 Hedef

Bu yapı sayesinde:
- Kod **temiz ve sürdürülebilir** kalır.
- Yeni bir özellik eklemek için yalnızca ilgili katmanda çalışırsın.
- Büyük ölçekli Flutter projelerinde **profesyonel mimari** sağlar.

---

> 📘 Not: Bu `README` proje boyunca **ana rehber** olarak kullanılmalıdır.  
> Yeni ekranlar, modüller veya servisler eklenirken bu yapıya sadık kal.