# 🎗️ Breast Cancer Recurrence Prediction with Random Forest

**BLM0463 Veri Madenciliğine Giriş - Dönem Projesi**

Bursa Teknik Üniversitesi | Bilgisayar Mühendisliği | 2025-2026 Bahar Dönemi

---

## 📋 Proje Hakkında

Bu proje, UCI Machine Learning Repository'den alınan **Breast Cancer (Ljubljana)** veri seti üzerinde **Random Forest** sınıflandırma algoritması kullanarak meme kanseri hastalarında **kanserin tekrarlama (recurrence) olasılığını** tahmin etmeyi amaçlamaktadır.

### 🎯 Problem Tanımı

Meme kanseri ameliyatı geçirmiş bir hastanın klinik bulgularına dayanarak, kanserin gelecekte tekrarlayıp tekrarlamayacağını ikili sınıflandırma (binary classification) problemi olarak ele aldık:

- **No-Recurrence Events (0):** Kanser tekrarlamayacak
- **Recurrence Events (1):** Kanser tekrarlayacak

---

## 📊 Veri Seti

- **Kaynak:** [UCI Machine Learning Repository - Breast Cancer (id=14)](https://archive-beta.ics.uci.edu/dataset/14/breast+cancer)
- **Bağışlayan:** Matjaz Zwitter & Milan Soklic, University Medical Centre, Institute of Oncology, Ljubljana, Yugoslavia
- **Örnek Sayısı:** 286
- **Özellik Sayısı:** 9
- **Sınıf Sayısı:** 2 (no-recurrence-events, recurrence-events)
- **Veri Tipi:** Kategorik

### Özellikler

| # | Özellik | Açıklama | Değerler |
|---|---------|----------|----------|
| 1 | `age` | Hastanın yaş aralığı | 20-29, 30-39, ..., 70-79 |
| 2 | `menopause` | Menopoz durumu | lt40, ge40, premeno |
| 3 | `tumor-size` | Tümör boyutu (mm) | 0-4, 5-9, ..., 55-59 |
| 4 | `inv-nodes` | İstilacı lenf düğümü sayısı | 0-2, 3-5, ..., 36-39 |
| 5 | `node-caps` | Lenf düğümü kapsülü | yes, no |
| 6 | `deg-malig` | Kötü huyluluk derecesi | 1, 2, 3 |
| 7 | `breast` | Etkilenen göğüs | left, right |
| 8 | `breast-quad` | Göğsün hangi bölgesi | left-up, left-low, right-up, right-low, central |
| 9 | `irradiat` | Radyoterapi alındı mı | yes, no |

### Sınıf Dağılımı

- **No-Recurrence Events:** 201 örnek (~%70.3)
- **Recurrence Events:** 85 örnek (~%29.7)

---

## 🛠️ Kullanılan Teknolojiler

- **Programlama Dili:** Python 3.12
- **Geliştirme Ortamı:** Visual Studio Code + Jupyter Notebook
- **Kütüphaneler:**
  - `pandas` — Veri işleme
  - `numpy` — Sayısal hesaplamalar
  - `scikit-learn` — Makine öğrenmesi modelleri ve metrikler
  - `matplotlib` — Görselleştirme
  - `seaborn` — İstatistiksel görselleştirme

---

## 🧠 Yöntem

### Sınıflandırma Algoritması: Random Forest

**Random Forest**, çok sayıda karar ağacının (decision tree) birleşiminden oluşan bir **ensemble** öğrenme algoritmasıdır. Her ağaç farklı bir alt örneklem (bootstrap) ve rastgele seçilmiş özellik alt kümesi üzerinde eğitilir. Tahmin aşamasında ağaçların oyları birleştirilerek nihai karar verilir.

#### Random Forest'in Avantajları

- ✅ Aşırı öğrenmeye (overfitting) karşı dirençli
- ✅ Kategorik ve sayısal verilerle iyi çalışır
- ✅ Özellik önem skorları (feature importance) sağlar
- ✅ Eksik değerlere karşı toleranslı
- ✅ Yüksek doğruluk ve genelleme kabiliyeti

### Model Parametreleri

| Parametre | Değer |
|-----------|-------|
| `n_estimators` | 100 |
| `max_depth` | None (sınırsız) |
| `min_samples_split` | 2 |
| `min_samples_leaf` | 1 |
| `random_state` | 42 |

### İş Akışı

1. **Veri Yükleme** → `breast-cancer.data` dosyası okuma
2. **Veri Keşfi** → Eksik değer, sınıf dağılımı, veri tipleri
3. **Ön İşleme** → Eksik değerleri mod ile doldurma
4. **Encoding** → LabelEncoder ile kategorikleri sayısala çevirme
5. **Train-Test Ayrımı** → %80 eğitim, %20 test (stratified)
6. **Model Eğitimi** → Random Forest fit
7. **Tahmin** → Test seti üzerinde predict
8. **Değerlendirme** → Metrikler ve görselleştirme
9. **Çapraz Doğrulama** → 10-fold cross validation
10. **Literatür Karşılaştırması** → Önceki çalışmalarla kıyas

---

## 📈 Sonuçlar

### Test Seti Performansı

| Metrik | Değer |
|--------|-------|
| **Accuracy** | ~%67 |
| **Precision** | ~%43 |
| **Sensitivity (Recall)** | ~%35 |
| **Specificity** | ~%80 |
| **F1-Score** | ~%39 |
| **ROC-AUC** | ~%53 |

> ⚠️ **Not:** Veri setinin dengesiz olması (~%70 - %30) ve örnek sayısının azlığı (286) nedeniyle model özellikle azınlık sınıfta (Recurrence) zorluk çekmektedir. Bu durum literatürdeki diğer çalışmalarda da gözlemlenmektedir.

---

## 📚 Literatür Karşılaştırması

| Yöntem | Accuracy (%) | Kaynak |
|--------|--------------|--------|
| **Random Forest (Bu Çalışma)** | **~67.24** | 2026 |
| Naive Bayes | 73.43 | Lavanya & Usha Rani, 2011 |
| C4.5 Decision Tree | 74.47 | Karabatak & Ince, 2009 |
| SVM | 76.22 | Karabatak & Ince, 2009 |
| Neural Network | 75.26 | Karabatak & Ince, 2009 |

---

## 🚀 Kurulum ve Çalıştırma

### Gereksinimler

```bash
pip install numpy pandas matplotlib seaborn scikit-learn jupyter ipykernel
```

### Çalıştırma

1. Bu repoyu klonlayın:

```bash
git clone https://github.com/[kullanici-adi]/breast-cancer-random-forest.git
cd breast-cancer-random-forest
```

2. `breast-cancer.data` dosyasının proje klasöründe olduğundan emin olun.

3. Jupyter Notebook'u açın:

```bash
jupyter notebook proje.ipynb
```

4. Tüm hücreleri sırayla çalıştırın (**Run All**).

---

## 📁 Proje Yapısı

```
veri_proje/
├── breast-cancer.data              # UCI'dan indirilen veri seti
├── proje.ipynb                     # Ana Jupyter Notebook (analiz + model)
├── proje.py                        # Python script versiyonu
├── README.md                       # Bu dosya
└── BLM463_Proje_Rapor.pdf          # Detaylı proje raporu
```

---

## 📊 Görselleştirmeler

Projede aşağıdaki görseller üretilmiştir:

1. **Confusion Matrix** — Doğru/yanlış sınıflandırma sayıları
2. **ROC Eğrisi** — Modelin ayırt etme yeteneği
3. **Metrik Çubuk Grafiği** — Tüm değerlendirme metrikleri
4. **Özellik Önemi** — Hangi özellik kararı ne kadar etkiliyor
5. **Sınıf Dağılımı** — Veri setindeki sınıf oranları
6. **10-Katlı CV Sonuçları** — Çapraz doğrulama performansı
7. **Korelasyon Matrisi** — Özellikler arası ilişkiler
8. **Literatür Karşılaştırması** — Önceki çalışmalarla kıyas

---

## 📖 Referanslar

1. Zwitter, M., & Soklic, M. (1988). *Breast Cancer Dataset*. UCI Machine Learning Repository.

2. Karabatak, M., & Ince, M. C. (2009). An expert system for detection of breast cancer based on association rules and neural network. *Expert Systems with Applications*, 36(2), 3465-3469.

3. Lavanya, D., & Usha Rani, K. (2011). Analysis of feature selection with classification: Breast cancer datasets. *Indian Journal of Computer Science and Engineering*, 2(5), 756-763.

4. Breiman, L. (2001). Random forests. *Machine Learning*, 45(1), 5-32.

5. Pedregosa, F., et al. (2011). Scikit-learn: Machine learning in Python. *Journal of Machine Learning Research*, 12, 2825-2830.

---

## 👤 Yazar

Furkan BULDUKLU

- 📧 Öğrenci No: 23360859084
- 🏫 Bursa Teknik Üniversitesi - Bilgisayar Mühendisliği
- 📅 2025-2026 Bahar Dönemi

---

