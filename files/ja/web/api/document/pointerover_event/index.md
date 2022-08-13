---
title: 'Document: pointerover イベント'
slug: Web/API/Document/pointerover_event
tags:
  - API
  - Document
  - Event
  - PointerEvent
  - Reference
  - Web
  - onpointerover
  - pointer
  - pointerover
  - イベント
  - ポインター
translation_of: Web/API/Document/pointerover_event
---
{{APIRef}}

`pointerover` イベントは、ポインティングデバイスが要素のヒットテスト境界内に移動したときに発生します。

| バブリング                   | あり                                                                                     |
| ---------------------------- | ---------------------------------------------------------------------------------------- |
| キャンセル可能               | はい                                                                                     |
| インターフェイス             | {{domxref("PointerEvent")}}                                                     |
| イベントハンドラープロパティ | {{domxref("GlobalEventHandlers/onpointerover", "onpointerover")}} |

## 例

`addEventListener()` を使用した場合

```js
document.addEventListener('pointerover', (event) => {
  console.log('Pointer moved in');
});
```

`onpointerover` イベントハンドラープロパティを使用した場合

```js
document.onpointerover = (event) => {
  console.log('Pointer moved in');
};
```

## 仕様書

| 仕様書                                                                       | 状態                                 |
| ---------------------------------------------------------------------------- | ------------------------------------ |
| {{SpecName('Pointer Events', '#the-pointerover-event')}} | {{Spec2('Pointer Events')}} |

## ブラウザーの対応

{{Compat("api.Document.pointerover_event")}}

## 関連情報

- {{domxref("Document/gotpointercapture_event", "gotpointercapture")}}
- {{domxref("Document/lostpointercapture_event", "lostpointercapture")}}
- {{domxref("Document/pointerenter_event", "pointerenter")}}
- {{domxref("Document/pointerdown_event", "pointerdown")}}
- {{domxref("Document/pointermove_event", "pointermove")}}
- {{domxref("Document/pointercancel_event", "pointercancel")}}
- {{domxref("Document/pointerout_event", "pointerout")}}
- {{domxref("Document/pointerleave_event", "pointerleave")}}
- {{domxref("GlobalEventHandlers/onpointerover", "onpointerover")}} event handler property
- `HTMLElement` を対象としたこのイベント: {{domxref("HTMLElement/pointerover_event", "pointerover")}} イベント
