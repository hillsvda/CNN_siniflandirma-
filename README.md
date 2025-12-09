# Proje 1: Evrişimli Sinir Ağları (CNN) ile Görüntü Sınıflandırma

Bu proje, Makine Öğrenmesi dersi kapsamında, derin öğrenme yöntemleri kullanılarak görüntü sınıflandırma modellerinin geliştirilmesi, eğitilmesi ve performanslarının karşılaştırılması amacıyla hazırlanmıştır.

## 📂 Proje İçeriği ve Dosya Yapısı

Bu klasör, proje kapsamında geliştirilen 3 farklı modeli ve eğitimde kullanılan veri setini içerir:

```text
Proje_1_CNN_Siniflandirma/
│
├── dataset/                # Eğitim ve test için kullanılan görüntüler
│   ├── [Sınıf_1_Adı]/      # Örn: mouse
│   └── [Sınıf_2_Adı]/      # Örn: cüzdan
│
├── model1.ipynb            # Model 1: Temel CNN Modeli
├── model2.ipynb            # Model 2: Veri Artırma (Data Augmentation) Uygulanmış Model
├── model3.ipynb            # Model 3: Transfer Learning (VGG16/ResNet) Modeli
└── README.md               # Proje dökümantasyonu
Proje kapsamında performans artışını gözlemlemek amacıyla adım adım üç farklı yaklaşım uygulanmıştır:

1. Model 1: Temel CNN (Baseline)
Amaç: Sıfırdan basit bir Evrişimli Sinir Ağı (Convolutional Neural Network) mimarisi kurarak temel başarım skorunu elde etmek.

Mimari: Conv2D, MaxPooling2D, Flatten ve Dense katmanlarından oluşan standart yapı.

Sonuç: Veri seti küçük olduğu için bu modelde [Aşırı Öğrenme (Overfitting) gözlemlendi / Düşük başarı elde edildi].

2. Model 2: Veri Artırma (Data Augmentation)
Amaç: Veri setindeki görüntü sayısının azlığından kaynaklanan ezberleme (overfitting) sorununu çözmek.

Yöntem: ImageDataGenerator kullanılarak mevcut görüntüler döndürme, yakınlaştırma ve kaydırma işlemleriyle çoğaltıldı. Dropout katmanları eklendi.

Sonuç: Modelin genelleme yeteneği artırıldı.

3. Model 3: Transfer Learning (Transfer Öğrenme)
Amaç: Çok az veri ile yüksek başarı elde etmek için önceden eğitilmiş (pre-trained) güçlü bir model kullanmak.

Yöntem: ImageNet veri seti üzerinde eğitilmiş [VGG16 / ResNet50 / MobileNet - Hangisini kullandıysan yaz] modelinin ağırlıkları kullanıldı. Son sınıflandırma katmanları kendi veri setimize göre uyarlandı.

Sonuç: En yüksek doğruluk oranı ve en kararlı eğitim bu modelde elde edildi.
