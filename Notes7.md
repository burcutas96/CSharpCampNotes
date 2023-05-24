# String Türü Nedir?
#### String, programlama dilinde referans türlü olduğu halde bir keyword olan tek değerdir.
#### Referans türlü değişkenlerde, sadece string değişkeni bir keyword'dür. String haricindeki tüm referans türlü değişkenlerin bir keyword'ü yoktur. Yani keyword değildirler.

<a href="nullvsempty">Null ve empty farkı</a>
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
türlü değişkenler null alamıyor. En kötü ihitmalle default değerlerini atamak zorundayız. Aksi taktirde hata alırız.
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
<p>Yukarıdaki her iki varyasyonda da string değişkenlere empty değerlerini atamış oluruz.</p>





