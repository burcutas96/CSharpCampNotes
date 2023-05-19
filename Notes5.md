# Keywordler
#### Keyword dediğimiz yapılanma, derleyici için önceden tanımlanmış ve özel anlamlara sahip olan anahtar sözcüklerdir. Belirli işlemleri, belirli operasyonları gerçekleştirmemizi sağlayan  operasyonel yapılanmalardır.
#### Keywordler programlamanın temel yapı taşlarıdır. En atomik parçalarıdır.
#### Derleyici için ön tanımlı olan, nerede, hangi amaca hizmet edeceği belli olan ve kod içerisinde hangi noktalarda çağrılabileceği, kullanılabileceği kurallarla sınırlandırılmış olan anahtar sözcüklerdir.   
<br>

* <a href="#keywordvsoperator">Keywordlerin operatörlerle ne farkı vardır?</a>
<br><br>


<h2 id="keywordvsoperator">Keywordlerin operatörlerle ne farkı vardır?</h2>
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

<br><br>


<h2 id="breakcommand">Break komutu nedir?</h2>
<p>Sadece switch case, foreach ve döngülerde kullanılabilen bir keyword'dür.</p>
<p>Kullanıldığı yapıdan çıkış yapılmasını, kullanıldığı yapıyı sonlandırmayı sağlayan bir keyword'dür.</p>
<p>Örneğin;</p>

```c#
switch (10)
{
    case 5:
	//...
	break;
    case 10:
	//...
	break;
}
```














