# Soru Bankası — Alan Alan

> `/test` bu soruları **sohbet içinde tek tek** sorar. Her aktivite **0–4** (olgunluk);
> her iş kolu sonunda **ilgi 0–3**. Ölçek ve akış: `00_Test_Mantigi.md`.
> Aktiviteler `../03_Basis_Operasyonlari/04_Yetkinlik_Alanlari_Matrisi.md` ile büyük ölçüde aynı
> (matristeki "yeni dönem" maddeleri dahil).

> **Olgunluk:** 0 Hiç duymadım · 1 Duydum, yapmadım · 2 Bir-iki kez · 3 Düzenli · 4 Öğretebilirim/tasarlarım.

---

## 0. Klasik Basis (ısınma — temel zemin)
1. Kurulum / upgrade / transport (SWPM, STMS, SPAM, client copy/refresh)
2. Performans & izleme (ST03N, ST22, SM37, RZ20)
3. DB yedek / restore ve büyüme takibi
4. HA/DR tasarımı (replikasyon, failover, RTO/RPO)
> *(Klasik Basis bir "yeni dönem iş kolu" değil; ilgi sorusu sorulmaz, sadece zemin ölçülür.)*

## 1. AI
1. Joule (SAP yapay zekâ asistanı) kullanımı/yapılandırması
2. Generative AI Hub / AI Core ile dış LLM bağlama, orkestrasyon
3. Agentic akış / RAG / prompt tasarımı (n8n, Build Process Automation dahil)
4. Bir Basis işini AI ile otomatikleştirme (ör. dump triyajı, rapor üretimi)
5. *(Yeni dönem)* AI ajan yönetişimi/izleme, MCP sunucusu, model seçimi & AI Units takibi
> **İlgi (0–3):** AI/otomasyon alanında gelişmek ister misin?

## 2. BTP Development
1. CAP (uygulama geliştirme çatısı) ile servis geliştirme
2. Fiori / UI5 ön yüz geliştirme
3. SAP Build Code, Git, CI/CD, Cloud Transport Management (CTMS)
4. ABAP Cloud / RAP, side-by-side extensibility
> **İlgi (0–3):** BTP'de uygulama geliştirmede gelişmek ister misin?

## 3. Integration Suite
1. Cloud Integration (CPI) iFlow tasarımı
2. API Management (API yayınlama / koruma / izleme)
3. Advanced Event Mesh (olay-tabanlı mimari)
4. Adaptör / B2B / EDI senaryoları
> **İlgi (0–3):** Entegrasyon alanında gelişmek ister misin?

## 4. Build Apps (az-kodlu / citizen development)
1. SAP Build Process Automation (iş akışı + RPA)
2. SAP Build Work Zone (portal / launchpad)
3. Az-kodlu uygulama kurgusu
> **İlgi (0–3):** Az-kodlu çözüm/otomasyonda gelişmek ister misin?

## 5. BTP Core Services
1. Subaccount / entitlement / kota yönetimi
2. Cloud Connector kurulumu / HA
3. Destination, service key, XSUAA
4. HANA Cloud provisioning / yönetimi
5. Cloud ALM kurulumu / izleme
> **İlgi (0–3):** BTP çekirdek servislerinde gelişmek ister misin?

## 6. Rise Onboarding
1. SAP for Me ile sistem yönetimi, Service Request (SR) süreçleri
2. ECS ile sorumluluk paylaşımı, provizyon / refresh talepleri
3. DMO with System Move ile göç
4. RISE'a dahil Cloud ALM ile izleme kurulumu
> **İlgi (0–3):** RISE/ECS onboarding & operasyonunda gelişmek ister misin?

## 7. Yetkilendirme
1. Kullanıcı yaşam döngüsü (SU01/SU10), rol tasarımı (PFCG), öneri değerleri (SU24)
2. Yetki sorun giderme (SU53/ST01), SUIM analizleri
3. IAS/IPS ile cloud kimlik sağlama
4. CUA / merkezi kullanıcı yönetimi
> **İlgi (0–3):** Yetkilendirme alanında gelişmek ister misin?

## 8. SAP Güvenliği
1. Güvenlik notu yönetimi (SNOTE), parametreler, sertleştirme
2. Denetim kaydı (SM19/SM20, RSAU), Security Optimization Service (SOS)
3. SoD (görevler ayrılığı) risk analizi
4. ETD / Sentinel for SAP ile tehdit algılama; güvenlik sağlık taraması
5. *(Yeni dönem)* sıfır-gün hızlı yama, tedarik zinciri/CI-CD güvenliği, DORA, kuantum-güvenli kripto
> **İlgi (0–3):** SAP güvenliğinde gelişmek ister misin?

## 9. Veri Yönetimi
1. Tablo partitioning, HANA NSE, data tiering
2. Arşivleme (SARA) ve ILM (KVKK/GDPR)
3. Veri büyüme yönetimi (DVM), housekeeping
4. Backup & DR tasarımı (HSR replikasyon)
> **İlgi (0–3):** Veri yönetimi / TCO alanında gelişmek ister misin?

## 10. BDC (Business Data Cloud)
1. Cloud Connector & DP Agent ile on-prem veri bağlama
2. SDA / SDI (sanallaştırma / replikasyon), Remote Table Mapping
3. Spaces, grafiksel/SQL modelleme, Python veri akışları
4. SAC Live, SAML/RBAC, Joule & AI besleme
5. *(Yeni dönem)* zero-copy bağlayıcılar (Databricks/Snowflake/AWS), Data Product Studio
> **İlgi (0–3):** BDC / hibrit veri mimarisinde gelişmek ister misin?

---

## Açık uçlu sorular (sonda)
1. **En gurur duyduğun iş** neydi? (Hangi problem, hangi müşteri/sistem?)
2. **En çok merak ettiğin** SAP ürünü/alanı hangisi?
3. **En büyük engelin** ne? (zaman, erişim, eğitim, ortam…)

> Bu üç cevap birebirdeki "kaynak sorgulama / ilk adım" sorularına hazırlık ve `/proje`'nin
> dinamik önerisi için kritik girdidir.
