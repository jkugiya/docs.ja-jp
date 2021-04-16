---
title: ブール演算子
description: F# プログラミング言語で使用できるブール演算子について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: ad4bdd1121389f7e280647dbe0c4d0098ffb17df
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641899"
---
# <a name="boolean-operators"></a><span data-ttu-id="e49a2-103">ブール演算子</span><span class="sxs-lookup"><span data-stu-id="e49a2-103">Boolean Operators</span></span>

<span data-ttu-id="e49a2-104">このトピックでは、F# 言語のブール演算子のサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="e49a2-104">This topic describes the support for Boolean operators in the F# language.</span></span>

## <a name="summary-of-boolean-operators"></a><span data-ttu-id="e49a2-105">ブール演算子の概要</span><span class="sxs-lookup"><span data-stu-id="e49a2-105">Summary of Boolean Operators</span></span>

<span data-ttu-id="e49a2-106">次の表では、F# 言語で使用できるブール演算子がまとめられています。</span><span class="sxs-lookup"><span data-stu-id="e49a2-106">The following table summarizes the Boolean operators that are available in the F# language.</span></span> <span data-ttu-id="e49a2-107">これらの演算子でサポートされている型は、`bool` 型のみです。</span><span class="sxs-lookup"><span data-stu-id="e49a2-107">The only type supported by these operators is the `bool` type.</span></span>

|<span data-ttu-id="e49a2-108">演算子</span><span class="sxs-lookup"><span data-stu-id="e49a2-108">Operator</span></span>|<span data-ttu-id="e49a2-109">説明</span><span class="sxs-lookup"><span data-stu-id="e49a2-109">Description</span></span>|
|--------|-----------|
|`not`|<span data-ttu-id="e49a2-110">ブール値の否定</span><span class="sxs-lookup"><span data-stu-id="e49a2-110">Boolean negation</span></span>|
|<code>&#124;&#124;</code>|<span data-ttu-id="e49a2-111">ブール値の OR</span><span class="sxs-lookup"><span data-stu-id="e49a2-111">Boolean OR</span></span>|
|`&&`|<span data-ttu-id="e49a2-112">ブール値の AND</span><span class="sxs-lookup"><span data-stu-id="e49a2-112">Boolean AND</span></span>|

<span data-ttu-id="e49a2-113">ブール値の AND および OR 演算子では、 *"短絡評価"* が実行されます。つまり、式の全体の結果を確認する必要がある場合にのみ、演算子の右側で式が評価されます。</span><span class="sxs-lookup"><span data-stu-id="e49a2-113">The Boolean AND and OR operators perform *short-circuit evaluation*, that is, they evaluate the expression on the right of the operator only when it is necessary to determine the overall result of the expression.</span></span> <span data-ttu-id="e49a2-114">`&&` 演算子の 2 番目の式は、最初の式が `true` に評価される場合にのみ評価され、`||` 演算子の 2 番目の式は、最初の式が `false` に評価される場合にのみ評価されます。</span><span class="sxs-lookup"><span data-stu-id="e49a2-114">The second expression of the `&&` operator is evaluated only if the first expression evaluates to `true`; the second expression of the `||` operator is evaluated only if the first expression evaluates to `false`.</span></span>

## <a name="see-also"></a><span data-ttu-id="e49a2-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="e49a2-115">See also</span></span>

- [<span data-ttu-id="e49a2-116">ビット処理演算子 &、^、&#124;</span><span class="sxs-lookup"><span data-stu-id="e49a2-116">Bitwise Operators</span></span>](bitwise-operators.md)
- [<span data-ttu-id="e49a2-117">算術演算子</span><span class="sxs-lookup"><span data-stu-id="e49a2-117">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="e49a2-118">シンボルと演算子のリファレンス</span><span class="sxs-lookup"><span data-stu-id="e49a2-118">Symbol and Operator Reference</span></span>](index.md)
