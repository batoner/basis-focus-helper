# Güvenlik & Uyumluluk — Haberler

> Format: **[Başlık](URL)** — *Kaynak, tarih.* Özet. **Basis için:** anlamı. `Etiket`
> Not: vendor (Onapsis, SecurityBridge vb.) blogları kaynak gösterildiğinde istatistikler o kaynağın iddiasıdır.
> `community.sap.com`/`help.sap.com` bağlantıları otomatik araçlara 403 dönebilir; tarayıcıda açılır.

1. **[Active Exploitation of SAP Vulnerability CVE-2025-31324](https://onapsis.com/blog/active-exploitation-of-sap-vulnerability-cve-2025-31324/)** — *Onapsis Research Labs, 2025-04.*
   NetWeaver Visual Composer'da kimlik doğrulama eksikliği (CVSS 10.0) aktif olarak istismar edildi; saldırganlar yetkisiz dosya yükleyerek sistemi ele geçirebildi, 24 Nisan'da yamalandı. **Basis için:** Visual Composer içeren Java sistemlerini kontrol et, acil yama uygula. `Etiket: Güvenlik`

2. **[The Year of the Zero-Day: Top SAP Vulnerabilities of 2025 — 2026 Watchlist](https://onapsis.com/blog/sap-vulnerabilities-2025/)** — *Onapsis, 2025-12.*
   2025'te SAP tehdit ortamı kalıcı değişti: sıfır-gün açıkları açıklamadan saatler içinde silahlandırıldı; çok sayıda HotNews/yüksek-öncelik notu. **Basis için:** aylık yama döngüsü yetmez; sıfır-gün için acil müdahale protokolü kurmak gerekir. `Etiket: Güvenlik`

3. **[SAP Security Notes 2025: A Year of Intensifying Critical Risks](https://drj.com/industry_news/sap-security-notes-2025-a-year-of-intensifying-critical-risks/)** — *Disaster Recovery Journal, 2025-12.*
   2025'te yayımlanan güvenlik notu sayısı belirgin arttı; çok sayıda CVSS ≥9.0 HotNews notu çekirdek bileşenleri etkiledi. **Basis için:** SAP Patch Day'leri yakından izlemek, HotNews'i önceliklendirmek. `Etiket: Güvenlik`

4. **[SAP-Related npm Packages Compromised in Credential-Stealing Supply Chain Attack](https://thehackernews.com/2026/04/sap-npm-packages-compromised-by-mini.html)** — *The Hacker News, 2026-04.*
   "Mini Shai-Hulud" kampanyası dört SAP npm paketini (mbt, @cap-js/db-service, -postgres, -sqlite) ele geçirip preinstall hook ile geliştirici kimlik bilgilerini/token'ları çaldı; dikkat çekici olarak `.claude/settings.json` ve `.vscode/tasks.json` enjekte ederek AI kodlama ajanı yapılandırmalarını hedefledi. **Basis için:** BTP/CAP ekiplerine npm paket bütünlüğü, preinstall hook denetimi ve CI/CD güvenlik kontrolü uyarısı. `Etiket: Güvenlik`

5. **[SAP Security Patch Day — January 2026 (HANA Privilege Escalation)](https://securitybridge.com/blog/sap-security-patch-day-january-2026/)** — *SecurityBridge, 2026-01.*
   HANA 2.0 SP7/SP8'de ayrıcalık yükseltme açığı (Security Note 3691059) ve aynı günde SQL Anywhere Monitor'da kritik bir açık yamalandı. **Basis için:** HANA Support Package güncellemelerini kontrol etmek; SQL Anywhere/HANA entegrasyonunda izleme. `Etiket: Güvenlik`

6. **[SAP Patches Critical S/4HANA & Commerce Vulnerabilities](https://www.securityweek.com/sap-patches-critical-s-4hana-commerce-vulnerabilities/)** — *SecurityWeek, 2026-05.*
   SAP Commerce/S-4HANA tarafında kritik açıklar (kod yürütme riski) yamalandı; canlı sipariş/ödeme akışları risk altındaydı. **Basis için:** Commerce kullanan kuruluşlarda yama aciliyeti ve işlem izleme için ETD değerlendirmesi. `Etiket: Güvenlik`

7. **[SAP Security 2026 Predictions: The Year of Acceleration](https://securitybridge.com/blog/sap-security-2026-predictions/)** — *SecurityBridge, 2025-12.*
   2026'da kritik açıkların artacağı, istismarların AI ile hızlanacağı ve Basis rollerinin "platform mühendisi"ne dönüşeceği öngörüldü. **Basis için:** acil yama, RISE paylaşılan sorumluluk ve CI/CD'ye güvenlik katmaya hazırlık. `Etiket: Güvenlik`

8. **[RISE with SAP Security: Understanding Shared Responsibility](https://securitybridge.com/blog/rise-with-sap-security/)** — *SecurityBridge, 2025-01.*
   RISE'de müşteri uygulama güvenliği, kimlik, erişim ve uyumluluktan; SAP altyapı güvenliğinden sorumlu. **Basis için:** RISE'de müşteri tarafı kontrolleri (kimlik, özel kod güvenliği, konfigürasyon, tehdit izleme) kurmak. `Etiket: Güvenlik`

9. **[SAP Cloud Identity Services — SCIM API v1 Decommissioning](https://help.sap.com/docs/identity-provisioning/identity-provisioning/proxy-identity-authentication)** — *SAP Help, 2025-06.*
   Identity Authentication SCIM API v1 ve eski temel kimlik doğrulama entegrasyonları kullanımdan kaldırılıyor; SCIM 2.0'a geçiş gerekli. **Basis için:** IAS ile SCIM 2.0'a geçişi planlamak; eski entegrasyonları kapatmak. `Etiket: Güvenlik`

10. **[SAP SuccessFactors — Basic Authentication End of Life](https://help.sap.com/docs/successfactors-platform/implementing-security-features-for-sap-successfactors/sap-successfactors-security-recommendations)** — *SAP Help, 2025-06.*
    SuccessFactors'ta temel kimlik doğrulama ve eski SOAP API'ler kullanımdan kaldırılıyor; Cloud Identity Services'e geçiş zorunlu. **Basis için:** IAS'a geçiş, OData API göçü ve yeni güvenlik özelliklerini açma. `Etiket: Güvenlik`

11. **[The Ultimate SAP BTP Security Guide for 2025 (KMS, Quantum-Safe)](https://securitybridge.com/blog/sap-btp-security-guide/)** — *SecurityBridge, 2025-07.*
    BTP'de Application Vulnerability Report (beta), Key Management Service (KMS) ve kuantum-güvenli kriptografi tanıtıldı. **Basis için:** BTP'de müşteri-kontrollü şifreleme, KMS ve kimlik API'lerini değerlendirmek. `Etiket: Güvenlik`

12. **[SAP GRC for SAP HANA — Early Adopter Care Program](https://community.sap.com/t5/financial-management-blog-posts-by-sap/sap-grc-for-sap-hana-early-adopter-care-program-is-open/ba-p/14233031)** — *SAP Community, 2026-03.*
    S/4HANA/HANA üzerine inşa edilen yeni nesil GRC (Access/Process Control + Risk Management) erken-benimseyen programıyla geliyor. **Basis için:** yetki yönetimi, SoD denetimi ve uyumluluk raporlamasında yeni GRC platformu. `Etiket: Güvenlik`

13. **[DORA Enforcement in 2026: What It Means for SAP Landscapes](https://onapsis.com/blog/dora-enforcement-2026-sap-landscapes/)** — *Onapsis, 2026-05.*
    DORA (Dijital Operasyonel Dayanıklılık Yasası, 17 Ocak 2025'te yürürlükte) finansal kurumlardan sürekli izleme, düzenli yamalama, denetim kaydı saklama ve raporlama istiyor. **Basis için:** sistem sertleştirme, kimlik yönetimi, denetim kaydı saklama ve kesintisiz güvenlik izleme. `Etiket: Güvenlik`

14. **[New Access Risks, New SoD Matrix: How S/4HANA Changes the Approach](https://community.sap.com/t5/financial-management-blog-posts-by-members/new-access-risks-new-sod-matrix-how-s-4hana-changes-the-approach-to/ba-p/14298296)** — *SAP Community, 2025-10.*
    S/4HANA geçişinde SoD matrisi yeniden değerlendirilmeli; Joule'ün geniş erişimli kullanıcılarda çakışma riski yaratabileceği vurgulandı. **Basis için:** görev-bazlı rol tasarımı ve AI-aracılı çakışma risklerini kapsayan yetki kontrolleri. `Etiket: Güvenlik`

15. **[Protecting SAP Systems in the Cybersecurity Era](https://www.isaca.org/resources/news-and-trends/industry-news/2025/protecting-sap-systems-in-the-cybersecurity-era)** — *ISACA, 2025-11.*
    SAP sistemlerini korumada genel strateji ve CVE-2025-31324 örneği; sıfır-güven ve SAP-spesifik protokollerin (DIAG, RFC, ICF) güvenliği vurgulanıyor. **Basis için:** RFC/SAP protokol güvenliği ve RISE ortamlarında sıfır-güven ilkeleri. `Etiket: Güvenlik`

16. **[SAP Cryptographic Library 8.6: Quantum-Safe TLS 1.3 for NetWeaver](https://community.sap.com/t5/technology-blog-posts-by-sap/new-version-8-6-of-the-sap-cryptographic-library-with-quantum-safe/ba-p/14280039)** — *SAP Community, 2025-09.*
    CommonCryptoLib 8.6, NetWeaver ABAP'ta kuantum-güvenli TLS 1.3 ve FIPS 140-3 modu sağlıyor (tam PQC geçişi sürüyor). **Basis için:** kuantum-güvenli kriptografiye geçişte CommonCryptoLib 8.6 değerlendirmesi. `Etiket: Güvenlik`
