# String Türü Nedir?
#### String, programlama dilinde referans türlü olduğu halde bir keyword olan tek değerdir.
#### Referans türlü değişkenlerde, sadece string değişkeni bir keyword'dür. String haricindeki tüm referans türlü değişkenlerin bir keyword'ü yoktur. Yani keyword değildirler.

* <a href="#nullvsempty">Null ve empty farkı</a>
* <a href="#nullvsemptyimportant">Null ve empty arasındaki önemli fark!</a>
* <a href="#isnullorempty">IsNullOrEmpty() Fonksiyonu</a>
* <a href="#isnullorwhitespace">IsNullOrWhiteSpace() Fonksiyonu</a>
* <a href="#string">String neden referans türlüdür?</a>
* <a href="#arraysegment1">Array segment nedir?</a>
* <a href="#arraysegment2">Array segment nasıl oluşturulur?</a>
<br><br>


<h2 id="nullvsempty">Null ve empty farkı</h2>
<h3>Null</h3>
<p>
Nullable değişkene veya referans türlü bir değişkene eğer ki null atanmışsa, bu durum ilgili değişkenin 
herhangi bir alanı tahsis etmediği anlamına gelir. Hem kapladığı bir alan yoktur hem de değeri yoktur.
Belleğimiz 100 birimlik bir bellekse yine 100 birim olarak kalır.
</p>
<p> ! Null alan değişkenlerde arsa da yok ev de yok.</p>

```c#
string x = null;
```
<p>
Örneğin yukarıdaki x değişkeni stack'te oluşturuluyor, tanımlanıyor ancak x değişkeninin 
heap'te bir karşılığı yok. Herhangi bir değeri referans etmiyor.
</p>
<p>
Değer türlü değişkenlere null değerini atayabilmemiz için nullable (?) operatörünü kullanmamız gerekiyor. Çünkü değer 
türlü değişkenler null alamıyor. En kötü ihtimalle default değerlerini atamak zorundayız. Aksi taktirde hata alırız.
</p>

```c#
int? a = null;
char? b = null; 
```
<br>

<h3>Empty</h3>
<p>
Nullable değişkene veya referans türlü bir değişkene eğer ki empty atanmışsa, bu değişkenin bellekte 
kapladığı bir alan vardır, alan tahsisinde bulunulmuştur ancak değeri yoktur.
Belleğimiz 100 birimlik bir bellekse atıyorum 98 birimlik alana düşer. 
</p>
<p>! Empty değişkenlerde arsa var ama ev yok. </p>
<p>Tüm değerlere empty atanabilir. Alan tahsisinde bulunulduktan sonra ilgili alana bir değer koymamak empty durumudur.</p>
<p>Örneğin;</p>

```c#
int a = 0;
bool b = false;
double[] x = new double[55]; 
```
<p>Default değerlerin olduğu durumlar empty olarak kabul edilir.</p>
<p>Yukarıdaki örneklerin hepsinde bir alan tahsisinde bulunulmuş ancak değerleri atanmamıştır. Bu sebeple empty durumuna birer örnektirler.</p>
<p>
Default değerler için string bir istisnadır. Çünkü string'in default değeri null'dır ve empty 
değerini atayabilmemiz için ya "" bu ifadeyi ya da string.Empty özelliğini kullanırız.
</p>

```c#
string a = "";
string b = string.Empty; 
```
<p>Yukarıdaki her iki varyasyonda da string değişkenlere empty değerlerini atamış oluruz.</p><br><br>


<h2 id="nullvsemptyimportant">Null ve empty arasındaki önemli fark!</h2>
<p>
Null olan bir değer üzerinde işlem yapmaya çalıştığımızda run time hatası meydana 
gelirken empty olan bir değişken üzerinde herhangi bir işlem gerçekleştirebiliriz.
</p><br><br>


<h2 id="isnullorempty">IsNullOrEmpty() Fonksiyonu</h2>
<p>Elimizdeki string ifadelerin işleme tabii tutulmadan önce kesinlikle kontrol edilmesi gerekir.</p>
<p>
IsNullOrEmpty() fonksiyonu, elimizdeki string ifadenin null yahut empty olup olmama durumları hakkında bir kontrol 
yapar ve geriye bool türde sonuç döndürür. Eğer ki değer null ya da empty ise geriye true, değilse false döndürür.
</p>

```c#
string x = string.Empty;
if (string.IsNullOrEmpty(x))  //x değişkeni empty olduğu için if bloğuna girilecektir.
{
    //Operasyonlar...
}
```
<br><br>


<h2 id="isnullorwhitespace">IsNullOrWhiteSpace() Fonksiyonu</h2>
<p>
IsNullOrWhiteSpace() fonksiyonu, elimizdeki string ifadenin null, empty veya boşluk karekterlerini içerip içermemesi durumunu 
kontrol eden bir fonksiyondur. Eğer bu üç durumdan herhangi birini içeriyorsa geriye true döner, içermiyorsa false döner.
</p>
<p>Örneğin;</p>

```c#
string x = "  ";
if (string.IsNullOrWhiteSpace(x))  //x değişkeni boşluk karakterlerini içerdiği için if bloğu tetiklenecektir.
{
    //Operasyonlar...
}

string y = "sebepsiz boş yere ayrılacaksan";
if (string.IsNullOrWhiteSpace(x))  //Burada if bloğu tetiklenmeyecektir.
{
    //Operasyonlar...
}
```
<br><br>


<h2 id="string">String neden referans türlüdür?</h2>
<p>
- String ifadeler esasında bir char dizisidir. Yani yazılım açısından string bir ifade yoktur. Esasında karakterlerin 
bir araya gelmiş hali vardır. Dolayısıyla karakterleri bir araya getirebilecek yegane şey bir dizidir. String ifadeler;
yazılımsal açıdan, bilgisayarda bir char dizisi olarak tarif edilmekte ve o şekilde tutulmaktadırlar.
</p>
<p>
- String ifadeler; özünde bir char dizisi, yani dizi olmasından dolayı referans türlü 
değişkenlerdir. Çünkü diziler referans türlüdür, nesnedir. Yani heap'te tutulurlar.
</p>
<p>
- String ifadeler char dizisi olduklarından dolayı yapısal olarak her bir karakter baştan sona 
indexlenmektedir. Dolayısıyla string bir ifade üzerinde indexer operatörünü de kullanabilmekteyiz.
</p>
<p>- Peki string bir değişkeni Array türüyle karşılayabilir miyiz?</p>

```c#
string metin = "Ben bir metinim.";
Array array = metin;
```
<p>
- Karşılayamayız. Çünkü string özünde bir char dizisi olabilir ancak yapısal olarak 
yine de string olduğu için Array referansına atanamaz, Array ile karşılanamaz.
</p><br><br>


<h2 id="arraysegment1">Array segment nedir?</h2>
<p>Bir dizinin belirli bir aralığı üzerinde dilin getirdiği fonksiyonlarla herhangi bir işlem yaptığımızda, mimarinin default davranışı;
ilgili diziyi kopyalamak / türetmek ve bu yeni dizi üzerinde işlemler yapmak olacaktır. Ve bu değişiklikler orijinal diziye yansıtılmayacaktır.
</p>
<p>
Örneğin; aşağıdaki sayilar dizisindeki 2. ve 5. elemanların arasındaki değerler 
üzerinde bir işlem yaptığımızda bu değişiklik orijinal diziyi etkilemeyecektir.
</p>

```c#
int[] sayilar = {10, 20, 30, 40, 50, 60, 70, 80};
int[] sayilar2 = sayilar[1..5];
sayilar2[0] *= 10;
Console.WriteLine(sayilar[1]);
```
<p>
Eğer bu değişikliklerin ilgili dizi üzerinde uygulanmasını istemiyorsak o zaman 
bir sorun yok ancak uygulanmasını istiyorsak array segment'i kullanmalıyız.
</p><br>
<p>
Array segment, bir dizinin bütününden ziyade belirli bir kısmına yahut parçasına ihtiyaç dahilinde ilgili diziyi 
kopyalamak yerine bağımsız bir referans ile erişmemizi ve böylece salt bir şekilde temsil etmemizi sağlayan bir yapıdır.
</p>
<p>
Böylelikle elimizdeki ram'i, işlemciyi yani kaynakları daha az tüketeceğimizden 
dolayı daha hızlı, daha performanslı bir çalışma gerçekleştirmiş oluyoruz.
</p>
<p>
Verilerimizin türetilmemesi gereken durumlarda kesinlikle tercih edilmesi gereken bir yaklaşımdır.
</p><br><br>


<h2 id="arraysegment2">Array segment nasıl oluşturulur?</h2>
<p>Array segment'in kullanımı:</p>

```c#
ArraySegment<T> arraySegment = new ArraySegment<T>(dizininAdi);  
```
<p>Yukarıdaki çalışma ile herhangi bir tipteki dizinin referansını array segment ile tutmuş oluyoruz.</p><br>
<p>Bir önceki başlıkta bahsedilen sayilar dizisi üzerinde herhangi bir işlem yapmak istiyorsak şu şekilde bir işlem yapmalıyız:</p>

```c#
ArraySegment<int> arraySegment = new ArraySegment<int>(sayilar);
//sayilar dizisinin bütün elemanlarını temsil eder. Yani bütün elemanları üzerinde bir işlem yapabiliriz.
```
<p>Eğer dizinin sadece belirli bir aralığı üzerinde bir işlem yapmak istiyorsak:</p>

```c#
ArraySegment<int> arraySegment = new ArraySegment<int>(sayilar, 1, 5);
//sayilar dizisinin 2. ve 5. elemanları arasındaki değerleri temsil eder. 
//Yani 2. ve 5. elemanları arasındaki değerler üzerinde bir işlem yapabiliriz.
```
<p>
Ancak yukarıdaki işlemde önemli bir nokta vardır. O da şu ki: Belirli bir değer aralığını 
temsil eden segment'ler dizinin bütün elemanlarını tutar. Yani dizinin kendisini yine referans eder. 
Amma velakin sadece belirlenen aralık üzerinde bir işlem gerçekleştirir.
</p><br>
<p>
Görüldüğü üzere array segment'ler referans mantığıyla çalışmaktadır. Bu sebeple segment üzerinde 
yapılan değişiklik, ilgli diziyi; ilgili dizi üzerinde yapılan değişiklik de segment'i etkilemektedir.
</p>









