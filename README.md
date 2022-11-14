
# TODOLİST PROJESİ

 ### Eğitim Notları

###### Kaynak: https://www.udemy.com/course/komple-sifirdan-web-gelistirme-kursu/

projeyi modüler hale getirebilmek için birden fazla js dosyası kullandk.

Adım 1: 
    -film.js de film constructor ı yazarak başlıyoruz. Her filmin bir başlığı yönetmeni ve url(film afiş linki) si olacağı için constructor içine bunları yazdık. bu Constructor ı ana js (project.js) dosyasında kullanacağız. Ancak film ekleme işlemi yapabilmek için önce formu şeçmek gerekiyor

Adım 2: 
    -project js dosyasında formu ıd si ile seçtik. daha sonra 3 tane input alanını da seçtik

Adım 3: 
    -Arayüze filmleri eklemeye çalışacağımız için bir tane ui constructor ına ihtiyacımmız var. UI objesinin prototype in de arayüz işlemlerini yapmaya çalışacağız  bunu da ui.js de oluşturuyoruz. Bu Uı ın bir özelliği olmayacak sadece prototype larına fonksiyonlarımızı yazacağız

Adım 4: 
    -Project.js de UI constructorından ui objesini oluşturduk 
    -tüm eventleri yüklemek için bir event fonksiyonu oluşturduk,
    -seçtiğimiz form için bu foksiyon içinde bir submit eventi oluşturup aşşağıda addFilm() şeklinde fonskiyonumuzu oluşturduk
    -artık seçtiğimiz elementlerin değerlerini almamız gerekiyor. (title - director - url)
    -addFilm fonskiyonu içinde const ile bu değişkenleri aynı isimle tekrar oluşturup seçtiğimiz inputların değerlerini aldık ve aynı zamanda bunlardan biri boşsa hata göstermek için bir if bloğu kullandık
    -eğer inputlar boş değilse else bloğu içinde yeni bir film oluşturmak istiyoruz. Bunun için de else bloğu içinde Film.js deki constructor a göre yeni bir obje oluşturuyoruz (newFilm). Bu objede title, director ve url alıyor.
    -bunları yaptıktan sonra oluşturduğumuz ui objesi üzerinde bir fonksiyon ismi (addFilmToUI) yazacağız ve film objemizi buraya göndererek arayüze eklemeye çalışşacağız. Else bloğu içindeki ui.addFilmToUı(newFilm) bu fonksiyon sayesinde arayüze ekleme yapabiliyoruz.

Adım 5: 
    -ui.js de UI objesinin prototype ine project.js de oluşturduğumuz addFilmToUI fonksiyonunu oluşturduk ve bu fonksiyon yeni bir film eklemesi olduğunda bu filmi arayüze alacak. 
    -newFilm objemizin özelliklerini consolda yazdırdık ve bir sorun olmadığını gördük. Sıra şimdi bu objeyi arayüzde eklemeye geldi

Adım 6:
    -Filmi Arayüze ekleme için html tarafındaki table elementinin tbody sini seçmemiz gerekiyor ve Html tarafındaki yorum kısmına alınmış etiketlerin yapısındaki gibi bir tasarımı ui.js de oluşturup element ekleme işlemini bu şekilde yapacağız
    - Bunu yapabilmek için ui.js içindeki UI objemize bir fonksiyon atadık ve bu fonksiyon çalıştığında bir filmList değişkeni ile seçitiğimiz tbody nin  innerHTML i içine yazdığımız tr ve td ler sayesinde oluşacak ve form input olduğunda arayüze ekleme işlemi böylece gerçekleşecek
    -filmList.innerHTML += şeklinde kullandık.. sadece = kullanırsak bir önceki veriler silicenek bu sebeple 2. eklememizi innerHTml in üzerine yapabilmek için += kullandık.


Adım 7: 
    -Ekleme işlemini yaptıktan sonra inputlarımız dolu şekilde kalıyor bunu da bir fonksiyon yazarak engelleyebiliriz. Bunun için yine ui.js de işlem yapacağız. Arayüz düzenleme işlemlerinin hepsi burada yapılarak arayüz kısmı modüler hale getirilecek.
    -UI constructor ının prototype ına clearInputs fonksiyonunu ekliyoruz. Daha sonra bu fonksiyonnu project.js deki addFilm fonksiyonu içinde çalıştırıyoruzz. gÖNDERDİĞİMİZ PARAMETRELER EŞLEŞTİĞİ İÇİN ekleme işleminden sonra yani form input olduktan sonra text elemanlarının içi boşalıyor.


//ALLERT MESAJI GÖSTERME

Adım 8: 
    Hata ya da bilgilendirme mesajlarımızı yazdırmak için bootstraptan classlara baktık. bu bölümde alert mesajlarını oluşturucaz.
    -Önce ui.js de UI in proto suna displayMessage fonksiyonunu ekliyoruz. fonksiyon parametrelerinde alertin mesajı ve tipi var yani danger mi olacak succses mi vs bunu type argüman göndererek yapıcaz.
    -project.js gelip if bloğu içinde displayMessages fonksiyonumuzu kullanıyoruz.
    -bu aşamadan sonra bir tane div oluşturup bu divi formun altındaki hr nin altına bir child olarak eklememiz gerekiyor. Yani ilk html kısmındaki ilke card-body i seçip altına alert divini eklememiz gerekiyor.
    ui.js deki displayMessages fonskiyonumuzda ilk card-body i seçtik
    -Daha sonra createElement methoduyla div oluşturuyoruz. clasını ve textcontentini verdikten sonra cardbody içine bunu appenchild ile ekliyoruz.
    -allertin belli bir süre sonra arayüzden silinmesini sağlamak için de setTimeout fonksiyonunu kullandık (js e hazır vardı bu)
    -son olarak project.js deki else bloğuna displayMessages fonskiyonunu tekrar yazıp başarılı ekleme durumunda ki mesajı yazdık

    Adım : 9
        -arayüze eklediğimiz filmleri local storageye eklemeye çalışacağız. Bunun için storage.js de Storage isminde bir özelliği olmayan bir constructor  oluşturuyoruz. Bunun da UI gibi bir özelliği olmayacak sadece prototype ine fonksiyonlarımızı ekleyeceğiz.
        -storageye ekeleme işlemini bilgilendirme mesajında önce yapacağız. Bunun için project.js de storage isimli bir obje oluşturuyoruz. bu objeyi de storage de oluşturduğumuz costructor dan oluşturduk.
        -else bloğu içine gelip addFilmToStorage fonksiyonunu oluşturup newfilmi parametre olarak gönderdik.
        -Storage js de constructor ın protosuna bu fonksiyonu oluşturduk
        -Sırada filmi bir array e yazmak ve daha sonra da bu array i local storageye eklemek var.
        -Local Storage de içinde 1-2 film bulunan bir array olabilir bu sebeple ilk başta bunları almamız gerekiyr.
        bunun için bir films değişkeni oluşturduk. films key i local storagede var mı diye kontrol etmemiz gerekiyor. eğer yoksa bize null bir değer geliyordu ve daha sonra keyi biz oluşturuyorduk.
        -local storage ye gönderilen değerler sadece string olabildiği için key kontrolü yaparken getıtem metodnun parantezinde "films" yazarak bunu kontol ediyoruz
        -ELSE bLOĞU İÇİNDE films key i varsa else bloğunda bunu alıp üzerine ekleme yapıyoruz. Ancak local storage sadece string değerler kabul etttiği için ve string olarak değer gönderdiğimiz için buradan aldığımız değerimizi parse edip stringe çevirerek alıyoruz ve array e ekliyoruz.

Adım : 10
    -local storageye ekleme işlemini bir çok yerde yapacağımız için bunu bir fonksiyona çevirmeye kaRar verdik ve hemen aşşağıda Storagenin protosuna getFilmFromstorage fonksiyonunu yazdık ve yorum kısmına aldığımız bölümü bu fonksiyon içine kopyaladık
    -return ile array i mizi döndük
    -getFilmFromStorage fonksiyonu bize bir array dönüyor bizim bu array i addFilmToStorage fonksiyonunda almamamız gerekiyor. bunun için bu fonksiyonda yine block scope de bir let films değişkeni oluşturup this.getFilmsFromStorageden dönen array değerini alıyoruz. Bu array değerini newFilm e push ile ekliyoruz.

Açıklama:
-daha önce arraylerimizin içine string değerlerimizi yazıyorduk ancak şimdi array içine film objelerimizi de yazıyoruz.
{title:"asdds", director:"asdasd", url:"asdda"} şeklinde
    
    -newFilm objesini films array ine attık daha sonra bunu local storage ye göndermemiz gerekiyor. Bu sebeple stringe çevirerek local storageye set ediyoruz.
    burada keye films dedik, value ise films array i 

           
ADIM : 11
    -Sayfayı yenilediğimiz zaman bilgiler siliniyor, sayfa yenilendiğinde local storageden bilgileri alıp arayüzde tekrar göstereceğiz. Böylece sayfa yenilendiğinda bilgiler silinmeyecek.
    -önce project.js ye gelip dökümana DOMContentLoaded eventini ekledik
    -sayfa yenilendiğinde local storageden tüm bilgileri almamız gerekiyor. Bunun storage.js de getFilmFromStorage fonksiyonunda yapıyorduk. Bu fonksiyonu project.js de oluşturduğumuz event içindeki fonksiyonda bir değişken oluşturarak dönen array i alıyoruz.
    -Daha sonra bu array i ui.js içindek bir fonnksiyonuna göndereceğiz. Bu fonksiyonun adı loadAllFilms() şeklinde olacak.
    -ui.js ye geçip UI constructor ının protosuna loadAllFilms fonksiyonunu ekledik ve parametre olarak films array ini buraya gönderdik. Bu fonksiyon film şeklinde bir array alıyor ve bunu arayüzdeki film listesine eklemeye çalışacağız. 
    -Film listesi tbody idi bunun id si "films" ti. loadAllFilms içinde seçiyoruz. films array ini forEach ile dönüp değerleri filmList değişkeninin innerHTML ine += geçen seferki gibi ile ekledik. dolarlı süslü parantezler içindeki
    newFilm yerine film yazdık 

Açıklama: 
    -Bu projenin diğer projelerden farkı projeyi modüllere böldük. Storage işlemlerini storage.js de 
    arayüz işlemlerini ui.js de yapıyoruz. Tepsini tek bir js dosyasında yapmak yerine projeyi bu şekilde modüllere ayırmak hem projenin okunabilirliğini arttırır hem de fonksiyonları yazmak daha rahat olur.

Adım 12: 
    -Bu adımda filmleri arayüzden silmeye çalışacağız. Bunun için event capturing kullanacağız. card body e bir click eventi atayıp bu olayı e.target ile almaya çalışacağız.
    -önce project.js de 2. card body i seçip cardbody değişkenine atadık
    -daha sonca bu cardbody e bir click eventi atadık ve aşşağıda bu eventin deleteFilm şeklinde fonksiyonunu yazdık.
    -bu fonksiyon çalıştığında bardbody içşindeki click hareketini yakalayıp eğer film sil butonuna tıkladıysak cardbody içindeki tüm tr bloğunun silmek istiyoruz. bunun için 2 üst parenta gitmemiz ve tr bloğunu kaldırmamız gerekiyor.
    - if bloğu içinde click eventinin id si a etiketinin yani film sil butonunun id sine eşit ise tıklanmış demektir mantığıyla kurguyu yaptık ve blok içinede  ui.deleteFilmFromUI(e.target) fonksiyonunu yazıp e.target ı ui.js ye gönderdik burada da  
    
    UI.prototype.deleteFilmFromUI = function(element)...
    
    şeklinde foknsiyonu oluşturup UI ın protosuna ekleyeceğiz
    

Adım 13: 
    -Bu bölümde arayüzden sildiğimiz filmleri local storae den de sileceğiz.
    -Filmleri silerken isimlerine göre lacal storageden sileceğiz. bu sebeple önce bu isimleri almamız gerekiyor. 
    -Daha sonra local storage de bu ismi sorgulayaağız, storage ye göndermiş olduğumuz objelerin tittle ı ile isim eşleşirse kaldırma işlemi gerçekleşecek 
    -film sil butonuna basıldığında yukarıda aldığımız e.target bilgisi bir td nin içindeydi burada yapacağımız şey bir üst elemente çıkıp yani td ye gelip title ın bulunduğu kendinden önceki kardeş elementine gidip oradan film isminin bilgisini almak.
    - önce project.js de storage.deleteFilmFromStorage() fonksiyonunu yazdık.
    -daha sonra storage.js de bu fonksiyonu oluşturduk
    -splice metodu arra içinden index değeri vererek bilgi silmeye yarıyordu.
    -silme işlemini yaptıktan sonra bunu local storageye tekrardan yazdırmamız gerekiyor.  localStorage.setItem("films" , JSON.stringify(films)) yazarak tekrar güncelledik.
    -daha sonra project.js içinde deleteFilm() fonksiyonu içinde ui.displayMessage fonskiyonunu yazdırarak silme işlemi başarılı şeklinde alert çıkardık.

Adım 14: 
    -Bu aşamada tüm filmleri hem storageden hem de arayüzden temizleyeceğiz
    -Önce project.js de tüm filmleri temizle yazan butonu id si ile seçiyoruz
    -daha sonra bu butona bir click eventi atıyoruz. event çalıştığında clearAllFilms fonksiyonu çalışacak bu fonksiyonu en alta yazıyoruz
    -ui.js ye gidip bu fonksiyon içinde çalıştıracağımız ve kaldırma işlemlerini yapacak clearAllFilmsFromUI ve fonskiyonunu oluşturuyoruz.
    -storage.js ye gidip clearAllFilmsFromStorage fonskiyonunu oluşturuyoruz.
    -daha sonra project.js ye gidip clearAllFilms fonksiyonu içinde if içinde bir confrim ile kullanıcıya eminmisiniz sorusu çıkartıyoruz. kullanıcı tamam yani true seçim yaparsa blok içi çalışacak. 
    -proje böylece bitti

