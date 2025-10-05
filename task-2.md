Öğrenci No:250542026
AD-SOYAD:Muhammet Eren Mente

Lütfen seçtiğiniz algoritmaya ait çözümü ve diğer isterleri aşağıya ekleyiniz:







![Hello_There](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExYW0ydWU0NGRuMW93b2ZjdG54dmhpZmw2enIwbHFkajZkazJ1emh5ZCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/Nx0rz3jtxtEre/giphy.gif)


### Merhaba,yazılım 1-b'den Eren;  
### bu dosyayı ödevde söylendiği gibi bir LLM olan chat gpt desteğiyle yaptım içerikteki hiçbir şey şahsıma ait değildir. 
### Saygılar...


### SAYI TAHMİN OYUNUNDA OPTİMAL STRATEJİ — PSEUDOCODE

## BAŞLA

1. *GEREKLİ DEĞİŞKENLERİ TANIMLA*  
   - **alt_sinir** ← *tahmin aralığının alt limiti (örneğin 1)*  
   - **ust_sinir** ← *tahmin aralığının üst limiti (örneğin 100)*  
   - **tahmin** ← *yapılan sayı tahmini (geçici)*  
   - **deneme_sayisi** ← *başlangıçta 0*  
   - **hedef_sayi** ← *bilinmeyen hedef (sistem tarafından belirlenir)*  
   - **geri_bildirim** ← *kullanıcıdan alınan yönlendirme (“daha_buyuk”, “daha_kucuk”, “dogru”)*  
   - **max_deneme_hakki** ← *isteğe bağlı maksimum deneme limiti*  
   - **olasilik_dagilimi** ← *önsel (prior) olasılıklar; eğer bilinmiyorsa uniform dağılım kabul edilir*  
   - **yanlis_sayisi** ← *opsiyonel hata toleransı (yalan veya belirsizlik sayısı)*  

---

2. *KULLANICIDAN GİRDİ AL*  
   - "Alt sınırı giriniz:" → **alt_sinir**  
   - "Üst sınırı giriniz:" → **ust_sinir**  
   - Eğer maksimum deneme hakkı tanımlanacaksa → **max_deneme_hakki**  
   - Eğer özel olasılık dağılımı tanımlanacaksa → **olasilik_dagilimi**  

---

3. *BAŞLANGIÇ AYARLARINI YAP*  
   - **deneme_sayisi** ← 0  
   - **aktif_alt** ← **alt_sinir**  
   - **aktif_ust** ← **ust_sinir**  
   - Eğer **olasilik_dagilimi** boşsa → *uniform dağılım oluştur*  
   - Eğer **yanlis_sayisi** tanımlıysa → **kalan_yalan** ← **yanlis_sayisi**  

---

4. *STRATEJİ SEÇİMİ (KOŞULLU DURUMLAR)*  
   - Eğer **yanlis_sayisi** == 0 VE **olasilik_dagilimi** uniform ise  
       → *"binary search stratejisi" uygula*  
   - Eğer **yanlis_sayisi** == 0 VE **olasilik_dagilimi** non-uniform ise  
       → *"medyan / entropi tabanlı strateji" uygula*  
   - Eğer **yanlis_sayisi** > 0 ise  
       → *"Ulam hata toleranslı stratejisi" uygula*  
   - Aksi durumda  
       → *"adaptif strateji" (bilgi kazancı maksimize eden) uygula*  

---

5. *ANA TAHMİN DÖNGÜSÜ*  

   WHILE **dogru_tahmin_bulunamadi** DO  
   - Eğer **deneme_sayisi** ≥ **max_deneme_hakki**  
       → *“Deneme hakkı bitti, oyun sonlandı”*  
       → BREAK  

   - Eğer strateji “binary” ise  
       → **tahmin** ← (**aktif_alt** + **aktif_ust**) / 2  
   - Eğer strateji “entropi tabanlı” ise  
       → **tahmin** ← *olasılık medyanına denk gelen sayı*  
   - Eğer strateji “Ulam” ise  
       → **tahmin** ← *kalan_yalan + 1 kadar alt bölgeye ayırarak pivot seç*  
   - Eğer strateji “adaptif” ise  
       → **tahmin** ← *beklenen bilgi kazancını maksimize eden sayı*  

   - **deneme_sayisi** ← **deneme_sayisi** + 1  
   - YAZDIR *“Tahmin #”,* **deneme_sayisi**, *“: ”*, **tahmin**  
   - **geri_bildirim** ← *kullanıcıdan veya sistemden alınır*  

   ---

   *KOŞULLU GERİ BİLDİRİM İŞLEMLERİ*  
   - Eğer **geri_bildirim** == “dogru”  
       → YAZDIR *“Doğru tahmin bulundu!”*  
       → *döngüden çık*  
   - Eğer **geri_bildirim** == “daha_buyuk”  
       → **aktif_alt** ← **tahmin** + 1  
       → *alt sınırı güncelle ve olasılık dağılımını yeniden hesapla*  
   - Eğer **geri_bildirim** == “daha_kucuk”  
       → **aktif_ust** ← **tahmin** - 1  
       → *üst sınırı güncelle ve olasılık dağılımını yeniden hesapla*  
   - Eğer **geri_bildirim** == “belirsiz”  
       → **kalan_yalan** ← **kalan_yalan** - 1  
       → *Ulam hata toleranslı stratejiye geç*  

   ---

   *TEKRAR EDEN İŞLEMLER*  
   - Eğer **aktif_alt** > **aktif_ust**  
       → *“Tutarsız aralık, hata oluştu”*  
       → *rekonsiliasyon (yeniden değerlendirme) başlat*  

   - Eğer **olasilik_dagilimi** tek bir değere yoğunlaştıysa  
       → **tahmin** ← *en yüksek olasılığa sahip sayı*  
       → *erken durdurma uygula*  

   END WHILE  

---

6. *SONUÇLARI GÖSTER*  
   - Eğer doğru tahmin bulunduysa:  
       → YAZDIR *“Tebrikler! Doğru tahmin: ”*, **tahmin**, *“ - Deneme sayısı:”*, **deneme_sayisi**  
   - Aksi durumda:  
       → YAZDIR *“Oyun sonlandı. Doğru tahmin yapılamadı.”*  

---

7. *KARMAŞIKLIK VE STRATEJİ KARŞILAŞTIRMASI*  
   - *Binary Search:* Ortalama **O(log₂N)** adım, kesin geribildirim için optimal  
   - *Entropi Tabanlı Strateji:* Ortalama tahmin sayısı genelde daha düşük, hesaplama maliyeti yüksek  
   - *Ulam Stratejisi:* Hata toleranslı, yalan içeren oyunlar için uygundur  
   - *Adaptif Strateji:* Dinamik güncellemeli, en yüksek bilgi kazanımı hedeflenir  

## BİTİR

---
**Kaynakça:**  
- ChatGPT (LLM) desteğiyle oluşturulmuştur, 2025.  
---
---


![surprise](https://ngdblog.africa/wp-content/uploads/2023/01/Wow-gif.gif)
