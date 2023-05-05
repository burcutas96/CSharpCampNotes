# Özel ders formatında a'dan z'ye C# 10 programlama eğitimi
### Gençay Yıldız tarafından hazırlanan "Özel ders formatında a'dan z'ye C# 10 programlama eğitimi" eğitim setinden aldığım notlar.

* <a href="#char">Char türünün sayısal türe dönüştürülmesi</a>
* <a href="#byte">(byte) * (byte) = ? (İstisna-Mülakat)!</a>
* <a href="#ternary">Birden fazla koşullu ternary operatörü oluşturmak</a>
* <a href="#typeof">typeof operatörü</a>
* <a href="goto">goto keyword'ünü kullanmak yerine çoklu case kullanımı</a>
* <a href="switchexpression">switch expression 1</a>
* <a href="switchexpressiontuple">switch expression - tuple patterns</a>
* <a href="switchexpressionproperty">switch expression - property patterns</a>

<br><br>

<h2 id="char">Char türünün sayısal türe dönüştürülmesi</h2>
<p>'a' karakterinin ASCII kaynak kodundaki sayısal değeri, int türüne dönüştürülür.</p>

```ruby
char a = 'a';
int a_ = (int)a;
Console.WriteLine(a_);  //97
```
<br><br>


<h2 id="byte">(byte) * (byte) = ? (İstisna-Mülakat)!</h2>
<p>
- Normalde aynı türdeki iki değerin aritmetik işlem sonucunun, yine aynı türde olması beklenirken int'den
daha az boyutlu türlerde böyle bir şey söz konusu değildir. Sonucun türü int olacaktır. 
</p>

```ruby
byte sayi1 = 10;
byte sayi2 = 5;
int sonuc = sayi1 + sayi2;
```
<p>
- Aynı şekilde farklı türlerdeki iki değerin aritmetik işlem sonucu, büyük olan verinin türünde olması beklenirken int'den daha az boyutlu türlerde böyle bir şey söz konusu değildir. Sonucun türü yine int olacaktır.
</p>

```ruby
short sayi1 = 25;
byte sayi2 = 35;
int sonuc = sayi1 + sayi2;
```
<br><br>


<h2 id="ternary">Birden fazla koşullu ternary operatörü oluşturmak</h2>
<p>
Soru: Yaşı; 25'den küçük olanlara "A", 25'e eşit olanlara "B", 25'den büyük olanlara "C" değerini
döndüren ternary operatörünü oluşturunuz.
</p>

```ruby
int yas = 24;
string sonuc = yas < 25 ? "A" : (yas == 25 ? "B" : "C");
Console.WriteLine(sonuc);  //C
```
<br><br>


<h2 id="typeof">typeof operatörü</h2>
<p>typeof operatörü verilen tür ile ilgili bilgileri getirir.</p>

```ruby
Type intType = typeof(int);
Console.WriteLine("int türünün adı: " + intType.Name);
Console.WriteLine("int türü primitive mi?: " + intType.IsPrimitive);
Console.WriteLine("int türü class mı?: " + intType.IsClass);
Console.WriteLine("int türü value type mı?: " + intType.IsValueType);
```




