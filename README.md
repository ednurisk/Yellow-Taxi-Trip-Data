## 🚖 NYC Taxi Trip Data Analizi


### 📘 TaxiTrip1.pynb 
- `matplotlib` ve `seaborn` ile veri görselleştirmeleri yapıldı:
  - `trip_distance` ve `total_amount` dağılımları
  - Yoğun saat ve gün analizleri
  - Pickup & dropoff noktalarına göre mesafe karşılaştırmaları
- En kısa/uzun yolculuklar ve ücret aralıkları belirlendi.
<br>

### 📘 TaxiTrip2.pynb 
- Kredi kartı ile nakit ödeme yapan yolcuların ortalama ücret farkını ölçmek için
  **bağımsız örneklem t-testi** (`scipy.stats.ttest_ind`) uygulandı.
<br>

### 📘 TaxiTrip3.pynb 
- Veri Yükleme & Temizlik
  - Eksik veri ve tekrar eden kayıtlar kontrol edildi (bulunmadı).
  - Tarih-saat sütunları `datetime` formatına dönüştürüldü.
  - Uç değerler (`trip_distance`, `fare_amount`, `duration`) tespit edilip incelendi.

- Keşifsel Veri Analizi (EDA)
  - Genel istatistikler (`describe`) incelendi.
  - Boxplot ve scatterplot grafiklerle dağılımlar görselleştirildi.
  - `trip_distance` değeri 0 olan kayıtlar veri kalitesi açısından analiz edildi.

- Modelleme: Doğrusal Regresyon
  - Hedef değişken: `fare_amount`
  - Bağımsız değişkenler: mesafe, süre vb. seyahat özellikleri.
  - Veri eğitim (%80) ve test (%20) olarak ayrıldı.
  - Özellikler `StandardScaler` ile ölçeklendirildi.
  - `LinearRegression` modeli ile eğitim yapıldı.

- Model Performansı
  - **Eğitim seti** ve **test seti** üzerinde R², MAE, MSE, RMSE metrikleri hesaplandı.
  - Tahmin & gerçek değer karşılaştırma grafikleri çizildi.
  - Artık (residual) analizleri ile modelin hata dağılımı incelendi.
  - Model katsayıları yorumlandı.
<br>

### 📘 TaxiTrip4.pynb 

- Veri Yükleme & Ön İşleme
  - Kullanılmayan sütunlar (`Unnamed: 0`, `payment_type`, vb.) veri setinden çıkarıldı.
  - Kategorik değişkenler (`RatecodeID`, `PULocationID`, `DOLocationID`, `VendorID`) string tipe dönüştürüldü.

- Özellik Mühendisliği
  - Zaman bazlı değişkenler:
    - `day`: Yolculuk günü (`Monday`, `Tuesday`, vb.).
    - `am_rush`: Sabah yoğun saat (06:00–10:00).
    - `daytime`: Gün ortası (10:00–16:00).
    - `pm_rush`: Akşam yoğun saat (16:00–20:00).
    - `nighttime`: Gece saatleri (20:00–06:00).
  - Bu zaman aralıkları binary (0/1) formatına dönüştürüldü.

- Modelleme
  - Hedef değişken: Belirli bir sınıflandırma hedefi (ör. yüksek/düşük ücret, vb.).
  - Eğitim ve test verisi %80 / %20 oranında ayrıldı.
  - Modeller:
    - `RandomForestClassifier`
    - `XGBClassifier` (XGBoost)
  - **Hiperparametre optimizasyonu**: `GridSearchCV` kullanıldı.
  - Model değerlendirme metrikleri: 
    - Accuracy, Precision, Recall, F1-score
    - ROC-AUC ve ROC eğrisi
    - Confusion Matrix
  - Özellik önem sıralaması: XGBoost `plot_importance` ile görselleştirildi.
<br>

## In English
## 🚖 NYC Taxi Trip Data Analysis

### 📘 TaxiTrip1.pynb
- Data visualizations created with `matplotlib` and `seaborn`:
  - Distributions of `trip_distance` and `total_amount`
  - Peak hour and day analysis
  - Distance comparisons by pickup & dropoff locations
- Identified the shortest/longest trips and fare ranges.
<br>

### 📘 TaxiTrip2.pynb
- Applied an **independent samples t-test** (`scipy.stats.ttest_ind`) to compare
  the average fare difference between credit card and cash payments.
<br>

### 📘 TaxiTrip3.pynb
- **Data Loading & Cleaning**
  - Checked for missing values and duplicates (none found).
  - Converted datetime columns to `datetime` format.
  - Detected and examined outliers (`trip_distance`, `fare_amount`, `duration`).

- **Exploratory Data Analysis (EDA)**
  - Reviewed general statistics (`describe`).
  - Visualized distributions with boxplots and scatterplots.
  - Analyzed records with `trip_distance` equal to 0 for data quality.

- **Modeling: Linear Regression**
  - Target variable: `fare_amount`
  - Features: distance, duration, and other trip characteristics.
  - Split data into training (80%) and testing (20%) sets.
  - Scaled features using `StandardScaler`.
  - Trained a `LinearRegression` model.

- **Model Performance**
  - Calculated R², MAE, MSE, RMSE for both training and test sets.
  - Plotted predicted vs. actual values.
  - Conducted residual analysis to assess error distribution.
  - Interpreted model coefficients.
<br>

### 📘 TaxiTrip4.pynb
- **Data Loading & Preprocessing**
  - Removed unused columns (`Unnamed: 0`, `payment_type`, etc.).
  - Converted categorical variables (`RatecodeID`, `PULocationID`, `DOLocationID`, `VendorID`) to string type.

- **Feature Engineering**
  - Created time-based features:
    - `day`: Day of the trip (`Monday`, `Tuesday`, etc.).
    - `am_rush`: Morning rush (06:00–10:00).
    - `daytime`: Midday (10:00–16:00).
    - `pm_rush`: Evening rush (16:00–20:00).
    - `nighttime`: Night hours (20:00–06:00).
  - Converted these time intervals into binary (0/1) format.

- **Modeling**
  - Target variable: Specific classification objective (e.g., high/low fare, etc.).
  - Split data into training (80%) and testing (20%).
  - Models:
    - `RandomForestClassifier`
    - `XGBClassifier` (XGBoost)
  - **Hyperparameter tuning** with `GridSearchCV`.
  - Model evaluation metrics:
    - Accuracy, Precision, Recall, F1-score
    - ROC-AUC and ROC curve
    - Confusion Matrix
  - **Feature importance** visualized using XGBoost `plot_importance`.








