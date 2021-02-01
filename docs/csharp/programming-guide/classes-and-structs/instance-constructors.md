---
title: インスタンス コンストラクター - C# プログラミング ガイド
description: C# のインスタンス コンストラクターは、new 式を使ってクラスのオブジェクトを作成するときに、インスタンス メンバー変数を作成および初期化します。
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], instance constructors
- instance constructors [C#]
ms.assetid: 24663779-c1e5-4af4-a942-ca554e4c542d
ms.openlocfilehash: 0f9372c744a7bdfab44c8cd020a4378cff729c57
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899036"
---
# <a name="instance-constructors-c-programming-guide"></a><span data-ttu-id="51d74-103">インスタンス コンストラクター (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="51d74-103">Instance Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="51d74-104">インスタンス コンストラクターは、[new](../../language-reference/operators/new-operator.md) 式を使って[クラス](../../language-reference/keywords/class.md)のオブジェクトを作成するときに、インスタンス メンバー変数を作成および初期化するために使われます。</span><span class="sxs-lookup"><span data-stu-id="51d74-104">Instance constructors are used to create and initialize any instance member variables when you use the [new](../../language-reference/operators/new-operator.md) expression to create an object of a [class](../../language-reference/keywords/class.md).</span></span> <span data-ttu-id="51d74-105">[静的](../../language-reference/keywords/static.md)クラスを初期化する場合、または非静的クラスの静的変数を初期化する場合は、静的コンストラクターを定義します。</span><span class="sxs-lookup"><span data-stu-id="51d74-105">To initialize a [static](../../language-reference/keywords/static.md) class, or static variables in a non-static class, you define a static constructor.</span></span> <span data-ttu-id="51d74-106">詳細については、「[静的コンストラクター](./static-constructors.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="51d74-106">For more information, see [Static Constructors](./static-constructors.md).</span></span>  
  
 <span data-ttu-id="51d74-107">次に示すのは、インスタンス コンストラクターの例です。</span><span class="sxs-lookup"><span data-stu-id="51d74-107">The following example shows an instance constructor:</span></span>  
  
 [!code-csharp[CoordsWithParameterlessConstructorOnly#1](snippets/instance-constructors/coords/Program.cs#1)]
  
> [!NOTE]
> <span data-ttu-id="51d74-108">わかりやすくするため、このクラスにはパブリック フィールドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="51d74-108">For clarity, this class contains public fields.</span></span> <span data-ttu-id="51d74-109">パブリック フィールドを使うと、プログラム内の任意の場所にある任意のメソッドが、制限も検証もなしにオブジェクトの内部動作にアクセスできるため、パブリック フィールドは推奨されるプログラミング手法ではありません。</span><span class="sxs-lookup"><span data-stu-id="51d74-109">The use of public fields is not a recommended programming practice because it allows any method anywhere in a program unrestricted and unverified access to an object's inner workings.</span></span> <span data-ttu-id="51d74-110">データ メンバーは、一般にプライベートにする必要があり、クラスのメソッドとプロパティを介してのみアクセスする必要があります。</span><span class="sxs-lookup"><span data-stu-id="51d74-110">Data members should generally be private, and should be accessed only through class methods and properties.</span></span>  
  
 <span data-ttu-id="51d74-111">このインスタンス コンストラクターは、`Coords` クラスに基づくオブジェクトが作成されるたびに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="51d74-111">This instance constructor is called whenever an object based on the `Coords` class is created.</span></span> <span data-ttu-id="51d74-112">引数を受け取らないこのようなコンストラクターは、*パラメーターなしのコンストラクター* と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="51d74-112">A constructor like this one, which takes no arguments, is called a *parameterless constructor*.</span></span> <span data-ttu-id="51d74-113">ただし、コンストラクターを追加すると便利な場合がよくあります。</span><span class="sxs-lookup"><span data-stu-id="51d74-113">However, it is often useful to provide additional constructors.</span></span> <span data-ttu-id="51d74-114">たとえば、データ メンバーの初期値を指定できるコンストラクターを `Coords` クラスに追加できます。</span><span class="sxs-lookup"><span data-stu-id="51d74-114">For example, we can add a constructor to the `Coords` class that allows us to specify the initial values for the data members:</span></span>  
  
 [!code-csharp[TwoArgumentConstructor#2](snippets/instance-constructors/coords/Program.cs#2)]
  
 <span data-ttu-id="51d74-115">これにより、次のように、既定値または特定の初期値で `Coords` オブジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="51d74-115">This allows `Coords` objects to be created with default or specific initial values, like this:</span></span>  
  
 [!code-csharp[InstantiatingCoords#3](snippets/instance-constructors/coords/Program.cs#3)]
  
 <span data-ttu-id="51d74-116">クラスにコンストラクターがない場合は、パラメーターなしのコンストラクターが自動的に生成され、既定値を使ってオブジェクトのフィールドが初期化されます。</span><span class="sxs-lookup"><span data-stu-id="51d74-116">If a class does not have a constructor, a parameterless constructor is automatically generated and default values are used to initialize the object fields.</span></span> <span data-ttu-id="51d74-117">たとえば、[int](../../language-reference/builtin-types/integral-numeric-types.md) は 0 に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="51d74-117">For example, an [int](../../language-reference/builtin-types/integral-numeric-types.md) is initialized to 0.</span></span> <span data-ttu-id="51d74-118">値の既定値の詳細については、「[C# 型の既定値](../../language-reference/builtin-types/default-values.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="51d74-118">For information about the type default values, see [Default values of C# types](../../language-reference/builtin-types/default-values.md).</span></span> <span data-ttu-id="51d74-119">したがって、`Coords` クラスのパラメーターなしのコンストラクターは、すべてのデータ メンバーをゼロに初期化するため、クラスの動作を変更することなくまとめて削除することができます。</span><span class="sxs-lookup"><span data-stu-id="51d74-119">Therefore, because the `Coords` class parameterless constructor initializes all data members to zero, it can be removed altogether without changing how the class works.</span></span> <span data-ttu-id="51d74-120">複数のコンストラクターを使う完全な例は後の例 1 で、自動的に生成されたコンストラクターの例は例 2 で示します。</span><span class="sxs-lookup"><span data-stu-id="51d74-120">A complete example using multiple constructors is provided in Example 1 later in this topic, and an example of an automatically generated constructor is provided in Example 2.</span></span>  
  
 <span data-ttu-id="51d74-121">インスタンス コンストラクターを使って、基底クラスのインスタンス コンストラクターを呼び出すこともできます。</span><span class="sxs-lookup"><span data-stu-id="51d74-121">Instance constructors can also be used to call the instance constructors of base classes.</span></span> <span data-ttu-id="51d74-122">次のように、クラスのコンストラクターは、初期化子を使って基底クラスのコンストラクターを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="51d74-122">The class constructor can invoke the constructor of the base class through the initializer, as follows:</span></span>  
  
```csharp
class Circle : Shape
{
    public Circle(double radius)
        : base(radius, 0)
    {
    }
}
```
  
 <span data-ttu-id="51d74-123">この例では、`Circle` クラスは、半径と高さを表す値を、`Circle` の派生元である `Shape` によって提供されるコンストラクターに渡しています。</span><span class="sxs-lookup"><span data-stu-id="51d74-123">In this example, the `Circle` class passes values representing radius and height to the constructor provided by `Shape` from which `Circle` is derived.</span></span> <span data-ttu-id="51d74-124">`Shape` と `Circle` を使う完全な例は、例 3 をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="51d74-124">A complete example using `Shape` and `Circle` appears in this topic as Example 3.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="51d74-125">例 1</span><span class="sxs-lookup"><span data-stu-id="51d74-125">Example 1</span></span>  

 <span data-ttu-id="51d74-126">次の例で示すクラスには、引数を持たないクラス コンストラクターと、2 つの引数を持つクラス コンストラクターがあります。</span><span class="sxs-lookup"><span data-stu-id="51d74-126">The following example demonstrates a class with two class constructors, one without arguments and one with two arguments.</span></span>  
  
 [!code-csharp[CoordsFullExample#4](snippets/instance-constructors/coords/Program.cs#4)]
  
## <a name="example-2"></a><span data-ttu-id="51d74-127">例 2</span><span class="sxs-lookup"><span data-stu-id="51d74-127">Example 2</span></span>  

 <span data-ttu-id="51d74-128">この例の `Person` クラスにはコンストラクターがありません。このような場合は、パラメーターなしのコンストラクターが自動的に提供され、フィールドは既定値に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="51d74-128">In this example, the class `Person` does not have any constructors, in which case, a parameterless constructor is automatically provided and the fields are initialized to their default values.</span></span>  
  
 [!code-csharp[Person](snippets/instance-constructors/person/Program.cs)]
  
 <span data-ttu-id="51d74-129">`age` の既定値は `0`、`name` の既定値は `null` であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="51d74-129">Notice that the default value of `age` is `0` and the default value of `name` is `null`.</span></span>
  
## <a name="example-3"></a><span data-ttu-id="51d74-130">例 3</span><span class="sxs-lookup"><span data-stu-id="51d74-130">Example 3</span></span>  

 <span data-ttu-id="51d74-131">次の例では、基底クラスの初期化子の使い方を示します。</span><span class="sxs-lookup"><span data-stu-id="51d74-131">The following example demonstrates using the base class initializer.</span></span> <span data-ttu-id="51d74-132">`Circle` クラスは汎用クラス `Shape` から派生し、`Cylinder` クラスは `Circle` クラスから派生しています。</span><span class="sxs-lookup"><span data-stu-id="51d74-132">The `Circle` class is derived from the general class `Shape`, and the `Cylinder` class is derived from the `Circle` class.</span></span> <span data-ttu-id="51d74-133">各派生クラスのコンストラクターでは、その基底クラスの初期化子が使われています。</span><span class="sxs-lookup"><span data-stu-id="51d74-133">The constructor on each derived class is using its base class initializer.</span></span>  
  
 [!code-csharp[ShapesExample](snippets/instance-constructors/shapes/Program.cs)]
  
 <span data-ttu-id="51d74-134">基底クラスのコンストラクターの呼び出しに関する他の例については、「[virtual](../../language-reference/keywords/virtual.md)」、「[override](../../language-reference/keywords/override.md)」、「[base](../../language-reference/keywords/base.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="51d74-134">For more examples on invoking the base class constructors, see [virtual](../../language-reference/keywords/virtual.md), [override](../../language-reference/keywords/override.md), and [base](../../language-reference/keywords/base.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51d74-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="51d74-135">See also</span></span>

- [<span data-ttu-id="51d74-136">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="51d74-136">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="51d74-137">クラスと構造体</span><span class="sxs-lookup"><span data-stu-id="51d74-137">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="51d74-138">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="51d74-138">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="51d74-139">ファイナライザー</span><span class="sxs-lookup"><span data-stu-id="51d74-139">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="51d74-140">static</span><span class="sxs-lookup"><span data-stu-id="51d74-140">static</span></span>](../../language-reference/keywords/static.md)
