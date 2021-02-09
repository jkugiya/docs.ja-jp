---
description: '詳細情報: Implements 句 (Visual Basic)'
title: Implements 句
ms.date: 07/20/2015
f1_keywords:
- vb.ImplementsClause
helpviewer_keywords:
- interface implementation [Visual Basic], reimplementation
- interface members [Visual Basic], reimplementation
- interface members [Visual Basic], Implements keyword
- interface members
- members [Visual Basic], reimplementation
- interface implementation [Visual Basic], Implements keyword
- interface members [Visual Basic], implementing
- Implements keyword [Visual Basic]
- Implements statement [Visual Basic], about Implements
- members [Visual Basic], implementing
- members [Visual Basic], Implements keyword
- reimplementation
ms.assetid: 5252cdf9-964d-4fc6-af0f-0449b7126b5a
ms.openlocfilehash: 360d8812a7c49d6462818246b1448e171dcd597f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99769001"
---
# <a name="implements-clause-visual-basic"></a><span data-ttu-id="07b1f-103">Implements 句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="07b1f-103">Implements Clause (Visual Basic)</span></span>

<span data-ttu-id="07b1f-104">クラスまたは構造体のメンバーがインターフェイスで定義されているメンバーの実装を提供していることを示します。</span><span class="sxs-lookup"><span data-stu-id="07b1f-104">Indicates that a class or structure member is providing the implementation for a member defined in an interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07b1f-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="07b1f-105">Remarks</span></span>  

<span data-ttu-id="07b1f-106">`Implements` キーワードは、[Implements ステートメント](implements-statement.md)と同じではありません。</span><span class="sxs-lookup"><span data-stu-id="07b1f-106">The `Implements` keyword is not the same as the [Implements Statement](implements-statement.md).</span></span> <span data-ttu-id="07b1f-107">`Implements` ステートメントを使用して、クラスまたは構造体が 1 つ以上のインターフェイスを実装することを指定し、メンバーごとに `Implements` キーワードを使用して、実装するインターフェイスとメンバーを指定します。</span><span class="sxs-lookup"><span data-stu-id="07b1f-107">You use the `Implements` statement to specify that a class or structure implements one or more interfaces, and then for each member you use the `Implements` keyword to specify which interface and which member it implements.</span></span>

<span data-ttu-id="07b1f-108">クラスまたは構造体がインターフェイスを実装する場合は、[Class ステートメント](class-statement.md)または [Structure ステートメント](structure-statement.md)の直後に `Implements` ステートメントを含める必要があります。また、インターフェイスによって定義されたすべてのメンバーを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="07b1f-108">If a class or structure implements an interface, it must include the `Implements` statement immediately after the [Class Statement](class-statement.md) or [Structure Statement](structure-statement.md), and it must implement all the members defined by the interface.</span></span>

## <a name="reimplementation"></a><span data-ttu-id="07b1f-109">再実装</span><span class="sxs-lookup"><span data-stu-id="07b1f-109">Reimplementation</span></span>  

<span data-ttu-id="07b1f-110">派生クラスでは、基底クラスによって既に実装されているインターフェイス メンバーを再実装できます。</span><span class="sxs-lookup"><span data-stu-id="07b1f-110">In a derived class, you can reimplement an interface member that the base class has already implemented.</span></span> <span data-ttu-id="07b1f-111">これは、基底クラスのメンバーのオーバーライドとは、次の点で異なります。</span><span class="sxs-lookup"><span data-stu-id="07b1f-111">This is different from overriding the base class member in the following respects:</span></span>

- <span data-ttu-id="07b1f-112">基底クラスのメンバーは、再実装するために [Overridable](../modifiers/overridable.md) である必要はありません。</span><span class="sxs-lookup"><span data-stu-id="07b1f-112">The base class member does not need to be [Overridable](../modifiers/overridable.md) to be reimplemented.</span></span>
- <span data-ttu-id="07b1f-113">別の名前を使用してメンバーを再実装できます。</span><span class="sxs-lookup"><span data-stu-id="07b1f-113">You can reimplement the member with a different name.</span></span>

<span data-ttu-id="07b1f-114">`Implements` キーワードは、次のコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="07b1f-114">The `Implements` keyword can be used in the following contexts:</span></span>

- [<span data-ttu-id="07b1f-115">Event ステートメント</span><span class="sxs-lookup"><span data-stu-id="07b1f-115">Event Statement</span></span>](event-statement.md)
- [<span data-ttu-id="07b1f-116">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="07b1f-116">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="07b1f-117">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="07b1f-117">Property Statement</span></span>](property-statement.md)
- [<span data-ttu-id="07b1f-118">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="07b1f-118">Sub Statement</span></span>](sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="07b1f-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="07b1f-119">See also</span></span>

- [<span data-ttu-id="07b1f-120">Implements ステートメント</span><span class="sxs-lookup"><span data-stu-id="07b1f-120">Implements Statement</span></span>](implements-statement.md)
- [<span data-ttu-id="07b1f-121">Interface ステートメント</span><span class="sxs-lookup"><span data-stu-id="07b1f-121">Interface Statement</span></span>](interface-statement.md)
- [<span data-ttu-id="07b1f-122">Class ステートメント</span><span class="sxs-lookup"><span data-stu-id="07b1f-122">Class Statement</span></span>](class-statement.md)
- [<span data-ttu-id="07b1f-123">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="07b1f-123">Structure Statement</span></span>](structure-statement.md)
