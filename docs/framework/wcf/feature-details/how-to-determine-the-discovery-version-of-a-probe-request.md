---
description: '詳細については、「方法: プローブ要求の探索バージョンを確認する」を参照してください。'
title: '方法: Probe 要求の探索バージョンを特定する'
ms.date: 03/30/2017
ms.assetid: b3c4e2e2-2957-4074-ae6a-776a5ca84278
ms.openlocfilehash: c41283cb84d75dd2dbf7e86da0dec075ab8b6635
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793793"
---
# <a name="how-todetermine-the-discovery-version-of-a-probe-request"></a><span data-ttu-id="d285e-103">方法: Probe 要求の探索バージョンを特定する</span><span class="sxs-lookup"><span data-stu-id="d285e-103">How to:Determine the Discovery Version of a Probe Request</span></span>

<span data-ttu-id="d285e-104">探索プロキシでは、異なる探索バージョンを使用する複数の探索エンドポイントを公開する場合があります。</span><span class="sxs-lookup"><span data-stu-id="d285e-104">A discovery proxy may expose multiple discovery endpoints using different discovery versions.</span></span> <span data-ttu-id="d285e-105">UDP マルチキャストプローブ要求がプロキシに到着すると、プロキシはマルチキャスト抑制メッセージで応答する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d285e-105">When a UDP multicast Probe request arrives at the proxy, the proxy should respond with a multicast suppression message.</span></span> <span data-ttu-id="d285e-106">このためには、要求の探索バージョンを把握している必要があります。</span><span class="sxs-lookup"><span data-stu-id="d285e-106">In order to do this, it would have to know the discovery version of the request.</span></span>

## <a name="to-determine-the-discovery-version-of-a-probe-request"></a><span data-ttu-id="d285e-107">Probe 要求の探索バージョンを特定するには</span><span class="sxs-lookup"><span data-stu-id="d285e-107">To Determine the Discovery Version of a Probe Request</span></span>

<span data-ttu-id="d285e-108">プローブ要求に応答するメソッド (たとえば) では、 <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType> <xref:System.ServiceModel.OperationContext.Current%2A?displayProperty=nameWithType> 次のコードに示すように、静的プロパティを使用してを検索し <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension> ます。</span><span class="sxs-lookup"><span data-stu-id="d285e-108">In the method that responds to a Probe request (for example <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType>) use the static <xref:System.ServiceModel.OperationContext.Current%2A?displayProperty=nameWithType> property to search for a <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension>, as shown in the following code.</span></span>

```csharp
DiscoveryOperationContextExtension doce = OperationContext.Current.Extensions.Find<DiscoveryOperationContextExtension>();
// Access the discovery version from the DiscoveryOperationContextExtension
doce.DiscoveryVersion;
```

## <a name="see-also"></a><span data-ttu-id="d285e-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="d285e-109">See also</span></span>

- <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion%2A>
- [<span data-ttu-id="d285e-110">探索プロキシの実装</span><span class="sxs-lookup"><span data-stu-id="d285e-110">Implementing a Discovery Proxy</span></span>](implementing-a-discovery-proxy.md)
