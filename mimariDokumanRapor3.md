# Proje Mimarisi Raporu

**Tarih:** 23 Kasım 2025
**Konu:** Projenin Genel Teknik Yapısı ve Mimarisi Hakkında Bilgilendirme

---

## Yönetici Özeti

Bu rapor, mevcut projenin mimari temelini ve teknolojik altyapısını özetlemektedir. Proje, modern, güvenli ve ölçeklenebilir bir web uygulaması olarak tasarlanmıştır. Mimarisi, birbirinden bağımsız çalışan bir **Kullanıcı Arayüzü (Frontend)** ve bir **Sunucu Uygulamasından (Backend)** oluşmaktadır. Bu yapı, geliştirme süreçlerini hızlandırırken, sistemin uzun vadede sürdürülebilir ve güvenilir kalmasını sağlamaktadır.

---

## 1. Görselleştirilmiş Mimari Modeli (Genel Bakış)

Aşağıdaki şema, sistemin ana bileşenlerini ve aralarındaki etkileşim akışını göstermektedir.

```mermaid
graph TD;
    subgraph "Kullanıcı"
        A[👤 Kullanıcı]
    end

    subgraph "Frontend (Tarayıcı)"
        B[React Uygulaması];
    end

    subgraph "Backend (Sunucu)"
        E[API Servisi];
    end

    subgraph "Veritabanı"
        I[🐘 PostgreSQL];
    end

    A -- "1. Web Sitesini Kullanır" --> B;
    B -- "2. Veri İsteği (API Çağrısı)" --> E;
    E -- "3. Veritabanı İşlemleri" --> I;
    I -- "4. Veri Yanıtı" --> E;
    E -- "5. Veriyi Gönderir (API Yanıtı)" --> B;
    B -- "6. Arayüzü Günceller" --> A;
```

---

## 2. Sunucu Mimarisi ve Akış Diyagramları

Uygulamanın beyni olarak kabul edilebilecek backend, tüm iş mantığını, veri yönetimini ve güvenliği sağlar. Aşağıdaki diyagramlar, backend'in iç yapısını ve işleyişini detaylandırmaktadır.

### 2.1. Backend Paket Akış Diyagramı

Bu diyagram, bir isteğin sunucu içindeki temel katmanlar arasında nasıl bir yol izlediğini özetler.

```mermaid
graph TD;
    A[HTTP İsteği] --> B["api/auth.router.js"];
    B -- "Yönlendirir" --> C["controllers/authController.js"];
    C -- "Çağırır" --> D["services/authService.js"];
    D -- "Çağırır" --> E["repositories/postgresUserRepository.js"];
    E -- "Kullanır ve Sorgular" --> F["models/user.js"];
    E -- "Erişir" --> G[("🐘 Veritabanı")];
```

### 2.2. Detaylı Backend Akış Modeli (Middleware ve Hata Yönetimi ile)

Bu model, bir HTTP isteğinin backend içerisindeki tüm yaşam döngüsünü, ara katmanları ve **tüm hata durumlarını (veritabanı hataları dahil)** içerecek şekilde göstermektedir.

```mermaid
graph TD;
    A[HTTP İsteği] --> MW_Validate[validationMiddleware];

    subgraph "Başarılı Akış"
        MW_Auth[authMiddleware] --> Router[api/ Router];
        Router --> Controller;
        Controller --> Service;
        Service --> Repository;
        Repository --> DB[(Veritabanı)];
        DB --> Repository;
        Repository --> Service;
        Service --> Controller;
        Controller --> Presenter_DTO[Presenter / DTO];
        Presenter_DTO --> SuccessResponse[HTTP 200 OK Yanıtı];
    end

    subgraph "Giriş Kontrolü"
        MW_Validate -- "Başarılı" --> MW_Auth;
    end
    
    subgraph "Hata Yönetimi"
        ErrorHandler[errorHandler.js] --> ErrorResponse[HTTP 4xx/5xx Hata Yanıtı];
        MW_Validate -- "Validasyon Hatası" --> ErrorHandler;
        MW_Auth -- "Yetki Hatası" --> ErrorHandler;
        Service -- "İş Mantığı Hatası" --> ErrorHandler;
        Controller -- "İstek Hatası" --> ErrorHandler;
        Repository -- "Veritabanı Hatası" --> ErrorHandler;
    end
```

---

## Genel Değerlendirme

Proje, güncel teknolojilerle ve en iyi endüstri pratiklerine uygun olarak geliştirilmiştir. Sahip olduğu modüler ve düzenli mimari sayesinde gelecekteki yeni özelliklerin kolayca eklenmesine ve sistemin büyütülmesine olanak tanır. Bu yapı, projenin uzun vadede istikrarlı ve sürdürülebilir olmasını güvence altına almaktadır.
