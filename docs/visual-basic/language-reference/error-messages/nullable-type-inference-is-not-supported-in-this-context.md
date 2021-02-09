---
description: '詳細情報: BC36629:Null 許容型の推論はこのコンテキストではサポートされていません'
title: Null 許容型の推論はこのコンテキストではサポートされていません
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: 915f964d55068f39b0468e2c47cc6e5538be1a6f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795626"
---
# <a name="bc36629-nullable-type-inference-is-not-supported-in-this-context"></a><span data-ttu-id="fcdc4-103">BC36629:Null 許容型の推論はこのコンテキストではサポートされていません</span><span class="sxs-lookup"><span data-stu-id="fcdc4-103">BC36629: Nullable type inference is not supported in this context</span></span>

<span data-ttu-id="fcdc4-104">値の型と構造体は、Null 許容と宣言できます。</span><span class="sxs-lookup"><span data-stu-id="fcdc4-104">Value types and structures can be declared nullable.</span></span>

```vb
Dim a? As Integer
Dim b As Integer?
```

 <span data-ttu-id="fcdc4-105">ただし、Null 許容の宣言を型の推定と組み合わせて使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="fcdc4-105">However, you cannot use the nullable declaration in combination with type inference.</span></span> <span data-ttu-id="fcdc4-106">次の例では、このエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="fcdc4-106">The following examples cause this error.</span></span>

```vb
' Not valid.
' Dim c? = 10
' Dim d? = a
```

 <span data-ttu-id="fcdc4-107">**エラー ID:** BC36629</span><span class="sxs-lookup"><span data-stu-id="fcdc4-107">**Error ID:** BC36629</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="fcdc4-108">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="fcdc4-108">To correct this error</span></span>

- <span data-ttu-id="fcdc4-109">`As` 句を使用して、変数を null 許容値型として宣言します。</span><span class="sxs-lookup"><span data-stu-id="fcdc4-109">Use an `As` clause to declare the variable as a nullable value type.</span></span>

## <a name="see-also"></a><span data-ttu-id="fcdc4-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="fcdc4-110">See also</span></span>

- [<span data-ttu-id="fcdc4-111">null 許容値型</span><span class="sxs-lookup"><span data-stu-id="fcdc4-111">Nullable Value Types</span></span>](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="fcdc4-112">ローカル型の推論</span><span class="sxs-lookup"><span data-stu-id="fcdc4-112">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
