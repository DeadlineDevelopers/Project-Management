
> .. great features wont matter unless customers trust our software. So now, when we face a choice between adding features and resolving security issues, need to choose security. **-Bill Gates**

# **Yazılım Güvenliği - Tanım**
- Yazılımın, saldırı altında doğru bir şekilde çalışmaya devam etmesidir.
- Yazılımın işlediği, servis ettiği verinin bozulmaması.
- Yazılımın işlediği, servis ettiği verinin gizli kalması.
- Yazılımın servis vermeye devam etmesi.

#### Uygulama Güvenliğinde Kullanılan Denetim Yöntemleri
1. **Tehtid Modelleme:** Güvenlik risklerinin sistematik bir şekilde bulunması ve önem sırasına konulmasıdır.Uygulamanın ne yaptığı, hangi kaynakları nasıl kullandığı, önemli kullnanım senaryoları gibi konular konuşuldukça tek sayfalık bir aktörler, kaynaklar, bileşenler,iletişim trafiği bilgisi ortaya çıkar. Bu bilgiler yardımıyla tehditler ortaya çıkartilabilir.

2. **Statik Kaynak Kod Analizi:** Kod blokları çalıştırılmadan yapılan güvenlik kontrolleridir. Genellikler otomatik olarka yapılır (*Örn. sonar vb.*).

3. **Penetration Test:** Hedef uygulamalar üzerinde dinamik olarak güvenlik zafiyeti bulma metodudur. Hedefin ne kadar güvenli olduğunu değil, ne kadar güvensiz olduğunu gösterir.


### Güvenli Yazılım Prensipleri
Jerome H. Saltzer ve Michael D. Schroeder tarafından 1973 yılında yazılan bir makalede 8(+2) dizayn prensibinden bahsetmişlerdir. Bu prensiplerin anlaşılması önemlidir.

1. **Basit Dizayn:** Uygulama olabildiğince basit ve küçük olmalı.
  -  _Örnek_  : denetlemesi zor bir email validation regexi:
  > (?:(?:\r\n)?[ \t])*(?:(?:(?:[^()<>@,;:\\".\[\] \000-\031]+(?:(?:(?:\r\n)?[ \t])+|\Z|(?=[\["()<>@,;:\\".\[\]]))|"(?:[^\"\r\\]|\\.|(?:(?:\r\n)?[ \t]))*"(?:(?:\r\n)?[ \t])*)(?:\.(?:(?:\r\n)?[ \t])*(?:[^()<>@,;:\\".\[\] \000-\031]+(?:(?:(?:\r\n)?[\t])+|\Z|(?=[\["()<>@,;:...

2. **Her Kaynağa Erişim Kontrolü:** Uygulamanın servis ettiği her kaynak için yetki kontrolleri kullanılmalıdır. Bazı örnekler:
  - Sadece yetkilendirilmiş kullanıcılar tarafından çağrılması gereken menüleri yetkisi olmayan kullanıcılar da çağırabilmekteler midir?
  - Uygulamayı kullanırken rol bilgisi değiştirilen kullanıcı, oturum boyunca eski rolüne sahip olarak mı işlem yapabilmektedir?
  - Yetkilendirme kontrolleri sadece istemci tarafında mı gerçekleştirilmektedir.

3. **Bilinmezlik, Güvenlik Değildir:** Kötü niyetli kullnıcıların _"tahmin edememesi"_ üzerine kurulu olan hatalardır.
  - Uygulamada kullabnılan şifreleme anahtarları dışında başka gizli kalması gereken algoritma, akış vs. var mıdır?
  - YÖnetici arayüzü tahmin edilmesi zor bir URL ile mi korunmaktadır.
  - Executable dosyalar decompile edilip şiflere vs. alınabilir mi?

4. **Kullanılabilirlik Zarar Görmemeli:** Bu prensibe verilebilecek örnekler:
  - CAPTCHA için kullanılan imajların okunması zor mudur?
  - Resim doğrulama herhangi bir saldırı anlaşılmadan mı gözükmektedir.

5. **Önlemlerin Gereksiz Olması:**  Güvenlik önlemlerinin gerekli yerlerde ve seviyede alınması.
6. **İşlemlerin Kayıt Altına Alınması:** Saldırı Önlenemiyorsa bile, adli analiz ve tecrübe için işlemler kayıt altına alınmalıdır.

7. **Pareto İlkesi:** Pareto ilkesi kabaca _"etkilerin %80'i etkenlerin %20'sinden kaynaklanır."_ der. Örneğin Steve Balmer, Microsoft yazılımlarında yapılan çalışmaya göre bulunan ciddi hataların %80'lik bölümünün, %20'lik bir hatalı kod bulgu tipinden kaynaklandığını belirtmiştir. Dolayısıyla internet uygulamalarındaki zafiyetlerin %80'ini oluşturan önemli konulara yer verilmeye çalışılmıştır.

  6. İlk kural, kullanıcıdan alınan girdi sayısı minimumda tutulmalı. Arka uçta kullanıcının çok fazla verisini tutmak, güvenlik zafiyetlerine yol açabilir.

  5. İkinci kural belkide tüm injection problemlerini ortadan kaldırabilecek olan önlemdir. Kullanıcı girdileri kontrolsüz string birleştirme işlemlerinde kullanılmamalı.

  4. Bir başka önemli konu ise yetkilendir kontrollerinin sunucu tarafında eksiksiz bir şekilde uygulanmasıdır.
  3. HTTP trafiği iyi anlaşılmalıdır.
