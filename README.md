# Özel ders formatında a'dan z'ye C# 10 programlama eğitimi
### Gençay Yıldız tarafından hazırlanan "Özel ders formatında a'dan z'ye C# 10 programlama eğitimi" eğitim setinden aldığım notlar.

* <a href="#char">Char türünün sayısal türe dönüştürülmesi</a>
* <a href="#byte">(byte) * (byte) = ? (İstisna-Mülakat)!</a>
* <a href="#ternary">Birden fazla koşullu ternary operatörü oluşturmak</a>
* <a href="#typeof">typeof operatörü</a>
* <a href="#goto">goto keyword'ünü kullanmak yerine çoklu case kullanımı</a>
* <a href="#switchexpression">switch expression</a>
* <a href="#switchexpressiontuple">switch expression - tuple patterns</a>
* <a href="#switchexpressionproperty">switch expression - property patterns</a>

<br><br>

<h2 id="char">Char türünün sayısal türe dönüştürülmesi</h2>
<p>'a' karakterinin ASCII kaynak kodundaki sayısal değeri, int türüne dönüştürülür.</p>

```c#
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

```c#
byte sayi1 = 10;
byte sayi2 = 5;
int sonuc = sayi1 + sayi2;
```
<p>
- Aynı şekilde farklı türlerdeki iki değerin aritmetik işlem sonucu, büyük olan verinin türünde olması beklenirken 
int'den daha az boyutlu türlerde böyle bir şey söz konusu değildir. Sonucun türü yine int olacaktır.
</p>

```c#
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

```c#
int yas = 24;
string sonuc = yas < 25 ? "A" : (yas == 25 ? "B" : "C");
Console.WriteLine(sonuc);  //C
```
<br><br>


<h2 id="typeof">typeof operatörü</h2>
<p>typeof operatörü verilen tür ile ilgili bilgileri getirir.</p>

```c#
Type intType = typeof(int);
Console.WriteLine("int türünün adı: " + intType.Name);
Console.WriteLine("int türü primitive mi?: " + intType.IsPrimitive);
Console.WriteLine("int türü class mı?: " + intType.IsClass);
Console.WriteLine("int türü value type mı?: " + intType.IsValueType);
```
<br><br>


<h2 id="goto">goto keyword'ünü kullanmak yerine çoklu case kullanımı</h2>
<p>
i değişkeninin 5'e veya 7'ye veya 10'a eşit olması durumunda ikinci case bloğu çalışacaktır.
Bu sayede daha temiz ve okunaklı bir kodsal çalışma yapmış olduk.
</p>

```c#
int i = 7;
switch (i)
{
    case 6:
        Console.WriteLine(i/5);
        break;
    case 5:
    case 7:
    case 10:
        Console.WriteLine(i * 10);
        break;
}
```
<br><br>


<h2 id="switchexpression">Switch expression</h2>
<p>Tek satırlık işlemler için maliyet düşürücü ve kullanışlı semantiktir.</p>
<p>
- Eski Yöntem
</p>

```c#
string mesaj = "";

switch (DateTime.Now.DayOfWeek) 
{
    case DayOfWeek.Monday:
        mesaj = "Bugun günlerden Pazartesi";
        break;
    case DayOfWeek.Tuesday:
        mesaj = "Bugun günlerden Salı";
        break;
}
Console.WriteLine(mesaj);
```
<p>
- Yeni Yöntem
</p>

```c#
string mesaj = DateTime.Now.DayOfWeek switch
{
    DayOfWeek.Monday => "Bugun günlerden Pazartesi",
    DayOfWeek.Tuesday => "Bugun günlerden Salı"
};
Console.WriteLine(mesaj);
```
<br><br>


<h2 id="switchexpressiontuple">Switch expression - tuple patterns</h2>
<p>
- Eski Yöntem
</p>

```c#
string adi = "Nevin";
int yasi = 27;

string mesaj = "";
switch (adi, yasi)
{
    case ("Hüseyin", 20):
        mesaj = "Hoşgeldin Hüseyin";
        break;
    case ("Nevin", 27):
        mesaj = "Hoşgeldin Nevin";
        break;
    default:
        mesaj = "Hoşgeldin";
        break;
}
Console.WriteLine(mesaj);
```
<p>
- Yeni Yöntem
</p>

```c#
string adi = "Nevin";
int yasi = 27;

string mesaj = (adi, yasi) switch
{
    ("Hüseyin", 20) => "Hoşgeldin Hüseyin",
    ("Nevin", 27) => "Hoşgeldin Nevin",
    (_,_) => "Hoşgeldin"  //Tuple türünde _ (alt tire), default'a denk gelir.
};
Console.WriteLine(mesaj);
```
<br><br>


<h2 id="switchexpressionproperty">Switch expression - property patterns</h2>
<p>
Property patterns, nesnenin property'lerine girerek belirli durumları
hızlı bir şekilde kontrol etmemizi sağlan bir gelişimdir.
</p>
<p>
- Eski Yöntem
</p>

```c#
Ogrenci ogrenci = new Ogrenci
{
    Meslek = "Yazılım Uzmanı"
};
double maas = 0;
switch (ogrenci.Meslek)
{
    case "Kasap":
        maas = 50;
        break;
    case "Tesisat Ustası" when !true:
        maas = 45;
        break;
    case "Yazılım Uzmanı":
        maas = 55;
        break;
}
Console.WriteLine(maas);

class Ogrenci
{
    public string Meslek { get; set; }
}
```

<p>
- Yeni Yöntem
</p>

```c#
Ogrenci ogrenci = new Ogrenci
{
    Meslek = "Yazılım Uzmanı"
};

double maas = ogrenci switch 
{
    { Meslek: "Kasap"} => 50,
    { Meslek: "Tesisat Ustası" } when !true => 45, 
    { Meslek: "Yazılım Uzmanı" } => 55
};
Console.WriteLine(maas);

class Ogrenci
{
    public string Meslek { get; set; }
}
```







