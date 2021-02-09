---
description: '詳細情報: Friend (Visual Basic)'
title: Friend
ms.date: 07/20/2015
f1_keywords:
- vb.Friend
helpviewer_keywords:
- Friend keyword [Visual Basic]
- Friend access modifier
- Friend keyword [Visual Basic], syntax
- Protected Friend keyword combination
- Friend keyword [Visual Basic], and Protected
ms.assetid: b664605e-1c79-4728-b996-aa59c50846bc
ms.openlocfilehash: ef2444555c05d6a4b24048316e282d269d4b7f1b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774591"
---
# <a name="friend-visual-basic"></a><span data-ttu-id="cb6af-103">Friend (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb6af-103">Friend (Visual Basic)</span></span>

<span data-ttu-id="cb6af-104">1 つ以上の宣言されたプログラミング要素が、その宣言を含むアセンブリ内からのみアクセス可能であることを示します。</span><span class="sxs-lookup"><span data-stu-id="cb6af-104">Specifies that one or more declared programming elements are accessible only from within the assembly that contains their declaration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb6af-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="cb6af-105">Remarks</span></span>  

 <span data-ttu-id="cb6af-106">多くの場合、クラスや構造体などのプログラミング要素は、それを宣言するコンポーネントだけでなく、アセンブリ全体で使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb6af-106">In many cases, you want programming elements such as classes and structures to be used by the entire assembly, not only by the component that declares them.</span></span> <span data-ttu-id="cb6af-107">ただし、アセンブリ外部のコードからアクセスできないようにすることもできます (アプリケーションが専用のものである場合など)。</span><span class="sxs-lookup"><span data-stu-id="cb6af-107">However, you might not want them to be accessible by code outside the assembly (for example, if the application is proprietary).</span></span> <span data-ttu-id="cb6af-108">この方法で要素へのアクセスを制限する場合は、`Friend` 修飾子を使用して宣言できます。</span><span class="sxs-lookup"><span data-stu-id="cb6af-108">If you want to limit access to an element in this way, you can declare it by using the `Friend` modifier.</span></span>  
  
 <span data-ttu-id="cb6af-109">同じアセンブリにコンパイルされる他のクラス、構造体、およびモジュール内のコードは、そのアセンブリ内のすべての `Friend` 要素にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="cb6af-109">Code in other classes, structures, and modules that are compiled to the same assembly can access all the `Friend` elements in that assembly.</span></span>  
  
 <span data-ttu-id="cb6af-110">`Friend` アクセスは、多くの場合はアプリケーションのプログラミング要素に優先されるレベルであり、`Friend` はインターフェイス、モジュール、クラス、または構造体の既定のアクセス レベルです。</span><span class="sxs-lookup"><span data-stu-id="cb6af-110">`Friend` access is often the preferred level for an application's programming elements, and `Friend` is the default access level of an interface, a module, a class, or a structure.</span></span>  
  
 <span data-ttu-id="cb6af-111">`Friend` は、モジュール、インターフェイス、または名前空間レベルでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="cb6af-111">You can use `Friend` only at the module, interface, or namespace level.</span></span> <span data-ttu-id="cb6af-112">そのため、`Friend` 要素の宣言コンテキストはソース ファイル、名前空間、インターフェイス、モジュール、クラス、または構造体にする必要があり、プロシージャにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="cb6af-112">Therefore, the declaration context for a `Friend` element must be a source file, a namespace, an interface, a module, a class, or a structure; it can't be a procedure.</span></span>  

> [!NOTE]
> <span data-ttu-id="cb6af-113">また、[Protected Friend](protected-friend.md) アクセス修飾子を使用することもできます。これにより、クラス メンバーには、クラス内、派生クラス、およびクラスが定義されている同じアセンブリからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="cb6af-113">You can also use the [Protected Friend](protected-friend.md) access modifier, which makes a class member accessible from within that class, from derived classes, and from the same assembly in which the class is defined.</span></span> <span data-ttu-id="cb6af-114">クラス内および同じアセンブリ内の派生クラスからのメンバーへのアクセスを制限するには、[Private Protected](private-protected.md) アクセス修飾子を使用します。</span><span class="sxs-lookup"><span data-stu-id="cb6af-114">To restrict access to a member from within its class and from derived classes in the same assembly, you use the [Private Protected](private-protected.md) access modifier.</span></span>

 <span data-ttu-id="cb6af-115">`Friend` とその他のアクセス修飾子の比較については、「[Visual Basic でのアクセス レベル](../../programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb6af-115">For a comparison of `Friend` and the other access modifiers, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cb6af-116">別のアセンブリがフレンド アセンブリであることを指定できます。これにより、`Friend` としてマークされているすべての型とメンバーにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="cb6af-116">You can specify that another assembly is a friend assembly, which allows it to access all types and members that are marked as `Friend`.</span></span> <span data-ttu-id="cb6af-117">詳細については、[Friend アセンブリ](../../../standard/assembly/friend.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb6af-117">For more information, see [Friend Assemblies](../../../standard/assembly/friend.md).</span></span>

## <a name="example"></a><span data-ttu-id="cb6af-118">例</span><span class="sxs-lookup"><span data-stu-id="cb6af-118">Example</span></span>  

 <span data-ttu-id="cb6af-119">次のクラスは、`Friend` 修飾子を使用して、同じアセンブリ内の他のプログラミング要素が特定のメンバーにアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="cb6af-119">The following class uses the `Friend` modifier to allow other programming elements within the same assembly to access certain members.</span></span>  
  
 [!code-vb[VbVbalrAccessModifiers#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalraccessmodifiers/vb/class1.vb#1)]  
  
## <a name="usage"></a><span data-ttu-id="cb6af-120">使用方法</span><span class="sxs-lookup"><span data-stu-id="cb6af-120">Usage</span></span>  

 <span data-ttu-id="cb6af-121">`Friend` 修飾子は、次のコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="cb6af-121">You can use the `Friend` modifier in these contexts:</span></span>  
  
 [<span data-ttu-id="cb6af-122">Class ステートメント</span><span class="sxs-lookup"><span data-stu-id="cb6af-122">Class Statement</span></span>](../statements/class-statement.md)  
  
 [<span data-ttu-id="cb6af-123">Const ステートメント</span><span class="sxs-lookup"><span data-stu-id="cb6af-123">Const Statement</span></span>](../statements/const-statement.md)  
  
 [<span data-ttu-id="cb6af-124">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="cb6af-124">Declare Statement</span></span>](../statements/declare-statement.md)  
  
 [<span data-ttu-id="cb6af-125">Delegate ステートメント</span><span class="sxs-lookup"><span data-stu-id="cb6af-125">Delegate Statement</span></span>](../statements/delegate-statement.md)  
  
 [<span data-ttu-id="cb6af-126">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="cb6af-126">Dim Statement</span></span>](../statements/dim-statement.md)  
  
 [<span data-ttu-id="cb6af-127">Enum ステートメント</span><span class="sxs-lookup"><span data-stu-id="cb6af-127">Enum Statement</span></span>](../statements/enum-statement.md)  
  
 [<span data-ttu-id="cb6af-128">Event ステートメント</span><span class="sxs-lookup"><span data-stu-id="cb6af-128">Event Statement</span></span>](../statements/event-statement.md)  
  
 [<span data-ttu-id="cb6af-129">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="cb6af-129">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="cb6af-130">Interface ステートメント</span><span class="sxs-lookup"><span data-stu-id="cb6af-130">Interface Statement</span></span>](../statements/interface-statement.md)  
  
 [<span data-ttu-id="cb6af-131">Module ステートメント</span><span class="sxs-lookup"><span data-stu-id="cb6af-131">Module Statement</span></span>](../statements/module-statement.md)  
  
 [<span data-ttu-id="cb6af-132">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="cb6af-132">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="cb6af-133">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="cb6af-133">Structure Statement</span></span>](../statements/structure-statement.md)  
  
 [<span data-ttu-id="cb6af-134">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="cb6af-134">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="cb6af-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="cb6af-135">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="cb6af-136">Public</span><span class="sxs-lookup"><span data-stu-id="cb6af-136">Public</span></span>](public.md)
- [<span data-ttu-id="cb6af-137">Protected</span><span class="sxs-lookup"><span data-stu-id="cb6af-137">Protected</span></span>](protected.md)
- [<span data-ttu-id="cb6af-138">Private</span><span class="sxs-lookup"><span data-stu-id="cb6af-138">Private</span></span>](private.md)
- [<span data-ttu-id="cb6af-139">Private Protected</span><span class="sxs-lookup"><span data-stu-id="cb6af-139">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="cb6af-140">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="cb6af-140">Protected Friend</span></span>](./protected-friend.md)
- [<span data-ttu-id="cb6af-141">Visual Basic でのアクセス レベル</span><span class="sxs-lookup"><span data-stu-id="cb6af-141">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="cb6af-142">手順</span><span class="sxs-lookup"><span data-stu-id="cb6af-142">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="cb6af-143">構造体</span><span class="sxs-lookup"><span data-stu-id="cb6af-143">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="cb6af-144">クラスとオブジェクト</span><span class="sxs-lookup"><span data-stu-id="cb6af-144">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
