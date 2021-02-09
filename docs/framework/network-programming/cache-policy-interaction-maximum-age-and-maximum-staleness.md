---
description: '詳細情報: キャッシュ ポリシーの相互作用 — 最大有効期間と最大期限延長'
title: キャッシュ ポリシーの相互作用 — 最大有効期間と最大期限延長
ms.date: 03/30/2017
helpviewer_keywords:
- maximum staleness
- freshness of cached resources
- time, cached resources
- maximum age policy
- staleness of cached resources
- age of cached resources
ms.assetid: 7f775925-89a1-4956-ba90-c869c1749a94
ms.openlocfilehash: 909a7203d4c9813c90dc0dea9bae7f8a1f7336cf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791661"
---
# <a name="cache-policy-interactionmaximum-age-and-maximum-staleness"></a><span data-ttu-id="60948-103">キャッシュ ポリシーの相互作用 — 最大有効期間と最大期限延長</span><span class="sxs-lookup"><span data-stu-id="60948-103">Cache Policy Interaction—Maximum Age and Maximum Staleness</span></span>

<span data-ttu-id="60948-104">最新のコンテンツをクライアント アプリケーションに確実に返すために、クライアントのキャッシュ ポリシーとサーバーの再検証要件の相互作用によって、常に最も保守的なキャッシュ ポリシーが適用されます。</span><span class="sxs-lookup"><span data-stu-id="60948-104">To help ensure that the freshest content is returned to the client application, the interaction of client cache policy and server revalidation requirements always results in the most conservative cache policy.</span></span> <span data-ttu-id="60948-105">このトピックの例はいずれも、1 月 1 日にキャッシュされ、1 月 4 日に期限切れになるリソースのキャッシュ ポリシーを示しています。</span><span class="sxs-lookup"><span data-stu-id="60948-105">All the examples in this topic illustrate the cache policy for a resource that is cached on January 1 and expires on January 4.</span></span>  
  
 <span data-ttu-id="60948-106">以下の例では、最大期限延長値 (`maxStale`) と最大有効期間 (`maxAge`) を組み合わせて使用しています。</span><span class="sxs-lookup"><span data-stu-id="60948-106">In the following examples, the maximum staleness value (`maxStale`) is used in conjunction with a maximum age (`maxAge`):</span></span>  
  
- <span data-ttu-id="60948-107">キャッシュ ポリシーで `maxAge` = 5 日間が設定され、`maxStale` 値が指定されていない場合は、`maxAge` 値に従い、コンテンツは 1 月 6 日まで使用できます。</span><span class="sxs-lookup"><span data-stu-id="60948-107">If the cache policy sets `maxAge` = 5 days and does not specify a `maxStale` value, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="60948-108">ただし、サーバーの再検証要件に従い、コンテンツは 1 月 4 日に期限切れになります。</span><span class="sxs-lookup"><span data-stu-id="60948-108">However, according to the server's revalidation requirements, the content expires on January 4.</span></span> <span data-ttu-id="60948-109">コンテンツの有効期限の方が保守的 (早い) ので、`maxAge` ポリシーよりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="60948-109">Because the content expiration date is more conservative (sooner), it takes precedence over the `maxAge` policy.</span></span> <span data-ttu-id="60948-110">そのため、コンテンツは 1 月 4 日に期限切れになり、最大有効期間に達していないとしても、必ず再検証されます。</span><span class="sxs-lookup"><span data-stu-id="60948-110">Therefore, the content expires on January 4 and must be revalidated even though its maximum age has not been reached.</span></span>  
  
- <span data-ttu-id="60948-111">キャッシュ ポリシーで `maxAge` = 5 日間と `maxStale` = 3 日間が設定されている場合、`maxAge` 値に従い、コンテンツは 1 月 6 日まで使用できます。</span><span class="sxs-lookup"><span data-stu-id="60948-111">If the cache policy sets `maxAge` = 5 days and `maxStale` = 3 days, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="60948-112">`maxStale` 値に従い、コンテンツは 1 月 7 日まで使用できます。</span><span class="sxs-lookup"><span data-stu-id="60948-112">According to the `maxStale` value, the content is usable until January 7.</span></span> <span data-ttu-id="60948-113">そのため、コンテンツは 1 月 6 日に再検証されます。</span><span class="sxs-lookup"><span data-stu-id="60948-113">Therefore, the content gets revalidated on January 6.</span></span>  
  
- <span data-ttu-id="60948-114">キャッシュ ポリシーで `maxAge` = 5 日間と `maxStale` = 1 日間が設定されている場合、`maxAge` 値に従い、コンテンツは 1 月 6 日まで使用できます。</span><span class="sxs-lookup"><span data-stu-id="60948-114">If the cache policy sets `maxAge` = 5 days and `maxStale` = 1 day, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="60948-115">`maxStale` 値に従い、コンテンツは 1 月 5 日まで使用できます。</span><span class="sxs-lookup"><span data-stu-id="60948-115">According to the `maxStale` value, the content is usable until January 5.</span></span> <span data-ttu-id="60948-116">そのため、コンテンツは 1 月 5 日に再検証されます。</span><span class="sxs-lookup"><span data-stu-id="60948-116">Therefore, the content gets revalidated on January 5.</span></span>  
  
 <span data-ttu-id="60948-117">最大有効期間がコンテンツの有効期限よりも短い場合、より保守的なキャッシュ動作が常に優先され、最大期限延長値の影響はありません。</span><span class="sxs-lookup"><span data-stu-id="60948-117">When the maximum age is less than the content expiration date, the more conservative caching behavior always prevails and the maximum staleness value has no effect.</span></span> <span data-ttu-id="60948-118">以下の例は、コンテンツの期限切れ前に最大有効期間 (`maxAge`) に達したときの最大期限延長 (`maxStale`) 値の影響を示しています。</span><span class="sxs-lookup"><span data-stu-id="60948-118">The following examples illustrate the effect of setting a maximum staleness (`maxStale`) value when the maximum age (`maxAge`) is reached before the content expires:</span></span>  
  
- <span data-ttu-id="60948-119">キャッシュ ポリシーで `maxAge` = 1 日間に設定され、`maxStale` 値が指定されていない場合、期限切れ前でも、コンテンツは 1 月 2 日に再検証されます。</span><span class="sxs-lookup"><span data-stu-id="60948-119">If the cache policy sets `maxAge` = 1 day and does not specify a value for `maxStale` value, the content is revalidated on January 2 even though it has not expired.</span></span>  
  
- <span data-ttu-id="60948-120">キャッシュ ポリシーで `maxAge` = 1 日、`maxStale` = 3 日間が設定されている場合、より保守的なポリシー設定を適用するために、コンテンツは 1 月 2 日に再検証されます。</span><span class="sxs-lookup"><span data-stu-id="60948-120">If the cache policy sets `maxAge` = 1 day and `maxStale` = 3 days, the content is revalidated on January 2 to enforce the more conservative policy setting.</span></span>  
  
- <span data-ttu-id="60948-121">キャッシュ ポリシーで `maxAge` = 1 日、`maxStale` = 1 日が設定されている場合、コンテンツは 1 月 2 日に再検証されます。</span><span class="sxs-lookup"><span data-stu-id="60948-121">If the cache policy sets `maxAge` = 1 day and `maxStale` = 1 day, the content is revalidated on January 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60948-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="60948-122">See also</span></span>

- [<span data-ttu-id="60948-123">ネットワーク アプリケーションのキャッシュ管理</span><span class="sxs-lookup"><span data-stu-id="60948-123">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="60948-124">キャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="60948-124">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="60948-125">場所ベースのキャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="60948-125">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="60948-126">時間ベースのキャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="60948-126">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="60948-127">ネットワーク アプリケーションでのキャッシュの構成</span><span class="sxs-lookup"><span data-stu-id="60948-127">Configuring Caching in Network Applications</span></span>](configuring-caching-in-network-applications.md)
- [<span data-ttu-id="60948-128">キャッシュ ポリシーの相互作用 — 最大有効期間と最小鮮度</span><span class="sxs-lookup"><span data-stu-id="60948-128">Cache Policy Interaction—Maximum Age and Minimum Freshness</span></span>](cache-policy-interaction-maximum-age-and-minimum-freshness.md)
