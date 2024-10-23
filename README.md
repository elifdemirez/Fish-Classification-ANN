# Fish Species Classification with Deep Learning

Bu proje, Kaggle'daki [A Large-Scale Fish Dataset](https://www.kaggle.com/datasets/crowww/a-large-scale-fish-dataset) veri setini kullanarak balık türlerini sınıflandırmak için derin öğrenme modellerinin nasıl uygulanacağını göstermektedir. Projede, balık görüntüleri üzerinde bir sınıflandırma modeli geliştirildi ve modelin doğruluğunu çeşitli metriklerle değerlendirildi. 

## Projenin Amacı

Projenin temel amacı, farklı balık türlerini doğru bir şekilde sınıflandırabilen bir model geliştirmektir. Derin öğrenme yöntemleri ve sinir ağları kullanılarak balıkların görüntüleri üzerinden hangi türe ait olduklarını belirlek hedeflendi. Bu sayede, görüntü işleme ve derin öğrenme alanlarında uygulamalı bir çalışma gerçekleştirildi.

## Proje Adımları

### 1. Veri Yükleme ve Keşif

İlk olarak, balık veri setini yükleyip, veri setinin genel yapısı anlanmaya çalışıldı. Veri setinde, her bir balık türü için farklı klasörlerde toplanmış görüntüler vardı. Bu klasörlerdeki her bir görüntü için, balık türünü etiket olarak belirledik ve görsellerin yol bilgilerini kaydettik.

Veri setinde toplam kaç görüntü bulunduğunu ve her balık türünden kaç örnek olduğunu gözlemlendi. Ayrıca eksik verilerin olup olmadığı kontrol edildi. Görüntülerin boyutlandırılması ve normalize edilmesi işlemleri de bu aşamada gerçekleştirildi.

### 2. Görselleştirme ve Veri Analizi

Veri setinde hangi balık türünden kaç adet bulunduğunu bir bar grafiği ile görselleştirildi. Bu adım, veri dağılımını anlamamıza ve dengesiz sınıfların olup olmadığını görmemize yardımcı oldu. Ayrıca, rastgele seçilen birkaç görüntüyü ve etiketlerini görselleştirerek, veri setinin kalitesi kontrol edildi.

Balık türlerinin dağılımını görselleştirerek, sınıf dengesizlikleri olup olmadığı incelendi. Veri setinde bazı sınıfların diğerlerinden daha fazla örneğe sahip olduğu gözlemlendi, bu da eğitim aşamasında dikkat edilmesi gereken bir husustu.

### 3. Veri Ön İşleme

Görüntüler, modele uygun hale getirilmek için 64x64 piksel boyutuna küçültüldü ve her piksel değeri 0 ile 1 arasında normalize edildi. Bu adım, modelin daha hızlı öğrenmesi ve daha iyi sonuçlar vermesi için kritik bir adımdı.

Ayrıca, etiketler (balık türleri) one-hot encoding yöntemi ile dönüştürülerek modele giriş olarak uygun bir hale getirildi. Bu sayede model, balık türlerini çok sınıflı sınıflandırma problemi olarak ele alabilecek hale geldi.

### 4. Modelin Tasarımı

Derin öğrenme modeli olarak bir Sinir Ağı (Neural Network) oluşturuldu. Model, birden fazla tam bağlantılı (Dense) katmandan oluşuyordu. İlk katman olarak `Flatten` ile giriş verisini vektör haline getirip, birkaç tane `Dense` katman kullanarak öğrenmesi sağlandı. ReLU aktivasyon fonksiyonları ve dropout katmanları ekleyerek aşırı öğrenmeyi (overfitting) önleme çalışıldı.

Çıkış katmanında ise softmax aktivasyon fonksiyonu kullanarak, modelin her bir balık türü için olasılık tahmin etmesi sağlandı.

### 5. Modelin Eğitimi

Model, eğitim verisi üzerinde 50 epoch boyunca eğitildi. Eğitim süresince modelin kayıp (loss) ve doğruluk (accuracy) metrikleri izlendi. Eğitim sırasında sınıf dengesizliğini dikkate almak için `class_weight` hesaplamaları yapıldı ve eğitim işlemi dengelenerek modelin tüm sınıfları öğrenebilmesi sağlandı.

### 6. Modelin Değerlendirilmesi

Eğitimin ardından, test verisi üzerinde modelin performansı ölçüldü. Modelin doğruluğunu, eğitim ve test veri setleri için kayıp ve doğruluk grafikleri oluşturarak analiz ettirildi. Bu grafikler, modelin ne kadar iyi öğrenebildiğini ve doğrulama (validation) verisi üzerindeki başarısını gösterdi.

Ek olarak, sınıflandırma raporu (classification report) ve karmaşıklık matrisi (confusion matrix) ile modelin hangi sınıflarda başarılı olduğunu, hangi sınıflarda zorlandığını detaylı bir şekilde incelendi.

## Kaggle Notebook

Tüm kodları ve çıktıları içeren Kaggle notebook dosyasına buradan ulaşabilirsiniz : https://www.kaggle.com/code/elifnurdemirezen/fish-classification-ann
