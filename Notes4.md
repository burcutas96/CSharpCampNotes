# Döngüler
#### Döngüler; tekrar eden yapılanmaları, kodlarımızı, tekrar etmesi gereken programımızı bir koşula, kombinasyona bağlı olarak belirli sayıda tekrarlayabilen, işleyebilen yapılardır.
#### Döngülerde amaç, kodlarımızdaki analitik çözümleri hızlı bir şekilde yapmamızı sağlamaktır.
#### Temelde üç tane döngümüz vardır. Bunlar for döngüsü, while döngüsü ve do while döngüsüdür. (Foreach bir döngü değildir. Foreach bir iterasyondur.)
<br>

* <a href="#which">Hangi döngü nerede kullanılır?</a>
* <a href="#forloop">For döngüsü</a>
* <a href="#whileloop">While döngüsü</a>
* <a href="#dowhileloop">Do While döngüsü</a>
* <a href="#loopwithoutscope">Döngüleri scope'suz kullanma</a>
* <a href="#infiniteloop">Sonsuz döngüler</a>
* <a href="#infiniteforloop">For ile sonsuz döngü</a>
* <a href="#infinitewhileloop">While ile sonsuz döngü</a>
* <a href="#infinitedowhileloop">Do while ile sonsuz döngü</a>
* <a href="#foreach">Foreach bir döngü mü?</a>
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
<br><br>


<h2 id="dowhileloop">III. Do While döngüsü</h2>
<p>While döngüsü, önce şarta bakıp sonra kodu çalıştırırken do while döngüsü önce kodu çalıştırıp daha sonra şarta bakar.</p>
<p>While ile yapılan kontrolde şart true olursa döngü tetiklenecek, false olursa hiçbir zaman tetiklenmeyecektir.</p>
<p>Ancak do wihle döngüsünde şart true'da olsa false'da olsa kod, en az bir kere çalıştırılacaktır.</p>

```c#
do
{
    //....
    
}while(sart)
```
<br><br>


<h2 id="loopwithoutscope">Döngüleri scope'suz kullanma</h2>
<p>Eğer döngülerde tek satırlık bir işlem yapacaksak döngümüzü scope kullanmadan inşa edebiliriz.</p>
<p>- For döngüsü için örnek:</p>

```c#
for (int i = 0; i < 10; i++)
    Console.WriteLine("Gençay");
```
<p>- While döngüsü için örnek:</p>

```c#
while (true)
    Console.WriteLine("Hüseyin");
```
<p>- Do while döngüsü için örnek:</p>

```c#
do
    Console.WriteLine("Hilmi");
while (true);
```
<br><br>


<h2 id="infiniteloop">Sonsuz döngüler</h2>
<p>
Sonsuz döngüler; bazen bizim için farkında olmadan, iradesizce girmiş olduğumuz bir hatayı tarif ederken, bazen de bazı operasyonlarda 
irademizle, kasıtlı bir şekilde kullandığımız bir durumu tarif etmektedir.
</p>
<p>
Bir döngünün kombinasyonunun sonsuza kadar olma ihtimali, durumu varsa o döngü hiçbir zaman sonlanmayacağından dolayı sonsuz kere 
çalışacak yani sonsuz bir döngüye girecektir. İşte bu döngülere sonsuz döngü denilmektedir.
</p>
<br><br>


<h2 id="infiniteforloop">For ile sonsuz döngü</h2>
<p>For ile sonsuz döngü oluştururken dikkat etmemiz gereken bazı noktalar vardır.</p>

```c#
for (int i = 0; true; i++)
{
}
```
<p>
Yukarıdaki örnek her ne kadar sonsuz bir döngü gibi görünse de aslında sonsuz bir döngü değildir. Çünkü başlangıç değişkenimizi birer birer 
arttırdığımız için bu değer bir yerden sonra integer'ın değer aralığını aşacak ve program patlayacaktır. İşte bu yüzden sonlu bir döngü oluşturmuş oluyoruz. 
</p>
<br>
<p>!!! Kritik: Eğer for döngüsü ile sonsuz bir döngü oluşturmak istiyorsak başlangıç değerini ve buna bağlı olarak artış azalış kısmını oluşturmamalıyız.</p>

```c#
for (; true;)   
{
}
```
<p>Yukarıdaki döngü sonsuz bir döngüyü ifade eder. Şart kısmındaki true değerini de yazmadan sonsuz bir döngü oluşturabiliriz.</p>
<p>
For yapılanmasında sonsuz bir döngüye girdiğimizde yapısal olarak bir zamanda sonra çıkmak isteyebiliriz. işte bu çıkma operasyonunu 
manevratik keyword'ler ile de yapabiliriz ya da şartı bir şekilde kontrol edecek bir yapılanma ile de yapabiliriz. Örneğin;
</p>

```c#
bool kosul = true;
for (;kosul;)   
{
    if(true)   //Buraya (true'nun yerine) döngünün sonlaması için bir şart belirtiriz. 
    {
        kosul = !kosul;
    }
}
```
<p>
Döngünün sonlanması için aradığımız durum, koşul her neyse onu if parantezinin içinde belirtiriz. Ve daha sonra döngünün 
sonlanması için döngü içinde kontrol ettiğimiz değişkeni tam tersi değeriyle değiştiririz.
</p>
<br><br>


<h2 id="infinitewhileloop">While ile sonsuz döngü</h2>
<p>
While döngüsü yapısal olarak sonsuz bir döngüye girebilmek için zaten öncelikli bir hazırlığa
sahip olan bir döngüdür. Bu sebeple while döngüsü, fıtrat olarak sonsuz döngüye en yakın döngüdür.
</p>

```c#
while(true)  
{
    //...   
}
```
<p>
While döngüsü ile sonsuz bir döngü yukarıdaki gibi yapılır. Eğer kontrollü bir sonsuz döngü yapmak istiyorsak önceden 
incelediğimiz for ile kontrollü sonsuz döngü yapma işlemindeki mantığı while döngüsünde de kullanırız.
</p>
<br><br>


<h2 id="infinitedowhileloop">Do while ile sonsuz döngü </h2>
<p>Do while ile sonsuz döngü aşağıdaki gibi yapılır.</p>

```c#
do
{
    //...
    
}while(true)  
```
<br><br>


<h2 id="foreach">Foreach bir döngü mü?</h2>
<p>Foreach bir döngü değildir, bir iterasyondur. Peki iterasyon ne demek, döngü'den farkı ne?</p> <br>
<p>Döngü: Belirli bir kombinasyon eşliğinde çalışan, belirli bir şarta bağlı olan, periyodik işlemler gerçekleştiren yapılanmalardır.</p>
<p>
İterasyon: İterasyon mantığında ne kombinasyon ne de şart vardır. İterasyonda; sonraki veri, öteki veri anlamına gelen itere etme fiili vardır.
Bir veri kümesi üzerinde işlem yapmamızı / verileri elde etmemizi sağlayan yapılanmadır. 
</p>
<p>
Aralarındaki ayrı bir fark ise; herhangi bir veri kümesi üzerinde döngü ile dönerken istediğimiz noktadan 
başlayabilirken iterasyonda böyle bir durum söz konusu değildir. İterasyon baştan başlar kümenin sonuna kadar gider.
</p>




