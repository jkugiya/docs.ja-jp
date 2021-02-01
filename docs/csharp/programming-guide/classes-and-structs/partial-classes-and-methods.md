---
title: 部分クラスと部分メソッド - C# プログラミング ガイド
description: C# の部分クラスと部分メソッドでは、クラス、構造体、インターフェイス、またはメソッドの定義を、2 つ以上のソース ファイルに分割できます。
ms.date: 07/20/2015
helpviewer_keywords:
- partial methods [C#]
- partial classes [C#]
- C# language, partial classes and methods
ms.assetid: 804cecb7-62db-4f97-a99f-60975bd59fa1
ms.openlocfilehash: cfda3b89bfd9dc046274dfa53d62a0789d4d597e
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899101"
---
# <a name="partial-classes-and-methods-c-programming-guide"></a><span data-ttu-id="3dc3a-103">部分クラスと部分メソッド (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="3dc3a-103">Partial Classes and Methods (C# Programming Guide)</span></span>

<span data-ttu-id="3dc3a-104">[クラス](../../language-reference/keywords/class.md)、[構造体](../../language-reference/builtin-types/struct.md)、[インターフェイス](../../language-reference/keywords/interface.md)やメソッドの定義を複数のソース ファイルに分割できます。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-104">It is possible to split the definition of a [class](../../language-reference/keywords/class.md), a [struct](../../language-reference/builtin-types/struct.md), an [interface](../../language-reference/keywords/interface.md) or a method over two or more source files.</span></span> <span data-ttu-id="3dc3a-105">各ソース ファイルには型やメソッドの定義のセクションが含まれ、分割されたすべての部分はアプリケーションのコンパイル時に結合されます。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-105">Each source file contains a section of the type or method definition, and all parts are combined when the application is compiled.</span></span>

## <a name="partial-classes"></a><span data-ttu-id="3dc3a-106">部分クラス</span><span class="sxs-lookup"><span data-stu-id="3dc3a-106">Partial Classes</span></span>

<span data-ttu-id="3dc3a-107">クラス定義を分割するのが望ましいのは、次のような場合です。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-107">There are several situations when splitting a class definition is desirable:</span></span>

- <span data-ttu-id="3dc3a-108">大型プロジェクトを開発する際にクラスを別個のファイルに分割すると、複数のプログラマーが同時にそのクラスの作業を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-108">When working on large projects, spreading a class over separate files enables multiple programmers to work on it at the same time.</span></span>

- <span data-ttu-id="3dc3a-109">自動的に生成されたソースを使用する場合、ソース ファイルを再作成することなく、コードをクラスに追加できます。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-109">When working with automatically generated source, code can be added to the class without having to recreate the source file.</span></span> <span data-ttu-id="3dc3a-110">Visual Studio では、Windows フォームや Web サービス ラッパー コードなどを作成するときにこのアプローチを使用します。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-110">Visual Studio uses this approach when it creates Windows Forms, Web service wrapper code, and so on.</span></span> <span data-ttu-id="3dc3a-111">Visual Studio によって作成されたファイルを変更せずに、これらのクラスを使用するコードを作成できます。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-111">You can create code that uses these classes without having to modify the file created by Visual Studio.</span></span>

- <span data-ttu-id="3dc3a-112">クラス定義を分割するには、次のように [partial](../../language-reference/keywords/partial-type.md) キーワード修飾子を使用します。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-112">To split a class definition, use the [partial](../../language-reference/keywords/partial-type.md) keyword modifier, as shown here:</span></span>

  [!code-csharp[EmployeeExample#1](snippets/partial-classes-and-methods/Program.cs#1)]

<span data-ttu-id="3dc3a-113">`partial` キーワードは、クラス、構造体、またはインターフェイスの他の部分を名前空間内で定義できることを示します。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-113">The `partial` keyword indicates that other parts of the class, struct, or interface can be defined in the namespace.</span></span> <span data-ttu-id="3dc3a-114">`partial` キーワードは、すべての部分で使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-114">All the parts must use the `partial` keyword.</span></span> <span data-ttu-id="3dc3a-115">最終的な型を形成するためには、コンパイル時にすべての部分が利用可能である必要があります。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-115">All the parts must be available at compile time to form the final type.</span></span> <span data-ttu-id="3dc3a-116">また、すべての部分で同じアクセシビリティ (`public` や `private` など) を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-116">All the parts must have the same accessibility, such as `public`, `private`, and so on.</span></span>

<span data-ttu-id="3dc3a-117">abstract と宣言された部分がある場合、型全体が抽象と見なされます。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-117">If any part is declared abstract, then the whole type is considered abstract.</span></span> <span data-ttu-id="3dc3a-118">sealed と宣言された部分がある場合、型全体が sealed と見なされます。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-118">If any part is declared sealed, then the whole type is considered sealed.</span></span> <span data-ttu-id="3dc3a-119">また、基本データ型を宣言する部分がある場合は、型全体が該当するクラスを継承します。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-119">If any part declares a base type, then the whole type inherits that class.</span></span>

<span data-ttu-id="3dc3a-120">基底クラスを指定する部分はすべて一致する必要がありますが、基底クラスを省略する部分も基本データ型を継承します。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-120">All the parts that specify a base class must agree, but parts that omit a base class still inherit the base type.</span></span> <span data-ttu-id="3dc3a-121">部分は別の基本インターフェイスを指定でき、すべての部分宣言で示されたすべてのインターフェイスが最終的な型によって実装されます。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-121">Parts can specify different base interfaces, and the final type implements all the interfaces listed by all the partial declarations.</span></span> <span data-ttu-id="3dc3a-122">部分定義で宣言されたクラス、構造体、インターフェイスの各メンバーは、他のすべての部分で利用できます。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-122">Any class, struct, or interface members declared in a partial definition are available to all the other parts.</span></span> <span data-ttu-id="3dc3a-123">最終的な型は、コンパイル時にすべての部分を結合して形成されます。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-123">The final type is the combination of all the parts at compile time.</span></span>

> [!NOTE]
> <span data-ttu-id="3dc3a-124">`partial` 識別子は、デリゲートや列挙宣言では使用できません。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-124">The `partial` modifier is not available on delegate or enumeration declarations.</span></span>

<span data-ttu-id="3dc3a-125">次の例は、入れ子にされた型は、それを包含する型自体が partial でない場合でも、partial にできることを示しています。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-125">The following example shows that nested types can be partial, even if the type they are nested within is not partial itself.</span></span>

[!code-csharp[NestedPartialTypes#2](snippets/partial-classes-and-methods/Program.cs#2)]

<span data-ttu-id="3dc3a-126">部分型定義の属性は、コンパイル時に結合されます。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-126">At compile time, attributes of partial-type definitions are merged.</span></span> <span data-ttu-id="3dc3a-127">たとえば、次のような宣言があるとします。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-127">For example, consider the following declarations:</span></span>

[!code-csharp[PartialMoonDeclarations#3](snippets/partial-classes-and-methods/Program.cs#3)]

<span data-ttu-id="3dc3a-128">これらは、次の宣言と等価です。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-128">They are equivalent to the following declarations:</span></span>

[!code-csharp[SingleMoonDeclaration#4](snippets/partial-classes-and-methods/Program.cs#4)]

<span data-ttu-id="3dc3a-129">各部分型定義に含まれる次の要素は、すべて結合されます。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-129">The following are merged from all the partial-type definitions:</span></span>

- <span data-ttu-id="3dc3a-130">XML コメント</span><span class="sxs-lookup"><span data-stu-id="3dc3a-130">XML comments</span></span>

- <span data-ttu-id="3dc3a-131">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3dc3a-131">interfaces</span></span>

- <span data-ttu-id="3dc3a-132">ジェネリック型パラメーター属性</span><span class="sxs-lookup"><span data-stu-id="3dc3a-132">generic-type parameter attributes</span></span>

- <span data-ttu-id="3dc3a-133">クラス属性</span><span class="sxs-lookup"><span data-stu-id="3dc3a-133">class attributes</span></span>

- <span data-ttu-id="3dc3a-134">メンバー</span><span class="sxs-lookup"><span data-stu-id="3dc3a-134">members</span></span>

<span data-ttu-id="3dc3a-135">たとえば、次のような宣言があるとします。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-135">For example, consider the following declarations:</span></span>

[!code-csharp[PartialEarthDeclarations#5](snippets/partial-classes-and-methods/Program.cs#5)]

<span data-ttu-id="3dc3a-136">これらは、次の宣言と等価です。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-136">They are equivalent to the following declarations:</span></span>

[!code-csharp[SingleEarthDeclaration#6](snippets/partial-classes-and-methods/Program.cs#6)]

### <a name="restrictions"></a><span data-ttu-id="3dc3a-137">制約</span><span class="sxs-lookup"><span data-stu-id="3dc3a-137">Restrictions</span></span>

<span data-ttu-id="3dc3a-138">部分クラス定義を使用する場合は、いくつかの規則に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-138">There are several rules to follow when you are working with partial class definitions:</span></span>

- <span data-ttu-id="3dc3a-139">同じ型の部分である部分型定義はすべて `partial` で修飾する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-139">All partial-type definitions meant to be parts of the same type must be modified with `partial`.</span></span> <span data-ttu-id="3dc3a-140">たとえば、次のクラス宣言はエラーになります。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-140">For example, the following class declarations generate an error:</span></span>

  [!code-csharp[AllDefinitionsMustBePartials#7](snippets/partial-classes-and-methods/Program.cs#7)]

- <span data-ttu-id="3dc3a-141">`partial` 修飾子は、`class`、`struct`、または `interface` キーワードの直前にのみ配置できます。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-141">The `partial` modifier can only appear immediately before the keywords `class`, `struct`, or `interface`.</span></span>

- <span data-ttu-id="3dc3a-142">入れ子にされた部分型は、次の例に示すように、部分型定義で宣言できます。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-142">Nested partial types are allowed in partial-type definitions as illustrated in the following example:</span></span>

  [!code-csharp[NestedPartialTypes#8](snippets/partial-classes-and-methods/Program.cs#8)]

- <span data-ttu-id="3dc3a-143">同じ型の部分である部分型定義は、すべて同じアセンブリおよび同じモジュール (.exe ファイルまたは .dll ファイル) 内で定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-143">All partial-type definitions meant to be parts of the same type must be defined in the same assembly and the same module (.exe or .dll file).</span></span> <span data-ttu-id="3dc3a-144">部分定義は、複数のモジュールにまたがることができません。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-144">Partial definitions cannot span multiple modules.</span></span>

- <span data-ttu-id="3dc3a-145">クラス名とジェネリック型パラメーターはすべての部分型定義で一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-145">The class name and generic-type parameters must match on all partial-type definitions.</span></span> <span data-ttu-id="3dc3a-146">ジェネリック型は partial にできます。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-146">Generic types can be partial.</span></span> <span data-ttu-id="3dc3a-147">それぞれの部分宣言では、同じパラメーター名を同じ順序で使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-147">Each partial declaration must use the same parameter names in the same order.</span></span>

- <span data-ttu-id="3dc3a-148">以下のキーワードは、部分型定義では省略できますが、ある 1 つの部分型定義に存在する場合は、同じ型の別の部分定義で指定されているキーワードと競合できません。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-148">The following keywords on a partial-type definition are optional, but if present on one partial-type definition, cannot conflict with the keywords specified on another partial definition for the same type:</span></span>

  - [<span data-ttu-id="3dc3a-149">public</span><span class="sxs-lookup"><span data-stu-id="3dc3a-149">public</span></span>](../../language-reference/keywords/public.md)

  - [<span data-ttu-id="3dc3a-150">private</span><span class="sxs-lookup"><span data-stu-id="3dc3a-150">private</span></span>](../../language-reference/keywords/private.md)

  - [<span data-ttu-id="3dc3a-151">protected</span><span class="sxs-lookup"><span data-stu-id="3dc3a-151">protected</span></span>](../../language-reference/keywords/protected.md)

  - [<span data-ttu-id="3dc3a-152">internal</span><span class="sxs-lookup"><span data-stu-id="3dc3a-152">internal</span></span>](../../language-reference/keywords/internal.md)

  - [<span data-ttu-id="3dc3a-153">abstract</span><span class="sxs-lookup"><span data-stu-id="3dc3a-153">abstract</span></span>](../../language-reference/keywords/abstract.md)

  - [<span data-ttu-id="3dc3a-154">sealed</span><span class="sxs-lookup"><span data-stu-id="3dc3a-154">sealed</span></span>](../../language-reference/keywords/sealed.md)

  - <span data-ttu-id="3dc3a-155">基本クラス</span><span class="sxs-lookup"><span data-stu-id="3dc3a-155">base class</span></span>

  - <span data-ttu-id="3dc3a-156">[new](../../language-reference/keywords/new-modifier.md) 修飾子 (入れ子にされた部分)</span><span class="sxs-lookup"><span data-stu-id="3dc3a-156">[new](../../language-reference/keywords/new-modifier.md) modifier (nested parts)</span></span>

  - <span data-ttu-id="3dc3a-157">ジェネリック制約</span><span class="sxs-lookup"><span data-stu-id="3dc3a-157">generic constraints</span></span>

<span data-ttu-id="3dc3a-158">詳細については、「[型パラメーターの制約](../generics/constraints-on-type-parameters.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-158">For more information, see [Constraints on Type Parameters](../generics/constraints-on-type-parameters.md).</span></span>

## <a name="example-1"></a><span data-ttu-id="3dc3a-159">例 1</span><span class="sxs-lookup"><span data-stu-id="3dc3a-159">Example 1</span></span>

### <a name="description"></a><span data-ttu-id="3dc3a-160">説明</span><span class="sxs-lookup"><span data-stu-id="3dc3a-160">Description</span></span>

<span data-ttu-id="3dc3a-161">次の例では、クラス `Coords` のフィールドとコンストラクターを 1 つの部分クラス定義で宣言し、メンバー `PrintCoords` を別の部分クラス定義で宣言しています。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-161">In the following example, the fields and the constructor of the class, `Coords`, are declared in one partial class definition, and the member, `PrintCoords`, is declared in another partial class definition.</span></span>

### <a name="code"></a><span data-ttu-id="3dc3a-162">コード</span><span class="sxs-lookup"><span data-stu-id="3dc3a-162">Code</span></span>

[!code-csharp[CoordsExample#9](snippets/partial-classes-and-methods/Program.cs#9)]

## <a name="example-2"></a><span data-ttu-id="3dc3a-163">例 2</span><span class="sxs-lookup"><span data-stu-id="3dc3a-163">Example 2</span></span>

### <a name="description"></a><span data-ttu-id="3dc3a-164">説明</span><span class="sxs-lookup"><span data-stu-id="3dc3a-164">Description</span></span>

<span data-ttu-id="3dc3a-165">次の例は、部分構造体と部分インターフェイスも開発できることを示しています。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-165">The following example shows that you can also develop partial structs and interfaces.</span></span>

### <a name="code"></a><span data-ttu-id="3dc3a-166">コード</span><span class="sxs-lookup"><span data-stu-id="3dc3a-166">Code</span></span>

[!code-csharp[PartialStructsAndInterfaces#10](snippets/partial-classes-and-methods/Program.cs#10)]

## <a name="partial-methods"></a><span data-ttu-id="3dc3a-167">部分メソッド</span><span class="sxs-lookup"><span data-stu-id="3dc3a-167">Partial Methods</span></span>

<span data-ttu-id="3dc3a-168">部分クラスまたは構造体には部分メソッドを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-168">A partial class or struct may contain a partial method.</span></span> <span data-ttu-id="3dc3a-169">クラスのある部分に、メソッドのシグネチャが含まれます。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-169">One part of the class contains the signature of the method.</span></span> <span data-ttu-id="3dc3a-170">同じ部分または別の部分に、オプションの実装を定義できます。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-170">An optional implementation may be defined in the same part or another part.</span></span> <span data-ttu-id="3dc3a-171">実装が指定されていない場合、メソッドとメソッドに対するすべての呼び出しは、コンパイル時に削除されます。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-171">If the implementation is not supplied, then the method and all calls to the method are removed at compile time.</span></span>

<span data-ttu-id="3dc3a-172">部分メソッドを使用すると、イベントと同様に、クラスのある部分の実装者がメソッドを定義できます。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-172">Partial methods enable the implementer of one part of a class to define a method, similar to an event.</span></span> <span data-ttu-id="3dc3a-173">クラスの別の部分の実装者は、メソッドを実装するかどうかを決定できます。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-173">The implementer of the other part of the class can decide whether to implement the method or not.</span></span> <span data-ttu-id="3dc3a-174">メソッドが実装されない場合、コンパイラは、メソッド シグネチャとメソッドに対するすべての呼び出しを削除します。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-174">If the method is not implemented, then the compiler removes the method signature and all calls to the method.</span></span> <span data-ttu-id="3dc3a-175">このメソッドの呼び出しは、呼び出しの引数の評価から発生するすべての結果を含め、実行時に影響を及ぼしません。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-175">The calls to the method, including any results that would occur from evaluation of arguments in the calls, have no effect at run time.</span></span> <span data-ttu-id="3dc3a-176">そのため、実装が指定されていない場合でも、部分クラス内のすべてのコードで部分メソッドを自由に使用できます。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-176">Therefore, any code in the partial class can freely use a partial method, even if the implementation is not supplied.</span></span> <span data-ttu-id="3dc3a-177">実装されていないメソッドが呼び出された場合、コンパイル時エラーまたは実行時エラーにはなりません。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-177">No compile-time or run-time errors will result if the method is called but not implemented.</span></span>

<span data-ttu-id="3dc3a-178">部分メソッドは、生成されるコードをカスタマイズする方法として特に便利です。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-178">Partial methods are especially useful as a way to customize generated code.</span></span> <span data-ttu-id="3dc3a-179">メソッドの名前とシグネチャを予約できるため、生成されるコードでメソッドを呼び出すことができます。ただし、メソッドを実装するかどうかは開発者が決定できます。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-179">They allow for a method name and signature to be reserved, so that generated code can call the method but the developer can decide whether to implement the method.</span></span> <span data-ttu-id="3dc3a-180">部分クラスと同様に、部分メソッドでも、コード ジェネレーターによって作成されたコードと人間である開発者によって作成されたコードを実行時コストなしで連携させることができます。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-180">Much like partial classes, partial methods enable code created by a code generator and code created by a human developer to work together without run-time costs.</span></span>

<span data-ttu-id="3dc3a-181">部分メソッドの宣言は、定義と実装の 2 つの部分から成ります。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-181">A partial method declaration consists of two parts: the definition, and the implementation.</span></span> <span data-ttu-id="3dc3a-182">これらは部分クラスの別々の部分にあっても同じ部分にあってもかまいません。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-182">These may be in separate parts of a partial class, or in the same part.</span></span> <span data-ttu-id="3dc3a-183">実装宣言がない場合は、定義宣言とメソッドに対するすべての呼び出しの両方が、コンパイラによる最適化によって除外されます。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-183">If there is no implementation declaration, then the compiler optimizes away both the defining declaration and all calls to the method.</span></span>

```csharp
// Definition in file1.cs
partial void onNameChanged();

// Implementation in file2.cs
partial void onNameChanged()
{
  // method body
}
```

- <span data-ttu-id="3dc3a-184">部分メソッドの宣言はコンテキスト キーワード [partial](../../language-reference/keywords/partial-type.md) で始まる必要があり、メソッドは [void](../../language-reference/builtin-types/void.md) を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-184">Partial method declarations must begin with the contextual keyword [partial](../../language-reference/keywords/partial-type.md) and the method must return [void](../../language-reference/builtin-types/void.md).</span></span>

- <span data-ttu-id="3dc3a-185">部分メソッドには、[in](../../language-reference/keywords/in-parameter-modifier.md) や [ref](../../language-reference/keywords/ref.md) パラメーターを使用できますが、[out](../../language-reference/keywords/out-parameter-modifier.md) パラメーターは使用できません。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-185">Partial methods can have [in](../../language-reference/keywords/in-parameter-modifier.md) or [ref](../../language-reference/keywords/ref.md) but not [out](../../language-reference/keywords/out-parameter-modifier.md) parameters.</span></span>

- <span data-ttu-id="3dc3a-186">部分メソッドは暗黙的に [private](../../language-reference/keywords/private.md) です。したがって部分メソッドを [virtual](../../language-reference/keywords/virtual.md) にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-186">Partial methods are implicitly [private](../../language-reference/keywords/private.md), and therefore they cannot be [virtual](../../language-reference/keywords/virtual.md).</span></span>

- <span data-ttu-id="3dc3a-187">部分メソッドを [extern](../../language-reference/keywords/extern.md) にすることはできません。部分メソッドの定義なのか実装なのかは、本体の存在で決まるためです。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-187">Partial methods cannot be [extern](../../language-reference/keywords/extern.md), because the presence of the body determines whether they are defining or implementing.</span></span>

- <span data-ttu-id="3dc3a-188">部分メソッドには [static](../../language-reference/keywords/static.md) 修飾子と [unsafe](../../language-reference/keywords/unsafe.md) 修飾子を使用できます。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-188">Partial methods can have [static](../../language-reference/keywords/static.md) and [unsafe](../../language-reference/keywords/unsafe.md) modifiers.</span></span>

- <span data-ttu-id="3dc3a-189">部分メソッドはジェネリックにできます。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-189">Partial methods can be generic.</span></span> <span data-ttu-id="3dc3a-190">制約は部分メソッドの定義宣言に置き、必要に応じて実装宣言で繰り返すことができます。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-190">Constraints are put on the defining partial method declaration, and may optionally be repeated on the implementing one.</span></span> <span data-ttu-id="3dc3a-191">パラメーター名と型パラメーター名は、定義宣言と実装宣言で同じである必要はありません。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-191">Parameter and type parameter names do not have to be the same in the implementing declaration as in the defining one.</span></span>

- <span data-ttu-id="3dc3a-192">[delegate](../../language-reference/builtin-types/reference-types.md) は、定義および実装されている部分メソッドには使用できますが、定義されているのみの部分メソッドには使用できません。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-192">You can make a [delegate](../../language-reference/builtin-types/reference-types.md) to a partial method that has been defined and implemented, but not to a partial method that has only been defined.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3dc3a-193">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="3dc3a-193">C# Language Specification</span></span>

<span data-ttu-id="3dc3a-194">詳細については、「[C# 言語仕様](/dotnet/csharp/language-reference/language-specification/introduction)」の[部分型](~/_csharplang/spec/classes.md#partial-types)に関するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-194">For more information, see [Partial types](~/_csharplang/spec/classes.md#partial-types) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="3dc3a-195">言語仕様は、C# の構文と使用法に関する信頼性のある情報源です。</span><span class="sxs-lookup"><span data-stu-id="3dc3a-195">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="3dc3a-196">関連項目</span><span class="sxs-lookup"><span data-stu-id="3dc3a-196">See also</span></span>

- [<span data-ttu-id="3dc3a-197">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="3dc3a-197">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="3dc3a-198">クラス</span><span class="sxs-lookup"><span data-stu-id="3dc3a-198">Classes</span></span>](./classes.md)
- [<span data-ttu-id="3dc3a-199">構造体型</span><span class="sxs-lookup"><span data-stu-id="3dc3a-199">Structure types</span></span>](../../language-reference/builtin-types/struct.md)
- [<span data-ttu-id="3dc3a-200">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3dc3a-200">Interfaces</span></span>](../interfaces/index.md)
- [<span data-ttu-id="3dc3a-201">partial (型)</span><span class="sxs-lookup"><span data-stu-id="3dc3a-201">partial (Type)</span></span>](../../language-reference/keywords/partial-type.md)
