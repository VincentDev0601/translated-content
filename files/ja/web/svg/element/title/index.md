---
title: title
slug: Web/SVG/Element/title
tags:
  - Element
  - Reference
  - SVG
  - SVG Descriptive
translation_of: Web/SVG/Element/title
---
<div>{{SVGRef}}</div>

<p>SVG における各コンテナ要素またはグラフィックス要素の描画は、説明がテキストのみの文字列を含む <strong><code>&lt;title&gt;</code></strong> 要素を供給することができます。文書フラグメントがSVG視覚メディアとしてレンダリングされるとき、<code>&lt;title&gt;</code> 要素は、グラフィックスの一部としてはレンダリングされません。しかし、一部のユーザーエージェントは、例えば、ツールチップとして <code>&lt;title&gt;</code>要素を表示するかもしれません。 <code>&lt;title&gt;</code> 要素を表示するが <code>path</code> 要素または他のグラフィックス要素を表示しない、視覚と聴覚の両方の代替プレゼンテーションが可能です。<code>&lt;title&gt;</code> 要素は一般に SVG 文書のアクセシビリティを向上させます。</p>

<p>一般に、<code>&lt;title&gt;</code> 要素は その <code>&lt;title&gt;</code> 要素の親の最初の子にするべきです。 <code>&lt;title&gt;</code>が実際にその <code>&lt;title&gt;</code> の親の最初の子要素である場合、ツールチップを表示するためにタイトルを使用する実装のみが表示することに注意してください。</p>

<h2 id="利用可能な場所">利用可能な場所</h2>

<p>{{svginfo}}</p>

<h2 id="属性">属性</h2>

<h3 id="グローバル属性">グローバル属性</h3>

<ul>
 <li><a href="/ja/docs/Web/SVG/Attribute#Core_attributes">コア属性</a></li>
 <li>{{SVGAttr("class")}}</li>
 <li>{{SVGAttr("style")}}</li>
</ul>

<h3 id="専用属性">専用属性</h3>

<p><em>この要素には専用属性はありません。</em></p>

<h2 id="DOM_インターフェイス">DOM インターフェイス</h2>

<p>この要素は {{domxref("SVGTitleElement")}} インターフェイスを実装します。</p>

<h2 id="例">例</h2>

<pre class="brush: xml">&lt;svg width="500" height="300" xmlns="http://www.w3.org/2000/svg"&gt;
  &lt;g&gt;
    &lt;title&gt;SVG Title Demo example&lt;/title&gt;
    &lt;rect x="10" y="10" width="200" height="50"
    style="fill:none; stroke:blue; stroke-width:1px"/&gt;
  &lt;/g&gt;
&lt;/svg&gt;
</pre>

<h2 id="仕様">仕様</h2>

<table class="standard-table">
 <thead>
  <tr>
   <th scope="col">仕様</th>
   <th scope="col">状態</th>
   <th scope="col">コメント</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td>{{SpecName('SVG2', 'struct.html#TitleElement', '&lt;title&gt;')}}</td>
   <td>{{Spec2('SVG2')}}</td>
   <td></td>
  </tr>
  <tr>
   <td>{{SpecName('SVG1.1', 'struct.html#DescriptionAndTitleElements', '&lt;title&gt;')}}</td>
   <td>{{Spec2('SVG1.1')}}</td>
   <td>初期の定義</td>
  </tr>
 </tbody>
</table>

<h2 id="ブラウザー互換性">ブラウザー互換性</h2>



<p>{{Compat("svg.elements.title")}}</p>

<h2 id="関連情報">関連情報</h2>

<ul>
 <li>{{SVGElement("desc")}}</li>
</ul>
