---
description: '詳細情報: 場所ベースのキャッシュ ポリシー'
title: 場所ベースのキャッシュ ポリシー
ms.date: 03/30/2017
helpviewer_keywords:
- Cache If Available policy
- reload policy
- location-based cache policies
- Cache Only policy
- local cache
- intermediate cache
- No Cache No Store policy
- cache [.NET Framework], location-based policies
- Revalidate policy
- freshness of cached resources
- Cache Or Next Cache Only policy
- Refresh policy
ms.assetid: e41d7f1a-0a6a-4dee-97d1-c6a8b6a07fc2
ms.openlocfilehash: ef770b45f173fee66c80d721766a0be6244bbeb9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662716"
---
# <a name="location-based-cache-policies"></a><span data-ttu-id="7308b-103">場所ベースのキャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="7308b-103">Location-Based Cache Policies</span></span>

<span data-ttu-id="7308b-104">場所ベースのキャッシュ ポリシーでは、要求されたリソースを取得できる場所に基づいて、有効なキャッシュされたエントリの鮮度を定義します。</span><span class="sxs-lookup"><span data-stu-id="7308b-104">A location-based cache policy defines the freshness of valid cached entries based on where the requested resource can be taken from.</span></span> <span data-ttu-id="7308b-105">キャッシュされたリソースを使用しても、サーバーに指定されている再検証要件に違反しない場合、キャッシュされたリソースは有効です。</span><span class="sxs-lookup"><span data-stu-id="7308b-105">A cached resource is valid if using it does not does not violate server-specified revalidation requirements.</span></span> <span data-ttu-id="7308b-106">場所ベースのキャッシュ ポリシーをプログラムで作成するには、<xref:System.Net.Cache.RequestCachePolicy> または <xref:System.Net.Cache.HttpRequestCachePolicy> クラス コンストラクターを使用します。</span><span class="sxs-lookup"><span data-stu-id="7308b-106">A location-based cache policy is created programmatically by using a <xref:System.Net.Cache.RequestCachePolicy> or <xref:System.Net.Cache.HttpRequestCachePolicy> class constructor.</span></span> <span data-ttu-id="7308b-107">場所ベースのポリシーの種類は、<xref:System.Net.Cache.RequestCacheLevel> または <xref:System.Net.Cache.HttpRequestCacheLevel> 列挙値を使用してコンストラクターに渡されます。</span><span class="sxs-lookup"><span data-stu-id="7308b-107">The type of location-based policy is passed to the constructor using a <xref:System.Net.Cache.RequestCacheLevel> or <xref:System.Net.Cache.HttpRequestCacheLevel> enumeration value.</span></span> <span data-ttu-id="7308b-108">場所ベースのキャッシュ ポリシーを作成するコード例については、「[How to: Set a Location-Based Cache Policy for an Application](how-to-set-a-location-based-cache-policy-for-an-application.md)」(方法: アプリケーションの場所ベースのキャッシュ ポリシーを設定する) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7308b-108">For code examples that create location-based cache policies, see [How to: Set a Location-Based Cache Policy for an Application](how-to-set-a-location-based-cache-policy-for-an-application.md).</span></span> <span data-ttu-id="7308b-109">以下のセクションでは、ハイパーテキスト転送プロトコル (http と https) リソースに使用できる各種の場所ベースのキャッシュ ポリシーを定義します。</span><span class="sxs-lookup"><span data-stu-id="7308b-109">The following sections explain each type of location-based cache policy for Hypertext Transfer Protocol (http and https) resources.</span></span>  
  
## <a name="cache-if-available-policy"></a><span data-ttu-id="7308b-110">"利用可能ならキャッシュを使用" ポリシー</span><span class="sxs-lookup"><span data-stu-id="7308b-110">Cache If Available Policy</span></span>  

 <span data-ttu-id="7308b-111">有効な要求されたリソースがローカル キャッシュ内にある場合、キャッシュされたリソースが使用されます。それ以外の場合、そのリソースの要求はサーバーに送信されます。</span><span class="sxs-lookup"><span data-stu-id="7308b-111">If a valid requested resource is in the local cache, the cached resource is used; otherwise, the request for the resource is sent to the server.</span></span> <span data-ttu-id="7308b-112">要求されたリソースがクライアントとサーバーの間の何らかのキャッシュ内にある場合、中間のキャッシュが要求を満たすことができます。</span><span class="sxs-lookup"><span data-stu-id="7308b-112">If the requested resource is available in any cache between the client and the server, the request can be satisfied by an intermediate cache.</span></span>  
  
## <a name="cache-only-policy"></a><span data-ttu-id="7308b-113">"キャッシュのみを使用" ポリシー</span><span class="sxs-lookup"><span data-stu-id="7308b-113">Cache Only Policy</span></span>  

 <span data-ttu-id="7308b-114">有効な要求されたリソースがローカル キャッシュ内にある場合、キャッシュされたリソースが使用されます。</span><span class="sxs-lookup"><span data-stu-id="7308b-114">If a valid requested resource is in the local cache, the cached resource is used.</span></span> <span data-ttu-id="7308b-115">このキャッシュ ポリシー レベルが指定された場合、項目がローカル キャッシュ内にない場合は <xref:System.Net.WebException> 例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="7308b-115">When this cache policy level is specified, a <xref:System.Net.WebException> exception is thrown if the item is not in the local cache.</span></span>  
  
## <a name="cache-or-next-cache-only-policy"></a><span data-ttu-id="7308b-116">"キャッシュまたは次のキャッシュのみを使用" ポリシー</span><span class="sxs-lookup"><span data-stu-id="7308b-116">Cache Or Next Cache Only Policy</span></span>  

 <span data-ttu-id="7308b-117">有効な要求されたリソースがローカル キャッシュ内にあるか、ローカル エリア ネットワーク上の中間キャッシュ内にある場合、キャッシュされたリソースが使用されます。</span><span class="sxs-lookup"><span data-stu-id="7308b-117">If a valid requested resource is in the local cache or an intermediate cache on the local area network, the cached resource is used.</span></span> <span data-ttu-id="7308b-118">このような操作を行わない場合、<xref:System.Net.WebException> 例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="7308b-118">Otherwise, a <xref:System.Net.WebException> exception is thrown.</span></span> <span data-ttu-id="7308b-119">HTTP キャッシュ プロトコルの場合、only-if-cached キャッシュ コントロール ディレクティブを使用してこの処理が実行されます。</span><span class="sxs-lookup"><span data-stu-id="7308b-119">In the HTTP caching protocol, this is achieved using the only-if-cached cache control directive.</span></span>  
  
## <a name="no-cache-no-store-policy"></a><span data-ttu-id="7308b-120">"キャッシュを使用せず格納しない" ポリシー</span><span class="sxs-lookup"><span data-stu-id="7308b-120">No Cache No Store Policy</span></span>  

 <span data-ttu-id="7308b-121">要求されたリソースはキャッシュ内からは使用されず、キャッシュには格納されません。</span><span class="sxs-lookup"><span data-stu-id="7308b-121">A requested resource is never used from any cache and is never placed in any cache.</span></span> <span data-ttu-id="7308b-122">要求されたリソースがローカル キャッシュ内にある場合は削除されます。</span><span class="sxs-lookup"><span data-stu-id="7308b-122">If a requested resource is present in the local cache, it is removed.</span></span> <span data-ttu-id="7308b-123">このポリシー レベルは、リソースの削除も必要な中間キャッシュに指定します。</span><span class="sxs-lookup"><span data-stu-id="7308b-123">This policy level indicates to intermediate caches that they should also remove the resource.</span></span> <span data-ttu-id="7308b-124">HTTP キャッシュ プロトコルの場合、no-store キャッシュ コントロール ディレクティブを使用してこの処理が実行されます。</span><span class="sxs-lookup"><span data-stu-id="7308b-124">In the HTTP caching protocol, this is achieved using the no-store cache control directive.</span></span>  
  
## <a name="refresh-policy"></a><span data-ttu-id="7308b-125">更新ポリシー</span><span class="sxs-lookup"><span data-stu-id="7308b-125">Refresh Policy</span></span>  

 <span data-ttu-id="7308b-126">要求されたリソースがサーバーから取得された場合、またはローカル キャッシュ以外のキャッシュで見つかった場合、その要求されたリソースを使用できます。</span><span class="sxs-lookup"><span data-stu-id="7308b-126">A requested resource can be used if it is obtained from the server or found in a cache other than the local cache.</span></span> <span data-ttu-id="7308b-127">中間キャッシュが要求を満たす前に、そのキャッシュは、サーバーに対してキャッシュされたエントリの再検証を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="7308b-127">Before the request can be satisfied by an intermediate cache, that cache must revalidate its cached entry with the server.</span></span> <span data-ttu-id="7308b-128">HTTP キャッシュ プロトコルの場合、max-age = 0 キャッシュ コントロール ディレクティブと、no-cache Pragma ヘッダーを使用してこの処理が実行されます。</span><span class="sxs-lookup"><span data-stu-id="7308b-128">In the HTTP caching protocol, this is achieved using the max-age = 0 cache control directive and the no-cache Pragma header.</span></span>  
  
## <a name="reload-policy"></a><span data-ttu-id="7308b-129">ポリシーの再読み込み</span><span class="sxs-lookup"><span data-stu-id="7308b-129">Reload Policy</span></span>  

 <span data-ttu-id="7308b-130">要求されたリソースは、サーバーから取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7308b-130">Requested resources must be obtained from the server.</span></span> <span data-ttu-id="7308b-131">リソースがローカル キャッシュに保存されている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7308b-131">The response might be saved in the local cache.</span></span> <span data-ttu-id="7308b-132">HTTP キャッシュ プロトコルの場合、no-cache キャッシュ コントロール ディレクティブと、no-cache Pragma ヘッダーを使用してこの処理が実行されます。</span><span class="sxs-lookup"><span data-stu-id="7308b-132">In the HTTP caching protocol, this is achieved using the no-cache cache control directive and the no-cache Pragma header.</span></span>  
  
## <a name="revalidate-policy"></a><span data-ttu-id="7308b-133">再検証ポリシー</span><span class="sxs-lookup"><span data-stu-id="7308b-133">Revalidate Policy</span></span>  

 <span data-ttu-id="7308b-134">キャッシュ内のリソースのコピーとサーバー上のコピーを比較します。</span><span class="sxs-lookup"><span data-stu-id="7308b-134">Compares the copy of the resource in the cache with the copy on the server.</span></span> <span data-ttu-id="7308b-135">サーバー上のコピーが新しい場合は、要求を満たすために使用され、キャッシュ内のコピーは置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="7308b-135">If the copy on the server is newer, it is used to satisfy the request and replaces the copy in the cache.</span></span> <span data-ttu-id="7308b-136">キャッシュ内のコピーがサーバー上のコピーと同じ場合、キャッシュされたコピーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="7308b-136">If the copy in the cache is the same as the server copy, the cached copy is used.</span></span> <span data-ttu-id="7308b-137">HTTP キャッシュ プロトコルの場合、条件付き要求を使用してこの処理が実行されます。</span><span class="sxs-lookup"><span data-stu-id="7308b-137">In the HTTP caching protocol, this is achieved using a conditional request.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7308b-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="7308b-138">See also</span></span>

- [<span data-ttu-id="7308b-139">ネットワーク アプリケーションのキャッシュ管理</span><span class="sxs-lookup"><span data-stu-id="7308b-139">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="7308b-140">キャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="7308b-140">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="7308b-141">時間ベースのキャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="7308b-141">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="7308b-142">ネットワーク アプリケーションでのキャッシュの構成</span><span class="sxs-lookup"><span data-stu-id="7308b-142">Configuring Caching in Network Applications</span></span>](configuring-caching-in-network-applications.md)
- [<span data-ttu-id="7308b-143">\<requestCaching> 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="7308b-143">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
