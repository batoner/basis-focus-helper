# Test Mantığı — Claude Soruları Nasıl Sorar ve Puanlar

> Bu dosya `/test` ve `/start` komutlarının izlediği **akış kılavuzudur** (form DEĞİL).
> Soruların kendisi `01_Soru_Bankasi.md`'de; puanlama `02_Puanlama_ve_Yonlendirme.md`'de.

## Temel ilke
Bu bir **sınav değil, envanterdir.** Doğru/yanlış yok; amaç kişinin güç–boşluk–ilgi
haritasını çıkarmak. Ton: sade, yargısız, "bilmiyorsan normal".

## Ölçekler
- **Olgunluk (her aktivite):** 0 Hiç duymadım · 1 Duydum, yapmadım · 2 Bir-iki kez yaptım ·
  3 Düzenli yapıyorum · 4 Başkalarına öğretebilirim / tasarlayabilirim.
- **İlgi (her iş kolu sonunda):** 0 Hiç · 1 Az · 2 Orta · 3 Yüksek.

## Akış (Claude bunu yürütür)
1. **Karşılama:** ne yaptığını 2 cümleyle açıkla; "envanter, sınav değil; istediğin an
   'geç' diyebilirsin" de.
2. **Alan alan ilerle:** `01_Soru_Bankasi.md`'deki sırayla. Önce **Klasik Basis** (ısınma,
   çoğu kişi burada güçlü → güven verir), sonra 10 iş kolu.
3. **Her aktiviteyi tek tek sor**, 0–4 cevabı al. Kullanıcı bir terimi bilmiyorsa **tek
   cümleyle açıkla** ve "bu durumda muhtemelen 0 veya 1" diye yönlendir.
4. **Kullanıcıyı boğma:** bir iş kolu bitince **mini özet** ver ("bu alanda ortalaman ~X")
   ve devam onayı al. Uzun listelerde 4–6 aktiviteyle sınırlı kal.
5. **İş kolu sonunda ilgi sorusu** (0–3): "Bu alanda gelişmek ister misin?"
6. **Sonda açık uçlu 3 soru** (bkz. soru bankası).
7. **Sonucu yaz:** `Benim_Ciktilarim/Test_Sonucu.md`'ye aşağıdaki formatta kaydet.
8. **Yönlendir:** "/harita ile haritanı çıkaralım" de.

## Sonuç dosyası formatı (`Benim_Ciktilarim/Test_Sonucu.md`)
```
# Test Sonucu — [tarih]
## Skorlar (iş kolu: yetkinlik ortalaması / ilgi)
- Klasik Basis: 3.2 / -
- AI: 1.0 / 3
- BTP Development: 1.5 / 2
... (tüm alanlar)
## Açık uçlu cevaplar
- En gurur duyduğun iş: ...
- En çok merak ettiğin ürün: ...
- En büyük engelin: ...
## Ham cevaplar (aktivite: puan)
...
```

> Kısa yol: kullanıcı acelesindeyse, her iş kolundan yalnız **2 çekirdek aktivite** + ilgi
> sorusuyla "hızlı tarama" yapılabilir. Tam envanter daha doğru sonuç verir.
