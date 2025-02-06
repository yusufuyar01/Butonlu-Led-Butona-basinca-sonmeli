# Buton ile LED Kontrolü

Bu proje, bir buton ve bir LED kullanarak basit bir kontrol mekanizması oluşturmayı amaçlar. Butona basıldığında LED söner, buton bırakıldığında ise LED yanar.

## İçindekiler

- [Açıklama](#açıklama)
- [Gereksinimler](#gereksinimler)
- [Kurulum](#kurulum)
- [Kullanım](#kullanım)
- [Kod Açıklaması](#kod-açıklaması)

## Açıklama

Bu proje, Arduino platformunda geliştirilmiş basit bir uygulamadır. Bir buton ve bir LED kullanılarak, butonun durumuna göre LED'in yanıp sönmesi kontrol edilir. Proje, temel Arduino kullanımını ve dijital giriş/çıkış işlemlerini göstermektedir.

## Gereksinimler

- Arduino kartı (Örneğin, Arduino Uno)
- 1 adet LED
- 1 adet buton
- Jumper kabloları
- 220 ohm direnç (LED için)
- 10k ohm direnç (buton için)

## Kurulum

1. Arduino IDE'yi bilgisayarınıza indirin ve kurun.
2. Gerekli kütüphaneleri yükleyin (bu proje için herhangi bir ek kütüphane gerekmemektedir).
3. Devre şemasını aşağıdaki gibi kurun:
    - LED'in anot ucunu (uzun bacak) 9. pine bir 220 ohm direnç üzerinden bağlayın.
    - LED'in katot ucunu (kısa bacak) GND'ye bağlayın.
    - Butonun bir bacağını 8. pine bağlayın.
    - Butonun diğer bacağını GND'ye bir 10k ohm direnç üzerinden bağlayın.
    - Butonun bir bacağını 5V'ye bağlayın.
    ![Image](https://github.com/user-attachments/assets/f59b0d54-552c-4439-8264-e6aeeab7d3fd)
4. Arduino IDE'de doğru kartı ve portu seçin.
5. Aşağıdaki kodu Arduino IDE'ye kopyalayın ve yükleyin.

## Kullanım

Proje yüklendikten sonra, butona basıldığında LED sönecektir. Buton bırakıldığında ise LED yanacaktır.

## Kod Açıklaması

```c++
int led = 9; // LED'in bağlı olduğu pin
int buton = 8; // Butonun bağlı olduğu pin
int butonDurumu = 0; // Butonun durumunu saklayan değişken

void setup() {
  pinMode(buton, INPUT); // Buton pinini giriş olarak ayarla
  pinMode(led, OUTPUT); // LED pinini çıkış olarak ayarla
}

void loop() {
  butonDurumu = digitalRead(buton); // Butonun durumunu oku

  if (butonDurumu == HIGH) { // Butona basıldıysa
    digitalWrite(led, LOW); // LED'i söndür
  } else { // Buton bırakıldıysa
    digitalWrite(led, HIGH); // LED'i yak
  }
}
