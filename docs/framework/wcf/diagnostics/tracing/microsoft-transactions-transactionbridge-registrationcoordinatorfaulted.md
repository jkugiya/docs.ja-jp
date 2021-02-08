---
description: 詳細については、RegistrationCoordinatorFaulted を参照してください。
title: Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFaulted
ms.date: 03/30/2017
ms.assetid: 8193027e-9db2-4af9-a072-27300cd24330
ms.openlocfilehash: aae2d5824f4205a05e98c7ef00d27c6a844e1566
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99770600"
---
# <a name="microsofttransactionstransactionbridgeregistrationcoordinatorfaulted"></a><span data-ttu-id="bf632-103">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFaulted</span><span class="sxs-lookup"><span data-stu-id="bf632-103">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFaulted</span></span>

<span data-ttu-id="bf632-104">WS-AT プロトコル サービスは、Register メッセージへの応答として、コーディネーターからエラーを受信しました。</span><span class="sxs-lookup"><span data-stu-id="bf632-104">The WS-AT protocol service received a fault from its coordinator in response to a Register message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="bf632-105">説明</span><span class="sxs-lookup"><span data-stu-id="bf632-105">Description</span></span>  

 <span data-ttu-id="bf632-106">エラーが返されたためにローカルの TransactionManager がその上位の TransactionManager に登録できない場合に、トレースされます。</span><span class="sxs-lookup"><span data-stu-id="bf632-106">Traced if the local TransactionManager is not able to Register with its superior TransactionManager due to a fault being returned.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="bf632-107">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="bf632-107">Troubleshooting</span></span>  

 <span data-ttu-id="bf632-108">トレース メッセージを調べて、返されたエラーを確認してください。</span><span class="sxs-lookup"><span data-stu-id="bf632-108">Inspect the trace message for the fault returned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf632-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="bf632-109">See also</span></span>

- [<span data-ttu-id="bf632-110">トレース</span><span class="sxs-lookup"><span data-stu-id="bf632-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="bf632-111">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="bf632-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="bf632-112">管理と診断</span><span class="sxs-lookup"><span data-stu-id="bf632-112">Administration and Diagnostics</span></span>](../index.md)
