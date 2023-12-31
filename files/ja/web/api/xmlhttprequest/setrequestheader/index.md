---
title: XMLHttpRequest.setRequestHeader()
slug: Web/API/XMLHttpRequest/setRequestHeader
l10n:
  sourceCommit: b5b33acd44e7bb9c7be2efc75ba9a04b8bf8b2b2
---

{{APIRef('XMLHttpRequest')}}

{{domxref("XMLHttpRequest")}} の **`setRequestHeader()`** メソッドは、HTTP リクエストヘッダーの値を設定します。`setRequestHeader()` は、 {{domxref("XMLHttpRequest.open", "open()")}} の呼び出しの後、 {{domxref("XMLHttpRequest.send", "send()")}} の呼び出しの前に呼び出さなければなりません。同じヘッダーについてこのメソッドを複数回呼び出された場合は、複数の値が単一のリクエストヘッダーにマージされます。

最初に `setRequestHeader()` を呼び出した後、呼び出す度に、指定されたテキストは既存のヘッダーの内容の末尾に追加されます。

この関数を使用して {{HTTPHeader("Accept")}} ヘッダーが設定されなかった場合、 {{domxref("XMLHttpRequest.send", "send()")}} が呼び出されると、 `Accept` ヘッダーは `*/*` の値で送信されます。

セキュリティ上の理由から、ユーザーエージェントによって値が制御される{{Glossary("Forbidden_header_name", "禁止ヘッダー名")}}がいくつかあります。フロントエンドの JavaScript コードからこれらのヘッダーの値を設定しようとすると、警告やエラーなしに無視されます。

> **メモ:** カスタムフィールドについては、ドメインをまたがってリクエストを行うと、 "**not
> allowed by Access-Control-Allow-Headers in preflight response**" の例外に遭遇することがあります。この場合、サーバー側でレスポンスヘッダーに {{HTTPHeader("Access-Control-Allow-Headers")}} を設定する必要があります。

## 構文

```js-nolint
setRequestHeader(header, value)
```

### 引数

- `header`
  - : 値を設定するヘッダーの名前。
- `value`
  - : そのヘッダーの本体として設定する値。

### 返値

なし ({{jsxref("undefined")}})。

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat}}

## 関連情報

- [XMLHttpRequest の使用](/ja/docs/Web/API/XMLHttpRequest/Using_XMLHttpRequest)
- [XMLHttpRequest での HTML](/ja/docs/Web/API/XMLHttpRequest/HTML_in_XMLHttpRequest)
