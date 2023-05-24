# Diziler
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
<p>- Diziler, array sınıfından türetilmektedir.</p>
<p>- Dolayısıyla dizilerde array sınıfından gelen metotlar ve özellikler mevcuttur.</p>
<br>


## Array sınıfı clear metodu
<p>
Clear metodu, dizi içerisindeki tüm elemanları siliyor diye bilinir. Ancak bu yanlıştır. 
Dizi içerisindeki elemanlara, dizinin türüne uygun default değerleri atayan bir metottur.
</p>
<br>


## Çok boyutlu / biçimli / dereceli diziler
<p>Çok boyutlu diziler, oyun programlamada yahut yüksek istatiksel çalışmalarda kullanılan bir yapıdır.</p>
<p>Çok boyutlu bir dizinin eleman sayısı, bütün boyutların eleman sayısı çarpılarak elde edilir.</p>
<p>Örneğin;</p>

```c#
int[,,] sayilar = new int[2,2,4];
Console.WriteLine(sayilar.Length);  //16
```
<p>Yukarıdaki dizinin eleman sayısı 2*2*4'den 16 sonucunu verecektir.</p>
<br>


## Dizi içerisinde dizi tanımlama / Düzensiz diziler / Dizi dizileri
<p>Düzensiz diziler, her bir elemanı kendi içerisinde farklı bir dizi barındıran dizilerdir.</p>
<p>Çok boyutlu dizilerden tek farkı; çok boyutlu dizilerin sütun sayılarının sabit, düzensiz dizilerin ise sütun sayılarının değişken olmasıdır.</p>

```c#
int[][] sayilar = new int[3][];
sayilar[0] = new int[3] {3, 5, 7};    //sayilar dizisinin 0. dizisine 3 elemanlı bir dizi ekledim. 
sayilar[1] = new int[6] {1, 2, 28, 9, 5, 12};    //sayilar dizisinin 1. dizisine 6 elemanlı bir dizi ekledim. 

Console.WriteLine(sayilar[0][2]);   //sayilar dizisinin 0. dizisindeki 2. elemanı konsola yazdırıyorum. 
                                    //Yani çıktı olarak 7'yi elde edeceğim.
```

