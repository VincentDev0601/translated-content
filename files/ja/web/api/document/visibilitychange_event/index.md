---
title: 'Document: visibilitychange イベント'
slug: Web/API/Document/visibilitychange_event
tags:
  - API
  - Document
  - Event
  - Reference
  - Visibility
  - Web
  - visibilitychange
translation_of: Web/API/Document/visibilitychange_event
---
<div>{{APIRef}}</div>

<p><code>visibilitychange</code> イベントは、タブのコンテンツが表示状態または非表示状態になったときに document に発生します。</p>

<table class="properties">
 <tbody>
  <tr>
   <th scope="row">バブリング</th>
   <td>あり</td>
  </tr>
  <tr>
   <th scope="row">キャンセル可能</th>
   <td>いいえ</td>
  </tr>
  <tr>
   <th scope="row">インターフェイス</th>
   <td>{{domxref("Event")}}</td>
  </tr>
  <tr>
   <th scope="row">イベントハンドラープロパティ</th>
   <td>{{domxref("Document.onvisibilitychange", "onvisibilitychange")}}</td>
  </tr>
 </tbody>
</table>

<h2 id="Usage_notes" name="Usage_notes">使用上の注意</h2>

<p>このイベントには、更新された文書の表示・非表示状態が含まれていませんが、この情報は document の {{domxref("Document.visibilityState", "visibilityState")}} プロパティから取得することができます。</p>

<h2 id="Examples" name="Examples">例</h2>

<p>この例は、文書が表示状態になった時に音楽を再生し、文書が非表示になった時に音楽を停止します。</p>

<pre class="brush:js notranslate">document.addEventListener("visibilitychange", function() {
  if (document.visibilityState === 'visible') {
    backgroundMusic.play();
  } else {
    backgroundMusic.pause();
  }
});
</pre>

<h2 id="Specifications" name="Specifications">仕様書</h2>

<table class="standard-table">
 <thead>
  <tr>
   <th scope="col">仕様書</th>
   <th scope="col">状態</th>
   <th scope="col">備考</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td>{{SpecName('Page Visibility API','#sec-visibilitychange-event','visibilitychange')}}</td>
   <td>{{Spec2('Page Visibility API')}}</td>
   <td></td>
  </tr>
 </tbody>
</table>

<h2 id="Browser_compatibility" name="Browser_compatibility">ブラウザーの互換性</h2>

<p>{{Compat("api.Document.visibilitychange")}}</p>

<h2 id="See_also" name="See_also">関連情報</h2>

<ul>
 <li><a href="/ja/docs/DOM/Using_the_Page_Visibility_API">Page Visibility API の使用</a></li>
 <li>{{domxref("Document.visibilityState")}}</li>
</ul>
