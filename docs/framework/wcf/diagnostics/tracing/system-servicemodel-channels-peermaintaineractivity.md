---
description: 詳細については、「PeerMaintainerActivity」を参照してください。
title: System.ServiceModel.Channels.PeerMaintainerActivity
ms.date: 03/30/2017
ms.assetid: ef28d086-d7fb-4e81-82e9-45a54647783b
ms.openlocfilehash: da4e4cf87da808cb6779445b6507b51d098132b3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780882"
---
# <a name="systemservicemodelchannelspeermaintaineractivity"></a><span data-ttu-id="382ac-103">System.ServiceModel.Channels.PeerMaintainerActivity</span><span class="sxs-lookup"><span data-stu-id="382ac-103">System.ServiceModel.Channels.PeerMaintainerActivity</span></span>

<span data-ttu-id="382ac-104">PeerMaintainer モジュールは、特定の操作を実行しています (詳細はトレース メッセージの本文に含まれています)。</span><span class="sxs-lookup"><span data-stu-id="382ac-104">The PeerMaintainer module is performing a specific operation (details contained within the trace message body).</span></span>  
  
## <a name="description"></a><span data-ttu-id="382ac-105">説明</span><span class="sxs-lookup"><span data-stu-id="382ac-105">Description</span></span>  

 <span data-ttu-id="382ac-106">このトレースは、各種の PeerMaintainer 操作中に行われます。</span><span class="sxs-lookup"><span data-stu-id="382ac-106">This trace occurs during various PeerMaintainer operations.</span></span>  
  
 <span data-ttu-id="382ac-107">PeerMaintainer は PeerNode の内部コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="382ac-107">PeerMaintainer is an internal component of PeerNode.</span></span> <span data-ttu-id="382ac-108">このコンポーネントは、毎分または 32 通のメッセージを受信するたびに近隣ノードに LinkUtility メッセージを送信します。このとき、交換されたメッセージ数と、有効な (重複および改ざんされていない) メッセージの数に関する統計が一緒に送信されます。</span><span class="sxs-lookup"><span data-stu-id="382ac-108">Every minute, or every 32 messages received, it sends a LinkUtility message to its neighbors with statistics about how many messages are exchanged and how many are useful (non-duplicates, untampered).</span></span> <span data-ttu-id="382ac-109">これは、特定の近隣ノードのリンク ユーティリティの特定に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="382ac-109">This helps determine a particular neighbor's Link Utility.</span></span> <span data-ttu-id="382ac-110">約 5 分ごとに、保守管理者は近隣ノードの接続が正常かどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="382ac-110">Approximately every five minutes, the maintainer checks the health of neighbor connections.</span></span> <span data-ttu-id="382ac-111">近隣ノードへの接続数が適切な数を超えている場合、保守管理者は使用頻度が最も少ない接続を削除します。</span><span class="sxs-lookup"><span data-stu-id="382ac-111">If the number of neighbor connections exceeds the ideal amount, the maintainer prunes off the least useful connections.</span></span> <span data-ttu-id="382ac-112">接続数が十分でなければ、保守管理者は新しい接続を取得します。</span><span class="sxs-lookup"><span data-stu-id="382ac-112">If there are not enough connections, the maintainer acquires new connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="382ac-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="382ac-113">See also</span></span>

- [<span data-ttu-id="382ac-114">トレース</span><span class="sxs-lookup"><span data-stu-id="382ac-114">Tracing</span></span>](index.md)
- [<span data-ttu-id="382ac-115">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="382ac-115">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="382ac-116">管理と診断</span><span class="sxs-lookup"><span data-stu-id="382ac-116">Administration and Diagnostics</span></span>](../index.md)
