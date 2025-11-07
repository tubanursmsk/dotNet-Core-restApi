# 🌐 Kuaför Randevu Sistemi - .NET Core API

> **dotNet-Core-restApi**, .NET Core 9 Web API kullanılarak geliştirilmiş modern bir kuaför ve güzellik salonu randevu takip sistemidir.
Sistem, kullanıcı kaydı, kimlik doğrulama, hizmet listeleme ve gelişmiş randevu oluşturma özelliklerini içerir.
Uygulama güvenliği **JWT tabanlı kimlik doğrulama** sistemiyle sağlanır.


## 🚀 Temel Özellikler
- Kullanıcı Yönetimi: Kullanıcı kaydı (Register) ve girişi (Login).
- Güvenlik: JWT (JSON Web Token) tabanlı kimlik doğrulama ve yetkilendirme (Authorization).
- Randevu Yönetimi: Yeni randevu oluşturma (POST /api/appointment/add).
- Akıllı Randevu Önerisi: İstenen bir saat doluysa, sistem otomatik olarak en yakın 5 uygun alternatif saati (suggestedSlots) bularak kullanıcıya önerir.
- Hizmet Yönetimi: Salonda sunulan hizmetlerin listelenmesi (GET /api/service/all).
- Veritabanı: Veritabanı işlemleri için Entity Framework Core ve SQLite kullanılmıştır.


---


## 🛠️ Kullanılan Teknolojiler ve Mimari
Bu proje, modern .NET API geliştirme prensipleri ve katmanlı bir mimari yaklaşımıyla oluşturulmuştur.

- Framework: .NET Core 9 (Web API)
- Veritabanı: Entity Framework Core & SQLite
- 🔐 Kimlik Doğrulama: JWT (JSON Web Tokens)

  ### 🧠Mimari:
- 🔄 Controllers (Garson): API endpoint'lerini tanımlar, HTTP isteklerini karşılar ve Service katmanına yönlendirir.
  
- 💻 Services (Aşçı): Tüm iş mantığının (business logic) yaşadığı yerdir (örn: randevu çakışma kontrolü, öneri motoru).
  
- 🧰 Models (Entity): Veritabanı tablolarını temsil eden C# sınıfları (örn: User.cs, Appointment.cs).
  
- 📁 DTOs (Data Transfer Objects): API ve dış dünya arasındaki veri sözleşmelerini tanımlar.
  
- ✨ AutoMapper: Model ve DTO nesneleri arasındaki veri kopyalama işlemlerini otomatikleştirir.
  
- 🧩 API Dokümantasyonu: Swagger (OpenAPI) entegrasyonu ile tüm endpoint'ler belgelenmiştir.
  
- ⚙️ Hata Yönetimi: GlobalExceptionHandler middleware'i ile merkezi hata yakalama.

---

## 🏁 Projeyi Başlatma

### 1️⃣ Projeyi Klonlayın:
```bash
git clone https://github.com/tubanursmsk/dotNet-Core-restApi.git
```

### 2️⃣ Bağımlılıkları yükle
```bash
dotnet restore
```

### 3️⃣ Veritabanını Oluşturun
```bash
dotnet ef database update
```

### 4️⃣ Bu komut, proje ana dizininde restApi.db adlı SQLite veritabanını oluşturur.

### 5️⃣ Uygulamayı Çalıştırın
```bash
dotnet run
```

---

## 👥 Örnek Kullanıcı Hesapları

| Rol    | Email                                   | Şifre        |
| ------ | --------------------------------------- | ------------ |
| User   | [ali@mail.com](mailto:ali@mail.com)     | Password1234 |

---

## 📖 API Kullanımı
Projeyi çalıştırdıktan sonra Swagger arayüzüne giderek tüm endpoint'leri test edebilirsiniz:
```bash
Swagger UI Adresi: https://localhost:5223/swagger
```

---

##  Ana Endpoint'ler
### POST /api/user/register
- Yeni bir kullanıcı (müşteri veya personel) kaydı oluşturur.
  
<img width="960" height="517" alt="image" src="https://github.com/user-attachments/assets/b971c8b4-8b6b-4b41-8bdd-d10fabc0f336" />

---

### POST /api/user/login
- Başarılı giriş sonrası bir JWT token döndürür.
  
  <img width="960" height="517" alt="image" src="https://github.com/user-attachments/assets/27c818e5-842a-45d6-b4f6-33fb2808aa23" />

---

### POST /api/Service/add
- Staff rolü ile servis ekleme
  
<img width="960" height="517" alt="image" src="https://github.com/user-attachments/assets/96366e36-923a-43a0-a8a5-bc25a62f7a51" />

---

### GET /api/Service/all

<img width="960" height="517" alt="image" src="https://github.com/user-attachments/assets/c513b49b-28f6-4851-8822-c0369b14a12d" />

---

### POST /api/appointment/add [Authorize]
- Giriş yapmış (token sahibi) kullanıcının yeni bir randevu almasını sağlar.
  
<img width="683" height="369" alt="appointmentAdd" src="https://github.com/user-attachments/assets/e8a76eca-1ed4-45f6-af01-d57d2eda76a8" />

- Randevu saatlerinde çakışma
  
<img width="683" height="369" alt="randevu çakışması" src="https://github.com/user-attachments/assets/16c40ca6-9f79-4d5d-9035-5dea25bfc8e9" />

- Müşterinin istediği saatler doluysa en uygun beş randevu önerisi sunar.

 <img width="683" height="369" alt="İstediğiniz saat dolu  Alternatif saatler önersi" src="https://github.com/user-attachments/assets/521519eb-5642-4c1d-a421-177c8b1ab7cc" />

---

### 📸 DataBase  Görselleri
<img width="683" height="369" alt="image" src="https://github.com/user-attachments/assets/bd3ee098-f87a-4cfb-87a0-2265b58ee474" />

<img width="683" height="369" alt="servicesdb" src="https://github.com/user-attachments/assets/3e759122-ae0f-41ac-88cb-e497b437e028" />

<img width="683" height="369" alt="usedb" src="https://github.com/user-attachments/assets/abf82d3f-af3e-411c-881c-e3b7a7777be0" />

---

### 🧱 Lisans

MIT Lisansı © 2025 — [tubanursmsk](https://github.com/tubanursmsk)

---

### 🏷️ Etiketler

`Node.js` `ASP.NET Core` `TypeScript` `SQLLite` `DTO` `JWT` `bcrypt` `swagger`  
`Katmanlı Mimari` `MVC` `REST API` `RBAC` `Session Management`  
 `kuaför` `Randevu Takip Sistemi`  `Backend Development` `API Documentation`
 `Full Stack` `hairdresser` `Barber` `hairstylist` `salon`
