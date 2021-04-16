---
title: 不要なコード規則
description: コード分析の不要なコード規則について
ms.date: 09/30/2020
ms.topic: reference
author: gewarren
ms.author: gewarren
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 16c4ba0e4bee2388736bf9813a3e8290d8d4da32
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "96593857"
---
# <a name="unnecessary-code-rules"></a><span data-ttu-id="cf334-103">不要なコード規則</span><span class="sxs-lookup"><span data-stu-id="cf334-103">Unnecessary code rules</span></span>

<span data-ttu-id="cf334-104">不要なコード規則は、不要でリファクタリングまたは削除することができるコード ベースのさまざまな部分を特定します。</span><span class="sxs-lookup"><span data-stu-id="cf334-104">Unnecessary code rules identify different parts of the code base that are unnecessary and can be refactored or removed.</span></span> <span data-ttu-id="cf334-105">不要なコードが存在する場合は、次の問題の 1 つ以上が存在することを示しています。</span><span class="sxs-lookup"><span data-stu-id="cf334-105">The presence of unnecessary code indicates one of more of the following problems:</span></span>

- <span data-ttu-id="cf334-106">読みやすさ: 読みやすさを不必要に低下させるコード。</span><span class="sxs-lookup"><span data-stu-id="cf334-106">Readability: Code that is unnecessarily degrading readability.</span></span> <span data-ttu-id="cf334-107">たとえば、[IDE0001](ide0001.md) は不要な型名の修飾にフラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="cf334-107">For example, [IDE0001](ide0001.md) flags unnecessary type-name qualifications.</span></span>
- <span data-ttu-id="cf334-108">保守容易性: リファクタリング後に使用されなくなり、不必要に管理されるコード。</span><span class="sxs-lookup"><span data-stu-id="cf334-108">Maintainability: Code that is no longer used after refactoring and is unnecessarily being maintained.</span></span> <span data-ttu-id="cf334-109">たとえば、[IDE0051](ide0051.md) は、使用されていないプライベート フィールド、プロパティ、イベント、およびメソッドにフラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="cf334-109">For example, [IDE0051](ide0051.md) flags unused private fields, properties, events, and methods.</span></span>
- <span data-ttu-id="cf334-110">パフォーマンス: 副作用がなく、不要なパフォーマンスのオーバーヘッドが発生する不要な計算。</span><span class="sxs-lookup"><span data-stu-id="cf334-110">Performance: Unnecessary computation that has no side effects and leads to unnecessary performance overhead.</span></span> <span data-ttu-id="cf334-111">たとえば、[IDE0059](ide0059.md) は、値を計算する式に副作用がない未使用の値の割り当てにフラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="cf334-111">For example, [IDE0059](ide0059.md) flags unused value assignments where the expression to compute a value has no side effects.</span></span>
- <span data-ttu-id="cf334-112">機能: コードの冗長なレンダリングが必要となるコードの機能の問題。</span><span class="sxs-lookup"><span data-stu-id="cf334-112">Functionality: Functional issue in code leading to required code being rendered redundant.</span></span> <span data-ttu-id="cf334-113">たとえば、[IDE0060](ide0060.md) は、メソッドで誤って入力パラメーターを無視した場合に、未使用のパラメーターにフラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="cf334-113">For example, [IDE0060](ide0060.md) flags unused parameters where the method accidentally ignores an input parameter.</span></span>

<span data-ttu-id="cf334-114">このセクションの規則では、次の不要なコード規則について考慮します。</span><span class="sxs-lookup"><span data-stu-id="cf334-114">The rules in this section concern the following unnecessary code rules:</span></span>

- [<span data-ttu-id="cf334-115">名前を簡略化する (IDE0001)</span><span class="sxs-lookup"><span data-stu-id="cf334-115">Simplify name (IDE0001)</span></span>](ide0001.md)
- [<span data-ttu-id="cf334-116">メンバー アクセスを簡略化する (IDE0002)</span><span class="sxs-lookup"><span data-stu-id="cf334-116">Simplify member access (IDE0002)</span></span>](ide0002.md)
- [<span data-ttu-id="cf334-117">不要なキャストを削除する (IDE0004)</span><span class="sxs-lookup"><span data-stu-id="cf334-117">Remove unnecessary cast (IDE0004)</span></span>](ide0004.md)
- [<span data-ttu-id="cf334-118">不要なインポートを削除する (IDE0005)</span><span class="sxs-lookup"><span data-stu-id="cf334-118">Remove unnecessary import (IDE0005)</span></span>](ide0005.md)
- [<span data-ttu-id="cf334-119">到達できないコードを削除する (IDE0035)</span><span class="sxs-lookup"><span data-stu-id="cf334-119">Remove unreachable code (IDE0035)</span></span>](ide0035.md)
- [<span data-ttu-id="cf334-120">使用されていない非公開メンバーを削除する (IDE0051)</span><span class="sxs-lookup"><span data-stu-id="cf334-120">Remove unused private member (IDE0051)</span></span>](ide0051.md)
- [<span data-ttu-id="cf334-121">読み取られていない非公開メンバーを削除する (IDE0052)</span><span class="sxs-lookup"><span data-stu-id="cf334-121">Remove unread private member (IDE0052)</span></span>](ide0052.md)
- [<span data-ttu-id="cf334-122">使用されていない式の値を削除する (IDE0058)</span><span class="sxs-lookup"><span data-stu-id="cf334-122">Remove unused expression value (IDE0058)</span></span>](ide0058.md)
- [<span data-ttu-id="cf334-123">不要な値の代入を削除する (IDE0059)</span><span class="sxs-lookup"><span data-stu-id="cf334-123">Remove unnecessary value assignment (IDE0059)</span></span>](ide0059.md)
- [<span data-ttu-id="cf334-124">使用されていないパラメーターを削除する (IDE0060)</span><span class="sxs-lookup"><span data-stu-id="cf334-124">Remove unused parameter (IDE0060)</span></span>](ide0060.md)
- [<span data-ttu-id="cf334-125">不要な抑制を削除する (IDE0079)</span><span class="sxs-lookup"><span data-stu-id="cf334-125">Remove unnecessary suppression (IDE0079)</span></span>](ide0079.md)
- <span data-ttu-id="cf334-126">[不要な抑制演算子を削除する (IDE0080)](ide0080.md) - C# のみ。</span><span class="sxs-lookup"><span data-stu-id="cf334-126">[Remove unnecessary suppression operator (IDE0080)](ide0080.md) - C# only.</span></span>
- <span data-ttu-id="cf334-127">['ByVal' を削除する (IDE0081)](ide0081.md) - Visual Basic のみ。</span><span class="sxs-lookup"><span data-stu-id="cf334-127">[Remove 'ByVal' (IDE0081)](ide0081.md) - Visual Basic only.</span></span>
- [<span data-ttu-id="cf334-128">不要な等値演算子を削除する (IDE0100)</span><span class="sxs-lookup"><span data-stu-id="cf334-128">Remove unnecessary equality operator (IDE0100)</span></span>](ide0100.md)
- <span data-ttu-id="cf334-129">[不要な破棄を削除する (IDE0110)](ide0110.md) - C# のみ。</span><span class="sxs-lookup"><span data-stu-id="cf334-129">[Remove unnecessary discard (IDE0110)](ide0110.md) - C# only.</span></span>

<span data-ttu-id="cf334-130">これらの規則の一部には、規則の動作を構成するためのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="cf334-130">Some of these rules have options to configure the rule behavior:</span></span>

- [<span data-ttu-id="cf334-131">csharp_style_unused_value_expression_statement_preference (IDE0058)</span><span class="sxs-lookup"><span data-stu-id="cf334-131">csharp_style_unused_value_expression_statement_preference (IDE0058)</span></span>](ide0058.md#csharp_style_unused_value_expression_statement_preference)
- [<span data-ttu-id="cf334-132">visual_basic_style_unused_value_expression_statement_preference (IDE0058)</span><span class="sxs-lookup"><span data-stu-id="cf334-132">visual_basic_style_unused_value_expression_statement_preference (IDE0058)</span></span>](ide0058.md#visual_basic_style_unused_value_expression_statement_preference)
- [<span data-ttu-id="cf334-133">csharp_style_unused_value_assignment_preference (IDE0059)</span><span class="sxs-lookup"><span data-stu-id="cf334-133">csharp_style_unused_value_assignment_preference (IDE0059)</span></span>](ide0059.md#csharp_style_unused_value_assignment_preference)
- [<span data-ttu-id="cf334-134">visual_basic_style_unused_value_assignment_preference (IDE0059)</span><span class="sxs-lookup"><span data-stu-id="cf334-134">visual_basic_style_unused_value_assignment_preference (IDE0059)</span></span>](ide0059.md#visual_basic_style_unused_value_assignment_preference)
- [<span data-ttu-id="cf334-135">dotnet_code_quality_unused_parameters (IDE0060)</span><span class="sxs-lookup"><span data-stu-id="cf334-135">dotnet_code_quality_unused_parameters (IDE0060)</span></span>](ide0060.md#dotnet_code_quality_unused_parameters)
- [<span data-ttu-id="cf334-136">dotnet_remove_unnecessary_suppression_exclusions (IDE0079)</span><span class="sxs-lookup"><span data-stu-id="cf334-136">dotnet_remove_unnecessary_suppression_exclusions (IDE0079)</span></span>](ide0079.md#dotnet_remove_unnecessary_suppression_exclusions)

## <a name="see-also"></a><span data-ttu-id="cf334-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="cf334-137">See also</span></span>

- [<span data-ttu-id="cf334-138">コード スタイルの言語規則</span><span class="sxs-lookup"><span data-stu-id="cf334-138">Code style language rules</span></span>](language-rules.md)
- [<span data-ttu-id="cf334-139">コード スタイルの規則のリファレンス</span><span class="sxs-lookup"><span data-stu-id="cf334-139">Code style rules reference</span></span>](index.md)
