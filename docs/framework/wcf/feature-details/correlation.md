---
description: 詳細については、「関連付け」を参照してください。
title: 相関関係
ms.date: 03/30/2017
ms.assetid: 60151f6c-19b7-47af-9cdc-76c2ac95f301
ms.openlocfilehash: c4142a4e7c9472eaf52fc5339221bb59c1883f9e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780363"
---
# <a name="correlation"></a><span data-ttu-id="9265b-103">相関関係</span><span class="sxs-lookup"><span data-stu-id="9265b-103">Correlation</span></span>

<span data-ttu-id="9265b-104">ワークフロー サービス アプリケーションが他のサービスと通信するときには、やり取りされるメッセージが、適切なワークフロー インスタンスにディスパッチされることが重要です。</span><span class="sxs-lookup"><span data-stu-id="9265b-104">When workflow service applications communicate with other services, it is important that messages between them are dispatched to the appropriate workflow instance.</span></span> <span data-ttu-id="9265b-105">相関関係によって、これを実現する機構が提供されます。</span><span class="sxs-lookup"><span data-stu-id="9265b-105">Correlation provides the mechanism for this.</span></span> <span data-ttu-id="9265b-106">このセクションの各トピックでは、相関関係の概要を示し、さまざまなワークフロー サービス シナリオで相関関係を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9265b-106">The topics in this section provide an overview of correlation and how to use it in different workflow service scenarios.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9265b-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="9265b-107">In This Section</span></span>  

 [<span data-ttu-id="9265b-108">相関関係の概要</span><span class="sxs-lookup"><span data-stu-id="9265b-108">Correlation Overview</span></span>](correlation-overview.md)  
 <span data-ttu-id="9265b-109">[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] で使用可能な相関関係の種類の概要を示します。</span><span class="sxs-lookup"><span data-stu-id="9265b-109">Provides an overview of the types of correlation available in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="9265b-110">永続的な二重</span><span class="sxs-lookup"><span data-stu-id="9265b-110">Durable Duplex</span></span>](durable-duplex-correlation.md)  
 <span data-ttu-id="9265b-111">永続的な二重の相関関係について説明します。</span><span class="sxs-lookup"><span data-stu-id="9265b-111">Describes durable duplex correlation.</span></span>
  
 [<span data-ttu-id="9265b-112">要求/応答</span><span class="sxs-lookup"><span data-stu-id="9265b-112">Request-Reply</span></span>](request-reply-correlation.md)  
 <span data-ttu-id="9265b-113">要求/応答の相関関係について説明します。</span><span class="sxs-lookup"><span data-stu-id="9265b-113">Describes request-reply correlation.</span></span>  
  
 [<span data-ttu-id="9265b-114">相関関係のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="9265b-114">Troubleshooting Correlation</span></span>](troubleshooting-correlation.md)  
 <span data-ttu-id="9265b-115">相関関係のトラブルシューティング方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="9265b-115">Provides methods for troubleshooting correlation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9265b-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="9265b-116">See also</span></span>

- <xref:System.ServiceModel.Activities.CorrelationHandle>
- <xref:System.ServiceModel.Activities.Send>
- <xref:System.ServiceModel.Activities.Receive>
- <xref:System.ServiceModel.CorrelationQuery>
