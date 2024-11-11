---
layout: "../../layouts/Layout.astro"
title: "Spread və Rest"
path: "spread-rest"
---

# Rest və Spread Operatorları

JavaScript-də Rest operatoru funksiyaya müəyyən sayda arqument götürmək əvəzinə, istənilən sayda arqument götürməyə imkan verir. Bu, neçə arqumentin ötürüldüyünü əvvəlcədən bilmədən arqumentləri funksiyaya dinamik şəkildə ötürməyə şərait yaradır.

### Rest Operatoru:

```javascript
function collectArgs(...args) {
  console.log(args); // args is an Array
}

collectArgs(1, 2, 3, 4); // [1, 2, 3, 4]
```

> Rest operatoru funksiyanın arqumentlər siyahısının sonunda istifadə olunur və bütün ötürülən arqumentləri bir arraydə toplayır.

### Spread Operatoru:

> Spread operatoru da üç nöqtə (...) ilə işarələnir, lakin fərqli olaraq, array və ya obyekt elementlərini ayrı-ayrılıqda yaymağa xidmət edir.

```javascript
const numbers = [1, 2, 3];

function sum(x, y, z) {
  return x + y + z;
}

console.log(sum(...numbers)); // 6
```

### Rest və Spread Operatorlarını Necə Ayırmaq Olar:

- Əgər `...` funksiyanın arqumentlər siyahısının sonunda istifadə olunursa, bu, rest operatorudur və ötürülən arqumentlərin qalan hissəsini bir arraydə toplamaq üçündür.

- Əgər `...` funksiya çağırışı zamanı və ya obyektlərin yayılması ilə əlaqədar istifadə olunursa, bu, spread operatorudur və array və ya obyektin elementlərini tək-tək yaymaq üçün istifadə edilir.
