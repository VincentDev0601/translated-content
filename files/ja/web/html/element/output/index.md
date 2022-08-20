---
title: '<output>: 出力要素'
slug: Web/HTML/Element/output
tags:
  - Element
  - HTML
  - HTML forms
  - HTML5
  - HTML:Flow content
  - HTML:フローコンテンツ
  - Reference
  - Web
translation_of: Web/HTML/Element/output
---
{{HTMLRef}}

**HTML の出力要素** (**`<output>`**) は、サイトやアプリが計算結果やユーザー操作の結果を挿入することができるコンテナー要素です。

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/ja/docs/Web/HTML/Content_categories">コンテンツカテゴリ</a>
      </th>
      <td>
        <a href="/ja/docs/Web/HTML/Content_categories#フローコンテンツ"
          >フローコンテンツ</a
        >、<a href="/ja/docs/Web/HTML/Content_categories#記述コンテンツ"
          >記述コンテンツ</a
        >、<a href="/ja/docs/Web/HTML/Content_categories#フォーム関連コンテンツ"
          >フォーム関連要素</a
        >
        (<a href="/ja/docs/Web/HTML/Content_categories#リスト化">リスト化</a
        >、<a href="/ja/docs/Web/HTML/Content_categories#ラベル付け可能"
          >ラベル付け可能</a
        >、<a href="/ja/docs/Web/HTML/Content_categories#リセット可能"
          >リセット可能</a
        >)、知覚可能コンテンツ
      </td>
    </tr>
    <tr>
      <th scope="row">許可された内容</th>
      <td>
        <a href="/ja/docs/Web/HTML/Content_categories#記述コンテンツ"
          >記述コンテンツ</a
        >
      </td>
    </tr>
    <tr>
      <th scope="row">タグの省略</th>
      <td>{{no_tag_omission}}</td>
    </tr>
    <tr>
      <th scope="row">許可された親要素</th>
      <td>
        <a href="/ja/docs/Web/HTML/Content_categories#記述コンテンツ"
          >記述コンテンツ</a
        >を受け入れるすべての要素
      </td>
    </tr>
    <tr>
      <th scope="row">暗黙の ARIA ロール</th>
      <td>{{ARIARole("status")}}</td>
    </tr>
    <tr>
      <th scope="row">許可された ARIA ロール</th>
      <td>すべて</td>
    </tr>
    <tr>
      <th scope="row">DOM インターフェイス</th>
      <td>{{domxref("HTMLOutputElement")}}</td>
    </tr>
  </tbody>
</table>

## 属性

この要素には[グローバル属性](/ja/docs/Web/HTML/Global_attributes)があります。

<dl><dt>{{htmlattrdef("for")}}</dt><dd>他の要素の {{htmlattrxref("id")}} の空白区切りのリストで、入力値が計算に使用される (または何らかの影響を与える) 要素を示します。</dd><dt>{{htmlattrdef("form")}}</dt><dd>この要素に関連付けられた (<em>フォームオーナー</em>である) {{HTMLElement("form")}} 要素を指定します。この値は、同じ文書内の <code>&#x3C;form></code> 要素の {{htmlattrxref("id")}} である必要があります。 (この属性が設定されていない場合、 <code>&#x3C;output></code> 要素は祖先の <code>&#x3C;form></code> があれば、その要素に関連づけられます。</dd><dd>この属性は <code>&#x3C;output></code> 要素を、包含する <code>&#x3C;form></code> に限らず文書中のどこにある <code>&#x3C;form></code> にも結び付けることができます。これは祖先の <code>&#x3C;form></code> 要素を上書きもします。</dd><dt>{{htmlattrdef("name")}}</dt><dd>要素の名前です。 {{domxref("HTMLFormElement.elements", "form.elements")}} API で使用されます。</dd></dl>

`<output>` の値、名前、内容はフォーム送信の過程で送信されません。

## 例

以下の例では、フォームに `0` から `100` までの範囲の値を取るスライダーと、第 2 の値を入力できる {{HTMLElement("input")}} 要素があります。どちらかのコントロールの値が変更されるたびに、2 つの値が合計された結果が `<output>` 要素の中に表示されます。

```html
<form oninput="result.value=parseInt(a.value)+parseInt(b.value)">
  <input type="range" id="b" name="b" value="50" /> +
  <input type="number" id="a" name="a" value="10" /> =
  <output name="result" for="a b">60</output>
</form>
```

{{ EmbedLiveSample('Examples')}}

## アクセシビリティの考慮

多くのブラウザーでは、この要素を [`aria-live`](/ja/docs/Web/Accessibility/ARIA/ARIA_Live_Regions) 領域として実装しています。これにより、支援技術は、その中に投稿された UI インタラクションの結果を発表しますが、その結果を生成するコントロールからフォーカスを外す必要はありません。

## 仕様書

| 仕様書                                                                                                       | 状態                             | 備考 |
| ------------------------------------------------------------------------------------------------------------ | -------------------------------- | ---- |
| {{SpecName('HTML WHATWG', 'forms.html#the-output-element', '&lt;output&gt;')}}     | {{Spec2('HTML WHATWG')}} |      |
| {{SpecName('HTML5 W3C', 'sec-forms.html#the-output-element', '&lt;output&gt;')}} | {{Spec2('HTML5 W3C')}}     |      |

## ブラウザーの互換性

{{Compat("html.elements.output")}}
