# bgp-201-odev3
[soru 1.txt](https://github.com/user-attachments/files/23424130/soru.1.txt)

mergeArrays fonksiyonu iki farklı tipte dizi alıyor (T[] ve U[]).
T ve U, jenerik tiplerdir (yani dinamik tip parametreleri).
(...arr1, ...arr2) ifadesiyle spread operatörü kullanılarak diziler birleştirilir.
Dönüş tipi (T | U)[], yani iki dizideki elemanlar her iki tipin birleşimi olabilir.
Böylece [1, 2, 3] ve ["a", "b", "c"] dizilerini birleştirip [1, 2, 3, "a", "b", "c"] çıktısını alıyoruz.


[soru2.txt](https://github.com/user-attachments/files/23424264/soru2.txt)

Car ve Truck sınıfları benzer metodlara sahip ama Truck’ta ekstra loadCargo() var.
Vehicle tipi, birleşim tipidir (Car | Truck).
useVehicle() fonksiyonunda, vehicle.drive() her iki tipte de vardır, o yüzden doğrudan çağrılır.
Ancak loadCargo() sadece Truck’ta olduğundan önce if ("loadCargo" in vehicle) ile tip koruyucusu (type guard) kullanılır.
Bu sayede TypeScript vehicle’ın bir Truck olduğunu anlar ve loadCargo() çağrılabilir hale gelir.


[soru3.txt](https://github.com/user-attachments/files/23424281/soru3.txt)

private logHistory özelliği sadece sınıf içinde erişilebilir; dışarıdan (logger.logHistory) erişmek hata verir.
log(message) metodu: hem console.log() ile mesajı yazdırır hem de logHistory dizisine ekler.
getHistory() metodu: geçmişte kaydedilen tüm logları döndürür.
Bu yapı, enkapsülasyon (encapsulation) ilkesine örnektir — iç veriler gizlenir, sadece kontrollü şekilde erişim sağlanır


[soru4.txt](https://github.com/user-attachments/files/23424288/soru4.txt)

keyof T ifadesi, T tipindeki tüm anahtarların birleşimini temsil eder.
→ Örneğin user nesnesi için keyof typeof user = "name" | "age" olur.
K extends keyof T diyerek key parametresini sadece bu anahtarlardan biriyle sınırlandırıyoruz.
Fonksiyonun dönüş tipi T[K], yani anahtarın değerinin tipi oluyor.
→ "name" gönderilirse string, "age" gönderilirse number döner.
Bu sayede tip güvenli bir şekilde nesne özelliklerine erişim sağlanmış olur. 



[soru5.txt](https://github.com/user-attachments/files/23424291/soru5.txt)

Fonksiyon overload sayesinde aynı fonksiyon ismini farklı parametre türleriyle kullanabiliyoruz.
search(param: number) → bir kullanıcı döndürür (User | undefined).
search(param: string) → bir kullanıcı dizisi döndürür (User[]).
typeof kontrolü ile hangi overload’ın çalışacağını belirliyoruz:
number → find() ile tek kullanıcıyı bulur.
string → filter() ile ismi eşleşen kullanıcıları döndürür.
TypeScript, overload’lar sayesinde dönüş tipini otomatik olarak doğru şekilde çıkarır. 


[soru6.txt](https://github.com/user-attachments/files/23424299/soru6.txt)

private data = new Map<K, V>() → TypeScript’in Map yapısını kullanıyoruz (anahtar-değer ilişkisi tutar).
set() → belirtilen anahtar-değer çiftini kaydeder.
get() → anahtara göre veriyi getirir.
clear() → tüm kayıtları siler.
Bu sayede bellek içinde çalışan, küçük bir önbellek (cache) mekanizması oluşturulmuş olur.



[soru7.txt](https://github.com/user-attachments/files/23424305/soru7.txt)

Partial<User> → User tipindeki tüm alanları isteğe bağlı hale getirir.
(Yani sadece güncellenmesi gereken alanları gönderebilirsin.)
Readonly<User> → Dönen değerin değiştirilemez (immutable) olmasını sağlar.
Object.assign({}, user, updates) →
user nesnesinin bir kopyasını alır ve updates’teki alanları bu kopya ile birleştirir.
Fonksiyon, güncellenmiş kullanıcıyı döndürür ama orijinal users dizisini değiştirmez. 



[soru8.txt](https://github.com/user-attachments/files/23424392/soru8.txt)

...numbers: number[] → Rest parametresidir.
Fonksiyona kaç tane argüman verilirse verilsin, hepsi numbers dizisinde toplanır. reduce() → Dizideki tüm sayıları sırayla toplar.
(total, num) => total + num ifadesi her elemanı birikimli şekilde ekler. Başlangıç değeri 0 olduğu için boş liste verilse bile hata vermez.



[soru9.txt](https://github.com/user-attachments/files/23424396/soru9.txt)

abstract class Shape → Soyut sınıftır, doğrudan örneklenemez.
abstract getArea(): number → Bu metodun alt sınıflarda zorunlu olarak tanımlanması gerekir.
Circle sınıfı Shape’ten türediği için getArea() metodunu kendi içinde tanımlar.
Alan formülü: π × r²
(Math.PI * radius * radius) 



[soru10.txt](https://github.com/user-attachments/files/23424407/soru10.txt)

static anahtar kelimesiyle tanımlanan özellikler ve metotlar sınıfa ait olur, örneğe (new MathHelper()) değil.
MathHelper.PI doğrudan sınıf adıyla erişilir.
calculateCircumference → çevre formülü 2 × π × r’yi hesaplar.
Bu yüzden nesne oluşturmadan MathHelper.calculateCircumference(10) şeklinde çağırabiliyoruz. 



[soru11.txt](https://github.com/user-attachments/files/23424438/soru11.txt)

T extends Promise<infer U> ? U : T: Eğer T bir Promise<...> ise iç tip U’yu çıkarır; değilse T’yi aynen döndürür.
UnwrapPromise<pNum> → number, UnwrapPromise<number> → number. "string" ataması beklenen şekilde tip hatası verir. 



[soru12.txt](https://github.com/user-attachments/files/23424456/soru12.txt)

(...args: any[]) infer R kalıbı ile fonksiyonun dönüş tipini R olarak yakalıyoruz.
Fonksiyon değilse never döner. typeof fn1 ⇒ string, typeof fn2 ⇒ number; yanlış atama beklenen hatayı üretir.



[soru13.txt](https://github.com/user-attachments/files/23424461/soru13.txt)

mapped type ile her K anahtarını get${Capitalize<K>} adına dönüştürüyoruz (as ile yeniden adlandırma).
Değer tipi () => T[K]: orijinal özelliğin tipini döndüren bir getter.
string & K anahtarın string olarak işlenmesini sağlar; Capitalize ilk harfi büyütür.
Böylece { id: number; name: string } → { getId: () => number; getName: () => string }.



[soru14.txt](https://github.com/user-attachments/files/23424469/soru14.txt)

Fonksiyonlar değişmeden bırakılır (readonly anlamsızdır).
Diziler ReadonlyArray<...>’a dönüştürülür; elemanları da derin readonly yapılır (bu yüzden push hatalı).
Nesnelerde tüm alanlar readonly olur ve her alan için yine DeepReadonly uygulanır.
İlkel tipler (string, number, vb.) aynen döner. 



[soru15.txt](https://github.com/user-attachments/files/23424485/soru15.txt)

as ile anahtar yeniden adlandırma yapıyoruz: T[K] V’ye uyuyorsa K, yoksa never (atar ve eler).
Sonuç: Sample içinden string | number değerli alanlar seçilir → { name: string; age: number }. 



[soru16.txt](https://github.com/user-attachments/files/23424497/soru16.txt)

Brand<K, T>: Temel tip K’yi (örneğin string) ve markayı (T) birleştirir.
UserID ve PostID her ikisi de string’dir ama farklı “brand”’e sahip oldukları için birbirine atanamazlar.
logID fonksiyonu string kabul ettiği için, branded tipler string olarak da geçerlidir.
@ts-expect-error satırında tip hatası beklenir .
UserID ≠ PostID, ikisi de string gibi davranır. 



[soru17.txt](https://github.com/user-attachments/files/23424521/soru17.txt)

T extends U ? never : T ifadesi, dağıtılmış koşullu tip örneğidir.
AllStatus 'pending' | 'active' | 'inactive' | 'deleted'’e dağıtılır ve her parça U’ya (ActiveStatus) uyuyorsa never olur.
'pending' ve 'active' elenir, kalan 'inactive' | 'deleted' kalır.
Böylece InactiveStatus = 'inactive' | 'deleted' olur.
pending atanırken hata verir 



[soru18.txt](https://github.com/user-attachments/files/23424523/soru18.txt)

(...args: [...infer _Rest, infer L]) ile fonksiyonun parametrelerini dağıtıp son elemanı L olarak yakalıyoruz.
Koşullu tip: Fonksiyon tipine uyuyorsa L, yoksa never.
fn1 için boolean, fn2 için Date döner; yanlış atamada beklenen tip hatası oluşur.



[soru19.txt](https://github.com/user-attachments/files/23424530/soru19.txt)

T extends (infer U)[] ? U : T: Eğer T bir dizi tipiyse eleman tipini U olarak yakalar ve döner; değilse T’yi aynen döndürür.
Böylece Flatten<number[]> = number, Flatten<string> = string.
Yanlış atama ("string" → number) beklenen tip hatasını üretir.



[soru20.txt](https://github.com/user-attachments/files/23424535/soru20.txt)

Şablon ayrıştırma: /:${infer P}/${infer R} ile sıradaki param adı P, kalan rota R olarak yakalanır.
Rekürsiyon: Bulunan anahtar { [K in P]: string } ile eklenir ve kalan rota için tekrar çağrılır.
Son parça için ikinci dal: /:${infer P} ➝ tek bir { [K in P]: string }.
Parametre yoksa {} döner. Bu sayede /users/:id → { id: string }, /posts/:postId/comments/:commentId → { postId: string; commentId: string }.
