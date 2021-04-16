---
description: '詳細情報: Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorResponseInvalidMetadata'
title: Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorResponseInvalidMetadata
ms.date: 03/30/2017
ms.assetid: a174bbf5-0ffe-4fda-969d-e7fbd1996123
ms.openlocfilehash: 2eeb5955f2d0bf3afd01ebfc7474cbccbcb70980
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99635689"
---
# <a name="microsofttransactionstransactionbridgeregistrationcoordinatorresponseinvalidmetadata"></a><span data-ttu-id="b9a24-103">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorResponseInvalidMetadata</span><span class="sxs-lookup"><span data-stu-id="b9a24-103">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorResponseInvalidMetadata</span></span>

<span data-ttu-id="b9a24-104">WS-AtomicTransaction プロトコル サービスは、無効または互換性のないメタデータのあるエンドポイント参照を含むそのコーディネーターから、RegisterResponse メッセージを受信しました。</span><span class="sxs-lookup"><span data-stu-id="b9a24-104">The WS-Atomic Transaction protocol service received a RegisterResponse message from its coordinator that contains an endpoint reference with invalid or incompatible metadata.</span></span>  
  
## <a name="description"></a><span data-ttu-id="b9a24-105">説明</span><span class="sxs-lookup"><span data-stu-id="b9a24-105">Description</span></span>  

 <span data-ttu-id="b9a24-106">ローカルのトランザクション マネージャーが、その上位のトランザクション マネージャーに登録を試み、上位のトランザクション マネージャーが、RegisterResponse メッセージ内の無効なアドレスを返すときにトレースされます。</span><span class="sxs-lookup"><span data-stu-id="b9a24-106">Traced when the local Transaction Manager tries to register with its superior Transaction Manager and the superior returns an invalid address within the RegisterResponse message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9a24-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="b9a24-107">See also</span></span>

- [<span data-ttu-id="b9a24-108">トレース</span><span class="sxs-lookup"><span data-stu-id="b9a24-108">Tracing</span></span>](index.md)
- [<span data-ttu-id="b9a24-109">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="b9a24-109">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="b9a24-110">管理と診断</span><span class="sxs-lookup"><span data-stu-id="b9a24-110">Administration and Diagnostics</span></span>](../index.md)
