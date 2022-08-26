---
title: tabs.MutedInfoReason
slug: Mozilla/Add-ons/WebExtensions/API/tabs/MutedInfoReason
translation_of: Mozilla/Add-ons/WebExtensions/API/tabs/MutedInfoReason
---
<div>{{AddonSidebar()}}</div>

<p>タブがミュート・アンミュートになった理由を指定します。</p>

<h2 id="型">型</h2>

<p>値のタイプは文字列型です。可能な値:</p>

<dl>
 <dt>"capture"</dt>
 <dd>タブのキャプチャが開始され、ミュート状態に強いられました。</dd>
 <dt>"extension"</dt>
 <dd>拡張機能がミュート状態に設定しました。もしこれが理由なら、{{WebExtAPIRef("tabs.mutedInfo")}}の<code>extensionId</code>が責任のある拡張機能のIDを含んでいます。</dd>
 <dt>"user"</dt>
 <dd>ユーザがミュート状態に設定しました。</dd>
</dl>

<h2 id="ブラウザ互換性">ブラウザ互換性</h2>



<p>{{Compat("webextensions.api.tabs.MutedInfoReason")}}</p>

<p>{{WebExtExamples}}</p>

<div class="note"><strong>謝辞</strong>

<p>このAPIはChromiumの<a href="https://developer.chrome.com/extensions/tabs#type-MutedInfoReason"><code>chrome.tabs</code></a> APIに基づいています。このドキュメントはChromiumコードの<a href="https://chromium.googlesource.com/chromium/src/+/master/chrome/common/extensions/api/tabs.json"><code>tabs.json</code></a>から派生したものです。</p>

<p>Microsoft Edgeの互換性データはMicrosoft Corporationから提供されており、Creative Commons Attribution 3.0 United States Licenseのもとにここに含まれています。</p>
</div>

<div class="hidden">
<pre>// Copyright 2015 The Chromium Authors. All rights reserved.
//
// Redistribution and use in source and binary forms, with or without
// modification, are permitted provided that the following conditions are
// met:
//
//    * Redistributions of source code must retain the above copyright
// notice, this list of conditions and the following disclaimer.
//    * Redistributions in binary form must reproduce the above
// copyright notice, this list of conditions and the following disclaimer
// in the documentation and/or other materials provided with the
// distribution.
//    * Neither the name of Google Inc. nor the names of its
// contributors may be used to endorse or promote products derived from
// this software without specific prior written permission.
//
// THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS
// "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT
// LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR
// A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT
// OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
// SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT
// LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE,
// DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY
// THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
// (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
// OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
</pre>
</div>
