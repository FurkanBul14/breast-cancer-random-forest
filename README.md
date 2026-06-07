# 🎗️ Breast Cancer Recurrence Prediction with Random Forest

**BLM0463 Veri Madenciliğine Giriş - Dönem Projesi**

Bursa Teknik Üniversitesi | Bilgisayar Mühendisliği | 2025-2026 Bahar Dönemi

---

## 📋 Proje Hakkında

Bu proje, UCI Machine Learning Repository'den alınan **Breast Cancer (Ljubljana)** veri seti üzerinde **Random Forest** algoritması kullanarak meme kanseri hastalarında **kanserin tekrarlama (recurrence) olasılığını** tahmin etmeyi amaçlamaktadır.

İkili sınıflandırma problemi:
- **No-Recurrence Events (0):** Kanser tekrarlamayacak
- **Recurrence Events (1):** Kanser tekrarlayacak

---

## 📊 Veri Seti

- **Kaynak:** [UCI ML Repository - Breast Cancer (id=14)](https://archive.ics.uci.edu/dataset/14/breast+cancer)
- **Örnek Sayısı:** 286 | **Özellik Sayısı:** 9 (kategorik)
- **Sınıf Dağılımı:** 201 no-recurrence (~%70) / 85 recurrence (~%30)

**Özellikler:** age, menopause, tumor-size, inv-nodes, node-caps, deg-malig, breast, breast-quad, irradiat

---

## 🛠️ Teknolojiler

- **Dil:** Python 3.12
- **Ortam:** VSCode + Jupyter Notebook
- **Kütüphaneler:** pandas, numpy, scikit-learn, matplotlib, seaborn

---

## 🧠 Yöntem

**Random Forest** (n_estimators=100, random_state=42), %80 eğitim - %20 test bölümü, eksik değerler mod ile dolduruldu, kategorik özellikler LabelEncoder ile sayısallaştırıldı, 10-Katlı Çapraz Doğrulama ile değerlendirildi.

---

## 📈 Sonuçlar

| Metrik | Değer |
|--------|-------|
| Accuracy | %68.97 |
| Precision | %46.67 |
| Sensitivity | %41.18 |
| Specificity | %80.49 |
| F1-Score | %43.75 |
| ROC-AUC | 0.5416 |
| **10-Katlı CV** | **%70.39** |

---

## 📚 Literatür Karşılaştırması

| Yöntem | Accuracy | Kaynak |
|--------|----------|--------|
| **Random Forest (Bu Çalışma)** | **%68.97** | 2026 |
| SimpleLogistic | %75.17 | Mohamed & Khalifah, 2023 (IEEE) |

---

## 🚀 Kurulum ve Çalıştırma

```bash
pip install numpy pandas matplotlib seaborn scikit-learn jupyter ipykernel
git clone https://github.com/FurkanBul14/breast-cancer-random-forest.git
cd breast-cancer-random-forest
jupyter notebook proje.ipynb
```

---

## 📁 Proje Yapısı

```
veri_proje/
├── breast-cancer.data
├── proje.ipynb
├── README.md
└── BLM463_Proje_Rapor.pdf
```

---

## 📖 Referanslar

1. Zwitter, M., & Soklic, M. (1988). *Breast Cancer Dataset*. UCI Machine Learning Repository.
2. Mohamed, T. S., & Khalifah, S. M. (2023). Breast Cancer Prediction: The Classification of Non-Recurrence-Events and Recurrence-Events Using Functions Classifiers. *IEEE Xplore Conference Paper*.
3. Breiman, L. (2001). Random forests. *Machine Learning*, 45(1), 5-32.
4. Pedregosa, F., et al. (2011). Scikit-learn: Machine learning in Python. *JMLR*, 12, 2825-2830.
5. Anthropic. (2026). *Claude (Opus 4.7)* — Kod yazımı, hata ayıklama ve rapor düzenleme.
6. Google. (2026). *Gemini* — Araştırma ve doğrulama.

---

## 👤 Yazar

**Furkan BULDUKLU**
- 📧 Öğrenci No: 23360859084
- 🏫 Bursa Teknik Üniversitesi - Bilgisayar Mühendisliği
- 📅 2025-2026 Bahar Dönemi
