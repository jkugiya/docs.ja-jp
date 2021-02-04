---
title: Enable および Disable ディレクティブ
ms.date: 01/28/2021
helpviewer_keywords:
- directives, enable
- directives, disable
- disable directive
ms.openlocfilehash: 3104b25c903465f3a650304f477b25a74591c8ba
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2021
ms.locfileid: "99217272"
---
# <a name="disable-and-enable-directives-visual-basic"></a><span data-ttu-id="6b640-102">#Disable および #Enable ディレクティブ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6b640-102">#Disable and #Enable directives (Visual Basic)</span></span>

<span data-ttu-id="6b640-103">`#Disable` および `#Enable` ディレクティブは Visual Basic ソース コード コンパイラ ディレクティブです。</span><span class="sxs-lookup"><span data-stu-id="6b640-103">The `#Disable` and `#Enable` directives are Visual Basic source code compiler directives.</span></span> <span data-ttu-id="6b640-104">これらは、コードの領域に対して特定の警告を無効にしたり、再度有効にするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="6b640-104">They are used to disable and re-enable specific warnings for regions of code.</span></span>

```vb
' Suppress warning about no awaits in this method.
#Disable Warning BC42356
    Async Function TestAsync() As Task
        Console.WriteLine("testing")
    End Function
#Enable Warning BC42356
```

<span data-ttu-id="6b640-105">警告コードのコンマ区切りリストを無効および有効にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="6b640-105">You can also disable and enable a comma-separated list of warning codes.</span></span>

## <a name="see-also"></a><span data-ttu-id="6b640-106">関連項目</span><span class="sxs-lookup"><span data-stu-id="6b640-106">See also</span></span>

- [<span data-ttu-id="6b640-107">Visual Basic の言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="6b640-107">Visual Basic Language Reference</span></span>](../index.md)
- [<span data-ttu-id="6b640-108">コード分析の警告を抑制する方法</span><span class="sxs-lookup"><span data-stu-id="6b640-108">How to suppress code analysis warnings</span></span>](../../../fundamentals/code-analysis/suppress-warnings.md)
