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
# <a name="disable-and-enable-directives-visual-basic"></a>#Disable および #Enable ディレクティブ (Visual Basic)

`#Disable` および `#Enable` ディレクティブは Visual Basic ソース コード コンパイラ ディレクティブです。 これらは、コードの領域に対してすべてまたは特定の警告を無効にしたり、再度有効にするために使用されます。

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

警告コードのコンマ区切りリストを無効および有効にすることもできます。

## <a name="see-also"></a>関連項目

- [Visual Basic の言語リファレンス](../index.md)
- [コード分析の警告を抑制する方法](../../../fundamentals/code-analysis/suppress-warnings.md)
