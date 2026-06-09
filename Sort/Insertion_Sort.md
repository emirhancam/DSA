# Insertion Sort

- Insertion Sort, dizinin sıralanmış kısmını her seferinde tek bir eleman alarak adım adım inşa eder.
- Sıralanmamış bir sonraki elemanı seçer ve onu halihazırda sıralanmış bölgenin içindeki doğru konuma yerleştirir.
- Algoritmanın çalışması esnasında dizi her zaman iki ana bölgeye ayrılır:
  1) Sıralanmış Bölge (Sol taraf) : Buradaki elemanlar birbirine göre doğru sıraladadır.
  2) Sıralanmamış Bölge (Sağ taraf) : Buradaki elemanlar henüz işleme alınmamıştır.
 
<img width="677" height="338" alt="image" src="https://github.com/user-attachments/assets/f256e5d7-1a82-4b41-a4fb-d67ccae9f3b9" />

- Algoritma, sağdaki sıralanmamış bölgeden ilk elemanı alıp soldaki sıralı bölgede olması gereken yere koyarken, araya yer açmak için kendinden büyük elemanları bir adım sağa kaydırır.

## Algoritma Adımları
1) İkinci elemandan (index = 1) başla. İlk eleman tek başına zaten sıralı kabul edilir.
2) Geçerli elemanı `key` adında geçici bir değişkene kaydet.
3) `key` değerini, sıralanmış bölgedeki elemanlarla sağdan sola doğru (geriye doğru) sırayla karşılaştır.
4) `key` değerinden daha büyük olan her elemanı bir pozisyon sağa kaydır.
5) Kaydırmalar sonucu oluşan boşluğa `key` değerini yerleştir.
6) Sıralanmamış bir sonraki elemana geç ve tüm dizi sıralanana kadar bu işlemleri tekrarla.

- Standart uygulama, elemanları birbirleriyle swap etmek yerine sağa kaydırma (shift) yöntemi kullanır.
- Kaydırma işlemi, swap'e göre daha verimlidir çünkü bir kaydırma işlemi tek bir atama yaparken, swapta 3 atama gerekir.

## Kodlama 

- C++
```cpp
void insertionSort(vector<int>& arr) {
    int n = arr.size();

    for (int i = 1; i < n; i++) {
        int key = arr[i];
        int j = i - 1;

        while (j >= 0 && arr[j] > key) {
            arr[j+1] = arr[j];
            j--;
        }

        arr[j+1] = key;
    }
}
```
- GO
```go
package main

func insertionSort(arr []int) {
	n := len(arr)

	for i := 1; i < n; i++ {
		key := arr[i]
		j := i - 1

		for j >= 0 && arr[j] > key {
			arr[j+1] = arr[j]
			j--
		}

		arr[j+1] = key
	}
}
```


Örnek:

`[7, 3, 5, 1, 9, 2]`

1.Adım : i = 1, key = 3  --> `[3, 7, 5, 1, 9, 2]`   
2.Adım : i = 2, key = 5  --> `[3, 5, 7, 1, 9, 2]`   
3.Adım : i = 3, key = 1  --> `[1, 3, 5, 7, 9, 2]`   
4.Adım : i = 4, key = 9  --> `[1, 3, 5, 7, 9, 2]`   
5.Adım : i = 5, key = 2  --> `[1, 2, 3, 5, 7, 9]`   

## Hangi Senaryolarda Kullanılmalı ? 
- Dizi zaten sıralanmaya çok yakınsa, insertion sort çok verimlidir. Adaptive yapısı sayesinde yer değiştirmesi gereken az sayıdaki elemanı sadece birkaç kaydırmayla çözer.
- 10-20 elemandan daha küçük dizilerde Merge veya Quick sort'un prosedür yükünden kurtardığı için pratikte onlardan daha hızlıdır.
- Veriler bir akış halinde sisteme tekrar tekrar ge liyorsa, listeyi her zaman sıralı tutmak için yeni gelen elemanı doğrudan kendi yerine sokarak harika bir iş çıkarır.

## Hangilerinde Uzak Durmalı ? 
- O(n^2) ortalama durumu sebebiyle O(n log n) algoritmalarıyla rekabet edemez. 1 milyon elemanlık rastgele bir veriyi sıralamak Merge sort ile 20 milyon işlem alırken, insertion sort ile ortalama 200 MİLYAR işlem alır.
- Sisteme girecek veri boyutunu veya ne kadar karışık olabileceğini garanti edemezsek, daha genel maksatlı algoritmalar kullanılmalı. 















