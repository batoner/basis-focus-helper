# Integration Suite — Entegrasyon ve Advanced Event Mesh

> Sistemleri birbirine konuşturma işi: SAP'nin bulut entegrasyon platformu ve olay-tabanlı mimari. Bilmiyorsan normal — aşağıda nereden başlanır yazıyor.

## 1. Bu nedir? (tek paragraf)

SAP Integration Suite, farklı sistemleri (SAP'ler arası, SAP ile üçüncü-parti uygulamalar, on-prem ile bulut) birbirine bağlayan SAP'nin bulut entegrasyon platformudur. Kısaca "n8n'in kurumsal karşılığı" diye düşünebilirsin: n8n nasıl küçük servisleri görsel akışlarla birbirine bağlıyorsa, Integration Suite de aynı işi kurumsal ölçekte, güvenlik/yönetişim/izleme katmanıyla yapar. Bu bir "ürün ailesi"dir; içinde en çok kullanılan üç parça var: **Cloud Integration** (entegrasyon akışları çalıştırır — eski adıyla CPI), **API Management** (API'leri yayınlama, koruma, izleme) ve **Advanced Event Mesh** (olay-tabanlı haberleşme). SAP, bu alanda 2026 Gartner iPaaS Magic Quadrant'ında altıncı kez "Lider" gösterildi — yani SAP ekosisteminde entegrasyon stratejik bir konum (bkz. ../02_SAP_Haberleri/02_BTP_ve_Gelistirme.md, [SAP Recognized as Six-Time Leader in 2026 Gartner Magic Quadrant for iPaaS](https://news.sap.com/2026/03/sap-six-time-leader-gartner-magic-quadrant-ipaas/)).

## 2. Neden önemli / nereye gidiyor?

Çünkü hiçbir sistem tek başına yaşamıyor. S/4HANA, SuccessFactors, Ariba, bir banka API'si, bir lojistik firması — hepsinin konuşması lazım, bu da entegrasyon demek. Yön ise net: platform **AI-destekli** hale geliyor. 2025-2026 yol haritasında Joule (SAP'nin yapay zekâ asistanı) ile akış keşfi, anomali tespiti, API trafik tahmini ve yeni adaptörler (Adobe Sign, Google, Oracle, Salesforce) geldi (bkz. ../02_SAP_Haberleri/02_BTP_ve_Gelistirme.md, [Integration Suite in 2025 & 2026: AI-Ready Integration Fabric](https://community.sap.com/t5/technology-blog-posts-by-members/integration-suite-in-2025-amp-2026/ba-p/14320912)). Senin takımın açısından ayrıca somut: ekibin bir **Integration Suite partnerlik anlaşması** var ve dönüşüm yol haritasında "Integration Suite uzman ekibi" açık bir hedef (bkz. ../01_Sunum_Ozetleri/Servis_Otomasyon.md).

## 3. Basis için ne anlama geliyor?

Burası senin doğal genişlemen. AI tarafında tezimiz "AI'ı *neye* uygulayacağını bilmek" idi (bkz. ../03_AI_ve_Otomasyon.md); Integration Suite ise **"AI'ı ve sistemleri birbirine nasıl bağlayacağın"** katmanı. Cloud Connector'da yüzlerce sistem bağlamış bir Basis mühendisi olarak ağ, kimlik, sertifika, on-prem→bulut köprüsü zaten senin dünyan — Integration Suite bunun bir üst katı. Pratikte Basis'in payına düşen: tenant kurulumu/kapasite planlama, güvenli bağlantı (Cloud Connector, sertifika, OAuth), izleme ve **maliyet kontrolü**. Bu sonuncusu kritik: platform **mesaj-başına faturalanır** — işlenen her mesaj kredi tüketir, 250 KB'tan büyük mesajlar her 250 KB için ek mesaj sayılır ([SAP Integration Suite Pricing](https://www.sap.com/products/technology-platform/integration-suite/pricing.html)). Yani "her şeyi entegrasyon akışından geçirmek" sessizce pahalıya patlar; ne zaman gerçekten gerekli, ne zaman basit bir bağlantı yeter — bu ayrımı yapmak Basis bilgisiyle FinOps düşüncesinin tam kesişimi (bkz. ../09_FinOps_Maliyet.md).

**Ne zaman Advanced Event Mesh?** Sıradan istek-cevap entegrasyonu için Cloud Integration yeter. Olaylar gerçek-zamanlı, asenkron ve çok sistem dinliyorsa (ör. "stok değişti" olayını 5 sistem anında duysun) olay-tabanlı mimari gerekir. AEM, küçük olan SAP Event Mesh'in teknik sınırına gelindiğinde devreye giren ağır çözümdür — küçük senaryolar için fazladır.

## 4. Hangi somut beceriler gerekiyor?

- **iFlow (integration flow) tasarımı:** Cloud Integration içinde "kaynak → dönüştür → hedef" akışı kurmak. Bir mesajı al, biçim değiştir (ör. IDoc→JSON), filtrele, yönlendir.
- **Adaptörler ve protokoller:** HTTPS, OData, SOAP, SFTP, IDoc; hangi sistemin hangi adaptörle bağlandığını bilmek.
- **API Management:** Bir back-end'i kontrollü, ölçülebilir API'ye çevirmek; oran sınırlama (rate limiting), anahtar/OAuth ile koruma, kullanım izleme.
- **Güvenli bağlantı:** Cloud Connector, sertifika yönetimi, OAuth/SAML — senin güçlü tarafın.
- **İzleme ve maliyet:** Mesaj sayacını, hata kuyruğunu izlemek; mesaj-başına faturayı kontrol altında tutmak.
- **EDA temeli:** Olay nedir, "publish/subscribe" (yayınla/abone ol) nedir, ne zaman gerekir.

## 5. Hiç bilmiyorsam ilk adım

Hiç dokunmadıysan endişelenme — giriş eşiği düşük. **(1)** SAP Discovery Center'da ücretsiz/trial Integration Suite tenant'ı açıp tek bir basit iFlow kur: bir HTTPS isteği alıp sabit cevap dönen "hello" akışı. **(2)** Sonra iki sistemi gerçekten bağla: ör. bir REST API'den veri çekip e-postayla/dosyaya yaz. **(3)** API Management tarafında küçük bir API proxy yayınla ve anahtarla koru. **(4)** Mantığı zaten n8n ile biliyorsan (ekibin bir iç otomasyon örneği n8n kullandı, bkz. ../03_AI_ve_Otomasyon.md), aynı "düğüm-bağla" mantığının kurumsal hali olduğunu göreceksin — kavram aynı, kelimeler farklı. Resmî öğrenme yolu: SAP Learning'deki Integration Suite öğrenme yolları + Discovery Center'daki "mission" senaryoları.

## 6. Terimler sözlüğü (kısa)

- **iPaaS:** Integration Platform as a Service — sistemleri bağlayan bulut entegrasyon platformu kategorisi.
- **Cloud Integration (CPI):** Integration Suite içinde entegrasyon akışlarını çalıştıran ana bileşen.
- **iFlow (integration flow):** Bir mesajın kaynaktan hedefe nasıl aktığını tanımlayan görsel akış.
- **Adaptör:** İki sistem arasında protokol/biçim çeviren bağlantı parçası (HTTPS, OData, IDoc, SFTP…).
- **API Management:** API'leri yayınlama, koruma, oran sınırlama ve kullanım izleme katmanı.
- **EDA (event-driven architecture):** Sistemlerin "olay" mesajlarıyla asenkron haberleştiği mimari desen.
- **Advanced Event Mesh (AEM):** Kurumsal ölçekte olayları yöneten, dağıtık, yönetilen olay-akış servisi.
- **Mesaj-başına faturalama:** Maliyetin işlenen mesaj sayısına göre hesaplanması; 250 KB üstü her dilim ek mesaj sayılır.
