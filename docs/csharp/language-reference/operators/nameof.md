---
description: nameof 式 - C# リファレンス
title: nameof 式 - C# リファレンス
ms.date: 04/23/2020
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof expression [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 568127a64efc02717b34fbd9d1e508e2e40596fd
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100464392"
---
# <a name="nameof-expression-c-reference"></a><span data-ttu-id="d8fb6-103">nameof 式 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="d8fb6-103">nameof expression (C# reference)</span></span>

<span data-ttu-id="d8fb6-104">`nameof` 式を使うと、変数、型、またはメンバーの名前が文字列定数として生成されます。</span><span class="sxs-lookup"><span data-stu-id="d8fb6-104">A `nameof` expression produces the name of a variable, type, or member as the string constant:</span></span>

[!code-csharp-interactive[nameof expression](snippets/shared/NameOfOperator.cs#Examples)]

<span data-ttu-id="d8fb6-105">前の例で示されているように、型と名前空間の場合、生成される名前は[完全修飾](~/_csharplang/spec/basic-concepts.md#fully-qualified-names)ではありません。</span><span class="sxs-lookup"><span data-stu-id="d8fb6-105">As the preceding example shows, in the case of a type and a namespace, the produced name is not [fully qualified](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span></span>

<span data-ttu-id="d8fb6-106">[逐語的識別子](../tokens/verbatim.md)の場合、次の例に示すように、`@` 文字は名前の一部ではありません。</span><span class="sxs-lookup"><span data-stu-id="d8fb6-106">In the case of [verbatim identifiers](../tokens/verbatim.md), the `@` character is not the part of a name, as the following example shows:</span></span>

[!code-csharp-interactive[nameof verbatim](snippets/shared/NameOfOperator.cs#Verbatim)]

<span data-ttu-id="d8fb6-107">`nameof` 式はコンパイル時に評価され、実行時には影響を与えません。</span><span class="sxs-lookup"><span data-stu-id="d8fb6-107">A `nameof` expression is evaluated at compile time and has no effect at run time.</span></span>

<span data-ttu-id="d8fb6-108">`nameof` 式を使って、引数をチェックするコードの保守性を高めることができます。</span><span class="sxs-lookup"><span data-stu-id="d8fb6-108">You can use a `nameof` expression to make the argument-checking code more maintainable:</span></span>

[!code-csharp[nameof and argument check](snippets/shared/NameOfOperator.cs#ExceptionMessage)]

<span data-ttu-id="d8fb6-109">`nameof` 式は C# 6 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="d8fb6-109">A `nameof` expression is available in C# 6 and later.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d8fb6-110">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="d8fb6-110">C# language specification</span></span>

<span data-ttu-id="d8fb6-111">詳細については、[C# 言語仕様](~/_csharplang/spec/introduction.md)の「[Nameof 式](~/_csharplang/spec/expressions.md#nameof-expressions)」セクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d8fb6-111">For more information, see the [Nameof expressions](~/_csharplang/spec/expressions.md#nameof-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d8fb6-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="d8fb6-112">See also</span></span>

- [<span data-ttu-id="d8fb6-113">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="d8fb6-113">C# reference</span></span>](../index.md)
- [<span data-ttu-id="d8fb6-114">C# の演算子と式</span><span class="sxs-lookup"><span data-stu-id="d8fb6-114">C# operators and expressions</span></span>](index.md)
