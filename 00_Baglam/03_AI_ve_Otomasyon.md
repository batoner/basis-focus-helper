# AI ve Otomasyon — Joule, GenAI Hub, AI Core, Agentic AI, RPA

> SAP'nin AI dünyasının haritası: ne olduğu, nereye gittiği ve bir Basis mühendisinin burada nereye basacağı. Bilmiyorsan normal — herkes yeni başlıyor.

## 1. Bu nedir? (tek paragraf)

SAP, son iki yılda tüm ürünlerine bir yapay zekâ katmanı ekledi. Bu katmanın birkaç temel parçası var. **Joule** (SAP'nin kurumsal AI asistanı; sistem içinde soru sorduğun, iş yaptırdığın sohbet arayüzü) kullanıcının önündeki yüz. **AI Core** (BTP üzerinde AI modellerini çalıştıran/yöneten altyapı servisi) ve onun üstündeki **Generative AI Hub** (dış büyük dil modellerini — OpenAI, Gemini, Claude gibi — SAP'ye güvenli, tek bir kapıdan bağlayan servis) ise motor odası. Son olarak **agentic AI** (kendi başına çok adımlı iş yapan, karar verip araç çağıran AI "ajanları") ve bunları görsel akışlarla birbirine bağlayan **n8n / RPA** (tekrarlayan işleri otomatikleştiren akış araçları) var. Kısacası: önde asistan, arkada model orkestrasyonu, etrafta otonom ajanlar.

## 2. Neden önemli / nereye gidiyor?

SAP yönünü açıkça "Otonom İşletme"ye çevirdi: Sapphire 2026'da onlarca Joule asistanı ve 200+ uzman ajan tek bir Business AI Platform çatısı altında sunuldu ([SAP Unveils the Autonomous Enterprise](https://news.sap.com/2026/05/sap-sapphire-sap-unveils-autonomous-enterprise/)). Generative AI Hub artık GPT, Gemini, Claude ve Perplexity modellerini birlikte destekliyor; 35 çözümde 30+ uzman ajan çalışıyor ([SAP Business AI: Release Highlights Q1 2026](https://news.sap.com/2026/04/sap-business-ai-release-highlights-q1-2026/)). SAP, Anthropic'in Claude modellerini Joule ajanlarında "birincil akıl yürütme yeteneği" yapma planını duyurdu ve bağlantıyı **MCP** (Model Context Protocol; AI'ın kurumsal sistemlere standart şekilde bağlanmasını sağlayan açık protokol) üzerinden kuruyor ([SAP and Anthropic Plan to Bring Claude to SAP Business AI Platform](https://news.sap.com/2026/05/sap-anthropic-to-bring-claude-sap-business-ai-platform/)). Önemli bir sinyal: SAP, otomasyon platformu n8n'e stratejik yatırım yaptı ve onu Joule Studio'ya gömdü ([n8n's valuation doubles to $5.2BN](https://tech.eu/2026/05/12/n8n-s-valuation-doubles-to-5-2bn-following-sap-strategic-investment/)). Yani "hype" değil, ürün yol haritasının merkezi.

## 3. Basis için ne anlama geliyor?

Burada güzel haber şu: ajanlar çoğaldıkça birinin onları **bağlaması, yönetmesi, izlemesi ve denetlemesi** gerekiyor — bu doğrudan Basis işi. AI ajanlarını mevcut kontrol/uyumluluk çerçevesi içinde bağlamak, kaynak (AI Units) tüketimini izlemek, model seçimini ve veri temelini yönetmek artık operasyonun parçası. SAP bunun için **AI Agent Hub** adında ayrı bir yönetişim katmanı çıkardı: SAP ve SAP-dışı tüm ajanları keşfedip yönetmek, insan onay döngüleri ve denetim logu (audit trail) sağlamak için. Kurumsal AI'da SAP'nin tariflediği beş kritik eşikten ikisi — **veri temeli ve yönetişim** — doğrudan Basis sorumluluğu ([Enterprise AI Strategy: The Five Moments That Matter in 2026](https://news.sap.com/2026/04/five-make-or-break-moments-2026-ai-ambitions/)).

Asıl farklılaşma tezi de burada: **"AI mühendisi olmak" değil, AI'ı NEYE uygulayacağını bilmek.** Bir LLM'e SAP verisini verip "analiz et" demek kolay; o çıktının kritik olup olmadığını, hangi aksiyonu gerektirdiğini ancak yılların Basis bilgisi söyler. Sen modeli kuran değil, modele *ne öğreteceğini* bilen kişisin. (Detay: ekibin iç kaynağı — paylaşılan repoda yer almaz)

## 4. Hangi somut beceriler gerekiyor?

- **n8n / agentic akış mantığı:** Tetik → adım → karar → aksiyon zinciri kurabilmek. Görsel, kod gerektirmeden başlanabilir.
- **AI Core / GenAI Hub konfigürasyonu:** Model bağlama, AI Units lisans/maliyet takibi, model seçimi.
- **MCP ve A2A** (Agent-to-Agent; ajanların birbiriyle konuşması için açık protokol) kavramlarını bilmek; HANA Cloud'un MCP sunucusunu tanımak.
- **RAG** (Retrieval-Augmented Generation; modele kendi belgelerinden bağlam verme tekniği) ile runbook/SAP notu üzerinde soru-cevap.
- **Yönetişim refleksi:** Hangi işin otomatikleştirilebileceğini, hangisinin (ör. güvenlik notu otomatik uygulama) tehlikeli olduğunu ayırt etmek.

## 5. Hiç bilmiyorsam ilk adım

Panik yok — herkes burada eşit derecede yeni. Ekibin bir iç otomasyon örneği: müşteri e-postalarını okuyup otomatik kayıt açan bir akış. Binlerce kayıt el değmeden açıldı; lokal bir açık-kaynak LLM (veri dışarı çıkmaz), n8n + PostgreSQL, ServiceNow/Teams entegrasyonu, sıfır lisans maliyeti. *(Bu bir ekip örneğidir, kullanıcıya ait değildir.)* Senin ilk adımın bunu kopyalamak değil, mantığını anlamak.

Pratik başlangıç: (1) Günlük işinde tekrarlayan, sıkıcı tek bir manuel işi seç. (2) n8n'de küçük bir PoC kur — örneğin bir uyarıyı okuyup özetleyen akış. (3) Joule'u ve GenAI Hub'ı kendi sistemlerinde keşfet. (4) Daha derin örnekler ve haber kanıtı için `../02_SAP_Haberleri/01_AI_BusinessAI_Joule.md` dosyasına bak; ekip vizyonu için `../01_Sunum_Ozetleri/Servis_Otomasyon.md`.

## 6. Terimler sözlüğü (kısa)

- **Joule:** SAP'nin kurumsal AI asistanı; kullanıcının önündeki sohbet arayüzü.
- **AI Core:** BTP'de AI modellerini çalıştıran/yöneten altyapı servisi.
- **Generative AI Hub:** Dış LLM'leri SAP'ye güvenli, tek kapıdan bağlayan servis.
- **Agentic AI:** Çok adımlı işi kendi başına planlayıp yapan AI ajanı.
- **Orchestration:** Birden çok adımı/ajanı/aracı tek bir otomatik iş akışında birleştirme.
- **MCP:** AI'ı kurumsal sistemlere bağlayan açık standart protokol.
- **A2A:** Ajanların birbiriyle konuşması için açık protokol.
- **RAG:** Modele kendi belgelerinden bağlam verip daha doğru cevap aldırma tekniği.
- **n8n / RPA:** Tekrarlayan işleri otomatikleştiren görsel akış araçları.
- **AI Units:** GenAI Hub kullanımının ölçüldüğü/faturalandığı lisans birimi.
