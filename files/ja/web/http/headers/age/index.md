---
title: Age
slug: Web/HTTP/Headers/Age
tags:
  - Caching
  - HTTP
  - ヘッダー
  - レスポンス
translation_of: Web/HTTP/Headers/Age
---
{{HTTPSidebar}}

**`Age`** ヘッダーには、プロキシーのキャッシュに入ってからの経過時間（秒）が含まれています。

`Age` ヘッダーは通常０に近い値となっています。もし `Age: 0` であるなら、 おそらくオリジンサーバーからフェッチされただけでしょう。 それ以外の場合は、一般的にプロキシーの現在の日時と HTTP レスポンスに含まれていた{{HTTPHeader("Date")}} ヘッダーとの差分から算出されます。

| ヘッダー種別                                                                         | {{Glossary("Response header","レスポンスヘッダー")}} |
| ------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------- |
| {{Glossary("Forbidden header name", "禁止ヘッダー名")}} | いいえ                                                                           |

## 構文

    Age: <delta-seconds>

## ディレクティブ

- \<delta-seconds>
  - : オブジェクトがプロキシキャッシュに入っていた時間 (秒単位) を表す負でない整数。

## 例

    Age: 24

## 仕様

| 仕様書                                   | タイトル                                        |
| ---------------------------------------- | ----------------------------------------------- |
| {{RFC("7234", "Age", "5.1")}} | Hypertext Transfer Protocol (HTTP/1.1): Caching |

## ブラウザの互換性

{{Compat("http.headers.Age")}}

## 関連情報

- {{HTTPHeader("Cache-Control")}}
- {{HTTPHeader("Expires")}}
