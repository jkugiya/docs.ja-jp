---
description: '詳細については、次を参照してください: System.servicemodel. ConnectionPoolCloseException'
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.date: 03/30/2017
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
ms.openlocfilehash: a65739cc872f3cd175d76e9113380f9f4185d498
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99644633"
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a><span data-ttu-id="9994a-103">System.ServiceModel.Channels.ConnectionPoolCloseException</span><span class="sxs-lookup"><span data-stu-id="9994a-103">System.ServiceModel.Channels.ConnectionPoolCloseException</span></span>

<span data-ttu-id="9994a-104">この接続プールの接続を閉じている間に例外が発生しました。</span><span class="sxs-lookup"><span data-stu-id="9994a-104">An exception occurred while closing the connections in this connection pool.</span></span>  
  
## <a name="description"></a><span data-ttu-id="9994a-105">説明</span><span class="sxs-lookup"><span data-stu-id="9994a-105">Description</span></span>  

 <span data-ttu-id="9994a-106">このエラーレベルのトレースは、Windows Communication Foundation (WCF) の接続プール機能によって使用される接続プールを閉じるときにエラーが発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="9994a-106">This error level trace indicates that an error has occurred while closing the connection pools used by Windows Communication Foundation (WCF)’s connection pooling feature.</span></span> <span data-ttu-id="9994a-107">このエラーの原因としては、プールされた接続を閉じることに失敗した、またはプールされた接続で CloseTimeout が設定されていることが考えられます。</span><span class="sxs-lookup"><span data-stu-id="9994a-107">One possible reason for this is an unsuccessful closure of a pooled connection, or a set of pooled connections within the CloseTimeout.</span></span> <span data-ttu-id="9994a-108">この例外がスローされると、このプール内でまだ閉じられていない接続はすべて中断され、他のプールにある閉じられていない接続は破棄されます。</span><span class="sxs-lookup"><span data-stu-id="9994a-108">When this exception is thrown, any remaining unclosed connections within that pool are aborted; unclosed connections within other pools are abandoned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9994a-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="9994a-109">See also</span></span>

- [<span data-ttu-id="9994a-110">トレース</span><span class="sxs-lookup"><span data-stu-id="9994a-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="9994a-111">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="9994a-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="9994a-112">管理と診断</span><span class="sxs-lookup"><span data-stu-id="9994a-112">Administration and Diagnostics</span></span>](../index.md)
