---
description: Checked と Unchecked - C# リファレンス
title: Checked と Unchecked - C# リファレンス
ms.date: 05/15/2018
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
ms.openlocfilehash: 0121090265881bfa8287e2f9e83ad4b886bf17c1
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477484"
---
# <a name="checked-and-unchecked-c-reference"></a><span data-ttu-id="2bae3-103">Checked と Unchecked (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="2bae3-103">Checked and Unchecked (C# Reference)</span></span>

<span data-ttu-id="2bae3-104">C# のステートメントは、checked または unchecked のいずれかのコンテキストで実行できます。</span><span class="sxs-lookup"><span data-stu-id="2bae3-104">C# statements can execute in either checked or unchecked context.</span></span> <span data-ttu-id="2bae3-105">checked コンテキストでは、算術オーバーフローにより例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="2bae3-105">In a checked context, arithmetic overflow raises an exception.</span></span> <span data-ttu-id="2bae3-106">unchecked コンテキストでは、算術オーバーフローが無視され、結果の格納先の型に収まらない上位ビットが破棄されて、結果が切り詰められます。</span><span class="sxs-lookup"><span data-stu-id="2bae3-106">In an unchecked context, arithmetic overflow is ignored and the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>  
  
- <span data-ttu-id="2bae3-107">[checked](checked.md): checked コンテキストを指定します。</span><span class="sxs-lookup"><span data-stu-id="2bae3-107">[checked](checked.md) Specify checked context.</span></span>  
  
- <span data-ttu-id="2bae3-108">[unchecked](unchecked.md): unchecked コンテキストを指定します。</span><span class="sxs-lookup"><span data-stu-id="2bae3-108">[unchecked](unchecked.md) Specify unchecked context.</span></span>  
  
 <span data-ttu-id="2bae3-109">オーバーフロー チェックにより、次の操作が影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="2bae3-109">The following operations are affected by the overflow checking:</span></span>  
  
- <span data-ttu-id="2bae3-110">整数型で次の定義済み演算子を使用する式:</span><span class="sxs-lookup"><span data-stu-id="2bae3-110">Expressions using the following predefined operators on integral types:</span></span>  
  
     <span data-ttu-id="2bae3-111">`++`、`--`、(単項) `-`、`+`、`-`、`*`、`/`</span><span class="sxs-lookup"><span data-stu-id="2bae3-111">`++`, `--`, unary `-`, `+`, `-`, `*`, `/`</span></span>  
  
- <span data-ttu-id="2bae3-112">整数型間か、`float` または `double` から整数型へのの明示的な数値変換。</span><span class="sxs-lookup"><span data-stu-id="2bae3-112">Explicit numeric conversions between integral types, or from `float` or `double` to an integral type.</span></span>  
  
 <span data-ttu-id="2bae3-113">`checked` と `unchecked` のいずれも指定されない場合、非定数式 (実行時に評価される式) の既定のコンテキストは [**CheckForOverflowUnderflow**](../compiler-options/language.md#checkforoverflowunderflow) コンパイラ オプションの値によって定義されます。</span><span class="sxs-lookup"><span data-stu-id="2bae3-113">If neither `checked` nor `unchecked` is specified, the default context for non-constant expressions (expressions that are evaluated at run time) is defined by the value of the [**CheckForOverflowUnderflow**](../compiler-options/language.md#checkforoverflowunderflow) compiler option.</span></span> <span data-ttu-id="2bae3-114">既定では、そのオプションの値の設定が解除され、算術演算が unchecked コンテキストで実行されます。</span><span class="sxs-lookup"><span data-stu-id="2bae3-114">By default the value of that option is unset and arithmetic operations are executed in an unchecked context.</span></span>

 <span data-ttu-id="2bae3-115">定数式 (コンパイル時に完全に評価される式) の場合、既定のコンテキストは常に確認されます。</span><span class="sxs-lookup"><span data-stu-id="2bae3-115">For constant expressions (expressions that can be fully evaluated at compile time), the default context is always checked.</span></span> <span data-ttu-id="2bae3-116">定数式が unchecked コンテキストに明示的に配置されていない限り、式のコンパイル時の評価中に発生するオーバーフローによってコンパイル時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="2bae3-116">Unless a constant expression is explicitly placed in an unchecked context, overflows that occur during the compile-time evaluation of the expression cause compile-time errors.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="2bae3-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="2bae3-117">See also</span></span>

- [<span data-ttu-id="2bae3-118">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="2bae3-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="2bae3-119">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="2bae3-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="2bae3-120">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="2bae3-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="2bae3-121">ステートメントのキーワード</span><span class="sxs-lookup"><span data-stu-id="2bae3-121">Statement Keywords</span></span>](statement-keywords.md)
