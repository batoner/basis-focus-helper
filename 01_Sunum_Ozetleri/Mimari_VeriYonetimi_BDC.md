# Çözüm & Mimari Takımı — Veri Yönetimi + BDC

> İş kolları: **Veri Yönetimi · BDC (Business Data Cloud)** — ikisi de sunumda **"Yeni Odak!"**
> Kaynak: retro sunumu "Mimari" (görsel-içi metinler dahil).

## Ana mesaj

İki ayrı ama bağlantılı yön: (1) mevcut veriyi **ucuz, hızlı, uyumlu** tutmak; (2) veriyi
buluta taşımadan analitiğe/AI'a açmak.

### Veri Yönetimi (TCO odaklı) — *donanım maliyetini düşür, performansı koru*
- **Veri Yönetimi & Mimari:** Table Maintenance (çok seviyeli partitioning), HANA NSE (sıcak/ılık
  veri katmanları), Data Tiering (NSE/ILM/Dynamic Tiering), Backup & DR (RTO/RPO uyumlu HSR replikasyonu).
- **Proaktif Housekeeping:** büyüme/trend analizi + kapasite planlama, gereksiz indeks temizliği,
  Cloud ALM/SolMan ile teknik izleme, log/trace otomatik temizlik.
- **Arşivleme & ILM:** SARA arşiv stratejisi, S/4HANA hazırlığı için veri küçültme, ILM
  (KVKK/GDPR — yasal saklama + imha), Content Server entegrasyonu.
- *(TCO: toplam sahip olma maliyeti. ILM: bilgi yaşam döngüsü yönetimi.)*

### BDC — Business Data Cloud — *veriyi taşımadan analitiğe/AI'a aç*
- **Mimari & Bağlantı:** Cloud Connector & **DP Agent** ile on-prem S/4HANA'ya güvenli tünel;
  **SDA/SDI** (veriyi taşımadan sanallaştırma / anlık replikasyon); Remote Table Mapping.
- **Modelleme Katmanı:** Spaces (izole sanal çalışma alanları), grafiksel & SQL view'lar,
  Python tabanlı veri akışı/dönüşümü.
- **Güvenlik & Uç Nokta:** SAML 2.0 & satır bazlı yetki (RBAC), **SAC Live** (veriyi tarayıcı
  dışına çıkarmadan görselleştirme), **Joule & AI** entegrasyonu (vektör engine ile LLM beslemesi).

## Senin için fırsat nerede?

HANA, veri mimarisi, arşivleme veya bağlantı/entegrasyona ilgin varsa burası. **Önemli nüans:**
BDC'nin "Mimari & Bağlantı" sütunu (Cloud Connector, SDA/SDI, SAC Live) çoğu deneyimli Basis
mühendisinin zaten yaptığı işle örtüşür — yani buraya giriş eşiği düşük olabilir. Tipik giriş
hamleleri: bir housekeeping/arşiv stratejisi çıkarmak, bir BDC bağlantı mimarisini PoC'lemek.
