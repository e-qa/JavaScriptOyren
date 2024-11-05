---
layout: "../../layouts/Layout.astro"
title: "Deep və shallow copy"
path: "deep-vs-shallow-copy"
---

# Deep copy və Shallow copy

Kopyalama (copy) nədir?
Bir şeyi kopyalamaq istəyəndə orijinalını dəyişmədən kopyası üzərində dəyişikliklər etmək istəyirik. Yəni, gözləyirik ki, orijinal eyni qalsın, yalnız kopyalanmış dəyişsin.

### Primitive Tiplər

JavaScript-də [Primitive tiplər ](/blog/data-types) kopyalandığı zaman yeni dəyərlər yaradılır və orijinal dəyərlərə toxunulmur.

Məsələn:

```javascript
const a = 10;
let b = a; // 'b' yeni bir dəyər alır
b = 20;
console.log(a); //10
console.log(b); //20
```

Bu nümunədə, `b` dəyişəni `a` dəyişəninin dəyərini kopyalayır, amma bu kopyalama `a` dəyişəninin referansını saxlamır. Primitive tiplər kopyalananda yeni dəyərlər yaradılır. Bu səbəbdən, `b`-daki dəyişiklik `a`-ya təsir etmir, orijinal `a` dəyəri eyni qalır.

amma obyektlər daha mürəkkəb strukturlardır. Onların kopyalanması zamanı **Shallow Copy** və **Deep Copy** anlayışları tətbiq edilir.

### Copy

JavaScript-də obyektlərin kopyalanması üçün aşağıdakı üç üsuldan istifadə olunur:

**Spread Operator (`...`)**:

```javascript
const person = { name: "Eli", surname: "Qarayev" };
let person1 = { ...person }; // shallow copy
```

**Object.assign()**:

```javascript
const person = { name: "Eli", surname: "Qarayev" };
let person1 = Object.assign({}, person); // shallow copy
```

**JSON.stringify()** və **JSON.parse()**:

```javascript
let person3 = JSON.parse(JSON.stringify(person)); // deep copy
```

### Shallow Copy

Shallow Copy bir obyektin ilk leveldəki xüsusiyyətlərinin kopyalayir. Əgər orijinal obyekt içində başqa obyektlər varsa, bu iç kopyalanmır.

```javascript
const original = { name: "Eli", hobbies: ["music", "sports"] };
const shallowCopy = { ...original };

shallowCopy.hobbies.push("reading");

console.log(original.hobbies); // ["music", "sports", "reading"]
console.log(shallowCopy.hobbies); // ["music", "sports", "reading"]
```

Bu nümunədə, `shallowCopy` kopyası original obyektinin hobbies dizəsinin referansını saxlayır. Bu səbəbdən, `shallowCopy` içindəki hobbies-ə yeni bir dəyər əlavə edildikdə, original obyektində də bu dəyişiklik görünür.

### Deep Copy

Deep Copy isə bir obyektin bütün level dəyərlərinin kopyalanmasıdır. Yəni, orijinal obyekt içindeki bütün alt obyektlər kopyalanır. Bu sayədə, kopyalanan obyekt orijinal obyekt ilə heç bir əlaqəsi qalmir.

```javascript
const original = { name: "Eli", hobbies: ["music", "sports"] };
const deepCopy = JSON.parse(JSON.stringify(original));

deepCopy.hobbies.push("reading");

console.log(original.hobbies); // ["music", "sports"]
console.log(deepCopy.hobbies); // ["music", "sports", "reading"]
```

Bu nümunədə, `deepCopy` kopyası original obyektinin hobbies dizəsini tamamilə ayrı bir dizi kimi kopyalayır. Bu səbəbdən, `deepCopy`-ə yeni bir dəyər əlavə edildikdə, original obyektində heç bir dəyişiklik baş vermir.
