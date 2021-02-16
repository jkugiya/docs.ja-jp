---
description: '詳細情報: 方法: Visual Basic の StringBuilder を使用して文字列を作成する'
title: '方法: StringBuilder を使用して文字列を作成する'
ms.date: 07/20/2015
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
ms.openlocfilehash: 6def32517f71ec3c2a7795c3395e3e572903ce1e
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100429820"
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a><span data-ttu-id="e5d73-103">方法: Visual Basic の StringBuilder を使用して文字列を作成する</span><span class="sxs-lookup"><span data-stu-id="e5d73-103">How to: create strings using a StringBuilder in Visual Basic</span></span>

<span data-ttu-id="e5d73-104">この例では、<xref:System.Text.StringBuilder> クラスを使用して、多数の短い文字列から長い文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="e5d73-104">This example constructs a long string from many smaller strings using the <xref:System.Text.StringBuilder> class.</span></span> <span data-ttu-id="e5d73-105">多数の文字列を連結する場合、<xref:System.Text.StringBuilder> クラスは `&=` 演算子よりも効率的です。</span><span class="sxs-lookup"><span data-stu-id="e5d73-105">The <xref:System.Text.StringBuilder> class is more efficient than the `&=` operator for concatenating many strings.</span></span>

## <a name="example"></a><span data-ttu-id="e5d73-106">例</span><span class="sxs-lookup"><span data-stu-id="e5d73-106">Example</span></span>

<span data-ttu-id="e5d73-107">次の例では、<xref:System.Text.StringBuilder> クラスのインスタンスを作成し、そのインスタンスに 1,000 個の文字列を追加した後、その文字列表現を返します。</span><span class="sxs-lookup"><span data-stu-id="e5d73-107">The following example creates an instance of the <xref:System.Text.StringBuilder> class, appends 1,000 strings to that instance, and then returns its string representation:</span></span>

 [!code-vb[VbVbalrStrings#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#70)]

## <a name="see-also"></a><span data-ttu-id="e5d73-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="e5d73-108">See also</span></span>

- [<span data-ttu-id="e5d73-109">StringBuilder クラスの使用</span><span class="sxs-lookup"><span data-stu-id="e5d73-109">Using the StringBuilder Class</span></span>](../../../../standard/base-types/stringbuilder.md)
- [<span data-ttu-id="e5d73-110">& = 演算子</span><span class="sxs-lookup"><span data-stu-id="e5d73-110">&= Operator</span></span>](../../../language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="e5d73-111">文字列</span><span class="sxs-lookup"><span data-stu-id="e5d73-111">Strings</span></span>](index.md)
- [<span data-ttu-id="e5d73-112">新しい文字列の作成</span><span class="sxs-lookup"><span data-stu-id="e5d73-112">Creating New Strings</span></span>](../../../../standard/base-types/creating-new.md)
- [<span data-ttu-id="e5d73-113">文字列の操作</span><span class="sxs-lookup"><span data-stu-id="e5d73-113">Manipulating Strings</span></span>](../../../../standard/base-types/best-practices-strings.md)
