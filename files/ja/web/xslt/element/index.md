---
title: XSLT 要素リファレンス
slug: Web/XSLT/Element
tags:
  - Element
  - Reference
  - XSLT
  - 概要
translation_of: Web/XSLT/Element
---
<div>{{XSLTRef}}{{QuickLinksWithSubpages("/ja/docs/Web/XSLT")}}</div>

<p>ここでは、最上位要素と指示の 2 種類の要素について説明します。最上位の要素は <code>&lt;xsl:stylesheet&gt;</code> または <code>&lt;xsl:transform&gt;</code> の子として表示する必要があります。一方、指示はテンプレートに関連付けられています。スタイルシートにはいくつかのテンプレートが含まれています。ここでは説明しない第 3 のタイプの要素はリテラル結果要素 (LRE) です。 LRE もテンプレートに表示されます。これは、HTML 変換スタイルシートの <code>&lt;hr&gt;</code> 要素など、結果ドキュメントにそのままコピーする必要のある非命令要素から構成されます。</p>

<p>関連するメモでは、 LRE 内の任意の属性と限られた数の XSLT 要素の一部の属性には、属性値テンプレートとして知られているものも含めることができます。属性値テンプレートは、属性の値を指定するために使用される埋め込み XPath 式を含む文字列です。実行時に式が評価され、XPath 式の代わりに評価結果が使用されます。たとえば、変数 "<code>image-dir</code>" が次のように定義されているとします。</p>

<pre>&lt;xsl:variable name="image-dir"&gt;/images&lt;/xsl:variable&gt;</pre>

<p>評価される式は、中括弧の中に置かれます。</p>

<pre>&lt;img src="{$image-dir}/mygraphic.jpg"/&gt;</pre>

<p>この結果、次のようになります。</p>

<pre>&lt;img src="/images/mygraphic.jpg"/&gt;</pre>

<p>続く要素の注釈には説明、構文リスト、必須およびオプションの属性のリスト、タイプと位置の説明、W3C 勧告のソース、および現在の Gecko サポートの程度の説明が含まれます。</p>

<div class="hidden">
<div class="blockIndicator todo">\{{ListSubpages}} マクロを、<a href="/ja/docs/MDN/Contribute/Structures/Compatibility_tables">ブラウザー互換性データ</a> が <code><a href="/ja/docs/Web/XSLT/Element/fallback">&lt;xsl:fallback&gt;</a></code>, <code><a href="/ja/docs/Web/XSLT/Element/import">&lt;xsl:import&gt;</a></code>, <code><a href="/ja/docs/Web/XSLT/Element/namespace-alias">&lt;xsl:namespace-alias&gt;</a></code>, <code><a href="/ja/docs/Web/XSLT/Element/number">&lt;xsl:number&gt;</a></code>, <code><a href="/ja/docs/Web/XSLT/Element/output">&lt;xsl:output&gt;</a></code>, <code><a href="/ja/docs/Web/XSLT/Element/stylesheet">&lt;xsl:stylesheet&gt;</a></code>, <code><a href="/ja/docs/Web/XSLT/Element/text">&lt;xsl:text&gt;</a></code> and <code><a href="/ja/docs/Web/XSLT/Element/value-of">&lt;xsl:value-of&gt;</a></code> で完全に移行されたときに使用してください。</div>
{{ListSubpages("/ja/docs/Web/XSLT/Element")}}</div>

<ul>
 <li><code><a href="/ja/docs/Web/XSLT/Element/apply-imports">&lt;xsl:apply-imports&gt;</a></code></li>
 <li><code><a href="/ja/docs/Web/XSLT/Element/apply-templates">&lt;xsl:apply-templates&gt;</a></code></li>
 <li><code><a href="/ja/docs/Web/XSLT/Element/attribute">&lt;xsl:attribute&gt;</a></code></li>
 <li><code><a href="/ja/docs/Web/XSLT/Element/attribute-set">&lt;xsl:attribute-set&gt;</a></code></li>
 <li><code><a href="/ja/docs/Web/XSLT/Element/call-template">&lt;xsl:call-template&gt;</a></code></li>
 <li><code><a href="/ja/docs/Web/XSLT/Element/choose">&lt;xsl:choose&gt;</a></code></li>
 <li><code><a href="/ja/docs/Web/XSLT/Element/comment">&lt;xsl:comment&gt;</a></code></li>
 <li><code><a href="/ja/docs/Web/XSLT/Element/copy">&lt;xsl:copy&gt;</a></code></li>
 <li><code><a href="/ja/docs/Web/XSLT/Element/copy-of">&lt;xsl:copy-of&gt;</a></code></li>
 <li><code><a href="/ja/docs/Web/XSLT/Element/decimal-format">&lt;xsl:decimal-format&gt;</a></code></li>
 <li><code><a href="/ja/docs/Web/XSLT/Element/element">&lt;xsl:element&gt;</a></code></li>
 <li><code><a href="/ja/docs/Web/XSLT/Element/fallback">&lt;xsl:fallback&gt;</a></code> <em>(対応外)</em></li>
 <li><code><a href="/ja/docs/Web/XSLT/Element/for-each">&lt;xsl:for-each&gt;</a></code></li>
 <li><code><a href="/ja/docs/Web/XSLT/Element/if">&lt;xsl:if&gt;</a></code></li>
 <li><code><a href="/ja/docs/Web/XSLT/Element/import">&lt;xsl:import&gt;</a></code> <em>(ほぼ対応)</em></li>
 <li><code><a href="/ja/docs/Web/XSLT/Element/include">&lt;xsl:include&gt;</a></code></li>
 <li><code><a href="/ja/docs/Web/XSLT/Element/key">&lt;xsl:key&gt;</a></code></li>
 <li><code><a href="/ja/docs/Web/XSLT/Element/message">&lt;xsl:message&gt;</a></code></li>
 <li><code><a href="/ja/docs/Web/XSLT/Element/namespace-alias">&lt;xsl:namespace-alias&gt;</a></code> <em>(対応外)</em></li>
 <li><code><a href="/ja/docs/Web/XSLT/Element/number">&lt;xsl:number&gt;</a></code> <em>(一部対応)</em></li>
 <li><code><a href="/ja/docs/Web/XSLT/Element/otherwise">&lt;xsl:otherwise&gt;</a></code></li>
 <li><code><a href="/ja/docs/Web/XSLT/Element/output">&lt;xsl:output&gt;</a></code> <em>(一部対応)</em></li>
 <li><code><a href="/ja/docs/Web/XSLT/Element/param">&lt;xsl:param&gt;</a></code></li>
 <li><code><a href="/ja/docs/Web/XSLT/Element/preserve-space">&lt;xsl:preserve-space&gt;</a></code></li>
 <li><code><a href="/ja/docs/Web/XSLT/Element/processing-instruction">&lt;xsl:processing-instruction&gt;</a></code></li>
 <li><code><a href="/ja/docs/Web/XSLT/Element/sort">&lt;xsl:sort&gt;</a></code></li>
 <li><code><a href="/ja/docs/Web/XSLT/Element/strip-space">&lt;xsl:strip-space&gt;</a></code></li>
 <li><code><a href="/ja/docs/Web/XSLT/Element/stylesheet">&lt;xsl:stylesheet&gt;</a></code> <em>(一部対応)</em></li>
 <li><code><a href="/ja/docs/Web/XSLT/Element/template">&lt;xsl:template&gt;</a></code></li>
 <li><code><a href="/ja/docs/Web/XSLT/Element/text">&lt;xsl:text&gt;</a></code> <em>(一部対応)</em></li>
 <li><code><a href="/ja/docs/Web/XSLT/Element/transform">&lt;xsl:transform&gt;</a></code></li>
 <li><code><a href="/ja/docs/Web/XSLT/Element/value-of">&lt;xsl:value-of&gt;</a></code> <em>(一部対応)</em></li>
 <li><code><a href="/ja/docs/Web/XSLT/Element/variable">&lt;xsl:variable&gt;</a></code></li>
 <li><code><a href="/ja/docs/Web/XSLT/Element/when">&lt;xsl:when&gt;</a></code></li>
 <li><code><a href="/ja/docs/Web/XSLT/Element/with-param">&lt;xsl:with-param&gt;</a></code></li>
</ul>
