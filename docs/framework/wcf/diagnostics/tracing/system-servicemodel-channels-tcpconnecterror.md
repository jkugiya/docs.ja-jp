---
description: '詳細情報: System.ServiceModel.Channels.TcpConnectError'
title: System.ServiceModel.Channels.TcpConnectError
ms.date: 03/30/2017
ms.assetid: 22d93797-072e-405d-a3e0-5c519ddf290b
ms.openlocfilehash: e8c8e682100080e8622d0371505c9f3b9ddb84d0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99634389"
---
# <a name="systemservicemodelchannelstcpconnecterror"></a><span data-ttu-id="d0a08-103">System.ServiceModel.Channels.TcpConnectError</span><span class="sxs-lookup"><span data-stu-id="d0a08-103">System.ServiceModel.Channels.TcpConnectError</span></span>

<span data-ttu-id="d0a08-104">TCP 接続の操作に失敗しました。</span><span class="sxs-lookup"><span data-stu-id="d0a08-104">The TCP connect operation failed.</span></span>  
  
## <a name="description"></a><span data-ttu-id="d0a08-105">説明</span><span class="sxs-lookup"><span data-stu-id="d0a08-105">Description</span></span>  

 <span data-ttu-id="d0a08-106">この警告レベルのトレースは、TCP エンドポイントへの接続に失敗したことを示しています。</span><span class="sxs-lookup"><span data-stu-id="d0a08-106">This warning level trace indicates a failure to connect to a TCP endpoint.</span></span> <span data-ttu-id="d0a08-107">これは、リモート エンドポイントが指定された IP アドレスとポートで応答していない場合に発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="d0a08-107">This could happen if the remote endpoint is not responding at a given IP address and port.</span></span> <span data-ttu-id="d0a08-108">別の有効な IP アドレス (IPv4 アドレスや IPv6 アドレス、または指定のホスト名を表す別の IP アドレスなど) への後続する接続試行が成功した場合、このトレースは無視できます。</span><span class="sxs-lookup"><span data-stu-id="d0a08-108">This trace can be ignored if subsequent attempts to connect to other valid IP addresses (such as IPv4 or IPv6 addresses, or other IP addresses representing a given hostname) succeed.</span></span> <span data-ttu-id="d0a08-109">このトレースに含まれる例外により、エラーに関する追加情報が公開されることがあります。</span><span class="sxs-lookup"><span data-stu-id="d0a08-109">The exception within this trace can reveal additional information about the error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0a08-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="d0a08-110">See also</span></span>

- [<span data-ttu-id="d0a08-111">トレース</span><span class="sxs-lookup"><span data-stu-id="d0a08-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="d0a08-112">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="d0a08-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="d0a08-113">管理と診断</span><span class="sxs-lookup"><span data-stu-id="d0a08-113">Administration and Diagnostics</span></span>](../index.md)
