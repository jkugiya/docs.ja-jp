---
title: 保守容易性の規則 (コード分析)
description: コード分析の保守容易性の規則について説明します。
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.maintainabilityrules
helpviewer_keywords:
- rules, maintainability
- managed code analysis rules, maintainability rules
- maintainability rules
author: gewarren
ms.author: gewarren
ms.openlocfilehash: fc2ef2b42eeba241b7af66b579a60365ad2b88c7
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "96591194"
---
# <a name="maintainability-rules"></a><span data-ttu-id="fd514-103">保守容易性の規則</span><span class="sxs-lookup"><span data-stu-id="fd514-103">Maintainability rules</span></span>

<span data-ttu-id="fd514-104">保守容易性の規則は、ライブラリとアプリケーションの保守をサポートします。</span><span class="sxs-lookup"><span data-stu-id="fd514-104">Maintainability rules support library and application maintenance.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="fd514-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="fd514-105">In this section</span></span>

| <span data-ttu-id="fd514-106">ルール</span><span class="sxs-lookup"><span data-stu-id="fd514-106">Rule</span></span> | <span data-ttu-id="fd514-107">説明</span><span class="sxs-lookup"><span data-stu-id="fd514-107">Description</span></span> |
|-----------|-----------------------------------|
| [<span data-ttu-id="fd514-108">CA1501:継承を使用しすぎないでください</span><span class="sxs-lookup"><span data-stu-id="fd514-108">CA1501: Avoid excessive inheritance</span></span>](ca1501.md) | <span data-ttu-id="fd514-109">型が、その継承階層内の 5 つ以上深いレベルにあります。</span><span class="sxs-lookup"><span data-stu-id="fd514-109">A type is more than four levels deep in its inheritance hierarchy.</span></span> <span data-ttu-id="fd514-110">深いレベルで入れ子にされた型の確認、理解、および保守は困難です。</span><span class="sxs-lookup"><span data-stu-id="fd514-110">Deeply nested type hierarchies can be difficult to follow, understand, and maintain.</span></span> |
| [<span data-ttu-id="fd514-111">CA1502:メソッドの実装を複雑にしすぎないでください</span><span class="sxs-lookup"><span data-stu-id="fd514-111">CA1502: Avoid excessive complexity</span></span>](ca1502.md) | <span data-ttu-id="fd514-112">この規則は、線形独立のメソッド経路数を示す尺度で、条件分岐の数と複雑さによって決まります。</span><span class="sxs-lookup"><span data-stu-id="fd514-112">This rule measures the number of linearly independent paths through the method, which is determined by the number and complexity of conditional branches.</span></span> |
| [<span data-ttu-id="fd514-113">CA1505:メンテナンスできないコードを使用しないでください</span><span class="sxs-lookup"><span data-stu-id="fd514-113">CA1505: Avoid unmaintainable code</span></span>](ca1505.md) | <span data-ttu-id="fd514-114">型またはメソッドの保守容易性指数が低い値です。</span><span class="sxs-lookup"><span data-stu-id="fd514-114">A type or method has a low maintainability index value.</span></span> <span data-ttu-id="fd514-115">保守容易性指数の低い型またはメソッドは、保守が困難な可能性があるため、デザインの変更を検討することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="fd514-115">A low maintainability index indicates that a type or method is probably difficult to maintain and would be a good candidate for redesign.</span></span> |
| [<span data-ttu-id="fd514-116">CA1506:クラス結合度を大きくしすぎないでください</span><span class="sxs-lookup"><span data-stu-id="fd514-116">CA1506: Avoid excessive class coupling</span></span>](ca1506.md) | <span data-ttu-id="fd514-117">この規則は、型またはメソッドに含まれる一意の型参照の数をカウントすることによって、クラス結合度を計測します。</span><span class="sxs-lookup"><span data-stu-id="fd514-117">This rule measures class coupling by counting the number of unique type references that a type or method contains.</span></span> |
| [<span data-ttu-id="fd514-118">CA1507:文字列の代わりに nameof を使用します</span><span class="sxs-lookup"><span data-stu-id="fd514-118">CA1507: Use nameof in place of string</span></span>](ca1507.md) | <span data-ttu-id="fd514-119">`nameof` 式を使用できる場合に、文字列リテラルが引数として使用されています。</span><span class="sxs-lookup"><span data-stu-id="fd514-119">A string literal is used as an argument where a `nameof` expression could be used.</span></span> |
| [<span data-ttu-id="fd514-120">CA1508:使用されない条件付きコードを回避する</span><span class="sxs-lookup"><span data-stu-id="fd514-120">CA1508: Avoid dead conditional code</span></span>](ca1508.md) | <span data-ttu-id="fd514-121">実行時に常に `true` または `false` と評価される条件付きコードがメソッドにあります。</span><span class="sxs-lookup"><span data-stu-id="fd514-121">A method has conditional code that always evaluates to `true` or `false` at runtime.</span></span> <span data-ttu-id="fd514-122">このため、条件の `false` 分岐で実行されないコードになります。</span><span class="sxs-lookup"><span data-stu-id="fd514-122">This leads to dead code in the `false` branch of the condition.</span></span> |
| [<span data-ttu-id="fd514-123">CA1509: コード メトリック構成ファイルのエントリが無効です</span><span class="sxs-lookup"><span data-stu-id="fd514-123">CA1509: Invalid entry in code metrics configuration file</span></span>](ca1509.md) | <span data-ttu-id="fd514-124">[CA1501](ca1501.md)、[CA1502](ca1502.md)、[CA1505](ca1505.md)、[CA1506](ca1506.md) などのコード メトリック規則で、無効なエントリを含んだ `CodeMetricsConfig.txt` という名前の構成ファイルが指定されました。</span><span class="sxs-lookup"><span data-stu-id="fd514-124">Code metrics rules, such as [CA1501](ca1501.md), [CA1502](ca1502.md), [CA1505](ca1505.md) and [CA1506](ca1506.md), supplied a configuration file named `CodeMetricsConfig.txt` that has an invalid entry.</span></span> |

## <a name="see-also"></a><span data-ttu-id="fd514-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="fd514-125">See also</span></span>

- [<span data-ttu-id="fd514-126">マネージド コードの複雑さと保守性の測定</span><span class="sxs-lookup"><span data-stu-id="fd514-126">Measure Complexity and Maintainability of Managed Code</span></span>](/visualstudio/code-quality/code-metrics-values)
