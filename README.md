# COVID-19 GÖĞÜS RÖNTGEN GÖRÜNTÜLERİNİN DERİN ÖĞRENME İLE SINIFLANDIRILMASI
Bu çalışmada veri seti olarak, kullanıma açık olan COVID-19 röntgen fotoğraflarından oluşan veri seti kullandık.[31] Bu röntgen görüntüleri farklı boyut ve çözünürlüğe sahip olduğundan bunları 299 x 299 olarak yeniden boyutlandırdık. Bu çalışmada DenseNet201, VGG16, ResNet50, InceptionV3 gibi CNN mimarileri üzerinden sınıflandırma yaparak bu modellerin, doğruluk, kesinlik, kayıp, geri çağırma verileri ile kayıp ve doğruluk grafikleri bulunarak karşılaştırma tabloları hazırlanmıştır. Şekil 4.2.1’de modelin mimarisi gösterilmektedir ve adımlar aşağıda açıklanmıştır.
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
4.3.1 Veri Seti:
Bu çalışmada COVID-19 hastalarına ve normal hastalara ait göğüs röntgen fotoğrafları kullandık. Bu modelde 1000 tanesi normal akciğer ve 904 tanesi COVID-19’dan etkilenen akciğer olmak üzere toplam 1904 göğüs röntgen fotoğrafı kullanıldı. Veri seti eğitim için %70, test için %20 ve onaylama için %10 olarak ayrıldı. Tüm röntgen görüntüleri şekil ve boyut olarak farklı olduğu için  görüntüler 299 × 299 olarak yeniden boyutlandırıldı.
![image](https://user-images.githubusercontent.com/36737805/174456691-a871a279-b1db-48ee-8964-f2a7ce9458f8.png)

4.3.1 Sonuçlar ve Değerlendirme:
![image](https://user-images.githubusercontent.com/36737805/174456701-03953e01-5599-40d4-8823-1957b6d6063f.png)
