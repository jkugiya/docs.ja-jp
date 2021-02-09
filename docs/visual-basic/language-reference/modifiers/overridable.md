---
description: '詳細情報: Overridable (Visual Basic)'
title: Overridable
ms.date: 07/20/2015
f1_keywords:
- Overridable
- vb.Overridable
helpviewer_keywords:
- elements [Visual Basic], concrete
- properties [Visual Basic], redefining
- overriding, Overridable keyword
- elements [Visual Basic], virtual
- virtual [elements VB]
- procedures [Visual Basic], overriding
- concrete [elements VB]
- procedures [Visual Basic], redefining
- Overridable keyword [Visual Basic]
- properties [Visual Basic], overriding
ms.assetid: 612581e7-8a4c-4a5d-beff-3402fffa6f35
ms.openlocfilehash: acbbd715113c836a3fb7f8a88bf74307c38ac682
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99730500"
---
# <a name="overridable-visual-basic"></a><span data-ttu-id="3b30d-103">Overridable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b30d-103">Overridable (Visual Basic)</span></span>

<span data-ttu-id="3b30d-104">プロパティまたはプロシージャが派生クラスで同じ名前のプロパティまたはプロシージャによってオーバーライドできることを示します。</span><span class="sxs-lookup"><span data-stu-id="3b30d-104">Specifies that a property or procedure can be overridden by an identically named property or procedure in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b30d-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="3b30d-105">Remarks</span></span>  

 <span data-ttu-id="3b30d-106">`Overridable` 修飾子を使用すると、クラス内のプロパティまたはメソッドを派生クラスでオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="3b30d-106">The `Overridable` modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="3b30d-107">[NotOverridable](notoverridable.md) 修飾子は、派生クラス内のプロパティまたはメソッドがオーバーライドされるのを防ぎます。</span><span class="sxs-lookup"><span data-stu-id="3b30d-107">The [NotOverridable](notoverridable.md) modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="3b30d-108">詳細については、「[継承の基本](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3b30d-108">For more information, see [Inheritance Basics](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="3b30d-109">`Overridable` または `NotOverridable` 修飾子が指定されていない場合、既定の設定は、プロパティまたはメソッドが基底クラスのプロパティまたはメソッドをオーバーライドするかどうかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="3b30d-109">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="3b30d-110">プロパティまたはメソッドが基底クラスのプロパティまたはメソッドをオーバーライドする場合、既定の設定は `Overridable` であり、そうでない場合は `NotOverridable` です。</span><span class="sxs-lookup"><span data-stu-id="3b30d-110">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="3b30d-111">シャドウまたはオーバーライドによって継承された要素を再定義できますが、この 2 つの方法には大きな違いがあります。</span><span class="sxs-lookup"><span data-stu-id="3b30d-111">You can shadow or override to redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="3b30d-112">詳細については、「[Visual Basic におけるシャドウ](../../programming-guide/language-features/declared-elements/shadowing.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3b30d-112">For more information, see [Shadowing in Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
 <span data-ttu-id="3b30d-113">オーバーライドできる要素は、*仮想* 要素と呼ばれることもあります。</span><span class="sxs-lookup"><span data-stu-id="3b30d-113">An element that can be overridden is sometimes referred to as a *virtual* element.</span></span> <span data-ttu-id="3b30d-114">オーバーライドは可能でも、必要がない場合は、*具象* 要素と呼ばれることもあります。</span><span class="sxs-lookup"><span data-stu-id="3b30d-114">If it can be overridden, but does not have to be, it is sometimes also called a *concrete* element.</span></span>  
  
 <span data-ttu-id="3b30d-115">`Overridable` は、プロパティまたはプロシージャの宣言ステートメントでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="3b30d-115">You can use `Overridable` only in a property or procedure declaration statement.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="3b30d-116">結合された修飾子</span><span class="sxs-lookup"><span data-stu-id="3b30d-116">Combined Modifiers</span></span>  

 <span data-ttu-id="3b30d-117">`Private` メソッドに `Overridable` または `NotOverridable` を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="3b30d-117">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="3b30d-118">同じ宣言内で `Overridable` を `MustOverride`、`NotOverridable`、または `Shared` と共に指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="3b30d-118">You cannot specify `Overridable` together with `MustOverride`, `NotOverridable`, or `Shared` in the same declaration.</span></span>  
  
 <span data-ttu-id="3b30d-119">オーバーライドする要素は暗黙的にオーバーライド可能であるため、`Overridable` と `Overrides` を結合することはできません。</span><span class="sxs-lookup"><span data-stu-id="3b30d-119">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="3b30d-120">使用方法</span><span class="sxs-lookup"><span data-stu-id="3b30d-120">Usage</span></span>  

 <span data-ttu-id="3b30d-121">`Overridable` 修飾子は、次のコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="3b30d-121">The `Overridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="3b30d-122">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="3b30d-122">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="3b30d-123">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="3b30d-123">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="3b30d-124">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="3b30d-124">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="3b30d-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="3b30d-125">See also</span></span>

- [<span data-ttu-id="3b30d-126">修飾子</span><span class="sxs-lookup"><span data-stu-id="3b30d-126">Modifiers</span></span>](index.md)
- [<span data-ttu-id="3b30d-127">継承の基本</span><span class="sxs-lookup"><span data-stu-id="3b30d-127">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="3b30d-128">MustOverride</span><span class="sxs-lookup"><span data-stu-id="3b30d-128">MustOverride</span></span>](mustoverride.md)
- [<span data-ttu-id="3b30d-129">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="3b30d-129">NotOverridable</span></span>](notoverridable.md)
- [<span data-ttu-id="3b30d-130">Overrides</span><span class="sxs-lookup"><span data-stu-id="3b30d-130">Overrides</span></span>](overrides.md)
- [<span data-ttu-id="3b30d-131">キーワード</span><span class="sxs-lookup"><span data-stu-id="3b30d-131">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="3b30d-132">Visual Basic におけるシャドウ</span><span class="sxs-lookup"><span data-stu-id="3b30d-132">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
