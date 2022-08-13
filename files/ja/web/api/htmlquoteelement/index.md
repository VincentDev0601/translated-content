---
title: HTMLQuoteElement
slug: Web/API/HTMLQuoteElement
tags:
  - API
  - HTML DOM
  - Interface
  - Reference
translation_of: Web/API/HTMLQuoteElement
---
<div>{{APIRef("HTML DOM")}}</div>

<p><span class="seoSummary"><strong><code>HTMLQuoteElement</code></strong>インターフェースは，引用要素を扱う為に（継承する{{domxref("HTMLElement")}}インターフェースを越えた）固有の属性を提供します。</span>ここで引用要素とは{{HTMLElement("blockquote")}}や{{HTMLElement("q")}}といった要素であり，{{HTMLElement("cite")}}要素ではありません。</p>

<p>{{InheritanceDiagram(600, 120)}}</p>

<h2 id="属性">属性</h2>

<p><em>親である{{domxref("HTMLElement")}}からメソッドを継承します。</em></p>

<dl>
 <dt>{{domxref("HTMLQuoteElement.cite")}}</dt>
 <dd>は{{domxref("DOMString")}}であり，HTML属性{{htmlattrxref("cite", "blockquote")}}に格納している引用元URLを表します。</dd>
</dl>

<h2 id="メソッド">メソッド</h2>

<p><em>固有のメソッドなし。親である{{domxref("HTMLElement")}}からメソッドを継承します。</em></p>

<h2 id="仕様書">仕様書</h2>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="col">仕様書</th>
   <th scope="col">状態</th>
   <th scope="col">備考</th>
  </tr>
  <tr>
   <td>{{SpecName('HTML WHATWG', "#htmlquoteelement", "HTMLQuoteElement")}}</td>
   <td>{{Spec2('HTML WHATWG')}}</td>
   <td></td>
  </tr>
  <tr>
   <td>{{SpecName('HTML5 W3C', "grouping-content.html#the-blockquote-element", "HTMLQuoteElement")}}</td>
   <td>{{Spec2('HTML5 W3C')}}</td>
   <td>{{SpecName("DOM2 HTML")}}より変更なし。</td>
  </tr>
  <tr>
   <td>{{SpecName('DOM2 HTML', 'html.html#ID-70319763', 'HTMLQuoteElement')}}</td>
   <td>{{Spec2('DOM2 HTML')}}</td>
   <td>{{SpecName("DOM1")}}より変更なし。</td>
  </tr>
  <tr>
   <td>{{SpecName('DOM1', 'level-one-html.html#ID-70319763', 'HTMLQuoteElement')}}</td>
   <td>{{Spec2('DOM1')}}</td>
   <td>初回定義。</td>
  </tr>
 </tbody>
</table>

<h2 id="ブラウザ互換性">ブラウザ互換性</h2>



<p>{{Compat("api.HTMLQuoteElement")}}</p>

<h2 id="関連項目">関連項目</h2>

<ul>
 <li>本インターフェースを実装するHTML要素: {{HTMLElement("blockquote")}}及び{{HTMLElement("q")}}，然し{{HTMLElement("cite")}}ではない。</li>
</ul>
