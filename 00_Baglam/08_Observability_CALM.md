# Observability ve Cloud ALM — SolMan Emekliliği (2027/2030)

> SolMan kapanıyor, izleme ve operasyon işi buluttaki Cloud ALM'e taşınıyor. Bu, Basis için yeni bir alet kutusu ve birkaç tarih demek.

## 1. Bu nedir? (tek paragraf)

Yıllardır SAP sistemlerini izlemek, uyarı kurmak, transport ve değişiklikleri yönetmek için **Solution Manager (SolMan)** kullanıldı — kendi sunucusuna, veritabanına kurulan ağır bir araç. SAP bunu emekliye ayırıyor ve yerine **SAP Cloud ALM (CALM)**'i koyuyor (ALM = Application Lifecycle Management, yani bir uygulamanın projeden canlıya, oradan da operasyona kadar tüm yaşam döngüsünün yönetimi). CALM bir **SaaS** ürünü (Software as a Service — kurmadığın, SAP'nin bulutta çalıştırdığı, sen sadece bağlanıp kullandığın hizmet); donanım, OS, HANA lisansı istemez, dakikalar içinde aktif olur. Bu dosyanın çevresinde sürekli geçecek terim **observability** (gözlemlenebilirlik): sistemin "ayakta mı?" sorusunun ötesine geçip metrik, log ve trace'lerle "içeride ne oluyor, nerede yavaşlıyor, hangi entegrasyon hata veriyor?" sorularını yanıtlayabilme yeteneği.

## 2. Neden önemli / nereye gidiyor?

İki tarih bu işi acil yapıyor: **SolMan ana bakımı 31 Aralık 2027'de** bitiyor, ardından sadece **2030'a kadar sınırlı (ücretli) genişletilmiş bakım** var (bkz. [../02_SAP_Haberleri/07_Maintenance_2027_2030_Lisans.md](../02_SAP_Haberleri/07_Maintenance_2027_2030_Lisans.md), madde 8). SAP geçişi şimdi başlatıp **2028'den önce** bitirmeyi öneriyor. Bir uyarı: CALM, SolMan'in birebir kopyası değil — örneğin **ChaRM** (Change Request Management, değişiklik/transport onay süreci) için doğrudan karşılığı yok ve veri göçü sağlanmıyor; çoğu kurum bir süre iki aracı paralel çalıştıracak. Bu yüzden ChaRM/ITSM yoğun kullanan müşterilerde geçiş en zorlu yer. Öte yandan CALM tarafına yatırım hızlanıyor: 2025–2026'da RFC metrik izleme (tRFC/qRFC/bgRFC kuyrukları), Configuration & Security Analysis ve yeni API'ler eklendi (bkz. aynı dosya, madde 9). Yön net: izleme ve operasyon merkezi buluta kayıyor.

## 3. Basis için ne anlama geliyor?

Rol bitmiyor, **kabuk değiştiriyor**. "Sistemi kurdum, CCMS alert'i bağladım" işi yerine, CALM'i bağlamak ve içinden hangi verinin akacağını **kurgulamak** geliyor. En kritik iki yeni sorumluluk:

- **Fair Use / 8 GB sınırı.** CALM lisans olarak çoğu müşteride ücretsiz gelir (Enterprise Support, Cloud editions veya PSLE kapsamında). Ama bedava gelen tenant belirli bir bellek kotasıyla gelir; standart paket **8 GB**. Yüzlerce sistemi tek tenant'a bağlar ya da log/exception verisini yıllarca tutmaya kalkarsan kota şişer ve SAP **CPEA** (Cloud Platform Enterprise Agreement — kullandıkça ödenen bulut tüketim sözleşmesi) üzerinden ek depolama satar (genelde 4 GB'lık bloklar).
- **Data Retention (veri saklama) politikası.** "Hangi veriyi ne kadar tutalım?" artık bir Basis kararı. Doğru ayar = hem yeterli geçmiş hem maliyet kontrolü. (FinOps tarafıyla doğrudan ilişkili — bkz. [09_FinOps_Maliyet.md](09_FinOps_Maliyet.md).)

## 4. Hangi somut beceriler gerekiyor?

- **Private Cloud (ECS/PCE) aktivasyonu.** S/4HANA Private Cloud Edition (PCE) veya ECS (Enterprise Cloud Services, SAP'nin yönettiği özel bulut operasyonu) "Enterprise Support, cloud editions" kapsamındadır; CALM hakkı dahildir. Sistem tarafında **ST-PI** ve **ST-A/PI** add-on'larının güncel olması, **SAP for Me** portalından tenant provisioning, ve sistemde `/n/SDF/ALM_SETUP` işlem kodu ile Service Key girilip bağlantının kurulması gerekir.
- **Bağlantı teyidi.** ECS çoğu zaman boru hattını zaten kurmuş olur. `/n/SDF/ALM_SETUP`'ta "Registered" yeşilse ve **SM37**'de `SAP_ALM_DATA_COLLECTOR_DISPATCH` job'ı düzenli çalışıyorsa veri akıyordur; "Push Data" ile test edilir.
- **Scope ve uyarı kurgusu.** Health Monitoring, Business Process Monitoring, hangi metriğe alert, bildirimin kime gideceği — boru hattı kurulmuş olsa bile bu kurgu Basis'in işi.
- **Bağlantı altyapısı.** HTTPS/proxy/firewall'ın CALM endpoint'ine çıkışı; rol atamaları için BTP role collection bilgisi (bkz. [02_BTP_Platformu.md](02_BTP_Platformu.md)).

## 5. Hiç bilmiyorsam ilk adım

Bilmiyorsan normal — CALM nispeten yeni ve çoğu kişi SolMan'den geliyor. İşte başlangıç: (1) Müşterinin destek sözleşmesini kontrol et; Enterprise Support / Cloud editions / PSLE varsa **tenant talep etme hakkın hazır demektir.** (2) SAP for Me > Systems & Provisioning'de CALM'in "Provisioned" olup olmadığına bak — belki ECS zaten kurmuştur. (3) Bir test sisteminde `/n/SDF/ALM_SETUP` ekranını aç, sadece durumu okumayı öğren. (4) CALM içinde bir basit Health Monitoring scope'u tanımlayıp tek bir uyarı kur. Bağlamak için aylar değil dakikalar yeter; en hızlı öğrenme arayüzü kurcalamaktan gelir. (Genel resim için bkz. [01_Cloud_Donusumu.md](01_Cloud_Donusumu.md).)

## 6. Terimler sözlüğü (kısa)

- **SolMan (Solution Manager):** Eski, kurulumlu izleme/operasyon aracı; bakımı 2027 (sınırlı 2030).
- **Cloud ALM (CALM):** SolMan'in bulut tabanlı, kurulumsuz halefi.
- **Observability:** Metrik/log/trace ile "içeride ne oluyor" görünürlüğü.
- **SaaS:** Sunucusunu sen yönetmediğin, bulutta hazır gelen yazılım hizmeti.
- **Fair Use / 8 GB:** CALM'in ücretsiz tenant'ındaki standart bellek kotası.
- **Data Retention:** Verinin ne kadar süre saklanacağı; kota ve maliyeti belirler.
- **CPEA:** Kotayı aşınca ek kaynağın satın alındığı bulut tüketim sözleşmesi.
- **ChaRM:** SolMan'deki değişiklik/transport onay süreci; CALM'de doğrudan karşılığı yok.
- **ECS / PCE:** SAP'nin yönettiği özel bulut operasyonu / S/4HANA Private Cloud Edition.
- **ST-PI / ST-A·PI:** Sistemin CALM'e veri gönderebilmesi için gereken add-on'lar.
- **`/n/SDF/ALM_SETUP`:** Sistemi CALM tenant'ına bağlayan/teyit eden işlem kodu.
