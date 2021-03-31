---
description: '詳細情報: finally ブロックを使用する方法'
title: '方法: finally ブロックを使用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, try/catch blocks
- exceptions, finally blocks
- try/catch blocks
- finally blocks
- ArgumentOutOfRangeException class
ms.assetid: 4b9c0137-04af-4468-91d1-b9014df8ddd2
ms.openlocfilehash: 0c296e5cba8e3f4f50005a6178886a116f6e7bac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99629605"
---
# <a name="how-to-use-finally-blocks"></a><span data-ttu-id="e62da-103">finally ブロックを使用する方法</span><span class="sxs-lookup"><span data-stu-id="e62da-103">How to use finally blocks</span></span>

<span data-ttu-id="e62da-104">例外が発生すると、実行が停止され、コントロールが適切な例外ハンドラーに付与されます。</span><span class="sxs-lookup"><span data-stu-id="e62da-104">When an exception occurs, execution stops and control is given to the appropriate exception handler.</span></span> <span data-ttu-id="e62da-105">これは、多くの場合、実行されるはずのコード行がバイパスされることを意味します。</span><span class="sxs-lookup"><span data-stu-id="e62da-105">This often means that lines of code you expect to be executed are bypassed.</span></span> <span data-ttu-id="e62da-106">ファイルを閉じるなどのいくつかのリソースのクリーンアップは、例外がスローされた場合でも実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e62da-106">Some resource cleanup, such as closing a file, needs to be done even if an exception is thrown.</span></span> <span data-ttu-id="e62da-107">これを行うために、`finally` ブロックを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="e62da-107">To do this, you can use a `finally` block.</span></span> <span data-ttu-id="e62da-108">`finally` ブロックは、例外がスローされるかどうかに関係なく、常に実行されます。</span><span class="sxs-lookup"><span data-stu-id="e62da-108">A `finally` block always executes, regardless of whether an exception is thrown.</span></span>

<span data-ttu-id="e62da-109">次のコード例では、`try`/`catch` ブロックを使用して <xref:System.ArgumentOutOfRangeException> をキャッチします。</span><span class="sxs-lookup"><span data-stu-id="e62da-109">The following code example uses a `try`/`catch` block to catch an <xref:System.ArgumentOutOfRangeException>.</span></span> <span data-ttu-id="e62da-110">`Main` メソッドは 2 つの配列を作成し、一方の配列をもう一方にコピーすることを試みます。</span><span class="sxs-lookup"><span data-stu-id="e62da-110">The `Main` method creates two arrays and attempts to copy one to the other.</span></span> <span data-ttu-id="e62da-111">アクションが、<xref:System.ArgumentOutOfRangeException> を生成し、エラーは、コンソールに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="e62da-111">The action generates an <xref:System.ArgumentOutOfRangeException> and the error is written to the console.</span></span> <span data-ttu-id="e62da-112">`finally` ブロックは、コピー操作の結果に関係なく実行されます。</span><span class="sxs-lookup"><span data-stu-id="e62da-112">The `finally` block executes regardless of the outcome of the copy action.</span></span>

[!code-cpp[CodeTryCatchFinallyExample#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CPP/source2.cpp#3)]
[!code-csharp[CodeTryCatchFinallyExample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CS/source2.cs#3)]
[!code-vb[CodeTryCatchFinallyExample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeTryCatchFinallyExample/VB/source2.vb#3)]  

## <a name="see-also"></a><span data-ttu-id="e62da-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="e62da-113">See also</span></span>

- [<span data-ttu-id="e62da-114">例外</span><span class="sxs-lookup"><span data-stu-id="e62da-114">Exceptions</span></span>](index.md)
