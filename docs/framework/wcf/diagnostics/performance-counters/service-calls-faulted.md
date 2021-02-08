---
description: '詳細情報: サービス: 失敗した呼び出し'
title: 'サービス : 失敗した呼び出し'
ms.date: 03/30/2017
ms.assetid: 6da7f100-3f61-4b3c-9409-fe1360829b8a
ms.openlocfilehash: 8689c68be01447721d75763e23e83f6c2b0c053d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803335"
---
# <a name="service-calls-faulted"></a><span data-ttu-id="eacf1-103">サービス : 失敗した呼び出し</span><span class="sxs-lookup"><span data-stu-id="eacf1-103">Service: Calls Faulted</span></span>

<span data-ttu-id="eacf1-104">カウンター名 : 失敗した呼び出し。</span><span class="sxs-lookup"><span data-stu-id="eacf1-104">Counter Name: Calls Faulted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="eacf1-105">説明</span><span class="sxs-lookup"><span data-stu-id="eacf1-105">Description</span></span>  

 <span data-ttu-id="eacf1-106">このサービスの呼び出しのうち、エラーとなったものの回数です。</span><span class="sxs-lookup"><span data-stu-id="eacf1-106">Number of calls to this service that have returned faults.</span></span> <span data-ttu-id="eacf1-107">Windows Communication Foundation (WCF) アプリケーションでは、サービスメソッドは SOAP エラーメッセージを使用して処理エラー情報を通信します。</span><span class="sxs-lookup"><span data-stu-id="eacf1-107">In Windows Communication Foundation (WCF) applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="eacf1-108">SOAP エラーは、サービス操作のメタデータに含まれるメッセージ型であり、堅牢かつインタラクティブに実行できるようにクライアントが使用するエラー コントラクトを作成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="eacf1-108">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="eacf1-109">SOAP エラーは XML 形式でクライアントに渡されるので、相互運用性の面でも優れています。</span><span class="sxs-lookup"><span data-stu-id="eacf1-109">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eacf1-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="eacf1-110">See also</span></span>

- [<span data-ttu-id="eacf1-111">コントラクトおよびサービスのエラーの指定と処理</span><span class="sxs-lookup"><span data-stu-id="eacf1-111">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
