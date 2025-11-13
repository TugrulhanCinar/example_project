# 🚀 Flutter Proje Yapısı Dokümantasyonu

<div align="center">

![Flutter](https://img.shields.io/badge/Flutter-02569B?style=for-the-badge&logo=flutter&logoColor=white)
![Dart](https://img.shields.io/badge/Dart-0175C2?style=for-the-badge&logo=dart&logoColor=white)
![BLoC](https://img.shields.io/badge/BLoC-6C3483?style=for-the-badge)

**Modern, Ölçeklenebilir ve Bakımı Kolay Flutter Uygulama Mimarisi**

[Özellikler](#-özellikler) • [Yapı](#-proje-yapısı) • [Başlangıç](#-başlangıç) • [Katkıda Bulunma](#-katkıda-bulunma)

</div>

---

## 📋 İçindekiler

- [Özellikler](#-özellikler)
- [Proje Yapısı](#-proje-yapısı)
- [Klasör Detayları](#-klasör-detayları)
- [Başlangıç](#-başlangıç)
- [Best Practices](#-best-practices)
- [Katkıda Bulunma](#-katkıda-bulunma)

---

## ✨ Özellikler

<table>
<tr>
<td>

🎯 **Feature-First Architecture**
> Her özellik bağımsız modül olarak organize edilir

</td>
<td>

🔄 **State Management**
> Bloc/Cubit ile güçlü durum yönetimi

</td>
</tr>
<tr>
<td>

♻️ **Reusable Components**
> Ortak bileşenlerle kod tekrarını önleme

</td>
<td>

🌍 **Localization Ready**
> Çoklu dil desteği altyapısı

</td>
</tr>
<tr>
<td>

🎨 **Theme Management**
> Merkezi tema yönetimi

</td>
<td>

🧪 **Test-Friendly**
> Test edilebilir kod yapısı

</td>
</tr>
</table>

---

## 🏗️ Proje Yapısı

```
lib/
├── 🔧 core/                          # Temel altyapı bileşenleri
│   ├── config/                       # Yapılandırma dosyaları
│   ├── services/                     # API, Storage servisleri
│   ├── utils/                        # Yardımcı fonksiyonlar
│   └── localization/                 # Çoklu dil desteği
│
├── 🎯 features/                      # Özellik modülleri
│   └── home/                         # Örnek: Ana sayfa modülü
│       ├── model/                    # Veri modelleri
│       ├── cubit/                    # Durum yönetimi
│       └── view/                     # UI katmanı
│           └── widget/               # Ekrana özel widget'lar
│
├── 🛠️ product/                       # Ortak bileşenler
│   ├── constants/                    # Sabit değerler
│   │   ├── color_constants.dart
│   │   ├── padding_constants.dart
│   │   └── text_constants.dart
│   │
│   ├── widgets/                      # Ortak UI bileşenleri
│   ├── utils/                        # Genel yardımcılar
│   ├── extensions/                   # Extension metodlar
│   └── theme/                        # Tema yönetimi
│
├── 📱 app.dart                       # MaterialApp yapılandırması
└── 🎬 main.dart                      # Uygulama giriş noktası
```

---

## 📦 Klasör Detayları

### 🔧 `core/` - Temel Altyapı

> Uygulamanın temel altyapı bileşenlerini içerir. Bu klasördeki değişiklikler tüm uygulamayı etkiler.

| Klasör | Açıklama | Örnekler |
|--------|----------|----------|
| `config/` | Uygulama yapılandırmaları | API endpoints, environment variables |
| `services/` | Servis katmanı | API client, Local storage, Cache manager |
| `utils/` | Genel yardımcı fonksiyonlar | Logger, Exception handler |
| `localization/` | Çoklu dil desteği | i18n, l10n dosyaları |

**💡 Ne zaman kullanılır:**
- API entegrasyonu
- Hata yönetimi ve loglama
- Çoklu dil implementasyonu

---

### 🎯 `features/` - Özellik Modülleri

> Her ekran veya ana özellik burada ayrı bir modül olarak organize edilir.

```
features/
└── home/
    ├── model/     # 📊 Veri modelleri (HomeModel, UserModel)
    ├── cubit/     # 🔄 Durum yönetimi (HomeCubit, HomeState)
    └── view/      # 🎨 UI katmanı
        ├── home_view.dart
        └── widget/
            ├── home_header.dart
            └── home_list_item.dart
```

**💡 Yeni Özellik Ekleme:**
```
features/
├── home/       ✅ Mevcut
├── profile/    ➕ Yeni
└── settings/   ➕ Yeni
```

---

### 🛠️ `product/` - Ortak Bileşenler

> Tüm proje genelinde kullanılan ortak bileşenleri içerir.

<details>
<summary><b>📌 constants/</b> - Sabit Değerler</summary>

```dart
// color_constants.dart
class ColorConstants {
  static const Color primary = Color(0xFF6200EE);
  static const Color secondary = Color(0xFF03DAC6);
}

// padding_constants.dart
class PaddingConstants {
  static const double small = 8.0;
  static const double medium = 16.0;
  static const double large = 24.0;
}
```
</details>

<details>
<summary><b>🧩 widgets/</b> - Ortak UI Bileşenleri</summary>

```dart
// custom_button.dart
class CustomButton extends StatelessWidget {
  final String text;
  final VoidCallback onPressed;
  // ...
}
```
</details>

<details>
<summary><b>🔌 extensions/</b> - Extension Metodlar</summary>

```dart
// context_extension.dart
extension ContextExtension on BuildContext {
  double get height => MediaQuery.of(this).size.height;
  double get width => MediaQuery.of(this).size.width;
}
```
</details>

<details>
<summary><b>🎨 theme/</b> - Tema Yönetimi</summary>

```dart
// app_theme.dart
class AppTheme {
  static ThemeData get lightTheme => ThemeData(
    primaryColor: ColorConstants.primary,
    // ...
  );
}
```
</details>

---

## 🚀 Başlangıç

### 📋 Gereksinimler

```bash
Flutter SDK: >=3.0.0
Dart SDK: >=3.0.0
```

### ⚡ Hızlı Başlangıç

```bash
# Projeyi klonla
git clone <repository-url>

# Bağımlılıkları yükle
flutter pub get

# Uygulamayı çalıştır
flutter run
```

---

## 🎓 Yeni Özellik Ekleme Rehberi

### Adım 1️⃣: Feature Klasörü Oluştur

```bash
features/profile/
├── model/
├── cubit/
└── view/
    └── widget/
```

### Adım 2️⃣: Model Oluştur

```dart
// features/profile/model/profile_model.dart
class ProfileModel {
  final String name;
  final String email;
  
  ProfileModel({
    required this.name, 
    required this.email
  });
}
```

### Adım 3️⃣: Cubit ve State Oluştur

```dart
// features/profile/cubit/profile_cubit.dart
class ProfileCubit extends Cubit<ProfileState> {
  ProfileCubit() : super(ProfileInitial());
  
  void loadProfile() async {
    emit(ProfileLoading());
    // Load profile logic
    emit(ProfileLoaded(profile));
  }
}
```

### Adım 4️⃣: View Oluştur

```dart
// features/profile/view/profile_view.dart
class ProfileView extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return BlocProvider(
      create: (context) => ProfileCubit()..loadProfile(),
      child: ProfilePage(),
    );
  }
}
```

### Adım 5️⃣: Routing Ekle

```dart
// app.dart
routes: {
  '/profile': (context) => ProfileView(),
}
```

---

## ✅ Best Practices

### 📌 Genel Kurallar

```
✅ Her feature modülü bağımsız çalışabilmeli
✅ Ortak bileşenler product/ klasöründe tutulmalı
✅ Business logic UI'dan ayrılmalı (Cubit/Bloc)
✅ Extension metodlar kodun okunabilirliğini artırır
✅ Sabit değerler magic number olarak kullanılmamalı
```

### 📌 Naming Conventions

| Tip | Convention | Örnek |
|-----|------------|-------|
| **Dosya** | snake_case | `home_view.dart` |
| **Class** | PascalCase | `HomeView` |
| **Variable** | camelCase | `userName` |
| **Constant** | camelCase | `primaryColor` |

### 📌 Code Organization

```dart
// ❌ Kötü Örnek
Widget build(BuildContext context) {
  return Container(
    padding: EdgeInsets.all(16.0),
    color: Color(0xFF6200EE),
  );
}

// ✅ İyi Örnek
Widget build(BuildContext context) {
  return Container(
    padding: EdgeInsets.all(PaddingConstants.medium),
    color: ColorConstants.primary,
  );
}
```

---

## 📚 Ek Kaynaklar

<div align="center">

| Kaynak | Link |
|--------|------|
| 📖 Flutter Documentation | [flutter.dev/docs](https://flutter.dev/docs) |
| 🔄 Bloc Library | [bloclibrary.dev](https://bloclibrary.dev) |
| 📝 Style Guide | [Flutter Style Guide](https://github.com/flutter/flutter/wiki/Style-guide-for-Flutter-repo) |

</div>

---

## 🤝 Katkıda Bulunma

Katkıda bulunmak için:

1. 🍴 Fork edin
2. 🌿 Feature branch oluşturun (`git checkout -b feature/amazing-feature`)
3. 💾 Commit edin (`git commit -m 'feat: Add amazing feature'`)
4. 📤 Push edin (`git push origin feature/amazing-feature`)
5. 🎉 Pull Request açın

**Yeni özellik eklerken:**
- Feature-first yapısına uygun klasör oluştur
- Ortak bileşenleri `product/` klasöründe tut
- Unit test yaz
- Dokümantasyon ekle

---

## 📄 Lisans

Bu proje [MIT](LICENSE) lisansı altında lisanslanmıştır.

---

<div align="center">

**⭐ Bu projeyi beğendiyseniz yıldız vermeyi unutmayın!**

Made with ❤️ by Flutter Developers

</div>