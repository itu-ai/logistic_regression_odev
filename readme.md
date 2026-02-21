# ITU AI CLUB Ödev 3 Lojistik Regresyon (Logistic Regression)

## Lojistik Regresyon Nedir?

Lojistik regresyon, bağımlı değişkenin **kategorik** olduğu durumlarda kullanılan bir sınıflandırma algoritmasıdır. Lineer regresyondan farklı olarak sürekli bir değer tahmin etmez; bunun yerine bir gözlemin belirli bir sınıfa ait olma **olasılığını** hesaplar.

### Temel Mantık

1. Lineer regresyondaki gibi bir doğrusal kombinasyon hesaplanır:

$$z = w_0 + w_1 x_1 + w_2 x_2 + \dots + w_n x_n$$

2. Bu değer **sigmoid (logistic) fonksiyonundan** geçirilerek 0–1 arasında bir olasılığa dönüştürülür:

$$\sigma(z) = \frac{1}{1 + e^{-z}}$$

3. Elde edilen olasılık bir eşik değeriyle (genellikle 0.5) karşılaştırılarak sınıf tahmini yapılır.

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
3. **Veriyi bölün** – Eğitim ve test setlerine ayırın (`train_test_split`).
4. **Modeli kurun ve eğitin** – `sklearn.linear_model.LogisticRegression` kullanarak modeli eğitim verisiyle fit edin.
5. **Tahmin yapın** – Test seti üzerinde predict edin.
6. **Accuracy (doğruluk) hesaplayın** – Modelin test setindeki başarı oranını yazdırın.
