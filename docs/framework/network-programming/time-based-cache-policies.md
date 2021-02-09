---
description: '詳細情報: 時間ベースのキャッシュ ポリシー'
title: 時間ベースのキャッシュ ポリシー
ms.date: 03/30/2017
helpviewer_keywords:
- time-based cache policies
- cache synchronization date policy
- cache [.NET Framework], time-based policies
- freshness of cached resources
- time, cached resources
- maximum age policy
- synchronization, cache
- staleness of cached resources
- default time-based cache policy
- maximum staleness policy
- content cache policies
- expired content
- minimum freshness policy
- age of cached resources
ms.assetid: 74f0bcaf-5c95-40c1-9967-f3bbf1d2360a
ms.openlocfilehash: 42a76be0da664899295a583d72477de0698cc39e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712299"
---
# <a name="time-based-cache-policies"></a><span data-ttu-id="07c03-103">時間ベースのキャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="07c03-103">Time-Based Cache Policies</span></span>

<span data-ttu-id="07c03-104">時間ベースのキャッシュ ポリシーは、リソースの取得時間、リソースと共に返されたヘッダー、現在時刻を利用し、キャッシュされているエントリの更新の確認間隔を定義します。</span><span class="sxs-lookup"><span data-stu-id="07c03-104">A time-based cache policy defines the freshness of cached entries using the time the resource was retrieved, the headers returned with the resource, and the current time.</span></span> <span data-ttu-id="07c03-105">時間ベースのキャッシュ ポリシーを設定するとき、<xref:System.Net.Cache.HttpRequestCacheLevel.Default> 時間ベース キャッシュ ポリシーを利用するか、カスタマイズした時間ベース ポリシーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="07c03-105">When setting a time-based cache policy, you can either use the <xref:System.Net.Cache.HttpRequestCacheLevel.Default> time-based policy or create a customized time-based policy.</span></span> <span data-ttu-id="07c03-106">ハイパーテキスト転送プロトコル (HTTP) を利用して取得されるリソースに既定の時間ベース ポリシーを利用するとき、厳密なキャッシュ動作は、キャッシュされている応答に含まれているヘッダーと、RFC 2616 のセクション 13 とセクション 14 に指定されている動作で決定されます。RFC 2616 は [インターネット技術標準化委員会 (IETF)](https://www.ietf.org/) Web サイトで確認できます。</span><span class="sxs-lookup"><span data-stu-id="07c03-106">When using the default time-based policy for resources obtained using Hypertext Transfer Protocol (HTTP), the exact cache behavior is determined by the headers included in the cached response and by the behaviors specified in sections 13 and 14 of RFC 2616, available at [Internet Engineering Task Force (IETF)](https://www.ietf.org/) website.</span></span> <span data-ttu-id="07c03-107">HTTP リソースの既定の時間ベース ポリシーを設定する方法を示すコード例については、「[How to: Set the Default Time-Based Cache Policy for an Application](how-to-set-the-default-time-based-cache-policy-for-an-application.md)」(方法: アプリケーションの既定の時間ベースのキャッシュ ポリシーを設定する) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="07c03-107">For a code example that demonstrates setting the default time-based policy for HTTP resources, see [How to: Set the Default Time-Based Cache Policy for an Application](how-to-set-the-default-time-based-cache-policy-for-an-application.md).</span></span> <span data-ttu-id="07c03-108">キャッシュ ポリシーを作成し、利用する方法を示すコード例については、「[ネットワーク アプリケーションでのキャッシュの構成](configuring-caching-in-network-applications.md)」(ネットワーク アプリケーションでのキャッシュの構成) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="07c03-108">For code examples that demonstrate creating and using cache policies, see [Configuring Caching in Network Applications](configuring-caching-in-network-applications.md).</span></span>  
  
## <a name="criteria-to-determine-freshness-of-cached-entries"></a><span data-ttu-id="07c03-109">キャッシュされたエントリの更新の確認間隔を決定する基準</span><span class="sxs-lookup"><span data-stu-id="07c03-109">Criteria to Determine Freshness of Cached Entries</span></span>  

 <span data-ttu-id="07c03-110">時間ベースのキャッシュ ポリシーをカスタマイズするとき、次の条件を 1 つまたは複数利用し、キャッシュされているエントリの更新の確認間隔を決定するように指定できます。</span><span class="sxs-lookup"><span data-stu-id="07c03-110">To customize a time-based cache policy, you can specify that one or more of the following criteria be used to determine the freshness of cached entries:</span></span>  
  
- <span data-ttu-id="07c03-111">最大有効期間</span><span class="sxs-lookup"><span data-stu-id="07c03-111">Maximum age</span></span>  
  
- <span data-ttu-id="07c03-112">最大期限延長</span><span class="sxs-lookup"><span data-stu-id="07c03-112">Maximum staleness</span></span>  
  
- <span data-ttu-id="07c03-113">最小鮮度</span><span class="sxs-lookup"><span data-stu-id="07c03-113">Minimum freshness</span></span>  
  
- <span data-ttu-id="07c03-114">キャッシュ同期日付</span><span class="sxs-lookup"><span data-stu-id="07c03-114">Cache synchronization date</span></span>  
  
> [!NOTE]
> <span data-ttu-id="07c03-115">既定の時間ベース キャッシュ ポリシーを使用することと、アプリケーションの既定のキャッシュ ポリシーを設定することを混同しないでください。</span><span class="sxs-lookup"><span data-stu-id="07c03-115">Using the default time-based cache policy should not be confused with setting a default cache policy for your application.</span></span> <span data-ttu-id="07c03-116">既定の時間ベース ポリシーは、要求またはアプリケーション レベルで利用できる特定のポリシーです。</span><span class="sxs-lookup"><span data-stu-id="07c03-116">The default time-based policy is a specific policy that can be used at the request or application level.</span></span> <span data-ttu-id="07c03-117">アプリケーションの既定のキャッシュ ポリシーは、要求にポリシーが設定されていないときに有効なポリシーです (場所ベースまたは時間ベース)。</span><span class="sxs-lookup"><span data-stu-id="07c03-117">The default cache policy for your application is a policy (location-based or time-based) that takes effect when no policy is set on a request.</span></span> <span data-ttu-id="07c03-118">アプリケーションの既定のキャッシュ ポリシーを設定する方法については、「<xref:System.Net.WebRequest.DefaultCachePolicy%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="07c03-118">For details on setting a default cache policy for your application, see <xref:System.Net.WebRequest.DefaultCachePolicy%2A>.</span></span>  
  
### <a name="maximum-age"></a><span data-ttu-id="07c03-119">最大有効期間</span><span class="sxs-lookup"><span data-stu-id="07c03-119">Maximum Age</span></span>  

 <span data-ttu-id="07c03-120">最大有効期間というポリシー基準は、リソースのキャッシュ済みコピーを利用できる時間を指定します。</span><span class="sxs-lookup"><span data-stu-id="07c03-120">The maximum age policy criterion specifies the amount of time a cached copy of a resource can be used.</span></span> <span data-ttu-id="07c03-121">そのリソースのキャッシュ済みコピーが指定された時間より古い場合、サーバーのコンテンツに対して確認し、リソースを再検証する必要があります。</span><span class="sxs-lookup"><span data-stu-id="07c03-121">If the cached copy of the resource is older than the amount of time specified, the resource must be revalidated by checking it against the content on the server.</span></span> <span data-ttu-id="07c03-122">最大有効期間で、失効後にリソースの利用が許可される場合、最大期限延長も指定されない限り、この基準は守られません。</span><span class="sxs-lookup"><span data-stu-id="07c03-122">If the maximum age would allow the resource to be used after it expires, this criteria is not honored unless a maximum staleness value is also specified.</span></span>  
  
### <a name="maximum-staleness"></a><span data-ttu-id="07c03-123">最大期限延長</span><span class="sxs-lookup"><span data-stu-id="07c03-123">Maximum Staleness</span></span>  

 <span data-ttu-id="07c03-124">最大期限延長というポリシー基準は、リソースのキャッシュ済みコピーを利用できる時間をコンテンツの失効後に指定します。</span><span class="sxs-lookup"><span data-stu-id="07c03-124">The maximum staleness policy criterion specifies the length of time after content expiration that the cached copy of the resource can be used.</span></span> <span data-ttu-id="07c03-125">これは、失効後、リソースの利用を許可する唯一のキャッシュ ポリシー基準です。</span><span class="sxs-lookup"><span data-stu-id="07c03-125">This is the only cache policy criterion that permits resources to be used after they have expired.</span></span>  
  
### <a name="minimum-freshness"></a><span data-ttu-id="07c03-126">最小鮮度</span><span class="sxs-lookup"><span data-stu-id="07c03-126">Minimum Freshness</span></span>  

 <span data-ttu-id="07c03-127">最小鮮度というポリシー基準は、リソースのキャッシュ済みコピーを利用できる時間をコンテンツの失効前に指定します。</span><span class="sxs-lookup"><span data-stu-id="07c03-127">The minimum freshness policy criterion specifies the length of time before content expiration that the cached copy of the resource can be used.</span></span> <span data-ttu-id="07c03-128">このポリシーにより、有効期限前にキャッシュ エントリが失効します。最小鮮度と最大期限延長は互いに排他的になります。</span><span class="sxs-lookup"><span data-stu-id="07c03-128">This policy has the effect of causing a cache entry to expire before its expiration date; therefore, the minimum freshness and maximum staleness settings are mutually exclusive.</span></span>  
  
## <a name="cache-synchronization-date"></a><span data-ttu-id="07c03-129">キャッシュ同期日付</span><span class="sxs-lookup"><span data-stu-id="07c03-129">Cache Synchronization Date</span></span>  

 <span data-ttu-id="07c03-130">キャッシュ同期日付というポリシー基準は、サーバーのコンテンツに対して確認することで、リソースのキャッシュ済みコピーを再検証するタイミングを決定します。</span><span class="sxs-lookup"><span data-stu-id="07c03-130">The cache synchronization date policy criterion determines when a cached copy of a resource must be revalidated by checking it against the content on the server.</span></span> <span data-ttu-id="07c03-131">アイテムのキャッシュ後にコンテンツが変更された場合、そのコンテンツはサーバーから取得され、キャッシュに保存され、アプリケーションに返されます。</span><span class="sxs-lookup"><span data-stu-id="07c03-131">If the content has changed since the item was cached, it is retrieved from the server, stored in the cache, and returned to the application.</span></span> <span data-ttu-id="07c03-132">コンテンツが変わっていない場合、そのタイムスタンプが更新され、アプリケーションはキャッシュ済みコンテンツを取得します。</span><span class="sxs-lookup"><span data-stu-id="07c03-132">If the content has not changed, its timestamp is updated and the application gets the cached content.</span></span>  
  
 <span data-ttu-id="07c03-133">キャッシュ同期日付を利用し、キャッシュ済みコンテンツを再検証する絶対的日付を指定できます。</span><span class="sxs-lookup"><span data-stu-id="07c03-133">The cache synchronization date allows you to specify an absolute date when cached contents must be revalidated.</span></span> <span data-ttu-id="07c03-134">新しいキャッシュ エントリが最後に再検証されたのがキャッシュ同期日付より前であれば、サーバーにより再検証が発生します。</span><span class="sxs-lookup"><span data-stu-id="07c03-134">If a fresh cache entry was last revalidated prior to the cache synchronization date, revalidation with the server still occurs.</span></span> <span data-ttu-id="07c03-135">キャッシュ同期日付後にキャッシュ エントリが再検証されたとき、キャッシュ済みエントリを無効にする、付加的な更新確認要件またはサーバー再検証要件がなければ、キャッシュからのエントリが利用されます。</span><span class="sxs-lookup"><span data-stu-id="07c03-135">If the cache entry was revalidated after the cache synchronization date and there are no additional freshness or server revalidation requirements that invalidate the cached entry, the entry from the cache is used.</span></span> <span data-ttu-id="07c03-136">キャッシュ同期日付が未来の日付に設定されている場合、キャッシュ同期日付が過ぎるまで、要求のたびにエントリが再検証されます。</span><span class="sxs-lookup"><span data-stu-id="07c03-136">If the cache synchronization date is set to a future date, the entry is revalidated every time it is requested, until the cache synchronization date passes.</span></span>  
  
 <span data-ttu-id="07c03-137">後続のトピックでは、時間ベース キャッシュ ポリシー基準の組み合わせについて説明します。</span><span class="sxs-lookup"><span data-stu-id="07c03-137">The following topics provide information about the effects of combining time-based cache policy criteria:</span></span>  
  
- [<span data-ttu-id="07c03-138">キャッシュ ポリシーの相互作用 — 最大有効期間と最大期限延長</span><span class="sxs-lookup"><span data-stu-id="07c03-138">Cache Policy Interaction—Maximum Age and Maximum Staleness</span></span>](cache-policy-interaction-maximum-age-and-maximum-staleness.md)  
  
- [<span data-ttu-id="07c03-139">キャッシュ ポリシーの相互作用 — 最大有効期間と最小鮮度</span><span class="sxs-lookup"><span data-stu-id="07c03-139">Cache Policy Interaction—Maximum Age and Minimum Freshness</span></span>](cache-policy-interaction-maximum-age-and-minimum-freshness.md)  
  
## <a name="see-also"></a><span data-ttu-id="07c03-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="07c03-140">See also</span></span>

- [<span data-ttu-id="07c03-141">ネットワーク アプリケーションのキャッシュ管理</span><span class="sxs-lookup"><span data-stu-id="07c03-141">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="07c03-142">キャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="07c03-142">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="07c03-143">場所ベースのキャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="07c03-143">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="07c03-144">ネットワーク アプリケーションでのキャッシュの構成</span><span class="sxs-lookup"><span data-stu-id="07c03-144">Configuring Caching in Network Applications</span></span>](configuring-caching-in-network-applications.md)
- [<span data-ttu-id="07c03-145">\<requestCaching> 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="07c03-145">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
