---
title: 미디어 쿼리 초보자 안내서
slug: Learn/CSS/CSS_layout/Media_queries
tags:
  - 미디어 쿼리
  - 씨에스에스
  - 조판
  - 초보자
  - 학습
translation_of: Learn/CSS/CSS_layout/Media_queries
original_slug: Learn/CSS/CSS_layout/미디어_쿼리_초보자_안내서
---
<p>{{learnsidebar}}{{PreviousMenuNext("Learn/CSS/CSS_layout/Responsive_Design", "Learn/CSS/CSS_layout/Legacy_Layout_Methods", "Learn/CSS/CSS_layout")}}</p>

<p><strong>CSS Media Query</strong>는 예를 들어 "뷰포트가 480 픽셀보다 넓다."라고 여러분이 지정한 규칙에 브라우저 및 장치 환경이 일치하는 경우에만 씨에스에스를 적용할 수 있는 방법을 제공합니다. 미디어 쿼리는 반응형 웹 디자인의 핵심 부분이다. 뷰포트의 크기에 따라 서로 다른 조판을 생성할 수 있기 때문이다. 그러나 예를들면 사용자는 마우스가 아닌 터치스크린을 사용하는지와 같이 실행 중인 사이트 환경에 대한 여러 내용들을 탐지하는 데도 사용할 수 있습니다. 이번 단원에서는 먼저 미디어 쿼리에 사용된 구문에 대해 배우고, 이어 해당 구문을 가공의 예제에서 사용하여 간단한 디자인이 어떻게 반응할 수 있는지 살펴보겠습니다.</p>

<table class="learn-box standard-table">
 <tbody>
  <tr>
   <th scope="row">선결 사항:</th>
   <td>에이치티엠엘의 기초인 (<a href="/ko/docs/Learn/HTML/Introduction_to_HTML">에이치티엠엘 입문서</a>를 공부하세요), 그리고 씨에스에스의 작동 방식을 파악하기 위해 (<a href="/en-US/docs/Learn/CSS/First_steps">씨에스에스 첫걸음</a>과 <a href="/ko/docs/Learn/CSS/Building_blocks">씨에스에스 구성 블록</a>를 공부하세요.)</td>
  </tr>
  <tr>
   <th scope="row">목표:</th>
   <td>미디어 쿼리를 사용하는 방법과 그걸 이용해 반응형 디자인을 생성하기 위한 가장 대표적인 접근법 파악하기.</td>
  </tr>
 </tbody>
</table>

<h2 id="미디어_쿼리_기본">미디어 쿼리 기본</h2>

<p>가장 간단한 미디어 쿼리 구문은 다음과 같습니다:</p>

<pre class="brush: css">@media <em>media-type</em> and (<em>media-feature-rule</em>) {
  /* CSS rules go here */
}</pre>

<p>미디어 쿼리 구문의 구성 요소:</p>

<ul>
 <li>여기 코드가 어떤 미디어를 위한 것인지 브라우저에 알려주는 미디어 유형(예를 들어, 인쇄 또는 화면).</li>
 <li>괄호로 묶은 씨에스에스 규칙이 적용되기 위해 전달되어야 하는 규칙 또는 조건문 격인 미디어 표현식.</li>
 <li>조건문을 통과하고 미디어 유형이 올바른 경우 적용되는 씨에스에스 규칙 집합.</li>
</ul>

<h3 id="미디어_유형">미디어 유형</h3>

<p>당신이 지정할 수 있는 미디어 유형</p>

<ul>
 <li><code>all</code></li>
 <li><code>print</code></li>
 <li><code>screen</code></li>
 <li><code>speech</code></li>
</ul>

<p>다음 미디어 쿼리는 페이지가 인쇄된 경우에만 본문을 12pt로 설정합니다. 페이지가 브라우저에 로드될 때에는 적용되지 않습니다.</p>

<pre class="brush: css"><code>@media print {
    body {
        font-size: 12pt;
    }
}</code></pre>

<div class="blockIndicator note">
<p><strong>참고</strong>: 수준 3 미디어 쿼리 규격에 정의된 여러 가지 다른 미디어 유형이 있습니다. 이들은 사장되었으니 피해야 합니다.</p>
</div>

<div class="blockIndicator note">
<p><strong>참고</strong>: 미디어 유형은 선택사항입니다. 미디어 쿼리에 미디어 유형을 표시하지 않으면 미디어 쿼리는 기본값으로 모든 미디어 유형에 대한 것으로 해석됩니다.</p>
</div>

<h3 id="미디어_기능_규칙">미디어 기능 규칙</h3>

<p>미디어 유형을 지정한 뒤에 규칙을 적용할 미디어 기능을 선정할 수 있습니다.</p>

<h4 id="너비와_높이">너비와 높이</h4>

<p>반응형 디자인을(그리고 광범위한 브라우저 지원이 되도록) 만들기 위해 가장 자주 탐문하는 기능은 뷰포트 너비이며, <code>min-width</code>와 <code>max-width</code>, <code>width</code> 등의 미디어 기능을 활용하여 뷰포트가 특정 너비 이상 또는 이하인 경우 씨에스에스를 적용할 수 있습니다.</p>

<p>이러한 특징들은 다른 화면 크기에 반응하는 조판을 생성하는 데 사용됩니다. 예를 들어 뷰포트가 정확히 600픽셀인 경우 본문 색상을 빨간색으로 변경하려면 다음과 같은 미디어 쿼리를 사용합니다.</p>

<pre class="brush: css"><code>@media screen and (width: 600px) {
    body {
        color: red;
    }
}</code></pre>

<p><a href="https://mdn.github.io/css-examples/learn/media-queries/width.html">이 예제를</a> 브라우저에서 열거나 <a href="https://github.com/mdn/css-examples/blob/master/learn/media-queries/width.html">소스를 보세요</a>.</p>

<p><code>width</code>(및 <code>height</code>) 미디어 기능은 범위 지정에 사용될 수 있다. 따라서 <code>min-</code> or <code>max-</code> 접두사를 붙이게 되면 최소값인지 최대값인지 표시할 수 있다. 예를 들어 뷰포트가 400 픽셀보다 좁은 경우 색깔을 파란색으로 만들기 위해 <code>max-width</code>:를 사용할 수 있다.</p>

<pre class="brush: css"><code>@media screen and (max-width: 400px) {
    body {
        color: blue;
    }
}</code></pre>

<p><a href="https://mdn.github.io/css-examples/learn/media-queries/max-width.html">이 예제를</a>를 브라우저에서 열거나 <a href="https://github.com/mdn/css-examples/blob/master/learn/media-queries/max-width.html">소스를 보세요</a>.</p>

<p>실제로 최소값 또는 최대값을 사용하는 것이 반응형 디자인인 경우에 훨씬 유용하므로 <code>width</code> 또는 <code>height</code> 값을 사용하는 경우는 좀처럼 흔치앖습니다.</p>

<p>미디어 쿼리 규격 수준 4 및 5에 소개된 최신 기능 중 일부가 제한적으로 브라우저 지원이 되지만, 당신이 테스트할 수 있는 다른 여러 미디어 기능이 있습니다. 각 기능은 브라우저 지원 정보와 함께 MDN에 문서화되어 있으니만큼 당신은 <a href="/en-US/docs/Web/CSS/Media_Queries/Using_media_queries#Media_features">미디어 쿼리 사용: 미디어 기능</a>에서 전체 목록을 찾을 수 있습니다.</p>

<h4 id="방향성">방향성</h4>

<p>잘 지원되는 미디어 기능 중 하나는 <code>orientation</code>로 세로 모드인지 가로 모드인지를 검사할 수 있도록 해줍니다. 장치가 가로 방향에 있는 경우 본문 텍스트 색상을 변경하려면 다음과 같은 미디어 쿼리를 사용합니다.</p>

<pre class="brush: css"><code>@media (orientation: landscape) {
    body {
        color: rebeccapurple;
    }
}</code></pre>

<p><a href="https://mdn.github.io/css-examples/learn/media-queries/orientation.html">이 예제를</a> 브라우저에서 열거나 <a href="https://github.com/mdn/css-examples/blob/master/learn/media-queries/orientation.html">소스를 보세요</a>.</p>

<p>표준 데스크톱 뷰에는 가로 방향이 주종을 이루고 있으며, 이 가로 방향에서 잘 작동하는 디자인은 휴대폰 또는 태블릿상에서 세로 모드로 볼 때 잘 작동하지 않을 수 있습니다. (가로/세로 모드의) 방향성 테스트는 여러분이 세로 모드의 장치에 최적화된 조판을 생성할 수 있게 도움을 줄 수 있습니다.</p>

<h4 id="포인팅_장치의_사용">포인팅 장치의 사용</h4>

<p>수준 4 규격의 일부로 <code>hover</code> 미디어 기능이 도입되었다. 이 기능은 사용자가 요소 위에 (마우스 커서를) 올릴 수 있는 능력을 가진 조건인지를 시험할 수 있다는 것을 의미합니다. 본질적으로 사람들이 어떤 종류의 포인팅 장치를 사용하는지를 말합니다. 터치 스크린 및 키보드 네비게이션은 요소 위에 식별자를 올릴 수 없습니다.</p>

<pre class="brush: css"><code>@media (hover: hover) {
    body {
        color: rebeccapurple;
    }
}</code></pre>

<p><a href="https://mdn.github.io/css-examples/learn/media-queries/hover.html">이 예제를</a> 브라우저에서 열거나 <a href="https://github.com/mdn/css-examples/blob/master/learn/media-queries/hover.html">소스를 보세요</a>.</p>

<p>사용자가 포인팅 장치를 사용할 수 없다고 파악했다면 기본적으로 대화형 기능을 표시할 수 있습니다. 포인팅 장치를 사용할 수 있는 사용자의 경우 링크에 마우스를 올리는 기능을 이용하도록 선택할 수 있습니다.</p>

<p>마찬가지로 <code>pointer</code> 미디어 기능이 수준 4 규격에 포함되어 있다. 이것은 <code>none</code>과 <code>fine</code> <code>coarse</code>의 세 가지 값을 취할 수 있다. <code>fine</code> 포인터는 마우스나 트랙패드와 같은 것이다. 이 값으로 사용자가 작은 영역을 정확하게 공략할 수 있게 된다. <code>coarse</code> 포인터는 터치스크린상에 손가락을 말한다. <code>none</code> 값은 사용자가 포인팅 장치가 없다는 의미이다. 아마도 키보드 단독 또는 음성 명령으로 탐색하고 있다고 하겠다.</p>

<p><code>pointer</code> 사용이 당신에게 주는 잇점이 있다면 사용자가 화면상에서 상호 작용하는 유형에 반응하는 더 나은 인터페이스를 설계할 수 있다는 것입니다. 예를 들어, 사용자가 터치스크린으로 장치와 상호 작용하고 있다는 것을 알면 히트 영역을 더 크게 만들 수 있습니다.</p>

<h2 id="더_복잡한_미디어_쿼리">더 복잡한 미디어 쿼리</h2>

<p>당신은 가능한 모든 이종의 미디어 쿼리를 가지고 그것들을 결합하거나, 쿼리 목록을 만들고 싶을 수도 있다. 그 중 어느 경우가 (조건문과) 일치할 수 있습니다.</p>

<h3 id="논리곱_미디어_쿼리">"논리곱" 미디어 쿼리</h3>

<p><code>and</code>를 사용해 미디어 기능을 결합할 수 있습니다. 이는 마치 앞에서 미디어 유형과 기능을 결합하기 위해 <code>and</code>를 사용했던 방식과 같습니다. 예를 들어, <code>min-width</code>와 <code>orientation</code>의 논리곱 조건을 테스트해보고 싶을 수도 있습니다. 여기서 에이치티엠엘 본문 텍스트가 파란색이 되는 유일한 경우는 뷰포트의 너비가 최소 400픽셀 이상이고 장치가 가로 모드인 경우에만 해당합니다.</p>

<pre class="brush: css"><code>@media screen and (min-width: 400px) and (orientation: landscape) {
    body {
        color: blue;
    }
}</code></pre>

<p><a href="https://mdn.github.io/css-examples/learn/media-queries/and.html">이 예제를</a> 브라우저에서 열거나 <a href="https://github.com/mdn/css-examples/blob/master/learn/media-queries/and.html">소스를 보세요</a>.</p>

<h3 id="논리합_미디어_쿼리">"논리합" 미디어 쿼리</h3>

<p>만약 여러분에게 쿼리는 잔뜩있는 데, 그 중 일도 일치할 수 없다면, 여러분은 해당 쿼리들을 콤마로 분리할 수 있습니다. 아래 예제에서 뷰포트가 최소 400픽셀 너비 또는 장치가 가로 보기 방향이라면 텍스트는 파란색이 될 것입니다. 둘 중 하나라도 사실이 아니라면 쿼리의 조건문은 일치합니다.</p>

<pre class="brush: css"><code>@media screen and (min-width: 400px), screen and (orientation: landscape) {
    body {
        color: blue;
    }
}</code></pre>

<p><a href="https://mdn.github.io/css-examples/learn/media-queries/or.html">이 예제를</a> 브라우저에서 열거나 <a href="https://github.com/mdn/css-examples/blob/master/learn/media-queries/or.html">소스를 보세요</a>.</p>

<p>"</p>

<h3 id="부정_논리_미디어_쿼리">"부정 논리" 미디어 쿼리</h3>

<p><code>not</code> 연산자를 사용하여 전체 미디어 쿼리를 부정할 수 있습니다. 이것은 미디어 쿼리의 전체 의미를 반대로 뒤집습니다. 따라서 다음 예에서 텍스트는 보기 방향이 세로일 경우에만 파란색이 됩니다.</p>

<pre class="brush: css"><code>@media not all and (orientation: landscape) {
    body {
        color: blue;
    }
}</code></pre>

<p><a href="https://mdn.github.io/css-examples/learn/media-queries/not.html">이 예제를</a> 브라우저에서 열거나 <a href="https://github.com/mdn/css-examples/blob/master/learn/media-queries/not.html">소스를 보세요</a>.</p>

<h2 id="분기점을_선정하는_방법">분기점을 선정하는 방법</h2>

<p>반응형 디자인 초창기에는 많은 디자이너가 매우 구체적인 화면 크기를 공략 대상으로 삼으려고 시도했습니다. 인기있는 휴대폰 및 태블릿 화면의 크기 목록이 공개되어 해당 기기의 뷰포트와 깔끔하게 일치하도록 디자인을 만들 수 있게 되었습니다.</p>

<p>지금은 엄청나게 다양한 크기의 지나치게 너무 많은 장치가 있어 그런 방식은 현실성이 없습니다. 즉, 모든 디자인마다 (기기의) 특정 크기에 맞추는 공략보다 더 나은 접근 방법은 콘텐츠가 어떤 식으로든 깨지기 시작하는 해당 (기기의) 크기에 해당하는 디자인을 변경하는 것입니다. 어쩌면 선 길이가 너무 길어지거나 상자 형태의 사이드바가 찌그러져 읽기가 어려워질 수도 있습니다. 그 지경이 되면 미디어 쿼리를 사용하여 이용할 수 있는 공간 대비 개선된 형태의 사이트가 나오도록 디자인을 변경해야할 지점인 것입니다. 이는 사용 기기의 정확한 화면 크기가 무엇이든 상관없이 모든 범주에 맞는 전방위적인 접금법을 말합니다. 미디어 쿼리가 도입되는 지점을 <strong>breakpoints</strong>라고 합니다.</p>

<p>Firefox DevTools의 <a href="/en-US/docs/Tools/Responsive_Design_Mode">반응형 디자인 모드</a>는 이러한 분기점이 어느 부분이 될지 알아내는 데 매우 유용합니다. 동 툴은 미디어 쿼리를 추가하고 디자인을 조정하면서 콘텐츠가 개선되는 위치를 파악하기 위해 뷰포트를 쉽게 크거나 작게 만들 수 있습니다.</p>

<p><img alt="파이어폭스 개발툴상에 조판 갈무리" src="https://mdn.mozillademos.org/files/16867/rwd-mode.png" style="height: 917px; width: 1443px;"></p>

<h2 id="능동_학습_모바일_우선_반응형_디자인">능동 학습: 모바일 우선 반응형 디자인</h2>

<p>대체로 반응형 디자인에 대한 두 가지 접근법을 취할 수 있습니다. 데스크톱 또는 가장 넓은 뷰로 시작한 뒤 뷰포트의 축소에 맞춰 요소를 주변으로 이동시키기 위한 분기점을 추가하거나 가장 작은 뷰로 시작한 뒤에 뷰포트의 크기 확대에 맞춰 조판을 추가할 수 있습니다. 이 두 번째 접근법은 <strong>mobile first</strong> 반응형 디자인으로 설명되며 종종 선호되는 최상의 접근법입니다.</p>



<p>가장 작은 장치용 뷰는 일반 대열에서 나타나는 것처럼 종종 단순한 단일 열 형태의 콘텐츠가 됩니다. 즉 여러분은 작은 장치용이라 많은 조판을 할 필요가 없다는 말입니다. 다시말해 소스를 순서대로 잘 정렬하면 기본값으로 읽을 수 있는 조판이 됩니다.</p>

<p>아래의 길라잡이는 매우 간단한 조판으로 동 접근 방식을 안내해 줄 것입니다. 사이트 제작 과정에서는 미디어 쿼리내에서 조정할 수 있는 것이 더 많을 수 있지만, 그 접근 방식은 정확히 동일하게 됩니다.</p>

<h3 id="길라잡이_간단한_모바일_우선_조판">길라잡이: 간단한 모바일 우선 조판</h3>

<p>우리는 조판에 포함된 다양한 요소에 배경색을 추가하기 위해 일정한 씨에스에스를 적용한 에이치티엠엘 문서를 가지고 출발합니다.</p>

<pre class="brush: css"><code>* {
    box-sizing: border-box;
}

body {
    width: 90%;
    margin: 2em auto;
    font: 1em/1.3 Arial, Helvetica, sans-serif;
}

a:link,
a:visited {
    color: #333;
}

nav ul,
    aside ul {
    list-style: none;
    padding: 0;
}

nav a:link,
nav a:visited {
    background-color: rgba(207, 232, 220, 0.2);
    border: 2px solid rgb(79, 185, 227);
    text-decoration: none;
    display: block;
    padding: 10px;
    color: #333;
    font-weight: bold;
}

nav a:hover {
    background-color: rgba(207, 232, 220, 0.7);
}

.related {
    background-color: rgba(79, 185, 227, 0.3);
    border: 1px solid rgb(79, 185, 227);
    padding: 10px;
}

.sidebar {
    background-color: rgba(207, 232, 220, 0.5);
    padding: 10px;
}

article {
    margin-bottom: 1em;
}
</code></pre>

<p>우리는 우리가 조판에 변경을 가하지는 않았지만, 문서의 원본은 콘텐츠를 읽을 수 있는 방식으로 순서대로 정렬됩니다. 이것은 중요한 첫 번째 단계이며, 콘텐츠가 화면 읽기 프로그램(tts)에 의해 소리내여 읽혀질 경우 콘텐츠가 (읽을 문자열를) 이해될 수도록 보장합니다.</p>

<pre class="brush: html"><code>&lt;body&gt;
    &lt;div class="wrapper"&gt;
      &lt;header&gt;
        &lt;nav&gt;
          &lt;ul&gt;
            &lt;li&gt;&lt;a href=""&gt;사이트 소개&lt;/a&gt;&lt;/li&gt;
            &lt;li&gt;&lt;a href=""&gt;연락처&lt;/a&gt;&lt;/li&gt;
            &lt;li&gt;&lt;a href=""&gt;우리팀 안내&lt;/a&gt;&lt;/li&gt;
            &lt;li&gt;&lt;a href=""&gt;블로그&lt;/a&gt;&lt;/li&gt;
          &lt;/ul&gt;
        &lt;/nav&gt;
      &lt;/header&gt;
      &lt;main&gt;
        &lt;article&gt;
          &lt;div class="content"&gt;
            &lt;h1&gt;채식주의자!&lt;/h1&gt;
            &lt;p&gt;
              ...
            &lt;/p&gt;
          &lt;/aside&gt;
        &lt;/article&gt;

        &lt;aside class="sidebar"&gt;
          &lt;h2&gt;채식에 관한 외부 링크&lt;/h2&gt;
          &lt;ul&gt;
            &lt;li&gt;
              ...
            &lt;/li&gt;
          &lt;/ul&gt;
        &lt;/aside&gt;
      &lt;/main&gt;

      &lt;footer&gt;&lt;p&gt;&amp;copy;2019&lt;/p&gt;&lt;/footer&gt;
    &lt;/div&gt;
  &lt;/body&gt;
</code></pre>

<p>이 간단한 조판은 모바일에서도 잘 작동한다. 우리가 파이어폭스 데브툴 내부 반응형 디자인 모드에서 조판을 본다면, 우리는 그것이 사이트의 직관적인 모바일 뷰로 보더라도 꽤 잘 작동한다는 것을 알 수 있다.</p>

<p><a href="https://mdn.github.io/css-examples/learn/media-queries/step1.html">이 예제를</a> 브라우저에서 열거나 <a href="https://github.com/mdn/css-examples/blob/master/learn/media-queries/step1.html">소스를 보세요</a>.</p>

<p><strong>당신이 우리의 진행 과정대로 이 예제를 실행해보려면 <a href="https://github.com/mdn/css-examples/blob/master/learn/media-queries/step1.html">step1.html</a>의 사본을 당신 컴퓨터에 만드세요.</strong></p>

<p>이 지점부터는 반응형 디자인 모드뷰가 점차 확대되어 라인 길이가 상당히 길어지는 모습을 확인할 정도가 되며, 수평선 형태의 탐색 메뉴가 표시될 공간을 갖추고 있습니다. 여기에서 우리는 첫 번째 미디어 쿼리를 추가할 것입니다. 사용자가 텍스트 크기를 늘리게 되면, 텍스트 크기가 작은 장비를 가진 사람과 비교해 비슷한 라인 길이지만 뷰포트가 확대되는 순간에 분기점이 발생한다는 의미입니다. 따라서 우리는 ems 단위를 사용할 것입니다.</p>

<p><strong>아래 코드를 step1.html 씨에스에스의 하단에 추가하세요.</strong></p>

<pre class="brush: css"><code>@media screen and (min-width: 40em) {
    article {
        display: grid;
        grid-template-columns: 3fr 1fr;
        column-gap: 20px;
    }

    nav ul {
        display: flex;
    }

    nav li {
        flex: 1;
    }
}
</code></pre>

<p>이 씨에스에스는 문서 안에 있는 문서 콘텐츠와 aside 요소 내부 관련 정보까지 2단 조판을 우리에게 제공합니다. 또한 우리는 가변상자를 사용하여 탐색 메뉴를 일렬로 배치했습니다.</p>

<p><a href="https://mdn.github.io/css-examples/learn/media-queries/step2.html">2단계</a> 파일을 브라우저에서 열거나 <a href="https://github.com/mdn/css-examples/blob/master/learn/media-queries/step2.html">소스를 보세요</a>.</p>

<p>사이드바가 새 단을 형성할 수 있는 충분한 공간이 있다고 느낄 때까지 너비를 계속 확장합니다. 미디어 쿼리안에서 주요 요소를 두 개의 열 형태의 격자로 만들 것입니다. 그런 다음 두 개의 사이드바가 서로 나란히 정렬되도록 문서의 {{cssxref("margin-bottom")}}을 제거해야하며, 바닥글 상단에 {{cssxref("border")}}(테두리)를 추가하게 됩니다. 일반적으로 이러한 미세 조정은 각 분기점 도달시 디자인을 좋게 보이게 하기 위해 여러분이 할 일입니다.</p>

<p><strong>다시 한 번 아래 코드를 step1.html 씨에스에스의 하단에 추가합니다.</strong></p>

<pre class="brush: css"><code>@media screen and (min-width: 70em) {
    main {
        display: grid;
        grid-template-columns: 3fr 1fr;
        column-gap: 20px;
    }

    article {
        margin-bottom: 0;
    }

    footer {
        border-top: 1px solid #ccc;
        margin-top: 2em;
    }
}</code>
</pre>

<p><a href="https://mdn.github.io/css-examples/learn/media-queries/step3.html">3단계</a> 파일을 브라우저에서 열거나 <a href="https://github.com/mdn/css-examples/blob/master/learn/media-queries/step3.html">소스를 보세요</a>.</p>

<p>최종 예제를 다른 너비로 보면 사용 가능한 너비에 따라 디자인이 반응하고 단일 열, 2열 또는 3열로 작동하는 방법을 볼 수 있습니다. 이것은 모바일 우선 반응형 디자인의 아주 간단한 예입니다.</p>

<h2 id="당신에게_정말_미디어_쿼리가_필요할까요">당신에게 정말 미디어 쿼리가 필요할까요?</h2>

<p>가변상자, 격자 및 다단 조판은 모두 굳이 미디어 쿼리를 필요로 하지 않고도 가변적이며 심지어 반응형 구성 요소를 만들 수 있는 방법을 제공합니다. 미디어 쿼리를 추가하지 않고도 이러한 조판 메서드를 사용해 원하는 것을 달성할 수 있는지 고려할 가치가 있습니다. 예를 들어, 여러분은 적어도 200 픽셀 너비의 카드 집합을 원할 수 있으며, 최대 200 픽셀이라면 주요 문서 부분에 맞아떨어질 수 있습니다. 이는 미디어 쿼리를 전혀 사용하지 않고 격자 조판만으로 얻을 수 있습니다.</p>

<p>이것은 아래 용법으로 달성될 수 있습니다.</p>

<pre class="brush: html"><code>&lt;ul class="grid"&gt;
    &lt;li&gt;
        &lt;h2&gt;카드 1&lt;/h2&gt;
        &lt;p&gt;...&lt;/p&gt;
    &lt;/li&gt;
    &lt;li&gt;
        &lt;h2&gt;카드 2&lt;/h2&gt;
        &lt;p&gt;...&lt;/p&gt;
    &lt;/li&gt;
    &lt;li&gt;
        &lt;h2&gt;카드 3&lt;/h2&gt;
        &lt;p&gt;...&lt;/p&gt;
    &lt;/li&gt;
    &lt;li&gt;
        &lt;h2&gt;카드 4&lt;/h2&gt;
        &lt;p&gt;...&lt;/p&gt;
    &lt;/li&gt;
    &lt;li&gt;
        &lt;h2&gt;카드 5&lt;/h2&gt;
        &lt;p&gt;...&lt;/p&gt;
    &lt;/li&gt;
&lt;/ul&gt;</code></pre>

<pre class="brush: css"><code>.grid {
    list-style: none;
    margin: 0;
    padding: 0;
    display: grid;
    gap: 20px;
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
}

.grid li {
    border: 1px solid #666;
    padding: 10px;
}</code></pre>

<p><a href="https://mdn.github.io/css-examples/learn/media-queries/grid.html">이 격자 예제를</a> 브라우저에서 열거나 <a href="https://github.com/mdn/css-examples/blob/master/learn/media-queries/grid.html">소스를 보세요</a>.</p>

<p>상기 예제를 브라우저에서 열면 화면을 넓히거나 좁히거나 하여 열 트랙 수가 변경되는 것을 확인할 수 있습니다. 이 방법의 좋은 점은 격자가 뷰포트 너비를 보는 게 아니라 해당 구성 요소에 맞춰 이용할 수 있는 너비를 살핀다는 것입니다. 당신에게 미디어 쿼리가 전혀 필요하지 않을수도! 있다는 제안으로 이번 절을 마감하는 것은 이상하게 보일 수도 있습니다. 그러나 실제로 미디어 쿼리로 강화된 현대적 조판 메서드를 잘 사용하면 최상의 결과를 얻을 수 있습니다.</p>

<h2 id="요약정리">요약정리</h2>

<p>여러분은 이 단원에서 미디어 쿼리에 대해 배웠으며 모바일 우선 반응형 디자인을 실제로 생성하는 방법도 알아 보았습니다.</p>

<p>우리가 만든 것을 시작점로 더 많은 미디어 쿼리 조건을 테스트할 수 있습니다. 예를 들어, 방문자가 <code>pointer</code> 미디어 기능을 사용하여 거친 포인터를 가지고 있는 것을 감지하면 탐색 메뉴의 크기를 변경할 수 있습니다.</p>

<p>또한 서로 다른 구성 요소를 추가하고 미디어 쿼리를 추가한다든지 또는 가변상자나 격자와 같은 조판 방법을 사용하는 것이 구성 요소를 반응형으로 만드는 가장 적절한 방법인지 여부를 실험할 수 있습니다. 바른 방식 혹은 그른 방식 따윈 없습니다. 말하자면 어떤 것이 디자인과 콘텐츠에 가장 적합한지 실험하고 관찰해야 합니다.</p>



<p>{{PreviousMenuNext("Learn/CSS/CSS_layout/Responsive_Design", "Learn/CSS/CSS_layout/Legacy_Layout_Methods", "Learn/CSS/CSS_layout")}}</p>

<h2 id="이번_단위에는">이번 단위에는</h2>

<ul>
 <li><a href="/ko/docs/Learn/CSS/CSS_layout/Introduction">씨에스에스 조판 소개</a></li>
 <li><a href="/ko/docs/Learn/CSS/CSS_layout/일반_흐름">일반 대열</a></li>
 <li><a href="/ko/docs/Learn/CSS/CSS_layout/Flexbox">가변상자</a></li>
 <li><a href="/ko/docs/Learn/CSS/CSS_layout/Grids">격자</a></li>
 <li><a href="/ko/docs/Learn/CSS/CSS_layout/Floats">부동체</a></li>
 <li><a href="/ko/docs/Learn/CSS/CSS_layout/위치잡기">위치잡기</a></li>
 <li><a href="/ko/docs/Learn/CSS/CSS_layout/Multiple-column_Layout">다단 조판</a></li>
 <li><a href="/ko/docs/Learn/CSS/CSS_layout/반응형_디자인">반응형 디자인</a></li>
 <li><a href="/ko/docs/Learn/CSS/CSS_layout/미디어_쿼리_초보자_안내서">미디어 쿼리 초보자 안내서</a></li>
 <li><a href="/ko/docs/Learn/CSS/CSS_layout/레거시_조판_메서드">레거시 조판 메서드</a></li>
 <li><a href="/ko/docs/Learn/CSS/CSS_layout/%EC%9D%B4%EC%A0%84_%EB%B8%8C%EB%9D%BC%EC%9A%B0%EC%A0%80_%EC%A7%80%EC%9B%90">이전 브라우저 지원</a></li>
 <li><a href="/ko/docs/Learn/CSS/CSS_layout/Fundamental_Layout_Comprehension">조판 이해도 필수 평가</a></li>
</ul>
