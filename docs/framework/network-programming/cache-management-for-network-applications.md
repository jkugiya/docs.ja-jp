---
description: '詳細情報: ネットワーク アプリケーションのキャッシュ管理'
title: ネットワーク アプリケーションのキャッシュ管理
ms.date: 03/30/2017
helpviewer_keywords:
- cache [.NET Framework], network applications
- network resources, caching
- Internet, caching
ms.assetid: fc258a40-f370-434f-ae09-4a8cb11ddaeb
ms.openlocfilehash: 6383403b41440f26b29fbb5a22c5b25ee6aab465
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791674"
---
# <a name="cache-management-for-network-applications"></a><span data-ttu-id="e9055-103">ネットワーク アプリケーションのキャッシュ管理</span><span class="sxs-lookup"><span data-stu-id="e9055-103">Cache Management for Network Applications</span></span>

<span data-ttu-id="e9055-104">このトピックと関連するサブトピックでは、<xref:System.Net.WebClient>、<xref:System.Net.WebRequest>、<xref:System.Net.HttpWebRequest>、および <xref:System.Net.FtpWebRequest> クラスを使用して取得したリソースのキャッシュ処理について説明します。</span><span class="sxs-lookup"><span data-stu-id="e9055-104">This topic and its related subtopics describe caching for resources obtained using the <xref:System.Net.WebClient>, <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, and <xref:System.Net.FtpWebRequest> classes.</span></span>  
  
 <span data-ttu-id="e9055-105">キャッシュは、アプリケーションから要求されたリソースの一時的な記憶域として機能します。</span><span class="sxs-lookup"><span data-stu-id="e9055-105">A cache provides temporary storage of resources that have been requested by an application.</span></span> <span data-ttu-id="e9055-106">アプリケーションから同じリソースを複数回要求される場合、キャッシュからリソースを返すことで、サーバーから再要求するオーバーヘッドを回避できます。</span><span class="sxs-lookup"><span data-stu-id="e9055-106">If an application requests the same resource more than once, the resource can be returned from the cache, avoiding the overhead of re-requesting it from the server.</span></span> <span data-ttu-id="e9055-107">キャッシュによって、要求されたリソースの取得にかかる時間が短縮されるので、アプリケーションのパフォーマンスを改善できます。</span><span class="sxs-lookup"><span data-stu-id="e9055-107">Caching can improve application performance by reducing the time required to get a requested resource.</span></span> <span data-ttu-id="e9055-108">また、サーバーへのトリップ回数が減るので、ネットワーク トラフィックを減らすこともできます。</span><span class="sxs-lookup"><span data-stu-id="e9055-108">Caching can also decrease network traffic by reducing the number of trips to the server.</span></span> <span data-ttu-id="e9055-109">キャッシュによってパフォーマンスは改善されますが、アプリケーションに古いリソースが返される危険性もあります。つまり、キャッシュを使用していなかった場合にサーバーから送信されたリソースと、キャッシュのリソースは同じではないということです。</span><span class="sxs-lookup"><span data-stu-id="e9055-109">While caching improves performance, it increases the risk that the resource returned to the application is stale, meaning that it is not identical to the resource that would have been sent by the server if caching were not in use.</span></span>  
  
 <span data-ttu-id="e9055-110">また、キャッシュによって、権限のないユーザーまたはプロセスが機密データを閲覧できる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e9055-110">Caching may allow unauthorized users or processes to read sensitive data.</span></span> <span data-ttu-id="e9055-111">キャッシュされている認証済みの応答が、追加の承認なしでキャッシュから取得される可能性があるからです。</span><span class="sxs-lookup"><span data-stu-id="e9055-111">An authenticated response that is cached may be retrieved from the cache without an additional authorization.</span></span> <span data-ttu-id="e9055-112">キャッシュを有効にする場合は、<xref:System.Net.WebRequest.CachePolicy%2A> を <xref:System.Net.Cache.RequestCacheLevel.BypassCache> または <xref:System.Net.Cache.RequestCacheLevel.NoCacheNoStore> に変更して、この要求のキャッシュを無効にしてください。</span><span class="sxs-lookup"><span data-stu-id="e9055-112">If caching is enabled, change to <xref:System.Net.WebRequest.CachePolicy%2A> to <xref:System.Net.Cache.RequestCacheLevel.BypassCache> or <xref:System.Net.Cache.RequestCacheLevel.NoCacheNoStore> to disable caching for this request.</span></span>  
  
 <span data-ttu-id="e9055-113">セキュリティの懸念事項があるため、中間層のシナリオにキャッシュを使用することは **推奨されません**。</span><span class="sxs-lookup"><span data-stu-id="e9055-113">Due to security concerns, caching is **not** recommended for middle tier scenarios.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e9055-114">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="e9055-114">In This Section</span></span>  

 [<span data-ttu-id="e9055-115">キャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="e9055-115">Cache Policy</span></span>](cache-policy.md)  
 <span data-ttu-id="e9055-116">キャッシュ ポリシーの概要と定義方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e9055-116">Explains what a cache policy is and how to define one.</span></span>  
  
 [<span data-ttu-id="e9055-117">場所ベースのキャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="e9055-117">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)  
 <span data-ttu-id="e9055-118">ハイパーテキスト転送プロトコル (http と https) リソースに使用できる各種の場所ベースのキャッシュ ポリシーを定義します。</span><span class="sxs-lookup"><span data-stu-id="e9055-118">Defines each type of location-based cache policy available for Hypertext Transfer Protocol (http and https) resources.</span></span>  
  
 [<span data-ttu-id="e9055-119">時間ベースのキャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="e9055-119">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)  
 <span data-ttu-id="e9055-120">時間ベースのキャッシュ ポリシーのカスタマイズに使用できる条件について説明します。</span><span class="sxs-lookup"><span data-stu-id="e9055-120">Describes the criteria that can be used to customize a time-based cache policy.</span></span>  
  
 [<span data-ttu-id="e9055-121">ネットワーク アプリケーションでのキャッシュの構成</span><span class="sxs-lookup"><span data-stu-id="e9055-121">Configuring Caching in Network Applications</span></span>](configuring-caching-in-network-applications.md)  
 <span data-ttu-id="e9055-122">キャッシュ ポリシーとキャッシュを使用する要求をプログラムで作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e9055-122">Describes how to programmatically create cache policies and requests that use caching.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e9055-123">リファレンス</span><span class="sxs-lookup"><span data-stu-id="e9055-123">Reference</span></span>  

 <xref:System.Net.Cache>  
 <span data-ttu-id="e9055-124">取得したリソースのキャッシュ ポリシーを <xref:System.Net.WebRequest>、<xref:System.Net.HttpWebRequest>、および <xref:System.Net.FtpWebRequest> クラスを使用して定義するために使用する型および列挙体を定義します。</span><span class="sxs-lookup"><span data-stu-id="e9055-124">Defines the types and enumerations used to define cache policies for resources obtained using the <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, and <xref:System.Net.FtpWebRequest> classes.</span></span>
