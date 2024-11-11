---
layout: "../../layouts/Layout.astro"
title: "Closure"
path: "closure"
---

# Closure

JavaScript-də **closure**, bir funksiyanın daxilində təyin olunan **inner function**-un **outer function**-un dəyişənlərinə xaricdən giriş imkanı əldə etməsi hadisəsidir.

```js
function greeting(name) {
  let greet = "Good morning";

  setTimeout(function () {
    console.log(greet + name);
  }, 5000);
}
greeting("john");
```

Bu nümunədə, `greeting` funksiyası daxilində `greet` adlı bir dəyişən təyin olunub. Normalda, `greeting` funksiyası çağırıldıqda işini bitirir və stack-dan silinir. Funksiya daxilindəki dəyişənlər də bu zaman yaddaşdan silinməlidir. Lakin burada bir sual yaranır: **setTimeout** necə işləyir? Əgər `greet` dəyişəni silinibsə, niyə bu dəyişənə hələ də giriş mümkündür?

Bu məqamda **closure** anlayışı işə düşür. JavaScript mühərriki görür ki, `greet` dəyişəninə daxili funksiya (`setTimeout` daxilindəki anonim funksiya) tərəfindən istinad edilir. Buna görə də, `greet` yaddaşda saxlanılır və həmin funksiyaya əlçatan olur. Yəni, closure sayəsində `greeting` funksiyasının daxilindəki `greet` dəyişəni `setTimeout` funksiyası icra olunana qədər yaddaşda qalır və silinmir.

Başqa bir nümunəyə baxaq:

```js
function makeFunc() {
  const name = "closure";

  function displayName() {
    console.log(name);
  }

  return displayName;
}

const myFunc = makeFunc();
myFunc();
```

Bu nümunədə, `makeFunc` funksiyası daxilində `name` adlı bir dəyişən təyin olunub. `displayName` adlı daxili funksiya, `name` dəyişənini çap etmək üçün istifadə olunur. `makeFunc` funksiyası çağırıldıqda, `displayName` funksiyası geri qaytarılır və `myFunc` adlı bir dəyişənə təyin edilir.

`myFunc` çağırıldıqda, `displayName` funksiyası işə düşür və `name` dəyişəninə daxil olur. Bu vəziyyətdə, `displayName` funksiyası `makeFunc` funksiyası bitdikdən sonra belə `name` dəyişəninə giriş imkanı saxlayır. Bu, **closure** anlayışının bir nümunəsidir; `displayName` funksiyası, `makeFunc` funksiyası icra olunduqdan sonra belə `name` dəyişənini yaddaşda saxlayır.
