# Cloud Dönüşümü — RISE / ECS / GROW / Private vs Public Cloud

> SAP'nin iş modeli buluta kayıyor; bu, Basis işinin de nereye doğru değiştiğini anlatan harita.

## 1. Bu nedir? (tek paragraf)

SAP, müşterileri kendi sunucularında çalışan klasik ERP'den (eski adıyla ECC — kurumun içindeki SAP sistemi) bulut tabanlı ERP'ye taşıyor. Bunu iki ana paketle yapıyor: **RISE with SAP** (kuruma özel, izole bir kurulum — "Private Cloud") ve **GROW with SAP** (standart, hazır gelen, paylaşımlı kurulum — "Public Cloud"). Her iki pakette de altyapı artık AWS/Azure/GCP gibi **hyperscaler**'larda (devasa bulut altyapı sağlayıcıları) duruyor, fiziksel sunucu odasında değil. RISE tarafında sistemi teknik olarak işleten birim **SAP ECS** (Enterprise Cloud Services — SAP'nin altyapıyı SLA ile yöneten ekibi). Bilmiyorsan normal; çoğu Basis mühendisi bunu yeni öğreniyor.

## 2. Neden önemli / nereye gidiyor?

Bu sadece moda değil, SAP'nin para kazanma biçimi. ECC için ana destek **2027'de** bitiyor (bazı senaryolarda 2030/2033'e uzatma var), yani göç bir tercih değil takvim. SAP'nin Q1 2026 sonuçlarında bulut ERP geliri çift haneli büyüdü (bkz. [../02_SAP_Haberleri/03_RISE_GROW_Cloud_ERP.md](../02_SAP_Haberleri/03_RISE_GROW_Cloud_ERP.md), madde 5) ve benchmark raporlarına göre tam buluta geçiş 2027 öncesi hızlanıyor (a.g.e., madde 8). Önemli bir ayrıntı: SAP 2025 baharında ürün adlarını sadeleştirdi — *S/4HANA Cloud Private Edition* artık pazarlama dilinde **"SAP Cloud ERP Private"**, *Public Edition* ise **"SAP Cloud ERP"** olarak geçiyor, ikisi de **SAP Business Suite** şemsiyesi altında. Sözleşme/teknik isimler aynı kaldı; sadece konuşma dili değişti — bir mülakatta yeni isimleri bilmek fark yaratır.

## 3. Basis için ne anlama geliyor?

En büyük değişiklik **sorumluluk sınırı**. Klasik dünyada işletim sistemi, veritabanı, yedek, yama hepsi Basis'indi. RISE/ECS'te bunların çoğu SAP ECS'e geçiyor — buna **paylaşılan sorumluluk modeli** denir (kimin neyden sorumlu olduğunu belirleyen çerçeve). ECS altyapıyı, OS'u, DB'yi tutar; sen uygulama katmanını, kullanıcı/yetki yönetimini, **görev ayrılığı** (SoD — tek kişide çakışan kritik yetki olmaması) uyumunu ve sistem üstü işleri tutarsın. SAP, 1000'den fazla görevi tek tek "kim yapar" diye listeleyen bir R&R (Roles & Responsibilities — roller ve sorumluluklar) matrisi yayınlıyor; Basis'in yeni başucu belgesi bu. Yani Basis kaybolmuyor: sunucuya doğrudan müdahale eden rolden, **ECS'i yöneten / koordine eden** role dönüşüyor — SAP for Me üzerinden Service Request açmak, refresh/provizyon talep etmek, izlemeyi kurmak. Detaylı aktivite envanteri için bkz. [../03_Basis_Operasyonlari/02_Cloud_Operasyonlar.md](../03_Basis_Operasyonlari/02_Cloud_Operasyonlar.md).

## 4. Hangi somut beceriler gerekiyor?

- **R&R matrisini okumak:** ECS neyi yapar, neyi yapmaz — bir göç projesinde en sık sorulan soru.
- **SAP for Me / Service Request akışı:** ECS ile günlük iletişimin tek kanalı.
- **Cloud ALM ile izleme:** SolMan'in bulut halefi; health/integration monitoring kurulumu.
- **Göç metodolojisi:** özellikle **DMO with System Move** (veritabanını dönüştürüp aynı anda buluta taşıma).
- **Hyperscaler temeli:** Azure/AWS'de ağ, bölge, performans izleme mantığını anlamak (bkz. haberler, madde 1 — RISE on Azure).
- **GROW tarafı:** Public Cloud'da Basis eforu çok daha az; orada beceri "hızlı kurulum + entegrasyon + kimlik yönetimi" eksenine kayar.

## 5. Hiç bilmiyorsam ilk adım

Panik yok, herkes bir yerden başladı. Önerilen sıra: (1) Bu dosyayı ve iki kaynak operasyon dosyasını oku, kavramları oturt. (2) SAP for Me portalını gez — ücretsiz, sistem yönetiminin yeni yüzü. (3) RISE referans mimarisini bir kez baştan sona çiz: müşteri ↔ ECS ↔ hyperscaler — kim neyden sorumlu? (4) Cloud ALM'in ne yaptığını bir tanıtım videosuyla öğren. (5) İlgini RISE/ECS operasyonu çekiyorsa, retroda "Cloud ALM kurulum/izleme" veya "RISE onboarding şablonlama" gibi küçük, somut bir taahhüt seç (bkz. [../01_Sunum_Ozetleri/Deneyim_RISE_MSP.md](../01_Sunum_Ozetleri/Deneyim_RISE_MSP.md)).

## 6. Terimler sözlüğü (kısa)

- **RISE with SAP / SAP Cloud ERP Private:** Kuruma özel Private Cloud ERP paketi; ECS tarafından işletilir.
- **GROW with SAP / SAP Cloud ERP:** Standart, hazır Public Cloud (SaaS) ERP; orta ölçek için hızlı go-live.
- **ECS (Enterprise Cloud Services):** SAP'nin RISE altyapısını SLA ile işleten birimi.
- **Hyperscaler:** AWS/Azure/GCP — fiziksel bulut altyapısını sağlayan dev sağlayıcılar.
- **Paylaşılan sorumluluk:** Hangi işin SAP'de, hangisinin müşteride olduğunu belirleyen R&R çerçevesi.
- **Private vs Public Cloud:** Private = sana özel izole sistem (RISE); Public = paylaşımlı, standart sistem (GROW).
- **DMO with System Move:** Veritabanı dönüşümü + buluta taşımayı tek adımda yapan göç yöntemi.
