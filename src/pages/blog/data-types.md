---
layout: "../../layouts/BlogLayout.astro"
title: "Data tipləri"
---

# Data Tipləri-Data Types

Proqram təminatında (software) ən vacib şey məlumatdır (data). Proqram yazarkən, məlumatları toplayır, emal edir və onlardan mənalı nəticələr əldə edirik. Məsələn, bir oyun yaratmaq və ya veb tətbiqləri qurmaq kimi proseslər hamısı məlumatlarla sıx əlaqəlidir.

Məlumatları düzgün idarə üçün müxtəlif məlumat tiplərindən(data types) istifadə olunur.

JavaScript də **8** data tip(data types) var:

- number
- string
- boolean
- undefined
- null
- bigint
- symbol
- object

Və bunlar iki kateqoriyaya bölünür: **primitiv** (primitive) və **primitiv olmayan** (non-primitiv) tiplər.

### Primitiv (primitive)

> **Object** istisna olmaqla, digər 7 tip primitivdir.

Primitiv dəyərlər aşağıdakı xüsusiyyətlərə malikdir:

- **immutable** dəyərlərdir: bir dəfə yaratdiqdan sonra dəyişmək olmaz.
- Onlar birbaşa **memory stack** də saxlanılır.

```js
let sayHi = "Salam!";
console.log(sayHi); // Salam!
console.log(sayHi[0]); // S
sayHi[0] = "T";
console.log(sayHi); // Salam!
```

Kodda göründüyü kimi, `string` **immutable** dəyərdir və dəyişdirilə bilmir.

### Memory stack nədir ?

Source for help:
https://www.youtube.com/watch?v=nCwQY8inRvU
https://frontendjoy.substack.com/p/javascript-data-types-27-quick-questions
