---
title: HTMLLIElement
slug: Web/API/HTMLLIElement
tags:
  - API
  - HTML DOM
  - Interface
  - Reference
translation_of: Web/API/HTMLLIElement
---
<div>
<div>{{ APIRef("HTML DOM") }}</div>
</div>

<p><span class="seoSummary"><strong><code>HTMLLIElement</code></strong> インターフェースは列挙要素を扱う為の，（継承される{{domxref("HTMLElement")}}を越えた）属性及びメソッドを提供します。</span></p>

<p>{{InheritanceDiagram(600, 120)}}</p>

<h2 id="属性">属性</h2>

<p><em>親である{{domxref("HTMLElement")}}より属性を継承します。</em></p>

<dl>
 <dt>{{domxref("HTMLLIElement.type")}} {{obsolete_inline}}</dt>
 <dd>とは{{domxref("DOMString")}}であり，箇条記号の種別<code>"disc"</code>, <code>"square"</code>又は<code>"circle"</code>を表します。CSS属性{{cssxref("list-style-type")}}を介して箇条の種別を定める方法が標準的であり，CSSOMメソッドを用いて設定します。</dd>
 <dt>{{domxref("HTMLLIElement.value")}}</dt>
 <dd>は<code>32ビット整数</code>であり，与{{HTMLElement("ol")}}配下の列挙要素の序数を指示します。HTML要素{{HTMLElement("li")}}の{{htmlattrxref("value", "li")}}属性と連動しており，<code>0</code>以下の値も取り得ます。{{HTMLElement("li")}}要素が{{HTMLElement("ol")}}要素の子でない場合，当属性は意味を成しません。</dd>
</dl>

<h2 id="メソッド">メソッド</h2>

<p><em>固有のメソッドなし。親である{{domxref("HTMLElement")}}からメソッドを継承しています。</em></p>

<h2 id="仕様書">仕様書</h2>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="col">仕様書</th>
   <th scope="col">状態</th>
   <th scope="col">備考</th>
  </tr>
  <tr>
   <td>{{SpecName('HTML WHATWG', "#htmllielement", "HTMLLIElement")}}</td>
   <td>{{Spec2('HTML WHATWG')}}</td>
   <td></td>
  </tr>
  <tr>
   <td>{{SpecName('HTML5 W3C', "grouping-content.html#the-li-element", "HTMLLIElement")}}</td>
   <td>{{Spec2('HTML5 W3C')}}</td>
   <td>次の要素が廃止されました: <code>type</code>。</td>
  </tr>
  <tr>
   <td>{{SpecName('DOM2 HTML', 'html.html#ID-74680021', 'HTMLLIElement')}}</td>
   <td>{{Spec2('DOM2 HTML')}}</td>
   <td>{{SpecName("DOM1")}}より変更なし。</td>
  </tr>
  <tr>
   <td>{{SpecName('DOM1', 'level-one-html.html#ID-74680021', 'HTMLLIElement')}}</td>
   <td>{{Spec2('DOM1')}}</td>
   <td>初回定義。</td>
  </tr>
 </tbody>
</table>

<h2 id="ブラウザ互換性">ブラウザ互換性</h2>

<div>


<p>{{Compat("api.HTMLLIElement")}}</p>
</div>

<h2 id="関連項目">関連項目</h2>

<ul>
 <li>本インターフェースを実装するHTML要素: {{HTMLElement("li")}}</li>
</ul>
