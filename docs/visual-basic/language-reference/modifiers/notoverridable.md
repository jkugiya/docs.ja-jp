---
description: '詳細情報: NotOverridable (Visual Basic)'
title: NotOverridable
ms.date: 07/20/2015
f1_keywords:
- vb.NotOverridable
- NotOverridable
helpviewer_keywords:
- sealed methods [Visual Basic]
- NotOverridable keyword [Visual Basic]
- properties [Visual Basic], redefining
- elements [Visual Basic], sealed
- sealed [elements VB]
- procedures [Visual Basic], overriding
- procedures [Visual Basic], redefining
- overriding
- methods [Visual Basic], sealed
- properties [Visual Basic], overriding
ms.assetid: 66ec6984-f5f5-4857-b362-6a3907aaf9e0
ms.openlocfilehash: f0363024aacc1ed6ab9d8820cc965b5b71e557b6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666096"
---
# <a name="notoverridable-visual-basic"></a><span data-ttu-id="be1c2-103">NotOverridable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="be1c2-103">NotOverridable (Visual Basic)</span></span>

<span data-ttu-id="be1c2-104">派生クラス内のプロパティまたはプロシージャをオーバーライドできないことを示します。</span><span class="sxs-lookup"><span data-stu-id="be1c2-104">Specifies that a property or procedure cannot be overridden in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be1c2-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="be1c2-105">Remarks</span></span>  

 <span data-ttu-id="be1c2-106">`NotOverridable` 修飾子は、派生クラス内のプロパティまたはメソッドがオーバーライドされるのを防ぎます。</span><span class="sxs-lookup"><span data-stu-id="be1c2-106">The `NotOverridable` modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="be1c2-107">[Overridable](overridable.md) 修飾子を使用すると、クラス内のプロパティまたはメソッドを派生クラスでオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="be1c2-107">The [Overridable](overridable.md) modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="be1c2-108">詳細については、「[継承の基本](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="be1c2-108">For more information, see [Inheritance Basics](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="be1c2-109">`Overridable` または `NotOverridable` 修飾子が指定されていない場合、既定の設定は、プロパティまたはメソッドが基底クラスのプロパティまたはメソッドをオーバーライドするかどうかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="be1c2-109">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="be1c2-110">プロパティまたはメソッドが基底クラスのプロパティまたはメソッドをオーバーライドする場合、既定の設定は `Overridable` であり、そうでない場合は `NotOverridable` です。</span><span class="sxs-lookup"><span data-stu-id="be1c2-110">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="be1c2-111">オーバーライドできない要素は、*シールド* 要素と呼ばれることもあります。</span><span class="sxs-lookup"><span data-stu-id="be1c2-111">An element that cannot be overridden is sometimes called a *sealed* element.</span></span>  
  
 <span data-ttu-id="be1c2-112">`NotOverridable` は、プロパティまたはプロシージャの宣言ステートメントでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="be1c2-112">You can use `NotOverridable` only in a property or procedure declaration statement.</span></span> <span data-ttu-id="be1c2-113">`NotOverridable` は、別のプロパティまたはプロシージャをオーバーライドするプロパティまたはプロシージャでのみ、つまり `Overrides` との組み合わせでのみ指定できます。</span><span class="sxs-lookup"><span data-stu-id="be1c2-113">You can specify `NotOverridable` only on a property or procedure that overrides another property or procedure, that is, only in combination with `Overrides`.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="be1c2-114">結合された修飾子</span><span class="sxs-lookup"><span data-stu-id="be1c2-114">Combined Modifiers</span></span>  

 <span data-ttu-id="be1c2-115">`Private` メソッドに `Overridable` または `NotOverridable` を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="be1c2-115">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="be1c2-116">同じ宣言内で `NotOverridable` を `MustOverride`、`Overridable`、または `Shared` と共に指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="be1c2-116">You cannot specify `NotOverridable` together with `MustOverride`, `Overridable`, or `Shared` in the same declaration.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="be1c2-117">使用方法</span><span class="sxs-lookup"><span data-stu-id="be1c2-117">Usage</span></span>  

 <span data-ttu-id="be1c2-118">`NotOverridable` 修飾子は、次のコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="be1c2-118">The `NotOverridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="be1c2-119">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="be1c2-119">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="be1c2-120">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="be1c2-120">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="be1c2-121">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="be1c2-121">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="be1c2-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="be1c2-122">See also</span></span>

- [<span data-ttu-id="be1c2-123">修飾子</span><span class="sxs-lookup"><span data-stu-id="be1c2-123">Modifiers</span></span>](index.md)
- [<span data-ttu-id="be1c2-124">継承の基本</span><span class="sxs-lookup"><span data-stu-id="be1c2-124">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="be1c2-125">MustOverride</span><span class="sxs-lookup"><span data-stu-id="be1c2-125">MustOverride</span></span>](mustoverride.md)
- [<span data-ttu-id="be1c2-126">Overridable</span><span class="sxs-lookup"><span data-stu-id="be1c2-126">Overridable</span></span>](overridable.md)
- [<span data-ttu-id="be1c2-127">Overrides</span><span class="sxs-lookup"><span data-stu-id="be1c2-127">Overrides</span></span>](overrides.md)
- [<span data-ttu-id="be1c2-128">キーワード</span><span class="sxs-lookup"><span data-stu-id="be1c2-128">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="be1c2-129">Visual Basic におけるシャドウ</span><span class="sxs-lookup"><span data-stu-id="be1c2-129">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
