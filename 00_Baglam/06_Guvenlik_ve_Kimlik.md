# Güvenlik ve Kimlik — IAS/IPS, ETD, SoD, MSSP/SOC

> SAP güvenliği artık tek tek görevler değil; kimlik, tehdit izleme ve uyumluluğu birleştiren bir hizmet portföyü. Bu sayfa o haritayı çıkarır.

## 1. Bu nedir? (tek paragraf)

Bu alan, "SAP sistemine kim, nasıl giriyor ve sistemde kötü niyetli bir şey olduğunda bunu nasıl görüyoruz?" sorularının tamamını kapsar. İçinde dört ana parça var: kimlik (kullanıcıların güvenli ve tek noktadan giriş yapması), yetki (kimin neye erişebileceği ve riskli yetki birikimini engelleme), tehdit algılama (saldırıyı gerçek zamanlı yakalama) ve uyumluluk (denetim/regülasyon kayıtlarını tutma). Eskiden bunlar dağınık görevlerdi; bugün **paketlenmiş, hizmet olarak sunulan** bir portföye dönüşüyor (bkz. `../01_Sunum_Ozetleri/Guvenlik.md`).

## 2. Neden önemli / nereye gidiyor?

2025, SAP için "sıfır-gün yılı" oldu: açıklar, yayımlandıktan saatler içinde saldırıya çevrildi ([The Year of the Zero-Day](https://onapsis.com/blog/sap-vulnerabilities-2025/)). NetWeaver'da CVSS 10.0'lık bir açık aktif olarak istismar edildi ([CVE-2025-31324](https://onapsis.com/blog/active-exploitation-of-sap-vulnerability-cve-2025-31324/)) ve kritik güvenlik notu sayısı belirgin arttı ([SAP Security Notes 2025](https://drj.com/industry_news/sap-security-notes-2025-a-year-of-intensifying-critical-risks/)). Bunun anlamı: aylık yama döngüsü artık yetmiyor, **acil müdahale** ve **7/24 izleme** gerekiyor. Yön ise net — kimlik buluta taşınıyor (eski temel kimlik doğrulama ve SCIM v1 kullanımdan kaldırılıyor, bkz. `../02_SAP_Haberleri/06_Guvenlik_Uyumluluk.md` madde 9-10), izleme SIEM'e bağlanıyor (SAP ETD + Microsoft Sentinel) ve uyumluluk yasal zorunluluk haline geliyor (DORA için bkz. aynı dosya madde 13).

## 3. Basis için ne anlama geliyor?

Basis rolü "sunucuyu ayakta tutan kişi"den **platform/güvenlik mühendisine** kayıyor. RISE'de (SAP'nin yönettiği bulut aboneliği) sorumluluk paylaşılıyor: altyapı güvenliği SAP'de, ama **kimlik, erişim, özel kod ve konfigürasyon güvenliği müşteride** kalıyor ([RISE Shared Responsibility](https://securitybridge.com/blog/rise-with-sap-security/)). Yani Basis mühendisi artık IAS bağlamak, SoD risklerini görmek, ETD alarmlarını yorumlamak ve denetim kaydını saklamak zorunda. Bu, retro için güçlü bir odak: ekibimizin MSSP/SOC vizyonu (7/24 yönetilen güvenlik hizmeti) tam buraya oturuyor (bkz. `../01_Sunum_Ozetleri/Guvenlik.md`).

## 4. Hangi somut beceriler gerekiyor?

- **Kimlik & SSO:** IAS/IPS'i bir uygulamaya bağlamak; SAML 2.0 / OIDC ile tek oturum açma (SSO) kurmak; Microsoft Entra ID gibi kurumsal kimlik sağlayıcılarla SCIM 2.0 üzerinden kullanıcı senkronizasyonu yapmak.
- **Yetki & SoD:** PFCG/SU01 ile rol yönetimi; SoD matrisini okuyup çakışma riskini analiz etmek (S/4HANA geçişinde matris yeniden tasarlanıyor — bkz. `../02_SAP_Haberleri/06_Guvenlik_Uyumluluk.md` madde 14).
- **Tehdit algılama:** ETD veya Sentinel for SAP'ta alarm kuralı okumak/optimize etmek; şüpheli RFC/oturum davranışını tanımak.
- **Operasyon & uyumluluk:** Güvenlik notu önceliklendirme (HotNews), audit log (denetim kaydı) yönetimi, güvenlik parametre takibi, güvenlik sağlık taraması yapmak.

## 5. Hiç bilmiyorsam ilk adım

Bilmiyorsan normal — buradan başla. (1) Bir test/eğitim sisteminde **IAS deneme kiracısı** açıp tek bir uygulamaya SAML SSO bağlamayı dene; tüm akışı bu küçük denemede görürsün. (2) Sistemindeki **güvenlik notlarını** (System Recommendations / EarlyWatch raporları) bir kez baştan sona oku, HotNews'leri ayıkla. (3) Bir **SoD matrisi** örneği bul ve "bu iki yetki neden birlikte tehlikeli?" sorusunu yanıtlamaya çalış. (4) ETD/Sentinel için önce **kavramı** anla: log topla → korele et → alarm üret. Üçü de yarım günlük okumayla başlanabilir; ürün sertifikasına gerek yok.

## 6. Terimler sözlüğü (kısa)

- **IAS (Identity Authentication Service):** Kullanıcıların SAP bulut uygulamalarına güvenli ve merkezi giriş yapmasını sağlayan kimlik doğrulama servisi.
- **IPS (Identity Provisioning Service):** Kullanıcı/grup hesaplarını sistemler arasında otomatik oluşturan/senkronlayan servis.
- **SSO (Single Sign-On):** Bir kez giriş yapıp birden çok uygulamaya tekrar şifre girmeden erişme.
- **SAML 2.0 / OIDC:** SSO için kullanılan iki standart kimlik protokolü.
- **SCIM 2.0:** Kullanıcı/grup bilgisini sistemler arası taşıyan standart provizyon (hesap aktarım) API'si.
- **SoD (Segregation of Duties / Görevler Ayrılığı):** Bir kişide riskli yetki birikimini (ör. hem ödeme oluşturup hem onaylamak) engelleme ilkesi.
- **ETD (Enterprise Threat Detection):** SAP loglarını gerçek zamanlı izleyip saldırı/tehdit tespit eden SAP aracı; bulut sürümü Microsoft Sentinel ile entegre çalışabiliyor.
- **SIEM:** Tüm sistemlerin güvenlik loglarını toplayıp korele eden güvenlik izleme platformu (ör. Sentinel).
- **MSSP / SOC:** Dışarıdan sağlanan 7/24 yönetilen güvenlik hizmeti / güvenlik operasyon merkezi.
- **Audit Log (Denetim Kaydı):** Sistemde kimin ne yaptığını kanıt olarak saklayan kayıt; denetim ve regülasyon için zorunlu.
- **RISE paylaşılan sorumluluk:** RISE'de güvenliğin bir kısmı SAP'de, bir kısmı müşteride; sınırı bilmek kritik.
