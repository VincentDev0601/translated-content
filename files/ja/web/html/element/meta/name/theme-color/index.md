---
title: theme-color
slug: Web/HTML/Element/meta/name/theme-color
tags:
  - Attribute
  - HTML
  - HTML document metadata
  - Reference
  - metadata
translation_of: Web/HTML/Element/meta/name/theme-color
browser-compat: html.elements.meta.name.theme-color
---
{{HTMLRef}}

**`theme-color`** の値は {{htmlelement("meta")}} 要素の {{htmlattrxref("name", "meta")}} 属性において、ユーザーエージェントがページやその周辺のユーザーインターフェイスの表示をカスタマイズするために使用すべき推奨色を示します。指定された場合、 {{htmlattrxref("content", "meta")}} 属性には有効な CSS の {{cssxref("&lt;color&gt;")}} が含まれていなければなりません。

## 例

```html
<meta name="theme-color" content="#4285f4">
```

次の画像は、上記の {{htmlelement("meta")}} 要素が、 Android モバイル端末上で動作する Chrome で表示された文書に与える影響を示しています。

![theme-color を使用した影響を表す図](theme-color.png)

<figcaption><small>画像の出典: <a href="https://developers.google.com/web/fundamentals/design-and-ux/browser-customization">Icons &#x26; Browser Colors</a> より、<a href="https://developers.google.com/readme/policies">Google</a> が作成・共有し <a href="https://creativecommons.org/licenses/by/4.0/">Creative Commons 4.0 Attribution License</a> に記載された条件に従って使用されています。</small></figcaption>

{{htmlattrxref("media", "meta")}} 属性で、メディア種別やクエリーを指定することができ、メディアの条件が真である場合にのみ、色が設定されます。例えば、以下のようになります。

```html
<meta name="theme-color" media="(prefers-color-scheme: light)" content="white">
<meta name="theme-color" media="(prefers-color-scheme: dark)" content="black">
```

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat}}
