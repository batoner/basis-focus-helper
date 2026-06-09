# Basisçi Ne Yapar — Rol Tanımı

> Bu klasör, "bir SAP Basis mühendisi ne yapar"ı **kapsayıcı bir aktivite envanteri** olarak
> dökümante eder. Amaç: testte "ben bunların hangisini yaptım?" diye işaretleyebilmen.
>
> *SAP Basis: SAP sistemlerinin teknik temelini kuran, işleten ve güvende tutan mühendislik
> alanı — işletim sistemi/veritabanı ile uygulama arasındaki katman.*

---

## Tek cümlede

Basisçi, SAP sistemlerinin **kurulmasından, çalışır/performanslı/güvenli kalmasından ve
değişimlerin (yama, transport, upgrade, göç) güvenle yapılmasından** sorumlu teknik mühendistir.

## Sorumluluk alanları (klasik çerçeve)

- **Kurulum & mimari:** Yeni sistem kurulumu, sizing, sistem kopyalama/refresh, DR/HA tasarımı.
- **İşletim & izleme:** Sistem sağlığı, performans, iş yükü (batch), spool, kuyruklar, dump'lar.
- **Değişim yönetimi:** Transport, kernel/SP/EHP yama ve upgrade'ler, güvenlik notları.
- **Veritabanı:** Yedek/restore, büyüme/kapasite, HANA yönetimi.
- **Kullanıcı & yetki:** Kullanıcı yaşam döngüsü, rol tasarımı.
- **Güvenlik:** Parametreler, denetim kaydı (audit log), güvenlik notları, sertleştirme.

## Rol nereye evriliyor (klasik → cloud)

Geleneksel "sistemi ayakta tut" işi duruyor; ama ağırlık giderek **bulut tarafına** kayıyor:
BTP hesap yönetimi, Cloud Connector, kimlik servisleri (IAS/IPS), HANA Cloud, Cloud ALM ile
izleme, RISE/ECS operasyonu, tüketim/maliyet takibi ve giderek **otomasyon + AI**. Yani Basisçi,
"operatör"den "**platform mühendisi + otomasyon tasarımcısı**"na doğru genişliyor.
Bu evrimin alan alan ayrıntısı ve güncel kanıtı için → [`../00_Baglam/00_Genel_Bakis.md`](../00_Baglam/00_Genel_Bakis.md).

> Bu yüzden bu envanter iki ana parçaya ayrılır:
> - [`01_Klasik_OnPrem_Operasyonlar.md`](01_Klasik_OnPrem_Operasyonlar.md)
> - [`02_Cloud_Operasyonlar.md`](02_Cloud_Operasyonlar.md)
>
> Rutinler: [`03_Gunluk_Haftalik_Aylik_Rutinler.md`](03_Gunluk_Haftalik_Aylik_Rutinler.md) ·
> İş koluna eşleme (testin köprüsü): [`04_Yetkinlik_Alanlari_Matrisi.md`](04_Yetkinlik_Alanlari_Matrisi.md)

## Tipik bir gün / hafta (örnek)

- **Her gün:** Gece batch'lerini ve yedekleri kontrol, sistem sağlığı (kırmızı uyarılar),
  açık ticket'lar, kuyruk/dump kontrolü.
- **Her hafta:** Performans bakışı, transport'lar, kullanıcı/yetki talepleri, kapasite trendi.
- **Periyodik:** Yama/SP planlama, güvenlik notu değerlendirme, housekeeping, DR tatbikatı,
  upgrade/göç projeleri.

> Not: Hiç kimse bunların **hepsini** yapmaz; herkesin bir kısmında derinliği, bir kısmında
> boşluğu vardır. Testin amacı tam olarak bu haritayı senin için çıkarmak — eksik olman normal.
