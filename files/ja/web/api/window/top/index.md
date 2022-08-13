---
title: window.top
slug: Web/API/Window/top
tags:
  - API
  - DOM
  - HTML
  - Window
translation_of: Web/API/Window/top
---
<div>{{APIRef}}</div>

<p>ウィンドウ階層における最上位のウィンドウへの参照を返します。</p>

<h2 id="構文">構文</h2>

<pre class="syntaxbox">var <var>topWindow</var> = window.top;
</pre>

<h2 id="注記">注記</h2>

<p>{{domxref("window.parent")}} プロパティは、現在のウィンドウの直近の親を返しますが、<code>window.top</code> は、ウィンドウオブジェクトの階層における最上位のウィンドウを返します。</p>

<p>このプロパティは、親、あるいは、階層になっているウィンドウのサブフレーム内にあるウィンドウを扱っていて、最上位のフレームセットを取得したいときに特に役立ちます。</p>

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
   <td>{{SpecName('HTML WHATWG', 'browsers.html#dom-top', 'window.top')}}</td>
   <td>{{Spec2('HTML WHATWG')}}</td>
   <td></td>
  </tr>
  <tr>
   <td>{{SpecName('HTML5 W3C', 'browsers.html#dom-top', 'window.top')}}</td>
   <td>{{Spec2('HTML5 W3C')}}</td>
   <td>初期の定義</td>
  </tr>
 </tbody>
</table>

<h2 id="ブラウザー互換性">ブラウザー互換性</h2>



<p>{{Compat("api.Window.top")}}</p>
