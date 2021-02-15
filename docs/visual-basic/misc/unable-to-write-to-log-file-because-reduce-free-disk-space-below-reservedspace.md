---
description: '詳細情報: ログファイルへの書き込みにより、ReservedSpace 値未満の空きディスク領域が減少するため、ログファイルに書き込むことができません。'
title: 書き込みを行うと、空きディスク領域が ReservedSpace 値よりも少なくなるため、ログ ファイルに書き込めません
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_ReservedSpaceEncroached
ms.assetid: 95832e70-4ecc-47aa-90c1-f35c4d468151
ms.openlocfilehash: e02fa9527539169da3ea99f89246dafe82646cff
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100456953"
---
# <a name="unable-to-write-to-log-file-because-writing-to-it-would-reduce-free-disk-space-below-reservedspace-value"></a><span data-ttu-id="b552a-103">書き込みを行うと、空きディスク領域が ReservedSpace 値よりも少なくなるため、ログ ファイルに書き込めません</span><span class="sxs-lookup"><span data-stu-id="b552a-103">Unable to write to log file because writing to it would reduce free disk space below ReservedSpace value</span></span>

<span data-ttu-id="b552a-104">次の理由により、 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> クラスは、ログ ファイルに書き込むことができませんでした。</span><span class="sxs-lookup"><span data-stu-id="b552a-104">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not write to the log file because:</span></span>  
  
- <span data-ttu-id="b552a-105">ディスクの空き容量 (バイト単位) の量が <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> プロパティの値より小さい</span><span class="sxs-lookup"><span data-stu-id="b552a-105">The amount of free disk space (in bytes) is less than the value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> property</span></span>  
  
     <span data-ttu-id="b552a-106">- および -</span><span class="sxs-lookup"><span data-stu-id="b552a-106">—and—</span></span>  
  
- <span data-ttu-id="b552a-107"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> プロパティの値が <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>でした。</span><span class="sxs-lookup"><span data-stu-id="b552a-107">The value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> property was <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b552a-108">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="b552a-108">To correct this error</span></span>  
  
1. <span data-ttu-id="b552a-109">既存のログをアーカイブし、それらをコンピューターから削除して、 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> オブジェクトが新しいログを作成できるようにします。</span><span class="sxs-lookup"><span data-stu-id="b552a-109">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
2. <span data-ttu-id="b552a-110"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> プロパティの値を小さくしてディスク領域の予約を減らします。</span><span class="sxs-lookup"><span data-stu-id="b552a-110">Change the value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> property to a smaller number to reserve less disk space.</span></span>  
  
3. <span data-ttu-id="b552a-111"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> プロパティを <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> に設定して、十分な空きディスク領域がない場合に、警告なしでメッセージを破棄します。</span><span class="sxs-lookup"><span data-stu-id="b552a-111">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> property to <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> to discard messages without warning if there is not enough free disk space.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b552a-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="b552a-112">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>
- [<span data-ttu-id="b552a-113">.Log</span><span class="sxs-lookup"><span data-stu-id="b552a-113">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
- <span data-ttu-id="b552a-114">[[DirectoryPath]](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)</span><span class="sxs-lookup"><span data-stu-id="b552a-114">[My.Application.Info.DirectoryPath](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)</span></span>
