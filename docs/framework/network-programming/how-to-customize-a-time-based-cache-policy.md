---
description: '詳細情報: 方法: 時間ベースのキャッシュ ポリシーをカスタマイズする'
title: '方法: 時間ベースのキャッシュ ポリシーをカスタマイズする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time-based cache policies
- customizing time-based cache policies
- cache [.NET Framework], time-based policies
ms.assetid: 8d84f936-2376-4356-9264-03162e0f9279
ms.openlocfilehash: bb00faa5c2cd3170a0f56b74032867d489c1fb8a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747453"
---
# <a name="how-to-customize-a-time-based-cache-policy"></a><span data-ttu-id="2144e-103">方法: 時間ベースのキャッシュ ポリシーをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="2144e-103">How to: customize a time-based cache policy</span></span>

<span data-ttu-id="2144e-104">時間ベースのキャッシュ ポリシーを作成する場合、最大有効期間、最小鮮度、最大期限延長、またはキャッシュ同期日付の値を指定することで、キャッシュの動作をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="2144e-104">When creating a time-based cache policy, you can customize caching behavior by specifying values for maximum age, minimum freshness, maximum staleness, or cache synchronization date.</span></span> <span data-ttu-id="2144e-105"><xref:System.Net.Cache.HttpRequestCachePolicy> オブジェクトは、これらの値の有効な組み合わせを指定できるようにする複数のコンストラクターを提供します。</span><span class="sxs-lookup"><span data-stu-id="2144e-105">The <xref:System.Net.Cache.HttpRequestCachePolicy> object provides several constructors that allow you to specify valid combinations of these values.</span></span>

## <a name="to-create-a-time-based-cache-policy-that-uses-a-cache-synchronization-date"></a><span data-ttu-id="2144e-106">キャッシュ同期日付を使用する時間ベースのキャッシュ ポリシーを作成するには</span><span class="sxs-lookup"><span data-stu-id="2144e-106">To create a time-based cache policy that uses a cache synchronization date</span></span>

<span data-ttu-id="2144e-107"><xref:System.Net.Cache.HttpRequestCachePolicy> コンストラクターに <xref:System.DateTime> オブジェクトを渡して、キャッシュ同期日付を使用する時間ベースのキャッシュ ポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="2144e-107">Create a time-based cache policy that uses a cache synchronization date by passing a <xref:System.DateTime> object to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor:</span></span>

```csharp
public static HttpRequestCachePolicy CreateLastSyncPolicy(DateTime when)
{
    var policy = new HttpRequestCachePolicy(when);
    Console.WriteLine("When: {0}", when);
    Console.WriteLine(policy.ToString());
    return policy;
}
```

```vb
Public Shared Function CreateLastSyncPolicy([when] As DateTime) As HttpRequestCachePolicy
    Dim policy As New HttpRequestCachePolicy([when])
    Console.WriteLine("When: {0}", [when])
    Console.WriteLine(policy.ToString())
    Return policy
End Function
```

<span data-ttu-id="2144e-108">次のように出力されます。</span><span class="sxs-lookup"><span data-stu-id="2144e-108">The output is similar to the following:</span></span>

```output
When: 1/14/2004 8:07:30 AM
Level:Default CacheSyncDate:1/14/2004 8:07:30 AM
```

## <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness"></a><span data-ttu-id="2144e-109">最小鮮度に基づく時間ベースのキャッシュ ポリシーを作成するには</span><span class="sxs-lookup"><span data-stu-id="2144e-109">To create a time-based cache policy that is based on minimum freshness</span></span>

<span data-ttu-id="2144e-110">`cacheAgeControl` パラメーター値として <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> を指定し、<xref:System.Net.Cache.HttpRequestCachePolicy> コンストラクターに <xref:System.TimeSpan> オブジェクトを渡して、最小鮮度に基づく時間ベースのキャッシュ ポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="2144e-110">Create a time-based cache policy that is based on minimum freshness by specifying <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> as the `cacheAgeControl` parameter value and passing a <xref:System.TimeSpan> object to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor:</span></span>

```csharp
public static HttpRequestCachePolicy CreateMinFreshPolicy(TimeSpan span)
{
    var policy = new HttpRequestCachePolicy(HttpCacheAgeControl.MinFresh, span);
    Console.WriteLine(policy.ToString());
    return policy;
}
```

```vb
Public Shared Function CreateMinFreshPolicy(span As TimeSpan) As HttpRequestCachePolicy
    Dim policy As New HttpRequestCachePolicy(HttpCacheAgeControl.MinFresh, span)
    Console.WriteLine(policy.ToString())
    Return policy
End Function
```

<span data-ttu-id="2144e-111">呼び出しと出力例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="2144e-111">For the following invocation:</span></span>

```csharp
CreateMinFreshPolicy(new TimeSpan(1,0,0));
```

<span data-ttu-id="2144e-112">出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="2144e-112">The output is:</span></span>

```output
Level:Default MinFresh:3600
```

## <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness-and-maximum-age"></a><span data-ttu-id="2144e-113">最小鮮度と最大有効期間に基づく時間ベースのキャッシュ ポリシーを作成するには</span><span class="sxs-lookup"><span data-stu-id="2144e-113">To create a time-based cache policy that is based on minimum freshness and maximum age</span></span>

<span data-ttu-id="2144e-114">`cacheAgeControl` パラメーター値として <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> を指定し、<xref:System.Net.Cache.HttpRequestCachePolicy> コンストラクターに 2 つの <xref:System.TimeSpan> オブジェクト (1 つはリソースの最大有効期間を指定し、もう 1 つはキャッシュから返されたオブジェクトで許可される最小鮮度を指定する) を渡して、最小鮮度と最大有効期間に基づく時間ベースのキャッシュ ポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="2144e-114">Create a time-based cache policy that is based on minimum freshness and maximum age by specifying <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> as the `cacheAgeControl` parameter value and passing two <xref:System.TimeSpan> objects to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor, one to specify the maximum age for resources and a second to specify the minimum freshness permitted for an object returned from the cache:</span></span>

```csharp
public static HttpRequestCachePolicy CreateFreshAndAgePolicy(TimeSpan freshMinimum, TimeSpan ageMaximum)
{
    var policy = new HttpRequestCachePolicy(HttpCacheAgeControl.MaxAgeAndMinFresh, ageMaximum, freshMinimum);
    Console.WriteLine(policy.ToString());
    return policy;
}
```

```vb
Public Shared Function CreateFreshAndAgePolicy(freshMinimum As TimeSpan, ageMaximum As TimeSpan) As HttpRequestCachePolicy
    Dim policy As New HttpRequestCachePolicy(HttpCacheAgeControl.MaxAgeAndMinFresh, ageMaximum, freshMinimum)
    Console.WriteLine(policy.ToString())
    Return policy
End Function
```

<span data-ttu-id="2144e-115">呼び出しと出力例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="2144e-115">For the following invocation:</span></span>
  
```csharp
CreateFreshAndAgePolicy(new TimeSpan(5,0,0), new TimeSpan(10,0,0));  
```  

<span data-ttu-id="2144e-116">出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="2144e-116">The output is:</span></span>
  
```output
Level:Default MaxAge:36000 MinFresh:18000  
```  
  
## <a name="see-also"></a><span data-ttu-id="2144e-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="2144e-117">See also</span></span>

- [<span data-ttu-id="2144e-118">ネットワーク アプリケーションのキャッシュ管理</span><span class="sxs-lookup"><span data-stu-id="2144e-118">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="2144e-119">キャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="2144e-119">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="2144e-120">場所ベースのキャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="2144e-120">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="2144e-121">時間ベースのキャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="2144e-121">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="2144e-122">\<requestCaching> 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="2144e-122">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
