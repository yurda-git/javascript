# Proje Mimarisi ve Geliştirme Raporu - 21.11.2025

## 1. Proje Özeti

Bu rapor, mevcut web uygulamasının teknik yapısı, kullanılan teknolojiler ve genel yetenekleri hakkında bilgi sunmaktadır. Proje, güvenli bir kullanıcı kayıt ve giriş altyapısı sunan modern bir web uygulamasıdır. Proje kök dizininde mimari, isimlendirme standartları ve gereksinimler gibi konularda oldukça detaylı dokümantasyon dosyaları bulunmaktadır. Bu durum, projenin planlı ve düzenli bir şekilde geliştirildiğini göstermektedir.

## 2. Teknik Yapı

Uygulama, birbirinden bağımsız olarak geliştirilebilen ve ölçeklendirilebilen **Backend** (sunucu tarafı) ve **Frontend** (istemci tarafı) olmak üzere iki ana bileşenden oluşmaktadır.

### 2.1. Backend Mimarisi

*   **Teknoloji:** Sunucu tarafı, Node.js çalışma zamanı ortamı ve Express.js web çatısı kullanılarak geliştirilmiştir.
*   **Mimari Yaklaşım:** Sürdürülebilir ve bakımı kolay, katmanlı ((Layered Architecture)) bir mimari benimsenmiştir. 

      **API Katmanı:** Dış dünyadan gelen HTTP isteklerinin ilk temas noktasıdır
      **Controller Katmanı:**İstemci isteklerini karşılayarak, isteği işlenmek üzere ilgili iş mantığı katmanına iletir. İşlem sonucunu istemciye standart bir HTTP yanıtı olarak formatlar.
      **Service Katmanı:**Uygulamanın çekirdek iş mantığını barındırır.
       **Repository Katmanı:** Veritabanı işlemleri, esneklik sağlayan **Repository Tasarım Deseni** ile yönetilmektedir. iş mantığı katmanının farklı veritabanı sistemleriyle (örneğin, PostgreSQL veya MongoDB) minimum değişiklikle çalışabilmesine olanak tanır ve kodun esnekliğini artırır Son geliştirmeler ile MongoDB desteği kaldırılmıştır.  Mevcut durumda yalnızca **PostgreSQL** veritabanı kullanılmaktadır.
      
      Bağımlılık yönetimi, kodun modülerliğini artıran bir DI (Dependency Injection) container'ı ile sağlanmaktadır. Bu, bileşenler arasındaki sıkı bağımlılığı (tight coupling) azaltır.
      
     
      
*   **Kod Kalitesi ve Araçlar:** Kod kalitesini sağlamak için ESLint, test süreçleri için Jest ve geliştirme ortamında verimliliği artırmak için Nodemon gibi endüstri standardı araçlar kullanılmaktadır.

### 2.2. Frontend Mimarisi
Frontend uygulaması, modern bir kullanıcı arayüzü oluşturmak için Vite üzerinde çalışan bir React uygulamasıdır.

*   **Teknoloji:** İstemci tarafı, popüler JavaScript kütüphanesi olan React ile geliştirilmiştir. Projenin derlenmesi ve geliştirme sunucusu için hızlı bir deneyim sunan Vite aracı tercih edilmiştir.
*   **Mimari Yaklaşım:** Kullanıcı arayüzü, yeniden kullanılabilir bileşenlerden (components) oluşmaktadır. Kullanıcı oturum yönetimi gibi global durumlar React Context API ile yönetilmekte, yetkilendirme kontrolleri ise korumalı rotalar (Protected Routes) aracılığıyla güvenli bir şekilde yapılmaktadır.
*   **Stil ve Arayüz:** Proje genelinde standart bir görünüm sağlamak amacıyla arayüz geliştirme kütüphanesi olarak **Bootstrap** kullanılmaktadır.

## 3. Yapılan Son İyileştirme Çalışmaları

Projenin bakımını kolaylaştırmak ve teknoloji yığınını sadeleştirmek amacıyla aşağıdaki önemli değişiklikler yapılmıştır:

1.  **Veritabanı Desteğinin Sadeleştirilmesi:** Daha önce mevcut olan MongoDB desteği kaldırılmıştır. Proje artık yalnızca PostgreSQL veritabanını desteklemektedir.
2.  **Arayüz Kütüphanesinin Standartlaştırılması:** Frontend tarafında standartlaşmayı sağlamak ve bakım maliyetini düşürmek amacıyla Material-UI (MUI) kütüphanesi kaldırılmış ve arayüz tamamen Bootstrap kullanılarak yeniden yapılandırılmıştır.

## 4. Genel Değerlendirme ve Sonuç

Mevcut durum itibarıyla proje, temel hedeflerini başarıyla karşılayan fonksiyonel bir yapıya sahiptir. Uygulama, aşağıdaki temel yetenekleri sunmaktadır:

*   **Güvenli Kullanım:** Uygulama, kullanıcı verilerinin korunmasına yönelik temel güvenlik prensipleriyle tasarlanmıştır.
*   **Modern ve Esnek Mimari:** Hem backend hem de frontend tarafında benimsenen katmanlı ve bileşen tabanlı mimariler, projenin gelecekte yeni özelliklerle genişletilmesini kolaylaştırmaktadır.
*   **Standartlaştırılmış Arayüz:** Bootstrap kullanımı, tüm platformlarda tutarlı ve responsive (cihaz uyumlu) bir kullanıcı deneyimi sağlamaktadır.

Sonuç olarak, proje sağlam bir temel üzerine inşa edilmiş olup, yeni fonksiyonellikler eklenmesi için hazır durumdadır. Mevcut yapı, projenin kararlı, güvenli ve sürdürülebilir bir şekilde geliştirilmesine olanak tanımaktadır.

## 5. Mimari Şemalar (Mermaid)

Aşağıdaki metin tabanlı diyagramlar, bu dokümanda açıklanan mimari yapıyı görselleştirmektedir. Diyagramlar, GitHub üzerinde veya Mermaid destekli bir görüntüleyicide otomatik olarak şemaya dönüşecektir.

### 5.1. Genel Sistem Mimarisi

Bu şema, istemci ile sunucu arasındaki genel etkileşimi ve ana teknoloji bileşenlerini göstermektedir.

```mermaid
graph TD
    classDef frontend fill:#E6F3FF,stroke:#007BFF,stroke-width:2px;
    classDef backend fill:#E8F5E9,stroke:#28A745,stroke-width:2px;

    subgraph "İstemci Tarafı (Browser)"
        direction LR
        User[fa:fa-user Kullanıcı] --> FE(React Frontend<br/>(Bootstrap))
    end

    subgraph "Sunucu Tarafı (Node.js)"
        direction TB
        BE(Backend API<br/>(Express.js))
    end

    FE -- "HTTP/S Çağrıları" --> BE

    class User,FE frontend;
    class BE backend;
```

### 5.2. Backend Katmanlı Mimarisi

Bu şema, backend uygulamasının iç katmanlarını, bir isteğin bu katmanlar arasındaki akışını ve her katmanın sorumluluğunu renk kodlaması ile detaylandırmaktadır.

```mermaid
graph TD
    classDef entrypoint fill:#f9f9f9,stroke:#333,stroke-width:2px;
    classDef controller fill:#E6F3FF,stroke:#007BFF;
    classDef service fill:#E8F5E9,stroke:#28A745;
    classDef repository fill:#FFF3E0,stroke:#FF9800;
    classDef database fill:#F1E4E4,stroke:#D32F2F,stroke-width:2px;

    A[İstemci<br/>(HTTP İsteği)] --> B{API Router};

    subgraph "Backend Uygulaması (Express.js)"
        B --> C[Controller Katmanı];
        C --> D[Service Katmanı<br/>(İş Mantığı)];
        D --> E[Repository Katmanı<br/>(Veri Erişim Soyutlaması)];
        E --> F[(PostgreSQL)];
    end

    class A entrypoint;
    class B,C controller;
    class D service;
    class E repository;
    class F database;
```

