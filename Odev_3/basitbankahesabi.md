```python
class Hesap: # her şeyi bir düzene sokmak için Hesap adında bir class yapıyoruz.
    def __init__(self, hesap_isim, hesap_no, bakiye=0): # özellikler ekliyoruz isim, no, bakiye
        self.hesap_isim = hesap_isim
        self.hesap_no = hesap_no
        self.bakiye = bakiye

    def para_yatir(self, miktar): # fonksiyon tanımlıyoruz
        if miktar > 0: # miktar 0'dan büyükse bakiye = bakiye + miktar yapıyoruz.
            self.bakiye += miktar
            print(f"{miktar} TL yatırıldı. Yeni bakiye: {self.bakiye} TL")
        else: # değilse ekrana yatırılacak tutar 0'dan büyük olmalıdır yazıyoruz.
            print("Yatırılacak tutar 0'dan büyük olmalıdır.")

    def para_cek(self, miktar): # fonksiyon tanımlıyoruz
        if miktar <= 0: # eğer 0 veya 0'dan küçük bir miktar girilirse
            print("Çekilecek tutar 0'dan büyük olmalıdır.")
        elif miktar > self.bakiye: # miktar bakiyeden büyük olduğu için para çekilemediğini söylemek istiyoruz.
            print("Yetersiz bakiye! Çekmek istediğiniz tutar mevcut bakiyenizden fazla.")
        else:
            self.bakiye -= miktar # bakiye = bakiye - miktar yapıyoruz çünkü kalan bakiyeyi ekrana yazmak istiyoruz.
            print(f"{miktar} TL çekildi. Kalan bakiye: {self.bakiye} TL")

    def bakiye_goruntule(self): # mevcut hesap bilgilerini ve bakiyeyi ekrana yazdırıyoruz.
        print(f"Hesap Sahibi: {self.hesap_isim} | Hesap No: {self.hesap_no} | Güncel Bakiye: {self.bakiye} TL")


isim = input("Hesap sahibinin adı ve soyadı: ") # Kullanıcıdan hesap bilgilerini alıyoruz
numara = input("Hesap numarası: ")
baslangic_bakiye = float(input("Başlangıç bakiyesini girin: "))

musteri_hesabi = Hesap(isim, numara, baslangic_bakiye) # girilen bilgilerle Hesap classından bir nesne oluşturuyoruz

while True: # Kullanıcı çıkış yapana kadar devam eden bir döngü kuruyoruz
    print("\n--- Banka Hesap Menüsü ---")
    print("1 - Para Yatır")
    print("2 - Para Çek")
    print("3 - Bakiye Görüntüle")
    print("4 - Çıkış")

    secim = input("Yapmak istediğiniz işlemi seçin (1-4): ") # kullanıcıdan 1 ile 4 arası değer alıyoruz.

    if secim == "1": # eğer seçim 1 ise
        tutar = float(input("Yatırmak istediğiniz tutarı girin: "))
        musteri_hesabi.para_yatir(tutar)
    elif secim == "2": # eğer seçim 2 ise
        tutar = float(input("Çekmek istediğiniz tutarı girin: "))
        musteri_hesabi.para_cek(tutar)
    elif secim == "3": # eğer seçim 3 ise
        musteri_hesabi.bakiye_goruntule()
    elif secim == "4": # eğer seçim 4 ise
        print("İşlem sonlandırıldı. İyi günler!")
        break
    else:
        print("Hatalı seçim! Lütfen 1 ile 4 arasında bir değer girin.")
```
