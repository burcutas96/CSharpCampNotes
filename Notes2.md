* <a href="#typepattern">Type pattern</a>
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





