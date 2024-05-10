#  Query string attack (Sorgu dizisi saldırısı)

Web uygulamalarını hedefleyen bir saldırı türüdür. Bu saldırıda, saldırganlar URL'nin sorgu dizisini manipüle ederek hedef web uygulamasına zararlı parametreler enjekte ederler.

Genellikle, web uygulamaları kullanıcı girişi veya veritabanı sorguları gibi işlemler için URL'de parametreler kullanır. Saldırganlar, `bu parametreleri değiştirerek veya zararlı kod ekleyerek web uygulamasının normal işleyişini bozmaya çalışırlar.` Örneğin, bir kullanıcı oturumunu çalmak, yetkilendirme düzeylerini değiştirmek veya veritabanına erişmek için bu yöntemi kullanabilirler.

Özellikle, web uygulamasının sorgu dizisi parametrelerini işlediği alanlarda güvenlik açıkları bulunabilir. Bu açıkları kullanarak saldırganlar, uygulamanın normalde izin verilmeyen işlemleri gerçekleştirmesini sağlayabilirler.

Kullandığımız örnek web sitesinin geliştiricisi, kullanıcıların giriş yaptığı login.php sayfasında, giriş bilgilerini URL'de bulunan parametreler aracılığıyla iletiyor. Bu tür bir zayıflık keşfettiğimizde, parametreleri değiştirerek başka bir hesaba geçiş yapabiliriz. Başka bir hesaba geçtiğimizde, aşağıdaki gibi işlemleri gerçekleştirebiliriz:


https://github.com/yasir723/query-string-attack/assets/111686779/a48faa09-0a5d-435d-851e-a4e776608a37

Videoda, hacker olarak sisteme doğru bir şekilde giriş yaptık. Ancak, dikkatimizi çeken bir şey vardı: Geliştirici, giriş bilgilerini URL parametreleri olarak iletiyordu. Bu durumu fark edince, sistemde "Jena" adında bir kullanıcının hesabının bulunduğunu biliyorduk. Bu nedenle, URL'de parametre olarak bulunan kendi kullanıcı adımızı "Jena" olarak değiştirdik ve böylece sisteme onun hesabı üzerinden giriş yapmış gibi olduk. Onun hesabıyla kendi hesabımıza para transferi gibi işlemler gerçekleştirebildik.


Elbette bu tür büyük zayıflıklarla sık sık karşılaşmayabiliriz, ancak bu tür saldırıları gerçekleştirdiğimizde parametrelerin şifrelenmiş halini görebiliriz. Örneğin, `userName=admin` yerine `userName=benjo` gibi şifrelenmiş bir formda görebiliriz. Her harf bir sonraki harf olarak kaydırılmış gibi görünüyor, yani "a" harfi "b" ile, "b" harfi "c" ile değiştirilmiş gibi. Bu nedenle, şifreleme yöntemini çözmemiz gerekecek. Sunucuya kelimeler gönderip şifrelenmiş hallerini alarak birden fazla örnek elde edebiliriz. onları, şifreleme yöntemini çözmek için kullanabiliriz. Bu şifreleme hakkında bilgi toplamak için [Gathering Information on the Target](https://github.com/yasir723/gathering-Information-on-the-target) saldırısını deneyebiliriz. Ayrıca, parametrelerde değişiklik yaparak sistemde nasıl bir etki yaratacağını gözlemleyebiliriz. Parametrelerde değişiklik yaptığımızda aldığımız hata mesajları bize bilgi sağlayacaktır. Tüm bu bilgiler, sistemde zafiyet bulmamıza ve buna uygun bir saldırı planı oluşturmamıza yardımcı olacaktır.

