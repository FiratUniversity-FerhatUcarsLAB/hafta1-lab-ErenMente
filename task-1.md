Öğrenci No:250542026
AD-SOYAD:Muhammet Eren Mente

Lütfen seçtiğiniz algoritmaya ait çözümü ve diğer isterleri aşağıya ekleyiniz:



![Hello_There](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExYW0ydWU0NGRuMW93b2ZjdG54dmhpZmw2enIwbHFkajZkazJ1emh5ZCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/Nx0rz3jtxtEre/giphy.gif)



### Merhaba,yazılım 1-b'den Eren;  
### bu dosyayı miraç hocamın dediği gibi bir LLM olan chat gpt desteğiyle yaptım içerikteki hiçbir şey şahsımın değildir. 
### Saygılar...


### BAŞLA

1. *GEREKLİ DEĞİŞKENLERİ TANIMLA*
   - **butce** ← *kullanıcının toplam harcama limiti*
   - **urun_listesi** ← *alınması gereken ürünlerin listesi*
   - **fiyat_listesi** ← *her ürünün birim fiyatlarını içeren liste*
   - **alternatif_marketler** ← *aynı ürünleri satan farklı marketlerin fiyat bilgileri*
   - **sepet** ← *satın alınan ürünlerin listesi (başlangıçta boş)*
   - **toplam_tutar** ← *0*

2. *KULLANICIDAN GİRDİ AL*
   - *"Toplam bütçenizi giriniz:"* → **butce**
   - *"Alınacak ürün sayısını giriniz:"* → **urun_sayisi**
   - *HER ürün İÇİN:*
       - **urun_adi** → *urun_listesi’ne ekle*
       - **tahmini_fiyat** → *fiyat_listesi’ne ekle*

3. *HER ÜRÜN İÇİN ALTERNATİF FİYATLARI TOPLA*
   - *HER* **urun** *İÇİN:*
       - *HER marketten fiyat al →* **alternatif_marketler**[*urun*] *listesine ekle*

4. *FİYATLARI KARŞILAŞTIR*
   - *HER* **urun** *İÇİN:*
       - **en_ucuz_fiyat** ← *alternatif_marketler[urun] içindeki minimum fiyat*
       - **en_ucuz_market** ← *o fiyatı veren market*
       - *"Ürün:"*, **urun**, *"için en uygun fiyat:"*, **en_ucuz_fiyat**, *"Market:"*, **en_ucuz_market**, *yazdır*

5. *OPTİMUM SEPETİ OLUŞTUR*
   - *HER* **urun** *İÇİN:*
       - *EĞER* **toplam_tutar** + **en_ucuz_fiyat** ≤ **butce** *İSE*
            → **sepet**’e (**urun**, **en_ucuz_market**, **en_ucuz_fiyat**) *ekle*
            → **toplam_tutar** ← **toplam_tutar** + **en_ucuz_fiyat**
       - *DEĞİLSE:*
            → *"Bütçe yetersiz, bu ürünü atla."* *yazdır*
            → *DEVAM ET*

6. *TEKRAR EDEN İŞLEMLER*
   - *EĞER kullanıcı “farklı kombinasyon dene” isterse:*
        → **alternatif_marketler**’den *farklı fiyat kombinasyonları oluştur*
        → *HER kombinasyonun* **toplam_tutar**’ını *hesapla*
        → *minimum* **toplam_tutar**’a *sahip kombinasyonu seç*

7. *KOŞULLU DURUMLAR*
   - *EĞER* **toplam_tutar** > **butce** *İSE*
        → *"Bütçen aşıldı, bazı ürünleri çıkar."* *mesajı ver*
        → *en az öncelikli ürünleri listeden çıkar*
        → **toplam_tutar**’ı *tekrar hesapla*
   - *DEĞİLSE:*
        → *"Alışveriş planı uygun!"* *yazdır*

8. *SONUÇLARI GÖSTER*
   - *"Satın alınacak ürünler ve seçilen marketler:"*
   - *HER öğe için* **sepet** *içeriğini yazdır*
   - *"Toplam tutar:"*, **toplam_tutar**, *"Kalan bütçe:"*, **butce** - **toplam_tutar**

BİTİR

![surprise](https://ngdblog.africa/wp-content/uploads/2023/01/Wow-gif.gif)
