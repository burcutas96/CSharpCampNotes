* <a href="#typepattern">Type pattern</a>
* <a href="#varpattern">Var pattern</a>
* <a href="#typevarpattern">Type pattern ve var pattern üzerine kritik</a>
* <a href="#patternmatching">C# 9.0 Pattern Matching Enhancements</a>
* <a href="#simpletypepattern">Simple Type Pattern</a>
* <a href="#relationalpattern">Relational Pattern</a>
* <a href="#logicalpattern">Logical Pattern</a>

<br><br>


<h2 id="typepattern">Type pattern</h2>
<p>
Object içerisindeki bir tipin belirlenmesinde kullanılan is operatörünün desenleştirilmiş 
hâlidir. is ile belirlenen türün direkt dönüşümünü sağlar.</p>
<p>
Yani object türüne atanmış herhangi bir değerin türünü tespit
ettikten sonra cast işlemini otomatik yapan bir desendir.
</p>
<p>
--- Normalde, x değişkenine unboxing işlemi uygulamak istiyorsak aşağıdaki işlemi yapmamız gerekirken 
type pattern ile bu işlemi yapmamıza gerek kalmıyor. Type pattern, türü belirlenen veriyi
daha kolay bir şekilde unboxing yapmamızı sağlıyor.
</p>

```c#
object x = "Gençay";
if (x is string)
{
  string name = (string)x;
}
```
<p>
--- Eğer x'in türü string ise ayrıca cast ile uğraşmamıza gerek kalmıyor. Type pattern bizim 
yerimize cast işlemini yapıp x değişkeninin değerini name değişkenine kendi öz türünde atıyor.
</p>

```c#
object x = "Gençay";
if (x is string name)
{
}
```

<p>
!!! Kritik 1: name değişkeni, if scope'unun içinde tanımlanmadığı için class'ın içerisinde 
tanımlanmış kabul edilir. Bu yüzden de başka bir yerde name isimli bir değişken oluşturamayız.
</p>
<br>
<p>
!!! Kritik 2: name değişkeni class'ın içerisinde tanımlanmış kabul edilmesine rağmen if scope'larının 
dışında kullanılmasına izin verilmez. Çünkü x değişkenimiz string olmayabilir, olmazsa da name 
değişkenine null değeri atanır. Yani name değişkeninin null olma ihtimali var. Bu yüzden bu değişkenimize
class içerisinde erişebiliyoruz ama üzerinde herhangi bir işlem yapamıyoruz. (değer vermek hariç)
</p>
<p>
Örneğin aşağıdaki işlemi yapamayız: <br>
Console.WriteLine(name);
</p>
<br><br>


<h2 id="varpattern">Var pattern</h2>
<p>
Var pattern, type pattern'ın bir üst versiyonudur diyebiliriz. Object türüne atanmış bir veriyi type 
pattern ile kendi öz türüne çıkarmak istiyorsak, sorguladığımız tip yerine var keyword'ünü yazabiliriz. 
Böylelikle türü sorgulamamıza gerek kalmıyor. Var keyword'ü verinin türüne bürünüyor. 
</p>

```c#
object x = "Bugün hava yağmurlu";
if (x is var newValue)
{
  Console.WriteLine(newValue);
}
```
<p>
Ama bu pattern'daki türe bürünme işlemi runtime'da oluyor. Dolayısıyla normal var keyword'ü ile 
var pattern'daki var keyword'ü arasında davranış farkı vardır.
</p>
<p>
!!! Normal var keyword'ü: Compiler zamanında türü belirlenecektir. <br>
  var pattern'daki var keyword'ü: Runtime'da türü belirlenecektir.
</p>

```c#
var y = 1236   //Compiler zamanında türü belirlenir.
object x = "Bugün hava yağmurlu";
if (x is var newValue)    //Runtime'da türü belirlenir.
{
  Console.WriteLine(newValue);
}
```
<p>
!!! Bu pattern dynamic keyword'ü ile kullanılamıyor. 
Çünkü böyle bir desen yok. Kullanılması halinde hata alınacaktır.
</p>

```c#
object x = "Bugün hava yağmurlu";
if (x is dynamic newValue)   //Yanlış kullanım
{
  Console.WriteLine(newValue); 
}
```
<br><br>


<h2 id="typevarpattern">Type pattern ve var pattern üzerine kritik</h2>
<p>
Her iki pattern'ı da if bloklarına yazmadan kullanabiliriz. 
</p>

```c#
object x = "Gençay";
bool result1 = x is string m1;
Console.WriteLine(m1);   //Hata alınacak

bool result2 = x is var m2;
Console.WriteLine(m2);
```
<p>
Yukarıdaki örnekte de belirtildiği üzere type pattern ile cast ettiğimiz m1 değişkenini consol'a yazdırmak 
istediğimizde hata fırlatılacaktır. Çünkü x değişkeninin türü string olmayabilir ve string olmadığı durumda
bize null değerini dönderecektir. Bu null dönme ihtimalinden dolayı m1'i dışarıda kullanamayız. 
Bu yüzden type pattern'ı if blokları ile kullanmamız daha doğru olacaktır.
</p>
<br>
<p>
Var pattern'ı uyguladığımız diğer yazdırma işleminde ise bir hata alınmayacaktır. Çünkü var keyword'ü 
x değişkeninin türü hangi tür ise o türe bürünecektir. Dolayısıyla null dönme ihtimali yoktur. 
Bu sebeple de m2 değişkenini consol'a yazdırmak istediğimizde bir hata ile karşılaşılmayacaktır.
</p>
<br><br>


<h2 id="patternmatching">C# 9.0 Pattern Matching Enhancements</h2>
<p>
C# 9.0 sürümü ile gelen pattern'lardır. Bu sürüm ile birlikte gelen 4 tane pattern'ımız vardır.<br>
I. Simple Type Pattern <br>
II. Relational Pattern <br>
III. Logical Pattern <br>
IV. Not Pattern <br>
</p>
<br><br>


<h2 id="simpletypepattern">I. Simple Type Pattern</h2>
<p>
Bir değişken içerisindeki değerin belirli bir türde olup olmadığını hızlı bir şekilde kontrol etmemizi sağlayan desendir.
</p>

<p>
C# 9.0'dan önce type pattern ile yapılan tür bildirimlerinin yanına değişken adı tanımlaması yahut discard 
ifadesinin kullanılması zaruruiydi. C# 9.0 ile bu gereksiz zorunluluk ortadan kaldırıldı ve direkt olarak 
tür kontrol işlemine odaklanılması sağlanmıştır.
</p>

<p>
Aşağıdaki örnekte switch ile beraber type pattern uygulanarak değişkenin türü belirlenmeye çalışılmıştır. Ve değiken, 
belirlenen türde p isimli bir değişkene atanmıştır. Ancak biz p isimli değişkeni herhangi bir yerde kullanmayacaksak simple type 
pattern ile gelen kolaylık sayesinde bu p isimli değişkeni oluşturmamıza gerek kalmıyor.
</p>

```c#
object obj = new Person();
switch (obj)
{
    case Person p:
        //....
        break;
}
```
<p>
Yukarıdaki örneğin simple type pattern kullanılarak çözülmüş hâli:
</p>

```c#
object obj = new Person();
switch (obj)
{
    case Person:
        //....
        break;
}
```
<br>
<p>Başka bir örnek</p>

```c#
string GetProduct(IProduct product) => p switch
{
    Technologic _ => "Teknolojik",
    Computer _ => "Bilgisayar",
    Goggles _ => "Gözlük"
}
```

```c#
string GetProduct(IProduct product) => p switch
{
    Technologic => "Teknolojik",
    Computer => "Bilgisayar",
    Goggles => "Gözlük"
}
```
<br><br>


<h2 id="relationalpattern">II. Relational Pattern</h2>
<p>
Switch özü itibariyle sadece eşitlik durumunu inceleyen bir akış kontrol şemasıydı. Ancak Relational 
pattern sayesinde artık diğer karşılaştırmaları da yapabilmekteyiz. 
</p>
<br>
<p>
Relational pattern; <, >, <=, >= operatörlerini switch'de kullanmamızı 
sağlayan, bu nitelikleri switch'e kazandıran pattern'dır.
</p>
  
```c#
int number = 111;
string result = number switch 
{
    < 50 => "50'den küçük",
    > 50 => "50'den büyük",
    50 => "50'ye eşit"
    _ => "Hiçbiri"
}
```
<h3>If ile Switch arasındaki fark nedir? - (Mülakat Sorusu)</h3>
<p>
If, bütün karşılaştırmaları yapabilmektedir. Switch ise normal şartlarda sadece eşitlik durumuna bakmaktayken C# 9.0
versiyonu ile gelen relational pattern sayesinde diğer kıyaslamaları da yapabilmektedir.
</p>
<br><br>
 







