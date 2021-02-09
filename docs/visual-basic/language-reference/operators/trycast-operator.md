---
description: '詳細情報: TryCast 演算子 (Visual Basic)'
title: TryCast 演算子
ms.date: 07/20/2015
f1_keywords:
- vb.trycast
- trycast
helpviewer_keywords:
- TryCast keyword [Visual Basic]
ms.assetid: d1ef5d47-fef4-491e-b014-1d910628f65c
ms.openlocfilehash: 5b941ec40c4ba0198fced64d0ef039605efad472
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795249"
---
# <a name="trycast-operator-visual-basic"></a><span data-ttu-id="db828-103">TryCast 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="db828-103">TryCast Operator (Visual Basic)</span></span>

<span data-ttu-id="db828-104">例外をスローしない型変換操作を導入します。</span><span class="sxs-lookup"><span data-stu-id="db828-104">Introduces a type conversion operation that does not throw an exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db828-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="db828-105">Remarks</span></span>  

 <span data-ttu-id="db828-106">試行された変換が失敗した場合、`CType` と `DirectCast` はどちらも <xref:System.InvalidCastException> エラーをスローします。</span><span class="sxs-lookup"><span data-stu-id="db828-106">If an attempted conversion fails, `CType` and `DirectCast` both throw an <xref:System.InvalidCastException> error.</span></span> <span data-ttu-id="db828-107">これは、アプリケーションのパフォーマンスに悪影響を与える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="db828-107">This can adversely affect the performance of your application.</span></span> <span data-ttu-id="db828-108">`TryCast` は [Nothing](../nothing.md) を返します。そのため、発生する可能性がある例外を処理する必要はなく、代わりに、返された結果を `Nothing` に対してテストすることのみ必要です。</span><span class="sxs-lookup"><span data-stu-id="db828-108">`TryCast` returns [Nothing](../nothing.md), so that instead of having to handle a possible exception, you need only test the returned result against `Nothing`.</span></span>  
  
 <span data-ttu-id="db828-109">`TryCast` キーワードは、[CType 関数](../functions/ctype-function.md)および [DirectCast 演算子](directcast-operator.md)キーワードを使用するのと同じ方法で使用します。</span><span class="sxs-lookup"><span data-stu-id="db828-109">You use the `TryCast` keyword the same way you use the [CType Function](../functions/ctype-function.md) and the [DirectCast Operator](directcast-operator.md) keyword.</span></span> <span data-ttu-id="db828-110">1 番目の引数として式を指定し、2 番目の引数としてその式の変換先の型を指定します。</span><span class="sxs-lookup"><span data-stu-id="db828-110">You supply an expression as the first argument and a type to convert it to as the second argument.</span></span> <span data-ttu-id="db828-111">`TryCast` は、クラスやインターフェイスなどの参照型に対してのみ動作します。</span><span class="sxs-lookup"><span data-stu-id="db828-111">`TryCast` operates only on reference types, such as classes and interfaces.</span></span> <span data-ttu-id="db828-112">2 つの型間の継承関係または実装関係が必要になります。</span><span class="sxs-lookup"><span data-stu-id="db828-112">It requires an inheritance or implementation relationship between the two types.</span></span> <span data-ttu-id="db828-113">つまり、一方の型が他方の型を継承または実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="db828-113">This means that one type must inherit from or implement the other.</span></span>  
  
## <a name="errors-and-failures"></a><span data-ttu-id="db828-114">エラーと障害</span><span class="sxs-lookup"><span data-stu-id="db828-114">Errors and Failures</span></span>  

 <span data-ttu-id="db828-115">`TryCast` で、継承関係または実装関係が存在しないことが検出されると、コンパイラ エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="db828-115">`TryCast` generates a compiler error if it detects that no inheritance or implementation relationship exists.</span></span> <span data-ttu-id="db828-116">ただし、コンパイラ エラーが発生しない場合でも、変換が正常に行われるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="db828-116">But the lack of a compiler error does not guarantee a successful conversion.</span></span> <span data-ttu-id="db828-117">目的の変換が縮小変換の場合、実行時に失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="db828-117">If the desired conversion is narrowing, it could fail at run time.</span></span> <span data-ttu-id="db828-118">これが発生すると、`TryCast` は [Nothing](../nothing.md) を返します。</span><span class="sxs-lookup"><span data-stu-id="db828-118">If this happens, `TryCast` returns [Nothing](../nothing.md).</span></span>  
  
## <a name="conversion-keywords"></a><span data-ttu-id="db828-119">変換キーワード</span><span class="sxs-lookup"><span data-stu-id="db828-119">Conversion Keywords</span></span>  

 <span data-ttu-id="db828-120">型変換のキーワードの比較を次に示します。</span><span class="sxs-lookup"><span data-stu-id="db828-120">A comparison of the type conversion keywords is as follows.</span></span>  
  
|<span data-ttu-id="db828-121">キーワード</span><span class="sxs-lookup"><span data-stu-id="db828-121">Keyword</span></span>|<span data-ttu-id="db828-122">データの種類</span><span class="sxs-lookup"><span data-stu-id="db828-122">Data types</span></span>|<span data-ttu-id="db828-123">引数の関係</span><span class="sxs-lookup"><span data-stu-id="db828-123">Argument relationship</span></span>|<span data-ttu-id="db828-124">ランタイム エラー</span><span class="sxs-lookup"><span data-stu-id="db828-124">Run-time failure</span></span>|  
|---|---|---|---|  
|[<span data-ttu-id="db828-125">CType 関数</span><span class="sxs-lookup"><span data-stu-id="db828-125">CType Function</span></span>](../functions/ctype-function.md)|<span data-ttu-id="db828-126">任意のデータ型</span><span class="sxs-lookup"><span data-stu-id="db828-126">Any data types</span></span>|<span data-ttu-id="db828-127">2 つのデータ型の間で拡大変換または縮小変換を定義する必要があります</span><span class="sxs-lookup"><span data-stu-id="db828-127">Widening or narrowing conversion must be defined between the two data types</span></span>|<span data-ttu-id="db828-128"><xref:System.InvalidCastException> がスローされます</span><span class="sxs-lookup"><span data-stu-id="db828-128">Throws <xref:System.InvalidCastException></span></span>|  
|[<span data-ttu-id="db828-129">DirectCast 演算子</span><span class="sxs-lookup"><span data-stu-id="db828-129">DirectCast Operator</span></span>](directcast-operator.md)|<span data-ttu-id="db828-130">任意のデータ型</span><span class="sxs-lookup"><span data-stu-id="db828-130">Any data types</span></span>|<span data-ttu-id="db828-131">一方の型が他方の型を継承または実装する必要があります</span><span class="sxs-lookup"><span data-stu-id="db828-131">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="db828-132"><xref:System.InvalidCastException> がスローされます</span><span class="sxs-lookup"><span data-stu-id="db828-132">Throws <xref:System.InvalidCastException></span></span>|  
|`TryCast`|<span data-ttu-id="db828-133">参照型のみ</span><span class="sxs-lookup"><span data-stu-id="db828-133">Reference types only</span></span>|<span data-ttu-id="db828-134">一方の型が他方の型を継承または実装する必要があります</span><span class="sxs-lookup"><span data-stu-id="db828-134">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="db828-135">[Nothing](../nothing.md) が返されます</span><span class="sxs-lookup"><span data-stu-id="db828-135">Returns [Nothing](../nothing.md)</span></span>|  
  
## <a name="example"></a><span data-ttu-id="db828-136">例</span><span class="sxs-lookup"><span data-stu-id="db828-136">Example</span></span>  

 <span data-ttu-id="db828-137">次の例は、`TryCast` を使用する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="db828-137">The following example shows how to use `TryCast`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="db828-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="db828-138">See also</span></span>

- [<span data-ttu-id="db828-139">拡大変換と縮小変換</span><span class="sxs-lookup"><span data-stu-id="db828-139">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="db828-140">暗黙の型変換と明示的な型変換</span><span class="sxs-lookup"><span data-stu-id="db828-140">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
