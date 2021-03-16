---
title: .NET ライブラリ作成者のためのオプション パターン ガイダンス
author: IEvangelist
description: .NET でライブラリ作成者としてオプション パターンを公開する方法について説明します。
ms.author: dapine
ms.date: 01/28/2021
ms.openlocfilehash: d0da94a8f25c9e5aba6093fab07ccca6a0a7c345
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2021
ms.locfileid: "102402142"
---
# <a name="options-pattern-guidance-for-net-library-authors"></a>.NET ライブラリ作成者のためのオプション パターン ガイダンス

依存関係の挿入の助けを借りて、サービスとそれに対応する構成を登録すると、"*オプション パターン*" を利用できるようになります。 オプション パターンを使用すると、ライブラリ (およびサービス) のコンシューマーで、`TOptions` がオプション クラスである[オプション インターフェイス](options.md#options-interfaces)のインスタンスを要求できます。 厳密に型指定されたオブジェクトを使用して構成オプションを使用すると、一貫性のある値の表現が保証され、文字列値を手動で解析する負担がなくなります。 ライブラリのコンシューマーで使用する多くの[構成プロバイダー](configuration-providers.md)があります。 コンシューマーでこれらのプロバイダーを使用すると、さまざまな方法でライブラリを構成できます。

.NET ライブラリの作成者のために、ライブラリのコンシューマーにオプション パターンを正しく公開する方法に関する一般的なガイダンスを説明します。 同じことを実現するのにさまざまな方法があり、いくつかの考慮事項があります。

## <a name="naming-conventions"></a>名前付け規則

慣例により、サービスを登録する拡張メソッドの名前は `Add{Service}` であり、`{Service}` は意味のあるわかりやすい名前です。 パッケージによっては、サービスの登録に `Use{Service}` 拡張メソッドが付随する場合があります。 `Use{Service}` 拡張メソッドは、[ASP.NET Core](/aspnet) では一般的です。

✔️ 自分のサービスと他のオファリングを明確に区別できる名前を考えます。

❌ .既に NET エコシステムの一部になっている、Microsoft の公式パッケージに含まれる名前は使用しないでください。

✔️ 拡張メソッドを公開する静的クラスは、`{Type}Extensions` という名前にします。`{Type}` は拡張する型です。

### <a name="namespace-guidance"></a>名前空間のガイダンス

Microsoft のパッケージでは、`Microsoft.Extensions.DependencyInjection` 名前空間を使用して、さまざまなサービス オファリングの登録が統合されています。

✔️ 自分のパッケージ オファリングを明確に識別できる名前空間を考えます。

❌ Microsoft が公式に認めていないパッケージには、`Microsoft.Extensions.DependencyInjection` 名前空間を使用しないでください。

## <a name="parameterless"></a>パラメーターなし

サービスが最小限の構成または明示的ではない構成で動作できる場合は、パラメーターなしの拡張メソッドを検討します。

:::code language="csharp" source="snippets/configuration/options-noparams/ServiceCollectionExtensions.cs" highlight="10-14":::

上のコードの `AddMyLibraryService` では、次のことが行われています。

- <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection> のインスタンスを拡張します
- `LibraryOptions` の型パラメーターを使用して <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%60%601(Microsoft.Extensions.DependencyInjection.IServiceCollection)?displayProperty=nameWithType> を呼び出します
- <xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A> の呼び出しをチェーンします。ここでは、既定のオプション値を指定します

## <a name="iconfiguration-parameter"></a>`IConfiguration` パラメーター

多くのオプションをコンシューマーに公開するライブラリを作成するときは、`IConfiguration` パラメーター拡張メソッドが必要になる場合があります。 予想される `IConfiguration` インスタンスでは、<xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A?displayProperty=nameWithType> 関数を使用することにより、構成の名前付きセクションにスコープを設定する必要があります。

:::code language="csharp" source="snippets/configuration/options-configparam/ServiceCollectionExtensions.cs" highlight="10,12-16":::

上のコードの `AddMyLibraryService` では、次のことが行われています。

- <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection> のインスタンスを拡張します
- <xref:Microsoft.Extensions.Configuration.IConfiguration> パラメーターの `namedConfigurationSection` を定義します
- <xref:Microsoft.Extensions.Configuration.ConfigurationBinder.Bind(Microsoft.Extensions.Configuration.IConfiguration,System.Object)> を呼び出し、構成のバインド先となるオプション インスタンスを渡します

このパターンのコンシューマーは、名前付きセクションのスコープ設定された `IConfiguration` インスタンスを提供します。

:::code language="csharp" source="snippets/configuration/options-configparam/Program.cs" highlight="22-23":::

`.AddMyLibraryService` の呼び出しは、<xref:Microsoft.Extensions.Hosting.IHostBuilder.ConfigureServices%2A> メソッドで行われます。 `Startup` クラスを使用する場合も同様です。登録されるサービスの追加は、`ConfigureServices` で行われます。

既定値を指定するかどうかは、ライブラリの作成者が決定します。

> [!NOTE]
> 構成をオプション インスタンスにバインドすることができます。 ただし、名前が衝突してエラーが発生するリスクがあります。 また、この方法を使用して手動でバインドするときは、オプション パターンの使用を読み取り 1 回に制限します。 設定を変更しても再バインドされないため、コンシューマーは [IOptionsMonitor](options.md#ioptionsmonitor) インターフェイスを使用できません。
>
> ```csharp
> services.AddOptions<LibraryOptions>()
>     .Configure<IConfiguration>(
>         (options, configuration) =>
>             configuration.GetSection("LibraryOptions").Bind(options));
> ```

## <a name="actiontoptions-parameter"></a>`Action<TOptions>` パラメーター

ライブラリのコンシューマーは、オプション クラスのインスタンスを生成するラムダ式を提供することに関心を持つ場合があります。 このシナリオに場合は、拡張メソッドで `Action<LibraryOptions>` パラメーターを定義します。

:::code language="csharp" source="snippets/configuration/options-action/ServiceCollectionExtensions.cs" highlight="10,12":::

上のコードの `AddMyLibraryService` では、次のことが行われています。

- <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection> のインスタンスを拡張します
- <xref:System.Action%601> を定義します。`T` は `LibraryOptions` パラメーターの `configureOptions` です
- `configureOptions` アクションを指定して <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.Configure%2A> を呼び出します

このパターンのコンシューマーは、ラムダ式 (または、`Action<LibraryOptions>` パラメーターを満たすデリゲート) を提供します。

:::code language="csharp" source="snippets/configuration/options-action/Program.cs" highlight="22-26":::

## <a name="options-instance-parameter"></a>オプション インスタンスのパラメーター

ライブラリのコンシューマーは、インラインのオプション インスタンスを使用することを好む場合があります。 このシナリオの場合は、オプション オブジェクト `LibraryOptions` のインスタンスを受け取る拡張メソッドを公開します。

:::code language="csharp" source="snippets/configuration/options-object/ServiceCollectionExtensions.cs" highlight="9,11-17":::

上のコードの `AddMyLibraryService` では、次のことが行われています。

- <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection> のインスタンスを拡張します
- `LibraryOptions` の型パラメーターを使用して <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%60%601(Microsoft.Extensions.DependencyInjection.IServiceCollection)?displayProperty=nameWithType> を呼び出します
- <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.Configure%2A> の呼び出しをチェーンします。そこでは、特定の `userOptions` インスタンスからオーバーライドできる既定のオプション値を指定します

このパターンのコンシューマーは、`LibraryOptions` クラスのインスタンスを提供し、必要なプロパティ値をインラインで定義します。

:::code language="csharp" source="snippets/configuration/options-object/Program.cs" highlight="22-26":::

## <a name="post-configuration"></a>構成後

すべての構成オプション値をバインドまたは指定すると、事後構成の機能を使用できるようになります。 前に詳しく説明したのと同じ [`Action<TOptions>` パラメーター](#actiontoptions-parameter)を公開すると、<xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigure%2A> を呼び出すことができます。 事後構成は、`.Configure` のすべての呼び出しの後に実行されます。

:::code language="csharp" source="snippets/configuration/options-postconfig/ServiceCollectionExtensions.cs" highlight="10,12":::

上のコードの `AddMyLibraryService` では、次のことが行われています。

- <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection> のインスタンスを拡張します
- <xref:System.Action%601> を定義します。`T` は `LibraryOptions` パラメーターの `configureOptions` です
- `configureOptions` アクションを指定して <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigure%2A> を呼び出します

このパターンのコンシューマーは、事後構成ではないシナリオの [`Action<TOptions>` パラメーター] と同様に、ラムダ式 (または、`Action<LibraryOptions>` パラメーターを満たすデリゲート) を提供します。

:::code language="csharp" source="snippets/configuration/options-postconfig/Program.cs" highlight="22-26":::

## <a name="see-also"></a>関連項目

- [.NET でのオプション パターン](options.md)
- [.NET での依存関係の挿入](dependency-injection.md)
- [依存関係の挿入のガイドライン](dependency-injection-guidelines.md)
