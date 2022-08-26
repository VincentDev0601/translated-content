---
title: clipboard
slug: Mozilla/Add-ons/WebExtensions/API/clipboard
tags:
  - API
  - Add-ons
  - Clipboard
  - Extensions
  - Reference
  - WebExtensions
translation_of: Mozilla/Add-ons/WebExtensions/API/clipboard
---
<div>{{AddonSidebar}}</div>

<p>クリップボード API は、拡張機能がシステムのクリップボードに要素をクリップするのを可能にします。現在この API は画像のコピーだけをサボートしていますが、将来的にはテキストとHTMLのコピーをサボートする計画です。</p>

<p>この WebExtension API は主に標準の web クリップボード API が<a href="https://w3c.github.io/clipboard-apis/#writing-to-clipboard">クリップボードに画像を書き込めない</a>ために存在しています。標準 web API にこの力が備わった時には、このAPI は非推奨になるはずです。</p>

<p>クリップボードの読み込みはこの API でサポートしません。なぜならクリップボードはすでに標準 web プラットホーム API を用いて読むことができるからです。<a href="/ja/Add-ons/WebExtensions/Interact_with_the_clipboard#Reading_from_the_clipboard">クリップボードとやりとりする</a>を見てください。</p>

<p>この API は Chrome の <code><a class="external external-icon" href="https://developer.chrome.com/apps/clipboard">clipboard</a></code> API に基づきますが、その API はChrome アプリだけで利用できて、拡張機能ではできません。</p>

<p>この API を使うには "clipboardWrite" <a href="/ja/docs/Mozilla/Add-ons/WebExtensions/manifest.json/permissions">パーミッション</a>が必要です。</p>

<h2 id="Functions" name="Functions">関数</h2>

<dl>
 <dt>{{WebExtAPIRef("clipboard.setImageData()")}}</dt>
 <dd>画像をクリップボードにコピーする</dd>
</dl>

<h2 id="Browser compatibility" name="Browser compatibility">ブラウザー互換性</h2>

<p>{{Compat("webextensions.api.clipboard", 1, 1)}} {{WebExtExamples("h2")}}</p>

<div class="note"><strong>Acknowledgements</strong>

<p>この API は Chromiumの <a href="https://developer.chrome.com/apps/clipboard"><code>chrome.clipboard</code></a> API に基づきます。</p>
</div>
