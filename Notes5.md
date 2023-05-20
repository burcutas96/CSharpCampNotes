# Keywordler
#### Keyword dediğimiz yapılanma, derleyici için önceden tanımlanmış ve özel anlamlara sahip olan anahtar sözcüklerdir. Belirli işlemleri, belirli operasyonları gerçekleştirmemizi sağlayan  operasyonel yapılanmalardır.
#### Keywordler programlamanın temel yapı taşlarıdır. En atomik parçalarıdır.
#### Derleyici için ön tanımlı olan, nerede, hangi amaca hizmet edeceği belli olan ve kod içerisinde hangi noktalarda çağrılabileceği, kullanılabileceği kurallarla sınırlandırılmış olan anahtar sözcüklerdir.   
<br><br>


<h2>Keywordlerin operatörlerle ne farkı vardır?</h2>
<p>Operatörler, esas olarak belirli bir operasyonu / eylemi üstlenen yapılardır.</p>
<p>
Keywordler ise daha geniş bir kavramdır. Bir keyword bazen bir operatörü temsil edebilir. 
Örneğin is, typeof keyword'leri; bir keyword'dür ancak operatör işlemi yapan bir keyword'dür. 
<p>
<p>
Yani direkt eyleme, bir fiiliyata odaklanan bir yapılanma varsa bu zaten bir operatördür. Ancak eylem değilde daha 
farklı amaçlara, modellemeye hizmet ediyorsa bu bir keyword'dür. (örneğin static, class keywordleri)
</p>
<p>Bunun için şöyle bir kanıya varabiliriz; Operatörler esasında bir keyword'dür ancak her keyword bir operatör değildir.</p>
<br><br>



# Manevratik komutlar
#### Kodu durdurmak, devamını okumamak, var olan bir döngüden çıkış yapmak yahut komple metodu sonlandırmak için kullanılan komutlardır.
#### Manevratik komutlar, yapamadığımız şeyleri yapmamızı sağlayan komutlar değildir. Yapabileceğimiz manevraları / kodun yönlendirmelerini daha efektif daha profesyonel bir şekilde yapmamızı sağlayan komutlardır.
#### 4 tane manevratik komutlarımız vardır. Bunlar break, continue, return ve goto komutlarıdır.
<br>


* <a href="#breakcommand">Break komutu nedir?</a>
* <a href="#continuecommand">Continue komutu nedir?</a>
* <a href="#returncommand">Return komutu nedir?</a>

<br><br>


<h2 id="breakcommand">Break komutu nedir?</h2>
<p>Döngülerde, switch case ve foreach yapılanmalarında kullanılabilen bir keyword'dür.</p>
<p>Kullanıldığı yapıdan çıkış yapılmasını, kullanıldığı yapıyı sonlandırmayı sağlayan bir keyword'dür.</p>
<p>Örneğin;</p>

```c#
for (int i = 0; i < 100; i++)
{
    if (i == 22)
        break;
    Console.WriteLine(i);
}
```
<br><br>


<h2 id="continuecommand">Continue komutu nedir?</h2>
<p>Sedece döngülerde ve foreach yapılanmasında kullanılabilen, erişilebilen bir keyword'dür.</p>
<p>Amaç: Döngüde bir sonraki tura geçilmesini sağlar. Yani bir sonraki periyoda direkt geçiş sağlar.</p>
<p>Continue komutunun altındaki kodlar çalıştırılmadan bir sonraki döngüye geçilecektir.</p>
<p>- Örneğin, 1 ile 100 arasındaki 7'nin katı olmayan sayıları ekrana yazdıralım.</p>

```c#
for (int i = 1; i <= 100; i++)
{
    if (i % 7 == 0)
        continue;
    Console.WriteLine(i);
}
```
<br><br>


<h2 id="returncommand">Return komutu nedir?</h2>
<p>Metot içerisinde her yerde kullanılabilir, erişilebilir bir keyword'dür. İki işlevi vardır:</p>
<p>1- Nerede çağrılırsa çağrılsın bulunduğu metottan çıkış yapar. Yani metodu sonlandırır.</p>
<p>2- Metotlarda geriye bir değer döndürür.</p>
<br><br>









