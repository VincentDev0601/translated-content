---
title: HTMLTableRowElement.insertCell
slug: Web/API/HTMLTableRowElement/insertCell
tags:
  - DOM
  - Gecko
  - Gecko DOM Reference
  - tableRow
translation_of: Web/API/HTMLTableRowElement/insertCell
---
<div>
 {{ApiRef}}</div>
<h2 id="Summary" name="Summary">概要</h2>
<p>テーブル行に新規セルを挿入し、セルへの参照を返します。</p>
<h2 id="Syntax" name="Syntax">構文</h2>
<pre class="syntaxbox">var <var>cell</var> = <var>HTMLTableRowElement</var>.insertCell(<var>index</var>);
</pre>
<ul>
 <li><code>HTMLTableRowElement</code> : HTML の tr 要素への参照</li>
 <li><code>index</code> : 新しいセルのセルインデックス</li>
 <li><code>cell</code> : 新しいセルへの参照が割り当てられる。<br>
  <code>index</code> が -1 またはセル数と同じである場合は、セルは行内の最後のセルとして挿入される。 <code>index</code> が省略されているか行のセル数より大きい場合は IndexSizeError が発生する。</li>
</ul>
<h2 id="Example" name="Example">例</h2>
<pre class="brush:html">&lt;table&gt;
  &lt;tr id="row0"&gt;
    &lt;td&gt;Original cell&lt;/td&gt;
  &lt;/tr&gt;
&lt;/table&gt;

&lt;script type="text/javascript"&gt;

function addCell(tableRowID) {
  // 引数に指定された id によりテーブル行要素への参照を取得
  var rowRef = document.getElementById(tableRowID);

  // セルインデックス 0 の箇所にセルを挿入
  var newCell   = rowRef.insertCell(0);

  // セルにテキストノードを追加
  var newText  = document.createTextNode('New cell')
  newCell.appendChild(newText);
}

// 対象テーブル行の id をパラメータとし、関数 addCell を実行
addCell('row0');

&lt;/script&gt;
</pre>
<p>対象テーブルを valid な HTML とするには、tr 要素が最低でもひとつ td 要素を持っていなければなりません。</p>
<p><code>insertCell</code> はテーブルにセルを直接的に挿入して新しい参照を返すものである事に注意して下さい。このメソッドを用いる場合、 予め {{domxref("document.createElement()")}} によって td 要素を生成する必要はありません。</p>
<h2 id="Browser_compatibility" name="Browser_compatibility">ブラウザ互換性</h2>
<h3 id="Gecko-specific_notes" name="Gecko-specific_notes">Gecko 固有の注意事項</h3>
<ul>
 <li>Gecko 20.0 (Firefox 20.0 / Thunderbird 20.0 / SeaMonkey 2.17) 以降では、引数 <var>index</var> は HTML の仕様に則り省略可能となり、初期値は <code>-1</code> となりました。</li>
</ul>
<h2 id="Specification" name="Specification">仕様書</h2>
<ul>
 <li><a href="http://www.w3.org/TR/DOM-Level-2-HTML/html.html#ID-68927016">DOM Level 2 HTML: insertCell</a></li>
 <li><a class="external" href="http://www.whatwg.org/specs/web-apps/current-work/multipage/tabular-data.html#dom-tr-insertcell">HTML Living Standard HTMLTableRowElement.insertCell</a></li>
</ul>
