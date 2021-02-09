---
description: '詳細情報: Overloads (Visual Basic)'
title: Overloads
ms.date: 07/20/2015
f1_keywords:
- vb.Overloads
- Overloads
helpviewer_keywords:
- Overloads keyword [Visual Basic]
- hiding by signature
- Shadows keyword [Visual Basic]
- signature, hiding by
ms.assetid: 0c6820b8-25b2-4664-bc59-5ca93c99c042
ms.openlocfilehash: 7f0b440b537500595e465d8aabc7724671f3ae95
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99730513"
---
# <a name="overloads-visual-basic"></a><span data-ttu-id="32284-103">Overloads (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="32284-103">Overloads (Visual Basic)</span></span>

<span data-ttu-id="32284-104">プロパティまたはプロシージャが、同じ名前の 1 つ以上の既存のプロパティまたはプロシージャを再度宣言することを示します。</span><span class="sxs-lookup"><span data-stu-id="32284-104">Specifies that a property or procedure redeclares one or more existing properties or procedures with the same name.</span></span>

## <a name="remarks"></a><span data-ttu-id="32284-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="32284-105">Remarks</span></span>

<span data-ttu-id="32284-106">*オーバーロード* とは、特定のプロパティ名またはプロシージャ名に対し、同じスコープ内で複数の定義を与えることです。</span><span class="sxs-lookup"><span data-stu-id="32284-106">*Overloading* is the practice of supplying more than one definition for a given property or procedure name in the same scope.</span></span> <span data-ttu-id="32284-107">異なるシグネチャによるプロパティまたはプロシージャの再宣言は、*シグネチャによる隠ぺい* と呼ばれることがあります。</span><span class="sxs-lookup"><span data-stu-id="32284-107">Redeclaring a property or procedure with a different signature is sometimes called *hiding by signature*.</span></span>

## <a name="rules"></a><span data-ttu-id="32284-108">ルール</span><span class="sxs-lookup"><span data-stu-id="32284-108">Rules</span></span>

- <span data-ttu-id="32284-109">**宣言コンテキスト。**</span><span class="sxs-lookup"><span data-stu-id="32284-109">**Declaration Context.**</span></span> <span data-ttu-id="32284-110">`Overloads` は、プロパティまたはプロシージャの宣言ステートメントでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="32284-110">You can use `Overloads` only in a property or procedure declaration statement.</span></span>

- <span data-ttu-id="32284-111">**結合された修飾子。**</span><span class="sxs-lookup"><span data-stu-id="32284-111">**Combined Modifiers.**</span></span> <span data-ttu-id="32284-112">同じプロシージャ宣言内で `Overloads` を [Shadows](shadows.md) と共に指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="32284-112">You cannot specify `Overloads` together with [Shadows](shadows.md) in the same procedure declaration.</span></span>

- <span data-ttu-id="32284-113">**必要な相違点。**</span><span class="sxs-lookup"><span data-stu-id="32284-113">**Required Differences.**</span></span> <span data-ttu-id="32284-114">この宣言内の *シグネチャ* は、オーバーロードされるすべてのプロパティまたはプロシージャのシグネチャと異なる必要があります。</span><span class="sxs-lookup"><span data-stu-id="32284-114">The *signature* in this declaration must be different from the signature of every property or procedure that it overloads.</span></span> <span data-ttu-id="32284-115">シグネチャは、プロパティまたはプロシージャの名前と以下の項目で構成されます。</span><span class="sxs-lookup"><span data-stu-id="32284-115">The signature comprises the property or procedure name together with the following:</span></span>

  - <span data-ttu-id="32284-116">パラメーターの数</span><span class="sxs-lookup"><span data-stu-id="32284-116">the number of parameters</span></span>

  - <span data-ttu-id="32284-117">パラメーターの順序</span><span class="sxs-lookup"><span data-stu-id="32284-117">the order of the parameters</span></span>

  - <span data-ttu-id="32284-118">パラメーターのデータ型</span><span class="sxs-lookup"><span data-stu-id="32284-118">the data types of the parameters</span></span>

  - <span data-ttu-id="32284-119">型パラメーターの数 (ジェネリック プロシージャの場合)</span><span class="sxs-lookup"><span data-stu-id="32284-119">the number of type parameters (for a generic procedure)</span></span>

  - <span data-ttu-id="32284-120">戻り値の型 (変換演算子プロシージャの場合のみ)</span><span class="sxs-lookup"><span data-stu-id="32284-120">the return type (only for a conversion operator procedure)</span></span>

  <span data-ttu-id="32284-121">すべてのオーバーロードを同じ名前にする必要はありますが、各オーバーロードは、前の項目の 1 つ以上において他のすべてのオーバーロードと異なっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="32284-121">All overloads must have the same name, but each must differ from all the others in one or more of the preceding respects.</span></span> <span data-ttu-id="32284-122">これにより、コンパイラは、コードでプロパティまたはプロシージャが呼び出すときに使用するバージョンを区別できます。</span><span class="sxs-lookup"><span data-stu-id="32284-122">This allows the compiler to distinguish which version to use when code calls the property or procedure.</span></span>

- <span data-ttu-id="32284-123">**許可されない相違点。**</span><span class="sxs-lookup"><span data-stu-id="32284-123">**Disallowed Differences.**</span></span> <span data-ttu-id="32284-124">以下の項目はシグネチャに含まれないため、これらの項目の 1 つ以上を変更しても、プロパティまたはプロシージャのオーバーロードには有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="32284-124">Changing one or more of the following is not valid for overloading a property or procedure, because they are not part of the signature:</span></span>

  - <span data-ttu-id="32284-125">値を返すかどうか (プロシージャの場合)</span><span class="sxs-lookup"><span data-stu-id="32284-125">whether or not it returns a value (for a procedure)</span></span>

  - <span data-ttu-id="32284-126">戻り値のデータ型 (変換演算子を除く)</span><span class="sxs-lookup"><span data-stu-id="32284-126">the data type of the return value (except for a conversion operator)</span></span>

  - <span data-ttu-id="32284-127">パラメーターまたは型パラメーターの名前</span><span class="sxs-lookup"><span data-stu-id="32284-127">the names of the parameters or type parameters</span></span>

  - <span data-ttu-id="32284-128">型パラメーターに対する制約 (ジェネリック プロシージャの場合)</span><span class="sxs-lookup"><span data-stu-id="32284-128">the constraints on the type parameters (for a generic procedure)</span></span>

  - <span data-ttu-id="32284-129">パラメーター修飾子キーワード (`ByRef` や `Optional` など)</span><span class="sxs-lookup"><span data-stu-id="32284-129">parameter modifier keywords (such as `ByRef` or `Optional`)</span></span>

  - <span data-ttu-id="32284-130">プロパティまたはプロシージャ修飾子キーワード (`Public` や `Shared` など)</span><span class="sxs-lookup"><span data-stu-id="32284-130">property or procedure modifier keywords (such as `Public` or `Shared`)</span></span>

- <span data-ttu-id="32284-131">**省略可能な修飾子。**</span><span class="sxs-lookup"><span data-stu-id="32284-131">**Optional Modifier.**</span></span> <span data-ttu-id="32284-132">同じクラス内でオーバーロードされるプロパティまたはプロシージャを複数定義する場合、`Overloads` 修飾子を使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="32284-132">You do not have to use the `Overloads` modifier when you are defining multiple overloaded properties or procedures in the same class.</span></span> <span data-ttu-id="32284-133">ただし、宣言の 1 つで `Overloads` を使用した場合は、すべての宣言で Overloads を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="32284-133">However, if you use `Overloads` in one of the declarations, you must use it in all of them.</span></span>

- <span data-ttu-id="32284-134">**シャドウとオーバーロード。**</span><span class="sxs-lookup"><span data-stu-id="32284-134">**Shadowing and Overloading.**</span></span> <span data-ttu-id="32284-135">`Overloads` は、基底クラスで既存のメンバーや一連のオーバーロードされたメンバーをシャドウする場合にも使用できます。</span><span class="sxs-lookup"><span data-stu-id="32284-135">`Overloads` can also be used to shadow an existing member, or set of overloaded members, in a base class.</span></span> <span data-ttu-id="32284-136">この方法で `Overloads` を使用する場合は、基底クラスのメンバーと同じ名前とパラメーター リストを使用してプロパティまたはメソッドを宣言し、`Shadows` キーワードは指定しません。</span><span class="sxs-lookup"><span data-stu-id="32284-136">When you use `Overloads` in this way, you declare the property or method with the same name and the same parameter list as the base class member, and you do not supply the `Shadows` keyword.</span></span>

<span data-ttu-id="32284-137">`Overrides` を使用する場合は、ライブラリ API と C# が連携しやすくなるように、コンパイラが暗黙的に `Overloads` を追加します。</span><span class="sxs-lookup"><span data-stu-id="32284-137">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span></span>

<span data-ttu-id="32284-138">`Overloads` 修飾子は、次のコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="32284-138">The `Overloads` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="32284-139">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="32284-139">Function Statement</span></span>](../statements/function-statement.md)

- [<span data-ttu-id="32284-140">Operator ステートメント</span><span class="sxs-lookup"><span data-stu-id="32284-140">Operator Statement</span></span>](../statements/operator-statement.md)

- [<span data-ttu-id="32284-141">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="32284-141">Property Statement</span></span>](../statements/property-statement.md)

- [<span data-ttu-id="32284-142">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="32284-142">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="32284-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="32284-143">See also</span></span>

- [<span data-ttu-id="32284-144">Shadows</span><span class="sxs-lookup"><span data-stu-id="32284-144">Shadows</span></span>](shadows.md)
- [<span data-ttu-id="32284-145">プロシージャのオーバーロード</span><span class="sxs-lookup"><span data-stu-id="32284-145">Procedure Overloading</span></span>](../../programming-guide/language-features/procedures/procedure-overloading.md)
- [<span data-ttu-id="32284-146">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="32284-146">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="32284-147">演算子プロシージャ</span><span class="sxs-lookup"><span data-stu-id="32284-147">Operator Procedures</span></span>](../../programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="32284-148">方法: 変換演算子を定義する</span><span class="sxs-lookup"><span data-stu-id="32284-148">How to: Define a Conversion Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
