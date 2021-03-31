---
description: '詳細情報: プロバイダーを実装する方法'
title: '方法: プロバイダーを実装する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- observer design pattern [.NET], implementing providers
- providers [.NET], in observer design pattern
- observables [.NET], in observer design pattern
ms.assetid: 790b5d8b-d546-40a6-beeb-151b574e5ee5
ms.openlocfilehash: 09c2e5127a241bc1d522e19ae71df420131c3d4d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641773"
---
# <a name="how-to-implement-a-provider"></a><span data-ttu-id="7f35d-103">方法: プロバイダーを実装する</span><span class="sxs-lookup"><span data-stu-id="7f35d-103">How to: Implement a Provider</span></span>

<span data-ttu-id="7f35d-104">オブザーバー デザイン パターンでは、データを監視して通知を送信するプロバイダーと、プロバイダーから通知 (コールバック) を受信する 1 つまたは複数のオブザーバーを分ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="7f35d-104">The observer design pattern requires a division between a provider, which monitors data and sends notifications, and one or more observers, which receive notifications (callbacks) from the provider.</span></span> <span data-ttu-id="7f35d-105">このトピックでは、プロバイダーを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7f35d-105">This topic discusses how to create a provider.</span></span> <span data-ttu-id="7f35d-106">関連トピックの「[方法: オブザーバーを実装する](how-to-implement-an-observer.md)」でオブザーバーの作成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7f35d-106">A related topic, [How to: Implement an Observer](how-to-implement-an-observer.md), discusses how to create an observer.</span></span>  
  
### <a name="to-create-a-provider"></a><span data-ttu-id="7f35d-107">プロバイダーを作成するには</span><span class="sxs-lookup"><span data-stu-id="7f35d-107">To create a provider</span></span>  
  
1. <span data-ttu-id="7f35d-108">プロバイダーがオブザーバーに送信するデータを定義します。</span><span class="sxs-lookup"><span data-stu-id="7f35d-108">Define the data that the provider is responsible for sending to observers.</span></span> <span data-ttu-id="7f35d-109">プロバイダーとそれがオブザーバーに送信するデータは 1 つの型にすることができますが、一般的には、異なる型で表されます。</span><span class="sxs-lookup"><span data-stu-id="7f35d-109">Although the provider and the data that it sends to observers can be a single type, they are generally represented by different types.</span></span> <span data-ttu-id="7f35d-110">たとえば、温度を監視するアプリケーションでは、`Temperature` 構造によって、プロバイダー (次の手順で定義する `TemperatureMonitor` クラスで表されます) が監視し、オブザーバーがサブスクライブするデータが定義されます。</span><span class="sxs-lookup"><span data-stu-id="7f35d-110">For example, in a temperature monitoring application, the `Temperature` structure defines the data that the provider (which is represented by the `TemperatureMonitor` class defined in the next step) monitors and to which observers subscribe.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/data.cs#1)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/data.vb#1)]  
  
2. <span data-ttu-id="7f35d-111">データ プロバイダーを定義します。これは <xref:System.IObservable%601?displayProperty=nameWithType> インターフェイスを実装する型です。</span><span class="sxs-lookup"><span data-stu-id="7f35d-111">Define the data provider, which is a type that implements the <xref:System.IObservable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="7f35d-112">プロバイダーのジェネリック型引数は、プロバイダーがオブザーバーに送信する型です。</span><span class="sxs-lookup"><span data-stu-id="7f35d-112">The provider's generic type argument is the type that the provider sends to observers.</span></span> <span data-ttu-id="7f35d-113">次の例では、`TemperatureMonitor` クラスが定義されています。これは構築 <xref:System.IObservable%601?displayProperty=nameWithType> 実装であり、ジェネリック型引数の `Temperature` が指定されています。</span><span class="sxs-lookup"><span data-stu-id="7f35d-113">The following example defines a `TemperatureMonitor` class, which is a constructed <xref:System.IObservable%601?displayProperty=nameWithType> implementation with a generic type argument of `Temperature`.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#2)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#2)]  
  
3. <span data-ttu-id="7f35d-114">各オブザーバーに適時通知できるようにプロバイダーがオブザーバーの参照を格納する方法を定義します。</span><span class="sxs-lookup"><span data-stu-id="7f35d-114">Determine how the provider will store references to observers so that each observer can be notified when appropriate.</span></span> <span data-ttu-id="7f35d-115">最も一般的には、ジェネリック <xref:System.Collections.Generic.List%601> オブジェクトのようなコレクション オブジェクトがこの目的で使用されます。</span><span class="sxs-lookup"><span data-stu-id="7f35d-115">Most commonly, a collection object such as a generic <xref:System.Collections.Generic.List%601> object is used for this purpose.</span></span> <span data-ttu-id="7f35d-116">次の例では、`TemperatureMonitor` クラス コンストラクターでインスタンス化されるプライベート <xref:System.Collections.Generic.List%601> オブジェクトが定義されます。</span><span class="sxs-lookup"><span data-stu-id="7f35d-116">The following example defines a private <xref:System.Collections.Generic.List%601> object that is instantiated in the `TemperatureMonitor` class constructor.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#3)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#3)]  
  
4. <span data-ttu-id="7f35d-117">通知の受信をいつでも停止できるように、プロバイダーがサブスクライバーに返す <xref:System.IDisposable> 実装を定義します。</span><span class="sxs-lookup"><span data-stu-id="7f35d-117">Define an <xref:System.IDisposable> implementation that the provider can return to subscribers so that they can stop receiving notifications at any time.</span></span> <span data-ttu-id="7f35d-118">次の例では、入れ子になった `Unsubscriber` クラスが定義されています。インスタンス化されるとき、サブスクライバー コレクションとサブスクライバーの参照がこのクラスに渡されます。</span><span class="sxs-lookup"><span data-stu-id="7f35d-118">The following example defines a nested `Unsubscriber` class that is passed a reference to the subscribers collection and to the subscriber when the class is instantiated.</span></span> <span data-ttu-id="7f35d-119">このコードによって、サブスクライバーはオブジェクトの <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 実装を呼び出し、それ自体をサブスクライバー コレクションから削除できます。</span><span class="sxs-lookup"><span data-stu-id="7f35d-119">This code enables the subscriber to call the object's <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation to remove itself from the subscribers collection.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#4)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#4)]  
  
5. <span data-ttu-id="7f35d-120"><xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="7f35d-120">Implement the <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="7f35d-121">このメソッドには <xref:System.IObserver%601?displayProperty=nameWithType> インターフェイスの参照が渡されます。手順 3 で、その目的のために作られたオブジェクトに格納されます。</span><span class="sxs-lookup"><span data-stu-id="7f35d-121">The method is passed a reference to the <xref:System.IObserver%601?displayProperty=nameWithType> interface and should be stored in the object designed for that purpose in step 3.</span></span> <span data-ttu-id="7f35d-122">このメソッドはその後、手順 4 で作られる <xref:System.IDisposable> 実装を返します。</span><span class="sxs-lookup"><span data-stu-id="7f35d-122">The method should then return the <xref:System.IDisposable> implementation developed in step 4.</span></span> <span data-ttu-id="7f35d-123">次の例は、`TemperatureMonitor` クラスの <xref:System.IObservable%601.Subscribe%2A> メソッドの実装です。</span><span class="sxs-lookup"><span data-stu-id="7f35d-123">The following example shows the implementation of the <xref:System.IObservable%601.Subscribe%2A> method in the `TemperatureMonitor` class.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#5)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#5)]  
  
6. <span data-ttu-id="7f35d-124"><xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>、<xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>、<xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> の実装を呼び出し、オブザーバーに適宜通知します。</span><span class="sxs-lookup"><span data-stu-id="7f35d-124">Notify observers as appropriate by calling their <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, and <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementations.</span></span> <span data-ttu-id="7f35d-125">エラーが発生し、プロバイダーが <xref:System.IObserver%601.OnError%2A> メソッドを呼び出さない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="7f35d-125">In some cases, a provider may not call the <xref:System.IObserver%601.OnError%2A> method when an error occurs.</span></span> <span data-ttu-id="7f35d-126">たとえば、次の `GetTemperature` メソッドは 5 秒おきに温度データを読み取るモニターをシミュレートし、温度が前の計測から 1 度以上変化するとオブザーバーに通知します。</span><span class="sxs-lookup"><span data-stu-id="7f35d-126">For example, the following `GetTemperature` method simulates a monitor that reads temperature data every five seconds and notifies observers if the temperature has changed by at least .1 degree since the previous reading.</span></span> <span data-ttu-id="7f35d-127">デバイスが温度を報告しないと (つまり、その値が null)、プロバイダーは転送が完了していることをオブザーバーに通知します。</span><span class="sxs-lookup"><span data-stu-id="7f35d-127">If the device does not report a temperature (that is, if its value is null), the provider notifies observers that the transmission is complete.</span></span> <span data-ttu-id="7f35d-128">各オブザーバーの <xref:System.IObserver%601.OnCompleted%2A> メソッドを呼び出すだけではなく、`GetTemperature` メソッドは <xref:System.Collections.Generic.List%601> コレクションを消去することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7f35d-128">Note that, in addition to calling each observer's <xref:System.IObserver%601.OnCompleted%2A> method, the `GetTemperature` method clears the <xref:System.Collections.Generic.List%601> collection.</span></span> <span data-ttu-id="7f35d-129">この場合、プロバイダーはそのオブザーバーの <xref:System.IObserver%601.OnError%2A> メソッドを呼び出しません。</span><span class="sxs-lookup"><span data-stu-id="7f35d-129">In this case, the provider makes no calls to the <xref:System.IObserver%601.OnError%2A> method of its observers.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#6)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="7f35d-130">例</span><span class="sxs-lookup"><span data-stu-id="7f35d-130">Example</span></span>  

 <span data-ttu-id="7f35d-131">次の例では、温度を監視するアプリケーションの <xref:System.IObservable%601> 実装を定義するソース コードをまるごと確認できます。</span><span class="sxs-lookup"><span data-stu-id="7f35d-131">The following example contains the complete source code for defining an <xref:System.IObservable%601> implementation for a temperature monitoring application.</span></span> <span data-ttu-id="7f35d-132">オブザーバーに送信されるデータである `Temperature` 構造と <xref:System.IObservable%601> 実装である `TemperatureMonitor` クラスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7f35d-132">It includes the `Temperature` structure, which is the data sent to observers, and the `TemperatureMonitor` class, which is the <xref:System.IObservable%601> implementation.</span></span>  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#7)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="7f35d-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="7f35d-133">See also</span></span>

- <xref:System.IObservable%601>
- [<span data-ttu-id="7f35d-134">オブサーバー デザイン パターン</span><span class="sxs-lookup"><span data-stu-id="7f35d-134">Observer Design Pattern</span></span>](observer-design-pattern.md)
- [<span data-ttu-id="7f35d-135">方法: オブザーバーを実装する</span><span class="sxs-lookup"><span data-stu-id="7f35d-135">How to: Implement an Observer</span></span>](how-to-implement-an-observer.md)
- [<span data-ttu-id="7f35d-136">オブザーバー デザイン パターンのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="7f35d-136">Observer Design Pattern Best Practices</span></span>](observer-design-pattern-best-practices.md)
