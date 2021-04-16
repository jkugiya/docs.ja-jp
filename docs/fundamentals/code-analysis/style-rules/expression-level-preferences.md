---
title: 式レベルの基本設定
description: 式レベルの基本設定のコード分析言語規則について説明します
ms.date: 09/30/2020
ms.topic: reference
author: gewarren
ms.author: gewarren
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 9933111b1ed76166e5ae86e9bc1a2332c3c77c81
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "96593791"
---
# <a name="expression-level-preferences"></a><span data-ttu-id="83591-103">式レベルの基本設定</span><span class="sxs-lookup"><span data-stu-id="83591-103">Expression-level preferences</span></span>

## <a name="net-expression-level-preferences"></a><span data-ttu-id="83591-104">.NET の式レベルのユーザー設定</span><span class="sxs-lookup"><span data-stu-id="83591-104">.NET expression-level preferences</span></span>

<span data-ttu-id="83591-105">このセクションのスタイル規則では、C# と Visual Basic に共通する次の式レベルの基本設定について考慮します。</span><span class="sxs-lookup"><span data-stu-id="83591-105">The style rules in this section concern the following expression-level preferences that are common to C# and Visual Basic:</span></span>

- [<span data-ttu-id="83591-106">不足しているケースを switch ステートメントに追加する (IDE0010)</span><span class="sxs-lookup"><span data-stu-id="83591-106">Add missing cases to switch statement (IDE0010)</span></span>](ide0010.md)
- [<span data-ttu-id="83591-107">オブジェクト初期化子を使用する (IDE0017)</span><span class="sxs-lookup"><span data-stu-id="83591-107">Use object initializers (IDE0017)</span></span>](ide0017.md)
- [<span data-ttu-id="83591-108">コレクション初期化子を使用する (IDE0028)</span><span class="sxs-lookup"><span data-stu-id="83591-108">Use collection initializers (IDE0028)</span></span>](ide0028.md)
- [<span data-ttu-id="83591-109">自動プロパティを使用する (IDE0032)</span><span class="sxs-lookup"><span data-stu-id="83591-109">Use auto property (IDE0032)</span></span>](ide0032.md)
- [<span data-ttu-id="83591-110">明示的に提供されたタプル名を使用する (IDE0033)</span><span class="sxs-lookup"><span data-stu-id="83591-110">Use explicitly provided tuple name (IDE0033)</span></span>](ide0033.md)
- [<span data-ttu-id="83591-111">推定メンバーの名前を使用する (IDE0037)</span><span class="sxs-lookup"><span data-stu-id="83591-111">Use inferred member name (IDE0037)</span></span>](ide0037.md)
- [<span data-ttu-id="83591-112">代入に条件式を使用する (IDE0045)</span><span class="sxs-lookup"><span data-stu-id="83591-112">Use conditional expression for assignment (IDE0045)</span></span>](ide0045.md)
- [<span data-ttu-id="83591-113">戻り値に条件式を使用する (IDE0046)</span><span class="sxs-lookup"><span data-stu-id="83591-113">Use conditional expression for return (IDE0046)</span></span>](ide0046.md)
- [<span data-ttu-id="83591-114">匿名型をタプルに変換する (IDE0050)</span><span class="sxs-lookup"><span data-stu-id="83591-114">Convert anonymous type to tuple (IDE0050)</span></span>](ide0050.md)
- [<span data-ttu-id="83591-115">複合代入を使用する (IDE0054 および IDE0074)</span><span class="sxs-lookup"><span data-stu-id="83591-115">Use compound assignment (IDE0054 and IDE0074)</span></span>](ide0054-ide0074.md)
- [<span data-ttu-id="83591-116">'System.HashCode.Combine' を使用する (IDE0070)</span><span class="sxs-lookup"><span data-stu-id="83591-116">Use 'System.HashCode.Combine' (IDE0070)</span></span>](ide0070.md)
- [<span data-ttu-id="83591-117">補間を簡略化する (IDE0071)</span><span class="sxs-lookup"><span data-stu-id="83591-117">Simplify interpolation (IDE0071)</span></span>](ide0071.md)
- [<span data-ttu-id="83591-118">条件式を簡略化する (IDE0075)</span><span class="sxs-lookup"><span data-stu-id="83591-118">Simplify conditional expression (IDE0075)</span></span>](ide0075.md)
- [<span data-ttu-id="83591-119">'typeof' を 'nameof' に変換する (IDE0082)</span><span class="sxs-lookup"><span data-stu-id="83591-119">Convert 'typeof' to 'nameof' (IDE0082)</span></span>](ide0082.md)

## <a name="c-expression-level-preferences"></a><span data-ttu-id="83591-120">C# の式レベルのユーザー設定</span><span class="sxs-lookup"><span data-stu-id="83591-120">C# expression-level preferences</span></span>

<span data-ttu-id="83591-121">このセクションのスタイル規則では、C# に固有な次の式レベルの基本設定について考慮します。</span><span class="sxs-lookup"><span data-stu-id="83591-121">The style rules in this section concern the following expression-level preferences that are specific to C#:</span></span>

- [<span data-ttu-id="83591-122">インライン変数宣言 (IDE0018)</span><span class="sxs-lookup"><span data-stu-id="83591-122">Inline variable declaration (IDE0018)</span></span>](ide0018.md)
- [<span data-ttu-id="83591-123">’default' 式を簡略化する (IDE0034)</span><span class="sxs-lookup"><span data-stu-id="83591-123">Simplify 'default' expression (IDE0034)</span></span>](ide0034.md)
- [<span data-ttu-id="83591-124">ラムダの代わりにローカル関数を使用する (IDE0039)</span><span class="sxs-lookup"><span data-stu-id="83591-124">Use local function instead of lambda (IDE0039)</span></span>](ide0039.md)
- [<span data-ttu-id="83591-125">変数宣言を分解する (IDE0042)</span><span class="sxs-lookup"><span data-stu-id="83591-125">Deconstruct variable declaration (IDE0042)</span></span>](ide0042.md)
- [<span data-ttu-id="83591-126">インデックス演算子を使用する (IDE0056)</span><span class="sxs-lookup"><span data-stu-id="83591-126">Use index operator (IDE0056)</span></span>](ide0056.md)
- [<span data-ttu-id="83591-127">範囲演算子を使用する (IDE0057)</span><span class="sxs-lookup"><span data-stu-id="83591-127">Use range operator (IDE0057)</span></span>](ide0057.md)
- [<span data-ttu-id="83591-128">不足しているケースを switch 式に追加する (IDE0072)</span><span class="sxs-lookup"><span data-stu-id="83591-128">Add missing cases to switch expression (IDE0072)</span></span>](ide0072.md)
- [<span data-ttu-id="83591-129">'new' 式を簡略化する (IDE0090)</span><span class="sxs-lookup"><span data-stu-id="83591-129">Simplify 'new' expression (IDE0090)</span></span>](ide0090.md)

## <a name="see-also"></a><span data-ttu-id="83591-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="83591-130">See also</span></span>

- [<span data-ttu-id="83591-131">コード スタイルの規則のリファレンス</span><span class="sxs-lookup"><span data-stu-id="83591-131">Code style rules reference</span></span>](index.md)
- [<span data-ttu-id="83591-132">コード スタイルの言語規則</span><span class="sxs-lookup"><span data-stu-id="83591-132">Code style language rules</span></span>](language-rules.md)
