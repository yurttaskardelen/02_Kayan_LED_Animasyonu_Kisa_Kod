# STM32F407 Kayan LED Animasyonu (v2 - Refactor Edilmiş Kod)

Bu proje, **STM32F407-Discovery** kartı üzerinde 4 adet LED kullanarak klasik **Kara Şimşek (Knight Rider)** benzeri bir ileri-geri kayan ışık animasyonu gerçekleştirir.

Bu deponun amacı, aynı sonuca **daha verimli, ölçeklenebilir ve profesyonel** bir kod yapısıyla nasıl ulaşılabileceğini göstermektir. Proje, "Temiz Kod" (Clean Code) ve "Kendini Tekrar Etme" (DRY - Don't Repeat Yourself) prensiplerinin basit bir uygulamasını içerir.

> **💡 Temel Versiyon (Açık Kod)**
>
> Bu projenin, her komutun adım adım, tekrar edilerek yazıldığı **en temel ve açık** halini görmek için v1 deposunu inceleyebilirsiniz.
>
> ➡️ **[01_Kayan_LED_Animasyonu (v1 - Temel Yöntem)](https://github.com/yurttaskardelen/01_Kayan_LED_Animasyonu)**

---

### 🎯 Kod Yapısındaki Fark Nedir? (v1 vs v2)

Bu projenin (v2) var olma amacı, v1'deki kod tekrarını ortadan kaldırmaktır. 
İlk projede, her LED pini için ayrı ayrı `HAL_GPIO_WritePin` ve `HAL_Delay` komutları kullanılmıştı. 4 LED için yönetilebilir olsa da, 16 LED'li bir projede bu yöntem verimsizdir.

---

### 🎯 Proje Senaryosu

Animasyon, 4 LED üzerinde sıralı bir hareketle çalışır:
1.  LED'ler `PA1`'den `PA4`'e doğru sırayla yanar (Sağa hareket).
2.  LED'ler `PA4`'den `PA1`'ye doğru sırayla yanar (Sola hareket).
3.  Döngü başa döner.

**Zamanlama:**
* **LED Yanma Süresi:** 200 ms
* **LED Sönme Süresi:** 100 ms (Bir sonraki LED'e geçmeden önce)

---

### 🛠️ Gerekli Donanım

* **1x** STM32F407-Discovery Geliştirme Kartı
* **4x** Tercih edilen renkte LED
* **4x** 220 Ohm Direnç (LED'ler için ön direnç)
* Breadboard ve Jumper kablolar

---

### 🔌 Devre Şeması

LED'lerin anot (uzun) bacakları STM32 pinlerine, katot (kısa) bacakları ise direnç üzerinden GND hattına bağlanmalıdır.

| LED | Direnç | STM32 Pini |
| :--- | :--- | :--- |
| LED 1 | 220 Ohm | `PA1` |
| LED 2 | 220 Ohm | `PA2` |
| LED 3 | 220 Ohm | `PA3` |
| LED 4 | 220 Ohm | `PA4` |
| (Tümü) | - | `GND` |

<img width="473" height="404" alt="Pin_Baglantilari" src="https://github.com/user-attachments/assets/7103876f-9e8b-4da0-b089-e8e4b43abb4a" />


### Kod Bloğu

<img width="1200" height="638" alt="02" src="https://github.com/user-attachments/assets/fe69999c-2cc9-4cb1-bae5-c2f7f2cf9522" />


---

### 🚀 Nasıl Kullanılır?

1.  Bu depoyu klonlayın (`git clone ...`).
2.  STM32CubeIDE yazılımını açın.
3.  `File > Open Projects from File System...` seçeneği ile proje klasörünü seçin.
4.  Proje içindeki `.ioc` dosyasını açarak pin yapılandırmasını inceleyebilirsiniz.
5.  Derleyin (Build) ve ST-Link V2 üzerinden kartınıza yükleyin (Run).
