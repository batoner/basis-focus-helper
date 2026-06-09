# Yetkinlik Alanları Matrisi — Aktivite → 10 İş Kolu

> **Bu dosya köprüdür.** Yukarıdaki aktivite envanterini (`01`, `02`, `03`) retronun **10 iş
> koluna** bağlar. `/test` soruları buradan üretir; `/harita` skoru buradaki iş koluna oturtur.
>
> Her iş kolu altında **somut, işaretlenebilir aktiviteler** var (testte 0–4). Bir aktivite
> birden çok kola değebilir; o zaman **birincil** kola yazıp diğerine *(ayrıca …)* notu düşülür.

> **Olgunluk ölçeği (tüm aktiviteler için):**
> 0 Hiç duymadım · 1 Duydum, yapmadım · 2 Bir-iki kez yaptım · 3 Düzenli yapıyorum ·
> 4 Başkalarına öğretebilirim / tasarlayabilirim.
>
> *Güncel: bazı kollara 2025–2026 haber korpusundan ("yeni dönem" işaretli) aktiviteler eklendi.*

---

## Temel katman — Klasik Basis (tüm kolların altında)
*Çoğu kişinin güçlü olduğu zemin; tek başına bir "yeni dönem" iş kolu değil ama her şeyin temeli.*
- Kurulum/upgrade/transport/client (SWPM, STMS, SPAM, client copy/refresh)
- Performans & izleme (ST03N, ST22, SM37, RZ20), DB yedek/restore
- HA/DR tasarımı

---

## 1. AI
*SAP operasyonlarına yapay zekâ/otomasyon uygulamak.*
- Joule kullanımı/yapılandırması
- Generative AI Hub / AI Core ile dış LLM bağlama, orkestrasyon
- Agentic akış / RAG / prompt tasarımı (n8n, Build Process Automation dahil)
- Bir Basis işini AI ile otomatikleştirme (örn. dump triyajı, rapor üretimi)
- *Yeni dönem:* AI ajan yönetişimi/izleme, MCP sunucusu, model seçimi & AI Units takibi

## 2. BTP Development
*BTP üzerinde uygulama geliştirmek (Clean Core).*
- CAP (uygulama geliştirme çatısı) ile servis geliştirme
- Fiori / UI5 ön yüz geliştirme
- SAP Build Code, Git, CI/CD; **Cloud Transport Management (CTMS)** *(ayrıca BTP Core)*
- ABAP Cloud / RAP, side-by-side extensibility

## 3. Integration Suite
*Sistemleri/servisleri birbirine bağlamak.*
- Cloud Integration (CPI) iFlow tasarımı
- API Management (API yayınlama/koruma)
- Advanced Event Mesh (olay tabanlı mimari)
- Adaptör/B2B/EDI senaryoları

## 4. Build Apps
*Az-kodlu (low-code) uygulama ve süreç otomasyonu — "citizen development".*
- SAP Build Process Automation (iş akışı + RPA)
- SAP Build Work Zone (portal/launchpad) *(ayrıca BTP Core)*
- Az-kodlu uygulama kurgusu
- *(Not: "SAP Build Apps" ürünü 23 Mart 2026'da emekliye ayrıldı; pratik ağırlık Process
  Automation / Work Zone / Fiori tarafına kaydı. İş kolu olarak "az-kodlu çözüm" canlı.)*

## 5. BTP Core Services
*Platformun çekirdek teknik servisleri — Basis'in cloud'daki doğal evi.*
- Subaccount / entitlement / kota yönetimi
- Cloud Connector kurulumu/HA
- Destination, service key, **XSUAA** *(ayrıca Yetkilendirme)*
- HANA Cloud provisioning/yönetimi
- Cloud ALM kurulumu/izleme *(ayrıca Rise Onboarding)*

## 6. Rise Onboarding
*Müşteriyi RISE/Private Cloud'a almak ve işletmek.*
- SAP for Me ile sistem yönetimi, **Service Request (SR)** süreçleri
- ECS ile sorumluluk paylaşımı, provizyon/refresh talepleri
- DMO with System Move ile göç
- RISE'a dahil Cloud ALM ile izleme kurulumu

## 7. Yetkilendirme
*Kullanıcı ve rol/yetki yönetimi.*
- Kullanıcı yaşam döngüsü (SU01/SU10), rol tasarımı (PFCG), öneri değerleri (SU24)
- Yetki sorun giderme (SU53/ST01), SUIM analizleri
- IAS/IPS ile cloud kimlik sağlama *(ayrıca BTP Core / SAP Güvenliği)*
- CUA / merkezi kullanıcı yönetimi

## 8. SAP Güvenliği
*Sistemi tehditlere ve uyumsuzluğa karşı korumak.*
- Güvenlik notu yönetimi (SNOTE), güvenlik parametreleri, sertleştirme
- Denetim kaydı (SM19/SM20, RSAU), Security Optimization Service (SOS)
- SoD (görevler ayrılığı) risk analizi
- ETD / Sentinel for SAP ile tehdit algılama; güvenlik sağlık taraması
- *Yeni dönem:* sıfır-gün hızlı yama, tedarik zinciri/CI-CD güvenliği, DORA uyumu, kuantum-güvenli kripto

## 9. Veri Yönetimi
*Veriyi ucuz, hızlı ve uyumlu tutmak (TCO).*
- Tablo partitioning, HANA NSE, data tiering
- Arşivleme (SARA) ve ILM (KVKK/GDPR)
- Veri büyüme yönetimi (DVM), housekeeping
- Backup & DR tasarımı (HSR replikasyon) *(ayrıca Klasik Basis)*

## 10. BDC (Business Data Cloud)
*Veriyi taşımadan analitiğe/AI'a açmak — hibrit veri mimarisi.*
- Cloud Connector & **DP Agent** ile on-prem veri bağlama
- SDA / SDI (sanallaştırma / replikasyon), Remote Table Mapping
- Spaces, grafiksel/SQL modelleme, Python veri akışları
- SAC Live, SAML/RBAC, Joule & AI besleme (vektör engine)
- *Yeni dönem:* zero-copy bağlayıcılar (Databricks/Snowflake/AWS), Data Product Studio yönetişimi

---

## Hızlı bakış: çakışan aktiviteler (birincil → ikincil)
| Aktivite | Birincil iş kolu | Ayrıca |
|---|---|---|
| XSUAA / rol koleksiyonu | BTP Core Services | Yetkilendirme |
| IAS / IPS | BTP Core Services | Yetkilendirme · SAP Güvenliği |
| Cloud ALM kurulumu | BTP Core Services | Rise Onboarding |
| Cloud Transport Mgmt | BTP Development | BTP Core Services |
| Cloud Connector | BTP Core Services | BDC |
| Backup & DR | Klasik Basis | Veri Yönetimi |
| Work Zone | Build Apps | BTP Core Services |

> Bu çakışmalar puanlamada **çift sayım yapılmadan** ele alınır: aktivite birincil kola
> yazılır, ikincil kol "ilgi/komşuluk" sinyali olarak `/harita`da dikkate alınır.
