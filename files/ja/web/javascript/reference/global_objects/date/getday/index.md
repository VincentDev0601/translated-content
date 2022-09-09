---
title: Date.prototype.getDay()
slug: Web/JavaScript/Reference/Global_Objects/Date/getDay
---
{{JSRef}}

**`getDay()`** メソッドは、地方時に基づき、指定された日付の「曜日」を返します。 0 は日曜日を表します。「日」を取得する方法は {{jsxref("Date.prototype.getDate()")}} をご覧ください。

{{EmbedInteractiveExample("pages/js/date-getday.html", "shorter")}}

## 構文

```
dateObj.getDay()
```

### 返値

整数値で、 0 から 6 までの値を取り、地方時に基づいて指定された日付の曜日に対応し、 0 は日曜日、 1 は月曜日、 2 は火曜日のようになります。

## 例

### getDay の使用

以下の 2 行目の文は、{{jsxref("Date")}} オブジェクト `Xmas95` の値に基づき、`weekday` に 1 という値を代入します。1995 年 12 月 25 日は月曜日です。

```js
var Xmas95 = new Date('December 25, 1995 23:15:30');
var weekday = Xmas95.getDay();

console.log(weekday); // 1
```

> **Note:** **注:** 必要であれば、曜日の完全な名前 (例えば "`Monday`") は {{jsxref("DateTimeFormat", "Intl.DateTimeFormat")}} に `options` 引数を設定することで取得することができます。このメソッドを使用すれば、国際化がより簡単になります。
>
> ```js
> var options = { weekday: 'long'};
> console.log(new Intl.DateTimeFormat('en-US', options).format(Xmas95));
> // Monday
> console.log(new Intl.DateTimeFormat('de-DE', options).format(Xmas95));
> // Montag
> ```

## 仕様書

| 仕様書                                                                                                   |
| -------------------------------------------------------------------------------------------------------- |
| {{SpecName('ESDraft', '#sec-date.prototype.getday', 'Date.prototype.getDay')}} |

## ブラウザーの互換性

{{Compat("javascript.builtins.Date.getDay")}}

## 関連情報

- {{jsxref("Date.prototype.getUTCDate()")}}
- {{jsxref("Date.prototype.getUTCDay()")}}
- {{jsxref("Date.prototype.setDate()")}}
