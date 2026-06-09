# Örnek (Anonim) — Dolu Taahhüt Dökümanı Nasıl Görünür

> Bu, tamamlanmış gerçek bir retro dökümanının **özet/anonimleştirilmiş** halidir —
> "işte dolu hali böyle görünür" referansı. Kişisel detaylar sadeleştirildi; yapı ve ton korundu.
> Kendi taslağın için: `Taahhut_Sablonu.md` (boş iskelet), yönerge: `00_Sablon_Nasil_Doldurulur.md`.

---

**Seçilen İş Kolları:** AI · BTP Development · BTP Core Services

## Genel Bakış
SAP yatırımları buluta (S/4HANA Cloud) ve yapay zekaya kayarken Basis'in rolü de "sistemi
ayakta tutmak"tan öteye, **BTP'de uygulama geliştiren, AI araçlarını entegre eden ve bulut
maliyetlerini yöneten** proaktif bir yapıya evriliyor. Odağımı bu üç alana çekiyorum ve
yetkinliğimi gerçek operasyonel ihtiyaçlara dayanan somut çıktılarla destekleyeceğim.

## Farklılaşma Noktası
AI'ın kendisi farklılaşma değil; **AI'ı *hangi* Basis problemine uygulayacağını bilmek**
farklılaşmadır. Çıktının kritik olup olmadığını, hangi aksiyonu gerektirdiğini ancak yılların
Basis bilgisi söyler. Yani "AI mühendisi" değil, **operasyonu AI ile yeniden tasarlayan
domain-uzmanı.**

## 1) AI
- **Pazar:** SAP yapay zekayı tüm ürünlere gömüyor (Joule, Generative AI Hub); ekibin stratejik yönü.
- **Yetkinliğim:** Modern agentic AI (çoklu ajan, ajan iş akışları) pratiğim var; bunu Basis deneyimiyle birleştiriyorum.
- **Katkım:** Operasyonel bir ihtiyaçta serbest metni analiz edip doğru çözüme/şablona yönlendiren lokal bir AI asistanı.

## 2) BTP Development
- **Pazar:** Clean Core ile özel geliştirmeler ABAP'tan BTP'ye taşınıyor; BTP'de geliştirme temel yetkinlik.
- **Yetkinliğim:** CAP ve Fiori (UI5) geliştiriyorum; OAuth, service key, destination zaten günlük işim.
- **Katkım:** Gerçek bir ihtiyaca dayanan BTP uygulamasını uçtan uca, çalışan ürün olarak geliştirmek.

## 3) BTP Core Services
- **Pazar:** RISE/Private Cloud yaygınlaştıkça Cloud Connector, kimlik, HANA Cloud, tüketim raporlama Basis'in yeni ana alanı.
- **Yetkinliğim:** Cloud Connector'da çok çeşitli topolojiler kurdum; BTP hesap hiyerarşisi, yetkilendirme, service key uzmanlığım.
- **Katkım:** Çekirdek servisleri (UDMS, destination, XSUAA, HANA Cloud) yapılandırıp her müşterinin yalnız kendi verisini gördüğü izole bir mimari kurmak.

## 3 Aylık Somut Taahhüt
3 ay içinde: (1) serbest metni doğru şablona eşleyip taslağını hazırlayan lokal AI asistanının
**çalışan bir PoC'si**; ve (2) tüketimi subaccount bazında gösteren (ilk aşamada kendi Core
hesabımız üzerinde), **BTP'de koşan Fiori (UI5) tabanlı uygulamanın ilk sürümü.**

---
> Dikkat: Bu örnek "tek takımda tutarlı hikâye" (AI çatı + BTP'de inşa + çekirdek servis derinliği)
> ve "ölçülebilir, 3 aya sığan çıktı" ilkelerini gösterir. Kendi dökümanın **senin** profiline
> ve gerçek dayanaklarına oturmalı — kopyalama, esinlen.
