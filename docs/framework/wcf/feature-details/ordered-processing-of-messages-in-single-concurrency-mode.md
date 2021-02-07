---
description: 詳細については、「単一の同時実行モードでのメッセージの順序付け処理」を参照してください。
title: Single コンカレンシー モードでメッセージを順番に処理する
ms.date: 03/30/2017
ms.assetid: a90f5662-a796-46cd-ae33-30a4072838af
ms.openlocfilehash: 2dd876f1831dda8b388108f238810be333e693be
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99733685"
---
# <a name="ordered-processing-of-messages-in-single-concurrency-mode"></a><span data-ttu-id="c5c06-103">Single コンカレンシー モードでメッセージを順番に処理する</span><span class="sxs-lookup"><span data-stu-id="c5c06-103">Ordered Processing of Messages in Single Concurrency Mode</span></span>

<span data-ttu-id="c5c06-104">基になるチャネルがセッションフルの場合を除き、WCF はメッセージの処理順序について一切保証しません。</span><span class="sxs-lookup"><span data-stu-id="c5c06-104">WCF makes no guarantees about the order in which messages are processed, unless the underlying channel is sessionful.</span></span>  <span data-ttu-id="c5c06-105">たとえば、セッションフルチャネルではなく MsmqInputChannel を使用する WCF サービスでは、メッセージを順番に処理することができません。</span><span class="sxs-lookup"><span data-stu-id="c5c06-105">For instance, a WCF service that uses MsmqInputChannel, which is not a sessionful channel, will fail to process messages in order.</span></span> <span data-ttu-id="c5c06-106">場合によっては、開発者が注文処理の動作を必要としても、セッションを使用しないようにすることがあります。</span><span class="sxs-lookup"><span data-stu-id="c5c06-106">There are some circumstances where a developer may want the in order processing behavior but not want to use sessions.</span></span> <span data-ttu-id="c5c06-107">このトピックでは、サービスが Single コンカレンシー モードで実行されている場合にこの動作を構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c5c06-107">This topic describes how to configure this behavior when a service is running in Single Concurrency Mode.</span></span>  
  
## <a name="in-order-message-processing"></a><span data-ttu-id="c5c06-108">順番に従ったメッセージの処理</span><span class="sxs-lookup"><span data-stu-id="c5c06-108">In-order Message Processing</span></span>  

 <span data-ttu-id="c5c06-109"><xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> という名前の新しい属性が <xref:System.ServiceModel.ServiceBehaviorAttribute> に追加されました。</span><span class="sxs-lookup"><span data-stu-id="c5c06-109">A new attribute called <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> has been added to the <xref:System.ServiceModel.ServiceBehaviorAttribute>.</span></span> <span data-ttu-id="c5c06-110"><xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> を true に設定し、<xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> を <xref:System.ServiceModel.ConcurrencyMode.Single> に設定すると、サービスに送信されたメッセージは順番に処理されます。</span><span class="sxs-lookup"><span data-stu-id="c5c06-110">When <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> is set to true and <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to <xref:System.ServiceModel.ConcurrencyMode.Single> messages sent to the service will be processed in order.</span></span> <span data-ttu-id="c5c06-111">次のコードは、これらの属性の設定方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="c5c06-111">The following code snippet illustrates how to set these attributes.</span></span>  
  
```csharp
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, EnsureOrderedDispatch = true )]  
    class Service : IService  
    {  
         // ...  
    }  
```  
  
 <span data-ttu-id="c5c06-112"><xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> をその他の値に設定すると、<xref:System.InvalidOperationException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="c5c06-112">If <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to any other value, an <xref:System.InvalidOperationException> is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5c06-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="c5c06-113">See also</span></span>

- [<span data-ttu-id="c5c06-114">セッション、インスタンス化、およびコンカレンシー</span><span class="sxs-lookup"><span data-stu-id="c5c06-114">Sessions, Instancing, and Concurrency</span></span>](sessions-instancing-and-concurrency.md)
- [<span data-ttu-id="c5c06-115">コンカレンシー</span><span class="sxs-lookup"><span data-stu-id="c5c06-115">Concurrency</span></span>](../samples/concurrency.md)
