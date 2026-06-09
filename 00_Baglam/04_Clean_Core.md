# Clean Core — Temiz Çekirdek Stratejisi, ABAP → BTP Geçişi

> SAP'nin "standardı bozma, yanına yap" felsefesi: çekirdeği temiz tutarak yükseltmeyi ucuz ve AI'ı mümkün kılmak.

## 1. Bu nedir? (tek paragraf)

Clean Core (temiz çekirdek), S/4HANA'nın standart kodunu ve veri yapısını **değiştirmeden** bırakıp, ihtiyaç duyduğun özel geliştirmeleri sistemin onayladığı temiz yollarla yapma stratejisidir. Eski dünyada Z-kodlar (müşteriye özel, "Z" ile başlayan ABAP programları) doğrudan standardın içine girer, hatta SAP nesnelerini "modifikasyon" ile değiştirirdi; her yükseltmede bunlar kırılır, elle tamir edilirdi. Clean Core bunu tersine çevirir: özel mantık ya sistem içinde sadece **public (kamuya açık, sürüm garantili) arayüzler** üzerinden (in-app), ya da tamamen sistem dışında, BTP'de (SAP Business Technology Platform — SAP'nin bulut geliştirme platformu) **side-by-side** (yan tarafta, ayrı çalışan uygulama) inşa edilir. Çekirdek temiz kalınca yükseltme neredeyse otomatik, dokunulmadan geçer.

## 2. Neden önemli / nereye gidiyor?

Çünkü SAP herkesi RISE/bulut S/4HANA'ya taşıyor ve bulutta "standardı değiştirme" lüksü artık yok — sürekli güncellenen bir sistemde her modifikasyon bir borçtur. Clean Core bugün SAP'nin **1 numaralı mantrası**; RISE müşterilerinin işletme modelinin temeli ([Clean Core in RISE with SAP](https://thesiliconpartners.com/insights/clean-core-in-rise-with-sap/)). Daha kritik olan: AI ön koşulu olması. Joule (SAP'nin yapay zekâ asistanı) ve gelecek AI ajanları ancak **öngörülebilir, standart** bir sistemde güvenle çalışabilir; karmaşık özelleştirme AI'ı kör eder. Bu yüzden "2026'da Joule ajanlarının çalışması için ön koşul" olarak çerçeveleniyor ([Clean Core Strategy: What It Means](https://prolifics.com/usa/resource-center/blog/clean-core-strategy-in-sap)). SAP olgunluğu ölçülebilir hale de getirdi: RISE Dashboard'a Clean Core KPI'ları geldi ve bunlar sertifikasyona girdi ([SAP Certification in the AI Era](https://news.sap.com/2026/05/certification-ai-era-knowledge-capability/)).

## 3. Basis için ne anlama geliyor?

Bu salt geliştirici işi değil; Basis bunun **mimari ve yönetişim** tarafında. Bir müşteri sisteminin yükseltilebilir olup olmadığını, ne kadar teknik borç taşıdığını söyleyen kişi Basis'tir. Pratikte: Z-kod envanteri çıkarmak, bunları olgunluk seviyelerine göre sınıflamak, yükseltme riskini ölçmek, hangi kodun BTP'ye taşınacağına karar veren ekibe veri sağlamak. SAP bunu dört seviyeli bir **olgunluk modeli** ile standartlaştırdı ([SAP Clean Core Maturity Model A–D](https://www.sap.com/products/erp/rise/methodology/clean-core.html), [How to Extend S/4HANA Cloud the Right Way](https://news.sap.com/2025/08/extend-sap-s4hana-cloud-right-way-clean-clear/)):

- **A — Altın standart:** sadece public arayüzler; ABAP Cloud veya SAP Build ile. Yükseltme güvenli.
- **B — Klasik API'ler:** A kriterlerine ek olarak belgeli klasik API'ler. Genelde yükseltme-stabil.
- **C — İç nesnelere erişim:** eski senaryolar için SAP iç nesnelerine dokunur. **Yükseltme riski var**; SAP "Changelog for SAP Objects" ile uyumsuz değişiklikleri erken görmeyi sağlıyor.
- **D — Önerilmeyen:** modifikasyon, SAP tablolarına yazma, implicit enhancement. En yüksek risk, en yüksek borç.

Yükseltme sırasında bu envanteri yöneten araçlar yine Basis'in alanına girer (bkz. ../02_SAP_Haberleri/04_CleanCore_S4_Roadmap.md, S/4HANA 2025 Custom Code Migration Advisor).

## 4. Hangi somut beceriler gerekiyor?

- **ATC (ABAP Test Cockpit):** özel kodu statik olarak tarayıp S/4HANA uyumsuzluklarını işaretleyen SAP aracı. Simplification Database ile çalışır; bugün "ATC Explain" ile her bulguya AI açıklama + adım adım çözüm üretiyor.
- **Custom Code Migration App / Advisor:** taşınacak kod kapsamını belirleyip Cloud Connector üzerinden on-prem sistemi uzaktan analiz eder.
- **SCMON / Usage Procedure Logging:** hangi Z-kodun gerçekten kullanıldığını ölçer — kullanılmayanı taşımak yerine silmek en temiz remediation'dır.
- **In-app vs side-by-side ayrımını bilmek:** uzantıyı sistem içinde mi (BAdI, key user extensibility) yoksa BTP'de mi yapmak gerektiğine karar verebilmek.
- **ABAP Cloud** farkındalığı: kısıtlı, sadece public arayüzlere izin veren yeni ABAP modeli — Level A'nın temeli.

## 5. Hiç bilmiyorsam ilk adım

Bilmiyorsan normal; çoğu Basis'çi bunu yeni öğreniyor. Başlangıç: bir sistemde **SE38/SE80 yerine ATC çalıştır** ve "S/4HANA Readiness" ruleset'iyle bir Z-program tara — çıkan bulgulara ve ATC Explain açıklamalarına bak. Paralelde A–D modelini iki sayfada özümse: kendi sistemindeki 3-4 Z-objesini hangi seviyeye düştüğünü tahmin ederek pratik yap. Derinleşmek için ../02_SAP_Haberleri/04_CleanCore_S4_Roadmap.md dosyasındaki güncel haberleri ve SAP Learning'in ücretsiz "Clean Core Extensibility" kursunu kaynak al. Retro'da bunu somut bir fikre bağlamak istersen, "AI Custom Code / Clean Core Danışmanı" (ATC + SCMON + AI) fikri tam buraya oturuyor (ekibin iç kaynağı — paylaşılan repoda yer almaz, fikir ⑥).

## 6. Terimler sözlüğü (kısa)

- **Clean Core:** standardı bozmadan, temiz yollarla genişletme stratejisi.
- **In-app extensibility:** uzantıyı S/4HANA sistemin *içinde* (BAdI, key user araçları) yapmak.
- **Side-by-side extensibility:** uzantıyı sistemin *dışında*, BTP'de ayrı uygulama olarak yapmak.
- **ABAP Cloud:** sadece public, sürüm-garantili arayüzlere izin veren kısıtlı yeni ABAP modeli.
- **ATC:** özel kodu S/4HANA uyumu için statik tarayan denetim aracı.
- **Custom code remediation:** mevcut Z-kodu S/4HANA'ya uyumlu hale getirme/temizleme işi.
- **A–D olgunluk modeli:** uzantıları yükseltme güvenliğine göre A (en temiz) → D (en riskli) sıralayan çerçeve.
- **Joule:** SAP'nin yapay zekâ asistanı; temiz çekirdek onun ön koşulu (bkz. ../00_Baglam/03_AI_ve_Otomasyon.md).
