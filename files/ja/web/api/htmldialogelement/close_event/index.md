---
title: window.onclose
slug: Web/API/HTMLDialogElement/close_event
tags:
  - API
  - Dialog
  - Event Handler
  - Experimental
  - GlobalEventHandlers
  - HTML DOM
  - NeedsExample
  - Property
  - Reference
translation_of: Web/API/GlobalEventHandlers/onclose
original_slug: Web/API/GlobalEventHandlers/onclose
---
{{ApiRef("HTML DOM")}} {{SeeCompatTable}}

**`onclose`** は {{domxref("GlobalEventHandlers")}} ミックスインのプロパティで、ダイアログ要素に送信された {{event("close")}} イベントを処理するための {{domxref("EventHandler", "イベントハンドラー")}} です。

`close` イベントは、ユーザーが `<dialog>` を閉じたときに発生します。

> **Note:** **注:** ウィンドウのクローズを処理するには、{{domxref("WindowEventHandlers.onbeforeunload", "onbeforeunload")}} または {{domxref("WindowEventHandlers.onunload", "onunload")}} を使用します。

## 構文

```
target.onclose = functionRef;
```

### 値

`functionRef` は、関数名または[関数式](/ja/docs/Web/JavaScript/Reference/Operators/function)です。この関数は、{{domxref("Event")}} オブジェクトを唯一の引数として受け取ります。

一度に 1 つのオブジェクトに割り当てることができる `onclose` ハンドラーは 1 つだけです。代わりに、より柔軟性のある {{domxref("EventTarget.addEventListener()")}} メソッドを使用することをお勧めします。

## 仕様

| 仕様書                                                                                           | 状態                             | 備考 |
| ------------------------------------------------------------------------------------------------ | -------------------------------- | ---- |
| {{SpecName('HTML WHATWG','webappapis.html#handler-onclose','onclose')}} | {{Spec2('HTML WHATWG')}} |      |

## ブラウザの互換性

{{Compat("api.GlobalEventHandlers.onclose")}}

## 関連情報

- {{event("close")}} event
- HTML {{HTMLElement("dialog")}} element
- Related event handler: {{domxref("GlobalEventHandlers.oncancel")}}
