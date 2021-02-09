---
description: "詳細情報: BC41999:'ByRef' パラメーター '<typename1>' の値を、一致する引数に戻してコピーする際の、'<typename2>' から '<parametername>' への暗黙的な変換です。"
title: "'ByRef' パラメーター '<typename1>' の値を、一致する引数に戻してコピーする際の、'<typename2>' から '<parametername>' への暗黙的な変換です。"
ms.date: 07/20/2015
f1_keywords:
- vbc41999
- bc41999
helpviewer_keywords:
- BC41999
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
ms.openlocfilehash: debe9d248a41d1b5c1f541392a1846b8598c126f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796081"
---
# <a name="bc41999-implicit-conversion-from-typename1-to-typename2-in-copying-the-value-of-byref-parameter-parametername-back-to-the-matching-argument"></a><span data-ttu-id="c5052-103">BC41999:'ByRef' パラメーター '\<typename1>' の値を、一致する引数に戻してコピーする際の、'\<typename2>' から '\<parametername>' への暗黙的な変換です。</span><span class="sxs-lookup"><span data-stu-id="c5052-103">BC41999: Implicit conversion from '\<typename1>' to '\<typename2>' in copying the value of 'ByRef' parameter '\<parametername>' back to the matching argument.</span></span>

<span data-ttu-id="c5052-104">プロシージャが、対応するパラメーターとは異なる型の [ByRef](../modifiers/byref.md) 引数を指定して呼び出されました。</span><span class="sxs-lookup"><span data-stu-id="c5052-104">A procedure is called with a [ByRef](../modifiers/byref.md) argument of a different type than that of its corresponding parameter.</span></span>

 <span data-ttu-id="c5052-105">引数 `ByRef` を渡した場合、Visual Basic は参照を渡す代わりに、引数の値をプロシージャのローカル変数にコピーすることがあります。</span><span class="sxs-lookup"><span data-stu-id="c5052-105">If you pass an argument `ByRef`, Visual Basic sometimes copies the argument value into a local variable in the procedure instead of passing a reference.</span></span> <span data-ttu-id="c5052-106">このような場合は、プロシージャから戻るときに、Visual Basic で呼び出し元のコードの引数にローカル変数の値をコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5052-106">In such a case, when the procedure returns, Visual Basic must then copy the local variable value back into the argument in the calling code.</span></span>

 <span data-ttu-id="c5052-107">`ByRef` 引数の値がプロシージャにコピーされ、引数とパラメーターが同じ型である場合、変換は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="c5052-107">If a `ByRef` argument value is copied into the procedure and the argument and parameter are of the same type, no conversion is necessary.</span></span> <span data-ttu-id="c5052-108">型が異なる場合、Visual Basic では双方向で変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5052-108">But if the types are different, Visual Basic must convert in both directions.</span></span> <span data-ttu-id="c5052-109">プロシージャの引数またはパラメーターで `CType` または他の変換キーワードを使用することはできないため、このような変換は常に暗黙的です。</span><span class="sxs-lookup"><span data-stu-id="c5052-109">Because you cannot use `CType` or any of the other conversion keywords on a procedure argument or parameter, such a conversion is always implicit.</span></span>

 <span data-ttu-id="c5052-110">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="c5052-110">By default, this message is a warning.</span></span> <span data-ttu-id="c5052-111">警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c5052-111">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="c5052-112">**エラー ID:** BC41999</span><span class="sxs-lookup"><span data-stu-id="c5052-112">**Error ID:** BC41999</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="c5052-113">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="c5052-113">To correct this error</span></span>

- <span data-ttu-id="c5052-114">可能な場合は、プロシージャのパラメーターと同じ型の呼び出し元の引数を使用して、Visual Basic で変換する必要がないようにします。</span><span class="sxs-lookup"><span data-stu-id="c5052-114">If possible, use a calling argument of the same type as the procedure parameter, so Visual Basic does not need to do any conversion.</span></span>

- <span data-ttu-id="c5052-115">パラメーター型とは異なる引数型を使用してプロシージャを呼び出す必要があり、呼び出し元の引数に値を返す必要がない場合は、 [ByRef](../modifiers/byval.md) ではなく `ByRef`になるようにパラメーターを定義します。</span><span class="sxs-lookup"><span data-stu-id="c5052-115">If you need to call the procedure with an argument type different from the parameter type but do not need to return a value into the calling argument, define the parameter to be [ByVal](../modifiers/byval.md) instead of `ByRef`.</span></span>

## <a name="see-also"></a><span data-ttu-id="c5052-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="c5052-116">See also</span></span>

- [<span data-ttu-id="c5052-117">手順</span><span class="sxs-lookup"><span data-stu-id="c5052-117">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="c5052-118">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="c5052-118">Procedure Parameters and Arguments</span></span>](../../programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [<span data-ttu-id="c5052-119">引数の値渡しと参照渡し</span><span class="sxs-lookup"><span data-stu-id="c5052-119">Passing Arguments by Value and by Reference</span></span>](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="c5052-120">暗黙の型変換と明示的な型変換</span><span class="sxs-lookup"><span data-stu-id="c5052-120">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
