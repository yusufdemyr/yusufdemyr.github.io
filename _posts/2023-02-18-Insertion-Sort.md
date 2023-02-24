---
layout: post
title: "Insertion Sort"
draft: false
permalink: community/Sorting-Algorithms/Insertion Sort/
---

Günümüzün hızlı ve veri dolu dünyasında, sıralama algoritmaları oldukça önemlidir. En basit sıralama algoritmalarından biri olan Insertion Sort, küçük veri setleri için oldukça verimli bir seçenektir. Bu yazıda Insertion Sort nedir, nasıl çalışır ve ne zaman kullanılır gibi sorulara cevap vereceğim.

## Insertion Sort Nedir?
Insertion Sort, adından da anlaşılacağı gibi verileri sıralarken bir veri setindeki bir elemanı, sıralanmış diğer veri setleriyle karşılaştırır ve uygun konuma yerleştirir. Bu işlem, diğer sıralama algoritmalarına kıyasla oldukça basit ve anlaşılırdır. Ancak, bu algoritma daha büyük veri setleri için yavaş çalışabilir.

## Nasıl Çalışır?
Insertion Sort algoritması, bir döngü içinde her elemanı sırayla işler. Bu döngü her elemanın, sıralanmış diğer elemanlarla karşılaştırılarak doğru konuma yerleştirilene kadar devam eder.

Adım adım Insertion Sort algoritmasının çalışma prensibini inceleyelim:
<ol><li><p>İlk eleman sıralanmış olarak kabul edilir.</p></li><li><p>Sonraki eleman, sıralı bölgedeki diğer elemanlarla karşılaştırılır ve uygun yere yerleştirilir.</p></li><li><p>Bu işlem, tüm elemanlar sıralanana kadar devam eder.</p></li></ol>

İşte bir örnek C kodu, belirtilen bir dizi için Insertion Sort algoritmasını kullanarak sıralama yapar:

~~~c
#include <stdio.h>

// Insertion Sort algoritması
void insertionSort(int arr[], int n) {
   int i, key, j;
   for (i = 1; i < n; i++) { // dizinin 2. elemanından başlayarak son elemana kadar gezin
       key = arr[i]; // geçici olarak i. elemanı key değişkenine atayın
       j = i - 1; // j değişkeni, i. elemanın solundaki son elemanı gösterir
       while (j >= 0 && arr[j] > key) { // i. elemanın solundaki elemanlarla karşılaştırma yaparak elemanları kaydırın
           arr[j + 1] = arr[j];
           j = j - 1;
       }
       arr[j + 1] = key; // i. elemanın doğru pozisyona yerleştirin
   }
}

int main() {
   int arr[] = { 12, 11, 13, 5, 6 }; // sıralanacak dizi
   int n = sizeof(arr) / sizeof(arr[0]); // dizinin boyutu
   int i;
   printf("Before sorting:\n"); // sıralama öncesi diziyi yazdırın
   for (i = 0; i < n; i++) {
       printf("%d ", arr[i]);
   }
   printf("\n");

   insertionSort(arr, n); // Insertion Sort algoritmasını kullanarak diziyi sıralayın

   printf("After sorting:\n"); // sıralama sonrası diziyi yazdırın
   for (i = 0; i < n; i++) {
       printf("%d ", arr[i]);
   }
   printf("\n");

   return 0; // programı sonlandırın
}
~~~
Output:
```python
Before sorting:
12 11 13 5 6
After sorting:
5 6 11 12 13 
```
<img src="../../assets/asset.png"> 
<style>
    th, td {
  padding-top: 3.5px;
  padding-bottom: 5px;
  padding-left: 7.5px;
  padding-right: 10px;
}
</style>
<table><thead><tr><th>Adım</th><th>Dizi</th><th>Açıklama</th></tr></thead><tbody><tr><td>1</td><td>12 11 13 5 6</td><td>İlk durum</td></tr><tr><td>2</td><td>11 12 13 5 6</td><td>11 ve 12 yer değiştirir</td></tr><tr><td>3</td><td>11 12 13 5 6</td><td>13 doğru yere yerleştirilir</td></tr><tr><td>4</td><td>11 12 13 5 6</td><td>5 sıralanmış kısma eklenir</td></tr><tr><td>5</td><td>5 11 12 13 6</td><td>6 sıralanmış kısma eklenir</td></tr><tr><td>6</td><td>5 11 12 13 13</td><td>Son eleman, doğru yere yerleştirilir</td></tr><tr><td>7</td><td>5 11 12 12 13</td><td>13, 12'nin sağ tarafına yerleştirilir</td></tr><tr><td>8</td><td>5 11 11 12 13</td><td>12, 11'in sol tarafına yerleştirilir</td></tr><tr><td>9</td><td>5 11 12 13 6</td><td>6 sıralanmış kısma eklenir</td></tr><tr><td>10</td><td>5 11 12 12 13</td><td>6, 12'nin sol tarafına yerleştirilir</td></tr><tr><td>11</td><td>5 11 11 12 13</td><td>6, 11'in sol tarafına yerleştirilir</td></tr><tr><td>12</td><td>5 6 11 12 13</td><td>5 sıralanmış kısma eklenir</td></tr><tr><td>Son</td><td>5 6 11 12 13</td><td>Sıralama tamamlandı</td></tr></tbody></table>

Farkedebileceğiniz seçili eleman `arr[j] > key` durumu var ise sürekli soluyla yer değiştiriyor. Yani soldaki eleman keyden büyükse key'i soldaki eleman olarak değiştiriyor`arr[j + 1] = arr[j];`. Eğer kendisinden daha küçük elemanla karşılaşırsada `arr[j + 1] = key;` sayesinde bir sola kaydırılıyor ve her adımda `j = i - 1;` çalıştığından sürekli kaydırılarak while döngüsü `arr[j] > key` durumu sağlanana kadar sola kaydırılıyor .

## Ne zaman kullanılır?

Insertion sort algoritması, küçük veri kümelerinde oldukça etkili olan bir sıralama algoritmasıdır. Bu algoritmanın en büyük avantajı, veri kümesindeki eleman sayısı arttıkça diğer sıralama algoritmalarına kıyasla daha yavaş olmasıdır. Bu nedenle, özellikle küçük veri kümelerinde performansı yüksek olduğu için, rekabetçi programlama yarışmalarında sıklıkla kullanılır.

Insertion sort, veri kümesindeki elemanların sayısı az olduğunda (örneğin, n <= 1000) veya veri kümesi nispeten sıralı ise özellikle yararlıdır. Ayrıca, insertion sort algoritması, nispeten düşük bellek tüketimi gerektirdiği için, sınırlı bellekli cihazlar veya sınırlı kaynaklara sahip ortamlar için de tercih edilebilir.

Bununla birlikte, insertion sort algoritması, veri kümesindeki elemanların sayısı çok büyük olduğunda, diğer daha verimli sıralama algoritmaları (örneğin merge sort, quick sort veya heap sort) daha avantajlı hale gelebilir. Bu nedenle, veri kümesinin boyutu büyük olduğunda insertion sort algoritması tercih edilmemelidir.

Özetle, küçük boyutlu veri kümeleri ve sınırlı bellek/kaynak ortamları için insertion sort algoritması kullanılabilir. Ancak, büyük boyutlu veri kümeleri için daha verimli algoritmalar kullanmak daha uygundur.