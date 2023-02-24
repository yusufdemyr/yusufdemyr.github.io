---
layout: post
title: "Zaman, Yürütme ve Bellek Karmaşıklıkları"
categories: [algorithm,community]
draft: false
permalink: /community/:title/
---

<style>
hr{
  border-top: 8px solid #bbb;
  border-radius: 5px;
}
</style>
Bir algoritmanın performansı, işlem gücü ve bellek kullanımı gibi faktörlere göre değerlendirilir. İşlem gücünün ölçüsü zaman karmaşıklığıdır ve bellek kullanımı ise bellek karmaşıklığı olarak tanımlanır. İkisi de algoritmanın verimliliğini ve scalability'ini etkiler.

<h3>Yürütme Karmaşıklığı</h3>


Bir algoritmadaki yürütme zamanı, atama maliyeti olarak hesaplanabilir. T($$n$$) şeklinde gösterilen bu yürütme zamanı algoritmanın çalışması bitene kadar gerçekleştirilen geçen süredir. Bu karmaşıklık hesaplanırken tüm atama maliyetleri dikkate alınır.

```c
for(i=1; i<n;i++){
  for(j=i+1;j<=n;j++){
    if(A[i]==A[j]) return false;
    return true;
  }
}
```

Örneğin yukarıdaki algoritma T($$n^2$$)'den daha düşük bir yürütme zamanına sahiptir. Çünkü nxn şeklinde verilmiş olan bir matrisin sadece köşegenleri dahil olmayan üst üçgen matrisini kontrol eder.
<img src="/assets/yurutmezamani.png">
<hr>

<h3>Zaman Karmaşıklığı</h3>
{:.myClass}
Bir algoritmanın zaman karmaşıklığı, işlem sayısı ile ölçülür. Bir algoritmanın zaman karmaşıklığı, girdi boyutu artarken artan işlem sayısını gösterir. O($$n$$) gibi notasyonlar kullanılarak ifade edilir, burada "n" girdi boyutudur. Örneğin, O($$n^2$$) zaman karmaşıklığı girdi boyutunun kare ile artan işlem sayısını gösterir.
<li>Aşağıdaki örnek, bir dizinin elemanlarının toplamını bulan bir fonksiyonun zaman karmaşıklığını hesaplamayı gösterir.</li>

~~~c
#include <stdio.h>
#include <time.h>

int sum(int arr[], int n) {
    int result = 0;
    for (int i = 0; i < n; i++) {
        result += arr[i];
    }
    return result;
}

int main() {
    int arr[10000];
    for (int i = 0; i < 10000; i++) {
        arr[i] = i;
    }

    clock_t start = clock();
    int total = sum(arr, 10000);
    clock_t end = clock();

    double time_taken = ((double)(end - start)) / CLOCKS_PER_SEC;
    printf("Time taken: %f\n", time_taken);
    return 0;
}
~~~

Bu kod, `sum` fonksiyonunun 10000 elemanlı bir dizi üzerinde ne kadar süre çalıştığını ölçer. `clock` fonksiyonu, programın çalışma zamanını ölçmek için kullanılır. `CLOCKS_PER_SEC` değeri, bir saniyedeki clock tick sayısıdır.

Zaman karmaşıklığı, `sum` fonksiyonunun girdi boyutu n olduğu zaman O(n) dir. Yani, girdi boyutu 2 katına çıktığında, zaman karmaşıklığı 2 katına çıkar.

Main fonksiyonundan başlayarak algoritmamızı çalıştırdığımızda ilk for döngüsünde sabit olarak 1000 kez dönecektir bu bir sabit olduğundan dolayı zaman karmaşıklığı yaratmaz. <br>Fakat <code>int total = sum(arr,10000)</code> satırındaki fonksiyonun ikinci parametresindeki girdiğiye göre fonksiyondaki tekrarlama sayısı değişeceğinden bu bir zaman karmaşıklığı yaratır. <br>Bu algoritma için algoritmanın çalışma süresi ikinci parametre olarak girilen yani dizinin eleman sayısı arttıkça algoritmanın çalışma süreside artacaktır.

Eğer iki kere sum fonksiyonunu main içinde çalıştırsaydık bu sefer algoritmamızın karmaşıklığı $$n^2$$ olacaktı. Çünkü ilk fonksiyon $$n$$ kadar çalışacak ve ikinci fonksiyon $$n$$ kadar daha çalıştığında toplamda $$n^2$$ kadar sürede çalışmasını tamamlayacaktır.

Yürütme süresi, CPU'nun hızı, kullanılabilir bellek miktarı ve giriş verilerinin boyutu gibi faktörleri dikkate alarak, belirli bir donanım ve yazılım kurulumunda belirli bir kod parçasını çalıştırmak için gereken gerçek süreyi ifade eder. .

Zaman karmaşıklığı ise, bir algoritmanın yürütme süresinin girdi boyutuyla nasıl büyüdüğünün teorik bir ölçüsüdür. Yürütme süresinin büyüme hızı üzerinde bir üst sınır sağlar ve belirli donanım veya yazılım yapılandırmalarını hesaba katmadan algoritmaların verimliliklerine göre karşılaştırılmasına yardımcı olur.

Başka bir deyişle, zaman karmaşıklığı bize bir algoritmanın performansının nasıl ölçeklenmesinin beklendiği hakkında bir fikir verirken, gerçek yürütme süresi belirli bir ortamda nasıl performans gösterdiğinin somut bir ölçümüdür.
<hr>

<h3>Bellek Karmaşıklığı</h3>

Bellek karmaşıklığı, bir algoritmanın bellek kullanımını ölçer. Bir algoritmanın bellek karmaşıklığı, girdi boyutu artarken bellekte tutulan verilerin sayısını gösterir.
Yukarıdaki kodun bellek karmaşıklığı, yalnızca int tipinde 10,000 elemanlı bir dizi (arr) için gereken bellek miktarıdır. Bu bellek miktarı, her bir elemanın int tipinde veri saklamak için gereken bellek miktarının toplamıdır.

Örnek olarak, int tipinde bellek boyutu 4 bayt olduğu varsayılırsa, 10,000 elemanlı dizi için toplam bellek boyutu 4 * 10,000 = 40,000 bayt olacaktır.

<hr>
<h3>Sonuç</h3>
Her algoritma için en iyi zaman ve bellek karmaşıklığı O(1)dir, ancak bu tür algoritmalar her zaman mümkün değildir ve genellikle kabul edilebilir bir trade-off yapılması gerekir. Örneğin, daha hızlı bir algoritma daha fazla bellek kullanabilir veya daha az bellek kullanılan bir algoritma daha yavaş çalışabilir.

Sonuç olarak, Zaman karmaşıklığı genellikle O($$n$$) gibi big O notasyonuyla gösterilir ve algoritmanın en fazla ne kadar zaman harcayabileceğini gösterir. Bellek karmaşıklığı ise MB, GB gibi veri ölçü birimleriyle gösterilir ve algoritmanın en fazla ne kadar bellek kullanabileceğini gösterir. Algoritmaların zaman ve bellek karmaşıklığı, algoritmanın verimliliğini ve scalability'ini etkiler ve bu faktörler dikkate alınarak en uygun algoritma seçilmelidir.

<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>
