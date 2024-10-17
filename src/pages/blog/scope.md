---
layout: "../../layouts/Layout.astro"
title: "Scope"
path: "scope"
---

# Scope

> Scope, kodun icra olunması zamanı dəyərlərin və funksiyaların görünür olduğu əhatə dairəsidir.

JavaScript-də üç əsas scope növü var:

- Global Scope
- Function Scope
- Block Scope

`var`: <mark style="background-color:yellow color:white">global scope, function scope.</mark>
`let` və `const`: <mark style="background-color:yellow; color:black">global scope, function scope, block scope. </mark>

### Global Scope

JavaScript faylında kod yazmağa başladığınız zaman, bu kod global scope-da yerləşir. Global scope-da təyin olunan dəyişənlər hər yerdən əlcatandır. Bir JavaScript faylında yalnız bir qlobal scope var.

```js
var name = "Ramiz";
console.log(name); // Ramiz
```

Qlobal scope-da olan dəyişənlər hər yerdən əlcatandır və onları dəyişmək mümkündür.

```js
var name = "Ramiz";
console.log(name); // Ramiz

function displayName() {
  console.log(name); // Ramiz
}
displayName(); // Ramiz
```

### Function Scope

Bir dəyişən funksiyanın daxilində təyin olunubsa, bu dəyişən yalnız həmin funksiyanın daxilində əlçatandır.

```js
function greet() {
  var message = "Salam!";
  console.log(message); // Salam!
}

greet();
console.log(message); // message is not defined
```

Bu misalda, `message` dəyişəni yalnız `greet` funksiyası daxilində mövcuddur. Funksiya xaricində bu dəyişənə çatmaq mümkün deyil.

### Block Scope

`let` və `const` açar sözləri ilə təyin olunan dəyişənlər yalnız daxil olduqları blokda əlçatandır. Bu blok ifadələri `if`, `for` və `while` kimi şərt və dövr ifadələrinin daxilində yaradıla bilər.

```js
if (true) {
  let age = 28;
  const name = "Ramiz";
}
console.log(age); // age is not defined
console.log(name); // name is not defined
```

amma `var` açar sözündə block scope yoxdur:

```js
if (true) {
  var name = "Ramiz";
  let surname = "Ramizov";
}
console.log(name); // Ramiz
console.log(surname); // surname is not defined
```

> **Qlobal Scope** proqram davam etdiyi müddətcə yaşayır. **Function Scope** isə funksiyalar çağırılıb icra olunana qədər mövcuddur.

### Scope Chain

Scope chain JavaScript-də dəyişənlərin axtarılması prosesini izah edir. Daxili (nested) scope-lar əvvəlcə öz daxilindəki dəyişənləri yoxlayır. Əgər dəyişən tapılmasa, JavaScript xarici scope-lara baxır. Dəyişən heç bir xarici əhatə dairəsində tapılmadıqda, **error** verir.

```js
function outerFunction() {
  const name = "Ramiz";

  function innerFunction() {
    console.log(name); // "Ramiz"
    console.log(lastName); // lastName is not defined
  }
  innerFunction();
}
outerFunction();
```

Bu kodda `outerFunction` çağırılır və onun içindəki `innerFunction` funksiyası da iş düşür. `innerFunction` daxilində `name` dəyişəni yoxlanılır. Bu dəyişən `innerFunction` daxilində təyin edilmədiyi üçün JavaScript **scope chain**-dən istifadə edərək daha geniş scope-lara baxır. yəni bir yuxarı `outerFunction`-a

`outerFunction` daxilindəki scope-da `name` tapılır və onun dəyəri "Ramiz" ekrana yazılır. Lakin `lastName` dəyişəni nə `innerFunction` daxilində, nə də `outerFunction` daxilində deyil yenə **scope chain**-dən istifadə edərək bir yuxarı daha gedirik
qlobal scopa-a. Qlobal scope-da da bu dəyişən tapılmadığı üçün **error** verir

Bu nümunə, **scope chain**-in necə işlədiyini göstərir. Əgər bir dəyişən daxili scope-da tapılmırsa, JavaScript xarici scope-lara baxaraq dəyişəni tapmağa çalışır. Əgər heç bir yerdə tapılmırsa, səhv baş verir.

Başqa bir nümünə:

```js
const lastName = "Smith";
function outerOuterFunction() {
  const lastName = "Ramizov";
  function outerFunction() {
    const name = "Ramiz";

    function innerFunction() {
      console.log(name); // "Ramiz"
      console.log(lastName); // "Ramizov"
    }
    innerFunction();
  }
  outerFunction();
}
outerOuterFunction();
```

Bu kodda `scope chain` mexanizmi `innerFunction` içində `lastName` dəyişənini axtardıqda, ilk olaraq `outerFunction` daxilinə baxir `lastName`-i tapmır. Sonra `outerOuterFunction` daxilinə baxır `lastName`-i (yəni "Ramizov") tapır və tapdığı üçün qlobal scope-dakı `lastName` (yəni "Smith") baxmır
