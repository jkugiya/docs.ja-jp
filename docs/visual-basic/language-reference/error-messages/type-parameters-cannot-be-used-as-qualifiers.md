---
description: '詳細情報: BC32098:型パラメーターは修飾子として使用できません。'
title: 型パラメーターは修飾子として使用できません。
ms.date: 07/20/2015
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords:
- BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
ms.openlocfilehash: 61be8e81c9cf6c7a8339c7bbf0ad9566f582eb57
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675053"
---
# <a name="bc32098-type-parameters-cannot-be-used-as-qualifiers"></a><span data-ttu-id="9dd9e-103">BC32098:型パラメーターは修飾子として使用できません。</span><span class="sxs-lookup"><span data-stu-id="9dd9e-103">BC32098: Type parameters cannot be used as qualifiers</span></span>

<span data-ttu-id="9dd9e-104">プログラミング要素は、型パラメーターを含む修飾文字列で修飾されます。</span><span class="sxs-lookup"><span data-stu-id="9dd9e-104">A programming element is qualified with a qualification string that includes a type parameter.</span></span>

<span data-ttu-id="9dd9e-105">型パラメーターは、ジェネリック型が構築されるときに指定される型の要件を表します。</span><span class="sxs-lookup"><span data-stu-id="9dd9e-105">A type parameter represents a requirement for a type that is to be supplied when the generic type is constructed.</span></span> <span data-ttu-id="9dd9e-106">これは定義されている特定の型を表していません。</span><span class="sxs-lookup"><span data-stu-id="9dd9e-106">It does not represent a specific defined type.</span></span> <span data-ttu-id="9dd9e-107">修飾文字列には、コンパイル時に定義された要素のみを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="9dd9e-107">A qualification string must include only elements that are defined at compile time.</span></span>

<span data-ttu-id="9dd9e-108">次のコードでは、このエラーが生成される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9dd9e-108">The following code can generate this error:</span></span>

```vb
Public Function CheckText(Of c As System.Windows.Forms.Control)(
    badText As String) As Boolean

    Dim saveText As c.Text
    ' Insert code to look for badText within saveText.
End Function
```

 <span data-ttu-id="9dd9e-109">**エラー ID:** BC32098</span><span class="sxs-lookup"><span data-stu-id="9dd9e-109">**Error ID:** BC32098</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="9dd9e-110">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="9dd9e-110">To correct this error</span></span>

1. <span data-ttu-id="9dd9e-111">修飾文字列から型パラメーターを削除するか、それを定義済みの型で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="9dd9e-111">Remove the type parameter from the qualification string, or replace it with a defined type.</span></span>

2. <span data-ttu-id="9dd9e-112">構築された型を使用して、修飾するプログラミング要素を見つける必要がある場合は、追加のプログラム ロジックを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9dd9e-112">If you need to use a constructed type to locate the programming element being qualified, you must use additional program logic.</span></span>

## <a name="see-also"></a><span data-ttu-id="9dd9e-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="9dd9e-113">See also</span></span>

- [<span data-ttu-id="9dd9e-114">宣言された要素の参照</span><span class="sxs-lookup"><span data-stu-id="9dd9e-114">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="9dd9e-115">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9dd9e-115">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="9dd9e-116">型リスト</span><span class="sxs-lookup"><span data-stu-id="9dd9e-116">Type List</span></span>](../statements/type-list.md)
