---
description: '詳細情報: BC36599:範囲変数の名前は、引数なしの簡易名または修飾名からのみ推論できます'
title: 範囲変数の名前は、引数なしの簡易名または修飾名からのみ推論できます
ms.date: 07/20/2015
f1_keywords:
- vbc36599
- bc36599
helpviewer_keywords:
- BC36599
ms.assetid: 17763dbe-f74f-4ccb-8086-cb7e45ec4d12
ms.openlocfilehash: b729b6786f9b7803a794b9a4e786d94fa41a57ec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792064"
---
# <a name="bc36599-range-variable-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a><span data-ttu-id="57999-103">BC36599:範囲変数の名前は、引数なしの簡易名または修飾名からのみ推論できます</span><span class="sxs-lookup"><span data-stu-id="57999-103">BC36599: Range variable name can be inferred only from a simple or qualified name with no arguments</span></span>

<span data-ttu-id="57999-104">1 つ以上の引数を取るプログラミング要素が、LINQ クエリに含まれています。</span><span class="sxs-lookup"><span data-stu-id="57999-104">A programming element that takes one or more arguments is included in a LINQ query.</span></span> <span data-ttu-id="57999-105">コンパイラは、そのプログラミング要素から範囲変数を推論できません。</span><span class="sxs-lookup"><span data-stu-id="57999-105">The compiler is unable to infer a range variable from that programming element.</span></span>

<span data-ttu-id="57999-106">**エラー ID:** BC36599</span><span class="sxs-lookup"><span data-stu-id="57999-106">**Error ID:** BC36599</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="57999-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="57999-107">To correct this error</span></span>

<span data-ttu-id="57999-108">次のコードに示すように、プログラミング要素に明示的な変数名を指定します。</span><span class="sxs-lookup"><span data-stu-id="57999-108">Supply an explicit variable name for the programming element, as shown in the following code:</span></span>

```vb
Dim query = From var1 In collection1
            Select VariableAlias= SampleFunction(var1), var1
```

## <a name="see-also"></a><span data-ttu-id="57999-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="57999-109">See also</span></span>

- [<span data-ttu-id="57999-110">Visual Basic における LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="57999-110">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="57999-111">Select 句</span><span class="sxs-lookup"><span data-stu-id="57999-111">Select Clause</span></span>](../queries/select-clause.md)
