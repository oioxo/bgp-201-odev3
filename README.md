[soru 1.txt](https://github.com/user-attachments/files/23424130/soru.1.txt)

mergeArrays fonksiyonu iki farklı tipte dizi alıyor (T[] ve U[]).
T ve U, jenerik tiplerdir (yani dinamik tip parametreleri).
(...arr1, ...arr2) ifadesiyle spread operatörü kullanılarak diziler birleştirilir.
Dönüş tipi (T | U)[], yani iki dizideki elemanlar her iki tipin birleşimi olabilir.
Böylece [1, 2, 3] ve ["a", "b", "c"] dizilerini birleştirip [1, 2, 3, "a", "b", "c"] çıktısını alıyoruz.
