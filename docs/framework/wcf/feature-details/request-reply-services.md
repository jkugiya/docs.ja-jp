---
description: 詳細については、「Request-Reply Services」を参照してください。
title: 要求/応答サービス
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], request-reply services
- contracts [WCF], request-reply services
- WCF [WCF], request-reply services
- request-reply contracts [WCF]
ms.assetid: 2fa710f1-47f4-4598-b063-3ab3bd22ebba
ms.openlocfilehash: 804441d91577623b2a5fac9292f183628f9e542e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99632829"
---
# <a name="request-reply-services"></a><span data-ttu-id="643f5-103">要求/応答サービス</span><span class="sxs-lookup"><span data-stu-id="643f5-103">Request-Reply Services</span></span>

<span data-ttu-id="643f5-104">要求/応答サービスは、Windows Communication Foundation (WCF) の操作コントラクトの既定の種類です。</span><span class="sxs-lookup"><span data-stu-id="643f5-104">Request-reply services are the default type of operation contract in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="643f5-105">クライアントはサービス操作を呼び出し、サービスからの応答を待機します。</span><span class="sxs-lookup"><span data-stu-id="643f5-105">Clients make calls to service operations and wait for a response from the service.</span></span> <span data-ttu-id="643f5-106">サービス操作の呼び出しは、同期的または非同期的に実行できます。同期呼び出しでは、応答を受信するか、呼び出しがタイムアウトするまで、クライアントがブロックされます。非同期呼び出しでは、クライアントはサービス操作の呼び出し後、動作を続行し、別のスレッドのサービスからの応答を受信できます。</span><span class="sxs-lookup"><span data-stu-id="643f5-106">You can perform calls to a service operation either synchronously, where the client blocks until it receives a response from the service or the call times, or asynchronously, where the client makes a call to the service operation, continues working, and receives the response from the service on another thread.</span></span>  
  
 <span data-ttu-id="643f5-107">要求/応答サービス コントラクトを作成するには、サービス コントラクトを定義し、次のサンプル コードに示すように <xref:System.ServiceModel.OperationContractAttribute> クラスを各操作に適用します。</span><span class="sxs-lookup"><span data-stu-id="643f5-107">To create a request-reply service contract, define your service contract, and apply the <xref:System.ServiceModel.OperationContractAttribute> class to each operation, as shown in the following sample code.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IRequestReplyCalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="643f5-108">これは既定の動作であるため、<xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> プロパティを `false` に設定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="643f5-108">You do not have to set the  <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `false` because this is the default behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="643f5-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="643f5-109">See also</span></span>

- [<span data-ttu-id="643f5-110">一方向サービス</span><span class="sxs-lookup"><span data-stu-id="643f5-110">One-Way Services</span></span>](one-way-services.md)
- [<span data-ttu-id="643f5-111">双方向サービス</span><span class="sxs-lookup"><span data-stu-id="643f5-111">Duplex Services</span></span>](duplex-services.md)
