* <a href="#stringbuilder">StringBuilder Sınıfı Nedir?</a>
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


















