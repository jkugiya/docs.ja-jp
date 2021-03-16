---
title: 破壊的変更:Linux 上の .NET 用の既定の TLS 暗号スイート
description: .NET 5 での破壊的変更について学習します。Linux 上の .NET では、TLS/SSL の実行時に既定の暗号スイートとして OpenSSL 構成が尊重されるようになりました。
ms.date: 10/16/2020
ms.openlocfilehash: c28207aa5bf4324a7921deb006c57fbd5e1d6f5f
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256817"
---
# <a name="default-tls-cipher-suites-for-net-on-linux"></a>Linux 上の .NET 用の既定の TLS 暗号スイート

Linux 上の .NET で、<xref:System.Net.Security.SslStream> クラスを介した TLS/SSL を実行するとき、または <xref:System.Net.Http.HttpClient> クラスを介した HTTPS などの上位レベルの操作を実行するとき、既定の TLS 暗号スイートとして OpenSSL 構成が尊重されるようになりました。 既定の暗号スイートを明示的に構成していない場合、Linux 上の .NET で許可される暗号スイートの一覧は厳しく制限されます。

## <a name="change-description"></a>変更内容

以前のバージョンの .NET で、システム構成で既定の暗号スイートは考慮されません。 Linux 上の .NET の既定の暗号スイートの一覧は、ほとんど制約を課しません。

.NET 5 以降で、Linux 上の .NET は、*openssl.cnf* で指定されている場合、既定の暗号スイートとして OpenSSL 構成が尊重されます。 暗号スイートを明示的に構成しない場合、許可される暗号スイートは次のみになります。

- TLS 1.3 暗号スイート
- TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384
- TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256
- TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384
- TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256
- TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA384
- TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA256
- TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384
- TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256

このフォールバックの既定には、TLS 1.0 または TLS 1.1 と互換性のある暗号スイートは含まれていないため、これらの古いプロトコル バージョンは実質的に既定で無効です。

特定のセッションで SslStream に CipherSuitePolicy 値を指定しても、構成ファイルの内容や .NET フォールバックの既定は置き換えられます。

## <a name="reason-for-change"></a>変更理由

Linux で .NET を実行しているユーザーから、サードパーティの評価ツールでセキュリティの評価が高いものに <xref:System.Net.Security.SslStream> の既定の構成を変更するよう求められました。

## <a name="version-introduced"></a>導入されたバージョン

5.0

## <a name="recommended-action"></a>推奨アクション

新しい既定では、最新のクライアントまたはサーバーを使用して通信する場合、機能する可能性が高いです。 レガシ クライアントが許可されるように (またはレガシ サーバーに接続できるように) 既定の暗号スイートの一覧を増やす必要がある場合は、`CipherSuitePolicy` 値を指定するか、OpenSSL の構成ファイルを変更してください。 多くの Linux ディストリビューションでは、OpenSSL の構成ファイルは */etc/ssl/openssl.cnf* にあります。

このサンプル *openssl.cnf* ファイルは、Linux 上の .NET 5 以降の既定の暗号スイートのポリシーに相当する、それの最小限のファイルです。 システム ファイルを置き換える代わりに、お使いのシステム上のファイルにこれらの概念をマージしてください。

```ini
openssl_conf = default_conf

[default_conf]
ssl_conf = ssl_sect

[ssl_sect]
system_default = system_default_sect

[system_default_sect]
CipherString = ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-SHA384:ECDHE-ECDSA-AES128-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256
```

Red Hat Enterprise Linux、CentOS、Fedora の各ディストリビューションでの .NET アプリケーションの既定は、システム全体の暗号化ポリシーによって許可されている暗号スイートです。 これらのディストリビューションでは、*openssl.cnf* の代わりに、crypto-policies 構成が使用されます。

## <a name="affected-apis"></a>影響を受ける API

API 分析では検出できません。

<!--

### Affected APIs

- Not detectible via API analysis.

### Category

- Cryptography
- Security

-->
