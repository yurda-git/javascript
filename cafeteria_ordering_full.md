METU COMPUTER CENTER Software Requirements Specification Document\
Cafeteria Ordering System Hazırlayan Yurdagül ÖZTÜRK Onaylayan Dr. Özgür
Kaya Yürürlük Tarihi 14.11.2025 Revizyon Tarihi 14.11.2025 Revizyon
Numarası 1 1 BIDB2025-1/V1.0

Table of Contents
METU...................................................................................................................................................
1 Software Requirements Specification Document Cafeteria Ordering System
..................................... 1 1. Giriş (Introduction)
...........................................................................................................................
3 1.1 Amaç (Purpose)
..........................................................................................................................
3 1.2 Kapsam (Project scope)
.............................................................................................................
3 2. Overall description
...........................................................................................................................
4 2.1 Ürün Perspektifi (Product perspective)
......................................................................................
4 2.2 Ürün Yaşam Döngüsü (State Transition)
...................................................................................
5 2.3 Kullanıcı Sınıfları ve Özellikleri (User classes and
characteristics) .......................................... 6 3. Sistem
Özellikleri (System features)
................................................................................................
7 3.1 İş
Süreçleri.................................................................................................................................
7 3.1.1 İş Gereksinimleri
................................................................................................................
7 3.1.2 Ana İş Süreci
......................................................................................................................
7 3.1.x Alt İş Süreci
x......................................................................................................................
7 3.2 Kullanıcıların Sistemde Gerçekleştireceği İşlemler
.................................................................. 8
3.2.1 Genel Kullanıcı Senaryoları
...............................................................................................
8 3.2.1 Kullanım senaryosu 1
.........................................................................................................
9 3.2.2.1 Kullanım Senaryosu Tanımı (Use Case Definition)
................................................... 9 3.2.x.2 Kullanıcı
Arayüzleri (User Interfaces)
..................................................................... 11
3.2.x.3 Akış Diyagramları (Flowchart)
.................................................................................
11 4. Veri Gereksinimleri (Data requirements)
.......................................................................................
12 4.1 Mantıksal Veri Modeli (Logical data model)
...........................................................................
12 4.2 Veri Sözlüğü (Data dictionary)
................................................................................................
13 8 Gereksinimler \[Requirements\]
........................................................................................................
15 8.1.x Kullanım Senaryosunun Fonksiyonel Gereksinimleri
.......................................................... 15 8.2.x İş
Gereksinimleri (Business Rules)
.......................................................................................
15 8.3. Diğer Gereksinimler \[Other requirements\]
.............................................................................
16 2 BIDB2025-1/V1.0

1.  Giriş (Introduction) The introduction presents an overview to help
    the reader understand how the SRS is organized and how to use it.
    1.1 Amaç (Purpose) This SRS describes the functional and
    nonfunctional requirements for the Cafeteria Ordering System (COS).
    This document is intended to be used by the members of the project
    team who will implement and verify the correct functioning of the
    system. 1.2 Kapsam (Project scope) The COS will permit METU
    employees to order meals from the METU cafeteria online to be
    delivered to specified campus locations. Only "Müşteri Yemek
    Siparişi Verir" use case whith its business rules will be developed
    in this scope, other use cases and busiess rules will be developed
    in the following releases. "Ödemenin Yapılması" use case will also
    be developed in the following releases Aktör Kullanım Senaryosu
    Müşteri 1. Yemek Siparişi Verir

2.  Yemek Siparişini Değiştirir

3.  Yemek Siparişini İptal Eder

4.  Menüyü Görüntüler

5.  Ödemesini Yapabilir1.st release 1.st release Following releases 1.st
    release Following releases Menü Yöneticisi 8. Menü Oluşturabilir

6.  Menüleri Arşivleyebilir

7.  Yemek Spesiyali Tanımlayabilir1.st release Following releases
    Following releases Kafeterya Personeli 11. Yemek Teslimatı Talep
    Edebilir

8.  Raporlar OluşturabilirFollowing releases Following releases Yemek
    Dağıtımcısı 13. Yemek Teslimatını Kaydedebilir

9.  Teslimat Talimatlarını YazdırabilirFollowing releases Following
    releases 3 BIDB2025-1/V1.0

10. Overall description 2.1 Ürün Perspektifi (Product perspective) The
    Cafeteria Ordering System is a new software system that replaces the
    current manual and smart card processes for ordering and picking up
    meals in the Process Impact cafeteria. The system is expected to
    evolve over several releases, ultimately connecting to the Internet
    ordering services for several local restaurants and to credit and
    debit card authorization services. 4 BIDB2025-1/V1.0

2.2 Ürün Yaşam Döngüsü (State Transition) Model 5 BIDB2025-1/V1.0

2.3 Kullanıcı Sınıfları ve Özellikleri (User classes and
characteristics) 6 BIDB2025-1/V1.0

3.  Sistem Özellikleri (System features) 3.1 İş Süreçleri 3.1.1 İş
    Gereksinimleri
4.  Kafeterya karını arttırmak
5.  Müşteri memnuniyetini arttırmak
6.  Daha fazla müşteriye ulaşmak 3.1.2 Ana İş Süreci Definition: Model:
    3.1.x Alt İş Süreci x 7 BIDB2025-1/V1.0

3.2 Kullanıcıların Sistemde Gerçekleştireceği İşlemler 3.2.1 Genel
Kullanıcı Senaryoları Use Cases Aktör Kullanım Senaryosu Müşteri 1.
Yemek Siparişi Verir 2. Yemek Siparişini Değiştirir 3. Yemek Siparişini
İptal Eder 4. Menüyü Görüntüler 5. Ödemesini Yapabilir Menü Yöneticisi
8. Menü Oluşturabilir 9. Menüleri Arşivleyebilir 10. Yemek Spesiyali
Tanımlayabilir Kafeterya Personeli 11. Yemek Teslimatı Talep Edebilir
12. Raporlar Oluşturabilir Yemek Dağıtımcısı 13. Yemek Teslimatını
Kaydedebilir 14. Teslimat Talimatlarını Yazdırabilir Use Case Model
Figure 1: Kullanıcı Senaryo Diyagramı 8 BIDB2025-1/V1.0

3.2.1 Kullanım senaryosu 1 3.2.2 Müşteri Yemek Siparişi Verir 3.2.2.1
Kullanım Senaryosu Tanımı (Use Case Definition) ID and Name: UC-1: Order
a Meal ( Müşteri Yemek Siparişi Verir ) Created By: Prithvi Raj Date
Created: October 4, 2013 Primary Actor: Patron Secondary Actors:
Cafeteria Inventory System Description: A Patron accesses the Cafeteria
Ordering System from either the corporate intranet or external Internet,
views the menu for a specific date, selects food\
items, and places an order for a meal to be picked up in the cafeteria
or delivered to a specified location within a specified 15-minute time
window. Trigger: A Patron indicates that he wants to order a meal.
Preconditions: PRE-1. Patron is logged into COS. PRE-2. Patron is
registered for meal payments by payroll deduction Postconditions:
POST-1. Meal order is stored in COS with a status of "Accepted." POST-2.
Inventory of available food items is updated to reflect items in this\
order. POST-3. Remaining delivery capacity for the requested time window
is updated. Normal Flow: 1.0 Order a Single Meal 1. Patron asks to view
menu for a specific date. (see 1.0.E1, 1.0.E2) 2. COS displays menu of
available food items and the daily special. 3. Patron selects one or
more food items from menu. (see 1.1) 4. Patron indicates that meal order
is complete. (see 1.2) 5. COS displays ordered menu items, individual
prices, and total price, including taxes and delivery charge. 6. Patron
either confirms meal order (continue normal flow) or requests to modify
meal order (return to step 2). 7. COS displays available delivery times
for the delivery date. 8. Patron selects a delivery time and specifies
the delivery location. 9. Patron specifies payment method. 10. COS
confirms acceptance of the order. 11. COS sends Patron an email message
confirming order details, price, and\
delivery instructions. 12. COS stores order, sends food item information
to Cafeteria Inventory System, and updates available delivery times.
Alternative Flows: 1.1 Order multiple identical meals 1. Patron requests
a specified number of identical meals. (see 1.1.E1) 2. Return to step 4
of normal flow. 1.2 Order multiple meals 9 BIDB2025-1/V1.0

1.  Patron asks to order another meal.
2.  Return to step 1 of normal flow. Exceptions: 1.0.E1 Requested date
    is today and current time is after today's order cutoff time
3.  COS informs Patron that it's too late to place an order for today.
    2a. If Patron cancels the meal ordering process, then COS terminates
    use case. 2b. Else if Patron requests another date, then COS
    restarts use case. 1.0.E2 No delivery times left
4.  COS informs Patron that no delivery times are available for the meal
    date. 2a. If Patron cancels the meal ordering process, then COS
    terminates use case. 2b. Else if Patron requests to pick the order
    up at the cafeteria, then continue with normal flow, but skip steps
    7 and 8. 1.1.E1 Insufficient inventory to fulfill multiple meal
    order
5.  COS informs Patron of the maximum number of identical meals he can
    order, based oncurrent available inventory. 2a. If Patron modifies
    number of meals ordered, then return to step 4 of normal flow. 2b.
    Else if Patron cancels the meal ordering process, then COS
    terminates use case. Priority: High Frequency of Use: Approximately
    300 users, average of one usage per day. Peak usage load for\
    this use case is between 9:00 A.M. and 10:00 A.M. local time.
    Business Rules: BR-1, BR-2, BR-3, BR-4, BR-11, BR-12, BR-33
    Functional Requirements Other Information: 1. Patron shall be able
    to cancel the meal ordering process at any time prior to confirming
    it.
6.  Patron shall be able to view all meals he ordered within the
    previous six months and repeat one of those meals as the new order,
    provided that all food items are available on the menu for the
    requested delivery date. (Priority = medium) \[Note: You could also
    show this as an alternative flow for the use case.\]
7.  The default date is the current date if the Patron is using the
    system before today's order cutoff time. Otherwise, the default date
    is the next day that the cafeteria is open. Assumptions: Assume that
    15 percent of Patrons will order the daily special (Source: previous
    6 months of cafeteria data). 10 BIDB2025-1/V1.0

3.2.x.2 Kullanıcı Arayüzleri (User Interfaces) Ekran arayüzleri. Buraya
eklenebilir veya referans verilebilir 3.2.x.3 Akış Diyagramları
(Flowchart) Detay İş akışları. Buraya eklenebilir veya referans
verilebilir 11 BIDB2025-1/V1.0

4.  Veri Gereksinimleri (Data requirements) 4.1 Mantıksal Veri Modeli
    (Logical data model) 12 BIDB2025-1/V1.0

4.2 Veri Sözlüğü (Data dictionary) Data element Description Composition
or data\
typeLengthValues delivery instruction where and to whom a meal is to be
delivered, if it isn't being picked up in the cafeteriapatron name +
patron phone number + meal date + delivery location + delivery time
window delivery location building and room to which an ordered meal is
to be deliveredalphanumeric 50hyphens and commas permitted delivery time
beginning time of a 15-minute range on the meal date during which an
ordered meal is to be deliveredtime hh:mm employee ID company ID number
of the employee who placed a meal orderinteger 6 food item
descriptiondescription of a food item on a menualphabetic 100 food item
price pre-tax cost of a single unit of a menu food itemnumeric, dollars
and TLdd.cc meal order details about a meal a Patron orderedmeal order
number + order date + meal date + 1:m{ordered food item} + delivery
instruction + meal order status meal order number unique ID that COS
assigns to each accepted meal orderinteger 7 menu list of food items
available for purchase on a specific datemenu date + 1:m{menu food item}
menu food item description of a menu item food item description + food
item price patron a Process Impact employee who is authorized to
orderpatron name + employee ID 13 BIDB2025-1/V1.0

a mea + patron phone number + patron location + patron email patron
email email address of the employee who placed a meal orderalphanumeric
50 patron location building and room numbers of the employee who placed
a meal orderalphanumeric 50hyphens and commas permitted patron name name
of the employee who placed a meal orderalphabetic 30 patron phone
numbertelephone number of the employee who placed a meal
orderAAA-EEE-NNNN xXXXX for area code (A), exchange (E), number (N), and
extension (X)18 meal order details about a meal a Patron orderedmeal
order number + order date + meal date + 1:m{ordered food item} +
delivery instruction + meal order status meal order number unique ID
that COS assigns to each accepted meal orderinteger 7Initial value is 1
meal order status status of a meal order that a Patron
initiatedalphabetic 16Incomplete, accepted, prepared, pending delivery,
delivered, canceled 14 BIDB2025-1/V1.0

8 Gereksinimler \[Requirements\] NoGereksinim AdıGereksinim
KaynağıÖncelikGereksinim Türü Bağlı Gereksini mBağlantı Açıklaması
Fonksiyonel Fonksiyonel Olmayan Yönetmelikler , Kanunlar, ... kaynaklı\
gereksinimler Teknik Gereksinim 8.1.x Kullanım Senaryosunun Fonksiyonel
Gereksinimleri 8.2.x İş Gereksinimleri (Business Rules) BR-1, BR-2,
BR-3, BR-4, BR-11, BR-12, BR-33 IDRule definition Type of rule Static or
dynamicSource BR-1Delivery time windows are 15 minutes, beginning on
each quarter hour.Fact Dynamic Cafeteria Manager BR-2Deliveries must be
completed between 11:00 A.M. and 2:00 P.M. local time,
inclusive.Constraint Dynamic Cafeteria Manager BR-3All meals in a single
order must be delivered to the same locationConstraint Static Cafeteria
Manager BR-4All meals in a single order must be paid for by using the
same payment method.Constraint Static Cafeteria Manager BR-8Meals must
be ordered within 14 calendar days of the meal date.Constraint Dynamic
Cafeteria Manager BR-11If an order is to be delivered, the patron must
pay by payroll deduction.Constraint Dynamic Cafeteria Manager BR-12Order
price is calculated as the sum of each food item price times the
quantity of that food item ordered, plus applicable sales tax, plus a
delivery charge if a meal is delivered outside the free delivery
zone.Computation Dynamic cafeteria policy; state tax code 15
BIDB2025-1/V1.0

BR-33Network transmissions that involve financial information or
personally identifiable information require 256-bit
encryption.Constraint Static corporate security policy 8.3. Diğer
Gereksinimler \[Other requirements\] 16 BIDB2025-1/V1.0
