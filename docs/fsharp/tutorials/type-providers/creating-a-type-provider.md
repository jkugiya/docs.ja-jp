---
title: 'チュートリアル: 型プロバイダーを作成する'
description: 'いくつかの単純型プロバイダーを調べて基本的な概念を説明することで、F # 3.0 で独自の F # 型プロバイダーを作成する方法について説明します。'
ms.date: 11/04/2019
ms.openlocfilehash: 803b6ea141ed4404daf5daccd1a53212d8b42234
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100468305"
---
# <a name="tutorial-create-a-type-provider"></a><span data-ttu-id="786be-103">チュートリアル: 型プロバイダーを作成する</span><span class="sxs-lookup"><span data-stu-id="786be-103">Tutorial: Create a Type Provider</span></span>

<span data-ttu-id="786be-104">F # の型プロバイダーのメカニズムは、情報豊富なプログラミングをサポートするうえで非常に重要です。</span><span class="sxs-lookup"><span data-stu-id="786be-104">The type provider mechanism in F# is a significant part of its support for information rich programming.</span></span> <span data-ttu-id="786be-105">このチュートリアルでは、基本的な概念を示すために単純な型プロバイダーをいくつか作成する過程を通して、独自の型プロバイダーを作成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="786be-105">This tutorial explains how to create your own type providers by walking you through the development of several simple type providers to illustrate the basic concepts.</span></span> <span data-ttu-id="786be-106">F # の型プロバイダー機構の詳細については、「 [型プロバイダー](index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="786be-106">For more information about the type provider mechanism in F#, see [Type Providers](index.md).</span></span>

<span data-ttu-id="786be-107">F # エコシステムには、一般的に使用されるインターネットおよびエンタープライズデータサービス用のさまざまな種類のプロバイダーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="786be-107">The F# ecosystem contains a range of type providers for commonly used Internet and enterprise data services.</span></span> <span data-ttu-id="786be-108">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="786be-108">For example:</span></span>

- <span data-ttu-id="786be-109">Fsharp.core には、JSON、XML、CSV、HTML ドキュメント形式の型プロバイダーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="786be-109">FSharp.Data includes type providers for JSON, XML, CSV and HTML document formats.</span></span>

- <span data-ttu-id="786be-110">[Sqlprovider](https://fsprojects.github.io/SQLProvider/) は、これらのデータソースに対するオブジェクトマッピングと F # LINQ クエリを使用して、SQL データベースへの厳密に型指定されたアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="786be-110">[SQLProvider](https://fsprojects.github.io/SQLProvider/) provides strongly typed access to SQL databases through a object mapping and F# LINQ queries against these data sources.</span></span>

- <span data-ttu-id="786be-111">[FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) には、F# の T-SQL のコンパイル時チェック埋め込み用の型プロバイダーのセットがあります。</span><span class="sxs-lookup"><span data-stu-id="786be-111">[FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) has a set of type providers for compile-time checked embedding of T-SQL in F#.</span></span>

- <span data-ttu-id="786be-112">[Fsharp.core](https://fsprojects.github.io/FSharp.Data.TypeProviders/) は、SQL、Entity Framework、OData、および WSDL データサービスにアクセスするための .NET Framework プログラミングでのみ使用するための、以前の種類のプロバイダーのセットです。</span><span class="sxs-lookup"><span data-stu-id="786be-112">[FSharp.Data.TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) is an older set of type providers for use only with .NET Framework programming for accessing SQL, Entity Framework, OData and WSDL data services.</span></span>

<span data-ttu-id="786be-113">必要に応じて、カスタム型プロバイダーを作成することも、他のユーザーが作成した型プロバイダーを参照することもできます。</span><span class="sxs-lookup"><span data-stu-id="786be-113">Where necessary, you can create custom type providers, or you can reference type providers that others have created.</span></span> <span data-ttu-id="786be-114">たとえば、組織に 1 つのデータ サービスを用意し、そのデータ サービスにより、増加し続ける名前付きデータセット群と各データセットの安定したデータ スキーマを提供することができます。</span><span class="sxs-lookup"><span data-stu-id="786be-114">For example, your organization could have a data service that provides a large and growing number of named data sets, each with its own stable data schema.</span></span> <span data-ttu-id="786be-115">スキーマを読み取り、最新のデータセットを厳密に型指定してプログラマに提示する型プロバイダーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="786be-115">You can create a type provider that reads the schemas and presents the current data sets to the programmer in a strongly typed way.</span></span>

## <a name="before-you-start"></a><span data-ttu-id="786be-116">開始前の準備</span><span class="sxs-lookup"><span data-stu-id="786be-116">Before You Start</span></span>

<span data-ttu-id="786be-117">型プロバイダー メカニズムは、主に F# のプログラミング作業にデータとサービスの安定した情報空間を提供するために設計されています。</span><span class="sxs-lookup"><span data-stu-id="786be-117">The type provider mechanism is primarily designed for injecting stable data and service information spaces into the F# programming experience.</span></span>

<span data-ttu-id="786be-118">このメカニズムは、プログラム ロジックに合うようにプログラムの実行中にスキーマが変わるような情報空間を提供するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="786be-118">This mechanism isn’t designed for injecting information spaces whose schema changes during program execution in ways that are relevant to program logic.</span></span> <span data-ttu-id="786be-119">また、このメカニズムは言語内メタプログラミングでいくつか有効な使用法がありますが、この分野のために設計されたものではありません。</span><span class="sxs-lookup"><span data-stu-id="786be-119">Also, the mechanism isn't designed for intra-language meta-programming, even though that domain contains some valid uses.</span></span> <span data-ttu-id="786be-120">このメカニズムは型プロバイダーの作成が非常に高い価値をもたらし必要な場合にのみ使用してください。</span><span class="sxs-lookup"><span data-stu-id="786be-120">You should use this mechanism only where necessary and where the development of a type provider yields very high value.</span></span>

<span data-ttu-id="786be-121">スキーマを使用できない場合は、型プロバイダーを作成しないでください。</span><span class="sxs-lookup"><span data-stu-id="786be-121">You should avoid writing a type provider where a schema isn't available.</span></span> <span data-ttu-id="786be-122">同様に、通常の (または既存の) .NET ライブラリが十分に機能する場合は、型プロバイダーを作成しないでください。</span><span class="sxs-lookup"><span data-stu-id="786be-122">Likewise, you should avoid writing a type provider where an ordinary (or even an existing) .NET library would suffice.</span></span>

<span data-ttu-id="786be-123">開始する前に、次の検討事項を確認してください。</span><span class="sxs-lookup"><span data-stu-id="786be-123">Before you start, you might ask the following questions:</span></span>

- <span data-ttu-id="786be-124">情報ソースのスキーマがあるか。</span><span class="sxs-lookup"><span data-stu-id="786be-124">Do you have a schema for your information source?</span></span> <span data-ttu-id="786be-125">その場合、F# および .NET の型システムへのマッピングはどうか。</span><span class="sxs-lookup"><span data-stu-id="786be-125">If so, what’s the mapping into the F# and .NET type system?</span></span>

- <span data-ttu-id="786be-126">既存の (動的に型指定された) API を実装の開始点として使用できるか。</span><span class="sxs-lookup"><span data-stu-id="786be-126">Can you use an existing (dynamically typed) API as a starting point for your implementation?</span></span>

- <span data-ttu-id="786be-127">型プロバイダーを作成する理由として十分な使用が見込まれるか。</span><span class="sxs-lookup"><span data-stu-id="786be-127">Will you and your organization have enough uses of the type provider to make writing it worthwhile?</span></span> <span data-ttu-id="786be-128">通常の .NET ライブラリでニーズに対応できるか。</span><span class="sxs-lookup"><span data-stu-id="786be-128">Would a normal .NET library meet your needs?</span></span>

- <span data-ttu-id="786be-129">使用するスキーマがどの程度変わるか。</span><span class="sxs-lookup"><span data-stu-id="786be-129">How much will your schema change?</span></span>

- <span data-ttu-id="786be-130">スキーマがコーディング中に変わるか。</span><span class="sxs-lookup"><span data-stu-id="786be-130">Will it change during coding?</span></span>

- <span data-ttu-id="786be-131">スキーマがコーディング セッション間で変わるか。</span><span class="sxs-lookup"><span data-stu-id="786be-131">Will it change between coding sessions?</span></span>

- <span data-ttu-id="786be-132">スキーマがプログラムの実行中に変わるか。</span><span class="sxs-lookup"><span data-stu-id="786be-132">Will it change during program execution?</span></span>

<span data-ttu-id="786be-133">型プロバイダーはスキーマが実行時とコンパイル済みコードの有効期間中に安定している場合に最も適しています。</span><span class="sxs-lookup"><span data-stu-id="786be-133">Type providers are best suited to situations where the schema is stable at runtime and during the lifetime of compiled code.</span></span>

## <a name="a-simple-type-provider"></a><span data-ttu-id="786be-134">単純な型プロバイダー</span><span class="sxs-lookup"><span data-stu-id="786be-134">A Simple Type Provider</span></span>

<span data-ttu-id="786be-135">このサンプルは、 `examples` [F # 型プロバイダー SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/)のディレクトリにあるサンプルと同様に HelloWorldTypeProvider です。</span><span class="sxs-lookup"><span data-stu-id="786be-135">This sample is Samples.HelloWorldTypeProvider, similar to the samples in the `examples` directory of the [F# Type Provider SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/).</span></span> <span data-ttu-id="786be-136">このプロバイダーは、次のコードが示すように、F# シグネチャ構文を使用して `Type1` 以外の詳細を省略することで、消去型 100 個を含む "型空間" を使用可能にします。</span><span class="sxs-lookup"><span data-stu-id="786be-136">The provider makes available a "type space" that contains 100 erased types, as the following code shows by using F# signature syntax and omitting the details for all except `Type1`.</span></span> <span data-ttu-id="786be-137">消去型の詳細については、このトピックで後述する「 [指定された型の消去に関する詳細](#details-about-erased-provided-types) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="786be-137">For more information about erased types, see [Details About Erased Provided Types](#details-about-erased-provided-types) later in this topic.</span></span>

```fsharp
namespace Samples.HelloWorldTypeProvider

type Type1 =
    /// This is a static property.
    static member StaticProperty : string

    /// This constructor takes no arguments.
    new : unit -> Type1

    /// This constructor takes one argument.
    new : data:string -> Type1

    /// This is an instance property.
    member InstanceProperty : int

    /// This is an instance method.
    member InstanceMethod : x:int -> char

    nested type NestedType =
        /// This is StaticProperty1 on NestedType.
        static member StaticProperty1 : string
        …
        /// This is StaticProperty100 on NestedType.
        static member StaticProperty100 : string

type Type2 =
…
…

type Type100 =
…
```

<span data-ttu-id="786be-138">指定された型とメンバーのセットは静的で既知であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="786be-138">Note that the set of types and members provided is statically known.</span></span> <span data-ttu-id="786be-139">この例では、スキーマに依存する型を指定するプロバイダーの機能を利用しません。</span><span class="sxs-lookup"><span data-stu-id="786be-139">This example doesn't leverage the ability of providers to provide types that depend on a schema.</span></span> <span data-ttu-id="786be-140">型プロバイダーの実装は次のコードでその概要を示し、詳細については、このトピックの後半のセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="786be-140">The implementation of the type provider is outlined in the following code, and the details are covered in later sections of this topic.</span></span>

> [!WARNING]
> <span data-ttu-id="786be-141">このコードとオンラインサンプルには違いがある場合があります。</span><span class="sxs-lookup"><span data-stu-id="786be-141">There may be differences between this code and the online samples.</span></span>

```fsharp
namespace Samples.FSharp.HelloWorldTypeProvider

open System
open System.Reflection
open ProviderImplementation.ProvidedTypes
open FSharp.Core.CompilerServices
open FSharp.Quotations

// This type defines the type provider. When compiled to a DLL, it can be added
// as a reference to an F# command-line compilation, script, or project.
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =

  // Inheriting from this type provides implementations of ITypeProvider
  // in terms of the provided types below.
  inherit TypeProviderForNamespaces(config)

  let namespaceName = "Samples.HelloWorldTypeProvider"
  let thisAssembly = Assembly.GetExecutingAssembly()

  // Make one provided type, called TypeN.
  let makeOneProvidedType (n:int) =
  …
  // Now generate 100 types
  let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]

  // And add them to the namespace
  do this.AddNamespace(namespaceName, types)

[<assembly:TypeProviderAssembly>]
do()
```

<span data-ttu-id="786be-142">このプロバイダーを使用するには、Visual Studio の別のインスタンスを開き、F # スクリプトを作成した後、次のコードに示すように、#r を使用してスクリプトからプロバイダーへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="786be-142">To use this provider, open a separate instance of Visual Studio, create an F# script, and then add a reference to the provider from your script by using #r as the following code shows:</span></span>

```fsharp
#r @".\bin\Debug\Samples.HelloWorldTypeProvider.dll"

let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")

let obj2 = Samples.HelloWorldTypeProvider.Type1("some other data")

obj1.InstanceProperty
obj2.InstanceProperty

[ for index in 0 .. obj1.InstanceProperty-1 -> obj1.InstanceMethod(index) ]
[ for index in 0 .. obj2.InstanceProperty-1 -> obj2.InstanceMethod(index) ]

let data1 = Samples.HelloWorldTypeProvider.Type1.NestedType.StaticProperty35
```

<span data-ttu-id="786be-143">型プロバイダーが生成した `Samples.HelloWorldTypeProvider` という名前空間で型を探します。</span><span class="sxs-lookup"><span data-stu-id="786be-143">Then look for the types under the `Samples.HelloWorldTypeProvider` namespace that the type provider generated.</span></span>

<span data-ttu-id="786be-144">プロバイダーを再コンパイルする前に、そのプロバイダーの DLL を使用する Visual Studio と F# Interactive のすべてのインスタンスを閉じる必要があります。</span><span class="sxs-lookup"><span data-stu-id="786be-144">Before you recompile the provider, make sure that you have closed all instances of Visual Studio and F# Interactive that are using the provider DLL.</span></span> <span data-ttu-id="786be-145">これを行わない場合、出力の DLL がロックされているためビルド エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="786be-145">Otherwise, a build error will occur because the output DLL will be locked.</span></span>

<span data-ttu-id="786be-146">print ステートメントを使ってこのプロバイダーをデバッグするには、プロバイダーの問題を明らかにするスクリプトを作成して、次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="786be-146">To debug this provider by using print statements, make a script that exposes a problem with the provider, and then use the following code:</span></span>

```console
fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="786be-147">Visual Studio を使用してこのプロバイダーをデバッグするには、管理者資格情報を使用して Visual Studio の開発者コマンドプロンプトを開き、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="786be-147">To debug this provider by using Visual Studio, open the Developer Command Prompt for Visual Studio with administrative credentials, and run the following command:</span></span>

```console
devenv.exe /debugexe fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="786be-148">別の方法として、Visual Studio を開き、[デバッグ] メニューを開いてを選択 `Debug/Attach to process…` し、スクリプトを編集している別のプロセスにアタッチし `devenv` ます。</span><span class="sxs-lookup"><span data-stu-id="786be-148">As an alternative, open Visual Studio, open the Debug menu, choose `Debug/Attach to process…`, and attach to another `devenv` process where you’re editing your script.</span></span> <span data-ttu-id="786be-149">この方法を使用すると、2 番目のインスタンス (IntelliSense およびその他の機能をすべて備えている) に式を対話形式で入力できるので、型プロバイダー内の特定のロジックを簡単に対象とすることができます。</span><span class="sxs-lookup"><span data-stu-id="786be-149">By using this method, you can more easily target particular logic in the type provider by interactively typing expressions into the second instance (with full IntelliSense and other features).</span></span>

<span data-ttu-id="786be-150">生成されたコード内のエラーを特定しやすくするために、マイ コードのみのデバッグを無効にできます。</span><span class="sxs-lookup"><span data-stu-id="786be-150">You can disable Just My Code debugging to better identify errors in generated code.</span></span> <span data-ttu-id="786be-151">この機能を有効または無効にする方法の詳細については、「 [デバッガーでのコード間の移動](/visualstudio/debugger/navigating-through-code-with-the-debugger)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="786be-151">For information about how to enable or disable this feature, see [Navigating through Code with the Debugger](/visualstudio/debugger/navigating-through-code-with-the-debugger).</span></span> <span data-ttu-id="786be-152">また、メニューを開き、 `Debug` `Exceptions` Ctrl + Alt + E キーを選択してダイアログボックスを開くことで、初回例外のキャッチを設定することもでき `Exceptions` ます。</span><span class="sxs-lookup"><span data-stu-id="786be-152">Also, you can also set first-chance exception catching by opening the `Debug` menu and then choosing `Exceptions` or by choosing the Ctrl+Alt+E keys to open the `Exceptions` dialog box.</span></span> <span data-ttu-id="786be-153">このダイアログボックスの [] で、 `Common Language Runtime Exceptions` チェックボックスをオンにし `Thrown` ます。</span><span class="sxs-lookup"><span data-stu-id="786be-153">In that dialog box, under `Common Language Runtime Exceptions`, select the `Thrown` check box.</span></span>

### <a name="implementation-of-the-type-provider"></a><span data-ttu-id="786be-154">型プロバイダーの実装</span><span class="sxs-lookup"><span data-stu-id="786be-154">Implementation of the Type Provider</span></span>

<span data-ttu-id="786be-155">ここでは、型プロバイダーの実装の主なセクションを順に説明します。</span><span class="sxs-lookup"><span data-stu-id="786be-155">This section walks you through the principal sections of the type provider implementation.</span></span> <span data-ttu-id="786be-156">まず、カスタム型プロバイダーの型自体を定義します。</span><span class="sxs-lookup"><span data-stu-id="786be-156">First, you define the type for the custom type provider itself:</span></span>

```fsharp
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =
```

<span data-ttu-id="786be-157">この型はパブリックである必要があります。また、別の F # プロジェクトが型を含むアセンブリを参照している場合にコンパイラが型プロバイダーを認識するように、 [typeprovider](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-compilerservices-typeproviderattribute.html) 属性でマークする必要があります。</span><span class="sxs-lookup"><span data-stu-id="786be-157">This type must be public, and you must mark it with the [TypeProvider](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-compilerservices-typeproviderattribute.html) attribute so that the compiler will recognize the type provider when a separate F# project references the assembly that contains the type.</span></span> <span data-ttu-id="786be-158">*Config* パラメーターは省略可能であり、存在する場合は、F # コンパイラによって作成される型プロバイダーインスタンスのコンテキスト構成情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="786be-158">The *config* parameter is optional, and, if present, contains contextual configuration information for the type provider instance that the F# compiler creates.</span></span>

<span data-ttu-id="786be-159">次に、 [ITypeProvider](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-compilerservices-itypeprovider.html) インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="786be-159">Next, you implement the [ITypeProvider](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-compilerservices-itypeprovider.html) interface.</span></span> <span data-ttu-id="786be-160">この場合、基本型として `TypeProviderForNamespaces` API の `ProvidedTypes` 型を使用します。</span><span class="sxs-lookup"><span data-stu-id="786be-160">In this case, you use the `TypeProviderForNamespaces` type from the `ProvidedTypes` API as a base type.</span></span> <span data-ttu-id="786be-161">このヘルパー型は、集中的に指定された名前空間の有限のコレクションを指定できます。個々の名前空間には、集中的に指定された固定の型 (有限数) が直接含まれています。</span><span class="sxs-lookup"><span data-stu-id="786be-161">This helper type can provide a finite collection of eagerly provided namespaces, each of which directly contains a finite number of fixed, eagerly provided types.</span></span> <span data-ttu-id="786be-162">このコンテキストでは、プロバイダー *集中的* は、必要または使用されていない場合でも型を生成します。</span><span class="sxs-lookup"><span data-stu-id="786be-162">In this context, the provider *eagerly* generates types even if they aren't needed or used.</span></span>

```fsharp
inherit TypeProviderForNamespaces(config)
```

<span data-ttu-id="786be-163">次に、指定された型の名前空間を指定するローカル プライベート値を定義し、型プロバイダー アセンブリ自体を見つけます。</span><span class="sxs-lookup"><span data-stu-id="786be-163">Next, define local private values that specify the namespace for the provided types, and find the type provider assembly itself.</span></span> <span data-ttu-id="786be-164">このアセンブリは後で、指定された型が消去される場合の論理親の型として使用されます。</span><span class="sxs-lookup"><span data-stu-id="786be-164">This assembly is used later as the logical parent type of the erased types that are provided.</span></span>

```fsharp
let namespaceName = "Samples.HelloWorldTypeProvider"
let thisAssembly = Assembly.GetExecutingAssembly()
```

<span data-ttu-id="786be-165">次に、各型 (Type1…Type100) を指定する関数を作成します。</span><span class="sxs-lookup"><span data-stu-id="786be-165">Next, create a function to provide each of the types Type1…Type100.</span></span> <span data-ttu-id="786be-166">この関数は、このトピックの後半で詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="786be-166">This function is explained in more detail later in this topic.</span></span>

```fsharp
let makeOneProvidedType (n:int) = …
```

<span data-ttu-id="786be-167">次に、指定された型 100 個を生成します。</span><span class="sxs-lookup"><span data-stu-id="786be-167">Next, generate the 100 provided types:</span></span>

```fsharp
let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]
```

<span data-ttu-id="786be-168">次に、指定された名前空間としてそれらの型を追加します。</span><span class="sxs-lookup"><span data-stu-id="786be-168">Next, add the types as a provided namespace:</span></span>

```fsharp
do this.AddNamespace(namespaceName, types)
```

<span data-ttu-id="786be-169">最後に、型プロバイダー DLL を作成していることを示すアセンブリ属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="786be-169">Finally, add an assembly attribute that indicates that you are creating a type provider DLL:</span></span>

```fsharp
[<assembly:TypeProviderAssembly>]
do()
```

### <a name="providing-one-type-and-its-members"></a><span data-ttu-id="786be-170">1 つの型とそのメンバーの指定</span><span class="sxs-lookup"><span data-stu-id="786be-170">Providing One Type And Its Members</span></span>

<span data-ttu-id="786be-171">`makeOneProvidedType` 関数は、型の 1 つを指定する実際の処理を行います。</span><span class="sxs-lookup"><span data-stu-id="786be-171">The `makeOneProvidedType` function does the real work of providing one of the types.</span></span>

```fsharp
let makeOneProvidedType (n:int) =
…
```

<span data-ttu-id="786be-172">この手順では、この関数の実装を説明します。</span><span class="sxs-lookup"><span data-stu-id="786be-172">This step explains the implementation of this function.</span></span> <span data-ttu-id="786be-173">最初に、指定された型を作成します (たとえば、n = 1 のときは Type1、n = 57 のときは Type57)。</span><span class="sxs-lookup"><span data-stu-id="786be-173">First, create the provided type (for example, Type1, when n = 1, or Type57, when n = 57).</span></span>

```fsharp
// This is the provided type. It is an erased provided type and, in compiled code,
// will appear as type 'obj'.
let t = ProvidedTypeDefinition(thisAssembly, namespaceName,
                               "Type" + string n,
                               baseType = Some typeof<obj>)
```

<span data-ttu-id="786be-174">次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="786be-174">You should note the following points:</span></span>

- <span data-ttu-id="786be-175">この指定された型は消去されます。</span><span class="sxs-lookup"><span data-stu-id="786be-175">This provided type is erased.</span></span>  <span data-ttu-id="786be-176">基本型がであることを示すため `obj` 、インスタンスはコンパイル済みコードで [obj](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-obj.html) 型の値として表示されます。</span><span class="sxs-lookup"><span data-stu-id="786be-176">Because you indicate that the base type is `obj`, instances will appear as values of type [obj](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-obj.html) in compiled code.</span></span>

- <span data-ttu-id="786be-177">入れ子になっていない型を指定する場合、アセンブリと名前空間を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="786be-177">When you specify a non-nested type, you must specify the assembly and namespace.</span></span> <span data-ttu-id="786be-178">消去型の場合、アセンブリは型プロバイダー アセンブリ自体である必要があります。</span><span class="sxs-lookup"><span data-stu-id="786be-178">For erased types, the assembly should be the type provider assembly itself.</span></span>

<span data-ttu-id="786be-179">次に、型に XML ドキュメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="786be-179">Next, add XML documentation to the type.</span></span> <span data-ttu-id="786be-180">このドキュメントは遅延されます。つまり、ホスト コンパイラで必要な場合に、要求に応じて計算されます。</span><span class="sxs-lookup"><span data-stu-id="786be-180">This documentation is delayed, that is, computed on-demand if the host compiler needs it.</span></span>

```fsharp
t.AddXmlDocDelayed (fun () -> $"""This provided type {"Type" + string n}""")
```

<span data-ttu-id="786be-181">次に、指定された静的プロパティを型に追加します。</span><span class="sxs-lookup"><span data-stu-id="786be-181">Next you add a provided static property to the type:</span></span>

```fsharp
let staticProp = ProvidedProperty(propertyName = "StaticProperty",
                                  propertyType = typeof<string>,
                                  isStatic = true,
                                  getterCode = (fun args -> <@@ "Hello!" @@>))
```

<span data-ttu-id="786be-182">このプロパティを取得すると、常に文字列 "Hello!" に評価されます。</span><span class="sxs-lookup"><span data-stu-id="786be-182">Getting this property will always evaluate to the string "Hello!".</span></span> <span data-ttu-id="786be-183">プロパティの `GetterCode` は F# クォートを使用しますが、これはホスト コンパイラがプロパティを取得するために生成するコードを表します。</span><span class="sxs-lookup"><span data-stu-id="786be-183">The `GetterCode` for the property uses an F# quotation, which represents the code that the host compiler generates for getting the property.</span></span> <span data-ttu-id="786be-184">引用符の詳細については、「 [コード引用符 (F #)](../../language-reference/code-quotations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="786be-184">For more information about quotations, see [Code Quotations (F#)](../../language-reference/code-quotations.md).</span></span>

<span data-ttu-id="786be-185">XML ドキュメントをプロパティに追加します。</span><span class="sxs-lookup"><span data-stu-id="786be-185">Add XML documentation to the property.</span></span>

```fsharp
staticProp.AddXmlDocDelayed(fun () -> "This is a static property")
```

<span data-ttu-id="786be-186">ここで、指定された型に指定されたプロパティを添付します。</span><span class="sxs-lookup"><span data-stu-id="786be-186">Now attach the provided property to the provided type.</span></span> <span data-ttu-id="786be-187">指定された各メンバーは 1 つの型にのみ添付します。</span><span class="sxs-lookup"><span data-stu-id="786be-187">You must attach a provided member to one and only one type.</span></span> <span data-ttu-id="786be-188">これに従わない場合、そのメンバーにアクセスできなくなります。</span><span class="sxs-lookup"><span data-stu-id="786be-188">Otherwise, the member will never be accessible.</span></span>

```fsharp
t.AddMember staticProp
```

<span data-ttu-id="786be-189">ここで、パラメーターを受け取らない指定されたコンストラクターを作成します。</span><span class="sxs-lookup"><span data-stu-id="786be-189">Now create a provided constructor that takes no parameters.</span></span>

```fsharp
let ctor = ProvidedConstructor(parameters = [ ],
                               invokeCode = (fun args -> <@@ "The object data" :> obj @@>))
```

<span data-ttu-id="786be-190">そのコンストラクターの `InvokeCode` は F# クォートを返しますが、これはコンストラクターが呼び出されたときにホスト コンパイラが生成するコードを表します。</span><span class="sxs-lookup"><span data-stu-id="786be-190">The `InvokeCode` for the constructor returns an F# quotation, which represents the code that the host compiler generates when the constructor is called.</span></span> <span data-ttu-id="786be-191">たとえば、次のようなコンストラクターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="786be-191">For example, you can use the following constructor:</span></span>

```fsharp
new Type10()
```

<span data-ttu-id="786be-192">指定された型のインスタンスは、基になるデータである "The object data" を使って作成されます。</span><span class="sxs-lookup"><span data-stu-id="786be-192">An instance of the provided type will be created with underlying data "The object data".</span></span> <span data-ttu-id="786be-193">引用符で囲まれたコードには、指定された型を宣言したときに指定したように、その型がこの指定された型の消去であるため、 [obj](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-obj.html) への変換が含まれています。</span><span class="sxs-lookup"><span data-stu-id="786be-193">The quoted code includes a conversion to [obj](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-obj.html) because that type is the erasure of this provided type (as you specified when you declared the provided type).</span></span>

<span data-ttu-id="786be-194">XML ドキュメントをコンストラクターに追加し、指定された型に指定されたコンストラクターを追加します。</span><span class="sxs-lookup"><span data-stu-id="786be-194">Add XML documentation to the constructor, and add the provided constructor to the provided type:</span></span>

```fsharp
ctor.AddXmlDocDelayed(fun () -> "This is a constructor")

t.AddMember ctor
```

<span data-ttu-id="786be-195">パラメーターを 1 つ受け取る指定された 2 番目のコンストラクターを作成します。</span><span class="sxs-lookup"><span data-stu-id="786be-195">Create a second provided constructor that takes one parameter:</span></span>

```fsharp
let ctor2 =
ProvidedConstructor(parameters = [ ProvidedParameter("data",typeof<string>) ],
                    invokeCode = (fun args -> <@@ (%%(args.[0]) : string) :> obj @@>))
```

<span data-ttu-id="786be-196">そのコンストラクターの `InvokeCode` も F# クォートを返しますが、そのクォートはそのメソッドを呼び出すためにホスト コンパイラが生成したコードを表します。</span><span class="sxs-lookup"><span data-stu-id="786be-196">The `InvokeCode` for the constructor again returns an F# quotation, which represents the code that the host compiler generated for a call to the method.</span></span> <span data-ttu-id="786be-197">たとえば、次のようなコンストラクターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="786be-197">For example, you can use the following constructor:</span></span>

```fsharp
new Type10("ten")
```

<span data-ttu-id="786be-198">指定された型のインスタンスが、基になるデータである "ten" を使って作成されます。</span><span class="sxs-lookup"><span data-stu-id="786be-198">An instance of the provided type is created with underlying data "ten".</span></span> <span data-ttu-id="786be-199">既に気付いている読者もいるかもしれませんが、`InvokeCode` 関数の戻り値はクォートです。</span><span class="sxs-lookup"><span data-stu-id="786be-199">You may have already noticed that the `InvokeCode` function returns a quotation.</span></span> <span data-ttu-id="786be-200">この関数への入力は式のリストで、コンストラクター パラメーターごとに 1 つのリストです。</span><span class="sxs-lookup"><span data-stu-id="786be-200">The input to this function is a list of expressions, one per constructor parameter.</span></span> <span data-ttu-id="786be-201">この場合、1 つのパラメーター値を表す式は `args.[0]` にあります。</span><span class="sxs-lookup"><span data-stu-id="786be-201">In this case, an expression that represents the single parameter value is available in `args.[0]`.</span></span> <span data-ttu-id="786be-202">コンストラクターへの呼び出しのコードは、戻り値を消去型 `obj` に強制的に変換します。</span><span class="sxs-lookup"><span data-stu-id="786be-202">The code for a call to the constructor coerces the return value to the erased type `obj`.</span></span> <span data-ttu-id="786be-203">指定された 2 番目のコンストラクターをその型に追加した後、指定されたインスタンス プロパティを作成します。</span><span class="sxs-lookup"><span data-stu-id="786be-203">After you add the second provided constructor to the type, you create a provided instance property:</span></span>

```fsharp
let instanceProp =
    ProvidedProperty(propertyName = "InstanceProperty",
                     propertyType = typeof<int>,
                     getterCode= (fun args ->
                        <@@ ((%%(args.[0]) : obj) :?> string).Length @@>))
instanceProp.AddXmlDocDelayed(fun () -> "This is an instance property")
t.AddMember instanceProp
```

<span data-ttu-id="786be-204">このプロパティを取得すると、その戻り値は表現オブジェクトである文字列の長さです。</span><span class="sxs-lookup"><span data-stu-id="786be-204">Getting this property will return the length of the string, which is the representation object.</span></span> <span data-ttu-id="786be-205">`GetterCode` プロパティは、ホスト コンパイラがプロパティを取得するために生成するコードを指定する F# クォートを返します。</span><span class="sxs-lookup"><span data-stu-id="786be-205">The `GetterCode` property returns an F# quotation that specifies the code that the host compiler generates to get the property.</span></span> <span data-ttu-id="786be-206">`InvokeCode` と同様に、`GetterCode` 関数はクォートを返します。</span><span class="sxs-lookup"><span data-stu-id="786be-206">Like `InvokeCode`, the `GetterCode` function returns a quotation.</span></span> <span data-ttu-id="786be-207">ホスト コンパイラはこの関数を一連の引数を使って呼び出します。</span><span class="sxs-lookup"><span data-stu-id="786be-207">The host compiler calls this function with a list of arguments.</span></span> <span data-ttu-id="786be-208">この場合、引数には、getter が呼び出されるインスタンスを表す単一の式だけが含まれます。これは、を使用してアクセスでき `args.[0]` ます。</span><span class="sxs-lookup"><span data-stu-id="786be-208">In this case, the arguments include just the single expression that represents the instance upon which the getter is being called, which you can access by using `args.[0]`.</span></span> <span data-ttu-id="786be-209">次に、の実装では、消去された `GetterCode` 型の結果の引用符に分割 `obj` し、キャストを使用して、オブジェクトが文字列であることを型を確認するためのコンパイラの機構を満たしています。</span><span class="sxs-lookup"><span data-stu-id="786be-209">The implementation of `GetterCode` then splices into the result quotation at the erased type `obj`, and a cast is used to satisfy the compiler's mechanism for checking types that the object is a string.</span></span> <span data-ttu-id="786be-210">`makeOneProvidedType` の次の部分は 1 個のパラメーターを持つインスタンス メソッドを指定します。</span><span class="sxs-lookup"><span data-stu-id="786be-210">The next part of `makeOneProvidedType` provides an instance method with one parameter.</span></span>

```fsharp
let instanceMeth =
    ProvidedMethod(methodName = "InstanceMethod",
                   parameters = [ProvidedParameter("x",typeof<int>)],
                   returnType = typeof<char>,
                   invokeCode = (fun args ->
                       <@@ ((%%(args.[0]) : obj) :?> string).Chars(%%(args.[1]) : int) @@>))

instanceMeth.AddXmlDocDelayed(fun () -> "This is an instance method")
// Add the instance method to the type.
t.AddMember instanceMeth
```

<span data-ttu-id="786be-211">最後に、100 個のプロパティを含む入れ子構造の型を作成します。</span><span class="sxs-lookup"><span data-stu-id="786be-211">Finally, create a nested type that contains 100 nested properties.</span></span> <span data-ttu-id="786be-212">この入れ子構造の型とそのプロパティの作成は遅延されます。つまり、要求に応じて計算されます。</span><span class="sxs-lookup"><span data-stu-id="786be-212">The creation of this nested type and its properties is delayed, that is, computed on-demand.</span></span>

```fsharp
t.AddMembersDelayed(fun () ->
  let nestedType = ProvidedTypeDefinition("NestedType", Some typeof<obj>)

  nestedType.AddMembersDelayed (fun () ->
    let staticPropsInNestedType =
      [
          for i in 1 .. 100 ->
              let valueOfTheProperty = "I am string "  + string i

              let p =
                ProvidedProperty(propertyName = "StaticProperty" + string i,
                  propertyType = typeof<string>,
                  isStatic = true,
                  getterCode= (fun args -> <@@ valueOfTheProperty @@>))

              p.AddXmlDocDelayed(fun () ->
                  $"This is StaticProperty{i} on NestedType")

              p
      ]

    staticPropsInNestedType)

  [nestedType])
```

### <a name="details-about-erased-provided-types"></a><span data-ttu-id="786be-213">指定された型が消去される場合の詳細</span><span class="sxs-lookup"><span data-stu-id="786be-213">Details about Erased Provided Types</span></span>

<span data-ttu-id="786be-214">このセクションの例では、 *指定された型の消去* のみを行います。これは、次のような場合に特に便利です。</span><span class="sxs-lookup"><span data-stu-id="786be-214">The example in this section provides only *erased provided types*, which are particularly useful in the following situations:</span></span>

- <span data-ttu-id="786be-215">データとメソッドのみを含む情報空間のプロバイダーを作成する場合。</span><span class="sxs-lookup"><span data-stu-id="786be-215">When you are writing a provider for an information space that contains only data and methods.</span></span>

- <span data-ttu-id="786be-216">情報空間の実用上、正確なランタイム型のセマンティクスが重要ではないプロバイダーを作成する場合。</span><span class="sxs-lookup"><span data-stu-id="786be-216">When you are writing a provider where accurate runtime-type semantics aren't critical for practical use of the information space.</span></span>

- <span data-ttu-id="786be-217">情報空間のプロバイダーを作成する際に、情報空間の規模が大きく相互接続していて、情報空間の .NET 型を実際に生成するのが技術的に不可能な場合。</span><span class="sxs-lookup"><span data-stu-id="786be-217">When you are writing a provider for an information space that is so large and interconnected that it isn’t technically feasible to generate real .NET types for the information space.</span></span>

<span data-ttu-id="786be-218">この例では、指定された型は消去されてそれぞれ型 `obj` に変換され、コンパイル済みコードではすべて型 `obj` で表されます。</span><span class="sxs-lookup"><span data-stu-id="786be-218">In this example, each provided type is erased to type `obj`, and all uses of the type will appear as type `obj` in compiled code.</span></span> <span data-ttu-id="786be-219">実際、次の例の基になるオブジェクトは文字列ですが、.NET コンパイル済みコードでは `System.Object` として表されます。</span><span class="sxs-lookup"><span data-stu-id="786be-219">In fact, the underlying objects in these examples are strings, but the type will appear as `System.Object` in .NET compiled code.</span></span> <span data-ttu-id="786be-220">使用されるすべての型消去に当てはまりますが、明示的なボックス化、ボックス化解除、およびキャストを使用すると消去型を無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="786be-220">As with all uses of type erasure, you can use explicit boxing, unboxing, and casting to subvert erased types.</span></span> <span data-ttu-id="786be-221">この場合、オブジェクトを使用したときに無効なキャスト例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="786be-221">In this case, a cast exception that isn’t valid may result when the object is used.</span></span> <span data-ttu-id="786be-222">プロバイダー ランタイムは間違った表現から保護するため独自のプライベート表現型を定義できます。</span><span class="sxs-lookup"><span data-stu-id="786be-222">A provider runtime can define its own private representation type to help protect against false representations.</span></span> <span data-ttu-id="786be-223">F# では消去型を定義できません。</span><span class="sxs-lookup"><span data-stu-id="786be-223">You can’t define erased types in F# itself.</span></span> <span data-ttu-id="786be-224">指定された型が消去される場合があるだけです。</span><span class="sxs-lookup"><span data-stu-id="786be-224">Only provided types may be erased.</span></span> <span data-ttu-id="786be-225">型プロバイダーで消去型を使用する場合、または消去型を指定するプロバイダーで消去型を使用する場合のいずれも、実際およびセマンティクスの両方の影響を理解しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="786be-225">You must understand the ramifications, both practical and semantic, of using either erased types for your type provider or a provider that provides erased types.</span></span> <span data-ttu-id="786be-226">消去型には実際の .NET 型はありません。</span><span class="sxs-lookup"><span data-stu-id="786be-226">An erased type has no real .NET type.</span></span> <span data-ttu-id="786be-227">したがって、型に対して正確なリフレクションを実行できず、厳密なランタイム型のセマンティクスに依存するランタイム キャストなどの手法を使用する場合は消去型が無効になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="786be-227">Therefore, you cannot do accurate reflection over the type, and you might subvert erased types if you use runtime casts and other techniques that rely on exact runtime type semantics.</span></span> <span data-ttu-id="786be-228">消去型の無効化により、多くの場合、実行時に型キャスト例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="786be-228">Subversion of erased types frequently results in type cast exceptions at runtime.</span></span>

### <a name="choosing-representations-for-erased-provided-types"></a><span data-ttu-id="786be-229">指定された型が消去される場合の表現の選択</span><span class="sxs-lookup"><span data-stu-id="786be-229">Choosing Representations for Erased Provided Types</span></span>

<span data-ttu-id="786be-230">指定された型の消去を使用する場合、表現が必須ではない場合があります。</span><span class="sxs-lookup"><span data-stu-id="786be-230">For some uses of erased provided types, no representation is required.</span></span> <span data-ttu-id="786be-231">たとえば、指定された型が消去される場合にその型には静的なプロパティとメンバーのみが含まれてコンストラクターは含まれない場合があり、メソッドもプロパティもその型のインスタンスを返しません。</span><span class="sxs-lookup"><span data-stu-id="786be-231">For example, the erased provided type might contain only static properties and members and no constructors, and no methods or properties would return an instance of the type.</span></span> <span data-ttu-id="786be-232">指定された型が消去される場合のインスタンスを取得できる場合は、次の事項を検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="786be-232">If you can reach instances of an erased provided type, you must consider the following questions:</span></span>

<span data-ttu-id="786be-233">**指定された型の消去はどのようなものか。**</span><span class="sxs-lookup"><span data-stu-id="786be-233">**What is the erasure of a provided type?**</span></span>

- <span data-ttu-id="786be-234">指定された型の消去は、コンパイル済みの .NET コードにおけるその型の表現である。</span><span class="sxs-lookup"><span data-stu-id="786be-234">The erasure of a provided type is how the type appears in compiled .NET code.</span></span>

- <span data-ttu-id="786be-235">指定された消去クラス型の消去は、常に型の継承チェーンにおける消去型でない最初の基本型である。</span><span class="sxs-lookup"><span data-stu-id="786be-235">The erasure of a provided erased class type is always the first non-erased base type in the inheritance chain of the type.</span></span>

- <span data-ttu-id="786be-236">指定された消去インターフェイス型の消去は、常に `System.Object` である。</span><span class="sxs-lookup"><span data-stu-id="786be-236">The erasure of a provided erased interface type is always `System.Object`.</span></span>

<span data-ttu-id="786be-237">**指定された型はどのように表現されるか。**</span><span class="sxs-lookup"><span data-stu-id="786be-237">**What are the representations of a provided type?**</span></span>

- <span data-ttu-id="786be-238">指定された型が消去される場合に使用可能なオブジェクトのセットがその表現として呼び出される。</span><span class="sxs-lookup"><span data-stu-id="786be-238">The set of possible objects for an erased provided type are called its representations.</span></span> <span data-ttu-id="786be-239">このドキュメントの例では、指定された型 `Type1..Type100` が消去される場合の表現はすべて、常に文字列オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="786be-239">In the example in this document, the representations of all the erased provided types `Type1..Type100` are always string objects.</span></span>

<span data-ttu-id="786be-240">指定された型の表現はすべて指定された型の消去と互換性がある必要があります </span><span class="sxs-lookup"><span data-stu-id="786be-240">All representations of a provided type must be compatible with the erasure of the provided type.</span></span> <span data-ttu-id="786be-241">(互換性がない場合、F# コンパイラがその型プロバイダーの使用に対してエラーを生成するか、または検証不可能で無効な .NET コードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="786be-241">(Otherwise, either the F# compiler will give an error for a use of the type provider, or unverifiable .NET code that isn't valid will be generated.</span></span> <span data-ttu-id="786be-242">有効ではない表現を指定するコードを返す型プロバイダーは無効です)。</span><span class="sxs-lookup"><span data-stu-id="786be-242">A type provider isn’t valid if it returns code that gives a  representation that isn't valid.)</span></span>

<span data-ttu-id="786be-243">次のアプローチのどちらかを使って指定されたオブジェクトの表現を選択できます。どちらもよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="786be-243">You can choose a representation for provided objects by using either of the following approaches, both of which are very common:</span></span>

- <span data-ttu-id="786be-244">既存の .NET 型に対して厳密に型指定されたラッパーを指定するだけであれば、多くの場合、使用する型を消去してその型に変換し、その型のインスタンスを表現として使用するのが理にかなっています。</span><span class="sxs-lookup"><span data-stu-id="786be-244">If you're simply providing a strongly typed wrapper over an existing .NET type, it often makes sense for your type to erase to that type, use instances of that type as representations, or both.</span></span> <span data-ttu-id="786be-245">このアプローチは、厳密に型指定されたバージョンを使用するとき、その型の既存のメソッドのほとんどをそのまま使用できる場合に適しています。</span><span class="sxs-lookup"><span data-stu-id="786be-245">This approach is appropriate when most of the existing methods on that type still make sense when using the strongly typed version.</span></span>

- <span data-ttu-id="786be-246">既存の .NET API とは大きく異なる API を作成する場合は、指定された型の型消去および表現となるランタイム型を作成するのが理にかなっています。</span><span class="sxs-lookup"><span data-stu-id="786be-246">If you want to create an API that differs significantly from any existing .NET API, it makes sense to create runtime types that will be the type erasure and representations for the provided types.</span></span>

<span data-ttu-id="786be-247">このドキュメントの例では、指定されたオブジェクトの表現として文字列を使用します。</span><span class="sxs-lookup"><span data-stu-id="786be-247">The example in this document uses strings as representations of provided objects.</span></span> <span data-ttu-id="786be-248">しばしば、表現に他のオブジェクトを使用する方が適切な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="786be-248">Frequently, it may be appropriate to use other objects for representations.</span></span> <span data-ttu-id="786be-249">たとえば、プロパティ バッグとしてディクショナリを使用できます。</span><span class="sxs-lookup"><span data-stu-id="786be-249">For example, you may use a dictionary as a property bag:</span></span>

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new Dictionary<string,obj>()) :> obj @@>))
```

<span data-ttu-id="786be-250">もう 1 つの方法として、型プロバイダーで、1 つ以上のランタイム操作と共に表現を形成するために実行時に使用される型を定義できます。</span><span class="sxs-lookup"><span data-stu-id="786be-250">As an alternative, you may define a type in your type provider that will be used at runtime to form the representation, along with one or more runtime operations:</span></span>

```fsharp
type DataObject() =
    let data = Dictionary<string,obj>()
    member x.RuntimeOperation() = data.Count
```

<span data-ttu-id="786be-251">指定されたメンバーはこのオブジェクト型のインスタンスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="786be-251">Provided members can then construct instances of this object type:</span></span>

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new DataObject()) :> obj @@>))
```

<span data-ttu-id="786be-252">この場合、必要に応じて、`baseType` を作成するときにこの型を `ProvidedTypeDefinition` として指定することによって、この型を型消去として使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="786be-252">In this case, you may (optionally) use this type as the type erasure by specifying this type as the `baseType` when constructing the `ProvidedTypeDefinition`:</span></span>

```fsharp
ProvidedTypeDefinition(…, baseType = Some typeof<DataObject> )
…
ProvidedConstructor(…, InvokeCode = (fun args -> <@@ new DataObject() @@>), …)
```

### <a name="key-lessons"></a><span data-ttu-id="786be-253">レッスンの要点</span><span class="sxs-lookup"><span data-stu-id="786be-253">Key Lessons</span></span>

<span data-ttu-id="786be-254">前のセクションでは、一連の型、プロパティ、およびメソッドを指定する、消去の単純な型プロバイダーの作成方法を説明しました。</span><span class="sxs-lookup"><span data-stu-id="786be-254">The previous section explained how to create a simple erasing type provider that provides a range of types, properties, and methods.</span></span> <span data-ttu-id="786be-255">また、型プロバイダーから消去型を指定することの長所と短所を含む型消去の概念について、および消去型の表現についても説明しました。</span><span class="sxs-lookup"><span data-stu-id="786be-255">This section also explained the concept of type erasure, including some of the advantages and disadvantages of providing erased types from a type provider, and discussed representations of erased types.</span></span>

## <a name="a-type-provider-that-uses-static-parameters"></a><span data-ttu-id="786be-256">静的パラメーターを使用する型プロバイダー</span><span class="sxs-lookup"><span data-stu-id="786be-256">A Type Provider That Uses Static Parameters</span></span>

<span data-ttu-id="786be-257">静的データによって型プロバイダーをパラメーター化できると、プロバイダーがローカルまたはリモート データにアクセスする必要がないような、多くの興味深いシナリオが可能になります。</span><span class="sxs-lookup"><span data-stu-id="786be-257">The ability to parameterize type providers by static data enables many interesting scenarios, even in cases when the provider doesn't need to access any local or remote data.</span></span> <span data-ttu-id="786be-258">このセクションでは、このようなプロバイダーを用意するための基本的な手法について説明します。</span><span class="sxs-lookup"><span data-stu-id="786be-258">In this section, you’ll learn some basic techniques for putting together such a provider.</span></span>

### <a name="type-checked-regex-provider"></a><span data-ttu-id="786be-259">型チェック済み Regex プロバイダー</span><span class="sxs-lookup"><span data-stu-id="786be-259">Type Checked Regex Provider</span></span>

<span data-ttu-id="786be-260">.NET <xref:System.Text.RegularExpressions.Regex> ライブラリをラップする正規表現の型プロバイダーを、次のコンパイル時保証を提供するインターフェイスに実装するとしたらどうでしょう。</span><span class="sxs-lookup"><span data-stu-id="786be-260">Imagine that you want to implement a type provider for regular expressions that wraps the .NET <xref:System.Text.RegularExpressions.Regex> libraries in an interface that provides the following compile-time guarantees:</span></span>

- <span data-ttu-id="786be-261">正規表現が有効かどうかを確認できる。</span><span class="sxs-lookup"><span data-stu-id="786be-261">Verifying whether a regular expression is valid.</span></span>

- <span data-ttu-id="786be-262">パターンが一致したとき、正規表現内のグループ名に基づいて名前付きプロパティを提供できる。</span><span class="sxs-lookup"><span data-stu-id="786be-262">Providing named properties on matches that are based on any group names in the regular expression.</span></span>

<span data-ttu-id="786be-263">このセクションでは、これらの利点が実現するように正規表現パターンによってパラメーター化される `RegexTyped` 型を作成するための型プロバイダーを使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="786be-263">This section shows you how to use type providers to create a `RegexTyped` type that the regular expression pattern parameterizes to provide these benefits.</span></span> <span data-ttu-id="786be-264">コンパイラは、提供されたパターンが有効でない場合にエラーを報告しますが、型プロバイダーはパターンからグループを抽出できるので、パターンが一致したとき名前付きプロパティを使用してグループにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="786be-264">The compiler will report an error if the supplied pattern isn't valid, and the type provider can extract the groups from the pattern so that you can access them by using named properties on matches.</span></span> <span data-ttu-id="786be-265">型プロバイダーを設計するとき、公開された API がエンド ユーザーにどのように表示される必要があるか、そのデザインが .NET コードにどのように変換されるかを考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="786be-265">When you design a type provider, you should consider how its exposed API should look to end users and how this design will translate to .NET code.</span></span> <span data-ttu-id="786be-266">次の例は、市外局番のコンポーネントを取得するために、このような API を使用する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="786be-266">The following example shows how to use such an API to get the components of the area code:</span></span>

```fsharp
type T = RegexTyped< @"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)">
let reg = T()
let result = T.IsMatch("425-555-2345")
let r = reg.Match("425-555-2345").Group_AreaCode.Value //r equals "425"
```

<span data-ttu-id="786be-267">型プロバイダーがこれらの呼び出しをどのように変換するかを次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="786be-267">The following example shows how the type provider translates these calls:</span></span>

```fsharp
let reg = new Regex(@"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)")
let result = reg.IsMatch("425-123-2345")
let r = reg.Match("425-123-2345").Groups.["AreaCode"].Value //r equals "425"
```

<span data-ttu-id="786be-268">以下の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="786be-268">Note the following points:</span></span>

- <span data-ttu-id="786be-269">標準 Regex 型は、パラメーター化された `RegexTyped` 型を表します。</span><span class="sxs-lookup"><span data-stu-id="786be-269">The standard Regex type represents the parameterized `RegexTyped` type.</span></span>

- <span data-ttu-id="786be-270">`RegexTyped` コンストラクターは、Regex コンストラクターを呼び出し、パターンの静的な型引数を渡します。</span><span class="sxs-lookup"><span data-stu-id="786be-270">The `RegexTyped` constructor results in a call to the Regex constructor, passing in the static type argument for the pattern.</span></span>

- <span data-ttu-id="786be-271">`Match` メソッドの結果は、標準の <xref:System.Text.RegularExpressions.Match> 型で表されます。</span><span class="sxs-lookup"><span data-stu-id="786be-271">The results of the `Match` method are represented by the standard <xref:System.Text.RegularExpressions.Match> type.</span></span>

- <span data-ttu-id="786be-272">各名前付きグループは指定されたプロパティになり、プロパティにアクセスすると、パターン一致の `Groups` コレクションでインデクサーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="786be-272">Each named group results in a provided property, and accessing the property results in a use of an indexer on a match’s `Groups` collection.</span></span>

<span data-ttu-id="786be-273">次のコードはこのようなプロバイダーの実装におけるコア ロジックです。この例では指定された型へのすべてのメンバーの追加は省略されています。</span><span class="sxs-lookup"><span data-stu-id="786be-273">The following code is the core of the logic to implement such a provider, and this example omits the addition of all members to the provided type.</span></span> <span data-ttu-id="786be-274">それぞれの追加されたメンバーについては、このトピックの後半の該当するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="786be-274">For information about each added member, see the appropriate section later in this topic.</span></span> <span data-ttu-id="786be-275">完全なコードについては、CodePlex web サイトの [F # 3.0 サンプルパック](https://archive.codeplex.com/?p=fsharp3sample) からサンプルをダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="786be-275">For the full code, download the sample from the [F# 3.0 Sample Pack](https://archive.codeplex.com/?p=fsharp3sample) on the CodePlex website.</span></span>

```fsharp
namespace Samples.FSharp.RegexTypeProvider

open System.Reflection
open Microsoft.FSharp.Core.CompilerServices
open Samples.FSharp.ProvidedTypes
open System.Text.RegularExpressions

[<TypeProvider>]
type public CheckedRegexProvider() as this =
    inherit TypeProviderForNamespaces()

    // Get the assembly and namespace used to house the provided types
    let thisAssembly = Assembly.GetExecutingAssembly()
    let rootNamespace = "Samples.FSharp.RegexTypeProvider"
    let baseTy = typeof<obj>
    let staticParams = [ProvidedStaticParameter("pattern", typeof<string>)]

    let regexTy = ProvidedTypeDefinition(thisAssembly, rootNamespace, "RegexTyped", Some baseTy)

    do regexTy.DefineStaticParameters(
        parameters=staticParams,
        instantiationFunction=(fun typeName parameterValues ->

          match parameterValues with
          | [| :? string as pattern|] ->

            // Create an instance of the regular expression.
            //
            // This will fail with System.ArgumentException if the regular expression is not valid.
            // The exception will escape the type provider and be reported in client code.
            let r = System.Text.RegularExpressions.Regex(pattern)

            // Declare the typed regex provided type.
            // The type erasure of this type is 'obj', even though the representation will always be a Regex
            // This, combined with hiding the object methods, makes the IntelliSense experience simpler.
            let ty =
              ProvidedTypeDefinition(
                thisAssembly,
                rootNamespace,
                typeName,
                baseType = Some baseTy)

            ...

            ty
          | _ -> failwith "unexpected parameter values"))

    do this.AddNamespace(rootNamespace, [regexTy])

[<TypeProviderAssembly>]
do ()
```

<span data-ttu-id="786be-276">以下の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="786be-276">Note the following points:</span></span>

- <span data-ttu-id="786be-277">型プロバイダーは、`pattern` (必須) と `options` (既定値が指定されるので省略可能) の 2 つの静的パラメーターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="786be-277">The type provider takes two static parameters: the `pattern`, which is mandatory, and the `options`, which are optional (because a default value is provided).</span></span>

- <span data-ttu-id="786be-278">静的引数が提供された後、正規表現のインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="786be-278">After the static arguments are supplied, you create an instance of the regular expression.</span></span> <span data-ttu-id="786be-279">Regex が正しくない場合、このインスタンスは例外をスローし、このエラーはユーザーに報告されます。</span><span class="sxs-lookup"><span data-stu-id="786be-279">This instance will throw an exception if the Regex is malformed, and this error will be reported to users.</span></span>

- <span data-ttu-id="786be-280">`DefineStaticParameters` コールバック内では、引数が提供された後に返される型を定義します。</span><span class="sxs-lookup"><span data-stu-id="786be-280">Within the `DefineStaticParameters` callback, you define the type that will be returned after the arguments are supplied.</span></span>

- <span data-ttu-id="786be-281">IntelliSense による効率化が損なわれないように、このコードは `HideObjectMethods` を true に設定します。</span><span class="sxs-lookup"><span data-stu-id="786be-281">This code sets `HideObjectMethods` to true so that the IntelliSense experience will remain streamlined.</span></span> <span data-ttu-id="786be-282">この属性により、`Equals`、`GetHashCode`、`Finalize`、`GetType` の各メンバーが指定されたオブジェクトの IntelliSense リストで抑制されます。</span><span class="sxs-lookup"><span data-stu-id="786be-282">This attribute causes the `Equals`, `GetHashCode`, `Finalize`, and `GetType` members to be suppressed from IntelliSense lists for a provided object.</span></span>

- <span data-ttu-id="786be-283">`obj` をそのメソッドの基本型として使用しますが、この型のランタイム表現には `Regex` オブジェクトを使用します。次にその例を示します。</span><span class="sxs-lookup"><span data-stu-id="786be-283">You use `obj` as the base type of the method, but you’ll use a `Regex` object as the runtime representation of this type, as the next example shows.</span></span>

- <span data-ttu-id="786be-284">正規表現が有効でない場合、`Regex` コンストラクターを呼び出すと <xref:System.ArgumentException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="786be-284">The call to the `Regex` constructor throws a <xref:System.ArgumentException> when a regular expression isn’t valid.</span></span> <span data-ttu-id="786be-285">コンパイラはこの例外をキャッチし、コンパイル時、または Visual Studio のエディターでエラー メッセージを表示します。</span><span class="sxs-lookup"><span data-stu-id="786be-285">The compiler catches this exception and reports an error message to the user at compile time or in the Visual Studio editor.</span></span> <span data-ttu-id="786be-286">この例外によって、アプリケーションを実行せずに正規表現が有効かどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="786be-286">This exception enables regular expressions to be validated without running an application.</span></span>

<span data-ttu-id="786be-287">前に定義した型は、まだ意味のあるメソッドまたはプロパティを含んでいないので、有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="786be-287">The type defined above isn't useful yet because it doesn’t contain any meaningful methods or properties.</span></span> <span data-ttu-id="786be-288">最初に、静的な `IsMatch` メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="786be-288">First, add a static `IsMatch` method:</span></span>

```fsharp
let isMatch =
    ProvidedMethod(
        methodName = "IsMatch",
        parameters = [ProvidedParameter("input", typeof<string>)],
        returnType = typeof<bool>,
        isStatic = true,
        invokeCode = fun args -> <@@ Regex.IsMatch(%%args.[0], pattern) @@>)

isMatch.AddXmlDoc "Indicates whether the regular expression finds a match in the specified input string."
ty.AddMember isMatch
```

<span data-ttu-id="786be-289">このコードは、文字列を入力として受け取り `IsMatch` を返す `bool` メソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="786be-289">The previous code defines a method `IsMatch`, which takes a string as input and returns a `bool`.</span></span> <span data-ttu-id="786be-290">唯一わかりにくい部分は、`args` 定義内の `InvokeCode` 引数の使用です。</span><span class="sxs-lookup"><span data-stu-id="786be-290">The only tricky part is the use of the `args` argument within the `InvokeCode` definition.</span></span> <span data-ttu-id="786be-291">この例では、`args` はこのメソッドの引数を表すクォートのリストです。</span><span class="sxs-lookup"><span data-stu-id="786be-291">In this example, `args` is a list of quotations that represents the arguments to this method.</span></span> <span data-ttu-id="786be-292">メソッドがインスタンス メソッドの場合、最初の引数が `this` 引数を表します。</span><span class="sxs-lookup"><span data-stu-id="786be-292">If the method is an instance method, the first argument represents the `this` argument.</span></span> <span data-ttu-id="786be-293">ただし、静的メソッドでは、引数はすべて、メソッドの明示的な引数でしかありません。</span><span class="sxs-lookup"><span data-stu-id="786be-293">However, for a static method, the arguments are all just the explicit arguments to the method.</span></span> <span data-ttu-id="786be-294">クォート値の型は指定された戻り値の型 (この場合は `bool`) に一致していることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="786be-294">Note that the type of the quoted value should match the specified return type (in this case, `bool`).</span></span> <span data-ttu-id="786be-295">また、このコードでは、指定されたメソッドも IntelliSense によって提供できる有用なドキュメントを持つように `AddXmlDoc` メソッドが使用されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="786be-295">Also note that this code uses the `AddXmlDoc` method to make sure that the provided method also has useful documentation, which you can supply through IntelliSense.</span></span>

<span data-ttu-id="786be-296">次に、インスタンスの Match メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="786be-296">Next, add an instance Match method.</span></span> <span data-ttu-id="786be-297">ただし、厳密に型指定された方法でグループにアクセスできるように、このメソッドは指定された型 `Match` の値を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="786be-297">However, this method should return a value of a provided `Match` type so that the groups can be accessed in a strongly typed fashion.</span></span> <span data-ttu-id="786be-298">したがって、最初に `Match` 型を宣言します。</span><span class="sxs-lookup"><span data-stu-id="786be-298">Thus, you first declare the `Match` type.</span></span> <span data-ttu-id="786be-299">この型は静的引数として提供されたパターンに依存するため、パラメーター化された型定義内に入れ子にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="786be-299">Because this type depends on the pattern that was supplied as a static argument, this type must be nested within the parameterized type definition:</span></span>

```fsharp
let matchTy =
    ProvidedTypeDefinition(
        "MatchType",
        baseType = Some baseTy,
        hideObjectMethods = true)

ty.AddMember matchTy
```

<span data-ttu-id="786be-300">次に、各グループの Match 型にプロパティを 1 つ追加します。</span><span class="sxs-lookup"><span data-stu-id="786be-300">You then add one property to the Match type for each group.</span></span> <span data-ttu-id="786be-301">実行時には、一致は <xref:System.Text.RegularExpressions.Match> 値として表されるので、そのプロパティを定義するクォートはインデックス付きの <xref:System.Text.RegularExpressions.Match.Groups> プロパティを使用して適切なグループを取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="786be-301">At runtime, a match is represented as a <xref:System.Text.RegularExpressions.Match> value, so the quotation that defines the property must use the <xref:System.Text.RegularExpressions.Match.Groups> indexed property to get the relevant group.</span></span>

```fsharp
for group in r.GetGroupNames() do
    // Ignore the group named 0, which represents all input.
    if group <> "0" then
    let prop =
      ProvidedProperty(
        propertyName = group,
        propertyType = typeof<Group>,
        getterCode = fun args -> <@@ ((%%args.[0]:obj) :?> Match).Groups.[group] @@>)
        prop.AddXmlDoc($"""Gets the ""{group}"" group from this match""")
    matchTy.AddMember prop
```

<span data-ttu-id="786be-302">ここでも指定されたプロパティに XML ドキュメントを追加していることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="786be-302">Again, note that you’re adding XML documentation to the provided property.</span></span> <span data-ttu-id="786be-303">`GetterCode` 関数が指定されている場合はプロパティを読み取ることができ、`SetterCode` 関数が指定されている場合はプロパティを書き出すことができるので、その結果、プロパティは読み取り専用になることにも注意してください。</span><span class="sxs-lookup"><span data-stu-id="786be-303">Also note that a property can be read if a `GetterCode` function is provided, and the property can be written if a `SetterCode` function is provided, so the resulting property is read only.</span></span>

<span data-ttu-id="786be-304">これで、この `Match` 型の値を返すインスタンス メソッドを作成できます。</span><span class="sxs-lookup"><span data-stu-id="786be-304">Now you can create an instance method that returns a value of this `Match` type:</span></span>

```fsharp
let matchMethod =
    ProvidedMethod(
        methodName = "Match",
        parameters = [ProvidedParameter("input", typeof<string>)],
        returnType = matchTy,
        invokeCode = fun args -> <@@ ((%%args.[0]:obj) :?> Regex).Match(%%args.[1]) :> obj @@>)

matchMeth.AddXmlDoc "Searches the specified input string for the first occurrence of this regular expression"

ty.AddMember matchMeth
```

<span data-ttu-id="786be-305">インスタンス メソッドを作成しているので、`args.[0]` はそのメソッドが呼び出される `RegexTyped` インスタンスを表し、`args.[1]` は入力引数を表します。</span><span class="sxs-lookup"><span data-stu-id="786be-305">Because you are creating an instance method, `args.[0]` represents the `RegexTyped` instance on which the method is being called, and `args.[1]` is the input argument.</span></span>

<span data-ttu-id="786be-306">最後に、指定された型のインスタンスを作成できるように、コンストラクターを指定します。</span><span class="sxs-lookup"><span data-stu-id="786be-306">Finally, provide a constructor so that instances of the provided type can be created.</span></span>

```fsharp
let ctor =
    ProvidedConstructor(
        parameters = [],
        invokeCode = fun args -> <@@ Regex(pattern, options) :> obj @@>)

ctor.AddXmlDoc("Initializes a regular expression instance.")

ty.AddMember ctor
```

<span data-ttu-id="786be-307">このコンストラクターは単に消去して標準の .NET Regex インスタンスの作成に変換します。`obj` は指定された型の消去なので、このインスタンスもまたオブジェクトにボックス化されます。</span><span class="sxs-lookup"><span data-stu-id="786be-307">The constructor merely erases to the creation of a standard .NET Regex instance, which is again boxed to an object because `obj` is the erasure of the provided type.</span></span> <span data-ttu-id="786be-308">この変更によって、トピックの前半で示した API の使用例は期待どおりに機能します。</span><span class="sxs-lookup"><span data-stu-id="786be-308">With that change, the sample API usage that specified earlier in the topic works as expected.</span></span> <span data-ttu-id="786be-309">次に最終的に完成したコードを示します。</span><span class="sxs-lookup"><span data-stu-id="786be-309">The following code is complete and final:</span></span>

```fsharp
namespace Samples.FSharp.RegexTypeProvider

open System.Reflection
open Microsoft.FSharp.Core.CompilerServices
open Samples.FSharp.ProvidedTypes
open System.Text.RegularExpressions

[<TypeProvider>]
type public CheckedRegexProvider() as this =
    inherit TypeProviderForNamespaces()

    // Get the assembly and namespace used to house the provided types.
    let thisAssembly = Assembly.GetExecutingAssembly()
    let rootNamespace = "Samples.FSharp.RegexTypeProvider"
    let baseTy = typeof<obj>
    let staticParams = [ProvidedStaticParameter("pattern", typeof<string>)]

    let regexTy = ProvidedTypeDefinition(thisAssembly, rootNamespace, "RegexTyped", Some baseTy)

    do regexTy.DefineStaticParameters(
        parameters=staticParams,
        instantiationFunction=(fun typeName parameterValues ->

            match parameterValues with
            | [| :? string as pattern|] ->

                // Create an instance of the regular expression.

                let r = System.Text.RegularExpressions.Regex(pattern)

                // Declare the typed regex provided type.

                let ty =
                    ProvidedTypeDefinition(
                        thisAssembly,
                        rootNamespace,
                        typeName,
                        baseType = Some baseTy)

                ty.AddXmlDoc "A strongly typed interface to the regular expression '%s'"

                // Provide strongly typed version of Regex.IsMatch static method.
                let isMatch =
                    ProvidedMethod(
                        methodName = "IsMatch",
                        parameters = [ProvidedParameter("input", typeof<string>)],
                        returnType = typeof<bool>,
                        isStatic = true,
                        invokeCode = fun args -> <@@ Regex.IsMatch(%%args.[0], pattern) @@>)

                isMatch.AddXmlDoc "Indicates whether the regular expression finds a match in the specified input string"

                ty.AddMember isMatch

                // Provided type for matches
                // Again, erase to obj even though the representation will always be a Match
                let matchTy =
                    ProvidedTypeDefinition(
                        "MatchType",
                        baseType = Some baseTy,
                        hideObjectMethods = true)

                // Nest the match type within parameterized Regex type.
                ty.AddMember matchTy

                // Add group properties to match type
                for group in r.GetGroupNames() do
                    // Ignore the group named 0, which represents all input.
                    if group <> "0" then
                        let prop =
                          ProvidedProperty(
                            propertyName = group,
                            propertyType = typeof<Group>,
                            getterCode = fun args -> <@@ ((%%args.[0]:obj) :?> Match).Groups.[group] @@>)
                        prop.AddXmlDoc(sprintf @"Gets the ""%s"" group from this match" group)
                        matchTy.AddMember(prop)

                // Provide strongly typed version of Regex.Match instance method.
                let matchMeth =
                  ProvidedMethod(
                    methodName = "Match",
                    parameters = [ProvidedParameter("input", typeof<string>)],
                    returnType = matchTy,
                    invokeCode = fun args -> <@@ ((%%args.[0]:obj) :?> Regex).Match(%%args.[1]) :> obj @@>)
                matchMeth.AddXmlDoc "Searches the specified input string for the first occurrence of this regular expression"

                ty.AddMember matchMeth

                // Declare a constructor.
                let ctor =
                  ProvidedConstructor(
                    parameters = [],
                    invokeCode = fun args -> <@@ Regex(pattern) :> obj @@>)

                // Add documentation to the constructor.
                ctor.AddXmlDoc "Initializes a regular expression instance"

                ty.AddMember ctor

                ty
            | _ -> failwith "unexpected parameter values"))

    do this.AddNamespace(rootNamespace, [regexTy])

[<TypeProviderAssembly>]
do ()
```

### <a name="key-lessons"></a><span data-ttu-id="786be-310">レッスンの要点</span><span class="sxs-lookup"><span data-stu-id="786be-310">Key Lessons</span></span>

<span data-ttu-id="786be-311">このセクションでは静的パラメーターを操作する型プロバイダーを作成する方法を説明しました。</span><span class="sxs-lookup"><span data-stu-id="786be-311">This section explained how to create a type provider that operates on its static parameters.</span></span> <span data-ttu-id="786be-312">プロバイダーは、静的パラメーターをチェックし、その値に基づいて操作を指定します。</span><span class="sxs-lookup"><span data-stu-id="786be-312">The provider checks the static parameter and provides operations based on its value.</span></span>

## <a name="a-type-provider-that-is-backed-by-local-data"></a><span data-ttu-id="786be-313">ローカル データに基づく型プロバイダー</span><span class="sxs-lookup"><span data-stu-id="786be-313">A Type Provider That Is Backed By Local Data</span></span>

<span data-ttu-id="786be-314">しばしば、静的パラメーターだけでなくローカルまたはリモート システムからの情報にも基づく API を提供する型プロバイダーが便利な場合があります。</span><span class="sxs-lookup"><span data-stu-id="786be-314">Frequently you might want type providers to present APIs based on not only static parameters but also information from local or remote systems.</span></span> <span data-ttu-id="786be-315">このセクションでは、ローカル データ ファイルなどのローカル データに基づく型プロバイダーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="786be-315">This section discusses type providers that are based on local data, such as local data files.</span></span>

### <a name="simple-csv-file-provider"></a><span data-ttu-id="786be-316">単純な CSV ファイル プロバイダー</span><span class="sxs-lookup"><span data-stu-id="786be-316">Simple CSV File Provider</span></span>

<span data-ttu-id="786be-317">単純な例として、コンマ区切り値 (CSV) 形式の指数データにアクセスするための型プロバイダーを考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="786be-317">As a simple example, consider a type provider for accessing scientific data in Comma Separated Value (CSV) format.</span></span> <span data-ttu-id="786be-318">ここでは、次の表に示すように、CSV ファイルにはヘッダー行があり、その後に浮動小数点型のデータが続いているとします。</span><span class="sxs-lookup"><span data-stu-id="786be-318">This section assumes that the CSV files contain a header row followed by floating point data, as the following table illustrates:</span></span>

|<span data-ttu-id="786be-319">距離 (メートル)</span><span class="sxs-lookup"><span data-stu-id="786be-319">Distance (meter)</span></span>|<span data-ttu-id="786be-320">時間 (秒)</span><span class="sxs-lookup"><span data-stu-id="786be-320">Time (second)</span></span>|
|----------------|-------------|
|<span data-ttu-id="786be-321">50.0</span><span class="sxs-lookup"><span data-stu-id="786be-321">50.0</span></span>|<span data-ttu-id="786be-322">3.7</span><span class="sxs-lookup"><span data-stu-id="786be-322">3.7</span></span>|
|<span data-ttu-id="786be-323">100.0</span><span class="sxs-lookup"><span data-stu-id="786be-323">100.0</span></span>|<span data-ttu-id="786be-324">5.2</span><span class="sxs-lookup"><span data-stu-id="786be-324">5.2</span></span>|
|<span data-ttu-id="786be-325">150.0</span><span class="sxs-lookup"><span data-stu-id="786be-325">150.0</span></span>|<span data-ttu-id="786be-326">6.4</span><span class="sxs-lookup"><span data-stu-id="786be-326">6.4</span></span>|

<span data-ttu-id="786be-327">ここでは、`Distance` 型の `float<meter>` プロパティと `Time` 型の `float<second>` プロパティの行を取得するために使用できる型を指定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="786be-327">This section shows how to provide a type that you can use to get rows with a `Distance` property of type `float<meter>` and a `Time` property of type `float<second>`.</span></span> <span data-ttu-id="786be-328">説明を簡単にするために、次のように仮定します。</span><span class="sxs-lookup"><span data-stu-id="786be-328">For simplicity, the following assumptions are made:</span></span>

- <span data-ttu-id="786be-329">ヘッダー名の形式は、"名前 (単位)" または "名前 (単位)" で、コンマは使用できません。</span><span class="sxs-lookup"><span data-stu-id="786be-329">Header names are either unit-less or have the form "Name (unit)" and don't contain commas.</span></span>

- <span data-ttu-id="786be-330">単位は、 [Fsharp.core モジュール (F #)](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-data-unitsystems-si-unitnames.html) モジュールで定義されているすべてのシステムインターナショナル (si) 単位です。</span><span class="sxs-lookup"><span data-stu-id="786be-330">Units are all System International (SI) units as the [FSharp.Data.UnitSystems.SI.UnitNames Module (F#)](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-data-unitsystems-si-unitnames.html) module defines.</span></span>

- <span data-ttu-id="786be-331">単位はすべて単純な単位 (たとえば、メートル) で、複合単位 (メートル/秒など) ではありません。</span><span class="sxs-lookup"><span data-stu-id="786be-331">Units are all simple (for example, meter) rather than compound (for example, meter/second).</span></span>

- <span data-ttu-id="786be-332">すべての列に浮動小数点データが含まれています。</span><span class="sxs-lookup"><span data-stu-id="786be-332">All columns contain floating point data.</span></span>

<span data-ttu-id="786be-333">より詳細なプロバイダーを使用すると、これらの制限は緩和されます。</span><span class="sxs-lookup"><span data-stu-id="786be-333">A more complete provider would loosen these restrictions.</span></span>

<span data-ttu-id="786be-334">ここでも、最初の手順は API がどのように表示されるかを検討することです。</span><span class="sxs-lookup"><span data-stu-id="786be-334">Again the first step is to consider how the API should look.</span></span> <span data-ttu-id="786be-335">前の表の内容を含む `info.csv` ファイル (コンマ区切り形式) の場合、プロバイダーを使用して次の例のようなコードを作成できます。</span><span class="sxs-lookup"><span data-stu-id="786be-335">Given an `info.csv` file with the contents from the previous table (in comma-separated format), users of the provider should be able to write code that resembles the following example:</span></span>

```fsharp
let info = new MiniCsv<"info.csv">()
for row in info.Data do
let time = row.Time
printfn $"{float time}"
```

<span data-ttu-id="786be-336">この場合、コンパイラはこれらの呼び出しを次の例のように変換します。</span><span class="sxs-lookup"><span data-stu-id="786be-336">In this case, the compiler should convert these calls into something like the following example:</span></span>

```fsharp
let info = new CsvFile("info.csv")
for row in info.Data do
let (time:float) = row.[1]
printfn $"%f{float time}"
```

<span data-ttu-id="786be-337">最適な変換を行うには、型プロバイダーのアセンブリで実際の `CsvFile` 型を定義する型プロバイダーが必要です。</span><span class="sxs-lookup"><span data-stu-id="786be-337">The optimal translation will require the type provider to define a real `CsvFile` type in the type provider's assembly.</span></span> <span data-ttu-id="786be-338">型プロバイダーは、多くの場合、重要なロジックをラップするためにいくつかのヘルパー型とメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="786be-338">Type providers often rely on a few helper types and methods to wrap important logic.</span></span> <span data-ttu-id="786be-339">メジャーは実行時に消去されるので、行の消去型として `float[]` を使用できます。</span><span class="sxs-lookup"><span data-stu-id="786be-339">Because measures are erased at runtime, you can use a `float[]` as the erased type for a row.</span></span> <span data-ttu-id="786be-340">コンパイラでは、異なる列は異なるメジャー型を持つと見なして処理します。</span><span class="sxs-lookup"><span data-stu-id="786be-340">The compiler will treat different columns as having different measure types.</span></span> <span data-ttu-id="786be-341">たとえば、この例の最初の列は `float<meter>` 型、2 番目の列は `float<second>` 型を持ちます。</span><span class="sxs-lookup"><span data-stu-id="786be-341">For example, the first column in our example has type `float<meter>`, and the second has `float<second>`.</span></span> <span data-ttu-id="786be-342">ただし、消去された表現は非常に単純です。</span><span class="sxs-lookup"><span data-stu-id="786be-342">However, the erased representation can remain quite simple.</span></span>

<span data-ttu-id="786be-343">次のコードはその実装のコアを示します。</span><span class="sxs-lookup"><span data-stu-id="786be-343">The following code shows the core of the implementation.</span></span>

```fsharp
// Simple type wrapping CSV data
type CsvFile(filename) =
    // Cache the sequence of all data lines (all lines but the first)
    let data =
        seq {
            for line in File.ReadAllLines(filename) |> Seq.skip 1 ->
                line.Split(',') |> Array.map float
        }
        |> Seq.cache
    member _.Data = data

[<TypeProvider>]
type public MiniCsvProvider(cfg:TypeProviderConfig) as this =
    inherit TypeProviderForNamespaces(cfg)

    // Get the assembly and namespace used to house the provided types.
    let asm = System.Reflection.Assembly.GetExecutingAssembly()
    let ns = "Samples.FSharp.MiniCsvProvider"

    // Create the main provided type.
    let csvTy = ProvidedTypeDefinition(asm, ns, "MiniCsv", Some(typeof<obj>))

    // Parameterize the type by the file to use as a template.
    let filename = ProvidedStaticParameter("filename", typeof<string>)
    do csvTy.DefineStaticParameters([filename], fun tyName [| :? string as filename |] ->

        // Resolve the filename relative to the resolution folder.
        let resolvedFilename = Path.Combine(cfg.ResolutionFolder, filename)

        // Get the first line from the file.
        let headerLine = File.ReadLines(resolvedFilename) |> Seq.head

        // Define a provided type for each row, erasing to a float[].
        let rowTy = ProvidedTypeDefinition("Row", Some(typeof<float[]>))

        // Extract header names from the file, splitting on commas.
        // use Regex matching to get the position in the row at which the field occurs
        let headers = Regex.Matches(headerLine, "[^,]+")

        // Add one property per CSV field.
        for i in 0 .. headers.Count - 1 do
            let headerText = headers.[i].Value

            // Try to decompose this header into a name and unit.
            let fieldName, fieldTy =
                let m = Regex.Match(headerText, @"(?<field>.+) \((?<unit>.+)\)")
                if m.Success then

                    let unitName = m.Groups.["unit"].Value
                    let units = ProvidedMeasureBuilder.Default.SI unitName
                    m.Groups.["field"].Value, ProvidedMeasureBuilder.Default.AnnotateType(typeof<float>,[units])

                else
                    // no units, just treat it as a normal float
                    headerText, typeof<float>

            let prop =
                ProvidedProperty(fieldName, fieldTy,
                    getterCode = fun [row] -> <@@ (%%row:float[]).[i] @@>)

            // Add metadata that defines the property's location in the referenced file.
            prop.AddDefinitionLocation(1, headers.[i].Index + 1, filename)
            rowTy.AddMember(prop)

        // Define the provided type, erasing to CsvFile.
        let ty = ProvidedTypeDefinition(asm, ns, tyName, Some(typeof<CsvFile>))

        // Add a parameterless constructor that loads the file that was used to define the schema.
        let ctor0 =
            ProvidedConstructor([],
                invokeCode = fun [] -> <@@ CsvFile(resolvedFilename) @@>)
        ty.AddMember ctor0

        // Add a constructor that takes the file name to load.
        let ctor1 = ProvidedConstructor([ProvidedParameter("filename", typeof<string>)],
            invokeCode = fun [filename] -> <@@ CsvFile(%%filename) @@>)
        ty.AddMember ctor1

        // Add a more strongly typed Data property, which uses the existing property at runtime.
        let prop =
            ProvidedProperty("Data", typedefof<seq<_>>.MakeGenericType(rowTy),
                getterCode = fun [csvFile] -> <@@ (%%csvFile:CsvFile).Data @@>)
        ty.AddMember prop

        // Add the row type as a nested type.
        ty.AddMember rowTy
        ty)

    // Add the type to the namespace.
    do this.AddNamespace(ns, [csvTy])
```

<span data-ttu-id="786be-344">実装の次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="786be-344">Note the following points about the implementation:</span></span>

- <span data-ttu-id="786be-345">オーバーロードされたコンストラクターでは、元のファイル、またはそれと同一のスキーマを持つファイルを読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="786be-345">Overloaded constructors allow either the original file or one that has an identical schema to be read.</span></span> <span data-ttu-id="786be-346">このパターンは、ローカルまたはリモートのデータ ソースの型プロバイダーを作成するときによく使用され、ローカル ファイルをリモート データのテンプレートとして使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="786be-346">This pattern is common when you write a type provider for local or remote data sources, and this pattern allows a local file to be used as the template for remote data.</span></span>

- <span data-ttu-id="786be-347">型プロバイダーコンストラクターに渡された [Typeproviderconfig](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-compilerservices-typeproviderconfig.html) 値を使用して、相対ファイル名を解決できます。</span><span class="sxs-lookup"><span data-stu-id="786be-347">You can use the [TypeProviderConfig](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-compilerservices-typeproviderconfig.html) value that’s passed in to the type provider constructor to resolve relative file names.</span></span>

- <span data-ttu-id="786be-348">指定されたプロパティの場所を定義するには `AddDefinitionLocation` メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="786be-348">You can use the `AddDefinitionLocation` method to define the location of the provided properties.</span></span> <span data-ttu-id="786be-349">したがって、指定されたプロパティでを使用すると、 `Go To Definition` CSV ファイルが Visual Studio で開かれます。</span><span class="sxs-lookup"><span data-stu-id="786be-349">Therefore, if you use `Go To Definition` on a provided property, the CSV file will open in Visual Studio.</span></span>

- <span data-ttu-id="786be-350">SI 単位を調べて適切な `ProvidedMeasureBuilder` 型を生成するには、`float<_>` 型を使用できます。</span><span class="sxs-lookup"><span data-stu-id="786be-350">You can use the `ProvidedMeasureBuilder` type to look up the SI units and to generate the relevant `float<_>` types.</span></span>

### <a name="key-lessons"></a><span data-ttu-id="786be-351">レッスンの要点</span><span class="sxs-lookup"><span data-stu-id="786be-351">Key Lessons</span></span>

<span data-ttu-id="786be-352">このセクションでは、単純なスキーマがデータ ソース自体に含まれているローカル データ ソースのための型プロバイダーを作成する方法を説明しました。</span><span class="sxs-lookup"><span data-stu-id="786be-352">This section explained how to create a type provider for a local data source with a simple schema that's contained in the data source itself.</span></span>

## <a name="going-further"></a><span data-ttu-id="786be-353">理解を深める</span><span class="sxs-lookup"><span data-stu-id="786be-353">Going Further</span></span>

<span data-ttu-id="786be-354">以降のセクションでは、さらに理解を深めるための参考情報を示します。</span><span class="sxs-lookup"><span data-stu-id="786be-354">The following sections include suggestions for further study.</span></span>

### <a name="a-look-at-the-compiled-code-for-erased-types"></a><span data-ttu-id="786be-355">コンパイル済みコードにおける消去型</span><span class="sxs-lookup"><span data-stu-id="786be-355">A Look at the Compiled Code for Erased Types</span></span>

<span data-ttu-id="786be-356">型プロバイダーの使用が生成されたコードにどのように対応するかを説明するために、このトピックの前半で使用した `HelloWorldTypeProvider` を使って次の関数を見てみます。</span><span class="sxs-lookup"><span data-stu-id="786be-356">To give you some idea of how the use of the type provider corresponds to the code that's emitted, look at the following function by using the `HelloWorldTypeProvider` that's used earlier in this topic.</span></span>

```fsharp
let function1 () =
    let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")
    obj1.InstanceProperty
```

<span data-ttu-id="786be-357">ildasm.exe を使用して逆コンパイルされたコードのイメージを次に示します。</span><span class="sxs-lookup"><span data-stu-id="786be-357">Here’s an image of the resulting code decompiled by using ildasm.exe:</span></span>

```il
.class public abstract auto ansi sealed Module1
extends [mscorlib]System.Object
{
.custom instance void [FSharp.Core]Microsoft.FSharp.Core.CompilationMappingAtt
ribute::.ctor(valuetype [FSharp.Core]Microsoft.FSharp.Core.SourceConstructFlags)
= ( 01 00 07 00 00 00 00 00 )
.method public static int32  function1() cil managed
{
// Code size       24 (0x18)
.maxstack  3
.locals init ([0] object obj1)
IL_0000:  nop
IL_0001:  ldstr      "some data"
IL_0006:  unbox.any  [mscorlib]System.Object
IL_000b:  stloc.0
IL_000c:  ldloc.0
IL_000d:  call       !!0 [FSharp.Core_2]Microsoft.FSharp.Core.LanguagePrimit
ives/IntrinsicFunctions::UnboxGeneric<string>(object)
IL_0012:  callvirt   instance int32 [mscorlib_3]System.String::get_Length()
IL_0017:  ret
} // end of method Module1::function1

} // end of class Module1
```

<span data-ttu-id="786be-358">例に示すように、`Type1` 型と `InstanceProperty` プロパティについて示す部分はすべて消去されています。残っているのは関係するランタイム型に対する操作のみです。</span><span class="sxs-lookup"><span data-stu-id="786be-358">As the example shows, all mentions of the type `Type1` and the `InstanceProperty` property have been erased, leaving only operations on the runtime types involved.</span></span>

### <a name="design-and-naming-conventions-for-type-providers"></a><span data-ttu-id="786be-359">型プロバイダーのデザインと名前付け規則</span><span class="sxs-lookup"><span data-stu-id="786be-359">Design and Naming Conventions for Type Providers</span></span>

<span data-ttu-id="786be-360">型プロバイダーを作成するときは、次の規則に従ってください。</span><span class="sxs-lookup"><span data-stu-id="786be-360">Observe the following conventions when authoring type providers.</span></span>

<span data-ttu-id="786be-361">**接続プロトコルのプロバイダー** 一般に、OData や SQL 接続など、データおよびサービス接続プロトコル用のほとんどのプロバイダー Dll の名前は、またはで終了する必要があり `TypeProvider` `TypeProviders` ます。</span><span class="sxs-lookup"><span data-stu-id="786be-361">**Providers for Connectivity Protocols** In general, names of most provider DLLs for data and service connectivity protocols, such as OData or SQL connections, should end in `TypeProvider` or `TypeProviders`.</span></span> <span data-ttu-id="786be-362">たとえば、次の文字列のような DLL 名を使用します。</span><span class="sxs-lookup"><span data-stu-id="786be-362">For example, use a DLL name that resembles the following string:</span></span>

`Fabrikam.Management.BasicTypeProviders.dll`

<span data-ttu-id="786be-363">指定された型が対応する名前空間のメンバーであり、実装した接続プロトコルを示すようにします。</span><span class="sxs-lookup"><span data-stu-id="786be-363">Ensure that your provided types are members of the corresponding namespace, and indicate the connectivity protocol that you implemented:</span></span>

```fsharp
  Fabrikam.Management.BasicTypeProviders.WmiConnection<…>
  Fabrikam.Management.BasicTypeProviders.DataProtocolConnection<…>
```

<span data-ttu-id="786be-364">**一般的なコーディング用のユーティリティプロバイダー**。</span><span class="sxs-lookup"><span data-stu-id="786be-364">**Utility Providers for General Coding**.</span></span>  <span data-ttu-id="786be-365">正規表現用などのユーティリティ型プロバイダーでは、次の例に示すように、型プロバイダーが基本ライブラリに含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="786be-365">For a utility type provider such as that for regular expressions, the type provider may be part of a base library, as the following example shows:</span></span>

```fsharp
#r "Fabrikam.Core.Text.Utilities.dll"
```

<span data-ttu-id="786be-366">この場合、指定された型は、通常の .NET デザイン規則に従って適切な位置に表示されます。</span><span class="sxs-lookup"><span data-stu-id="786be-366">In this case, the provided type would appear at an appropriate point according to normal .NET design conventions:</span></span>

```fsharp
  open Fabrikam.Core.Text.RegexTyped

  let regex = new RegexTyped<"a+b+a+b+">()
```

<span data-ttu-id="786be-367">**シングルトンデータソース**。</span><span class="sxs-lookup"><span data-stu-id="786be-367">**Singleton Data Sources**.</span></span> <span data-ttu-id="786be-368">型プロバイダーの中には、単一の専用データ ソースに接続してデータのみを指定するものがあります。</span><span class="sxs-lookup"><span data-stu-id="786be-368">Some type providers connect to a single dedicated data source and provide only data.</span></span> <span data-ttu-id="786be-369">この場合、`TypeProvider` サフィックスを削除して、通常の .NET の名前付け規則を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="786be-369">In this case, you should drop the `TypeProvider` suffix and use normal conventions for .NET naming:</span></span>

```fsharp
#r "Fabrikam.Data.Freebase.dll"

let data = Fabrikam.Data.Freebase.Astronomy.Asteroids
```

<span data-ttu-id="786be-370">詳細については、このトピックで後述する `GetConnection` デザイン規則を参照してください。</span><span class="sxs-lookup"><span data-stu-id="786be-370">For more information, see the `GetConnection` design convention that's described later in this topic.</span></span>

### <a name="design-patterns-for-type-providers"></a><span data-ttu-id="786be-371">型プロバイダーのパターンのデザイン</span><span class="sxs-lookup"><span data-stu-id="786be-371">Design Patterns for Type Providers</span></span>

<span data-ttu-id="786be-372">以降のセクションでは、型プロバイダーを作成するときに使用できるデザイン パターンを説明します。</span><span class="sxs-lookup"><span data-stu-id="786be-372">The following sections describe design patterns you can use when authoring type providers.</span></span>

#### <a name="the-getconnection-design-pattern"></a><span data-ttu-id="786be-373">GetConnection デザイン パターン</span><span class="sxs-lookup"><span data-stu-id="786be-373">The GetConnection Design Pattern</span></span>

<span data-ttu-id="786be-374">ほとんどの型プロバイダーは、FSharp.Data.TypeProviders.dll で型プロバイダーに使用される `GetConnection` パターンを使用するように作成されます。次にその例を示します。</span><span class="sxs-lookup"><span data-stu-id="786be-374">Most type providers should be written to use the `GetConnection` pattern that's used by the type providers in FSharp.Data.TypeProviders.dll, as the following example shows:</span></span>

```fsharp
#r "Fabrikam.Data.WebDataStore.dll"

type Service = Fabrikam.Data.WebDataStore<…static connection parameters…>

let connection = Service.GetConnection(…dynamic connection parameters…)

let data = connection.Astronomy.Asteroids
```

#### <a name="type-providers-backed-by-remote-data-and-services"></a><span data-ttu-id="786be-375">リモート データとサービスに基づく型プロバイダー</span><span class="sxs-lookup"><span data-stu-id="786be-375">Type Providers Backed By Remote Data and Services</span></span>

<span data-ttu-id="786be-376">リモート データとサービスに基づく型プロバイダーを作成する前に、接続型プログラミングに内在するさまざまな問題を検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="786be-376">Before you create a type provider that's backed by remote data and services, you must consider a range of issues that are inherent in connected programming.</span></span> <span data-ttu-id="786be-377">これらの問題には、次の検討事項が含まれています。</span><span class="sxs-lookup"><span data-stu-id="786be-377">These issues include the following considerations:</span></span>

- <span data-ttu-id="786be-378">スキーマ マッピング</span><span class="sxs-lookup"><span data-stu-id="786be-378">schema mapping</span></span>

- <span data-ttu-id="786be-379">スキーマ変更がある場合の活性と無効化</span><span class="sxs-lookup"><span data-stu-id="786be-379">liveness and invalidation in the presence of schema change</span></span>

- <span data-ttu-id="786be-380">スキーマ キャッシュ</span><span class="sxs-lookup"><span data-stu-id="786be-380">schema caching</span></span>

- <span data-ttu-id="786be-381">データ アクセス操作の非同期実装</span><span class="sxs-lookup"><span data-stu-id="786be-381">asynchronous implementations of data access operations</span></span>

- <span data-ttu-id="786be-382">LINQ クエリを含むクエリのサポート</span><span class="sxs-lookup"><span data-stu-id="786be-382">supporting queries, including LINQ queries</span></span>

- <span data-ttu-id="786be-383">資格情報と認証</span><span class="sxs-lookup"><span data-stu-id="786be-383">credentials and authentication</span></span>

<span data-ttu-id="786be-384">このトピックでは、これらの問題をこれ以上説明しません。</span><span class="sxs-lookup"><span data-stu-id="786be-384">This topic doesn't explore these issues further.</span></span>

### <a name="additional-authoring-techniques"></a><span data-ttu-id="786be-385">その他の作成方法</span><span class="sxs-lookup"><span data-stu-id="786be-385">Additional Authoring Techniques</span></span>

<span data-ttu-id="786be-386">独自の型プロバイダーを作成するとき、次の方法も使用できます。</span><span class="sxs-lookup"><span data-stu-id="786be-386">When you write your own type providers, you might want to use the following additional techniques.</span></span>

### <a name="creating-types-and-members-on-demand"></a><span data-ttu-id="786be-387">型およびメンバーを要求に応じて作成する</span><span class="sxs-lookup"><span data-stu-id="786be-387">Creating Types and Members On-Demand</span></span>

<span data-ttu-id="786be-388">ProvidedType API には遅延バージョンの AddMember があります。</span><span class="sxs-lookup"><span data-stu-id="786be-388">The ProvidedType API has delayed versions of AddMember.</span></span>

```fsharp
  type ProvidedType =
      member AddMemberDelayed  : (unit -> MemberInfo)      -> unit
      member AddMembersDelayed : (unit -> MemberInfo list) -> unit
```

<span data-ttu-id="786be-389">これらのバージョンは、型のオンデマンド空間の作成に使用されます。</span><span class="sxs-lookup"><span data-stu-id="786be-389">These versions are used to create on-demand spaces of types.</span></span>

### <a name="providing-array-types-and-generic-type-instantiations"></a><span data-ttu-id="786be-390">配列型とジェネリック型のインスタンス化の提供</span><span class="sxs-lookup"><span data-stu-id="786be-390">Providing Array types and Generic Type Instantiations</span></span>

<span data-ttu-id="786be-391">(を `MakeArrayType` `MakePointerType` 含む) `MakeGenericType` の任意のインスタンスで、通常の、、およびを使用して、指定されたメンバー (シグネチャに配列型、byref 型、およびジェネリック型のインスタンス化が含まれる) を作成し <xref:System.Type> `ProvidedTypeDefinitions` ます。</span><span class="sxs-lookup"><span data-stu-id="786be-391">You make provided members (whose signatures include array types, byref types, and instantiations of generic types) by using the normal `MakeArrayType`, `MakePointerType`, and `MakeGenericType` on any instance of <xref:System.Type>, including `ProvidedTypeDefinitions`.</span></span>

> [!NOTE]
> <span data-ttu-id="786be-392">場合によっては、でヘルパーを使用する必要があり `ProvidedTypeBuilder.MakeGenericType` ます。</span><span class="sxs-lookup"><span data-stu-id="786be-392">In some cases you may have to use the helper in `ProvidedTypeBuilder.MakeGenericType`.</span></span>  <span data-ttu-id="786be-393">詳細については、 [型プロバイダー SDK のドキュメント](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="786be-393">See the [Type Provider SDK documentation](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) for more details.</span></span>

### <a name="providing-unit-of-measure-annotations"></a><span data-ttu-id="786be-394">測定単位の注釈を指定する</span><span class="sxs-lookup"><span data-stu-id="786be-394">Providing Unit of Measure Annotations</span></span>

<span data-ttu-id="786be-395">ProvidedTypes API は、メジャーの注釈を指定するためのヘルパーを指定します。</span><span class="sxs-lookup"><span data-stu-id="786be-395">The ProvidedTypes API provides helpers for providing measure annotations.</span></span> <span data-ttu-id="786be-396">たとえば、`float<kg>` 型を指定するには次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="786be-396">For example, to provide the type `float<kg>`, use the following code:</span></span>

```fsharp
  let measures = ProvidedMeasureBuilder.Default
  let kg = measures.SI "kilogram"
  let m = measures.SI "meter"
  let float_kg = measures.AnnotateType(typeof<float>,[kg])
```

  <span data-ttu-id="786be-397">`Nullable<decimal<kg/m^2>>` 型を指定するには次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="786be-397">To provide the type `Nullable<decimal<kg/m^2>>`, use the following code:</span></span>

```fsharp
  let kgpm2 = measures.Ratio(kg, measures.Square m)
  let dkgpm2 = measures.AnnotateType(typeof<decimal>,[kgpm2])
  let nullableDecimal_kgpm2 = typedefof<System.Nullable<_>>.MakeGenericType [|dkgpm2 |]
```

### <a name="accessing-project-local-or-script-local-resources"></a><span data-ttu-id="786be-398">プロジェクト ローカル リソースまたはスクリプト ローカル リソースにアクセスする</span><span class="sxs-lookup"><span data-stu-id="786be-398">Accessing Project-Local or Script-Local Resources</span></span>

<span data-ttu-id="786be-399">型プロバイダーの各インスタンスには、構築時に `TypeProviderConfig` 値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="786be-399">Each instance of a type provider can be given a `TypeProviderConfig` value during construction.</span></span> <span data-ttu-id="786be-400">この値には、そのプロバイダー用の "解決フォルダー"(コンパイル用のプロジェクト フォルダーまたはスクリプトを含んでいるディレクトリ)、参照されるアセンブリのリスト、その他の情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="786be-400">This value contains the "resolution folder" for the provider (that is, the project folder for the compilation or the directory that contains a script), the list of referenced assemblies, and other information.</span></span>

### <a name="invalidation"></a><span data-ttu-id="786be-401">無効化</span><span class="sxs-lookup"><span data-stu-id="786be-401">Invalidation</span></span>

<span data-ttu-id="786be-402">プロバイダーは、無効化シグナルを生成して F# 言語サービスにスキーマの前提が変わった可能性があることを通知できます。</span><span class="sxs-lookup"><span data-stu-id="786be-402">Providers can raise invalidation signals to notify the F# language service that the schema assumptions may have changed.</span></span> <span data-ttu-id="786be-403">無効化が発生すると、プロバイダーが Visual Studio にホストされている場合は型チェックが再度実行されます。</span><span class="sxs-lookup"><span data-stu-id="786be-403">When invalidation occurs, a typecheck is redone if the provider is being hosted in Visual Studio.</span></span> <span data-ttu-id="786be-404">このシグナルは、プロバイダーが F# Interactive または F# コンパイラ (fsc.exe) でホストされている場合は無視されます。</span><span class="sxs-lookup"><span data-stu-id="786be-404">This signal will be ignored when the provider is hosted in F# Interactive or by the F# Compiler (fsc.exe).</span></span>

### <a name="caching-schema-information"></a><span data-ttu-id="786be-405">スキーマ情報をキャッシュする</span><span class="sxs-lookup"><span data-stu-id="786be-405">Caching Schema Information</span></span>

<span data-ttu-id="786be-406">多くの場合、プロバイダーはスキーマ情報へのアクセスをキャッシュする必要があります。</span><span class="sxs-lookup"><span data-stu-id="786be-406">Providers must often cache access to schema information.</span></span> <span data-ttu-id="786be-407">キャッシュされたデータは静的パラメーターまたはユーザー データとして指定されたファイル名を使用して格納されます。</span><span class="sxs-lookup"><span data-stu-id="786be-407">The cached data should be stored by using a file name that's given as a static parameter or as user data.</span></span> <span data-ttu-id="786be-408">スキーマ キャッシュの例には、`LocalSchemaFile` アセンブリ内の型プロバイダーの `FSharp.Data.TypeProviders` パラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="786be-408">An example of schema caching is the `LocalSchemaFile` parameter in the type providers in the `FSharp.Data.TypeProviders` assembly.</span></span> <span data-ttu-id="786be-409">これらのプロバイダーの実装では、この静的パラメーターは、型プロバイダーがデータ ソースにネットワーク経由でアクセスする代わりに、指定されたローカル ファイル内のスキーマ情報を使用するように指定します。</span><span class="sxs-lookup"><span data-stu-id="786be-409">In the implementation of these providers, this static parameter directs the type provider to use the schema information in the specified local file instead of accessing the data source over the network.</span></span> <span data-ttu-id="786be-410">また、キャッシュされたスキーマ情報を使用するには、静的パラメーター `ForceUpdate` を `false` に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="786be-410">To use cached schema information, you must also set the static parameter `ForceUpdate` to `false`.</span></span> <span data-ttu-id="786be-411">同様の手法でオンラインとオフラインのデータ アクセスを有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="786be-411">You could use a similar technique to enable online and offline data access.</span></span>

### <a name="backing-assembly"></a><span data-ttu-id="786be-412">バッキング アセンブリ</span><span class="sxs-lookup"><span data-stu-id="786be-412">Backing Assembly</span></span>

<span data-ttu-id="786be-413">またはファイルをコンパイルすると `.dll` `.exe` 、生成された型のバッキング .dll ファイルは、結果のアセンブリに静的にリンクされます。</span><span class="sxs-lookup"><span data-stu-id="786be-413">When you compile a `.dll` or `.exe` file, the backing .dll file for generated types is statically linked into the resulting assembly.</span></span> <span data-ttu-id="786be-414">このリンクは、中間言語 (IL) の型定義とマネージド リソースをバッキング アセンブリから最終アセンブリにコピーして作成されます。</span><span class="sxs-lookup"><span data-stu-id="786be-414">This link is created by copying the Intermediate Language (IL) type definitions and any managed resources from the backing assembly into the final assembly.</span></span> <span data-ttu-id="786be-415">F# Interactive を使用すると、バッキング .dll ファイルはコピーされず、代わりに F# Interactive プロセスに直接読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="786be-415">When you use F# Interactive, the backing .dll file isn't copied and is instead loaded directly into the F# Interactive process.</span></span>

### <a name="exceptions-and-diagnostics-from-type-providers"></a><span data-ttu-id="786be-416">型プロバイダーからの例外と診断</span><span class="sxs-lookup"><span data-stu-id="786be-416">Exceptions and Diagnostics from Type Providers</span></span>

<span data-ttu-id="786be-417">指定された型のすべてのメンバーの使用において例外がスローされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="786be-417">All uses of all members from provided types may throw exceptions.</span></span> <span data-ttu-id="786be-418">いずれの場合も、型プロバイダーが例外をスローした場合、ホスト コンパイラはそのエラーの原因を特定の型プロバイダーに求めます。</span><span class="sxs-lookup"><span data-stu-id="786be-418">In all cases, if a type provider throws an exception, the host compiler attributes the error to a specific type provider.</span></span>

- <span data-ttu-id="786be-419">型プロバイダーの例外は、内部コンパイル エラーになることはありません。</span><span class="sxs-lookup"><span data-stu-id="786be-419">Type provider exceptions should never result in internal compiler errors.</span></span>

- <span data-ttu-id="786be-420">型プロバイダーは警告を発生できません。</span><span class="sxs-lookup"><span data-stu-id="786be-420">Type providers can't report warnings.</span></span>

- <span data-ttu-id="786be-421">F# コンパイラ、F# 開発環境、または F# Interactive でホストされている型プロバイダーからの例外はすべてキャッチされます。</span><span class="sxs-lookup"><span data-stu-id="786be-421">When a type provider is hosted in the F# compiler, an F# development environment, or F# Interactive, all exceptions from that provider are caught.</span></span> <span data-ttu-id="786be-422">Message プロパティは常にエラー テキストであり、スタック トレースは表示されません。</span><span class="sxs-lookup"><span data-stu-id="786be-422">The Message property is always the error text, and no stack trace appears.</span></span> <span data-ttu-id="786be-423">例外をスローする場合は、、、の各例をスローすることができます `System.NotSupportedException` `System.IO.IOException` `System.Exception` 。</span><span class="sxs-lookup"><span data-stu-id="786be-423">If you’re going to throw an exception, you can throw the following examples: `System.NotSupportedException`, `System.IO.IOException`, `System.Exception`.</span></span>

#### <a name="providing-generated-types"></a><span data-ttu-id="786be-424">生成された型の指定</span><span class="sxs-lookup"><span data-stu-id="786be-424">Providing Generated Types</span></span>

<span data-ttu-id="786be-425">ここまでで、このドキュメントでは、消去された型を指定する方法について説明しました。</span><span class="sxs-lookup"><span data-stu-id="786be-425">So far, this document has explained how to provide erased types.</span></span> <span data-ttu-id="786be-426">F# の型プロバイダー メカニズムを使用して、ユーザー プログラムに実際の .NET 型定義として追加される生成された型を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="786be-426">You can also use the type provider mechanism in F# to provide generated types, which are added as real .NET type definitions into the users' program.</span></span> <span data-ttu-id="786be-427">生成され指定された型は型定義を使用して参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="786be-427">You must refer to generated provided types by using a type definition.</span></span>

```fsharp
open Microsoft.FSharp.TypeProviders

type Service = ODataService<"http://services.odata.org/Northwind/Northwind.svc/">
```

<span data-ttu-id="786be-428">F# 3.0 リリースに含まれている ProvidedTypes-0.2 ヘルパー コードは、生成された型を指定するためのサポートが限られています。</span><span class="sxs-lookup"><span data-stu-id="786be-428">The ProvidedTypes-0.2 helper code that is part of the F# 3.0 release has only limited support for providing generated types.</span></span> <span data-ttu-id="786be-429">生成された型の定義は次の条件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="786be-429">The following statements must be true for a generated type definition:</span></span>

- <span data-ttu-id="786be-430">`isErased` が `false` に設定されていること。</span><span class="sxs-lookup"><span data-stu-id="786be-430">`isErased` must be set to `false`.</span></span>

- <span data-ttu-id="786be-431">生成された型は、生成された `ProvidedAssembly()` コードフラグメントのコンテナーを表す、新しく構築されたに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="786be-431">The generated type must be added to a newly constructed `ProvidedAssembly()`, which represents a container for generated code fragments.</span></span>

- <span data-ttu-id="786be-432">プロバイダーは、実際のバッキング .NET .dll ファイルを含むアセンブリを持ち、対応する .dll ファイルがディスク上にある。</span><span class="sxs-lookup"><span data-stu-id="786be-432">The provider must have an assembly that has an actual backing .NET .dll file with a matching .dll file on disk.</span></span>

## <a name="rules-and-limitations"></a><span data-ttu-id="786be-433">規則と制約</span><span class="sxs-lookup"><span data-stu-id="786be-433">Rules and Limitations</span></span>

<span data-ttu-id="786be-434">型プロバイダーを作成するときは、次の規則と制約に注意してください。</span><span class="sxs-lookup"><span data-stu-id="786be-434">When you write type providers, keep the following rules and limitations in mind.</span></span>

### <a name="provided-types-must-be-reachable"></a><span data-ttu-id="786be-435">指定された型は到達可能でなければなりません</span><span class="sxs-lookup"><span data-stu-id="786be-435">Provided types must be reachable</span></span>

<span data-ttu-id="786be-436">すべての指定された型は、入れ子になっていない型から到達可能である必要があります。</span><span class="sxs-lookup"><span data-stu-id="786be-436">All provided types should be reachable from the non-nested types.</span></span> <span data-ttu-id="786be-437">入れ子になっていない型は、`TypeProviderForNamespaces` コンストラクターへの呼び出し、または `AddNamespace` への呼び出しで指定されます。</span><span class="sxs-lookup"><span data-stu-id="786be-437">The non-nested types are given in the call to the `TypeProviderForNamespaces` constructor or a call to `AddNamespace`.</span></span> <span data-ttu-id="786be-438">たとえば、プロバイダーが `StaticClass.P : T` 型を指定する場合、T は入れ子になっていない型、または 1 階層だけ入れ子になっている型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="786be-438">For example, if the provider provides a type `StaticClass.P : T`, you must ensure that T is either a non-nested type or nested under one.</span></span>

<span data-ttu-id="786be-439">たとえば、一部のプロバイダーには、`DataTypes` の各型を含む `T1, T2, T3, ...` などの静的クラスがあります。</span><span class="sxs-lookup"><span data-stu-id="786be-439">For example, some providers have a static class such as `DataTypes` that contain these `T1, T2, T3, ...` types.</span></span> <span data-ttu-id="786be-440">それ以外の場合、アセンブリ A 内の型 T に対する参照は見つかるが、型はそのアセンブリ内に見つからないというエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="786be-440">Otherwise, the error says that a reference to type T in assembly A was found, but the type couldn't be found in that assembly.</span></span> <span data-ttu-id="786be-441">このエラーが表示された場合は、すべての下位の型が指定された型から到達可能であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="786be-441">If this error appears, verify that all your subtypes can be reached from the provider types.</span></span> <span data-ttu-id="786be-442">注: これらの `T1, T2, T3...` 型は *、* 実行中の型と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="786be-442">Note: These `T1, T2, T3...` types are referred to as the *on-the-fly* types.</span></span> <span data-ttu-id="786be-443">必ずこれらの型をアクセス可能な名前空間または親の型に入れてください。</span><span class="sxs-lookup"><span data-stu-id="786be-443">Remember to put them in an accessible namespace or a parent type.</span></span>

### <a name="limitations-of-the-type-provider-mechanism"></a><span data-ttu-id="786be-444">型プロバイダー メカニズムの制約</span><span class="sxs-lookup"><span data-stu-id="786be-444">Limitations of the Type Provider Mechanism</span></span>

<span data-ttu-id="786be-445">F# の型プロバイダー メカニズムには、次の制約があります。</span><span class="sxs-lookup"><span data-stu-id="786be-445">The type provider mechanism in F# has the following limitations:</span></span>

- <span data-ttu-id="786be-446">F# の型プロバイダーの基になるインフラストラクチャは、指定されたジェネリック型または指定されたジェネリック メソッドをサポートしません。</span><span class="sxs-lookup"><span data-stu-id="786be-446">The underlying infrastructure for type providers in F# doesn't support provided generic types or provided generic methods.</span></span>

- <span data-ttu-id="786be-447">このメカニズムは、静的パラメーターを持つ入れ子になった型をサポートしません。</span><span class="sxs-lookup"><span data-stu-id="786be-447">The mechanism doesn't support nested types with static parameters.</span></span>

## <a name="development-tips"></a><span data-ttu-id="786be-448">開発のヒント</span><span class="sxs-lookup"><span data-stu-id="786be-448">Development Tips</span></span>

<span data-ttu-id="786be-449">開発プロセスでは、次のヒントが役に立つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="786be-449">You might find the following tips helpful during the development process:</span></span>

### <a name="run-two-instances-of-visual-studio"></a><span data-ttu-id="786be-450">Visual Studio の2つのインスタンスを実行する</span><span class="sxs-lookup"><span data-stu-id="786be-450">Run two instances of Visual Studio</span></span>

<span data-ttu-id="786be-451">型プロバイダーがリビルドされることを防止する .dll ファイルのロックをテスト IDE が取得するので、型プロバイダーを 1 つのインスタンスで作成し、そのプロバイダーを別のインスタンスでテストできます。</span><span class="sxs-lookup"><span data-stu-id="786be-451">You can develop the type provider in one instance and test the provider in the other because the test IDE will take a lock on the .dll file that prevents the type provider from being rebuilt.</span></span> <span data-ttu-id="786be-452">したがって、最初のインスタンスでプロバイダーをビルドしている間は Visual Studio の 2 番目のインスタンスを閉じておき、プロバイダーがビルドされた後に、2 番目のインスタンスを再び開く必要があります。</span><span class="sxs-lookup"><span data-stu-id="786be-452">Thus, you must close the second instance of Visual Studio while the provider is built in the first instance, and then you must reopen the second instance after the provider is built.</span></span>

### <a name="debug-type-providers-by-using-invocations-of-fscexe"></a><span data-ttu-id="786be-453">fsc.exe の呼び出しを使用して型プロバイダーをデバッグする</span><span class="sxs-lookup"><span data-stu-id="786be-453">Debug type providers by using invocations of fsc.exe</span></span>

<span data-ttu-id="786be-454">次のツールを使用して型プロバイダーを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="786be-454">You can invoke type providers by using the following tools:</span></span>

- <span data-ttu-id="786be-455">fsc.exe (F# コマンド ライン コンパイラ)</span><span class="sxs-lookup"><span data-stu-id="786be-455">fsc.exe (The F# command line compiler)</span></span>

- <span data-ttu-id="786be-456">fsi.exe (F# Interactive コンパイラ)</span><span class="sxs-lookup"><span data-stu-id="786be-456">fsi.exe (The F# Interactive compiler)</span></span>

- <span data-ttu-id="786be-457">devenv.exe (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="786be-457">devenv.exe (Visual Studio)</span></span>

<span data-ttu-id="786be-458">多くの場合、型プロバイダーは、テスト スクリプト ファイル (script.fsx など) で fsc.exe を使用することによって、最も簡単にデバッグできます。</span><span class="sxs-lookup"><span data-stu-id="786be-458">You can often debug type providers most easily by using fsc.exe on a test script file (for example, script.fsx).</span></span> <span data-ttu-id="786be-459">コマンド プロンプトからデバッガーを起動できます。</span><span class="sxs-lookup"><span data-stu-id="786be-459">You can launch a debugger from a command prompt.</span></span>

```console
devenv /debugexe fsc.exe script.fsx
```

  <span data-ttu-id="786be-460">stdout への出力のログを使用できます。</span><span class="sxs-lookup"><span data-stu-id="786be-460">You can use print-to-stdout logging.</span></span>

## <a name="see-also"></a><span data-ttu-id="786be-461">関連項目</span><span class="sxs-lookup"><span data-stu-id="786be-461">See also</span></span>

- [<span data-ttu-id="786be-462">型プロバイダー</span><span class="sxs-lookup"><span data-stu-id="786be-462">Type Providers</span></span>](index.md)
- [<span data-ttu-id="786be-463">型プロバイダー SDK</span><span class="sxs-lookup"><span data-stu-id="786be-463">The Type Provider SDK</span></span>](https://github.com/fsprojects/FSharp.TypeProviders.SDK)
