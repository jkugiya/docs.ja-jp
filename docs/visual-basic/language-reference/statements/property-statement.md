---
description: '詳細情報: Property Statement'
title: Property Statement
ms.date: 05/12/2018
f1_keywords:
- vb.PropertySet
- vb.Property
- vb.PropertyGet
helpviewer_keywords:
- Property statement [Visual Basic]
- default modifier
- property procedures [Visual Basic], Property statements
- Property keyword [Visual Basic]
ms.assetid: 3155edaf-8ebd-45c6-9cef-11d5d2dc8d38
ms.openlocfilehash: 95f2ac1f993fc8698d2033dfe50d925cd55a7dc4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741394"
---
# <a name="property-statement"></a><span data-ttu-id="b9524-103">Property Statement</span><span class="sxs-lookup"><span data-stu-id="b9524-103">Property Statement</span></span>

<span data-ttu-id="b9524-104">プロパティの名前、およびプロパティの値を格納して取得するために使用されるプロパティ プロシージャを宣言します。</span><span class="sxs-lookup"><span data-stu-id="b9524-104">Declares the name of a property, and the property procedures used to store and retrieve the value of the property.</span></span>

## <a name="syntax"></a><span data-ttu-id="b9524-105">構文</span><span class="sxs-lookup"><span data-stu-id="b9524-105">Syntax</span></span>

```vb
[ <attributelist> ] [ Default ] [ accessmodifier ]
[ propertymodifiers ] [ Shared ] [ Shadows ] [ ReadOnly | WriteOnly ] [ Iterator ]
Property name ( [ parameterlist ] ) [ As returntype ] [ Implements implementslist ]
    [ <attributelist> ] [ accessmodifier ] Get
        [ statements ]
    End Get
    [ <attributelist> ] [ accessmodifier ] Set ( ByVal value As returntype [, parameterlist ] )
        [ statements ]
    End Set
End Property
- or -
[ <attributelist> ] [ Default ] [ accessmodifier ]
[ propertymodifiers ] [ Shared ] [ Shadows ] [ ReadOnly | WriteOnly ]
Property name ( [ parameterlist ] ) [ As returntype ] [ Implements implementslist ]
```

## <a name="parts"></a><span data-ttu-id="b9524-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="b9524-106">Parts</span></span>

- `attributelist`

  <span data-ttu-id="b9524-107">任意。</span><span class="sxs-lookup"><span data-stu-id="b9524-107">Optional.</span></span> <span data-ttu-id="b9524-108">このプロパティか、`Get` または `Set` プロシージャに適用される属性の一覧です。</span><span class="sxs-lookup"><span data-stu-id="b9524-108">List of attributes that apply to this property or `Get` or `Set` procedure.</span></span> <span data-ttu-id="b9524-109">「[属性リスト](attribute-list.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9524-109">See [Attribute List](attribute-list.md).</span></span>

- `Default`

  <span data-ttu-id="b9524-110">任意。</span><span class="sxs-lookup"><span data-stu-id="b9524-110">Optional.</span></span> <span data-ttu-id="b9524-111">このプロパティが、定義されているクラスまたは構造体の既定のプロパティであることを指定します。</span><span class="sxs-lookup"><span data-stu-id="b9524-111">Specifies that this property is the default property for the class or structure on which it is defined.</span></span> <span data-ttu-id="b9524-112">既定のプロパティはパラメーターを受け取る必要があり、プロパティ名を指定せずに設定および取得できます。</span><span class="sxs-lookup"><span data-stu-id="b9524-112">Default properties must accept parameters and can be set and retrieved without specifying the property name.</span></span> <span data-ttu-id="b9524-113">プロパティを `Default` として宣言する場合、プロパティで、またはそのプロパティ プロシージャのいずれかで `Private` を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="b9524-113">If you declare the property as `Default`, you cannot use `Private` on the property or on either of its property procedures.</span></span>

- `accessmodifier`

  <span data-ttu-id="b9524-114">`Property` ステートメントで、および `Get` ステートメントと `Set` ステートメントのうちのいずれかで省略可能です。</span><span class="sxs-lookup"><span data-stu-id="b9524-114">Optional on the `Property` statement and on at most one of the `Get` and `Set` statements.</span></span> <span data-ttu-id="b9524-115">次のいずれかの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="b9524-115">Can be one of the following:</span></span>

  - [<span data-ttu-id="b9524-116">Public</span><span class="sxs-lookup"><span data-stu-id="b9524-116">Public</span></span>](../modifiers/public.md)

  - [<span data-ttu-id="b9524-117">Protected</span><span class="sxs-lookup"><span data-stu-id="b9524-117">Protected</span></span>](../modifiers/protected.md)

  - [<span data-ttu-id="b9524-118">Friend</span><span class="sxs-lookup"><span data-stu-id="b9524-118">Friend</span></span>](../modifiers/friend.md)

  - [<span data-ttu-id="b9524-119">Private</span><span class="sxs-lookup"><span data-stu-id="b9524-119">Private</span></span>](../modifiers/private.md)

  - [<span data-ttu-id="b9524-120">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="b9524-120">Protected Friend</span></span>](../modifiers/protected-friend.md)

  - [<span data-ttu-id="b9524-121">Private Protected</span><span class="sxs-lookup"><span data-stu-id="b9524-121">Private Protected</span></span>](../modifiers/private-protected.md)

  <span data-ttu-id="b9524-122">「 [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9524-122">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `propertymodifiers`

  <span data-ttu-id="b9524-123">任意。</span><span class="sxs-lookup"><span data-stu-id="b9524-123">Optional.</span></span> <span data-ttu-id="b9524-124">次のいずれかの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="b9524-124">Can be one of the following:</span></span>

  - [<span data-ttu-id="b9524-125">Overloads</span><span class="sxs-lookup"><span data-stu-id="b9524-125">Overloads</span></span>](../modifiers/overloads.md)

  - [<span data-ttu-id="b9524-126">Overrides</span><span class="sxs-lookup"><span data-stu-id="b9524-126">Overrides</span></span>](../modifiers/overrides.md)

  - [<span data-ttu-id="b9524-127">Overridable</span><span class="sxs-lookup"><span data-stu-id="b9524-127">Overridable</span></span>](../modifiers/overridable.md)

  - [<span data-ttu-id="b9524-128">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="b9524-128">NotOverridable</span></span>](../modifiers/notoverridable.md)

  - [<span data-ttu-id="b9524-129">MustOverride</span><span class="sxs-lookup"><span data-stu-id="b9524-129">MustOverride</span></span>](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  <span data-ttu-id="b9524-130">任意。</span><span class="sxs-lookup"><span data-stu-id="b9524-130">Optional.</span></span> <span data-ttu-id="b9524-131">「[Shared](../modifiers/shared.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9524-131">See [Shared](../modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="b9524-132">任意。</span><span class="sxs-lookup"><span data-stu-id="b9524-132">Optional.</span></span> <span data-ttu-id="b9524-133">「[Shadows](../modifiers/shadows.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9524-133">See [Shadows](../modifiers/shadows.md).</span></span>

- `ReadOnly`

  <span data-ttu-id="b9524-134">任意。</span><span class="sxs-lookup"><span data-stu-id="b9524-134">Optional.</span></span> <span data-ttu-id="b9524-135">「[ReadOnly](../modifiers/readonly.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9524-135">See [ReadOnly](../modifiers/readonly.md).</span></span>

- `WriteOnly`

  <span data-ttu-id="b9524-136">任意。</span><span class="sxs-lookup"><span data-stu-id="b9524-136">Optional.</span></span> <span data-ttu-id="b9524-137">「[WriteOnly](../modifiers/writeonly.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9524-137">See [WriteOnly](../modifiers/writeonly.md).</span></span>

- `Iterator`

  <span data-ttu-id="b9524-138">任意。</span><span class="sxs-lookup"><span data-stu-id="b9524-138">Optional.</span></span> <span data-ttu-id="b9524-139">「[Iterator](../modifiers/iterator.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9524-139">See [Iterator](../modifiers/iterator.md).</span></span>

- `name`

  <span data-ttu-id="b9524-140">必須です。</span><span class="sxs-lookup"><span data-stu-id="b9524-140">Required.</span></span> <span data-ttu-id="b9524-141">プロパティ名。</span><span class="sxs-lookup"><span data-stu-id="b9524-141">Name of the property.</span></span> <span data-ttu-id="b9524-142">「 [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9524-142">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

- `parameterlist`

  <span data-ttu-id="b9524-143">任意。</span><span class="sxs-lookup"><span data-stu-id="b9524-143">Optional.</span></span> <span data-ttu-id="b9524-144">このプロパティのパラメーターと、`Set` プロシージャの指定できるその他のパラメーターを表すローカル変数名の一覧です。</span><span class="sxs-lookup"><span data-stu-id="b9524-144">List of local variable names representing the parameters of this property, and possible additional parameters of the `Set` procedure.</span></span> <span data-ttu-id="b9524-145">[パラメーター リスト](parameter-list.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9524-145">See [Parameter List](parameter-list.md).</span></span>

- `returntype`

  <span data-ttu-id="b9524-146">`Option Strict` が `On` の場合は必ず指定します。</span><span class="sxs-lookup"><span data-stu-id="b9524-146">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="b9524-147">このプロパティによって返される値のデータ型。</span><span class="sxs-lookup"><span data-stu-id="b9524-147">Data type of the value returned by this property.</span></span>

- `Implements`

  <span data-ttu-id="b9524-148">任意。</span><span class="sxs-lookup"><span data-stu-id="b9524-148">Optional.</span></span> <span data-ttu-id="b9524-149">このプロパティが、それぞれがこのプロパティの含まれているクラスまたは構造体によって実装されたインターフェイスに定義されている、1 つ以上のプロパティを実装することを示します。</span><span class="sxs-lookup"><span data-stu-id="b9524-149">Indicates that this property implements one or more properties, each one defined in an interface implemented by this property's containing class or structure.</span></span> <span data-ttu-id="b9524-150">「[Implements ステートメント](implements-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9524-150">See [Implements Statement](implements-statement.md).</span></span>

- `implementslist`

  <span data-ttu-id="b9524-151">`Implements` を指定する場合は、必ず指定します。</span><span class="sxs-lookup"><span data-stu-id="b9524-151">Required if `Implements` is supplied.</span></span> <span data-ttu-id="b9524-152">実装されるプロパティの一覧です。</span><span class="sxs-lookup"><span data-stu-id="b9524-152">List of properties being implemented.</span></span>

  `implementedproperty [ , implementedproperty ... ]`

  <span data-ttu-id="b9524-153">`implementedproperty` の構文と指定項目は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b9524-153">Each `implementedproperty` has the following syntax and parts:</span></span>

  `interface.definedname`

  |<span data-ttu-id="b9524-154">パーツ</span><span class="sxs-lookup"><span data-stu-id="b9524-154">Part</span></span>|<span data-ttu-id="b9524-155">説明</span><span class="sxs-lookup"><span data-stu-id="b9524-155">Description</span></span>|
  |---|---|
  |`interface`|<span data-ttu-id="b9524-156">必須です。</span><span class="sxs-lookup"><span data-stu-id="b9524-156">Required.</span></span> <span data-ttu-id="b9524-157">このプロパティの含まれているクラスまたは構造体によって実装されたインターフェイスの名前です。</span><span class="sxs-lookup"><span data-stu-id="b9524-157">Name of an interface implemented by this property's containing class or structure.</span></span>|
  |`definedname`|<span data-ttu-id="b9524-158">必須です。</span><span class="sxs-lookup"><span data-stu-id="b9524-158">Required.</span></span> <span data-ttu-id="b9524-159">`interface` の中でプロパティを定義するために使用する名前です。</span><span class="sxs-lookup"><span data-stu-id="b9524-159">Name by which the property is defined in `interface`.</span></span>|

- `Get`

  <span data-ttu-id="b9524-160">任意。</span><span class="sxs-lookup"><span data-stu-id="b9524-160">Optional.</span></span> <span data-ttu-id="b9524-161">プロパティが `ReadOnly` とマークされている場合は、必ず指定します。</span><span class="sxs-lookup"><span data-stu-id="b9524-161">Required if the property is marked `ReadOnly`.</span></span> <span data-ttu-id="b9524-162">プロパティの値を返すために使用される `Get` プロパティ プロシージャを開始します。</span><span class="sxs-lookup"><span data-stu-id="b9524-162">Starts a `Get` property procedure that is used to return the value of the property.</span></span>  <span data-ttu-id="b9524-163">`Get` ステートメントは、[自動実装プロパティ](../../programming-guide/language-features/procedures/auto-implemented-properties.md)と一緒には使用されません。</span><span class="sxs-lookup"><span data-stu-id="b9524-163">The `Get` statement is not used with [auto-implemented properties](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>

- `statements`

  <span data-ttu-id="b9524-164">任意。</span><span class="sxs-lookup"><span data-stu-id="b9524-164">Optional.</span></span> <span data-ttu-id="b9524-165">`Get` または `Set` プロシージャ内で実行するためのステートメントのブロック。</span><span class="sxs-lookup"><span data-stu-id="b9524-165">Block of statements to run within the `Get` or `Set` procedure.</span></span>

- `End Get`

  <span data-ttu-id="b9524-166">`Get` プロパティ プロシージャを終了します。</span><span class="sxs-lookup"><span data-stu-id="b9524-166">Terminates the `Get` property procedure.</span></span>

- `Set`

  <span data-ttu-id="b9524-167">任意。</span><span class="sxs-lookup"><span data-stu-id="b9524-167">Optional.</span></span> <span data-ttu-id="b9524-168">プロパティが `WriteOnly` とマークされている場合は、必ず指定します。</span><span class="sxs-lookup"><span data-stu-id="b9524-168">Required if the property is marked `WriteOnly`.</span></span> <span data-ttu-id="b9524-169">プロパティの値を格納するために使用される `Set` プロパティ プロシージャを開始します。</span><span class="sxs-lookup"><span data-stu-id="b9524-169">Starts a `Set` property procedure that is used to store the value of the property.</span></span>  <span data-ttu-id="b9524-170">`Set` ステートメントは、[自動実装プロパティ](../../programming-guide/language-features/procedures/auto-implemented-properties.md)と一緒には使用されません。</span><span class="sxs-lookup"><span data-stu-id="b9524-170">The `Set` statement is not used with [auto-implemented properties](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>

- `End Set`

  <span data-ttu-id="b9524-171">`Set` プロパティ プロシージャを終了します。</span><span class="sxs-lookup"><span data-stu-id="b9524-171">Terminates the `Set` property procedure.</span></span>

- `End Property`

  <span data-ttu-id="b9524-172">このプロパティの定義を終了します。</span><span class="sxs-lookup"><span data-stu-id="b9524-172">Terminates the definition of this property.</span></span>

## <a name="remarks"></a><span data-ttu-id="b9524-173">Remarks</span><span class="sxs-lookup"><span data-stu-id="b9524-173">Remarks</span></span>

<span data-ttu-id="b9524-174">`Property` ステートメントは、プロパティの宣言を導入します。</span><span class="sxs-lookup"><span data-stu-id="b9524-174">The `Property` statement introduces the declaration of a property.</span></span> <span data-ttu-id="b9524-175">プロパティには `Get` プロシージャ (読み取り専用)、`Set` プロシージャ (書き込み専用)、またはその両方 (読み取り/書き込み) を指定できます。</span><span class="sxs-lookup"><span data-stu-id="b9524-175">A property can have a `Get` procedure (read only), a `Set` procedure (write only), or both (read-write).</span></span> <span data-ttu-id="b9524-176">自動実装プロパティを使用する場合は、`Get` プロシージャと `Set` プロシージャを省略できます。</span><span class="sxs-lookup"><span data-stu-id="b9524-176">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="b9524-177">詳細については、「[自動実装プロパティ](../../programming-guide/language-features/procedures/auto-implemented-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9524-177">For more information, see [Auto-Implemented Properties](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>

<span data-ttu-id="b9524-178">`Property` は、クラス レベルでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="b9524-178">You can use `Property` only at class level.</span></span> <span data-ttu-id="b9524-179">つまり、プロパティの *宣言コンテキスト* は、クラス、構造体、モジュール、またはインターフェイスであることが必要で、ソース ファイル、名前空間、プロシージャ、ブロックでは宣言できません。</span><span class="sxs-lookup"><span data-stu-id="b9524-179">This means the *declaration context* for a property must be a class, structure, module, or interface, and cannot be a source file, namespace, procedure, or block.</span></span> <span data-ttu-id="b9524-180">詳細については、「[宣言コンテキストと既定のアクセス レベル](declaration-contexts-and-default-access-levels.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9524-180">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="b9524-181">既定では、プロパティはパブリック アクセスを使用します。</span><span class="sxs-lookup"><span data-stu-id="b9524-181">By default, properties use public access.</span></span> <span data-ttu-id="b9524-182">`Property` ステートメントでアクセス修飾子を使用してプロパティのアクセス レベルを調整できます。また、必要に応じて、そのプロパティ プロシージャの 1 つをより制限の厳しいアクセス レベルに調整することもできます。</span><span class="sxs-lookup"><span data-stu-id="b9524-182">You can adjust a property's access level with an access modifier on the `Property` statement, and you can optionally adjust one of its property procedures to a more restrictive access level.</span></span>

<span data-ttu-id="b9524-183">Visual Basic は、プロパティの割り当て時に `Set` プロシージャにパラメーターを渡します。</span><span class="sxs-lookup"><span data-stu-id="b9524-183">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="b9524-184">`Set` のパラメーターを指定しない場合、統合開発環境 (IDE) では `value` という名前の暗黙的なパラメーターが使用されます。</span><span class="sxs-lookup"><span data-stu-id="b9524-184">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="b9524-185">このパラメーターは、プロパティに割り当てられる値を保持します。</span><span class="sxs-lookup"><span data-stu-id="b9524-185">This parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="b9524-186">通常はこの値をプライベート ローカル変数に格納し、これは `Get` プロシージャが呼び出されるたびに返されます。</span><span class="sxs-lookup"><span data-stu-id="b9524-186">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>

## <a name="rules"></a><span data-ttu-id="b9524-187">ルール</span><span class="sxs-lookup"><span data-stu-id="b9524-187">Rules</span></span>

- <span data-ttu-id="b9524-188">**混合アクセス レベル。**</span><span class="sxs-lookup"><span data-stu-id="b9524-188">**Mixed Access Levels.**</span></span> <span data-ttu-id="b9524-189">読み取り/書き込みプロパティを定義する場合は、必要に応じて、`Get` または `Set` のいずれかのプロシージャに対して異なるアクセス レベルを指定できますが、両方に対して指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="b9524-189">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="b9524-190">この場合、プロシージャのアクセス レベルは、プロパティのアクセス レベルよりも制限されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9524-190">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="b9524-191">たとえば、プロパティが `Friend` として宣言されている場合は、`Set` プロシージャを、`Public` ではなく `Private` として宣言できます。</span><span class="sxs-lookup"><span data-stu-id="b9524-191">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>

  <span data-ttu-id="b9524-192">`ReadOnly` または `WriteOnly` プロパティを定義する場合、1 つのプロパティ プロシージャ (それぞれ `Get` または `Set`) がプロパティのすべてを表します。</span><span class="sxs-lookup"><span data-stu-id="b9524-192">If you are defining a `ReadOnly` or `WriteOnly` property, the single property procedure (`Get` or `Set`, respectively) represents all of the property.</span></span> <span data-ttu-id="b9524-193">このようなプロシージャに対して異なるアクセス レベルを宣言することはできません。これは、プロパティに 2 つのアクセス レベルが設定されるためです。</span><span class="sxs-lookup"><span data-stu-id="b9524-193">You cannot declare a different access level for such a procedure, because that would set two access levels for the property.</span></span>

- <span data-ttu-id="b9524-194">**戻り値の型。**</span><span class="sxs-lookup"><span data-stu-id="b9524-194">**Return Type.**</span></span> <span data-ttu-id="b9524-195">`Property` ステートメントは、返される値のデータ型を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="b9524-195">The `Property` statement can declare the data type of the value it returns.</span></span> <span data-ttu-id="b9524-196">任意のデータ型や、列挙、構造体、クラス、またはインターフェイスの名前を指定できます。</span><span class="sxs-lookup"><span data-stu-id="b9524-196">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>

  <span data-ttu-id="b9524-197">`returntype` を指定しない場合、プロパティは `Object` を返します。</span><span class="sxs-lookup"><span data-stu-id="b9524-197">If you do not specify `returntype`, the property returns `Object`.</span></span>

- <span data-ttu-id="b9524-198">**実装。**</span><span class="sxs-lookup"><span data-stu-id="b9524-198">**Implementation.**</span></span> <span data-ttu-id="b9524-199">このプロパティで `Implements` キーワードが使用されている場合、含まれているクラスまたは構造体には、その `Class` または `Structure` ステートメントの直後に `Implements` ステートメントが必要です。</span><span class="sxs-lookup"><span data-stu-id="b9524-199">If this property uses the `Implements` keyword, the containing class or structure must have an `Implements` statement immediately following its `Class` or `Structure` statement.</span></span> <span data-ttu-id="b9524-200">`Implements` ステートメントには、`implementslist` で指定された各インターフェイスを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9524-200">The `Implements` statement must include each interface specified in `implementslist`.</span></span> <span data-ttu-id="b9524-201">ただし、インターフェイスが `Property` を定義するときに使用する名前 (`definedname`) は、このプロパティの名前と同じである必要はありません (`name`)。</span><span class="sxs-lookup"><span data-stu-id="b9524-201">However, the name by which an interface defines the `Property` (in `definedname`) does not have to be the same as the name of this property (in `name`).</span></span>

## <a name="behavior"></a><span data-ttu-id="b9524-202">動作</span><span class="sxs-lookup"><span data-stu-id="b9524-202">Behavior</span></span>

- <span data-ttu-id="b9524-203">**プロパティ プロシージャからの復帰。**</span><span class="sxs-lookup"><span data-stu-id="b9524-203">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="b9524-204">`Get` または `Set` プロシージャから呼び出し元のコードに返されると、実行は、それを呼び出したステートメントの後のステートメントを使用して続行されます。</span><span class="sxs-lookup"><span data-stu-id="b9524-204">When the `Get` or `Set` procedure returns to the calling code, execution continues with the statement following the statement that invoked it.</span></span>

  <span data-ttu-id="b9524-205">`Exit Property` および `Return` ステートメントでは、プロパティ プロシージャがすぐに終了します。</span><span class="sxs-lookup"><span data-stu-id="b9524-205">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="b9524-206">任意の数の `Exit Property` および `Return` ステートメントをプロシージャ内の任意の場所に記述でき、`Exit Property` ステートメントと `Return` ステートメントを混在させることができます。</span><span class="sxs-lookup"><span data-stu-id="b9524-206">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>

- <span data-ttu-id="b9524-207">**戻り値。**</span><span class="sxs-lookup"><span data-stu-id="b9524-207">**Return Value.**</span></span> <span data-ttu-id="b9524-208">`Get` プロシージャから値を返すには、プロパティ名に値を割り当てるか、`Return` ステートメントに値を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="b9524-208">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a `Return` statement.</span></span> <span data-ttu-id="b9524-209">次の例では、プロパティ名 `quoteForTheDay` に戻り値を割り当ててから、`Exit Property` ステートメントを使用して返します。</span><span class="sxs-lookup"><span data-stu-id="b9524-209">The following example assigns the return value to the property name `quoteForTheDay` and then uses the `Exit Property` statement to return.</span></span>

  [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]

  [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]

  <span data-ttu-id="b9524-210">`name` に値を割り当てずに `Exit Property` を使用すると、`Get` プロシージャは、プロパティのデータ型の既定値を返します。</span><span class="sxs-lookup"><span data-stu-id="b9524-210">If you use `Exit Property` without assigning a value to `name`, the `Get` procedure returns the default value for the property's data type.</span></span>

  <span data-ttu-id="b9524-211">同時に、`Return` ステートメントによって `Get` プロシージャの戻り値が割り当てられ、プロシージャが終了します。</span><span class="sxs-lookup"><span data-stu-id="b9524-211">The `Return` statement at the same time assigns the `Get` procedure return value and exits the procedure.</span></span> <span data-ttu-id="b9524-212">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="b9524-212">The following example shows this.</span></span>

  [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]

  [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]

## <a name="example"></a><span data-ttu-id="b9524-213">例</span><span class="sxs-lookup"><span data-stu-id="b9524-213">Example</span></span>

<span data-ttu-id="b9524-214">次の例では、クラス内にプロパティを宣言しています。</span><span class="sxs-lookup"><span data-stu-id="b9524-214">The following example declares a property in a class.</span></span>

[!code-vb[VbVbalrStatements#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#51)]

## <a name="see-also"></a><span data-ttu-id="b9524-215">関連項目</span><span class="sxs-lookup"><span data-stu-id="b9524-215">See also</span></span>

- [<span data-ttu-id="b9524-216">自動実装プロパティ</span><span class="sxs-lookup"><span data-stu-id="b9524-216">Auto-Implemented Properties</span></span>](../../programming-guide/language-features/procedures/auto-implemented-properties.md)
- [<span data-ttu-id="b9524-217">クラスとオブジェクト</span><span class="sxs-lookup"><span data-stu-id="b9524-217">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="b9524-218">Get ステートメント</span><span class="sxs-lookup"><span data-stu-id="b9524-218">Get Statement</span></span>](get-statement.md)
- [<span data-ttu-id="b9524-219">Set ステートメント</span><span class="sxs-lookup"><span data-stu-id="b9524-219">Set Statement</span></span>](set-statement.md)
- [<span data-ttu-id="b9524-220">パラメーター リスト</span><span class="sxs-lookup"><span data-stu-id="b9524-220">Parameter List</span></span>](parameter-list.md)
- [<span data-ttu-id="b9524-221">default</span><span class="sxs-lookup"><span data-stu-id="b9524-221">Default</span></span>](../modifiers/default.md)
