---
description: 詳細については、「TxFailedToNegotiateOleTx」を参照してください。
title: System.ServiceModel.TxFailedToNegotiateOleTx
ms.date: 03/30/2017
ms.assetid: 3f0f0b4b-a1ad-4704-8329-455daf54892d
ms.openlocfilehash: c7f18ef73ff9c09cc51ad3aa6c54c2bd672d0cc3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99735570"
---
# <a name="systemservicemodeltxfailedtonegotiateoletx"></a><span data-ttu-id="49131-103">System.ServiceModel.TxFailedToNegotiateOleTx</span><span class="sxs-lookup"><span data-stu-id="49131-103">System.ServiceModel.TxFailedToNegotiateOleTx</span></span>

<span data-ttu-id="49131-104">指定されたコーディネーション コンテキストのための OleTransactions プロトコル ネゴシエーションに失敗しました。</span><span class="sxs-lookup"><span data-stu-id="49131-104">The OleTransactions protocol negotiation failed to complete for the specified coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="49131-105">説明</span><span class="sxs-lookup"><span data-stu-id="49131-105">Description</span></span>  

 <span data-ttu-id="49131-106">OleTx 情報が添付された受信トランザクションがその OleTx 情報を使用できず、代わりに WS-AT 使用した場合にトレースされます。</span><span class="sxs-lookup"><span data-stu-id="49131-106">Traced when an incoming transaction with OleTx information is unable to use the attached OleTx information, and will fall-back to using WS-AT instead.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="49131-107">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="49131-107">Troubleshooting</span></span>  

 <span data-ttu-id="49131-108">コンピューター間の MSDTC RPC 通信に潜在的な問題があることを示しています。</span><span class="sxs-lookup"><span data-stu-id="49131-108">Indicates a potential problem with MSDTC RPC communication between the machines.</span></span> <span data-ttu-id="49131-109">これらのトレースが多数ログに記録されている場合は、大幅なパフォーマンス低下が発生している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="49131-109">If many of these traces appear in the log, a drastic decrease in performance can result.</span></span>  <span data-ttu-id="49131-110">OleTx が必要ない場合は、WS-AT のレジストリ構成で `OleTxUpgradeEnabled` を 0 に設定してください。</span><span class="sxs-lookup"><span data-stu-id="49131-110">If OleTx is not desired, set `OleTxUpgradeEnabled` to 0 in the WS-AT registry configuration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49131-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="49131-111">See also</span></span>

- [<span data-ttu-id="49131-112">トレース</span><span class="sxs-lookup"><span data-stu-id="49131-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="49131-113">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="49131-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="49131-114">管理と診断</span><span class="sxs-lookup"><span data-stu-id="49131-114">Administration and Diagnostics</span></span>](../index.md)
