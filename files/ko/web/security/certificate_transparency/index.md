---
title: 인증서 투명성
slug: Web/Security/Certificate_Transparency
l10n:
  sourceCommit: 199c317d91bf506a81a6f68f53d6c63499651dff
---

{{QuickLinksWithSubpages("/ko/docs/Web/Security")}}

**인증서 투명성**은 잘못된 인증서 발급을 방지하고 모니터링하도록 설계된 개방형 프레임워크로, [RFC 9162](https://www.rfc-editor.org/rfc/rfc9162)에 정의되어 있습니다. 인증서 투명성을 통해 새로 발급된 인증서는 공개적으로 실행되고, 종종 독립적인 **CT 로그**에 '로그'됩니다. 이 로그는 발급된 TLS 인증서의 추가 전용 암호화 보증 레코드를 유지합니다.

이러한 방식으로 인증 기관(CA)은 훨씬 더 많은 공개 조사와 감독을 받을 수 있습니다. CA/B 포럼 **기본 요구 사항**을 위반하는 것과 같은 잠재적으로 악의적 사항이 있는 인증서를 훨씬 더 빠르게 감지하고 해지시킬 수 있습니다. 또한 브라우저 벤더와 루트 저장소 관리자는 그들이 불신하기로 결정할 수 있는 문제가 있는 CA에 대해 더 많은 정보에 입각한 결정을 내릴 수 있습니다.

## 배경

CT 로그는 **Merkle 트리** 데이터 구조를 기반으로 구축됩니다. 노드는 하위 노드의 **암호화 해시**로 레이블되고, 리프 노드에는 실제 데이터 조각의 해시가 포함됩니다. 따라서 루트 노드의 레이블은 트리의 다른 모든 노드에 따라 달라집니다.

인증서 투명성의 맥락에서 리프 노드에 의해 해시된 데이터는 오늘날 운영되는 다양한 CA에서 발급된 인증서입니다. 인증서 포함은 O(log n) 시간 복잡도로 효율적으로 생성되고 검증할 수 있는 **감사 증명**을 통해 검증될 수 있습니다.

인증서 투명성은 CA 침해(2011년 DigiNotar 위반), 의심스러운 결정안(2012년 Trustwave 하위 루트 사건) 및 기술적 발급 문제(말레이시아의 Digicert Sdn Bhd에 의한 512비트 취약 인증서 발급)를 배경으로 2013년에 시작되었습니다.

## 구현

인증서가 CT 로그에 제출되면 **서명된 인증서 타임스탬프**(SCT)가 생성되어 반환됩니다. 이는 인증서가 제출되었고 로그에 추가된다는 증거로 사용됩니다.

명세서에는 호환 서버가 연결할 때 **반드시** TLS 클라이언트에 이러한 다수의 SCT를 제공해야 한다고 명시되어 있습니다. 이는 다음과 같은 다양한 메커니즘을 통해 수행될 수 있습니다.

- 서명된 인증서 타임스탬프를 리프 인증서에 직접 포함하는 X.509v3 인증서 확장
- 핸드셰이크 중에 전송된 `signed_certificate_timestamp` 유형의 TLS 확장
- OCSP 스테이플링(즉, `status_request` TLS 확장) 및 하나 이상의 SCT로 `SignedCertificateTimestampList` 제공

X.509 인증서 확장을 사용하면 포함된 SCT가 발급 CA에 의해 결정됩니다. 2021년 6월부터 가장 활발하게 사용되고 공개적으로 신뢰할 수 있는 인증서에는 이 확장에 포함된 투명성 데이터가 포함되어 있습니다. 이 방법은 웹 서버를 수정할 필요가 없는 방법입니다.

후자의 방법을 사용하는 경우 필요한 데이터를 전송하려면 서버를 업데이트해야 합니다. 이 벙법의 장점은 서버 운영자가 TLS 확장/스테이플링된 OCSP 응답을 통해 전송된 SCT를 제공하는 CT 로그 소스를 사용자 정의할 수 있다는 것입니다.

## 브라우저 요구 사항

Google Chrome은 notBefore 날짜가 2018년 4월 30일 이후인 모든 인증서 대해 CT 로그 포함을 요구합니다. 사용자는 비호환 TLS 인증서를 사용하여 사이트를 방문할 수 없습니다. 이전에 Chrome은 _Extended Validation_ (EV)와 Symantec 발급 인증서에 CT 포함을 요구했었습니다.

Apple은 Safari 및 기타 서버가 서버 인증서를 신뢰하기 위해 여러개의 SCT를 [요구합니다](https://support.apple.com/en-gb/HT205280).

Firefox는 현재 사용자가 방문하는 사이트에 대해 CT 로그 사용을 확인하거나 요구하지 [않습니다](https://bugzilla.mozilla.org/show_bug.cgi?id=1281469).
