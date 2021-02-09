---
description: '詳細情報: 方法:アプリケーションの場所ベースのキャッシュ ポリシーを設定する'
title: '方法: アプリケーションの場所ベースのキャッシュ ポリシーを設定します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- explicitly defining cache behavior
- location-based cache policies
- local cache
- request cache policies
- cache [.NET Framework], location-based policies
ms.assetid: 683bb88e-3411-4f46-9686-3411b6ba511c
ms.openlocfilehash: d86e40e24eacb6ce3107e50213941c1169191943
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662781"
---
# <a name="how-to-set-a-location-based-cache-policy-for-an-application"></a><span data-ttu-id="06218-103">方法: アプリケーションの場所ベースのキャッシュ ポリシーを設定します。</span><span class="sxs-lookup"><span data-stu-id="06218-103">How to: Set a Location-Based Cache Policy for an Application</span></span>

<span data-ttu-id="06218-104">場所ベースのキャッシュ ポリシーを使用すると、要求されたリソースの場所を基にしてアプリケーションでキャッシュの動作を明示的に定義することができます。</span><span class="sxs-lookup"><span data-stu-id="06218-104">Location-based cache policies allow an application to explicitly define caching behavior based on the location of the requested resource.</span></span> <span data-ttu-id="06218-105">このトピックでは、キャッシュ ポリシーをプログラムで設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="06218-105">This topic demonstrates setting the cache policy programmatically.</span></span> <span data-ttu-id="06218-106">構成ファイルを使用してアプリケーションのポリシーを設定する方法については、「[\<requestCaching> 要素 (ネットワーク設定)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="06218-106">For information on setting the policy for an application using the configuration files, see [\<requestCaching> Element (Network Settings)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md).</span></span>  
  
### <a name="to-set-a-location-based-cache-policy-for-an-application"></a><span data-ttu-id="06218-107">アプリケーションの場所ベースのキャッシュ ポリシーを設定するには</span><span class="sxs-lookup"><span data-stu-id="06218-107">To set a location-based cache policy for an application</span></span>  
  
1. <span data-ttu-id="06218-108"><xref:System.Net.Cache.RequestCachePolicy> または <xref:System.Net.Cache.HttpRequestCachePolicy> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="06218-108">Create a <xref:System.Net.Cache.RequestCachePolicy> or <xref:System.Net.Cache.HttpRequestCachePolicy> object.</span></span>  
  
2. <span data-ttu-id="06218-109">アプリケーション ドメインの既定値として、ポリシー オブジェクトを設定します。</span><span class="sxs-lookup"><span data-stu-id="06218-109">Set the policy object as the default for the application domain.</span></span>  
  
### <a name="to-set-a-policy-that-takes-requested-resources-from-a-cache"></a><span data-ttu-id="06218-110">要求されたリソースをキャッシュから取得するポリシーを設定するには</span><span class="sxs-lookup"><span data-stu-id="06218-110">To set a policy that takes requested resources from a cache</span></span>  
  
- <span data-ttu-id="06218-111">可能な場合は要求されたリソースをキャッシュから取得するポリシーを作成します。それ以外の場合は、キャッシュのレベルを <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable> に設定して、サーバーに要求を送信します。</span><span class="sxs-lookup"><span data-stu-id="06218-111">Create a policy that takes requested resources from a cache if available, and otherwise, sends requests to the server, by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable>.</span></span> <span data-ttu-id="06218-112">要求は、リモートのキャッシュを含めて、クライアントとサーバー間にある任意のキャッシュによって満たすことができます。</span><span class="sxs-lookup"><span data-stu-id="06218-112">A request can be fulfilled by any cache between the client and server, including remote caches.</span></span>  
  
    ```csharp  
    public static void UseCacheIfAvailable()  
    {  
        HttpRequestCachePolicy policy = new HttpRequestCachePolicy  
            (HttpRequestCacheLevel.CacheIfAvailable);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub UseCacheIfAvailable()  
        Dim policy As New HttpRequestCachePolicy _  
             (HttpRequestCacheLevel.CacheIfAvailable)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-resources"></a><span data-ttu-id="06218-113">どのキャッシュもリソースを提供しないようにするポリシーを設定するには</span><span class="sxs-lookup"><span data-stu-id="06218-113">To set a policy that prevents any cache from supplying resources</span></span>  
  
- <span data-ttu-id="06218-114">どのキャッシュも要求されたリソースを提供しないようにするポリシーを作成するには、キャッシュ レベルを <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore> に設定します。</span><span class="sxs-lookup"><span data-stu-id="06218-114">Create a policy that prevents any cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore>.</span></span> <span data-ttu-id="06218-115">このポリシー レベルは、リソースが存在する場合にローカル キャッシュからリソースを削除し、さらにリモート キャッシュにもリソースを削除するように指示します。</span><span class="sxs-lookup"><span data-stu-id="06218-115">This policy level removes the resource from the local cache if it is present and indicates to remote caches that they should also remove the resource.</span></span>  
  
    ```csharp  
    public static void DoNotUseCache()  
    {  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy
            (HttpRequestCacheLevel.NoCacheNoStore);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub DoNotUseCache()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.NoCacheNoStore)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-returns-requested-resources-only-if-they-are-in-the-local-cache"></a><span data-ttu-id="06218-116">リソースがローカル キャッシュ内にある場合にのみ、要求されたリソースを返すポリシーを設定するには</span><span class="sxs-lookup"><span data-stu-id="06218-116">To set a policy that returns requested resources only if they are in the local cache</span></span>  
  
- <span data-ttu-id="06218-117">リソースがローカル キャッシュ内にある場合にのみ、要求されたリソースを返すポリシーを作成するには、キャッシュ レベルを <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly> に設定します。</span><span class="sxs-lookup"><span data-stu-id="06218-117">Create a policy that returns requested resources only if they are in the local cache by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly>.</span></span> <span data-ttu-id="06218-118">要求されたリソースがキャッシュにない場合、<xref:System.Net.WebException> 例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="06218-118">If the requested resource is not in the cache, a <xref:System.Net.WebException> exception is thrown.</span></span>  
  
    ```csharp  
    public static void OnlyUseCache()  
    {  
        HttpRequestCachePolicy policy = new HttpRequestCachePolicy
            (HttpRequestCacheLevel.CacheOnly);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub OnlyUseCache()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.CacheOnly)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-prevents-the-local-cache-from-supplying-resources"></a><span data-ttu-id="06218-119">ローカル キャッシュがリソースを提供しないようにするポリシーを設定するには</span><span class="sxs-lookup"><span data-stu-id="06218-119">To set a policy that prevents the local cache from supplying resources</span></span>  
  
- <span data-ttu-id="06218-120">ローカル キャッシュが要求されたリソースを提供しないようにするポリシーを作成するには、キャッシュ レベルを <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh> に設定します。</span><span class="sxs-lookup"><span data-stu-id="06218-120">Create a policy that prevents the local cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh>.</span></span> <span data-ttu-id="06218-121">要求されたリソースが中間のキャッシュに存在し、正常に再検証された場合は、中間のキャッシュが要求されたリソースを提供できます。</span><span class="sxs-lookup"><span data-stu-id="06218-121">If the requested resource is in an intermediate cache and is successfully revalidated, the intermediate cache can supply the requested resource.</span></span>  
  
    ```csharp  
    public static void DoNotUseLocalCache()  
    {  
     HttpRequestCachePolicy policy = new HttpRequestCachePolicy
            (HttpRequestCacheLevel.Refresh);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub DoNotUseLocalCache()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.Refresh)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-requested-resources"></a><span data-ttu-id="06218-122">どのキャッシュも要求されたリソースを提供しないようにするポリシーを設定するには</span><span class="sxs-lookup"><span data-stu-id="06218-122">To set a policy that prevents any cache from supplying requested resources</span></span>  
  
- <span data-ttu-id="06218-123">どのキャッシュも要求されたリソースを提供しないようにするポリシーを作成するには、キャッシュ レベルを <xref:System.Net.Cache.HttpRequestCacheLevel.Reload> に設定します。</span><span class="sxs-lookup"><span data-stu-id="06218-123">Create a policy that prevents any cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Reload>.</span></span> <span data-ttu-id="06218-124">サーバーによって返されるリソースは、キャッシュに格納できます。</span><span class="sxs-lookup"><span data-stu-id="06218-124">The resource returned by the server can be stored in the cache.</span></span>  
  
    ```csharp  
    public static void SendToServer()  
    {  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy
            (HttpRequestCacheLevel.Reload);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub SendToServer()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.Reload)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-allows-any-cache-to-supply-requested-resources-if-the-resource-on-the-server-is-not-newer-than-the-cached-copy"></a><span data-ttu-id="06218-125">サーバー上のリソースがキャッシュされたコピーよりも新しいバージョンではない場合に、要求されたリソースをキャッシュが提供することを許可するポリシーを設定するには</span><span class="sxs-lookup"><span data-stu-id="06218-125">To set a policy that allows any cache to supply requested resources if the resource on the server is not newer than the cached copy</span></span>  
  
- <span data-ttu-id="06218-126">サーバー上のリソースがキャッシュされたコピーよりも新しいバージョンではない場合に、要求されたリソースをキャッシュが提供することを許可するポリシーを作成するには、キャッシュ レベルを <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate> に設定します。</span><span class="sxs-lookup"><span data-stu-id="06218-126">Create a policy that allows any cache to supply requested resources if the resource on the server is not newer than the cached copy by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate>.</span></span>  
  
    ```csharp  
    public static void CheckServer()  
    {  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy  
             (HttpRequestCacheLevel.Revalidate);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub CheckServer()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.Revalidate)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="06218-127">参照</span><span class="sxs-lookup"><span data-stu-id="06218-127">See also</span></span>

- [<span data-ttu-id="06218-128">ネットワーク アプリケーションのキャッシュ管理</span><span class="sxs-lookup"><span data-stu-id="06218-128">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="06218-129">キャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="06218-129">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="06218-130">場所ベースのキャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="06218-130">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="06218-131">時間ベースのキャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="06218-131">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="06218-132">\<requestCaching> 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="06218-132">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
