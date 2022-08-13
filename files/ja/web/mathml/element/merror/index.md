---
title: <merror>
slug: Web/MathML/Element/merror
tags:
  - MathML
  - MathML Reference
  - 'MathML:Element'
  - 'MathML:General Layout Schemata'
translation_of: Web/MathML/Element/merror
---
<div>{{MathMLRef}}</div>

<p class="summary">MathML <code>&lt;merror&gt;</code> 要素は、エラーメッセージとしてコンテンツを表示するために使用されます。Firefox でこのエラーメッセージは、典型的な XML エラーメッセージのようにレンダリングされます。MathML マークアップが間違っているか整形式でない XML のときに、このエラーがスロー<strong>されない</strong>ことに注意してください。<code>&lt;merror&gt;</code> とは何の関係もない、（MathML の XHTML 表記の場合に）依然として XML 解析エラーが発生します。</p>

<h2 id="属性">属性</h2>

<dl>
 <dt id="attr-class-id-style">class, id, style</dt>
 <dd><a href="/ja/docs/CSS">スタイルシート</a>と一緒に用いて提供されます。</dd>
 <dt id="attr-href">href</dt>
 <dd>指定された URI へのハイパーリンクの設定に使用されます。</dd>
 <dt id="attr-mathbackground">mathbackground</dt>
 <dd>背景色。<code>#rgb</code>、<code>#rrggbb</code>および<a href="/ja/docs/CSS/color_value#Color_Keywords">HTML色名</a>を使用できます。</dd>
 <dt id="attr-mathcolor">mathcolor</dt>
 <dd>文字色と分数の線の色。<code>#rgb</code>、<code>#rrggbb</code>および<a href="/ja/docs/CSS/color_value#Color_Keywords">HTML色名</a>を使用できます。</dd>
</dl>

<h2 id="例">例</h2>

<pre class="brush: html">&lt;math&gt;

&lt;merror&gt;
  &lt;mrow&gt;
    &lt;mtext&gt; Division by zero: &lt;/mtext&gt;
    &lt;mfrac&gt;
      &lt;mn&gt; 1 &lt;/mn&gt;
      &lt;mn&gt; 0 &lt;/mn&gt;
    &lt;/mfrac&gt;
  &lt;/mrow&gt;
&lt;/merror&gt;

&lt;/math&gt;
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
   <td>{{ SpecName('MathML3', 'chapter3.html#presm.merror', 'merror') }}</td>
   <td>{{ Spec2('MathML3') }}</td>
   <td>現在の仕様</td>
  </tr>
  <tr>
   <td>{{ SpecName('MathML2', 'chapter3.html#presm.merror', 'merror') }}</td>
   <td>{{ Spec2('MathML2') }}</td>
   <td>初期の仕様</td>
  </tr>
 </tbody>
</table>

<h2 id="ブラウザー互換性">ブラウザー互換性</h2>



<p>{{Compat("mathml.elements.merror")}}</p>
