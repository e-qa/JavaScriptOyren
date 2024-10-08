---
layout: "../../layouts/Layout.astro"
title: "Data tipləri"
path: "/blog/data-types"
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

- Primitiv məlumat növləri yalnız bir dəyər saxlaya bilər.
- **İmmutable** dəyərlərdir: bir dəfə yaratdiqdan sonra dəyişmək olmaz.
- Onlar **memory stack** də saxlanılır.

```js
let sayHi = "Salam!";
console.log(sayHi); // Salam!
console.log(sayHi[0]); // S
sayHi[0] = "T";
console.log(sayHi); // Salam!
```

Kodda göründüyü kimi, `string` **immutable** dəyərdir və dəyişdirilə bilmir.

2-ci nümunəyə baxaq:

```js
let name = "JavaScript";
name = "Typescript";
```

Burada `name` dəyişənini "TypeScript" ilə yenidən təyin etdik (reassign). İlk baxışda `name` dəyişmiş kimi görünsə də, əslində yaddaşda `name` adlı yeni bir yer yaradıldı və "TypeScript" dəyəri ora yazıldı. `name` dəyişəni artıq "JavaScript" dəyərini saxlamır "TypeScript" dəyərinə işarə edir.

> Bütün primitive data tipləri immutable-dır, çünki onların dəyərləri heç vaxt dəyişmir. Bu o deməkdir ki, bir primitive dəyəri dəyişdirdikdə, yeni bir dəyər yaradılır və bu yeni dəyər yaddaşda yeni bir yerə yazılır.

### Memory stack nədir?

Məlumatlarımızı saxlamaq və yazmaq üçün bir yerə ehtiyacımız var. JavaScript-də **heap** və **stack** adlanan iki əsas yaddaş sahəsi mövcuddur.

**Stack**: Statik məlumatları (sabit ölçülü verilənlər) saxlayır. Primitive dəyərlər dəyişməz və sabit olduğuna görə burada saxlanılır.

**Heap**: Dinamik məlumatları saxlayır. Obyetlər (objects), massivlər (arrays) və funksiyalar (functions) kimi daha mürəkkəb verilənlər burada saxlanılır. Heap-də verilənlər dinamik olaraq yaradılır və ölçüləri dəyişə bilir.

### Primitiv olmayan (non-primitiv)

Obyekt tipi yeganə qeyri-primitiv məlumat növüdür(data type). JavaScript-də hər şey Obyet olduğu üçün bura `function` `array` də daxildir.

non-primitiv dəyərlər aşağıdakı xüsusiyyətlərə malikdir:

- Primitiv olmayan data tipləri çoxlu dəyər saxlaya bilər.
- **Mutable** dəyərlərdir: dəyərləri(value) dəyişə bilər
- Onlar **memory Heap** də saxlanılır.

```js
let numbers = [2, 4, 6, 8, 10];
numbers.push(12);
console.log(numbers); // [2,4,6,8,10,12]
```

Obyektlər mutable dəyər olduğu üçün onların dəyərlərini dəyişdirmək mümkündür. Bu nümunədə `numbers` massivi əvvəlcə `[2, 4, 6, 8, 10]` dəyərlərini sağlayır. `push` metodu ilə massivin sonuna `12` dəyəri əlavə edirik. Bu zaman `numbers` massivi yaddaşda eyni yerdə qalır, amma içindəki dəyərlər dəyişir. Yəni, obyektin içərisindəki dəyərləri dəyişdirərək, yaddaşda eyni yerə işarə etməyə davam edirik.

<br/>
<br/>
<br/>

| Primitive                                                                        | Non-Primitive                                        |
| -------------------------------------------------------------------------------- | ---------------------------------------------------- |
| Number, string, boolean, undefined, null, bigint, symbol primitiv data tiplərdir | Object, array, functions non-primitiv data tiplərdir |
| Yalnız bir dəyər saxlaya bilər.                                                  | Çoxlu dəyər saxlaya bilər.                           |
| İmmutable dəyərlərdir                                                            | Mutable dəyərlərdir                                  |
| Stack də saxlanılır.                                                             | Heap də saxlanılır.                                  |
