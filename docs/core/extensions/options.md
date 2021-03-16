---
title: .NET でのオプション パターン
author: IEvangelist
description: .NET アプリで関連のある設定のグループを表すオプション パターンを使用する方法について説明します。
ms.author: dapine
ms.date: 02/18/2021
ms.openlocfilehash: df30928cdb1832e94f89abbdf8cc41e1304f8e2e
ms.sourcegitcommit: bdbf6472de867a0a11aaa5b9384a2506c24f27d2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2021
ms.locfileid: "102402166"
---
# <a name="options-pattern-in-net"></a><span data-ttu-id="3d8aa-103">.NET でのオプション パターン</span><span class="sxs-lookup"><span data-stu-id="3d8aa-103">Options pattern in .NET</span></span>

<span data-ttu-id="3d8aa-104">オプション パターンでは、クラスを使用して、関連する設定のグループへの、厳密に型指定されたアクセスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-104">The options pattern uses classes to provide strongly-typed access to groups of related settings.</span></span> <span data-ttu-id="3d8aa-105">[構成設定](configuration.md)がシナリオ別に個々のクラスに分離されるとき、アプリは次の 2 つの重要なソフトウェア エンジニアリング原則に従います。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-105">When [configuration settings](configuration.md) are isolated by scenario into separate classes, the app adheres to two important software engineering principles:</span></span>

- <span data-ttu-id="3d8aa-106">[インターフェイス分離の原則 (ISP) またはカプセル化](../../architecture/modern-web-apps-azure/architectural-principles.md#encapsulation): 使用する構成設定のみに依存するシナリオ (クラス)。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-106">The [Interface Segregation Principle (ISP) or Encapsulation](../../architecture/modern-web-apps-azure/architectural-principles.md#encapsulation): Scenarios (classes) that depend on configuration settings depend only on the configuration settings that they use.</span></span>
- <span data-ttu-id="3d8aa-107">[懸念事項の分離](../../architecture/modern-web-apps-azure/architectural-principles.md#separation-of-concerns): アプリのさまざまな部分の設定は、互いに依存していないか、結合されていない。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-107">[Separation of Concerns](../../architecture/modern-web-apps-azure/architectural-principles.md#separation-of-concerns): Settings for different parts of the app aren't dependent or coupled to one another.</span></span>

<span data-ttu-id="3d8aa-108">構成データを検証するメカニズムもオプションによって提供されます。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-108">Options also provide a mechanism to validate configuration data.</span></span> <span data-ttu-id="3d8aa-109">詳しくは、「[オプションの検証](#options-validation)」セクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-109">For more information, see the [Options validation](#options-validation) section.</span></span>

## <a name="bind-hierarchical-configuration"></a><span data-ttu-id="3d8aa-110">階層的な構成をバインドする</span><span class="sxs-lookup"><span data-stu-id="3d8aa-110">Bind hierarchical configuration</span></span>

<span data-ttu-id="3d8aa-111">関連する構成値を読み取る方法としては、オプション パターンを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-111">The preferred way to read related configuration values is using the options pattern.</span></span> <span data-ttu-id="3d8aa-112">オプション パターンは、<xref:Microsoft.Extensions.Options.IOptions%601> インターフェイスを通して使用できます。ジェネリック型パラメーター `TOptions` は、`class` に制限されます。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-112">The options pattern is possible through the <xref:Microsoft.Extensions.Options.IOptions%601> interface, where the generic type parameter `TOptions` is constrained to `class`.</span></span> <span data-ttu-id="3d8aa-113">後で、依存関係の挿入により `IOptions<TOptions>` を提供できます。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-113">The `IOptions<TOptions>` can later be provided through dependency injection.</span></span> <span data-ttu-id="3d8aa-114">詳細については、「[.NET での依存関係の挿入](dependency-injection.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-114">For more information, see [Dependency injection in .NET](dependency-injection.md).</span></span>

<span data-ttu-id="3d8aa-115">たとえば、以下の構成値を読み取るには、次のようにします:</span><span class="sxs-lookup"><span data-stu-id="3d8aa-115">For example, to read the following configuration values:</span></span>

:::code language="json" source="snippets/configuration/console-json/appsettings.json" range="3-6":::

<span data-ttu-id="3d8aa-116">次の `TransientFaultHandlingOptions` クラスを作成します:</span><span class="sxs-lookup"><span data-stu-id="3d8aa-116">Create the following `TransientFaultHandlingOptions` class:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/TransientFaultHandlingOptions.cs" range="5-9":::

<span data-ttu-id="3d8aa-117"><span id="options-class"></span> オプション パターンを使用する場合、オプション クラスは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-117"><span id="options-class"></span> When using the options pattern, an options class:</span></span>

- <span data-ttu-id="3d8aa-118">パラメーターなしのパブリック コンストラクターを持った非抽象でなければなりません</span><span class="sxs-lookup"><span data-stu-id="3d8aa-118">Must be non-abstract with a public parameterless constructor</span></span>
- <span data-ttu-id="3d8aa-119">バインドする読み取り/書き込みのパブリック プロパティが含まれます (フィールドはバインド "***されません***")</span><span class="sxs-lookup"><span data-stu-id="3d8aa-119">Contain public read-write properties to bind (fields are ***not*** bound)</span></span>

<span data-ttu-id="3d8aa-120">コード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-120">The following code:</span></span>

* <span data-ttu-id="3d8aa-121">[ConfigurationBinder.Bind](xref:Microsoft.Extensions.Configuration.ConfigurationBinder.Bind%2A) を呼び出して、`TransientFaultHandlingOptions` クラスを `"TransientFaultHandlingOptions"` セクションにバインドします。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-121">Calls [ConfigurationBinder.Bind](xref:Microsoft.Extensions.Configuration.ConfigurationBinder.Bind%2A) to bind the `TransientFaultHandlingOptions` class to the `"TransientFaultHandlingOptions"` section.</span></span>
* <span data-ttu-id="3d8aa-122">構成データを表示します。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-122">Displays the configuration data.</span></span>

:::code language="csharp" source="snippets/configuration/console-json/Program.cs" range="31-38":::

<span data-ttu-id="3d8aa-123">上記のコードでは、アプリが開始された後の JSON 構成ファイルへの変更が読み取られます。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-123">In the preceding code, changes to the JSON configuration file after the app has started are read.</span></span>

<span data-ttu-id="3d8aa-124">[`ConfigurationBinder.Get<T>`](xref:Microsoft.Extensions.Configuration.ConfigurationBinder.Get%2A) 指定された型をバインドして返します。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-124">[`ConfigurationBinder.Get<T>`](xref:Microsoft.Extensions.Configuration.ConfigurationBinder.Get%2A) binds and returns the specified type.</span></span> <span data-ttu-id="3d8aa-125">`ConfigurationBinder.Get<T>` は `ConfigurationBinder.Bind` を使用するよりも便利な場合があります。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-125">`ConfigurationBinder.Get<T>` may be more convenient than using `ConfigurationBinder.Bind`.</span></span> <span data-ttu-id="3d8aa-126">次のコードは、`TransientFaultHandlingOptions` クラスで `ConfigurationBinder.Get<T>` を使用する方法を示しています:</span><span class="sxs-lookup"><span data-stu-id="3d8aa-126">The following code shows how to use `ConfigurationBinder.Get<T>` with the `TransientFaultHandlingOptions` class:</span></span>

```csharp
IConfigurationRoot configurationRoot = configuration.Build();

var options =
    configurationRoot.GetSection(nameof(TransientFaultHandlingOptions))
                     .Get<TransientFaultHandlingOptions>();

Console.WriteLine($"TransientFaultHandlingOptions.Enabled={options.Enabled}");
Console.WriteLine($"TransientFaultHandlingOptions.AutoRetryDelay={options.AutoRetryDelay}");
```

<span data-ttu-id="3d8aa-127">上記のコードでは、アプリが開始された後の JSON 構成ファイルへの変更が読み取られます。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-127">In the preceding code, changes to the JSON configuration file after the app has started are read.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3d8aa-128"><xref:Microsoft.Extensions.Configuration.ConfigurationBinder> クラスにより、`class` に制約 "***されない***" API がいくつか公開されます (`.Bind(object instance)` や `.Get<T>()` など)。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-128">The <xref:Microsoft.Extensions.Configuration.ConfigurationBinder> class exposes several APIs, such as `.Bind(object instance)` and `.Get<T>()` that are ***not*** constrained to `class`.</span></span> <span data-ttu-id="3d8aa-129">いずれかの[オプション インターフェイス](#options-interfaces)を使用するときは、前に説明した[オプション クラスの制約](#options-class)に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-129">When using any of the [Options interfaces](#options-interfaces), you must adhere to aforementioned [options class constraints](#options-class).</span></span>

<span data-ttu-id="3d8aa-130">オプション パターンを使用するときのもう 1 つの方法は、`"TransientFaultHandlingOptions"` セクションをバインドし、それを[依存関係挿入サービス コンテナー](dependency-injection.md)に追加することです。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-130">An alternative approach when using the options pattern is to bind the `"TransientFaultHandlingOptions"` section and add it to the [dependency injection service container](dependency-injection.md).</span></span> <span data-ttu-id="3d8aa-131">次のコードでは、`TransientFaultHandlingOptions` は <xref:Microsoft.Extensions.DependencyInjection.OptionsConfigurationServiceCollectionExtensions.Configure%2A> でサービスコンテナーに追加され、構成にバインドされます:</span><span class="sxs-lookup"><span data-stu-id="3d8aa-131">In the following code, `TransientFaultHandlingOptions` is added to the service container with <xref:Microsoft.Extensions.DependencyInjection.OptionsConfigurationServiceCollectionExtensions.Configure%2A> and bound to configuration:</span></span>

```csharp
services.Configure<TransientFaultHandlingOptions>(
    configurationRoot.GetSection(
        key: nameof(TransientFaultHandlingOptions)));
```

> [!TIP]
> <span data-ttu-id="3d8aa-132">`key` パラメーターは、検索する構成セクションの名前です。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-132">The `key` parameter is the name of the configuration section to search for.</span></span> <span data-ttu-id="3d8aa-133">それを表す型の名前と一致する必要は "*ありません*"。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-133">It does *not* have to match the name of the type that represents it.</span></span> <span data-ttu-id="3d8aa-134">たとえば、`"FaultHandling"` という名前のセクションを使用し、`TransientFaultHandlingOptions` クラスによってそれを表すことができます。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-134">For example, you could have a section named `"FaultHandling"` and it could be represented by the `TransientFaultHandlingOptions` class.</span></span> <span data-ttu-id="3d8aa-135">この場合は、代わりに `"FaultHandling"` を <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> 関数に渡します。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-135">In this instance, you'd pass `"FaultHandling"` to the <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> function instead.</span></span> <span data-ttu-id="3d8aa-136">`nameof` 演算子は、名前付きセクションとそれが対応する型が一致する場合に使用すると便利です。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-136">The `nameof` operator is used as a convenience when the named section matches the type it corresponds to.</span></span>

<span data-ttu-id="3d8aa-137">下記のコードは、上記のコードを使用して位置オプションを読み取ります:</span><span class="sxs-lookup"><span data-stu-id="3d8aa-137">Using the preceding code, the following code reads the position options:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/ExampleService.cs":::

<span data-ttu-id="3d8aa-138">上のコードでは、アプリが開始された後の JSON 構成ファイルへの変更は読み取られ ***ません***。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-138">In the preceding code, changes to the JSON configuration file after the app has started are ***not*** read.</span></span> <span data-ttu-id="3d8aa-139">アプリの開始後に変更を読み取るには、[IOptionsSnapshot](#use-ioptionssnapshot-to-read-updated-data) を使用します。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-139">To read changes after the app has started, use [IOptionsSnapshot](#use-ioptionssnapshot-to-read-updated-data).</span></span>

## <a name="options-interfaces"></a><span data-ttu-id="3d8aa-140">オプションのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="3d8aa-140">Options interfaces</span></span>

<span data-ttu-id="3d8aa-141"><xref:Microsoft.Extensions.Options.IOptions%601>:</span><span class="sxs-lookup"><span data-stu-id="3d8aa-141"><xref:Microsoft.Extensions.Options.IOptions%601>:</span></span>

- <span data-ttu-id="3d8aa-142">サポートされて "***いません***"。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-142">Does ***not*** support:</span></span>
  - <span data-ttu-id="3d8aa-143">アプリが開始された後の構成データの読み取り。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-143">Reading of configuration data after the app has started.</span></span>
  - [<span data-ttu-id="3d8aa-144">名前付きオプション</span><span class="sxs-lookup"><span data-stu-id="3d8aa-144">Named options</span></span>](#named-options-support-using-iconfigurenamedoptions)
- <span data-ttu-id="3d8aa-145">[シングルトン](dependency-injection.md#singleton)として登録されており、任意の[サービスの有効期間](dependency-injection.md#service-lifetimes)に挿入できます。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-145">Is registered as a [Singleton](dependency-injection.md#singleton) and can be injected into any [service lifetime](dependency-injection.md#service-lifetimes).</span></span>

<span data-ttu-id="3d8aa-146"><xref:Microsoft.Extensions.Options.IOptionsSnapshot%601>:</span><span class="sxs-lookup"><span data-stu-id="3d8aa-146"><xref:Microsoft.Extensions.Options.IOptionsSnapshot%601>:</span></span>

- <span data-ttu-id="3d8aa-147">[スコープ指定または一時的な有効期間](dependency-injection.md#service-lifetimes)において、すべての挿入解決でオプションを再計算する必要がある場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-147">Is useful in scenarios where options should be recomputed on every injection resolution, in [scoped or transient lifetimes](dependency-injection.md#service-lifetimes).</span></span> <span data-ttu-id="3d8aa-148">詳細については、「[IOptionsSnapshot を使用して更新データを読み取る](#use-ioptionssnapshot-to-read-updated-data)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-148">For more information, see [Use IOptionsSnapshot to read updated data](#use-ioptionssnapshot-to-read-updated-data).</span></span>
- <span data-ttu-id="3d8aa-149">[スコープ](dependency-injection.md#scoped)として登録されているため、シングルトン サービスには挿入できません。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-149">Is registered as [Scoped](dependency-injection.md#scoped) and therefore cannot be injected into a Singleton service.</span></span>
- <span data-ttu-id="3d8aa-150">[名前付きオプション](#named-options-support-using-iconfigurenamedoptions)をサポートします。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-150">Supports [named options](#named-options-support-using-iconfigurenamedoptions)</span></span>

<span data-ttu-id="3d8aa-151"><xref:Microsoft.Extensions.Options.IOptionsMonitor%601>:</span><span class="sxs-lookup"><span data-stu-id="3d8aa-151"><xref:Microsoft.Extensions.Options.IOptionsMonitor%601>:</span></span>

- <span data-ttu-id="3d8aa-152">オプションを取得し、`TOptions` インスタンスのオプション通知を管理するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-152">Is used to retrieve options and manage options notifications for `TOptions` instances.</span></span>
- <span data-ttu-id="3d8aa-153">[シングルトン](dependency-injection.md#singleton)として登録されており、任意の[サービスの有効期間](dependency-injection.md#service-lifetimes)に挿入できます。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-153">Is registered as a [Singleton](dependency-injection.md#singleton) and can be injected into any [service lifetime](dependency-injection.md#service-lifetimes).</span></span>
- <span data-ttu-id="3d8aa-154">サポートするものは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-154">Supports:</span></span>
  - <span data-ttu-id="3d8aa-155">変更通知</span><span class="sxs-lookup"><span data-stu-id="3d8aa-155">Change notifications</span></span>
  - [<span data-ttu-id="3d8aa-156">名前付きオプション</span><span class="sxs-lookup"><span data-stu-id="3d8aa-156">Named options</span></span>](#named-options-support-using-iconfigurenamedoptions)
  - [<span data-ttu-id="3d8aa-157">再読み込み可能な構成</span><span class="sxs-lookup"><span data-stu-id="3d8aa-157">Reloadable configuration</span></span>](#use-ioptionssnapshot-to-read-updated-data)
  - <span data-ttu-id="3d8aa-158">選択的なオプションの無効化 (<xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601>)</span><span class="sxs-lookup"><span data-stu-id="3d8aa-158">Selective options invalidation (<xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601>)</span></span>

<span data-ttu-id="3d8aa-159"><xref:Microsoft.Extensions.Options.IOptionsFactory%601> は、新しいオプション インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-159"><xref:Microsoft.Extensions.Options.IOptionsFactory%601> is responsible for creating new options instances.</span></span> <span data-ttu-id="3d8aa-160"><xref:Microsoft.Extensions.Options.IOptionsFactory%601.Create%2A> メソッドが 1 つ含まれています。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-160">It has a single <xref:Microsoft.Extensions.Options.IOptionsFactory%601.Create%2A> method.</span></span> <span data-ttu-id="3d8aa-161">既定の実装では、登録されている <xref:Microsoft.Extensions.Options.IConfigureOptions%601> と <xref:Microsoft.Extensions.Options.IPostConfigureOptions%601> がすべて受け取られ、先にすべての構成を実行し、その後、ポスト構成を実行します。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-161">The default implementation takes all registered <xref:Microsoft.Extensions.Options.IConfigureOptions%601> and <xref:Microsoft.Extensions.Options.IPostConfigureOptions%601> and runs all the configurations first, followed by the post-configuration.</span></span> <span data-ttu-id="3d8aa-162"><xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> と <xref:Microsoft.Extensions.Options.IConfigureOptions%601> が区別され、適切なインターフェイスのみが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-162">It distinguishes between <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> and <xref:Microsoft.Extensions.Options.IConfigureOptions%601> and only calls the appropriate interface.</span></span>

<span data-ttu-id="3d8aa-163"><xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601> は <xref:Microsoft.Extensions.Options.IOptionsMonitor%601> によって使用され、`TOptions` インスタンスをキャッシュします。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-163"><xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601> is used by <xref:Microsoft.Extensions.Options.IOptionsMonitor%601> to cache `TOptions` instances.</span></span> <span data-ttu-id="3d8aa-164"><xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601> は、値が再計算されるよう、モニターのオプション インスタンスを無効にします (<xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.TryRemove%2A>)。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-164">The <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601> invalidates options instances in the monitor so that the value is recomputed (<xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.TryRemove%2A>).</span></span> <span data-ttu-id="3d8aa-165"><xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.TryAdd%2A> を利用し、手動で値を入力できます。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-165">Values can be manually introduced with <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.TryAdd%2A>.</span></span> <span data-ttu-id="3d8aa-166"><xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.Clear%2A> メソッドは、すべての名前付きインスタンスをオンデマンドで再作成するときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-166">The <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.Clear%2A> method is used when all named instances should be recreated on demand.</span></span>

### <a name="options-interfaces-benefits"></a><span data-ttu-id="3d8aa-167">オプション インターフェイスの利点</span><span class="sxs-lookup"><span data-stu-id="3d8aa-167">Options interfaces benefits</span></span>

<span data-ttu-id="3d8aa-168">ジェネリック ラッパー型を使用すると、オプションの有効期間を DI コンテナーから切り離すことができます。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-168">Using a generic wrapper type gives you the ability to decouple the lifetime of the option from the DI container.</span></span> <span data-ttu-id="3d8aa-169"><xref:Microsoft.Extensions.Options.IOptions%601.Value?displayProperty=nameWithType> インターフェイスにより、ジェネリック制約を含む抽象レイヤーがオプションの型に提供されます。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-169">The <xref:Microsoft.Extensions.Options.IOptions%601.Value?displayProperty=nameWithType> interface provides a layer of abstraction, including generic constraints, on your options type.</span></span> <span data-ttu-id="3d8aa-170">これには次のようなメリットがあります。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-170">This provides the following benefits:</span></span>

- <span data-ttu-id="3d8aa-171">`T` 構成インスタンスの評価が、挿入時ではなく、<xref:Microsoft.Extensions.Options.IOptions%601.Value?displayProperty=nameWithType> のアクセスまで遅延されます。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-171">The evaluation of the `T` configuration instance is deferred to the accessing of <xref:Microsoft.Extensions.Options.IOptions%601.Value?displayProperty=nameWithType>, rather than when it is injected.</span></span> <span data-ttu-id="3d8aa-172">これは、さまざまな場所から `T` オプションを使用でき、`T` について何も変更せずに有効期間のセマンティクスを選択できるため、重要なことです。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-172">This is important because you can consume the `T` option from various places and choose the lifetime semantics without changing anything about `T`.</span></span>
- <span data-ttu-id="3d8aa-173">`T` 型のオプションを登録するときに、`T` 型を明示的に登録する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-173">When registering options of type `T`, you do not need to explicitly register the `T` type.</span></span> <span data-ttu-id="3d8aa-174">これは、簡単な既定値を使用して[ライブラリを作成](options-library-authors.md)していて、特定の有効期間での DI コンテナーへのオプションの登録を呼び出し元に強制したくない場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-174">This is a convenience when you're [authoring a library](options-library-authors.md) with simple defaults, and you don't want to force the caller to register options into the DI container with a specific lifetime.</span></span>
- <span data-ttu-id="3d8aa-175">API の観点からは、それにより `T` 型への制約に対応できます (この例では、`T` は参照型に制約されます)。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-175">From the perspective of the API, it allows for constraints on the type `T` (in this case, `T` is constrained to a reference type).</span></span>

## <a name="use-ioptionssnapshot-to-read-updated-data"></a><span data-ttu-id="3d8aa-176">IOptionsSnapshot を使用して更新データを読み取る</span><span class="sxs-lookup"><span data-stu-id="3d8aa-176">Use IOptionsSnapshot to read updated data</span></span>

<span data-ttu-id="3d8aa-177"><xref:Microsoft.Extensions.Options.IOptionsSnapshot%601> を使用すると、オプションは要求ごとにアクセス時に 1 回計算され、要求の有効期間中キャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-177">When you use <xref:Microsoft.Extensions.Options.IOptionsSnapshot%601>, options are computed once per request when accessed and are cached for the lifetime of the request.</span></span> <span data-ttu-id="3d8aa-178">更新された構成値の読み取りをサポートする構成プロバイダーを使用しているとき、構成の変更は、アプリの開始後に読み取られます。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-178">Changes to the configuration are read after the app starts when using configuration providers that support reading updated configuration values.</span></span>

<span data-ttu-id="3d8aa-179">`IOptionsMonitor` と `IOptionsSnapshot` の違いは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-179">The difference between `IOptionsMonitor` and `IOptionsSnapshot` is that:</span></span>

- <span data-ttu-id="3d8aa-180">`IOptionsMonitor` は常に最新のオプション値を取得する[シングルトン サービス](dependency-injection.md#singleton) です。これは、シングルトンの依存関係で特に便利です。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-180">`IOptionsMonitor` is a [singleton service](dependency-injection.md#singleton) that retrieves current option values at any time, which is especially useful in singleton dependencies.</span></span>
- <span data-ttu-id="3d8aa-181">`IOptionsSnapshot` は[スコープ サービス](dependency-injection.md#scoped) であり、`IOptionsSnapshot<T>` オブジェクトの構築時にオプションのスナップショットを提供します。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-181">`IOptionsSnapshot` is a [scoped service](dependency-injection.md#scoped) and provides a snapshot of the options at the time the `IOptionsSnapshot<T>` object is constructed.</span></span> <span data-ttu-id="3d8aa-182">オプションのスナップショットは、一時的な依存関係およびスコープのある依存関係で使用されるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-182">Options snapshots are designed for use with transient and scoped dependencies.</span></span>

<span data-ttu-id="3d8aa-183">次のコードでは <xref:Microsoft.Extensions.Options.IOptionsSnapshot%601> を使用します。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-183">The following code uses <xref:Microsoft.Extensions.Options.IOptionsSnapshot%601>.</span></span>

:::code language="csharp" source="snippets/configuration/console-json/ScopedService.cs":::

<span data-ttu-id="3d8aa-184">次のコードは、`TransientFaultHandlingOptions` のバインド先となる構成インスタンスを登録します。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-184">The following code registers a configuration instance which `TransientFaultHandlingOptions` binds against:</span></span>

```csharp
services.Configure<TransientFaultHandlingOptions>(
    configurationRoot.GetSection(
        nameof(TransientFaultHandlingOptions)));
```

<span data-ttu-id="3d8aa-185">上記のコードでは、アプリが開始された後の JSON 構成ファイルへの変更が読み取られます。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-185">In the preceding code, changes to the JSON configuration file after the app has started are read.</span></span>

## <a name="ioptionsmonitor"></a><span data-ttu-id="3d8aa-186">IOptionsMonitor</span><span class="sxs-lookup"><span data-stu-id="3d8aa-186">IOptionsMonitor</span></span>

<span data-ttu-id="3d8aa-187">次のコードは、`TransientFaultHandlingOptions` のバインド先となる構成インスタンスを登録します。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-187">The following code registers a configuration instance which `TransientFaultHandlingOptions` binds against.</span></span>

```csharp
services.Configure<TransientFaultHandlingOptions>(
    configurationRoot.GetSection(
        nameof(TransientFaultHandlingOptions)));
```

<span data-ttu-id="3d8aa-188"><xref:Microsoft.Extensions.Options.IOptionsMonitor%601> の使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-188">The following example uses <xref:Microsoft.Extensions.Options.IOptionsMonitor%601>:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/MonitorService.cs":::

<span data-ttu-id="3d8aa-189">上記のコードでは、アプリが開始された後の JSON 構成ファイルへの変更が読み取られます。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-189">In the preceding code, changes to the JSON configuration file after the app has started are read.</span></span>

## <a name="named-options-support-using-iconfigurenamedoptions"></a><span data-ttu-id="3d8aa-190">IConfigureNamedOptions を使用した名前付きオプションのサポート</span><span class="sxs-lookup"><span data-stu-id="3d8aa-190">Named options support using IConfigureNamedOptions</span></span>

<span data-ttu-id="3d8aa-191">名前付きオプション:</span><span class="sxs-lookup"><span data-stu-id="3d8aa-191">Named options:</span></span>

- <span data-ttu-id="3d8aa-192">複数の構成セクションが同じプロパティにバインドされている場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-192">Are useful when multiple configuration sections bind to the same properties.</span></span>
- <span data-ttu-id="3d8aa-193">大文字と小文字の区別があります。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-193">Are case-sensitive.</span></span>

<span data-ttu-id="3d8aa-194">以下の *appsettings.json* ファイルについて考えます:</span><span class="sxs-lookup"><span data-stu-id="3d8aa-194">Consider the following *appsettings.json* file:</span></span>

```json
{
  "Features": {
    "Personalize": {
      "Enabled": true,
      "ApiKey": "aGEgaGEgeW91IHRob3VnaHQgdGhhdCB3YXMgcmVhbGx5IHNvbWV0aGluZw=="
    },
    "WeatherStation": {
      "Enabled": true,
      "ApiKey": "QXJlIHlvdSBhdHRlbXB0aW5nIHRvIGhhY2sgdXM/"
    }
  }
}
```

<span data-ttu-id="3d8aa-195">`Features:Personalize` と `Features:WeatherStation` をバインドする 2 つのクラスを作成するのではなく、各セクションに対して次のクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-195">Rather than creating two classes to bind `Features:Personalize` and `Features:WeatherStation`, the following class is used for each section:</span></span>

```csharp
public class Features
{
    public const string Personalize = nameof(Personalize);
    public const string WeatherStation = nameof(WeatherStation);

    public bool Enabled { get; set; }
    public string ApiKey { get; set; }
}
```

<span data-ttu-id="3d8aa-196">次のコードは、名前付きオプションを構成します。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-196">The following code configures the named options:</span></span>

```csharp
ConfigureServices(services =>
{
    services.Configure<Features>(
        Features.Personalize,
        Configuration.GetSection("Features:Personalize"));

    services.Configure<Features>(
        Features.WeatherStation,
        Configuration.GetSection("Features:WeatherStation"));
});
```

<span data-ttu-id="3d8aa-197">次のコードは、名前付きオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-197">The following code displays the named options:</span></span>

```csharp
public class Service
{
    private readonly Features _personalizeFeature;
    private readonly Features _weatherStationFeature;

    public Service(IOptionsSnapshot<Features> namedOptionsAccessor)
    {
        _personalizeFeature = namedOptionsAccessor.Get(Features.Personalize);
        _weatherStationFeature = namedOptionsAccessor.Get(Features.WeatherStation);
    }
}
```

<span data-ttu-id="3d8aa-198">すべてのオプションが名前付きインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-198">All options are named instances.</span></span> <span data-ttu-id="3d8aa-199"><xref:Microsoft.Extensions.Options.IConfigureOptions%601> インスタンスは、`string.Empty` である、`Options.DefaultName` インスタンスを対象とするものとして処理されます。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-199"><xref:Microsoft.Extensions.Options.IConfigureOptions%601> instances are treated as targeting the `Options.DefaultName` instance, which is `string.Empty`.</span></span> <span data-ttu-id="3d8aa-200"><xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> はまた、<xref:Microsoft.Extensions.Options.IConfigureOptions%601> を実装します。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-200"><xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> also implements <xref:Microsoft.Extensions.Options.IConfigureOptions%601>.</span></span> <span data-ttu-id="3d8aa-201"><xref:Microsoft.Extensions.Options.IOptionsFactory%601> の既定の実装には、それぞれを適切に使用するロジックがあります。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-201">The default implementation of the <xref:Microsoft.Extensions.Options.IOptionsFactory%601> has logic to use each appropriately.</span></span> <span data-ttu-id="3d8aa-202">名前付きオプション `null` は、特定の名前付きインスタンスではなく、すべての名前付きインスタンスを対象とするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-202">The `null` named option is used to target all of the named instances instead of a specific named instance.</span></span> <span data-ttu-id="3d8aa-203"><xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.ConfigureAll%2A> と <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigureAll%2A> では、この規則が使用されます。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-203"><xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.ConfigureAll%2A> and <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigureAll%2A> use this convention.</span></span>

## <a name="optionsbuilder-api"></a><span data-ttu-id="3d8aa-204">OptionsBuilder API</span><span class="sxs-lookup"><span data-stu-id="3d8aa-204">OptionsBuilder API</span></span>

<span data-ttu-id="3d8aa-205"><xref:Microsoft.Extensions.Options.OptionsBuilder%601> は、`TOptions` インスタンスの構成に使用されます。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-205"><xref:Microsoft.Extensions.Options.OptionsBuilder%601> is used to configure `TOptions` instances.</span></span> <span data-ttu-id="3d8aa-206">`OptionsBuilder` は名前付きオプションの作成を簡略化します。これは最初の `AddOptions<TOptions>(string optionsName)` の呼び出しに対する 1 つのパラメーターにすぎず、後続のすべての呼び出しが表示されなくなるためです。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-206">`OptionsBuilder` streamlines creating named options as it's only a single parameter to the initial `AddOptions<TOptions>(string optionsName)` call instead of appearing in all of the subsequent calls.</span></span> <span data-ttu-id="3d8aa-207">サービスの依存関係を受け入れるオプションの検証と `ConfigureOptions` のオーバーロードは、`OptionsBuilder` を介してのみ可能です。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-207">Options validation and the `ConfigureOptions` overloads that accept service dependencies are only available via `OptionsBuilder`.</span></span>

<span data-ttu-id="3d8aa-208">`OptionsBuilder` は、「[オプションの検証](#options-validation)」セクションで使用されます。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-208">`OptionsBuilder` is used in the [Options validation](#options-validation) section.</span></span>

## <a name="use-di-services-to-configure-options"></a><span data-ttu-id="3d8aa-209">DI サービスを使用してオプションを構成する</span><span class="sxs-lookup"><span data-stu-id="3d8aa-209">Use DI services to configure options</span></span>

<span data-ttu-id="3d8aa-210">オプションの構成中、次の 2 つの方法で依存関係挿入からサービスにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-210">Services can be accessed from dependency injection while configuring options in two ways:</span></span>

- <span data-ttu-id="3d8aa-211">[OptionsBuilder\<TOptions>](xref:Microsoft.Extensions.Options.OptionsBuilder%601) で [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) に構成デリゲートを渡します。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-211">Pass a configuration delegate to [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) on [OptionsBuilder\<TOptions>](xref:Microsoft.Extensions.Options.OptionsBuilder%601).</span></span> <span data-ttu-id="3d8aa-212">`OptionsBuilder<TOptions>` から [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) のオーバーロードが与えられます。これにより、最大 5 つのサービスを使用してオプションを構成できます。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-212">`OptionsBuilder<TOptions>` provides overloads of [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) that allow use of up to five services to configure options:</span></span>

  ```csharp
  services.AddOptions<MyOptions>("optionalName")
      .Configure<ExampleService, ScopedService, MonitorService>(
          (options, es, ss, ms) =>
              options.Property = DoSomethingWith(es, ss, ms));
  ```

- <span data-ttu-id="3d8aa-213"><xref:Microsoft.Extensions.Options.IConfigureOptions%601> または <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> を実装する型を作成し、その型をサービスとして登録します。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-213">Create a type that implements <xref:Microsoft.Extensions.Options.IConfigureOptions%601> or <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> and register the type as a service.</span></span>

<span data-ttu-id="3d8aa-214">サービスの作成は複雑なため、[Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) に構成デリゲートを渡す方法をおすすめします。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-214">We recommend passing a configuration delegate to [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A), since creating a service is more complex.</span></span> <span data-ttu-id="3d8aa-215">型を作成することは、[Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) を呼び出すときにフレームワークが行うことと同じです。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-215">Creating a type is equivalent to what the framework does when calling [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A).</span></span> <span data-ttu-id="3d8aa-216">[Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) を呼び出すと、一時的な汎用の <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> が登録されます。これには、指定された汎用サービスの型を受け入れるコンストラクターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-216">Calling [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) registers a transient generic <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601>, which has a constructor that accepts the generic service types specified.</span></span>

## <a name="options-validation"></a><span data-ttu-id="3d8aa-217">オプションの検証</span><span class="sxs-lookup"><span data-stu-id="3d8aa-217">Options validation</span></span>

<span data-ttu-id="3d8aa-218">オプションの検証により、オプションの値を検証できます。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-218">Options validation enables option values to be validated.</span></span>

<span data-ttu-id="3d8aa-219">以下の *appsettings.json* ファイルについて考えます:</span><span class="sxs-lookup"><span data-stu-id="3d8aa-219">Consider the following *appsettings.json* file:</span></span>

```json
{
  "Settings": {
    "SiteTitle": "Amazing docs from Awesome people!",
    "Scale": 10,
    "VerbosityLevel": 32
  }
}
```

<span data-ttu-id="3d8aa-220">次のクラスは、`"Settings"` 構成セクションにバインドされ、いくつかの `DataAnnotations` 規則を適用します。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-220">The following class binds to the `"Settings"` configuration section and applies a couple of `DataAnnotations` rules:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/SettingsOptions.cs":::

<span data-ttu-id="3d8aa-221">コード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-221">The following code:</span></span>

- <span data-ttu-id="3d8aa-222"><xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%2A> を呼び出し、`SettingsOptions` クラスにバインドされる [OptionsBuilder\<TOptions>](xref:Microsoft.Extensions.Options.OptionsBuilder%601) を取得します。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-222">Calls <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%2A> to get an [OptionsBuilder\<TOptions>](xref:Microsoft.Extensions.Options.OptionsBuilder%601) that binds to the `SettingsOptions` class.</span></span>
- <span data-ttu-id="3d8aa-223"><xref:Microsoft.Extensions.DependencyInjection.OptionsBuilderDataAnnotationsExtensions.ValidateDataAnnotations%2A> を呼び出し、`DataAnnotations` を利用した検証を有効にします。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-223">Calls <xref:Microsoft.Extensions.DependencyInjection.OptionsBuilderDataAnnotationsExtensions.ValidateDataAnnotations%2A> to enable validation using `DataAnnotations`.</span></span>

```csharp
services.AddOptions<SettingsOptions>()
    .Bind(Configuration.GetSection(SettingsOptions.Settings))
    .ValidateDataAnnotations();
```

<span data-ttu-id="3d8aa-224">`ValidateDataAnnotations` 拡張メソッドは [Microsoft.Extensions.Options.DataAnnotations](https://www.nuget.org/packages/Microsoft.Extensions.Options.DataAnnotations) NuGet パッケージに定義されています。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-224">The `ValidateDataAnnotations` extension method is defined in the [Microsoft.Extensions.Options.DataAnnotations](https://www.nuget.org/packages/Microsoft.Extensions.Options.DataAnnotations) NuGet package.</span></span>

<span data-ttu-id="3d8aa-225">次のコードは、構成値または検証エラーを表示します。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-225">The following code displays the configuration values or the validation errors:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/ValidationService.cs":::

<span data-ttu-id="3d8aa-226">次のコードは、デリゲートを使用して、より複雑な検証規則を適用します。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-226">The following code applies a more complex validation rule using a delegate:</span></span>

```csharp
services.AddOptions<SettingsOptions>()
    .Bind(Configuration.GetSection(SettingsOptions.Settings))
    .ValidateDataAnnotations()
    .Validate(config =>
    {
        if (config.Scale != 0)
        {
            return config.VerbosityLevel > config.Scale;
        }

        return true;
    }, "VerbosityLevel must be > than Scale.");
```

### <a name="ivalidateoptions-for-complex-validation"></a><span data-ttu-id="3d8aa-227">複雑な検証用の IValidateOptions</span><span class="sxs-lookup"><span data-stu-id="3d8aa-227">IValidateOptions for complex validation</span></span>

<span data-ttu-id="3d8aa-228">次のクラスは、<xref:Microsoft.Extensions.Options.IValidateOptions%601> を実装します。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-228">The following class implements <xref:Microsoft.Extensions.Options.IValidateOptions%601>:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/ValidateSettingsOptions.cs":::

<span data-ttu-id="3d8aa-229">`IValidateOptions` を使用すると、検証コードをクラスに移動できます。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-229">`IValidateOptions` enables moving the validation code into a class.</span></span>

<span data-ttu-id="3d8aa-230">前のコードを使用すると、次のコードにより `ConfigureServices` で検証が有効になります。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-230">Using the preceding code, validation is enabled in `ConfigureServices` with the following code:</span></span>

```csharp
services.Configure<SettingsOptions>(
    Configuration.GetSection(
        SettingsOptions.Settings));
services.TryAddEnumerable(
    ServiceDescriptor.Singleton
        <IValidateOptions<SettingsOptions>, ValidateSettingsOptions>());
```

## <a name="options-post-configuration"></a><span data-ttu-id="3d8aa-231">オプションのポスト構成</span><span class="sxs-lookup"><span data-stu-id="3d8aa-231">Options post-configuration</span></span>

<span data-ttu-id="3d8aa-232">ポスト構成を <xref:Microsoft.Extensions.Options.IPostConfigureOptions%601> を使用して設定します。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-232">Set post-configuration with <xref:Microsoft.Extensions.Options.IPostConfigureOptions%601>.</span></span> <span data-ttu-id="3d8aa-233">事後構成は、<xref:Microsoft.Extensions.Options.IConfigureOptions%601> のすべての構成が行われた後に実行され、構成をオーバーライドする必要があるシナリオに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-233">Post-configuration runs after all <xref:Microsoft.Extensions.Options.IConfigureOptions%601> configuration occurs, and can be useful in scenarios when you need to override configuration:</span></span>

```csharp
services.PostConfigure<CustomOptions>(customOptions =>
{
    customOptions.Option1 = "post_configured_option1_value";
});
```

<span data-ttu-id="3d8aa-234"><xref:Microsoft.Extensions.Options.IPostConfigureOptions%601.PostConfigure%2A> は、名前付きオプションのポスト構成に使用できます。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-234"><xref:Microsoft.Extensions.Options.IPostConfigureOptions%601.PostConfigure%2A> is available to post-configure named options:</span></span>

```csharp
services.PostConfigure<CustomOptions>("named_options_1", customOptions =>
{
    customOptions.Option1 = "post_configured_option1_value";
});
```

<span data-ttu-id="3d8aa-235">すべての構成インスタンスをポスト構成するには、<xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigureAll%2A> を使用します。</span><span class="sxs-lookup"><span data-stu-id="3d8aa-235">Use <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigureAll%2A> to post-configure all configuration instances:</span></span>

```csharp
services.PostConfigureAll<CustomOptions>(customOptions =>
{
    customOptions.Option1 = "post_configured_option1_value";
});
```

## <a name="see-also"></a><span data-ttu-id="3d8aa-236">関連項目</span><span class="sxs-lookup"><span data-stu-id="3d8aa-236">See also</span></span>

- [<span data-ttu-id="3d8aa-237">.NET での構成</span><span class="sxs-lookup"><span data-stu-id="3d8aa-237">Configuration in .NET</span></span>](configuration.md)
- [<span data-ttu-id="3d8aa-238">.NET ライブラリ作成者のためのオプション パターン ガイダンス</span><span class="sxs-lookup"><span data-stu-id="3d8aa-238">Options pattern guidance for .NET library authors</span></span>](options-library-authors.md)
