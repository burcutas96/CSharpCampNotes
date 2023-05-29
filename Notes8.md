* <a href="#stringbuilder">StringBuilder Sınıfı Nedir?</a>
* <a href="#collections">Koleksiyonlar Nelerdir? Diziler Varken Neden Koleksiyon Yapıları İnşa Edilmiştir?</a>
* <a href="#arrayList">ArrayList Nedir?</a>
<br><br>


<h2 id="stringbuilder">StringBuilder Sınıfı Nedir?</h2>
<p>
StringBuilder, string birleştirme operasyonlarında + operatörüne nazaran yüksek 
maliyeti absorbe edebilmek için arkaplanda StringSegment algoritmasını kullanan ve bu 
algoritma ile ilgili değerleri olabilecek en az maliyetle birleştirip döndüren bir sınıftır.
</p>
<p>StringBuilder sınıfını kullanabilmek için System.Text kütüphanesini uygulamaya using etmeliyiz.</p>

```c#
string isim = "Gençay";
string soyisim = "Yıldız";

//Console.WriteLine(isim + soyisim);   //Bunun yerine

StringBuilder builder = new StringBuilder();
builder.Append(isim);
builder.Append(" ");
builder.Append(soyisim);  
//Yukarıdaki çalışmayı yaparak daha az maliyetli bir birleştirme işlemi yapmış oluyoruz.
```
<br><br>


<h2 id="collections">Koleksiyonlar Nelerdir? Diziler Varken Neden Koleksiyon Yapıları İnşa Edilmiştir?</h2>
<p>
Koleksiyonlar, dizilerin daha gelişmiş yapılanmasıdır. İkisinde de birden fazla veriyi tek bir dizi içerisinde tutup yönetebiliyoruz. Yani ikisinde de amaç aynı. Peki neden diziler varken koleksiyonlara ihtiyaç duyulmuş? Aralarındaki fark ne?
</p>
<p>
Önceki başlıklarda incelediğimiz gibi dizilerde sınırlılıklar vardı.İşte bu sınırlılıkları ortadan kaldıran yapılanma, koleksiyonlardır.
</p>
<p>
- Birinci sınırlılık; dizilerde eleman sayısını önceden, tanımlama yaparken bildirmek bir sınırlılıktı, dizinin eleman sayısını önceden bilmek zorundaydık.
</p>
<p>
Ancak koleksiyonlarda böyle bir zorunluluk yoktur. Koleksiyonun eleman sayısını bildirmeyiz. Arkaplanda, diziye eklenen eleman kadar alan tahsisinde bulunulur.
</p><br>
<p>
- İkinci sınırlılık; diziler tanımlandığında, kullansak da kullanmasak da bellekte belirtilen eleman sayısı kadar alan tahsisinde bulunurlar. Bu bir sınırlılıktır.
</p>
<p>
Ancak koleksiyonlarda böyle bir durum söz konusu değil. Az önce de bahsettiğimiz gibi ne kadar eleman eklersek ram de o kadar yer ayırılır.
</p><br>
<p>
- Üçüncü sınırlılık; dizilerde eleman sayısı başta belirlendiği için ihtiyaca binaen daha fazla değer atamak istediğimizde bu değerleri atayamayacağımızdan dolayı bu bir sınırlılıktır.
</p>
<p>
Ancak koleksiyonlarda istediğimiz zaman eleman sayısını arttırabiliyoruz. Böylelikle dizilerdeki bu sınırlılığa da bir çözüm getirilmiş oldu.
</p><br><br>


<h2 id="arrayList">ArrayList Nedir?</h2>
<p> Aslında koleksiyonlar içerisinde birçok koleksiyon barındırır ve bu koleksiyonların ilki ArrayList koleksiyonudur diyebiliriz.</p>
<p>
ArrayList her ne kadar dizilerdeki sınırlılıkları ortadan kaldıran bir koleksiyon olsa da 
kendine has sınırlılıkları mevcuttur. Bu sebepten ötürü de diğer koleksiyonlar ortaya çıkmıştır.
</p>
<p>ArrayList'in kendine has sınırlılığı ise verilen datayı boxing işlemine tabi tutmasıdır.</p>
<p>
ArrayList içerisindeki herhangi bir veriyi talep etttiğimizde ilgili veri object türünde getirilecektir. 
Dolayısıyla verinin üzerinde kendi türüne özgü işlem yapabilmek için veriye unboxing işlemini uygulamamız gerekecektir.
</p>











