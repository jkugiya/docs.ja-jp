---
title: .NET ライブラリ作成者のためのオプション パターン ガイダンス
author: IEvangelist
description: .NET でライブラリ作成者としてオプション パターンを公開する方法について説明します。
ms.author: dapine
ms.date: 04/12/2021
ms.openlocfilehash: 7e1bfeadff92f5d0d979ef2d7da11d7c1b47c58d
ms.sourcegitcommit: bbc724b72fb6c978905ac715e4033efa291f84dc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2021
ms.locfileid: "107369622"
---
# <a name="options-pattern-guidance-for-net-library-authors"></a><span data-ttu-id="e718f-103">.NET ライブラリ作成者のためのオプション パターン ガイダンス</span><span class="sxs-lookup"><span data-stu-id="e718f-103">Options pattern guidance for .NET library authors</span></span>

<span data-ttu-id="e718f-104">依存関係の挿入の助けを借りて、サービスとそれに対応する構成を登録すると、"*オプション パターン*" を利用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="e718f-104">With the help of dependency injection, registering your services and their corresponding configurations can make use of the *options pattern*.</span></span> <span data-ttu-id="e718f-105">オプション パターンを使用すると、ライブラリ (およびサービス) のコンシューマーで、`TOptions` がオプション クラスである[オプション インターフェイス](options.md#options-interfaces)のインスタンスを要求できます。</span><span class="sxs-lookup"><span data-stu-id="e718f-105">The options pattern enables consumers of your library (and your services) to require instances of [options interfaces](options.md#options-interfaces) where `TOptions` is your options class.</span></span> <span data-ttu-id="e718f-106">厳密に型指定されたオブジェクトを使用して構成オプションを使用すると、一貫性のある値の表現が保証され、文字列値を手動で解析する負担がなくなります。</span><span class="sxs-lookup"><span data-stu-id="e718f-106">Consuming configuration options through strongly-typed objects helps to ensure consistent value representation, and removes the burden of manually parsing string values.</span></span> <span data-ttu-id="e718f-107">ライブラリのコンシューマーで使用する多くの[構成プロバイダー](configuration-providers.md)があります。</span><span class="sxs-lookup"><span data-stu-id="e718f-107">There are many [configuration providers](configuration-providers.md) for consumers of your library to use.</span></span> <span data-ttu-id="e718f-108">コンシューマーでこれらのプロバイダーを使用すると、さまざまな方法でライブラリを構成できます。</span><span class="sxs-lookup"><span data-stu-id="e718f-108">With these providers, consumers can configure your library in many ways.</span></span>

<span data-ttu-id="e718f-109">.NET ライブラリの作成者のために、ライブラリのコンシューマーにオプション パターンを正しく公開する方法に関する一般的なガイダンスを説明します。</span><span class="sxs-lookup"><span data-stu-id="e718f-109">As a .NET library author, you'll learn general guidance on how to correctly expose the options pattern to consumers of your library.</span></span> <span data-ttu-id="e718f-110">同じことを実現するのにさまざまな方法があり、いくつかの考慮事項があります。</span><span class="sxs-lookup"><span data-stu-id="e718f-110">There are various ways to achieve the same thing, and several considerations to make.</span></span>

## <a name="naming-conventions"></a><span data-ttu-id="e718f-111">名前付け規則</span><span class="sxs-lookup"><span data-stu-id="e718f-111">Naming conventions</span></span>

<span data-ttu-id="e718f-112">慣例により、サービスを登録する拡張メソッドの名前は `Add{Service}` であり、`{Service}` は意味のあるわかりやすい名前です。</span><span class="sxs-lookup"><span data-stu-id="e718f-112">By convention, extension methods responsible for registering services are named `Add{Service}`, where `{Service}` is a meaningful and descriptive name.</span></span> <span data-ttu-id="e718f-113">パッケージによっては、サービスの登録に `Use{Service}` 拡張メソッドが付随する場合があります。</span><span class="sxs-lookup"><span data-stu-id="e718f-113">Depending on the package, the registration of services may be accompanied by `Use{Service}` extension methods.</span></span> <span data-ttu-id="e718f-114">`Use{Service}` 拡張メソッドは、[ASP.NET Core](/aspnet) では一般的です。</span><span class="sxs-lookup"><span data-stu-id="e718f-114">The `Use{Service}` extension methods are commonplace in [ASP.NET Core](/aspnet).</span></span>

<span data-ttu-id="e718f-115">✔️ 自分のサービスと他のオファリングを明確に区別できる名前を考えます。</span><span class="sxs-lookup"><span data-stu-id="e718f-115">✔️ CONSIDER names that disambiguate your service from other offerings.</span></span>

<span data-ttu-id="e718f-116">❌ .既に NET エコシステムの一部になっている、Microsoft の公式パッケージに含まれる名前は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="e718f-116">❌ DO NOT use names that are already part of the .NET ecosystem from official Microsoft packages.</span></span>

<span data-ttu-id="e718f-117">✔️ 拡張メソッドを公開する静的クラスは、`{Type}Extensions` という名前にします。`{Type}` は拡張する型です。</span><span class="sxs-lookup"><span data-stu-id="e718f-117">✔️ CONSIDER naming static classes that expose extension methods as `{Type}Extensions`, where `{Type}` is the type that you're extending.</span></span>

### <a name="namespace-guidance"></a><span data-ttu-id="e718f-118">名前空間のガイダンス</span><span class="sxs-lookup"><span data-stu-id="e718f-118">Namespace guidance</span></span>

<span data-ttu-id="e718f-119">Microsoft のパッケージでは、`Microsoft.Extensions.DependencyInjection` 名前空間を使用して、さまざまなサービス オファリングの登録が統合されています。</span><span class="sxs-lookup"><span data-stu-id="e718f-119">Microsoft packages make use of the `Microsoft.Extensions.DependencyInjection` namespace to unify the registration of various service offerings.</span></span>

<span data-ttu-id="e718f-120">✔️ 自分のパッケージ オファリングを明確に識別できる名前空間を考えます。</span><span class="sxs-lookup"><span data-stu-id="e718f-120">✔️ CONSIDER a namespace that clearly identifies your package offering.</span></span>

<span data-ttu-id="e718f-121">❌ Microsoft が公式に認めていないパッケージには、`Microsoft.Extensions.DependencyInjection` 名前空間を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="e718f-121">❌ DO NOT use the `Microsoft.Extensions.DependencyInjection` namespace for non-official Microsoft packages.</span></span>

## <a name="parameterless"></a><span data-ttu-id="e718f-122">パラメーターなし</span><span class="sxs-lookup"><span data-stu-id="e718f-122">Parameterless</span></span>

<span data-ttu-id="e718f-123">サービスが最小限の構成または明示的ではない構成で動作できる場合は、パラメーターなしの拡張メソッドを検討します。</span><span class="sxs-lookup"><span data-stu-id="e718f-123">If your service can work with minimal or no explicit configuration, consider a parameterless extension method.</span></span>

:::code language="csharp" source="snippets/configuration/options-noparams/ServiceCollectionExtensions.cs" highlight="10-14":::

<span data-ttu-id="e718f-124">上のコードの `AddMyLibraryService` では、次のことが行われています。</span><span class="sxs-lookup"><span data-stu-id="e718f-124">In the preceding code, the `AddMyLibraryService`:</span></span>

- <span data-ttu-id="e718f-125"><xref:Microsoft.Extensions.DependencyInjection.IServiceCollection> のインスタンスを拡張します</span><span class="sxs-lookup"><span data-stu-id="e718f-125">Extends an instance of <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection></span></span>
- <span data-ttu-id="e718f-126">`LibraryOptions` の型パラメーターを使用して <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%60%601(Microsoft.Extensions.DependencyInjection.IServiceCollection)?displayProperty=nameWithType> を呼び出します</span><span class="sxs-lookup"><span data-stu-id="e718f-126">Calls <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%60%601(Microsoft.Extensions.DependencyInjection.IServiceCollection)?displayProperty=nameWithType> with the type parameter of `LibraryOptions`</span></span>
- <span data-ttu-id="e718f-127"><xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A> の呼び出しをチェーンします。ここでは、既定のオプション値を指定します</span><span class="sxs-lookup"><span data-stu-id="e718f-127">Chains a call to <xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A>, which specifies the default option values</span></span>

## <a name="iconfiguration-parameter"></a><span data-ttu-id="e718f-128">`IConfiguration` パラメーター</span><span class="sxs-lookup"><span data-stu-id="e718f-128">`IConfiguration` parameter</span></span>

<span data-ttu-id="e718f-129">多くのオプションをコンシューマーに公開するライブラリを作成するときは、`IConfiguration` パラメーター拡張メソッドが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="e718f-129">When you author a library that exposes many options to consumers, you may want to consider requiring an `IConfiguration` parameter extension method.</span></span> <span data-ttu-id="e718f-130">予想される `IConfiguration` インスタンスでは、<xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A?displayProperty=nameWithType> 関数を使用することにより、構成の名前付きセクションにスコープを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e718f-130">The expected `IConfiguration` instance should be scoped to a named section of the configuration by using the <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A?displayProperty=nameWithType> function.</span></span>

:::code language="csharp" source="snippets/configuration/options-configparam/ServiceCollectionExtensions.cs" highlight="10,12-14":::

<span data-ttu-id="e718f-131">上のコードの `AddMyLibraryService` では、次のことが行われています。</span><span class="sxs-lookup"><span data-stu-id="e718f-131">In the preceding code, the `AddMyLibraryService`:</span></span>

- <span data-ttu-id="e718f-132"><xref:Microsoft.Extensions.DependencyInjection.IServiceCollection> のインスタンスを拡張します</span><span class="sxs-lookup"><span data-stu-id="e718f-132">Extends an instance of <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection></span></span>
- <span data-ttu-id="e718f-133"><xref:Microsoft.Extensions.Configuration.IConfiguration> パラメーターの `namedConfigurationSection` を定義します</span><span class="sxs-lookup"><span data-stu-id="e718f-133">Defines an <xref:Microsoft.Extensions.Configuration.IConfiguration> parameter `namedConfigurationSection`</span></span>
- <span data-ttu-id="e718f-134">`LibraryOptions` のジェネリック型パラメーターと、構成する `namedConfigurationSection` インスタンスを渡して <xref:Microsoft.Extensions.DependencyInjection.OptionsConfigurationServiceCollectionExtensions.Configure%60%601(Microsoft.Extensions.DependencyInjection.IServiceCollection,Microsoft.Extensions.Configuration.IConfiguration)> を呼び出します</span><span class="sxs-lookup"><span data-stu-id="e718f-134">Calls <xref:Microsoft.Extensions.DependencyInjection.OptionsConfigurationServiceCollectionExtensions.Configure%60%601(Microsoft.Extensions.DependencyInjection.IServiceCollection,Microsoft.Extensions.Configuration.IConfiguration)> passing the generic type parameter of `LibraryOptions` and the `namedConfigurationSection` instance to configure</span></span>

<span data-ttu-id="e718f-135">このパターンのコンシューマーは、名前付きセクションのスコープ設定された `IConfiguration` インスタンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="e718f-135">Consumers in this pattern provide the scoped `IConfiguration` instance of the named section:</span></span>

:::code language="csharp" source="snippets/configuration/options-configparam/Program.cs" highlight="22-23":::

<span data-ttu-id="e718f-136">`.AddMyLibraryService` の呼び出しは、<xref:Microsoft.Extensions.Hosting.IHostBuilder.ConfigureServices%2A> メソッドで行われます。</span><span class="sxs-lookup"><span data-stu-id="e718f-136">The call to `.AddMyLibraryService` is made in the <xref:Microsoft.Extensions.Hosting.IHostBuilder.ConfigureServices%2A> method.</span></span> <span data-ttu-id="e718f-137">`Startup` クラスを使用する場合も同様です。登録されるサービスの追加は、`ConfigureServices` で行われます。</span><span class="sxs-lookup"><span data-stu-id="e718f-137">The same is true when using a `Startup` class, the addition of services being registered occurs in `ConfigureServices`.</span></span>

<span data-ttu-id="e718f-138">既定値を指定するかどうかは、ライブラリの作成者が決定します。</span><span class="sxs-lookup"><span data-stu-id="e718f-138">As the library author, specifying default values is up to you.</span></span>

> [!NOTE]
> <span data-ttu-id="e718f-139">構成をオプション インスタンスにバインドすることができます。</span><span class="sxs-lookup"><span data-stu-id="e718f-139">It is possible to bind configuration to an options instance.</span></span> <span data-ttu-id="e718f-140">ただし、名前が衝突してエラーが発生するリスクがあります。</span><span class="sxs-lookup"><span data-stu-id="e718f-140">However, there is a risk of name collisions - which will cause errors.</span></span> <span data-ttu-id="e718f-141">また、この方法を使用して手動でバインドするときは、オプション パターンの使用を読み取り 1 回に制限します。</span><span class="sxs-lookup"><span data-stu-id="e718f-141">Additionally, when manually binding in this way, you limit the consumption of your options pattern to read-once.</span></span> <span data-ttu-id="e718f-142">設定を変更しても再バインドされないため、コンシューマーは [IOptionsMonitor](options.md#ioptionsmonitor) インターフェイスを使用できません。</span><span class="sxs-lookup"><span data-stu-id="e718f-142">Changes to settings will not be re-bound, as such consumers will not be able to use the [IOptionsMonitor](options.md#ioptionsmonitor) interface.</span></span>
>
> ```csharp
> services.AddOptions<LibraryOptions>()
>     .Configure<IConfiguration>(
>         (options, configuration) =>
>             configuration.GetSection("LibraryOptions").Bind(options));
> ```

## <a name="actiontoptions-parameter"></a><span data-ttu-id="e718f-143">`Action<TOptions>` パラメーター</span><span class="sxs-lookup"><span data-stu-id="e718f-143">`Action<TOptions>` parameter</span></span>

<span data-ttu-id="e718f-144">ライブラリのコンシューマーは、オプション クラスのインスタンスを生成するラムダ式を提供することに関心を持つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="e718f-144">Consumers of your library may be interested in providing a lambda expression that yields an instance of your options class.</span></span> <span data-ttu-id="e718f-145">このシナリオに場合は、拡張メソッドで `Action<LibraryOptions>` パラメーターを定義します。</span><span class="sxs-lookup"><span data-stu-id="e718f-145">In this scenario, you define an `Action<LibraryOptions>` parameter in your extension method.</span></span>

:::code language="csharp" source="snippets/configuration/options-action/ServiceCollectionExtensions.cs" highlight="10,12":::

<span data-ttu-id="e718f-146">上のコードの `AddMyLibraryService` では、次のことが行われています。</span><span class="sxs-lookup"><span data-stu-id="e718f-146">In the preceding code, the `AddMyLibraryService`:</span></span>

- <span data-ttu-id="e718f-147"><xref:Microsoft.Extensions.DependencyInjection.IServiceCollection> のインスタンスを拡張します</span><span class="sxs-lookup"><span data-stu-id="e718f-147">Extends an instance of <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection></span></span>
- <span data-ttu-id="e718f-148"><xref:System.Action%601> を定義します。`T` は `LibraryOptions` パラメーターの `configureOptions` です</span><span class="sxs-lookup"><span data-stu-id="e718f-148">Defines an <xref:System.Action%601> where `T` is `LibraryOptions` parameter `configureOptions`</span></span>
- <span data-ttu-id="e718f-149">`configureOptions` アクションを指定して <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.Configure%2A> を呼び出します</span><span class="sxs-lookup"><span data-stu-id="e718f-149">Calls <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.Configure%2A> given the `configureOptions` action</span></span>

<span data-ttu-id="e718f-150">このパターンのコンシューマーは、ラムダ式 (または、`Action<LibraryOptions>` パラメーターを満たすデリゲート) を提供します。</span><span class="sxs-lookup"><span data-stu-id="e718f-150">Consumers in this pattern provide a lambda expression (or a delegate that satisfies the `Action<LibraryOptions>` parameter):</span></span>

:::code language="csharp" source="snippets/configuration/options-action/Program.cs" highlight="22-26":::

## <a name="options-instance-parameter"></a><span data-ttu-id="e718f-151">オプション インスタンスのパラメーター</span><span class="sxs-lookup"><span data-stu-id="e718f-151">Options instance parameter</span></span>

<span data-ttu-id="e718f-152">ライブラリのコンシューマーは、インラインのオプション インスタンスを使用することを好む場合があります。</span><span class="sxs-lookup"><span data-stu-id="e718f-152">Consumers of your library might prefer to provide an inlined options instance.</span></span> <span data-ttu-id="e718f-153">このシナリオの場合は、オプション オブジェクト `LibraryOptions` のインスタンスを受け取る拡張メソッドを公開します。</span><span class="sxs-lookup"><span data-stu-id="e718f-153">In this scenario, you expose an extension method that takes an instance of your options object, `LibraryOptions`.</span></span>

:::code language="csharp" source="snippets/configuration/options-object/ServiceCollectionExtensions.cs" highlight="9,11-17":::

<span data-ttu-id="e718f-154">上のコードの `AddMyLibraryService` では、次のことが行われています。</span><span class="sxs-lookup"><span data-stu-id="e718f-154">In the preceding code, the `AddMyLibraryService`:</span></span>

- <span data-ttu-id="e718f-155"><xref:Microsoft.Extensions.DependencyInjection.IServiceCollection> のインスタンスを拡張します</span><span class="sxs-lookup"><span data-stu-id="e718f-155">Extends an instance of <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection></span></span>
- <span data-ttu-id="e718f-156">`LibraryOptions` の型パラメーターを使用して <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%60%601(Microsoft.Extensions.DependencyInjection.IServiceCollection)?displayProperty=nameWithType> を呼び出します</span><span class="sxs-lookup"><span data-stu-id="e718f-156">Calls <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%60%601(Microsoft.Extensions.DependencyInjection.IServiceCollection)?displayProperty=nameWithType> with the type parameter of `LibraryOptions`</span></span>
- <span data-ttu-id="e718f-157"><xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.Configure%2A> の呼び出しをチェーンします。そこでは、特定の `userOptions` インスタンスからオーバーライドできる既定のオプション値を指定します</span><span class="sxs-lookup"><span data-stu-id="e718f-157">Chains a call to <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.Configure%2A>, which specifies default option values that can be overridden from the given `userOptions` instance</span></span>

<span data-ttu-id="e718f-158">このパターンのコンシューマーは、`LibraryOptions` クラスのインスタンスを提供し、必要なプロパティ値をインラインで定義します。</span><span class="sxs-lookup"><span data-stu-id="e718f-158">Consumers in this pattern provide an instance of the `LibraryOptions` class, defining desired property values inline:</span></span>

:::code language="csharp" source="snippets/configuration/options-object/Program.cs" highlight="22-26":::

## <a name="post-configuration"></a><span data-ttu-id="e718f-159">構成後</span><span class="sxs-lookup"><span data-stu-id="e718f-159">Post configuration</span></span>

<span data-ttu-id="e718f-160">すべての構成オプション値をバインドまたは指定すると、事後構成の機能を使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="e718f-160">After all configuration option values are bound or specified, post configuration functionality is available.</span></span> <span data-ttu-id="e718f-161">前に詳しく説明したのと同じ [`Action<TOptions>` パラメーター](#actiontoptions-parameter)を公開すると、<xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigure%2A> を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="e718f-161">Exposing the same [`Action<TOptions>` parameter](#actiontoptions-parameter) detailed earlier, you could choose to call <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigure%2A>.</span></span> <span data-ttu-id="e718f-162">事後構成は、`.Configure` のすべての呼び出しの後に実行されます。</span><span class="sxs-lookup"><span data-stu-id="e718f-162">Post configure runs after all `.Configure` calls.</span></span>

:::code language="csharp" source="snippets/configuration/options-postconfig/ServiceCollectionExtensions.cs" highlight="10,12":::

<span data-ttu-id="e718f-163">上のコードの `AddMyLibraryService` では、次のことが行われています。</span><span class="sxs-lookup"><span data-stu-id="e718f-163">In the preceding code, the `AddMyLibraryService`:</span></span>

- <span data-ttu-id="e718f-164"><xref:Microsoft.Extensions.DependencyInjection.IServiceCollection> のインスタンスを拡張します</span><span class="sxs-lookup"><span data-stu-id="e718f-164">Extends an instance of <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection></span></span>
- <span data-ttu-id="e718f-165"><xref:System.Action%601> を定義します。`T` は `LibraryOptions` パラメーターの `configureOptions` です</span><span class="sxs-lookup"><span data-stu-id="e718f-165">Defines an <xref:System.Action%601> where `T` is `LibraryOptions` parameter `configureOptions`</span></span>
- <span data-ttu-id="e718f-166">`configureOptions` アクションを指定して <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigure%2A> を呼び出します</span><span class="sxs-lookup"><span data-stu-id="e718f-166">Calls <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigure%2A> given the `configureOptions` action</span></span>

<span data-ttu-id="e718f-167">このパターンのコンシューマーは、事後構成ではないシナリオの [`Action<TOptions>` パラメーター] と同様に、ラムダ式 (または、`Action<LibraryOptions>` パラメーターを満たすデリゲート) を提供します。</span><span class="sxs-lookup"><span data-stu-id="e718f-167">Consumers in this pattern provide a lambda expression (or a delegate that satisfies the `Action<LibraryOptions>` parameter), just as they would with the [`Action<TOptions>` parameter] in a non-post configuration scenario:</span></span>

:::code language="csharp" source="snippets/configuration/options-postconfig/Program.cs" highlight="22-26":::

## <a name="see-also"></a><span data-ttu-id="e718f-168">関連項目</span><span class="sxs-lookup"><span data-stu-id="e718f-168">See also</span></span>

- [<span data-ttu-id="e718f-169">.NET でのオプション パターン</span><span class="sxs-lookup"><span data-stu-id="e718f-169">Options pattern in .NET</span></span>](options.md)
- [<span data-ttu-id="e718f-170">.NET での依存関係の挿入</span><span class="sxs-lookup"><span data-stu-id="e718f-170">Dependency injection in .NET</span></span>](dependency-injection.md)
- [<span data-ttu-id="e718f-171">依存関係の挿入のガイドライン</span><span class="sxs-lookup"><span data-stu-id="e718f-171">Dependency injection guidelines</span></span>](dependency-injection-guidelines.md)
