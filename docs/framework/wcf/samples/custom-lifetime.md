---
description: '詳細情報: カスタム有効期間'
title: カスタム有効期間
ms.date: 08/20/2018
ms.assetid: 52806c07-b91c-48fe-b992-88a41924f51f
ms.openlocfilehash: 24845aaa20e60f92e2add568c81ab3d6502ebedf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99732476"
---
# <a name="custom-lifetime"></a><span data-ttu-id="b7f6d-103">カスタム有効期間</span><span class="sxs-lookup"><span data-stu-id="b7f6d-103">Custom lifetime</span></span>

<span data-ttu-id="b7f6d-104">このサンプルでは、Windows Communication Foundation (WCF) 拡張機能を記述して、共有 WCF サービスインスタンスにカスタムの有効期間サービスを提供する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-104">This sample demonstrates how to write a Windows Communication Foundation (WCF) extension to provide custom lifetime services for shared WCF service instances.</span></span>

> [!NOTE]
> <span data-ttu-id="b7f6d-105">このサンプルのセットアップ手順とビルド手順については、この記事の最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-105">The setup procedure and build instructions for this sample are located at the end of this article.</span></span>

## <a name="shared-instancing"></a><span data-ttu-id="b7f6d-106">共有インスタンス化</span><span class="sxs-lookup"><span data-stu-id="b7f6d-106">Shared instancing</span></span>

<span data-ttu-id="b7f6d-107">WCF には、サービスインスタンスに対して複数のインスタンス化モードが用意されています。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-107">WCF offers several instancing modes for your service instances.</span></span> <span data-ttu-id="b7f6d-108">この記事で説明されている共有インスタンス化モードでは、複数のチャネル間でサービスインスタンスを共有する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-108">The shared instancing mode covered in this article provides a way to share a service instance between multiple channels.</span></span> <span data-ttu-id="b7f6d-109">クライアントは、サービスのファクトリメソッドに接続して、通信を開始するための新しいチャネルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-109">Clients can contact a factory method in the service and create a new channel to start communication.</span></span> <span data-ttu-id="b7f6d-110">次のコードスニペットは、クライアントアプリケーションが既存のサービスインスタンスへの新しいチャネルを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-110">The following code snippet shows how a client application creates a new channel to an existing service instance:</span></span>

```csharp
// Create a header for the shared instance id
MessageHeader shareableInstanceContextHeader = MessageHeader.CreateHeader(
        CustomHeader.HeaderName,
        CustomHeader.HeaderNamespace,
        Guid.NewGuid().ToString());

// Create the channel factory
ChannelFactory<IEchoService> channelFactory =
    new ChannelFactory<IEchoService>("echoservice");

// Create the first channel
IEchoService proxy = channelFactory.CreateChannel();

// Call an operation to create shared service instance
using (new OperationContextScope((IClientChannel)proxy))
{
    OperationContext.Current.OutgoingMessageHeaders.Add(shareableInstanceContextHeader);
    Console.WriteLine("Service returned: " + proxy.Echo("Apple"));
}

((IChannel)proxy).Close();

// Create the second channel
IEchoService proxy2 = channelFactory.CreateChannel();

// Call an operation using the same header that will reuse the shared service instance
using (new OperationContextScope((IClientChannel)proxy2))
{
    OperationContext.Current.OutgoingMessageHeaders.Add(shareableInstanceContextHeader);
    Console.WriteLine("Service returned: " + proxy2.Echo("Apple"));
}
```

<span data-ttu-id="b7f6d-111">他のインスタンス化モードとは異なり、共有インスタンス化モードでは、独特の方法でサービス インスタンスを解放します。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-111">Unlike other instancing modes, the shared instancing mode has a unique way of releasing the service instances.</span></span> <span data-ttu-id="b7f6d-112">既定では、すべてのチャネルがに対して閉じられると、 <xref:System.ServiceModel.InstanceContext> WCF サービスランタイムは、サービスがまたはに構成されているかどうかを確認し、 <xref:System.ServiceModel.InstanceContextMode> <xref:System.ServiceModel.InstanceContextMode.PerCall> インスタンスを解放してリソースを要求するかどうかを確認し <xref:System.ServiceModel.InstanceContextMode.PerSession> ます。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-112">By default, when all the channels are closed for an <xref:System.ServiceModel.InstanceContext>, the WCF service runtime checks to see if the service <xref:System.ServiceModel.InstanceContextMode> is configured to <xref:System.ServiceModel.InstanceContextMode.PerCall> or <xref:System.ServiceModel.InstanceContextMode.PerSession>, and if so releases the instance and claims the resources.</span></span> <span data-ttu-id="b7f6d-113">カスタム <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> が使用されている場合、WCF は、 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> インスタンスを解放する前に、プロバイダーの実装のメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-113">If a custom <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> is being used, WCF invokes the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method of the provider implementation before releasing the instance.</span></span> <span data-ttu-id="b7f6d-114"><xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>がを返した場合、 `true` インスタンスは解放されます。それ以外の場合、 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 実装は、 `Dispatcher` コールバックメソッドを使用してアイドル状態のに通知を行います。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-114">If <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> returns `true` the instance is released, otherwise the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is responsible for notifying the `Dispatcher` of the idle state by using a callback method.</span></span> <span data-ttu-id="b7f6d-115">これは、プロバイダーのメソッドを呼び出すことによって行われ <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-115">This is done by calling the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> method of the provider.</span></span>

<span data-ttu-id="b7f6d-116">このサンプルでは、 <xref:System.ServiceModel.InstanceContext> アイドルタイムアウトが20秒のの解放を遅延させる方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-116">This sample demonstrates how you can delay releasing the <xref:System.ServiceModel.InstanceContext> with an idle timeout of 20 seconds.</span></span>

## <a name="extending-the-instancecontext"></a><span data-ttu-id="b7f6d-117">InstanceContext の拡張</span><span class="sxs-lookup"><span data-stu-id="b7f6d-117">Extending the InstanceContext</span></span>

<span data-ttu-id="b7f6d-118">WCF で <xref:System.ServiceModel.InstanceContext> は、はサービスインスタンスとの間のリンクです `Dispatcher` 。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-118">In WCF, <xref:System.ServiceModel.InstanceContext> is the link between the service instance and the `Dispatcher`.</span></span> <span data-ttu-id="b7f6d-119">WCF では、拡張可能なオブジェクトパターンを使用して新しい状態または動作を追加することで、このランタイムコンポーネントを拡張できます。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-119">WCF allows you to extend this runtime component by adding new state or behavior by using its extensible object pattern.</span></span> <span data-ttu-id="b7f6d-120">拡張可能オブジェクトパターンは、既存のランタイムクラスを新しい機能で拡張するか、オブジェクトに新しい状態機能を追加するために WCF で使用されます。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-120">The extensible object pattern is used in WCF to either extend existing runtime classes with new functionality or to add new state features to an object.</span></span> <span data-ttu-id="b7f6d-121">拡張可能オブジェクト パターンには、<xref:System.ServiceModel.IExtensibleObject%601>、<xref:System.ServiceModel.IExtension%601>、および <xref:System.ServiceModel.IExtensionCollection%601> の 3 つのインターフェイスがあります。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-121">There are three interfaces in the extensible object pattern: <xref:System.ServiceModel.IExtensibleObject%601>, <xref:System.ServiceModel.IExtension%601>, and <xref:System.ServiceModel.IExtensionCollection%601>.</span></span>

<span data-ttu-id="b7f6d-122">インターフェイスは、 <xref:System.ServiceModel.IExtensibleObject%601> 機能をカスタマイズする拡張を可能にするために、オブジェクトによって実装されます。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-122">The <xref:System.ServiceModel.IExtensibleObject%601> interface is implemented by objects to allow extensions that customize their functionality.</span></span>

<span data-ttu-id="b7f6d-123"><xref:System.ServiceModel.IExtension%601> インターフェイスは、`T` 型のクラスの拡張が可能なオブジェクトによって実装されます。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-123">The <xref:System.ServiceModel.IExtension%601> interface is implemented by objects that can be extensions of classes of type `T`.</span></span>

<span data-ttu-id="b7f6d-124">最後に、 <xref:System.ServiceModel.IExtensionCollection%601> インターフェイスは、 <xref:System.ServiceModel.IExtension%601> <xref:System.ServiceModel.IExtension%601> 型によっての実装を取得できるようにする実装のコレクションです。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-124">And finally, the <xref:System.ServiceModel.IExtensionCollection%601> interface is a collection of <xref:System.ServiceModel.IExtension%601> implementations that allows for retrieving an implementation of <xref:System.ServiceModel.IExtension%601> by their type.</span></span>

<span data-ttu-id="b7f6d-125">したがって、を拡張するには、 <xref:System.ServiceModel.InstanceContext> インターフェイスを実装する必要があり <xref:System.ServiceModel.IExtension%601> ます。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-125">Therefore, in order to extend the <xref:System.ServiceModel.InstanceContext>, you must implement the <xref:System.ServiceModel.IExtension%601> interface.</span></span> <span data-ttu-id="b7f6d-126">このサンプルプロジェクトでは、 `CustomLeaseExtension` クラスにこの実装が含まれています。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-126">In this sample project, the `CustomLeaseExtension` class contains this implementation.</span></span>

```csharp
class CustomLeaseExtension : IExtension<InstanceContext>
{
}
```

<span data-ttu-id="b7f6d-127"><xref:System.ServiceModel.IExtension%601> インターフェイスには、<xref:System.ServiceModel.IExtension%601.Attach%2A> と <xref:System.ServiceModel.IExtension%601.Detach%2A> の 2 つのメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-127">The <xref:System.ServiceModel.IExtension%601> interface has two methods <xref:System.ServiceModel.IExtension%601.Attach%2A> and <xref:System.ServiceModel.IExtension%601.Detach%2A>.</span></span> <span data-ttu-id="b7f6d-128">名前が示すように、これらの 2 つのメソッドは、ランタイムが <xref:System.ServiceModel.InstanceContext> クラスのインスタンスに拡張機能を関連付けるときと関連付けを解除するときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-128">As their names imply, these two methods are called when the runtime attaches and detaches the extension to an instance of the <xref:System.ServiceModel.InstanceContext> class.</span></span> <span data-ttu-id="b7f6d-129">このサンプルでは、`Attach` メソッドを使用して、拡張機能の現在のインスタンスに属する <xref:System.ServiceModel.InstanceContext> オブジェクトを追跡します。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-129">In this sample, the `Attach` method is used to keep track of the <xref:System.ServiceModel.InstanceContext> object that belongs to the current instance of the extension.</span></span>

```csharp
InstanceContext owner;

public void Attach(InstanceContext owner)
{
    this.owner = owner;
}
```

<span data-ttu-id="b7f6d-130">また、有効期間の延長をサポートするには、必要な実装を拡張機能に追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-130">In addition, you must add the necessary implementation to the extension to provide the extended lifetime support.</span></span> <span data-ttu-id="b7f6d-131">したがって、 `ICustomLease` インターフェイスは目的のメソッドを使用して宣言され、クラスに実装され `CustomLeaseExtension` ます。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-131">Therefore, the `ICustomLease` interface is declared with the desired methods and is implemented in the `CustomLeaseExtension` class.</span></span>

```csharp
interface ICustomLease
{
    bool IsIdle { get; }
    InstanceContextIdleCallback Callback { get; set; }
}

class CustomLeaseExtension : IExtension<InstanceContext>, ICustomLease
{
}
```

<span data-ttu-id="b7f6d-132">WCF <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> が実装でメソッドを呼び <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 出すと、この呼び出しはのメソッドにルーティングされ <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> `CustomLeaseExtension` ます。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-132">When WCF invokes the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method in the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation, this call is routed to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method of the `CustomLeaseExtension`.</span></span> <span data-ttu-id="b7f6d-133">次に、はその `CustomLeaseExtension` プライベート状態をチェックして、がアイドル状態かどうかを確認し <xref:System.ServiceModel.InstanceContext> ます。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-133">Then, the `CustomLeaseExtension` checks its private state to see whether the <xref:System.ServiceModel.InstanceContext> is idle.</span></span> <span data-ttu-id="b7f6d-134">アイドル状態の場合は、を返し `true` ます。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-134">If it is idle, it returns `true`.</span></span> <span data-ttu-id="b7f6d-135">それ以外の場合は、延長された指定の有効期間のタイマーが開始されます。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-135">Otherwise, it starts a timer for a specified amount of extended lifetime.</span></span>

```csharp
public bool IsIdle
{
  get
  {
    lock (thisLock)
    {
      if (isIdle)
      {
        return true;
      }
      else
      {
        StartTimer();
        return false;
      }
    }
  }
}
```

<span data-ttu-id="b7f6d-136">タイマーのイベントで `Elapsed` は、別のクリーンアップサイクルを開始するために、ディスパッチャーのコールバック関数が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-136">In the timer’s `Elapsed` event, the callback function in the Dispatcher is called in order to start another clean-up cycle.</span></span>

```csharp
void idleTimer_Elapsed(object sender, ElapsedEventArgs args)
{
    lock (thisLock)
    {
        StopTimer();
        isIdle = true;
        Utility.WriteMessageToConsole(
            ResourceHelper.GetString("MsgLeaseExpired"));
        callback(owner);
    }
}
```

<span data-ttu-id="b7f6d-137">インスタンスをアイドル状態に移行するために新しいメッセージが到着したときに、実行中のタイマーを更新する方法はありません。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-137">There's no way to renew the running timer when a new message arrives for the instance being moved to the idle state.</span></span>

<span data-ttu-id="b7f6d-138">このサンプルでは、<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> メソッドの呼び出しを受け取って <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> にルーティングするために `CustomLeaseExtension` を実装します。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-138">The sample implements <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> to intercept the calls to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method and route them to the `CustomLeaseExtension`.</span></span> <span data-ttu-id="b7f6d-139"><xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 実装は、`CustomLifetimeLease` クラスに含まれています。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-139">The <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is contained in `CustomLifetimeLease` class.</span></span> <span data-ttu-id="b7f6d-140">メソッドは、 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> WCF がサービスインスタンスを解放しようとしているときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-140">The <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method is invoked when WCF is about to release the service instance.</span></span> <span data-ttu-id="b7f6d-141">ただし、ServiceBehavior の `ISharedSessionInstance` コレクションに存在する特定の <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 実装のインスタンスは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-141">However, there is only one instance of a particular `ISharedSessionInstance` implementation in the ServiceBehavior’s <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> collection.</span></span> <span data-ttu-id="b7f6d-142">つまり、WCF によって <xref:System.ServiceModel.InstanceContext> メソッドがチェックされるときにが閉じられているかどうかを知る方法はありません <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> 。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-142">This means there's no way of knowing if the <xref:System.ServiceModel.InstanceContext> is closed at the time WCF checks the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span> <span data-ttu-id="b7f6d-143">したがって、このサンプルでは、スレッドロックを使用して、メソッドに要求をシリアル化し <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-143">Therefore, this sample uses thread locking to serialize requests to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b7f6d-144">シリアル化はアプリケーションのパフォーマンスに大きな影響を及ぼす可能性があるので、スレッド ロックは使用しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-144">Using thread locking is not a recommended approach because serialization can severely affect the performance of your application.</span></span>

<span data-ttu-id="b7f6d-145">プライベートメンバーフィールドは、 `CustomLifetimeLease` アイドル状態を追跡するためにクラスで使用され、メソッドによって返され <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-145">A private member field is used in the `CustomLifetimeLease` class to track the idle state and is returned by the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span> <span data-ttu-id="b7f6d-146">メソッドが呼び出されるたびに、 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> `isIdle` フィールドが返され、にリセットされ `false` ます。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-146">Each time the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method is called, the `isIdle` field is returned and reset to `false`.</span></span>  <span data-ttu-id="b7f6d-147">ディスパッチャーが `false` メソッドを呼び出すようにするには、この値を <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-147">It is essential to set this value to `false` in order to make sure the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> method.</span></span>

```csharp
public bool IsIdle(InstanceContext instanceContext)
{
    get
    {
        lock (thisLock)
        {
            //...
            bool idleCopy = isIdle;
            isIdle = false;
            return idleCopy;
        }
    }
}
```

<span data-ttu-id="b7f6d-148">メソッドが <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType> を返す場合 `false` 、ディスパッチャーはメソッドを使用してコールバック関数を登録し <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-148">If the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType> method returns `false`, the Dispatcher registers a callback function by using the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> method.</span></span> <span data-ttu-id="b7f6d-149">このメソッドは、解放される <xref:System.ServiceModel.InstanceContext> への参照を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-149">This method receives a reference to the <xref:System.ServiceModel.InstanceContext> being released.</span></span> <span data-ttu-id="b7f6d-150">このため、サンプルコードでは、型拡張に対してクエリを実行し、拡張され `ICustomLease` た状態のプロパティを確認でき `ICustomLease.IsIdle` ます。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-150">Therefore, the sample code can query the `ICustomLease` type extension and check the `ICustomLease.IsIdle` property in the extended state.</span></span>

```csharp
public void NotifyIdle(InstanceContextIdleCallback callback,
            InstanceContext instanceContext)
{
    lock (thisLock)
    {
       ICustomLease customLease =
           instanceContext.Extensions.Find<ICustomLease>();
       customLease.Callback = callback;
       isIdle = customLease.IsIdle;
       if (isIdle)
       {
             callback(instanceContext);
       }
    }
}
```

<span data-ttu-id="b7f6d-151">プロパティをチェックする前に `ICustomLease.IsIdle` 、コールバックプロパティを設定する必要があります。これは、が `CustomLeaseExtension` アイドル状態になったときにディスパッチャーに通知するために必要です。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-151">Before the `ICustomLease.IsIdle` property is checked, the Callback property needs to be set as this is essential for `CustomLeaseExtension` to notify the Dispatcher when it becomes idle.</span></span> <span data-ttu-id="b7f6d-152">`ICustomLease.IsIdle` が `true` を返す場合は、`isIdle` プライベート メンバーが `CustomLifetimeLease` で単に `true` に設定され、コールバック メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-152">If `ICustomLease.IsIdle` returns `true`, the `isIdle` private member is simply set in `CustomLifetimeLease` to `true` and calls the callback method.</span></span> <span data-ttu-id="b7f6d-153">コードはロックを保持しているため、他のスレッドがこのプライベートメンバーの値を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-153">Because the code holds a lock, other threads can't change the value of this private member.</span></span> <span data-ttu-id="b7f6d-154">次にディスパッチャーがを呼び出すときに、を <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType> 返し、ディスパッチャーがインスタンスを解放できるようにし `true` ます。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-154">And the next time Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType>, it returns `true` and lets Dispatcher release the instance.</span></span>

<span data-ttu-id="b7f6d-155">これでカスタム拡張機能の基礎が完成したので、この拡張機能をサービス モデルにフックする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-155">Now that the groundwork for the custom extension is completed, it has to be hooked up to the service model.</span></span> <span data-ttu-id="b7f6d-156">実装をにフックするために、WCF には `CustomLeaseExtension` <xref:System.ServiceModel.InstanceContext> <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> のブートストラップを実行するためのインターフェイスが用意されて <xref:System.ServiceModel.InstanceContext> います。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-156">To hook up the `CustomLeaseExtension` implementation to the <xref:System.ServiceModel.InstanceContext>, WCF provides the <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> interface to perform the bootstrapping of <xref:System.ServiceModel.InstanceContext>.</span></span> <span data-ttu-id="b7f6d-157">このサンプルでは、`CustomLeaseInitializer` クラスでこのインターフェイスを実装し、`CustomLeaseExtension` のインスタンスを唯一のメソッドの初期化から得られる <xref:System.ServiceModel.InstanceContext.Extensions%2A> コレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-157">In the sample, the `CustomLeaseInitializer` class implements this interface and adds an instance of `CustomLeaseExtension` to the <xref:System.ServiceModel.InstanceContext.Extensions%2A> collection from the only method initialization.</span></span> <span data-ttu-id="b7f6d-158">このメソッドは、<xref:System.ServiceModel.InstanceContext> の初期化中にディスパッチャーによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-158">This method is called by Dispatcher while initializing the <xref:System.ServiceModel.InstanceContext>.</span></span>

```csharp
public void InitializeInstanceContext(InstanceContext instanceContext,
    System.ServiceModel.Channels.Message message, IContextChannel channel)

    //...

    IExtension<InstanceContext> customLeaseExtension =
        new CustomLeaseExtension(timeout, headerId);
    instanceContext.Extensions.Add(customLeaseExtension);
}
```

 <span data-ttu-id="b7f6d-159">最後に、実装を <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 使用して、サービスモデルに実装をフックし <xref:System.ServiceModel.Description.IServiceBehavior> ます。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-159">Finally the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is hooked up to the service model by using the <xref:System.ServiceModel.Description.IServiceBehavior> implementation.</span></span> <span data-ttu-id="b7f6d-160">この実装は、`CustomLeaseTimeAttribute` クラスに配置されています。また、<xref:System.Attribute> 基本クラスから派生してこの動作を属性として公開します。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-160">This implementation is placed in the `CustomLeaseTimeAttribute` class and it also derives from the <xref:System.Attribute> base class to expose this behavior as an attribute.</span></span>

```csharp
public void ApplyDispatchBehavior(ServiceDescription description,
           ServiceHostBase serviceHostBase)
{
    CustomLifetimeLease customLease = new CustomLifetimeLease(timeout);

    foreach (ChannelDispatcherBase cdb in serviceHostBase.ChannelDispatchers)
    {
        ChannelDispatcher cd = cdb as ChannelDispatcher;

        if (cd != null)
        {
            foreach (EndpointDispatcher ed in cd.Endpoints)
            {
                ed.DispatchRuntime.InstanceContextProvider = customLease;
            }
        }
    }
}
```

<span data-ttu-id="b7f6d-161">この動作は、`CustomLeaseTime` 属性を使用して注釈を付けることにより、サンプル サービス クラスに追加できます。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-161">This behavior can be added to a sample service class by annotating it with the `CustomLeaseTime` attribute.</span></span>

```csharp
[CustomLeaseTime(Timeout = 20000)]
public class EchoService : IEchoService
{
  //…
}
```

<span data-ttu-id="b7f6d-162">このサンプルを実行すると、操作要求と応答がサービスとクライアントの両方のコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-162">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="b7f6d-163">どちらかのコンソールで Enter キーを押すと、サービスとクライアントがどちらもシャットダウンされます。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-163">Press ENTER in each console window to shut down the service and client.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b7f6d-164">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="b7f6d-164">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="b7f6d-165">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-165">Ensure that you've performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="b7f6d-166">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-166">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="b7f6d-167">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-167">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b7f6d-168">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-168">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b7f6d-169">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-169">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="b7f6d-170">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-170">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b7f6d-171">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="b7f6d-171">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Lifetime`
