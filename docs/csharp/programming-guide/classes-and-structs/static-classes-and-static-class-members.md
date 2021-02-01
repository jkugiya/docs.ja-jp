---
title: 静的クラスと静的クラス メンバー - C# プログラミング ガイド
description: 静的クラスは、C# ではインスタンス化できません。 静的クラスのメンバーにアクセスするには、クラス名自体を使用します。
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, static members
- static members [C#]
- static classes [C#]
- C# language, static classes
- static class members [C#]
ms.assetid: 235614b5-1371-4dbd-9abd-b406a8b0298b
ms.openlocfilehash: 31de2a7d58d610213bfa4fc0377e1ab7283e111e
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899010"
---
# <a name="static-classes-and-static-class-members-c-programming-guide"></a><span data-ttu-id="04d26-104">静的クラスと静的クラス メンバー (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="04d26-104">Static Classes and Static Class Members (C# Programming Guide)</span></span>

<span data-ttu-id="04d26-105">[静的](../../language-reference/keywords/static.md)クラスは基本的には非静的クラスと同じですが、静的クラスはインスタンス化できないという点が異なります。</span><span class="sxs-lookup"><span data-stu-id="04d26-105">A [static](../../language-reference/keywords/static.md) class is basically the same as a non-static class, but there is one difference: a static class cannot be instantiated.</span></span> <span data-ttu-id="04d26-106">つまり、[new](../../language-reference/operators/new-operator.md) 演算子を使用して、そのクラス型の変数を作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="04d26-106">In other words, you cannot use the [new](../../language-reference/operators/new-operator.md) operator to create a variable of the class type.</span></span> <span data-ttu-id="04d26-107">インスタンス変数がないため、静的クラスのメンバーにアクセスするには、クラス名自体を使用します。</span><span class="sxs-lookup"><span data-stu-id="04d26-107">Because there is no instance variable, you access the members of a static class by using the class name itself.</span></span> <span data-ttu-id="04d26-108">たとえば、`UtilityClass` という静的クラスがあり、`MethodA` というパブリック静的メソッドが定義されている場合、このメソッドを呼び出すには次の例のようにします。</span><span class="sxs-lookup"><span data-stu-id="04d26-108">For example, if you have a static class that is named `UtilityClass` that has a public static method named `MethodA`, you call the method as shown in the following example:</span></span>  
  
```csharp  
UtilityClass.MethodA();  
```  
  
 <span data-ttu-id="04d26-109">静的クラスは、入力パラメーターに対してのみ処理を行い、内部のインスタンス フィールドを取得したり設定したりする必要のない一連のメソッドを格納する、便利なコンテナーとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="04d26-109">A static class can be used as a convenient container for sets of methods that just operate on input parameters and do not have to get or set any internal instance fields.</span></span> <span data-ttu-id="04d26-110">たとえば、.NET クラス ライブラリでは、静的クラス <xref:System.Math?displayProperty=nameWithType> に、数値演算を実行するメソッドが含まれており、<xref:System.Math> クラスの特定のインスタンスに固有のデータを格納または取得する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="04d26-110">For example, in the .NET Class Library, the static <xref:System.Math?displayProperty=nameWithType> class contains methods that perform mathematical operations, without any requirement to store or retrieve data that is unique to a particular instance of the <xref:System.Math> class.</span></span> <span data-ttu-id="04d26-111">つまり、次の例に示すように、クラス名とメソッド名を指定して、クラスのメンバーを適用します。</span><span class="sxs-lookup"><span data-stu-id="04d26-111">That is, you apply the members of the class by specifying the class name and the method name, as shown in the following example.</span></span>  
  
```csharp  
double dub = -3.14;  
Console.WriteLine(Math.Abs(dub));  
Console.WriteLine(Math.Floor(dub));  
Console.WriteLine(Math.Round(Math.Abs(dub)));  
  
// Output:  
// 3.14  
// -4  
// 3  
```  
  
 <span data-ttu-id="04d26-112">すべてのクラス型の場合と同様に、静的クラスの型情報は、.NET ランタイムによって、そのクラスを参照しているプログラムが読み込まれるときに読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="04d26-112">As is the case with all class types, the type information for a static class is loaded by the .NET runtime when the program that references the class is loaded.</span></span> <span data-ttu-id="04d26-113">プログラムでは、クラスが読み込まれるタイミングを正確に指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="04d26-113">The program cannot specify exactly when the class is loaded.</span></span> <span data-ttu-id="04d26-114">ただし、クラスがプログラム内で最初に参照される前に、そのクラスが読み込まれ、そのフィールドが初期化され、その静的コンストラクターが呼び出されることが保証されます。</span><span class="sxs-lookup"><span data-stu-id="04d26-114">However, it is guaranteed to be loaded and to have its fields initialized and its static constructor called before the class is referenced for the first time in your program.</span></span> <span data-ttu-id="04d26-115">静的コンストラクターは一度だけ呼び出され、静的クラスは、プログラムが存在するアプリケーション ドメインの有効期間にわたってメモリに保持されます。</span><span class="sxs-lookup"><span data-stu-id="04d26-115">A static constructor is only called one time, and a static class remains in memory for the lifetime of the application domain in which your program resides.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="04d26-116">インスタンスの作成を 1 つしか許可しない非静的クラスを作成する場合は、「[C# でのシングルトンの実装](/previous-versions/msp-n-p/ff650316(v=pandp.10))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04d26-116">To create a non-static class that allows only one instance of itself to be created, see [Implementing Singleton in C#](/previous-versions/msp-n-p/ff650316(v=pandp.10)).</span></span>  
  
 <span data-ttu-id="04d26-117">静的クラスの主な特徴を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="04d26-117">The following list provides the main features of a static class:</span></span>  
  
- <span data-ttu-id="04d26-118">静的メンバーだけが含まれます。</span><span class="sxs-lookup"><span data-stu-id="04d26-118">Contains only static members.</span></span>  
  
- <span data-ttu-id="04d26-119">インスタンス化できません。</span><span class="sxs-lookup"><span data-stu-id="04d26-119">Cannot be instantiated.</span></span>  
  
- <span data-ttu-id="04d26-120">シールされています。</span><span class="sxs-lookup"><span data-stu-id="04d26-120">Is sealed.</span></span>  
  
- <span data-ttu-id="04d26-121">[インスタンス コンストラクター](./instance-constructors.md)を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="04d26-121">Cannot contain [Instance Constructors](./instance-constructors.md).</span></span>  
  
 <span data-ttu-id="04d26-122">したがって、静的クラスを作成することと、静的メンバーとプライベート コンストラクターのみを含むクラスを作成することは、基本的に同じです。</span><span class="sxs-lookup"><span data-stu-id="04d26-122">Creating a static class is therefore basically the same as creating a class that contains only static members and a private constructor.</span></span> <span data-ttu-id="04d26-123">プライベート コンストラクターは、クラスのインスタンス化を防ぎます。</span><span class="sxs-lookup"><span data-stu-id="04d26-123">A private constructor prevents the class from being instantiated.</span></span> <span data-ttu-id="04d26-124">静的クラスを使用する利点は、インスタンス メンバーが誤って追加されないことをコンパイラで確認できるという点です。</span><span class="sxs-lookup"><span data-stu-id="04d26-124">The advantage of using a static class is that the compiler can check to make sure that no instance members are accidentally added.</span></span> <span data-ttu-id="04d26-125">コンパイラによって、このクラスのインスタンスを作成できないことが保証されます。</span><span class="sxs-lookup"><span data-stu-id="04d26-125">The compiler will guarantee that instances of this class cannot be created.</span></span>  
  
 <span data-ttu-id="04d26-126">静的クラスはシールされるため、継承できません。</span><span class="sxs-lookup"><span data-stu-id="04d26-126">Static classes are sealed and therefore cannot be inherited.</span></span> <span data-ttu-id="04d26-127"><xref:System.Object> 以外のクラスから継承することはできません。</span><span class="sxs-lookup"><span data-stu-id="04d26-127">They cannot inherit from any class except <xref:System.Object>.</span></span> <span data-ttu-id="04d26-128">静的クラスには、インスタンス コンストラクターを含めることができません。</span><span class="sxs-lookup"><span data-stu-id="04d26-128">Static classes cannot contain an instance constructor.</span></span> <span data-ttu-id="04d26-129">ただし、静的コンストラクターを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="04d26-129">However, they can contain a static constructor.</span></span> <span data-ttu-id="04d26-130">特別な初期化を必要とする静的メンバーがクラスに含まれている場合は、非静的クラスであっても静的コンストラクターを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="04d26-130">Non-static classes should also define a static constructor if the class contains static members that require non-trivial initialization.</span></span> <span data-ttu-id="04d26-131">詳細については、「[静的コンストラクター](./static-constructors.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04d26-131">For more information, see [Static Constructors](./static-constructors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="04d26-132">例</span><span class="sxs-lookup"><span data-stu-id="04d26-132">Example</span></span>  

 <span data-ttu-id="04d26-133">次に、摂氏と華氏の間で温度を変換する 2 つのメソッドを含む静的クラスの例を示します。</span><span class="sxs-lookup"><span data-stu-id="04d26-133">Here is an example of a static class that contains two methods that convert temperature from Celsius to Fahrenheit and from Fahrenheit to Celsius:</span></span>  
  
 [!code-csharp[TemperatureConverter#1](snippets/static-classes-and-static-class-members/Program.cs#1)]  
  
## <a name="static-members"></a><span data-ttu-id="04d26-134">静的メンバー</span><span class="sxs-lookup"><span data-stu-id="04d26-134">Static Members</span></span>  

 <span data-ttu-id="04d26-135">非静的クラスには、静的メソッド、フィールド、プロパティ、またはイベントを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="04d26-135">A non-static class can contain static methods, fields, properties, or events.</span></span> <span data-ttu-id="04d26-136">静的メンバーは、クラスのインスタンスが作成されていない場合でも、クラスで呼び出すことです。</span><span class="sxs-lookup"><span data-stu-id="04d26-136">The static member is callable on a class even when no instance of the class has been created.</span></span> <span data-ttu-id="04d26-137">静的メンバーには、必ずインスタンス名ではなくクラス名でアクセスします。</span><span class="sxs-lookup"><span data-stu-id="04d26-137">The static member is always accessed by the class name, not the instance name.</span></span> <span data-ttu-id="04d26-138">クラスのインスタンスの作成数に関係なく、静的メンバーのコピーは 1 つしか存在しません。</span><span class="sxs-lookup"><span data-stu-id="04d26-138">Only one copy of a static member exists, regardless of how many instances of the class are created.</span></span> <span data-ttu-id="04d26-139">静的メソッドと静的プロパティは、それを含んでいる型の非静的フィールドや非静的イベントにはアクセスできません。また、メソッド パラメーターに明示的に渡されない限り、どのオブジェクトのインスタンス変数にもアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="04d26-139">Static methods and properties cannot access non-static fields and events in their containing type, and they cannot access an instance variable of any object unless it's explicitly passed in a method parameter.</span></span>  
  
 <span data-ttu-id="04d26-140">クラス全体を静的として宣言するよりも、非静的クラスを宣言して、いくつかの静的メンバーを含める方が一般的です。</span><span class="sxs-lookup"><span data-stu-id="04d26-140">It is more typical to declare a non-static class with some static members, than to declare an entire class as static.</span></span> <span data-ttu-id="04d26-141">静的フィールドの一般的な用途として、インスタンス化されたオブジェクトの数を保持することと、すべてのインスタンスで共有する必要のある値を格納することの 2 つがあります。</span><span class="sxs-lookup"><span data-stu-id="04d26-141">Two common uses of static fields are to keep a count of the number of objects that have been instantiated, or to store a value that must be shared among all instances.</span></span>  
  
 <span data-ttu-id="04d26-142">静的メソッドのオーバーロードはできますが、オーバーライドはできません。これは、静的メソッドがクラスのインスタンスではなくクラスに属しているためです。</span><span class="sxs-lookup"><span data-stu-id="04d26-142">Static methods can be overloaded but not overridden, because they belong to the class, and not to any instance of the class.</span></span>  
  
 <span data-ttu-id="04d26-143">フィールドを `static const` として宣言することはできませんが、[const](../../language-reference/keywords/const.md) フィールドは、その動作において本質的に静的です。</span><span class="sxs-lookup"><span data-stu-id="04d26-143">Although a field cannot be declared as `static const`, a [const](../../language-reference/keywords/const.md) field is essentially static in its behavior.</span></span> <span data-ttu-id="04d26-144">これは、型のインスタンスではなく、型に属します。</span><span class="sxs-lookup"><span data-stu-id="04d26-144">It belongs to the type, not to instances of the type.</span></span> <span data-ttu-id="04d26-145">そのため、`const` フィールドにアクセスするには、静的フィールドに対して使用するのと同じ `ClassName.MemberName` 表記法を使用します。</span><span class="sxs-lookup"><span data-stu-id="04d26-145">Therefore, `const` fields can be accessed by using the same `ClassName.MemberName` notation that's used for static fields.</span></span> <span data-ttu-id="04d26-146">オブジェクト インスタンスは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="04d26-146">No object instance is required.</span></span>  
  
 <span data-ttu-id="04d26-147">C# では、静的なローカル変数 (つまり、メソッドのスコープで宣言された変数) はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="04d26-147">C# does not support static local variables (that is, variables that are declared in method scope).</span></span>  
  
 <span data-ttu-id="04d26-148">静的クラスのメンバーを宣言するには、次の例に示すように、メンバーの戻り値の型の前で `static` キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="04d26-148">You declare static class members by using the `static` keyword before the return type of the member, as shown in the following example:</span></span>  
  
 [!code-csharp[AutomobileExample#2](snippets/static-classes-and-static-class-members/Program.cs#2)]  
  
 <span data-ttu-id="04d26-149">静的メンバーは初めてアクセスされる前に初期化されます。また、静的コンストラクターがある場合は、それが呼び出される前に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="04d26-149">Static members are initialized before the static member is accessed for the first time and before the static constructor, if there is one, is called.</span></span> <span data-ttu-id="04d26-150">静的クラスのメンバーにアクセスするには、次の例に示すように、変数名の代わりにクラス名を使用してメンバーの位置を指定します。</span><span class="sxs-lookup"><span data-stu-id="04d26-150">To access a static class member, use the name of the class instead of a variable name to specify the location of the member, as shown in the following example:</span></span>  
  
 [!code-csharp[AccessingStaticMembers#3](snippets/static-classes-and-static-class-members/Program.cs#3)]  
  
 <span data-ttu-id="04d26-151">クラスに静的フィールドが含まれている場合は、クラスが読み込まれたときに静的フィールドを初期化する静的コンストラクターを用意します。</span><span class="sxs-lookup"><span data-stu-id="04d26-151">If your class contains static fields, provide a static constructor that initializes them when the class is loaded.</span></span>  
  
 <span data-ttu-id="04d26-152">静的メソッドの呼び出しでは、Microsoft Intermediate Language (MSIL) の call 命令が生成されます。これに対して、インスタンス メソッドの呼び出しでは `callvirt` 命令が生成され、null オブジェクト参照もチェックされます。</span><span class="sxs-lookup"><span data-stu-id="04d26-152">A call to a static method generates a call instruction in Microsoft intermediate language (MSIL), whereas a call to an instance method generates a `callvirt` instruction, which also checks for null object references.</span></span> <span data-ttu-id="04d26-153">ただし、ほとんどの場合、2 つの間にパフォーマンス上の違いはそれほどありません。</span><span class="sxs-lookup"><span data-stu-id="04d26-153">However, most of the time the performance difference between the two is not significant.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="04d26-154">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="04d26-154">C# Language Specification</span></span>  

<span data-ttu-id="04d26-155">詳細については、「[C# 言語仕様](/dotnet/csharp/language-reference/language-specification/introduction)」の[静的クラス](~/_csharplang/spec/classes.md#static-classes)と[静的およびインスタンス メンバー](~/_csharplang/spec/classes.md#static-and-instance-members)に関するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="04d26-155">For more information, see [Static classes](~/_csharplang/spec/classes.md#static-classes) and [Static and instance members](~/_csharplang/spec/classes.md#static-and-instance-members) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="04d26-156">言語仕様は、C# の構文と使用法に関する信頼性のある情報源です。</span><span class="sxs-lookup"><span data-stu-id="04d26-156">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="04d26-157">関連項目</span><span class="sxs-lookup"><span data-stu-id="04d26-157">See also</span></span>

- [<span data-ttu-id="04d26-158">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="04d26-158">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="04d26-159">static</span><span class="sxs-lookup"><span data-stu-id="04d26-159">static</span></span>](../../language-reference/keywords/static.md)
- [<span data-ttu-id="04d26-160">クラス</span><span class="sxs-lookup"><span data-stu-id="04d26-160">Classes</span></span>](./classes.md)
- [<span data-ttu-id="04d26-161">class</span><span class="sxs-lookup"><span data-stu-id="04d26-161">class</span></span>](../../language-reference/keywords/class.md)
- [<span data-ttu-id="04d26-162">静的コンストラクター</span><span class="sxs-lookup"><span data-stu-id="04d26-162">Static Constructors</span></span>](./static-constructors.md)
- [<span data-ttu-id="04d26-163">インスタンス コンストラクター</span><span class="sxs-lookup"><span data-stu-id="04d26-163">Instance Constructors</span></span>](./instance-constructors.md)
