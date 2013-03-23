---
layout: post
title: "Log kayitlarini toplama"
date: 2013-03-22 22:29
comments: true
categories: mimari
---

Yazilim projeniz tamamlandi, ya da en azindan musterinizin hayatini kolaylastiracak ilk fonksiyon tamamlandi ve uretim ortamina yuklediniz, peki ya daha sonra? Calisan sisteminiz de neler olup bitiyor? Her sey yolunda mi gidiyor? Herhangi bir calisma zamani hatasi olusmus mu? Bunlari takip etmek icin log dosyalari tutariz ve eger calistiginiz sistem sadece bir bilgisayar uzerine yuklenmis bir web sitesi vb bir sistem ise sorun degildir bu kayitlari takip etmek.

Ancak yuksek erisebilirlik -hangi yazilim icin gereksinim degil ki bu?-  ve aldigi yogun yuk sebebiyle olceklenebilir (scalable) bir sistem gelistirdiginiz de bu sistemi ozellikle canli ortamda izlemek dikkatle planlanmasi gereken bir islemdir. 

Soyle bir sistem hayal edin, bir MVC web uygulamasi, arka planda toplu veya asenkronize isleme yapan windows servisleri, bir kac web servisiniz var ve bunlarin hic birisi sadece bir sunucu uzerinde calismiyor, ayni anda en azindan bir kac tane arka plan servisi calistirarark asiri yuku dagitiyorsunuz. Bu durumda olusturdunuz log dosyalari sadece sunucu uzerinde kaliyor ise o kayitlarin sizin icin hic bir faydasi olamaz. Ayrica bu log dosyalarini sadece sizin olusturdunuz uygulamaniza ozel log dosyalari olarak dusunmeyin, web sunucunuzun loglarindan, kullandiginiz reserve proxy sunucunun loglarindan, uzerinde calistiginiz isletim sisteminin sistem loglarina kadar her seyi toparlayip tek bir ekran uzerinde gorebilmenin verdigi rahatligi dusunun! Harika olurdu degil mi?

Zira herhangi bir sebeple log dosyalarini kontrol etmek istediginiz de web servisinizi yuklediginiz tum sunuculara tek tek gidip log dosyalarini kontrol etmeniz gerekecektir, web servisinde buldugunuz hatanin asil sebebini bulmak icin arkaplan servis log dosyalarini da kontrol etmek istediginiz de cileden cikabilir ve bir seylerin yanlis oldugunu dusunmeye baslayabilirsiniz. Bu duruma dusmeden bunu dusunmeye basladik bile sanirim? O halde bu yazida bahsedecegim cozumden bahsedelim.

Ozetle tum sunucularinizdan log kayitlarini alip merkezi bir noktada toplamaniz ve birlestirmeniz gerekmektedir. Bu sayede sisteminizin nasil calistigini izleyebilir, sisteminizin gercek hayatta ki davranislarini ogrenebilirsiniz. Log toplama sayesinde sadece hata kayitlarina degil tum loglariniza erisebilirsiniz ve bu veri ile ne yapabileceginiz, hangi bilgileri loglayip hangi amac icin kullanacaginiz daha cok log stratejiniz ile alakali olacaktir. 

### Log Stash ve Graylog2 

LogStash ve Graylog2 gibi log toplama araclari genellikle log kayitlarini toplamaka istediginiz sunuculariniz uzerinde calisan uygulari ile log verinizi merkezi sunucularina aktarir ve bir web arayuzu ile bunlari goruntuler. Tabiki bu yontem log kayitlarinizi toplamaniz icin yapilmasi gereken tek yol degil, AMQP gibi mesajlasma protokolleri ile de log kayitlarinin merkezi sunucuya toplanmasi soz konusudur. Eger buyuk bir dagitik sistem uzerinde calisiyorsaniz bir AMQP messajlasma sistemi uzerinden bu mesajlari dagitmak guvenilir ve olceklenebilir bir log toplama sistemi kurmaniza yardimci olacaktir. Ornegin log verilerini topladiginiz sunucunuzu gecici olarak kapatsaniz bile, tekrar calistirdiniz da mesaj kuyrugunda bekleyen log verilerini bulup, isleyecektir. 

Bu araclari nasil kurup isleteceginize dair takip eden baska bir blog yazim daha olacak simdilik bahsettigim araclara su adreslerden bakabilirsiniz.

Kibana hakkinda fikir vermesi acisindan Logstash ile toplanmis loglarin tek bir arayuz ile timeline uzerinde gosteren ornek bir ekran goruntusu ile bitiriyorum simdilik.
{% img left /images/content/kibana-screenshot.png Kibana ekran goruntusu %}



- <http://logstash.net>
- <http://kibana.org/>
- <http://www.rabbitmq.com>
- <http://graylog2.org>