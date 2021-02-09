---
description: '詳細情報: Private (Visual Basic)'
title: Private
ms.date: 07/20/2015
f1_keywords:
- vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
ms.openlocfilehash: 20dcd943856e20ccb1b7cb5c0603fa5f313d2421
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700950"
---
# <a name="private-visual-basic"></a><span data-ttu-id="758b3-103">Private (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="758b3-103">Private (Visual Basic)</span></span>

<span data-ttu-id="758b3-104">1 つ以上の宣言されたプログラミング要素が、含まれている型の中からを含め、その宣言コンテキスト内からのみアクセス可能であることを示します。</span><span class="sxs-lookup"><span data-stu-id="758b3-104">Specifies that one or more declared programming elements are accessible only from within their declaration context, including from within any contained types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="758b3-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="758b3-105">Remarks</span></span>  

 <span data-ttu-id="758b3-106">プログラミング要素が独自の機能を表している場合、または機密データが含まれている場合は、通常、できるだけ厳密にアクセスを制限することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="758b3-106">If a programming element represents proprietary functionality, or contains confidential data, you usually want to limit access to it as strictly as possible.</span></span> <span data-ttu-id="758b3-107">最大の制限を達成するには、それを定義するモジュール、クラス、または構造体だけがアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="758b3-107">You achieve the maximum limitation by allowing only the module, class, or structure that defines it to access it.</span></span> <span data-ttu-id="758b3-108">この方法で要素へのアクセスを制限するには、`Private` を使用して宣言できます。</span><span class="sxs-lookup"><span data-stu-id="758b3-108">To limit access to an element in this way, you can declare it with `Private`.</span></span>  

> [!NOTE]
> <span data-ttu-id="758b3-109">また、[Private Protected](private-protected.md) アクセス修飾子を使用することもできます。これにより、メンバーには、クラス内から、および包含アセンブリにある派生クラスからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="758b3-109">You can also use the [Private Protected](private-protected.md) access modifier, which makes a member accessible from within that class and from derived classes located in its containing assembly.</span></span>

## <a name="rules"></a><span data-ttu-id="758b3-110">ルール</span><span class="sxs-lookup"><span data-stu-id="758b3-110">Rules</span></span>  

- <span data-ttu-id="758b3-111">**宣言コンテキスト。**</span><span class="sxs-lookup"><span data-stu-id="758b3-111">**Declaration Context.**</span></span> <span data-ttu-id="758b3-112">`Private` は、モジュール レベルでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="758b3-112">You can use `Private` only at module level.</span></span> <span data-ttu-id="758b3-113">つまり、`Private` 要素の宣言コンテキストは、モジュール、クラス、または構造体にする必要があり、ソース ファイル、名前空間、インターフェイス、またはプロシージャにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="758b3-113">This means the declaration context for a `Private` element must be a module, class, or structure, and cannot be a source file, namespace, interface, or procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="758b3-114">動作</span><span class="sxs-lookup"><span data-stu-id="758b3-114">Behavior</span></span>  
  
- <span data-ttu-id="758b3-115">**アクセス レベル。**</span><span class="sxs-lookup"><span data-stu-id="758b3-115">**Access Level.**</span></span> <span data-ttu-id="758b3-116">宣言コンテキスト内のすべてのコードは、その `Private` 要素にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="758b3-116">All code within a declaration context can access its `Private` elements.</span></span> <span data-ttu-id="758b3-117">これには、入れ子になったクラスや列挙内の代入式など、含まれている型内のコードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="758b3-117">This includes code within a contained type, such as a nested class or an assignment expression in an enumeration.</span></span> <span data-ttu-id="758b3-118">宣言コンテキストの外側のコードは、その `Private` 要素にアクセスすることはできません。</span><span class="sxs-lookup"><span data-stu-id="758b3-118">No code outside of the declaration context can access its `Private` elements.</span></span>  
  
- <span data-ttu-id="758b3-119">**アクセス修飾子。**</span><span class="sxs-lookup"><span data-stu-id="758b3-119">**Access Modifiers.**</span></span> <span data-ttu-id="758b3-120">アクセス レベルを指定するキーワードは、*アクセス修飾子* と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="758b3-120">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="758b3-121">アクセス修飾子の比較については、「[Visual Basic でのアクセス レベル](../../programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="758b3-121">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="758b3-122">`Private` 修飾子は、次のコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="758b3-122">The `Private` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="758b3-123">Class ステートメント</span><span class="sxs-lookup"><span data-stu-id="758b3-123">Class Statement</span></span>](../statements/class-statement.md)  
  
 [<span data-ttu-id="758b3-124">Const ステートメント</span><span class="sxs-lookup"><span data-stu-id="758b3-124">Const Statement</span></span>](../statements/const-statement.md)  
  
 [<span data-ttu-id="758b3-125">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="758b3-125">Declare Statement</span></span>](../statements/declare-statement.md)  
  
 [<span data-ttu-id="758b3-126">Delegate ステートメント</span><span class="sxs-lookup"><span data-stu-id="758b3-126">Delegate Statement</span></span>](../statements/delegate-statement.md)  
  
 [<span data-ttu-id="758b3-127">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="758b3-127">Dim Statement</span></span>](../statements/dim-statement.md)  
  
 [<span data-ttu-id="758b3-128">Enum ステートメント</span><span class="sxs-lookup"><span data-stu-id="758b3-128">Enum Statement</span></span>](../statements/enum-statement.md)  
  
 [<span data-ttu-id="758b3-129">Event ステートメント</span><span class="sxs-lookup"><span data-stu-id="758b3-129">Event Statement</span></span>](../statements/event-statement.md)  
  
 [<span data-ttu-id="758b3-130">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="758b3-130">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="758b3-131">Interface ステートメント</span><span class="sxs-lookup"><span data-stu-id="758b3-131">Interface Statement</span></span>](../statements/interface-statement.md)  
  
 [<span data-ttu-id="758b3-132">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="758b3-132">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="758b3-133">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="758b3-133">Structure Statement</span></span>](../statements/structure-statement.md)  
  
 [<span data-ttu-id="758b3-134">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="758b3-134">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="758b3-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="758b3-135">See also</span></span>

- [<span data-ttu-id="758b3-136">Public</span><span class="sxs-lookup"><span data-stu-id="758b3-136">Public</span></span>](public.md)
- [<span data-ttu-id="758b3-137">Protected</span><span class="sxs-lookup"><span data-stu-id="758b3-137">Protected</span></span>](protected.md)
- [<span data-ttu-id="758b3-138">Friend</span><span class="sxs-lookup"><span data-stu-id="758b3-138">Friend</span></span>](friend.md)
- [<span data-ttu-id="758b3-139">Private Protected</span><span class="sxs-lookup"><span data-stu-id="758b3-139">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="758b3-140">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="758b3-140">Protected Friend</span></span>](./protected-friend.md)
- [<span data-ttu-id="758b3-141">Visual Basic でのアクセス レベル</span><span class="sxs-lookup"><span data-stu-id="758b3-141">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="758b3-142">手順</span><span class="sxs-lookup"><span data-stu-id="758b3-142">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="758b3-143">構造体</span><span class="sxs-lookup"><span data-stu-id="758b3-143">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="758b3-144">クラスとオブジェクト</span><span class="sxs-lookup"><span data-stu-id="758b3-144">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
