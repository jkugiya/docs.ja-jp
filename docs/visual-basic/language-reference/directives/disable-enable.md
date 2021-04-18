---
description: '詳細情報: #Disable および #Enable ディレクティブ (Visual Basic)'
title: Enable および Disable ディレクティブ
ms.date: 01/28/2021
helpviewer_keywords:
- directives, enable
- directives, disable
- disable directive
ms.openlocfilehash: 14f8fbd0ac49829f99643d3eb0ac3149ddd9d647
ms.sourcegitcommit: aab60b21144bf04b3057b5d59aa7c58edaef32d1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2021
ms.locfileid: "107494780"
---
# <a name="disable-and-enable-directives-visual-basic"></a><span data-ttu-id="8213a-103">#Disable および #Enable ディレクティブ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8213a-103">#Disable and #Enable directives (Visual Basic)</span></span>

<span data-ttu-id="8213a-104">`#Disable` および `#Enable` ディレクティブは Visual Basic ソース コード コンパイラ ディレクティブです。</span><span class="sxs-lookup"><span data-stu-id="8213a-104">The `#Disable` and `#Enable` directives are Visual Basic source code compiler directives.</span></span> <span data-ttu-id="8213a-105">これらは、コードの領域に対してすべてまたは特定の警告を無効にしたり、再度有効にするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="8213a-105">They are used to disable and re-enable all or specific warnings for regions of code.</span></span>

```vb
    Dim variable1    'warning BC42024: Unused local variable: 'variable1'.
#Disable Warning
    Dim variable2    'no warning
#Enable Warning 
    Dim variable3    'warning BC42024: Unused local variable: 'variable3'.
```

```vb
' Suppress warning about no awaits in this method.
#Disable Warning BC42356
    Async Function TestAsync() As Task
        Console.WriteLine("testing")
    End Function
#Enable Warning BC42356
```

<span data-ttu-id="8213a-106">警告コードのコンマ区切りリストを無効および有効にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="8213a-106">You can also disable and enable a comma-separated list of warning codes.</span></span>

## <a name="see-also"></a><span data-ttu-id="8213a-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="8213a-107">See also</span></span>

- [<span data-ttu-id="8213a-108">Visual Basic の言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="8213a-108">Visual Basic Language Reference</span></span>](../index.md)
- [<span data-ttu-id="8213a-109">コード分析の警告を抑制する方法</span><span class="sxs-lookup"><span data-stu-id="8213a-109">How to suppress code analysis warnings</span></span>](../../../fundamentals/code-analysis/suppress-warnings.md)
