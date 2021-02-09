---
description: '詳細情報: 数値演算子および比較演算子'
title: 数値演算子および比較演算子
ms.date: 03/30/2017
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
ms.openlocfilehash: 5b17f19769436ac4e575ac974668eadc3b17b8f6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695529"
---
# <a name="numeric-and-comparison-operators"></a><span data-ttu-id="9bca6-103">数値演算子および比較演算子</span><span class="sxs-lookup"><span data-stu-id="9bca6-103">Numeric and Comparison Operators</span></span>

<span data-ttu-id="9bca6-104">算術演算子と比較演算子は、次の点を除いて、共通言語ランタイム (CLR) では期待どおりに動作します。</span><span class="sxs-lookup"><span data-stu-id="9bca6-104">Arithmetic and comparison operators work as expected in the common language runtime (CLR) except as follows:</span></span>

- <span data-ttu-id="9bca6-105">SQL では、浮動小数点数に対して剰余演算子がサポートされません。</span><span class="sxs-lookup"><span data-stu-id="9bca6-105">SQL does not support the modulus operator on floating-point numbers.</span></span>

- <span data-ttu-id="9bca6-106">SQL ではチェックされない算術はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="9bca6-106">SQL does not support unchecked arithmetic.</span></span>

- <span data-ttu-id="9bca6-107">インクリメント演算子とデクリメント演算子は、SQL に複製できない式で使用すると副作用があるため、SQL ではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="9bca6-107">Increment and decrement operators cause side-effects when you use them in expressions that cannot be replicated in SQL and are, therefore, not supported.</span></span>

## <a name="supported-operators"></a><span data-ttu-id="9bca6-108">サポートされる演算子</span><span class="sxs-lookup"><span data-stu-id="9bca6-108">Supported Operators</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="9bca6-109">は、次の演算子をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="9bca6-109">supports the following operators.</span></span>

- <span data-ttu-id="9bca6-110">基本算術演算子</span><span class="sxs-lookup"><span data-stu-id="9bca6-110">Basic arithmetic operators:</span></span>

  - `+`

  - <span data-ttu-id="9bca6-111">`-` (減算)</span><span class="sxs-lookup"><span data-stu-id="9bca6-111">`-` (subtraction)</span></span>

  - `*`

  - `/`

  - <span data-ttu-id="9bca6-112">Visual Basic 整数除算 (`\`)</span><span class="sxs-lookup"><span data-stu-id="9bca6-112">Visual Basic integer division (`\`)</span></span>

  - <span data-ttu-id="9bca6-113">`%` (Visual Basic `Mod`)</span><span class="sxs-lookup"><span data-stu-id="9bca6-113">`%` (Visual Basic `Mod`)</span></span>

  - `<<`

  - `>>`

  - <span data-ttu-id="9bca6-114">`-` (単項マイナス符号)</span><span class="sxs-lookup"><span data-stu-id="9bca6-114">`-` (unary negation)</span></span>

- <span data-ttu-id="9bca6-115">基本比較演算子</span><span class="sxs-lookup"><span data-stu-id="9bca6-115">Basic comparison operators:</span></span>

  - <span data-ttu-id="9bca6-116">Visual Basic `=` および C# `==`</span><span class="sxs-lookup"><span data-stu-id="9bca6-116">Visual Basic `=` and C# `==`</span></span>

  - <span data-ttu-id="9bca6-117">Visual Basic `<>` および C# `!=`</span><span class="sxs-lookup"><span data-stu-id="9bca6-117">Visual Basic `<>` and C# `!=`</span></span>

  - <span data-ttu-id="9bca6-118">Visual Basic `Is/IsNot`</span><span class="sxs-lookup"><span data-stu-id="9bca6-118">Visual Basic `Is/IsNot`</span></span>

  - `<`

  - `<=`

  - `>`

  - `>=`

## <a name="see-also"></a><span data-ttu-id="9bca6-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="9bca6-119">See also</span></span>

- [<span data-ttu-id="9bca6-120">データ型と関数</span><span class="sxs-lookup"><span data-stu-id="9bca6-120">Data Types and Functions</span></span>](data-types-and-functions.md)
- [<span data-ttu-id="9bca6-121">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="9bca6-121">C# Operators</span></span>](../../../../../csharp/language-reference/operators/index.md)
- [<span data-ttu-id="9bca6-122">演算子</span><span class="sxs-lookup"><span data-stu-id="9bca6-122">Operators</span></span>](../../../../../visual-basic/language-reference/operators/index.md)
