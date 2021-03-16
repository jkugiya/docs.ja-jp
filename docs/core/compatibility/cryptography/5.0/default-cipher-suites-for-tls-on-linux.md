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
# <a name="default-tls-cipher-suites-for-net-on-linux"></a><span data-ttu-id="3fa57-103">Linux 上の .NET 用の既定の TLS 暗号スイート</span><span class="sxs-lookup"><span data-stu-id="3fa57-103">Default TLS cipher suites for .NET on Linux</span></span>

<span data-ttu-id="3fa57-104">Linux 上の .NET で、<xref:System.Net.Security.SslStream> クラスを介した TLS/SSL を実行するとき、または <xref:System.Net.Http.HttpClient> クラスを介した HTTPS などの上位レベルの操作を実行するとき、既定の TLS 暗号スイートとして OpenSSL 構成が尊重されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="3fa57-104">.NET, on Linux, now respects the OpenSSL configuration for default cipher suites when doing TLS/SSL via the <xref:System.Net.Security.SslStream> class or higher-level operations, such as HTTPS via the <xref:System.Net.Http.HttpClient> class.</span></span> <span data-ttu-id="3fa57-105">既定の暗号スイートを明示的に構成していない場合、Linux 上の .NET で許可される暗号スイートの一覧は厳しく制限されます。</span><span class="sxs-lookup"><span data-stu-id="3fa57-105">When default cipher suites aren't explicitly configured, .NET on Linux uses a tightly restricted list of permitted cipher suites.</span></span>

## <a name="change-description"></a><span data-ttu-id="3fa57-106">変更内容</span><span class="sxs-lookup"><span data-stu-id="3fa57-106">Change description</span></span>

<span data-ttu-id="3fa57-107">以前のバージョンの .NET で、システム構成で既定の暗号スイートは考慮されません。</span><span class="sxs-lookup"><span data-stu-id="3fa57-107">In previous .NET versions, .NET does not respect system configuration for default cipher suites.</span></span> <span data-ttu-id="3fa57-108">Linux 上の .NET の既定の暗号スイートの一覧は、ほとんど制約を課しません。</span><span class="sxs-lookup"><span data-stu-id="3fa57-108">The default cipher suite list for .NET on Linux is very permissive.</span></span>

<span data-ttu-id="3fa57-109">.NET 5 以降で、Linux 上の .NET は、*openssl.cnf* で指定されている場合、既定の暗号スイートとして OpenSSL 構成が尊重されます。</span><span class="sxs-lookup"><span data-stu-id="3fa57-109">Starting in .NET 5, .NET on Linux respects the OpenSSL configuration for default cipher suites when it's specified in *openssl.cnf*.</span></span> <span data-ttu-id="3fa57-110">暗号スイートを明示的に構成しない場合、許可される暗号スイートは次のみになります。</span><span class="sxs-lookup"><span data-stu-id="3fa57-110">When cipher suites aren't explicitly configured, the only permitted cipher suites are as follows:</span></span>

- <span data-ttu-id="3fa57-111">TLS 1.3 暗号スイート</span><span class="sxs-lookup"><span data-stu-id="3fa57-111">TLS 1.3 cipher suites</span></span>
- <span data-ttu-id="3fa57-112">TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384</span><span class="sxs-lookup"><span data-stu-id="3fa57-112">TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384</span></span>
- <span data-ttu-id="3fa57-113">TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256</span><span class="sxs-lookup"><span data-stu-id="3fa57-113">TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256</span></span>
- <span data-ttu-id="3fa57-114">TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384</span><span class="sxs-lookup"><span data-stu-id="3fa57-114">TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384</span></span>
- <span data-ttu-id="3fa57-115">TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256</span><span class="sxs-lookup"><span data-stu-id="3fa57-115">TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256</span></span>
- <span data-ttu-id="3fa57-116">TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA384</span><span class="sxs-lookup"><span data-stu-id="3fa57-116">TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA384</span></span>
- <span data-ttu-id="3fa57-117">TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA256</span><span class="sxs-lookup"><span data-stu-id="3fa57-117">TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA256</span></span>
- <span data-ttu-id="3fa57-118">TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384</span><span class="sxs-lookup"><span data-stu-id="3fa57-118">TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384</span></span>
- <span data-ttu-id="3fa57-119">TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256</span><span class="sxs-lookup"><span data-stu-id="3fa57-119">TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256</span></span>

<span data-ttu-id="3fa57-120">このフォールバックの既定には、TLS 1.0 または TLS 1.1 と互換性のある暗号スイートは含まれていないため、これらの古いプロトコル バージョンは実質的に既定で無効です。</span><span class="sxs-lookup"><span data-stu-id="3fa57-120">Since this fallback default doesn't include any cipher suites that are compatible with TLS 1.0 or TLS 1.1, these older protocol versions are effectively disabled by default.</span></span>

<span data-ttu-id="3fa57-121">特定のセッションで SslStream に CipherSuitePolicy 値を指定しても、構成ファイルの内容や .NET フォールバックの既定は置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="3fa57-121">Supplying a CipherSuitePolicy value to SslStream for a specific session will still replace the configuration file content and/or .NET fallback default.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="3fa57-122">変更理由</span><span class="sxs-lookup"><span data-stu-id="3fa57-122">Reason for change</span></span>

<span data-ttu-id="3fa57-123">Linux で .NET を実行しているユーザーから、サードパーティの評価ツールでセキュリティの評価が高いものに <xref:System.Net.Security.SslStream> の既定の構成を変更するよう求められました。</span><span class="sxs-lookup"><span data-stu-id="3fa57-123">Users running .NET on Linux requested that the default configuration for <xref:System.Net.Security.SslStream> be changed to one that provided a high security rating from third-party assessment tools.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="3fa57-124">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="3fa57-124">Version introduced</span></span>

<span data-ttu-id="3fa57-125">5.0</span><span class="sxs-lookup"><span data-stu-id="3fa57-125">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="3fa57-126">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="3fa57-126">Recommended action</span></span>

<span data-ttu-id="3fa57-127">新しい既定では、最新のクライアントまたはサーバーを使用して通信する場合、機能する可能性が高いです。</span><span class="sxs-lookup"><span data-stu-id="3fa57-127">The new defaults are likely to work when communicating with modern clients or servers.</span></span> <span data-ttu-id="3fa57-128">レガシ クライアントが許可されるように (またはレガシ サーバーに接続できるように) 既定の暗号スイートの一覧を増やす必要がある場合は、`CipherSuitePolicy` 値を指定するか、OpenSSL の構成ファイルを変更してください。</span><span class="sxs-lookup"><span data-stu-id="3fa57-128">If you need to expand the default cipher suite list to accept legacy clients (or to contact legacy servers), either specify a `CipherSuitePolicy` value or change the OpenSSL configuration file.</span></span> <span data-ttu-id="3fa57-129">多くの Linux ディストリビューションでは、OpenSSL の構成ファイルは */etc/ssl/openssl.cnf* にあります。</span><span class="sxs-lookup"><span data-stu-id="3fa57-129">On many Linux distributions, the OpenSSL configuration file is at */etc/ssl/openssl.cnf*.</span></span>

<span data-ttu-id="3fa57-130">このサンプル *openssl.cnf* ファイルは、Linux 上の .NET 5 以降の既定の暗号スイートのポリシーに相当する、それの最小限のファイルです。</span><span class="sxs-lookup"><span data-stu-id="3fa57-130">This sample *openssl.cnf* file is a minimal file that's equivalent to the default cipher suites policy for .NET 5 and later on Linux.</span></span> <span data-ttu-id="3fa57-131">システム ファイルを置き換える代わりに、お使いのシステム上のファイルにこれらの概念をマージしてください。</span><span class="sxs-lookup"><span data-stu-id="3fa57-131">Instead of replacing the system file, merge these concepts with the file that's present on your system.</span></span>

```ini
openssl_conf = default_conf

[default_conf]
ssl_conf = ssl_sect

[ssl_sect]
system_default = system_default_sect

[system_default_sect]
CipherString = ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-SHA384:ECDHE-ECDSA-AES128-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256
```

<span data-ttu-id="3fa57-132">Red Hat Enterprise Linux、CentOS、Fedora の各ディストリビューションでの .NET アプリケーションの既定は、システム全体の暗号化ポリシーによって許可されている暗号スイートです。</span><span class="sxs-lookup"><span data-stu-id="3fa57-132">On the Red Hat Enterprise Linux, CentOS, and Fedora distributions, .NET applications default to the cipher suites permitted by the system-wide cryptographic policies.</span></span> <span data-ttu-id="3fa57-133">これらのディストリビューションでは、*openssl.cnf* の代わりに、crypto-policies 構成が使用されます。</span><span class="sxs-lookup"><span data-stu-id="3fa57-133">On these distributions, use the crypto-policies configuration instead of *openssl.cnf*.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="3fa57-134">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="3fa57-134">Affected APIs</span></span>

<span data-ttu-id="3fa57-135">API 分析では検出できません。</span><span class="sxs-lookup"><span data-stu-id="3fa57-135">Not detectible via API analysis.</span></span>

<!--

### Affected APIs

- Not detectible via API analysis.

### Category

- Cryptography
- Security

-->
