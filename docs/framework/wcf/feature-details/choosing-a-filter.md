---
description: 詳細については、「フィルターの選択」を参照してください。
title: フィルターの選択
ms.date: 03/30/2017
ms.assetid: 67ab5af9-b9d9-4300-b3b1-41abb5a1fd10
ms.openlocfilehash: 7fa484775f0a08ccef28da358cd057465c49f390
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705279"
---
# <a name="choosing-a-filter"></a><span data-ttu-id="1b7a8-103">フィルターの選択</span><span class="sxs-lookup"><span data-stu-id="1b7a8-103">Choosing a Filter</span></span>

<span data-ttu-id="1b7a8-104">ルーティング サービスを構成する際には、適切なメッセージ フィルターを選択し、受信するメッセージと正確に一致できるように、それらのフィルターを構成することが重要です。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-104">When configuring the Routing Service, it is important to select correct message filters and configure them to allow you to make exact matches against the messages you receive.</span></span> <span data-ttu-id="1b7a8-105">選択したフィルターの適合基準が幅広すぎる場合や、適切に構成されていない場合は、メッセージが正しくルーティングされません。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-105">If the filters you select are overly broad in their matches or are incorrectly configured, messages are routed incorrectly.</span></span> <span data-ttu-id="1b7a8-106">フィルターの適合基準が厳格すぎると、一部のメッセージの有効なルーティング先が見つからないことがあります。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-106">If the filters are too restrictive, you may not have any valid routes available for some of your messages.</span></span>

## <a name="filter-types"></a><span data-ttu-id="1b7a8-107">フィルターの種類</span><span class="sxs-lookup"><span data-stu-id="1b7a8-107">Filter Types</span></span>

<span data-ttu-id="1b7a8-108">ルーティング サービスで使用するフィルターを選択する際には、各フィルターのしくみと、受信メッセージの一部として使用できる情報について理解しておくことが重要です。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-108">When selecting the filters that are used by the Routing Service, it is important that you understand how each filter works as well as what information is available as part of the incoming messages.</span></span> <span data-ttu-id="1b7a8-109">たとえば、すべてのメッセージが同じエンドポイントを介して受信される場合は、すべてのメッセージが Address フィルターと EndpointName フィルターに一致するため、これらのフィルターは役に立ちません。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-109">For instance, if all messages are received over the same endpoint, the Address and EndpointName filters are not useful because all messages match these filters.</span></span>

### <a name="action"></a><span data-ttu-id="1b7a8-110">操作</span><span class="sxs-lookup"><span data-stu-id="1b7a8-110">Action</span></span>

<span data-ttu-id="1b7a8-111">Action フィルターは <xref:System.ServiceModel.Channels.MessageHeaders.Action%2A> プロパティを確認します。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-111">The Action filter inspects the <xref:System.ServiceModel.Channels.MessageHeaders.Action%2A> property.</span></span> <span data-ttu-id="1b7a8-112">メッセージの Action ヘッダーの内容が、フィルター構成で指定されているフィルター データ値と一致する場合、このフィルターは `true` を返します。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-112">If the contents of the Action header in the message match the filter data value specified in the filter configuration, then this filter returns `true`.</span></span> <span data-ttu-id="1b7a8-113">次の例では、アクションフィルターを使用して、 `FilterElement` の値を含むアクションヘッダーを持つメッセージを照合するを定義し `http://namespace/contract/operation/` ます。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-113">The following example defines a `FilterElement` that uses the Action filter to match messages with an action header that contains a value of `http://namespace/contract/operation/`.</span></span>

```xml
<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation/" />
```

```csharp
ActionMessageFilter action1 = new ActionMessageFilter(new string[] { "http://namespace/contract/operation" });
```

<span data-ttu-id="1b7a8-114">一意のアクション ヘッダーを含むメッセージをルーティングするときは、このフィルターを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-114">This filter should be used when routing messages that contain a unique Action header.</span></span>

### <a name="endpointaddress"></a><span data-ttu-id="1b7a8-115">EndpointAddress</span><span class="sxs-lookup"><span data-stu-id="1b7a8-115">EndpointAddress</span></span>

<span data-ttu-id="1b7a8-116">EndpointAddress フィルターは、メッセージを受信した EndpointAddress を確認します。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-116">The EndpointAddress filter inspects the EndpointAddress that the message was received on.</span></span> <span data-ttu-id="1b7a8-117">メッセージが着信したアドレスが、フィルター構成で指定されたフィルター アドレスと正確に一致した場合、このフィルターは `true` を返します。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-117">If the address that the message arrives at exactly matches the filter address specified in the filter configuration, then this filter returns `true`.</span></span> <span data-ttu-id="1b7a8-118">次の例では、 `FilterElement` アドレスフィルターを使用して "http:///vdir/s.svc/b" にアドレス指定されたすべてのメッセージを照合するを定義し \<hostname> ます。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-118">The following example defines a `FilterElement` that uses the Address filter to match any messages addressed to "http://\<hostname>/vdir/s.svc/b".</span></span>

```xml
<filter name="address1" filterType="EndpointAddress" filterData="http://host/vdir/s.svc/b" />
```

```csharp
EndpointAddressMessageFilter address1 = new EndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);
```

> [!NOTE]
> <span data-ttu-id="1b7a8-119">アドレスのホスト名部分は、クライアントで完全修飾ドメイン名、NetBIOS 名、IP アドレス、それ以外の名前のどれが使用されるかによって異なることがあります。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-119">It is important to note that the host name portion of an address can differ based on whether the client uses the fully qualified domain name, NetBIOS name, IP address, or other name.</span></span> <span data-ttu-id="1b7a8-120">異なる値が同じホストを参照している場合があるため、この比較の既定の動作では、照合の際にアドレスのホスト名部分は使用されません。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-120">Because differing values can refer to the same host, the default behavior for this comparison is to not use the host name portion of the address when performing matches.</span></span>
>
> <span data-ttu-id="1b7a8-121">ルーティング サービスをプログラムで構成する際に、比較の際にホスト名を評価できるように、この動作を変更できます。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-121">This behavior can be modified to allow the comparison to evaluate the host name when configuring the Routing Service programmatically.</span></span>

<span data-ttu-id="1b7a8-122">受信メッセージが一意のアドレス宛てである場合は、このフィルターを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-122">This filter should be used when the incoming messages are addressed to a unique address.</span></span>

### <a name="endpointaddressprefix"></a><span data-ttu-id="1b7a8-123">EndpointAddressPrefix</span><span class="sxs-lookup"><span data-stu-id="1b7a8-123">EndpointAddressPrefix</span></span>

<span data-ttu-id="1b7a8-124">EndpointAddressPrefix フィルターは、EndpointAddress フィルターに似ています。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-124">The EndpointAddressPrefix filter is similar to the EndpointAddress filter.</span></span> <span data-ttu-id="1b7a8-125">EndpointAddressPrefix フィルターは、メッセージを受信した EndpointAddress を確認します。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-125">The EndpointAddressPrefix filter inspects the EndpointAddress that the message was received on.</span></span> <span data-ttu-id="1b7a8-126">ただし、EndpointAddressPrefix フィルターは、フィルター構成で指定された値で始まるアドレスを一致させることによって、ワイルドカードとして機能します。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-126">However the EndpointAddressPrefix filter acts as a wildcard by matching addresses that begin with the value specified in the filter configuration.</span></span> <span data-ttu-id="1b7a8-127">次の例では、 `FilterElement` EndpointAddressPrefix フィルターを使用して宛てのメッセージを照合するを定義し `http://<hostname>/vdir*` ます。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-127">The following example defines a `FilterElement` that uses the EndpointAddressPrefix filter to match any messages addressed to `http://<hostname>/vdir*`.</span></span>

```xml
<filter name="prefix1" filterType="EndpointAddressPrefix" filterData="http://host/vdir" />
```

```csharp
PrefixEndpointAddressMessageFilter prefix1 = new PrefixEndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);
```

> [!NOTE]
> <span data-ttu-id="1b7a8-128">アドレスのホスト名部分は、クライアントで完全修飾ドメイン名、NetBIOS 名、IP アドレス、それ以外の名前のどれが使用されるかによって異なることがあります。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-128">It is important to note that the host name portion of an address can differ based on whether the client uses the fully qualified domain name, NetBIOS name, IP address, or other name.</span></span> <span data-ttu-id="1b7a8-129">異なる値が同じホストを参照している場合があるため、この比較の既定の動作では、照合の際にアドレスのホスト名部分は使用されません。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-129">Because differing values can refer to the same host, the default behavior for this comparison is to not use the host name portion of the address when performing matches.</span></span>

<span data-ttu-id="1b7a8-130">共通のアドレス プレフィックスを共有する受信メッセージをルーティングするときは、このフィルターを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-130">This filter should be used when routing incoming messages that share a common address prefix.</span></span>

### <a name="and"></a><span data-ttu-id="1b7a8-131">AND</span><span class="sxs-lookup"><span data-stu-id="1b7a8-131">AND</span></span>

<span data-ttu-id="1b7a8-132">AND フィルターが、メッセージ内の値を直接フィルターすることはありません。しかし、AND フィルターを使用すると、他の 2 つのフィルターを組み合わせて `AND` 条件を作成し、それらのフィルターの両方がメッセージと一致した場合に、AND フィルターが `true` に評価されるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-132">The AND filter does not directly filter on a value within a message, but allows you to combine two other filters to create an `AND` condition where both filters must match the message before the AND filter evaluates to `true`.</span></span> <span data-ttu-id="1b7a8-133">これにより、すべてのサブフィルターが一致した場合にだけ一致する、複雑なフィルターを作成できます。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-133">This allows you to create complex filters that only match if all the sub-filters match.</span></span> <span data-ttu-id="1b7a8-134">次の例では、Address フィルターと Action フィルターを定義した後で、それらのフィルターの両方に照合してメッセージを評価する AND フィルターを定義します。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-134">The following example defines an address filter and an action filter, and then defines an AND filter that evaluates a message against both the address and action filters.</span></span> <span data-ttu-id="1b7a8-135">Address フィルターと Action フィルターの両方と一致した場合、AND フィルターは `true` を返します。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-135">If both the address and the action filters match, then the AND filter returns `true`.</span></span>

```xml
<filter name="address1" filterType="AddressPrefix" filterData="http://host/vdir"/>
<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation/"/>
<filter name="and1" filterType="And" filter1="address1" filter2="action1" />
```

```csharp
EndpointAddressMessageFilter address1 = new EndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);
ActionMessageFilter action1 = new ActionMessageFilter(new string[] { "http://namespace/contract/operation" });
StrictAndMessageFilter and1=new StrictAndMessageFilter(address1, action1);
```

<span data-ttu-id="1b7a8-136">複数のフィルターのロジックを組み合わせて一致を判断する必要がある場合は、このフィルターを使用します。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-136">This filter should be used when you must combine the logic from multiple filters to determine when a match should be made.</span></span> <span data-ttu-id="1b7a8-137">たとえば、アクションとメッセージの特定の組み合わせだけを特定のアドレスに受け取る必要がある複数の送信先がある場合は、AND フィルターを使用して、必要な Action フィルターと Address フィルターを組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-137">For example, if you have multiple destinations that must receive only certain combinations of actions and messages to particular addresses, you can use an AND filter to combine the necessary Action and Address filters.</span></span>

### <a name="custom"></a><span data-ttu-id="1b7a8-138">カスタム</span><span class="sxs-lookup"><span data-stu-id="1b7a8-138">Custom</span></span>

<span data-ttu-id="1b7a8-139">カスタムフィルターの種類を選択する場合は、このフィルターに使用する **Messagefilter** 実装を含むアセンブリの型を含む customtype 値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-139">When selecting the Custom filter type, you must provide a customType value that contains the type of the assembly that contains the **MessageFilter** implementation to be used for this filter.</span></span> <span data-ttu-id="1b7a8-140">また、filterData には、Custom フィルターがメッセージの評価に必要とするすべての値が格納されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-140">Additionally, filterData must contain any values that the custom filter may require in its evaluation of messages.</span></span> <span data-ttu-id="1b7a8-141">次の例では、`FilterElement` MessageFilter 実装を使用する `CustomAssembly.MyCustomMsgFilter` を定義します。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-141">The following example defines a `FilterElement` that uses the `CustomAssembly.MyCustomMsgFilter` MessageFilter implementation.</span></span>

```xml
<filter name="custom1" filterType="Custom" customType="CustomAssembly.MyCustomMsgFilter, CustomAssembly" filterData="Custom Data" />
```

```csharp
MyCustomMsgFilter custom1=new MyCustomMsgFilter("Custom Data");
```

<span data-ttu-id="1b7a8-142">に用意されているフィルターの対象ではないメッセージに対してカスタムの照合ロジックを実行する必要がある場合は、 [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] **messagefilter** クラスの実装であるカスタムフィルターを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-142">If you need to perform custom matching logic against a message that is not covered by the filters provided with [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)], you must create a custom filter that is an implementation of the **MessageFilter** class.</span></span> <span data-ttu-id="1b7a8-143">たとえば、受信メッセージ内の 1 つのフィールドを、構成としてフィルターに指定された既知の値のリストと比較するカスタム フィルターや、特定のメッセージ要素をハッシュしてから、その値を調査してフィルターが `true` と `false` のどちらを返すかを判断するカスタム フィルターを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-143">For example, you might create a custom filter that compares a field in the incoming message against a list of known values given to the filter as configuration, or that hashes a particular message element and then examines that value to determine whether the filter should return `true` or `false`.</span></span>

### <a name="endpointname"></a><span data-ttu-id="1b7a8-144">EndpointName</span><span class="sxs-lookup"><span data-stu-id="1b7a8-144">EndpointName</span></span>

<span data-ttu-id="1b7a8-145">EndpointName フィルターは、メッセージを受信したエンドポイントの名前を確認します。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-145">The EndpointName filter inspects the name of the endpoint that received the message.</span></span> <span data-ttu-id="1b7a8-146">次の例では、EndpointName フィルターを使用して、 `FilterElement` "SvcEndpoint" で受信したメッセージをルーティングするを定義します。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-146">The following example defines a `FilterElement` that uses the EndpointName filter to route messages received on the "SvcEndpoint".</span></span>

```xml
<filter name="name1" filterType="Endpoint" filterData="SvcEndpoint" />
```

```csharp
EndpointNameMessageFilter name1 = new EndpointNameMessageFilter("SvcEndpoint");
```

<span data-ttu-id="1b7a8-147">このフィルターは、ルーティング サービスが複数の名前付きサービス エンドポイントを公開する場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-147">This filter is useful when the Routing Service exposes more than one named service endpoint.</span></span> <span data-ttu-id="1b7a8-148">たとえば、ルーティング サービスがメッセージの受信に使用する 2 つのエンドポイントを公開し、その 1 つを、メッセージのリアルタイム処理を必要とする優先顧客が使用し、残りの 1 つを使用して、受信のタイミングが重要でないメッセージを受信する場合があります。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-148">For example, you might expose two endpoints that the Routing Service uses to receive messages; one is used by priority customers who require real-time processing of their messages, while the other endpoint receives messages that are not time sensitive.</span></span>

<span data-ttu-id="1b7a8-149">メッセージを受信したエンドポイントを特定する際に完全なアドレスの一致を使用することはよくありますが、定義されたエンドポイント名を使用すると、エラーの可能性が少なく、すばやく処理できるので便利です。特に、エンドポイント名が必須の属性となる、構成ファイルを使用したルーティング サービスの構成では、この方法が便利です。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-149">While you can often use full address matching to determine which endpoint a message was received on, using the defined endpoint name instead is a convenient shortcut that is often less error prone, especially when configuring a Routing Service using a configuration file (where endpoint names are a required attribute).</span></span>

### <a name="matchall"></a><span data-ttu-id="1b7a8-150">MatchAll</span><span class="sxs-lookup"><span data-stu-id="1b7a8-150">MatchAll</span></span>

<span data-ttu-id="1b7a8-151">MatchAll フィルターは、受信したすべてのメッセージと一致します。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-151">The MatchAll filter matches any received message.</span></span> <span data-ttu-id="1b7a8-152">受信したすべてのメッセージのコピーを格納するログ サービスの場合など、受信したすべてのメッセージを常に特定のエンドポイントにルーティングする必要がある場合は、このフィルターが便利です。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-152">It is useful if you must always route all received messages to a specific endpoint, such as a logging service that stores a copy of all received messages.</span></span> <span data-ttu-id="1b7a8-153">次の例で定義する `FilterElement` では、MatchAll フィルターを使用します。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-153">The following example defines a `FilterElement` that uses the MatchAll filter.</span></span>

```xml
<filter name="matchAll1" filterType="MatchAll" />
```

```csharp
MatchAllMessageFilter matchAll1 = new MatchAllMessageFilter();
```

### <a name="xpath"></a><span data-ttu-id="1b7a8-154">XPath</span><span class="sxs-lookup"><span data-stu-id="1b7a8-154">XPath</span></span>

<span data-ttu-id="1b7a8-155">XPath フィルターを使用すると、XPath クエリを指定して、メッセージ内の特定の要素を確認できます。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-155">The XPath filter allows you to specify an XPath query that is used to inspect a specific element within the message.</span></span> <span data-ttu-id="1b7a8-156">XPath フィルターは、メッセージ内の XML アドレス指定可能なエントリを直接確認できる、強力なフィルター オプションです。ただし、このフィルターを使用するには、受信するメッセージの構造に関する特定の知識が必要です。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-156">XPath filtering is a powerful filtering option that allows you to directly inspect any XML addressable entry within the message; however it requires that you have specific knowledge of the structure of the messages that you are receiving.</span></span> <span data-ttu-id="1b7a8-157">次の例では、 `FilterElement` XPath フィルターを使用して、"ns" 名前空間プレフィックスによって参照される名前空間内の "element" という名前の要素についてメッセージを検査するを定義します。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-157">The following example defines a `FilterElement` that uses the XPath filter to inspect the message for an element named "element" within the namespace referenced by the "ns" namespace prefix.</span></span>

```xml
<filter name="xpath1" filterType="XPath" filterData="//ns:element" />
```

```csharp
XPathMessageFilter xpath1=new XPathMessageFilter("//ns:element");
```

<span data-ttu-id="1b7a8-158">受信するメッセージに特定の値が含まれていることがわかっている場合は、このフィルターが便利です。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-158">This filter is useful if you know that the messages you are receiving contain a specific value.</span></span> <span data-ttu-id="1b7a8-159">たとえば、同じサービスの 2 つのバージョンをホストしており、そのサービスの新しい方のバージョン宛てのメッセージのカスタム ヘッダーに一意の値が含まれていることがわかっている場合は、XPath を使用するフィルターを作成してそのヘッダーに移動し、そのヘッダー内にある値を、フィルター構成で指定されている別の値と比較して、そのフィルターが一致するかどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-159">For example, if you are hosting two versions of the same service and you know that messages addressed to the newer version of the service contain a unique value in a custom header, you can create a filter that uses XPath to navigate to this header and compares the value present in the header to another given in the filter configuration to determine if the filter matches.</span></span>

<span data-ttu-id="1b7a8-160">XPath クエリには、長い文字列値または複雑な文字列値である一意の名前空間が含まれていることが多いため、XPath フィルターでは、名前空間用の一意のプレフィックスを定義する名前空間テーブルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-160">Because XPath queries often contain unique namespaces, which are often lengthy or complex string values, the XPath filter allows you to use the namespace table to define unique prefixes for your namespaces.</span></span> <span data-ttu-id="1b7a8-161">名前空間テーブルの詳細については、「 [メッセージフィルター](message-filters.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-161">For more information about the namespace table, see [Message Filters](message-filters.md).</span></span>

<span data-ttu-id="1b7a8-162">XPath クエリのデザインの詳細については、「 [Xpath 構文](/previous-versions/dotnet/netframework-4.0/ms256471(v=vs.100))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1b7a8-162">For more information about designing XPath queries, see [XPath Syntax](/previous-versions/dotnet/netframework-4.0/ms256471(v=vs.100)).</span></span>

## <a name="see-also"></a><span data-ttu-id="1b7a8-163">関連項目</span><span class="sxs-lookup"><span data-stu-id="1b7a8-163">See also</span></span>

- [<span data-ttu-id="1b7a8-164">メッセージ フィルター</span><span class="sxs-lookup"><span data-stu-id="1b7a8-164">Message Filters</span></span>](message-filters.md)
- [<span data-ttu-id="1b7a8-165">方法: フィルターの使用</span><span class="sxs-lookup"><span data-stu-id="1b7a8-165">How To: Use Filters</span></span>](how-to-use-filters.md)
