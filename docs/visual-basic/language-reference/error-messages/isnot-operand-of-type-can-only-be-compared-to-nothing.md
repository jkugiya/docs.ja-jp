---
description: "詳細情報: BC32128:'typename' は Null 許容型であるため、'typename' 型の 'IsNot' オペランドは 'Nothing' とのみ比較できます"
title: "'typename' は Null 許容型であるため、'typename' 型の 'IsNot' オペランドは 'Nothing' とのみ比較できます"
ms.date: 07/20/2015
f1_keywords:
- bc32128
- vbc32128
helpviewer_keywords:
- BC32128
ms.assetid: 1155b23a-ad75-4bab-b9da-73f35c767a36
ms.openlocfilehash: 732c8bee2ae352824c7d50bba8b2b35598d6f53b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795990"
---
# <a name="bc32128-isnot-operand-of-type-typename-can-only-be-compared-to-nothing-because-typename-is-a-nullable-type"></a><span data-ttu-id="c13fb-103">BC32128:'typename' は Null 許容型であるため、'typename' 型の 'IsNot' オペランドは 'Nothing' とのみ比較できます</span><span class="sxs-lookup"><span data-stu-id="c13fb-103">BC32128: 'IsNot' operand of type 'typename' can only be compared to 'Nothing', because 'typename' is a nullable type</span></span>

<span data-ttu-id="c13fb-104">Null 許容値型として宣言された変数が、`Nothing` 演算子を使用して、`IsNot` 以外の式と比較されました。</span><span class="sxs-lookup"><span data-stu-id="c13fb-104">A variable declared as a nullable value type has been compared to an expression other than `Nothing` using the `IsNot` operator.</span></span>

<span data-ttu-id="c13fb-105">**エラー ID:** BC32128</span><span class="sxs-lookup"><span data-stu-id="c13fb-105">**Error ID:** BC32128</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="c13fb-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="c13fb-106">To correct this error</span></span>

<span data-ttu-id="c13fb-107">`Nothing` 演算子を使用して、Null 許容型を `IsNot` 以外の式と比較するには、次の例に示すように、Null 許容型に対して `GetType` メソッドを呼び出し、その結果を式と比較します。</span><span class="sxs-lookup"><span data-stu-id="c13fb-107">To compare a nullable type to an expression other than `Nothing` by using the `IsNot` operator, call the `GetType` method on the nullable type and compare the result to the expression, as shown in the following example.</span></span>

```vb
Dim number? As Integer = 5

If number IsNot Nothing Then
  If number.GetType() IsNot Type.GetType("System.Int32") Then

  End If
End If
```

## <a name="see-also"></a><span data-ttu-id="c13fb-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="c13fb-108">See also</span></span>

- [<span data-ttu-id="c13fb-109">null 許容値型</span><span class="sxs-lookup"><span data-stu-id="c13fb-109">Nullable Value Types</span></span>](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="c13fb-110">IsNot 演算子</span><span class="sxs-lookup"><span data-stu-id="c13fb-110">IsNot Operator</span></span>](../operators/isnot-operator.md)
