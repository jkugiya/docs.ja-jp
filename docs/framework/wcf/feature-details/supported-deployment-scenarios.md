---
description: '詳細情報: サポートされている展開シナリオ'
title: サポートされている展開シナリオ
ms.date: 03/30/2017
ms.assetid: 3399f208-3504-4c70-a22e-a7c02a8b94a6
ms.openlocfilehash: 090f0912660fc113bad8640afb1360b64071fa78
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793364"
---
# <a name="supported-deployment-scenarios"></a><span data-ttu-id="19a77-103">サポートされている展開シナリオ</span><span class="sxs-lookup"><span data-stu-id="19a77-103">Supported deployment scenarios</span></span>

<span data-ttu-id="19a77-104">部分的に信頼されたアプリケーションでの使用がサポートされている Windows Communication Foundation (WCF) 機能のサブセットは、WCF を使用する場合のすべてではなく、一部のシナリオの要件を満たすように設計されています。</span><span class="sxs-lookup"><span data-stu-id="19a77-104">The subset of Windows Communication Foundation (WCF) features supported for use in partially trusted applications is designed to meet the requirements of some, but not all, scenarios for using WCF.</span></span> <span data-ttu-id="19a77-105">サーバーでは、WCF は、セキュリティ上の理由から、ASP.NET 2.0 Medium Trust アクセス許可セットでサードパーティ製アプリケーションを実行するインターネット規模の共有ホスティングプロバイダーの要件を満たしています。</span><span class="sxs-lookup"><span data-stu-id="19a77-105">On the server, WCF meets the requirements of Internet-scale shared hosting providers who run third-party applications in the ASP.NET 2.0 Medium Trust permission set for security reasons.</span></span> <span data-ttu-id="19a77-106">クライアントでは、WCF 部分信頼のサポートは、 [ClickOnce 配置](/visualstudio/deployment/clickonce-security-and-deployment) や WPF の XAML ブラウザーアプリケーションテクノロジなどの配置テクノロジの要件を満たすように設計されています。これにより、信頼されていないサイトからのデスクトップアプリケーションのシームレスで安全な展開が可能になります。</span><span class="sxs-lookup"><span data-stu-id="19a77-106">On the client, WCF partial trust support is designed to meet the requirements of deployment technologies such as [ClickOnce Deployment](/visualstudio/deployment/clickonce-security-and-deployment) or WPF's XAML Browser Application technology, which allow seamless and secure deployment of desktop applications from untrusted sites.</span></span>

## <a name="minimum-permission-requirements"></a><span data-ttu-id="19a77-107">最小アクセス許可の要件</span><span class="sxs-lookup"><span data-stu-id="19a77-107">Minimum permission requirements</span></span>

<span data-ttu-id="19a77-108">WCF では、次の標準の名前付きアクセス許可セットのいずれかで実行されるアプリケーションの機能のサブセットをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="19a77-108">WCF supports a subset of features in applications running under either of the following standard named permission sets:</span></span>

- <span data-ttu-id="19a77-109">中程度の信頼アクセス許可</span><span class="sxs-lookup"><span data-stu-id="19a77-109">Medium Trust permissions</span></span>

- <span data-ttu-id="19a77-110">インターネット ゾーン アクセス許可</span><span class="sxs-lookup"><span data-stu-id="19a77-110">Internet Zone permissions</span></span>

<span data-ttu-id="19a77-111">部分的に信頼されたアプリケーションで、より制限の厳しい権限で WCF を使用しようとすると、実行時にセキュリティ例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="19a77-111">Attempting to use WCF in partially trusted applications with more restrictive permissions may result in security exceptions at runtime.</span></span>

<span data-ttu-id="19a77-112">このようなアクセス許可セットでサポートされる機能の詳細については、「 [Partial Trust Feature Compatibility](partial-trust-feature-compatibility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="19a77-112">For more information about the features supported in these permission sets, see [Partial Trust Feature Compatibility](partial-trust-feature-compatibility.md).</span></span>

## <a name="partial-trust-on-the-server"></a><span data-ttu-id="19a77-113">サーバー上の部分信頼</span><span class="sxs-lookup"><span data-stu-id="19a77-113">Partial trust on the server</span></span>

<span data-ttu-id="19a77-114">ASP.NET Web アプリケーションホスティングサービスの多くの商用プロバイダーは、サーバー上で実行されているアプリケーションが ASP.NET 2.0 Medium Trust アクセス許可セットで実行されることを義務付けています。</span><span class="sxs-lookup"><span data-stu-id="19a77-114">Many commercial providers of ASP.NET Web application hosting services mandate that applications running on their servers run in the ASP.NET 2.0 Medium Trust permission set.</span></span> <span data-ttu-id="19a77-115">WCF サービスは、、、 <xref:System.ServiceModel.BasicHttpBinding> <xref:System.ServiceModel.WebHttpBinding> またはをトランスポートレベルのセキュリティで使用している場合に、これらの環境で実行でき <xref:System.ServiceModel.WSHttpBinding> ます。</span><span class="sxs-lookup"><span data-stu-id="19a77-115">WCF services can run in these environments provided they use the <xref:System.ServiceModel.BasicHttpBinding>, the <xref:System.ServiceModel.WebHttpBinding>, or the <xref:System.ServiceModel.WSHttpBinding> with transport-level security.</span></span>

<span data-ttu-id="19a77-116">中程度の信頼のホスト環境で実行されている WCF サービスは、クライアント要求への応答として他のサーバーにメッセージを送信することで、中間層サービスとして機能することもできます。</span><span class="sxs-lookup"><span data-stu-id="19a77-116">WCF services running in Medium Trust hosting environments can also act as middle-tier services by sending messages to other servers in response to client requests.</span></span> <span data-ttu-id="19a77-117">ホスティング環境が適切な <xref:System.Net.WebPermission> をアプリケーションに与えて、目的のサーバーに送信要求を行うようにする場合は、サーバーでの中間層のシナリオがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="19a77-117">Middle-tier scenarios on the server are supported if the hosting environment has granted the application the appropriate <xref:System.Net.WebPermission> to make outbound requests to the desired server.</span></span>

<span data-ttu-id="19a77-118">サポートされている SOAP バインディングのいずれかを使用する SOAP メッセージングに加えて、WCF では、 <xref:System.ServiceModel.WebHttpBinding> 部分的に信頼されたアプリケーションで Web スタイルのサービスを構築するためのをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="19a77-118">In addition to SOAP messaging using one of the supported SOAP bindings, WCF supports the <xref:System.ServiceModel.WebHttpBinding> for building Web-style services in partially trusted applications.</span></span> <span data-ttu-id="19a77-119">Wcf [WEB HTTP プログラミングモデル](wcf-web-http-programming-model.md)、wcf [配信](wcf-syndication.md)、および [AJAX の統合と JSON のサポート](ajax-integration-and-json-support.md) 機能は、すべて部分信頼でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="19a77-119">The [WCF Web HTTP Programming Model](wcf-web-http-programming-model.md), [WCF Syndication](wcf-syndication.md), and [AJAX Integration and JSON Support](ajax-integration-and-json-support.md) features of WCF are all supported in partial trust.</span></span>

<span data-ttu-id="19a77-120">ワークフロー サービスは完全信頼のアクセス許可を必要とし、部分的に信頼されたアプリケーションでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="19a77-120">Workflow Services require Full Trust permissions and cannot be used in partially trusted applications.</span></span>

<span data-ttu-id="19a77-121">詳細については、「 [方法: ASP.NET 2.0 で中程度の信頼を使用する](/previous-versions/msp-n-p/ff648344(v=pandp.10))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="19a77-121">For more information, see [How to: Use Medium Trust in ASP.NET 2.0](/previous-versions/msp-n-p/ff648344(v=pandp.10)).</span></span>

## <a name="partial-trust-on-the-client"></a><span data-ttu-id="19a77-122">クライアントでの部分信頼</span><span class="sxs-lookup"><span data-stu-id="19a77-122">Partial trust on the client</span></span>

<span data-ttu-id="19a77-123">信頼されていないインターネット サイトからコードをダウンロードして実行する場合、ある程度のセキュリティ対策が必要です。</span><span class="sxs-lookup"><span data-stu-id="19a77-123">Certain security precautions must be taken when downloading and running code from untrusted Internet sites.</span></span> <span data-ttu-id="19a77-124">[ClickOnce 配置](/visualstudio/deployment/clickonce-security-and-deployment)と WPF の XAML ブラウザーアプリケーション (XBAP) テクノロジはどちらも、部分信頼を使用して、信頼されていないコードに制限付きのアクセス許可 (インターネットゾーン) を付与します。</span><span class="sxs-lookup"><span data-stu-id="19a77-124">Both [ClickOnce Deployment](/visualstudio/deployment/clickonce-security-and-deployment) and WPF's XAML Browser Application (XBAP) technology make use of partial trust to grant limited permissions (Internet Zone) to untrusted code.</span></span>

<span data-ttu-id="19a77-125">WCF を使用すると、 [ClickOnce 配置](/visualstudio/deployment/clickonce-security-and-deployment) または XBAP によって配置された部分信頼アプリケーション内からリモートサーバーと通信できます。</span><span class="sxs-lookup"><span data-stu-id="19a77-125">WCF can be used to communicate with remote servers from within partially trusted applications deployed by either [ClickOnce Deployment](/visualstudio/deployment/clickonce-security-and-deployment) or XBAP.</span></span> <span data-ttu-id="19a77-126">インターネットゾーンのアクセス許可セットには、元のホスト用のが含まれています <xref:System.Net.WebPermission> 。これにより、これらのアプリケーションは、「 [部分信頼機能の互換性](partial-trust-feature-compatibility.md)」で説明されているサポート対象の WCF バインディングを使用して、配信元サーバーと通信できます。</span><span class="sxs-lookup"><span data-stu-id="19a77-126">The Internet Zone permission set includes <xref:System.Net.WebPermission> for the originating host, which allows these applications to communicate with their origin server using any of the supported WCF bindings described in [Partial Trust Feature Compatibility](partial-trust-feature-compatibility.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="19a77-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="19a77-127">See also</span></span>

- [<span data-ttu-id="19a77-128">コード アクセス セキュリティ</span><span class="sxs-lookup"><span data-stu-id="19a77-128">Code Access Security</span></span>](../../misc/code-access-security.md)
- [<span data-ttu-id="19a77-129">Windows Presentation Foundation ブラウザーによってホストされるアプリケーションの概要</span><span class="sxs-lookup"><span data-stu-id="19a77-129">Windows Presentation Foundation Browser-Hosted Applications Overview</span></span>](/dotnet/desktop/wpf/app-development/wpf-xaml-browser-applications-overview)
- [<span data-ttu-id="19a77-130">部分信頼</span><span class="sxs-lookup"><span data-stu-id="19a77-130">Partial Trust</span></span>](partial-trust.md)
- <span data-ttu-id="19a77-131">[ASP.NET の信頼レベルとポリシー ファイル](/previous-versions/wyts434y(v=vs.140))</span><span class="sxs-lookup"><span data-stu-id="19a77-131">[ASP.NET Trust Levels and Policy Files](/previous-versions/wyts434y(v=vs.140))</span></span>
