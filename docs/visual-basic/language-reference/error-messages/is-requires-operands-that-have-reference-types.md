---
description: "詳細情報: BC30020:'Is' には参照型を持つオペランドが必要ですが、このオペランドの値型は '<typename>' です。"
title: "'Is' には参照型を持つオペランドが必要ですが、このオペランドの値型は '<typename>' です。"
ms.date: 07/20/2015
f1_keywords:
- bc30020
- vbc30020
helpviewer_keywords:
- BC30020
ms.assetid: 228afebd-1203-4bd3-8d7a-c5c56f3cedc4
ms.openlocfilehash: f05040c6174f4b1edd006d1302f0d94b871d1cd9
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100427545"
---
# <a name="bc30020-is-requires-operands-that-have-reference-types-but-this-operand-has-the-value-type-typename"></a><span data-ttu-id="24589-103">BC30020:'Is' には参照型を持つオペランドが必要ですが、このオペランドの値型は '\<typename>' です。</span><span class="sxs-lookup"><span data-stu-id="24589-103">BC30020: 'Is' requires operands that have reference types, but this operand has the value type '\<typename>'</span></span>

<span data-ttu-id="24589-104">`Is` 比較演算子は、2 つのオブジェクト変数が同じインスタンスを参照しているかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="24589-104">The `Is` comparison operator determines whether two object variables refer to the same instance.</span></span> <span data-ttu-id="24589-105">この比較は、値型に対して定義されていません。</span><span class="sxs-lookup"><span data-stu-id="24589-105">This comparison is not defined for value types.</span></span>

 <span data-ttu-id="24589-106">**エラー ID:** BC30020</span><span class="sxs-lookup"><span data-stu-id="24589-106">**Error ID:** BC30020</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="24589-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="24589-107">To correct this error</span></span>

- <span data-ttu-id="24589-108">適切な算術比較演算子または `Like` 演算子を使用して、2 つの値の型を比較します。</span><span class="sxs-lookup"><span data-stu-id="24589-108">Use the appropriate arithmetic comparison operator or the `Like` operator to compare two value types.</span></span>

## <a name="see-also"></a><span data-ttu-id="24589-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="24589-109">See also</span></span>

- [<span data-ttu-id="24589-110">Is 演算子</span><span class="sxs-lookup"><span data-stu-id="24589-110">Is Operator</span></span>](../operators/is-operator.md)
- [<span data-ttu-id="24589-111">Like 演算子</span><span class="sxs-lookup"><span data-stu-id="24589-111">Like Operator</span></span>](../operators/like-operator.md)
- [<span data-ttu-id="24589-112">比較演算子</span><span class="sxs-lookup"><span data-stu-id="24589-112">Comparison Operators</span></span>](../operators/comparison-operators.md)
