---
title: クラス
description: プロパティ、メソッド、イベントを持つことができるオブジェクトを表す型である F# クラスについて説明します。
ms.date: 05/16/2016
ms.openlocfilehash: fd6638e0f1c08cf667a73582e19b2bb5bba46e20
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970168"
---
# <a name="classes"></a><span data-ttu-id="ac807-103">クラス</span><span class="sxs-lookup"><span data-stu-id="ac807-103">Classes</span></span>

<span data-ttu-id="ac807-104">"*クラス*" は、オブジェクトを表す型であり、プロパティ、メソッド、イベントを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="ac807-104">*Classes* are types that represent objects that can have properties, methods, and events.</span></span>

## <a name="syntax"></a><span data-ttu-id="ac807-105">構文</span><span class="sxs-lookup"><span data-stu-id="ac807-105">Syntax</span></span>

```fsharp
// Class definition:
type [access-modifier] type-name [type-params] [access-modifier] ( parameter-list ) [ as identifier ] =
[ class ]
[ inherit base-type-name(base-constructor-args) ]
[ let-bindings ]
[ do-bindings ]
member-list
...
[ end ]
// Mutually recursive class definitions:
type [access-modifier] type-name1 ...
and [access-modifier] type-name2 ...
...
```

## <a name="remarks"></a><span data-ttu-id="ac807-106">解説</span><span class="sxs-lookup"><span data-stu-id="ac807-106">Remarks</span></span>

<span data-ttu-id="ac807-107">クラスは、.NET オブジェクト型の基本的な記述を表します。クラスは、F# でのオブジェクト指向プログラミングをサポートする主要な型の概念です。</span><span class="sxs-lookup"><span data-stu-id="ac807-107">Classes represent the fundamental description of .NET object types; the class is the primary type concept that supports object-oriented programming in F#.</span></span>

<span data-ttu-id="ac807-108">上記の構文で、`type-name` は任意の有効な識別子です。</span><span class="sxs-lookup"><span data-stu-id="ac807-108">In the preceding syntax, the `type-name` is any valid identifier.</span></span> <span data-ttu-id="ac807-109">`type-params` では、省略可能なジェネリック型パラメーターを記述します。</span><span class="sxs-lookup"><span data-stu-id="ac807-109">The `type-params` describes optional generic type parameters.</span></span> <span data-ttu-id="ac807-110">これは、型パラメーター名と、山かっこ (`<` と `>`) で囲まれた制約で構成されます。</span><span class="sxs-lookup"><span data-stu-id="ac807-110">It consists of type parameter names and constraints enclosed in angle brackets (`<` and `>`).</span></span> <span data-ttu-id="ac807-111">詳細については、「[ジェネリック](./generics/index.md)」と「[制約](./generics/constraints.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ac807-111">For more information, see [Generics](./generics/index.md) and [Constraints](./generics/constraints.md).</span></span> <span data-ttu-id="ac807-112">`parameter-list` では、コンストラクターのパラメーターを記述します。</span><span class="sxs-lookup"><span data-stu-id="ac807-112">The `parameter-list` describes constructor parameters.</span></span> <span data-ttu-id="ac807-113">最初のアクセス修飾子は、型に関連しています。2 つ目は、プライマリ コンストラクターに関連しています。</span><span class="sxs-lookup"><span data-stu-id="ac807-113">The first access modifier pertains to the type; the second pertains to the primary constructor.</span></span> <span data-ttu-id="ac807-114">どちらの場合も、既定値は `public` です。</span><span class="sxs-lookup"><span data-stu-id="ac807-114">In both cases, the default is `public`.</span></span>

<span data-ttu-id="ac807-115">クラスの基底クラスは、`inherit` キーワードを使用して指定します。</span><span class="sxs-lookup"><span data-stu-id="ac807-115">You specify the base class for a class by using the `inherit` keyword.</span></span> <span data-ttu-id="ac807-116">基底クラスのコンストラクターには、かっこで囲んだ引数を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac807-116">You must supply arguments, in parentheses, for the base class constructor.</span></span>

<span data-ttu-id="ac807-117">`let` バインドを使用して、クラスに対してローカルなフィールドまたは関数値を宣言します。これは、`let` バインドの一般的な規則に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac807-117">You declare fields or function values that are local to the class by using `let` bindings, and you must follow the general rules for `let` bindings.</span></span> <span data-ttu-id="ac807-118">`do-bindings` セクションには、オブジェクトの構築時に実行するコードを含めます。</span><span class="sxs-lookup"><span data-stu-id="ac807-118">The `do-bindings` section includes code to be executed upon object construction.</span></span>

<span data-ttu-id="ac807-119">`member-list` は、追加のコンストラクター、インスタンスと静的メソッドの宣言、インターフェイス宣言、抽象バインド、プロパティとイベントの宣言で構成されます。</span><span class="sxs-lookup"><span data-stu-id="ac807-119">The `member-list` consists of additional constructors, instance and static method declarations, interface declarations, abstract bindings, and property and event declarations.</span></span> <span data-ttu-id="ac807-120">これらについては、「[メンバー](./members/index.md)」に説明があります。</span><span class="sxs-lookup"><span data-stu-id="ac807-120">These are described in [Members](./members/index.md).</span></span>

<span data-ttu-id="ac807-121">省略可能な `as` キーワードと共に使用する `identifier` では、インスタンス変数 (自己識別子) の名前を指定します。これは、型定義の中で型のインスタンスを参照するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="ac807-121">The `identifier` that is used with the optional `as` keyword gives a name to the instance variable, or self identifier, which can be used in the type definition to refer to the instance of the type.</span></span> <span data-ttu-id="ac807-122">詳細については、このトピックで後述する「自己識別子」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac807-122">For more information, see the section Self Identifiers later in this topic.</span></span>

<span data-ttu-id="ac807-123">定義の開始と終了をマークするキーワード `class` と `end` は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="ac807-123">The keywords `class` and `end` that mark the start and end of the definition are optional.</span></span>

<span data-ttu-id="ac807-124">相互に参照する型である相互再帰型は、相互再帰関数と同様に、`and` キーワードで結合します。</span><span class="sxs-lookup"><span data-stu-id="ac807-124">Mutually recursive types, which are types that reference each other, are joined together with the `and` keyword just as mutually recursive functions are.</span></span> <span data-ttu-id="ac807-125">例については、セクション「相互再帰型」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ac807-125">For an example, see the section Mutually Recursive Types.</span></span>

## <a name="constructors"></a><span data-ttu-id="ac807-126">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="ac807-126">Constructors</span></span>

<span data-ttu-id="ac807-127">コンストラクターは、クラス型のインスタンスを作成するコードです。</span><span class="sxs-lookup"><span data-stu-id="ac807-127">The constructor is code that creates an instance of the class type.</span></span> <span data-ttu-id="ac807-128">F# におけるクラスのコンストラクターの動作は、他の .NET 言語とは少し異なります。</span><span class="sxs-lookup"><span data-stu-id="ac807-128">Constructors for classes work somewhat differently in F# than they do in other .NET languages.</span></span> <span data-ttu-id="ac807-129">F# のクラスには、常にプライマリ コンストラクターがあります。その引数を型名の後の `parameter-list` に記述し、その本体は、クラス宣言の先頭にある `let` (および `let rec`) バインドと、その後に続く `do` バインドで構成されます。</span><span class="sxs-lookup"><span data-stu-id="ac807-129">In an F# class, there is always a primary constructor whose arguments are described in the `parameter-list` that follows the type name, and whose body consists of the `let` (and `let rec`) bindings at the start of the class declaration and the `do` bindings that follow.</span></span> <span data-ttu-id="ac807-130">プライマリ コンストラクターの引数は、クラス宣言全体がスコープになります。</span><span class="sxs-lookup"><span data-stu-id="ac807-130">The arguments of the primary constructor are in scope throughout the class declaration.</span></span>

<span data-ttu-id="ac807-131">追加のコンストラクターは、次のように `new` キーワードを使用してメンバーを追加することにより追加できます。</span><span class="sxs-lookup"><span data-stu-id="ac807-131">You can add additional constructors by using the `new` keyword to add a member, as follows:</span></span>

<span data-ttu-id="ac807-132">`new`(`argument-list`) = `constructor-body`</span><span class="sxs-lookup"><span data-stu-id="ac807-132">`new`(`argument-list`) = `constructor-body`</span></span>

<span data-ttu-id="ac807-133">新しいコンストラクターの本体では、クラス宣言の先頭で指定されているプライマリ コンストラクターを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac807-133">The body of the new constructor must invoke the primary constructor that is specified at the top of the class declaration.</span></span>

<span data-ttu-id="ac807-134">この概念を説明する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ac807-134">The following example illustrates this concept.</span></span> <span data-ttu-id="ac807-135">次のコードでは、`MyClass` に 2 つのコンストラクターがあります。2 つの引数を受け取るプライマリ コンストラクターと、引数を受け取らないもう 1 つのコンストラクターです。</span><span class="sxs-lookup"><span data-stu-id="ac807-135">In the following code, `MyClass` has two constructors, a primary constructor that takes two arguments and another constructor that takes no arguments.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2401.fs)]

## <a name="let-and-do-bindings"></a><span data-ttu-id="ac807-136">let および do バインド</span><span class="sxs-lookup"><span data-stu-id="ac807-136">let and do Bindings</span></span>

<span data-ttu-id="ac807-137">クラス定義内の `let` および `do` バインドは、プライマリ クラス コンストラクターの本体を形成し、したがってクラスのインスタンスが作成されるたびに実行されます。</span><span class="sxs-lookup"><span data-stu-id="ac807-137">The `let` and `do` bindings in a class definition form the body of the primary class constructor, and therefore they run whenever a class instance is created.</span></span> <span data-ttu-id="ac807-138">`let` バインドが関数の場合は、メンバーにコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="ac807-138">If a `let` binding is a function, then it is compiled into a member.</span></span> <span data-ttu-id="ac807-139">`let` バインドが、どの関数またはメンバーでも使用されていない値である場合は、コンストラクターに対してローカルな変数にコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="ac807-139">If the `let` binding is a value that is not used in any function or member, then it is compiled into a variable that is local to the constructor.</span></span> <span data-ttu-id="ac807-140">それ以外の場合は、クラスのフィールドにコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="ac807-140">Otherwise, it is compiled into a field of the class.</span></span> <span data-ttu-id="ac807-141">これに続く `do` 式は、プライマリ コンストラクターにコンパイルされ、すべてのインスタンスに対して初期化コードを実行します。</span><span class="sxs-lookup"><span data-stu-id="ac807-141">The `do` expressions that follow are compiled into the primary constructor and execute initialization code for every instance.</span></span> <span data-ttu-id="ac807-142">追加のコンストラクターでは常にプライマリ コンストラクターが呼び出されるため、`let` バインドと `do` バインドは、どのコンストラクターが呼び出されるかに関係なく、常に実行されます。</span><span class="sxs-lookup"><span data-stu-id="ac807-142">Because any additional constructors always call the primary constructor, the `let` bindings and `do` bindings always execute regardless of which constructor is called.</span></span>

<span data-ttu-id="ac807-143">`let` バインドによって作成されるフィールドには、そのクラスのメソッドとプロパティを通じてアクセスできます。ただし、静的メソッドがインスタンス変数をパラメーターとして受け取る場合でも、静的メソッドからそれらにアクセスすることはできません。</span><span class="sxs-lookup"><span data-stu-id="ac807-143">Fields that are created by `let` bindings can be accessed throughout the methods and properties of the class; however, they cannot be accessed from static methods, even if the static methods take an instance variable as a parameter.</span></span> <span data-ttu-id="ac807-144">また、自己識別子 (存在する場合) を使用してアクセスすることはできません。</span><span class="sxs-lookup"><span data-stu-id="ac807-144">They cannot be accessed by using the self identifier, if one exists.</span></span>

## <a name="self-identifiers"></a><span data-ttu-id="ac807-145">自己識別子</span><span class="sxs-lookup"><span data-stu-id="ac807-145">Self Identifiers</span></span>

<span data-ttu-id="ac807-146">"*自己識別子*" は、現在のインスタンスを表す名前です。</span><span class="sxs-lookup"><span data-stu-id="ac807-146">A *self identifier* is a name that represents the current instance.</span></span> <span data-ttu-id="ac807-147">自己識別子は、C# または C++ の `this` キーワード、または Visual Basic の `Me` に似ています。</span><span class="sxs-lookup"><span data-stu-id="ac807-147">Self identifiers resemble the `this` keyword in C# or C++ or `Me` in Visual Basic.</span></span> <span data-ttu-id="ac807-148">自己識別子は、クラス定義全体を自己識別子のスコープにするか、または個別のメソッドのみにするかに応じて、2 つの異なる方法で定義できます。</span><span class="sxs-lookup"><span data-stu-id="ac807-148">You can define a self identifier in two different ways, depending on whether you want the self identifier to be in scope for the whole class definition or just for an individual method.</span></span>

<span data-ttu-id="ac807-149">クラス全体のための自己識別子を定義するには、コンストラクターのパラメーター リストの終わりかっこの後に `as` キーワードを使用し、識別子の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="ac807-149">To define a self identifier for the whole class, use the `as` keyword after the closing parentheses of the constructor parameter list, and specify the identifier name.</span></span>

<span data-ttu-id="ac807-150">1 つのメソッドのためだけの自己識別子を定義するには、自己識別子を、メンバー宣言内のメソッド名の直前にピリオド (.) を区切り記号として指定します。</span><span class="sxs-lookup"><span data-stu-id="ac807-150">To define a self identifier for just one method, provide the self identifier in the member declaration, just before the method name and a period (.) as a separator.</span></span>

<span data-ttu-id="ac807-151">次のコード例は、自己識別子を作成する 2 つの方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="ac807-151">The following code example illustrates the two ways to create a self identifier.</span></span> <span data-ttu-id="ac807-152">最初の行では、`as` キーワードを使用して自己識別子を定義しています。</span><span class="sxs-lookup"><span data-stu-id="ac807-152">In the first line, the `as` keyword is used to define the self identifier.</span></span> <span data-ttu-id="ac807-153">5 行目では、識別子 `this` を使用して、スコープがメソッド `PrintMessage` に限定された自己識別子を定義しています。</span><span class="sxs-lookup"><span data-stu-id="ac807-153">In the fifth line, the identifier `this` is used to define a self identifier whose scope is restricted to the method `PrintMessage`.</span></span>

```fsharp
type MyClass2(dataIn) as self =
    let data = dataIn
    do
        self.PrintMessage()
    member this.PrintMessage() =
        printf "Creating MyClass2 with Data %d" data
```

<span data-ttu-id="ac807-154">他の .NET 言語とは異なり、自己識別子には自由に名前を付けることができます。`self`、`Me`、`this` などの名前に限定されません。</span><span class="sxs-lookup"><span data-stu-id="ac807-154">Unlike in other .NET languages, you can name the self identifier however you want; you are not restricted to names such as `self`, `Me`, or `this`.</span></span>

<span data-ttu-id="ac807-155">`as` キーワードを使用して宣言した自己識別子は、基底コンストラクターの後まで初期化されません。</span><span class="sxs-lookup"><span data-stu-id="ac807-155">The self identifier that is declared with the `as` keyword is not initialized until after the base constructor.</span></span> <span data-ttu-id="ac807-156">したがって、基底コンストラクターの前または内部で使用すると、実行時に `System.InvalidOperationException: The initialization of an object or value resulted in an object or value being accessed recursively before it was fully initialized.` が発生します。</span><span class="sxs-lookup"><span data-stu-id="ac807-156">Therefore, when used before or inside the base constructor, `System.InvalidOperationException: The initialization of an object or value resulted in an object or value being accessed recursively before it was fully initialized.` will be raised during runtime.</span></span> <span data-ttu-id="ac807-157">自己識別子は、`let` バインドや `do` バインド内など、基底コンストラクターの後であれば自由に使用できます。</span><span class="sxs-lookup"><span data-stu-id="ac807-157">You can use the self identifier freely after the base constructor, such as in `let` bindings or `do` bindings.</span></span>

## <a name="generic-type-parameters"></a><span data-ttu-id="ac807-158">ジェネリック型の型パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac807-158">Generic Type Parameters</span></span>

<span data-ttu-id="ac807-159">ジェネリック型パラメーターは、山かっこ (`<` と `>`) で囲み、単一引用符の後に識別子を続ける形式で指定します。</span><span class="sxs-lookup"><span data-stu-id="ac807-159">Generic type parameters are specified in angle brackets (`<` and `>`), in the form of a single quotation mark followed by an identifier.</span></span> <span data-ttu-id="ac807-160">複数のジェネリック型パラメーターはコンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="ac807-160">Multiple generic type parameters are separated by commas.</span></span> <span data-ttu-id="ac807-161">ジェネリック型パラメーターは、宣言全体がスコープになります。</span><span class="sxs-lookup"><span data-stu-id="ac807-161">The generic type parameter is in scope throughout the declaration.</span></span> <span data-ttu-id="ac807-162">ジェネリック型パラメーターを指定する方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="ac807-162">The following code example shows how to specify generic type parameters.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2403.fs)]

<span data-ttu-id="ac807-163">型引数は、型が使用されるときに推論されます。</span><span class="sxs-lookup"><span data-stu-id="ac807-163">Type arguments are inferred when the type is used.</span></span> <span data-ttu-id="ac807-164">次のコードでは、推論される型はタプルのシーケンスです。</span><span class="sxs-lookup"><span data-stu-id="ac807-164">In the following code, the inferred type is a sequence of tuples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet24031.fs)]

## <a name="specifying-inheritance"></a><span data-ttu-id="ac807-165">継承の指定</span><span class="sxs-lookup"><span data-stu-id="ac807-165">Specifying Inheritance</span></span>

<span data-ttu-id="ac807-166">`inherit` 句では、直接基底クラス (存在する場合) を指定します。</span><span class="sxs-lookup"><span data-stu-id="ac807-166">The `inherit` clause identifies the direct base class, if there is one.</span></span> <span data-ttu-id="ac807-167">F# では、直接基底クラスを 1 つだけ使用できます。</span><span class="sxs-lookup"><span data-stu-id="ac807-167">In F#, only one direct base class is allowed.</span></span> <span data-ttu-id="ac807-168">クラスによって実装されるインターフェイスは、基底クラスとは見なされません。</span><span class="sxs-lookup"><span data-stu-id="ac807-168">Interfaces that a class implements are not considered base classes.</span></span> <span data-ttu-id="ac807-169">インターフェイスについては、トピック「[インターフェイス](Interfaces.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ac807-169">Interfaces are discussed in the [Interfaces](Interfaces.md) topic.</span></span>

<span data-ttu-id="ac807-170">派生クラスから基底クラスのメソッドとプロパティにアクセスするには、識別子として言語キーワード `base` を使用し、その後にピリオド (.) とメンバーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="ac807-170">You can access the methods and properties of the base class from the derived class by using the language keyword `base` as an identifier, followed by a period (.) and the name of the member.</span></span>

<span data-ttu-id="ac807-171">詳細については、「[継承](inheritance.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac807-171">For more information, see [Inheritance](inheritance.md).</span></span>

## <a name="members-section"></a><span data-ttu-id="ac807-172">メンバー セクション</span><span class="sxs-lookup"><span data-stu-id="ac807-172">Members Section</span></span>

<span data-ttu-id="ac807-173">このセクションでは、静的またはインスタンス メソッド、プロパティ、インターフェイスの実装、抽象メンバー、イベント宣言、追加のコンストラクターを定義できます。</span><span class="sxs-lookup"><span data-stu-id="ac807-173">You can define static or instance methods, properties, interface implementations, abstract members, event declarations, and additional constructors in this section.</span></span> <span data-ttu-id="ac807-174">let と do のバインドは、このセクションには記述できません。</span><span class="sxs-lookup"><span data-stu-id="ac807-174">Let and do bindings cannot appear in this section.</span></span> <span data-ttu-id="ac807-175">メンバーとしてはクラスに加えてさまざまな F# 型を追加できるため、別個のトピック「[メンバー](./members/index.md)」で説明します。</span><span class="sxs-lookup"><span data-stu-id="ac807-175">Because members can be added to a variety of F# types in addition to classes, they are discussed in a separate topic, [Members](./members/index.md).</span></span>

## <a name="mutually-recursive-types"></a><span data-ttu-id="ac807-176">相互再帰型</span><span class="sxs-lookup"><span data-stu-id="ac807-176">Mutually Recursive Types</span></span>

<span data-ttu-id="ac807-177">相互に参照する型を循環的な方法で定義する場合は、`and` キーワードを使用して型定義を連結します。</span><span class="sxs-lookup"><span data-stu-id="ac807-177">When you define types that reference each other in a circular way, you string together the type definitions by using the `and` keyword.</span></span> <span data-ttu-id="ac807-178">次のように、最初の定義以外のすべてで `type` キーワードを `and` キーワードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="ac807-178">The `and` keyword replaces the `type` keyword on all except the first definition, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2404.fs)]

<span data-ttu-id="ac807-179">出力は、現在のディレクトリにあるすべてのファイルの一覧です。</span><span class="sxs-lookup"><span data-stu-id="ac807-179">The output is a list of all the files in the current directory.</span></span>

## <a name="when-to-use-classes-unions-records-and-structures"></a><span data-ttu-id="ac807-180">クラス、共用体、レコード、構造体を使用するべき状況</span><span class="sxs-lookup"><span data-stu-id="ac807-180">When to Use Classes, Unions, Records, and Structures</span></span>

<span data-ttu-id="ac807-181">選択可能なさまざまな種類の型があるため、それぞれの型の設計目的を十分に理解し、特定の状況に適した型を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac807-181">Given the variety of types to choose from, you need to have a good understanding of what each type is designed for to select the appropriate type for a particular situation.</span></span> <span data-ttu-id="ac807-182">クラスは、オブジェクト指向プログラミングのコンテキストで使用するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="ac807-182">Classes are designed for use in object-oriented programming contexts.</span></span> <span data-ttu-id="ac807-183">オブジェクト指向プログラミングは、.NET Framework 用に記述されたアプリケーションで使用される最も重要なパラダイムです。</span><span class="sxs-lookup"><span data-stu-id="ac807-183">Object-oriented programming is the dominant paradigm used in applications that are written for the .NET Framework.</span></span> <span data-ttu-id="ac807-184">F# コードを .NET Framework または別のオブジェクト指向ライブラリと密接に連携させる必要がある場合、特に UI ライブラリなどのオブジェクト指向の型システムから拡張する必要がある場合は、おそらくクラスが適切です。</span><span class="sxs-lookup"><span data-stu-id="ac807-184">If your F# code has to work closely with the .NET Framework or another object-oriented library, and especially if you have to extend from an object-oriented type system such as a UI library, classes are probably appropriate.</span></span>

<span data-ttu-id="ac807-185">オブジェクト指向のコードと密接に相互運用していない場合、または自己完結型のコードを記述していて、オブジェクト指向のコードと頻繁にやり取りする必要がない場合は、レコードと判別共用体の使用を検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac807-185">If you are not interoperating closely with object-oriented code, or if you are writing code that is self-contained and therefore protected from frequent interaction with object-oriented code, you should consider using records and discriminated unions.</span></span> <span data-ttu-id="ac807-186">十分に考え抜かれた 1 つの判別共用体を適切なパターン マッチング コードと併用する方法は、オブジェクト階層のシンプルな代替手段としてよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="ac807-186">A single, well thought–out discriminated union, together with appropriate pattern matching code, can often be used as a simpler alternative to an object hierarchy.</span></span> <span data-ttu-id="ac807-187">判別共用体の詳細については、「[判別共用体](discriminated-unions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ac807-187">For more information about discriminated unions, see [Discriminated Unions](discriminated-unions.md).</span></span>

<span data-ttu-id="ac807-188">レコードにはクラスよりもシンプルであるという利点がありますが、型に対する要求がそのシンプルな機能で実現できることを超える場合、レコードは適切ではありません。</span><span class="sxs-lookup"><span data-stu-id="ac807-188">Records have the advantage of being simpler than classes, but records are not appropriate when the demands of a type exceed what can be accomplished with their simplicity.</span></span> <span data-ttu-id="ac807-189">レコードは、基本的には値の単純な集合体であり、カスタム アクションを実行できる個別のコンストラクターや、非表示フィールドや、継承またはインターフェイスの実装はありません。</span><span class="sxs-lookup"><span data-stu-id="ac807-189">Records are basically simple aggregates of values, without separate constructors that can perform custom actions, without hidden fields, and without inheritance or interface implementations.</span></span> <span data-ttu-id="ac807-190">レコードにプロパティやメソッドなどのメンバーを追加して、より複雑な動作をさせることはできますが、レコードに格納されるフィールドが値の単純な集合体であることに変わりはありません。</span><span class="sxs-lookup"><span data-stu-id="ac807-190">Although members such as properties and methods can be added to records to make their behavior more complex, the fields stored in a record are still a simple aggregate of values.</span></span> <span data-ttu-id="ac807-191">レコードの詳細については、「[レコード](records.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ac807-191">For more information about records, see [Records](records.md).</span></span>

<span data-ttu-id="ac807-192">構造体は、データの小さな集合体に使用する場合に役立ちますが、.NET 値型であるという点でクラスおよびレコードと異なります。</span><span class="sxs-lookup"><span data-stu-id="ac807-192">Structures are also useful for small aggregates of data, but they differ from classes and records in that they are .NET value types.</span></span> <span data-ttu-id="ac807-193">クラスとレコードは .NET 参照型です。</span><span class="sxs-lookup"><span data-stu-id="ac807-193">Classes and records are .NET reference types.</span></span> <span data-ttu-id="ac807-194">値型と参照型のセマンティクスは、値型が値渡しされるという点で異なります。</span><span class="sxs-lookup"><span data-stu-id="ac807-194">The semantics of value types and reference types are different in that value types are passed by value.</span></span> <span data-ttu-id="ac807-195">これは、パラメーターとして渡された場合、または関数から返された場合に、ビットごとにコピーされることを意味します。</span><span class="sxs-lookup"><span data-stu-id="ac807-195">This means that they are copied bit for bit when they are passed as a parameter or returned from a function.</span></span> <span data-ttu-id="ac807-196">また、これらはスタックに格納されるか、親オブジェクトの内部に埋め込まれます (フィールドで使用される場合)。ヒープ上にある専用の別個の場所に格納されるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="ac807-196">They are also stored on the stack or, if they are used as a field, embedded inside the parent object instead of stored in their own separate location on the heap.</span></span> <span data-ttu-id="ac807-197">したがって、ヒープにアクセスするオーバーヘッドが問題になる場合、頻繁にアクセスされるデータには構造体が適しています。</span><span class="sxs-lookup"><span data-stu-id="ac807-197">Therefore, structures are appropriate for frequently accessed data when the overhead of accessing the heap is a problem.</span></span> <span data-ttu-id="ac807-198">構造体の詳細については、「[構造体](structures.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ac807-198">For more information about structures, see [Structures](structures.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ac807-199">関連項目</span><span class="sxs-lookup"><span data-stu-id="ac807-199">See also</span></span>

- [<span data-ttu-id="ac807-200">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="ac807-200">F# Language Reference</span></span>](index.md)
- <span data-ttu-id="ac807-201">[[メンバー]](./members/index.md)</span><span class="sxs-lookup"><span data-stu-id="ac807-201">[Members](./members/index.md)</span></span>
- [<span data-ttu-id="ac807-202">継承</span><span class="sxs-lookup"><span data-stu-id="ac807-202">Inheritance</span></span>](inheritance.md)
- [<span data-ttu-id="ac807-203">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ac807-203">Interfaces</span></span>](interfaces.md)
