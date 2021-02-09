---
description: '詳細情報: Private Protected (Visual Basic)'
title: Private Protected
ms.date: 05/10/2018
f1_keywords:
- vb.PrivateProtected
helpviewer_keywords:
- Private Protected keyword [Visual Basic]
- Private Protected keyword [Visual Basic], syntax
ms.openlocfilehash: eb521ace77cd16f4904657cbdc035575e98e98fa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700963"
---
# <a name="private-protected-visual-basic"></a><span data-ttu-id="8b0f1-103">Private Protected (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b0f1-103">Private Protected (Visual Basic)</span></span>

<span data-ttu-id="8b0f1-104">キーワード組み合わせ `Private Protected` はメンバー アクセス修飾子です。</span><span class="sxs-lookup"><span data-stu-id="8b0f1-104">The `Private Protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="8b0f1-105">`Private Protected` メンバーは、その親クラスのすべてのメンバーと、親クラスから派生した型でアクセスできますが、それらがその親アセンブリにも存在する場合に限られます。</span><span class="sxs-lookup"><span data-stu-id="8b0f1-105">A `Private Protected` member is accessible by all members in its containing class, as well as by types derived from the containing class, but only if they are found in its containing assembly.</span></span>

<span data-ttu-id="8b0f1-106">`Private Protected` は、クラスのメンバーに対してのみ指定できます。構造体は継承できないため、構造体のメンバーに `Private Protected` を適用することはできません。</span><span class="sxs-lookup"><span data-stu-id="8b0f1-106">You can specify `Private Protected` only on members of classes; you cannot apply `Private Protected` to members of a structure because structures cannot be inherited.</span></span>

<span data-ttu-id="8b0f1-107">`Private Protected` アクセス修飾子は Visual Basic 15.5 以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="8b0f1-107">The `Private Protected` access modifier is supported by Visual Basic 15.5 and later.</span></span> <span data-ttu-id="8b0f1-108">これを使用するには、次の要素を Visual Basic プロジェクト (\*.vbproj) ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="8b0f1-108">To use it, you can add the following element to your Visual Basic project (\*.vbproj) file.</span></span> <span data-ttu-id="8b0f1-109">システムに Visual Basic 15.5 以降がインストールされている限り、Visual Basic コンパイラの最新バージョンでサポートされているすべての言語機能を利用できます。</span><span class="sxs-lookup"><span data-stu-id="8b0f1-109">As long as Visual Basic 15.5 or later is installed on your system, it lets you take advantage of all the language features supported by the latest version of the Visual Basic compiler:</span></span>

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="8b0f1-110">詳細については、[Visual Basic 言語バージョンの設定](../configure-language-version.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8b0f1-110">For more information see [setting the Visual Basic language version](../configure-language-version.md).</span></span>

> [!NOTE]
> <span data-ttu-id="8b0f1-111">Visual Studio で、`private protected` に対して F1 ヘルプを選択すると、[private](private.md) または [protected](protected.md) のヘルプが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8b0f1-111">In Visual Studio, selecting F1 help on `private protected` provides help for either [private](private.md) or [protected](protected.md).</span></span> <span data-ttu-id="8b0f1-112">IDE では、複合語ではなくカーソルの下にある 1 つのトークンが選択されます。</span><span class="sxs-lookup"><span data-stu-id="8b0f1-112">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="8b0f1-113">ルール</span><span class="sxs-lookup"><span data-stu-id="8b0f1-113">Rules</span></span>

- <span data-ttu-id="8b0f1-114">**宣言コンテキスト。**</span><span class="sxs-lookup"><span data-stu-id="8b0f1-114">**Declaration Context.**</span></span> <span data-ttu-id="8b0f1-115">`Private Protected` は、クラス レベルでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="8b0f1-115">You can use `Private Protected` only at the class level.</span></span> <span data-ttu-id="8b0f1-116">つまり、`Protected` 要素の宣言コンテキストはクラスにする必要があり、ソース ファイル、名前空間、インターフェイス、モジュール、構造体、またはプロシージャにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="8b0f1-116">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="behavior"></a><span data-ttu-id="8b0f1-117">動作</span><span class="sxs-lookup"><span data-stu-id="8b0f1-117">Behavior</span></span>

- <span data-ttu-id="8b0f1-118">**アクセス レベル。**</span><span class="sxs-lookup"><span data-stu-id="8b0f1-118">**Access Level.**</span></span> <span data-ttu-id="8b0f1-119">クラス内のすべてのコードで、その要素にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="8b0f1-119">All code in a class can access its elements.</span></span> <span data-ttu-id="8b0f1-120">基底クラスから派生し、同じアセンブリに含まれるすべてのクラスのコードで、基底クラスのすべての `Private Protected` 要素にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="8b0f1-120">Code in any class that derives from a base class and is contained in the same assembly can access all the `Private Protected` elements of the base class.</span></span> <span data-ttu-id="8b0f1-121">ただし、基底クラスから派生し、別のアセンブリに含まれるクラスのコードでは、基底クラスの `Private Protected` 要素にアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="8b0f1-121">However, code in any class that derives from a base class and is contained in a different assembly can't access the base class `Private Protected` elements.</span></span>

- <span data-ttu-id="8b0f1-122">**アクセス修飾子。**</span><span class="sxs-lookup"><span data-stu-id="8b0f1-122">**Access Modifiers.**</span></span> <span data-ttu-id="8b0f1-123">アクセス レベルを指定するキーワードは、*アクセス修飾子* と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="8b0f1-123">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="8b0f1-124">アクセス修飾子の比較については、「[Visual Basic でのアクセス レベル](../../programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8b0f1-124">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="8b0f1-125">`Private Protected` 修飾子は、次のコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="8b0f1-125">The `Private Protected` modifier can be used in these contexts:</span></span>

- <span data-ttu-id="8b0f1-126">入れ子になったクラスの [Class ステートメント](../statements/class-statement.md)</span><span class="sxs-lookup"><span data-stu-id="8b0f1-126">[Class Statement](../statements/class-statement.md) of a nested class</span></span>

- [<span data-ttu-id="8b0f1-127">Const ステートメント</span><span class="sxs-lookup"><span data-stu-id="8b0f1-127">Const Statement</span></span>](../statements/const-statement.md)

- [<span data-ttu-id="8b0f1-128">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="8b0f1-128">Declare Statement</span></span>](../statements/declare-statement.md)

- <span data-ttu-id="8b0f1-129">クラスに入れ子にされたデリゲートの [Delegate ステートメント](../statements/delegate-statement.md)</span><span class="sxs-lookup"><span data-stu-id="8b0f1-129">[Delegate Statement](../statements/delegate-statement.md) of a delegate nested in a class</span></span>

- [<span data-ttu-id="8b0f1-130">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="8b0f1-130">Dim Statement</span></span>](../statements/dim-statement.md)

- <span data-ttu-id="8b0f1-131">クラスに入れ子にされた列挙型の [Enum ステートメント](../statements/enum-statement.md)</span><span class="sxs-lookup"><span data-stu-id="8b0f1-131">[Enum Statement](../statements/enum-statement.md) of an enumeration nested in a class</span></span>

- [<span data-ttu-id="8b0f1-132">Event ステートメント</span><span class="sxs-lookup"><span data-stu-id="8b0f1-132">Event Statement</span></span>](../statements/event-statement.md)

- [<span data-ttu-id="8b0f1-133">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="8b0f1-133">Function Statement</span></span>](../statements/function-statement.md)

- <span data-ttu-id="8b0f1-134">クラスに入れ子にされたインターフェイスの [Interface ステートメント](../statements/interface-statement.md)</span><span class="sxs-lookup"><span data-stu-id="8b0f1-134">[Interface Statement](../statements/interface-statement.md) of an interface nested in a class</span></span>

- [<span data-ttu-id="8b0f1-135">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="8b0f1-135">Property Statement</span></span>](../statements/property-statement.md)

- <span data-ttu-id="8b0f1-136">クラスに入れ子にされた構造体の[Structure ステートメント](../statements/structure-statement.md)</span><span class="sxs-lookup"><span data-stu-id="8b0f1-136">[Structure Statement](../statements/structure-statement.md) of a structure nested in a class</span></span>

- [<span data-ttu-id="8b0f1-137">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="8b0f1-137">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="8b0f1-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="8b0f1-138">See also</span></span>

- [<span data-ttu-id="8b0f1-139">Public</span><span class="sxs-lookup"><span data-stu-id="8b0f1-139">Public</span></span>](public.md)
- [<span data-ttu-id="8b0f1-140">Protected</span><span class="sxs-lookup"><span data-stu-id="8b0f1-140">Protected</span></span>](protected.md)
- [<span data-ttu-id="8b0f1-141">Friend</span><span class="sxs-lookup"><span data-stu-id="8b0f1-141">Friend</span></span>](friend.md)
- [<span data-ttu-id="8b0f1-142">Private</span><span class="sxs-lookup"><span data-stu-id="8b0f1-142">Private</span></span>](private.md)
- [<span data-ttu-id="8b0f1-143">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="8b0f1-143">Protected Friend</span></span>](./protected-friend.md)
- [<span data-ttu-id="8b0f1-144">Visual Basic でのアクセス レベル</span><span class="sxs-lookup"><span data-stu-id="8b0f1-144">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="8b0f1-145">手順</span><span class="sxs-lookup"><span data-stu-id="8b0f1-145">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="8b0f1-146">構造体</span><span class="sxs-lookup"><span data-stu-id="8b0f1-146">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="8b0f1-147">クラスとオブジェクト</span><span class="sxs-lookup"><span data-stu-id="8b0f1-147">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
