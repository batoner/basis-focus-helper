# Klasik (On-Prem) Basis Operasyonları

> Geleneksel SAP Basis aktivitelerinin envanteri. Her madde testte 0–4 ile işaretlenebilecek
> somut bir aktivitedir. *(On-prem: sistemin kurumun kendi veri merkezinde çalışması.)*
>
> Parantez içindeki kısaltmalar ilgili SAP işlem kodu (transaction / "tcode")'dur.

## 1. Kurulum ve kurulum sonrası
- Yeni sistem kurulumu (**SWPM** — kurulum aracı), sizing (boyutlandırma).
- Kurulum sonrası yapılandırma: profil parametreleri (**RZ10/RZ11**), operasyon modları (**RZ04**).
- Lisans kurulumu (**SLICENSE**), STMS ilk kurulumu.

## 2. Sistem bakımı ve değişim
- Kernel güncelleme; **SPAM/SAINT** ile destek paketi / add-on kurulumu.
- **SPAU/SPDD** ile upgrade sonrası modifikasyon uyarlaması.
- EHP / Support Package Stack upgrade'leri.
- Güvenlik notu uygulama (**SNOTE**) — *not: bazı notlar risklidir, kontrollü uygulanır.*

## 3. Transport ve değişiklik yönetimi
- Transport sistemi (**STMS**), transport request yönetimi (**SE01/SE09/SE10**).
- Import kuyruğu yönetimi, transport of copies, cToC (cross-system).

## 4. İstemci (client) yönetimi
- Client copy (local/remote, **SCCL/SCC9**), client export/import (**SCC8**), silme (**SCC5**).
- Sistem kopyalama / refresh (homojen/heterojen), post-copy automation.

## 5. Performans ve izleme
- İş yükü analizi (**ST03/ST03N**), OS izleme (**ST06/OS07N**), iş süreçleri (**SM50/SM51**).
- Bellek/buffer (**ST02**), DB performansı (**ST04**), pahalı SQL (**ST05** trace).
- ABAP dump analizi (**ST22**), sistem log (**SM21**), update hataları (**SM13**).
- Merkezi izleme (**RZ20** / CCMS), kilitler (**SM12**), güncelleme (**SM14**).

## 6. İş yükü / batch / spool
- Arka plan işleri (**SM37/SM36**), olay tabanlı job'lar, kriko/zincir tasarımı.
- Spool ve yazıcı yönetimi (**SP01/SPAD**), TemSe tutarlılığı.
- RFC bağlantıları (**SM59**), qRFC/tRFC kuyrukları (**SMQ1/SMQ2**), **SM58**.

## 7. Veritabanı yönetimi
- Yedekleme/geri yükleme stratejisi ve testi; log yönetimi.
- HANA yönetimi (**HANA Cockpit / Studio**), tablo dağıtımı, delta merge, alert'ler.
- (Klasik DB'ler: Oracle/DB2/ASE bağlamında **DBACOCKPIT**), büyüme/kapasite takibi.

## 8. Kullanıcı ve yetki (temel)
- Kullanıcı yaşam döngüsü (**SU01**), rol/profil (**PFCG**), toplu kullanıcı (**SU10**).
- Yetki kontrolü (**SU53/ST01**), öneri değerleri (**SU24**). *(Derinlemesine: Yetkilendirme iş kolu.)*

## 9. Güvenlik (temel) ve uyumluluk
- Güvenlik parametreleri, denetim kaydı (**SM19/RSAU_CONFIG → SM20/RSAU_READ_LOG**).
- Güvenlik notu takibi (**SNOTE**, EWA/SOS raporları). *(Derinlemesine: SAP Güvenliği iş kolu.)*

## 10. Yüksek erişilebilirlik ve felaket kurtarma
- HA/DR mimarisi, replikasyon, failover testleri, RTO/RPO hedefleri.
- *(RTO/RPO: kurtarma süresi / kabul edilebilir veri kaybı hedefleri.)*

## 11. Güncel yükseltme & uyum notları (2025–2026)
- **Clean Core olgunluğu:** yükseltmelerde özelleştirmeleri A–D seviyesine göre değerlendir;
  Custom Code Migration Advisor ile remediation. (bkz. `../00_Baglam/04_Clean_Core.md`)
- **Compatibility Packs son tarihi 31 Mayıs 2026** — kullanan on-prem S/4HANA sistemlerini
  haritalayıp geçişi tamamla. (bkz. `../02_SAP_Haberleri/07_Maintenance_2027_2030_Lisans.md`)
- **ECC bakım takvimi:** EHP 6–8 ana bakım 31 Aralık 2027; göç planını buna göre kur.
- **Güvenlik notu hızlı müdahale:** SNOTE ile HotNews'leri öncelikli ve hızlı uygula (sıfır-gün riski).

> Bu aktivitelerin **iş koluna eşlemesi** için → [`04_Yetkinlik_Alanlari_Matrisi.md`](04_Yetkinlik_Alanlari_Matrisi.md)
