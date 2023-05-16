# Döngüler
#### Döngüler; tekrar eden yapılanmaları, kodlarımızı, tekrar etmesi gereken programımızı bir koşula, kombinasyona bağlı olarak belirli sayıda tekrarlayabilen, işleyebilen yapılardır.
#### Döngülerde amaç, kodlarımızdaki analitik çözümleri hızlı bir şekilde yapmamızı sağlamaktır.
#### Temelde üç tane döngümüz vardır. Bunlar for döngüsü, while döngüsü ve do while döngüsüdür. (Foreach bir döngü değildir. Foreach bir iterasyondur.)
<br>

* <a href="#which">Hangi döngü nerede kullanılır?</a>
* <a href="#forloop">For döngüsü</a>
* <a href="#whileloop">While döngüsü</a>

<br><br>

<h2 id="which">Hangi döngü nerede kullanılır?</h2>
<p>"Hangi döngü nerede kullanılır?" sorusu yanlış bir sorudur. Doğru sorunun "Hangi döngü nereye / hangi senaryoya daha çok yakışır." şeklinde olması gerekiyor.</p>
<p>
  Biz bütün senaryolarla bütün döngüleri kullanabiliriz. Çünkü bu döngülerin hepsi bir kombinasyona bağlı şekilde çalıştıkları için en nihayetinde birbirlerinin yerine kullanılabilirler.
  Ancak hangi senaryoya hangi döngü daha çok yakışıyorsa daha kolay, basit bir şekilde yapılabiliyorsa o döngüyü kullanmamız daha doğru olacaktır.
</p>
<br><br>

<h2 id="forloop">I. For döngüsü</h2>
<p>Prosedürel programlamada, döngü yapılarından birisi for döngüsüdür. Genellikle ardışık işlemlerde kullanılan bir döngü yapılanmasıdır.</p>
<img src="img/Screenshot 2023-05-15 091807.png"/>
<p>
For döngüsündeki üç parametreninde parantezlerin içinde tanımlanması zorunlu değildir. Peki zorunlu değilse neden böyle bir şey oluşturuldu? Çünkü bir algoritma oluşturuyoruz 
ve bu algoritmada kullanılan parametrelerin onun kalıbında, içinde olması kontrol açısından daha kolaylaştırıcıdır. Yani sadece for döngüsünün parametrelerinde kullanacağım 
değişkenleri başka bir yerde oluşturmak yerine tek bir merkezde oluşturup orada yönetmek daha kolay olacaktır.
</p>
<p>- Örnek: Klavyeden girilen sayının faktörüyelini ekrana yazdıran programı yapınız.</p>

```c#
Console.Write("Bir sayı giriniz: ");
int sayi = int.Parse(Console.ReadLine());
int faktoriyel = 1;
string ifade = "";

for (int i = sayi; i > 0; i--) 
{
    faktoriyel *= i;
    ifade += i + (i == 1 ? " = " : " x ");
}
Console.WriteLine("Faktöriyel: " + ifade + faktoriyel);
```
<p>For döngüsü varyasyonu:</p>

```c#
for (int i1 = 0, i2 = 0; i1 < 10 && i2 < 5; i1++ , i2++)
{
    Console.WriteLine("i1'in değeri: " + i1);
    Console.WriteLine("i2'nin değeri: " + i2);
}
```
<br><br>

<h2 id="whileloop">II. While döngüsü</h2>
<p>While döngüsü sadece şarta bağlı bir döngüdür. Şart doğrulandıkça tetiklenir.</p>
<p>While döngüsü, programlamanın ilk tasarlanmış döngüsüdür. For'a kıyasla daha ilkel ve sade bir döngüdür.</p>
<p>For döngüsü olmayan bir dil vardır. Mesela transact sql'de for döngüsü yoktur. Ancak bütün dillerde while döngüsü vardır.</p>
<p>Genellikle sonsuz döngülerde ya da süreci bilinmeyen durumlarda kullanılan bir döngüdür. Ama yine de istediğimiz yerde kullanabiliriz.</p>
<p>- Örnek: Klavyeden girilen sayının faktöriyelini hesaplayalım.</p>

```c#
Console.Write("Bir sayı giriniz: ");
int sayi = int.Parse(Console.ReadLine());
int sonuc = 1;

while(sayi > 0)
{
    sonuc *= sayi--;  //sayinin değerini işleme aldıktan sonra bir azaltacak. Bu yüzden bir alt satırda sayi--; yazmamıza gerek kalmadı.
}
Console.WriteLine(sonuc);
```










