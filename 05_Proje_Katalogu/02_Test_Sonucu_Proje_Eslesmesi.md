# Test Sonucu → İhtiyaç Eşlemesi & Dinamik Karar Mantığı

> `/proje` bu mantığı uygular. **Kopya seçim yapmaz**; ihtiyaç alanlarını + profili + tüm
> bağlamı okuyup **kişiye özel, ölçülebilir bir öneri üretir.**

## 1. Profil tipine göre yön
`/harita`'nın çıkardığı 2×2 profili, hangi **ihtiyaç alanından** ve hangi **zorlukta**
yararlanılacağını belirler:

| Profil (iş kolu için) | Yaklaşım | İhtiyaç alanı seçimi |
|---|---|---|
| **Güçlü Koz** (yetkinlik↑ ilgi↑) | İleri katkı, retro odağı | O kolun **İleri/Orta** ihtiyaçları; iddialı ama 3 aya sığan çıktı |
| **Büyüme Alanı** (yetkinlik↓ ilgi↑) | Öğren-sonra-üret | O kolun **Başlangıç/Orta** (starter) ihtiyaçları; önce küçük PoC |
| **Sessiz Güç** (yetkinlik↑ ilgi↓) | Mentorluk / dokümante | Katkı, üretimden çok standardizasyon/şablon/eğitim olabilir |
| **Şimdilik Geç** (ikisi de↓) | Önceliklendirme | Bu dönem önerilmez; başka kola yönlendir |

> **Çapraz & Yeni Dönem temaları (AIOps · FinOps · Observability · Sovereign):** Bunlar tek bir
> iş koluna bağlı değildir; herhangi bir profile, ilgili iş kolunun yanına bir **mercek** olarak
> eklenebilir (ör. seçilen kola AIOps veya FinOps katmanı). `/proje`, profil hangi kol olursa olsun,
> uygun olduğunda bu temaları öneriye katabilir.

## 2. Dinamik karar kuralları (Claude bunları izler)
1. **Kopyalama, uyarla.** İlgili ihtiyaç kaydını al; kişinin olgunluğuna/ilgisine/açık uçlu
   cevaplarına göre kapsamı, zorluğu ve çıktıyı **yeniden boyutla**. Gerekirse iki ihtiyacı
   birleştir veya yeni bir öneri türet — ama mutlaka bir **Dayanak**'a yaslan.
2. **3 aya sığsın, ölçülebilir olsun.** Çıktı net (PoC / ilk sürüm / rapor) ve tek cümlelik
   taahhüde dönüştürülebilir olmalı.
3. **Tek takım tutarlılığı.** ≤3 kol seçildiyse öneriler tutarlı bir hikâye anlatsın
   (bkz. `../01_Sunum_Ozetleri/00_INDEX.md`).
4. **Birebir savunulabilirliği hazırla.** Her öneride: *nereden geldi (Dayanak)*, *karşı argüman*,
   *ilk adım + risk* — brief'in 3 soru tipine (`../01_Sunum_Ozetleri/Yetkinlik_Haritasi_brief.md`).
5. **Erişim gerçekçiliği.** Gerçek müşteri verisi/sistemi yoksa PoC/demo/trial kapsamı öner
   (ör. UDMS'i kendi Core hesabında, trial tuzağına düşmeden).
6. **Geniş Basis avantajını kullan.** Birden çok kolda orta-üstü skor varsa, AI'ı *bu birikime*
   uygulayan domain-uzmanı çerçevesini öne çıkar (`../00_Baglam/03_AI_ve_Otomasyon.md`).

## 3. Öneri formatı (kullanıcıya)
```
Önerilen katkı: [kişiye uyarlanmış başlık]
- İş kolu / zorluk: …
- Neden sana uygun: [skor + ilgi + açık uçlu cevaba bağla]
- 3 aylık çıktı: [somut, ölçülebilir]
- Dayanak (nereden geldi): [sunum/haber/gerçek proje]
- İlk adım & risk: …
- Taahhüt cümlesi taslağı: "3 ay içinde …"
```
Sonra **`/taahhut`'a yönlendir** (bu öneriyi tek sayfalık dökümana döker).

## 4. Örnek (kısaltılmış)
> Profil: BTP Core = Güçlü Koz, AI = Büyüme Alanı, açık uçlu "maliyet görünürlüğü"ne ilgi.
> `/proje` → "Tüketim/maliyet şeffaflığı" ihtiyacını alır, kişinin CAP deneyimine göre
> **kendi Core hesabında row-level izolasyonlu UDMS dashboard ilk sürümü** olarak boyutlar;
> Dayanak: BTP Maliyet Tool + FinOps haberleri; ileri faz olarak AI özet katmanı (Büyüme Alanı).
