# İhtiyaç & Fırsat Alanları — İş Kolu Bazlı

> **Menü değil, bağlam.** `/proje` bunları okuyup öneriyi DİNAMİK üretir; "3 Aylık Çıktı" birer ÖRNEKTİR.
> Okuma kılavuzu: `00_Katalog_Nasil_Okunur.md` · Eşleme/karar mantığı: `02_Test_Sonucu_Proje_Eslesmesi.md`.
>
> **Bu bir örnek katalogdur:** haber korpusu + alan bağlamı + operasyon + sunum özetleri + fikir
> havuzundan damıtılmış, çeşitli iş kollarında **örnek** ihtiyaç/fırsat fikirleri. Kesin/bitmiş bir
> liste değil; ilham ve dayanak havuzudur.
>
> **Yöneticiler için:** Her kartta bir **Değer/Etki** satırı var — oylama gerekçesi. Her fikir gerçek bir
> **Dayanak**'a (corpus "Haber #N" / sunum / gerçek SAP ürün yeteneği) bağlıdır; uydurma kaynak yoktur.
> Yine de bunlar **fikir**dir, taahhüt değil — birebirde kişinin kendi bağlamıyla somutlaştırması beklenir.

---

## AI

### Runbook & SAP Notu Soru-Cevap Asistanı (RAG PoC)
- İş kolu: AI · Zorluk: Başlangıç
- İhtiyaç: Operasyon bilgisi runbook'lar, ServiceNow geçmişi ve SAP notlarına dağılmış; nöbetçi mühendis aynı bilgiyi her seferinde elle arıyor.
- Değer/Etki: "Bu hatada ne yapmıştık?" sorusuna kaynak gösteren hızlı cevap; yeni ekip üyesinin devreye girme süresini kısaltır ve ekibin iç otomasyon örneğindeki verinin doğal devamıdır. Düşük risk, hızlı somut çıktı.
- Dayanak: 03_AI_ve_Otomasyon.md madde 4 (RAG ile runbook/SAP notu Q&A) + Fikir Havuzu ④ Operasyon Bilgi Ajanı.
- 3 Aylık Çıktı (ölçülebilir): Seçili runbook seti üzerinde çalışan RAG demosu + 20 gerçek soruda doğruluk/kaynak-gösterme başarı oranı raporu.
- Gerekli yetkinlik: RAG temeli (belge gömme/arama), HANA Cloud vektör veya basit vektör deposu; yoksa önce "RAG nedir + embedding" öğren.

### Generative AI Hub Model Seçim & AI Units Maliyet Panosu
- İş kolu: AI · Zorluk: Orta
- İhtiyaç: GenAI Hub artık GPT 5.2, Gemini 3.0, Claude Opus/Sonnet 4.6 ve Perplexity'yi birlikte sunuyor; hangi senaryoda hangi model ve ne kadar AI Units tüketildiği izlenmeden maliyet kontrolsüz büyür.
- Değer/Etki: Model seçimini maliyet/performansa göre yönetmek doğrudan Basis sorumluluğu; gereksiz pahalı model çağrısını ayıklayarak somut FinOps kazanımı sunar. Kullanıcının BTP maliyet panosu tezine doğrudan oturur.
- Dayanak: Haber #3 (çoklu temel model + AI Units lisanslaması) + Cloud_Operasyonlar.md madde 8 (model seçimi ve AI Units tüketim takibi).
- 3 Aylık Çıktı (ölçülebilir): GenAI Hub kullanımını model bazında AI Units olarak gösteren ilk pano + senaryo-model eşleme önerisi (en az 3 senaryo için).
- Gerekli yetkinlik: AI Core/GenAI Hub konfigürasyonu, destination/service key, tüketim verisi okuma; yoksa önce GenAI Hub kurulumunu öğren.

### MCP Sunucusu ile S/4HANA'ya Güvenli Ajan Bağlantısı PoC
- İş kolu: AI · Zorluk: Orta
- İhtiyaç: SAP, Claude'u Joule ajanlarına MCP (Model Context Protocol; AI'ı kurumsal sisteme bağlayan açık standart) üzerinden bağlıyor; bu bağlantıyı kurumsal kontrol çerçevesinde güvenle kurmak Basis'in yeni işi ama ekipte uygulamalı tecrübe yok.
- Değer/Etki: MCP, SAP'nin agentic mimarisinin omurgası; bunu erken kuran ekip "ajanı sisteme kim güvenle bağlayacak" sorusunun cevabı olur — net farklılaşma.
- Dayanak: Haber #1 (Claude + MCP ile S/4HANA/SuccessFactors/Ariba) + Haber #5 (HANA Cloud MCP desteği GA) + Cloud_Operasyonlar.md madde 8 (MCP sunucusu kurulumu).
- 3 Aylık Çıktı (ölçülebilir): HANA Cloud veya bir SAP sistemine MCP üzerinden bağlanıp salt-okunur sorgu yapan çalışan PoC + bağlantı/yetki güvenlik notu.
- Gerekli yetkinlik: MCP kavramı, destination/principal propagation, XSUAA yetkilendirme; yoksa önce MCP + HANA Cloud MCP server dokümanını çalış.

### AI Ajan Envanteri & Yönetişim Panosu (AI Agent Hub Hazırlığı)
- İş kolu: AI · Zorluk: Orta
- İhtiyaç: Sapphire 2026 ile onlarca Joule asistanı ve 200+ uzman ajan geliyor; bunları kimin keşfedip izleyeceği, onay döngüsü ve denetim logu (audit trail) olmadan kontrolsüz çoğalır.
- Değer/Etki: Yönetişim, SAP'nin "beş kritik eşik"inden biri ve doğrudan Basis sorumluluğu; "ajanları yöneten katman bizde" tezi yönetici için güçlü oy gerekçesi.
- Dayanak: Haber #2 (Otonom İşletme, çok-ajanlı yönetişim) + 03_AI_ve_Otomasyon.md madde 3 (SAP AI Agent Hub: keşif, insan onay döngüsü, audit trail) + Haber #11 (yönetişim eşiği).
- 3 Aylık Çıktı (ölçülebilir): Mevcut/planlı ajanları listeleyen envanter panosu + her ajan için sahip/veri erişimi/onay gereksinimi içeren yönetişim kontrol-listesi (ilk sürüm).
- Gerekli yetkinlik: AI ajan yönetişimi/izleme, denetim logu mantığı, BTP rol koleksiyonları; yoksa önce AI Agent Hub yeteneklerini incele.

### Joule Studio'da İlk Özel Basis Ajanı (No-Code/Pro-Code)
- İş kolu: AI · Zorluk: Orta
- İhtiyaç: Joule Studio GA oldu ve n8n ile görsel orkestrasyonu destekliyor; özel ajan/iş akışı geliştirme ortamının altyapısı ve yönetişimi Basis'e düşüyor ama ekipte Joule Studio'da üretilmiş çıktı yok.
- Değer/Etki: Takımın "AI-native, BTP'de ürün geliştiren" hedefine somut ilk adım; SAP n8n'i Joule Studio'ya gömdüğü için ekibin iç otomasyon örneğinde kazanılan beceri doğrudan SAP-native platforma taşınır.
- Dayanak: Haber #8 (Joule Studio enterprise-scale agentic dev, n8n orkestrasyon) + Haber #9 (SAP'nin n8n yatırımı, Joule Studio'ya gömme) + Sunum hedef "AI-native kültür".
- 3 Aylık Çıktı (ölçülebilir): Joule Studio'da kurulmuş, bir Basis görevini yapan tek ajan PoC + no-code vs pro-code karşılaştırma notu.
- Gerekli yetkinlik: Joule Studio temeli, agentic akış mantığı, n8n; yoksa önce Joule Studio quick-start.

### Joule for Developers ile Custom Code / Clean Core Refactor Asistanı
- İş kolu: AI · Zorluk: İleri
- İhtiyaç: S/4 dönüşümlerinde Z-kodun uyumluluğu ve Clean Core'a uygun side-by-side refactor'u elle yapılan, yavaş bir iş; Joule for Developers ABAP AI yetenekleri bunu hızlandırabilir.
- Değer/Etki: Clean Core SAP'nin 1 numaralı mantrası ve aktif S/4 projelerinde doğrudan satılabilir hız kazanımı; corpus'ta "en kolay savunulan" fikirlerden biri.
- Dayanak: Haber #10 + #15 + #16 (Joule for Developers ABAP AI, S/4HANA Cloud Private Edition) + Fikir Havuzu ⑥ Custom Code/Clean Core Danışmanı.
- 3 Aylık Çıktı (ölçülebilir): Bir Z-program seti üzerinde ATC + AI ile uyumsuzluk tespiti + refactor önerisi raporu (en az N obje, öncesi/sonrası ölçüsü).
- Gerekli yetkinlik: ABAP/ATC, Clean Core ilkeleri, Joule for Developers; yoksa önce ABAP Cloud + ATC ile başla.

### Dump & Kök-Neden Analizcisi (AIOps PoC)
- İş kolu: AI · Zorluk: İleri
- İhtiyaç: ST22 dump + SM21 syslog + trace verisi elle korele edilip tekrarlayan kök-nedenler her seferinde yeniden bulunuyor; Cloud ALM/SolMan sinyalleri triage için otomatize değil.
- Değer/Etki: MSP "Run" modeline doğrudan değer; corpus'ta "3 ayda en somut demolanabilir" işaretli — yöneticiye gösterilebilir, kanıtlı bir çıktı sunar.
- Dayanak: Fikir Havuzu ⑬ Dump & Kök-Neden Analizcisi + ② AIOps + Cloud_Operasyonlar.md madde 5 (Cloud ALM exception/health monitoring).
- 3 Aylık Çıktı (ölçülebilir): Dump/syslog verisini okuyup tekrarlayan kök-nedeni gruplayan ve ilgili SAP notuna bağlayan demo + bir sistemde doğruluk değerlendirmesi.
- Gerekli yetkinlik: ST22/SM21 yorumlama, log toplama, LLM ile sınıflandırma + RAG (SAP notu eşleme); yoksa önce log toplama akışını kur.

### RISE/ECS Yarı-Otomatik Service Request Hazırlayıcı
- İş kolu: AI · Zorluk: İleri
- İhtiyaç: Private Cloud/ECS işleri Service Request (SR) ile yürüyor; SR açma için public API yok, bu yüzden saf otomasyon kırılgan/risklidir — ama SR içeriğini hazırlamak hâlâ tamamen elle yapılıyor.
- Değer/Etki: Deneyim takımının RISE/MSP tezine birebir oturur ve kullanıcının ECS deneyimini farklılaşmaya çevirir; "tehlikeli otomasyonu zorlamadan değer üretmek" olgun bir reframe — güçlü retro tezi adayı.
- Dayanak: Fikir Havuzu ⑮ (KBA 3554766: SR için public API yok) + Cloud_Operasyonlar.md madde 6 (SAP for Me, SR, ECS RACI).
- 3 Aylık Çıktı (ölçülebilir): Sık SR türleri için AI ile ön-doldurulmuş, insan onayıyla portala basılacak SR şablon seti (en az 3 tür) + el emeği azalma ölçümü.
- Gerekli yetkinlik: ECS/SAP for Me SR süreçleri, ITSM (ServiceNow) şablonlama, LLM ile metin üretimi; UI-RPA ile tam otomasyona GİRME (ToS riski).

---

## BTP Development

### CAP "Hello-to-Prod" Hızlı Başlangıç İskeleti (Starter Kit)
- İş kolu: BTP Development · Zorluk: Başlangıç
- İhtiyaç: Ekipte BTP geliştirme yüzeyi (CAP/Fiori/Cloud Foundry) yeni; her iş sıfırdan kuruluyor, Clean Core uyumlu tekrar kullanılabilir bir başlangıç şablonu yok.
- Değer/Etki: Yeni proje kurulumunu günlerden saatlere indirir; XSUAA rol koleksiyonu, destination, mta.yaml ve env-credential disiplini hazır gelir, ekip aynı standarttan başlar. Yöneticiye: tekrar eden kurulum kaybını kapatan, yeniden kullanılabilir iç hızlandırıcı (IP).
- Dayanak: BTP Platformu bağlamı §4-5 (CAP + Fiori/UI5 + SAP Build ana yol; SAP Build Apps emekliye ayrılıyor) · Haber #3 (CDS 9 / CAP Console).
- 3 Aylık Çıktı (ölçülebilir): `cf push` ile çalışan 1 referans CAP (Cloud Application Programming Model — Node.js/Java servis çatısı) + UI5 uygulaması; XSUAA (BTP kimlik/yetki servisi) rolleri, destination ve service key dahil; tek komutla yeni proje üreten kısa kurulum kılavuzu.
- Gerekli yetkinlik: CAP temeli, Cloud Foundry org/space, mta.yaml — yoksa önce SAP Learning "Operating SAP BTP" + bir CAP hello-world.

### ABAP-in-VS-Code Geçiş Pilotu ve Ekip Rehberi
- İş kolu: BTP Development · Zorluk: Başlangıç
- İhtiyaç: ABAP geliştirme Eclipse/ADT'den VS Code'a kayıyor; ekip Eclipse alışkanlığında. Hangi iş akışının değiştiği, neyin çalışıp neyin eksik olduğu kurum içinde test edilmedi.
- Değer/Etki: Ekip yeni cloud-native ABAP iş akışına kontrollü geçer, Joule AI (SAP yapay zekâ asistanı) entegrasyonunu erken görür. Yöneticiye: düşük riskli, hızlı yetkinlik kazanımı ve "modern dev" konumlanması.
- Dayanak: Haber #2 (ABAP Development Tools for VS Code, Marketplace'te; dosya-tabanlı deneyim, ABAP dil sunucusu, debug, Joule).
- 3 Aylık Çıktı (ölçülebilir): BTP ABAP Environment'a bağlı VS Code kurulumu + bir RAP servisinin uçtan uca geliştirilip dağıtıldığı pilot; "Eclipse vs VS Code: ne değişti, neler eksik" karşılaştırma raporu + ekip kurulum rehberi.
- Gerekli yetkinlik: ABAP, ADT temeli, BTP ABAP Environment bağlantısı — yoksa önce ADT/VS Code uzantısını kur ve bağlan.

### BTP Maliyet Dashboard'una FinOps Anomali & Forecast Katmanı
- İş kolu: BTP Development · Zorluk: Orta
- İhtiyaç: Mevcut BTP Cost Dashboard (per-müşteri CPEA tüketimi) sadece "ne oldu"yu gösteriyor; ani tüketim sıçramasını ya da kredi tükenme tarihini önceden uyarmıyor.
- Değer/Etki: Müşteri başına aşım/tükenme erken yakalanır, sürpriz fatura ve kredi bitişi önlenir — FinOps az işlenmiş bir alan. Yöneticiye: mevcut projeye doğrudan değer katan, somut tasarruf hikâyesi olan ek katman.
- Dayanak: BTP Maliyet Tool (ekibin iç kaynağı — paylaşılan repoda yer almaz) §1 ileri faz vizyonu (anomali/forecast) · Fikir Havuzu ⑨ (FinOps) · UDMS `uas reporting-ga-admin` veri kaynağı kararlı.
- 3 Aylık Çıktı (ölçülebilir): Aylık UDMS (Usage Data Management Service — BTP tüketim verisi servisi) verisi üzerinde eşik/trend tabanlı anomali tespiti + kredi tükenme tahmini; dashboard'a uyarı rozeti ve "tahmini tükenme tarihi" alanı olarak entegre PoC.
- Gerekli yetkinlik: CAP servis tarafı + temel zaman serisi mantığı; UDMS API erişimi (Core service key) — anomali için ileri ML şart değil.

### CAP MCP Sunucusu ile Agentic Geliştirme PoC'u
- İş kolu: BTP Development · Zorluk: İleri
- İhtiyaç: AI ajanlarının CAP projelerine bağlanması (agentic geliştirme) yeni; ekip MCP (Model Context Protocol — AI ajanına proje bağlamı veren standart) sunucusu altyapısını hiç denemedi.
- Değer/Etki: Ekip, AI ajanının CAP proje bağlamını okuyup kod/servis önerdiği yeni nesil iş akışını ilk elden görür; "AI'ı neye uygulayacağını bilmek" tezini somutlar. Yöneticiye: gelişmekte olan agentic alanında erken yetkinlik.
- Dayanak: Haber #4 (MCP Server for CAP — Java/Node.js projelerine AI ajanı bağlamı, yeniden kullanılabilir bileşen erişimi) · Beyin Fırtınası farklılaşma tezi §2.
- 3 Aylık Çıktı (ölçülebilir): Örnek bir CAP projesine bağlı çalışan MCP sunucusu + bir AI ajanının proje bağlamını kullanarak en az 2 somut görevi (servis/uç-nokta üretme veya açıklama) yaptığı kayıtlı demo; bulgular ve sınırlar raporu.
- Gerekli yetkinlik: CAP (Java/Node.js), MCP sunucu kurulumu, bir AI ajan istemcisi — yoksa önce MCP Server for CAP belgesini ve örnek projeyi çalıştır.

### XS Classic → CAP Modernizasyon Pilotu (GenAI Destekli)
- İş kolu: BTP Development · Zorluk: İleri
- İhtiyaç: HANA Classic XS (XSJS/XSODATA — eski HANA uygulama bileşenleri) hâlâ sahada; bunların modern CAP servislerine taşınması elle, yavaş ve riskli.
- Değer/Etki: Müşteri sistemlerindeki eski XS nesnelerini Clean Core uyumlu CAP'e taşıyan tekrarlanabilir bir yöntem doğar. Yöneticiye: satılabilir dönüşüm hizmetinin tohumu.
- Dayanak: Haber #6 (Joule-Based SAP HANA Application Migration Assistant / SAP Build Code — XS classic→CAP dönüşümü) · Clean Core §1 side-by-side.
- 3 Aylık Çıktı (ölçülebilir): Temsili bir XS Classic bileşeninin (1 XSODATA + 1 XSJS) SAP Build Code / migration assistant ile CAP'e dönüştürüldüğü pilot; "neyin otomatik dönüştüğü, neyin elle kaldığı" efor/kapsam raporu.
- Gerekli yetkinlik: HANA XS temeli + CAP hedef modeli; SAP Build Code erişimi — yoksa önce migration assistant belgesi.

### Z-Kod → Clean Core Side-by-Side Refactor Danışmanı (ATC + SCMON)
- İş kolu: BTP Development · Zorluk: İleri
- İhtiyaç: Z-kodların hangisinin gerçekten kullanıldığı, hangi Clean Core olgunluk seviyesine düştüğü ve hangisinin BTP'ye side-by-side taşınacağı sistematik analiz edilmiyor.
- Değer/Etki: Yükseltme riskini ve teknik borcu sayısallaştırır; "taşı / sil / in-app bırak" kararına veri sağlar — Clean Core, AI'ın da ön koşulu. Yöneticiye: RISE/geçiş işine doğrudan girdi.
- Dayanak: Clean Core §3-4 (ATC, SCMON/Usage Procedure Logging, A–D olgunluk modeli, Custom Code Migration) · Haber #5 (Joule/ABAP AI custom code migration) · Beyin Fırtınası fikir ⑥.
- 3 Aylık Çıktı (ölçülebilir): Bir sistemde ATC (ABAP Test Cockpit — statik uyum tarayıcı) + SCMON (kullanım kaydı) çıktısını birleştirip Z-objelerini A–D seviyesine sınıflayan ve "side-by-side aday" listesi üreten rapor + 2-3 obje için BTP refactor önerisi.
- Gerekli yetkinlik: ATC ruleset, SCMON, Clean Core A–D modeli, ABAP Cloud farkındalığı — yoksa önce SAP Learning "Clean Core Extensibility".

### Fiori Elements OData V4 Referans Uygulama Vitrini
- İş kolu: BTP Development · Zorluk: Orta
- İhtiyaç: Modern Fiori uygulamaları OData V4 ve yeni UX yetenekleri (toplu atama, diyalogla nesne oluşturma, grid performansı) gerektiriyor; ekipte V4 servis tasarımı bilgisi sınırlı.
- Değer/Etki: BTP Cost Dashboard dahil tüm gelecek Fiori işlerine yeniden kullanılabilir, performanslı bir UI deseni sağlar. Yöneticiye: tek seferlik öğrenme yatırımının çok projeye yayılan getirisi.
- Dayanak: Haber #10 (Fiori Elements for OData V4 — yeni UX: toplu değer atama, grid tablo performansı) · Haber #12 (RAP ile REST/Fiori).
- 3 Aylık Çıktı (ölçülebilir): CAP OData V4 servisi üzerine kurulu, toplu atama + diyalogla oluşturma + büyük tablo senaryosunu gösteren çalışır Fiori Elements vitrin uygulaması + tasarım notları.
- Gerekli yetkinlik: CAP OData V4 modelleme, Fiori Elements annotation'ları — yoksa önce bir V4 Fiori Elements list-report tutorial'ı.

### Joule Studio ile İlk SAP AI Ajanı (Operasyon Asistanı PoC)
- İş kolu: BTP Development · Zorluk: İleri
- İhtiyaç: Joule Studio genel kullanıma açıldı ve AI Agent Hub yolda; ekip SAP'nin yerel AI ajan yapım yüzeyini hiç denemedi, "AI'ı neye uygulayacağını bilmek" tezi henüz somut araca bağlanmadı.
- Değer/Etki: BTP/Basis verisini okuyup yöneten ilk yerel SAP AI ajanı deneyimi kazanılır; ekibin AI-native operasyon vizyonunu somutlar. Yöneticiye: en stratejik alanda (Business AI Platform) erken konumlanma.
- Dayanak: Haber #1 (SAP Business AI Platform + Joule Studio) · Haber #11 (Joule Studio GA, AI Agent Hub yolda) · BTP Platformu §2 · Beyin Fırtınası §2 farklılaşma tezi.
- 3 Aylık Çıktı (ölçülebilir): Joule Studio'da kurulmuş, dar kapsamlı tek bir operasyon görevini (ör. bir BTP/sistem verisini sorgulayıp özetleme) yapan AI ajan PoC'u + yetenek/sınır değerlendirme raporu.
- Gerekli yetkinlik: BTP hesap erişimi, Joule Studio yetkilendirmesi, temel prompt/ajan tasarımı — yoksa önce Joule Studio GA belgesi ve bir örnek ajan.

---

## Integration Suite

### İlk iFlow'dan Üretime: "Hello Integration" Referans Akışı ve Onboarding Kılavuzu
- İş kolu: Integration Suite · Zorluk: Başlangıç
- İhtiyaç: Partnerlik anlaşması var ama ekibin çoğu hiç iFlow (entegrasyon akışı) kurmadı; ilk eşiği aşacak elle tutulur, tekrar edilebilir bir başlangıç noktası yok.
- Değer/Etki: Tüm ekibe ortak giriş zemini kurar; "Integration Suite uzman ekibi" hedefinin ilk somut tuğlasıdır ve yeni üyenin onboarding süresini günlerden saatlere indirir.
- Dayanak: Bağlam dosyası §5 "Hiç bilmiyorsam ilk adım" (Discovery Center trial tenant + basit iFlow) ve Servis_Otomasyon "Geçiş: Integration Suite eğitimleri".
- 3 Aylık Çıktı (ölçülebilir): Trial/partner tenant'ta çalışan 3 referans iFlow (HTTPS→sabit cevap, REST→dosya/e-posta, IDoc→JSON dönüşümü) + adım adım onboarding kılavuzu; ekipten en az 3 kişinin kılavuzu izleyip kendi iFlow'unu kurması.
- Gerekli yetkinlik: Temel iFlow tasarımı, HTTPS/OData/SFTP adaptörleri (yoksa önce SAP Learning Integration Suite öğrenme yolu + Discovery Center mission).

### Mesaj-Başına Maliyet İzleme Panosu (Integration Suite FinOps)
- İş kolu: Integration Suite · Zorluk: Orta
- İhtiyaç: Platform mesaj-başına faturalanır ve 250 KB üstü her dilim ek mesaj sayılır; "her şeyi akıştan geçirmek" sessizce pahalıya patlar ama tüketimi gösteren bir görünürlük yok.
- Değer/Etki: Yöneticiye doğrudan maliyet kontrolü verir; Basis bilgisi ile FinOps düşüncesinin tam kesişimidir ve ekibin mevcut maliyet odağıyla satılabilir bir hizmete dönüşebilir.
- Dayanak: Bağlam dosyası §3 mesaj-başına faturalama uyarısı ve §4 "İzleme ve maliyet" becerisi; ekibin mevcut FinOps/maliyet odağı (MEMORY: BTP Cost Dashboard).
- 3 Aylık Çıktı (ölçülebilir): Mesaj sayacını, 250 KB üstü dilim tüketimini ve en pahalı iFlow'ları gösteren bir pano (PoC) + en az 1 gerçek/örnek tenant üzerinde "şu akış X kredi tüketiyor" raporu ve 3 maliyet-düşürme önerisi.
- Gerekli yetkinlik: Integration Suite mesaj izleme ekranları/monitoring verisi, temel veri görselleştirme (yoksa önce tenant monitoring ekranlarını öğren).

### Cloud Connector → Integration Suite Güvenli Bağlantı Hızlandırıcısı
- İş kolu: Integration Suite · Zorluk: Orta
- İhtiyaç: On-prem→bulut köprüsü, sertifika ve OAuth/SAML her projede yeniden kurulan, hataya açık manuel bir iş; standart bir kurulum reçetesi yok.
- Değer/Etki: Ekibin en güçlü tarafını (ağ, kimlik, sertifika) yeniden kullanılabilir bir varlığa çevirir; her yeni entegrasyon projesinin kurulum süresini ve hata riskini düşürür.
- Dayanak: Bağlam dosyası §3 "Basis'in payı: tenant kurulumu, güvenli bağlantı (Cloud Connector, sertifika, OAuth)" ve §4 "Güvenli bağlantı — senin güçlü tarafın".
- 3 Aylık Çıktı (ölçülebilir): Cloud Connector + Integration Suite güvenli bağlantı için adım adım kontrol listesi ve örnek konfigürasyon (sertifika/OAuth dahil) + en az 1 uçtan uca doğrulanmış bağlantı senaryosu.
- Gerekli yetkinlik: Cloud Connector, sertifika yönetimi, OAuth/SAML (ekibin mevcut güçlü alanı).

### Korunan API Proxy Şablonu: Oran Sınırlama + OAuth ile Back-end Yayını
- İş kolu: Integration Suite · Zorluk: Orta
- İhtiyaç: Bir back-end'i kontrollü, ölçülebilir, güvenli bir API'ye çevirmek için (oran sınırlama, anahtar/OAuth, kullanım izleme) tekrarlanabilir bir desen yok.
- Değer/Etki: API Management yetkinliğini elle tutulur kılar; müşteriye "API'nizi güvenle dışa açalım" diye sunulabilecek paketlenebilir bir hizmetin temelini atar.
- Dayanak: Bağlam dosyası §4 "API Management: back-end'i kontrollü API'ye çevirmek; oran sınırlama, anahtar/OAuth, kullanım izleme"; Haber #8 SAP'nin iPaaS Lideri konumu.
- 3 Aylık Çıktı (ölçülebilir): Yeniden kullanılabilir bir API proxy şablonu (oran sınırlama + OAuth/anahtar koruması + kullanım izleme paneli) + 1 örnek back-end üzerinde canlı demo.
- Gerekli yetkinlik: API Management (proxy, policy, rate limiting), OAuth temelleri (yoksa önce basit bir API proxy yayınlamayı öğren).

### Event-Driven İlk Adım: SAP Event Mesh ile "Stok Değişti" Yayınla/Abone Ol PoC
- İş kolu: Integration Suite · Zorluk: Orta
- İhtiyaç: Ekip olay-tabanlı mimariyi (EDA) teoride biliyor ama "ne zaman gerekir, nasıl kurulur" sorusunun pratik cevabı yok; AEM'e atlamadan önce hafif bir başlangıç şart.
- Değer/Etki: Asenkron/çok-dinleyicili senaryolar için yetkinlik açar ve AEM'in ne zaman aşırı, Event Mesh'in ne zaman yeterli olduğunu kanıta dayalı gösterir — yanlış ürün seçimi maliyetini önler.
- Dayanak: Bağlam dosyası §2/§6 EDA ve publish/subscribe; §3 "Ne zaman Advanced Event Mesh? AEM ağır çözümdür, küçük senaryolar için fazladır".
- 3 Aylık Çıktı (ölçülebilir): Bir "olay" (ör. stok değişti) yayınlayıp en az 2 abonenin tükettiği çalışan bir publish/subscribe PoC + "Event Mesh vs AEM ne zaman" karar rehberi (1 sayfa).
- Gerekli yetkinlik: EDA temelleri, Event Mesh queue/topic kurulumu (yoksa önce publish/subscribe kavramını çalış).

### n8n'den Integration Suite'e Köprü: İç Otomasyon Akışını Kurumsal Platforma Taşıma Fizibilitesi
- İş kolu: Integration Suite · Zorluk: Orta
- İhtiyaç: Ekibin iç otomasyon örneği n8n + yerel model ile çalışıyor; aynı "düğüm-bağla" mantığının kurumsal, yönetişimli karşılığının Integration Suite'te nasıl görüneceği bilinmiyor.
- Değer/Etki: Mevcut başarıyı kurumsal platforma taşıyarak hem öğrenmeyi hızlandırır hem de "ne zaman n8n yeter, ne zaman Integration Suite gerekir" stratejik ayrımını netleştirir.
- Dayanak: Servis_Otomasyon iç otomasyon örneği (n8n + yerel bir açık-kaynak LLM, ServiceNow/Teams) ve bağlam §1/§5 "n8n'in kurumsal karşılığı; kavram aynı, kelimeler farklı".
- 3 Aylık Çıktı (ölçülebilir): İç otomasyon örneğinin bir alt akışının Integration Suite iFlow karşılığını kuran PoC + fizibilite/karşılaştırma raporu (maliyet, yönetişim, çaba — n8n vs Integration Suite).
- Gerekli yetkinlik: iFlow tasarımı, mevcut n8n akış bilgisi, REST/HTTPS adaptörleri.

### Yeni Adaptörlerle Çoklu-Bulut Bağlantı Kataloğu (Salesforce/Google/Oracle)
- İş kolu: Integration Suite · Zorluk: İleri
- İhtiyaç: Yeni adaptörler (Adobe Sign, Google, Oracle, Salesforce) geldi ama ekip hangi adaptörün hangi senaryoda kullanılacağına dair denenmiş bir kataloğa sahip değil; hibrit/çoklu-bulut peyzajı modernize edilemiyor.
- Değer/Etki: SAP-dışı sistemlerle entegrasyon kapasitesini kanıtlar; iPaaS Lideri konumunu sahada satılabilir bir "her şeyi bağlarız" yetkinliğine çevirir.
- Dayanak: Haber #7 yeni adaptörler (Adobe Sign, Google, Oracle, Salesforce); Haber #8 "geniş veri merkezi ağı ve çok sayıda konnektör" (02_SAP_Haberleri/02_BTP_ve_Gelistirme.md).
- 3 Aylık Çıktı (ölçülebilir): En az 2 yeni adaptörle (ör. Salesforce + Google) uçtan uca doğrulanmış entegrasyon senaryosu + her adaptör için kurulum/sınır notlarını içeren bir bağlantı kataloğu.
- Gerekli yetkinlik: İlgili adaptör konfigürasyonu, hedef sistemlerin API/kimlik modeli (yoksa önce 1 üçüncü-parti adaptörle başla).

### BTP Marketplace İçin Entegrasyon İçerik Paketi (Yayınlanabilir Ürün Tohumu)
- İş kolu: Integration Suite · Zorluk: İleri
- İhtiyaç: Dönüşüm hedefi "BTP Marketplace'te ürün yayını" ama ekibin henüz paketlenmiş, yeniden dağıtılabilir bir entegrasyon varlığı yok.
- Değer/Etki: Soyut "ürün yayını" hedefini somut bir ilk adıma indirger; ekibin "servis üreten"den "ürün geliştiren" yapıya geçişinin görünür kanıtı olur ve yöneticiye doğrudan stratejik getiri sunar.
- Dayanak: Servis_Otomasyon "Hedef: BTP Marketplace'te ürün yayını" ve "servis üretiminden ürün geliştirmeye geçiş" ana mesajı; Haber #8 iPaaS Lideri ekosistemi.
- 3 Aylık Çıktı (ölçülebilir): Paketlenmiş 1 entegrasyon içerik varlığı (ör. parametreli iFlow + dokümantasyon) + Marketplace/Content yayın gereksinimlerini ve eksik adımları listeleyen yol haritası raporu.
- Gerekli yetkinlik: iFlow paketleme/içerik tasarımı, dokümantasyon, BTP/Marketplace yayın süreci (yoksa önce mevcut hazır içerik paketlerini incele).

---

## Build Apps

### Joule Studio + n8n ile İlk SAP-Native Ajan Akışı (İç Otomasyon Örneğinin Halefi)
- İş kolu: Build Apps · Zorluk: Başlangıç
- İhtiyaç: Ekip iç otomasyon örneğini kurum-dışı bir n8n + yerel açık-kaynak LLM yığınında çalıştırıyor; SAP ise n8n'i Joule Studio'ya gömdü. Aynı "e-posta → sınıflandır → kayıt aç" kalıbını SAP-native (Joule Studio + Build Process Automation) zemine taşıyan bir referans akış henüz yok.
- Değer/Etki: Kanıtlanmış bir iç varlığı (ekibin iç otomasyon örneği) SAP-desteklenen yönetişim/audit katmanına taşımak, ekibin "AI-native, BTP üzerinde ürün geliştiren" hedefine ilk somut, gösterilebilir adımdır ve müşteri tekliflerine doğrudan referans olur.
- Dayanak: AI Haberleri #8 (Joule Studio'nun n8n ile görsel orkestrasyonu) ve #9 (SAP'ın n8n'e stratejik yatırımı, Joule Studio'ya gömme); ekibin iç otomasyon örneği (Servis_Otomasyon.md).
- 3 Aylık Çıktı (ölçülebilir): Joule Studio/n8n üzerinde 1 uçtan uca ajan akışı PoC'u + "lokal n8n vs SAP-native" karşılaştırma raporu (yönetişim, maliyet, kurulum eforu).
- Gerekli yetkinlik: n8n akış mantığı (var), Joule Studio, Build Process Automation; önce Joule Studio ajan tanımını öğren.

### SAP Build Apps Emeklilik Envanteri ve Geçiş Önceliklendirme Panosu
- İş kolu: Build Apps · Zorluk: Başlangıç
- İhtiyaç: SAP Build Apps 23 Mart 2026'da emekliye ayrıldı; müşteri peyzajında hangi low-code uygulamaların var olduğu, hangisinin kullanıldığı/kritik olduğu çıkarılmadan göç planlanamıyor. Mevcut catalog "geçiş playbook'una" odaklı; bu fikir ondan ÖNCEKİ envanter/triyaj adımıdır.
- Değer/Etki: Yöneticiye "kaç uygulama, ne risk, hangi sırayla" netliği verir; göç projesini somut bir backlog'a çevirir ve emeklilik kaynaklı sessiz kesinti riskini görünür kılar.
- Dayanak: Build Apps emekliliği (00_Baglam/02_BTP_Platformu.md §4) + BTP Haberleri #11 (What's New in SAP BTP Q1 2026 — büyük yükseltme penceresi).
- 3 Aylık Çıktı (ölçülebilir): Build Apps uygulamalarını listeleyip kullanım/kritiklik/karmaşıklık skoruyla "kırmızı/sarı/yeşil" önceliklendiren bir envanter raporu + basit pano; en az 1 müşteri peyzajında uygulanmış.
- Gerekli yetkinlik: BTP subaccount keşfi, Build Apps uygulama yapısı, basit veri görselleştirme.

### Yeniden Kullanılabilir SBPA İş Akışı Şablon Kütüphanesi (Basis Süreçleri İçin)
- İş kolu: Build Apps · Zorluk: Başlangıç
- İhtiyaç: Basis operasyonundaki tekrarlayan onay/talep süreçleri (transport onayı, kullanıcı/yetki talebi, sistem refresh isteği) her seferinde sıfırdan kuruluyor. Build Process Automation'da hazır, parametrik bir Basis-süreç şablon seti yok.
- Değer/Etki: Yeni müşteri/projede süreç kurulum süresini günlerden saatlere indirir; ekibin otomasyon/DigiOps pratiğini tekrar kullanılabilir bir varlığa dönüştürür.
- Dayanak: SAP Build Process Automation (gerçek ürün yeteneği, hazır içerik modeli) + Joule for Developers'ın SBPA desteği (AI Haberleri #10); iç DigiOps/otomasyon backlog pratiği (Servis_Otomasyon.md).
- 3 Aylık Çıktı (ölçülebilir): 3-4 Basis sürecini kapsayan yeniden kullanılabilir SBPA şablon paketi + kısa kullanım dokümanı + 1 süreçte canlı pilot.
- Gerekli yetkinlik: SAP Build Process Automation (form, karar, onay adımları), iş süreci modelleme, S/4HANA OData bağlama.

### Transport Onay Akışını SBPA + Cloud ALM'e Taşıma (DigiOps)
- İş kolu: Build Apps · Zorluk: Orta
- İhtiyaç: Transport onayları çoğu yerde e-posta/sözlü yürüyor; izlenebilir, denetlenebilir bir akış yok. Cloud ALM Transport Management ekibin yeni servislerinden biri ama önündeki onay/karar adımı low-code ile modellenmemiş.
- Değer/Etki: Mevcut "Cloud ALM Transport Management" servisine onay/SoD kontrol katmanı ekleyerek hizmeti güçlendirir; üretilen denetim kaydı uyumluluk tarafına da değer taşır.
- Dayanak: İç servis "Cloud ALM Transport Management" (Servis_Otomasyon.md) + Cloud Transport Management/CTMS (03_Cloud_Operasyonlar §7) + SBPA onay yetenekleri (gerçek ürün).
- 3 Aylık Çıktı (ölçülebilir): SBPA'da transport onay/red akışı + Cloud ALM/CTMS tetikleme PoC'u; 1 ortamda en az birkaç transport'un akıştan geçirilmesi ve denetim kaydı çıktısı.
- Gerekli yetkinlik: Cloud Transport Management/CTMS, SAP Build Process Automation, onay/SoD kuralı modelleme.

### Work Zone "Basis Operasyon Kokpiti" — Tek Ekranda Sistem Durumu
- İş kolu: Build Apps · Zorluk: Orta
- İhtiyaç: Mevcut catalog'daki Work Zone fikri genel rol-bazlı portal; burada eksik olan Basis ekibinin kendi operasyonel görünümüdür: sistem sağlığı, açık SR'lar, transport kuyruğu, sertifika son-kullanma uyarıları tek launchpad'de toplanmıyor.
- Değer/Etki: Ekibin günlük/haftalık rutinlerini tek panele indirir, bağlam değiştirme kaybını azaltır; aynı zamanda Work Zone yetkinliğini iç bir üründe pişirip müşteriye satılabilir hale getirir.
- Dayanak: SAP Build Work Zone (gerçek ürün yeteneği) + Cloud ALM health/integration monitoring (03_Cloud_Operasyonlar §5) + günlük/haftalık rutin envanteri (03_Gunluk_Haftalik_Aylik_Rutinler.md).
- 3 Aylık Çıktı (ölçülebilir): 4-5 kartlı bir Work Zone operasyon launchpad'i (Cloud ALM + SR + sertifika izleme kartları) + ekip içi pilot kullanım.
- Gerekli yetkinlik: Work Zone konfigürasyonu, Fiori kart/içerik entegrasyonu, Cloud ALM/SAP for Me API bağlama, XSUAA rol koleksiyonu.

### AI Agent Hub Yönetişim ve Audit Kontrol Çerçevesi
- İş kolu: Build Apps · Zorluk: İleri
- İhtiyaç: AI Agent Hub yolda; SBPA akışlarına karar veren ajanlar girecek. Mevcut catalog "agentic karar PoC'u"na bakıyor; burada eksik olan ajanların yönetişimi: kim hangi ajanı çalıştırabilir, hangi adım insan onayı gerektirir, denetim kaydı nasıl tutulur.
- Değer/Etki: SAP'ın tariflediği yönetişim eşiği doğrudan Basis sorumluluğu; ajan otonomisi arttıkça kontrol çerçevesi olmadan kurumsal kullanım riskli. Bu, ekibe "AI'ı güvenle işletme" konumlandırması verir.
- Dayanak: BTP Haberleri #11 (AI Agent Hub yolda) + AI Agent Hub yönetişim/insan-onay döngüsü ve audit trail (00_Baglam/03_AI_ve_Otomasyon.md §3) + "Five Moments" yönetişim eşiği (AI Haberleri #11).
- 3 Aylık Çıktı (ölçülebilir): 1 SBPA agentic akışı için yönetişim spec'i (rol/yetki, insan-onay eşikleri, audit log şeması) + bir test akışında uygulanmış denetim kaydı örneği + kontrol listesi.
- Gerekli yetkinlik: SBPA, AI Agent Hub kavramları, XSUAA/rol tasarımı, audit/uyumluluk modelleme; önce AI Agent Hub beta belgelerini incele.

### Düşük-Kodlu Çözümler İçin Clean Core Uyum Kapısı (A–D Kontrol Listesi)
- İş kolu: Build Apps · Zorluk: Orta
- İhtiyaç: Low-code çözümler (Work Zone, SBPA, side-by-side) hızlı kurulurken Clean Core ilkelerini ihlal edebiliyor (örn. public arayüz yerine iç nesneye dokunma). Düşük-kodlu çıktıları A–D olgunluk modeline göre denetleyen bir kontrol kapısı yok.
- Değer/Etki: "Hızlı ama temiz" güvencesi vererek low-code çıktılarının yükseltme/AI-uyumunu korur; ekibin Clean Core yönetişim rolünü Build Apps tarafına da taşır — yöneticiye teknik borç önleme değeri.
- Dayanak: Clean Core A–D olgunluk modeli ve in-app/side-by-side ayrımı (00_Baglam/04_Clean_Core.md) + Build Apps emekliliği sonrası CAP/Fiori/SBPA'ya kayan ağırlık (Yetkinlik Matrisi §4).
- 3 Aylık Çıktı (ölçülebilir): Low-code çözümler için A–D bazlı bir uyum kontrol listesi + 2-3 örnek uygulamada uygulanmış denetim raporu (uyum skoru + düzeltme önerileri).
- Gerekli yetkinlik: Clean Core A–D modeli, public arayüz/side-by-side bilgisi, SBPA/Work Zone mimarisi.

---

## BTP Core Services

### Subaccount/Directory İskelet "Landing Zone" Otomasyonu (btp CLI + Terraform)
- İş kolu: BTP Core Services · Zorluk: Başlangıç
- İhtiyaç: Yeni müşteri/ortam açarken Global Account → Directory → Subaccount → entitlement → rol koleksiyonu adımları elle, tutarsız ve yavaş yapılıyor; ekipte "müşteri = directory, ortam = subaccount" deseni var ama tekrarlanabilir bir kurulum yok.
- Değer/Etki: Onboarding'i elle çoklu adımdan tek komuta indirir; tutarsız hak dağıtımı ve insan hatası riskini kaldırır, kurulumu denetlenebilir/sürüm kontrollü hale getirir — yöneticiye tekrarlanabilir, kanıtlanabilir bir varlık verir.
- Dayanak: 00_Baglam/02_BTP_Platformu.md (Global Account/Directory/Subaccount hiyerarşisi, entitlement dağıtımı) + BTP Maliyet Tool (ekibin iç kaynağı — paylaşılan repoda yer almaz) §6 (müşteri=directory, ortam=subaccount deseni); gerçek SAP ürün yeteneği: `btp` CLI ve Terraform Provider for SAP BTP.
- 3 Aylık Çıktı (ölçülebilir): Parametre alıp (müşteri adı, bölge, ortam tipi) tek komutla 1 directory + 1 subaccount + standart entitlement/rol setini kuran çalışan bir script/Terraform modülü + 2 örnek müşteri için demo kurulumu ve README.
- Gerekli yetkinlik: btp CLI, temel Terraform, entitlement/rol koleksiyonu mantığı (yoksa önce "Operating SAP BTP / Account Model" ücretsiz dersini bitir).

### CAP "Altın Şablon" — Standart Yeni Uzantı İskeleti
- İş kolu: BTP Core Services · Zorluk: Başlangıç
- İhtiyaç: "Clean core" yaklaşımıyla her yeni uzantı BTP'de CAP ile yazılıyor, ama her geliştirici farklı yapı kuruyor; XSUAA, Destination, mta.yaml, taşınabilirlik disiplini standart değil.
- Değer/Etki: Her yeni BTP uzantısını aynı güvenli/taşınabilir temelden başlatır; başlangıç süresini ve ortam-bağımlı hataları azaltır — ekip için yeniden kullanılabilir, somut bir varlık (template repo) bırakır.
- Dayanak: Haber #3 (CDS 9 / CAP Console) 02_SAP_Haberleri/02_BTP_ve_Gelistirme.md; 00_Baglam/02_BTP_Platformu.md (CAP ana yol, SAP Build Apps emekli); BTP Maliyet Tool (ekibin iç kaynağı — paylaşılan repoda yer almaz) (mta.yaml + deklaratif konfig + env credential disiplini).
- 3 Aylık Çıktı (ölçülebilir): XSUAA + Destination + örnek OData V4 servisi + mta.yaml içeren, `cf push` ile çalışan bir CAP başlangıç şablonu (template repo) + yeni projeyi hızlı ayağa kaldırmayı gösteren kısa kılavuz.
- Gerekli yetkinlik: CAP (Node.js/TypeScript), XSUAA temel, mta deploy; (yoksa önce CAP "hello world" + `cf push` adımını uygula).

### CPEA Kredi Erime Erken Uyarı Paneli (UDMS)
- İş kolu: BTP Core Services · Zorluk: Orta
- İhtiyaç: CPEA kredileri tüketime göre eriyor; krediler bitince veya bir servis beklenmedik tüketince fatura sürpriz oluyor. Erime hızını ve "bu hızla ne zaman biter" tahminini gösteren bir görünüm yok.
- Değer/Etki: Bütçe aşımını fatura gelmeden görünür kılar; beklenenden fazla tüketen servisi erken işaretler — yöneticiye maliyet riski yönetimi sağlar ve mevcut BTP Cost Tool track'ini besler.
- Dayanak: 00_Baglam/09_FinOps_Maliyet.md (CPEA, UDMS `/cloudCreditsDetails`, `reporting-ga-admin`); gerçek SAP servisi: Usage Data Management Service (`uas`) ve SAP-samples/btp-resource-consumption-monitor referans reposu.
- 3 Aylık Çıktı (ölçülebilir): UDMS `/cloudCreditsDetails` çağırıp kalan kredi + aylık erime eğrisi + basit doğrusal "tükenme tarihi" tahmini gösteren çalışan Fiori paneli (ilk sürüm, tek GA hesabı).
- Gerekli yetkinlik: UDMS OAuth2 çağrısı, CAP+Fiori temeli; (yoksa önce 09_FinOps §5'teki "ilk adım" — Postman ile token al, GET at).

### Cloud Connector + Destination Sağlık İzleyicisi
- İş kolu: BTP Core Services · Zorluk: Orta
- İhtiyaç: BTP uzantıları on-prem'e Cloud Connector ve Destination üzerinden bağlanıyor; bir tünel düşünce veya bir destination bozulunca sorun çoğu zaman kullanıcıdan duyuluyor, proaktif izleme yok.
- Değer/Etki: Hibrit bağlantı kesintilerini kullanıcı şikayetinden önce yakalar; klasik Basis izleme refleksini bulut bağlantı yüzeyine taşır — operasyonel güvenilirliği somut artırır.
- Dayanak: 00_Baglam/02_BTP_Platformu.md (Destination, service key, Cloud Connector, principal propagation — somut beceri listesi); gerçek SAP yeteneği: Destination service "check connection" ve Cloud Connector durum uç noktaları.
- 3 Aylık Çıktı (ölçülebilir): Bir subaccount'taki tüm destination'ları periyodik test edip (erişilebilir/erişilemez + yanıt süresi) durum tablosu üreten ve hata durumunda uyaran bir PoC + örnek 5 destination üzerinde rapor.
- Gerekli yetkinlik: Destination/Connectivity service API, Cloud Connector temel, zamanlanmış iş; (yoksa önce bir Destination + Cloud Connector ile on-prem bağlantısı kur).

### SolMan → Cloud ALM Geçiş için BTP İzleme Tabanı (RFC/tRFC Metrikleri)
- İş kolu: BTP Core Services · Zorluk: Orta
- İhtiyaç: Solution Manager ana bakımı 31.12.2027'de bitiyor; ChaRM/ITSM ve operasyonel izleme Cloud ALM'e taşınmalı, ama ekipte Cloud ALM API ve yeni metrik yetenekleri (tRFC/qRFC/bgRFC) henüz pratiğe dökülmedi.
- Değer/Etki: 2027 tarih-kritik geçişini erken ve düşük riskle başlatır; SolMan körlüğünü Cloud ALM ile kapatır — yöneticiye "deadline'a hazırlanıyoruz" diyebileceği somut bir ilk adım verir.
- Dayanak: 02_SAP_Haberleri/07_Maintenance_2027_2030_Lisans.md Haber #8 (SolMan bakım sonu 31.12.2027, Cloud ALM'e geçiş) ve Haber #9 (Cloud ALM API'lerinde yeni RFC metrik izleme — tRFC/qRFC/bgRFC, Configuration & Security Analysis).
- 3 Aylık Çıktı (ölçülebilir): Cloud ALM'in RFC metrik izlemesini bir test sisteminde devreye alıp tRFC/qRFC kuyruk metriklerini gösteren çalışan kurulum + SolMan işlevlerinin (ChaRM/ITSM/izleme) Cloud ALM karşılıklarını listeleyen geçiş haritası raporu.
- Gerekli yetkinlik: Cloud ALM temel, RFC kavramı (tRFC/qRFC/bgRFC), API token; (yoksa önce Cloud ALM tenant'ında ücretsiz izleme senaryosunu aç).

### UDMS Tüketimi için Müşteri-İzole (Row-Level) Maliyet Dashboard'u
- İş kolu: BTP Core Services · Zorluk: İleri
- İhtiyaç: UDMS global seviyede TÜM müşterilerin verisini döndürüyor; partner senaryosunda her müşteri yalnız kendi directory tüketimini görmeli. Bu izolasyon referans repoda hazır yok, uygulama katmanında (CAP row-level) kurulmalı — tek hatada bir müşteri diğerinin faturasını görür.
- Değer/Etki: Maliyet raporlama ile güvenlik/izolasyon ihtiyacını aynı anda karşılar; partnerin cross-charge ve müşteri self-service vizyonunu mümkün kılar — yüksek stratejik ve ticari etki, mevcut BTP Cost Tool track'inin çekirdeği.
- Dayanak: 00_Baglam/09_FinOps_Maliyet.md (UDMS global döner, izolasyon uygulama katmanında, row-level filtre) + BTP Maliyet Tool (ekibin iç kaynağı — paylaşılan repoda yer almaz) (karar kayıtları: directory segmentasyonu, server-side filtre, `/monthlySubaccountsCost`).
- 3 Aylık Çıktı (ölçülebilir): Gerçek/PAYG hesapta `/monthlySubaccountsCost` verisini çekip directory bazında server-side row-level filtreyle gösteren, en az 2 müşteri rolüyle izolasyonu kanıtlanmış (biri diğerinin verisini GÖREMİYOR) çalışan MVP dashboard.
- Gerekli yetkinlik: CAP + Fiori, XSUAA rol/scope, UDMS, server-side yetki filtresi; (kritik: önce row-level izolasyon desenini küçük bir CAP servisinde doğrula).

### HANA Cloud Bellek/FinOps "Sağ Boyutlandırma" Asistanı
- İş kolu: BTP Core Services · Zorluk: İleri
- İhtiyaç: HANA bellek-içi bir veritabanı; bellek doğrudan maliyet kalemi ve gereksiz veri tutmak para yakıyor. Hangi tabloların bellek yediği ve nerede housekeeping/right-sizing yapılabileceği BTP tarafında görünür değil.
- Değer/Etki: Doğrudan kredi tasarrufu argümanı üretir (bellek = para) ve "gereksiz tüketim" kararını veriye dayandırır; FinOps refleksini somut teknik aksiyona çevirir.
- Dayanak: 00_Baglam/09_FinOps_Maliyet.md (HANA memory doğrudan maliyet; fair-use/housekeeping FinOps refleksi); gerçek SAP yeteneği: HANA Cloud sistem görünümleri (memory/table footprint) + UDMS maliyet eşlemesi.
- 3 Aylık Çıktı (ölçülebilir): HANA Cloud bellek/tablo ayak izini okuyup en çok bellek yiyen ilk N nesneyi + tahmini aylık maliyet etkisini listeleyen ve right-sizing/housekeeping önerisi üreten bir rapor aracı (ilk sürüm, bir HANA Cloud örneği üzerinde).
- Gerekli yetkinlik: HANA Cloud yönetimi, SQL/sistem görünümleri, temel maliyet eşlemesi; (yoksa önce bir HANA Cloud örneğinde memory görünümlerini incele).

---

## Rise Onboarding

### RISE R&R (Roller ve Sorumluluklar) İnteraktif Sınır Haritası
- İş kolu: Rise Onboarding · Zorluk: Başlangıç
- İhtiyaç: ECS (Enterprise Cloud Services — SAP'nin RISE altyapısını SLA ile işleten birim) ile müşteri arasındaki paylaşılan sorumluluk sınırı, her onboarding'in en sık tartışılan ve en çok yanlış anlaşılan konusu; SAP'nin 1000'den fazla görev içeren R&R (Roles & Responsibilities) matrisi ham haliyle kullanılamaz.
- Değer/Etki: Kick-off'taki "bunu kim yapar" sorusunu anında cevaplayan ortak başvuru aracı; toplantıyı kısaltır, "kapsam dışı" sürtüşmesini düşürür ve her yeni RISE projesinde tekrar kullanılır.
- Dayanak: SAP RISE R&R matrisi (00_Baglam/01_Cloud_Donusumu.md §3 — "1000'den fazla görevi listeleyen R&R matrisi") · Haber #2 (Private Edition Transition Option göçü).
- 3 Aylık Çıktı (ölçülebilir): R&R matrisinden ayıklanmış, aranabilir/filtrelenebilir tek sayfa harita (kategori bazında "ECS / Müşteri / Ortak"), en sık ~50 aktiviteyi kapsayan ve gerçek bir RISE müşterisi kick-off'unda test edilmiş ilk sürüm.
- Gerekli yetkinlik: R&R matrisini okuma + basit web/Excel filtreleme; mevcut (Cloud_Donusumu §4'te "ilk adım" olarak işaretli).

### Cloud ALM Hızlı Aktivasyon Runbook'u (Private Cloud / ECS)
- İş kolu: Rise Onboarding · Zorluk: Başlangıç
- İhtiyaç: Her RISE/Private Cloud onboarding'inde Cloud ALM (SAP'nin SolMan halefi yaşam döngüsü/izleme platformu) aktivasyonu elle, tekrar tekrar yapılıyor; add-on, kurulum job'ı ve veri toplayıcı adımları kişilerin kafasında, hata ve gecikmeye açık.
- Değer/Etki: Onboarding'in standart teslimi olan "7/24 izleme kuruldu" çıktısını öngörülebilir bir kontrol listesine indirir; MSP "Run" modeline doğrudan değer üretir ve yeni ekip üyesini hızla devreye alır.
- Dayanak: 03_Basis_Operasyonlari/02_Cloud_Operasyonlar.md §5 (ST-PI / ST-A·PI add-on'ları, `/n/SDF/ALM_SETUP`, `SM37` `SAP_ALM_DATA_COLLECTOR_DISPATCH`) · Deneyim_RISE_MSP.md ("Cloud ALM ile 7/24 izleme").
- 3 Aylık Çıktı (ölçülebilir): Önkoşul → aktivasyon → health/integration monitoring → fair-use (8 GB) kontrolü adımlarını içeren, ekran görüntülü adım adım runbook + kontrol listesi; en az 1 sistemde uçtan uca uygulanıp doğrulanmış.
- Gerekli yetkinlik: Cloud ALM kurulumu, add-on/SM37 bilgisi; kısmen mevcut, "Cloud ALM tanıtım" ile tamamlanır.

### RISE/ECS Service Request (SR) Hazırlama Asistanı — PoC
- İş kolu: Rise Onboarding · Zorluk: Orta
- İhtiyaç: Private Cloud'da operasyonel işler (refresh, kernel/DB güncelleme, client copy, OS görevleri) doğrudan değil, SAP for Me'den SR (Service Request — ECS'ten operasyonel iş talebi) açılarak yürür; doğru şablonu seçip doğru doldurmak uzmanlık ister ve yanlış SR, ECS ile gecikmeli ileri-geri yazışmaya yol açar.
- Değer/Etki: Serbest yazılmış ihtiyacı doğru şablona + bağlamlı ön-doldurulmuş taslağa çeviren, gönderme kararını insanda bırakan asistan; ECS gecikmesini azaltır ve uzman bilgisini kişiden araca taşır.
- Dayanak: SR Asistanı tasarım notu (ekibin iç kaynağı — paylaşılan repoda yer almaz; tüm tasarım) · KBA 3554766 (SR açacak public API yok → tam otomasyon değil, hazırlama doğru seviye).
- 3 Aylık Çıktı (ölçülebilir): En sık 3 SR türü (örn. OS görevi, not uygulama, refresh) için çalışan PoC: ihtiyaç metni → önerilen şablon + ön-doldurulmuş taslak; 10–20 gerçek geçmiş SR üzerinde doğru-şablon eşleşme oranı ölçülmüş.
- Gerekli yetkinlik: Lokal AI/RAG (ekibin iç otomasyon örneğindeki yaklaşım) + SR şablon kataloğu; RAG kısmı yoksa önce küçük lokal model denemesi.

### SR Gerektirmeyen İşler Otomasyon Kataloğu (Cloud ALM + RunMyJobs)
- İş kolu: Rise Onboarding · Zorluk: Orta
- İhtiyaç: RISE operasyonunda her işin SR gerektirdiği sanılır; oysa bir kısım iş SR'siz, RISE referans mimarisindeki araçlarla (Cloud ALM, RunMyJobs by Redwood) yapılabilir. Bu sınır netleşmediği için gereksiz SR açılıp operasyon yavaşlar.
- Değer/Etki: "Hangi iş SR ister, hangisi araçla otomatik yapılır" kataloğu açılan SR sayısını ve operasyon maliyetini düşürür; MSP "Run" verimliliğine doğrudan etki eden, oylanabilir somut bir kazanç.
- Dayanak: Fikir Havuzu / Beyin Fırtınası (ekibin iç kaynağı — paylaşılan repoda yer almaz) TEMA VI ("SR gerektirMEYEN işleri otomatikleştir → Cloud ALM + RunMyJobs by Redwood, RISE reference architecture") · Cloud_Operasyonlar.md §6.
- 3 Aylık Çıktı (ölçülebilir): En sık operasyonel işlerin "SR / SR-siz araç" sınıflandırma kataloğu + 2 SR-siz işin (örn. job zamanlama, izleme alarmı) RunMyJobs/Cloud ALM ile çalışan demosu.
- Gerekli yetkinlik: RISE reference architecture + RunMyJobs/Cloud ALM job yönetimi; RunMyJobs yeni ise önce ürün tanıtımı.

### RISE Referans Mimarisi & Onboarding Şablon Paketi
- İş kolu: Rise Onboarding · Zorluk: Orta
- İhtiyaç: Her RISE onboarding'i müşteri ↔ ECS ↔ hyperscaler (AWS/Azure/GCP) mimarisini ve standart kurulum adımlarını sıfırdan çiziyor; tekrarlanabilir şablon olmadığı için projeler arası kalite ve süre dalgalanıyor.
- Değer/Etki: Yeniden kullanılabilir mimari çizimi + onboarding kontrol listesi + RACI; ilk Run müşterisini hızla devreye alan ve RISE büyümesini destekleyen bir hızlandırıcı (IP).
- Dayanak: Deneyim_RISE_MSP.md ("onboarding sürecini şablonlamak/otomatikleştirmek", "ilk Run müşterisi") · Cloud_Donusumu.md §5 ("RISE referans mimarisini bir kez baştan sona çiz").
- 3 Aylık Çıktı (ölçülebilir): Standart RISE onboarding paketi v1: referans mimari diyagramı + faz faz kontrol listesi (connectivity, kimlik, izleme, SR akışı) + RACI tablosu; 1 gerçek/örnek müşteride pilotlanmış.
- Gerekli yetkinlik: RISE mimarisi, connectivity, IAS/IPS temel bilgisi; ağırlıkla mevcut.

### GROW with SAP Hızlı Onboarding (Public Cloud) Kit'i
- İş kolu: Rise Onboarding · Zorluk: Başlangıç
- İhtiyaç: GROW with SAP (S/4HANA Public Cloud, hızlı go-live hedefli orta ölçek ERP) onboarding'inde Basis eforu RISE'tan farklı: odak "hızlı kurulum + entegrasyon + kimlik yönetimi"; bu hafif ama farklı akış için ayrı bir şablon yok.
- Değer/Etki: KOBİ/orta ölçek müşterilerde go-live süresini kısaltan tekrarlanabilir kit; SAP'nin GROW faz hedefini (eylem planı Faz 3) erken destekleyerek yeni müşteri segmenti açar.
- Dayanak: Haber #7 (GROW with SAP — hızlı go-live, düşük kurulum) + Haber #6 (Commerce Cloud ERP Edition KOBİ entegrasyonu) · Cloud_Donusumu.md §4 ("GROW tarafı: hızlı kurulum + entegrasyon + kimlik yönetimi").
- 3 Aylık Çıktı (ölçülebilir): GROW onboarding kontrol listesi + kimlik (IAS/IPS, SSO) ve temel entegrasyon kurulum şablonu; örnek bir Public Cloud tenant'ında uçtan uca denenmiş minimum go-live akışı.
- Gerekli yetkinlik: IAS/IPS, SSO (SAML/OIDC), temel entegrasyon; çoğu mevcut.

### DMO with System Move Göç Hazırlık & Cutover Playbook'u
- İş kolu: Rise Onboarding · Zorluk: İleri
- İhtiyaç: Legacy Business Suite 7 / ECC'den RISE Private Cloud'a geçişin ana teknik yöntemi DMO with System Move (veritabanı dönüşümü + buluta taşımayı tek adımda yapan göç); önkoşullar, sizing ve cutover adımları kritik ve hata payı düşük, ama derli toplu bir hazırlık/cutover rehberi yok.
- Değer/Etki: 2027 ECC desteği bitişinden önce kalan göçleri hızlandıran ve riski azaltan playbook; Private Edition Transition Option ile sunulan 2031–2033 iş sürekliliği fırsatını somut teslime çevirir (yüksek pazar potansiyeli).
- Dayanak: Haber #2 (Private Edition Transition Option, 2031–2033 iş sürekliliği) + Haber #8 (2027 öncesi göç hızlanıyor) · Cloud_Operasyonlar.md §6 (DMO with System Move) · Cloud_Donusumu.md §4.
- 3 Aylık Çıktı (ölçülebilir): DMO with System Move için önkoşul kontrol listesi + sizing girdileri + saatlik cutover planı + rollback adımları içeren playbook; 1 sandbox/örnek sistemde önkoşul kontrolleri çalıştırılmış.
- Gerekli yetkinlik: Göç metodolojisi, DMO, sizing, downtime planlama; DMO derinliği zayıfsa önce SAP DMO/SUM dokümantasyonu.

---

## Yetkilendirme

### Joule ve AI-Ajan Erişim Riski Tarama Çerçevesi
- İş kolu: Yetkilendirme · Zorluk: İleri
- İhtiyaç: Joule (SAP'nin yapay zeka asistanı) gibi geniş erişimli AI ajanları, bir kullanıcıda var olan yetkileri birleştirip yeni SoD (Segregation of Duties / görevler ayrılığı) çakışmaları yaratabiliyor; klasik SoD matrisi bu "AI-aracılı dolaylı erişim" riskini görmüyor.
- Değer/Etki: AI'nin SAP'ye girdiği bu dönemde müşteriye "ajan senin adına ne yapabilir, denetledik" güvencesi sunar; henüz az ekibin sahip olduğu erken bir yetkinlik olduğundan oy gerekçesi olarak ayrıştırıcıdır.
- Dayanak: Haber #14 (S/4HANA SoD matrisi yeniden tasarımı, Joule geniş erişim çakışma riski) 02_SAP_Haberleri/06_Guvenlik_Uyumluluk.md
- 3 Aylık Çıktı (ölçülebilir): Bir test sisteminde geniş erişimli bir ajan/servis kullanıcısının efektif yetkilerini çıkaran ve mevcut SoD matrisiyle çakışmaları listeleyen PoC rapor + 5-10 maddelik "AI ajan rol tasarım ilkeleri" rehberi (Joule canlı sistem yoksa servis-kullanıcı modeliyle).
- Gerekli yetkinlik: PFCG/SU01 rol-yetki okuma, SoD matrisi yorumlama; AI ajan yetki modeli için önce Joule yetkilendirme dokümanını oku.

### S/4HANA Geçişi için SoD Matrisi Yeniden Tasarım Kiti
- İş kolu: Yetkilendirme · Zorluk: İleri
- İhtiyaç: S/4HANA'da işlem kodları, Fiori uygulamaları ve veri modeli değiştiği için ECC'den taşınan eski SoD matrisi geçersiz kalıyor; çakışma kuralları yeniden eşlenmeli.
- Değer/Etki: S/4HANA geçişi yapan her müşteride gereken bir adımdır; ekibe tekrar kullanılabilir bir hizmet paketi kazandırır ve denetim risklerini geçişte erkenden kapatır.
- Dayanak: Haber #14 (New Access Risks, New SoD Matrix: S/4HANA yaklaşımı değiştiriyor) 02_SAP_Haberleri/06_Guvenlik_Uyumluluk.md
- 3 Aylık Çıktı (ölçülebilir): 1 örnek modül (ör. FI veya MM) için ECC→S/4HANA SoD kural eşleme tablosu + Fiori uygulaması/IAM (yetki nesnesi) bazlı güncellenmiş çakışma matrisi şablonu.
- Gerekli yetkinlik: SoD matrisi okuma, S/4HANA Fiori yetki modeli (katalog/grup/IAM), PFCG; eksikse önce Fiori yetkilendirme akışını öğren.

### SAP GRC for HANA Erken-Benimseyen Değerlendirme PoC
- İş kolu: Yetkilendirme · Zorluk: İleri
- İhtiyaç: Yeni nesil GRC (Access/Process Control) S/4HANA/HANA üzerine taşınıyor; ekibin bu platformu klasik GRC'den farkları, geçiş etkisi ve yetki yönetimi yetenekleri açısından henüz değerlendirmesi yok.
- Değer/Etki: GRC yenileme dalgasında müşterilere yön gösterecek erken bilgi sağlar; pazar olgunlaşmadan konumlanma fırsatı verir.
- Dayanak: Haber #12 (SAP GRC for SAP HANA — Early Adopter Care Program) 02_SAP_Haberleri/06_Guvenlik_Uyumluluk.md
- 3 Aylık Çıktı (ölçülebilir): Klasik GRC vs. GRC for HANA karşılaştırma raporu (mimari, erişim risk analizi, geçiş etkisi) + erken-benimseyen programına başvuru/erişim için aksiyon listesi.
- Gerekli yetkinlik: GRC Access Control kavramları, HANA temel mimari; eksikse önce klasik GRC Access Control modülünü gözden geçir.

### Görev-Bazlı (Task-Based) Rol Tasarım Standardı ve Şablon Kütüphanesi
- İş kolu: Yetkilendirme · Zorluk: Orta
- İhtiyaç: Geniş ve "şişmiş" tek tip roller hem SoD çakışması hem de en-az-yetki ihlali üretiyor; görev-bazlı modüler rol tasarımına geçecek bir standart yok.
- Değer/Etki: Yeni projelerde rol tasarımını standartlaştırıp denetimde tekrar çıkan bulguları azaltır; ekip içi tutarlılık ve hız kazandırır, müşteriye temiz başlangıç verir.
- Dayanak: Haber #14 (görev-bazlı rol tasarımı vurgusu) + Yetki & SoD ilkeleri 00_Baglam/06_Guvenlik_ve_Kimlik.md md.20
- 3 Aylık Çıktı (ölçülebilir): Tek-rol/türetilmiş-rol/kompozit-rol için adlandırma + tasarım standardı dokümanı + en az 3 örnek görev rolü (PFCG) ve "yapma/yap" kontrol listesi.
- Gerekli yetkinlik: PFCG (tek/türetilmiş/kompozit rol), SU24 öneri değerleri, en-az-yetki ilkesi.

### IAS Üzerinden SSO + Entra ID Kullanıcı Provizyon PoC
- İş kolu: Yetkilendirme · Zorluk: Orta
- İhtiyaç: Eski temel kimlik doğrulama ve SCIM v1 kullanımdan kaldırılıyor; kimlik buluta taşınırken IAS (Identity Authentication) ile SSO ve kurumsal kimlik sağlayıcıdan kullanıcı senkronizasyonu kurma becerisi gerekiyor.
- Değer/Etki: Çoğu bulut/RISE müşterisinde gereken temel bir yetkinliktir; göç zorunlu olduğu için talep süreklidir, ekip için yüksek getirili bir taban beceridir.
- Dayanak: Haber #9 (SCIM API v1 decommissioning, SCIM 2.0'a geçiş) ve Haber #10 (SuccessFactors temel kimlik doğrulama EOL) 02_SAP_Haberleri/06_Guvenlik_Uyumluluk.md
- 3 Aylık Çıktı (ölçülebilir): IAS deneme kiracısında 1 uygulamaya SAML 2.0 SSO bağlama + Entra ID'den SCIM 2.0 ile kullanıcı provizyon akışının çalışan PoC'si ve adım-adım runbook.
- Gerekli yetkinlik: IAS/IPS temel kavramları, SAML 2.0/OIDC, SCIM 2.0; eksikse "Hiç bilmiyorsam ilk adım" (IAS deneme kiracısı) ile başla.

### IPS ile Otomatik Joiner-Mover-Leaver (Yaşam Döngüsü) Provizyonu
- İş kolu: Yetkilendirme · Zorluk: Orta
- İhtiyaç: Kullanıcı işe başlama/rol değişimi/ayrılma süreçleri çoğu yerde elle yapılıyor; bu hem gecikme hem de "ayrılan kullanıcının yetkisi açık kaldı" gibi denetim riskleri doğuruyor.
- Değer/Etki: Erişim hijyenini otomatikleştirip artık (orphan) hesapları ve aşırı yetkiyi azaltır; denetim ve DORA gibi uyumluluk gereklerine doğrudan katkı sağlar.
- Dayanak: 00_Baglam/06_Guvenlik_ve_Kimlik.md md.19, md.31 (IPS ile sistemler arası provizyon/senkron) + Haber #13 (DORA: kimlik yönetimi) 02_SAP_Haberleri/06_Guvenlik_Uyumluluk.md
- 3 Aylık Çıktı (ölçülebilir): IPS ile kaynak kimlik sağlayıcıdan hedef sisteme otomatik joiner ve leaver (devre dışı bırakma) akışının PoC'si + kural/dönüşüm yapılandırma notları.
- Gerekli yetkinlik: IPS provizyon kuralları, SCIM 2.0, kaynak/hedef sistem bağlama; eksikse önce IPS temel akışını öğren.

### DORA Uyumlu Yetki & Denetim Kaydı Kontrol Listesi
- İş kolu: Yetkilendirme · Zorluk: Orta
- İhtiyaç: DORA (Dijital Operasyonel Dayanıklılık Yasası) finansal kurumlardan erişim kontrolü, denetim kaydı saklama ve raporlama istiyor; ekipte "yetki tarafında DORA için ne yapmalıyız" diye somut bir kontrol listesi yok.
- Değer/Etki: Finans sektörü müşterilerinde satışa ve denetime hazır bir uyumluluk artefaktı sağlar; düzenleyici baskı altındaki bir pazara doğrudan hitap eder.
- Dayanak: Haber #13 (DORA Enforcement in 2026: kimlik yönetimi, denetim kaydı saklama, raporlama) 02_SAP_Haberleri/06_Guvenlik_Uyumluluk.md + denetim kaydı SM19/RSAU_CONFIG 03_Basis_Operasyonlari/01_Klasik_OnPrem_Operasyonlar.md md.48
- 3 Aylık Çıktı (ölçülebilir): Yetki + denetim kaydı (RSAU/SM19-SM20) açısından DORA gereklerini madde madde eşleyen bir kontrol listesi + bir test sisteminde mevcut-durum boşluk (gap) raporu.
- Gerekli yetkinlik: SM19/RSAU_CONFIG denetim kaydı yapılandırma, SU01/PFCG, temel uyumluluk okuma.

### Acil Erişim (Firefighter) Yönetimi PoC
- İş kolu: Yetkilendirme · Zorluk: Orta
- İhtiyaç: Geçici yüksek yetki ihtiyaçları (üretimde acil müdahale) çoğu yerde kontrolsüz "süper kullanıcı" paylaşımıyla çözülüyor; kim, ne zaman, ne yaptı izlenemiyor.
- Değer/Etki: En-az-yetki ve denetlenebilirlik sağlayarak hem güvenlik hem uyumluluk riskini düşürür; denetimlerde sık çıkan bir bulguyu kapatır.
- Dayanak: GRC Access Control Emergency Access Management (EAM) ürün yeteneği + Haber #12 (yeni nesil GRC Access Control) 02_SAP_Haberleri/06_Guvenlik_Uyumluluk.md
- 3 Aylık Çıktı (ölçülebilir): Firefighter rolü + kayıt/onay/log inceleme akışının bir test sisteminde çalışan PoC'si (GRC EAM veya manuel-kontrollü model) + işletim prosedürü.
- Gerekli yetkinlik: PFCG, denetim kaydı okuma; GRC EAM varsa kullan, yoksa manuel firefighter modelini önce tasarla.

### Aşırı Yetki & SAP_ALL Temizlik (Authorization Cleanup) Analiz Aracı
- İş kolu: Yetkilendirme · Zorluk: Başlangıç
- İhtiyaç: Çoğu sistemde kullanıcılara zamanla biriken kullanılmayan yetkiler, SAP_ALL/SAP_NEW kalıntıları ve geniş yetki nesneleri var; bunlar saldırı yüzeyini ve SoD riskini büyütüyor.
- Değer/Etki: Hızlı, görünür bir kazanım (azaltılan riskli yetki sayısı) üretir; düşük giriş bariyeriyle ekibe somut bir "önce/sonra" metriği ve yöneticiye net ROI verir.
- Dayanak: En-az-yetki ilkesi 00_Baglam/06_Guvenlik_ve_Kimlik.md + kullanıcı/yetki temel operasyonları (SU01/PFCG, SU53/ST01/SU24) 03_Basis_Operasyonlari/01_Klasik_OnPrem_Operasyonlar.md md.44-45
- 3 Aylık Çıktı (ölçülebilir): Bir test sisteminde SAP_ALL/geniş yetkiye sahip kullanıcıları ve kullanılmayan yetkileri (ST03N/SU24 kullanım verisi + SUIM) listeleyen rapor + önerilen temizlik aksiyonları ve "azaltılan riskli kullanıcı sayısı" metriği.
- Gerekli yetkinlik: SUIM (kullanıcı bilgi sistemi), SU53/ST01, PFCG; başlangıç seviyesi için ideal, ek eğitim gerekmez.

### Kullanım-Temelli Rol İyileştirme (Role Right-Sizing) PoC
- İş kolu: Yetkilendirme · Zorluk: Başlangıç
- İhtiyaç: Roller genelde "ihtiyaç olur" diye geniş tasarlanıyor; oysa gerçek kullanım verisi (hangi işlem/yetki gerçekten çağrıldı) toplanırsa rol en-az-yetkiye çekilebilir, ama bu veri çoğu yerde hiç kullanılmıyor.
- Değer/Etki: Var olan rolleri kanıta dayalı küçültür; en-az-yetki ilkesini somut veriyle hayata geçirir ve gelecekteki SoD/denetim yükünü azaltır, düşük maliyetli yüksek etkili bir kazanım.
- Dayanak: SU24 öneri değerleri ve yetki kontrolü 03_Basis_Operasyonlari/01_Klasik_OnPrem_Operasyonlar.md md.45 + en-az-yetki 00_Baglam/06_Guvenlik_ve_Kimlik.md
- 3 Aylık Çıktı (ölçülebilir): Seçilen 1-2 rol için kullanım izleme (ST03N + SU24/STAUTHTRACE) verisiyle "kullanılan vs. tanımlı yetki" karşılaştırması ve önerilen küçültülmüş rol taslağı (PFCG).
- Gerekli yetkinlik: ST03N iş yükü/kullanım verisi, STAUTHTRACE/SU24, PFCG temel rol düzenleme.

---

## SAP Güvenliği

### CVE-2025-31324 İhlal Tarama (Compromise Assessment) Kiti — NetWeaver Java/Visual Composer
- İş kolu: SAP Güvenliği · Zorluk: Orta
- İhtiyaç: Visual Composer açığı (CVE-2025-31324, CVSS 10.0) yamalanmadan önce yetkisiz dosya yükleyen saldırganlar arka kapı bırakmış olabilir; yalnız yama yetmez, "yamadan önce zaten girildi mi?" sorusunu yanıtlayan bir ihlal tarama (compromise assessment) kiti yok.
- Değer/Etki: Yama sonrası sessiz kalmış web shell / yetkisiz yüklemeyi ortaya çıkarır, müşteriye "temiz misiniz?" güvencesi verir ve MSSP/SOC hizmetinin satılabilir somut bir parçasını üretir.
- Dayanak: Haber #1 (CVE-2025-31324 aktif istismar — yetkisiz dosya yükleme) + Haber #15 (ICF/RFC saldırı yüzeyi).
- 3 Aylık Çıktı (ölçülebilir): NetWeaver Java/ICF dizinlerinde IoC (şüpheli dosya/JSP, anormal yükleme zaman damgası) tarayan script + kontrol listesi; 1 test sisteminde uçtan uca koşturulmuş örnek rapor.
- Gerekli yetkinlik: NetWeaver Java/ICF yapısı, log/dosya sistemi analizi, IoC kavramı (yoksa önce CVE-2025-31324 Onapsis IoC notunu oku).

### Güvenlik Yapılandırma Sapma (Drift) İzleyici — RZ10/RZ11 Parametre Tabanı
- İş kolu: SAP Güvenliği · Zorluk: Başlangıç
- İhtiyaç: Güvenlik parametreleri (login/*, gw/*, snc/*, rfc) zamanla elle değiştirilip sertleştirme bozuluyor; "onaylı taban (baseline) ile bugünkü durum arasındaki sapma" düzenli ölçülmüyor.
- Değer/Etki: Sessiz güvenlik gerilemelerini düzenli yakalar, denetim öncesi "neden değişti" kanıtı sağlar; düşük efor, hızlı somut çıktı — yöneticinin görünür ROI gördüğü bir başlangıç projesi.
- Dayanak: Sunum özeti (Basis Güvenlik Operasyonları: "Güvenlik Parametre Takibi") + Bağlam §4 (güvenlik parametre takibi somut beceri).
- 3 Aylık Çıktı (ölçülebilir): Parametre snapshot toplayıcı + onaylı baseline ile diff üreten araç ve haftalık sapma raporu; 2-3 sistemde çalışan ilk sürüm.
- Gerekli yetkinlik: RZ10/RZ11 parametre bilgisi, SAP güvenlik best-practice tabanı, Python/PowerShell betikleme.

### HotNews Önceliklendirme Asistanı — System Recommendations'tan Etki Skoru
- İş kolu: SAP Güvenliği · Zorluk: Başlangıç
- İhtiyaç: Kritik güvenlik notu sayısı arttı; ham HotNews listesi "hangisi BENİM sistemimi etkiliyor, hangisi acil" sorusunu yanıtlamıyor — ekip her ay çok sayıda notu elle eliyor.
- Değer/Etki: Yama eforunu gerçekten etkilenen ve yüksek-CVSS notlara odaklar; aylık yama döngüsünü hızlandırır ve "neden bu sırayla yamaladık" gerekçesini denetime hazır kılar.
- Dayanak: Haber #3 (SAP Security Notes 2025 — kritik not sayısında artış) + Bağlam §5 (System Recommendations / EarlyWatch ile HotNews ayıklama).
- 3 Aylık Çıktı (ölçülebilir): System Recommendations çıktısını CVSS + bileşen kurulu mu + istismar durumu ile skorlayıp sıralayan rapor; bir aylık yama döngüsünde pilot kullanım.
- Gerekli yetkinlik: System Recommendations/SNOTE akışı, CVSS okuma, basit skorlama (mevcut Güvenlik Sağlık Taraması'ndan farkı: yalnız not önceliklendirme).

### RISE Güvenlik Sorumluluk (RACI) Matrisi & Müşteri-Tarafı Kontrol Kataloğu
- İş kolu: SAP Güvenliği · Zorluk: Orta
- İhtiyaç: RISE'de altyapı SAP'de, ama kimlik/erişim/özel kod/konfigürasyon/tehdit izleme müşteride; bu sınır çoğu projede yazılı değil, sonuçta kimsenin sahiplenmediği güvenlik boşlukları kalıyor.
- Değer/Etki: "Kimin işi" tartışmasını sözleşme öncesi netleştirir, denetimde boşluk göstermez ve MSSP teklifinin kapsamını somutlaştırarak satışı kolaylaştırır.
- Dayanak: Haber #8 (RISE paylaşılan sorumluluk) + Bağlam §3 (müşteri tarafı kontroller Basis'e kayıyor). (Onboarding R&R matrisinden farkı: yalnız GÜVENLİK kontrolleri ve müşteri-tarafı kanıt.)
- 3 Aylık Çıktı (ölçülebilir): RISE güvenlik kontrolleri için RACI matrisi + her müşteri-tarafı kontrol için "kanıt nasıl üretilir" şablonu; 1 müşteri kapsamında doldurulmuş örnek.
- Gerekli yetkinlik: RISE/ECS operasyon modeli, SAP güvenlik kontrol alanları, RACI/uyumluluk dokümantasyonu.

### HANA Ayrıcalık Yükseltme Sertleştirme & Yetki Denetimi (Note 3691059)
- İş kolu: SAP Güvenliği · Zorluk: Orta
- İhtiyaç: HANA 2.0 SP7/SP8'de ayrıcalık yükseltme açığı (Security Note 3691059) yamalandı; ama HANA DB seviyesinde aşırı yetkili kullanıcılar/sistem privileges'ler ve revizyon durumu çoğu sahada düzenli denetlenmiyor — yama tek başına yeterli sertleştirme değil.
- Değer/Etki: Veritabanı katmanındaki ayrıcalık yığılmasını ve eksik revizyonu görünür kılar; ABAP/uygulama katmanına odaklı klasik güvenlik işinin DB tarafındaki boşluğunu kapatır.
- Dayanak: Haber #5 (HANA 2.0 SP7/SP8 ayrıcalık yükseltme — Security Note 3691059).
- 3 Aylık Çıktı (ölçülebilir): HANA revizyon/SP doğrulama + sistem privileges ve aşırı yetkili kullanıcı denetim sorguları seti ve sertleştirme kontrol listesi; 1 HANA sisteminde örnek rapor.
- Gerekli yetkinlik: HANA kullanıcı/yetki modeli (system/object privileges), HANA SQL, SP/revizyon yönetimi.

### Transport/ABAP Güvenlik Kapısı — CI/CD'ye Güvenlik Denetimi Katma (DevSecOps)
- İş kolu: SAP Güvenliği · Zorluk: İleri
- İhtiyaç: İstismarlar AI ile hızlanırken ve Basis "platform mühendisi"ne dönüşürken, taşınan ABAP/transport içeriği üretime girmeden önce güvenlik açısından (yetki kontrolü açıkları, hardcoded kimlik, riskli FM çağrıları) otomatik denetlenmiyor; güvenlik üretimden sonra fark ediliyor.
- Değer/Etki: Güvenliği sola kaydırır (shift-left), insan inceleme yükünü azaltır ve "güvenli teslimat" anlatısıyla MSSP/RISE vizyonunu somut bir mühendislik pratiğine bağlar.
- Dayanak: Haber #7 (2026: istismarların AI ile hızlanması, Basis → platform mühendisi, CI/CD'ye güvenlik katma). (npm tedarik zinciri taramasından farkı: ABAP/transport içeriği ve ATC güvenlik kontrolleri.)
- 3 Aylık Çıktı (ölçülebilir): Transport öncesi ATC güvenlik kontrol seti (security variant) + onay kapısı (gate) tasarımı ve örnek bulgu raporu; bir transport hattında pilot.
- Gerekli yetkinlik: ABAP/ATC (Code Inspector), TMS, CI/CD pipeline mantığı, ABAP güvenlik anti-paternleri.

### Joule/AI Ajan Erişim Riski Değerlendirme Çerçevesi
- İş kolu: SAP Güvenliği · Zorluk: İleri
- İhtiyaç: Joule gibi geniş erişimli AI ajanları kullanıcı adına işlem yapınca beklenmedik görev-ayrılığı (SoD) çakışmaları ve aşırı yetki riski doğurabiliyor; "AI ajanı hangi yetkiyle, kimin adına ne yapabilir" sorusunu değerlendiren bir çerçeve yok.
- Değer/Etki: Gelişmekte olan bir saldırı/uyumluluk yüzeyini (agentic erişim) erkenden ele alır; ekibi "AI-çağı güvenliği"nde öne çıkarır ve denetçilerin yeni sorularına hazır eder.
- Dayanak: Haber #14 (S/4HANA SoD — Joule'ün geniş erişimli kullanıcılarda çakışma riski) + Haber #7 (AI-hızlandırılmış tehditler). (SoD matris yeniden tasarımından farkı: odak özel olarak AI/ajan kimliği ve yetki sınırı.)
- 3 Aylık Çıktı (ölçülebilir): Joule/ajan teknik kullanıcısının yetki envanteri + SoD çakışma tarama + "ne kısıtlanmalı" öneri raporu; 1 pilot sistemde değerlendirme.
- Gerekli yetkinlik: PFCG/yetki analizi, SoD çakışma mantığı, Joule yetkilendirme modeli temelleri (yoksa önce Joule teknik kullanıcı/scope kavramını öğren).

---

## Veri Yönetimi

### En Şişkin 10 Tablo Avı: TCO Hızlı Kazanç Raporu
- İş kolu: Veri Yönetimi · Zorluk: Başlangıç
- İhtiyaç: Çoğu sistemde RAM (sistemin pahalı hızlı belleği) birkaç dev tablo tarafından tüketilir ama büyüme trendi ölçülmez; görünmez büyüme kapasiteyi hep "daha fazla donanım al" çözümüne iter.
- Değer/Etki: Tek standart rapor TCO (toplam sahip olma maliyeti) konuşmasını başlatır; somut MB/GB kazanç sayısı yöneticiye donanım/lisans tasarrufunu doğrudan gösterir. Düşük efor, hızlı somut çıktı — oy gerekçesi net.
- Dayanak: 00_Baglam/07 madde 5 "büyüme/trend analizi + en şişkin 5-10 tabloyu bul, housekeeping/arşiv stratejisi öner".
- 3 Aylık Çıktı (ölçülebilir): 2-3 sistemde en şişkin 10 tablonun büyüme trendi + her biri için aksiyon (housekeeping/partition/arşiv) ve tahmini GB kazanç içeren tek standart rapor şablonu.
- Gerekli yetkinlik: DB02/temel SQL, tablo boyut/trend okuma (mevcut Basis becerisi; ileri bilgi gerekmez).

### NSE Pilotu: Sık Kullanılmayan Veriyi RAM'den Diske Taşıma
- İş kolu: Veri Yönetimi · Zorluk: Orta
- İhtiyaç: "Ilık" veri (nadiren okunan ama silinemeyen) pahalı RAM'i işgal eder; NSE (Native Storage Extension) bunu diske alıp RAM'i boşaltır ama çoğu ekip pratikte hiç denememiştir.
- Değer/Etki: Ölçülen RAM kazancı doğrudan donanım maliyetine dokunur; düşük riskli, geri alınabilir bir tekniğin kanıtlanması ekibe tekrar kullanılabilir bir TCO aracı kazandırır.
- Dayanak: 00_Baglam/07 madde 4 "NSE — diskte RAM'in ~4 katı kapasite, %10 buffer cache".
- 3 Aylık Çıktı (ölçülebilir): Test sisteminde 2-3 aday tabloya NSE uygulanıp önce/sonra RAM kullanımı ve sorgu süresi karşılaştırması; ölçülen RAM kazancı ve gecikme etkisini içeren PoC raporu + uygulama prosedürü.
- Gerekli yetkinlik: HANA NSE/Data Tiering temeli (yoksa önce SAP Learning'de NSE modülünü çalış).

### ILM/Arşiv Hazırlık Çantası: KVKK Saklama-İmha Matrisi
- İş kolu: Veri Yönetimi · Zorluk: Orta
- İhtiyaç: Veriyi yasal süre dolunca silmek (ILM) zorunlu ama çoğu sistemde hangi nesnenin ne kadar saklanacağı yazılı değil; arşivleme stratejisiz başlatılamaz.
- Değer/Etki: Hem uyum riskini (KVKK/GDPR) azaltır hem de S/4HANA geçişi öncesi veri küçültmenin önünü açar; yönetici için "hem uyum hem maliyet" çift kazanç.
- Dayanak: 00_Baglam/07 madde 4 "ILM, KVKK/GDPR uyumu, SARA arşiv stratejisi".
- 3 Aylık Çıktı (ölçülebilir): En hacimli 5-8 arşiv nesnesi için saklama süresi + imha kuralı + tahmini hacim kazancı içeren matris ve bir nesnede SARA ile pilot arşivleme çalıştırması (test).
- Gerekli yetkinlik: SARA arşivleme + ILM kavramları (yoksa önce ILM temel modülü).

### BDC Bağlantı PoC'i: S/4HANA Tablosunu Datasphere'e Bağla
- İş kolu: Veri Yönetimi · Zorluk: Başlangıç
- İhtiyaç: Ekip BDC'ye (Business Data Cloud) girmek istiyor ama "ilk bağlantıyı nasıl kurarız" deneyimi yok; Cloud Connector + DP Agent (on-prem veriyi buluta taşıyan köprü) kurulumu görülmemiş.
- Değer/Etki: Giriş eşiği düşük, etkisi büyük: ilk uçtan uca bağlantı kanıtlanınca ekip BDC projelerine güvenle teklif verebilir ve runbook tekrar kullanılabilir referans olur.
- Dayanak: 00_Baglam/07 madde 5 "küçük bir BDC bağlantı PoC'i — Cloud Connector + DP Agent ile test tablosunu Datasphere'e bağla"; Haber #2 (BDC Launch & Innovation Guide).
- 3 Aylık Çıktı (ölçülebilir): Test S/4HANA'dan 1 tablonun Cloud Connector + DP Agent üzerinden Datasphere/BDC'de canlı görünür hale gelmesi + adım adım kurulum runbook'u.
- Gerekli yetkinlik: Cloud Connector + DP Agent kurulumu (çoğu Basis bağlantı becerisiyle örtüşür; trial hesabı yeterli).

### Zero-Copy Federation Ölçüm Bankı: Snowflake/Azure SQL Bağlantısı
- İş kolu: Veri Yönetimi · Zorluk: İleri
- İhtiyaç: HANA Cloud, Data Access Agent ile Snowflake/Azure SQL'e federation (veriyi kopyalamadan sorgulama) yapabiliyor; ama gecikme ve bant genişliği yönetilmezse bu senaryolarda performans düşer.
- Değer/Etki: Zero-copy SAP'nin merkezi stratejisi; gecikme/maliyet ölçülebilir hale gelirse ekip müşteriye "kopyalamadan da çalışır, işte sayılar" diyebilir — somut bir farklılaştırıcı.
- Dayanak: Haber #13 (Data Access Agent ile Azure SQL/Snowflake federation), Haber #7 (SAC↔Snowflake canlı bağlantı, Data Access Agent), Haber #11 (SAP–Snowflake zero-copy).
- 3 Aylık Çıktı (ölçülebilir): HANA Cloud trial ↔ bir dış kaynak (Snowflake/Azure SQL) federation kurulup federated vs. replike sorgu gecikmesi/bant genişliği karşılaştırma raporu + öneri eşikleri.
- Gerekli yetkinlik: SDA/SDI, Data Access Agent, federation kurulumu (yoksa önce SDA virtual table temelini öğren).

### HANA Vektör + RAG Altyapı PoC'i: AI İçin Veri Hazırlığı
- İş kolu: Veri Yönetimi · Zorluk: İleri
- İhtiyaç: HANA Cloud'a vektör arama, embedding ve RAG (verilerle beslenen LLM cevabı) yetenekleri geldi; ama bunları kim kuracak, kaynak tüketimini kim yönetecek belirsiz — bu yeni iş Basis'in masasında.
- Değer/Etki: AI projelerinin altyapı kapısı burası; ekip vektör/RAG'ı kurabildiğini gösterirse büyüyen AI talebinde altyapı sahibi olur ve dışarıdan danışman bağımlılığını azaltır.
- Dayanak: Haber #4 (HANA Cloud embedding/AutoML, AI iş akışları); 00_Baglam/07 madde 4 "HANA vektör/Knowledge Graph altyapısı".
- 3 Aylık Çıktı (ölçülebilir): HANA Cloud'da küçük bir doküman setiyle embedding + vektör arama PoC'i; bellek/CPU tüketim ölçümü ve "RAG altyapısı için boyutlandırma" notu.
- Gerekli yetkinlik: HANA Cloud vektör engine + temel Python (yoksa önce HANA ML/vektör tanıtım modülü).

### Veri Ürünü Yaşam Döngüsü Yönetişim Şablonu (Data Product Studio)
- İş kolu: Veri Yönetimi · Zorluk: Orta
- İhtiyaç: BDC Data Product Studio ile yeniden kullanılabilir "veri ürünleri" oluşturuluyor ama metadata, erişim kontrolü ve yaşam döngüsü kuralları tanımlı değilse yönetişim dağılır.
- Değer/Etki: Yönetişimli veri katmanı Joule ve AI ajanlarının güvenilir yakıtı; ekip "kim hangi veri ürününe erişir, nasıl versiyonlanır" çerçevesini sunarsa BDC projelerinde altyapı + yönetişim sahibi olur.
- Dayanak: Haber #10 (Data Product Studio GA H1 2026, yaşam döngüsü/metadata/erişim kontrolü), Haber #8 (Joule ajanları BDC'den güvenilir bağlam tüketiyor).
- 3 Aylık Çıktı (ölçülebilir): Bir örnek veri ürünü için rol/erişim matrisi + versiyon/yaşam döngüsü + lineage politikası şablonu ve trial'da 1 veri ürününde uygulamalı doğrulama.
- Gerekli yetkinlik: BDC/Datasphere Spaces, RBAC, veri ürünü kavramı (yoksa önce Data Product Studio tanıtım kaynağı).

### Signavio Process Mining ↔ S/4HANA/BW Veri Besleme Mimarisi
- İş kolu: Veri Yönetimi · Zorluk: Orta
- İhtiyaç: Signavio Process Mining süreçleri analiz ederken kaynak veriyi (S/4HANA/BW) doğru, düzenli ve performanslı beslemeye ihtiyaç duyar; bu veri boru hattı ve izleme altyapısı Basis işidir ama çoğu yerde tasarlanmamıştır.
- Değer/Etki: Signavio Gartner Process Intelligence'ta Lider; süreç madenciliği talebi artarken veri besleme mimarisini hazır eden ekip bu projelere altyapı tarafından sahip olur ve hızlı devreye alma sağlar.
- Dayanak: Haber #14 (Signavio Gartner Process Intelligence Lideri; S/4HANA/BW entegrasyonu ve izleme altyapısı).
- 3 Aylık Çıktı (ölçülebilir): S/4HANA/BW'den Signavio'ya veri besleme mimari diyagramı + bir süreç (ör. satınalma) için örnek veri çıkarım/yenileme akışı PoC'i ve izleme/performans kontrol listesi.
- Gerekli yetkinlik: BW/S4 veri çıkarımı + Signavio bağlantı kavramı (yoksa önce Signavio data integration tanıtımı).

---

## BDC (Business Data Cloud)

### S/4HANA → Datasphere İlk Bağlantı PoC'i (Cloud Connector + DP Agent)
- İş kolu: BDC (Business Data Cloud) · Zorluk: Başlangıç
- İhtiyaç: Ekipte BDC'ye giriş için düşük eşikli, somut bir referans mimari yok; bağlantı kurulumu (Cloud Connector + DP Agent) belgesiz, kişiye bağlı tecrübeyle yapılıyor.
- Değer/Etki: Mevcut Basis becerisini (tünel, agent, ağ) doğrudan yeni stratejik alana taşır; ekibe tekrar kullanılabilir bir "ilk gün" şablonu kazandırarak müşteri PoC'lerinde kurulum süresini ve hata payını düşürür. Diğer tüm BDC çalışmalarının ön koşulu.
- Dayanak: Bağlam 00/07 madde 5 (önerilen ilk PoC) ve sunum "Mimari & Bağlantı" sütunu (Cloud Connector + DP Agent + Remote Table Mapping).
- 3 Aylık Çıktı (ölçülebilir): Bir test S/4HANA tablosunu Datasphere'e canlı bağlayan çalışan PoC + adım adım kurulum runbook'u (ekran görüntülü, ağ/port listesi dahil).
- Gerekli yetkinlik: Cloud Connector, DP Agent kurulumu, temel ağ/port bilgisi (mevcut Basis becerisiyle örtüşür).

### SDA vs. SDI Karar Rehberi ve Performans Kıyas Raporu
- İş kolu: BDC (Business Data Cloud) · Zorluk: Orta
- İhtiyaç: Veriyi taşımadan sanallaştırma (SDA) ile anlık replikasyon (SDI) arasında "ne zaman hangisi" kararı sezgisel veriliyor; gecikme ve yük etkisi ölçülmüyor.
- Değer/Etki: Veri çekme kararını yöneticiye ve müşteriye sayısal gerekçeyle sunma imkanı verir; yanlış teknoloji seçiminden doğan performans ve maliyet riskini somut veriyle azaltır.
- Dayanak: Sunum "Mimari & Bağlantı" (SDA/SDI, Remote Table Mapping) ve Bağlam 00/07 madde 4 (SDA/SDI ile sanallaştırma/replikasyon).
- 3 Aylık Çıktı (ölçülebilir): Aynı tablo seti üzerinde SDA ve SDI senaryolarının sorgu gecikmesi ve kaynak tüketimini kıyaslayan tablo + tek sayfalık karar ağacı.
- Gerekli yetkinlik: SDA/SDI yapılandırma, Remote Table Mapping, temel SQL performans okuma (HANA plan görselleştirme).

### Datasphere Spaces İçin RBAC ve Satır-Bazlı Yetki Şablonu
- İş kolu: BDC (Business Data Cloud) · Zorluk: Orta
- İhtiyaç: Spaces (izole çalışma alanları) çoğaldıkça erişim kontrolü ad-hoc kuruluyor; SAML 2.0 ve satır-bazlı yetki (RBAC) için standart bir kalıp yok.
- Değer/Etki: Yönetişim ve denetim (audit) riskini azaltır; yeni Space açılışını standartlaştırarak hızlandırır ve müşterideki güvenlik sorularına hazır cevap sağlar.
- Dayanak: Sunum "Güvenlik & Uç Nokta" (SAML 2.0 & satır bazlı yetki/RBAC) ve Bağlam 00/07 madde 4 (Spaces, SAML/RBAC).
- 3 Aylık Çıktı (ölçülebilir): 2-3 rol arketipi için (yönetici/modelleyici/okuyucu) hazır RBAC + satır-bazlı yetki şablonu ve SAML 2.0 kurulum kontrol listesi, bir test Space'inde uygulanmış.
- Gerekli yetkinlik: SAML 2.0 IdP entegrasyonu, Datasphere yetkilendirme modeli, RBAC tasarımı.

### Zero-Copy Hiper-Ölçekleyici Bağlantı Mimarisi Karşılaştırması (Databricks · Snowflake · AWS)
- İş kolu: BDC (Business Data Cloud) · Zorluk: İleri
- İhtiyaç: BDC Connect ile hiper-ölçekleyicilere (Databricks, Snowflake, AWS) zero-copy paylaşım açıldı; aralarındaki ağ, senkronizasyon ve yönetişim farkları için karşılaştırmalı bir Basis kılavuzu yok.
- Değer/Etki: Müşterinin mevcut bulut yatırımına göre doğru BDC entegrasyon yolunu seçmesini sağlar; ekibi çoklu-bulut veri fabric'i danışmanlığına hazırlar.
- Dayanak: Haber #1 (Databricks/Delta Sharing), Haber #11 (Snowflake data fabric), Haber #9 (AWS Athena zero-copy — H2 2026 GA planlı).
- 3 Aylık Çıktı (ölçülebilir): Üç hedef için ağ topolojisi, kimlik/yetki, senkronizasyon ve gecikme boyutlarını karşılaştıran matris + erişimi olan en az bir hedefte (örn. Snowflake veya Databricks) çalışan canlı bağlantı PoC'i. (AWS Athena GA'sı H2 2026 olduğundan masaüstü/dokümantasyon düzeyinde değerlendirilir.)
- Gerekli yetkinlik: Zero-copy/Delta Sharing kavramları, bulut ağı (VPC/private link), federation; eksikse önce BDC Connect dokümantasyonu çalışılır.

### Data Product Studio ile Yönetişimli Veri Ürünü Yaşam Döngüsü PoC'i
- İş kolu: BDC (Business Data Cloud) · Zorluk: Orta
- İhtiyaç: Data Product Studio (GA H1 2026) ile veri ürünleri SQL dönüşümlerle üretiliyor; ama veri ürünü yaşam döngüsü (oluşturma → versiyonlama → erişim → emeklilik) ve metadata yönetimi için Basis tarafında tanımlı süreç yok.
- Değer/Etki: "Veri ürünü sahipliği"ni Basis sorumluluğuna oturtur; tekrar kullanılabilir, denetlenebilir veri ürünleriyle müşteride veri kalitesi ve teslim hızı kazandırır.
- Dayanak: Haber #10 (Data Product Studio — SQL dönüşüm + tam yaşam döngüsü) ve Bağlam 00/07 madde 3 (veri ürünü yaşam döngüsü altyapı sorumluluğu).
- 3 Aylık Çıktı (ölçülebilir): Bir örnek veri ürününü uçtan uca (SQL dönüşüm + erişim kontrolü + versiyon) üreten PoC + yaşam döngüsü süreç akışı dokümanı.
- Gerekli yetkinlik: SQL view/dönüşüm, Datasphere modelleme, metadata/erişim kavramları.

### HANA Cloud Vektör/Embedding ve RAG Altyapısı Kurulumu (Joule Beslemesi)
- İş kolu: BDC (Business Data Cloud) · Zorluk: İleri
- İhtiyaç: Joule ve AI ajanları BDC'den güvenilir bağlam tüketiyor; bunun altında HANA Cloud embedding/vektör motoru ve RAG (bilgiyle zenginleştirilmiş üretim) iş akışı var, ama ekipte bu altyapıyı kuran yok.
- Değer/Etki: AI dalgasının altyapı katmanını Basis'e mal eder; "AI hazır veri" söylemini somut, kurulabilir bir yetkinliğe çevirerek yöneticiye geleceğe yatırım gerekçesi sunar.
- Dayanak: Haber #4 (HANA Cloud Q4 2025 — metin embedding ve AutoML), Haber #8 (Joule ajanları BDC'den bağlam tüketiyor), Bağlam 00/07 madde 4 (vektör/Knowledge Graph altyapısı).
- 3 Aylık Çıktı (ölçülebilir): HANA Cloud'da embedding/vektör tablosu + basit RAG sorgusu çalışan PoC + kaynak tüketimi (RAM/CPU) ölçüm raporu.
- Gerekli yetkinlik: HANA Cloud vektör/embedding özellikleri, RAG kavramı, temel Python; eksikse önce SAP HANA Cloud öğrenme kaynağı tamamlanır.

### Data Access Agent ile Federation Performans ve Bağlantı İzleme Çerçevesi
- İş kolu: BDC (Business Data Cloud) · Zorluk: Orta
- İhtiyaç: Data Access Agent ile Azure SQL ve Snowflake'e federation açıldı; SAC↔Snowflake canlı bağlantısında bant genişliği ve gecikme yönetimi kritik ama izleme/uyarı çerçevesi yok.
- Değer/Etki: Canlı federation senaryolarında gecikmeyi proaktif yönetir; müşterideki "yavaş rapor" şikayetlerini önleyerek SLA güvenini artırır.
- Dayanak: Haber #13 (Data Access Agent — Azure SQL/Snowflake federation, MCP GA), Haber #7 (SAC + canlı Snowflake — bant genişliği/gecikme yönetimi).
- 3 Aylık Çıktı (ölçülebilir): Data Access Agent ile bir federation bağlantısı kurulup gecikme/bant genişliği metriklerinin toplandığı izleme panosu + eşik-bazlı uyarı önerileri raporu.
- Gerekli yetkinlik: Data Access Agent yapılandırma, federation, temel izleme/metrik toplama.

### Collibra ile BDC Veri Kataloğu, Lineage ve AI Yönetişimi Senkronizasyon Tasarımı
- İş kolu: BDC (Business Data Cloud) · Zorluk: Orta
- İhtiyaç: Collibra ve SAP BDC entegrasyonuyla veri/AI yönetişimi tek platformda buluşuyor; ama veri kataloğu, lineage (verinin kökeni izi) ve yönetişim kurallarının BDC ile nasıl senkronize edileceği netleşmemiş.
- Değer/Etki: Düzenleyici denetim (audit) ve AI güveni için lineage'ı gösterilebilir kılar; "yönetişimli BDC" satışını destekleyen ayırt edici bir yetkinlik sağlar.
- Dayanak: Haber #15 (Collibra + SAP BDC — katalog, lineage, AI yönetişimi entegrasyonu) ve Bağlam 00/07 madde 3 (lineage altyapı sorumluluğu).
- 3 Aylık Çıktı (ölçülebilir): BDC veri ürünlerinin Collibra'ya yansıtıldığı entegrasyon tasarım dokümanı + bir uçtan uca lineage örneğinin gösterildiği demo (Collibra ortamı erişimi varsa PoC).
- Gerekli yetkinlik: Collibra temel kavramları (katalog/lineage), BDC metadata modeli, API entegrasyonu.

---

## Çapraz & Yeni Dönem (AIOps · FinOps · Observability · Sovereign)

### CALM Fair-Use Bütçe Bekçisi: 8 GB Kotası Şişmeden Uyaran Pano
- İş kolu: Çapraz & Yeni Dönem (AIOps · FinOps · Observability · Sovereign) · Zorluk: Başlangıç
- İhtiyaç: Cloud ALM (CALM — SolMan'in bulut halefi izleme aracı) ücretsiz tenant 8 GB bellek kotasıyla gelir; çok sistem bağlanınca veya veri uzun saklanınca kota sessizce şişer ve SAP CPEA (kullandıkça öde sözleşmesi) üzerinden ek depolama (genelde 4 GB'lık bloklar) satar. Bugün bu eşiğe yaklaşıldığını kimse önceden görmüyor.
- Değer/Etki: Sürpriz ek-depolama faturasını proaktif uyarıyla önler ve yöneticiye somut "kaçınılan maliyet" (avoided cost) rakamı sunar — düşük giriş engelli, FinOps refleksinin en görünür ilk kazanımı.
- Dayanak: 00_Baglam/08_Observability_CALM.md (Fair Use / 8 GB sınırı, CPEA ek depolama, Data Retention) + 02_SAP_Haberleri/07_Maintenance_2027_2030_Lisans.md Haber #9 (CALM API'leri).
- 3 Aylık Çıktı (ölçülebilir): CALM tenant doluluğunu izleyen, %70/%85/%95 eşiklerinde e-posta/Teams uyarısı atan bir pano + Data Retention öneri raporu (en çok yer kaplayan ilk 5 veri tipi). En az 1 gerçek tenant'ta canlı.
- Gerekli yetkinlik: CALM erişimi, temel API/script (Python/PowerShell); yoksa önce 00_Baglam/08'deki `/n/SDF/ALM_SETUP` ve veri toplayıcı akışını öğren.

### Sıfır-Gün Yama SLA Saati: HotNews → Yama Süresini Ölçen Operasyon Panosu
- İş kolu: Çapraz & Yeni Dönem (AIOps · FinOps · Observability · Sovereign) · Zorluk: Orta
- İhtiyaç: Sıfır-gün açıkları artık duyurulduktan saatler içinde silahlandırılıyor; aylık yama döngüsü yetmiyor. Çoğu ekibin "HotNews çıktı → bizim ortamda yamandı" arası geçen süreyi ölçen bir metriği yok.
- Değer/Etki: Güvenlik aciliyetini ölçülebilir bir KPI'ya (MTTR-patch) çevirir ve DORA (Dijital Operasyonel Dayanıklılık Yasası) gibi denetimlerde kanıt üretir — finans müşterilerine doğrudan satılabilir bir değer.
- Dayanak: 02_SAP_Haberleri/06_Guvenlik_Uyumluluk.md Haber #2 (zero-day silahlanması), #3 (artan kritik notlar), #13 (DORA sürekli izleme/raporlama).
- 3 Aylık Çıktı (ölçülebilir): HotNews/yüksek-öncelik notlarını sistem envanteriyle eşleyen, ortalama yama-süresini ve açık-kalan kritik not sayısını gösteren pano; 3 aylık bir baz çizgi (baseline) raporu.
- Gerekli yetkinlik: SAP Security Notes/System Recommendations akışı, temel raporlama; yoksa önce HotNews önceliklendirmesini öğren.

### Joule SoD Çakışma Tarayıcısı: AI Ajanı Erişimlerini Risk Matrisine Sokmak
- İş kolu: Çapraz & Yeni Dönem (AIOps · FinOps · Observability · Sovereign) · Zorluk: İleri
- İhtiyaç: Joule ve uzman ajanlar geniş erişimli teknik kullanıcılarla çalışıyor; bu, klasik SoD (Segregation of Duties — görevler ayrılığı) matrisinde görünmeyen yeni çakışma riskleri yaratıyor. Ajanların hangi yetkiyle ne yaptığını denetleyen bir görünürlük yok.
- Değer/Etki: Otonom işletmeye geçişin en büyük yönetişim boşluğunu kapatır; AI ajanlarını mevcut uyumluluk çerçevesine sokarak hem güvenlik hem audit riskini düşürür — yönetime "AI'ı güvenle açabiliriz" güvencesi.
- Dayanak: 02_SAP_Haberleri/06_Guvenlik_Uyumluluk.md Haber #14 (Joule'ün SoD çakışma riski) + 02_SAP_Haberleri/01_AI_BusinessAI_Joule.md Haber #2 (200+ ajan, ajan yönetişimi).
- 3 Aylık Çıktı (ölçülebilir): Ajan/teknik kullanıcı yetkilerini SoD matrisiyle kesiştiren bir analiz raporu + tespit edilen yüksek-riskli çakışmalar için somut rol-tasarımı önerisi (PoC olarak 1 sistem).
- Gerekli yetkinlik: Yetki/rol yönetimi, SoD mantığı, Joule/AI Core erişim modeli; yoksa önce 03_Basis_Operasyonlari/02_Cloud_Operasyonlar.md §8 (AI temelleri) ve XSUAA rol koleksiyonlarını öğren.

### SolMan → CALM Geçiş Hazırlık Radarı: 2027 Öncesi Boşluk Haritası
- İş kolu: Çapraz & Yeni Dönem (AIOps · FinOps · Observability · Sovereign) · Zorluk: Orta
- İhtiyaç: SolMan ana bakımı 31 Aralık 2027'de bitiyor; CALM birebir kopya değil (ChaRM'ın doğrudan karşılığı yok, veri göçü yok). Müşterilerin hangi SolMan işlevlerini kullandığı ve CALM'de karşılığının olup olmadığı çoğunlukla envanterlenmemiş.
- Değer/Etki: 2028 öncesi geçişin ilk somut adımını (boşluk analizi) üretir; müşteriye net bir yol haritası ve "paralel çalışma" maliyet/risk tablosu sunar — satış öncesi danışmanlık fırsatı.
- Dayanak: 00_Baglam/08_Observability_CALM.md (ChaRM boşluğu, paralel çalışma) + 02_SAP_Haberleri/07_Maintenance_2027_2030_Lisans.md Haber #8 (SolMan bakım bitişi).
- 3 Aylık Çıktı (ölçülebilir): 1 müşteri ortamı için SolMan kullanım envanteri (ChaRM/ITSM/Monitoring kapsamı) + her işlevin CALM karşılığını/boşluğunu işaretleyen geçiş hazırlık raporu ve aşamalı plan.
- Gerekli yetkinlik: SolMan işlev bilgisi, CALM kapsamı; yoksa önce 00_Baglam/08'deki CALM scope kurgusunu (Health/BPM) öğren.

### BTP Kredi Eritme Erken-Uyarı Sistemi: CPEA Tükenmeden Haber Veren Tahmin
- İş kolu: Çapraz & Yeni Dönem (AIOps · FinOps · Observability · Sovereign) · Zorluk: Orta
- İhtiyaç: BTP'de ödeme tüketime bağlı; krediler beklenmedik bir servis yüzünden hızla eriyince fatura sürpriz oluyor. UDMS (Usage Data Management Service — BTP tüketim verisini REST API ile veren ücretsiz servis) veriyi sunar ama "ne zaman biter, hangi servis hızlanıyor" uyarısını kimse kurmamış.
- Değer/Etki: Kredi tükenmesini önceden tahmin edip bütçe sürprizini engeller; "hangi servis beklenenden fazla yiyor" sorusunu yanıtlayarak doğrudan optimizasyon fırsatı çıkarır — yöneticinin sevdiği "para kazandıran" proje tipi.
- Dayanak: 00_Baglam/09_FinOps_Maliyet.md (CPEA kredi erimesi, UDMS `/cloudCreditsDetails`, `reporting-ga-admin` plan) + SAP-samples btp-resource-consumption-monitor referans reposu.
- 3 Aylık Çıktı (ölçülebilir): UDMS'ten kredi/tüketim çekip aylık erime hızını çıkaran, "tahmini tükenme tarihi" ve "anomali servis" uyarısı üreten bir araç (ilk sürüm, 1 global account'ta çalışır).
- Gerekli yetkinlik: UDMS API + OAuth 2.0 token, temel zaman-serisi tahmini; yoksa önce 09_FinOps §5'teki Discovery Center/API Reference ile başla (mevcut BTP Maliyet Tool deneyimine bitişik).

### CALM Entegrasyon & Exception İzleme PoC: "İçeride Ne Oluyor" Görünürlüğü
- İş kolu: Çapraz & Yeni Dönem (AIOps · FinOps · Observability · Sovereign) · Zorluk: Başlangıç
- İhtiyaç: Çoğu ekip CALM'i sadece "ayakta mı" (health) için kullanıyor; oysa observability'nin asıl değeri entegrasyon ve exception izlemede — "hangi arayüz hata veriyor, nerede yavaşlıyor". RFC metrik izleme (tRFC/qRFC/bgRFC kuyrukları) yeni eklendi ama kullanılmıyor.
- Değer/Etki: Reaktif "kullanıcı şikayet etti" operasyonundan proaktif hata yakalamaya geçiş; arıza süresini (downtime) düşürerek müşteri SLA'sını iyileştirir — somut operasyonel kalite kazanımı.
- Dayanak: 00_Baglam/08_Observability_CALM.md (Integration & Exception Monitoring, observability tanımı) + 02_SAP_Haberleri/07_Maintenance_2027_2030_Lisans.md Haber #9 (RFC metrik izleme tRFC/qRFC/bgRFC).
- 3 Aylık Çıktı (ölçülebilir): 1 sistemde Integration + Exception Monitoring kapsamı kurulmuş, RFC kuyruk metrikleri akıyor, en az 2 anlamlı uyarı tanımlı bir PoC + "yakalanan ilk N hata" raporu.
- Gerekli yetkinlik: CALM scope kurgusu, ST-PI/ST-A·PI add-on güncelliği; yoksa önce 03_Basis_Operasyonlari/02_Cloud_Operasyonlar.md §5'teki aktivasyon adımlarını uygula.

### AIOps Anomali Avcısı: Joule + n8n ile Otomatik Kök-Neden Triyaj Akışı
- İş kolu: Çapraz & Yeni Dönem (AIOps · FinOps · Observability · Sovereign) · Zorluk: İleri
- İhtiyaç: Uyarı sayısı artıyor ama her uyarıyı insan eliyle triyaj etmek (önceliklendirme + kök-neden ilk değerlendirme) ölçeklenmiyor. SAP, n8n'i (görsel iş akışı otomasyon platformu) Joule Studio'ya gömdü; bu, izleme uyarılarını AI ile zenginleştirip otomatik triyaj etmek için altyapı sunuyor.
- Değer/Etki: Operasyon ekibinin tekrar eden triyaj yükünü azaltır (AIOps = AI ile BT operasyonları), MTTR'yi düşürür ve mühendisi rutinden stratejik işe kaydırır — ekibi büyütmeden çıktı artıran kaldıraç.
- Dayanak: 02_SAP_Haberleri/01_AI_BusinessAI_Joule.md Haber #8 (Joule Studio + n8n) ve #9 (SAP'nin n8n yatırımı) + 03_Basis_Operasyonlari/02_Cloud_Operasyonlar.md §8 (n8n, AI ajan izleme).
- 3 Aylık Çıktı (ölçülebilir): Bir izleme uyarısını (örn. CALM/sistem alert) alıp AI ile zenginleştiren, kategorize edip ilgili ekibe yönlendiren bir n8n akışı PoC'u; en az 1 senaryoda uçtan uca çalışır + triyaj süresi öncesi/sonrası ölçümü.
- Gerekli yetkinlik: n8n iş akışı, AI Core/Generative AI Hub bağlama, webhook/API; yoksa önce n8n temelleri ve 03_Basis_Operasyonlari/02_Cloud_Operasyonlar.md §8'deki AI temellerini öğren.

### Çapraz-Müşteri Tüketim İzolasyon Denetçisi: Cross-Charge Sızıntı Kontrolü
- İş kolu: Çapraz & Yeni Dönem (AIOps · FinOps · Observability · Sovereign) · Zorluk: İleri
- İhtiyaç: Bir SAP iş ortağı tek global account altında çok müşteri barındırıp her birine tüketimini yansıtıyor (cross-charge). Kaynak API (UDMS) global seviyede TÜM müşterilerin verisini döndürür; izolasyonu uygulama katmanında kurmazsan bir müşteri diğerinin faturasını görür — hem maliyet hem güvenlik hatası.
- Değer/Etki: Veri sızıntısı riskini sistematik test eden bir güvence katmanı kurar; çok-kiracılı (multi-tenant) FinOps panolarının audit edilebilirliğini sağlar — müşteri güveni ve sözleşme uyumu için kritik.
- Dayanak: 00_Baglam/09_FinOps_Maliyet.md (UDMS global veri, row-level filtre izolasyonu, cross-charge tahminî) + mevcut BTP Maliyet Tool deneyimi (ekibin iç kaynağı — paylaşılan repoda yer almaz; §3, §6).
- 3 Aylık Çıktı (ölçülebilir): Row-level izolasyonu doğrulayan otomatik test seti (her müşteri yalnız kendi satırını görüyor mu?) + bulunan sızıntı/eksiklikler için düzeltme raporu; mevcut maliyet aracına entegre.
- Gerekli yetkinlik: CAP row-level filtre, çok-kiracılı yetkilendirme, test otomasyonu; yoksa önce 09_FinOps §3-4'teki izolasyon mantığını çalış.

---

> **Örnek katalog · 10 iş kolu + 1 çapraz tema.** Bu bir sipariş listesi değil; `/proje` bunları kişiye özel dinamik öneri için **bağlam/ilham** olarak kullanır.

