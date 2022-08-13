---
title: 'Window: afterprint イベント'
slug: Web/API/Window/afterprint_event
tags:
  - Event
  - Reference
  - イベント
translation_of: Web/API/Window/afterprint_event
---
{{APIRef}}

**`afterprint`** イベントは、関連する文書の印刷が開始されたか、印刷プレビューが閉じた後に発生します。

| バブリング                   | いいえ                                                                               |
| ---------------------------- | ------------------------------------------------------------------------------------ |
| キャンセル                   | 不可                                                                                 |
| インターフェイス             | {{domxref("Event")}}                                                         |
| イベントハンドラープロパティ | {{domxref("WindowEventHandlers/onafterprint", "onafterprint")}} |

## 例

`addEventListener()` の使用例:

```js
window.addEventListener('afterprint', (event) => {
  console.log('After print');
});
```

`onafterprint` イベントハンドラープロパティの使用例:

```js
window.onafterprint = (event) => {
  console.log('After print');
};
```

## 仕様書

| 仕様書                                                           | 状態                             |
| ---------------------------------------------------------------- | -------------------------------- |
|                                                                  |                                  |
| {{SpecName('HTML WHATWG', '#event-afterprint')}} | {{Spec2('HTML WHATWG')}} |

## ブラウザーの互換性

{{Compat("api.Window.afterprint_event")}}

## 関連情報

- 関連イベント: {{domxref("Window/beforeprint_event", "beforeprint")}}
