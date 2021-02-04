---
title: 型とそのメンバーの定義 ‐ C# のツアー
description: プログラムの構成要素は型です。 C# でクラス、構造体、インターフェイスなどを作成する方法について説明します。
ms.date: 08/06/2020
ms.openlocfilehash: b1ce24611fec6fdf01d5ecb8d6ae974e147c78c5
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2021
ms.locfileid: "99216604"
---
# <a name="types-and-members"></a><span data-ttu-id="921d5-104">型とメンバー</span><span class="sxs-lookup"><span data-stu-id="921d5-104">Types and members</span></span>

<span data-ttu-id="921d5-105">C# は、オブジェクト指向言語として、カプセル化、継承、およびポリモーフィズムの概念をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="921d5-105">As an object-oriented language, C# supports the concepts of encapsulation, inheritance, and polymorphism.</span></span> <span data-ttu-id="921d5-106">クラスは 1 つの親クラスから直接継承でき、任意の数のインターフェイスを実装できます。</span><span class="sxs-lookup"><span data-stu-id="921d5-106">A class may inherit directly from one parent class, and it may implement any number of interfaces.</span></span> <span data-ttu-id="921d5-107">親クラスの仮想メソッドをオーバーライドする場合、誤って再定義しないように、`override` キーワードを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="921d5-107">Methods that override virtual methods in a parent class require the `override` keyword as a way to avoid accidental redefinition.</span></span> <span data-ttu-id="921d5-108">C# の構造体はコンパクトなクラスのようなものです。インターフェイスを実装できるスタック割り当て型ですが、継承はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="921d5-108">In C#, a struct is like a lightweight class; it's a stack-allocated type that can implement interfaces but doesn't support inheritance.</span></span> <span data-ttu-id="921d5-109">C# には、主にデータ値を格納する目的を持つクラス型であるレコードも用意されています。</span><span class="sxs-lookup"><span data-stu-id="921d5-109">C# also provides records, which are class types whose purpose is primarily storing data values.</span></span>

## <a name="classes-and-objects"></a><span data-ttu-id="921d5-110">クラスとオブジェクト</span><span class="sxs-lookup"><span data-stu-id="921d5-110">Classes and objects</span></span>

<span data-ttu-id="921d5-111">"*クラス*" は C# の最も基本的な型です。</span><span class="sxs-lookup"><span data-stu-id="921d5-111">*Classes* are the most fundamental of C#’s types.</span></span> <span data-ttu-id="921d5-112">クラスは、状態 (フィールド) とアクション (メソッドおよびその他の関数メンバー) を 1 つの単位としてまとめたデータ構造です。</span><span class="sxs-lookup"><span data-stu-id="921d5-112">A class is a data structure that combines state (fields) and actions (methods and other function members) in a single unit.</span></span> <span data-ttu-id="921d5-113">クラスには、*オブジェクト* とも呼ばれる、クラスの *インスタンス* の定義があります。</span><span class="sxs-lookup"><span data-stu-id="921d5-113">A class provides a definition for *instances* of the class, also known as *objects*.</span></span> <span data-ttu-id="921d5-114">クラスでは、"*継承*"と "*ポリモーフィズム*" をサポートします。これによって "*派生クラス*" が "*基底クラス*" を拡張して特殊化できます。</span><span class="sxs-lookup"><span data-stu-id="921d5-114">Classes support *inheritance* and *polymorphism*, mechanisms whereby *derived classes* can extend and specialize *base classes*.</span></span>

<span data-ttu-id="921d5-115">新しいクラスはクラス宣言を使用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="921d5-115">New classes are created using class declarations.</span></span> <span data-ttu-id="921d5-116">クラス宣言は、ヘッダーで始まります。</span><span class="sxs-lookup"><span data-stu-id="921d5-116">A class declaration starts with a header.</span></span> <span data-ttu-id="921d5-117">ヘッダーでは次を指定します。</span><span class="sxs-lookup"><span data-stu-id="921d5-117">The header specifies:</span></span>

- <span data-ttu-id="921d5-118">クラスの属性と修飾子</span><span class="sxs-lookup"><span data-stu-id="921d5-118">The attributes and modifiers of the class</span></span>
- <span data-ttu-id="921d5-119">クラスの名前</span><span class="sxs-lookup"><span data-stu-id="921d5-119">The name of the class</span></span>
- <span data-ttu-id="921d5-120">基底クラス ([基底クラス](#base-classes)から継承する場合)</span><span class="sxs-lookup"><span data-stu-id="921d5-120">The base class (when inheriting from a [base class](#base-classes))</span></span>
- <span data-ttu-id="921d5-121">このクラスによって実装されるインターフェイス。</span><span class="sxs-lookup"><span data-stu-id="921d5-121">The interfaces implemented by the class.</span></span>

<span data-ttu-id="921d5-122">ヘッダーの後にはクラス本体が続きます。これは、区切り記号 `{` と `}` の間に記述するメンバー宣言のリストで構成されます。</span><span class="sxs-lookup"><span data-stu-id="921d5-122">The header is followed by the class body, which consists of a list of member declarations written between the delimiters `{` and `}`.</span></span>

<span data-ttu-id="921d5-123">次のコードは、`Point` という名前の単純なクラスの宣言を示しています。</span><span class="sxs-lookup"><span data-stu-id="921d5-123">The following code shows a declaration of a simple class named `Point`:</span></span>

:::code language="csharp" source="./snippets/shared/Types.cs" ID="PointClass":::

<span data-ttu-id="921d5-124">クラスのインスタンスは `new` 演算子を使用して作成されます。この演算子は新しいインスタンスのメモリを割り当て、コンストラクターを呼び出してインスタンスを初期化し、インスタンスへの参照を返します。</span><span class="sxs-lookup"><span data-stu-id="921d5-124">Instances of classes are created using the `new` operator, which allocates memory for a new instance, invokes a constructor to initialize the instance, and returns a reference to the instance.</span></span> <span data-ttu-id="921d5-125">次のステートメントは、2 つの `Point` オブジェクトを作成し、2 つの変数に、それらのオブジェクトへの参照を格納します。</span><span class="sxs-lookup"><span data-stu-id="921d5-125">The following statements create two `Point` objects and store references to those objects in two variables:</span></span>

:::code language="csharp" source="./snippets/shared/Types.cs" ID="CreatePoints":::

<span data-ttu-id="921d5-126">オブジェクトで占有されたメモリは、そのオブジェクトに到達できなくなると自動的に解放されます。</span><span class="sxs-lookup"><span data-stu-id="921d5-126">The memory occupied by an object is automatically reclaimed when the object is no longer reachable.</span></span> <span data-ttu-id="921d5-127">C# では、オブジェクトの割り当てを明示的に解除する必要がなく、また解除することもできません。</span><span class="sxs-lookup"><span data-stu-id="921d5-127">It's not necessary or possible to explicitly deallocate objects in C#.</span></span>

### <a name="type-parameters"></a><span data-ttu-id="921d5-128">型パラメーター</span><span class="sxs-lookup"><span data-stu-id="921d5-128">Type parameters</span></span>

<span data-ttu-id="921d5-129">ジェネリック クラスでは "[\***型パラメーター**](../programming-guide/generics/index.md)" を定義します。</span><span class="sxs-lookup"><span data-stu-id="921d5-129">Generic classes define [\***type parameters** _](../programming-guide/generics/index.md).</span></span> <span data-ttu-id="921d5-130">型パラメーターは、山かっこで囲まれた型パラメーターの一連の名前です。</span><span class="sxs-lookup"><span data-stu-id="921d5-130">Type parameters are a list of type parameter names enclosed in angle brackets.</span></span> <span data-ttu-id="921d5-131">型パラメーターは、クラス名の後にあります。</span><span class="sxs-lookup"><span data-stu-id="921d5-131">Type parameters follow the class name.</span></span> <span data-ttu-id="921d5-132">これで、クラスのメンバーを定義するクラス宣言の本体で型パラメーターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="921d5-132">The type parameters can then be used in the body of the class declarations to define the members of the class.</span></span> <span data-ttu-id="921d5-133">次の例では、`Pair` の型パラメーターは `TFirst` と `TSecond` です。</span><span class="sxs-lookup"><span data-stu-id="921d5-133">In the following example, the type parameters of `Pair` are `TFirst` and `TSecond`:</span></span>

:::code language="csharp" source="./snippets/shared/Types.cs" ID="DefinePairClass":::

<span data-ttu-id="921d5-134">型パラメーターを受け取るために宣言されるクラス型は、"ジェネリック クラス型" と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="921d5-134">A class type that is declared to take type parameters is called a _generic class type\*.</span></span> <span data-ttu-id="921d5-135">構造体、インターフェイス、およびデリゲートの型もジェネリックです。</span><span class="sxs-lookup"><span data-stu-id="921d5-135">Struct, interface, and delegate types can also be generic.</span></span>
<span data-ttu-id="921d5-136">ジェネリック クラスを使用する場合は、それぞれの型パラメーターの型引数を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="921d5-136">When the generic class is used, type arguments must be provided for each of the type parameters:</span></span>

:::code language="csharp" source="./snippets/shared/Types.cs" ID="CreatePairObject":::

<span data-ttu-id="921d5-137">上記の `Pair<int,string>` のような、型引数が指定されたジェネリック型は "*構築された型*" と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="921d5-137">A generic type with type arguments provided, like `Pair<int,string>` above, is called a *constructed type*.</span></span>

### <a name="base-classes"></a><span data-ttu-id="921d5-138">基底クラス</span><span class="sxs-lookup"><span data-stu-id="921d5-138">Base classes</span></span>

<span data-ttu-id="921d5-139">クラスの宣言で、基底クラスを指定する場合もあります。</span><span class="sxs-lookup"><span data-stu-id="921d5-139">A class declaration may specify a base class.</span></span> <span data-ttu-id="921d5-140">クラス名と型パラメーターの後には、コロンと基底クラスの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="921d5-140">Follow the class name and type parameters with a colon and the name of the base class.</span></span> <span data-ttu-id="921d5-141">基底クラスの指定の省略は、`object` 型からの派生と同じです。</span><span class="sxs-lookup"><span data-stu-id="921d5-141">Omitting a base class specification is the same as deriving from type `object`.</span></span> <span data-ttu-id="921d5-142">次の例の `Point3D` の基底クラスは `Point` です。</span><span class="sxs-lookup"><span data-stu-id="921d5-142">In the following example, the base class of `Point3D` is `Point`.</span></span> <span data-ttu-id="921d5-143">最初の例の `Point` の基底クラスは `object` です。</span><span class="sxs-lookup"><span data-stu-id="921d5-143">From the first example, the base class of `Point` is `object`:</span></span>

:::code language="csharp" source="./snippets/shared/Types.cs" ID="Create3DPoint":::

<span data-ttu-id="921d5-144">クラスは、その基底クラスのメンバーを継承します。</span><span class="sxs-lookup"><span data-stu-id="921d5-144">A class inherits the members of its base class.</span></span> <span data-ttu-id="921d5-145">継承は、クラスにその基底クラスのほぼすべてのメンバーが暗黙的に含まれることを意味します。</span><span class="sxs-lookup"><span data-stu-id="921d5-145">Inheritance means that a class implicitly contains almost all members of its base class.</span></span> <span data-ttu-id="921d5-146">クラスは、インスタンス コンストラクター、静的コンストラクター、およびファイナライザーを継承しません。</span><span class="sxs-lookup"><span data-stu-id="921d5-146">A class doesn't inherit the instance and static constructors, and the finalizer.</span></span> <span data-ttu-id="921d5-147">派生クラスでは、継承するメンバーに新しいメンバーを追加できますが、継承されたメンバーの定義を削除することはできません。</span><span class="sxs-lookup"><span data-stu-id="921d5-147">A derived class can add new members to those members it inherits, but it can't remove the definition of an inherited member.</span></span> <span data-ttu-id="921d5-148">前述の例では、`Point3D` は、`Point` から `X` メンバーと `Y` メンバーを継承しており、各 `Point3D` インスタンスには、`X`、`Y`、`Z` の 3 つのプロパティが含まれています。</span><span class="sxs-lookup"><span data-stu-id="921d5-148">In the previous example, `Point3D` inherits the `X` and `Y` members from `Point`, and every `Point3D` instance contains three properties, `X`, `Y`, and `Z`.</span></span>

<span data-ttu-id="921d5-149">暗黙的な変換は、クラス型からその基底クラス型のいずれかに存在します。</span><span class="sxs-lookup"><span data-stu-id="921d5-149">An implicit conversion exists from a class type to any of its base class types.</span></span> <span data-ttu-id="921d5-150">クラス型の変数は、そのクラスのインスタンスまたは任意の派生クラスのインスタンスを参照できます。</span><span class="sxs-lookup"><span data-stu-id="921d5-150">A variable of a class type can reference an instance of that class or an instance of any derived class.</span></span> <span data-ttu-id="921d5-151">たとえば、前述のクラス宣言では、`Point` 型の変数が `Point` または `Point3D` を参照できます。</span><span class="sxs-lookup"><span data-stu-id="921d5-151">For example, given the previous class declarations, a variable of type `Point` can reference either a `Point` or a `Point3D`:</span></span>

:::code language="csharp" source="./snippets/shared/Types.cs" ID="ImplicitCastToBase":::

## <a name="structs"></a><span data-ttu-id="921d5-152">構造体</span><span class="sxs-lookup"><span data-stu-id="921d5-152">Structs</span></span>

<span data-ttu-id="921d5-153">クラスは、継承とポリモーフィズムをサポートする型を定義します。</span><span class="sxs-lookup"><span data-stu-id="921d5-153">Classes define types that support inheritance and polymorphism.</span></span> <span data-ttu-id="921d5-154">これにより、派生クラスの階層に基づいて高度なビヘイビアーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="921d5-154">They enable you to create sophisticated behaviors based on hierarchies of derived classes.</span></span> <span data-ttu-id="921d5-155">これに対し、"[\***構造体**](../language-reference/builtin-types/struct.md)" 型は、データ値を格納することを主な目的とするより単純な型です。</span><span class="sxs-lookup"><span data-stu-id="921d5-155">By contrast, [\***struct** _](../language-reference/builtin-types/struct.md) types are simpler types whose primary purpose is to store data values.</span></span> <span data-ttu-id="921d5-156">構造体では基本データ型を宣言できません。これらは、暗黙的に <xref:System.ValueType?displayProperty=nameWithType> から派生します。</span><span class="sxs-lookup"><span data-stu-id="921d5-156">Structs can't declare a base type; they implicitly derive from <xref:System.ValueType?displayProperty=nameWithType>.</span></span> <span data-ttu-id="921d5-157">`struct` 型から、他の `struct` 型を派生させることはできません。</span><span class="sxs-lookup"><span data-stu-id="921d5-157">You can't derive other `struct` types from a `struct` type.</span></span> <span data-ttu-id="921d5-158">これらは、暗黙的にシールされています。</span><span class="sxs-lookup"><span data-stu-id="921d5-158">They're implicitly sealed.</span></span>

:::code language="csharp" source="./snippets/shared/Types.cs" ID="PointStruct":::

## <a name="interfaces"></a><span data-ttu-id="921d5-159">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="921d5-159">Interfaces</span></span>

<span data-ttu-id="921d5-160">"[_\*_インターフェイス_\*_](../programming-guide/interfaces/index.md)" では、クラスと構造体によって実装できるコントラクトを定義します。</span><span class="sxs-lookup"><span data-stu-id="921d5-160">An [_*_interface_*_](../programming-guide/interfaces/index.md) defines a contract that can be implemented by classes and structs.</span></span> <span data-ttu-id="921d5-161">1 つのインターフェイスには、メソッド、プロパティ、イベント、およびインデクサーが含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="921d5-161">An interface can contain methods, properties, events, and indexers.</span></span> <span data-ttu-id="921d5-162">インターフェイスは、定義するメンバーの実装を通常行いません。インターフェイスを実装するクラスまたは構造体が提供する必要があるメンバーを指定するだけです。</span><span class="sxs-lookup"><span data-stu-id="921d5-162">An interface typically doesn't provide implementations of the members it defines—it merely specifies the members that must be supplied by classes or structs that implement the interface.</span></span>

<span data-ttu-id="921d5-163">インターフェイスでは "_\*_多重継承_\*_" を使用できます。</span><span class="sxs-lookup"><span data-stu-id="921d5-163">Interfaces may employ _*_multiple inheritance_*_.</span></span> <span data-ttu-id="921d5-164">次の例では、インターフェイス `IComboBox` は `ITextBox` と `IListBox` の両方から継承します。</span><span class="sxs-lookup"><span data-stu-id="921d5-164">In the following example, the interface `IComboBox` inherits from both `ITextBox` and `IListBox`.</span></span>

:::code language="csharp" source="./snippets/shared/Types.cs" ID="FirstInterfaces":::

<span data-ttu-id="921d5-165">クラスと構造体は、複数のインターフェイスを実装できます。</span><span class="sxs-lookup"><span data-stu-id="921d5-165">Classes and structs can implement multiple interfaces.</span></span> <span data-ttu-id="921d5-166">次の例では、クラス `EditBox` は `IControl` と `IDataBound` の両方を実装しています。</span><span class="sxs-lookup"><span data-stu-id="921d5-166">In the following example, the class `EditBox` implements both `IControl` and `IDataBound`.</span></span>

:::code language="csharp" source="./snippets/shared/Types.cs" ID="ImplementInterfaces":::

<span data-ttu-id="921d5-167">クラスまたは構造体が特定のインターフェイスを実装する場合、そのクラスまたは構造体のインスタンスはそのインターフェイス型に暗黙的に変換できます。</span><span class="sxs-lookup"><span data-stu-id="921d5-167">When a class or struct implements a particular interface, instances of that class or struct can be implicitly converted to that interface type.</span></span> <span data-ttu-id="921d5-168">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="921d5-168">For example</span></span>

:::code language="csharp" source="./snippets/shared/Types.cs" ID="UseInterfaces":::

## <a name="enums"></a><span data-ttu-id="921d5-169">列挙型</span><span class="sxs-lookup"><span data-stu-id="921d5-169">Enums</span></span>

<span data-ttu-id="921d5-170">"[_\*_列挙_\*_](../language-reference/builtin-types/enum.md)" 型では、一連の定数値を定義します。</span><span class="sxs-lookup"><span data-stu-id="921d5-170">An [_*_Enum_*_](../language-reference/builtin-types/enum.md) type defines a set of constant values.</span></span> <span data-ttu-id="921d5-171">次の `enum` では、さまざまな根菜の定数の定義を宣言しています。</span><span class="sxs-lookup"><span data-stu-id="921d5-171">The following `enum` declares constants that define different root vegetables:</span></span>

:::code language="csharp" source="./snippets/shared/Types.cs" ID="EnumDeclaration":::

<span data-ttu-id="921d5-172">`enum` は組み合わせてフラグとして使用できるよう、定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="921d5-172">You can also define an `enum` to be used in combination as flags.</span></span> <span data-ttu-id="921d5-173">次の宣言では、4 つの季節のフラグのセットを宣言しています。</span><span class="sxs-lookup"><span data-stu-id="921d5-173">The following declaration declares a set of flags for the four seasons.</span></span> <span data-ttu-id="921d5-174">任意に季節を組み合わせることも、すべての季節を含む `All` 値を含め、適用することも可能です。</span><span class="sxs-lookup"><span data-stu-id="921d5-174">Any combination of the seasons may be applied, including an `All` value that includes all seasons:</span></span>

:::code language="csharp" source="./snippets/shared/Types.cs" ID="FlagsEnumDeclaration":::

<span data-ttu-id="921d5-175">次の例では、上記の両列挙型を宣言しています。</span><span class="sxs-lookup"><span data-stu-id="921d5-175">The following example shows declarations of both the preceding enums:</span></span>

:::code language="csharp" source="./snippets/shared/Types.cs" ID="UsingEnums":::

## <a name="nullable-types"></a><span data-ttu-id="921d5-176">null 許容型</span><span class="sxs-lookup"><span data-stu-id="921d5-176">Nullable types</span></span>

<span data-ttu-id="921d5-177">すべての型の変数は、"_*_null 非許容_*_" または "_*_null 許容_*_" として宣言できます。</span><span class="sxs-lookup"><span data-stu-id="921d5-177">Variables of any type may be declared as _*_non-nullable_*_ or _*_nullable_*_.</span></span> <span data-ttu-id="921d5-178">null 許容の変数には、値がないことを示す `null` 値をさらに含めることができます。</span><span class="sxs-lookup"><span data-stu-id="921d5-178">A nullable variable can hold an additional `null` value, indicating no value.</span></span> <span data-ttu-id="921d5-179">null 許容値型 (構造体または列挙型) は、<xref:System.Nullable%601?displayProperty=nameWithType> で表します。</span><span class="sxs-lookup"><span data-stu-id="921d5-179">Nullable Value types (structs or enums) are represented by <xref:System.Nullable%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="921d5-180">null 非許容の参照型と null 許容の参照型はいずれも、基になる参照型によって表します。</span><span class="sxs-lookup"><span data-stu-id="921d5-180">Non-nullable and Nullable Reference types are both represented by the underlying reference type.</span></span> <span data-ttu-id="921d5-181">この区別は、コンパイラと一部のライブラリに読み取られたメタデータによって表します。</span><span class="sxs-lookup"><span data-stu-id="921d5-181">The distinction is represented by metadata read by the compiler and some libraries.</span></span> <span data-ttu-id="921d5-182">null 許容の参照が、値を最初に `null` に対してチェックせずに逆参照されると、コンパイラによって警告が出されます。</span><span class="sxs-lookup"><span data-stu-id="921d5-182">The compiler provides warnings when nullable references are dereferenced without first checking their value against `null`.</span></span> <span data-ttu-id="921d5-183">null 非許容の参照が `null` である可能性のある値に割り当てられている場合にも、コンパイラによって警告が出されます。</span><span class="sxs-lookup"><span data-stu-id="921d5-183">The compiler also provides warnings when non-nullable references are assigned a value that may be `null`.</span></span> <span data-ttu-id="921d5-184">次の例では、`null` に初期化される "_*_null 許容 int_*_" を宣言しています。</span><span class="sxs-lookup"><span data-stu-id="921d5-184">The following example declares a _*_nullable int_*_, initializing it to `null`.</span></span> <span data-ttu-id="921d5-185">次いで、その値を `5` に設定しています。</span><span class="sxs-lookup"><span data-stu-id="921d5-185">Then, it sets the value to `5`.</span></span> <span data-ttu-id="921d5-186">同じ概念を、"_*_Null 許容文字列_*_" でも示しています。</span><span class="sxs-lookup"><span data-stu-id="921d5-186">It demonstrates the same concept with a _*_nullable string_*_.</span></span> <span data-ttu-id="921d5-187">詳細については、「[null 許容値型](../language-reference/builtin-types/nullable-value-types.md)」と「[null 許容参照型](../nullable-references.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="921d5-187">For more information, see [nullable value types](../language-reference/builtin-types/nullable-value-types.md) and [nullable reference types](../nullable-references.md).</span></span>

:::code language="csharp" source="./snippets/shared/Types.cs" ID="DeclareNullable":::

## <a name="tuples"></a><span data-ttu-id="921d5-188">タプル</span><span class="sxs-lookup"><span data-stu-id="921d5-188">Tuples</span></span>

<span data-ttu-id="921d5-189">C# では、軽量のデータ構造に複数のデータ要素を簡潔な構文でグループ化できる、"[*_タプル_*\*](../language-reference/builtin-types/value-tuples.md)" がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="921d5-189">C# supports [_ *_tuples_*\*](../language-reference/builtin-types/value-tuples.md), which provides concise syntax to group multiple data elements in a lightweight data structure.</span></span> <span data-ttu-id="921d5-190">タプルは、次の例のように、`(` と `)` の間にメンバーの型と名前を宣言することで、インスタンス化できます。</span><span class="sxs-lookup"><span data-stu-id="921d5-190">You instantiate a tuple by declaring the types and names of the members between `(` and `)`, as shown in the following example:</span></span>

:::code language="csharp" source="./snippets/shared/Types.cs" ID="DeclareTuples":::

<span data-ttu-id="921d5-191">タプルは、次の記事で説明する構成要素を使用しない、複数のメンバーを持つデータ構造の代わりとなります。</span><span class="sxs-lookup"><span data-stu-id="921d5-191">Tuples provide an alternative for data structure with multiple members, without using the building blocks described in the next article.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="921d5-192">[前へ](index.md)
>[次へ](program-building-blocks.md)</span><span class="sxs-lookup"><span data-stu-id="921d5-192">[Previous](index.md)
[Next](program-building-blocks.md)</span></span>
