---
title: コンストラクターの使用 - C# プログラミング ガイド
description: この例では、C# で new 演算子を使用してクラスをインスタンス化する方法を示します。 新しいオブジェクトに対してメモリが割り当てられると、単純なコンストラクターが呼び出されます。
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], about constructors
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
ms.openlocfilehash: 161c243f16f6705fa8fcf79360f92a74e4d0b27b
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899257"
---
# <a name="using-constructors-c-programming-guide"></a><span data-ttu-id="f5a0b-104">コンストラクターの使用 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="f5a0b-104">Using Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="f5a0b-105">[クラス](../../language-reference/keywords/class.md)または[構造体](../../language-reference/builtin-types/struct.md)を作成する際には、コンストラクターが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="f5a0b-105">When a [class](../../language-reference/keywords/class.md) or [struct](../../language-reference/builtin-types/struct.md) is created, its constructor is called.</span></span> <span data-ttu-id="f5a0b-106">コンストラクターの名前はクラスまたは構造体と同じで、通常は、このコンストラクターによって、新しいオブジェクトのデータ メンバーが初期化されます。</span><span class="sxs-lookup"><span data-stu-id="f5a0b-106">Constructors have the same name as the class or struct, and they usually initialize the data members of the new object.</span></span>  
  
 <span data-ttu-id="f5a0b-107">次の例では、`Taxi` というクラスが、簡単なコンストラクターを使用して定義された後、</span><span class="sxs-lookup"><span data-stu-id="f5a0b-107">In the following example, a class named `Taxi` is defined by using a simple constructor.</span></span> <span data-ttu-id="f5a0b-108">[new](../../language-reference/operators/new-operator.md) 演算子によってインスタンス化されます。</span><span class="sxs-lookup"><span data-stu-id="f5a0b-108">This class is then instantiated with the [new](../../language-reference/operators/new-operator.md) operator.</span></span> <span data-ttu-id="f5a0b-109">`Taxi` コンストラクターは、新しいオブジェクトに対してメモリが割り当てられるとすぐに、`new` 演算子によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="f5a0b-109">The `Taxi` constructor is invoked by the `new` operator immediately after memory is allocated for the new object.</span></span>  
  
 [!code-csharp[TaxiExample#1](snippets/using-constructors/Program.cs#1)]
  
 <span data-ttu-id="f5a0b-110">パラメーターを取らないコンストラクターを "*パラメーターなしのコンストラクター*" と呼びます。</span><span class="sxs-lookup"><span data-stu-id="f5a0b-110">A constructor that takes no parameters is called a *parameterless constructor*.</span></span> <span data-ttu-id="f5a0b-111">`new` 演算子を使ってオブジェクトをインスタンス化する際に `new` に引数を渡さなかった場合、常にパラメーターなしのコンストラクターが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="f5a0b-111">Parameterless constructors are invoked whenever an object is instantiated by using the `new` operator and no arguments are provided to `new`.</span></span> <span data-ttu-id="f5a0b-112">詳細については、「[インスタンス コンストラクター](./instance-constructors.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5a0b-112">For more information, see [Instance Constructors](./instance-constructors.md).</span></span>  
  
 <span data-ttu-id="f5a0b-113">クラスが[静的](../../language-reference/keywords/static.md)である場合を除き、コンストラクターが存在しないクラスには、クラスをインスタンス化できるように、パブリックなパラメーターなしのコンストラクターが C# コンパイラによって割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="f5a0b-113">Unless the class is [static](../../language-reference/keywords/static.md), classes without constructors are given a public parameterless constructor by the C# compiler in order to enable class instantiation.</span></span> <span data-ttu-id="f5a0b-114">詳細については、「[静的クラスと静的クラス メンバー](./static-classes-and-static-class-members.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5a0b-114">For more information, see [Static Classes and Static Class Members](./static-classes-and-static-class-members.md).</span></span>  
  
 <span data-ttu-id="f5a0b-115">次のようにコンストラクターをプライベートにすれば、クラスがインスタンス化されないようにできます。</span><span class="sxs-lookup"><span data-stu-id="f5a0b-115">You can prevent a class from being instantiated by making the constructor private, as follows:</span></span>  
  
 [!code-csharp[PrivateConstructor#2](snippets/using-constructors/Program.cs#2)]
  
 <span data-ttu-id="f5a0b-116">詳細については、「[プライベート コンストラクター](./private-constructors.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5a0b-116">For more information, see [Private Constructors](./private-constructors.md).</span></span>  
  
 <span data-ttu-id="f5a0b-117">[struct](../../language-reference/builtin-types/struct.md) 型のコンストラクターはクラス コンストラクターに似ていますが、`structs` には、明示的なパラメーターなしのコンストラクターを含めることができません。パラメーターなしのコンストラクターは、コンパイラによって自動的に提供されるためです。</span><span class="sxs-lookup"><span data-stu-id="f5a0b-117">Constructors for [struct](../../language-reference/builtin-types/struct.md) types resemble class constructors, but `structs` cannot contain an explicit parameterless constructor because one is provided automatically by the compiler.</span></span> <span data-ttu-id="f5a0b-118">このコンストラクターは、`struct` 内の各フィールドを[既定値](../../language-reference/builtin-types/default-values.md)に初期化します。</span><span class="sxs-lookup"><span data-stu-id="f5a0b-118">This constructor initializes each field in the `struct` to the [default value](../../language-reference/builtin-types/default-values.md).</span></span> <span data-ttu-id="f5a0b-119">ただし、このパラメーターなしのコンストラクターは、`struct` が `new` によってインスタンス化される場合にのみ呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="f5a0b-119">However, this parameterless constructor is only invoked if the `struct` is instantiated with `new`.</span></span> <span data-ttu-id="f5a0b-120">たとえば、次のコードでは、<xref:System.Int32> のパラメーターなしのコンストラクターが使用されるため、整数が確実に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="f5a0b-120">For example, this code uses the parameterless constructor for <xref:System.Int32>, so that you are assured that the integer is initialized:</span></span>  
  
```csharp  
int i = new int();  
Console.WriteLine(i);  
```  
  
 <span data-ttu-id="f5a0b-121">ただし、次のコードでは `new` が使用されておらず、コードは初期化されていないオブジェクトの使用を試みるため、コンパイラ エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="f5a0b-121">The following code, however, causes a compiler error because it does not use `new`, and because it tries to use an object that has not been initialized:</span></span>  
  
```csharp  
int i;  
Console.WriteLine(i);  
```  
  
 <span data-ttu-id="f5a0b-122">これに対して、`structs` をベースにしたオブジェクト (組み込みのすべての数値型など) は、次の例のように、初期化または代入してから使用できます。</span><span class="sxs-lookup"><span data-stu-id="f5a0b-122">Alternatively, objects based on `structs` (including all built-in numeric types) can be initialized or assigned and then used as in the following example:</span></span>  
  
```csharp  
int a = 44;  // Initialize the value type...  
int b;  
b = 33;      // Or assign it before using it.  
Console.WriteLine("{0}, {1}", a, b);  
```  
  
 <span data-ttu-id="f5a0b-123">このため、値型のパラメーターなしのコンストラクターを呼び出す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="f5a0b-123">So calling the parameterless constructor for a value type is not required.</span></span>  
  
 <span data-ttu-id="f5a0b-124">クラスと `structs` のどちらも、パラメーターを受け取るコンストラクターを定義できます。</span><span class="sxs-lookup"><span data-stu-id="f5a0b-124">Both classes and `structs` can define constructors that take parameters.</span></span> <span data-ttu-id="f5a0b-125">パラメーターを受け取るコンストラクターは、`new` ステートメントまたは [base](../../language-reference/keywords/base.md) ステートメントを使用して呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="f5a0b-125">Constructors that take parameters must be called through a `new` statement or a [base](../../language-reference/keywords/base.md) statement.</span></span> <span data-ttu-id="f5a0b-126">クラスと `structs` は複数のコンストラクターを定義することもできます。また、どちらも、パラメーターなしのコンストラクターの定義には必要ありません。</span><span class="sxs-lookup"><span data-stu-id="f5a0b-126">Classes and `structs` can also define multiple constructors, and neither is required to define a parameterless constructor.</span></span> <span data-ttu-id="f5a0b-127">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="f5a0b-127">For example:</span></span>  
  
 [!code-csharp[EmployeeExample#3](snippets/using-constructors/Program.cs#3)]
  
 <span data-ttu-id="f5a0b-128">このクラスは、次のいずれかのステートメントを使用して作成できます。</span><span class="sxs-lookup"><span data-stu-id="f5a0b-128">This class can be created by using either of the following statements:</span></span>  
  
 [!code-csharp[InstantiatingEmployeeConstructors#4](snippets/using-constructors/Program.cs#4)]
  
 <span data-ttu-id="f5a0b-129">コンストラクターでは、`base` キーワードを使用して、基底クラスのコンストラクターを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="f5a0b-129">A constructor can use the `base` keyword to call the constructor of a base class.</span></span> <span data-ttu-id="f5a0b-130">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="f5a0b-130">For example:</span></span>  
  
 [!code-csharp[ManagerInheritingEmployee#5](snippets/using-constructors/Program.cs#5)]
  
 <span data-ttu-id="f5a0b-131">この例では、コンストラクターのブロックを実行する前に、基底クラスのコンストラクターを呼び出しています。</span><span class="sxs-lookup"><span data-stu-id="f5a0b-131">In this example, the constructor for the base class is called before the block for the constructor is executed.</span></span> <span data-ttu-id="f5a0b-132">`base` キーワードは、パラメーターの有無に関係なく使用できます。</span><span class="sxs-lookup"><span data-stu-id="f5a0b-132">The `base` keyword can be used with or without parameters.</span></span> <span data-ttu-id="f5a0b-133">コンストラクターのパラメーターは、`base` のパラメーターまたは式の一部として使用できます。</span><span class="sxs-lookup"><span data-stu-id="f5a0b-133">Any parameters to the constructor can be used as parameters to `base`, or as part of an expression.</span></span> <span data-ttu-id="f5a0b-134">詳細については、「[base](../../language-reference/keywords/base.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5a0b-134">For more information, see [base](../../language-reference/keywords/base.md).</span></span>  
  
 <span data-ttu-id="f5a0b-135">派生クラスで基底クラスのコンストラクターが `base` キーワードを使用して明示的に呼び出されていない場合、パラメーターなしのコンストラクター (存在する場合) は暗黙的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="f5a0b-135">In a derived class, if a base-class constructor is not called explicitly by using the `base` keyword, the parameterless constructor, if there is one, is called implicitly.</span></span> <span data-ttu-id="f5a0b-136">つまり、次に示すコンストラクターの宣言は実質的に同じです。</span><span class="sxs-lookup"><span data-stu-id="f5a0b-136">This means that the following constructor declarations are effectively the same:</span></span>  
  
 [!code-csharp[ManagerImplicitlyCallingParameterlessBaseConstructor#6](snippets/using-constructors/Program.cs#6)]
  
 [!code-csharp[ManagerExplicitlyCallingParameterlessBaseConstructor#7](snippets/using-constructors/Program.cs#7)]
  
 <span data-ttu-id="f5a0b-137">基底クラスがパラメーターなしのコンストラクターを提供しない場合、派生クラスでは、`base` を使って基本コンストラクターを明示的に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="f5a0b-137">If a base class does not offer a parameterless constructor, the derived class must make an explicit call to a base constructor by using `base`.</span></span>  
  
 <span data-ttu-id="f5a0b-138">コンストラクターで [this](../../language-reference/keywords/this.md) キーワードを使用すると、同じオブジェクトで別のコンストラクターを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="f5a0b-138">A constructor can invoke another constructor in the same object by using the [this](../../language-reference/keywords/this.md) keyword.</span></span> <span data-ttu-id="f5a0b-139">`base` と同様、`this` もパラメーターの有無に関係なく使用でき、コンストラクターのパラメーターはいずれも `this` のパラメーターとしても、式の一部としても使用できます。</span><span class="sxs-lookup"><span data-stu-id="f5a0b-139">Like `base`, `this` can be used with or without parameters, and any parameters in the constructor are available as parameters to `this`, or as part of an expression.</span></span> <span data-ttu-id="f5a0b-140">たとえば、上の例の 2 番目のコンストラクターは `this` を使用して次のように書き直すことができます。</span><span class="sxs-lookup"><span data-stu-id="f5a0b-140">For example, the second constructor in the previous example can be rewritten using `this`:</span></span>  
  
 [!code-csharp[EmployeeCallingConstructorInSameClass#8](snippets/using-constructors/Program.cs#8)]
  
 <span data-ttu-id="f5a0b-141">上の例で `this` キーワードを使用すると、このコンストラクターが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="f5a0b-141">The use of the `this` keyword in the previous example causes this constructor to be called:</span></span>  
  
 [!code-csharp[ConstructorBeingCalledByThisKeyword#9](snippets/using-constructors/Program.cs#9)]
  
 <span data-ttu-id="f5a0b-142">コンストラクターは、[public](../../language-reference/keywords/public.md)、[private](../../language-reference/keywords/private.md)、[protected](../../language-reference/keywords/protected.md)、[internal](../../language-reference/keywords/internal.md)、[protected internal](../../language-reference/keywords/protected-internal.md) または [private protected](../../language-reference/keywords/private-protected.md) としてマークできます。</span><span class="sxs-lookup"><span data-stu-id="f5a0b-142">Constructors can be marked as [public](../../language-reference/keywords/public.md), [private](../../language-reference/keywords/private.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md) or [private protected](../../language-reference/keywords/private-protected.md).</span></span> <span data-ttu-id="f5a0b-143">こうしたアクセス修飾子により、クラスのユーザーによるクラスの作成方法が定義されます。</span><span class="sxs-lookup"><span data-stu-id="f5a0b-143">These access modifiers define how users of the class can construct the class.</span></span> <span data-ttu-id="f5a0b-144">詳細については、「[アクセス修飾子](./access-modifiers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5a0b-144">For more information, see [Access Modifiers](./access-modifiers.md).</span></span>  
  
 <span data-ttu-id="f5a0b-145">コンストラクターは、[static](../../language-reference/keywords/static.md) キーワードを使用して静的として宣言できます。</span><span class="sxs-lookup"><span data-stu-id="f5a0b-145">A constructor can be declared static by using the [static](../../language-reference/keywords/static.md) keyword.</span></span> <span data-ttu-id="f5a0b-146">静的コンストラクターは、静的フィールドがアクセスされる直前に自動的に呼び出され、通常は静的なクラス メンバーを初期化するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="f5a0b-146">Static constructors are called automatically, immediately before any static fields are accessed, and are generally used to initialize static class members.</span></span> <span data-ttu-id="f5a0b-147">詳細については、「[静的コンストラクター](./static-constructors.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5a0b-147">For more information, see [Static Constructors](./static-constructors.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="f5a0b-148">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="f5a0b-148">C# Language Specification</span></span>  

<span data-ttu-id="f5a0b-149">詳細については、「[C# 言語仕様](/dotnet/csharp/language-reference/language-specification/introduction)」の[インスタンス コンストラクター](~/_csharplang/spec/classes.md#instance-constructors)と[静的コンストラクター](~/_csharplang/spec/classes.md#static-constructors)に関するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5a0b-149">For more information, see [Instance constructors](~/_csharplang/spec/classes.md#instance-constructors) and [Static constructors](~/_csharplang/spec/classes.md#static-constructors) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="f5a0b-150">言語仕様は、C# の構文と使用法に関する信頼性のある情報源です。</span><span class="sxs-lookup"><span data-stu-id="f5a0b-150">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f5a0b-151">関連項目</span><span class="sxs-lookup"><span data-stu-id="f5a0b-151">See also</span></span>

- [<span data-ttu-id="f5a0b-152">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="f5a0b-152">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f5a0b-153">クラスと構造体</span><span class="sxs-lookup"><span data-stu-id="f5a0b-153">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="f5a0b-154">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="f5a0b-154">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="f5a0b-155">ファイナライザー</span><span class="sxs-lookup"><span data-stu-id="f5a0b-155">Finalizers</span></span>](./destructors.md)
