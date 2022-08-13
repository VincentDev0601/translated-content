---
title: 'HTMLFormElement: reset イベント'
slug: Web/API/HTMLFormElement/reset_event
tags:
  - API
  - Event
  - Forms
  - HTML DOM
  - HTMLFormElement
  - Reference
translation_of: Web/API/HTMLFormElement/reset_event
---
{{APIRef}}

**`reset`** イベントは {{HTMLElement("form")}} がリセットされたときに発行されます。

| バブリング                   | あり (ただし、バブリングしない単純なイベントとして指定されている) |
| ---------------------------- | ----------------------------------------------------------------- |
| キャンセル                   | 可                                                                |
| インターフェイス             | {{DOMxRef("Event")}}                                      |
| イベントハンドラープロパティ | {{domxref("GlobalEventHandlers.onreset")}}          |

## 例

この例は {{domxref("EventTarget.addEventListener()")}} を使用してフォームがリセットされるのを、実行されたときに現在の {{domxref("Event.timeStamp")}} をログ出力します。

### HTML

```html
<form id="form">
  <label>Test field: <input type="text"></label>
  <br><br>
  <button type="reset">Reset form</button>
</form>
<p id="log"></p>
```

### JavaScript

```js
function logReset(event) {
  log.textContent = `Form reset! Time stamp: ${event.timeStamp}`;
}

const form = document.getElementById('form');
const log = document.getElementById('log');
form.addEventListener('reset', logReset);
```

### 結果

{{EmbedLiveSample("Examples")}}

## 仕様書

| 仕様書                                                                                           | 状態                         | 備考     |
| ------------------------------------------------------------------------------------------------ | ---------------------------- | -------- |
| {{SpecName("HTML WHATWG", "indices.html#event-reset", "reset")}}             | {{Spec2("UI Events")}} | 変更なし |
| {{SpecName("HTML5.2", "fullindex.html#eventdef-global-reset", "reset")}} | {{Spec2("HTML5.2")}} | 変更なし |
| {{SpecName("HTML5.1", "fullindex.html#eventdef-global-reset", "reset")}} | {{Spec2("HTML5.1")}} | 変更なし |
| {{SpecName("HTML5 W3C", "index.html#events-0", "reset")}}                     | {{Spec2("HTML5 W3C")}} | 初回定義 |

## ブラウザーの互換性

{{Compat("api.HTMLFormElement.reset_event")}}

## 関連情報

- HTML の {{HTMLElement("form")}} 要素
