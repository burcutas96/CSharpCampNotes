# Döngüler
<p>- Tek bir değişken altında birden fazla "aynı türde" değeri toplamamızı sağlayan veri kümelerine dizi denmektedir.</p>
<p>- Diziler içerisinde birden fazla aynı türde değerleri tutabilen yapılardır.</p>
<p>- Eğer farklı türlerdeki değerleri dizi ile tutmak istiyorsak dizinin türünü object olarak ayarlamalıyız.</p>
<p>
- Prosedürel programlamanın temel veri kümeleridir. Yani yazılımsal boyutta, yazılım adına ram'de birden 
fazla değeri tek bir değişken altında bir veri kümesi halinde tutabilirler.
</p>
<p>- Diziler, veri kümeleri oldukları için içlerindeki birden fazla veri üzerinde kümesel işlemler yapmamızı sağlarlar.</p>
<p>
- Diziler, prosedürel programlamanın temel yapıları oldukları için daha gelişmiş yapılar olan koleksiyonlarında 
temelini teşkil etmektedirler ve gelişmelerine katkıda bulunmaktadırlar.
</p>
<p>- Diziler, referans türlü değerlerdir. Yani nesnel yapılardır. Özlerinde class'tırlar.</p>
<p>- Yapısal olarak ram'de heap belleğinde tutulurlar.</p>
<p>- Dizi içerisine her türlü değer koyulabilir. Her türlü değerden kastımız; referans ve değer türlü değerler koyulabilir.</p>
<p>- Diziler içerisine eleman / değer eklendikçe bunları serseri bir şekilde depolamaz. Sıralı, düzenli bir şekilde depolayacaktır.</p>
<p>- Dizilerde eklenen elemanlar index ismini verdiğimiz numaralarla ardışık bir şekilde numaralandırılırlar.</p>
<p>- Index no: Her bir elemana verilen ardışık sayıdır. 0'dan başlar n-1'e kadar gider.</p>
<p>Prototip:</p>

```c#
type[] name = new type[10]
```
<p>C# dilinde köşeli paranteze "indexer" denmektedir.</p>
<br>
<p>
- Dizi tanımlama sürecinde eleman sayısı mecburi girilmek zorundadır. Yani dizide 
çalışılacak değer adedi başta bildirilmelidir. Bu durum bir sınırlılıktır.
</p>
<p>
- Bir dizi tanımlaması yapıldığı an bellekte, o diziyi kullansakta kullanmasakta verilen 
eleman sayısı kadar alan tahsisinde bulunulur. Bu durum bir sınırlılıktır.
</p>
<p>- Dizilere alan tahsisi yapıldığında ilgili alanlara türüne uygun default değerler atanır.</p>


