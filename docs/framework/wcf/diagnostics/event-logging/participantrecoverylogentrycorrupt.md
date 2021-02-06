---
description: '詳細情報: ParticipantRecoveryLogEntryCorrupt'
title: ParticipantRecoveryLogEntryCorrupt
ms.date: 03/30/2017
ms.assetid: ab34785f-f953-4428-93ca-3c50d3f50a4a
ms.openlocfilehash: 974fbb543f1cdbcc196bf7fe6f83b738acbde6fa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99655891"
---
# <a name="participantrecoverylogentrycorrupt"></a><span data-ttu-id="9a36b-103">ParticipantRecoveryLogEntryCorrupt</span><span class="sxs-lookup"><span data-stu-id="9a36b-103">ParticipantRecoveryLogEntryCorrupt</span></span>

<span data-ttu-id="9a36b-104">Id: 138</span><span class="sxs-lookup"><span data-stu-id="9a36b-104">Id: 138</span></span>  
  
 <span data-ttu-id="9a36b-105">重大度 : エラー</span><span class="sxs-lookup"><span data-stu-id="9a36b-105">Severity: Error</span></span>  
  
 <span data-ttu-id="9a36b-106">カテゴリ : TransactionBridge</span><span class="sxs-lookup"><span data-stu-id="9a36b-106">Category: TransactionBridge</span></span>  
  
## <a name="description"></a><span data-ttu-id="9a36b-107">説明</span><span class="sxs-lookup"><span data-stu-id="9a36b-107">Description</span></span>  

 <span data-ttu-id="9a36b-108">このイベントは、参加要素の回復ログ エントリが破損し、逆シリアル化できなかったことを示します。</span><span class="sxs-lookup"><span data-stu-id="9a36b-108">This event indicates that a participant recovery log entry was corrupt and could not be deserialized.</span></span> <span data-ttu-id="9a36b-109">このエラーが原因で、データの損失が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="9a36b-109">Data loss may result from this error.</span></span> <span data-ttu-id="9a36b-110">イベントには、トランザクション ID、回復データ (Base64 エンコード)、例外、プロセス名、およびプロセス ID が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9a36b-110">The event lists the Transaction ID, Recovery data (Base64 encoded), exception, process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a36b-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="9a36b-111">See also</span></span>

- [<span data-ttu-id="9a36b-112">イベント ログ</span><span class="sxs-lookup"><span data-stu-id="9a36b-112">Event Logging</span></span>](index.md)
- [<span data-ttu-id="9a36b-113">イベント一覧</span><span class="sxs-lookup"><span data-stu-id="9a36b-113">Events General Reference</span></span>](events-general-reference.md)
