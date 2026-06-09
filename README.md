# Basis Focus Helper

> **Durum:** Hazır. Bağlam, SAP haberleri, operasyon matrisi, soru bankası, **örnek proje fikri
> kataloğu** ve taahhüt şablonu yerinde; komutlar çalışır durumda.

SAP Basis ekibindeki arkadaşların retro **"Yetkinlik Haritası"** taahhüdünü
hazırlayabilmesi için kurulmuş, **Claude Code ile interaktif çalışan** bir yardımcı bilgi
deposu.

> *Claude Code: terminalde/IDE'de çalışan, repodaki dosyaları okuyup seninle sohbet ederek
> iş yapan Anthropic yapay zekâ aracı.*

---

## Ne işe yarar?

Birçok arkadaş retro için "ne yapabilirim?" sorusuna takılıyor. Sebep yetenek eksikliği
değil — **görünürlük eksikliği**: bugüne kadar kullanmadıkları ürünlerden (BTP, RISE/ECS,
AI araçları, Integration Suite, CALM, BDC…) habersiz olunca insan *neye ihtiyaç olduğunu
ve neye yatkın olduğunu* bilemeyebiliyor.

Bu depo seni şu yoldan geçirir:

```
Bağlamı oku → Kendini test et → Güç/zayıf/ilgi haritanı gör
   → Sana uygun projeleri keşfet → Kendi taahhüt dökümanını üret
```

Çıkış: retroya koyabileceğin **gerekçeli, ölçülebilir, sana ait** bir 3 aylık taahhüt
cümlesi + tek sayfalık döküman taslağı.

---

## Nasıl çalışır? (özet)

1. Repoyu GitHub'dan klonla.
2. Klasörde **Claude Code**'u aç.
3. **`/start`** yaz.
4. Gerisi sohbet: Claude Code testi yürütür, haritanı çıkarır, proje önerir, taahhüdünü
   birlikte yazarsınız.

> Adım adım kurulum (Claude Code'u hiç kullanmadıysan da): **[`KURULUM_VE_KULLANIM.md`](KURULUM_VE_KULLANIM.md)**

### Komutlar

| Komut | Ne yapar |
|---|---|
| `/start` | Baştan sona tam yolculuk (önerilen giriş) |
| `/test` | Sadece interaktif öz-değerlendirme |
| `/harita` | Test sonucundan güç/zayıf/ilgi haritası + odak önerisi |
| `/proje` | Profiline uygun proje fikirleri |
| `/taahhut` | Tek sayfalık taahhüt taslağını birlikte doldur |

---

## Klasör haritası

| Klasör | İçerik |
|---|---|
| `00_Baglam/` | Basis nereye evriliyor — alan alan kısa rehberler |
| `01_Sunum_Ozetleri/` | Retro sunumlarının damıtılmış özeti + retro brief'i |
| `02_SAP_Haberleri/` | SAP ve geleceği üzerine 100+ haber, kategorili |
| `03_Basis_Operasyonlari/` | "Basisçi ne yapar" — kapsamlı aktivite envanteri |
| `04_Soru_Testi/` | İnteraktif testin soru bankası + puanlama mantığı |
| `05_Proje_Katalogu/` | Zorluk seviyeli proje fikirleri + profil eşlemesi |
| `06_Taahhut_Sablonu/` | Taahhüt dökümanı şablonu + anonim örnek |
| `.claude/commands/` | Testi yürüten slash komutları |
| `Benim_Ciktilarim/` | **Senin** çıktıların (GitHub'a gönderilmez) |

---

## Önerilen okuma sırası (Claude Code'suz, elle de okunabilir)

`01` retro brief → `00` bağlam → `02` haberlere göz at → `03` operasyonlar →
`04` testi yap → `05` proje seç → `06` şablonu doldur.

> En kolayı: sadece `/start` yaz, bu sırayı Claude Code senin için yürütür.

---

## Ton ve dürüstlük

Sade, jargonsuz, abartısız. Bir terim ilk geçtiğinde tek cümleyle açıklanır. "Bilmiyorsan
normal — işte başlangıç" yaklaşımı. Hiçbir haber uydurma değil; her madde gerçek bir
kaynağa (yayın + tarih, mümkünse bağlantı) dayanır.

## Gizlilik

Test cevapların ve taahhüt taslağın yalnızca senin makinendeki `Benim_Ciktilarim/`
klasöründe kalır; `.gitignore` sayesinde GitHub'a geri gönderilmez.
