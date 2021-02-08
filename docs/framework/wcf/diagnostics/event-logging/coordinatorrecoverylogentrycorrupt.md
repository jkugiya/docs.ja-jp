---
description: '詳細情報: CoordinatorRecoveryLogEntryCorrupt'
title: CoordinatorRecoveryLogEntryCorrupt
ms.date: 03/30/2017
ms.assetid: 3cd0c3e3-84c8-4d43-a561-a8851c78e565
ms.openlocfilehash: 3a848c634a226b34023a24898f9827162b4dafc7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99771341"
---
# <a name="coordinatorrecoverylogentrycorrupt"></a><span data-ttu-id="df9fe-103">CoordinatorRecoveryLogEntryCorrupt</span><span class="sxs-lookup"><span data-stu-id="df9fe-103">CoordinatorRecoveryLogEntryCorrupt</span></span>

<span data-ttu-id="df9fe-104">Id: 139</span><span class="sxs-lookup"><span data-stu-id="df9fe-104">Id: 139</span></span>  
  
 <span data-ttu-id="df9fe-105">重大度 : エラー</span><span class="sxs-lookup"><span data-stu-id="df9fe-105">Severity: Error</span></span>  
  
 <span data-ttu-id="df9fe-106">カテゴリ : TransactionBridge</span><span class="sxs-lookup"><span data-stu-id="df9fe-106">Category: TransactionBridge</span></span>  
  
## <a name="description"></a><span data-ttu-id="df9fe-107">説明</span><span class="sxs-lookup"><span data-stu-id="df9fe-107">Description</span></span>  

 <span data-ttu-id="df9fe-108">このイベントは、コーディネーターの回復ログ エントリが破損し、逆シリアル化できなかったことを示します。</span><span class="sxs-lookup"><span data-stu-id="df9fe-108">This event indicates that a  coordinator recovery log entry was corrupt and could not be deserialized.</span></span> <span data-ttu-id="df9fe-109">このエラーが原因で、データの損失が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="df9fe-109">Data loss may result from this error.</span></span> <span data-ttu-id="df9fe-110">イベントには、トランザクション ID、回復データ (Base64 エンコード)、例外、プロセス名、およびプロセス ID が表示されます。</span><span class="sxs-lookup"><span data-stu-id="df9fe-110">The event lists the Transaction ID, Recovery data (Base64 encoded), exception, process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df9fe-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="df9fe-111">See also</span></span>

- [<span data-ttu-id="df9fe-112">イベント ログ</span><span class="sxs-lookup"><span data-stu-id="df9fe-112">Event Logging</span></span>](index.md)
- [<span data-ttu-id="df9fe-113">イベント一覧</span><span class="sxs-lookup"><span data-stu-id="df9fe-113">Events General Reference</span></span>](events-general-reference.md)
