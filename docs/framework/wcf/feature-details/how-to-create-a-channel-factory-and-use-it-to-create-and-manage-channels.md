---
description: '詳細については、「方法: チャネルファクトリを作成し、それを使用してチャネルを作成および管理する」を参照してください。'
title: '方法: チャネル ファクトリを作成および使用して、チャネルを作成および管理する'
ms.date: 03/30/2017
ms.assetid: 018dcc30-9f61-419e-af8e-412a85e8d282
ms.openlocfilehash: 4e76e5ea0c6776e5623a2e716a3702e628f146f6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643476"
---
# <a name="how-to-create-a-channel-factory-and-use-it-to-create-and-manage-channels"></a><span data-ttu-id="0ce3f-103">方法: チャネル ファクトリを作成および使用して、チャネルを作成および管理する</span><span class="sxs-lookup"><span data-stu-id="0ce3f-103">How to: Create a Channel Factory and Use it to Create and Manage Channels</span></span>

<span data-ttu-id="0ce3f-104"><xref:System.ServiceModel.DuplexChannelFactory%601> クラスは、クライアントがサービス エンドポイントとの間でメッセージを送受信するために使用する、さまざまな種類の双方向チャネルを作成したり、管理したりする手段を提供します。</span><span class="sxs-lookup"><span data-stu-id="0ce3f-104">The <xref:System.ServiceModel.DuplexChannelFactory%601> class provides the means to create and manage duplex channels of different types that clients use to send and receive messages to and from service endpoints.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ce3f-105">例</span><span class="sxs-lookup"><span data-stu-id="0ce3f-105">Example</span></span>  

 <span data-ttu-id="0ce3f-106">次のコードは、チャネル ファクトリを作成および使用して、チャネルを作成および管理する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="0ce3f-106">The following code shows how to create a channel factory and use it to create and manage channels.</span></span>  
  
 [!code-csharp[S_CustomAuthentication#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_customauthentication/cs/instance.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="0ce3f-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="0ce3f-107">See also</span></span>

- <xref:System.ServiceModel.DuplexChannelFactory%601>
