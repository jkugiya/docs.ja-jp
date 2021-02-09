---
description: '詳細情報: Enum ステートメント (Visual Basic)'
title: Enum ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.Enum
helpviewer_keywords:
- enumerated constants [Visual Basic]
- Enum statement [Visual Basic]
- Private keyword [Visual Basic], Enum statements
- Public keyword [Visual Basic], in Enum statement
- variables [Visual Basic], enumeration
- constants [Visual Basic], enumerated
ms.assetid: a45e51f1-65ff-48e1-bf32-79130f137377
ms.openlocfilehash: dcaf28e949f8d34b8d72b07d8029ea10d6baeabf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99769170"
---
# <a name="enum-statement-visual-basic"></a><span data-ttu-id="d4ad5-103">Enum ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d4ad5-103">Enum Statement (Visual Basic)</span></span>

<span data-ttu-id="d4ad5-104">列挙型を宣言し、そのメンバーの値を定義します。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-104">Declares an enumeration and defines the values of its members.</span></span>

## <a name="syntax"></a><span data-ttu-id="d4ad5-105">構文</span><span class="sxs-lookup"><span data-stu-id="d4ad5-105">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ]  [ Shadows ]
Enum enumerationname [ As datatype ]
   memberlist
End Enum
```

## <a name="parts"></a><span data-ttu-id="d4ad5-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="d4ad5-106">Parts</span></span>

- `attributelist`

  <span data-ttu-id="d4ad5-107">任意。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-107">Optional.</span></span> <span data-ttu-id="d4ad5-108">この列挙型に適用される属性の一覧です。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-108">List of attributes that apply to this enumeration.</span></span> <span data-ttu-id="d4ad5-109">[属性リスト](attribute-list.md)は山かっこ ("`<`" および "`>`") で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-109">You must enclose the [attribute list](attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>

  <span data-ttu-id="d4ad5-110"><xref:System.FlagsAttribute> 属性は、列挙型のインスタンスの値に複数の列挙型メンバーを含めることができること、および各メンバーが列挙値のビット フィールドを表すことを示します。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-110">The <xref:System.FlagsAttribute> attribute indicates that the value of an instance of the enumeration can include multiple enumeration members, and that each member represents a bit field in the enumeration value.</span></span>

- `accessmodifier`

  <span data-ttu-id="d4ad5-111">任意。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-111">Optional.</span></span> <span data-ttu-id="d4ad5-112">どのようなコードからこの列挙型にアクセスできるのかを指定します。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-112">Specifies what code can access this enumeration.</span></span> <span data-ttu-id="d4ad5-113">次のいずれかの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-113">Can be one of the following:</span></span>

  - [<span data-ttu-id="d4ad5-114">Public</span><span class="sxs-lookup"><span data-stu-id="d4ad5-114">Public</span></span>](../modifiers/public.md)

  - [<span data-ttu-id="d4ad5-115">Protected</span><span class="sxs-lookup"><span data-stu-id="d4ad5-115">Protected</span></span>](../modifiers/protected.md)

  - [<span data-ttu-id="d4ad5-116">Friend</span><span class="sxs-lookup"><span data-stu-id="d4ad5-116">Friend</span></span>](../modifiers/friend.md)

  - [<span data-ttu-id="d4ad5-117">Private</span><span class="sxs-lookup"><span data-stu-id="d4ad5-117">Private</span></span>](../modifiers/private.md)

  - [<span data-ttu-id="d4ad5-118">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="d4ad5-118">Protected Friend</span></span>](../modifiers/protected-friend.md)

  - [<span data-ttu-id="d4ad5-119">Private Protected</span><span class="sxs-lookup"><span data-stu-id="d4ad5-119">Private Protected</span></span>](../modifiers/private-protected.md)

- `Shadows`

  <span data-ttu-id="d4ad5-120">任意。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-120">Optional.</span></span> <span data-ttu-id="d4ad5-121">この列挙型により、基底クラスにある、同じ名前を持つプログラミング要素、またはオーバーロードされる要素のセットが宣言し直されて隠ぺいされることを指定します。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-121">Specifies that this enumeration redeclares and hides an identically named programming element, or set of overloaded elements, in a base class.</span></span> <span data-ttu-id="d4ad5-122">[Shadows](../modifiers/shadows.md) は、そのメンバーではなく、列挙型自体でのみ指定できます。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-122">You can specify [Shadows](../modifiers/shadows.md) only on the enumeration itself, not on any of its members.</span></span>

- `enumerationname`

  <span data-ttu-id="d4ad5-123">必須です。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-123">Required.</span></span> <span data-ttu-id="d4ad5-124">列挙型の名前。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-124">Name of the enumeration.</span></span> <span data-ttu-id="d4ad5-125">有効な名前については、「[宣言された要素の名前](../../programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-125">For information on valid names, see [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

- `datatype`

  <span data-ttu-id="d4ad5-126">任意。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-126">Optional.</span></span> <span data-ttu-id="d4ad5-127">列挙型とそのすべてのメンバーのデータ型。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-127">Data type of the enumeration and all its members.</span></span>

- `memberlist`

  <span data-ttu-id="d4ad5-128">必須です。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-128">Required.</span></span> <span data-ttu-id="d4ad5-129">このステートメントで宣言されているメンバー定数の一覧。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-129">List of member constants being declared in this statement.</span></span> <span data-ttu-id="d4ad5-130">個々のソース コード行に複数のメンバーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-130">Multiple members appear on individual source code lines.</span></span>

  <span data-ttu-id="d4ad5-131">`member` の構文と指定項目は次のとおりです。`[<attribute list>] member name [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="d4ad5-131">Each `member` has the following syntax and parts: `[<attribute list>] member name [ = initializer ]`</span></span>

  |<span data-ttu-id="d4ad5-132">パーツ</span><span class="sxs-lookup"><span data-stu-id="d4ad5-132">Part</span></span>|<span data-ttu-id="d4ad5-133">説明</span><span class="sxs-lookup"><span data-stu-id="d4ad5-133">Description</span></span>|
  |---|---|
  |`membername`|<span data-ttu-id="d4ad5-134">必須です。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-134">Required.</span></span> <span data-ttu-id="d4ad5-135">このメンバーの名前。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-135">Name of this member.</span></span>|
  |`initializer`|<span data-ttu-id="d4ad5-136">任意。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-136">Optional.</span></span> <span data-ttu-id="d4ad5-137">コンパイル時に評価され、このメンバーに代入される式。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-137">Expression that is evaluated at compile time and assigned to this member.</span></span>|

- <span data-ttu-id="d4ad5-138">`End` `Enum`</span><span class="sxs-lookup"><span data-stu-id="d4ad5-138">`End` `Enum`</span></span>

  <span data-ttu-id="d4ad5-139">`Enum` ブロックを終了します。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-139">Terminates the `Enum` block.</span></span>

## <a name="remarks"></a><span data-ttu-id="d4ad5-140">Remarks</span><span class="sxs-lookup"><span data-stu-id="d4ad5-140">Remarks</span></span>

<span data-ttu-id="d4ad5-141">論理的に相互に関連付けられている変化しない値のセットがある場合は、それらを列挙型でまとめて定義できます。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-141">If you have a set of unchanging values that are logically related to each other, you can define them together in an enumeration.</span></span> <span data-ttu-id="d4ad5-142">これにより、列挙型とそのメンバーにわかりやすい名前が指定され、その値よりも覚えやすくなります。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-142">This provides meaningful names for the enumeration and its members, which are easier to remember than their values.</span></span> <span data-ttu-id="d4ad5-143">その後、コード内のさまざまな場所で列挙型メンバーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-143">You can then use the enumeration members in many places in your code.</span></span>

<span data-ttu-id="d4ad5-144">列挙型を使用する利点は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-144">The benefits of using enumerations include the following:</span></span>

- <span data-ttu-id="d4ad5-145">数の入れ替えや入力間違いによるエラーを減らせます。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-145">Reduces errors caused by transposing or mistyping numbers.</span></span>

- <span data-ttu-id="d4ad5-146">値を後で変更しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-146">Makes it easy to change values in the future.</span></span>

- <span data-ttu-id="d4ad5-147">コードが読みやすくなり、コードにエラーが生じる可能性を抑えられます。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-147">Makes code easier to read, which means it is less likely that errors will be introduced.</span></span>

- <span data-ttu-id="d4ad5-148">上位互換性を確保できます。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-148">Ensures forward compatibility.</span></span> <span data-ttu-id="d4ad5-149">列挙型を使用すると、今後メンバー名に対応する値が変更された場合に、コードでエラーが発生する確率が低くなります。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-149">If you use enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>

<span data-ttu-id="d4ad5-150">列挙型には、名前、基になるデータ型、およびメンバーのセットが含まれます。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-150">An enumeration has a name, an underlying data type, and a set of members.</span></span> <span data-ttu-id="d4ad5-151">各メンバーは定数を表します。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-151">Each member represents a constant.</span></span>

<span data-ttu-id="d4ad5-152">プロシージャの外部で、クラス、構造体、モジュール、またはインターフェイス レベルで宣言された列挙型は、*メンバー列挙型* です。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-152">An enumeration declared at class, structure, module, or interface level, outside any procedure, is a *member enumeration*.</span></span> <span data-ttu-id="d4ad5-153">それを宣言するには、クラス、構造体、モジュール、またはインターフェイスのメンバーです。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-153">It is a member of the class, structure, module, or interface that declares it.</span></span>

<span data-ttu-id="d4ad5-154">メンバー列挙型には、クラス、構造体、モジュール、またはインターフェイス内のどこからでもアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-154">Member enumerations can be accessed from anywhere within their class, structure, module, or interface.</span></span> <span data-ttu-id="d4ad5-155">クラス、構造体、またはモジュールの外部のコードでは、メンバー列挙型の名前を、そのクラス、構造体、またはモジュールの名前で修飾する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-155">Code outside a class, structure, or module must qualify a member enumeration's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="d4ad5-156">[Imports](imports-statement-net-namespace-and-type.md) ステートメントをソース ファイルに追加することで、完全修飾名を使用する必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-156">You can avoid the need to use fully qualified names by adding an [Imports](imports-statement-net-namespace-and-type.md) statement to the source file.</span></span>

<span data-ttu-id="d4ad5-157">クラス、構造体、モジュール、またはインターフェイスの外部で、名前空間レベルで宣言された列挙型は、それが表示される名前空間のメンバーになります。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-157">An enumeration declared at namespace level, outside any class, structure, module, or interface, is a member of the namespace in which it appears.</span></span>

<span data-ttu-id="d4ad5-158">列挙型の *宣言コンテキスト* は、ソース ファイル、名前空間、クラス、構造体、モジュール、またはインターフェイスのいずれかである必要があり、プロシージャでは宣言できません。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-158">The *declaration context* for an enumeration must be a source file, namespace, class, structure, module, or interface, and cannot be a procedure.</span></span> <span data-ttu-id="d4ad5-159">詳細については、「[宣言コンテキストと既定のアクセス レベル](declaration-contexts-and-default-access-levels.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-159">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="d4ad5-160">列挙型全体に属性を適用することはできますが、そのメンバーに個別に適用することはできません。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-160">You can apply attributes to an enumeration as a whole, but not to its members individually.</span></span> <span data-ttu-id="d4ad5-161">属性により、アセンブリのメタデータに情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-161">An attribute contributes information to the assembly's metadata.</span></span>

## <a name="data-type"></a><span data-ttu-id="d4ad5-162">データの種類</span><span class="sxs-lookup"><span data-stu-id="d4ad5-162">Data Type</span></span>

<span data-ttu-id="d4ad5-163">`Enum` ステートメントでは、列挙型のデータ型を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-163">The `Enum` statement can declare the data type of an enumeration.</span></span> <span data-ttu-id="d4ad5-164">各メンバーは、列挙型のデータ型を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-164">Each member takes the enumeration's data type.</span></span> <span data-ttu-id="d4ad5-165">`Byte`、`Integer`、`Long`、`SByte`、`Short`、`UInteger`、`ULong`、または `UShort` を指定できます。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-165">You can specify `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort`.</span></span>

<span data-ttu-id="d4ad5-166">列挙型に `datatype` を指定しない場合、各メンバーはその `initializer` のデータ型を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-166">If you do not specify `datatype` for the enumeration, each member takes the data type of its `initializer`.</span></span> <span data-ttu-id="d4ad5-167">`datatype` と `initializer` の両方を指定した場合、`initializer` のデータ型は `datatype` に変換可能である必要があります。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-167">If you specify both `datatype` and `initializer`, the data type of `initializer` must be convertible to `datatype`.</span></span> <span data-ttu-id="d4ad5-168">`datatype` も `initializer` も存在しない場合、データ型は既定で `Integer` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-168">If neither `datatype` nor `initializer` is present, the data type defaults to `Integer`.</span></span>

## <a name="initializing-members"></a><span data-ttu-id="d4ad5-169">メンバーの初期化</span><span class="sxs-lookup"><span data-stu-id="d4ad5-169">Initializing Members</span></span>

<span data-ttu-id="d4ad5-170">`Enum` ステートメントでは、`memberlist` で選択されたメンバーの内容を初期化できます。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-170">The `Enum` statement can initialize the contents of selected members in `memberlist`.</span></span> <span data-ttu-id="d4ad5-171">`initializer` を使用して、メンバーに代入される式を指定します。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-171">You use `initializer` to supply an expression to be assigned to the member.</span></span>

<span data-ttu-id="d4ad5-172">メンバーに `initializer` を指定しなかった場合、Visual Basic では、0 (`memberlist` の最初の `member` である場合)、または `member` の直前の値より 1 大きい値に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-172">If you do not specify `initializer` for a member, Visual Basic initializes it either to zero (if it is the first `member` in `memberlist`), or to a value greater by one than that of the immediately preceding `member`.</span></span>

<span data-ttu-id="d4ad5-173">各 `initializer` で指定される式には、リテラルの任意の組み合わせ、既に定義されている他の定数、および既に定義されている列挙型メンバー (この列挙型の前のメンバーを含む) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-173">The expression supplied in each `initializer` can be any combination of literals, other constants that are already defined, and enumeration members that are already defined, including a previous member of this enumeration.</span></span> <span data-ttu-id="d4ad5-174">算術演算子と論理演算子を使用して、そのような要素を組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-174">You can use arithmetic and logical operators to combine such elements.</span></span>

<span data-ttu-id="d4ad5-175">`initializer` では、変数や関数を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-175">You cannot use variables or functions in `initializer`.</span></span> <span data-ttu-id="d4ad5-176">ただし、`CByte` や `CShort` などの変換キーワードを使用できます。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-176">However, you can use conversion keywords such as `CByte` and `CShort`.</span></span> <span data-ttu-id="d4ad5-177">定数 `String` または `Char` 引数でそれを呼び出す場合は、コンパイル時に評価できるため、`AscW` を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-177">You can also use `AscW` if you call it with a constant `String` or `Char` argument, since that can be evaluated at compile time.</span></span>

<span data-ttu-id="d4ad5-178">列挙型に浮動小数点値を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-178">Enumerations cannot have floating-point values.</span></span> <span data-ttu-id="d4ad5-179">メンバーに浮動小数点値が割り当てられていて `Option Strict` が on に設定されている場合は、コンパイラ エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-179">If a member is assigned a floating-point value and `Option Strict` is set to on, a compiler error occurs.</span></span> <span data-ttu-id="d4ad5-180">`Option Strict` が off に設定されている場合は、値は自動的に `Enum` 型に変換されます。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-180">If `Option Strict` is off, the value is automatically converted to the `Enum` type.</span></span>

<span data-ttu-id="d4ad5-181">メンバーの値が、基になるデータ型で許容される範囲を超えている場合、またはメンバーを、基になるデータ型で許容される最大値に初期化した場合、コンパイラによってエラーが報告されます。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-181">If the value of a member exceeds the allowable range for the underlying data type, or if you initialize any member to the maximum value allowed by the underlying data type, the compiler reports an error.</span></span>

## <a name="modifiers"></a><span data-ttu-id="d4ad5-182">修飾子</span><span class="sxs-lookup"><span data-stu-id="d4ad5-182">Modifiers</span></span>

<span data-ttu-id="d4ad5-183">クラス、構造体、モジュール、およびインターフェイス メンバーの列挙型は、既定でパブリック アクセスに設定されます。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-183">Class, structure, module, and interface member enumerations default to public access.</span></span> <span data-ttu-id="d4ad5-184">アクセス修飾子を使用してこれらのアクセス レベルを調整できます。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-184">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="d4ad5-185">名前空間メンバーの列挙型は、既定で friend アクセスに設定されます。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-185">Namespace member enumerations default to friend access.</span></span> <span data-ttu-id="d4ad5-186">アクセス レベルはパブリックに調整できますが、プライベートにしたり保護することはできません。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-186">You can adjust their access levels to public, but not to private or protected.</span></span> <span data-ttu-id="d4ad5-187">詳しくは、「[Visual Basic でのアクセス レベル](../../programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-187">For more information, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="d4ad5-188">すべての列挙型メンバーにはパブリック アクセスがあり、それらのメンバーに対してアクセス修飾子を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-188">All enumeration members have public access, and you cannot use any access modifiers on them.</span></span> <span data-ttu-id="d4ad5-189">ただし、列挙型自体のアクセス レベルがより制限されている場合は、指定された列挙型アクセス レベルが優先されます。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-189">However, if the enumeration itself has a more restricted access level, the specified enumeration access level takes precedence.</span></span>

<span data-ttu-id="d4ad5-190">既定では、すべての列挙型は型であり、そのフィールドは定数です。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-190">By default, all enumerations are types and their fields are constants.</span></span> <span data-ttu-id="d4ad5-191">したがって、列挙型またはそのメンバーを宣言するときに、`Shared`、`Static`、および `ReadOnly` キーワードを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-191">Therefore the `Shared`, `Static`, and `ReadOnly` keywords cannot be used when declaring an enumeration or its members.</span></span>

## <a name="assigning-multiple-values"></a><span data-ttu-id="d4ad5-192">複数の値の割り当て</span><span class="sxs-lookup"><span data-stu-id="d4ad5-192">Assigning Multiple Values</span></span>

<span data-ttu-id="d4ad5-193">列挙型は、通常、相互に排他的な値を表します。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-193">Enumerations typically represent mutually exclusive values.</span></span> <span data-ttu-id="d4ad5-194">`Enum` 宣言に <xref:System.FlagsAttribute> 属性を含めることにより、複数の値を列挙型のインスタンスに割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-194">By including the <xref:System.FlagsAttribute> attribute in the `Enum` declaration, you can instead assign multiple values to an instance of the enumeration.</span></span> <span data-ttu-id="d4ad5-195"><xref:System.FlagsAttribute> 属性では、列挙型がビット フィールド、つまりフラグのセットとして扱われることが指定されます。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-195">The <xref:System.FlagsAttribute> attribute specifies that the enumeration be treated as a bit field, that is, a set of flags.</span></span> <span data-ttu-id="d4ad5-196">これらは、"*ビット単位の*" 列挙型と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-196">These are called *bitwise* enumerations.</span></span>

<span data-ttu-id="d4ad5-197"><xref:System.FlagsAttribute> 属性を使用して列挙型を宣言する場合は、値に対して 2 の累乗 (1、2、4、8、16 など) を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-197">When you declare an enumeration by using the <xref:System.FlagsAttribute> attribute, we recommend that you use powers of 2, that is, 1, 2, 4, 8, 16, and so on, for the values.</span></span> <span data-ttu-id="d4ad5-198">また、値が 0 のメンバーの名前を "None" にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-198">We also recommend that "None" be the name of a member whose value is 0.</span></span> <span data-ttu-id="d4ad5-199">その他のガイドラインについては、「<xref:System.FlagsAttribute>」および「<xref:System.Enum>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-199">For additional guidelines, see <xref:System.FlagsAttribute> and <xref:System.Enum>.</span></span>

## <a name="example"></a><span data-ttu-id="d4ad5-200">例</span><span class="sxs-lookup"><span data-stu-id="d4ad5-200">Example</span></span>

<span data-ttu-id="d4ad5-201">`Enum` ステートメントを使用する方法の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-201">The following example shows how to use the `Enum` statement.</span></span> <span data-ttu-id="d4ad5-202">メンバーは、`Medium` ではなく `EggSizeEnum.Medium` と呼ばれることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-202">Note that the member is referred to as `EggSizeEnum.Medium`, and not as `Medium`.</span></span>

[!code-vb[VbEnumsTask#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#41)]

## <a name="example"></a><span data-ttu-id="d4ad5-203">例</span><span class="sxs-lookup"><span data-stu-id="d4ad5-203">Example</span></span>

<span data-ttu-id="d4ad5-204">次の例のメソッドは、`Egg` クラスの外部にあります。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-204">The method in the following example is outside the `Egg` class.</span></span> <span data-ttu-id="d4ad5-205">したがって、`EggSizeEnum` は `Egg.EggSizeEnum` として完全修飾されます。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-205">Therefore, `EggSizeEnum` is fully qualified as `Egg.EggSizeEnum`.</span></span>

[!code-vb[VbEnumsTask#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#42)]

## <a name="example"></a><span data-ttu-id="d4ad5-206">例</span><span class="sxs-lookup"><span data-stu-id="d4ad5-206">Example</span></span>

<span data-ttu-id="d4ad5-207">次の例では、`Enum` ステートメントを使用して、関連する一連の名前付き定数値を定義します。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-207">The following example uses the `Enum` statement to define a related set of named constant values.</span></span> <span data-ttu-id="d4ad5-208">この場合、値は、データベースのデータ入力フォームをデザインするために選択できる色です。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-208">In this case, the values are colors you might choose to design data entry forms for a database.</span></span>

[!code-vb[VbEnumsTask#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#30)]

## <a name="example"></a><span data-ttu-id="d4ad5-209">例</span><span class="sxs-lookup"><span data-stu-id="d4ad5-209">Example</span></span>

<span data-ttu-id="d4ad5-210">次の例は、正の数と負の数の両方を含む値を示しています。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-210">The following example shows values that include both positive and negative numbers.</span></span>

[!code-vb[VbEnumsTask#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#31)]

## <a name="example"></a><span data-ttu-id="d4ad5-211">例</span><span class="sxs-lookup"><span data-stu-id="d4ad5-211">Example</span></span>

<span data-ttu-id="d4ad5-212">次の例では、`As` 句を使用して列挙型の `datatype` を指定します。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-212">In the following example, an `As` clause is used to specify the `datatype` of an enumeration.</span></span>

[!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]

## <a name="example"></a><span data-ttu-id="d4ad5-213">例</span><span class="sxs-lookup"><span data-stu-id="d4ad5-213">Example</span></span>

<span data-ttu-id="d4ad5-214">次の例は、ビット単位の列挙型を使用する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-214">The following example shows how to use a bitwise enumeration.</span></span> <span data-ttu-id="d4ad5-215">ビット単位の列挙型のインスタンスには複数の値を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-215">Multiple values can be assigned to an instance of a bitwise enumeration.</span></span> <span data-ttu-id="d4ad5-216">`Enum` 宣言には <xref:System.FlagsAttribute> 属性が含まれています。これは、列挙型をフラグのセットとして処理できることを示します。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-216">The `Enum` declaration includes the <xref:System.FlagsAttribute> attribute, which indicates that the enumeration can be treated as a set of flags.</span></span>

[!code-vb[VbEnumsTask#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#61)]

## <a name="example"></a><span data-ttu-id="d4ad5-217">例</span><span class="sxs-lookup"><span data-stu-id="d4ad5-217">Example</span></span>

<span data-ttu-id="d4ad5-218">次の例では、列挙型を反復処理します。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-218">The following example iterates through an enumeration.</span></span> <span data-ttu-id="d4ad5-219"><xref:System.Enum.GetNames%2A> メソッドを使用して列挙型からメンバー名の配列を取得し、<xref:System.Enum.GetValues%2A> を使用してメンバー値の配列を取得します。</span><span class="sxs-lookup"><span data-stu-id="d4ad5-219">It uses the <xref:System.Enum.GetNames%2A> method to retrieve an array of member names from the enumeration, and <xref:System.Enum.GetValues%2A> to retrieve an array of member values.</span></span>

[!code-vb[VbEnumsTask#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#51)]

## <a name="see-also"></a><span data-ttu-id="d4ad5-220">関連項目</span><span class="sxs-lookup"><span data-stu-id="d4ad5-220">See also</span></span>

- <xref:System.Enum>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [<span data-ttu-id="d4ad5-221">Const ステートメント</span><span class="sxs-lookup"><span data-stu-id="d4ad5-221">Const Statement</span></span>](const-statement.md)
- [<span data-ttu-id="d4ad5-222">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="d4ad5-222">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="d4ad5-223">暗黙の型変換と明示的な型変換</span><span class="sxs-lookup"><span data-stu-id="d4ad5-223">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="d4ad5-224">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="d4ad5-224">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="d4ad5-225">定数と列挙体</span><span class="sxs-lookup"><span data-stu-id="d4ad5-225">Constants and Enumerations</span></span>](../constants-and-enumerations.md)
