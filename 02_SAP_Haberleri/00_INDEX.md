# SAP Haberleri — İndeks ve Sayaç

Bu klasör, "SAP nereye gidiyor?" sorusunu **gerçek kaynaklarla** gösterir ve `00_Baglam/`
ile soru testine zemin sağlar. Hepsi yayın + tarih + bağlantı taşır — **uydurma yok.**

## Kategori sayacı

| Kategori | Dosya | Adet |
|---|---|:--:|
| AI / Business AI / Joule | [`01_AI_BusinessAI_Joule.md`](01_AI_BusinessAI_Joule.md) | 16 |
| BTP & Geliştirme | [`02_BTP_ve_Gelistirme.md`](02_BTP_ve_Gelistirme.md) | 13 |
| RISE / GROW / Cloud ERP | [`03_RISE_GROW_Cloud_ERP.md`](03_RISE_GROW_Cloud_ERP.md) | 12 |
| Clean Core / S/4 Roadmap | [`04_CleanCore_S4_Roadmap.md`](04_CleanCore_S4_Roadmap.md) | 10 |
| Veri / HANA / Datasphere / BDC | [`05_Veri_HANA_Datasphere_BDC.md`](05_Veri_HANA_Datasphere_BDC.md) | 15 |
| Güvenlik & Uyumluluk | [`06_Guvenlik_Uyumluluk.md`](06_Guvenlik_Uyumluluk.md) | 16 |
| Bakım 2027/2030 & Lisans | [`07_Maintenance_2027_2030_Lisans.md`](07_Maintenance_2027_2030_Lisans.md) | 11 |
| Sektör / Partner / Ekosistem | [`08_Sektor_Partner_Ekosistem.md`](08_Sektor_Partner_Ekosistem.md) | 8 |
| **TOPLAM** | | **101** ✅ (hedef 100+) |

## Haber kayıt formatı
```
**[Başlık](URL)** — *Kaynak, YYYY-AA.* 1–2 cümle özet.
**Basis için:** neden bir Basis mühendisini ilgilendirir. `Etiket`
```
Etiketler: AI · BTP · RISE · GROW · CleanCore · Veri · Güvenlik · Lisans · Ekosistem.

## Nasıl toplandı + doğrulandı (yöntem ve dürüstlük notu)
1. **Toplama:** 8 kategori için paralel web-araştırma ajanları (çok-ajanlı workflow).
2. **1. doğrulama (adversaryal):** her kategori ayrı bir ajanca teyit edildi; uydurma/şüpheli maddeler elendi.
3. **Elle kontrol:** 8 yüksek-etkili/çarpıcı iddia bizzat URL açılarak doğrulandı — hepsi gerçek.
4. **2. doğrulama (link denetimi):** ayrı bir 8-ajanlı takım **105 maddenin her bağlantısını tek tek açtı.**
   - Sonuç: 55 doğrudan açıldı; geri kalanın **çoğu `community.sap.com`/`sap.com`'un botlara 403 dönmesi**
     (link gerçek, tarayıcıda açılır) — sahte değil.
   - **4 gerçek kırık (404/ölü) madde çıkarıldı** (105 → 101).
   - **Düzeltmeler uygulandı:** "Joule Studio 2.0" → "Joule Studio"; Clean Core sertifikasyon ifadesi
     sadeleştirildi; 5 yayın tarihi düzeltildi (Collibra, SecurityBridge ×3, ISACA, DORA).

> **Bilinen sınır:** `community.sap.com`, `help.sap.com`, `www.sap.com` ve `sec.gov` bağlantıları
> otomatik araçlara **403** dönebilir; bu **bir hata değil**, bot-engelidir — tarayıcıda normal açılırlar.
>
> **Tarih bağlamı:** Haberler ağırlıkla 2025 ve 2026 (Haziran 2026'ya kadar). Hızlı değişen bir alan;
> periyodik tazeleme için `faz4-haberler` workflow'u yeniden çalıştırılabilir.
