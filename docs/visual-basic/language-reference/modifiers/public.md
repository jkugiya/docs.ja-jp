---
description: '詳細情報: Public (Visual Basic)'
title: Public
ms.date: 07/20/2015
f1_keywords:
- vb.Public
helpviewer_keywords:
- Public keyword [Visual Basic]
- Public keyword [Visual Basic], syntax
- Public access modifier
ms.assetid: 284c9e1b-ed23-499b-9bc9-ad87c11485a5
ms.openlocfilehash: 1083ca877cf99917291523fe10f6561784ff06a2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700924"
---
# <a name="public-visual-basic"></a><span data-ttu-id="74126-103">Public (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="74126-103">Public (Visual Basic)</span></span>

<span data-ttu-id="74126-104">1 つ以上の宣言されたプログラミング要素にアクセス制限がないことを示します。</span><span class="sxs-lookup"><span data-stu-id="74126-104">Specifies that one or more declared programming elements have no access restrictions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74126-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="74126-105">Remarks</span></span>  

 <span data-ttu-id="74126-106">クラス ライブラリなどのコンポーネントまたはコンポーネントのセットを公開する場合は、通常、アセンブリと相互運用できるコードでプログラミング要素にアクセスできるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="74126-106">If you are publishing a component or set of components, such as a class library, you usually want the programming elements to be accessible by any code that interoperates with your assembly.</span></span> <span data-ttu-id="74126-107">要素に対してこのような無制限のアクセス権を付与するには、`Public` で宣言します。</span><span class="sxs-lookup"><span data-stu-id="74126-107">To confer such unlimited access on an element, you can declare it with `Public`.</span></span>  
  
 <span data-ttu-id="74126-108">パブリック アクセスは、プログラミング要素へのアクセスを制限する必要がない場合の通常のレベルです。</span><span class="sxs-lookup"><span data-stu-id="74126-108">Public access is the normal level for a programming element when you do not need to limit access to it.</span></span> <span data-ttu-id="74126-109">インターフェイス、モジュール、クラス、または構造体で宣言されている要素のアクセス レベルは、宣言しない場合、既定では `Public` になることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="74126-109">Note that the access level of an element declared within an interface, module, class, or structure defaults to `Public` if you do not declare it otherwise.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="74126-110">ルール</span><span class="sxs-lookup"><span data-stu-id="74126-110">Rules</span></span>  
  
- <span data-ttu-id="74126-111">**宣言コンテキスト。**</span><span class="sxs-lookup"><span data-stu-id="74126-111">**Declaration Context.**</span></span> <span data-ttu-id="74126-112">`Public` は、モジュール、インターフェイス、または名前空間レベルでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="74126-112">You can use `Public` only at module, interface, or namespace level.</span></span> <span data-ttu-id="74126-113">つまり、`Public` 要素の宣言コンテキストは、ソース ファイル、名前空間、インターフェイス、モジュール、クラス、または構造体にする必要があり、プロシージャにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="74126-113">This means the declaration context for a `Public` element must be a source file, namespace, interface, module, class, or structure, and cannot be a procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="74126-114">動作</span><span class="sxs-lookup"><span data-stu-id="74126-114">Behavior</span></span>  
  
- <span data-ttu-id="74126-115">**アクセス レベル。**</span><span class="sxs-lookup"><span data-stu-id="74126-115">**Access Level.**</span></span> <span data-ttu-id="74126-116">モジュール、クラス、または構造体にアクセスできるすべてのコードは、その `Public` 要素にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="74126-116">All code that can access a module, class, or structure can access its `Public` elements.</span></span>  
  
- <span data-ttu-id="74126-117">**既定のアクセス。**</span><span class="sxs-lookup"><span data-stu-id="74126-117">**Default Access.**</span></span> <span data-ttu-id="74126-118">プロシージャ内のローカル変数は、既定でパブリック アクセスに設定されていて、それらでアクセス修飾子を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="74126-118">Local variables inside a procedure default to public access, and you cannot use any access modifiers on them.</span></span>  
  
- <span data-ttu-id="74126-119">**アクセス修飾子。**</span><span class="sxs-lookup"><span data-stu-id="74126-119">**Access Modifiers.**</span></span> <span data-ttu-id="74126-120">アクセス レベルを指定するキーワードは、*アクセス修飾子* と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="74126-120">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="74126-121">アクセス修飾子の比較については、「[Visual Basic でのアクセス レベル](../../programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="74126-121">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="74126-122">`Public` 修飾子は、次のコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="74126-122">The `Public` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="74126-123">Class ステートメント</span><span class="sxs-lookup"><span data-stu-id="74126-123">Class Statement</span></span>](../statements/class-statement.md)  
  
 [<span data-ttu-id="74126-124">Const ステートメント</span><span class="sxs-lookup"><span data-stu-id="74126-124">Const Statement</span></span>](../statements/const-statement.md)  
  
 [<span data-ttu-id="74126-125">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="74126-125">Declare Statement</span></span>](../statements/declare-statement.md)  
  
 [<span data-ttu-id="74126-126">Delegate ステートメント</span><span class="sxs-lookup"><span data-stu-id="74126-126">Delegate Statement</span></span>](../statements/delegate-statement.md)  
  
 [<span data-ttu-id="74126-127">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="74126-127">Dim Statement</span></span>](../statements/dim-statement.md)  
  
 [<span data-ttu-id="74126-128">Enum ステートメント</span><span class="sxs-lookup"><span data-stu-id="74126-128">Enum Statement</span></span>](../statements/enum-statement.md)  
  
 [<span data-ttu-id="74126-129">Event ステートメント</span><span class="sxs-lookup"><span data-stu-id="74126-129">Event Statement</span></span>](../statements/event-statement.md)  
  
 [<span data-ttu-id="74126-130">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="74126-130">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="74126-131">Interface ステートメント</span><span class="sxs-lookup"><span data-stu-id="74126-131">Interface Statement</span></span>](../statements/interface-statement.md)  
  
 [<span data-ttu-id="74126-132">Module ステートメント</span><span class="sxs-lookup"><span data-stu-id="74126-132">Module Statement</span></span>](../statements/module-statement.md)  
  
 [<span data-ttu-id="74126-133">Operator ステートメント</span><span class="sxs-lookup"><span data-stu-id="74126-133">Operator Statement</span></span>](../statements/operator-statement.md)  
  
 [<span data-ttu-id="74126-134">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="74126-134">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="74126-135">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="74126-135">Structure Statement</span></span>](../statements/structure-statement.md)  
  
 [<span data-ttu-id="74126-136">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="74126-136">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="74126-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="74126-137">See also</span></span>

- [<span data-ttu-id="74126-138">Protected</span><span class="sxs-lookup"><span data-stu-id="74126-138">Protected</span></span>](protected.md)
- [<span data-ttu-id="74126-139">Friend</span><span class="sxs-lookup"><span data-stu-id="74126-139">Friend</span></span>](friend.md)
- [<span data-ttu-id="74126-140">Private</span><span class="sxs-lookup"><span data-stu-id="74126-140">Private</span></span>](private.md)
- [<span data-ttu-id="74126-141">Private Protected</span><span class="sxs-lookup"><span data-stu-id="74126-141">Private Protected</span></span>](private-protected.md)
- [<span data-ttu-id="74126-142">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="74126-142">Protected Friend</span></span>](protected-friend.md)
- [<span data-ttu-id="74126-143">Visual Basic でのアクセス レベル</span><span class="sxs-lookup"><span data-stu-id="74126-143">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="74126-144">手順</span><span class="sxs-lookup"><span data-stu-id="74126-144">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="74126-145">構造体</span><span class="sxs-lookup"><span data-stu-id="74126-145">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="74126-146">クラスとオブジェクト</span><span class="sxs-lookup"><span data-stu-id="74126-146">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
