# FinOps ve Maliyet — CPEA, UDMS, Bulut Maliyet Yönetimi

> Bulut faturası artık sabit değil; ne kadar kullanırsan o kadar ödersin. "Kim ne kadar harcadı, nereyi kısabiliriz" sorusu yeni bir Basis işi. Bu konuyu hiç duymadıysan sorun yok; buradan başla.

## 1. Bu nedir?

On-prem dünyada lisansı bir kez alır, donanımı kurar, biterdi. Bulutta ise ödeme **tüketime** bağlı: çalıştırdığın her servis bir havuzdan kredi yer, ay sonunda hesap çıkar. **FinOps** (Financial Operations — bulut harcamasını görünür kılma, sahiplendirme ve optimize etme disiplini), bu harcamayı kontrol altında tutma işine verilen ad. SAP tarafında bunun ticari adı **CPEA**'dır (Cloud Platform Enterprise Agreement — BTP için yıllık taahhütle önceden kredi satın aldığın, servisleri kullandıkça bu kredilerin eridiği tüketim modeli). Krediler bittiğinde ya da beklenmedik bir servis çok yiyince fatura sürpriz olur; FinOps tam da bu sürprizi önlemekle ilgilenir.

## 2. Neden önemli / nereye gidiyor?

SAP'nin tüm yatırımı buluta kayıyor (bkz. `01_Cloud_Donusumu.md`, `02_BTP_Platformu.md`). Bulut büyüdükçe "fatura kontrolü" stratejik bir yetkinliğe dönüşüyor. Ticari modelin kendisi de evriliyor: SAP yeni müşterileri **BTPEA** (BTP Enterprise Agreement — CPEA'nın yenisi, kapsamı genişletilmiş hâli) ile karşılıyor; mevcut CPEA müşterileri ise "öngörülebilir gelecekte" devam edebiliyor ([ASUG: SAP Experts Detail New BTPEA](https://www.asug.com/insights/sap-experts-detail-new-sap-business-technology-platform-enterprise-agreement)). Aynı tüketim mantığı maliyetin diğer ucunda da var: SAP iş ortağı (partner) firmalar tek bir global account altında birçok müşteriyi barındırıp her birine kullanımını yansıtmak (cross-charge) istiyor. Yani "kim ne harcadı"yı çözmek artık sadece muhasebe değil, mimari bir gereksinim.

## 3. Basis için ne anlama geliyor?

Basis mühendisi sistemin sağlığından sorumluydu; artık sistemin **maliyetinden** de sorumlu. Pratikte: krediler ne hızla eriyor, hangi servis beklenenden fazla yiyor, bir müşterinin tüketimi diğerine sızmadan nasıl raporlanır. Bu, klasik Basis izleme refleksinin (bkz. `08_Observability_CALM.md`) maliyet eksenine taşınmış hâli. Somut bir örnek elinde olabilir: ayrı yürütülen bir BTP maliyet dashboard'u (ekibin iç çalışması — paylaşılan repoda yer almaz) tam olarak bunu yapar — global account altındaki subaccount'ların CPEA tüketimini, **her müşteri yalnız kendi verisini görecek** şekilde gösteren bir dashboard. İşin püf noktası da burada: kaynak API (UDMS) global seviyede **tüm** müşterilerin verisini döndürür; izolasyonu sen uygulama katmanında (CAP'te row-level filtre ile) kurmak zorundasın. Tek bir hatada bir müşteri diğerinin faturasını görür — yani bu, hem maliyet hem güvenlik işi (bkz. `06_Guvenlik_ve_Kimlik.md`).

## 4. Hangi somut beceriler gerekiyor?

- **UDMS API'sini çağırabilmek:** **UDMS** (Usage Data Management Service — BTP tüketim/maliyet verisini REST API ile veren ücretsiz SAP servisi; teknik adı `uas`). Ana plan `reporting-ga-admin`'dir; `/cloudCreditsDetails`, `/monthlySubaccountsCost` gibi uç noktaları OAuth 2.0 token alıp Bearer ile çağırırsın.
- **Doğru servisi seçmek:** CIS Entitlements API'si *hak/kota* verir, **tüketim vermez**; tüketim sadece UDMS'tedir. Bu ayrımı bilmek tek başına seni öne çıkarır.
- **Ticari modeli okumak:** CPEA / BTPEA / PAYG farkı; kredinin yalnız tüketim-bazlı (consumption-based) hesaplarda olduğu; subaccount maliyetinin **tahmin** olduğu (kuruşu kuruşuna fatura değil — raporda "tahmini" diye etiketle).
- **HANA memory ve fair-use mantığı:** HANA bellek-içi (in-memory) bir veritabanıdır; bellek doğrudan maliyettir, gereksiz veri tutmak para yakar. Benzer şekilde **CALM fair-use** (Cloud ALM'in ücretsiz gelen bellek/saklama kotası, varsayılan 8 GB) aşılınca ek lisans gerekir; housekeeping ayarıyla kotayı yönetmek bir FinOps refleksidir (bkz. `08_Observability_CALM.md`).
- **CAP + Fiori temeli:** Maliyet verisini çekip izole ekrana koyan uygulamayı CAP ile kurarsın (ekibin iç BTP maliyet projesinde işlenmiştir — paylaşılan repoda yer almaz).

## 5. Hiç bilmiyorsam ilk adım

Korkma, çoğu Basisçi bu API'leri hiç görmedi. İlk adım küçük: SAP Discovery Center'da **[Usage Data Management Service](https://discovery-center.cloud.sap/serviceCatalog/usage-data-management-service?service_plan=reporting-ga-admin&region=all&commercialModel=cpea)** sayfasını aç, hangi raporları döndürdüğüne bak. Sonra resmi **[API Reference](https://api.sap.com/api/APIUasReportingService/overview)**'ı incele; gerçek bir CPEA hesabın service key'i varsa Postman/curl ile `/cloudCreditsDetails`'i bir kez çağır — token al, GET at, dönen JSON'u oku. Topluluk tarafında **[BTP FinOps: Keeping Track of your Credits](https://community.sap.com/t5/cloud-finops-ideas/btp-finops-keeping-track-of-your-credits/ba-p/13737793)** iyi bir giriş okuması. Hazır referans bir uygulama görmek istersen SAP'nin **[btp-resource-consumption-monitor](https://github.com/SAP-samples/btp-resource-consumption-monitor)** reposu UDMS'in nasıl çağrıldığını ve veri modelini gösterir (ama izolasyonu sen ekleyeceksin). Retro açısından bu alan **AI + BTP Development + BTP Core Services** seçimlerinin tam kesişimi (ekibin iç kaynağı — paylaşılan repoda yer almaz).

Konunun "nereye gidiyor" tarafını gerçek haberlerle görmek için:
- **[SAP BW/4HANA to Extend Maintenance in Alignment with S/4HANA](https://community.sap.com/t5/technology-blog-posts-by-sap/sap-bw-4hana-to-extend-maintenance-in-alignment-with-sap-business-suite-and/ba-p/13457952)** (bkz. `../02_SAP_Haberleri/07_Maintenance_2027_2030_Lisans.md`) — bakım/lisans tarihleri maliyet planlamasının çapasıdır.
- **[SAP RISE in 2026: What Changed and What It Means for Your Negotiation](https://redresscompliance.com/sap-rise-2026-what-changed.html)** (bkz. `../02_SAP_Haberleri/07_Maintenance_2027_2030_Lisans.md`) — ticari modelin modüler SKU yapısına dönmesi, FinOps muhakemesini doğrudan etkiler.

## 6. Terimler sözlüğü (kısa)

- **FinOps:** Bulut harcamasını görünür kılıp sahiplendiren ve optimize eden disiplin.
- **CPEA:** BTP için yıllık taahhütle önceden kredi alıp kullandıkça eriten tüketim modeli.
- **BTPEA:** CPEA'nın yeni nesli; yeni müşteriler için kapsamı genişletilmiş hâli.
- **PAYG:** Kullandıkça öde — taahhütsüz tüketim modeli.
- **Cloud credits (bulut kredisi):** Önceden satın alınan, servis kullanımıyla tükenen harcama havuzu.
- **UDMS (`uas`):** BTP tüketim/maliyet verisini REST API ile veren ücretsiz SAP servisi.
- **`reporting-ga-admin`:** UDMS'in global account seviyesinde maliyet/kredi döndüren ana service plan'ı.
- **Subaccount / Directory:** İzole ortam birimi / onları gruplayan ara katman (önerilen desen: müşteri = directory).
- **Cross-charge:** Bir müşterinin tüketimini ona yansıtma; subaccount seviyesinde **tahminîdir**.
- **Row-level filtre:** Her kullanıcının yalnız yetkili olduğu satırları görmesini sağlayan uygulama-içi izolasyon.
- **HANA memory:** Bellek-içi veritabanının kullandığı RAM; doğrudan maliyet kalemi.
- **CALM fair-use:** Cloud ALM ile ücretsiz gelen bellek/saklama kotası (varsayılan 8 GB); aşılırsa ek lisans.
