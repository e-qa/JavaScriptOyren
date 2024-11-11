---
layout: "../../layouts/Layout.astro"
title: "Hoisting"
path: "hoisting"
---

# Hoisting

JavaScript mühərriki (engine), JavaScript kodunu icra edərkən bir icra konteksti (execution context) yaradır və bunun iki mərhələsi var:

- Yaradılış (Creation)
- İcra (Execution)

Yaradılış mərhələsində (Creation), JavaScript mühərriki dəyişən və funksiyaları kodun ən yuxarı hissəsinə qaldırır. Bu proses "hoisting" deyilir.

Aşağıda göstərilən nümunədə JavaScript dəyişəni yuxarı qaldırıldığı (hoisting) üçün səhv vermir:

```js
console.log(sayHi); // undefined
var sayHi = "Hello";
```

Yuxarıdakı kod, aşağıdakı kimi işləyir:

```js
var sayHi;
console.log(sayHi); // undefined
sayHi = "Hello";
```

Yaradılış (creation) mərhələsində, JavaScript mühərriki dəyişəni (variable) yaddaşa yerləşdirir `undefined` dəyərini verir.

### Let ilə hoisting

İndi isə həmin kodu `let` açar sözü ilə yazaq:

```js
console.log(sayHi);
let sayHi = "Hello";
```

Burada JavaScript xətası verəcək: _"ReferenceError: Cannot access 'sayHi' before initialization"_

Xətadan göründüyü kimi, `sayHi` dəyişəni artıq yaradılıb, `let` və `const` ilə yaradılmış dəyişənlər hoisting edilir, ancaq JavaScript onu bizim üçün əlçatan etmir.

```js
console.log(learnJavaScript);
let x = Math.random() * 10;
```

Burada `learnJavaScript` adlı dəyişən yaradılmadığı üçün JavaScript xətası verəcək: _"ReferenceError: learnJavaScript is not defined"_

**Bu qayda const üçün də keçərlidir.**

### Funksiya Hoisting

Dəyişənlər kimi, JavaScript mühərriki funksiyaları da yuxarı qaldırır (hoisting).

```js
let result = sum(2, 4);
console.log(result); // 6

function sum(a, b) {
  return a + b;
}
```

Yuxarıdakı kod, aşağıdakı kimi işləyir:

```js
function sum(a, b) {
  return a + b;
}

let result = sum(2, 4);
console.log(result); // 6
```

### Function expressions

```js
let result = sum(2, 4);
console.log(result); // Uncaught ReferenceError: sum is not defined

const sum = (a, b) => {
  return a + b;
};
```

Burada JavaScript `sum`-ı dəyişən kimi qəbul edir və yaradılış mərhələsində `sum` "undefined" olur.

**Bu qayda arrow function-lar üçün də keçərlidir.**
