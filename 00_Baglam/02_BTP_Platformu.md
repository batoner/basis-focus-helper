# BTP Platformu — Hesap Hiyerarşisi, CAP/Fiori/Build

> SAP'ın bulut çatısı: uygulamaların kurulduğu, bağlandığı ve faturalandığı yer. Basis'in yeni operasyon yüzeyi burası.

## 1. Bu nedir? (tek paragraf)

SAP BTP (Business Technology Platform — SAP'ın bulut uygulama ve geliştirme platformu), S/4HANA gibi çekirdek sistemlerin *yanında* duran, uzantıların ve entegrasyonların yaşadığı kattır. Eskiden bir uzantıyı doğrudan SAP sisteminin içine kodlardın; yeni yaklaşımda ("clean core" — çekirdeği bozmadan temiz tutma) bu kodu dışarı, BTP'ye alırsın. BTP üç hyperscaler (AWS/Azure/GCP) ve artık SAP'ın kendi altyapısı üzerinde de çalışır (bkz. `../02_SAP_Haberleri/02_BTP_ve_Gelistirme.md`, madde 9). Bilmiyorsan normal: BTP on-prem Basis'ten farklı bir dünya, ama mantığı tanıdık — hak ver, ortam kur, bağla, izle.

## 2. Neden önemli / nereye gidiyor?

2026 Sapphire'da SAP, BTP'yi Business Data Cloud ve AI Foundation ile birleştirip tek bir **"SAP Business AI Platform"** çatısı altında topladı; üç katman (bağlam, inşa, yönetişim) + Joule Studio tanıtıldı ([SAP Unveils Business AI Platform to Power the Autonomous Enterprise](https://news.sap.com/2026/05/sap-sapphire-keynote-business-ai-platform-power-autonomous-enterprise/)). Yani BTP tek tek servisler yığını olmaktan çıkıp bütünleşik bir "platform" gibi yönetilmeye başlıyor; bu da platform mühendisliğini ve yeni yönetişim katmanını işin merkezine koyuyor ([What's New in SAP BTP — Q1 2026 Innobytes](https://community.sap.com/t5/technology-blog-posts-by-sap/what-s-new-in-sap-btp-q1-2026-innobytes/ba-p/14368327)). Yön nettir: AI-destekli, konsolide bir bulut platformu.

## 3. Basis için ne anlama geliyor?

BTP, Basis rolünün **bulut tarafındaki envanteri**dir; eksik olman çok normal (bkz. `../03_Basis_Operasyonlari/02_Cloud_Operasyonlar.md`). Hesap iskeleti şöyle: en üstte **Global Account** (SAP ile imzaladığın sözleşmeyi temsil eder) → **Directory** (alt hesapları gruplayan, isteğe bağlı klasör katmanı; hakları dağıtabilir) → **Subaccount** (servislerin gerçekten çalıştığı, bir bölgeye bağlı çalışma alanı). Sözleşmeyle aldığın haklar (**Entitlement** — bir alt hesaba tanımlı kullanım hakkı/kota) global hesaptan, directory üzerinden subaccount'lara dağıtılır; tüketim de orada olur. Subaccount içinde bir **ortam** seçersin: **Cloud Foundry** (push komutuyla basit dağıtım, derin Kubernetes bilgisi gerektirmez) ya da **Kyma** (Kubernetes tabanlı; konteyner/serverless için esnek ama daha fazla uzmanlık ister). On-prem'deki "client/system/transport" düzenini düşün — burada da analog bir hiyerarşi ve hak yönetimi var; sadece sözlük değişti.

## 4. Hangi somut beceriler gerekiyor?

- **Hesap & hak yönetimi:** Global Account / Directory / Subaccount kurulumu; entitlement ve kota dağıtımı.
- **Ortam:** Cloud Foundry org/space ya da Kyma namespace yönetimi.
- **Bağlantı:** **Destination** (BTP'den dış/iç sisteme nasıl ulaşılacağını tanımlayan bağlantı kaydı), **service key** (bir servise programatik erişim için üretilen kimlik bilgisi seti), Cloud Connector ve principal propagation.
- **Kimlik & yetki:** **XSUAA** (BTP uygulamalarına kimlik/yetki sağlayan servis) ile rol koleksiyonları; IAS/IPS.
- **Geliştirme yüzeyini tanı:** **CAP** (Cloud Application Programming Model — Node.js/Java ile servis yazmanın SAP standardı), **Fiori/UI5** (SAP'ın web arayüz çatısı), **SAP Build** (az-kod araç ailesi). CAP tarafında CAP Console ve MCP sunucusu gibi yenilikler operasyonu kolaylaştırıyor ([SAP CAP Update: CDS 9 Revolutionizes Enterprise Development](https://community.sap.com/t5/technology-blog-posts-by-members/sap-cap-update-cds-9-revolutionizes-enterprise-development/ba-p/14054057)).
- **Maliyet:** CPEA sözleşmesi ve UDMS tüketim API'si (bkz. ekibin iç BTP maliyet projesi — paylaşılan repoda yer almaz).

> ⚠️ Dikkat: **SAP Build Apps 23 Mart 2026'da emekliye ayrıldı** — yeni iş için CAP + Fiori/UI5 ana yolu seç (kaynak: ekibin iç kaynağı — paylaşılan repoda yer almaz).

## 5. Hiç bilmiyorsam ilk adım

1. Bir **trial/free-tier** hesabı aç, içinde bir subaccount kur, bir entitlement ata — hiyerarşiyi elle gör. (Not: trial'da CPEA kredisi yoktur, tüketim verisi boş döner.)
2. Cloud Foundry'de bir CAP "hello world" servisini `cf push` ile dağıt; bir destination ve service key oluştur.
3. SAP Learning'in ücretsiz "Operating SAP BTP" / "Account Model" derslerini takip et.
4. Sonra köprüye geç: bir Destination + Cloud Connector ile on-prem'e bağlan — bu, mevcut Basis bilgini doğrudan kullanır.

## 6. Terimler sözlüğü (kısa)

- **Global Account:** SAP ile sözleşmeni temsil eden en üst hesap; faturalama burada.
- **Directory:** Subaccount'ları gruplayan, isteğe bağlı klasör katmanı.
- **Subaccount:** Servislerin gerçekten çalıştığı, bir bölgeye bağlı çalışma alanı.
- **Entitlement:** Bir alt hesaba tanımlı kullanım hakkı/kota.
- **Cloud Foundry:** Push-tabanlı, kolay; derin Kubernetes uzmanlığı gerektirmeyen ortam.
- **Kyma:** Kubernetes tabanlı, konteyner/serverless için esnek ortam.
- **CAP:** SAP'ın servis yazma çatısı (Node.js/Java).
- **Fiori/UI5:** SAP'ın web arayüz teknolojisi.
- **SAP Build:** Az-kod uygulama/otomasyon araç ailesi.
- **Destination:** BTP'den bir sisteme nasıl ulaşılacağını tanımlayan bağlantı kaydı.
- **Service key:** Bir servise programatik erişim için üretilen kimlik bilgisi.
- **XSUAA:** BTP uygulamalarına kimlik/yetki sağlayan servis.
