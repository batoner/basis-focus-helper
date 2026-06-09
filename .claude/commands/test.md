---
description: İnteraktif öz-değerlendirme — Basis yetkinlik/ilgi envanterini çıkar.
---

Karşındaki SAP Basis mühendisine interaktif bir **öz-değerlendirme** uygula. Bu bir sınav değil,
bir envanterdir; ton sade, yargısız, Türkçe, "bilmiyorsan normal".

## Yap
1. `04_Soru_Testi/00_Test_Mantigi.md` (akış/ölçek kuralları) ve `04_Soru_Testi/01_Soru_Bankasi.md`
   (sorular) dosyalarını **oku**.
2. Soruları **sohbet içinde tek tek** sor:
   - Önce **Klasik Basis** (ısınma), sonra 10 iş kolu.
   - **Tek seferde TEK aktivite** — birden çok aktiviteyi aynı mesajda toplayıp "virgülle puan yaz"
     deme. Her soruda ölçeği tek satırda hatırlat:
     `(0 hiç duymadım · 1 duydum, yapmadım · 2 bir-iki kez · 3 düzenli · 4 öğretebilirim)`
   - Kullanıcı **rakamla da kelimeyle de** cevap verebilir ("hiç duymadım", "ara sıra yaparım"…);
     kelimeyse 0–4'e çevir ve tek cümleyle teyit et ("→ 2 yazıyorum").
   - Bilinmeyen terimi **tek cümleyle açıkla**, sonra puanını al.
   - Her iş kolu sonunda **ilgi 0–3** sor; sonda **3 açık uçlu** soru.
   - Her iş kolu bitince **mini özet** ver ve devam onayı al. Kullanıcıyı boğma.
3. Bitince sonucu `00_Test_Mantigi.md`'deki formatta **`Benim_Ciktilarim/Test_Sonucu.md`** dosyasına yaz
   (skorlar + açık uçlu cevaplar + ham cevaplar).
4. Kullanıcıya **`/harita`** ile devam etmesini öner.

> Acelesi varsa: her iş kolundan 2 çekirdek aktivite + ilgi sorusuyla "hızlı tarama" yap; ama tam
> envanterin daha doğru sonuç verdiğini söyle.
