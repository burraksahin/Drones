# Motivasyon

5 sene evvel bu projeye başlarkenki motivasyonumuz belirttiğim gibi TSK'nın en fazla şehit verdiği operasyonların kapalı alanlarda gerçekleşiyor ve bu alanlarda çalışabilecek bir tasarımda bulunmak istedik. O zamanlar rehine kurtarma operasyonu sırasında maalesef birçok şehit verilmişti. Sonrasında 12 askerimizin gaz zehirlenmesi geçirdiği olay da göz önünde bulundurularak hala geliştirilme yapılması gerekliliği vardır. Sadece askeri olarka değil, maalesef çok fazla sayıdaki maden kazaları göz önüne alınınca bu alanda gelişmeler yapılması zaruridir.

<center>
   <img width="352" height="233" alt="cad" src="https://github.com/user-attachments/assets/7bea02e1-345c-48aa-be74-2993c0812e77" />
</center>
 
# Kullanlılan Malzemeler

* Uçuş bilgisayarı olarak Pixhawk3 ve uçuş yazılımı olarak ArduPilot
* Görev bilgisayarı olarak Raspberry Pi 3
* Quadcoper geometrisi için 4 tane Brushless (BLDC) motor
* Her motor için electronic speed controller (ESC)
* Gücü dağıtmak için power distributor
* LiPo batarya
* Başlangıç denemeleri için external GPS ve telemetri
* Mesafe sensörleri
* Karbonfiber Gövde
* Bağlantı elemanları (spacers, fasteners etc.)

# Prosedür

Bir hava aracı tasarımı, birden çok parametreye sahip optimizasyon problemi olarak tanımlanabilir. Göreve ve elde olan/edinilebilecek malzemelere göre isterleri yerine getirmeye çalıştık. 
Uçuş süresini 15 dakika, faydalı yükü 400 gram olarak belirledik. Diğer bir kritik özelliği ise GPS'siz uçuş yapabilecek şekilde tasarlamak oldu. Önce mekanik/aerodinemik hesaplar, sonra elektronik/yazılımsal çözümler anlatılacaktır. 

## Mekanik/Aerodinamik

Tasarımın doğası gereği iteratif bir süreç izledik. Belirlenen yük taşıma, uçuş süresi ve bütçe göz önünde bulundurularak BLDC motorların datasheetleri incelenmeye başlandı. 
* Motorlar için ürettikleri kaldırma kuvvetleri, diğer gerekli parametrelerle beraber (pervane pal sayısı, pervane genişliği, kullanılan güç, % kaç kullanım, maliyet etc.) kendi yazdığımız algoritmaya soktuk.

<center>
  <img width="596" height="165" alt="moto_thrust" src="https://github.com/user-attachments/assets/38d197d5-a66c-4497-bc41-2816f049572a" />
</center>

* LiPo bataryaların mAh değerleri, ağırlıkları ve ne kadar amper çekebileceğimize göre algoritmaya koyduk.
* Aviyonik, mekanik ve diğer komponentler için yaklaşık bir ağırlık tahmini yaptık.
* Toplam ağırlık ve faydalı yükü göz önünde bulundurarak, motor itkilerinin bu ağırlığın 2 katı olacak şekilde (maliyete de bakarak) başlangıç olarak motor, batarya ve pervane seçimleri yapıldı.
* Sonrasında motorların ve elektronik komponentlerin çekeceği gücü tahmin edip uçuş süresinin kurtarıp kurtarmayacağına baktık.
* Komponent seçimleri sonrası CAD çizimi yaptım. Parçaların nereye koyulacağı, bağlantıların nereden nasıl yapılacağı, yüklenmeler ve yüklere bağlı olarak ufak crash durumlarına dayanıklı, ağırlığı fazla olmayan ve ağırlık merkezi ortada, fazla da titreşmeyecek (doğal frekanslardan mümkün olduğunca uzak) (IMU ve mesafe sensörleri titreşime karşı hassaslar, izole etsek bile), kablajlamanın rahat yapılabileceği, sensörlerin elektromanyetik sinyallerden mümkün olduğunca etkilenmeyecek bir tasarım yapmaya çalıştım. Tasarımı yaptığım zamanlar daha lisans hayatımın başındaydım ve tecrübesizdim, tasarım kesinlikle geliştirilmeye açık.

<center>
  <img width="419" height="287" alt="tech_draw" src="https://github.com/user-attachments/assets/472039d0-3d69-4ffd-863e-e884592a7681" />
</center>

## Elektronik/Yazılım
* Motorların çekeceği amperlere uygun olarak ESC seçimi yaptık.
* Toplam güç için power distributor seçtik.
* GPS, barometre, pusula, IMU sensörü ve mesafe sensörleri entegre ettik (hcsr04 yanlış karardı ama lidar için paramız yoktu).
* Kablolamayı yaptık ve sarkmamaları için sabitledik.
* Yazılım olarak ArduPilot kullandık. GPS verisini çıkarması baya zorlayan bir part oldu.
* Simulasyonumuzu Gazebo üzerinden yaptık.

<center>
  <img width="1599" height="899"  alt="WhatsApp Image 2026-05-12 at 16 14 18" src="https://github.com/user-attachments/assets/4b943b8f-ef09-4f22-aec6-ca2b3daf3ac3"  />
</center>










