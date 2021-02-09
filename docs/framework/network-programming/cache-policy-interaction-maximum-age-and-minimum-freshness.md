---
description: '詳細情報: キャッシュ ポリシーの相互作用 — 最大有効期間と最小鮮度'
title: キャッシュ ポリシーの相互作用 — 最大有効期間と最小鮮度
ms.date: 03/30/2017
helpviewer_keywords:
- time-based cache policies
- Revalidate policy
- cache [.NET Framework], time-based policies
- freshness of cached resources
- maximum age policy
- minimum freshness policy
- age of cached resources
ms.assetid: 6567d451-ecec-496c-95a3-a415b99ba52a
ms.openlocfilehash: 882df93d44c0d745fcf30a7d9be3152797df4844
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791648"
---
# <a name="cache-policy-interactionmaximum-age-and-minimum-freshness"></a><span data-ttu-id="4a60f-103">キャッシュ ポリシーの相互作用 — 最大有効期間と最小鮮度</span><span class="sxs-lookup"><span data-stu-id="4a60f-103">Cache Policy Interaction—Maximum Age and Minimum Freshness</span></span>

<span data-ttu-id="4a60f-104">最新のコンテンツをクライアント アプリケーションに確実に返すために、クライアントのキャッシュ ポリシーとサーバーの再検証要件の相互作用によって、常に最も保守的なキャッシュ ポリシーが適用されます。</span><span class="sxs-lookup"><span data-stu-id="4a60f-104">To help ensure that the freshest content is returned to the client application, the interaction of client cache policy and server revalidation requirements always results in the most conservative cache policy.</span></span> <span data-ttu-id="4a60f-105">このトピックの例はいずれも、1 月 1 日にキャッシュされ、1 月 4 日に期限切れになるリソースのキャッシュ ポリシーを示しています。</span><span class="sxs-lookup"><span data-stu-id="4a60f-105">All the examples in this topic illustrate the cache policy for a resource that is cached on January 1 and expires on January 4.</span></span>  
  
 <span data-ttu-id="4a60f-106">以下の例は、最大有効期間 (`maxAge`) と最小鮮度 (`minFresh`) 値の相互作用の結果となるキャッシュ ポリシーを示しています。</span><span class="sxs-lookup"><span data-stu-id="4a60f-106">The following examples illustrate the cache policy that results from the interaction of the maximum age (`maxAge`) and minimum freshness (`minFresh`) values.</span></span>  
  
- <span data-ttu-id="4a60f-107">キャッシュ ポリシーで `maxAge` = 2 日間と設定され、`minFresh` が指定されていない場合、コンテンツは 1 月 3 日に再検証されます。</span><span class="sxs-lookup"><span data-stu-id="4a60f-107">If the cache policy sets `maxAge` = 2 days and `minFresh` is not specified, the content is revalidated on January 3.</span></span>  
  
- <span data-ttu-id="4a60f-108">キャッシュ ポリシーで `maxAge` = 2 日間と `minFresh` = 1 日間が設定されている場合、`maxAge` 値に従い、コンテンツは 1 月 3 日まで最新です。</span><span class="sxs-lookup"><span data-stu-id="4a60f-108">If the cache policy sets `maxAge` = 2 days and `minFresh` = 1 day, according to `maxAge`, the content is fresh until January 3.</span></span> <span data-ttu-id="4a60f-109">`minFresh` 値に従い、コンテンツは 1 月 3 日まで最新です。</span><span class="sxs-lookup"><span data-stu-id="4a60f-109">According to `minFresh`, the content is fresh until January 3.</span></span> <span data-ttu-id="4a60f-110">そのため、コンテンツは 1 月 3 日に再検証する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4a60f-110">Therefore, the content must be revalidated on January 3.</span></span>  
  
- <span data-ttu-id="4a60f-111">キャッシュ ポリシーで `maxAge` = 2 日間と `minFresh` = 2 日間が設定されている場合、`maxAge` 値に従い、コンテンツは 1 月 3 日まで最新です。</span><span class="sxs-lookup"><span data-stu-id="4a60f-111">If the cache policy sets `maxAge` = 2 days and `minFresh` = 2 days, according to `maxAge`, the content is fresh until January 3.</span></span> <span data-ttu-id="4a60f-112">`minFresh` 値に従い、コンテンツは 1 月 2 日まで最新です。</span><span class="sxs-lookup"><span data-stu-id="4a60f-112">According to `minFresh` the content is fresh until January 2.</span></span> <span data-ttu-id="4a60f-113">そのため、コンテンツは 1 月 2 日に再検証する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4a60f-113">Therefore, the content must be revalidated on January 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a60f-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="4a60f-114">See also</span></span>

- [<span data-ttu-id="4a60f-115">ネットワーク アプリケーションのキャッシュ管理</span><span class="sxs-lookup"><span data-stu-id="4a60f-115">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="4a60f-116">キャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="4a60f-116">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="4a60f-117">場所ベースのキャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="4a60f-117">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="4a60f-118">時間ベースのキャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="4a60f-118">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="4a60f-119">ネットワーク アプリケーションでのキャッシュの構成</span><span class="sxs-lookup"><span data-stu-id="4a60f-119">Configuring Caching in Network Applications</span></span>](configuring-caching-in-network-applications.md)
- [<span data-ttu-id="4a60f-120">キャッシュ ポリシーの相互作用 — 最大有効期間と最大期限延長</span><span class="sxs-lookup"><span data-stu-id="4a60f-120">Cache Policy Interaction—Maximum Age and Maximum Staleness</span></span>](cache-policy-interaction-maximum-age-and-maximum-staleness.md)
