---
description: '詳細情報: Protected (Visual Basic)'
title: Protected
ms.date: 07/20/2015
f1_keywords:
- vb.Protected
helpviewer_keywords:
- Protected Friend keyword combination
- Protected keyword [Visual Basic], and Friend
- Protected keyword [Visual Basic], syntax
- Protected access modifier
- Protected keyword [Visual Basic]
ms.assetid: 74ad3d56-309f-49d2-b60c-1d0157d010e8
ms.openlocfilehash: 74a695e7c8ff06543a7118c935365e31af258171
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700937"
---
# <a name="protected-visual-basic"></a><span data-ttu-id="0aeaf-103">Protected (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0aeaf-103">Protected (Visual Basic)</span></span>

<span data-ttu-id="0aeaf-104">1 つ以上の宣言されたプログラミング要素を指定するメンバー アクセス修飾子は、独自のクラス内から、または派生クラスからのみアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="0aeaf-104">A member access modifier that specifies that one or more declared programming elements are accessible only from within their own class or from a derived class.</span></span>

## <a name="remarks"></a><span data-ttu-id="0aeaf-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="0aeaf-105">Remarks</span></span>

<span data-ttu-id="0aeaf-106">場合によっては、クラスで宣言されたプログラミング要素に機密データまたは制限コードが含まれていて、要素へのアクセスを制限する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0aeaf-106">Sometimes a programming element declared in a class contains sensitive data or restricted code, and you want to limit access to the element.</span></span> <span data-ttu-id="0aeaf-107">ただし、クラスが継承可能であり、派生クラスの階層を想定している場合は、これらの派生クラスがデータまたはコードにアクセスする必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="0aeaf-107">However, if the class is inheritable and you expect a hierarchy of derived classes, it might be necessary for these derived classes to access the data or code.</span></span> <span data-ttu-id="0aeaf-108">このような場合は、基底クラスとすべての派生クラスの両方から要素にアクセスできるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0aeaf-108">In such a case, you want the element to be accessible both from the base class and from all derived classes.</span></span> <span data-ttu-id="0aeaf-109">この方法で要素へのアクセスを制限するには、`Protected` を使用して宣言できます。</span><span class="sxs-lookup"><span data-stu-id="0aeaf-109">To limit access to an element in this manner, you can declare it with `Protected`.</span></span>

> [!NOTE]
> <span data-ttu-id="0aeaf-110">`Protected` アクセス修飾子は、次の 2 つの修飾子と組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="0aeaf-110">The `Protected` access modifier can be combined with two other modifiers:</span></span>
>
> - <span data-ttu-id="0aeaf-111">[Protected Friend](protected-friend.md) 修飾子は、クラス メンバーに、クラス内、派生クラス、およびクラスが定義されている同じアセンブリからアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="0aeaf-111">The [Protected Friend](protected-friend.md) modifier makes a class member accessible from within that class, from derived classes, and from the same assembly in which the class is defined.</span></span>
> - <span data-ttu-id="0aeaf-112">[Private Protected](private-protected.md) 修飾子は、派生型によってクラス メンバーにアクセスできるようにしますが、その包含アセンブリ内に限られます。</span><span class="sxs-lookup"><span data-stu-id="0aeaf-112">The [Private Protected](private-protected.md) modifier makes a class member accessible by derived types, but only within its containing assembly.</span></span>

## <a name="rules"></a><span data-ttu-id="0aeaf-113">ルール</span><span class="sxs-lookup"><span data-stu-id="0aeaf-113">Rules</span></span>

<span data-ttu-id="0aeaf-114">**宣言コンテキスト。**</span><span class="sxs-lookup"><span data-stu-id="0aeaf-114">**Declaration Context.**</span></span> <span data-ttu-id="0aeaf-115">`Protected` は、クラス レベルでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="0aeaf-115">You can use `Protected` only at the class level.</span></span> <span data-ttu-id="0aeaf-116">つまり、`Protected` 要素の宣言コンテキストはクラスにする必要があり、ソース ファイル、名前空間、インターフェイス、モジュール、構造体、またはプロシージャにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="0aeaf-116">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="behavior"></a><span data-ttu-id="0aeaf-117">動作</span><span class="sxs-lookup"><span data-stu-id="0aeaf-117">Behavior</span></span>

- <span data-ttu-id="0aeaf-118">**アクセス レベル。**</span><span class="sxs-lookup"><span data-stu-id="0aeaf-118">**Access Level.**</span></span> <span data-ttu-id="0aeaf-119">クラス内のすべてのコードで、その要素にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="0aeaf-119">All code in a class can access its elements.</span></span> <span data-ttu-id="0aeaf-120">基底クラスから派生するすべてのクラスのコードで、基底クラスのすべての `Protected` 要素にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="0aeaf-120">Code in any class that derives from a base class can access all the `Protected` elements of the base class.</span></span> <span data-ttu-id="0aeaf-121">これは、派生のすべての世代に当てはまります。</span><span class="sxs-lookup"><span data-stu-id="0aeaf-121">This is true for all generations of derivation.</span></span> <span data-ttu-id="0aeaf-122">これは、クラスが基底クラスの基底クラスの `Protected` 要素にアクセスでき、以下同様に続くことを意味します。</span><span class="sxs-lookup"><span data-stu-id="0aeaf-122">This means that a class can access `Protected` elements of the base class of the base class, and so on.</span></span>

     <span data-ttu-id="0aeaf-123">保護されたアクセスは、フレンド アクセスのスーパーセットまたはサブセットではありません。</span><span class="sxs-lookup"><span data-stu-id="0aeaf-123">Protected access is not a superset or subset of friend access.</span></span>

- <span data-ttu-id="0aeaf-124">**アクセス修飾子。**</span><span class="sxs-lookup"><span data-stu-id="0aeaf-124">**Access Modifiers.**</span></span> <span data-ttu-id="0aeaf-125">アクセス レベルを指定するキーワードは、*アクセス修飾子* と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="0aeaf-125">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="0aeaf-126">アクセス修飾子の比較については、「[Visual Basic でのアクセス レベル](../../programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0aeaf-126">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="0aeaf-127">`Protected` 修飾子は、次のコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="0aeaf-127">The `Protected` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="0aeaf-128">Class ステートメント</span><span class="sxs-lookup"><span data-stu-id="0aeaf-128">Class Statement</span></span>](../statements/class-statement.md)

- [<span data-ttu-id="0aeaf-129">Const ステートメント</span><span class="sxs-lookup"><span data-stu-id="0aeaf-129">Const Statement</span></span>](../statements/const-statement.md)

- [<span data-ttu-id="0aeaf-130">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="0aeaf-130">Declare Statement</span></span>](../statements/declare-statement.md)

- [<span data-ttu-id="0aeaf-131">Delegate ステートメント</span><span class="sxs-lookup"><span data-stu-id="0aeaf-131">Delegate Statement</span></span>](../statements/delegate-statement.md)

- [<span data-ttu-id="0aeaf-132">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="0aeaf-132">Dim Statement</span></span>](../statements/dim-statement.md)

- [<span data-ttu-id="0aeaf-133">Enum ステートメント</span><span class="sxs-lookup"><span data-stu-id="0aeaf-133">Enum Statement</span></span>](../statements/enum-statement.md)

- [<span data-ttu-id="0aeaf-134">Event ステートメント</span><span class="sxs-lookup"><span data-stu-id="0aeaf-134">Event Statement</span></span>](../statements/event-statement.md)

- [<span data-ttu-id="0aeaf-135">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="0aeaf-135">Function Statement</span></span>](../statements/function-statement.md)

- [<span data-ttu-id="0aeaf-136">Interface ステートメント</span><span class="sxs-lookup"><span data-stu-id="0aeaf-136">Interface Statement</span></span>](../statements/interface-statement.md)

- [<span data-ttu-id="0aeaf-137">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="0aeaf-137">Property Statement</span></span>](../statements/property-statement.md)

- [<span data-ttu-id="0aeaf-138">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="0aeaf-138">Structure Statement</span></span>](../statements/structure-statement.md)

- [<span data-ttu-id="0aeaf-139">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="0aeaf-139">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="0aeaf-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="0aeaf-140">See also</span></span>

- [<span data-ttu-id="0aeaf-141">Public</span><span class="sxs-lookup"><span data-stu-id="0aeaf-141">Public</span></span>](public.md)
- [<span data-ttu-id="0aeaf-142">Friend</span><span class="sxs-lookup"><span data-stu-id="0aeaf-142">Friend</span></span>](friend.md)
- [<span data-ttu-id="0aeaf-143">Private</span><span class="sxs-lookup"><span data-stu-id="0aeaf-143">Private</span></span>](private.md)
- [<span data-ttu-id="0aeaf-144">Private Protected</span><span class="sxs-lookup"><span data-stu-id="0aeaf-144">Private Protected</span></span>](private-protected.md)
- [<span data-ttu-id="0aeaf-145">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="0aeaf-145">Protected Friend</span></span>](protected-friend.md)
- [<span data-ttu-id="0aeaf-146">Visual Basic でのアクセス レベル</span><span class="sxs-lookup"><span data-stu-id="0aeaf-146">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="0aeaf-147">手順</span><span class="sxs-lookup"><span data-stu-id="0aeaf-147">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="0aeaf-148">構造体</span><span class="sxs-lookup"><span data-stu-id="0aeaf-148">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="0aeaf-149">クラスとオブジェクト</span><span class="sxs-lookup"><span data-stu-id="0aeaf-149">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
