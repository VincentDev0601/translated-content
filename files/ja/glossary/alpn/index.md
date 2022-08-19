---
title: ALPN
slug: Glossary/ALPN
tags:
  - ALPN
  - Draft
  - Glossary
  - NeedsContent
  - TLS
translation_of: Glossary/ALPN
---
**Application-Layer {{Glossary("Protocol")}} Negotiation** (**ALPN**) は、 {{Glossary("TLS")}} 拡張であり、追加のラウンドトリップを必要とせずに、暗号化された接続をネゴシエートするアプリケーションレイヤープロトコルを示します。

| プロトコル                                     | 識別シーケンス                                         |
| ---------------------------------------------- | ------------------------------------------------------ |
| {{Glossary("HTTP")}}/1.1               | `0x68 0x74 0x74 0x70 0x2F 0x31 0x2E 0x31` ("http/1.1") |
| {{Glossary("HTTP 2", "HTTP/2")}}   | `0x68 0x32` ("h2")                                     |
| HTTP/2 over cleartext {{Glossary("TCP")}} | `0x68 0x32 0x63` ("h2c")                               |

## 仕様

| 仕様             | ステータス                             | 備考     |
| ---------------- | -------------------------------------- | -------- |
| {{RFC(7301)}} | <span class="spec-RFC">IETF RFC</span> | 初回定義 |

## 関連項目

- [IANA 登録 ALPN 識別子](https://www.iana.org/assignments/tls-extensiontype-values/tls-extensiontype-values.xhtml#alpn-protocol-ids)
