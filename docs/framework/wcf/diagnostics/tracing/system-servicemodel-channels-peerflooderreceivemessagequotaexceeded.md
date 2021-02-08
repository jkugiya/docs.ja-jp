---
description: 詳細については、「PeerFlooderReceiveMessageQuotaExceeded」を参照してください。
title: System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded
ms.date: 03/30/2017
ms.assetid: b8371d0a-843e-440b-b86a-6996db131cb0
ms.openlocfilehash: 8ad164b253491f3a533c4828cd76f915eb5aed68
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780870"
---
# <a name="systemservicemodelchannelspeerflooderreceivemessagequotaexceeded"></a><span data-ttu-id="12657-103">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span><span class="sxs-lookup"><span data-stu-id="12657-103">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span></span>

<span data-ttu-id="12657-104">メッセージの受信速度が速すぎます。</span><span class="sxs-lookup"><span data-stu-id="12657-104">The inbound receive rate of messages is too high.</span></span>  
  
## <a name="description"></a><span data-ttu-id="12657-105">説明</span><span class="sxs-lookup"><span data-stu-id="12657-105">Description</span></span>  

 <span data-ttu-id="12657-106">このトレースは、受信メッセージの処理を試みたときに行われます。</span><span class="sxs-lookup"><span data-stu-id="12657-106">This trace occurs when attempting to process inbound messages.</span></span> <span data-ttu-id="12657-107">特定の近隣ノードでクォータ セットが超過しているため、メッセージをその近隣ノードに転送できません。</span><span class="sxs-lookup"><span data-stu-id="12657-107">A message could not be forwarded to a specific neighbor because the quota set for that neighbor has been exceeded.</span></span> <span data-ttu-id="12657-108">応答しない近隣ノードが、メッセージ保留のバックログをクリアできなかった場合にこの状態が発生します。</span><span class="sxs-lookup"><span data-stu-id="12657-108">This occurs when an unresponsive neighbor fails to clear a backlog of messages pending for that neighbor.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="12657-109">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="12657-109">Troubleshooting</span></span>  

 <span data-ttu-id="12657-110">メッシュ内でメッセージが送信される速度を遅くしてください。</span><span class="sxs-lookup"><span data-stu-id="12657-110">Reduce the rate at which messages are sent within the mesh.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12657-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="12657-111">See also</span></span>

- [<span data-ttu-id="12657-112">トレース</span><span class="sxs-lookup"><span data-stu-id="12657-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="12657-113">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="12657-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="12657-114">管理と診断</span><span class="sxs-lookup"><span data-stu-id="12657-114">Administration and Diagnostics</span></span>](../index.md)
