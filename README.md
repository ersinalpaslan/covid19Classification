# COVID-19 GÖĞÜS RÖNTGEN GÖRÜNTÜLERİNİN DERİN ÖĞRENME İLE SINIFLANDIRILMASI
Bu çalışmada veri seti olarak, kullanıma açık olan COVID-19 röntgen fotoğraflarından oluşan veri seti kullandık.[31] Bu röntgen görüntüleri farklı boyut ve çözünürlüğe sahip olduğundan bunları 299 x 299 olarak yeniden boyutlandırdık. Bu çalışmada DenseNet201, VGG16, ResNet50, InceptionV3 gibi CNN mimarileri üzerinden sınıflandırma yaparak bu modellerin, doğruluk, kesinlik, kayıp, geri çağırma verileri ile kayıp ve doğruluk grafikleri bulunarak karşılaştırma tabloları hazırlanmıştır. Aşağıdaki şekilde modelin mimarisi gösterilmektedir ve adımlar aşağıda açıklanmıştır.
![image](https://user-images.githubusercontent.com/36737805/174456658-772bf7f3-80f5-4d8e-b7f7-ab66e794d905.png)
Adım1: Görüntüleri Elde Etme
COVID-19 ve COVID-19 olmayan hastaların röntgen görüntüleri Kaggle[31] gibi kullanıma açık sitelerden toplandı.
Adım2: Veri Güncelleme
Veri setini yükledikten sonra etiketler çıkartıldı. Tüm görüntüler BGR'den RGB kanallarına dönüştürüldü ve ardından 299 × 299 olarak yeniden boyutlandırıldı.
Adım3: Veri Seti Bölme
Bu adımda veri seti sırayla %70, %20, %10 olmak üzere eğitim, test ve doğrulama olarak 3’e bölündü.
Adım4: Temel Modelin Oluşturulması
VGG16, ResNet50, DenseNet gibi önceden eğitilmiş modelleri kullanarak temel modelimizi oluşturduk.
Adım5: Modelin Derlenmesi
Model,  Adam optimizer ile derlendi. Seçilen öğrenme oranı 0.001.
Adım6: Modelin Eğitilmesi
Model, 1000 COVID-19 negatif ve 904 COVID-19 pozitif röntgen fotoğrafı üzerinden 50 ‘epoch’ ve 32 ‘batch size’ ile eğitildi.
Adım7: Modelin Test Edilmesi
Daha sonra model, veri setinin kalan %20'si(176 adet pozitif ve 200 adet negatif) üzerinde test edildi ve doğruluk, geri çağırma, F1 puanı, özgüllük, duyarlılık vb. için gerekli sonuçlar elde edildi.
# Veri Seti:
Bu çalışmada COVID-19 hastalarına ve normal hastalara ait göğüs röntgen fotoğrafları kullandık. Bu modelde 1000 tanesi normal akciğer ve 904 tanesi COVID-19’dan etkilenen akciğer olmak üzere toplam 1904 göğüs röntgen fotoğrafı kullanıldı. Veri seti eğitim için %70, test için %20 ve onaylama için %10 olarak ayrıldı. Tüm röntgen görüntüleri şekil ve boyut olarak farklı olduğu için  görüntüler 299 × 299 olarak yeniden boyutlandırıldı.

![image](https://user-images.githubusercontent.com/36737805/174456691-a871a279-b1db-48ee-8964-f2a7ce9458f8.png)
# Sonuçlar ve Değerlendirme:
![image](https://user-images.githubusercontent.com/36737805/174456796-36bd0fed-cc27-4e8f-97dc-aeaf1c02c554.png)

Yukarıdaki tablo, COVID-19'u tanımlamada her bir transfer modeli için performans sonuçlarını göstermektedir. Çeşitli modeller farklı sonuçlar verdi, InceptionV3 ve DenseNet201 modelleri ile maksimum doğruluk elde edildi. Karışıklık matrisi yardımı ile diğer ölçerler olan F1-Skoru, duyarlılık ve kesinlik elde edildi.
Kesinlik, model tarafından tahmin edilen toplam pozitiflerin (TP+FP) gerçek pozitiflere olan yüzdesidir. Yani modelin hasta olarak tanımladığı tüm röntgen fotoğraflarının gerçekten hastalıklı olan fotoğraflara oranıdır. Duyarlılık, COVID-19 pozitif olan fotoğrafları doğru tespit etme oranıdır. F-1 Skoru ise kesinlik ve duyarlılık arasındaki harmonik bir ortalamadır. Doğruluk, tüm tahminler arasında doğru yapılan tahminleri belirtir. Yüksek hassaslık(gerçek pozitif oran olarak da bilinir) modelin pozitif bir COVID-19 vakasını ne sıklıkla doğru ve pozitif olarak sınıflandırdığının bir ölçüsüdür. Tüm hasta kişilerin doğru olarak tanımlanabilmesi için modelin yüksek hassaslık vermesi önemlidir. Bir diğer taraftan, yüksek özgüllük, modelin negatif COVID-19 vakalarını ne sıklıkla doğru bir şekilde sınıflandırdığını ölçer.
![dense_confusion](https://user-images.githubusercontent.com/36737805/174456848-51c88e32-ab89-4e2a-b293-f39f2efa1343.png)
![inception_confusion](https://user-images.githubusercontent.com/36737805/174456851-cf0c14b6-473c-43c1-b8e2-666660e4e9b4.png)
![vgg19_confusion](https://user-images.githubusercontent.com/36737805/174456853-749a0d08-7743-44cb-9a5c-f25256e0d5b9.png)
![resnet_confusion](https://user-images.githubusercontent.com/36737805/174456862-54b45097-4196-41d3-a708-9bd218ce8799.png)

Matrisler, Tablodaki performans sonuçlarını hesaplamak için kullanılan 4 farklı modelin karmaşıklık matrislerini göstermektedir. Matrisler, oluşturduğumuz %20’lik test veri setimize dayalı olarak hesaplandı ve değerler kullanılarak kesinlik, duyarlılık, F1-skoru, doğruluk, hassaslık ve özgüllük hesaplandı. Matrisin satırları röntgen fotoğraflarının gerçek değerlerini, matrisin sütunları modelin tahmin ettiği değerleri göstermektedir.

# Sonuçlar ve Öneriler:
Bu çalışma, X-ışını görüntülerinin kullanılarak COVID-19 pozitif ve normal hastaların sınıflandırılmasını ve önceden eğitilmiş dört modelin(VGG19, ResNet50, InceptionV3, DenseNet201) karmaşıklık matrislerinin oluşturulmasını ve kıyaslanmasını içermektedir. En yüksek doğruluk DenseNet201(%89) ve InceptionV3(%89) modellerinden elde edilmiştir. VGG19, %88  ve ResNet50, %65 doğruluk değerleri göstermiştir. InceptionV3, DenseNet201, VGG19 ve ResNet50 modelleri sırasıyla %89, %88, %87 ve %58 F1-skoru açısından performans göstermiştir. Gelecekteki çalışmalarda, röntgen görüntüleri gerekli ön işlem süreçlerine sokularak daha iyi sonuçlar elde edilebilir.



