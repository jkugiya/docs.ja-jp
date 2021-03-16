---
title: レコード - C# リファレンス
description: C# のレコード型について説明します
ms.date: 02/25/2021
f1_keywords:
- record_CSharpKeyword
helpviewer_keywords:
- record keyword [C#]
- record type [C#]
ms.openlocfilehash: 10fe7bcc1f3239b7a6bde0abcac41b177467cf0a
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102260030"
---
# <a name="records-c-reference"></a><span data-ttu-id="68113-103">レコード (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="68113-103">Records (C# reference)</span></span>

<span data-ttu-id="68113-104">C#9 以降では、`record` キーワードを使用して、データをカプセル化するための組み込み機能を提供する[参照型](reference-types.md)を定義します。</span><span class="sxs-lookup"><span data-stu-id="68113-104">Beginning with C# 9, you use the `record` keyword to define a [reference type](reference-types.md) that provides built-in functionality for encapsulating data.</span></span> <span data-ttu-id="68113-105">位置指定パラメーターまたは標準のプロパティ構文を使用して、不変のプロパティを持つレコード型を作成できます。</span><span class="sxs-lookup"><span data-stu-id="68113-105">You can create record types with immutable properties by using positional parameters or standard property syntax:</span></span>

:::code language="csharp" source="snippets/shared/RecordType.cs" id="PositionalRecord":::
:::code language="csharp" source="snippets/shared/RecordType.cs" id="ImmutableRecord":::

<span data-ttu-id="68113-106">また、変更可能なプロパティとフィールドを使用してレコード型を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="68113-106">You can also create record types with mutable properties and fields:</span></span>

:::code language="csharp" source="snippets/shared/RecordType.cs" id="MutableRecord":::

<span data-ttu-id="68113-107">レコードは変更可能ですが、これらは主に不変のデータ モデルをサポートすることを目的としています。</span><span class="sxs-lookup"><span data-stu-id="68113-107">While records can be mutable, they are primarily intended for supporting immutable data models.</span></span> <span data-ttu-id="68113-108">レコード型には次の機能があります。</span><span class="sxs-lookup"><span data-stu-id="68113-108">The record type offers the following features:</span></span>

* [<span data-ttu-id="68113-109">不変プロパティを持つ参照型を作成するための簡潔な構文</span><span class="sxs-lookup"><span data-stu-id="68113-109">Concise syntax for creating a reference type with immutable properties</span></span>](#positional-syntax-for-property-definition)
* <span data-ttu-id="68113-110">データ中心の参照型に役立つ組み込みの動作:</span><span class="sxs-lookup"><span data-stu-id="68113-110">Built-in behavior useful for a data-centric reference type:</span></span>
  * [<span data-ttu-id="68113-111">値の等価性</span><span class="sxs-lookup"><span data-stu-id="68113-111">Value equality</span></span>](#value-equality)
  * [<span data-ttu-id="68113-112">非破壊的な変化の簡潔な構文</span><span class="sxs-lookup"><span data-stu-id="68113-112">Concise syntax for nondestructive mutation</span></span>](#nondestructive-mutation)
  * [<span data-ttu-id="68113-113">表示用の組み込みの書式設定</span><span class="sxs-lookup"><span data-stu-id="68113-113">Built-in formatting for display</span></span>](#built-in-formatting-for-display)
* [<span data-ttu-id="68113-114">継承階層のサポート</span><span class="sxs-lookup"><span data-stu-id="68113-114">Support for inheritance hierarchies</span></span>](#inheritance)

<span data-ttu-id="68113-115">[構造型](struct.md)を使用して、値の等価性があり、動作がほとんどない、またはまったくないデータ中心の型を設計することもできます。</span><span class="sxs-lookup"><span data-stu-id="68113-115">You can also use [structure types](struct.md) to design data-centric types that provide value equality and little or no behavior.</span></span> <span data-ttu-id="68113-116">ただし、比較的大規模なデータ モデルの場合、構造体型にはいくつかの欠点があります。</span><span class="sxs-lookup"><span data-stu-id="68113-116">But for relatively large data models, structure types have some disadvantages:</span></span>

* <span data-ttu-id="68113-117">継承はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="68113-117">They don't support inheritance.</span></span>
* <span data-ttu-id="68113-118">値の等価性を決定する場合には効率的ではありません。</span><span class="sxs-lookup"><span data-stu-id="68113-118">They're less efficient at determining value equality.</span></span> <span data-ttu-id="68113-119">値型の場合、<xref:System.ValueType.Equals%2A?displayProperty=nameWithType> メソッドによってリフレクションが使用され、すべてのフィールドが検索されます。</span><span class="sxs-lookup"><span data-stu-id="68113-119">For value types, the <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> method uses reflection to find all fields.</span></span> <span data-ttu-id="68113-120">レコードの場合、コンパイラによって `Equals` メソッドが生成されます。</span><span class="sxs-lookup"><span data-stu-id="68113-120">For records, the compiler generates the `Equals` method.</span></span> <span data-ttu-id="68113-121">実際のところ、レコードでの値の等価性の実装は、多少は高速です。</span><span class="sxs-lookup"><span data-stu-id="68113-121">In practice, the implementation of value equality in records is measurably faster.</span></span>
* <span data-ttu-id="68113-122">すべてのインスタンスにすべてのデータの完全なコピーがあるため、一部のシナリオではより多くのメモリが使用されます。</span><span class="sxs-lookup"><span data-stu-id="68113-122">They use more memory in some scenarios, since every instance has a complete copy of all of the data.</span></span> <span data-ttu-id="68113-123">レコード型は[参照型](reference-types.md)であるため、レコード インスタンスにはデータへの参照のみが含まれます。</span><span class="sxs-lookup"><span data-stu-id="68113-123">Record types are [reference types](reference-types.md), so a record instance contains only a reference to the data.</span></span>

## <a name="positional-syntax-for-property-definition"></a><span data-ttu-id="68113-124">プロパティ定義の位置指定構文</span><span class="sxs-lookup"><span data-stu-id="68113-124">Positional syntax for property definition</span></span>

<span data-ttu-id="68113-125">位置指定パラメーターを使用すると、レコードのプロパティを宣言し、インスタンスを作成するときにプロパティ値を初期化できます。</span><span class="sxs-lookup"><span data-stu-id="68113-125">You can use positional parameters to declare properties of a record and to initialize the property values when you create an instance:</span></span>

:::code language="csharp" source="snippets/shared/RecordType.cs" id="InstantiatePositional":::

<span data-ttu-id="68113-126">プロパティ定義に位置指定構文を使用すると、コンパイラにより、以下が作成されます。</span><span class="sxs-lookup"><span data-stu-id="68113-126">When you use the positional syntax for property definition, the compiler creates:</span></span>

* <span data-ttu-id="68113-127">レコード宣言で指定される各位置指定パラメーターのパブリック init 専用自動実装プロパティ。</span><span class="sxs-lookup"><span data-stu-id="68113-127">A public init-only auto-implemented property for each positional parameter provided in the record declaration.</span></span> <span data-ttu-id="68113-128">[init 専用](../../whats-new/csharp-9.md#init-only-setters)プロパティは、コンストラクターで、またはプロパティ初期化子を使用して設定できます。</span><span class="sxs-lookup"><span data-stu-id="68113-128">An [init-only](../../whats-new/csharp-9.md#init-only-setters) property can only be set in the constructor or by using a property initializer.</span></span>
* <span data-ttu-id="68113-129">パラメーターがレコード宣言の位置指定パラメーターと一致するプライマリ コンストラクター。</span><span class="sxs-lookup"><span data-stu-id="68113-129">A primary constructor whose parameters match the positional parameters on the record declaration.</span></span>
* <span data-ttu-id="68113-130">レコード宣言で指定された各定位置指定パラメーターの `out` パラメーターを使用する `Deconstruct` メソッド。</span><span class="sxs-lookup"><span data-stu-id="68113-130">A `Deconstruct` method with an `out` parameter for each positional parameter provided in the record declaration.</span></span> <span data-ttu-id="68113-131">このメソッドは、2 つ以上の位置指定パラメーターがある場合にのみ指定されます。</span><span class="sxs-lookup"><span data-stu-id="68113-131">This method is provided only if there are two or more positional parameters.</span></span> <span data-ttu-id="68113-132">このメソッドにより、位置指定構文を使用して定義されたプロパティは分解されます。標準のプロパティ構文を使用して定義されたプロパティは無視されます。</span><span class="sxs-lookup"><span data-stu-id="68113-132">The method deconstructs properties defined by using positional syntax; it ignores properties that are defined by using standard property syntax.</span></span>

<span data-ttu-id="68113-133">生成された自動実装プロパティ定義が目的の内容ではない場合は、同じ名前の独自のプロパティを定義できます。</span><span class="sxs-lookup"><span data-stu-id="68113-133">If the generated auto-implemented property definition isn't what you want, you can define your own property of the same name.</span></span> <span data-ttu-id="68113-134">これを行うと、そのプロパティ定義が生成されたコンストラクターとデコンストラクターに使用されます。</span><span class="sxs-lookup"><span data-stu-id="68113-134">If you do that, the generated constructor and deconstructor will use your property definition.</span></span> <span data-ttu-id="68113-135">たとえば、次の例では、`public` ではなく `FirstName` 位置指定プロパティ `internal` が作成されます。</span><span class="sxs-lookup"><span data-stu-id="68113-135">For instance, the following example makes the `FirstName` positional property `internal` instead of `public`.</span></span>

:::code language="csharp" source="snippets/shared/RecordType.cs" id="PositionalWithManualProperty":::

<span data-ttu-id="68113-136">レコード型の場合、位置指定プロパティを宣言する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="68113-136">A record type doesn't have to declare any positional properties.</span></span> <span data-ttu-id="68113-137">次の例のように、位置指定プロパティを使用せずにレコードを宣言することや、追加のフィールドとプロパティを宣言することができます。</span><span class="sxs-lookup"><span data-stu-id="68113-137">You can declare a record without any positional properties, and you can declare additional fields and properties, as in the following example:</span></span>

:::code language="csharp" source="snippets/shared/RecordType.cs" id="MixedSyntax":::

<span data-ttu-id="68113-138">標準のプロパティ構文を使用してプロパティを定義し、アクセス修飾子を省略した場合、プロパティは暗黙的に `public` になります。</span><span class="sxs-lookup"><span data-stu-id="68113-138">If you define properties by using standard property syntax but omit the access modifier, the properties are implicitly `public`.</span></span>
<!-- Todo -- Explain issues surrounding use of attributes on positional properties. -->

## <a name="immutability"></a><span data-ttu-id="68113-139">不変性</span><span class="sxs-lookup"><span data-stu-id="68113-139">Immutability</span></span>

<span data-ttu-id="68113-140">レコード型は必ずしも不変ではありません。</span><span class="sxs-lookup"><span data-stu-id="68113-140">A record type is not necessarily immutable.</span></span> <span data-ttu-id="68113-141">`readonly` ではない `set` アクセサーとフィールドを使用してプロパティを宣言できます。</span><span class="sxs-lookup"><span data-stu-id="68113-141">You can declare properties with `set` accessors and fields that aren't `readonly`.</span></span> <span data-ttu-id="68113-142">ただし、レコードは変更可能ですが、不変のデータ モデルを簡単に作成できます。</span><span class="sxs-lookup"><span data-stu-id="68113-142">But while records can be mutable, they make it easier to create immutable data models.</span></span>

<span data-ttu-id="68113-143">不変性は、データ中心の型をスレッドセーフにする必要がある場合またはハッシュ テーブル内で変化のないハッシュ コードに依存している場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="68113-143">Immutability can be useful when you need a data-centric type to be thread-safe or you're depending on a hash code remaining the same in a hash table.</span></span> <span data-ttu-id="68113-144">ただし、不変性は、すべてのデータ シナリオに適しているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="68113-144">Immutability isn't appropriate for all data scenarios, however.</span></span> <span data-ttu-id="68113-145">たとえば、[Entity Framework Core](/ef/core/) では、不変のエンティティ型を使用した更新がサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="68113-145">[Entity Framework Core](/ef/core/), for example, doesn't support updating with immutable entity types.</span></span>

<span data-ttu-id="68113-146">位置指定パラメーターから作成されたか、`init` アクセサーを指定して作成されたかにかかわらず、init 専用プロパティには "*浅い不変性*" があります。</span><span class="sxs-lookup"><span data-stu-id="68113-146">Init-only properties, whether created from positional parameters or by specifying `init` accessors, have *shallow immutability*.</span></span> <span data-ttu-id="68113-147">初期化後に、値型プロパティの値または参照型プロパティの参照を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="68113-147">After initialization, you can't change the value of value-type properties or the reference of reference-type properties.</span></span> <span data-ttu-id="68113-148">ただし、参照型プロパティから参照されるデータは変更できます。</span><span class="sxs-lookup"><span data-stu-id="68113-148">However, the data that a reference-type property refers to can be changed.</span></span> <span data-ttu-id="68113-149">次の例は、参照型の不変プロパティ (この場合は配列) の内容が変更可能であることを示しています。</span><span class="sxs-lookup"><span data-stu-id="68113-149">The following example shows that the content of a reference-type immutable property (an array in this case) is mutable:</span></span>

:::code language="csharp" source="snippets/shared/RecordType.cs" id="ShallowImmutability":::

<span data-ttu-id="68113-150">レコード型に固有の機能は、コンパイラによって合成されたメソッドによって実装されます。このようなメソッドのいずれを使用してオブジェクトの状態を変更しても、不変性は損なわれません。</span><span class="sxs-lookup"><span data-stu-id="68113-150">The features unique to record types are implemented by compiler-synthesized methods, and none of these methods compromises immutability by modifying object state.</span></span>

## <a name="value-equality"></a><span data-ttu-id="68113-151">値の等価性</span><span class="sxs-lookup"><span data-stu-id="68113-151">Value equality</span></span>

<span data-ttu-id="68113-152">値の等価性とは、型が一致し、かつプロパティおよびフィールドの値がすべて一致する場合にレコード型の 2 つの変数が等しいことを意味します。</span><span class="sxs-lookup"><span data-stu-id="68113-152">Value equality means that two variables of a record type are equal if the types match and all property and field values match.</span></span> <span data-ttu-id="68113-153">その他の参照型の場合、等価性は ID を意味します。</span><span class="sxs-lookup"><span data-stu-id="68113-153">For other reference types, equality means identity.</span></span> <span data-ttu-id="68113-154">つまり、参照型の 2 つの変数は、同じオブジェクトを参照する場合、等しいことになります。</span><span class="sxs-lookup"><span data-stu-id="68113-154">That is, two variables of a reference type are equal if they refer to the same object.</span></span>

<span data-ttu-id="68113-155">一部のデータ モデルでは、参照の等価性が必要です。</span><span class="sxs-lookup"><span data-stu-id="68113-155">Reference equality is required for some data models.</span></span> <span data-ttu-id="68113-156">たとえば、[Entity Framework Core](/ef/core/) では、概念的に 1 つのエンティティであるものに対して、エンティティ型の 1 つのインスタンスだけが確実に使用されるようにするために、参照の等価性に依存します。</span><span class="sxs-lookup"><span data-stu-id="68113-156">For example, [Entity Framework Core](/ef/core/) depends on reference equality to ensure that it uses only one instance of an entity type for what is conceptually one entity.</span></span> <span data-ttu-id="68113-157">このため、レコード型は Entity Framework Core でエンティティ型として使用するのに適していません。</span><span class="sxs-lookup"><span data-stu-id="68113-157">For this reason, record types aren't appropriate for use as entity types in Entity Framework Core.</span></span>

<span data-ttu-id="68113-158">次の例は、レコード型の値が等しいことを示しています。</span><span class="sxs-lookup"><span data-stu-id="68113-158">The following example illustrates value equality of record types:</span></span>

:::code language="csharp" source="snippets/shared/RecordType.cs" id="Equality":::

<span data-ttu-id="68113-159">値の等価性を実装するために、コンパイラにより、次のメソッドが合成されます。</span><span class="sxs-lookup"><span data-stu-id="68113-159">To implement value equality, the compiler synthesizes the following methods:</span></span>

* <span data-ttu-id="68113-160"><xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> のオーバーライド。</span><span class="sxs-lookup"><span data-stu-id="68113-160">An override of <xref:System.Object.Equals(System.Object)?displayProperty=nameWithType>.</span></span>

  <span data-ttu-id="68113-161">このメソッドは、両方のパラメーターが null でない場合に、<xref:System.Object.Equals(System.Object,System.Object)?displayProperty=nameWithType> 静的メソッドの基礎として使用されます。</span><span class="sxs-lookup"><span data-stu-id="68113-161">This method is used as the basis for the <xref:System.Object.Equals(System.Object,System.Object)?displayProperty=nameWithType> static method when both parameters are non-null.</span></span>

* <span data-ttu-id="68113-162">パラメーターがレコード型である仮想 `Equals` メソッド。</span><span class="sxs-lookup"><span data-stu-id="68113-162">A virtual `Equals` method whose parameter is the record type.</span></span> <span data-ttu-id="68113-163">このメソッドは、<xref:System.IEquatable%601> を実装します。</span><span class="sxs-lookup"><span data-stu-id="68113-163">This method implements <xref:System.IEquatable%601>.</span></span>

* <span data-ttu-id="68113-164"><xref:System.Object.GetHashCode?displayProperty=nameWithType> のオーバーライド。</span><span class="sxs-lookup"><span data-stu-id="68113-164">An override of <xref:System.Object.GetHashCode?displayProperty=nameWithType>.</span></span>

* <span data-ttu-id="68113-165">演算子 `==` および `!=` のオーバーライド。</span><span class="sxs-lookup"><span data-stu-id="68113-165">Overrides of operators `==` and `!=`.</span></span>

<span data-ttu-id="68113-166">`class` 型では、等価性メソッドと演算子を手動でオーバーライドして値の等価性を実現できますが、そのコードの開発とテストには時間がかかり、エラーが発生しやすいものです。</span><span class="sxs-lookup"><span data-stu-id="68113-166">In `class` types, you could manually override equality methods and operators to achieve value equality, but developing and testing that code would be time-consuming and error-prone.</span></span> <span data-ttu-id="68113-167">この機能を組み込むと、プロパティまたはフィールドが追加または変更されたときにカスタムのオーバーライド コードの更新を忘れたことで発生するバグを防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="68113-167">Having this functionality built-in prevents bugs that would result from forgetting to update custom override code when properties or fields are added or changed.</span></span>

<span data-ttu-id="68113-168">このような合成されたメソッドのいずれかを置き換えるために、独自の実装を作成できます。</span><span class="sxs-lookup"><span data-stu-id="68113-168">You can write your own implementations to replace any of these synthesized methods.</span></span> <span data-ttu-id="68113-169">レコード型に、いずれかの合成メソッドのシグネチャと一致するメソッドがある場合、コンパイラでそのメソッドは合成されません。</span><span class="sxs-lookup"><span data-stu-id="68113-169">If a record type has a method that matches the signature of any synthesized method, the compiler doesn't synthesize that method.</span></span>

<span data-ttu-id="68113-170">レコード型で `Equals` の独自の実装を用意する場合は、`GetHashCode` の実装も用意してください。</span><span class="sxs-lookup"><span data-stu-id="68113-170">If you provide your own implementation of `Equals` in a record type, provide an implementation of `GetHashCode` also.</span></span>

## <a name="nondestructive-mutation"></a><span data-ttu-id="68113-171">非破壊な変化</span><span class="sxs-lookup"><span data-stu-id="68113-171">Nondestructive mutation</span></span>

<span data-ttu-id="68113-172">レコード インスタンスの不変プロパティを変更する必要がある場合は、`with` 式を使用して "*非破壊的な変化*" を実現できます。</span><span class="sxs-lookup"><span data-stu-id="68113-172">If you need to mutate immutable properties of a record instance, you can use a `with` expression to achieve *nondestructive mutation*.</span></span> <span data-ttu-id="68113-173">`with` 式を使用すると、指定したプロパティとフィールドが変更された、既存のレコード インスタンスのコピーである新しいレコード インスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="68113-173">A `with` expression makes a new record instance that is a copy of an existing record instance, with specified properties and fields modified.</span></span> <span data-ttu-id="68113-174">次の例に示すように、[オブジェクト初期化子](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)構文を使用して、変更する値を指定します。</span><span class="sxs-lookup"><span data-stu-id="68113-174">You use [object initializer](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) syntax to specify the values to be changed, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/shared/RecordType.cs" id="WithExpressions":::

<span data-ttu-id="68113-175">`with` 式により、位置指定プロパティ、または標準のプロパティ構文を使用して作成されたプロパティを設定できます。</span><span class="sxs-lookup"><span data-stu-id="68113-175">The `with` expression can set positional properties or properties created by using standard property syntax.</span></span> <span data-ttu-id="68113-176">位置指定ではないプロパティの場合、`with` 式で変更される `init` または `set` アクセサーが必要です。</span><span class="sxs-lookup"><span data-stu-id="68113-176">Non-positional properties must have an `init` or `set` accessor to be changed in a `with` expression.</span></span>

<span data-ttu-id="68113-177">`with` 式の結果は "*浅いコピー*" です。つまり、参照プロパティの場合、インスタンスへの参照のみがコピーされます。</span><span class="sxs-lookup"><span data-stu-id="68113-177">The result of a `with` expression is a *shallow copy*, which means that for a reference property, only the reference to an instance is copied.</span></span> <span data-ttu-id="68113-178">元のレコードとコピーの両方が、同じインスタンスへの参照になります。</span><span class="sxs-lookup"><span data-stu-id="68113-178">Both the original record and the copy end up with a reference to the same instance.</span></span>

<span data-ttu-id="68113-179">この機能を実装するために、コンパイラにより、クローン メソッドとコピー コンストラクターが合成されます。</span><span class="sxs-lookup"><span data-stu-id="68113-179">To implement this feature, the compiler synthesizes a clone method and a copy constructor.</span></span> <span data-ttu-id="68113-180">コンストラクターにより、コピーされるレコードのインスタンスが取得され、クローン メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="68113-180">The constructor takes an instance of the record to be copied and calls the clone method.</span></span> <span data-ttu-id="68113-181">`with` 式を使用すると、コピー コンストラクターを呼び出すコードがコンパイラによって作成され、`with` 式で指定されたプロパティが設定されます。</span><span class="sxs-lookup"><span data-stu-id="68113-181">When you use a `with` expression, the compiler creates code that calls the copy constructor and then sets the properties that are specified in the `with` expression.</span></span>

<span data-ttu-id="68113-182">別のコピー動作が必要な場合は、独自のコピー コンストラクターを作成できます。</span><span class="sxs-lookup"><span data-stu-id="68113-182">If you need different copying behavior, you can write your own copy constructor.</span></span> <span data-ttu-id="68113-183">こうすると、コンパイラによって合成されません。</span><span class="sxs-lookup"><span data-stu-id="68113-183">If you do that, the compiler won't synthesize one.</span></span> <span data-ttu-id="68113-184">レコードが `sealed` の場合はコンストラクターが `private` になり、それ以外の場合は `protected` になります。</span><span class="sxs-lookup"><span data-stu-id="68113-184">Make your constructor `private` if the record is `sealed`, otherwise make it `protected`.</span></span>

<span data-ttu-id="68113-185">クローン メソッドをオーバーライドすることや、`Clone` という名前のメンバーを作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="68113-185">You can't override the clone method, and you can't create a member named `Clone`.</span></span> <span data-ttu-id="68113-186">クローン メソッドの実際の名前はコンパイラによって生成されます。</span><span class="sxs-lookup"><span data-stu-id="68113-186">The actual name of the clone method is compiler-generated.</span></span>

## <a name="built-in-formatting-for-display"></a><span data-ttu-id="68113-187">表示用の組み込みの書式設定</span><span class="sxs-lookup"><span data-stu-id="68113-187">Built-in formatting for display</span></span>

<span data-ttu-id="68113-188">レコード型には、パブリック プロパティとフィールドの名前と値を表示する、コンパイラによって生成された <xref:System.Object.ToString%2A> メソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="68113-188">Record types have a compiler-generated <xref:System.Object.ToString%2A> method that displays the names and values of public properties and fields.</span></span> <span data-ttu-id="68113-189">`ToString` メソッドからは、次の形式の文字列が返されます。</span><span class="sxs-lookup"><span data-stu-id="68113-189">The `ToString` method returns a string of the following format:</span></span>

> <span data-ttu-id="68113-190">\<record type name> { \<property name> = \<value>, \<property name> = \<value>, ...}</span><span class="sxs-lookup"><span data-stu-id="68113-190">\<record type name> { \<property name> = \<value>, \<property name> = \<value>, ...}</span></span>

<span data-ttu-id="68113-191">参照型の場合、プロパティ値ではなく、プロパティから参照されるオブジェクトの型名が表示されます。</span><span class="sxs-lookup"><span data-stu-id="68113-191">For reference types, the type name of the object that the property refers to is displayed instead of the property value.</span></span> <span data-ttu-id="68113-192">次の例では、配列は参照型であるため、実際の配列要素値ではなく `System.String[]` が表示されます。</span><span class="sxs-lookup"><span data-stu-id="68113-192">In the following example, the array is a reference type, so `System.String[]` is displayed instead of the actual array element values:</span></span>

```
Person { FirstName = Nancy, LastName = Davolio, ChildNames = System.String[] } 
```

<span data-ttu-id="68113-193">この機能を実装するために、コンパイラにより、仮想 `PrintMembers` メソッドと <xref:System.Object.ToString%2A> のオーバーライドが合成されます。</span><span class="sxs-lookup"><span data-stu-id="68113-193">To implement this feature, the compiler synthesizes a virtual `PrintMembers` method and a <xref:System.Object.ToString%2A> override.</span></span>
<span data-ttu-id="68113-194">`ToString` のオーバーライドにより、型名の後に左角かっこが続く <xref:System.Text.StringBuilder> オブジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="68113-194">The `ToString` override creates a <xref:System.Text.StringBuilder> object with the type name followed by an opening bracket.</span></span> <span data-ttu-id="68113-195">プロパティの名前と値を追加する `PrintMembers` が呼び出され、右角かっこが追加されます。</span><span class="sxs-lookup"><span data-stu-id="68113-195">It calls `PrintMembers` to add property names and values, then adds the closing bracket.</span></span> <span data-ttu-id="68113-196">次の例は、合成されたオーバーライドに含まれているものと似たコードを示しています。</span><span class="sxs-lookup"><span data-stu-id="68113-196">The following example shows code similar to what the synthesized override contains:</span></span>

:::code language="csharp" source="snippets/shared/RecordType.cs" id="ToStringOverrideDefault":::

<span data-ttu-id="68113-197">`PrintMembers` または `ToString` のオーバーライドに独自の実装を用意できます。</span><span class="sxs-lookup"><span data-stu-id="68113-197">You can provide your own implementation of `PrintMembers` or the `ToString` override.</span></span> <span data-ttu-id="68113-198">たとえば、この記事で後述する「[派生レコードに含まれる `PrintMembers` の書式設定](#printmembers-formatting-in-derived-records)」です。</span><span class="sxs-lookup"><span data-stu-id="68113-198">Examples are provided in the [`PrintMembers` formatting in derived records](#printmembers-formatting-in-derived-records) section later in this article.</span></span>

## <a name="inheritance"></a><span data-ttu-id="68113-199">継承</span><span class="sxs-lookup"><span data-stu-id="68113-199">Inheritance</span></span>

<span data-ttu-id="68113-200">レコードは、別のレコードから継承できます。</span><span class="sxs-lookup"><span data-stu-id="68113-200">A record can inherit from another record.</span></span> <span data-ttu-id="68113-201">ただし、レコードはクラスから継承できません。また、クラスはレコードから継承できません。</span><span class="sxs-lookup"><span data-stu-id="68113-201">However, a record can't inherit from a class, and a class can't inherit from a record.</span></span>

### <a name="positional-parameters-in-derived-record-types"></a><span data-ttu-id="68113-202">派生レコード型の位置指定パラメーター</span><span class="sxs-lookup"><span data-stu-id="68113-202">Positional parameters in derived record types</span></span>

<span data-ttu-id="68113-203">派生レコードにより、基本レコードのプライマリ コンストラクターに含まれるすべてのパラメーターに対する位置指定パラメーターが宣言されます。</span><span class="sxs-lookup"><span data-stu-id="68113-203">The derived record declares positional parameters for all the parameters in the base record primary constructor.</span></span> <span data-ttu-id="68113-204">基本レコードにより、それらのプロパティが宣言されて初期化されます。</span><span class="sxs-lookup"><span data-stu-id="68113-204">The base record declares and initializes those properties.</span></span> <span data-ttu-id="68113-205">派生レコードによってそれらは隠ぺいされませんが、基本レコードで宣言されていないパラメーターのプロパティのみが作成されて初期化されます。</span><span class="sxs-lookup"><span data-stu-id="68113-205">The derived record doesn't hide them, but only creates and initializes properties for parameters that aren't declared in its base record.</span></span>

<span data-ttu-id="68113-206">次の例は、位置指定プロパティ構文を使用した継承を示しています。</span><span class="sxs-lookup"><span data-stu-id="68113-206">The following example illustrates inheritance with positional property syntax:</span></span>

:::code language="csharp" source="snippets/shared/RecordType.cs" id="PositionalInheritance":::

### <a name="equality-in-inheritance-hierarchies"></a><span data-ttu-id="68113-207">継承階層の等価性</span><span class="sxs-lookup"><span data-stu-id="68113-207">Equality in inheritance hierarchies</span></span>

<span data-ttu-id="68113-208">2 つのレコード変数が等しくなるには、ランタイム型が等しくなければなりません。</span><span class="sxs-lookup"><span data-stu-id="68113-208">For two record variables to be equal, the run-time type must be equal.</span></span> <span data-ttu-id="68113-209">含まれている変数型は異なっていていても構いません。</span><span class="sxs-lookup"><span data-stu-id="68113-209">The types of the containing variables might be different.</span></span> <span data-ttu-id="68113-210">これを次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="68113-210">This is illustrated in the following code example:</span></span>

:::code language="csharp" source="snippets/shared/RecordType.cs" id="InheritanceEquality":::

<span data-ttu-id="68113-211">この例では、すべてのインスタンスが同じプロパティであり、同じプロパティ値です。</span><span class="sxs-lookup"><span data-stu-id="68113-211">In the example, all instances have the same properties and the same property values.</span></span> <span data-ttu-id="68113-212">ただし、両方とも `Person` 型の変数であっても、`student == teacher` から `False` が返されます。また、いずれかが `Person` 変数でもう一方が `Student` 変数であっても `student == student2` から `True` が返されます。</span><span class="sxs-lookup"><span data-stu-id="68113-212">But `student == teacher` returns `False` although both are `Person`-type variables, and `student == student2` returns `True` although one is a `Person` variable and one is a `Student` variable.</span></span>

<span data-ttu-id="68113-213">この動作を実装するために、コンパイラにより、レコード型と一致する <xref:System.Type> オブジェクトを返す `EqualityContract` プロパティが合成されます。</span><span class="sxs-lookup"><span data-stu-id="68113-213">To implement this behavior, the compiler synthesizes an `EqualityContract` property that returns a <xref:System.Type> object that matches the type of the record.</span></span> <span data-ttu-id="68113-214">これで、等価性メソッドを使用して、等価性の確認時にオブジェクトのランタイム型を比較できるようになります。</span><span class="sxs-lookup"><span data-stu-id="68113-214">This enables the equality methods to compare the runtime type of objects when they are checking for equality.</span></span> <span data-ttu-id="68113-215">レコードの基本データ型が `object` の場合、このプロパティは `virtual` です。</span><span class="sxs-lookup"><span data-stu-id="68113-215">If the base type of a record is `object`, this property is `virtual`.</span></span> <span data-ttu-id="68113-216">基本データ型が別のレコード型である場合、プロパティはオーバーライドになります。</span><span class="sxs-lookup"><span data-stu-id="68113-216">If the base type is another record type, this property is an override.</span></span> <span data-ttu-id="68113-217">レコード型が `sealed` の場合、プロパティは `sealed` です。</span><span class="sxs-lookup"><span data-stu-id="68113-217">If the record type is `sealed`, this property is `sealed`.</span></span>

<span data-ttu-id="68113-218">派生型の 2 つのインスタンスを比較する場合、合成された等価性メソッドにより、基本型と派生型のすべてのプロパティの等価性が確認されます。</span><span class="sxs-lookup"><span data-stu-id="68113-218">When comparing two instances of a derived type, the synthesized equality methods check all properties of the base and derived types for equality.</span></span> <span data-ttu-id="68113-219">合成された `GetHashCode` メソッドには、基本データ型と派生レコード型で宣言されたすべてのプロパティとフィールドからの `GetHashCode` メソッドが使用されます。</span><span class="sxs-lookup"><span data-stu-id="68113-219">The synthesized `GetHashCode` method uses the `GetHashCode` method from all properties and fields declared in the base type and the derived record type.</span></span>

### <a name="with-expressions-in-derived-records"></a><span data-ttu-id="68113-220">派生レコードの `with` 式</span><span class="sxs-lookup"><span data-stu-id="68113-220">`with` expressions in derived records</span></span>

<span data-ttu-id="68113-221">合成されたクローン メソッドには[共変の戻り値の型](~/_csharplang/proposals/csharp-9.0/covariant-returns.md)が使用されるため、`with` 式の結果は式のオペランドと同じランタイム型になります。</span><span class="sxs-lookup"><span data-stu-id="68113-221">Because the synthesized clone method uses a [covariant return type](~/_csharplang/proposals/csharp-9.0/covariant-returns.md), the result of a `with` expression has the same run-time type as the expression's operand.</span></span> <span data-ttu-id="68113-222">ランタイム型のすべてのプロパティがコピーされますが、次の例に示すように、コンパイル時型のプロパティのみを設定できます。</span><span class="sxs-lookup"><span data-stu-id="68113-222">All properties of the run-time type get copied, but you can only set properties of the compile-time type, as the following example shows:</span></span>

:::code language="csharp" source="snippets/shared/RecordType.cs" id="WithExpressionInheritance":::

### <a name="printmembers-formatting-in-derived-records"></a><span data-ttu-id="68113-223">派生レコードに含まれる `PrintMembers` の書式設定</span><span class="sxs-lookup"><span data-stu-id="68113-223">`PrintMembers` formatting in derived records</span></span>

<span data-ttu-id="68113-224">派生レコード型の合成された `PrintMembers` メソッドから、基本実装が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="68113-224">The synthesized `PrintMembers` method of a derived record type calls the base implementation.</span></span> <span data-ttu-id="68113-225">その結果、次の例に示すように、派生型と基本型の両方のすべてのパブリック プロパティとフィールドが `ToString` の出力に含まれます。</span><span class="sxs-lookup"><span data-stu-id="68113-225">The result is that all public properties and fields of both derived and base types are included in the `ToString` output, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/shared/RecordType.cs" id="ToStringInheritance":::

<span data-ttu-id="68113-226">`PrintMembers` メソッドの独自の実装を用意できます。</span><span class="sxs-lookup"><span data-stu-id="68113-226">You can provide your own implementation of the `PrintMembers` method.</span></span> <span data-ttu-id="68113-227">その場合は、次のシグネチャを使用します。</span><span class="sxs-lookup"><span data-stu-id="68113-227">If you do that, use the following signature:</span></span>

* <span data-ttu-id="68113-228">`object` から派生した (基本レコードを宣言しない) `sealed` レコードの場合: `private bool PrintMembers(StringBuilder builder)`;</span><span class="sxs-lookup"><span data-stu-id="68113-228">For a `sealed` record that derives from `object` (doesn't declare a base record): `private bool PrintMembers(StringBuilder builder)`;</span></span>
* <span data-ttu-id="68113-229">別のレコードから派生した `sealed` レコードの場合: `protected sealed override bool PrintMembers(StringBuilder builder)`;</span><span class="sxs-lookup"><span data-stu-id="68113-229">For a `sealed` record that derives from another record: `protected sealed override bool PrintMembers(StringBuilder builder)`;</span></span>
* <span data-ttu-id="68113-230">`sealed` ではなく、オブジェクトから派生したレコードの場合: `protected virtual bool PrintMembers(StringBuilder builder);`</span><span class="sxs-lookup"><span data-stu-id="68113-230">For a record that isn't `sealed` and derives from object: `protected virtual bool PrintMembers(StringBuilder builder);`</span></span>
* <span data-ttu-id="68113-231">`sealed` ではなく、別のレコードから派生したレコードの場合: `protected override bool PrintMembers(StringBuilder builder);`</span><span class="sxs-lookup"><span data-stu-id="68113-231">For a record that isn't `sealed` and derives from another record: `protected override bool PrintMembers(StringBuilder builder);`</span></span>

<span data-ttu-id="68113-232">合成された `PrintMembers` メソッドを置き換えるコードの例を次に示します。1 つはオブジェクトから派生するレコード型であり、もう 1 つは別のレコードから派生するレコード型です。</span><span class="sxs-lookup"><span data-stu-id="68113-232">Here is an example of code that replaces the synthesized `PrintMembers` methods, one for a record type that derives from object, and one for a record type that derives from another record:</span></span>

:::code language="csharp" source="snippets/shared/RecordType.cs" id="PrintMembersImplementation":::

### <a name="deconstructor-behavior-in-derived-records"></a><span data-ttu-id="68113-233">派生レコードのデコンストラクターの動作</span><span class="sxs-lookup"><span data-stu-id="68113-233">Deconstructor behavior in derived records</span></span>

<span data-ttu-id="68113-234">派生レコードの `Deconstruct` メソッドからは、コンパイル時型のすべての位置指定プロパティの値が返されます。</span><span class="sxs-lookup"><span data-stu-id="68113-234">The `Deconstruct` method of a derived record returns the values of all positional properties of the compile-time type.</span></span> <span data-ttu-id="68113-235">変数の型が基本レコードの場合、オブジェクトが派生型にキャストされない限り、基本レコードのプロパティのみが分解されます。</span><span class="sxs-lookup"><span data-stu-id="68113-235">If the variable type is a base record, only the base record properties are deconstructed unless the object is cast to the derived type.</span></span> <span data-ttu-id="68113-236">派生レコードに対してデコンストラクターを呼び出す方法の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="68113-236">The following example demonstrates calling a deconstructor on a derived record.</span></span>

:::code language="csharp" source="snippets/shared/RecordType.cs" id="DeconstructorInheritance":::

## <a name="generic-constraints"></a><span data-ttu-id="68113-237">ジェネリック制約</span><span class="sxs-lookup"><span data-stu-id="68113-237">Generic constraints</span></span>

<span data-ttu-id="68113-238">型をレコードにする必要があるジェネリック制約はありません。</span><span class="sxs-lookup"><span data-stu-id="68113-238">There is no generic constraint that requires a type to be a record.</span></span> <span data-ttu-id="68113-239">レコードは `class` 制約を満たしています。</span><span class="sxs-lookup"><span data-stu-id="68113-239">Records satisfy the `class` constraint.</span></span> <span data-ttu-id="68113-240">レコード型の特定の階層に制約を設定するには、基底クラスと同じように基本レコードに制約を設定します。</span><span class="sxs-lookup"><span data-stu-id="68113-240">To make a constraint on a specific hierarchy of record types, put the constraint on the base record as you would a base class.</span></span> <span data-ttu-id="68113-241">詳細については、「[型パラメーターの制約](../../programming-guide/generics/constraints-on-type-parameters.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="68113-241">For more information, see [Constraints on type parameters](../../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="68113-242">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="68113-242">C# language specification</span></span>

<span data-ttu-id="68113-243">詳細については、[C# 言語仕様](~/_csharplang/spec/introduction.md)の「[クラス](~/_csharplang/spec/classes.md)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="68113-243">For more information, see the [Classes](~/_csharplang/spec/classes.md) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="68113-244">C# 9 以降で導入された機能の詳細については、次の機能の提案に関するメモを参照してください。</span><span class="sxs-lookup"><span data-stu-id="68113-244">For more information about features introduced in C# 9 and later, see the following feature proposal notes:</span></span>

- [<span data-ttu-id="68113-245">レコード</span><span class="sxs-lookup"><span data-stu-id="68113-245">Records</span></span>](~/_csharplang/proposals/csharp-9.0/records.md)
- [<span data-ttu-id="68113-246">init 専用セッター</span><span class="sxs-lookup"><span data-stu-id="68113-246">Init-only setters</span></span>](~/_csharplang/proposals/csharp-9.0/init.md)
- [<span data-ttu-id="68113-247">covariant の戻り値</span><span class="sxs-lookup"><span data-stu-id="68113-247">Covariant returns</span></span>](~/_csharplang/proposals/csharp-9.0/covariant-returns.md)

## <a name="see-also"></a><span data-ttu-id="68113-248">関連項目</span><span class="sxs-lookup"><span data-stu-id="68113-248">See also</span></span>

- [<span data-ttu-id="68113-249">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="68113-249">C# reference</span></span>](../index.md)
- [<span data-ttu-id="68113-250">デザインのガイドライン - クラスまたは構造体の選択</span><span class="sxs-lookup"><span data-stu-id="68113-250">Design guidelines - Choosing between class and struct</span></span>](../../../standard/design-guidelines/choosing-between-class-and-struct.md)
- [<span data-ttu-id="68113-251">デザインのガイドライン - 構造体のデザイン</span><span class="sxs-lookup"><span data-stu-id="68113-251">Design guidelines - Struct design</span></span>](../../../standard/design-guidelines/struct.md)
- [<span data-ttu-id="68113-252">クラスと構造体</span><span class="sxs-lookup"><span data-stu-id="68113-252">Classes and structs</span></span>](../../programming-guide/classes-and-structs/index.md)
- [<span data-ttu-id="68113-253">`with` 式</span><span class="sxs-lookup"><span data-stu-id="68113-253">`with` expression</span></span>](../operators/with-expression.md)
