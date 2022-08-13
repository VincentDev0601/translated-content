---
title: '<head>: 文書メタデータ (ヘッダー) 要素'
slug: Web/HTML/Element/head
tags:
  - Element
  - HTML
  - HTML document metadata
  - HTML:Metadata content
  - Reference
  - Web
translation_of: Web/HTML/Element/head
browser-compat: html.elements.head
---
{{HTMLRef}}

**HTML の `<head>` 要素**は、文書に関する機械可読な情報 ({{glossary("metadata", "メタデータ")}})、たとえば[題名](/ja/docs/Web/HTML/Element/title)、[スクリプト](/ja/docs/Web/HTML/Element/script)、[スタイルシート](/ja/docs/Web/HTML/Element/style)などを含みます。

> **Note:** **メモ:** `<head>` は機械処理のための情報を保持するためのものであり、人間が読むためのものではありません。人間が読むための情報、例えば最上位のヘッダーや著者のリストのためのものは、 {{HTMLElement("header")}} 要素を参照してください。

| [コンテンツカテゴリー](/ja/docs/Web/Guide/HTML/Content_categories) | なし                                                                                                                                                                                                                                                                                                                                   |
| ------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 許可されている内容                                                 | 文書が {{HTMLElement("iframe")}} の {{htmlattrxref("srcdoc", "iframe")}} 文書である場合、または題名情報がより上位のプロトコル (HTML メールの件名の行など) で使用される場合は、0 個以上のメタデータコンテンツ。他の場合は正確に 1 つの {{HTMLElement("title")}} 要素を含む、1 個以上のメタデータコンテンツ。 |
| タグの省略                                                         | `<head>` 要素内で最初に存在するものが要素である場合、開始タグを省略可能。 `<head>` 要素に続く最初のものが空白文字やコメントでない場合、終了タグが省略可能。                                                                                                                                                                            |
| 許可されている親要素                                               | {{HTMLElement("html")}} 要素の最初の子要素として配置可能。                                                                                                                                                                                                                                                                    |
| 暗黙の ARIA ロール                                                 | [対応するロールなし](https://www.w3.org/TR/html-aria/#dfn-no-corresponding-role)                                                                                                                                                                                                                                                       |
| 許可されている ARIA ロール                                         | なし                                                                                                                                                                                                                                                                                                                                   |
| DOM インターフェイス                                               | {{domxref("HTMLHeadElement")}}                                                                                                                                                                                                                                                                                               |

## 属性

この要素には[グローバル属性](/ja/docs/Web/HTML/Global_attributes)があります。

- {{htmlattrdef("profile")}} {{deprecated_inline}}
  - : 1 つ以上のメタデータプロファイルの {{glossary("URI")}} で、{{Glossary("whitespace", "ホワイトスペース")}}区切りです。

## 例

```html
<!doctype html>
<html>
  <head>
    <title>Document title</title>
  </head>
</html>
```

## メモ

HTML5 互換のブラウザーでは、タグが省略されていても `<head>` 要素を自動的に生成します。[この自動生成は、過去のブラウザーでは保証されていません](https://www.stevesouders.com/blog/2010/05/12/autohead-my-first-browserscope-user-test/)。

## 仕様書

| 仕様書                                                                                                           | 状態                             | 備考                               |
| ---------------------------------------------------------------------------------------------------------------- | -------------------------------- | ---------------------------------- |
| {{SpecName('HTML WHATWG', 'semantics.html#the-head-element', '&lt;head&gt;')}}         | {{Spec2('HTML WHATWG')}} | 最新のスナップショットから変更なし |
| {{SpecName('HTML5 W3C', 'document-metadata.html#the-head-element', '&lt;head&gt;')}} | {{Spec2('HTML5 W3C')}}     | `profile` を廃止                   |
| {{SpecName('HTML4.01', 'struct/global.html#h-7.4.1', '&lt;head&gt;')}}                     | {{Spec2('HTML4.01')}}     |                                    |

## ブラウザーの互換性

{{Compat}}

## 関連情報

- `<head>` の中で使用することができる要素:

  - {{HTMLElement("title")}}
  - {{HTMLElement("base")}}
  - {{HTMLElement("link")}}
  - {{HTMLElement("style")}}
  - {{HTMLElement("meta")}}
  - {{HTMLElement("script")}}
  - {{HTMLElement("noscript")}}
  - {{HTMLElement("template")}}
