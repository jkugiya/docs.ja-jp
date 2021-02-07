---
description: 詳細については、チャネルファクトリとキャッシュに関するページを参照してください。
title: チャネル ファクトリとキャッシュ
ms.date: 03/30/2017
ms.assetid: 954f030e-091c-4c0e-a7a2-10f9a6b1f529
ms.openlocfilehash: 6922191c2b99dea516d0e85aac9ed7bc12a67b81
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705201"
---
# <a name="channel-factory-and-caching"></a><span data-ttu-id="f6bd6-103">チャネル ファクトリとキャッシュ</span><span class="sxs-lookup"><span data-stu-id="f6bd6-103">Channel Factory and Caching</span></span>

<span data-ttu-id="f6bd6-104">WCF クライアント アプリケーションでは、<xref:System.ServiceModel.ChannelFactory%601> クラスを使用して WCF サービスとの通信チャネルを作成します。</span><span class="sxs-lookup"><span data-stu-id="f6bd6-104">WCF client applications use the <xref:System.ServiceModel.ChannelFactory%601> class to create a communication channel with a WCF service.</span></span>  <span data-ttu-id="f6bd6-105"><xref:System.ServiceModel.ChannelFactory%601> インスタンスを作成する場合は、次の操作が必要になるため、オーバーヘッドが生じます。</span><span class="sxs-lookup"><span data-stu-id="f6bd6-105">Creating <xref:System.ServiceModel.ChannelFactory%601> instances incurs some overhead because it involves the following operations:</span></span>

- <span data-ttu-id="f6bd6-106"><xref:System.ServiceModel.Description.ContractDescription> ツリーの構築</span><span class="sxs-lookup"><span data-stu-id="f6bd6-106">Constructing the <xref:System.ServiceModel.Description.ContractDescription> tree</span></span>

- <span data-ttu-id="f6bd6-107">必要なすべての CLR 型の反映</span><span class="sxs-lookup"><span data-stu-id="f6bd6-107">Reflecting all of the required CLR types</span></span>

- <span data-ttu-id="f6bd6-108">チャネル スタックの構築</span><span class="sxs-lookup"><span data-stu-id="f6bd6-108">Constructing the channel stack</span></span>

- <span data-ttu-id="f6bd6-109">リソースの破棄</span><span class="sxs-lookup"><span data-stu-id="f6bd6-109">Disposing of resources</span></span>

<span data-ttu-id="f6bd6-110">このオーバーヘッドを最小限に抑えるために、WCF では、WCF クライアント プロキシの使用時にチャネル ファクトリをキャッシュできます。</span><span class="sxs-lookup"><span data-stu-id="f6bd6-110">To help minimize this overhead, WCF can cache channel factories when you are using a WCF client proxy.</span></span>

> [!TIP]
> <span data-ttu-id="f6bd6-111"><xref:System.ServiceModel.ChannelFactory%601> クラスを直接使用する場合は、チャネル ファクトリの作成を直接制御できます。</span><span class="sxs-lookup"><span data-stu-id="f6bd6-111">You have direct control over channel factory creation when you use the <xref:System.ServiceModel.ChannelFactory%601> class directly.</span></span>

<span data-ttu-id="f6bd6-112">[ServiceModel メタデータユーティリティツール (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)を使用して生成された WCF クライアントプロキシは、から派生 <xref:System.ServiceModel.ClientBase%601> します。</span><span class="sxs-lookup"><span data-stu-id="f6bd6-112">WCF client proxies generated with [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) are derived from <xref:System.ServiceModel.ClientBase%601>.</span></span> <span data-ttu-id="f6bd6-113"><xref:System.ServiceModel.ClientBase%601> では、チャネル ファクトリのキャッシュ動作を定義する静的な <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> プロパティを定義します。</span><span class="sxs-lookup"><span data-stu-id="f6bd6-113"><xref:System.ServiceModel.ClientBase%601> defines a static <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> property that defines channel factory caching behavior.</span></span> <span data-ttu-id="f6bd6-114">キャッシュ設定は特定の型に対して行われます。</span><span class="sxs-lookup"><span data-stu-id="f6bd6-114">Cache settings are made for a specific type.</span></span> <span data-ttu-id="f6bd6-115">たとえば、  `ClientBase<ITest>.CacheSettings` 以下に定義されているいずれかの値に設定すると、型のプロキシ/ClientBase にのみ影響し `ITest` ます。</span><span class="sxs-lookup"><span data-stu-id="f6bd6-115">For example, setting  `ClientBase<ITest>.CacheSettings` to one of the values defined below will affect only those proxy/ClientBase of type `ITest`.</span></span> <span data-ttu-id="f6bd6-116">最初のプロキシ/ClientBase インスタンスが作成された時点で、特定の <xref:System.ServiceModel.ClientBase%601> のキャッシュ設定は不変になります。</span><span class="sxs-lookup"><span data-stu-id="f6bd6-116">The cache setting for a particular <xref:System.ServiceModel.ClientBase%601> is immutable as soon as the first proxy/ClientBase instance is created.</span></span>

## <a name="specifying-caching-behavior"></a><span data-ttu-id="f6bd6-117">キャッシュ動作の指定</span><span class="sxs-lookup"><span data-stu-id="f6bd6-117">Specifying Caching Behavior</span></span>

<span data-ttu-id="f6bd6-118">キャッシュ動作は、<xref:System.ServiceModel.ClientBase%601.CacheSetting> プロパティを次のいずれかの値に設定することで指定します。</span><span class="sxs-lookup"><span data-stu-id="f6bd6-118">Caching behavior is specified by setting the <xref:System.ServiceModel.ClientBase%601.CacheSetting> property to one of the following values.</span></span>

|<span data-ttu-id="f6bd6-119">キャッシュの設定値</span><span class="sxs-lookup"><span data-stu-id="f6bd6-119">Cache Setting Value</span></span>|<span data-ttu-id="f6bd6-120">説明</span><span class="sxs-lookup"><span data-stu-id="f6bd6-120">Description</span></span>|
|-------------------------|-----------------|
|<xref:System.ServiceModel.CacheSetting.AlwaysOn>|<span data-ttu-id="f6bd6-121">アプリケーション ドメイン内の <xref:System.ServiceModel.ClientBase%601> のすべてのインスタンスはキャッシュに参加できます。</span><span class="sxs-lookup"><span data-stu-id="f6bd6-121">All instances of <xref:System.ServiceModel.ClientBase%601> within the app-domain can participate in caching.</span></span> <span data-ttu-id="f6bd6-122">開発者は、セキュリティがキャッシュに悪影響を与えないことを確認しています。</span><span class="sxs-lookup"><span data-stu-id="f6bd6-122">The developer has determined that there are no adverse security implications to caching.</span></span> <span data-ttu-id="f6bd6-123">の "セキュリティに影響する" プロパティにアクセスする場合でも、キャッシュは無効になりません <xref:System.ServiceModel.ClientBase%601> 。</span><span class="sxs-lookup"><span data-stu-id="f6bd6-123">Caching will not be turned off even if "security-sensitive" properties on <xref:System.ServiceModel.ClientBase%601> are accessed.</span></span> <span data-ttu-id="f6bd6-124">の "セキュリティに影響する" プロパティ <xref:System.ServiceModel.ClientBase%601> は <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> 、、 <xref:System.ServiceModel.ClientBase%601.Endpoint%2A> および <xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A> です。</span><span class="sxs-lookup"><span data-stu-id="f6bd6-124">The "security-sensitive" properties of <xref:System.ServiceModel.ClientBase%601> are <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>, <xref:System.ServiceModel.ClientBase%601.Endpoint%2A> and <xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A>.</span></span>|
|<xref:System.ServiceModel.CacheSetting.Default>|<span data-ttu-id="f6bd6-125">構成ファイルで定義されているエンドポイントから作成された <xref:System.ServiceModel.ClientBase%601> のインスタンスのみがアプリケーション ドメイン内のキャッシュに参加します。</span><span class="sxs-lookup"><span data-stu-id="f6bd6-125">Only instances of <xref:System.ServiceModel.ClientBase%601> created from endpoints defined in configuration files participate in caching within the app-domain.</span></span> <span data-ttu-id="f6bd6-126">そのアプリケーション ドメイン内にプログラムで作成された <xref:System.ServiceModel.ClientBase%601> のインスタンスはキャッシュに参加しません。</span><span class="sxs-lookup"><span data-stu-id="f6bd6-126">Any instances of <xref:System.ServiceModel.ClientBase%601> created programmatically within that app-domain will not participate in caching.</span></span> <span data-ttu-id="f6bd6-127">また、 <xref:System.ServiceModel.ClientBase%601> "セキュリティに影響する" プロパティがアクセスされると、のインスタンスに対してキャッシュが無効になります。</span><span class="sxs-lookup"><span data-stu-id="f6bd6-127">Also, caching will be disabled for an instance of <xref:System.ServiceModel.ClientBase%601> once any of its "security-sensitive" properties is accessed.</span></span>|
|<xref:System.ServiceModel.CacheSetting.AlwaysOff>|<span data-ttu-id="f6bd6-128">対象となるアプリケーション ドメイン内にある特定の型の <xref:System.ServiceModel.ClientBase%601> のすべてのインスタンスのキャッシュが無効になります。</span><span class="sxs-lookup"><span data-stu-id="f6bd6-128">Caching is turned off for all instances of <xref:System.ServiceModel.ClientBase%601> of a particular type within the app-domain in question.</span></span>|

<span data-ttu-id="f6bd6-129"><xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> プロパティを使用する方法を次のコード スニペットに示します。</span><span class="sxs-lookup"><span data-stu-id="f6bd6-129">The following code snippets illustrate how to use the <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> property.</span></span>

```csharp
class Program
{
   static void Main(string[] args)
   {
      ClientBase<ITest>.CacheSettings = CacheSettings.AlwaysOn;
      foreach (string msg in messages)
      {
         using (TestClient proxy = new TestClient (new BasicHttpBinding(), new EndpointAddress(address)))
         {
            // ...
            proxy.Test(msg);
            // ...
         }
      }
   }
}
// Generated by SvcUtil.exe
public partial class TestClient : System.ServiceModel.ClientBase, ITest { }
```

<span data-ttu-id="f6bd6-130">上のコードでは、`TestClient` のすべてのインスタンスで同じチャネル ファクトリを使用します。</span><span class="sxs-lookup"><span data-stu-id="f6bd6-130">In the above code, all instances of `TestClient` will use the same channel factory.</span></span>

```csharp
class Program
{
   static void Main(string[] args)
   {
      ClientBase.CacheSettings = CacheSettings.Default;
      int i = 1;
      foreach (string msg in messages)
      {
         using (TestClient proxy = new TestClient ("MyEndpoint", new EndpointAddress(address)))
         {
            if (i == 4)
            {
               ServiceEndpoint endpoint = proxy.Endpoint;
               ... // use endpoint in some way
            }
            proxy.Test(msg);
         }
         i++;
   }
}

// Generated by SvcUtil.exe
public partial class TestClient : System.ServiceModel.ClientBase, ITest {}
```

<span data-ttu-id="f6bd6-131">上の例では、`TestClient` のすべてのインスタンスで同じチャネル ファクトリを使用します (インスタンス #4 を除く)。</span><span class="sxs-lookup"><span data-stu-id="f6bd6-131">In the example above, all instances of `TestClient` would use the same channel factory except instance #4.</span></span> <span data-ttu-id="f6bd6-132">インスタンス #4 では、そのインスタンス専用に作成されたチャネル ファクトリを使用します。</span><span class="sxs-lookup"><span data-stu-id="f6bd6-132">Instance #4 would use a channel factory that is created specifically for its use.</span></span> <span data-ttu-id="f6bd6-133">この設定は、特定のエンドポイントで同じチャネル ファクトリ型 (この場合は `ITest`) の他のエンドポイントと異なるセキュリティ設定が必要なシナリオに有効です。</span><span class="sxs-lookup"><span data-stu-id="f6bd6-133">This setting would work for scenarios where a particular endpoint needs different security settings from the other endpoints of the same channel factory type (in this case `ITest`).</span></span>

```csharp
class Program
{
   static void Main(string[] args)
   {
      ClientBase.CacheSettings = CacheSettings.AlwaysOff;
      foreach (string msg in messages)
      {
         using (TestClient proxy = new TestClient ("MyEndpoint", new EndpointAddress(address)))
         {
            proxy.Test(msg);
         }
      }
   }
}

// Generated by SvcUtil.exe
public partial class TestClient : System.ServiceModel.ClientBase, ITest {}
```

<span data-ttu-id="f6bd6-134">上の例では、`TestClient` のすべてのインスタンスで異なるチャネル ファクトリを使用します。</span><span class="sxs-lookup"><span data-stu-id="f6bd6-134">In the example above, all instances of `TestClient` would use different channel factories.</span></span> <span data-ttu-id="f6bd6-135">これは、エンドポイントごとにセキュリティ要件が異なり、キャッシュする意味がない場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="f6bd6-135">This is useful when each endpoint has different security requirements and it makes no sense to cache.</span></span>

## <a name="see-also"></a><span data-ttu-id="f6bd6-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="f6bd6-136">See also</span></span>

- <xref:System.ServiceModel.ClientBase%601>
- [<span data-ttu-id="f6bd6-137">クライアントを構築する</span><span class="sxs-lookup"><span data-stu-id="f6bd6-137">Building Clients</span></span>](../building-clients.md)
- [<span data-ttu-id="f6bd6-138">クライアント</span><span class="sxs-lookup"><span data-stu-id="f6bd6-138">Clients</span></span>](clients.md)
- [<span data-ttu-id="f6bd6-139">WCF クライアントを使用したサービスへのアクセス</span><span class="sxs-lookup"><span data-stu-id="f6bd6-139">Accessing Services Using a WCF Client</span></span>](../accessing-services-using-a-wcf-client.md)
- [<span data-ttu-id="f6bd6-140">方法: ChannelFactory を使用する</span><span class="sxs-lookup"><span data-stu-id="f6bd6-140">How to: Use the ChannelFactory</span></span>](how-to-use-the-channelfactory.md)
