# Hata Kontrol Mekanizmaları
#### 3 tür hata çeşidi vardır. Bunlardan birincisi compiler (derleme) hataları, ikincisi run-time (çalışma zamanı) hataları, üçüncüsü ise logical (mantıksal) hatalardır.

* <a href="#compiler">Compiler Hataları</a>
* <a href="#runtime">Run-Time Hataları</a>
* <a href="#logical">Logical Hatalar</a> 
<br><br>

<h2 id="compiler">I. Compiler Hataları</h2>
<p>- Programlama dili kurallarına aykırı olan syntax hatalarıdır.</p>
<p>- Özellikle gelişmiş editörler (VS) sayesinde söz dizimi hataları derlemeye gerek bile kalmaksızın fark edilebilmektedir.</p>
<p>- Hatanın bulunduğu satır derleyici tarafından rapor edilir. Gelişmiş editörlerde ise hataya nokta atışı yapılarak hatanın nerde olduğunu bize direkt söyler.</p>
<p>Örneğin;</p>
<img src="img/syntaxerror3.png"/>
<img src="img/syntaxerror2.png"/>
<img src="img/syntaxerror1.png"/>
<br><br>

<h2 id="runtime">II. Run-Time Hataları</h2>
<p>- Syntax'da bir promlem yok, kodun semantiği kusursuz ama çalışma zamanında patlamaya sebep veren hatalardır.</p>
<p>- Yazılım ayaktayken ortaya çıkan bir takım aykırı durumlardan dolayı programın işletim sistemi tarafından kesilmesiyle/sonlandırılmasıyla sonuçlanır.</p>
<p>- Çalışma zamanı hataları programın işleyişinin ortasında direkt kullanıcıyla temas edebilecek hatalardır. Ve hiçbir yazılımcı son kullanıcının hatayla 
karşılaşmasını istemez.</p>
<p>- Bu yüzden çalışma zamanında alınabilecek "olası" hataları yönetmemiz ve onları bir şekilde manipüle etmemiz gerekmektedir.</p>
<p>- Çalışma zamanı hataları genellikle kullanılan mimaride öntanımlı mesajları verecektir.</p>
<p>- Hata kontrol mekanizmaları çalışma zamanı hatalarını kullanıcıya hissettirmeden yakalayabilmek ve ilgili hatayı manipüle edebilmek için vardır.</p>













