# Basis Nereye Evriliyor — Genel Bakış

> Bu dosya `00_Baglam/` klasörünün giriş kapısıdır: hem kısa bir manifesto, hem de
> "hangi alana nereden bakacağım?" diye yön bulduran bir haritadır. `/start` komutu
> teste başlamadan önce buradan okur.

---

## Basis nereye evriliyor?

Klasik Basis işi — *SAP sistemlerinin teknik temelini kurup işleten, güvende tutan
mühendislik* (bkz. `../03_Basis_Operasyonlari/00_Basisci_Ne_Yapar.md`) — ortadan
kalkmıyor. Yedekler, transport'lar, yamalar, performans hâlâ birinin işi. Ama ağırlık
hızla yön değiştiriyor. SAP, müşterilerini buluta (S/4HANA Cloud) ve yapay zekâya
taşırken Basis de "**sistemi ayakta tutan operatör**"den; "**BTP'de uygulama geliştiren,
AI'ı entegre eden ve bulut maliyetini yöneten platform mühendisi / otomasyon
tasarımcısı**"na doğru genişliyor. (Bu çerçeve doğrudan retro taahhüt dokümanının giriş
paragrafından gelir — bkz. `06_Taahhut_Sablonu/Ornek_Anonim.md`.)

İki güç bu kaymayı zorluyor. Birincisi **takvim**: ECC 6.0'ın ana bakımı (EHP 6–8)
31 Aralık 2027'de bitiyor; göçler 18–36 ay sürdüğü için pratikte 2026 son makul başlama
penceresi. İkincisi **AI'ın çekirdeğe girmesi**: SAP, Sapphire 2026'da "Otonom İşletme"
vizyonunu ve 200'den fazla uzman ajanı tanıttı; bu ajanlar artık kurumsal verinin
içinde gerçek aksiyon alıyor. Yani bir Basis mühendisi için soru "buluta/AI'a geçecek
miyim" değil; "**bu yeni yüzeyde neyi iyi yapacağım**". Hiçbirini bilmiyorsan normal —
bu klasör tam olarak başlangıç noktanı bulman için var.

Kanıt olarak üç gerçek haber:
[ECC bakım bitişine uzatma yok (Rimini Street, 2025)](https://www.riministreet.com/blog/no-extension-to-ecc-support-2027-deadline/) ·
[SAP & Anthropic — Claude'u Joule'a getiriyor (SAP News, 2026-05)](https://news.sap.com/2026/05/sap-anthropic-to-bring-claude-sap-business-ai-platform/) ·
[Clean Core'u doğru kurmak (SAP News, 2025-08)](https://news.sap.com/2025/08/extend-sap-s4hana-cloud-right-way-clean-clear/).
(Daha fazlası için bkz. `../02_SAP_Haberleri/00_INDEX.md` — 101 doğrulanmış haber.)

---

## 9 alanın haritası

Bu klasördeki 9 dosyanın her biri tek bir evrim ekseninidir. Hepsi aynı 6 parçalı
yapıyı izler (nedir · nereye gidiyor · Basis için anlamı · gereken beceriler · ilk adım ·
terimler), böylece hızlı tarayıp kendine en yakın alanı seçebilirsin.

1. **[Cloud Dönüşümü](01_Cloud_Donusumu.md)** — RISE (Private Cloud/ECS), GROW (Public
   Cloud), hyperscaler'lar ve Basis'in değişen sorumluluk sınırı. *Tüm dönüşümün zemini.*
2. **[BTP Platformu](02_BTP_Platformu.md)** — Business Technology Platform: hesap
   hiyerarşisi, CAP/Fiori/Build, destination/service key/XSUAA. *Yeni operasyon yüzeyi.*
3. **[AI ve Otomasyon](03_AI_ve_Otomasyon.md)** — Joule, Generative AI Hub, agentic AI,
   RPA; "AI'ı *neye* uygulayacağını bilmek" farkı. *Ekibin stratejik yönü.*
4. **[Clean Core](04_Clean_Core.md)** — çekirdeği bozmadan özel kodu BTP'ye taşıma
   stratejisi; SAP'nin 1 numaralı mantrası ve AI ajanlarının ön koşulu.
5. **[Integration Suite](05_Integration_Suite.md)** — bulut entegrasyon platformu (CPI,
   API Management, Advanced Event Mesh) ve mesaj-başı maliyet nüansı.
6. **[Güvenlik ve Kimlik](06_Guvenlik_ve_Kimlik.md)** — IAS/IPS, SSO, SoD, ETD ve
   MSSP/SOC vizyonu. *Buluta geçince kimlik yeni çekirdek.*
7. **[Veri Yönetimi ve BDC](07_Veri_Yonetimi_BDC.md)** — HANA Cloud, Datasphere,
   Business Data Cloud, arşiv/ILM. *AI'ın beslendiği veri temeli.*
8. **[Observability ve Cloud ALM](08_Observability_CALM.md)** — Solution Manager'ın
   emekliliği (2027/2030) ve Cloud ALM'e geçiş; izlenebilirlik.
9. **[FinOps ve Maliyet](09_FinOps_Maliyet.md)** — CPEA tüketim modeli, UDMS API'si,
   bulut maliyet optimizasyonu. *Basis'in en yeni ve en somut işi.*

**Önerilen okuma sırası.** Acele etmeden iki turda:
- **Önce zemin:** 1 → 2 (cloud nereye gidiyor + üzerinde ne inşa ediliyor).
- **Sonra ilgi alanına dal:** AI/otomasyon istiyorsan 3 → 4 → 5; güvenlik/veri istiyorsan
  6 → 7; operasyon/maliyet tarafı istiyorsan 8 → 9.

Seçilen iş kolları ile bu alanlar birebir örtüşür: ekibin "Servis & Otomasyon" hattı
3-4-5'e, örnek taahhüt dokümanı ise 2-9 (BTP + maliyet) eksenine oturur
(bkz. `../01_Sunum_Ozetleri/Servis_Otomasyon.md`).

---

## Bu klasör nasıl kullanılır?

Amaç ezberlemek değil, **kendi yönünü seçmek**. Retroda senden ≤3 iş kolu seçip üç
mercekten (pazar · yetkinlik · katkı) gerekçelendirmen ve 3 aylık ölçülebilir bir taahhüt
vermen isteniyor (bkz. `../01_Sunum_Ozetleri/Yetkinlik_Haritasi_brief.md`). Bu dosyalar o
gerekçeyi besler:

- **Tarayarak başla** — 9 başlığı oku, sana en çok "bunu yapabilirim / yapmak isterim"
  dedirteni 1-3 tanesini işaretle.
- **Derinleş** — seçtiğin dosyaların "ilk adım" ve "gereken beceriler" bölümlerine bak;
  taahhüdünü buradan somutlaştır.
- **Kanıtla** — her iddianı `../02_SAP_Haberleri/` altındaki gerçek haberle destekle;
  uydurma sayı/URL kullanma.

Hiçbir alanda derin olmaman normal — kimse hepsini yapmaz. Bu harita, boşluğunu
kapatman için değil, **güçlü olduğun yöne bilinçli yatırım yapman** için var.
