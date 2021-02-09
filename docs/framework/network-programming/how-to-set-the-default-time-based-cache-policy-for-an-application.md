---
description: '詳細情報: 方法:アプリケーションの既定の時間ベースのキャッシュ ポリシーを設定する'
title: '方法: アプリケーションの既定の時間ベースのキャッシュ ポリシーを設定します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time-based cache policies
- cache [.NET Framework], time-based policies
- default time-based cache policy
ms.assetid: 6bfce066-a2e7-4add-a05e-85c12ec9f07f
ms.openlocfilehash: 1ca9504d8a6df20d3824230d5fb96eb0f13636eb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662768"
---
# <a name="how-to-set-the-default-time-based-cache-policy-for-an-application"></a><span data-ttu-id="a9655-103">方法: アプリケーションの既定の時間ベースのキャッシュ ポリシーを設定する</span><span class="sxs-lookup"><span data-stu-id="a9655-103">How to: Set the Default Time-Based Cache Policy for an Application</span></span>

<span data-ttu-id="a9655-104">既定の時間ベースのキャッシュ ポリシーにより、キャッシュされたリソースと共に送信されるヘッダーによってアプリケーションでキャッシュの動作を定義することができます。RFC 2616 のセクション 13 と 14 で定義されているキャッシュの動作については、[Internet Engineering Task Force (IETF)](https://www.ietf.org/) に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a9655-104">The default time-based cache policy allows an application to have its cache behavior defined by the headers sent with the cached resource and the cache behavior defined in sections 13 and 14 of RFC 2616, available at [Internet Engineering Task Force (IETF)](https://www.ietf.org/) website.</span></span> <span data-ttu-id="a9655-105">これは、ほとんどのアプリケーションの適切なキャッシュの動作です。</span><span class="sxs-lookup"><span data-stu-id="a9655-105">This is the appropriate cache behavior for most applications.</span></span>  
  
### <a name="to-set-the-default-automatic-policy-for-an-application"></a><span data-ttu-id="a9655-106">アプリケーションの既定の自動ポリシーを設定するには</span><span class="sxs-lookup"><span data-stu-id="a9655-106">To set the default automatic policy for an application</span></span>  
  
1. <span data-ttu-id="a9655-107">既定の時間ベースのポリシー オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="a9655-107">Create a default time-based policy object.</span></span>  
  
2. <span data-ttu-id="a9655-108">アプリケーション ドメインの既定値として、ポリシー オブジェクトを設定します。</span><span class="sxs-lookup"><span data-stu-id="a9655-108">Set the policy object as the default for the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9655-109">例</span><span class="sxs-lookup"><span data-stu-id="a9655-109">Example</span></span>  

 <span data-ttu-id="a9655-110">このセクションの 2 つの例では、同一のポリシーを生成します。</span><span class="sxs-lookup"><span data-stu-id="a9655-110">The two examples in this section produce identical policies.</span></span>  
  
 <span data-ttu-id="a9655-111">次の例では、既定の時間ベースのポリシーを作成し、アプリケーション ドメインの既定値として設定します。</span><span class="sxs-lookup"><span data-stu-id="a9655-111">The following example creates a default time-based policy and sets it as the default for the application domain.</span></span>  
  
```csharp  
public static void SetDefaultTimeBasedPolicy ()  
{  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy ();  
    HttpWebRequest.DefaultCachePolicy = policy ;  
}  
```  
  
```vb  
Public Shared Sub SetDefaultTimeBasedPolicy ()  
    Dim policy = New HttpRequestCachePolicy ()  
    HttpWebRequest.DefaultCachePolicy = policy  
End Sub  
```  
  
 <span data-ttu-id="a9655-112">次の例に示すように、<xref:System.Net.Cache.RequestCachePolicy> クラスを使用して既定の時間ベースのキャッシュ ポリシーを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="a9655-112">You can also create the default time-based cache policy using the <xref:System.Net.Cache.RequestCachePolicy> class as shown in the following example:</span></span>  
  
```csharp  
public static void SetDefaultTimeBasedPolicy2()  
{  
    RequestCachePolicy policy = new RequestCachePolicy ();  
    HttpWebRequest.DefaultCachePolicy = policy ;  
}  
```  
  
```vb  
Public Shared Sub SetDefaultTimeBasedPolicy2()  
    Dim policy As New RequestCachePolicy()  
    HttpWebRequest.DefaultCachePolicy = policy  
End Sub  
```  
  
## <a name="see-also"></a><span data-ttu-id="a9655-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="a9655-113">See also</span></span>

- [<span data-ttu-id="a9655-114">ネットワーク アプリケーションのキャッシュ管理</span><span class="sxs-lookup"><span data-stu-id="a9655-114">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="a9655-115">キャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="a9655-115">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="a9655-116">場所ベースのキャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="a9655-116">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="a9655-117">時間ベースのキャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="a9655-117">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="a9655-118">\<requestCaching> 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="a9655-118">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
