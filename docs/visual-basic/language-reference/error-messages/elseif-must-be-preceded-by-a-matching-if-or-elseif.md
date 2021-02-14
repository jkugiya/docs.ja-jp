---
description: "詳細情報: BC30014: '#ElseIf' の前には、対応する '#If' または '#ElseIf' が必要です"
title: "'#Else' の前には、対応する '#If' または '#ElseIf' が必要です。"
ms.date: 07/20/2015
f1_keywords:
- vbc30014
- bc30014
helpviewer_keywords:
- BC30014
ms.assetid: 5215585e-2efa-485a-9efe-9833a1cc83a0
ms.openlocfilehash: 5eeb9c2fc0fd7267d95a8713a7071cd08788e48b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796562"
---
# <a name="bc30014-elseif-must-be-preceded-by-a-matching-if-or-elseif"></a><span data-ttu-id="15241-103">BC30014: '#ElseIf' の前には、対応する '#If' または '#ElseIf' が必要です</span><span class="sxs-lookup"><span data-stu-id="15241-103">BC30014: '#ElseIf' must be preceded by a matching '#If' or '#ElseIf'</span></span>

<span data-ttu-id="15241-104">`#ElseIf` は条件付きコンパイル ディレクティブです。</span><span class="sxs-lookup"><span data-stu-id="15241-104">`#ElseIf` is a conditional compilation directive.</span></span> <span data-ttu-id="15241-105">`#If` または `#ElseIf` 句の前には、対応する `#ElseIf` が必要です。</span><span class="sxs-lookup"><span data-stu-id="15241-105">An `#ElseIf` clause must be preceded by a matching `#If` or `#ElseIf` clause.</span></span>

 <span data-ttu-id="15241-106">**エラー ID:** BC30014</span><span class="sxs-lookup"><span data-stu-id="15241-106">**Error ID:** BC30014</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="15241-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="15241-107">To correct this error</span></span>

1. <span data-ttu-id="15241-108">先行する `#If` または `#ElseIf` が、中間の条件付きコンパイル ブロックまたは正しくない位置にある `#ElseIf` によって、この `#End If` と分離されていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="15241-108">Check that a preceding `#If` or `#ElseIf` has not been separated from this `#ElseIf` by an intervening conditional compilation block or an incorrectly placed `#End If`.</span></span>

2. <span data-ttu-id="15241-109">`#ElseIf` の前に `#Else` ディレクティブがある場合は、`#Else` を削除するか、`#ElseIf` に変更します。</span><span class="sxs-lookup"><span data-stu-id="15241-109">If the `#ElseIf` is preceded by a `#Else` directive, either remove the `#Else` or change it to an `#ElseIf`.</span></span>

3. <span data-ttu-id="15241-110">他のすべての順序が正しい場合、 `#If` ディレクティブを条件付きコンパイル ブロックの先頭に追加します。</span><span class="sxs-lookup"><span data-stu-id="15241-110">If everything else is in order, add an `#If` directive to the beginning of the conditional compilation block.</span></span>

## <a name="see-also"></a><span data-ttu-id="15241-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="15241-111">See also</span></span>

- [<span data-ttu-id="15241-112">#If...Then...#Else ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="15241-112">#If...Then...#Else Directives</span></span>](../directives/if-then-else-directives.md)
