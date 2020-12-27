**Acces Modifiers anahtar kelimeleri nelerdir?** 


Private (Gizli)
Bir değerin private olarak tanımlanması demek, o değişkene sadece kendi class’ı içinden ulaşılabileceği anlamına gelmektedir. Program içinde kesinlikle değiştirilmemesi gereken, kritik kodlarda kullanılmaktadır.
Ayrıca; private, varsayılan erişim belirleyici tipidir. Örneğin; “int deneme = 0;” gibi bir değişken tanımlandığında program tarafından deneme değeri private olarak algılanmaktadır.

Public (Genel)
Bir değerin public olarak belirtilmesi; o değerin, kod içinde herhangi bir yerden erişilebilir durumda olmasını sağlamaktadır. Public erişim belirleyici tipinde hiç bir kısıtlama yoktur.

Protected (Korunumlu)
Kod içinde bir değerin protected olarak tanımlanması; o değere, bulunduğu class  ve ondan türetilen diğer sınıflar içinden erişilebilir olduğunu göstermektedir. Protected; bir anlamda, public ve private erişim belirleyicilerinin birleşimi olarak görülebilmektedir.

Internal (İçsel)
Internal olarak tanımlanan bir değer; aynı program içerisinden erişilebilir, fakat farklı bir program içerisinden erişilemez durumdadır. Program içerisinde herhangi bir kısıtlaması yoktur.

Protected Internal (İçsel Korunumlu)
Protected internal olarak tanımlanmış değer, tanımlandığı class’ın içinden ve ondan türetilen sınıfların içinden erişilebilir durumdadır. Türetilen sınıfın aynı program içinde olmaması sorun teşkil etmez.

**Virtual ile Abstract anahtar kelimelerinin kullanımları arasındaki temel farklar nelerdir?**

virtual anahtar kelimesi, “bu metod ezilebilir” derken,

abstract kelimesi “bu metodu ezilmek zorundadır” der.

metodunun nasıl çalışacağını bu abstract class tan türetilmiş(kalıtımı verilmiş) sınıf belirler. 

Metodun başında abstract olursa, metodun bulundugu class dan kalitim alan bir sinif o metodu override etmek zorundadır, virtual keywordünde ise override edilme zorunuluk değildir. 

Abstract metodlarin gövdesi olmaz, virtualda olmak zorundadır.

**İnterface ve Abstract Class arasındaki farklar nelerdir ?**

Interface ve abstract class’lar new anahtar sözcüğü ile oluşturulamazlar.

Bir sınıf birden fazla interface’i kalıtım olarak alınabilir ama bir sınıfa bir tane abstract class kalıtım alınabilir.

Interface içerisinde boş metodlar tanımlanabilir ama abstract class’larda hem boş metodlar tanımlanabilir hemde içi dolu metodlar tanımlabilir.

Abstract sınıflar içerisinde metod gövdeleri tanımlanıp özellik değerleri ayarlandığı için genellikle sonradan geliştirilmek için kullanılıır ama interface ise body ve değer set edilemediği için tamamen interface üzerinden tüm üyeleri implemente edilerek geliştirmelere yapılması gereken durumlarda kullanılır.

Abstract class’lar içerisinde sadece abstract olarak işaretlenmiş metod ve özellikler implement edilmek zorundadır fakat interface içerisindeki tüm özellik ve metodlar implement edilmek zorundadır.

Bir class bir tane abstract class’ı kalıtım olarak alabilir ama bir class istenilen sayıda interface’i kalıtım olarak alabilir.

Interface içerisinde özellik ve metodlarda erişim belirleyiciler kullanılmaz herşey public olarak kabul edilir fakat abstract sınıflarda kullanılabilir.

Abstract sınıflara diğer sınıf ve interface’ler kalıtım olarak geçilebilir fakat interface’e herhangi bir yapı kalıtım olarak geçilemez.

**SOLID nedir? SOLID başlıklarını kısaca açıklayınız.**

(S)ingle Responsibility Principle(Tek Sorumluluk Prensibi): Her method ve class’ın tek bir sorumluluğu olur örnek olarak database işlemleri yapan bir class içerisinde log’lama işlemlerini yürüten işlemler konulmamalı yada loglama class’ımız var ise bu class içerisinde loglama haricinde başka bir şeylerin dahil edilmemesi gerekiyor ve metod’lardada aynı şekilde switch/case ile yönlendirmemek gerekiyor her metodun tek bir sorumluluğu olmalıdır.

(O)pen/Closed Principle(Açık/Kapalı Prensibi): Değişime kapalı ama geliştirmeye açık şekilde kodlamanın kurgulanması gerekiyor mesela bugün log’lamaları xml’de yapıyorsunuz ama bir karar ile loglamanın artık xml’de değilde database’de yapılması istendi varolan kodlarınızda değişiklik değil güncelleme yapılması gerekiyor misal olarak xml log’laması yapan Single Reponsibility kuralına uymuş olan bir class’ınız var ve bu class ILogger arayüzünden türetilmiş Database loglaması yapacak class’ımızda bu arayüzden türetilip metod içerikleri ona göre yazılır böylelik bu değişiklik değil geliştirme olmuş olur. Kısacası Uygulama gelişime açık, değişime kapalı olmalıdır. Yani yeni eklenen bir modül için kodda gereksiz if blokları gibi değişiklikler olmamalıdır. Bunun yerine kalıtım yoluyla sorun çözülmelidir.

(L)iskov ‘s Substitution Principle(Liskov’un yerine geçme prensibi): Liskov’un yerine geçme prensibi alt sınıflardan oluşturulan nesnelerin üst sınıfların nesneleriyle yer değiştirdiklerinde aynı davranışı göstermek zorunda olduklarını söyler. Yani;türetilen sınıflar, türeyen sınıfların tüm özelliklerini kullanmak zorundadır. Eğer kullanmaz ise ortaya işlevsiz, dummy kodlar çıkacaktır. Bu durumda üst sınıfta if else blokları kullanarak tip kontrolü yapmamız gerekebilir ve böylelikle Açık Kapalı prensibine de ters düşmüş oluruz. Interface Segregation Prinsiple kısmında interface’le üzerinden bu konu anlatılırken burada abstract class’lar üzerindeki kullanımdan bahsediliyor.

(I)nterface Segregation Principle(Arayüz ayrımı prensibi): Bir arayüze gereğinden fazla kullanılmayacak özellik eklenmemelidir. Kullanılabilecek özellikler, metodlar eklenerek kullanılmalıdır.

(D)ependency Inversion Principle(Bağımlılığın ters çevrilmesi prensibi): Bu prensibe göre de bir sınıf diğer bir sınıfa doğrudan bağımlı olmamalıdır. Aralarındaki bağ soyut bir kavram üzerinden sağlanmalıdır. Bu soyut kavram interface de olabilir abstract class da olabilir.

**Static Nedir?**


Bir sınıf(class) içerisinde bulunan metodlar(methods) static olarak tanımlanabilir.
Static olarak tanımlanan bir metodun kullanılabilmesi için tanımlanmış olduğu tipin nesne örneğini oluşturmaya gerek yoktur. Bu durum çoğunlukla bir tipin asıl iş yapan fonksiyonelliklerin kullanılabilmesi için, tüm nesneyi örneklemenin gereksiz olduğu durumlarda ele alınır. 

Bir sınıf içerisinde bulunan alanlar (fields) static olarak tanımlanabilir.
Static metodlar gibi, bir sınıf içerisinde kullanılabilecek static alanlarda tanımlayabiliriz. Bir alanın static olarak tanımlanması halinde bellek üzerindeki yerleşim şeklide bilinmesi gereken noktalardan bir tanesidir.


Static yapıcı metoda ilişkin dikkat edilmesi gereken bir takım kurallar da vardır. Bu kurallara göre;

Static yapıcı metod erişim belirleyicisi (access modifiers) kullanamaz.

Static yapıcı metod parametre alamazlar.

Static yapıcı metod sınıfa ait tüm yapıcılardan önce çalışır.

Static yapıcı metod kaç nesne örneği oluşturulursa oluşturulsun bir kere çalışır.

Bir sınıf sadece bir static yapıcı metod içerebilir.

Static yapıcı metod ya ilk nesne örneği oluşturulduğunda ya da ilk static sınıf üyesi çağırılmadan hemen önce yürütülür.

Static Sınıflar 
1. Eğer nesneye bağlı işlemler geçekleştirmiyorsak yani amaç sadece belirli bir duruma hizmet eden birden fazla öğeyi barındırmak yada bir araya toplamak ise ilgili sınıfı static olarak tanımlamamız olağandır. Bu bağlamda static olarak işaretlenmiş sınıfların üyelelerine instance almadan erişebiliriz. 

2. Static olarak işaretlenmiş sınıflar sadece static üyeler barındırır. !!!!!!!

3. Static sınıflara en güzel örnek File, Math, String sınıflarıdır. Aynı amaca hizmet eden matemetiksel işlemlerin bir araya getirildiği ve tutulduğu sınıftır. Yani static sınıflar ortak bir amaca hizmet eden öğerleri içerisinde barındırırlar ve bu öğelere hızlıca erişebiliriz yani instance almadan erişebiliriz. Bu durumda instance maliyetinden kurtulmuş oluruz. 

4. Static sınıflar başka generic sınıflardan kalıtım almazlar kalıtım vermezler. Ama .Net Framework'ünde bütün sınıflar System.Object nesnesinden kalıtılır, static sınıflar da bu sınıflara dahildir. 

5. Static sınıflar tercih etmek duruma göre değişir. Evet büyük bir esneklik sağlamaktadır. Bizi instance almaktan ve sınıflar arasında bağımlılık kurmaktan kurtarır. Fakat her sınıf static olarak işaretlenmemelidir. Çünkü tanımlanmış her static sınıf size performans ve memory kayıpları olarak yani bir başka değiş ile her zaman göz önünde bulundurmamız gereken konu maliyet olarak geri döner. Buda static olarak tanımlanmış sınıfların içerisinde barındırdırdığımız üyelerin RAM'de tutulma şekli ile ilgilidir. 

**STACK ve HEAP Kavramı nedir?**

Bu iki veri tipi belleğin stack ve heap adlı bölgelerini kullanır. Değer tipleri (int, short, byte, long, decimal, double, float ) Stack’te tutulurken referans tipleri Heap bölgesinde tutulur. Stack Heap’e göre daha hızlıdır.

Stack:
Programımızın içerisindeki basit bir tamsayı türünden nesnenin çalışma zamanında yüklendiği yer RAM’in Stack dediğimiz bölgesidir. Mikroişlemciler yardımı ile veri çekilir ya da yazılır.

Heap: 
Heap’te stack bölgesi gibi RAM’deki hafıza alanıdır. Nesnelerin hepsi Heap’te bulunur ve veriler çalışma zamanında dinamik olarak yaratılırlar yani derleme aşamasında yer tahsis işlemi yapılmaz. Referans tipli değişkenlerin saklandıkları ve değişkene adres bilgisinin gönderildiği yerlerdir.

**Farkları nedir?**

Stack bellekten statik olarak yer tahsisi için kullanılırken, Heap dinamik olarak yer tahsisi içindir. Her ikisi de Ram bölgesinde bulunur.

Stack’te yer alan veriler direk bellek içine yerleştirilir dolayısıyla erişimi çok hızlıdır ve programın derleme aşamasında belleğe yerleşirler. Heap ise runtime(çalışma zamanında) anında kullanılırlar ve dağınık bir bellek göz yapısı olduğu için erişimi stack kadar kolay olmaz dolayısıyla yavaş çalışır. Program esnasında boyutları bildirilmiş, değişmez bir değer kullanacaksak ve buda çok büyük bir veri değilse stack, boyutu belli olmayan bir değer kullanıyorsak (ki nesne yönelimli programlama da bunlara obje denir) o zaman derleyici otomatik olarak Heap’ten yer tahsisi yapar. Stack bellekteki veri hemen silinirken Heap bellekteki verinin silinmesi Garbage Collector’a (Çöp toplama mekanizmasına) bağlıdır. Stack alanı sınırlı olduğundan çok büyük sayıda ve büyük tiplerde veri atanması belleğin dolmasına sebep olabilir.

Değer tipi (Valu Types) tipinden bir değişken tanımladığımızda, daha derleme aşamasında stack bellekten int tipinin bellekte tuttuğu yer kadar (4 byte) yer tahsis edilir ve değişkene değer atanmışsa ilk atanan değer yerleştirilir. Sonra bu değer değişse bile, bu değişkene 4 byte’lık (2^32 bit)’lik bir sayı yerleştirebileceğimiz için çok büyük sayıları bile atayabileceğimiz bir yer tahsis etmiş oluruz. Aşağıdaki örneğe bakacak olursak int tipinden “a” değişkeni tanımlayıp içine 5 sayısını atarsak, stack’te bu değişken için bir yer tahsisi yaptırmış oluruz ve yine int tipinden başka bir değişken tanımlanıp (b) değerini “a” değerine eşitlersek, stack’te bir 4 byte daha yer tahsis yapacak ve a’nın içeriğini kopyalayıp b’ye yazacaktır. Böylece toplam 8 byte’lık yer ayırmış oluruz. Person tipinde p1 adında bir nesne tanımlarsak bu sefer Heap bellekte yer tahsisi yapılacaktır. P2 adında yeni bir personel tanımlanıp p1’e atanırsa bu sefer heap’te bulunan nesne ortak nesne olacaktır.

**LAZY LOADİNG NEDİR? TERSİ NEDİR? NASIL KAPATABİLİRİZ?**
Lazy Loading; datanın ihtiyaç duyulmadığı sürece çağırılmaması, çalıştırılmaması anlamına gelir. Varsayılan olarak açıktır. Tersi Eager(istekli,hevesli) Loading’tir.  Kapatmak için;
  db.Configuration.LazyLoadingEnabled = false;



**.NET Framework ve .NET Core arasındaki fark nedir?**

.NET Framework geleneksel bir .NET platformudur. Bu platform ile konsol, masaüstü web ve mobil uygulamalar geliştirilebilir. Bu uygulamalar sadece Windows işletim sistemi üzerinde çalışır. Doğrudan .NET Framework kullanarak bir uygulama geliştirdiğimizde Framework Class Library adı verilen, içinde tüm bileşenleri barındıran ağır bir kütüphaneyi de kullanmamız zorunludur.

.NET core ise yeni jenerasyon olan, .NET Standart’ı kullanan bir uygulama platformudur. Geleneksel versiyonun dışında bir çok avantaj sağlar.

Bu avantajlardan biri hafif ve modüler olmasıdır. Bu yapıyla sadece ihtiyaç olan modüller kullanılır, gerekmeyen modüller yüklenmez böylece tüm .NET altyapısının tabiri caizse sırtına yüklenmesine gerek kalmaz.

Platform bağımsız olması sebebiyle tüm işletim sistemlerinde çalışır. Windows, Linux ve hatta MacOS’da bile!

Kullandığı yapı ve esneklik sayesinde yüksek performans sağlar. Günümüzde cloud ortamlarında uygulamaların barındırıldığını düşündüğümüzde gereksiz harcamaları azaltır ve tasarruf sağlar.

**Hangi durumlarda .NET Core kullanmak mantıklıdır?**

Çoklu platform bir uygulama yapmamız gerekiyor ve bir kaç farklı işletim sistemi üzerinde çalışacaksa.

Mikroservis mimarisinde uygulamalar geliştireceksek.

Docker containerlar üzerinde uygulama koşturulacaksa.

C# ile makine öğrenmesi uygulamaları geliştirmek istediğinizde.

Ölçeklenebilir, yüksek performans gerektiren ihtiyaçlarda.

Windows, Mac veya Linux’ta çalışan konsol uygulamaları geliştirmek istendiğinde.

Aynı projede çeşitli .NET versiyonlarını kullanmamız gerektiğinde.

Universal Windows 10 uygulamaları geliştirmek istendiğinde.

**ORM (Object Relational Mapping) Nedir?**
ORM; bir ilişkisel veritabanıyla nesneyi bağlamak için metadata (veri hakkında veri, üstbilgi) tanımlayan programlama tekniğidir. Nesne yani kod Java, C# gibi nesne yönelimli programlama(oop) dillerinde yazılır. ORM; ilişkisel veritabanı ve oop arasındaki veri dönüşümünü gerçekleştirir.Yüzeysel olarak bakıcak olursak ORM, yazılım ile veritabanı arasında bir köprü görevi görür.

Nesne tabanlı programlama standartlarına uygun olarak kod yazma imkanı verir.

Minimum SQL bilgisi ile veritabanı işlemleri yapmak imkanı tanır.

Veritabanı platformu bağımlılığı yoktur. Oracle kullanıyorken MSSQL geçişini sorunsuzca gerçekleştirebiliriz.

Ado.net’e karşı daha güvenlidir. Sql Injection gibi bilinen saldırılara karşı güvenlik önlemleri vardır.

Kod yazma süresini kısaltır.

Kod okunabilirliğini arttırır.

Veri modelinizi sadece bir yere yazarsınız ve kodu güncellemek, korumak ve yeniden kullanmak daha kolaydır.

Veritabanı işlemeden Lokalizasyona kadar birçok şey otomatik olarak yapılır .

Sonunda, kodunuzu biraz daha temiz hale getiren MVC kodunu yazmaya zorlar.

**Framework Nedir?** 

Framework bir uygulama çatısıdır biz uygulamamızı o çatıya göre geliştiririz.

Framework, yazılım geliştiricilerin kullandığı önceden hazırlanmış kütüphanelerin bunluduğu ve bunlara yenilerini ekleyebileceği yapıların adıdır. Gelişmiş frameworklerde form kontrolü, veri tabanı bağlantısı, kullanıcı giriş çıkış, mail atma, tema motoru gibi kütüphaneler mevcuttur.

Frameworkler ayrıca MVC (Model, View, Controller) gibi bölümlerden oluşarak projenizin daha okunabilir düzenlenebilir olmasını sağlamaktadır.

Yapılan projelerin çoğunda aradan belirli bir zaman geçtikten sonra düzenlemek zorlaşır. Hem kodların artması hem de yazılan kodun unutulması revize sürecini uzatmakta. Bu yapılar Modelde veritabanı işlemlerini, Controllerda genel mekaniği, Viewda ise görünüm kodu içerdiği için müdahale edilmesi gereken yer tam olarak bulanabilmektedir.

**Framework kullanmak ne gibi kazançlar sağlar?**
Frameworkler temel yapıları en çok kullanılan kütüphaneleri ve modülleri barındırır. Hiç bir framework ana yapısında gelişmiş yapıları içermez. Bunun yerine genişletmek yoluyla projenize uydurulur. Örneğin giriş yaparken genel olarak eposta değişkeni ile giriş yapılır. Siz eğer kullanıcı adı ile giriş yapmak istiyorsanız sadece o fonksiyonu değiştirerek projenizi yazmaya devam edebilirsiniz. Framework kullanmak size bu bağlamda hız katar. Veri tabanı bağlantıları, güvenlik sorunları veya yetkilendirme gibi en temel bölümleri yazmanıza gerek yoktur. Frameworkün ya içinde vardır yada çok kolay bir şekilde dahil edilebilir. Bu sayede tam olarak bitirilmesi 2 ayı bulacak projeler bazen 2-3 hafta da bitebilmektedir. Diğer bir kazancı ise belli standartları olduğu için bu standartlarda geliştirilen projeye yeni takım arkadaşları kolaylıkla entegre olabilir. Bu gibi faydalara rağmen kısıtlanmış ve bazı kriterlerinizde sorun yaşıyorsanız framework kullanmayabilirsiniz.

**Framework ve Library Arasındaki Fark Nedir?**

Library ile Framework ‘ün ayrıştığı nokta teknik kısımdır. İki arasındaki temel teknik fark,  kodun nasıl çağrıldığıdır. Library kullanırken, library size bazı özellikler vererek kullanmanızı sağlar, bu şekilde almış olduğunuzu kodu kendi sisteminize uygularken size kodu nerede ve ne zaman kullanacağınıza karışmaz veya bir diğer deyişle dikte etmez.  Framework ise Library'in tersine  kullanacağız özelliğe göre kodu nerede ve ne zaman kullanacağınız söyler, kullanacağız bu işlev, eğer Framework dokümanın belirtildiği gibi kullanılmaz ise kullanım dışı kalır.
