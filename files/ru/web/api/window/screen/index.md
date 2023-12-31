---
title: Window.screen
slug: Web/API/Window/screen
---

{{APIRef("CSSOM")}}

Свойство **`screen`** объекта {{DOMxRef("Window")}} возвращает ссылку на экран объекта, который содержит информацию об экране пользователя. Похожий по смыслу, объект `screen`, который имплементирует интерфейс {{DOMxRef("Screen")}} представляет собой совокупность свойств экрана пользователя.

## Синтаксис

```
let screenObj = window.screen;
```

## Пример

```js
if (screen.pixelDepth < 8) {
  // uиспользовать пониженную глубину пикселей
} else {
  // Использовать стандартную глубину пикселей(24)
}
```

## Спецификации

{{Specifications}}

## Совместимость с браузерами

{{Compat}}
