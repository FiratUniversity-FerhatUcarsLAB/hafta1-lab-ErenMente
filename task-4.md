Öğrenci No:250542026
AD-SOYAD:Muhammet Eren Mente

Lütfen seçtiğiniz algoritmaya ait çözümü ve diğer isterleri aşağıya ekleyiniz:






![Hello_There](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExYW0ydWU0NGRuMW93b2ZjdG54dmhpZmw2enIwbHFkajZkazJ1emh5ZCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/Nx0rz3jtxtEre/giphy.gif)


### Merhaba,yazılım 1-b'den Eren;  
### bu dosyayı ödevde söylendiği gibi bir LLM olan chat gpt desteğiyle yaptım içerikteki hiçbir şey şahsıma ait değildir. 
### Saygılar...


### Market envanterini kategorilere ayırma — PSEUDOCODE

1. *GEREKLİ DEĞİŞKENLERİ TANIMLA*  
   - **envanter_listesi** ← *market stokundaki tüm ürünlerin listesi*  
   - **kategori_listesi** ← *önceden tanımlı kategori isimleri (ör: gıda, temizlik, kozmetik, teknoloji, vb.)*  
   - **urun_kategorisi** ← *her ürünün ait olduğu kategori bilgisi (başlangıçta boş)*  
   - **stok_miktari** ← *her ürünün mevcut adedi*  
   - **kritik_stok_limiti** ← *stok azaldığında uyarı verecek sınır değeri*  
   - **yeni_kategori** ← *kullanıcının tanımlayacağı yeni kategori (isteğe bağlı)*  

---

2. *KULLANICIDAN GİRDİ AL*  
   - "Toplam ürün sayısını giriniz:" → **urun_sayisi**  
   - Her ürün için:  
       → ürün adı al → **envanter_listesi**’ne ekle  
       → stok miktarını al → **stok_miktari** listesine ekle  
       → kategori seçimi iste → **urun_kategorisi**’ne ekle  

   - Eğer kategori listesinde olmayan bir kategori girilirse:  
       → YAZDIR *“Bu kategori yeni, listeye eklenecek.”*  
       → **kategori_listesi**’ne **yeni_kategori** olarak ekle  

---

3. *KATEGORİLERE GÖRE GRUPLAMA YAP*  
   - Her kategori için:  
       → o kategoriye ait ürünleri filtrele  
       → **kategori_grubu** oluştur  
       → YAZDIR *kategori adı ve o kategoriye ait ürün listesi*  

   - Eğer bazı ürünler kategorisizse:  
       → YAZDIR *“Kategorisiz ürünler bulundu, manuel sınıflandırma gerekiyor.”*  
       → Kullanıcıdan yeni kategori seçimi al  

---

4. *KOŞULLU DURUMLAR VE UYARILAR*  
   - Her ürün için:  
       - Eğer **stok_miktari[urun]** < **kritik_stok_limiti** ise  
           → YAZDIR *“Uyarı: ”*, **urun_adı**, *“ stoğu azaldı!”*  
           → *stok_yenileme_listesi’ne ekle*  
       - Aksi durumda:  
           → *“Stok durumu normal.”*  

   - Eğer **kategori_listesi** boşsa  
       → *“Kategori tanımlanmadı, varsayılan kategoriler oluşturuluyor.”*  
       → **kategori_listesi** ← ["Gıda", "Temizlik", "Kozmetik", "Diğer"]  

---

5. *TEKRAR EDEN İŞLEMLER*  
   - Kullanıcı “Yeni ürün ekle” seçeneğini seçerse:  
       → ürün bilgilerini gir  
       → uygun kategoriye ata  
       → **envanter_listesi** ve **stok_miktari** güncelle  
   - Kullanıcı “Kategori düzenle” seçeneğini seçerse:  
       → **kategori_listesi**’nde değişiklik yap  
       → ürünlerin kategorilerini yeniden eşleştir  

   - Eğer kullanıcı “Envanteri yeniden sınıflandır” derse:  
       → tüm ürünleri tekrar kategorilere ayır  
       → güncel listeyi yazdır  

---

6. *SONUÇLARI GÖSTER*  
   - Tüm kategoriler ve bu kategorilere ait ürün listeleri yazdır  
   - Toplam ürün sayısı, eksik stok sayısı, yeni eklenen kategoriler göster  
   - YAZDIR *“Market envanteri başarıyla kategorilere ayrılmıştır.”*  

---

7. *KARŞILAŞTIRMALI DEĞERLENDİRME (İSTEĞE BAĞLI)*  
   - *Kural tabanlı sınıflandırma:* hızlı ama manuel  
   - *Anahtar kelime tabanlı sınıflandırma:* ürün adlarından otomatik kategori tespiti  
   - *Yapay zekâ tabanlı sınıflandırma:* doğal dil analiziyle dinamik kategori önerisi  
   - *Karma yaklaşım:* hem kullanıcı girdisi hem otomatik etiketleme kullanılır  

---

## 🔴 BİTİR

---
**Kaynakça:**  
- ChatGPT (LLM) desteğiyle oluşturulmuştur, 2025.  
---
---


![surprise](https://ngdblog.africa/wp-content/uploads/2023/01/Wow-gif.gif)
