---
description: '詳細情報: Shadows (Visual Basic)'
title: Overloads
ms.date: 07/20/2015
f1_keywords:
- vb.Shadows
- shadows
helpviewer_keywords:
- shadowing
- duplicate names [Visual Basic]
- scope [Visual Basic], shadowing
- Shadows keyword [Visual Basic]
- names [Visual Basic], shadowing
ms.assetid: 6bf687cd-0544-4797-b51b-911125ec57c6
ms.openlocfilehash: 4a455a78c36e15db977936b81c22e7a5b03d107e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700846"
---
# <a name="shadows-visual-basic"></a><span data-ttu-id="74859-103">Shadows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="74859-103">Shadows (Visual Basic)</span></span>

<span data-ttu-id="74859-104">宣言されたプログラミング要素が、基底クラスにある、同じ名前を持つ要素、またはオーバーロードされる要素のセットを宣言し直して非表示にすることを示します。</span><span class="sxs-lookup"><span data-stu-id="74859-104">Specifies that a declared programming element redeclares and hides an identically named element, or set of overloaded elements, in a base class.</span></span>

## <a name="remarks"></a><span data-ttu-id="74859-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="74859-105">Remarks</span></span>

<span data-ttu-id="74859-106">シャドウ (*名前による非表示* とも呼ばれます) の主な目的は、クラス メンバーの定義を保持することです。</span><span class="sxs-lookup"><span data-stu-id="74859-106">The main purpose of shadowing (which is also known as *hiding by name*) is to preserve the definition of your class members.</span></span> <span data-ttu-id="74859-107">基底クラスには、既に定義されているものと同じ名前の要素を作成する変更が含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="74859-107">The base class might undergo a change that creates an element with the same name as one you have already defined.</span></span> <span data-ttu-id="74859-108">この場合、`Shadows` 修飾子は、クラスによる参照が、新しい基底クラス要素ではなく定義したメンバーに強制的に解決されるようにします。</span><span class="sxs-lookup"><span data-stu-id="74859-108">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span></span>

<span data-ttu-id="74859-109">シャドウとオーバーライドは、どちらも継承された要素を再定義しますが、その方法は大きく異なります。</span><span class="sxs-lookup"><span data-stu-id="74859-109">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="74859-110">詳細については、「[Visual Basic におけるシャドウ](../../programming-guide/language-features/declared-elements/shadowing.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="74859-110">For more information, see [Shadowing in Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span></span>

## <a name="rules"></a><span data-ttu-id="74859-111">ルール</span><span class="sxs-lookup"><span data-stu-id="74859-111">Rules</span></span>

- <span data-ttu-id="74859-112">**宣言コンテキスト。**</span><span class="sxs-lookup"><span data-stu-id="74859-112">**Declaration Context.**</span></span> <span data-ttu-id="74859-113">`Shadows` は、クラス レベルでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="74859-113">You can use `Shadows` only at class level.</span></span> <span data-ttu-id="74859-114">つまり、`Shadows` 要素の宣言コンテキストはクラスにする必要があり、ソース ファイル、名前空間、インターフェイス、モジュール、構造体、またはプロシージャにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="74859-114">This means the declaration context for a `Shadows` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

  <span data-ttu-id="74859-115">1 つの宣言ステートメントでは、シャドウ要素を 1 つだけ宣言できます。</span><span class="sxs-lookup"><span data-stu-id="74859-115">You can declare only one shadowing element in a single declaration statement.</span></span>

- <span data-ttu-id="74859-116">**結合された修飾子。**</span><span class="sxs-lookup"><span data-stu-id="74859-116">**Combined Modifiers.**</span></span> <span data-ttu-id="74859-117">同じ宣言内で `Shadows` を `Overloads`、`Overrides`、または `Static` と共に指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="74859-117">You cannot specify `Shadows` together with `Overloads`, `Overrides`, or `Static` in the same declaration.</span></span>

- <span data-ttu-id="74859-118">**要素型。**</span><span class="sxs-lookup"><span data-stu-id="74859-118">**Element Types.**</span></span> <span data-ttu-id="74859-119">宣言された要素は、他の任意の種類の要素でシャドウできます。</span><span class="sxs-lookup"><span data-stu-id="74859-119">You can shadow any kind of declared element with any other kind.</span></span> <span data-ttu-id="74859-120">別のプロパティまたはプロシージャを使用してプロパティまたはプロシージャをシャドウする場合、パラメーターと戻り値の型が基底クラスのプロパティまたはプロシージャ内のパラメーターと一致する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="74859-120">If you shadow a property or procedure with another property or procedure, the parameters and the return type do not have to match those in the base class property or procedure.</span></span>

- <span data-ttu-id="74859-121">**アクセス。**</span><span class="sxs-lookup"><span data-stu-id="74859-121">**Accessing.**</span></span> <span data-ttu-id="74859-122">基底クラス内のシャドウされた要素は、通常、それをシャドウする派生クラス内からは使用できません。</span><span class="sxs-lookup"><span data-stu-id="74859-122">The shadowed element in the base class is normally unavailable from within the derived class that shadows it.</span></span> <span data-ttu-id="74859-123">ただし、次の考慮事項が適用されます。</span><span class="sxs-lookup"><span data-stu-id="74859-123">However, the following considerations apply.</span></span>

  - <span data-ttu-id="74859-124">シャドウ要素が、それを参照するコードからアクセスできない場合、参照はシャドウされた要素に解決されます。</span><span class="sxs-lookup"><span data-stu-id="74859-124">If the shadowing element is not accessible from the code referring to it, the reference is resolved to the shadowed element.</span></span> <span data-ttu-id="74859-125">たとえば、`Private` 要素が基底クラスの要素をシャドウすると、`Private` 要素へのアクセス許可を持たないコードが、代わりに基底クラスの要素にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="74859-125">For example, if a `Private` element shadows a base class element, code that does not have permission to access the `Private` element accesses the base class element instead.</span></span>

  - <span data-ttu-id="74859-126">要素をシャドウする場合でも、基底クラスの型で宣言されたオブジェクトを使用して、シャドウされた要素にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="74859-126">If you shadow an element, you can still access the shadowed element through an object declared with the type of the base class.</span></span> <span data-ttu-id="74859-127">また、`MyBase` を使用してアクセスすることもできます。</span><span class="sxs-lookup"><span data-stu-id="74859-127">You can also access it through `MyBase`.</span></span>

<span data-ttu-id="74859-128">`Shadows` 修飾子は、次のコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="74859-128">The `Shadows` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="74859-129">Class ステートメント</span><span class="sxs-lookup"><span data-stu-id="74859-129">Class Statement</span></span>](../statements/class-statement.md)

- [<span data-ttu-id="74859-130">Const ステートメント</span><span class="sxs-lookup"><span data-stu-id="74859-130">Const Statement</span></span>](../statements/const-statement.md)

- [<span data-ttu-id="74859-131">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="74859-131">Declare Statement</span></span>](../statements/declare-statement.md)

- [<span data-ttu-id="74859-132">Delegate ステートメント</span><span class="sxs-lookup"><span data-stu-id="74859-132">Delegate Statement</span></span>](../statements/delegate-statement.md)

- [<span data-ttu-id="74859-133">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="74859-133">Dim Statement</span></span>](../statements/dim-statement.md)

- [<span data-ttu-id="74859-134">Enum ステートメント</span><span class="sxs-lookup"><span data-stu-id="74859-134">Enum Statement</span></span>](../statements/enum-statement.md)

- [<span data-ttu-id="74859-135">Event ステートメント</span><span class="sxs-lookup"><span data-stu-id="74859-135">Event Statement</span></span>](../statements/event-statement.md)

- [<span data-ttu-id="74859-136">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="74859-136">Function Statement</span></span>](../statements/function-statement.md)

- [<span data-ttu-id="74859-137">Interface ステートメント</span><span class="sxs-lookup"><span data-stu-id="74859-137">Interface Statement</span></span>](../statements/interface-statement.md)

- [<span data-ttu-id="74859-138">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="74859-138">Property Statement</span></span>](../statements/property-statement.md)

- [<span data-ttu-id="74859-139">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="74859-139">Structure Statement</span></span>](../statements/structure-statement.md)

- [<span data-ttu-id="74859-140">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="74859-140">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="74859-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="74859-141">See also</span></span>

- [<span data-ttu-id="74859-142">Shared</span><span class="sxs-lookup"><span data-stu-id="74859-142">Shared</span></span>](shared.md)
- [<span data-ttu-id="74859-143">Static</span><span class="sxs-lookup"><span data-stu-id="74859-143">Static</span></span>](static.md)
- [<span data-ttu-id="74859-144">Private</span><span class="sxs-lookup"><span data-stu-id="74859-144">Private</span></span>](private.md)
- [<span data-ttu-id="74859-145">Me、My、MyBase、および MyClass</span><span class="sxs-lookup"><span data-stu-id="74859-145">Me, My, MyBase, and MyClass</span></span>](../../programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="74859-146">継承の基本</span><span class="sxs-lookup"><span data-stu-id="74859-146">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="74859-147">MustOverride</span><span class="sxs-lookup"><span data-stu-id="74859-147">MustOverride</span></span>](mustoverride.md)
- [<span data-ttu-id="74859-148">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="74859-148">NotOverridable</span></span>](notoverridable.md)
- [<span data-ttu-id="74859-149">Overloads</span><span class="sxs-lookup"><span data-stu-id="74859-149">Overloads</span></span>](overloads.md)
- [<span data-ttu-id="74859-150">Overridable</span><span class="sxs-lookup"><span data-stu-id="74859-150">Overridable</span></span>](overridable.md)
- [<span data-ttu-id="74859-151">Overrides</span><span class="sxs-lookup"><span data-stu-id="74859-151">Overrides</span></span>](overrides.md)
- [<span data-ttu-id="74859-152">Visual Basic におけるシャドウ</span><span class="sxs-lookup"><span data-stu-id="74859-152">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
