---
description: '詳細情報: #Disable および #Enable ディレクティブ (Visual Basic)'
title: Enable および Disable ディレクティブ
ms.date: 01/28/2021
helpviewer_keywords:
- directives, enable
- directives, disable
- disable directive
ms.openlocfilehash: d600cc959639a3f70bca5678fbc81aae0806c9cc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797264"
---
# <a name="disable-and-enable-directives-visual-basic"></a><span data-ttu-id="8ec6a-103">#Disable および #Enable ディレクティブ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8ec6a-103">#Disable and #Enable directives (Visual Basic)</span></span>

<span data-ttu-id="8ec6a-104">`#Disable` および `#Enable` ディレクティブは Visual Basic ソース コード コンパイラ ディレクティブです。</span><span class="sxs-lookup"><span data-stu-id="8ec6a-104">The `#Disable` and `#Enable` directives are Visual Basic source code compiler directives.</span></span> <span data-ttu-id="8ec6a-105">これらは、コードの領域に対して特定の警告を無効にしたり、再度有効にするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="8ec6a-105">They are used to disable and re-enable specific warnings for regions of code.</span></span>

```vb
' Suppress warning about no awaits in this method.
#Disable Warning BC42356
    Async Function TestAsync() As Task
        Console.WriteLine("testing")
    End Function
#Enable Warning BC42356
```

<span data-ttu-id="8ec6a-106">警告コードのコンマ区切りリストを無効および有効にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="8ec6a-106">You can also disable and enable a comma-separated list of warning codes.</span></span>

## <a name="see-also"></a><span data-ttu-id="8ec6a-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="8ec6a-107">See also</span></span>

- [<span data-ttu-id="8ec6a-108">Visual Basic の言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="8ec6a-108">Visual Basic Language Reference</span></span>](../index.md)
- [<span data-ttu-id="8ec6a-109">コード分析の警告を抑制する方法</span><span class="sxs-lookup"><span data-stu-id="8ec6a-109">How to suppress code analysis warnings</span></span>](../../../fundamentals/code-analysis/suppress-warnings.md)
