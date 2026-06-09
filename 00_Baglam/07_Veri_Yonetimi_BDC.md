# Veri Yönetimi ve BDC — HANA Cloud, Datasphere, Business Data Cloud, Arşiv/ILM

> Veriyi ucuz ve uyumlu tutmak (Veri Yönetimi) ile veriyi taşımadan analitiğe/AI'a açmak (BDC) — iki bağlantılı yön. Bilmiyorsan normal; aşağıda nereden başlayacağın var.

## 1. Bu nedir? (tek paragraf)

Bu alan iki yarımdan oluşur. Birincisi **Veri Yönetimi**: SAP sistemlerindeki veriyi performansı bozmadan, mümkün olduğunca ucuza ve yasal olarak tutmak. Veri büyür, RAM (sistemin hızlı ama pahalı belleği) pahalıdır; o yüzden veriyi "sıcak/ılık/soğuk" katmanlara ayırır, eskiyeni arşivler veya silersin. İkincisi **BDC — Business Data Cloud** (SAP'nin Datasphere + Analytics Cloud + iş içeriğini birleştiren yeni veri platformu): SAP verisini kopyalamadan, bulundukları yerde bırakarak raporlamaya ve yapay zekaya açmak. İkisinin de retro sunumunda "Yeni Odak!" etiketi var (bkz. `../01_Sunum_Ozetleri/Mimari_VeriYonetimi_BDC.md`).

## 2. Neden önemli / nereye gidiyor?

SAP'nin son iki yıldaki en görünür stratejik hamlesi bu alanda. "Zero-copy" (sıfır-kopya: veriyi fiziksel olarak çoğaltmadan başka platforma açma) artık merkezde: SAP, Databricks, Snowflake, Google BigQuery ve Microsoft Fabric ile veriyi taşımadan paylaşmayı **BDC Connect** üzerinden açtı ([SAP and Databricks Open a Bold New Era of Data and AI](https://news.sap.com/2025/02/sap-databricks-open-bold-new-era-data-ai/); [Introducing SAP Snowflake — New Data Fabric Innovations for BDC & HANA Cloud](https://news.sap.com/2025/11/sap-snowflake-new-data-fabric-innovations-sap-bdc-sap-hana-cloud/)). 2026'da AWS ile de çift yönlü zero-copy duyuruldu ([SAP and AWS: Bi-Directional Zero-Copy Data Sharing with SAP Business Data Cloud](https://news.sap.com/2026/05/sap-aws-next-generation-ai-bi-directional-zero-copy-data-sharing-sap-bdc/)). Yön net: veri, Joule (SAP'nin yapay zeka asistanı) ve diğer AI ajanlarının güvenilir yakıtı haline geliyor ([Accelerate the Autonomous Enterprise with SAP Business Data Cloud](https://news.sap.com/2026/05/sap-bdc-accelerate-autonomous-enterprise/)).

## 3. Basis için ne anlama geliyor?

Bu işin altyapısı büyük ölçüde Basis'in masasında. BDC tarafında bağlantı kurma (Cloud Connector, ağ tüneli), senkronizasyon ve performans yönetimi klasik Basis işine çok yakın — yani giriş eşiği düşük. Veri Yönetimi tarafında ise zaten yaptığın housekeeping, partitioning, backup ve arşivleme işleri TCO (toplam sahip olma maliyeti) konuşmasının tam ortasında. Ek olarak yönetişim büyüyor: veri ürünlerinin yaşam döngüsü, erişim kontrolü, lineage (verinin nereden geldiğinin izi) artık altyapı sorumluluğunun parçası ([Data Product Studio in SAP Business Data Cloud — GA H1 2026](https://www.sap.com/assetdetail/2026/03/50501ff5-437f-0010-bca6-c68f7e60039b.html)).

## 4. Hangi somut beceriler gerekiyor?

- **HANA katmanlama:** NSE (Native Storage Extension — sık erişilmeyen "ılık" veriyi diskte tutar, RAM'i boşaltır; diskte RAM'in ~4 katına kadar kapasite, %10 buffer cache ile makul hız), Data Tiering, çok seviyeli partitioning.
- **Arşivleme & ILM:** SARA (arşivleme işlem kodu) ile arşiv stratejisi, ILM (Information Lifecycle Management — verinin yasal saklama ve imha kurallarıyla yönetimi), KVKK/GDPR uyumu, Content Server entegrasyonu.
- **BDC bağlantısı:** Cloud Connector ve DP Agent (Data Provisioning Agent — on-prem veriyi buluta taşıyan köprü) kurulumu, SDA/SDI ile sanallaştırma/replikasyon, Remote Table Mapping.
- **Modelleme ve uç nokta:** Spaces (izole çalışma alanları), SAC Live (veriyi tarayıcıdan çıkarmadan görselleştirme), SAML/RBAC ile yetkilendirme.
- **Yeni dalga:** zero-copy ağ ve senkronizasyon yapılandırması, federation, HANA vektör/Knowledge Graph altyapısı ([New ML, NLP and AI Features in SAP HANA Cloud — Q4 2025](https://community.sap.com/t5/technology-blog-posts-by-sap/new-machine-learning-nlp-and-ai-features-in-sap-hana-cloud-2025-q4/ba-p/14293152)).

## 5. Hiç bilmiyorsam ilk adım

Bildiğin yerden başla. En düşük eşik: bir sistemde **büyüme/trend analizi** çıkarıp en şişkin 5-10 tabloyu bul, bir housekeeping veya arşiv stratejisi öner. Bu, hem TCO konuşmasına girer hem de mevcut becerini kullanır. İkinci adım: küçük bir **BDC bağlantı PoC'i** — Cloud Connector + DP Agent ile bir test S/4HANA tablosunu Datasphere'e bağla. Üçüncü adım: SAP HANA Cloud ve BDC için ücretsiz öğrenme kaynaklarını (SAP Learning, Discovery Center trial) tara. Komşu bağlamlar için bu klasördeki diğer odak dosyalarına, güncel haberler için (bkz. `../02_SAP_Haberleri/05_Veri_HANA_Datasphere_BDC.md`) bak.

## 6. Terimler sözlüğü (kısa)

- **TCO:** Toplam sahip olma maliyeti — donanım + lisans + işletme.
- **NSE:** Sık kullanılmayan veriyi RAM yerine diskte tutarak maliyeti düşüren HANA özelliği.
- **ILM:** Verinin yasal saklama ve imha kurallarıyla yönetilmesi.
- **Zero-copy:** Veriyi kopyalamadan, bulunduğu yerde başka platforma açma.
- **DP Agent:** On-prem veriyi buluta taşıyan köprü bileşeni.
- **SDA/SDI:** Veriyi taşımadan sanallaştırma (SDA) ve anlık replikasyon (SDI).
- **Spaces:** Datasphere/BDC içinde izole, sanal çalışma alanları.
- **SAC Live:** Veriyi çıkarmadan, kaynağında canlı görselleştirme.
- **Joule:** SAP'nin verilerden beslenen yapay zeka asistanı.
