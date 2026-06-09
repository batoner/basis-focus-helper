# Puanlama ve Yönlendirme — Skor → Odak

> `/harita` bu mantığı uygular. Girdi: `Benim_Ciktilarim/Test_Sonucu.md`. Yoksa önce `/test`.

## 1. Skorları hesapla
Her iş kolu için:
- **Yetkinlik skoru** = o koldaki aktivite puanlarının **ortalaması** (0–4).
- **İlgi skoru** = kolun sonundaki ilgi cevabı (0–3).
- **Klasik Basis** ayrı raporlanır (zemin göstergesi; iş kolu olarak önerilmez ama güç kaynağıdır).

> Eksik/atlanan aktiviteyi 0 sayma; ortalamayı **cevaplanan** aktiviteler üzerinden al,
> kaç aktivitenin atlandığını not et (güven düzeyi için).

## 2. Yüksek/düşük eşikleri
- **Yetkinlik YÜKSEK** ≈ ortalama **≥ 2.5** (düzenli yapıyor/öğretebilir ağırlıklı).
- **İlgi YÜKSEK** ≈ **≥ 2** (orta-yüksek).
- Eşikler kesin sınır değil; sınır vakalarında açık uçlu cevaplar ve bağlam belirleyici.

## 3. 2×2 yorumu
```
                 İlgi YÜKSEK              İlgi DÜŞÜK
Yetkinlik   ► GÜÇLÜ KOZ:               ► SESSİZ GÜÇ:
YÜKSEK        ileri katkı üret,          mentorluk / dokümante et,
             retro odağı yap            retro odağı olmayabilir
Yetkinlik   ► BÜYÜME ALANI:            ► ŞİMDİLİK GEÇ:
DÜŞÜK         öğren-sonra-üret,          başkasına bırak,
             starter katkı              bu dönem önceliklendirme
```

## 4. Çıktı: 2–3 önerilen iş kolu
- Öncelik sırası: **Güçlü Koz > Büyüme Alanı (ilgi çok yüksekse) > Sessiz Güç.**
- Her öneri için **kısa gerekçe** (skor + neden) ve **tek takım tutarlılığı** kontrolü:
  seçilen ≤3 kol mümkünse aynı/komşu takımda anlamlı bir hikâye oluştursun
  (bkz. `../01_Sunum_Ozetleri/00_INDEX.md` takım yapısı).
- "Geniş Basis" profilini hatırlat: birden çok kolda orta-üstü skor, **AI/dönüşümde en büyük silahtır**
  (AI'ı *neye* uygulayacağını bilmek — bkz. `../00_Baglam/03_AI_ve_Otomasyon.md`).

## 5. Sonra ne olur
- Haritayı `Benim_Ciktilarim/Test_Sonucu.md`'ye ekle (veya ekrana ver).
- **`/proje`'ye yönlendir:** önerilen kollar + profil tipi (Güçlü Koz / Büyüme Alanı…) +
  açık uçlu cevaplar, `/proje`'nin **dinamik** öneri üretmesi için girdi olur
  (katalog = ihtiyaç bağlamı; bkz. `../05_Proje_Katalogu/`).

## Örnek (kısaltılmış)
> AI: yetkinlik 1.2 / ilgi 3 → **Büyüme Alanı** (öğren-sonra-üret). BTP Core: 2.8 / 2 →
> **Güçlü Koz**. Veri Yönetimi: 3.0 / 1 → **Sessiz Güç**. → Öneri: BTP Core Services (koz) +
> AI (ilgi yüksek, starter) ekseni; Servis & Otomasyon / Deneyim hikâyesine oturur.
