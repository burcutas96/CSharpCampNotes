# Hata Kontrol Mekanizmaları
#### 3 tür hata çeşidi vardır. Bunlardan birincisi compiler (derleme) hataları, ikincisi run-time (çalışma zamanı) hataları, üçüncüsü ise logical (mantıksal) hatalardır.

* <a href="#compiler">Compiler Hataları</a>
* <a href="#runtime">Run-Time Hataları</a>
    * <a href="#trycatch">Try-catch mekanizması</a>
    * <a href="#trycatchparameters">Try-catch hata parametreleri</a>
    * <a href="#catch">Peki biz bu hataları nasıl yakalayacağız?</a>
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


* <h3 id="trycatchparameters">Try-catch hata parametreleri</h3>  
<p>Çalışma zamanında alınan hataya dair bizlere bilgi veren / taşıyan parametrelerdir.</p>
<p>- Örneğin aşağıdaki işlemde 10 sayısını sıfıra böldüğümüz için program çalıştırıldığında bize "DivideByZeroException" hatası fırlatılacaktır.</p>

```c#
int sayi1 = 0, sayi2 = 10;
int sonuc = sayi1 / sayi2;
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


* <h3 id="catch">Peki biz bu hataları nasıl yakalayacağız?</h3>
<p>try-catch yapılanmasında try bloğunda hata alınması durumunda, hatayı catch bloğu karşılıyordu. Haliyle hangi hata bilgisi olduğunu bize taşıyacak, 
bize getirecek olan blok; catch bloğudur.
</p>
<p>cath parantezinde Exception türünde bir parametre oluşturarak, alınan hataya dair bilgiler edinebilmekte ve gerekli operasyonları gerçekleştirebilmekteyiz.
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
















