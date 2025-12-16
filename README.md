# CNN ve Transfer Learning ile Görüntü Sınıflandırma Projesi 

Bu proje, **Derin Öğrenme (Deep Learning)** yöntemlerini kullanarak kişisel eşyaları (**Cüzdan** ve **Fare**) sınıflandırmak amacıyla geliştirilmiştir. Proje kapsamında üç farklı model mimarisi (Transfer Learning, Temel CNN ve Geliştirilmiş CNN) tasarlanmış, eğitilmiş ve performansları karşılaştırılmıştır.

## Proje Hakkında
Bu çalışmanın temel amacı, kısıtlı bir veri seti üzerinde farklı CNN mimarilerinin performansını analiz etmek ve hiperparametre optimizasyonu ile model başarısını artırmaktır.

Proje 3 aşamadan oluşmaktadır:
1.  **Model 1 (Transfer Learning):** VGG16 mimarisi kullanılarak özellik çıkarımı yapılmıştır.
2.  **Model 2 (Basic CNN):** Sıfırdan basit bir CNN modeli eğitilmiştir.
3.  **Model 3 (Optimized CNN):** Model 2 geliştirilerek, veri artırma (data augmentation) ve hiperparametre optimizasyonu ile en yüksek başarı hedeflenmiştir.

---

# Veri Seti
* **Sınıflar:** Cüzdan (Wallet) ve Fare (Mouse).
* **Görüntü Boyutu:** 64x64 piksel.
* **Kaynak:** Veri seti proje kapsamında özgün olarak oluşturulmuştur.
* **Ön İşleme:** Görüntüler normalize edilmiş (0-1 aralığına çekilmiş) ve yeniden boyutlandırılmıştır.

---

## 🧠 Modeller ve Mimariler

### 1. Model 1: VGG16 (Transfer Learning)
* **Mimari:** ImageNet ağırlıklarıyla eğitilmiş VGG16 modeli kullanıldı.
* **Yöntem:** Konvolüsyon katmanları donduruldu (Frozen Layers), sadece sınıflandırma katmanı eğitildi.
* **Sonuç:** Hızlı eğitim sağladı ancak veri seti boyutu küçük olduğu için %70 civarında başarıda kaldı.

### 2. Model 2: Temel CNN (Baseline)
* **Mimari:** 2 Konvolüsyon Bloğu (32 ve 64 Filtre).
* **Eksiklik:** Model kapasitesi düşük olduğu ve veri artırma uygulanmadığı için "Overfitting" (Ezberleme) sorunları yaşandı veya öğrenme yetersiz kaldı.
* **Başarı:** ~%50 (Rastgele tahmin seviyesi).

### 3. Model 3: Geliştirilmiş CNN  
Model 2 üzerinde şu kritik **hiperparametre değişiklikleri** yapılarak optimize edilmiştir:
* **Filtre Sayısı Artırıldı:** 32, 64 -> **64, 128, 256** (Daha derin özellik çıkarımı).
* **Katman Eklendi:** Model derinleştirildi.
* **Dropout Eklendi:** Ezberlemeyi (Overfitting) önlemek için **0.4** oranında Dropout eklendi.
* **Learning Rate (Öğrenme Oranı):** 0.001 yerine **0.0005** kullanılarak daha hassas öğrenme sağlandı.
* **Data Augmentation:** Veri seti yapay olarak çoğaltıldı (Döndürme, Kaydırma, Aynalama).

---

## 📊 Performans Karşılaştırması

| Model | Mimari Tipi | Doğruluk (Accuracy) | Durum |
| :--- | :--- | :--- | :--- |
| **Model 1** | VGG16 (Transfer Learning) | %70.00 | Orta Başarı |
| **Model 2** | Basit CNN | %50.00 | Başarısız |
| **Model 3** | **Geliştirilmiş CNN** | **%90.00** | En İyi Sonuç  |

---

## 🛠️ Kurulum ve Gereksinimler

Projeyi yerel makinenizde çalıştırmak için aşağıdaki kütüphanelerin yüklü olması gerekmektedir:

```bash
pip install tensorflow keras numpy matplotlib pandas opencv-python
