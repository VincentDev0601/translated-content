---
title: CSS.paintWorklet (静的プロパティ)
slug: Web/API/CSS/paintWorklet
tags:
  - API
  - CSS
  - CSS Paint API
  - Experimental
  - Houdini
  - Painting
  - Property
  - Reference
  - Worklet
  - paintWorklet
translation_of: Web/API/CSS/paintWorklet
---
<p>{{APIRef("CSSOM")}}{{Draft}}{{SeeCompatTable}}{{SecureContext_Header}}</p>

<p><span class="seoSummary"><strong><code>paintWorklet</code></strong> は {{DOMxRef("CSS")}} インターフェイスの静的な読み取り専用プロパティで、{{DOMxRef("PaintWorklet")}} へのアクセスを提供します。 これは、CSS のプロパティがファイルを期待する場所においてプログラムで画像を生成します。</span></p>

<h2 id="Syntax" name="Syntax">構文</h2>

<pre class="syntaxbox notranslate">var <em>worklet</em> = CSS.paintWorklet;</pre>

<h3 id="Value" name="Value">値</h3>

<p>{{DOMxRef('PaintWorklet')}} オブジェクト。</p>

<h2 id="Examples" name="Examples">例</h2>

<p>次の例は、js ファイルから {{DOMxRef('PaintWorklet')}} をロードする方法を示しており、機能検出によってロードします。</p>

<pre class="brush: js notranslate">&lt;script&gt;
  if ('paintWorklet' in CSS) {
    CSS.paintWorklet.addModule('checkerboard.js');
  }
&lt;/script&gt;</pre>

<h2 id="Specifications" name="Specifications">仕様</h2>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="col">仕様</th>
   <th scope="col">状態</th>
   <th scope="col">コメント</th>
  </tr>
  <tr>
   <td>{{SpecName('CSS Painting API','#dom-css-paintworklet','paintWorklet')}}</td>
   <td>{{Spec2('CSS Painting API')}}</td>
   <td>初期定義</td>
  </tr>
 </tbody>
</table>

<h2 id="Browser_compatibility" name="Browser_compatibility">ブラウザーの互換性</h2>



<p>{{Compat("api.CSS.paintWorklet")}}</p>

<h2 id="See_Also" name="See_Also">関連情報</h2>

<ul>
 <li><a href="/ja/docs/Web/API/CSS_Painting_API">CSS Painting API</a></li>
 <li><a href="/ja/docs/Web/Houdini">Houdini APIs</a></li>
 <li><a href="/ja/docs/Web/Houdini/learn">Houdini overview</a></li>
</ul>
