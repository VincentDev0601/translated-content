---
title: HTMLElement.offsetTop
slug: Web/API/HTMLElement/offsetTop
tags:
  - API
  - CSSOM View
  - Property
  - Read-only
  - Reference
translation_of: Web/API/HTMLElement/offsetTop
---
<div>{{ APIRef("HTML DOM") }}</div>

<p><strong><code>HTMLElement.offsetTop</code></strong> 読み取り専用プロパティは、{{domxref("element.offsetParent","offsetParent")}} ノードの上端に対して現在の要素の距離を返します。</p>

<h2 id="Syntax" name="Syntax">構文</h2>

<pre class="syntaxbox"><var>topPos</var> = element.offsetTop;</pre>

<h3 id="Parameters" name="Parameters">引数</h3>

<ul>
 <li><code>topPos</code> は、<em>相対的に最も近い</em>親要素の一番上からのピクセル数です。</li>
</ul>

<h2 id="Example" name="Example">例</h2>

<pre class="brush:js">var d = document.getElementById("div1");
var topPos = d.offsetTop;

if (topPos &gt; 10) {
  // 要素が offsetParent から 11px 以上離れている場合の処理をここに記述
}</pre>

<h2 id="Specification" name="Specification">仕様書</h2>

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
   <td>{{SpecName('CSSOM View', '#dom-htmlelement-offsettop', 'offsetTop')}}</td>
   <td>{{Spec2('CSSOM View')}}</td>
   <td></td>
  </tr>
 </tbody>
</table>

<h2 id="Compatibility" name="Compatibility">ブラウザー互換性</h2>



<p>{{Compat("api.HTMLElement.offsetTop")}}</p>

<p>仕様に従って、要素が非表示 (この要素または任意の祖先の <code>style.display</code> が <code>"none"</code>)である場合、または要素自体の <code>style.position</code> が <code>"fixed"</code> に設定される場合、このプロパティは WebKit で <code>null</code> を返します。</p>

<p>このプロパティは、要素自体の <code>style.position</code> が <code>"fixed"</code> に設定されている場合、Internet Explorer (9) で <code>null</code> を返します。(<code>display:none</code> であってもこのブラウザに影響しません。)</p>
