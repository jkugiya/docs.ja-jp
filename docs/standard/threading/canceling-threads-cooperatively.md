---
description: '詳細情報: スレッドの協調的な取り消し'
title: スレッドの協調的な取り消し
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- threads, cancellation
ms.assetid: d2d6d5fd-e263-4fa0-847b-2fc3e0d82337
ms.openlocfilehash: e166e95f3b7e000b4ea57cbd690de439b2883123
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675495"
---
# <a name="canceling-threads-cooperatively"></a><span data-ttu-id="f6082-103">スレッドの協調的な取り消し</span><span class="sxs-lookup"><span data-stu-id="f6082-103">Canceling threads cooperatively</span></span>

<span data-ttu-id="f6082-104">.NET Framework 4 より前のバージョンの .NET には、開始されたスレッドを協調的に取り消す手段は組み込まれていませんでした。</span><span class="sxs-lookup"><span data-stu-id="f6082-104">Prior to .NET Framework 4, .NET provided no built-in way to cancel a thread cooperatively after it was started.</span></span> <span data-ttu-id="f6082-105">ただし、.NET Framework 4 以降、<xref:System.Threading.Tasks.Task?displayProperty=nameWithType> オブジェクトや PLINQ クエリを取り消す場合と同様に、<xref:System.Threading.CancellationToken?displayProperty=nameWithType> を使用してスレッドを取り消すことができます。</span><span class="sxs-lookup"><span data-stu-id="f6082-105">However, starting with .NET Framework 4, you can use a <xref:System.Threading.CancellationToken?displayProperty=nameWithType> to cancel threads, just as you can use them to cancel <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects or PLINQ queries.</span></span> <span data-ttu-id="f6082-106"><xref:System.Threading.Thread?displayProperty=nameWithType> クラスにはキャンセル トークンのサポートは組み込まれていませんが、<xref:System.Threading.ParameterizedThreadStart> デリゲートを受け取る <xref:System.Threading.Thread> コンストラクターを使用して、トークンをスレッド プロシージャに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="f6082-106">Although the <xref:System.Threading.Thread?displayProperty=nameWithType> class does not offer built-in support for cancellation tokens, you can pass a token to a thread procedure by using the <xref:System.Threading.Thread> constructor that takes a <xref:System.Threading.ParameterizedThreadStart> delegate.</span></span> <span data-ttu-id="f6082-107">この方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="f6082-107">The following example demonstrates how to do this.</span></span>  
  
 [!code-csharp[Cancellation#14](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/CooperativeThreads.cs#14)]
 [!code-vb[Cancellation#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/CooperativeThreads.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="f6082-108">参照</span><span class="sxs-lookup"><span data-stu-id="f6082-108">See also</span></span>

- [<span data-ttu-id="f6082-109">スレッドの使用とスレッド処理</span><span class="sxs-lookup"><span data-stu-id="f6082-109">Using Threads and Threading</span></span>](using-threads-and-threading.md)
