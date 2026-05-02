# 🫀 ECG Görüntülerinin Derin Öğrenme ile Sınıflandırılması

![Field](https://img.shields.io/badge/Field-Deep%20Learning-blue)
![Task](https://img.shields.io/badge/Task-Image%20Classification-orange)
![Framework](https://img.shields.io/badge/Framework-TensorFlow%20Keras-red)
![Tech](https://img.shields.io/badge/Tech-Python%20%7C%20OpenCV%20%7C%20Scikit--Learn-informational)
![Models](https://img.shields.io/badge/Models-CNN%20%7C%20Transfer%20Learning-green)
![Evaluation](https://img.shields.io/badge/Metrics-ROC%20AUC%20%7C%20F1--Score-yellow)
![Status](https://img.shields.io/badge/Status-Completed-success)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

---

## 📌 Proje Hakkında

Bu çalışmada, ECG (Elektrokardiyogram) görüntülerinin derin öğrenme ve transfer öğrenme yöntemleri kullanılarak sınıflandırılması amaçlanmıştır. Proje kapsamında farklı CNN tabanlı mimariler ve hibrit modeller eğitilmiş, performansları karşılaştırılmış ve sonuçlar detaylı olarak analiz edilmiştir.

---

## 📌 Amaç

ECG görüntülerini kullanarak bireyleri aşağıdaki sınıflara otomatik olarak ayırabilen bir model geliştirmek:

- Abnormal Heartbeat.  
- History of Myocardial Infarction (MI).  
- Normal Person.  

---

## 📊 Veri Seti

Kullanılan veri seti Mendeley Data platformundan alınmıştır:  
https://data.mendeley.com/datasets/xw9sd3btcs/2  

Veri seti lisans ve boyut kısıtları nedeniyle repoya dahil edilmemiştir. Kullanım için aşağıdaki klasör yapısına yerleştirilmelidir:

dataset/  
└── ECG_Dataset/  
  ├── Abnormal heartbeat/  
  ├── History of MI/  
  └── Normal Person/  

---

## ⚠️ Veri Seti Problemi ve Temizleme Süreci

EDA sürecinde veri setinde ciddi miktarda duplicate (tekrar eden) görüntü tespit edilmiştir. Toplam 707 görüntünün 256 tanesinin tekrar olduğu belirlenmiş ve temizleme sonrası veri seti 451 görüntüye düşmüştür.

Duplicate görüntüler modelin gerçek öğrenme yerine ezberleme yapmasına neden olabileceğinden, proje kapsamında duplicate removal işlemi uygulanmıştır.

Bu işlem sonucunda:

dataset/ECG_Dataset_Clean/

klasörü otomatik olarak oluşturulmakta ve model eğitimleri bu temizlenmiş veri seti üzerinden gerçekleştirilmektedir.

---

## 🔬 Proje Akışı

Notebook aşağıdaki sırayla çalıştırılmalıdır:

EDA → Duplicate Removal → Clean Dataset EDA → Model Training → Model Evaluation.  

Bu sıranın bozulması durumunda model eğitimlerinde hata oluşabilir.

---

## 🧠 Kullanılan Modeller

### Transfer Learning Modelleri
- VGG16.  
- ResNet50V2.  
- DenseNet121.  
- InceptionV3.  
- EfficientNetV2B0.  

### Hibrit Modeller
- DenseNet121 + EfficientNetB0.  
- DenseNet121 + Custom CNN.  
- DenseNet121 + EfficientNetV2 + Attention.  
- ResNet50V2 + InceptionV3.  

Toplamda 9 farklı model eğitilmiş ve karşılaştırılmıştır.

Not: Bağımsız Custom CNN modeli, veri setinin küçük olması nedeniyle güvenilir sonuç vermediği için projeye dahil edilmemiştir. Ancak hibrit model içerisinde kullanılmıştır.

---

## 📈 Değerlendirme Metrikleri

Modeller aşağıdaki metrikler ile değerlendirilmiştir:

- Accuracy & Loss.  
- Precision, Recall, F1-Score.  
- Confusion Matrix.  
- ROC Curve ve AUC.  

Model çıktıları `results/` klasörü altında saklanmaktadır.

---

## 📌 Bulgular

- ResNet50V2 ve DenseNet121 en yüksek performansı göstermiştir.  
- Hibrit modeller, farklı mimarilerin avantajlarını birleştirerek güçlü sonuçlar üretmiştir.  
- History of MI sınıfı, diğer sınıflarla benzerlik gösterdiği için en zor ayrıştırılan sınıf olmuştur.  
- Veri setindeki duplicate görüntüler model performansını doğrudan etkilemektedir.  
- Transfer learning yöntemleri, sınırlı veri setlerinde yüksek başarı sağlamıştır.  

---

## 📁 Proje Yapısı

ECG-DeepLearning-Model-Comparison/  
├── dataset/  
├── notebooks/  
│  └── ECG_Classification_Model_Comparison.ipynb  
├── results/  
│  ├── EDA/  
│  ├── Data_Cleaning_EDA/  
│  └── models/  
├── LICENSE  
└── README.md  

---

## 🚀 Çalıştırma

1. Repoyu klonlayın:  
git clone https://github.com/EmirSafa0/ECG-DeepLearning-Model-Comparison.git  

2. Veri setini indirip uygun klasör yapısına yerleştirin.  

3. Notebook dosyasını açın:  
notebooks/ECG_Classification_Model_Comparison.ipynb  

4. Hücreleri sırayla çalıştırın.  

---

## ⚠️ Önemli Notlar

- Dataset repoya dahil değildir.  
- `ECG_Dataset_Clean` klasörü başlangıçta bulunmaz.  
- Duplicate removal çalıştırıldığında otomatik oluşur.  
- Model eğitiminden önce bu adım çalıştırılmalıdır.  
- `.ipynb_checkpoints` gibi gereksiz dosyalar repoya dahil edilmemelidir.  
- Sonuç görselleri ve metrikler `results/` klasöründedir.  

---

## 📊 Sonuç

Bu çalışma, ECG görüntülerinin derin öğrenme ve transfer öğrenme modelleri ile başarılı şekilde sınıflandırılabileceğini göstermektedir. Özellikle ResNet50V2 ve DenseNet121 modelleri yüksek doğruluk oranları ile öne çıkmıştır. Hibrit modeller ise farklı mimarilerin güçlü yönlerini birleştirerek rekabetçi sonuçlar üretmiştir. Veri kalitesi ve duplicate temizleme süreci, model performansını doğrudan etkileyen kritik faktörlerdir.

---

## 👨‍💻 Geliştirici

Emir Safa KAYMAKÇI  

---

## 📄 Lisans

Bu proje MIT License ile lisanslanmıştır.
