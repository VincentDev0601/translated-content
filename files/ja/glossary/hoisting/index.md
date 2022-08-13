---
title: Hoisting (巻き上げ、ホイスティング)
slug: Glossary/Hoisting
tags:
  - CodingScripting
  - Glossary
  - JavaScript
  - 用語集
translation_of: Glossary/Hoisting
---
<p>巻き上げ (Hoisting) は、<a href="http://www.ecma-international.org/ecma-262/6.0/index.html">ECMAScript® 2015 言語仕様</a>より前には、どんな規範的な仕様書にもなかったものです。巻き上げは JavaScript の実行コンテキスト (特に作成と実行のフェーズで) では一般的な方法と考えられていました。しかし、巻き上げの概念は誤解に繋がる可能性があります。</p>

<p>概念的には、例えば、厳密な定義では、変数や関数の宣言が物理的にコードの先頭に移動されることを示唆していますが、実際にはそうではありません。変数や関数の宣言は<em>コンパイル</em>時にメモリに格納されますが、コード内で入力された場所は変わりません。</p>

<h2 id="Learn_more" name="Learn_more">詳細情報</h2>

<h3 id="Technical_example" name="Technical_example">技術的な例</h3>

<p>JavaScript で関数宣言がコード領域を実行する前にメモリーに配置される利点は、コードで関数を定義する前に使うことができることです。例えば:</p>

<pre class="brush: js notranslate">function catName(name) {
  console.log("My cat's name is " + name);
}

catName("Tiger");

/*
上記のコードの結果: "My cat's name is Tiger"
*/
</pre>

<p>上記のコード断片はコードが動作するように書いたよう期待する方法です。今度は、関数を書く前に関数を呼び出したらどうでしょう。</p>

<pre class="brush: js notranslate">catName("Chloe");

function catName(name) {
  console.log("My cat's name is " + name);
}
/*
上記のコードの結果は: "My cat's name is Chloe"
*/
</pre>

<p>コード内で関数を書く前に、関数呼び出しを最初に書いても、コードは動作します。これは JavaScript でコンテキスト実行が動作するためです。</p>

<p>巻き上げはその他のデータ型や変数でも同様に動作します。変数は定義の前に初期化して使うことができます。しかし初期化しないと使うことができません。</p>

<h3 id="Only_declarations_are_hoisted" name="Only_declarations_are_hoisted">定義のみが巻き上げられる</h3>

<p>JavaScript では定義のみが巻き上げられ、初期化はそうでありません。変数が使用された後に定義や初期化された場合、値は undefined になります。例えば次のようになります。</p>

<pre class="brush: js notranslate">console.log(num); // undefined を返す。宣言のみが巻き上げられ、この段階では初期化が行われないため
var num; // 宣言
num = 6; // 初期化</pre>

<p>以下の例では初期化のみが行われています。巻き上げが行われませんので、変数を読み取ろうとすると ReferenceError 例外が発生します。</p>

<pre class="brush: js notranslate">console.log(num); // ReferenceError 例外が発生
num = 6; // 初期化</pre>

<p>巻き上げの例をもっと示します。</p>

<pre class="brush: js notranslate">// 例 1
// y のみが巻き上げられる

x = 1; // x を初期化し、まだ定義されていない場合は、定義する - ただし、文中に var がないので巻き上げは行われない。
console.log(x + " " + y); // '1 undefined'
// JavaScript は宣言のみを巻き上げるので、 y の値の表示はこうなる。
var y = 2; // y の宣言と初期化


// 例 2
// 巻き上げは行われないが、初期化は (まだ宣言されていない場合は) 宣言も行うので、変数は利用できる。

a = 'Cran'; // Initialize a
b = 'berry'; // Initialize b
console.log(a + "" + b); // 'Cranberry'</pre>

<h3 id="Technical_reference" name="Technical_reference">技術リファレンス</h3>

<ul>
 <li><a href="/ja/docs/Web/JavaScript/Reference/Statements/var">var 宣言</a> — MDN</li>
 <li><a href="/ja/docs/Web/JavaScript/Reference/Statements/function">関数 宣言</a> — MDN</li>
</ul>
