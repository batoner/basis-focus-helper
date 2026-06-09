# Katalog Nasıl Okunur — İhtiyaç/Fırsat Bağlamı

> **Bu klasör bir "seçim menüsü" değildir.** SAP alanının geleceğe yönelik **ihtiyaç/fırsat
> haritası**dır. `/proje` bunu **bağlam** alır ve kullanıcının cevaplarına göre öneriyi
> **dinamik** üretir — kopya seçmez.

## Niçin böyle?
- **Kişisellik:** Her insanın profili farklı; doğru öneri ancak cevaplara göre anlık şekillenir.
- **Savunulabilirlik:** Yine de öneri havadan olmamalı. Buradaki fikirler gerçek kaynaklara
  (haber korpusu, sunum yol haritası, gerçek projeler) bağlıdır → birebir görüşmedeki
  *"bu fikir nereden geldi?"* sorusuna hazır cevap verir. Bu yüzden her kartta **Dayanak** satırı var.

## Bu bir örnek katalogdur
`01_Projeler_Alan_Bazli.md`, çeşitli iş kollarında **örnek** ihtiyaç/fırsat fikirlerinden oluşan bir
havuzdur — kesin/bitmiş bir liste değil, ilham ve dayanak kaynağı. Fikirler haber korpusu + alan
bağlamı + operasyon + sunum + fikir havuzundan damıtıldı; her biri gerçek bir **Dayanak**'a bağlı.
`/proje` bunları kopyalamaz; profile göre dinamik öneri üretirken bağlam olarak kullanır.

## Bir proje fikri kaydı nasıl okunur
```
### [Proje fikri — başlık]
- İş kolu · Zorluk: Başlangıç / Orta / İleri
- İhtiyaç: hangi gerçek boşluğu/problemi kapatır
- Değer/Etki: ekip/müşteri/pazar için neden önemli (yöneticinin oy gerekçesi)
- Dayanak: hangi haber/sunum/ürün yeteneğine bağlı (birebirde "nereden geldi" cevabı)
- 3 Aylık Çıktı (ÖRNEK): ölçülebilir, elle tutulur ne çıkar — dayatma değil, şekil
- Gerekli yetkinlik: yoksa "önce şunu öğren"
```
"3 Aylık Çıktı" bir **örnektir**; `/proje` bunu kişinin olgunluğuna/ilgisine göre uyarlar veya bu
ihtiyaçtan yola çıkıp yeni bir öneri türetir. **Değer/Etki** satırı, fikirlerin yöneticilerce
oylanabilmesi için vardır.

## Akış
1. `/harita` profili çıkarır (Güçlü Koz / Büyüme Alanı / Sessiz Güç).
2. `02_Test_Sonucu_Proje_Eslesmesi.md` profili ilgili fikir alanlarına yönlendirir.
3. `/proje` bu fikirleri + profili + açık uçlu cevapları + `../00_Baglam/` + `../02_SAP_Haberleri/`
   bağlamını okuyup **kişiye özel, ölçülebilir bir 3 aylık katkı** önerir.
4. `/taahhut` bu öneriyi tek sayfalık dökümana döker.

> Dosyalar: proje fikirleri → `01_Projeler_Alan_Bazli.md`; profil eşlemesi/karar mantığı →
> `02_Test_Sonucu_Proje_Eslesmesi.md`.
