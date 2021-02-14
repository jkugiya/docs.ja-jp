---
description: "詳細情報: BC32053:'ByRef' パラメーター '<parametername>' の値を一致する引数へ戻してコピーすると、型 '<typename1>' から型 '<typename2>' に下位変換します"
title: "'ByRef' パラメーター '<parametername>' の値を一致する引数へ戻してコピーすると、型 '<typename1>' から型 '<typename2>' に下位変換します"
ms.date: 07/20/2015
f1_keywords:
- bc32053
- vbc32053
helpviewer_keywords:
- BC32053
ms.assetid: 281564b7-99f7-451f-b10d-f985e831bb25
ms.openlocfilehash: a90e64cd81443831a7b8f934fea646411eb5a220
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796705"
---
# <a name="bc32053-copying-the-value-of-byref-parameter-parametername-back-to-the-matching-argument-narrows-from-type-typename1-to-type-typename2"></a><span data-ttu-id="651a4-103">BC32053:'ByRef' パラメーター '\<parametername>' の値を一致する引数へ戻してコピーすると、型 '\<typename1>' から型 '\<typename2>' に下位変換します</span><span class="sxs-lookup"><span data-stu-id="651a4-103">BC32053: Copying the value of 'ByRef' parameter '\<parametername>' back to the matching argument narrows from type '\<typename1>' to type '\<typename2>'</span></span>

<span data-ttu-id="651a4-104">対応するパラメーターの型に拡大変換する引数でプロシージャが呼び出され、パラメーターから引数への変換が縮小されます。</span><span class="sxs-lookup"><span data-stu-id="651a4-104">A procedure is called with an argument that widens to the corresponding parameter type, and the conversion from the parameter to the argument is narrowing.</span></span>

 <span data-ttu-id="651a4-105">クラスまたは構造体を定義するときは、そのクラスまたは構造体の型を他の型に変換する 1 つまたは複数の変換演算子を定義できます。</span><span class="sxs-lookup"><span data-stu-id="651a4-105">When you define a class or structure, you can define one or more conversion operators to convert that class or structure type to other types.</span></span> <span data-ttu-id="651a4-106">その他の型をクラスまたは構造体の型に変換する逆の変換演算子を定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="651a4-106">You can also define reverse conversion operators to convert those other types back to your class or structure type.</span></span> <span data-ttu-id="651a4-107">プロシージャ呼び出しでクラスまたは構造体の型を使用すると、Visual Basic ではこれらの変換演算子を使用して、引数の型を、対応するパラメーターの型に変換できます。</span><span class="sxs-lookup"><span data-stu-id="651a4-107">When you use your class or structure type in a procedure call, Visual Basic can use these conversion operators to convert the type of an argument to the type of its corresponding parameter.</span></span>

 <span data-ttu-id="651a4-108">引数 [ByRef](../modifiers/byref.md) を渡した場合、Visual Basic では参照を渡す代わりに、引数の値をプロシージャのローカル変数にコピーすることがあります。</span><span class="sxs-lookup"><span data-stu-id="651a4-108">If you pass the argument [ByRef](../modifiers/byref.md), Visual Basic sometimes copies the argument value into a local variable in the procedure instead of passing a reference.</span></span> <span data-ttu-id="651a4-109">このような場合は、プロシージャから戻るときに、Visual Basic で呼び出し元のコードの引数にローカル変数の値をコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="651a4-109">In such a case, when the procedure returns, Visual Basic must then copy the local variable value back into the argument in the calling code.</span></span>

 <span data-ttu-id="651a4-110">`ByRef` 引数の値がプロシージャにコピーされ、引数とパラメーターが同じ型である場合、変換は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="651a4-110">If a `ByRef` argument value is copied into the procedure and the argument and parameter are of the same type, no conversion is necessary.</span></span> <span data-ttu-id="651a4-111">型が異なる場合、Visual Basic では双方向で変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="651a4-111">But if the types are different, Visual Basic must convert in both directions.</span></span> <span data-ttu-id="651a4-112">型のいずれかがクラスまたは構造体の型の場合、Visual Basic ではその型を他の型との間で変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="651a4-112">If one of the types is your class or structure type, Visual Basic must convert it both to and from the other type.</span></span> <span data-ttu-id="651a4-113">これらの変換のいずれかが拡大変換している場合、逆変換では縮小変換される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="651a4-113">If one of these conversions is widening, the reverse conversion might be narrowing.</span></span>

 <span data-ttu-id="651a4-114">**エラー ID:** BC32053</span><span class="sxs-lookup"><span data-stu-id="651a4-114">**Error ID:** BC32053</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="651a4-115">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="651a4-115">To correct this error</span></span>

- <span data-ttu-id="651a4-116">可能な場合は、プロシージャのパラメーターと同じ型の呼び出し元の引数を使用して、Visual Basic で変換する必要がないようにします。</span><span class="sxs-lookup"><span data-stu-id="651a4-116">If possible, use a calling argument of the same type as the procedure parameter, so Visual Basic does not need to do any conversion.</span></span>

- <span data-ttu-id="651a4-117">パラメーター型とは異なる引数型を使用してプロシージャを呼び出す必要があり、呼び出し元の引数に値を返す必要がない場合は、 [ByRef](../modifiers/byval.md) ではなく `ByRef`になるようにパラメーターを定義します。</span><span class="sxs-lookup"><span data-stu-id="651a4-117">If you need to call the procedure with an argument type different from the parameter type but do not need to return a value into the calling argument, define the parameter to be [ByVal](../modifiers/byval.md) instead of `ByRef`.</span></span>

- <span data-ttu-id="651a4-118">呼び出し元の引数に値を返す必要がある場合は、可能であれば[拡大変換](../modifiers/widening.md)として、逆変換演算子を定義します。</span><span class="sxs-lookup"><span data-stu-id="651a4-118">If you need to return a value into the calling argument, define the reverse conversion operator as [Widening](../modifiers/widening.md), if possible.</span></span>

## <a name="see-also"></a><span data-ttu-id="651a4-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="651a4-119">See also</span></span>

- [<span data-ttu-id="651a4-120">手順</span><span class="sxs-lookup"><span data-stu-id="651a4-120">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="651a4-121">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="651a4-121">Procedure Parameters and Arguments</span></span>](../../programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [<span data-ttu-id="651a4-122">引数の値渡しと参照渡し</span><span class="sxs-lookup"><span data-stu-id="651a4-122">Passing Arguments by Value and by Reference</span></span>](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="651a4-123">演算子プロシージャ</span><span class="sxs-lookup"><span data-stu-id="651a4-123">Operator Procedures</span></span>](../../programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="651a4-124">Operator ステートメント</span><span class="sxs-lookup"><span data-stu-id="651a4-124">Operator Statement</span></span>](../statements/operator-statement.md)
- [<span data-ttu-id="651a4-125">方法: 演算子を定義する</span><span class="sxs-lookup"><span data-stu-id="651a4-125">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="651a4-126">方法: 変換演算子を定義する</span><span class="sxs-lookup"><span data-stu-id="651a4-126">How to: Define a Conversion Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="651a4-127">Visual Basic における型変換</span><span class="sxs-lookup"><span data-stu-id="651a4-127">Type Conversions in Visual Basic</span></span>](../../programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="651a4-128">拡大変換と縮小変換</span><span class="sxs-lookup"><span data-stu-id="651a4-128">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
