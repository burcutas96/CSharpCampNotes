# Hata Kontrol Mekanizmaları
#### 3 tür hata çeşidi vardır. Bunlardan birincisi compiler (derleme) hataları, ikincisi run-time (çalışma zamanı) hataları, üçüncüsü ise logical (mantıksal) hatalardır.

* <a href="#compiler">Compiler Hataları</a>
* <a href="#runtime">Run-Time Hataları</a>
    * <a href="#trycatch">Try-catch mekanizması</a>
    * <a href="#trycatchparameters">Try-catch hata parametreleri</a>
    * <a href="#catch">Peki biz bu hataları nasıl yakalayacağız?</a>
    * <a href="#multiplecatches">Birden çok catch durumu</a>
    * <a href="#finally">Finally bloğu</a>
    * <a href="#when">When keyword'ü ile hata filtreleme</a>
* <a href="#logical">Logical Hatalar</a> 
<br><br>


<h2 id="compiler">I. Compiler Hataları</h2>
<p>- Programlama dili kurallarına aykırı olan syntax hatalarıdır.</p>
<p>- Özellikle gelişmiş editörler (VS) sayesinde söz dizimi hataları derlemeye gerek bile kalmaksızın fark edilebilmektedir.</p>
<p>- Hatanın bulunduğu satır derleyici tarafından rapor edilir. Gelişmiş editörlerde ise hataya nokta atışı yapılarak hatanın nerde olduğunu bize direkt söyler.</p>
<p>Örneğin;</p>
<img src="img/syntaxerror3.png"/>
<img src="img/syntaxerror2.png"/>
<img src="img/syntaxerror1.png"/>
<br><br>


<h2 id="runtime">II. Run-Time Hataları</h2>
<p>- Syntax'da bir promlem yok, kodun semantiği kusursuz ama çalışma zamanında patlamaya sebep veren hatalardır.</p>
<p>- Yazılım ayaktayken ortaya çıkan bir takım aykırı durumlardan dolayı programın işletim sistemi tarafından kesilmesiyle/sonlandırılmasıyla sonuçlanır.</p>
<p>- Çalışma zamanı hataları programın işleyişinin ortasında direkt kullanıcıyla temas edebilecek hatalardır. Ve hiçbir yazılımcı son kullanıcının hatayla 
karşılaşmasını istemez.</p>
<p>- Bu yüzden çalışma zamanında alınabilecek "olası" hataları yönetmemiz ve onları bir şekilde manipüle etmemiz gerekmektedir.</p>
<p>- Çalışma zamanı hataları genellikle kullanılan mimaride öntanımlı mesajları verecektir.</p>
<p>- Hata kontrol mekanizmaları çalışma zamanı hatalarını kullanıcıya hissettirmeden yakalayabilmek ve ilgili hatayı manipüle edebilmek için vardır.</p>
<br>

* <h3 id="trycatch">Try-catch mekanizması</h3> 
<p>Run-time'da alınan hataları manipüle etmemizi / karşılamamızı / kontrol etmemizi sağlayan programatik bir yapıdır.</p>
<p>Try-catch yapılanması, uygulama sürecinde yaşanan hatayı kullanıcıya hissettirmeksizin farklı bir durum ya da olağan bir mesaj gibi göstermemizi sağlayan 
ve bunun yanında patlamaya / hataya dair bizlere bilgi sunan ve bu bilgiler eşliğinde kayıt dosyaları / kayıtlar oluşturmamızı sağlayan bir mekanizmadır. 
</p>
<p> Amaç;</p>
<p> * Alınan hatayı, kullanıcıya hissettirmemek</p>
<p> * Alınan hatanın nedenine dair kullanıcıyı bilgilendirmek</p>
<p> * İşletim sistemleri aykırı durum yaşandığında uygulamayı sonlandırmak isterler ve sonlandırırlar. Try-catch yapılanması ile alınan hataya dair
manipülasyon gerçekleştirilir ve uygulamanın kapanmadan devam etmesi sağlanır.  
</p>
<p>Prototip:</p>

```c#
try
{
    //olası çalışma zamanı hatalarını barındıran / hata verebilecek kodları buraya yazıyoruz. 
}
catch
{
    //try içerisinde olası hata söz konusu olursa kodun akışı orada kesilecek ve akış, bu bloktan devam edecektir. 
}
```
<p>Try-catch yapılanması, bir hatanın fırlatılabileceği kodları durmadan kontrol eden maliyetli bir yapıdır. Dolayısıyla try içerisindeki kodlar, 
lüzumsuz kodlar olmamalıdır.</p>
<p>Sadece hata verebilecek kodları barındıran bir yaklaşım sergilememiz kontrol maliyeti açısından daha verimli ve  performanslı olacaktır.</p>
<br>

* <h3 id="trycatchparameters">Try-catch hata parametreleri</h3>  
<p>Çalışma zamanında alınan hataya dair bizlere bilgi veren / taşıyan parametrelerdir.</p>
<p>- Örneğin aşağıdaki işlemde 10 sayısını sıfıra böldüğümüz için program çalıştırıldığında bize "DivideByZeroException" hatası fırlatılacaktır.</p>

```c#
int sayi1 = 0, sayi2 = 10;
int sonuc = sayi2 / sayi1;
```
<p>- Bir başka örnek; değeri null olan bir değişken üzerinde işlem yapmaya çalışırsak "NullReferenceException" hatasını alırız.</p>

```c#
object x = null;
x.ToString(); 
```
<p>- Bir başka örnek; eğer metinsel bir ifade sayısal bir ifadenin formatına uygun değilse ve bu ifadeyi sayısal bir ifadeye dönüştürmek istersek
"FormatException" hatasını alırız.</p>

```c#
int.Parse("gençay");
```
<p>Biz bu hataları runtime'da editör üzerinde görebiliriz. Alınan hatanın yapısına, fıtratına göre hata türü fırlatılacaktır. Örneğin FormatException 
 hatası aldığımız / karşılaştığımız hatanın türünü ifade etmektedir.
</p>
<br>

* <h3 id="catch">Peki biz bu hataları nasıl yakalayacağız?</h3>
<p>Try-catch yapılanmasında try bloğunda hata alınması durumunda, hatayı catch bloğu karşılıyordu. Haliyle hangi hata bilgisi olduğunu bize taşıyacak, 
bize getirecek olan blok; catch bloğudur.
</p>
<p>Cath parantezinde Exception türünde bir parametre oluşturarak, alınan hataya dair bilgiler edinebilmekte ve gerekli operasyonları gerçekleştirebilmekteyiz.
</p>
<p>Ancak bu parametre tanımlanmak, oluşturulmak zorunda değildir. Eğer ki tanımlama yapılmazsa hata neticesinde catch bloğu çalışacak lakin hatayla ilgili 
bilgi alınmayacaktır.
</p>
<p>Exception türü: Bizlere fırlatılan hatayla ilgili tüm bilgileri getiren üst bir türdür.</p>

```c# 
try
{
    int.Parse("gençay");
}
catch (Exception exception)
{
    Console.WriteLine("Hata Mesajı: " + exception.Message);
}
```
<br>
<p>Catch parantezinde Exception türü yerine daha özelleştirilmiş hata türlerinde parametre oluşturabiliriz. Ancak böyle bir durumda sadece o türdeki hatayla 
ilgili bilgiler alabilliriz.</p>

```c# 
try
{
    int sayi1 = 0, sayi2 = 10;
    int sonuc = sayi2 / sayi1;
}
catch (DivideByZeroException exception)
{
    Console.WriteLine("Hata Mesajı: " + exception.Message);
}
```
<p>Eğer bu türün dışında farklı bir hata türü fırlatılırsa try-catch bloğu ilgili hatayı manipüle etmeyecek ve fiziksel olarak uygulamayı patlatıp sonlandıracaktır.</p>
<br>

* <h3 id="multiplecatches">Birden çok catch durumu</h3>
<p>Bir try-catch yapılanmasında neden birden fazla catch durumuna ihtiyaç duyulur? Çünkü try bloğunun içerisindeki kodlar çalışma zamanında birbirinden farklı hata türü
fırlatabilir. Bu yüzden her hata için ayrı bir catch bloğu oluştururuz.
</p>

```c# 
try
{
    int sayi1 = 0, sayi2 = 10;
    int sonuc = sayi2 / sayi1;   //DivideByZeroException hatasını fırlatacak.
    
    int.Parse("gençay");        //FormatException hatasını fırlatacak.
}
catch (Exception exception)
{
    Console.WriteLine("Hata Mesajı: " + exception.Message);
}
```
<p>Yukarıdaki örnekte, catch bloğu her iki hatada da aynı davranışı sergileyecektir. Dolayısıyla farklı türlerdeki hata durumlarında bir fark yaratamayız.
Eğer fark yaratmak istiyorsak, DivideByZeroException hatasında başka bir catch bloğunu FormatException hatasında başka bir catch bloğunu çalıştırmak istiyorsak
aşağıdaki örnekte olduğu gibi her hataya özel birden fazla catch bloğu oluşturmalıyız. 
</p>

```c# 
try
{
    int sayi1 = 0, sayi2 = 10;
    int sonuc = sayi2 / sayi1;   //DivideByZeroException hatasını fırlatacak.
    
    int.Parse("gençay");        //FormatException hatasını fırlatacak.
}
catch (DivideByZeroException exception)
{
}
catch (FormatException exception)
{
}
```
<p>- Catch bloklarının en sonunda Exception türünde catch bloğu oluşturulursa, alınan hata üstteki türlerden herhangi biri değilse Exception bloğundaki
kodlar kesinlikle çalıştırılacaktır.
</p>

```c# 
try
{
    int sayi1 = 0, sayi2 = 10;
    int sonuc = sayi2 / sayi1;  
    
    int.Parse("gençay");        
}
catch (DivideByZeroException exception)
{
}
catch (FormatException exception)
{
}
catch (Exception exception)
{
}
```
<p>!!! Kritik: Try-catch yapılanmasında hata alındığında hata, catch sıralamasına göre kontrol edilmektedir. Bu sıralama önemlidir. Bu yüzden birden fazla catch bloğu 
tanımlanmasında Exception türü de kullanılacaksa yukarıdaki örnekteki gibi Exception'ın en sonda tanımlanması gerekmektedir. Aksi taktirde compiler hata verecektir. 
</p>
<p>!!! Exception türünün en sonda tanımlanmasının bir başka sebebi ise; Exception türü, bütün hata türlerini karşılayabildiği için diğer catch'lere / türlere 
bakma gereği duymamasıdır.
</p>
<br>

* <h3 id="finally">Finally bloğu</h3>
<p>Finally bloğu try-catch yapılanmasında hata alınsada alınmasada her iki durumda da tetiklenmesi / çalıştırılması gereken kodları yazdığımız bloktur.</p>

```c# 
try
{
}
catch (Exception exception)
{
}
finally
{
}
```
<br>

* <h3 id="when">When keyword'ü ile hata filtreleme</h3>
<p>Try-catch bloklarına when keyword'ü ile şart uygulayabilmekteyiz.</p>
<p>Hem türün hem de şartın sağlanması durumunda ilgili catch bloğu çalıştırılacaktır.</p>

```c# 
try
{
    int sayi1 = 0, sayi2 = 10;
    int sonuc = sayi2 / sayi1;  
}
catch (DivideByZeroException exception) when (3 == 3)
{
}
catch (DivideByZeroException exception) when (5 == 5)
{
}
```
<p>Catch parantezinin içindeki hatanın türünü bildirmek zorunda değiliz. Yani catch parantezini oluşturmadan da when şartını oluşturabiliriz.</p>
<p>Farklı bir kullanım şekli:</p>

```c# 
try
{
    int.Parse("gençay");  
}
catch(Exception ex) when (ex is FormatException or NullReferenceException)
{
    //FormatException ve NullReferenceException hata türleri için çalıştırılacak ortak kodlar.
}
```
<br><br>


<h2 id="compiler">III. Logical Hatalar</h2>
<p>- Programın mantığında, akışında, algoritmasında, stratejisinde birtakım şeylerin yanlış hesaplanması, düşünülmesi, tasarlanması neticesinde alınan hatalardır.</p>

<p>- Syntax'ta, kodun derlenmesinde hatta çalışma zamanında bir hata yoktur. Kod çalışır ve sonuç verir lakin sonuçlar hatalıdır. Beklenen sonuçlar elde edilmez.</p>

<p>- Mantıksal hatalar ancak test süreçlerinde yahut müşteri kullanımında tespit edilebilir.</p>

<p>- Bazen hesaplanması gereken bir değerin eksik hesaplanmasıyla, bazen yanlış katsayının kullanılmasıyla, bazen de mantıksal işlemde yapılan bir hatayla ortaya çıkabilir.</p>

<p>- Günlük hayattaki karşılığı "bug"dur. Bug terimi, mantık hataları için kullanılan bir terimdir.</p>

<p>- Tespiti çok zor olduğu için hata türleri arasındaki en tehlikeli hatadır. Çünkü hatayı bulmak adına bir derleyici ya da editör size yardımcı olmuyor. Her şey bilgisayar 
açısından normal ancak sonuçlar beklediğimiz şekilde üretilmiyor. 
</p>

<p>- Mantıksal hatalarda bazen tek çözüm debug'dır.</p>

<p>Örneğin; projemizde iki sayının aritmetik ortalamasını almak istiyoruz.</p>

```c# 
int i1 = 15, i2 = 25;
Console.WriteLine(i1 + i2);
```
<p>
Yukarıdaki gibi bir işlem yaparsak eğer derlemede veya çalışma zamanında bir hata almayacağız ancak işlem sonucunda yanlış bir hesaplama yapıldığını fark etmiş olucaz.
Çünkü biz, amacımızı doğru bir şekilde karşılayabilen bir kodlama yapmadık. İki sayının sadece toplamını ekrana yazdırdık ancak bizim istediğimiz iki sayının aritmetik ortalamasını bulmaktı. Bu yüzden bu işlemde mantıksal bir hata yapmış olduk.
</p>






