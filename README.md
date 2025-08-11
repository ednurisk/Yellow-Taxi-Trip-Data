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
