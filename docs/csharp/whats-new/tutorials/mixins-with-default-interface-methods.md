---
title: 既定のインターフェイス メソッドを使用して mixin 型を作成する
description: 既定のインターフェイス メンバーを使用すると、実装のためにオプションの既定の実装を使用してインターフェイスを拡張できます。
ms.technology: csharp-advanced-concepts
ms.date: 10/04/2019
ms.openlocfilehash: 9137d42b1795b20385d2dde16548452eeb9807c3
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104878904"
---
# <a name="tutorial-mix-functionality-in-when-creating-classes-using-interfaces-with-default-interface-methods"></a><span data-ttu-id="9fa0b-103">チュートリアル: 既定のインターフェイス メソッドでインターフェイスを使用してクラスを作成するときの機能の混合</span><span class="sxs-lookup"><span data-stu-id="9fa0b-103">Tutorial: Mix functionality in when creating classes using interfaces with default interface methods</span></span>

<span data-ttu-id="9fa0b-104">.NET Core 3.0 上の C# 8.0 以降では、インターフェイスのメンバーを宣言するときに実装を定義できます。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-104">Beginning with C# 8.0 on .NET Core 3.0, you can define an implementation when you declare a member of an interface.</span></span> <span data-ttu-id="9fa0b-105">この機能により、インターフェイスで宣言された機能の既定の実装を定義できるという新機能が提供されます。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-105">This feature provides new capabilities where you can define default implementations for features declared in interfaces.</span></span> <span data-ttu-id="9fa0b-106">クラスでは、機能をオーバーライドする場合、既定の機能を使用する場合、および個別の機能のサポートを宣言しない場合を選択できます。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-106">Classes can pick when to override functionality, when to use the default functionality, and when not to declare support for discrete features.</span></span>

<span data-ttu-id="9fa0b-107">このチュートリアルでは、次の作業を行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-107">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="9fa0b-108">個別の機能を記述する実装を備えたインターフェイスを作成します。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-108">Create interfaces with implementations that describe discrete features.</span></span>
> * <span data-ttu-id="9fa0b-109">既定の実装を使用するクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-109">Create classes that use the default implementations.</span></span>
> * <span data-ttu-id="9fa0b-110">既定の実装の一部またはすべてをオーバーライドするクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-110">Create classes that override some or all of the default implementations.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9fa0b-111">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="9fa0b-111">Prerequisites</span></span>

<span data-ttu-id="9fa0b-112">お使いのコンピューターを、.NET Core が実行されるように設定する必要があります。C# 8.0 コンパイラも実行されるようにします。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-112">You’ll need to set up your machine to run .NET Core, including the C# 8.0 compiler.</span></span> <span data-ttu-id="9fa0b-113">C# 8.0 コンパイラは [Visual Studio 2019 バージョン 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) または [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet) 以降から使用できます。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-113">The C# 8.0 compiler is available starting with [Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), or the [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet) or later.</span></span>

## <a name="limitations-of-extension-methods"></a><span data-ttu-id="9fa0b-114">拡張メソッドの制限事項</span><span class="sxs-lookup"><span data-stu-id="9fa0b-114">Limitations of extension methods</span></span>

<span data-ttu-id="9fa0b-115">インターフェイスの一部として表示される動作を実装する方法の 1 つとして、既定の動作を提供する[拡張メソッド](../../programming-guide/classes-and-structs/extension-methods.md)を定義することがあります。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-115">One way you can implement behavior that appears as part of an interface is to define [extension methods](../../programming-guide/classes-and-structs/extension-methods.md) that provide the default behavior.</span></span> <span data-ttu-id="9fa0b-116">インターフェイスでは、そのインターフェイスを実装するクラスに対してより広い範囲の外部からのアクセスを提供すると同時に、最小セットのメンバーを宣言します。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-116">Interfaces declare a minimum set of members while providing a greater surface area for any class that implements that interface.</span></span> <span data-ttu-id="9fa0b-117">たとえば、<xref:System.Linq.Enumerable> の拡張メソッドは、任意のシーケンスの実装を LINQ クエリのソースとして提供します。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-117">For example, the extension methods in <xref:System.Linq.Enumerable> provide the implementation for any sequence to be the source of a LINQ query.</span></span>

<span data-ttu-id="9fa0b-118">拡張メソッドは、コンパイル時に変数の宣言型を使用して解決されます。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-118">Extension methods are resolved at compile time, using the declared type of the variable.</span></span> <span data-ttu-id="9fa0b-119">インターフェイスを実装するクラスを使用すると、すべての拡張メソッドに対してより適切な実装を提供できます。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-119">Classes that implement the interface can provide a better implementation for any extension method.</span></span> <span data-ttu-id="9fa0b-120">コンパイラで実装を選択できるようにするには、変数宣言が実装する型と一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-120">Variable declarations must match the implementing type to enable the compiler to choose that implementation.</span></span> <span data-ttu-id="9fa0b-121">コンパイル時の型がインターフェイスと一致する場合、メソッドの呼び出しは拡張メソッドに解決されます。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-121">When the compile-time type matches the interface, method calls resolve to the extension method.</span></span> <span data-ttu-id="9fa0b-122">拡張メソッドに関するもう 1 つの問題は、拡張メソッドを含むクラスにアクセスできる場所であれば、これらのメソッドにアクセスできることです。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-122">Another concern with extension methods is that those methods are accessible wherever the class containing the extension methods is accessible.</span></span> <span data-ttu-id="9fa0b-123">クラスでは、拡張メソッドで宣言された機能を提供する必要があるかどうかを宣言できません。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-123">Classes cannot declare if they should or should not provide features declared in extension methods.</span></span>

<span data-ttu-id="9fa0b-124">C# 8.0 以降では、既定の実装をインターフェイス メソッドとして宣言できます。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-124">Starting with C# 8.0, you can declare the default implementations as interface methods.</span></span> <span data-ttu-id="9fa0b-125">その後は、すべてのクラスで自動的に既定の実装が使用されます。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-125">Then, every class automatically uses the default implementation.</span></span> <span data-ttu-id="9fa0b-126">より適切な実装を提供できるクラスでは、インターフェイス メソッドの定義をより適切なアルゴリズムでオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-126">Any class that can provide a better implementation can override the interface method definition with a better algorithm.</span></span> <span data-ttu-id="9fa0b-127">ある意味では、この手法は[拡張メソッド](../../programming-guide/classes-and-structs/extension-methods.md)を使用する方法と似ています。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-127">In one sense, this technique sounds similar to how you could use [extension methods](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

<span data-ttu-id="9fa0b-128">この記事では、既定のインターフェイスの実装で新しいシナリオを実現する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-128">In this article, you'll learn how default interface implementations enable new scenarios.</span></span>

## <a name="design-the-application"></a><span data-ttu-id="9fa0b-129">アプリケーションを設計する</span><span class="sxs-lookup"><span data-stu-id="9fa0b-129">Design the application</span></span>

<span data-ttu-id="9fa0b-130">ホーム オートメーション アプリケーションについて考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-130">Consider a home automation application.</span></span> <span data-ttu-id="9fa0b-131">家庭内で使用される可能性がある照明とインジケーターには、おそらくさまざまな種類があります。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-131">You probably have many different types of lights and indicators that could be used throughout the house.</span></span> <span data-ttu-id="9fa0b-132">すべての照明が、オン/オフを切り替え、現在の状態を報告する API をサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-132">Every light must support APIs to turn them on and off, and to report the current state.</span></span> <span data-ttu-id="9fa0b-133">一部の照明とインジケーターでは、次のような他の機能がサポートされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-133">Some lights and indicators may support other features, such as:</span></span>

- <span data-ttu-id="9fa0b-134">照明をオンにして、タイマーの後にオフにする。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-134">Turn light on, then turn it off after a timer.</span></span>
- <span data-ttu-id="9fa0b-135">一定の期間、照明を点滅させる。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-135">Blink the light for a period of time.</span></span>

<span data-ttu-id="9fa0b-136">これらの拡張機能の一部は、最小セットをサポートするデバイスでエミュレートできます。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-136">Some of these extended capabilities could be emulated in devices that support the minimal set.</span></span> <span data-ttu-id="9fa0b-137">これは、既定の実装を提供することを示します。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-137">That indicates providing a default implementation.</span></span> <span data-ttu-id="9fa0b-138">より多くの機能が組み込まれているデバイスの場合、デバイス ソフトウェアではネイティブ機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-138">For those devices that have more capabilities built in, the device software would use the native capabilities.</span></span> <span data-ttu-id="9fa0b-139">他の照明については、インターフェイスを実装し、既定の実装を使用することを選択できます。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-139">For other lights, they could choose to implement the interface and use the default implementation.</span></span>

<span data-ttu-id="9fa0b-140">このシナリオでは、拡張メソッドよりも既定のインターフェイス メンバーの方が適したソリューションです。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-140">Default interface members is a better solution for this scenario than extension methods.</span></span> <span data-ttu-id="9fa0b-141">クラス作成者は、実装するインターフェイスを制御できます。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-141">Class authors can control which interfaces they choose to implement.</span></span> <span data-ttu-id="9fa0b-142">選択したインターフェイスはメソッドとして利用できます。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-142">Those interfaces they choose are available as methods.</span></span> <span data-ttu-id="9fa0b-143">また、既定のインターフェイス メソッドは既定で仮想であるため、メソッドのディスパッチでは常にクラス内の実装が選択されます。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-143">In addition, because default interface methods are virtual by default, the method dispatch always chooses the implementation in the class.</span></span>

<span data-ttu-id="9fa0b-144">これらの違いを示すコードを作成してみましょう。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-144">Let's create the code to demonstrate these differences.</span></span>

## <a name="create-interfaces"></a><span data-ttu-id="9fa0b-145">インターフェイスを作成する</span><span class="sxs-lookup"><span data-stu-id="9fa0b-145">Create interfaces</span></span>

<span data-ttu-id="9fa0b-146">まず、すべての照明の動作を定義するインターフェイスを作成します。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-146">Start by creating the interface that defines the behavior for all lights:</span></span>

[!code-csharp[Declare base interface](./snippets/mixins-with-default-interface-methods/UnusedExampleCode.cs?name=SnippetILightInterfaceV1)]

<span data-ttu-id="9fa0b-147">基本的な天井の照明器具では、次のコードに示すようにこのインターフェイスを実装する場合があります。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-147">A basic overhead light fixture might implement this interface as shown in the following code:</span></span>

[!code-csharp[First overhead light](./snippets/mixins-with-default-interface-methods/UnusedExampleCode.cs?name=SnippetOverheadLightV1)]

<span data-ttu-id="9fa0b-148">このチュートリアルでは、IoT デバイスを駆動していませんが、コンソールにメッセージを書き込んでそのアクティビティをエミュレートします。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-148">In this tutorial, the code doesn't drive IoT devices, but emulates those activities by writing messages to the console.</span></span> <span data-ttu-id="9fa0b-149">家を自動化せずにコードを調べることができます。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-149">You can explore the code without automating your house.</span></span>

<span data-ttu-id="9fa0b-150">次に、タイムアウト後に自動的にオフにできる照明のインターフェイスを定義します。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-150">Next, let's define the interface for a light that can automatically turn off after a timeout:</span></span>

[!code-csharp[pure Timer interface](./snippets/mixins-with-default-interface-methods/UnusedExampleCode.cs?name=SnippetPureTimerInterface)]

<span data-ttu-id="9fa0b-151">天井の照明に基本的な実装を追加することもできますが、おすすめのソリューションは、このインターフェイス定義を変更して `virtual` の既定の実装を提供することです。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-151">You could add a basic implementation to the overhead light, but a better solution is to modify this interface definition to provide a `virtual` default implementation:</span></span>

[!code-csharp[Timer interface](./snippets/mixins-with-default-interface-methods/ITimerLight.cs?name=SnippetTimerLightFinal)]

<span data-ttu-id="9fa0b-152">この変更を追加することで、`OverheadLight` クラスで、インターフェイスのサポートを宣言してタイマー関数を実装できます。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-152">By adding that change, the `OverheadLight` class can implement the timer function by declaring support for the interface:</span></span>

```csharp
public class OverheadLight : ITimerLight { }
```

<span data-ttu-id="9fa0b-153">照明の種類によっては、より高度なプロトコルがサポートされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-153">A different light type may support a more sophisticated protocol.</span></span> <span data-ttu-id="9fa0b-154">次のコードに示すように、`TurnOnFor` の独自の実装を提供できます。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-154">It can provide its own implementation for `TurnOnFor`, as shown in the following code:</span></span>

[!code-csharp[Override the timer function](./snippets/mixins-with-default-interface-methods/HalogenLight.cs?name=SnippetHalogenLight)]

<span data-ttu-id="9fa0b-155">仮想クラス メソッドのオーバーライドとは異なり、`HalogenLight` クラスの `TurnOnFor` の宣言では、`override` キーワードは使用されません。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-155">Unlike overriding virtual class methods, the declaration of `TurnOnFor` in the `HalogenLight` class does not use the `override` keyword.</span></span>

## <a name="mix-and-match-capabilities"></a><span data-ttu-id="9fa0b-156">機能の混在と対応付け</span><span class="sxs-lookup"><span data-stu-id="9fa0b-156">Mix and match capabilities</span></span>

<span data-ttu-id="9fa0b-157">より高度な機能を導入すると、既定のインターフェイス メソッドの利点が明らかになります。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-157">The advantages of default interface methods become clearer as you introduce more advanced capabilities.</span></span> <span data-ttu-id="9fa0b-158">インターフェイスを使用すると、機能を混在させて対応付けることができます。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-158">Using interfaces enables you to mix and match capabilities.</span></span> <span data-ttu-id="9fa0b-159">また、各クラスの作成者は、既定の実装とカスタム実装のいずれかを選択できるようになります。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-159">It also enables each class author to choose between the default implementation and a custom implementation.</span></span> <span data-ttu-id="9fa0b-160">点滅する照明の既定の実装を持つインターフェイスを追加してみましょう。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-160">Let's add an interface with a default implementation for a blinking light:</span></span>

[!code-csharp[Define the blinking light interface](./snippets/mixins-with-default-interface-methods/IBlinkingLight.cs?name=SnippetBlinkingLight)]

<span data-ttu-id="9fa0b-161">既定の実装では、任意の照明を点滅させることができます。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-161">The default implementation enables any light to blink.</span></span> <span data-ttu-id="9fa0b-162">天井の照明には、既定の実装を使用して、タイマーと点滅の両方の機能を追加できます。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-162">The overhead light can add both timer and blink capabilities using the default implementation:</span></span>

[!code-csharp[Use the default blink function](./snippets/mixins-with-default-interface-methods/OverheadLight.cs?name=SnippetOverheadLight)]

<span data-ttu-id="9fa0b-163">新しい照明の種類である `LEDLight` では、タイマー関数と点滅関数の両方を直接サポートします。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-163">A new light type, the `LEDLight` supports both the timer function and the blink function directly.</span></span> <span data-ttu-id="9fa0b-164">この照明のスタイルでは、`ITimerLight` と `IBlinkingLight` の両方のインターフェイスを実装し、`Blink` メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-164">This light style implements both the `ITimerLight` and `IBlinkingLight` interfaces, and overrides the `Blink` method:</span></span>

[!code-csharp[Override the blink function](./snippets/mixins-with-default-interface-methods/LEDLight.cs?name=SnippetLEDLight)]

<span data-ttu-id="9fa0b-165">`ExtraFancyLight` は、点滅とタイマーの両方の関数を直接サポートしている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-165">An `ExtraFancyLight` might support both blink and timer functions directly:</span></span>

[!code-csharp[Override the blink and timer function](./snippets/mixins-with-default-interface-methods/ExtraFancyLight.cs?name=SnippetExtraFancyLight)]

<span data-ttu-id="9fa0b-166">以前に作成した `HalogenLight` は、点滅をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-166">The `HalogenLight` you created earlier doesn't support blinking.</span></span> <span data-ttu-id="9fa0b-167">そのため、サポートされているインターフェイスの一覧に `IBlinkingLight` を追加しないでください。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-167">So, don't add the `IBlinkingLight` to the list of its supported interfaces.</span></span>

## <a name="detect-the-light-types-using-pattern-matching"></a><span data-ttu-id="9fa0b-168">パターン マッチングを使用して照明の種類を検出する</span><span class="sxs-lookup"><span data-stu-id="9fa0b-168">Detect the light types using pattern matching</span></span>

<span data-ttu-id="9fa0b-169">次に、テスト コードを書いてみましょう。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-169">Next, let's write some test code.</span></span> <span data-ttu-id="9fa0b-170">C# の[パターン マッチング](../../pattern-matching.md)機能を利用して、サポートされているインターフェイスを調べることで、照明の機能を決定することができます。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-170">You can make use of C#'s [pattern matching](../../pattern-matching.md) feature to determine a light's capabilities by examining which interfaces it supports.</span></span>  <span data-ttu-id="9fa0b-171">次のメソッドでは、各照明のサポートされている機能を実行します。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-171">The following method exercises the supported capabilities of each light:</span></span>

[!code-csharp[Test a light's capabilities](./snippets/mixins-with-default-interface-methods/Program.cs?name=SnippetTestLightFunctions)]

<span data-ttu-id="9fa0b-172">`Main` メソッドの次のコードでは、各照明の種類を順番に作成し、その照明をテストします。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-172">The following code in your `Main` method creates each light type in sequence and tests that light:</span></span>

[!code-csharp[Test a light's capabilities](./snippets/mixins-with-default-interface-methods/Program.cs?name=SnippetMainMethod)]

## <a name="how-the-compiler-determines-best-implementation"></a><span data-ttu-id="9fa0b-173">コンパイラで最適な実装を決定する方法</span><span class="sxs-lookup"><span data-stu-id="9fa0b-173">How the compiler determines best implementation</span></span>

<span data-ttu-id="9fa0b-174">このシナリオは、実装のない基底インターフェイスを示しています。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-174">This scenario shows a base interface without any implementations.</span></span> <span data-ttu-id="9fa0b-175">`ILight` インターフェイスにメソッドを追加すると、新たな複雑さが生じます。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-175">Adding a method into the `ILight` interface introduces new complexities.</span></span> <span data-ttu-id="9fa0b-176">既定のインターフェイス メソッドを管理する言語規則により、複数の派生インターフェイスを実装する具象クラスへの影響が最小限に抑えられます。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-176">The language rules governing default interface methods minimize the effect on the concrete classes that implement multiple derived interfaces.</span></span> <span data-ttu-id="9fa0b-177">元のインターフェイスを新しいメソッドで拡張して、その使用方法がどのように変わるかを説明します。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-177">Let's enhance the original interface with a new method to show how that changes its use.</span></span> <span data-ttu-id="9fa0b-178">すべてのインジケーター照明では、その電源の状態を列挙値として報告できます。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-178">Every indicator light can report its power status as an enumerated value:</span></span>

[!code-csharp[Enumeration for power status](./snippets/mixins-with-default-interface-methods/ILight.cs?name=SnippetPowerStatus)]

<span data-ttu-id="9fa0b-179">既定の実装では、電源は想定されていません。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-179">The default implementation assumes no power:</span></span>

[!code-csharp[Report a default power status](./snippets/mixins-with-default-interface-methods/ILight.cs?name=SnippetILightInterface)]

<span data-ttu-id="9fa0b-180">`ExtraFancyLight` が `ILight` インターフェイスと `ITimerLight` および `IBlinkingLight` 両方の派生インターフェイスのサポートを宣言していても、これらの変更は正常にコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-180">These changes compile cleanly, even though the `ExtraFancyLight` declares support for the `ILight` interface and both derived interfaces, `ITimerLight` and `IBlinkingLight`.</span></span> <span data-ttu-id="9fa0b-181">`ILight` インターフェイスで宣言される "最も近い" 実装は 1 つのみです。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-181">There's only one "closest" implementation declared in the `ILight` interface.</span></span> <span data-ttu-id="9fa0b-182">オーバーライドを宣言した任意のクラスは、1 つの "最も近い" 実装になります。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-182">Any class that declared an override would become the one "closest" implementation.</span></span> <span data-ttu-id="9fa0b-183">上記のクラスの例では、他の派生インターフェイスのメンバーをオーバーライドしています。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-183">You saw examples in the preceding classes that overrode the members of other derived interfaces.</span></span>

<span data-ttu-id="9fa0b-184">複数の派生インターフェイスで同じメソッドをオーバーライドすることは避けてください。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-184">Avoid overriding the same method in multiple derived interfaces.</span></span> <span data-ttu-id="9fa0b-185">このようにすると、クラスで両方の派生インターフェイスが実装されるたびに、あいまいなメソッド呼び出しが作成されます。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-185">Doing so creates an ambiguous method call whenever a class implements both derived interfaces.</span></span> <span data-ttu-id="9fa0b-186">コンパイラでは、より適切な 1 つのメソッドを選択できないため、エラーが発行されます。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-186">The compiler can't pick a single better method so it issues an error.</span></span> <span data-ttu-id="9fa0b-187">たとえば、`IBlinkingLight` と `ITimerLight` の両方で `PowerStatus` のオーバーライドが実装されている場合、`OverheadLight` にはより具体的なオーバーライドを用意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-187">For example, if both the `IBlinkingLight` and `ITimerLight` implemented an override of `PowerStatus`, the `OverheadLight` would need to provide a more specific override.</span></span> <span data-ttu-id="9fa0b-188">そうしないと、コンパイラでは 2 つの派生インターフェイスで実装を選択できません。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-188">Otherwise, the compiler can't pick between the implementations in the two derived interfaces.</span></span> <span data-ttu-id="9fa0b-189">通常、インターフェイスの定義を小さく保ち、1 つの機能に集中することで、この状況を回避できます。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-189">You can usually avoid this situation by keeping interface definitions small and focused on one feature.</span></span> <span data-ttu-id="9fa0b-190">このシナリオでは、照明の各機能は独自のインターフェイスです。複数のインターフェイスはクラスからのみ継承されます。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-190">In this scenario, each capability of a light is its own interface; multiple interfaces are only inherited by classes.</span></span>

<span data-ttu-id="9fa0b-191">このサンプルでは、クラスに混在させることができる個別の機能を定義できる 1 つのシナリオを示します。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-191">This sample shows one scenario where you can define discrete features that can be mixed into classes.</span></span> <span data-ttu-id="9fa0b-192">サポートされる機能のセットを宣言するには、クラスがサポートするインターフェイスを宣言します。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-192">You declare any set of supported functionality by declaring which interfaces a class supports.</span></span> <span data-ttu-id="9fa0b-193">仮想の既定のインターフェイス メソッドを使用すると、クラスでは、任意の、またはすべてのインターフェイス メソッドに対して異なる実装を使用または定義できます。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-193">The use of virtual default interface methods enables classes to use or define a different implementation for any or all the interface methods.</span></span> <span data-ttu-id="9fa0b-194">この言語機能によって、構築している実際のシステムをモデル化する新しい方法が提供されます。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-194">This language capability provides new ways to model the real-world systems you're building.</span></span> <span data-ttu-id="9fa0b-195">既定のインターフェイス メソッドでは、これらの機能の仮想実装を使用して、さまざまな機能を混在させて対応付けることができる関連クラスをより明確に表現できるようになります。</span><span class="sxs-lookup"><span data-stu-id="9fa0b-195">Default interface methods provide a clearer way to express related classes that may mix and match different features using virtual implementations of those capabilities.</span></span>