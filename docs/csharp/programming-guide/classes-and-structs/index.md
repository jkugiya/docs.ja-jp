---
title: クラス、構造体、およびレコード - C# プログラミング ガイド
description: C# でのクラス、構造体、およびレコードの使用について説明します。
ms.date: 04/06/2021
helpviewer_keywords:
- structs [C#], about structs
- records [C#], about records
- classes [C#], overview
- C# language, structs
- C# language, records
- C# language, objects
- objects [C#]
- C# language, classes
ms.openlocfilehash: 69b62160699ef43343a89fe8bb3deaa2fb3523ba
ms.sourcegitcommit: 4b7f6b348c986556ef805cb6baacfd5b9ec18ed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2021
ms.locfileid: "107075460"
---
# <a name="classes-structs-and-records-c-programming-guide"></a><span data-ttu-id="883a6-103">クラス、構造体、およびレコード (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="883a6-103">Classes, structs, and records (C# programming guide)</span></span>

<span data-ttu-id="883a6-104">クラスと構造体は、.NET の共通型システムの 2 つの基本構成です。</span><span class="sxs-lookup"><span data-stu-id="883a6-104">Classes and structs are two of the basic constructs of the common type system in .NET.</span></span> <span data-ttu-id="883a6-105">C# 9 では、クラスの一種であるレコードが追加されます。</span><span class="sxs-lookup"><span data-stu-id="883a6-105">C# 9 adds records, which are a kind of class.</span></span> <span data-ttu-id="883a6-106">クラスと構造体は、どちらも基本的にはデータと動作のセットを 1 つの論理単位としてカプセル化するデータ構造です。</span><span class="sxs-lookup"><span data-stu-id="883a6-106">Each is essentially a data structure that encapsulates a set of data and behaviors that belong together as a logical unit.</span></span> <span data-ttu-id="883a6-107">データとビヘイビアーはクラス、構造体、またはレコードの "*メンバー*" です。この記事で後述するように、そのメソッド、プロパティ、イベントなどが含まれます。</span><span class="sxs-lookup"><span data-stu-id="883a6-107">The data and behaviors are the *members* of the class, struct, or record, and they include its methods, properties, events, and so on, as listed later in this article.</span></span>

<span data-ttu-id="883a6-108">クラス、構造体、またはレコードの宣言は、実行時にインスタンスやオブジェクトを作成するために使用する設計図のようなものです。</span><span class="sxs-lookup"><span data-stu-id="883a6-108">A class, struct, or record declaration is like a blueprint that is used to create instances or objects at run time.</span></span> <span data-ttu-id="883a6-109">`Person` という名前のクラス、構造体、またはレコードを定義する場合、`Person` が、型の名前です。</span><span class="sxs-lookup"><span data-stu-id="883a6-109">If you define a class, struct, or record named `Person`, `Person` is the name of the type.</span></span> <span data-ttu-id="883a6-110">型 `p` の変数 `Person` を宣言して初期化すると、`p` は `Person` のオブジェクトまたはインスタンスになります。</span><span class="sxs-lookup"><span data-stu-id="883a6-110">If you declare and initialize a variable `p` of type `Person`, `p` is said to be an object or instance of `Person`.</span></span> <span data-ttu-id="883a6-111">同じ `Person` 型のインスタンスを複数作成し、各インスタンスのプロパティとフィールドに異なる値を設定することができます。</span><span class="sxs-lookup"><span data-stu-id="883a6-111">Multiple instances of the same `Person` type can be created, and each instance can have different values in its properties and fields.</span></span>  
  
<span data-ttu-id="883a6-112">クラスまたはレコードは参照型です。</span><span class="sxs-lookup"><span data-stu-id="883a6-112">A class or a record is a reference type.</span></span> <span data-ttu-id="883a6-113">型のオブジェクトが作成されると、オブジェクトが割り当てられている変数にはそのメモリへの参照だけが設定されます。</span><span class="sxs-lookup"><span data-stu-id="883a6-113">When an object of the type is created, the variable to which the object is assigned holds only a reference to that memory.</span></span> <span data-ttu-id="883a6-114">オブジェクト参照が新しい変数に割り当てられると、新しい変数は元のオブジェクトを参照します。</span><span class="sxs-lookup"><span data-stu-id="883a6-114">When the object reference is assigned to a new variable, the new variable refers to the original object.</span></span> <span data-ttu-id="883a6-115">いずれの変数も同じデータを参照しているため、1 つの変数に加えられた変更は他の変数にも反映されます。</span><span class="sxs-lookup"><span data-stu-id="883a6-115">Changes made through one variable are reflected in the other variable because they both refer to the same data.</span></span>
  
<span data-ttu-id="883a6-116">構造体は値の型です。</span><span class="sxs-lookup"><span data-stu-id="883a6-116">A struct is a value type.</span></span> <span data-ttu-id="883a6-117">構造体が作成されると、構造体が割り当てられている変数にはその構造体の実際のデータが設定されます。</span><span class="sxs-lookup"><span data-stu-id="883a6-117">When a struct is created, the variable to which the struct is assigned holds the struct's actual data.</span></span> <span data-ttu-id="883a6-118">構造体が新しい変数に割り当てられると、そのデータがコピーされます。</span><span class="sxs-lookup"><span data-stu-id="883a6-118">When the struct is assigned to a new variable, it is copied.</span></span> <span data-ttu-id="883a6-119">したがって、新しい変数と元の変数には、同じデータのコピーが別個に含まれることになります。</span><span class="sxs-lookup"><span data-stu-id="883a6-119">The new variable and the original variable therefore contain two separate copies of the same data.</span></span> <span data-ttu-id="883a6-120">一方のコピーに対して行われた変更は、もう一方のコピーには影響しません。</span><span class="sxs-lookup"><span data-stu-id="883a6-120">Changes made to one copy do not affect the other copy.</span></span>  
  
<span data-ttu-id="883a6-121">一般に、クラスは、より複雑な動作、つまりクラス オブジェクトの作成後に変更されることを意図されたデータをモデル化するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="883a6-121">In general, classes are used to model more complex behavior, or data that is intended to be modified after a class object is created.</span></span> <span data-ttu-id="883a6-122">構造体は、主として構造体の作成後に変更されることを意図しないデータを含む、小規模なデータ構造に最適です。</span><span class="sxs-lookup"><span data-stu-id="883a6-122">Structs are best suited for small data structures that contain primarily data that isn't intended to be modified after the struct is created.</span></span> <span data-ttu-id="883a6-123">レコードの種類は、主としてオブジェクトの作成後に変更されることを意図していないデータを含むより大規模なデータ構造を対象としています。</span><span class="sxs-lookup"><span data-stu-id="883a6-123">Record types are for larger data structures that contain primarily data that isn't intended to be modified after the object is created.</span></span>
  
## <a name="example"></a><span data-ttu-id="883a6-124">例</span><span class="sxs-lookup"><span data-stu-id="883a6-124">Example</span></span>

 <span data-ttu-id="883a6-125">次の例では、`ProgrammingGuide` 名前空間の `CustomClass` に 3 つのメンバー (インスタンス コンストラクター、`Number` という名前のプロパティ、`Multiply` という名前のメソッド) があります。</span><span class="sxs-lookup"><span data-stu-id="883a6-125">In the following example, `CustomClass` in the `ProgrammingGuide` namespace has three members: an instance constructor, a property named `Number`, and a method named `Multiply`.</span></span> <span data-ttu-id="883a6-126">`Program` クラスの `Main` メソッドによって `CustomClass` のインスタンス (オブジェクト) が作成され、オブジェクトのメソッドとプロパティにはドット表記を使用してアクセスします。</span><span class="sxs-lookup"><span data-stu-id="883a6-126">The `Main` method in the `Program` class creates an instance (object) of `CustomClass`, and the object's method and property are accessed by using dot notation.</span></span>
  
 :::code language="csharp" source="../../../../samples/snippets/csharp/programming-guide/classes-and-structs/class1.cs" id="Snippet1":::  
  
## <a name="encapsulation"></a><span data-ttu-id="883a6-127">カプセル化</span><span class="sxs-lookup"><span data-stu-id="883a6-127">Encapsulation</span></span>  

 <span data-ttu-id="883a6-128">"*カプセル化*" は、オブジェクト指向プログラミングの原理と言われることもあります。</span><span class="sxs-lookup"><span data-stu-id="883a6-128">*Encapsulation* is sometimes referred to as the first pillar or principle of object-oriented programming.</span></span> <span data-ttu-id="883a6-129">カプセル化の原理に基づくと、クラスまたは構造体は、クラスや構造体の外部のコードに対してメンバーがアクセスする方法を指定できます。</span><span class="sxs-lookup"><span data-stu-id="883a6-129">According to the principle of encapsulation, a class or struct can specify how accessible each of its members is to code outside of the class or struct.</span></span> <span data-ttu-id="883a6-130">クラスやアセンブリの外部からの使用を意図されていないメソッドや変数は非表示にして、コーディング エラーや悪意のある攻略が生じる潜在性を軽減できます。</span><span class="sxs-lookup"><span data-stu-id="883a6-130">Methods and variables that are not intended to be used from outside of the class or assembly can be hidden to limit the potential for coding errors or malicious exploits.</span></span> <span data-ttu-id="883a6-131">詳細については、「[オブジェクト指向プログラミング](../../tutorials/intro-to-csharp/object-oriented-programming.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="883a6-131">For more information, see [Object-oriented programming](../../tutorials/intro-to-csharp/object-oriented-programming.md).</span></span>

## <a name="members"></a><span data-ttu-id="883a6-132">メンバー</span><span class="sxs-lookup"><span data-stu-id="883a6-132">Members</span></span>

<span data-ttu-id="883a6-133">すべてのメソッド、フィールド、定数、プロパティ、およびイベントは型で宣言する必要があります。これらは、型の *メンバー* と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="883a6-133">All methods, fields, constants, properties, and events must be declared within a type; these are called the *members* of the type.</span></span> <span data-ttu-id="883a6-134">C# にはグローバル変数やグローバル メソッドはありません (言語によっては、グローバル変数やグローバル メソッドが存在する場合もあります)。</span><span class="sxs-lookup"><span data-stu-id="883a6-134">In C#, there are no global variables or methods as there are in some other languages.</span></span> <span data-ttu-id="883a6-135">プログラムのエントリ ポイントである `Main` メソッドも、クラスまたは構造体の中で宣言する必要があります ([最上位レベルのステートメント](../main-and-command-args/top-level-statements.md)の場合は暗黙的に)。</span><span class="sxs-lookup"><span data-stu-id="883a6-135">Even a program's entry point, the `Main` method, must be declared within a class or struct (implicitly in the case of [top-level statements](../main-and-command-args/top-level-statements.md)).</span></span>

<span data-ttu-id="883a6-136">クラス、構造体、またはレコードで宣言できるすべてのメンバーの種類を次に示します。</span><span class="sxs-lookup"><span data-stu-id="883a6-136">The following list includes all the various kinds of members that may be declared in a class, struct, or record.</span></span>
  
- [<span data-ttu-id="883a6-137">フィールド</span><span class="sxs-lookup"><span data-stu-id="883a6-137">Fields</span></span>](./fields.md)  
- [<span data-ttu-id="883a6-138">定数</span><span class="sxs-lookup"><span data-stu-id="883a6-138">Constants</span></span>](./constants.md)
- [<span data-ttu-id="883a6-139">プロパティ</span><span class="sxs-lookup"><span data-stu-id="883a6-139">Properties</span></span>](./properties.md)
- [<span data-ttu-id="883a6-140">メソッド</span><span class="sxs-lookup"><span data-stu-id="883a6-140">Methods</span></span>](./methods.md)
- [<span data-ttu-id="883a6-141">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="883a6-141">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="883a6-142">イベント</span><span class="sxs-lookup"><span data-stu-id="883a6-142">Events</span></span>](../events/index.md)
- [<span data-ttu-id="883a6-143">ファイナライザー</span><span class="sxs-lookup"><span data-stu-id="883a6-143">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="883a6-144">インデクサー</span><span class="sxs-lookup"><span data-stu-id="883a6-144">Indexers</span></span>](../indexers/index.md)
- [<span data-ttu-id="883a6-145">演算子</span><span class="sxs-lookup"><span data-stu-id="883a6-145">Operators</span></span>](../../language-reference/operators/index.md)
- [<span data-ttu-id="883a6-146">入れ子にされた型</span><span class="sxs-lookup"><span data-stu-id="883a6-146">Nested Types</span></span>](./nested-types.md)
  
## <a name="accessibility"></a><span data-ttu-id="883a6-147">ユーザー補助</span><span class="sxs-lookup"><span data-stu-id="883a6-147">Accessibility</span></span>  

 <span data-ttu-id="883a6-148">メソッドやプロパティの中には、クラスまたは構造体の外部にあるコード ("*クライアント コード*" と呼ばれます) から呼び出されたりアクセスされたりするように用意されているものがあります。</span><span class="sxs-lookup"><span data-stu-id="883a6-148">Some methods and properties are meant to be called or accessed from code outside a class or struct, known as *client code*.</span></span> <span data-ttu-id="883a6-149">その他のメソッドやプロパティは、クラスまたは構造体それ自体でのみ使用されるようになっています。</span><span class="sxs-lookup"><span data-stu-id="883a6-149">Other methods and properties might be only for use in the class or struct itself.</span></span> <span data-ttu-id="883a6-150">意図したクライアント コードだけがアクセスできるように、コードのアクセシビリティを制限することが重要です。</span><span class="sxs-lookup"><span data-stu-id="883a6-150">It is important to limit the accessibility of your code so that only the intended client code can reach it.</span></span> <span data-ttu-id="883a6-151">型やメンバーがクライアント コードにアクセスする方法を指定するには、次のアクセス修飾子を使用します。</span><span class="sxs-lookup"><span data-stu-id="883a6-151">You specify how accessible your types and their members are to client code by using the following access modifiers:</span></span>

- [<span data-ttu-id="883a6-152">public</span><span class="sxs-lookup"><span data-stu-id="883a6-152">public</span></span>](../../language-reference/keywords/public.md)
- [<span data-ttu-id="883a6-153">protected</span><span class="sxs-lookup"><span data-stu-id="883a6-153">protected</span></span>](../../language-reference/keywords/protected.md)
- [<span data-ttu-id="883a6-154">internal</span><span class="sxs-lookup"><span data-stu-id="883a6-154">internal</span></span>](../../language-reference/keywords/internal.md)
- [<span data-ttu-id="883a6-155">protected internal</span><span class="sxs-lookup"><span data-stu-id="883a6-155">protected internal</span></span>](../../language-reference/keywords/protected-internal.md)
- [<span data-ttu-id="883a6-156">private</span><span class="sxs-lookup"><span data-stu-id="883a6-156">private</span></span>](../../language-reference/keywords/private.md)
- <span data-ttu-id="883a6-157">[private protected](../../language-reference/keywords/private-protected.md).</span><span class="sxs-lookup"><span data-stu-id="883a6-157">[private protected](../../language-reference/keywords/private-protected.md).</span></span>

<span data-ttu-id="883a6-158">既定のアクセシビリティは `private` です。</span><span class="sxs-lookup"><span data-stu-id="883a6-158">The default accessibility is `private`.</span></span> <span data-ttu-id="883a6-159">詳細については、「[アクセス修飾子](./access-modifiers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="883a6-159">For more information, see [Access Modifiers](./access-modifiers.md).</span></span>  
  
## <a name="inheritance"></a><span data-ttu-id="883a6-160">継承</span><span class="sxs-lookup"><span data-stu-id="883a6-160">Inheritance</span></span>  

<span data-ttu-id="883a6-161">クラスでは、継承の概念がサポートされます (構造体ではサポートされません)。</span><span class="sxs-lookup"><span data-stu-id="883a6-161">Classes (but not structs) support the concept of inheritance.</span></span> <span data-ttu-id="883a6-162">他のクラス (*基底クラス*) から派生するクラスには、コンストラクターとファイナライザーを除く基底クラスのすべてのパブリック メンバー、プロテクト メンバー、および内部メンバーが自動的に含まれます。</span><span class="sxs-lookup"><span data-stu-id="883a6-162">A class that derives from another class (the *base class*) automatically contains all the public, protected, and internal members of the base class except its constructors and finalizers.</span></span> <span data-ttu-id="883a6-163">詳細については、「[継承](./inheritance.md)」および「[ポリモーフィズム](./polymorphism.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="883a6-163">For more information, see [Inheritance](./inheritance.md) and [Polymorphism](./polymorphism.md).</span></span>
  
<span data-ttu-id="883a6-164">クラスは、[abstract](../../language-reference/keywords/abstract.md) として宣言することもできます。このようなクラスは、1 つ以上のメソッドの実装を持っていないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="883a6-164">Classes may be declared as [abstract](../../language-reference/keywords/abstract.md), which means that one or more of their methods have no implementation.</span></span> <span data-ttu-id="883a6-165">抽象クラスを直接インスタンス化することはできませんが、他のクラスの基底クラスとして抽象クラスを使用し、不足している実装を提供することができます。</span><span class="sxs-lookup"><span data-stu-id="883a6-165">Although abstract classes cannot be instantiated directly, they can serve as base classes for other classes that provide the missing implementation.</span></span> <span data-ttu-id="883a6-166">また、クラスを [sealed](../../language-reference/keywords/sealed.md) として宣言して、他のクラスがそのクラスを継承しないようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="883a6-166">Classes can also be declared as [sealed](../../language-reference/keywords/sealed.md) to prevent other classes from inheriting from them.</span></span> <span data-ttu-id="883a6-167">詳細については、「[抽象クラスとシール クラス、およびクラス メンバー](./abstract-and-sealed-classes-and-class-members.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="883a6-167">For more information, see [Abstract and sealed classes and class members](./abstract-and-sealed-classes-and-class-members.md).</span></span>
  
## <a name="interfaces"></a><span data-ttu-id="883a6-168">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="883a6-168">Interfaces</span></span>  

<span data-ttu-id="883a6-169">クラス、構造体、およびレコードは、複数のインターフェイスを継承できます。</span><span class="sxs-lookup"><span data-stu-id="883a6-169">Classes, structs, and records can inherit multiple interfaces.</span></span> <span data-ttu-id="883a6-170">インターフェイスの継承は、そのインターフェイスで定義されたすべてのメソッドを型が実装することを意味します。</span><span class="sxs-lookup"><span data-stu-id="883a6-170">To inherit from an interface means that the type implements all the methods defined in the interface.</span></span> <span data-ttu-id="883a6-171">詳細については、「[インターフェイス](../interfaces/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="883a6-171">For more information, see [Interfaces](../interfaces/index.md).</span></span>  
  
## <a name="generic-types"></a><span data-ttu-id="883a6-172">ジェネリック型</span><span class="sxs-lookup"><span data-stu-id="883a6-172">Generic Types</span></span>  

 <span data-ttu-id="883a6-173">クラス、構造体、およびレコードは、1 つ以上の型パラメーターを指定して定義できます。</span><span class="sxs-lookup"><span data-stu-id="883a6-173">Classes, structs, and records can be defined with one or more type parameters.</span></span> <span data-ttu-id="883a6-174">クライアント コードでは、型のインスタンスの作成時に型を指定します。</span><span class="sxs-lookup"><span data-stu-id="883a6-174">Client code supplies the type when it creates an instance of the type.</span></span> <span data-ttu-id="883a6-175">たとえば、<xref:System.Collections.Generic.List%601> 名前空間の <xref:System.Collections.Generic> クラスは、1 つの型パラメーターを指定して定義されています。</span><span class="sxs-lookup"><span data-stu-id="883a6-175">For example The <xref:System.Collections.Generic.List%601> class in the <xref:System.Collections.Generic> namespace is defined with one type parameter.</span></span> <span data-ttu-id="883a6-176">クライアント コードでは、`List<string>` または `List<int>` のインスタンスを作成して、リストに保持する型を指定します。</span><span class="sxs-lookup"><span data-stu-id="883a6-176">Client code creates an instance of a `List<string>` or `List<int>` to specify the type that the list will hold.</span></span> <span data-ttu-id="883a6-177">詳細については、「[ジェネリック](../generics/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="883a6-177">For more information, see [Generics](../generics/index.md).</span></span>  
  
## <a name="static-types"></a><span data-ttu-id="883a6-178">静的な型</span><span class="sxs-lookup"><span data-stu-id="883a6-178">Static Types</span></span>  

<span data-ttu-id="883a6-179">クラス (ただし、構造体やレコードではありません) は、[静的](../../language-reference/keywords/static.md)として宣言できます。</span><span class="sxs-lookup"><span data-stu-id="883a6-179">Classes (but not structs or records) can be declared as [static](../../language-reference/keywords/static.md).</span></span> <span data-ttu-id="883a6-180">静的クラスに含めることができるのは静的メンバーだけであり、`new` キーワードでインスタンス化することはできません。</span><span class="sxs-lookup"><span data-stu-id="883a6-180">A static class can contain only static members and can't be instantiated with the `new` keyword.</span></span> <span data-ttu-id="883a6-181">プログラムが読み込まれると、クラスの 1 つのコピーがメモリに読み込まれます。そのメンバーには、クラス名を使用してアクセスします。</span><span class="sxs-lookup"><span data-stu-id="883a6-181">One copy of the class is loaded into memory when the program loads, and its members are accessed through the class name.</span></span> <span data-ttu-id="883a6-182">クラス、構造体、およびレコードには、静的メンバーを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="883a6-182">Classes, structs, and records can contain static members.</span></span> <span data-ttu-id="883a6-183">詳細については、「[静的クラスと静的クラス メンバー](./static-classes-and-static-class-members.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="883a6-183">For more information, see [Static classes and static class members](./static-classes-and-static-class-members.md).</span></span>
  
## <a name="nested-types"></a><span data-ttu-id="883a6-184">入れ子にされた型</span><span class="sxs-lookup"><span data-stu-id="883a6-184">Nested Types</span></span>

<span data-ttu-id="883a6-185">クラス、構造体、またはレコードは別のクラス、構造体、またはレコードで入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="883a6-185">A class, struct, or record can be nested within another class, struct, or record.</span></span> <span data-ttu-id="883a6-186">詳細については、「[入れ子にされた型](./nested-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="883a6-186">For more information, see [Nested Types](./nested-types.md).</span></span>
  
## <a name="partial-types"></a><span data-ttu-id="883a6-187">部分型</span><span class="sxs-lookup"><span data-stu-id="883a6-187">Partial Types</span></span>  

<span data-ttu-id="883a6-188">あるコード ファイルにクラス、構造体、またはメソッドの一部を定義して、別のコード ファイルに他の部分を定義することができます。</span><span class="sxs-lookup"><span data-stu-id="883a6-188">You can define part of a class, struct or method in one code file and another part in a separate code file.</span></span> <span data-ttu-id="883a6-189">詳細については、「[部分クラスと部分メソッド](./partial-classes-and-methods.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="883a6-189">For more information, see [Partial Classes and methods](./partial-classes-and-methods.md).</span></span>
  
## <a name="object-initializers"></a><span data-ttu-id="883a6-190">オブジェクト初期化子</span><span class="sxs-lookup"><span data-stu-id="883a6-190">Object Initializers</span></span>  

<span data-ttu-id="883a6-191">明示的にコンストラクターを呼び出さずに、クラス オブジェクトまたは構造体オブジェクト、およびオブジェクトのコレクションのインスタンス化と初期化を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="883a6-191">You can instantiate and initialize class or struct objects, and collections of objects, without explicitly calling their constructor.</span></span> <span data-ttu-id="883a6-192">詳細については、「[オブジェクト初期化子とコレクション初期化子](./object-and-collection-initializers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="883a6-192">For more information, see [Object and collection initializers](./object-and-collection-initializers.md).</span></span>  
  
## <a name="anonymous-types"></a><span data-ttu-id="883a6-193">匿名型</span><span class="sxs-lookup"><span data-stu-id="883a6-193">Anonymous Types</span></span>  

<span data-ttu-id="883a6-194">永続的に保持したり他のメソッドに渡したりする必要のないデータ構造体のリストを作成する場合など、名前付きクラスを作成することが適さない状況または不要な状況では、匿名型を使用します。</span><span class="sxs-lookup"><span data-stu-id="883a6-194">In situations where it is not convenient or necessary to create a named class, for example when you are populating a list with data structures that you do not have to persist or pass to another method, you use anonymous types.</span></span> <span data-ttu-id="883a6-195">詳細については、「[匿名型](./anonymous-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="883a6-195">For more information, see [Anonymous types](./anonymous-types.md).</span></span>
  
## <a name="extension-methods"></a><span data-ttu-id="883a6-196">拡張メソッド</span><span class="sxs-lookup"><span data-stu-id="883a6-196">Extension Methods</span></span>  

<span data-ttu-id="883a6-197">別の型を作成し、元の型に属しているかのようにそのメソッドを呼び出せるようにすることで、派生クラスを作成せずにクラスを "拡張" できます。</span><span class="sxs-lookup"><span data-stu-id="883a6-197">You can "extend" a class without creating a derived class by creating a separate type whose methods can be called as if they belonged to the original type.</span></span> <span data-ttu-id="883a6-198">詳細については、「[拡張メソッド](./extension-methods.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="883a6-198">For more information, see [Extension methods](./extension-methods.md).</span></span>
  
## <a name="implicitly-typed-local-variables"></a><span data-ttu-id="883a6-199">暗黙的に型指定されるローカル変数</span><span class="sxs-lookup"><span data-stu-id="883a6-199">Implicitly Typed Local Variables</span></span>  

<span data-ttu-id="883a6-200">クラスや構造体のメソッド内では、暗黙の型指定を使用して、コンパイル時に変数の型を判断するようにコンパイラに指示できます。</span><span class="sxs-lookup"><span data-stu-id="883a6-200">Within a class or struct method, you can use implicit typing to instruct the compiler to determine a variable's type at compile time.</span></span> <span data-ttu-id="883a6-201">詳細については、「[暗黙的に型指定されるローカル変数](./implicitly-typed-local-variables.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="883a6-201">For more information, see [Implicitly Typed Local Variables](./implicitly-typed-local-variables.md).</span></span>

## <a name="records"></a><span data-ttu-id="883a6-202">レコード</span><span class="sxs-lookup"><span data-stu-id="883a6-202">Records</span></span>

<span data-ttu-id="883a6-203">C# 9 では、クラスまたは構造体の代わりに作成できる参照型である `record` 型が導入されています。</span><span class="sxs-lookup"><span data-stu-id="883a6-203">C# 9 introduces the `record` type, a reference type that you can create instead of a class or a struct.</span></span> <span data-ttu-id="883a6-204">レコードは、不変の型でデータをカプセル化するための組み込みのビヘイビアーを持つクラスです。</span><span class="sxs-lookup"><span data-stu-id="883a6-204">Records are classes with built-in behavior for encapsulating data in immutable types.</span></span> <span data-ttu-id="883a6-205">レコードには次の機能があります。</span><span class="sxs-lookup"><span data-stu-id="883a6-205">A record provides the following features:</span></span>

* <span data-ttu-id="883a6-206">不変プロパティを持つ参照型を作成するための簡潔な構文。</span><span class="sxs-lookup"><span data-stu-id="883a6-206">Concise syntax for creating a reference type with immutable properties.</span></span>

* <span data-ttu-id="883a6-207">値の等価性。</span><span class="sxs-lookup"><span data-stu-id="883a6-207">Value equality.</span></span>

  <span data-ttu-id="883a6-208">レコード型の 2 つの変数は、レコード型の定義が同じで、すべてのフィールドについて、両方のレコードの値が等しい場合、等しいと見なされます。</span><span class="sxs-lookup"><span data-stu-id="883a6-208">Two variables of a record type are equal if the record type definitions are identical, and if for every field, the values in both records are equal.</span></span> <span data-ttu-id="883a6-209">これは、参照の等価性を使用するクラスとは異なります。クラス型の 2 つの変数が同じオブジェクトを参照している場合、これらは等しくなります。</span><span class="sxs-lookup"><span data-stu-id="883a6-209">This differs from classes, which use reference equality: two variables of a class type are equal if they refer to the same object.</span></span>

* <span data-ttu-id="883a6-210">非破壊変異の簡潔な構文。</span><span class="sxs-lookup"><span data-stu-id="883a6-210">Concise syntax for nondestructive mutation.</span></span>

  <span data-ttu-id="883a6-211">`with` 式を使用すると、新しいレコード インスタンスを作成できます。これは既存のインスタンスのコピーですが、指定したプロパティ値が変更されています。</span><span class="sxs-lookup"><span data-stu-id="883a6-211">A `with` expression lets you create a new record instance that is a copy of an existing instance but with specified property values changed.</span></span>

* <span data-ttu-id="883a6-212">表示用の組み込みの書式設定。</span><span class="sxs-lookup"><span data-stu-id="883a6-212">Built-in formatting for display.</span></span>

  <span data-ttu-id="883a6-213">`ToString` メソッドを使用すると、レコードの種類名と、パブリック プロパティの名前と値が出力されます。</span><span class="sxs-lookup"><span data-stu-id="883a6-213">The `ToString` method prints out the record type name and the names and values of public properties.</span></span>

* <span data-ttu-id="883a6-214">継承階層のサポート。</span><span class="sxs-lookup"><span data-stu-id="883a6-214">Support for inheritance hierarchies.</span></span>

  <span data-ttu-id="883a6-215">レコードは構造体ではなく、内部のクラスであるため、継承がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="883a6-215">Inheritance is supported because a record is a class under the covers, not a struct.</span></span>

<span data-ttu-id="883a6-216">詳細は、[レコード](../../language-reference/builtin-types/record.md)に関するページ参照してください。</span><span class="sxs-lookup"><span data-stu-id="883a6-216">For more information, see [Records](../../language-reference/builtin-types/record.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="883a6-217">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="883a6-217">C# Language Specification</span></span>  

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="883a6-218">関連項目</span><span class="sxs-lookup"><span data-stu-id="883a6-218">See also</span></span>

- [<span data-ttu-id="883a6-219">クラス</span><span class="sxs-lookup"><span data-stu-id="883a6-219">Classes</span></span>](./classes.md)
- [<span data-ttu-id="883a6-220">オブジェクト</span><span class="sxs-lookup"><span data-stu-id="883a6-220">Objects</span></span>](./objects.md)
- [<span data-ttu-id="883a6-221">構造体型</span><span class="sxs-lookup"><span data-stu-id="883a6-221">Structure types</span></span>](../../language-reference/builtin-types/struct.md)
- [<span data-ttu-id="883a6-222">レコード</span><span class="sxs-lookup"><span data-stu-id="883a6-222">Records</span></span>](../../language-reference/builtin-types/record.md)  
- [<span data-ttu-id="883a6-223">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="883a6-223">C# Programming Guide</span></span>](../index.md)
