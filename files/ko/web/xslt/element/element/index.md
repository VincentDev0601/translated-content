---
title: element
slug: Web/XSLT/Element/element
tags:
  - XSLT_Reference
translation_of: Web/XSLT/Element/element
---
<p>{{ XsltRef() }}</p>
<p><code>&lt;xsl:element&gt;</code> 요소는 출력 문서에 요소를 만듭니다.</p>
<h3 id=".EB.AC.B8.EB.B2.95" name=".EB.AC.B8.EB.B2.95">문법</h3>
<pre>&lt;xsl:element name=NAME namespace=URI use-attribute-sets=LIST-OF-NAMES &gt;
	TEMPLATE
&lt;/xsl:template&gt;</pre>
<h3 id=".ED.95.84.EC.88.98_.EC.86.8D.EC.84.B1" name=".ED.95.84.EC.88.98_.EC.86.8D.EC.84.B1">필수 속성</h3>
<dl>
 <dt>
  <code>name</code></dt>
 <dd>
  출력 요소에 바라는 이름을 지정합니다. 이름은 유효한 QName이어야 합니다.</dd>
</dl>
<h3 id=".EC.84.A0.ED.83.9D_.EC.86.8D.EC.84.B1" name=".EC.84.A0.ED.83.9D_.EC.86.8D.EC.84.B1">선택 속성</h3>
<dl>
 <dt>
  <code>namespace</code></dt>
 <dd>
  출력 요소에 이름공간을 지정합니다.</dd>
 <dt>
  <code>use-attribute-sets</code></dt>
 <dd>
  출력 요소에 쓸 이름 붙인 속성 집합을 나열합니다. 이름은 공백 문자로 구분해야 합니다.</dd>
</dl>
<h3 id=".ED.83.80.EC.9E.85" name=".ED.83.80.EC.9E.85">타입</h3>
<p>명령, 템플릿 안에 나타남.</p>
<h3 id=".EC.A0.95.EC.9D.98" name=".EC.A0.95.EC.9D.98">정의</h3>
<p><a class="external" href="http://www.w3.org/TR/xslt#section-Creating-Elements-with-xsl:element">XSLT section 7.1.2, Creating Elements with xsl:element</a></p>
<h3 id="Gecko_.EC.A7.80.EC.9B.90" name="Gecko_.EC.A7.80.EC.9B.90">Gecko 지원</h3>
<p>지원함.</p>
