# ITU AI CLUB Ödev 3 Lojistik Regresyon (Logistic Regression)

## Lojistik Regresyon Nedir?

Lojistik regresyon, bağımlı değişkenin **kategorik** olduğu durumlarda kullanılan bir sınıflandırma algoritmasıdır. Lineer regresyondan farklı olarak sürekli bir değer tahmin etmez; bunun yerine bir gözlemin belirli bir sınıfa ait olma **olasılığını** hesaplar.

### Temel Mantık

1. Lineer regresyondaki gibi bir doğrusal kombinasyon hesaplanır:

$$z = w_0 + w_1 x_1 + w_2 x_2 + \dots + w_n x_n$$

2. Bu değer **sigmoid (logistic) fonksiyonundan** geçirilerek 0–1 arasında bir olasılığa dönüştürülür:

$$\sigma(z) = \frac{1}{1 + e^{-z}}$$

3. Elde edilen olasılık bir eşik değeriyle (genellikle 0.5) karşılaştırılarak sınıf tahmini yapılır.

### Softmax Fonksiyonu

Çok sınıflı (multinomial) problemlerde sigmoid yerine **softmax** fonksiyonu kullanılır. Softmax, her sınıf için ayrı bir olasılık üretir ve bu olasılıkların toplamı 1'e eşittir:

$$P(y = k) = \frac{e^{z_k}}{\sum_{j=1}^{K} e^{z_j}}$$

Burada $K$ toplam sınıf sayısı, $z_k$ ise $k$. sınıf için hesaplanan doğrusal skorudur. En yüksek olasılığa sahip sınıf tahmin olarak seçilir.

### İki Türü

- **Binary (İkili):** Sınıf sayısı 2'dir. Örnek: Kredi onaylandı mı? (Evet / Hayır)
- **Multinomial (Çok Sınıflı):** Sınıf sayısı 3 veya daha fazladır. Örnek: Bölge sınıflandırma (0, 1, 2)

---

## Ödev Tanımı

Bu ödevde iki CSV dosyası verilmiştir. Her biri için lojistik regresyon modeli kurulmalı, eğitilmeli ve sonuçlar gözlemlenmelidir.

### 1. Binary Lojistik Regresyon (`binary_logistic_regression.csv`)

| Sütun | Açıklama |
|-------|----------|
| `income` | Kişinin geliri |
| `debt_ratio` | Borç oranı (%) |
| `loan_approved` | **Hedef değişken** – Kredi onayı (0 = Reddedildi, 1 = Onaylandı) |

- **1000 satır** veri içerir.
- `income` ve `debt_ratio` özniteliklerini kullanarak `loan_approved` sınıfını tahmin edin.

### 2. Multinomial Lojistik Regresyon (`multinomial_logistic_regression.csv`)

| Sütun | Açıklama |
|-------|----------|
| `age` | Kişinin yaşı |
| `annual_income` | Yıllık gelir |
| `zone` | **Hedef değişken** – Bölge sınıfı (0, 1, 2) |

- **450 satır** veri içerir.
- `age` ve `annual_income` özniteliklerini kullanarak `zone` sınıfını tahmin edin.

### Yapılması Gerekenler

1. **Veriyi yükleyin** – CSV dosyasını okuyun, ilk birkaç satıra göz atın.
2. **Öznitelikleri (X) ve hedef değişkeni (y) ayırın.**
3. **Modeli kurun ve eğitin** – Lojistik regresyon modelini sıfırdan (numpy ile) yazarak tüm veriyle eğitin.
4. **Tahmin yapın** – Eğitilen modelle tahmin yapın.
5. **Accuracy (doğruluk) hesaplayın** – Modelin başarı oranını yazdırın.

> **Not:** Bu ödevde hazır kütüphane (sklearn vb.) kullanılmamalıdır. Model, numpy kullanılarak sıfırdan kodlanmalıdır.

### Opsiyonel Araştırma

- **Gradient Descent (Gradyan İnişi):** Modelin ağırlıklarını güncellemek için kullanılan optimizasyon yöntemidir. Kayıp fonksiyonunun gradyanı hesaplanarak ağırlıklar her adımda küçük bir öğrenme oranı ($\alpha$) ile güncellenir. Araştırıp öğrenmek isteyenler için önerilir.
- **Learning Rate (Öğrenme Oranı):** Gradient descent'te ağırlıkların her adımda ne kadar güncelleneceğini belirleyen hiperparametredir. Farklı değerlerle deneyip etkisini gözlemleyebilirsiniz.
