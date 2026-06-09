# Selection Sort
- Büyük veri setleri için çok verimli olmasa da karşılaştırmalar, değiştirmeler (swap) arasındaki dengeyi gösterir.
- Bu özellik sayesinde algoritmaların birbirinden nasıl farklılaştığını anlamanın yolu bulunmuş oluyor.

## Selection Sort Nedir? 
- Selection sort, karşılaştırmaya dayalı bir algoritmadır.
- Sıralama işleminin herhangi bir noktasında bütün dizi 2 ana bölgeye ayrılır:
  1) Sıralanmış Bölge (Sol Taraf)
  2) Sıralanmamış Bölge (Sağ Taraf)

<img width="589" height="100" alt="image" src="https://github.com/user-attachments/assets/c12f6f0d-c721-412f-87c4-9e5c14759fd1" />

- Algoritma her bir adımda sıralanmamış bölgedeki en küçük elemanı bulup seçer ve bu elemanı sıralanmamış bölgenin ilk elemanıyla yer değiştirir.
- Bu işlem, sıralanmış bölgeyi bir eleman büyütürken, sıralanmamış bölgeyi bir eleman küçültür.

## Algoritma
- Algoritma temelde 5 akış adımından oluşur:
  1) Başlangıçta ilk konumu (index = 0) geçerli konum (current position) olarak belirle.
  2) En küçük elemanın indexini bulmak için sıralanmamış bölgeyi tara.
  3) Bulunan en küçük elemanı, geçerli konumdaki elemanla yer değiştir.
  4) Geçerli konumu bir adım sağa kaydır.
  5) Geçerli konum sondan bir önceki elemana ulaşana kadar 2-4 adımlarını tekrarla.
 
```cpp
#include <vector>
#include <algorithm>

void selectionSort(std::vector<int>& arr) {
    int n = arr.size();

    for (int i = 0; i < n - 1; i++) {
        int minIndex = i;
        for (int j = i + 1; j < n; j++) {
            if (arr[j] < arr[minIndex]) {
                minIndex = j;
            }
        }

        if (minIndex != i) {
            std::swap(arr[i], arr[minIndex]);
        }
    }
}
```

**Örnek : [29, 10, 14, 37, 13] **   

- 1.Geçiş : ` [10, 29, 14, 37, 13] `   --> 29 ve 10 yer değiştirdi.
- 2.Geçiş : ` [10, 13, 14, 37, 29] `   --> 29 ve 13 yer değiştirdi.
- 3.Geçiş : ` [10, 13, 14, 37, 29] `   --> Takasa gerek yok bu adımda.
- 4.Geçiş : ` [10, 13, 14, 29, 37] `   --> 37 ve 29 yer değiştirdi.














