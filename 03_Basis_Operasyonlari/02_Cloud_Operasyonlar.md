# Cloud Basis Operasyonları

> Basis rolünün bulut tarafındaki aktivite envanteri. Her madde testte 0–4 ile işaretlenebilir.
> Burası "yeni dönem yetkinlik seti"nin yaşadığı yer; eksik olman çok normal.

## 1. BTP hesap ve platform yönetimi
- Hesap hiyerarşisi: Global Account / Directory / **Subaccount** kurulumu.
- **Entitlement** ve kota yönetimi (hangi servise ne kadar hak). *(Entitlement: bir alt hesaba
  tanımlı kullanım hakkı.)*
- Ortam yönetimi: Cloud Foundry / Kyma; space/org yönetimi.
- Tüketim & maliyet takibi: **CPEA** sözleşmesi, **UDMS** tüketim API'si.

## 2. Bağlantı (connectivity)
- **Cloud Connector** kurulumu/HA'sı (on-prem ↔ BTP güvenli ters tünel), sertifika yönetimi.
- **Destination** ve **service key** yönetimi, principal propagation.
- *(Cloud Connector: şirket içi sistemi buluta güvenle bağlayan köprü ajan.)*

## 3. Kimlik ve erişim (cloud)
- **IAS** (Identity Authentication) / **IPS** (Identity Provisioning) yapılandırması.
- SSO: SAML 2.0 / OIDC; kurumsal IdP (Azure AD / Entra, AD, Google Workspace) entegrasyonu.
- **XSUAA** ile uygulama yetkilendirme; rol koleksiyonları.

## 4. HANA Cloud ve veri servisleri
- HANA Cloud instance provisioning, ölçekleme, yedek, kullanıcı/şema yönetimi.
- (Veri tarafı derinleşmesi: Veri Yönetimi ve BDC iş kolları.)

## 5. İzleme ve yaşam döngüsü (Cloud ALM)
- **Cloud ALM** kurulumu ve izleme kapsamı (health, integration & exception monitoring).
- Private Cloud (ECS/PCE) için CALM aktivasyonu: ST-PI / ST-A·PI add-on'ları,
  `/n/SDF/ALM_SETUP`, veri toplayıcı job'ı (**SM37** `SAP_ALM_DATA_COLLECTOR_DISPATCH`).
- Data Retention Policy / fair-use (8 GB) yönetimi. *(Cloud ALM: SolMan'in bulut halefi.)*

## 6. RISE / ECS operasyonu
- **SAP for Me** üzerinden sistem yönetimi, **Service Request (SR)** açma/izleme.
- ECS ile sorumluluk paylaşımı (RACI), provizyon talepleri, sistem refresh talebi.
- Göç metodolojileri: **DMO with System Move** (veritabanı dönüşümü + buluta taşıma).

## 7. Geliştirme ve teslim hattı (CI/CD)
- **Cloud Transport Management (CTMS)**, Git tabanlı akış, **SAP Build Code** ile teslim.
- (Geliştirme derinleşmesi: BTP Development iş kolu.)

## 8. AI ve otomasyon temelleri
- **AI Core / Generative AI Hub** (dış LLM'leri güvenli bağlama), destination/güvenlik.
- **Joule** kurulumu/kullanımı; otomasyon araçları (n8n, Build Process Automation).
- AI ajan yönetişimi/izleme, **MCP sunucusu** kurulumu, model seçimi ve **AI Units** tüketim takibi.
- (AI derinleşmesi: AI iş kolu.)

## 9. Yeni dönem operasyonları (2025–2026 haberlerinden)
> Haber korpusunun (`../02_SAP_Haberleri/`) Basis operasyonuna eklediği güncel sorumluluklar.
- **Güvenlikte hız:** sıfır-gün açıklarına saatler içinde yama (aylık döngü artık yetmiyor),
  tedarik zinciri/CI-CD güvenliği (npm paket bütünlüğü), DORA gibi uyumluluk kontrolleri,
  CommonCryptoLib 8.6 ile kuantum-güvenli TLS, SCIM 2.0/IAS göçü.
  (bkz. `../02_SAP_Haberleri/06_Guvenlik_Uyumluluk.md`)
- **Veri & zero-copy:** BDC bağlayıcıları (Databricks/Snowflake/AWS), Data Product Studio
  yönetişimi, HANA vektör/Knowledge Graph. (bkz. `../02_SAP_Haberleri/05_Veri_HANA_Datasphere_BDC.md`)
- **Yaşam döngüsü:** SolMan → Cloud ALM göç projesi; Cloud ALM'de RFC metrik izleme.
  (bkz. `../02_SAP_Haberleri/07_Maintenance_2027_2030_Lisans.md` ve `../00_Baglam/08_Observability_CALM.md`)
- **Geliştirme ortamı:** ABAP'ın VS Code'a taşınması, Joule for Developers ile kod/test.
  (bkz. `../02_SAP_Haberleri/02_BTP_ve_Gelistirme.md`)

> Bu aktivitelerin **iş koluna eşlemesi** için → [`04_Yetkinlik_Alanlari_Matrisi.md`](04_Yetkinlik_Alanlari_Matrisi.md)
