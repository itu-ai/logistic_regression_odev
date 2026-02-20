# ITU AI CLUB Ödev 3 Lojistik Regresyon (Logistic Regression)

## Lojistik Regresyon Nedir?

Lojistik regresyon, bağımlı değişkenin **kategorik** olduğu durumlarda kullanılan bir sınıflandırma algoritmasıdır. Lineer regresyondan farklı olarak sürekli bir değer tahmin etmez; bunun yerine bir gözlemin belirli bir sınıfa ait olma **olasılığını** hesaplar.

### Temel Mantık

1. Lineer regresyondaki gibi bir doğrusal kombinasyon hesaplanır:

$$z = w_0 + w_1 x_1 + w_2 x_2 + \dots + w_n x_n$$

2. Bu değer **sigmoid (logistic) fonksiyonundan** geçirilerek 0–1 arasında bir olasılığa dönüştürülür:

$$\sigma(z) = \frac{1}{1 + e^{-z}}$$

3. Elde edilen olasılık bir eşik değeriyle (genellikle 0.5) karşılaştırılarak sınıf tahmini yapılır.

### Kayıp Fonksiyonu (Loss Function)

Lojistik regresyonda **Binary Cross-Entropy (Log Loss)** kullanılır:

$$L = -\frac{1}{N} \sum_{i=1}^{N} \left[ y_i \log(\hat{y}_i) + (1 - y_i) \log(1 - \hat{y}_i) \right]$$

Bu fonksiyon, modelin tahmin ettiği olasılıkların gerçek etiketlerden ne kadar uzak olduğunu ölçer. Eğitim sırasında bu kayıp minimize edilir.

### İki Türü

| Tür | Sınıf Sayısı | Örnek |
|-----|--------------|-------|
| **Binary (İkili)** | 2 | Kredi onaylandı mı? (Evet / Hayır) |
| **Multinomial (Çok Sınıflı)** | 3+ | Bölge sınıflandırma (0, 1, 2) |

- **Binary** lojistik regresyonda tek bir sigmoid çıkışı yeterlidir.
- **Multinomial** lojistik regresyonda sigmoid yerine **softmax** fonksiyonu kullanılır; bu fonksiyon her sınıf için ayrı bir olasılık üretir ve toplamları 1'e eşittir.

---

## Ödev Tanımı

Bu ödevde iki CSV dosyası verilmiştir. Her biri için lojistik regresyon modeli kurulmalı, eğitilmeli ve değerlendirilmelidir.

### 1. Binary Lojistik Regresyon (`binary_logistic_regression.csv`)

| Sütun | Açıklama |
|-------|----------|
| `income` | Kişinin geliri |
| `debt_ratio` | Borç oranı (%) |
| `loan_approved` | **Hedef değişken** – Kredi onayı (0 = Reddedildi, 1 = Onaylandı) |

- **1000 satır** veri içerir.
- `income` ve `debt_ratio` özniteliklerini kullanarak `loan_approved` sınıfını tahmin edin.
- Bu bir **ikili sınıflandırma** problemidir.

### 2. Multinomial Lojistik Regresyon (`multinomial_logistic_regression.csv`)

| Sütun | Açıklama |
|-------|----------|
| `age` | Kişinin yaşı |
| `annual_income` | Yıllık gelir |
| `zone` | **Hedef değişken** – Bölge sınıfı (0, 1, 2) |

- **450 satır** veri içerir.
- `age` ve `annual_income` özniteliklerini kullanarak `zone` sınıfını tahmin edin.
- Bu bir **çok sınıflı sınıflandırma** problemidir (3 sınıf).

### Yapılması Gerekenler

1. **Veriyi yükleyin** ve keşifsel analiz yapın (ilk satırlar, istatistikler, eksik değer kontrolü).
2. **Veriyi bölün** – Eğitim (%80) ve test (%20) setlerine ayırın.
3. **Modeli kurun** – `sklearn.linear_model.LogisticRegression` veya kendi implementasyonunuzu kullanın.
4. **Modeli eğitin** – Eğitim seti üzerinde fit edin.
5. **Tahmin yapın** – Test seti üzerinde predict edin.
6. **Değerlendirin** – Aşağıdaki metrikleri raporlayın:
   - Accuracy (Doğruluk)
   - Confusion Matrix (Karışıklık Matrisi)
   - Classification Report (Precision, Recall, F1-Score)
7. **Görselleştirme** (Opsiyonel) – Karar sınırını (decision boundary) çizin.
