
Bu proje, RGB (Red, Green, Blue) formatındaki renk vektörlerini belirli bir aralığa ölçeklendirerek (normalizasyon), renkler arasındaki geometrik uzaklığı (Öklid Mesafesi) hesaplar ve iki rengin birbirine yüzde kaç benzediğini ortaya koyar.

## 🚀 Proje Amacı

RGB renk uzayında $255 \times 255 \times 255 = 16.581.375$ farklı renk kombinasyonu bulunur. Bu projede amaç, verilen renklerin ham RGB değerlerini $[0-100]$ arası standart bir ölçeğe taşımak ve ardından **Vektör Benzerliği** (Vector Similarity) algoritması kullanarak iki rengin analitik olarak ne kadar yakın olduğunu bulmaktır.

---

## 🛠️ Kullanılan Fonksiyonlar

Proje, herhangi bir dış kütüphane (NumPy vb.) kullanmadan tamamen saf Python matematik mantığıyla yazılmıştır:

* **`arrange(item, dim, min, max)`**: Renk vektöründeki her bir kanalı (R, G, B) $[0 - 100]$ aralığına normalize eder. Eğer eksik boyut verilirse varsayılan bir dolgu atar.
* **`kokal(x)`**: Bir sayının karekökünü hesaplar ($\sqrt{x}$).
* **`usal(x, level)`**: Bir sayının belirtilen üssünü alır ($x^{level}$).
* **`vectorSimilarity(A, B)`**: İki normalize edilmiş renk vektörü arasındaki mesafeyi Öklid formülü kullanarak hesaplar ve maksimum olası mesafeye oranlayarak `0` ile `1` arasında bir benzerlik skoru döner.

---

## 💻 Örnek Çalıştırma ve Çıktı

Sistem üzerinde tanımlı olan bazı temel renkler şunlardır:
* 🔴 Kırmızı (`[255, 0, 0]`)
* ⚫ Siyah (`[0, 0, 0]`)
* ⚪ Beyaz (`[255, 255, 255]`)
* 🔘 Gri (`[82, 82, 82]`)

### Kodun Çalıştırılması

Projede **Siyah** ve **Gri** renkleri arasındaki benzerliği test etmek için aşağıdaki adımlar yürütülür:

```python
kirmizi_normalized = arrange(kirmizi, 3, 0, 255)
siyah_normalized = arrange(siyah, 3, 0, 255)
gri_normalized = arrange(gri, 3, 0, 255)
```
# Siyah ve Gri arasındaki benzerlik oranı hesaplanır
```
benzerlik_orani = vectorSimilarity(siyah_normalized, gri_normalized)
print(f"Benzerlik Oranı: {benzerlik_orani}")
```
Hesaplama Mantığı
Program iki vektör arasındaki mesafeyi şu matematiksel formülle işler:
$$Distance = \sqrt{\sum_{i=1}^{n} (B_i - A_i)^2}
$$Elde edilen mesafe, $[0-100]$ ölçeğindeki maksimum olası uzaklığa bölünerek yüzdeye çevrilir:
$$Similarity = 1 - \left( \frac{Distance}{Max\_Dist} \right)
$$📦 Kurulum ve ÇalıştırmaProjeyi bilgisayarınıza klonlayın:
Bash
```
git clone https://github.com/TurkerAlbayrakC.git
```
Proje dizinine gidin:Bash
```
cd /python-color-similarity-ratio-computation
```
Scripti çalıştırın:
Bash
```
python color.py
```
