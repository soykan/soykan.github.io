# Temiz Kod Rehberi
Bu rehber "Clean Code: A Handbook of Agile Software Craftsmanship (Robert C. Martin)" kitabındaki görüşler göz önünde bulundurularak hazırlanmıştır.

## İsimlendirmeler
- İsimlendirme, isimlendirilen şeyin neden var olduğunu, ne yaptığını ve nasıl kullanıldığını açıklar nitelikte olmalıdır.

- Birbirine benzeyen uzun değişken isimlendirmelerinden kaçınılmalıdır çünkü otomatik kod tamamlama özelliğine sahip editör veya geliştirme ortamlarında hatalara yol açabilir.

- İsimlendirmeler birbirinden ayırt edilebilir olmalı, kafa karışıklığına yol açmamalıdır.\
Örneğin; "Product", "ProductData", "ProductInfo" gibi birbirine benzeyen ancak farklı amaçlara hizmet eden tanımlamalardan kaçınılmalıdır.

- Telaffuz edilebilir isimlendirmeler kullanılmalıdır.\
Örneğin "private Date genymdhms;" şeklinde bir tanımlama yerine "private Date generationTimestamp;" kullanılmalıdır.

- Sabit, nümerik veya string değerler constant değişkenlerde tutulmalı ve amacına uygun isimlendirilmelidir. Örneğin; \
public static final int NUMBER_OF_WHEELS = 4;\
public static final String BRAND_NAME = "TOYOTA";

- İsimlendirmede veri tipine yer verilirse, veri tipi değiştikçe, isimlendirme de değişmek zorunda kalır. İsimlendirmede gerekmedikçe veri tipine yer verilmez.

- Interface'lerin başına "I" harfi eklemek yerine, onu implemente eden sınıfların sonuna "Imp" eklenmesi daha uygundur. Örneğin; \
Interface: ShapeFactory\
Sınıf:     ShapeFactoryImp

- Method isimleri "verb" (eylem) olmalı, sınıf isimleri ise "verb" olmamalı, "noun" veya "noun phrase" (isim veya isim tamlaması) olmalıdır.

## Fonksiyonlar

- Fonksiyon veya method gövdesi uzadıkça parçalanabilirliği sorgulanmalıdır. Sorgu sonucu method veya fonksiyon birden fazla iş yapıyorsa, yeni method veya fonksiyonlar oluşturulup, her biri tek iş yapacak şekilde (Single Responsibility Principle ışığında) tasarlanmalıdır.

- If, Else, While yapılarının gövdesinde bulunan kod satırı sadece bir satır olmalı ve bu satırda fonksiyon veya method çağrısı olmalıdır.

- Fonksiyonlar veya methodlar fazla miktarda iç içe geçmiş yapıyı barındırmamalıdır ve fonksiyon veya methodlardaki indent sayısı ikiyi aşmamalıdır.

- İngilizce olarak isimlendirilmiş bir fonksiyonun veya methodun isminin başına "To" (Türkçe karşılığı -mek -mak olan mastar) konulduğunda fonksiyonun amacı anlaşılıyorsa, isimlendirme doğrudur.

- Fonksiyonlara veya methodlara uzun isim vermek, uzun yorum satırları yazmaktan iyidir ve uzun isim vermekten kaçınılmamalıdır.

- Fonksiyon veya method çok sayıda parametre almamalı, bu parametreler aynı bağlamda bir sınıf yapısı altında toplanabiliyorsa, fonksiyon veya method o sınıf yapısından oluşan nesneyi parametre almalıdır.

- Boolean değerler fonksiyon veya method parametresi olmamalıdır. Bunun yerine false ve true durumları için iki ayrı fonksiyon veya method yazılmalıdır.

- Fonksiyon adı "verb" (eylem) parametresinin adı ise "noun" (ad) olmalıdır.

- Fonksiyon veya methodlar hata kodu döndürmek yerine exception'lardan faydalanmalıdır.

- Fonksiyon veya method gövdesinde bulunan try-catch blokları altında birer satır kod bulunmalı ve onlarda fonksiyon veya method çağrısı olmalıdır.

- Her fonksiyon veya method tek bir iş yapacağına göre ve hata değerlendirme de bir iş olduğundan try ifadesinden önce ve catch/finally ifadelerinden sonra herhangi bir ifade fonksiyon veya method içinde yer almamalıdır.

## Yorumlar

- Yorum yazmaya zaman ayırmak yerine kodu temizlemeye zaman ayırılmalıdır. Yorum satırları kodu açıklamak adına daha iyi bir yöntem kalmadığında kullanılır.

- Regex ifadeleri açıklamak için yorum satırı yazılabilir.

- Standart kütüphaneye ait veya düzenleme şansımızın olmadığı koda yorum satırları eklenebilir.

- Projede çalışan diğer yazılımcıları, sorun çıkabilecek yani projeyi zor durumda bırakabilecek durumlara karşı uyarmak için yorum satırları yazılabilir.

- TODO kodlarını düzenli olarak gözden geçirip, temizlemek ve proje içerisinde unutmamak gerekir.

- Kaynak kod dosyasının başına her güncelleme yapıldığında tarih atarak yorum düşmek günümüzde gereksizdir, bunun yerine versiyon kontrol sistemleri kullanılır.

- Eklenen kodun içine ekleyenin kim olduğunu belirtir yorum satırı yazılmaz, bu versiyon kontrol sisteminin işidir.

- Eski kodlar yorum satırına alınmamalı, onun yerine gerektiğinde versiyon kontrol sistemi ile kurtarılmalıdır.

- Yazılan kod değiştikçe ona yönelik yazılmış yorum satırını da güncellemek unutulmamalıdır.

## Biçimlendirme

- Kaynak kod dosyalarının ismi basit ve açıklayıcı olmalı. İnceleyen kişi doğru modüle baktığını anlayabilmeli.

- Kaynak kod dosyasının, yukarıdan aşağıya doğru inerek okunduğu bilinmeli ve buna uygun şekilde anlaşılır halde hazırlanmalıdır.

- Kaynak kod dosyasının üst satırlara kalan kodları konsept ve algoritmaları high-level olarak açıklayıcı şekilde olmalı, aşağı indikçe low-level detayları barındıran kodlar yer almalıdır.

- Değişkenler fonksiyonun başında tanımlanır ancak döngülerle ilgili kontrol değişkenleri, döngünün hemen üstünde tanımlanır.

- Sınıf yapılarındaki üye değişkenler (member fields) sınıfta en üstte yer alır.

- Birbiri ile bağlantılı method yapıları sınıf içerisinde birbirine yakın konumlandırılmalıdır. Bir method diğerini çağırıyorsa, çağıran method çağrılanın hemen üstünde olmalıdır.

- Kod yazarken girintileme (indentation) mutlaka kullanılmalı, kısa koşul ve döngü ifadelerinde bile kullanılmalıdır.

- Takım halinde yapılan proje geliştirmelerinde ortak bir formatta yani ortak bir kodlama stilinde kod yazılmalıdır.

## Sınıflar

- Sınıflar değişkenlerle birlikte başlar. Public static constant değişkenler sınıfın en başında yer alır. Devamında private static değişkenler gelir. Ondan sonra ise private instance değişkenleri yer alır.

- Public fonksiyonlar değişkenlerden hemen sonra yer alır. Bir public fonksiyon tarafından çağırılan private fonksiyonlar, bu public fonksiyonun hemen altında konumlandırılır.

- Sınıf yapıları küçük olmalıdır. Fonksiyonların küçüklüğü noktasında satır sayıları fikir verirken, sınıflar noktasında sınıfa ait sorumluluk sayısı fikir verir. Sınıf isminin uzunluğundan sınıf yapısının sorumluluk anlamında genişliği anlaşılabilir.

- Çok sayıda, küçük ve tek amaca hizmet eden sınıf yapıları, az sayıda büyük sınıf yapılarından daha anlaşılır ve yönetilebilirdir. Çok sayıdaki küçük sınıf yapılarından yazılımcılar büyük resmi anlayamayacağını düşünerek kaçınırlar ancak bu yanlış bir tercihtir. İyi tanımlanmış ve isimlendirilmiş sınıf yapıları çok daha yönetilebilir ve anlaşılabilirdir. Bu sebeple yazılımı inceleyen kişinin aradığını, nerede bulabileceğini anlamasına yardımcı olan yapılar tasarlanmalıdır.

- Sınıf yapıları aynı zamanda "Open-Closed Principle" yaklaşımıyla tasarlanmalı. Yani yeni fonksiyonalite eklemeye açık fakat değişime kapalı olmalıdır. Yeni fonksiyonaliteler subclass'lar oluşturularak eklenir ve böylelikle diğer sınıf yapıları etkilenmez.
