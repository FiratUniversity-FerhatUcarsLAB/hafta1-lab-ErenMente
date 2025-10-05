Öğrenci No:250542026
AD-SOYAD:Muhammet Eren Mente

Lütfen seçtiğiniz algoritmaya ait çözümü ve diğer isterleri aşağıya ekleyiniz:






![Hello_There](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExYW0ydWU0NGRuMW93b2ZjdG54dmhpZmw2enIwbHFkajZkazJ1emh5ZCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/Nx0rz3jtxtEre/giphy.gif)


### Merhaba,yazılım 1-b'den Eren;  
### bu dosyayı ödevde söylendiği gibi bir LLM olan chat gpt desteğiyle yaptım içerikteki hiçbir şey şahsıma ait değildir. 
### Saygılar...


### Market envanterini kategorilere ayırma — PSEUDOCODE

### BAŞLA

1. *GEREKLİ DEĞİŞKENLERİ TANIMLA*
   - **uye_listesi**        ← *gruptaki üyelerin kimlik/isim listesi*
   - **secenek_listesi**    ← *karar için önerilen seçeneklerin listesi*
   - **oneriler**           ← *üyeler tarafından eklenen yeni öneriler (opsiyonel)*
   - **oy_listesi**         ← *her üyenin verdiği oy / tercih bilgileri (map)*
   - **karar_metodu**       ← *oylama yöntemi (örn. çoğunluk, konsensüs, borda, condorcet, ağırlıklı)*
   - **sure**               ← *oylama için son tarih / süre (tarih veya dakika cinsinden)*
   - **katilim_onaylari**   ← *karara katılmayı kabul eden üye sayısı*
   - **sonuc**              ← *hesaplanan nihai karar*
   - **esik_degeri**        ← *karar için gereken minimum destek oranı (örn. %50 veya %66)*
   - **tartisma_limiti**    ← *müzakere / tekrar turu sınırı (maks tur sayısı)*
   - **agirliklar**         ← *isteğe bağlı; üyelerin oy ağırlıkları (örn. liderin ağırlığı)*
   - **geribildirim**       ← *karar sonrası geri bildirim / memnuniyet puanları*

2. *KATILIM VE HAZIRLIK*
   - *Organizatör* karar tablosunu ve **sure**'yi belirler
   - *Tüm üyelere çağrı gönder* → katılım istenir
   - HER **uye** için:
       - *Eğer* üye katılmayı onaylarsa → **katilim_onaylari** ++
       - *Değilse* → kayıt pasif kalır
   - *Eğer* **katilim_onaylari** < MIN_KATILIM_THRESHOLD *ise*:
       → YAZDIR *"Yeterli katılım yok; tarih/çağrı tekrarlansın"* → BİTİR veya bekle

3. *ÖNERİLERİ TOPLA VE DOĞRULA*
   - *Varsa* üyeler **oneriler** ekler
   - **secenek_listesi** ← varsayılan + **oneriler**
   - HER **secenek** için:
       - *Format kontrolü yap (açık, uygulanabilir mi?)*  
       - *Eğer uygunsuz ise* → **secenek_listesi**'nden çıkar ve ilgili üyeye bildirim gönder

4. *OYLA / TERCİH TOPLA*
   - *Seçilen* **karar_metodu**'na göre işlem:
     - *EĞER* **karar_metodu** == "cogunluk" (majority) *ise*:
         → HER **uye** bir tercih/seçim yapar; **oy_listesi** güncellenir
     - *EĞER* **karar_metodu** == "borda" *ise*:
         → HER **uye** seçenekleri tercih sırasına göre puanlar; borda puanları toplanır
     - *EĞER* **karar_metodu** == "condorcet" *ise*:
         → HER **iki_secenek** çifti için ikili tercihler toplanır; condorcet kazananı belirlenir
     - *EĞER* **karar_metodu** == "agirlikli" *ise*:
         → HER **uye** oy verir; oy değeri **agirliklar** ile çarpılarak toplanır
     - *EĞER* **karar_metodu** == "konsensüs" *ise*:
         → Tüm üyeler tartışma turunda görüşlerini yazar; ortak kabul aranır (oy değil müzakere)
   - *Oy toplama* süresi **sure** ile sınırlıdır; süre dolunca otomatik kapanır

5. *OY SAYIMI VE İLK SONUÇ*
   - *Oylama kapandığında:* hesapla toplam destek / puan
   - *Eğer* **karar_metodu** != "konsensüs" ise:
       - **sonuc** ← METOD_HESAPLA(**oy_listesi**, **agirliklar**, **karar_metodu**)
       - destek_orani ← DESTEK_ORANI_HESAPLA(**sonuc**)
       - *Eğer* destek_orani ≥ **esik_degeri** *ise*:
            → YAZDIR *"İlk tur sonucu kabul edildi:"*, **sonuc**
            → GİT 7. (uygulama)
         *Değilse*:
            → YAZDIR *"İlk tur sonucu eşik altı; ikinci tur/uzlaşma başlatılıyor"*
            → GİT 6. (uzlaşma)

   - *Eğer* **karar_metodu** == "konsensüs" ise:
       - *Eğer* tüm üyeler kabul ettiyse → **sonuc** kabul edilir
       - *Değilse* → GİT 6. (uzlaşma)

6. *UZLAŞMA / İTİRAZ TURU*
   - TUR ← 1
   - WHILE TUR ≤ **tartisma_limiti** DO
       - *İtiraz edenler, gerekçe ve alternatif öneri sunar*
       - *Kısa tartışma (chat veya anket) yapılır; yeni öneri veya revizyon kaydedilir*
       - *Tekrar oy toplama (adım 4) yapılır*
       - *Sonuç hesapla (adım 5)*
       - *Eğer* destek_orani ≥ **esik_degeri** → BREAK
       - TUR ← TUR + 1
   - END WHILE
   - *Eğer* TUR > **tartisma_limiti** ve destek yine düşük ise:
       - *Fallback mekanizması çalıştır (örn. lider kararı, rastgele seçme, ya da external arbiter)*

7. *BAŞARILI KARARIN UYGULANMASI*
   - *Eğer* **sonuc** kabul edildiyse:
       - YAZDIR *"Nihai karar:"*, **sonuc**
       - *İlgili sorumlulara görev/hatırlatma gönder*  
       - *Uygulama takvimi oluştur ve paylaş*  
       - *Uygulama sonrası geribildirim toplamak üzere anket başlat*

8. *GERİBİLDİRİM & KAYITLAMA*
   - *Uygulama tamamlandığında veya karar yürürlüğe girdiğinde:*
       - HER **uye** den memnuniyet puanı al → **geribildirim**
       - Karar, oy kayıtları, itirazlar ve sonuç **kayıt_defteri**ne kaydedilir (şeffaflık için)
       - *Eğer belirli üyeler tekrar itiraz ediyorsa, not al ve gelecekte ağırlık/kurallar için analiz et*

9. *İSTİSNALAR & ÖZEL DURUMLAR*
   - *Eğer* acil durum (zaman kısıtı, kritik karar) *ise*:
       - *Hızlandırılmış mod* (kısa süre, çoğunlukla lider onayı) uygulanır
   - *Eğer* bazı üyeler çevrimdışı ise:
       - *Temsilci atama* veya *erteleme* seçenekleri sunulur
   - *Eğer* kötü niyetli davranış (spam/çifte oy) tespit edilirse:
       - oylama iptal edilir; moderatör müdahale eder

10. *SONUÇLARI BİLDİR*
    - YAZDIR *"Karar süreci tamamlandı. Nihai sonuç:"*, **sonuc**
    - Paylaşılan kayıtların bağlantısını gönder (örn. paylaşılan doküman / git repo linki)
    - *Süreçten elde edilen öğrenimler ve öneriler* özetlenir

### BİTİR


---
**Kaynakça:**  
- ChatGPT (LLM) desteğiyle oluşturulmuştur, 2025.  
---
---


![surprise](https://ngdblog.africa/wp-content/uploads/2023/01/Wow-gif.gif)
