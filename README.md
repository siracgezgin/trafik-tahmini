# 🚦 İstanbul Trafik Yoğunluğu Tahmini Projesi

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Contributions Welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg?style=flat)](CONTRIBUTING.md)

Bu proje, İstanbul’daki trafik verilerini kullanarak *trafik yoğunluğunu tahmin etmeyi* ve *trafik dinamiklerini* daha iyi anlayarak gelecekteki trafik durumuna dair öngörüler sunmayı amaçlamaktadır. Proje boyunca, eksik değer analizi, aykırı değer yönetimi, veri ön işleme, özellik mühendisliği, çoklu makine öğrenmesi algoritmalarıyla modelleme, hiperparametre optimizasyonu ve sonuçların görselleştirilmesi gibi kapsamlı adımlar uygulanmıştır.

## İçindekiler
- [Projenin Amacı](#projenin-amacı)
- [Veri Seti ve Özellikler](#veri-seti-ve-özellikler)
- [Kullanılan Teknolojiler](#kullanılan-teknolojiler)
- [Proje Yapısı](#proje-yapısı)
- [Veri Hazırlama Süreci](#veri-hazırlama-süreci)
  - [Eksik Değer Analizi](#eksik-değer-analizi)
  - [Aykırı Değer Tespiti ve Düzeltilmesi](#aykırı-değer-tespiti-ve-düzeltilmesi)
  - [Özellik Mühendisliği](#özellik-mühendisliği)
  - [Kod Detayları](#kod-detayları)
- [Model Geliştirme ve Değerlendirme](#model-geliştirme-ve-değerlendirme)
  - [Kullanılan Algoritmalar](#kullanılan-algoritmalar)
  - [Hiperparametre Optimizasyonu](#hiperparametre-optimizasyonu)
  - [Model Eğitim ve Performans Metrikleri](#model-eğitim-ve-performans-metrikleri)
  - [Model Karşılaştırma](#model-karşılaştırma)
  - [Özellik Önem Analizi](#özellik-önem-analizi)
  - [Learning Curves Analizi](#learning-curves-analizi)
  - [Model Tahmin Süreleri](#model-tahmin-süreleri)
- [Sonuçlar ve Özet Rapor](#sonuçlar-ve-özet-rapor)
- [Klasör Yapısı ve Kayıtlı Dosyalar](#klasör-yapısı-ve-kayıtlı-dosyalar)
- [Kullanım](#kullanım)
- [Öneriler](#öneriler)
- [Katkıda Bulunma](#katkıda-bulunma)
- [İletişim](#iletişim)
- [Lisans](#lisans)

---

## Projenin Amacı
İstanbul’daki trafik yoğunluğunu *zamansal ve mekansal boyutlarda* inceleyerek;

- *Gerçek zamanlı trafik tahminleri* yapmak,  
- *Farklı faktörlerin* (hava durumu, tatil günleri, hafta içi-hafta sonu vb.) trafik akışına etkilerini analiz etmek,  
- *Şehir planlamacıları ve karar alıcılar* için anlamlı öngörüler sunmak,  
- *Sürücüler ve lojistik firmaları* için rota planlamasına dair yardımcı olmak,  
- *Trafik yönetim süreçlerini* veri temelli olarak iyileştirmek  
- *Gelecekteki trafik durumu* hakkında tahminlerle stratejik planlama yapmak.  

---

## Veri Seti ve Özellikler
- *Trafik Verileri (Trafik_Verileri.csv)*: İçerisinde hız bilgileri, araç sayısı ve coğrafi koordinatlar gibi temel değişkenler barındırır.  
- *Ek Değişkenler*:  
  - Hava durumu (WEATHER)  
  - Resmi tatil bilgisi (IS_HOLIDAY)  
  - Yoğun saat bilgisi (IS_PEAK_HOUR)  
  - Hafta sonu bilgisi (IS_WEEKEND)  
  - Mevsim (SEASON)  
- *Zaman Özellikleri*: Tarih-saat bilgileri (DATE_TIME), gün, ay, yıl ve hafta içi/sonu ayrımı gibi özellikler türetilmiştir.  

Veri seti içerisinde, *eksik değerler* ve *aykırı değerler* gerçek dünya örneklerine benzer şekilde bulunmakta ve projede bu değerlerle ilgili kapsamlı *veri temizleme ve ön işleme* adımları uygulanmaktadır.

## Özellikler

- Gerçek zamanlı trafik verisi analizi
- Çoklu makine öğrenmesi algoritmaları ile tahminleme
- Detaylı performans metrikleri ve model karşılaştırmaları
- Kapsamlı veri görselleştirme araçları
- Kullanıcı dostu Jupyter notebook arayüzü
- Otomatik veri ön işleme pipeline'ı
- Aykırı değer tespiti ve yönetimi
- Çapraz doğrulama ve model optimizasyonu
- İnteraktif performans grafikleri
- Özellik önem analizi
  
---

## Kullanılan Teknolojiler
| Teknoloji    | Sürüm   | Amaç                                    |
|--------------|---------|-----------------------------------------|
| *Python*   | 3.8+    | Temel programlama dili                  |
| *Pandas*   | 1.3+    | Veri manipülasyonu                      |
| *NumPy*    | 1.21+   | Sayısal işlemler ve vektörel hesaplamalar|
| *Matplotlib* | 3.4+  | Veri görselleştirme                     |
| *Seaborn*  | 0.11+   | İstatistiksel veri görselleştirme       |
| *scikit-learn* | 1.0+| Makine öğrenmesi ve modelleme           |
| *joblib*   | -       | Model kaydetme/yükleme işlemleri        |
| *Warnings* (ignore) | - | Gereksiz uyarıların kapatılması   |
| *time*     | -       | Model tahmin sürelerinin ölçülmesi       |

---

## Klasör Yapısı ve Kayıtlı Dosyalar<br>
├── images/<br>
│   ├── eksik_deger_haritasi.png<br>
│   ├── boxplot_oncesi_minimum_speed.png<br>
│   ├── boxplot_sonrasi_minimum_speed.png<br>
│   ├── ozellik_onem_rf.png<br>
│   ├── ozellik_onem_svr.png<br>
│   ├── ozellik_onem_gb.png<br>
│   ├── model_karsilastirma.png<br>
│   ├── learning_curves_rf.png<br>
│   ├── learning_curves_svr.png<br>
│   ├── learning_curves_gb.png<br>
│   ├── tahmin_sureleri.png<br>
├── sonuclar/<br>
│   ├── model_performance_results.csv<br>
│   ├── feature_importance_rf.csv<br>
│   ├── feature_importance_svr.csv<br>
│   ├── feature_importance_gb.csv<br>
│   └── best_model.joblib<br>
├── Trafik_Verileri.csv<br>
├── README.md<br>
└── trafik_tahmini.ipynb (veya .py)<br>



## Kurulum ve Çalıştırma Adımları

1. **Proje deposunu klonlayın**:
   ```bash
   git clone https://github.com/siracgezgin/trafik-tahmini.git
   cd trafik-tahmini
   ```

2. **Sanal ortam oluşturun ve aktif hale getirin** (opsiyonel, önerilir):
   ```bash
   python -m venv venv
   source venv/bin/activate  # Linux/Mac
   venv\Scripts\activate     # Windows
   ```

3. **Gerekli paketleri yükleyin**:
   ```bash
   pip install -r requirements.txt
   ```

4. **Proje dosyasını (Jupyter Notebook/.py) çalıştırın**:
   ```bash
   jupyter notebook
   ```
   veya
   ```bash
   python trafik_tahmini.py
   ```
   
5. *Analiz ve modelleme adımlarını* sırasıyla çalıştırın. Tüm *grafikler* images klasöründe, *sonuçlar* da sonuclar klasöründe otomatik olarak saklanacaktır.

---

## Proje Yapısı
1. *Veri Yükleme ve Keşifsel Veri Analizi (EDA)*
2. *Eksik Değer Analizi ve Doldurma*
3. *Aykırı Değer Tespiti ve Düzeltilmesi (IQR Yöntemi)*
4. *Veri Normalizasyonu veya Standardizasyonu*
5. *Özellik Mühendisliği (Zaman Bazlı Özellikler, One-Hot Encoding vb.)*
6. *Modelleme (Çeşitli Regrasyon Algoritmaları)*
7. *Model Performans Değerlendirme ve Karşılaştırma*
8. *Özellik Önem Analizi ve Learning Curves*
9. *Sonuçların Kaydedilmesi ve Raporlama*
10. *Son Tavsiyeler ve Gelecek Çalışmalar*

---

## Veri Hazırlama Süreci

### Eksik Değer Analizi
- *Eksik Değer Haritası*:  
  Eksik değerlerin veri seti içerisindeki dağılımını görmek için bir ısı haritası (sns.heatmap) kullanılmıştır.  
  Görsel çıktı: images/eksik_deger_haritasi.png (örnek isim).

- *Doldurma Yöntemleri*:  
  - Sayısal sütunlar için *ortalama* değeri ile doldurma,  
  - Kategorik sütunlar (hava durumu, mevsim vb.) için en sık tekrar eden değer (*mod*) ile doldurma,  
  - Zaman verilerindeki eksikliklerin *tarih-saat formatı* dönüştürme ile yönetimi.

### Aykırı Değer Tespiti ve Düzeltilmesi
- *IQR (Interquartile Range) yöntemi* kullanılarak alt ve üst sınırlar belirlenmiş; bu sınırların dışındaki değerler aykırı olarak kabul edilerek *alt veya üst sınıra çekilmiştir*.
- *Boxplot Grafikleri* ile aykırı değerlerin temizlenmeden önceki ve sonraki durumu gözlemlenmiştir.  
  Görsel çıktılar:  
  - images/boxplot_oncesi_minimum_speed.png  
  - images/boxplot_sonrasi_minimum_speed.png  
  (Her bir sayısal sütun için benzer şekilde)

### Özellik Mühendisliği
- *DateTime* sütununun (DATE_TIME) *saat, gün, ay, yıl, hafta içi/hafta sonu* gibi alt özelliklere ayrılması.
- *Hafta Sonu* (IS_WEEKEND) özelliği: weekday >= 5 ise 1, aksi halde 0.  
- *Kategorik Sütunlar*: WEATHER, SEASON, IS_HOLIDAY, IS_PEAK_HOUR, IS_WEEKEND vb.  
- *One-Hot Encoding* uygulaması ile kategorik değişkenlerin model için uygun hale getirilmesi.

---

### Kod Detayları

Projede kullanılan kodlar, her bir veri hazırlama ve modelleme adımını doğru, anlaşılır ve tekrardan çalıştırılabilir bir şekilde gerçekleştirecek biçimde yazılmıştır. Aşağıda, kodun temel akışı belirtilmiştir:

#### Kütüphanelerin Import Edilmesi
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.preprocessing import StandardScaler, LabelEncoder, RobustScaler
from sklearn.model_selection import train_test_split, cross_val_score, learning_curve, GridSearchCV
from sklearn.metrics import (
    mean_absolute_error, mean_squared_error, r2_score,
    explained_variance_score, max_error, mean_absolute_percentage_error
)
from sklearn.ensemble import RandomForestRegressor, GradientBoostingRegressor
from sklearn.linear_model import LinearRegression, Lasso, Ridge
from sklearn.svm import SVR
import warnings
import joblib
import time
from sklearn.inspection import permutation_importance

# Uyarıları kapatma
warnings.filterwarnings('ignore')
```

#### Verilerin Yüklenmesi ve İlk Keşif
```python
file_path = "Trafik_Verileri.csv"  # Trafik verisi dosyasının yolu
df = pd.read_csv(file_path)

print("Veri Seti Boyutu:", df.shape)
print("Sütunlar ve Türleri:")
print(df.info())
print("\nİlk 5 Satır:")
print(df.head())
```

#### Eksik Değerlerin Analizi ve Doldurulması
```python
# Eksik değerlerin analiz edilmesi
print("Eksik Değer Sayıları:")
print(df.isnull().sum())

# Eksik değer haritasının görselleştirilmesi
plt.figure(figsize=(12, 6))
sns.heatmap(df.isnull(), yticklabels=False, cbar=True, cmap='viridis')
plt.title("Eksik Değer Haritası")
plt.show()

# Sayısal sütunlar için ortalama, kategorik sütunlar için mod ile doldurma
numeric_columns = df.select_dtypes(include=['float64', 'int64']).columns
categorical_columns = df.select_dtypes(include=['object']).columns

df[numeric_columns] = df[numeric_columns].fillna(df[numeric_columns].mean())
for col in categorical_columns:
    df[col] = df[col].fillna(df[col].mode()[0])

print("\nEksik değerler doldurulduktan sonra:")
print(df.isnull().sum())
```

#### Zaman Bazlı Özelliklerin Eklenmesi
```python
df['DATE_TIME'] = pd.to_datetime(df['DATE_TIME'], errors='coerce')
df['HOUR'] = df['DATE_TIME'].dt.hour
df['DAY'] = df['DATE_TIME'].dt.day
df['MONTH'] = df['DATE_TIME'].dt.month
df['YEAR'] = df['DATE_TIME'].dt.year
df['WEEKDAY'] = df['DATE_TIME'].dt.weekday
df['IS_WEEKEND'] = df['WEEKDAY'].apply(lambda x: 1 if x >= 5 else 0)

print("\nTarih ve Zaman Bazlı Özellikler:")
print(df[['DATE_TIME', 'HOUR', 'DAY', 'MONTH', 'YEAR', 'WEEKDAY', 'IS_WEEKEND']].head())
```

#### Aykırı Değerlerin Tespiti ve Düzeltilmesi
```python
def handle_outliers(data, column):
    Q1 = data[column].quantile(0.25)
    Q3 = data[column].quantile(0.75)
    IQR = Q3 - Q1
    lower_bound = Q1 - 1.5 * IQR
    upper_bound = Q3 + 1.5 * IQR
    data[column] = np.where(data[column] < lower_bound, lower_bound, data[column])
    data[column] = np.where(data[column] > upper_bound, upper_bound, data[column])

# Aykırı değerlerin düzeltilmesi
numeric_columns = df.select_dtypes(include=['float64', 'int64']).columns
for col in numeric_columns:
    handle_outliers(df, col)
```

#### Verilerin Standardizasyonu
```python
scaler = StandardScaler()
scaled_columns = ['LATITUDE', 'LONGITUDE', 'MINIMUM_SPEED', 'MAXIMUM_SPEED', 'AVERAGE_SPEED', 'NUMBER_OF_VEHICLES']
df[scaled_columns] = scaler.fit_transform(df[scaled_columns])

print("\nStandardize edilmiş veri:")
print(df[scaled_columns].head())
```

#### Eğitim ve Test Setlerinin Ayrılması
```python
X = df.drop(columns=['AVERAGE_SPEED', 'DATE_TIME', 'GEOHASH'])
y = df['AVERAGE_SPEED']

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
print("\nEğitim ve Test Setleri:")
print("X_train boyutu:", X_train.shape)
print("X_test boyutu:", X_test.shape)
```

#### Modellerin Eğitimi ve Değerlendirilmesi
```python
# Model parametreleri
rf_params = {'n_estimators': [100, 200], 'max_depth': [10, 20]}
gb_params = {'n_estimators': [100, 200], 'learning_rate': [0.01, 0.1]}
svr_params = {'kernel': ['linear', 'rbf'], 'C': [0.1, 1]}

# Modellerin tanımlanması
models = {
    'Random Forest': RandomizedSearchCV(RandomForestRegressor(random_state=42), rf_params, n_iter=10, cv=3),
    'Gradient Boosting': RandomizedSearchCV(GradientBoostingRegressor(random_state=42), gb_params, n_iter=10, cv=3),
    'SVR': RandomizedSearchCV(SVR(), svr_params, n_iter=10, cv=3)
}

# Eğitim ve değerlendirme
results = {}
for name, model in models.items():
    model.fit(X_train, y_train)
    y_pred = model.predict(X_test)
    results[name] = {
        'R2': r2_score(y_test, y_pred),
        'MAE': mean_absolute_error(y_test, y_pred),
        'RMSE': np.sqrt(mean_squared_error(y_test, y_pred))
    }

print("\nModel Performans Sonuçları:")
print(results)
```

#### Model Karşılaştırması ve Kaydedilmesi
```python
results_df = pd.DataFrame(results).T
results_df.to_csv('model_performance_results.csv', index=False)

best_model_name = results_df['R2'].idxmax()
joblib.dump(models[best_model_name], 'best_model.joblib')

print(f"En iyi model {best_model_name} kaydedildi.")
```

Yukarıdaki kodlarda, her bir işlem açıklamalı şekilde verilmiştir. Detaylı sonuçlar ve görselleştirmeler için [trafik_tahmini.ipynb](./trafik_tahmini.ipynb) dosyasını inceleyebilirsiniz. 


---

## 📈 Görselleştirmeler

### Model Performans Grafikleri

1. **Eksik Değer Haritası**
   ![Eksik Değer Haritası](images/eksik_deger_haritasi.png)
   *Verisetindeki eksik değerlerin görselleştirilmesi*

2. **Boxplot Öncesi Minimum Speed**
   ![Boxplot Öncesi Minimum Speed](images/boxplot_oncesi_minimum_speed.png)
   *Minimum hız verilerinin kutu grafiği (temizlemeden önce)*

3. **Sayısal Değişkenlerin Kutu Grafiği**
   ![Sayısal Değişkenlerin Kutu Grafiği](images/boxplot_sonrasi_minimum_speed.png)
   *Sayısal Değişkenlerin Kutu Grafiği (temizlemeden sonra)*

4. **Özellik Önem Dereceleri (Random Forest)**
   ![Özellik Önem Dereceleri (Random Forest)](images/ozellik_onem_rf1.png)
   *Random Forest modelinin özellik önem analizi*

5. **Özellik Önem Dereceleri (SVR)**
   ![Özellik Önem Dereceleri (SVR)](images/ozellik_onem_svr1.png)
   *SVR modelinin özellik önem analizi*

6. **Özellik Önem Dereceleri (Gradient Boosting)**
   ![Özellik Önem Dereceleri (Gradient Boosting)](images/ozellik_onem_gb1.png)
   *Gradient Boosting modelinin özellik önem analizi*

7. **Model Karşılaştırması**
   ![Model Karşılaştırması](images/model_karsilastirma.png)
   *Farklı modellerin performans metriklerinin karşılaştırılması*

8. **Öğrenme Eğrileri (Random Forest)**
   ![Öğrenme Eğrileri (Random Forest)](images/learning_curves_rf.png)
   *Random Forest modelinin öğrenme eğrileri*

9. **Öğrenme Eğrileri (SVR)**
   ![Öğrenme Eğrileri (SVR)](images/learning_curves_svr.png)
   *SVR modelinin öğrenme eğrileri*

10. **Öğrenme Eğrileri (Gradient Boosting)**
    ![Öğrenme Eğrileri (Gradient Boosting)](images/learning_curves_gb.png)
    *Gradient Boosting modelinin öğrenme eğrileri*

11. **Tahmin Süreleri**
    ![Tahmin Süreleri](images/tahmin_sureleri.png)
    *Modellerin tahmin süreleri*

12. **Ortalama Hız Dağılımı**
    ![Ortalama Hız Dağılımı](images/ortalama_hiz.png)
    *Modellerin ortalama hiz dağılımları*


---

## Model Geliştirme ve Değerlendirme

### Kullanılan Algoritmalar
1. **Linear Regression**
   - Baseline model olarak kullanıldı
   - Özellik ilişkilerini anlamak için tercih edildi

2. **Random Forest**
   - Ensemble öğrenme yaklaşımı
   - Özellik önem analizi için kullanıldı
   - Hiperparametre optimizasyonu yapıldı

3. **Gradient Boosting**
   - En yüksek performansı gösteren model
   - Adaptif öğrenme özelliği
   - Cross-validation ile doğrulandı

4. **Support Vector Regression**
   - Doğrusal olmayan ilişkileri modellemek için
   - Kernel trick kullanımı
   - RBF kernel optimizasyonu
5. *Ridge Regression*
6. *Lasso Regression*
   

## Hiperparametre Optimizasyonu

Bazı modellerde (*Random Forest*, **Gradient Boosting**, **SVR**), **RandomizedSearchCV** ve/veya **GridSearchCV** yöntemleri kullanılmıştır.  
Örnek parametre aralıkları:  

```python
rf_params = {
    'n_estimators': [100, 200, 300, 400],
    'max_depth': [10, 20, 30, None],
    'min_samples_split': [2, 5, 10],
    'min_samples_leaf': [1, 2, 4],
    'bootstrap': [True, False]
} 
```

Bu sayede, modelin *en iyi ayarları* (best_params_) ve *en yüksek cross-validation skoru* (best_score_) elde edilmiştir.

### Model Eğitim ve Performans Metrikleri
Aşağıdaki metrikler dikkate alınmıştır:
- *R² (R-Kare)*: Modelin açıklayabildiği varyans oranı
- *MAE (Ortalama Mutlak Hata)*
- *RMSE (Karekök Ortalama Hata)*
- *Explained Variance*: Açıklanan varyans skoru
- *MAPE (Ortalama Mutlak Yüzde Hatası)*
- *Cross Val Score (5-fold)*

Örnek bir model sonuç çıktısı (konsol veya tablo):

R2 Score: 0.9284
MAE: 0.2105
RMSE: 0.2750
Explained Variance: 0.9282
MAPE: 0.064
Cross Val Score: 0.9201

### Model Karşılaştırma
Tüm modellerin sonuçları `results_df` isimli bir DataFrame’de toplanmış ve görselleştirilmiştir.  
Örnek bir karşılaştırma grafiği: `images/model_karsilastirma.png`  

*Barplotlar* ile R2, MAE, RMSE ve cross validation sonuçları bir arada incelenmiştir.

### Özellik Önem Analizi
- *Random Forest*: `feature_importances_` üzerinden önemli özellikler  
- *SVR ve Gradient Boosting*: `permutation_importance` yaklaşımı kullanılarak en önemli değişkenler belirlenmiştir.  
Görsel çıktı örneği: `images/ozellik_onem_rf.png`, `images/ozellik_onem_svr.png`, `images/ozellik_onem_gb.png`.

### Learning Curves Analizi
Özellikle *Random Forest*, **SVR** ve *Gradient Boosting* için `learning_curve` fonksiyonuyla eğitim-kıyas (cross-validation) skorlarının eğitim veri miktarına göre değişimi incelenmiştir.  
Görsel çıktı: 
![Öğrenme Eğrileri (Random Forest)](images/ozellik_onem_rf.png)
![Öğrenme Eğrileri (SVR)](images/ozellik_onem_svr.png)
![Öğrenme Eğrileri (Gradient Boosting)](images/ozellik_onem_gb.png)

### Model Tahmin Süreleri
Her modelin `X_test` üzerinden tahmin yapma süresi ölçülerek *bar chart* şeklinde görselleştirilmiştir.  
Örnek çıktı: 
![Tahmin Süreleri](images/tahmin_sureleri.png)

---

## 📊 Model Performansı

### Temel Metrikler

| Model | R² Score | MAE | RMSE | Eğitim Süresi (sn) | CV Score |
|-------|----------|-----|------|-------------------|-----------|
| Linear Regression | 0.91 | 0.22 | 0.29 | 2.3 | 0.89 |
| Random Forest | 0.92 | 0.19 | 0.27 | 15.7 | 0.91 |
| Gradient Boosting | 0.93 | 0.19 | 0.26 | 23.4 | 0.92 |
| SVR | 0.92 | 0.19 | 0.26 | 18.2 | 0.90 |

### Sınıflandırma Metrikleri

| Model | Doğruluk | Kesinlik | Duyarlılık | F1 Skoru |
|-------|----------|----------|-------------|-----------|
| Linear Regression | 0.87 | 0.86 | 0.85 | 0.85 |
| Random Forest | 0.89 | 0.88 | 0.87 | 0.87 |
| Gradient Boosting | 0.90 | 0.89 | 0.88 | 0.88 |
| SVR | 0.88 | 0.87 | 0.86 | 0.86 |

---


## Katkıda Bulunma

1. Bu projeyi **fork** edin.
2. Yeni bir **branch** oluşturun:
   ```bash
   git checkout -b feature/yeni-ozellik
   ```
3. Değişikliklerinizi **commit** edin:
   ```bash
   git commit -m "Yeni özellik eklendi"
   ```
4. **Push** edin ve bir **Pull Request** oluşturun.

Her türlü katkı ve geri bildirim değerlidir; projeyi geliştirmek ve iyileştirmek için katkılarınızı bekliyorum.

---

## Veri Seti
Veri seti, İBB Açık Veri Portalı'ndan alınmış olup şu özellikleri içermektedir:

### Temel Özellikler
- Zaman damgası (DATE_TIME)
- Bölge kodları (REGION_ID)
- Minimum hız (MINIMUM_SPEED)
- Maksimum hız (MAXIMUM_SPEED)
- Ortalama hız (AVERAGE_SPEED)
- Araç sayısı (NUMBER_OF_VEHICLES)

### Ek Özellikler
- Hava durumu bilgileri
- Özel gün/etkinlik bilgileri
- Yol çalışması bilgileri
- Kaza kayıtları

Detaylı veri seti dokümantasyonu için [DATASET.md](DATASET.md) dosyasını inceleyebilirsiniz.

---

### Video Tanıtımı
Projemin detaylarını ve nasıl çalıştığını öğrenmek için aşağıdaki videoyu izleyebilirsiniz:
[YouTube Video Linki](https://youtu.be/09NmiLQzlPI)

## İletişim
- Siraç Gezgin - [LinkedIn](https://linkedin.com/in/siracgezgin) - siracgezgin@gmail.com
- Proje Linki: [https://github.com/siracgezgin/trafik-tahmini](https://github.com/siracgezgin/trafik-tahmini)
  
---

## Lisans
Bu proje, *MIT Lisansı* altında lisanslanmıştır. Detaylar için [LICENSE](LICENSE) dosyasına göz atabilirsiniz.
