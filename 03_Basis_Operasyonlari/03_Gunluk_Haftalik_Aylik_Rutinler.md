# Günlük / Haftalık / Aylık Rutinler

> Basis işinin "nabız tutma" tarafı. Testte "bu rutini düzenli yapıyor muyum?" diye
> değerlendirebilmen için periyot periyot listelenmiştir.

## Günlük
- Gece **batch** işleri ve **yedek** sonuçları kontrolü (başarısız job/yedek var mı?).
- Sistem sağlığı: kırmızı uyarılar (**RZ20**/Cloud ALM), iş süreçleri (**SM50**), kilitler (**SM12**).
- Yeni **ABAP dump'ları** (**ST22**) ve sistem log (**SM21**) taraması.
- Kuyruklar (**SMQ1/SMQ2**, **SM58**), update hataları (**SM13**), spool sıkışmaları.
- Açık ticket / olay (incident) gözden geçirme.

## Haftalık
- Performans bakışı (**ST03N** iş yükü trendi), en pahalı işlemler/SQL.
- Transport'lar ve değişiklikler; bekleyen kullanıcı/yetki talepleri.
- Kapasite/büyüme trendi (tablespace / HANA bellek), disk doluluk.
- **EarlyWatch Alert (EWA)** raporu okuma ve aksiyon çıkarma.

## Aylık / periyodik
- Güvenlik notu değerlendirme (**SNOTE**), yama/SP planlaması.
- **Housekeeping:** eski log/trace/dump temizliği, TemSe tutarlılığı, iş günlüğü reorg.
- Veri büyüme yönetimi (DVM), arşivleme adayları, indeks bakımı.
- DR/HA tatbikatı, yedekten geri dönüş (restore) testi.
- Lisans/kullanım ölçümü (**USMM/SLAW**; bulutta **UDMS** tüketimi).
- Cloud ALM / fair-use veri saklama gözden geçirme.

> İpucu: Bu rutinlerin çoğu **otomasyon ve AI** için en olgun adaylardır (raporlama,
> anomali tespiti, runbook). Bkz. `../00_Baglam/03_AI_ve_Otomasyon.md` ve proje kataloğu.
