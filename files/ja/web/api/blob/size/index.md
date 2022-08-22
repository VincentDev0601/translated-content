---
title: Blob.size
slug: Web/API/Blob/size
tags:
  - API
  - Blob
  - Bytes
  - File API
  - Files
  - Property
  - Reference
  - length
  - size
translation_of: Web/API/Blob/size
---
<div class="boxed translate-rendered text-content">
<div>{{APIRef("File API")}}</div>

<p>{{domxref("Blob")}} インターフェイスの <strong><code>size</code></strong> プロパティは、{{domxref("Blob")}} または {{domxref("File")}} のサイズをバイト単位で返します。</p>

<h2 id="シンタックス">シンタックス</h2>

<pre class="syntaxbox notranslate">var <em>sizeInBytes</em> = <em>blob</em>.size
</pre>

<h3 id="値">値</h3>

<p><code>Blob</code> (または <code>Blob</code> ベースのオブジェクト、例えば{{domxref("File")}}) 内に含まれるデータのバイト数。</p>

<h2 id="例">例</h2>

<p>この例では、<code>file</code> 型の {{HTMLElement("input")}} 要素を使用して、ユーザーにファイルのグループを尋ね、それらのファイルを繰り返し処理して、その名前と長さをバイト単位で出力しています。</p>

<pre class="brush:js notranslate">// fileInputは HTMLInputElement &lt;input type="file" multiple id="myfileinput"&gt; です。
var fileInput = document.getElementById("myfileinput");

// files は FileList オブジェクトです (NodeList に似ています)。
var files = fileInput.files;

for (var i = 0; i &lt; files.length; i++) {
  console.log(files[i].name + " has a size of " + files[i].size + " Bytes");
}</pre>

<h2 id="仕様">仕様</h2>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="col">仕様書</th>
   <th scope="col">ステータス</th>
   <th scope="col">コメント</th>
  </tr>
  <tr>
   <td>{{SpecName('File API', '#dfn-size', 'Blob.size')}}</td>
   <td>{{Spec2('File API')}}</td>
   <td>初期定義</td>
  </tr>
 </tbody>
</table>

<h2 id="ブラウザの互換性">ブラウザの互換性</h2>

<div>
<p>{{Compat("api.Blob.size")}}</p>
</div>

<h2 id="あわせて参照">あわせて参照</h2>

<ul>
 <li>{{domxref("Blob")}}</li>
 <li>
  <p><a href="/ja/docs/Web/API/File/Using_files_from_web_applications">Web アプリケーションからのファイルの使用</a></p>
 </li>
</ul>
</div>
