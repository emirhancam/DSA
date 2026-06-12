# Shell Sort
- Shell sort, birbirinden uzak olan elemanların yer değiştirmesine izin vererek Insertion Sort'un genelleştirilmiş bir versiyonudur.
- Sadece yan yana duran elemanları karşılaştırmak yerine, aralarında belirli bir "gap" bulunan elemanları karşılaştırır ve bu boşlukla ayrılmış her bir eleman grubuna Insertion Sort uygular.
- Ardışık geçişlerde bu boşluk 1 olana kadar küçülür; boşluk 1 olduğunda algoritma artık "neredeyse sıralı" durumdaki dizi üzerinde normal insertion sort işlemi yapar.
- Insertion Sort'ta, her eleman yalnızca hemen yanındaki komşusuyla karşılaştırılabilir. Shell sort ise elemanların tek adımda uzun mesafeler atlamasına izin vererek toplam işlem sayısını büyük ölçüde azaltır.

 ## Nasıl Çalışır ?
 - 3 seviyeli bir döngü yapısını takip edeceğiz:
   1) Başlangıç boşluğu (gap) seç. Genellikle dizi boyutunun yarısı olan n/2 ile başlanır.
   2) Geçerli boşluk değeri için, boşluklu bir insertion sort uygula
   3) Boşluğu küçült (genelde yarıya indirilir) ve gap = 1 olana kadar tekrarla.

- Gap, 1'den büyük olduğunda, algoritma gap kadar uzaktaki elemanları gruplandırır ve her bir grubu kendi içinde insertion sort kullanarak sıralar.
- Gap azaldıkça gruplar daha fazla örtüşmeye başlar.
- Gap 1'e ulaştığında ise yapılan işlem standart bir insertion sorttur, ancak dizi zaten büyük oranda sıralı hale geldiği için işlemler çok hızlı biter.

### KOD

#### C++
```cpp
#include <vector>

void shellSort(std::vector<int>& arr) {
    int n = arr.size();

    for (int gap = n / 2; gap > 0; gap /= 2) {
        for (int i = gap; i < n; i++) {
            int temp = arr[i];
            int j = i;

            while (j >= gap && arr[j - gap] > temp) {
                arr[j] = arr[j - gap];
                j -= gap;
            }

            arr[j] = temp;
        }
    }
}
```

#### Go

```go
package main

type ShellSort struct{}

func (s *ShellSort) Sort(arr []int) {
	n := len(arr)

	for gap := n / 2; gap > 0; gap /= 2 {
		for i := gap; i < n; i++ {
			temp := arr[i]
			j := i

			for j >= gap && arr[j-gap] > temp {
				arr[j] = arr[j-gap]
				j -= gap
			}

			arr[j] = temp
		}
	}
}
```

**Örnek:** `[12, 34, 54, 2, 3]` n = 5

// to be continued












