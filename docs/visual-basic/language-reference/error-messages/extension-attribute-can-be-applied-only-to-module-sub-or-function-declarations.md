---
description: "詳細情報: BC36550:'Extension' 属性は 'Module'、'Sub'、または 'Function' の各宣言にのみ適用できます"
title: "'Extension' 属性は 'Module'、'Sub'、または 'Function' の各宣言にのみ適用できます"
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: f0c87de34238974229bc572a0f634a16e8cc78d9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796315"
---
# <a name="bc36550-extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations"></a><span data-ttu-id="d6ae2-103">BC36550:'Extension' 属性は 'Module'、'Sub'、または 'Function' の各宣言にのみ適用できます</span><span class="sxs-lookup"><span data-stu-id="d6ae2-103">BC36550: 'Extension' attribute can be applied only to 'Module', 'Sub', or 'Function' declarations</span></span>

<span data-ttu-id="d6ae2-104">Visual Basic でデータ型を拡張する唯一の方法は、標準モジュール内で拡張メソッドを定義することです。</span><span class="sxs-lookup"><span data-stu-id="d6ae2-104">The only way to extend a data type in Visual Basic is to define an extension method inside a standard module.</span></span> <span data-ttu-id="d6ae2-105">拡張メソッドになるのは、`Sub` プロシージャまたは `Function` プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="d6ae2-105">The extension method can be a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="d6ae2-106">すべての拡張メソッドは、<xref:System.Runtime.CompilerServices?displayProperty=nameWithType> 名前空間の拡張属性 `<Extension()>` でマークする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d6ae2-106">All extension methods must be marked with the extension attribute, `<Extension()>`, from the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="d6ae2-107">必要に応じて、拡張メソッドを含むモジュールを同じ方法でマークすることもできます。</span><span class="sxs-lookup"><span data-stu-id="d6ae2-107">Optionally, a module that contains an extension method may be marked in the same way.</span></span> <span data-ttu-id="d6ae2-108">その他の拡張属性の使用は有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="d6ae2-108">No other use of the extension attribute is valid.</span></span>

<span data-ttu-id="d6ae2-109">**エラー ID:** BC36550</span><span class="sxs-lookup"><span data-stu-id="d6ae2-109">**Error ID:** BC36550</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="d6ae2-110">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="d6ae2-110">To correct this error</span></span>

- <span data-ttu-id="d6ae2-111">拡張属性を削除します。</span><span class="sxs-lookup"><span data-stu-id="d6ae2-111">Remove the extension attribute.</span></span>

- <span data-ttu-id="d6ae2-112">それを囲むモジュールに定義されているメソッドとして拡張機能を再設計します。</span><span class="sxs-lookup"><span data-stu-id="d6ae2-112">Redesign your extension as a method, defined in an enclosing module.</span></span>

## <a name="example"></a><span data-ttu-id="d6ae2-113">例</span><span class="sxs-lookup"><span data-stu-id="d6ae2-113">Example</span></span>

<span data-ttu-id="d6ae2-114">`String` データ型の `Print` メソッドを定義する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d6ae2-114">The following example defines a `Print` method for the `String` data type.</span></span>

```vb
Imports StringUtility
Imports System.Runtime.CompilerServices
Namespace StringUtility
    <Extension()>
    Module StringExtensions
        <Extension()>
        Public Sub Print (ByVal str As String)
            Console.WriteLine(str)
        End Sub
    End Module
End Namespace
```

## <a name="see-also"></a><span data-ttu-id="d6ae2-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="d6ae2-115">See also</span></span>

- [<span data-ttu-id="d6ae2-116">属性の概要</span><span class="sxs-lookup"><span data-stu-id="d6ae2-116">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="d6ae2-117">拡張メソッド</span><span class="sxs-lookup"><span data-stu-id="d6ae2-117">Extension Methods</span></span>](../../programming-guide/language-features/procedures/extension-methods.md)
- [<span data-ttu-id="d6ae2-118">Module ステートメント</span><span class="sxs-lookup"><span data-stu-id="d6ae2-118">Module Statement</span></span>](../statements/module-statement.md)
