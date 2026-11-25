
````python
metin = input("Bir cümle veya paragraf girin: ") # bir cümle veya paragraf girilmesini istiyoruz.

toplam_karakter = len(metin)# len() fonksiyonu karakter sayısının hesaplanmasını sağlar.

temiz_metin = metin.lower() # büyük-küçük harf farkını ortadan kaldırmak için .lower metodu kullamıp tüm harferleri küçük yaptık.

temiz_metin = temiz_metin.replace(".", "") # Noktalama işaretlerinin kelime sayımını bozmaması için .replace() metodu ile nokta işaretlerini siliyoruz.

temiz_metin = temiz_metin.replace("?", "") # yeniden .replace ile soru işaretini kaldırdık.

temiz_metin = temiz_metin.replace(",", "")# yeniden .replace ile virgülü siliyoruz

temiz_metin = temiz_metin.replace("!", "") # yeniden .replace ile ünlemi siliyoruz


kelimeler = temiz_metin.split(" ") # Metni boşluğa  göre bölerek kelimelerden oluşan bir liste elde ediyoruz.

while "" in kelimeler:
    kelimeler.remove("")# Kullanıcı arka arkaya birden fazla boşluk bıraktıysa listede "" bu yüzden remove kullanıyoruz.


toplam_kelime = len(kelimeler) 
# düzenlediğimiz listedeki eleman sayısını alarak toplam kelime sayısını buluyoruz.


en_uzun_uzunluk = 0 # en uzun değeri bulmak için 0 değişkeni tanımlıyoruz

# Her kelimenin kaç kez geçtiğini anahtar-değer (kelime: sayı) şeklinde tutmak için boş bir sözlük (dict) açıyoruz.
kelime_tekrarlari = {}


for kelime in kelimeler: # Listedeki her bir kelimeyi tek tek kontrol etmek için for döngüsü başlatıyoruz.
   
    if len(kelime) > en_uzun_uzunluk: # eğer sıradaki kelimenin uzunluğu şuana kadarki en uzun kelimeden büyükse
       
        en_uzun_uzunluk = len(kelime) # en uzun kelime uzunluğunu bu yeni değerle güncelliyoruz.

  
    if kelime in kelime_tekrarlari: # eğer kelime daha önce sözlüğe eklenmişse .
       
        kelime_tekrarlari[kelime] += 1 # kelimenin tekrar sayısını bir artırıyoruz.
    
    else:# eğer kelime sözlükte hiç yoksa.
        
        kelime_tekrarlari[kelime] = 1# kelimeyi sözlüğe ekleyip başlangıç değerini 1 yapıyoruz.


print(f"Toplam kelime sayısı: {toplam_kelime}")# Hesaplanan toplam kelime sayısını ekrana yazdırıyoruz.


print(f"toplam karakter ve boşluklar sayısı: {toplam_karakter}")# Hesaplanan toplam karakter sayısını ve artı olarak boşluk sayısını ekrana yazdırıyoruz.

print(f"en uzun kelimenin uzunluğu: {en_uzun_uzunluk}")# Bulunan en uzun kelimenin harf saysını ekrana yazıyoruz.


print("kelimelerin tekrar sayıları:")# tekrar sayılarını listelemeden önce başlık yazdırıyoruz.

# Sözlükteki her bir kelime için döngü kuruyoruz.

for kelime in kelime_tekrarlari: # İlgili kelimeyi ve sözlükteki karşılığı olan tekrar sayısını ekrana yazdırıyoruz.
   
    print(f"{kelime}: {kelime_tekrarlari[kelime]} kez")
```