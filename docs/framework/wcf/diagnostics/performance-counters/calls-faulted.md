---
description: '詳細情報: 失敗した呼び出し'
title: 失敗した呼び出し
ms.date: 03/30/2017
ms.assetid: bb9e8045-6aeb-4b7f-a825-8283c44252a1
ms.openlocfilehash: 0530d7a9bc337ce7ce4ba584a3e72addd13e0779
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99759693"
---
# <a name="calls-faulted"></a><span data-ttu-id="5e8b5-103">失敗した呼び出し</span><span class="sxs-lookup"><span data-stu-id="5e8b5-103">Calls Faulted</span></span>

<span data-ttu-id="5e8b5-104">カウンター名 : 失敗した呼び出し</span><span class="sxs-lookup"><span data-stu-id="5e8b5-104">Counter Name: Calls Faulted</span></span>  
  
## <a name="description"></a><span data-ttu-id="5e8b5-105">説明</span><span class="sxs-lookup"><span data-stu-id="5e8b5-105">Description</span></span>  

 <span data-ttu-id="5e8b5-106">この操作への呼び出しに失敗した回数です。</span><span class="sxs-lookup"><span data-stu-id="5e8b5-106">Number of calls to this operation that returned faults.</span></span> <span data-ttu-id="5e8b5-107">Windows Communication Foundation (WCF) アプリケーションでは、サービスメソッドは SOAP エラーメッセージを使用して処理エラー情報を通信します。</span><span class="sxs-lookup"><span data-stu-id="5e8b5-107">In Windows Communication Foundation (WCF) applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="5e8b5-108">SOAP エラーは、サービス操作のメタデータに含まれるメッセージ型であり、堅牢かつインタラクティブに実行できるようにクライアントが使用するエラー コントラクトを作成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="5e8b5-108">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="5e8b5-109">SOAP エラーは XML 形式でクライアントに渡されるので、相互運用性の面でも優れています。</span><span class="sxs-lookup"><span data-stu-id="5e8b5-109">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e8b5-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="5e8b5-110">See also</span></span>

- [<span data-ttu-id="5e8b5-111">コントラクトおよびサービスのエラーの指定と処理</span><span class="sxs-lookup"><span data-stu-id="5e8b5-111">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
