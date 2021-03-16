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
# <a name="options-pattern-in-net"></a>.NET でのオプション パターン

オプション パターンでは、クラスを使用して、関連する設定のグループへの、厳密に型指定されたアクセスが提供されます。 [構成設定](configuration.md)がシナリオ別に個々のクラスに分離されるとき、アプリは次の 2 つの重要なソフトウェア エンジニアリング原則に従います。

- [インターフェイス分離の原則 (ISP) またはカプセル化](../../architecture/modern-web-apps-azure/architectural-principles.md#encapsulation): 使用する構成設定のみに依存するシナリオ (クラス)。
- [懸念事項の分離](../../architecture/modern-web-apps-azure/architectural-principles.md#separation-of-concerns): アプリのさまざまな部分の設定は、互いに依存していないか、結合されていない。

構成データを検証するメカニズムもオプションによって提供されます。 詳しくは、「[オプションの検証](#options-validation)」セクションをご覧ください。

## <a name="bind-hierarchical-configuration"></a>階層的な構成をバインドする

関連する構成値を読み取る方法としては、オプション パターンを使用することをお勧めします。 オプション パターンは、<xref:Microsoft.Extensions.Options.IOptions%601> インターフェイスを通して使用できます。ジェネリック型パラメーター `TOptions` は、`class` に制限されます。 後で、依存関係の挿入により `IOptions<TOptions>` を提供できます。 詳細については、「[.NET での依存関係の挿入](dependency-injection.md)」を参照してください。

たとえば、以下の構成値を読み取るには、次のようにします:

:::code language="json" source="snippets/configuration/console-json/appsettings.json" range="3-6":::

次の `TransientFaultHandlingOptions` クラスを作成します:

:::code language="csharp" source="snippets/configuration/console-json/TransientFaultHandlingOptions.cs" range="5-9":::

<span id="options-class"></span> オプション パターンを使用する場合、オプション クラスは次のとおりです。

- パラメーターなしのパブリック コンストラクターを持った非抽象でなければなりません
- バインドする読み取り/書き込みのパブリック プロパティが含まれます (フィールドはバインド "***されません***")

コード例を次に示します。

* [ConfigurationBinder.Bind](xref:Microsoft.Extensions.Configuration.ConfigurationBinder.Bind%2A) を呼び出して、`TransientFaultHandlingOptions` クラスを `"TransientFaultHandlingOptions"` セクションにバインドします。
* 構成データを表示します。

:::code language="csharp" source="snippets/configuration/console-json/Program.cs" range="31-38":::

上記のコードでは、アプリが開始された後の JSON 構成ファイルへの変更が読み取られます。

[`ConfigurationBinder.Get<T>`](xref:Microsoft.Extensions.Configuration.ConfigurationBinder.Get%2A) 指定された型をバインドして返します。 `ConfigurationBinder.Get<T>` は `ConfigurationBinder.Bind` を使用するよりも便利な場合があります。 次のコードは、`TransientFaultHandlingOptions` クラスで `ConfigurationBinder.Get<T>` を使用する方法を示しています:

```csharp
IConfigurationRoot configurationRoot = configuration.Build();

var options =
    configurationRoot.GetSection(nameof(TransientFaultHandlingOptions))
                     .Get<TransientFaultHandlingOptions>();

Console.WriteLine($"TransientFaultHandlingOptions.Enabled={options.Enabled}");
Console.WriteLine($"TransientFaultHandlingOptions.AutoRetryDelay={options.AutoRetryDelay}");
```

上記のコードでは、アプリが開始された後の JSON 構成ファイルへの変更が読み取られます。

> [!IMPORTANT]
> <xref:Microsoft.Extensions.Configuration.ConfigurationBinder> クラスにより、`class` に制約 "***されない***" API がいくつか公開されます (`.Bind(object instance)` や `.Get<T>()` など)。 いずれかの[オプション インターフェイス](#options-interfaces)を使用するときは、前に説明した[オプション クラスの制約](#options-class)に従う必要があります。

オプション パターンを使用するときのもう 1 つの方法は、`"TransientFaultHandlingOptions"` セクションをバインドし、それを[依存関係挿入サービス コンテナー](dependency-injection.md)に追加することです。 次のコードでは、`TransientFaultHandlingOptions` は <xref:Microsoft.Extensions.DependencyInjection.OptionsConfigurationServiceCollectionExtensions.Configure%2A> でサービスコンテナーに追加され、構成にバインドされます:

```csharp
services.Configure<TransientFaultHandlingOptions>(
    configurationRoot.GetSection(
        key: nameof(TransientFaultHandlingOptions)));
```

> [!TIP]
> `key` パラメーターは、検索する構成セクションの名前です。 それを表す型の名前と一致する必要は "*ありません*"。 たとえば、`"FaultHandling"` という名前のセクションを使用し、`TransientFaultHandlingOptions` クラスによってそれを表すことができます。 この場合は、代わりに `"FaultHandling"` を <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> 関数に渡します。 `nameof` 演算子は、名前付きセクションとそれが対応する型が一致する場合に使用すると便利です。

下記のコードは、上記のコードを使用して位置オプションを読み取ります:

:::code language="csharp" source="snippets/configuration/console-json/ExampleService.cs":::

上のコードでは、アプリが開始された後の JSON 構成ファイルへの変更は読み取られ ***ません***。 アプリの開始後に変更を読み取るには、[IOptionsSnapshot](#use-ioptionssnapshot-to-read-updated-data) を使用します。

## <a name="options-interfaces"></a>オプションのインターフェイス

<xref:Microsoft.Extensions.Options.IOptions%601>:

- サポートされて "***いません***"。
  - アプリが開始された後の構成データの読み取り。
  - [名前付きオプション](#named-options-support-using-iconfigurenamedoptions)
- [シングルトン](dependency-injection.md#singleton)として登録されており、任意の[サービスの有効期間](dependency-injection.md#service-lifetimes)に挿入できます。

<xref:Microsoft.Extensions.Options.IOptionsSnapshot%601>:

- [スコープ指定または一時的な有効期間](dependency-injection.md#service-lifetimes)において、すべての挿入解決でオプションを再計算する必要がある場合に便利です。 詳細については、「[IOptionsSnapshot を使用して更新データを読み取る](#use-ioptionssnapshot-to-read-updated-data)」を参照してください。
- [スコープ](dependency-injection.md#scoped)として登録されているため、シングルトン サービスには挿入できません。
- [名前付きオプション](#named-options-support-using-iconfigurenamedoptions)をサポートします。

<xref:Microsoft.Extensions.Options.IOptionsMonitor%601>:

- オプションを取得し、`TOptions` インスタンスのオプション通知を管理するために使用されます。
- [シングルトン](dependency-injection.md#singleton)として登録されており、任意の[サービスの有効期間](dependency-injection.md#service-lifetimes)に挿入できます。
- サポートするものは次のとおりです。
  - 変更通知
  - [名前付きオプション](#named-options-support-using-iconfigurenamedoptions)
  - [再読み込み可能な構成](#use-ioptionssnapshot-to-read-updated-data)
  - 選択的なオプションの無効化 (<xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601>)

<xref:Microsoft.Extensions.Options.IOptionsFactory%601> は、新しいオプション インスタンスを作成します。 <xref:Microsoft.Extensions.Options.IOptionsFactory%601.Create%2A> メソッドが 1 つ含まれています。 既定の実装では、登録されている <xref:Microsoft.Extensions.Options.IConfigureOptions%601> と <xref:Microsoft.Extensions.Options.IPostConfigureOptions%601> がすべて受け取られ、先にすべての構成を実行し、その後、ポスト構成を実行します。 <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> と <xref:Microsoft.Extensions.Options.IConfigureOptions%601> が区別され、適切なインターフェイスのみが呼び出されます。

<xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601> は <xref:Microsoft.Extensions.Options.IOptionsMonitor%601> によって使用され、`TOptions` インスタンスをキャッシュします。 <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601> は、値が再計算されるよう、モニターのオプション インスタンスを無効にします (<xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.TryRemove%2A>)。 <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.TryAdd%2A> を利用し、手動で値を入力できます。 <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.Clear%2A> メソッドは、すべての名前付きインスタンスをオンデマンドで再作成するときに使用されます。

### <a name="options-interfaces-benefits"></a>オプション インターフェイスの利点

ジェネリック ラッパー型を使用すると、オプションの有効期間を DI コンテナーから切り離すことができます。 <xref:Microsoft.Extensions.Options.IOptions%601.Value?displayProperty=nameWithType> インターフェイスにより、ジェネリック制約を含む抽象レイヤーがオプションの型に提供されます。 これには次のようなメリットがあります。

- `T` 構成インスタンスの評価が、挿入時ではなく、<xref:Microsoft.Extensions.Options.IOptions%601.Value?displayProperty=nameWithType> のアクセスまで遅延されます。 これは、さまざまな場所から `T` オプションを使用でき、`T` について何も変更せずに有効期間のセマンティクスを選択できるため、重要なことです。
- `T` 型のオプションを登録するときに、`T` 型を明示的に登録する必要はありません。 これは、簡単な既定値を使用して[ライブラリを作成](options-library-authors.md)していて、特定の有効期間での DI コンテナーへのオプションの登録を呼び出し元に強制したくない場合に便利です。
- API の観点からは、それにより `T` 型への制約に対応できます (この例では、`T` は参照型に制約されます)。

## <a name="use-ioptionssnapshot-to-read-updated-data"></a>IOptionsSnapshot を使用して更新データを読み取る

<xref:Microsoft.Extensions.Options.IOptionsSnapshot%601> を使用すると、オプションは要求ごとにアクセス時に 1 回計算され、要求の有効期間中キャッシュされます。 更新された構成値の読み取りをサポートする構成プロバイダーを使用しているとき、構成の変更は、アプリの開始後に読み取られます。

`IOptionsMonitor` と `IOptionsSnapshot` の違いは次のとおりです。

- `IOptionsMonitor` は常に最新のオプション値を取得する[シングルトン サービス](dependency-injection.md#singleton) です。これは、シングルトンの依存関係で特に便利です。
- `IOptionsSnapshot` は[スコープ サービス](dependency-injection.md#scoped) であり、`IOptionsSnapshot<T>` オブジェクトの構築時にオプションのスナップショットを提供します。 オプションのスナップショットは、一時的な依存関係およびスコープのある依存関係で使用されるように設計されています。

次のコードでは <xref:Microsoft.Extensions.Options.IOptionsSnapshot%601> を使用します。

:::code language="csharp" source="snippets/configuration/console-json/ScopedService.cs":::

次のコードは、`TransientFaultHandlingOptions` のバインド先となる構成インスタンスを登録します。

```csharp
services.Configure<TransientFaultHandlingOptions>(
    configurationRoot.GetSection(
        nameof(TransientFaultHandlingOptions)));
```

上記のコードでは、アプリが開始された後の JSON 構成ファイルへの変更が読み取られます。

## <a name="ioptionsmonitor"></a>IOptionsMonitor

次のコードは、`TransientFaultHandlingOptions` のバインド先となる構成インスタンスを登録します。

```csharp
services.Configure<TransientFaultHandlingOptions>(
    configurationRoot.GetSection(
        nameof(TransientFaultHandlingOptions)));
```

<xref:Microsoft.Extensions.Options.IOptionsMonitor%601> の使用例を次に示します。

:::code language="csharp" source="snippets/configuration/console-json/MonitorService.cs":::

上記のコードでは、アプリが開始された後の JSON 構成ファイルへの変更が読み取られます。

## <a name="named-options-support-using-iconfigurenamedoptions"></a>IConfigureNamedOptions を使用した名前付きオプションのサポート

名前付きオプション:

- 複数の構成セクションが同じプロパティにバインドされている場合に便利です。
- 大文字と小文字の区別があります。

以下の *appsettings.json* ファイルについて考えます:

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

`Features:Personalize` と `Features:WeatherStation` をバインドする 2 つのクラスを作成するのではなく、各セクションに対して次のクラスを使用します。

```csharp
public class Features
{
    public const string Personalize = nameof(Personalize);
    public const string WeatherStation = nameof(WeatherStation);

    public bool Enabled { get; set; }
    public string ApiKey { get; set; }
}
```

次のコードは、名前付きオプションを構成します。

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

次のコードは、名前付きオプションを表示します。

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

すべてのオプションが名前付きインスタンスです。 <xref:Microsoft.Extensions.Options.IConfigureOptions%601> インスタンスは、`string.Empty` である、`Options.DefaultName` インスタンスを対象とするものとして処理されます。 <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> はまた、<xref:Microsoft.Extensions.Options.IConfigureOptions%601> を実装します。 <xref:Microsoft.Extensions.Options.IOptionsFactory%601> の既定の実装には、それぞれを適切に使用するロジックがあります。 名前付きオプション `null` は、特定の名前付きインスタンスではなく、すべての名前付きインスタンスを対象とするために使用されます。 <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.ConfigureAll%2A> と <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigureAll%2A> では、この規則が使用されます。

## <a name="optionsbuilder-api"></a>OptionsBuilder API

<xref:Microsoft.Extensions.Options.OptionsBuilder%601> は、`TOptions` インスタンスの構成に使用されます。 `OptionsBuilder` は名前付きオプションの作成を簡略化します。これは最初の `AddOptions<TOptions>(string optionsName)` の呼び出しに対する 1 つのパラメーターにすぎず、後続のすべての呼び出しが表示されなくなるためです。 サービスの依存関係を受け入れるオプションの検証と `ConfigureOptions` のオーバーロードは、`OptionsBuilder` を介してのみ可能です。

`OptionsBuilder` は、「[オプションの検証](#options-validation)」セクションで使用されます。

## <a name="use-di-services-to-configure-options"></a>DI サービスを使用してオプションを構成する

オプションの構成中、次の 2 つの方法で依存関係挿入からサービスにアクセスできます。

- [OptionsBuilder\<TOptions>](xref:Microsoft.Extensions.Options.OptionsBuilder%601) で [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) に構成デリゲートを渡します。 `OptionsBuilder<TOptions>` から [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) のオーバーロードが与えられます。これにより、最大 5 つのサービスを使用してオプションを構成できます。

  ```csharp
  services.AddOptions<MyOptions>("optionalName")
      .Configure<ExampleService, ScopedService, MonitorService>(
          (options, es, ss, ms) =>
              options.Property = DoSomethingWith(es, ss, ms));
  ```

- <xref:Microsoft.Extensions.Options.IConfigureOptions%601> または <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> を実装する型を作成し、その型をサービスとして登録します。

サービスの作成は複雑なため、[Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) に構成デリゲートを渡す方法をおすすめします。 型を作成することは、[Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) を呼び出すときにフレームワークが行うことと同じです。 [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) を呼び出すと、一時的な汎用の <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> が登録されます。これには、指定された汎用サービスの型を受け入れるコンストラクターが含まれています。

## <a name="options-validation"></a>オプションの検証

オプションの検証により、オプションの値を検証できます。

以下の *appsettings.json* ファイルについて考えます:

```json
{
  "Settings": {
    "SiteTitle": "Amazing docs from Awesome people!",
    "Scale": 10,
    "VerbosityLevel": 32
  }
}
```

次のクラスは、`"Settings"` 構成セクションにバインドされ、いくつかの `DataAnnotations` 規則を適用します。

:::code language="csharp" source="snippets/configuration/console-json/SettingsOptions.cs":::

コード例を次に示します。

- <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%2A> を呼び出し、`SettingsOptions` クラスにバインドされる [OptionsBuilder\<TOptions>](xref:Microsoft.Extensions.Options.OptionsBuilder%601) を取得します。
- <xref:Microsoft.Extensions.DependencyInjection.OptionsBuilderDataAnnotationsExtensions.ValidateDataAnnotations%2A> を呼び出し、`DataAnnotations` を利用した検証を有効にします。

```csharp
services.AddOptions<SettingsOptions>()
    .Bind(Configuration.GetSection(SettingsOptions.Settings))
    .ValidateDataAnnotations();
```

`ValidateDataAnnotations` 拡張メソッドは [Microsoft.Extensions.Options.DataAnnotations](https://www.nuget.org/packages/Microsoft.Extensions.Options.DataAnnotations) NuGet パッケージに定義されています。

次のコードは、構成値または検証エラーを表示します。

:::code language="csharp" source="snippets/configuration/console-json/ValidationService.cs":::

次のコードは、デリゲートを使用して、より複雑な検証規則を適用します。

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

### <a name="ivalidateoptions-for-complex-validation"></a>複雑な検証用の IValidateOptions

次のクラスは、<xref:Microsoft.Extensions.Options.IValidateOptions%601> を実装します。

:::code language="csharp" source="snippets/configuration/console-json/ValidateSettingsOptions.cs":::

`IValidateOptions` を使用すると、検証コードをクラスに移動できます。

前のコードを使用すると、次のコードにより `ConfigureServices` で検証が有効になります。

```csharp
services.Configure<SettingsOptions>(
    Configuration.GetSection(
        SettingsOptions.Settings));
services.TryAddEnumerable(
    ServiceDescriptor.Singleton
        <IValidateOptions<SettingsOptions>, ValidateSettingsOptions>());
```

## <a name="options-post-configuration"></a>オプションのポスト構成

ポスト構成を <xref:Microsoft.Extensions.Options.IPostConfigureOptions%601> を使用して設定します。 事後構成は、<xref:Microsoft.Extensions.Options.IConfigureOptions%601> のすべての構成が行われた後に実行され、構成をオーバーライドする必要があるシナリオに役立ちます。

```csharp
services.PostConfigure<CustomOptions>(customOptions =>
{
    customOptions.Option1 = "post_configured_option1_value";
});
```

<xref:Microsoft.Extensions.Options.IPostConfigureOptions%601.PostConfigure%2A> は、名前付きオプションのポスト構成に使用できます。

```csharp
services.PostConfigure<CustomOptions>("named_options_1", customOptions =>
{
    customOptions.Option1 = "post_configured_option1_value";
});
```

すべての構成インスタンスをポスト構成するには、<xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigureAll%2A> を使用します。

```csharp
services.PostConfigureAll<CustomOptions>(customOptions =>
{
    customOptions.Option1 = "post_configured_option1_value";
});
```

## <a name="see-also"></a>関連項目

- [.NET での構成](configuration.md)
- [.NET ライブラリ作成者のためのオプション パターン ガイダンス](options-library-authors.md)
