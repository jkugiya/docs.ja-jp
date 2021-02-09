---
description: '詳細情報: WithEvents (Visual Basic)'
title: ReadOnly
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: b27f84fe54aaa10bc9b2359cd74fad3d3ace1ad5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99674767"
---
# <a name="withevents-visual-basic"></a><span data-ttu-id="b3fe5-103">WithEvents (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3fe5-103">WithEvents (Visual Basic)</span></span>

<span data-ttu-id="b3fe5-104">1 つ以上の宣言されたメンバー変数が、イベントを発生させる可能性のあるクラスのインスタンスを参照していることを示します。</span><span class="sxs-lookup"><span data-stu-id="b3fe5-104">Specifies that one or more declared member variables refer to an instance of a class that can raise events.</span></span>

## <a name="remarks"></a><span data-ttu-id="b3fe5-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="b3fe5-105">Remarks</span></span>

<span data-ttu-id="b3fe5-106">変数が `WithEvents` を使用して定義されている場合は、メソッドが `Handles` キーワードを使用して変数のイベントを処理するように、宣言によって指定できます。</span><span class="sxs-lookup"><span data-stu-id="b3fe5-106">When a variable is defined using `WithEvents`, you can declaratively specify that a method handles the variable's events using the `Handles` keyword.</span></span>

<span data-ttu-id="b3fe5-107">`WithEvents` は、クラスまたはモジュール レベルでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="b3fe5-107">You can use `WithEvents` only at class or module level.</span></span> <span data-ttu-id="b3fe5-108">つまり、`WithEvents` 変数の宣言コンテキストはクラスまたはモジュールにする必要があり、ソース ファイル、名前空間、構造体、またはプロシージャにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="b3fe5-108">This means the declaration context for a `WithEvents` variable must be a class or module and cannot be a source file, namespace, structure, or procedure.</span></span>

<span data-ttu-id="b3fe5-109">構造体メンバーでは `WithEvents` は使用できません。</span><span class="sxs-lookup"><span data-stu-id="b3fe5-109">You cannot use `WithEvents` on a structure member.</span></span>

<span data-ttu-id="b3fe5-110">`WithEvents` では、配列ではなく個々の変数のみを宣言できます。</span><span class="sxs-lookup"><span data-stu-id="b3fe5-110">You can declare only individual variables—not arrays—with `WithEvents`.</span></span>

## <a name="rules"></a><span data-ttu-id="b3fe5-111">ルール</span><span class="sxs-lookup"><span data-stu-id="b3fe5-111">Rules</span></span>

<span data-ttu-id="b3fe5-112">**要素型。**</span><span class="sxs-lookup"><span data-stu-id="b3fe5-112">**Element Types.**</span></span> <span data-ttu-id="b3fe5-113">オブジェクト変数として `WithEvents` 変数を宣言して、クラス インスタンスを受け入れられるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b3fe5-113">You must declare `WithEvents` variables to be object variables so that they can accept class instances.</span></span> <span data-ttu-id="b3fe5-114">C++ では、これらを `Object` として宣言することはできません。</span><span class="sxs-lookup"><span data-stu-id="b3fe5-114">However, you cannot declare them as `Object`.</span></span> <span data-ttu-id="b3fe5-115">イベントを発生可能な特定のクラスとして宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b3fe5-115">You must declare them as the specific class that can raise the events.</span></span>

<span data-ttu-id="b3fe5-116">`WithEvents` 修飾子は、次のコンテキストで使用できます。[Dim ステートメント](../statements/dim-statement.md)</span><span class="sxs-lookup"><span data-stu-id="b3fe5-116">The `WithEvents` modifier can be used in this context: [Dim Statement](../statements/dim-statement.md)</span></span>

## <a name="example"></a><span data-ttu-id="b3fe5-117">例</span><span class="sxs-lookup"><span data-stu-id="b3fe5-117">Example</span></span>

```vb
Dim WithEvents app As Application
```

## <a name="see-also"></a><span data-ttu-id="b3fe5-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="b3fe5-118">See also</span></span>

- [<span data-ttu-id="b3fe5-119">Handles</span><span class="sxs-lookup"><span data-stu-id="b3fe5-119">Handles</span></span>](../statements/handles-clause.md)
- [<span data-ttu-id="b3fe5-120">キーワード</span><span class="sxs-lookup"><span data-stu-id="b3fe5-120">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="b3fe5-121">イベント</span><span class="sxs-lookup"><span data-stu-id="b3fe5-121">Events</span></span>](../../programming-guide/language-features/events/index.md)
