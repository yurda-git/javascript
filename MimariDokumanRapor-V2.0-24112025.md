# Proje Mimarisi ve Geliştirme Raporu - 21.11.2025

## 1. Proje Özeti

Bu rapor, mevcut web uygulamasının teknik yapısı, kullanılan teknolojiler ve genel yetenekleri hakkında bilgi sunmaktadır. Proje, güvenli bir kullanıcı kayıt ve giriş altyapısı sunan modern bir web uygulamasıdır. Proje kök dizininde mimari, isimlendirme standartları ve gereksinimler gibi konularda oldukça detaylı dokümantasyon dosyaları bulunmaktadır. Bu durum, projenin planlı ve düzenli bir şekilde geliştirildiğini göstermektedir.

## 2. Teknik Yapı

Uygulama, birbirinden bağımsız olarak geliştirilebilen ve ölçeklendirilebilen **Backend** (sunucu tarafı) ve **Frontend** (istemci tarafı) olmak üzere iki ana bileşenden oluşmaktadır.

### 2.1. Backend Mimarisi

*   **Teknoloji:** Sunucu tarafı, Node.js çalışma zamanı ortamı ve Express.js web çatısı kullanılarak geliştirilmiştir.

*   **Mimari Yaklaşım:** Sürdürülebilir ve bakımı kolay, katmanlı ((Layered Architecture)) bir mimari benimsenmiştir. 

      **API Katmanı:** Dış dünyadan gelen HTTP isteklerinin ilk temas noktasıdır
      
      **Controller Katmanı:** İstemci isteklerini karşılayarak, isteği işlenmek üzere ilgili iş mantığı katmanına iletir. İşlem sonucunu istemciye standart bir HTTP yanıtı olarak formatlar.
      
      **Service Katmanı:** Uygulamanın çekirdek iş mantığını barındırır.
      
       **Repository Katmanı:** Veritabanı işlemleri, esneklik sağlayan **Repository Tasarım Deseni** ile yönetilmektedir. iş mantığı katmanının farklı veritabanı sistemleriyle (örneğin, PostgreSQL veya MongoDB) minimum değişiklikle çalışabilmesine olanak tanır ve kodun esnekliğini artırır Son geliştirmeler ile MongoDB desteği kaldırılmıştır.  Mevcut durumda yalnızca **PostgreSQL** veritabanı kullanılmaktadır.
       
      
      Bağımlılık yönetimi, kodun modülerliğini artıran bir DI (Dependency Injection) container'ı ile sağlanmaktadır. Bu, bileşenler arasındaki sıkı bağımlılığı (tight coupling) azaltır.
      
*   **Merkezi Hata Yönetimi:** Sistem genelinde hataların tutarlı bir şekilde yakalanması, kaydedilmesi ve ilgili ekiplere anında bildirilmesi için merkezi bir mekanizma kurulmuştur. Bu yaklaşım, sistemin kararlılığını artırırken, olası sorunların proaktif olarak tespit edilmesini ve hızlıca çözülmesini sağlar. Kritik hatalar için otomatik bildirimler ve detaylı izleme yetenekleri sayesinde iş sürekliliği güvence altına alınmaktadır.
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

Aşağıdaki diyagramlar, C4 Model yaklaşımına göre hazırlanmış olup, sistem mimarisini farklı detay seviyelerinde sunmaktadır. Bu metin tabanlı diyagramlar, bilinen tüm platformlarla (GitHub, GitLab) uyumlu, en basit Mermaid sözdizimi kullanılarak oluşturulmuştur.

### 5.1. Sistem Bağlam Diyagramı (C4 Seviye 1: System Context Diagram)
Bu diyagram, sistemin (Web Uygulaması) dış dünya ile olan ilişkisini, kullanıcılarını ve etkileşimde bulunduğu diğer sistemleri en üst seviyeden gösterir. Sistem burada tek bir birim olarak ele alınır.

```mermaid
graph TD
    User("Kullanici")
    ExternalSystem("Dis Sistem (Orn: E-posta Servisi)")

    subgraph "Sistemimiz"
        OurSystem("Web Uygulamasi")
    end

    User -- "Kullanir" --> OurSystem
    OurSystem -- "Bildirim Gonderir" --> ExternalSystem
```

### 5.2. Konteyner Diyagramı (C4 Seviye 2: Container Diagram)
Bu diyagram, Seviye 1'deki 'Web Uygulaması' kutusunun içine zoom yaparak, sistemi oluşturan ana çalıştırılabilir birimleri (konteynerleri) ve aralarındaki etkileşimleri gösterir.

```mermaid
graph TD
    subgraph "Istemci Tarafi"
        User("Kullanici") --> Frontend("React Frontend (Bootstrap)");
    end

    subgraph "Sunucu Tarafi"
        Backend("Backend API (Express.js)");
    end

    Frontend -- "HTTP/S Cagrıları" --> Backend;
```

### 5.3. Bileşen Diyagramı (C4 Seviye 3: Component Diagram)
Bu diyagram, Seviye 2'deki 'Backend API' konteynerinin içine zoom yaparak, onun içindeki ana kod bileşenlerini ve katmanları gösterir. Her bir bileşenin sorumlulukları ve akışları burada detaylandırılır.

```mermaid
graph TD
    Istemci --> APIRouter["API Router"];

    subgraph "Backend Uygulamasi"
        APIRouter --> Controller["Controller Katmani"];
        Controller --> Service["Service Katmani (Is Mantigi)"];
        Service --> Repository["Repository Katmani (Veri Erisim)"];
        Repository --> Database[(PostgreSQL)];
    end
```

### 5.4. Frontend Bileşen Diyagramı (C4 Seviye 3: Frontend Component Diagram)
Bu diyagram, Seviye 2'deki 'Frontend Web Uygulaması' konteynerinin içine zoom yaparak, onun içindeki ana bileşenleri, sorumlulukları ve etkileşimleri gösterir.

```mermaid
graph TD
    User("Kullanici") --> Pages("Sayfalar (Login, Profile vb.)");
    
    subgraph "Frontend Uygulamasi (React)"
        Pages --> Components("Reusable Componentler");
        Components --> StateMgmt("Durum Yonetimi (Context API)");
        StateMgmt --> APIClient("Backend API Istemcisi");
    end
    
    APIClient -- "HTTP/S Cagrıları" --> Backend("Backend API");
```

### 5.5. Merkezi Hata Yönetimi Diyagramı (Centralized Error Management Diagram)

Bu model, sistem genelinde hataların nasıl yakalandığını, merkezi olarak işlendiğini ve ilgili paydaşlara nasıl bildirildiğini göstermektedir.

```mermaid
graph TD
    A[Gelen HTTP Istegi] --> B{Uygulama Akisi};

    subgraph "Hata Ortaya Cikisi"
        B -- "Validasyon Hatasi" --> EH;
        B -- "Yetkilendirme Hatasi" --> EH;
        B -- "Is Mantigi Hatasi" --> EH;
        B -- "Veritabani Hatasi" --> EH;
    end
    
    EH[Merkezi Hata Yakalayici Global Error Handler] --> CLM(Merkezi Hata Kaydi / Izleme);
    CLM --> Notif[Bildirimler Ekiplere];
    EH --> ErrResp[HTTP Hata Yaniti];
```

## 6. Referans Mimari Modelleri (Reference Architecture Models)

Bu bölümde, kurumsal referans mimari kılavuzumuzda tanımlanan ve standart bir proje yapısını temsil eden modeller sunulmaktadır.

### 6.1. Referans Konteyner Modeli (Reference Container Model)
Bu model, bir projenin temel yazılım birimlerinin (çalıştırılabilir uygulamalar, veritabanları gibi) nasıl bir araya gelmesi gerektiğini ve aralarındaki etkileşimleri göstermektedir.

```mermaid
graph TD
    User("User")
    
    subgraph "Standard Project Structure"
        Frontend("Frontend Web Application (React, Bootstrap, Vite)")
        Backend("Backend API (Node.js, Express.js)")
        Database("Project Database (PostgreSQL)")
    end

    ExternalSystem("External System (Email Service etc.)")

    User -- "Uses (HTTPS)" --> Frontend
    Frontend -- "API Calls (HTTPS/JSON)" --> Backend
    Backend -- "Reads/Writes (JDBC/TCP)" --> Database
    Backend -- "Communicates via API" --> ExternalSystem
```

### 6.2. Referans Dağıtım Modeli (Reference Deployment Model)
Bu model, bir projenin herhangi bir bulut veya yerel altyapı üzerinde standart olarak nasıl dağıtılması gerektiğini ve ana altyapı bileşenlerinin konumlandırılmasını göstermektedir.

```mermaid
graph TD
    Client("Client")
    
    subgraph "Public Network"
        LoadBalancer("Load Balancer")
    end

    subgraph "Private Network / Application Layer"
        ApplicationServers("Application Servers (Frontend + Backend)")
    end

    subgraph "Private Network / Data Layer"
        DatabaseServer("Database Server (PostgreSQL)")
    end

    Client -- "HTTPS" --> LoadBalancer
    LoadBalancer -- "Traffic Routing" --> ApplicationServers
    ApplicationServers -- "Data Access" --> DatabaseServer
```

## 7. Kullanıcı Giriş Akışı Sequence Diyagramı (User Login Flow)

Aşağıdaki sequence diyagramı, bir kullanıcının sisteme giriş yapma sürecini adım adım göstermektedir. Bu akış, frontend bileşenlerinden başlayarak backend servislerine ve veritabanına kadar olan tüm etkileşimi detaylandırır.

```mermaid
sequenceDiagram
    actor User
    participant LoginJSX as Login.jsx (React Component)
    participant AuthContext as AuthContext.jsx
    participant APIRouter as auth.router.js
    participant AuthController as authController.js
    participant AuthService as authService.js
    participant UserRepo as postgresUserRepository.js
    participant DB as PostgreSQL Database

    User->>LoginJSX: 1. E-posta ve şifre girer, "Giriş Yap" butonuna tıklar
    LoginJSX->>AuthContext: 2. login(email, password) fonksiyonunu çağırır
    AuthContext->>APIRouter: 3. POST /api/auth/login isteği gönderir
    APIRouter->>AuthController: 4. İsteği login metoduna yönlendirir
    AuthController->>AuthService: 5. loginUser(email, password) servisini çağırır
    AuthService->>UserRepo: 6. findByEmail(email) ile kullanıcıyı arar
    UserRepo->>DB: 7. Kullanıcıyı veritabanında sorgular
    DB-->>UserRepo: 8. Kullanıcı verisini döner (veya null)
    UserRepo-->>AuthService: 9. Kullanıcıyı iletir
    
    alt Kullanıcı bulundu ve şifre doğru
        AuthService->>AuthService: 10. bcrypt.compare ile şifreyi doğrular
        AuthService->>AuthService: 11. JWT (JSON Web Token) oluşturur
        AuthService-->>AuthController: 12. Token ve kullanıcı verisini döner
        AuthController-->>AuthContext: 13. HTTP 200 OK yanıtı ile token'ı döner
        AuthContext->>AuthContext: 14. Token'ı localStorage'a kaydeder ve state'i günceller
        AuthContext-->>User: 15. Kullanıcıyı profil sayfasına yönlendirir
    else Kullanıcı bulunamadı veya şifre yanlış
        AuthService-->>AuthController: Hata fırlatır (örn: Unauthorized)
        AuthController-->>AuthContext: HTTP 401 Unauthorized yanıtı döner
        AuthContext-->>LoginJSX: Hata mesajı gösterir
    end
```


