---
title: tabs.MutedInfo
slug: Mozilla/Add-ons/WebExtensions/API/tabs/MutedInfo
translation_of: Mozilla/Add-ons/WebExtensions/API/tabs/MutedInfo
---
<div>{{AddonSidebar()}}</div>

<p>This object contains a boolean indicating whether the tab is muted, and the reason for the last state change.</p>

<h2 id="型">型</h2>

<p>値の型はオブジェクトです。次のプロパティを含みます:</p>

<dl class="reference-values">
 <dt><code>extensionId</code>{{optional_inline}}</dt>
 <dd><code>string</code>. ミュートの状態を最後に変更した拡張機能のIDです。もし拡張機能がミュートの状態の最後の変更の理由でないなら設定されません。</dd>
 <dt><code>muted</code></dt>
 <dd><code>boolean</code>. タブが現在ミュートかどうか。Equivalent to whether the muted audio indicator is showing.</dd>
 <dt><code>reason</code>{{optional_inline}}</dt>
 <dd>{{WebExtAPIRef('tabs.MutedInfoReason')}}. ミュートもしくはアンピューとに設定された理由。Not set if the tab's muted state has never been changed.</dd>
</dl>

<h2 id="ブラウザ互換性">ブラウザ互換性</h2>



<p>{{Compat("webextensions.api.tabs.MutedInfo")}}</p>

<p>{{WebExtExamples}}</p>

<div class="note"><strong>Acknowledgements</strong>

<p>This API is based on Chromium's <a href="https://developer.chrome.com/extensions/tabs#type-MutedInfo"><code>chrome.tabs</code></a> API. This documentation is derived from <a href="https://chromium.googlesource.com/chromium/src/+/master/chrome/common/extensions/api/tabs.json"><code>tabs.json</code></a> in the Chromium code.</p>

<p>Microsoft Edge compatibility data is supplied by Microsoft Corporation and is included here under the Creative Commons Attribution 3.0 United States License.</p>
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
