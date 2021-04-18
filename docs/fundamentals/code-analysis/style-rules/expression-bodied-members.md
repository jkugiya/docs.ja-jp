---
title: 式形式のメンバー
description: 式形式のメンバーのコード分析言語規則について
ms.date: 09/30/2020
ms.topic: reference
author: gewarren
ms.author: gewarren
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 5aae09b1ac94219b7df802981e4e4598cd949035
ms.sourcegitcommit: bbc724b72fb6c978905ac715e4033efa291f84dc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2021
ms.locfileid: "107369609"
---
# <a name="expression-bodied-members"></a><span data-ttu-id="d3e81-103">式形式のメンバー</span><span class="sxs-lookup"><span data-stu-id="d3e81-103">Expression-bodied-members</span></span>

## <a name="overview"></a><span data-ttu-id="d3e81-104">概要</span><span class="sxs-lookup"><span data-stu-id="d3e81-104">Overview</span></span>

<span data-ttu-id="d3e81-105">このセクションのスタイル ルールは、ロジックが単一の式で構成される場合の[式形式のメンバー](../../../csharp/programming-guide/statements-expressions-operators/expression-bodied-members.md)の使用に関するものです。</span><span class="sxs-lookup"><span data-stu-id="d3e81-105">The style rules in this section concern the use of [expression-bodied members](../../../csharp/programming-guide/statements-expressions-operators/expression-bodied-members.md) when the logic consists of a single expression.</span></span>

- [<span data-ttu-id="d3e81-106">コンストラクターに式本体を使用する (IDE0021)</span><span class="sxs-lookup"><span data-stu-id="d3e81-106">Use expression body for constructors (IDE0021)</span></span>](ide0021.md)
- [<span data-ttu-id="d3e81-107">メソッドに式本体を使用する (IDE0022)</span><span class="sxs-lookup"><span data-stu-id="d3e81-107">Use expression body for methods (IDE0022)</span></span>](ide0022.md)
- [<span data-ttu-id="d3e81-108">演算子に式本体を使用する (IDE0023 および IDE0024)</span><span class="sxs-lookup"><span data-stu-id="d3e81-108">Use expression body for operators (IDE0023 and IDE0024)</span></span>](ide0023-ide0024.md)
- [<span data-ttu-id="d3e81-109">プロパティに式本体を使用する (IDE0025)</span><span class="sxs-lookup"><span data-stu-id="d3e81-109">Use expression body for properties (IDE0025)</span></span>](ide0025.md)
- [<span data-ttu-id="d3e81-110">インデクサーに式本体を使用する (IDE0026)</span><span class="sxs-lookup"><span data-stu-id="d3e81-110">Use expression body for indexers (IDE0026)</span></span>](ide0026.md)
- [<span data-ttu-id="d3e81-111">アクセサーに式本体を使用する (IDE0027)</span><span class="sxs-lookup"><span data-stu-id="d3e81-111">Use expression body for accessors (IDE0027)</span></span>](ide0027.md)
- [<span data-ttu-id="d3e81-112">ラムダ式に式本体を使用する (IDE0053)</span><span class="sxs-lookup"><span data-stu-id="d3e81-112">Use expression body for lambda expressions (IDE0053)</span></span>](ide0053.md)
- [<span data-ttu-id="d3e81-113">ローカル関数に式本体を使用する (IDE0061)</span><span class="sxs-lookup"><span data-stu-id="d3e81-113">Use expression body for local functions (IDE0061)</span></span>](ide0061.md)

## <a name="see-also"></a><span data-ttu-id="d3e81-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="d3e81-114">See also</span></span>

- [<span data-ttu-id="d3e81-115">コード スタイルの規則のリファレンス</span><span class="sxs-lookup"><span data-stu-id="d3e81-115">Code style rules reference</span></span>](index.md)
- [<span data-ttu-id="d3e81-116">コード スタイルの言語規則</span><span class="sxs-lookup"><span data-stu-id="d3e81-116">Code style language rules</span></span>](language-rules.md)
