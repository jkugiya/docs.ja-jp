---
title: 依存関係の挿入のガイドライン
description: さまざまな依存関係の挿入のガイドラインと、.NET アプリケーション開発のベスト プラクティスについて説明します。
author: IEvangelist
ms.author: dapine
ms.date: 10/29/2020
ms.topic: guide
ms.openlocfilehash: 105536df873829dc79dcca1b86d080360e71303f
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2021
ms.locfileid: "102402148"
---
# <a name="dependency-injection-guidelines"></a>依存関係の挿入のガイドライン

この記事では、.NET アプリケーションで依存関係の挿入を実装するための一般的なガイドラインとベスト プラクティスについて説明します。

## <a name="design-services-for-dependency-injection"></a>依存関係の挿入のためのサービスの設計

依存関係の挿入のためのサービスの設計時には:

- ステートフル、静的クラス、およびメンバーは避けてください。 代わりにシングルトン サービスを使用するようにアプリを設計し、グローバルな状態を作成しないようにします。
- サービス内部で依存関係のあるクラスを直接インスタンス化することを回避します。 直接のインスタンス化は、コードの固有の実装につながります。
- サービスを、小さく、十分に要素に分割された、テストしやすいものにします。

クラスに多数の挿入される依存関係がある場合、それは、クラスの責任が多すぎて、[単一責任の原則 (SRP)](/dotnet/standard/modern-web-apps-azure-architecture/architectural-principles#single-responsibility) に違反することを示している可能性があります。 責任の一部を新しいクラスに移動することにより、クラスのリファクタリングを試みます。

### <a name="disposal-of-services"></a>サービスの破棄

コンテナーで作成された型のクリーンアップはコンテナーによって行われ、<xref:System.IDisposable> インスタンスで <xref:System.IDisposable.Dispose%2A> が呼び出されます。 コンテナーから解決されたサービスが、開発者によって破棄されることはありません。 型またはファクトリがシングルトンとして登録されている場合、コンテナーによってシングルトンが自動的に破棄されます。

次の例では、サービスがサービス コンテナーによって作成され、自動的に破棄されます。

:::code language="csharp" source="snippets/configuration/console-di-disposable/TransientDisposable.cs":::

上の破棄は、一時的な有効期間を使用するためのものです。

:::code language="csharp" source="snippets/configuration/console-di-disposable/ScopedDisposable.cs":::

上の破棄は、スコープ付きの有効期間を使用するためのものです。

:::code language="csharp" source="snippets/configuration/console-di-disposable/SingletonDisposable.cs":::

上の破棄は、シングルトン有効期間を使用するためのものです。

:::code language="csharp" source="snippets/configuration/console-di-disposable/Program.cs" range="1-21,41-60" highlight="":::

デバッグ コンソールには、実行後に次のサンプル出力が表示されます。

```console
Scope 1...
ScopedDisposable.Dispose()
TransientDisposable.Dispose()

Scope 2...
ScopedDisposable.Dispose()
TransientDisposable.Dispose()

info: Microsoft.Hosting.Lifetime[0]
      Application started.Press Ctrl+C to shut down.
info: Microsoft.Hosting.Lifetime[0]
     Hosting environment: Production
info: Microsoft.Hosting.Lifetime[0]
     Content root path: .\configuration\console-di-disposable\bin\Debug\net5.0
info: Microsoft.Hosting.Lifetime[0]
     Application is shutting down...
SingletonDisposable.Dispose()
```

### <a name="services-not-created-by-the-service-container"></a>サービス コンテナーによって作成されていないサービス

次のコードがあるとします。

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddSingleton(new ExampleService());

    // ...
}
```

上のコードでは以下の操作が行われます。

- サービス コンテナーにより、`ExampleService` インスタンスが作成されることは **ありません**。
- フレームワークにより、サービスが自動的に破棄されることは **ありません**。
- サービスを破棄する責任は開発者にあります。

### <a name="idisposable-guidance-for-transient-and-shared-instances"></a>一時的なインスタンスと共有インスタンスのための IDisposable ガイダンス

#### <a name="transient-limited-lifetime"></a>一時的で限定的な有効期間

**シナリオ**

アプリには、次のいずれかのシナリオに対して一時的な有効期間を持つ <xref:System.IDisposable> インスタンスが必要です。

- インスタンスは、ルート スコープ (ルート コンテナー) で解決されます。
- インスタンスは、スコープが終了する前に破棄する必要があります。

**解決方法**

ファクトリ パターンを使用して、親スコープの外部にインスタンスを作成します。 このような状況では、通常、アプリケーションには、最終的な型のコンストラクターを直接呼び出す `Create` メソッドがあります。 最終的な型に他の依存関係がある場合、ファクトリは次のことができます。

- そのコンストラクターで <xref:System.IServiceProvider> を受け取る。
- <xref:Microsoft.Extensions.DependencyInjection.ActivatorUtilities.CreateInstance%2A?displayProperty=nameWithType> を使用してコンテナー外部でインスタンスをインスタンス化し、同時にコンテナーを依存関係のために使用する。

#### <a name="shared-instance-limited-lifetime"></a>共有インスタンス、限定的な有効期間

**シナリオ**

アプリでは、複数のサービスにわたって共有 <xref:System.IDisposable> インスタンスが必要ですが、<xref:System.IDisposable> インスタンスの有効期間は限られています。

**解決方法**

インスタンスをスコープ付きの有効期間で登録します。 <xref:Microsoft.Extensions.DependencyInjection.IServiceScopeFactory.CreateScope%2A?displayProperty=nameWithType> を使用して新しい <xref:Microsoft.Extensions.DependencyInjection.IServiceScope>を作成します。 スコープの <xref:System.IServiceProvider> を使用して必要なサービスを取得します。 不要になったスコープを破棄します。

#### <a name="general-idisposable-guidelines"></a>`IDisposable` の一般的なガイドライン

- <xref:System.IDisposable> インスタンスは、一時的な有効期間で登録しないでください。 代わりに、ファクトリ パターンを使用します。
- 一時的またはスコープ付きの有効期間の <xref:System.IDisposable> インスタンスをルート スコープ内で解決しないでください。 唯一の例外は、アプリが <xref:System.IServiceProvider> を作成/再作成し、破棄する場合ですが、これは理想的なパターンではありません。
- DI を使用して <xref:System.IDisposable> 依存関係を受け取る場合、受信側が <xref:System.IDisposable> 自体を実装する必要はありません。 <xref:System.IDisposable> 依存関係の受信側は、その依存関係で <xref:System.IDisposable.Dispose%2A> を呼び出してはなりません。
- サービスの有効期間を制御するには、スコープを使用します。 スコープは階層構造ではなく、スコープ間に特別な接続はありません。

リソースのクリーンアップの詳細については、「[`Dispose` メソッドの実装](../../standard/garbage-collection/implementing-dispose.md)」または「[`DisposeAsync` メソッドの実装](../../standard/garbage-collection/implementing-disposeasync.md)」を参照してください。 また、リソースのクリーンアップに関係があるので、「[コンテナーによってキャプチャされた破棄可能な一時サービス](#disposable-transient-services-captured-by-container)」のシナリオについても検討してください。

## <a name="default-service-container-replacement"></a>既定のサービス コンテナーの置換

組み込みのサービス コンテナーは、フレームワークと、ほとんどのコンシューマー アプリのニーズに対応することを目的としたものです。 次のようなサポートされない特定の機能が必要な場合でなければ、組み込みのコンテナーを使用することをお勧めします。

- プロパティの挿入
- 名前に基づく挿入
- 子コンテナー
- 有効期間のカスタム管理
- 遅延初期化に対する `Func<T>` のサポート
- 規則に基づく登録

次のサードパーティ コンテナーは ASP.NET Core アプリで使用できます。

- [Autofac](https://autofac.readthedocs.io/en/latest/integration/aspnetcore.html)
- [DryIoc](https://www.nuget.org/packages/DryIoc.Microsoft.DependencyInjection)
- [Grace](https://www.nuget.org/packages/Grace.DependencyInjection.Extensions)
- [LightInject](https://github.com/seesharper/LightInject.Microsoft.DependencyInjection)
- [Lamar](https://jasperfx.github.io/lamar/)
- [Stashbox](https://github.com/z4kn4fein/stashbox-extensions-dependencyinjection)
- [Unity](https://www.nuget.org/packages/Unity.Microsoft.DependencyInjection)

## <a name="thread-safety"></a>スレッド セーフ

スレッド セーフのシングルトン サービスを作成します。 シングルトン サービスに一時的なサービスへの依存関係がある場合、シングルトンによる使い方によっては、一時的なサービスもスレッド セーフであることが必要な場合があります。

シングルトン サービスのファクトリ メソッド (例: [AddSingleton\<TService>(IServiceCollection, Func\<IServiceProvider,TService>)](xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddSingleton%2A) に対する 2 番目の引数) を、スレッドセーフにする必要はありません。 型 (`static`) のコンストラクターのように、1 つのスレッドによって 1 回のみ呼び出されることが保証されます。

## <a name="recommendations"></a>Recommendations

- `async/await` および `Task` ベースのサービスの解決はサポートされていません。 C# では非同期コンストラクターがサポートされていないため、非同期メソッドはサービスを同期的に解決した後に使用してください。
- データと構成をサービス コンテナーに直接格納しないようにします。 たとえば、通常、ユーザーのショッピング カートはサービス コンテナーに追加しません。 構成では、オプション パターンを使う必要があります。 同様に、他のオブジェクトへのアクセスを許可するためだけに存在する "データ ホルダー" オブジェクトは避ける必要があります。 実際のアイテムを DI 経由で要求することをお勧めします。
- サービスへの静的なアクセスを行わないようにします。 たとえば、他の場所で使用するために [IApplicationBuilder.ApplicationServices](xref:Microsoft.AspNetCore.Builder.IApplicationBuilder.ApplicationServices) を静的フィールドまたはプロパティとしてキャプチャしないようにしてください。
- [DI ファクトリ](#async-di-factories-can-cause-deadlocks)の高速性と同期性を維持します。
- [*サービス ロケーター パターン*](#scoped-service-as-singleton)は使用しないようにします。 たとえば、サービス インスタンスを取得する場合、DI を使用できるときに、<xref:System.IServiceProvider.GetService%2A> を呼び出さないでください。
- 回避すべき別のサービス ロケーターのバリエーションは、実行時に依存関係を解決するファクトリを挿入することです。 この両方のプラクティスによって、複数の[制御の反転](/dotnet/standard/modern-web-apps-azure-architecture/architectural-principles#dependency-inversion)方式が組み合わせられます。
- `ConfigureServices` で <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> を呼び出すことは避けてください。 `BuildServiceProvider` の呼び出しは、通常、開発者が `ConfigureServices` でサービスを解決する必要がある場合に発生します。
- [破棄可能な一時サービスは、破棄のためにコンテナーによってキャプチャ](#disposable-transient-services-captured-by-container)されます。 これにより、最上位のコンテナーから解決された場合、メモリ リークが発生する可能性があります。
- スコープの検証を有効にすることで、アプリにスコープ付きサービスをキャプチャするシングルトンがないようにします。 詳しくは、「[スコープの検証](dependency-injection.md#scope-validation)」をご覧ください。

どのような推奨事項であっても、それを無視する必要がある状況が発生する可能性があります。 例外はまれです。ほとんどがフレームワーク自体の内の特殊なケースです。

DI は静的/グローバル オブジェクト アクセス パターンの *代替機能* です。 静的オブジェクト アクセスと併用した場合、DI のメリットを実現することはできません。

## <a name="example-anti-patterns"></a>アンチパターンの例

この記事のガイドラインに加えて、"*回避する **必要がある***" アンチパターンがいくつかあります。 このようなアンチパターンの一部は、ランタイム自体の開発によってわかることです。

> [!WARNING]
> これらはアンチパターンの例です。そのコードをコピー "*しないでください*"。これらのパターンを使用 "*しないでください*"。そして、これらのパターンは絶対に避けてください。

### <a name="disposable-transient-services-captured-by-container"></a>コンテナーによってキャプチャされる破棄可能な一時サービス

<xref:System.IDisposable> が実装されている "*一時*" サービスを登録すると、既定では、アプリケーションが停止してコンテナーが破棄されるまで (コンテナーから解決された場合) またはスコープが破棄されるまで (スコープから解決された場合)、これらの <xref:System.IDisposable.Dispose> ではなく、これらの参照が DI コンテナーに保持されます。 これにより、コンテナー レベルから解決された場合、メモリ リークが発生する可能性があります。

:::code language="csharp" source="snippets/configuration/di-anti-patterns/Program.cs" range="18-30":::

前のアンチパターンでは、1,000 の `ExampleDisposable` オブジェクトがインスタンス化されてルート化されます。 それらは、`serviceProvider` のインスタンスが破棄されるまで破棄されません。

メモリ リークのデバッグの詳細については、[.NET でのメモリ リークのデバッグ](../diagnostics/debug-memory-leak.md)に関する記事を参照してください。

### <a name="async-di-factories-can-cause-deadlocks"></a>非同期 DI ファクトリでデッドロックが発生する可能性がある

"DI ファクトリ" とは、`Add{LIFETIME}` を呼び出すと存在するようになるオーバーロード メソッドのことです。 `Func<IServiceProvider, T>` を受け入れるオーバーロードがあります。`T` は登録されているサービスであり、パラメーターの名前は `implementationFactory` です。 `implementationFactory` は、ラムダ式、ローカル関数、またはメソッドとして提供できます。 ファクトリが非同期であり、<xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> を使用している場合、デッドロックが発生します。

:::code language="csharp" source="snippets/configuration/di-anti-patterns/Program.cs" range="32-45" highlight="4-8":::

前のコードでは、`implementationFactory` にラムダ式が提供され、その本体で `Task<Bar>` の <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> が呼び出されてメソッドが返されます。 これにより、"***デッドロックが発生します***"。 `GetBarAsync` メソッドは <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> で非同期操作を単にエミュレートしてから、<xref:Microsoft.Extensions.DependencyInjection.ServiceProviderServiceExtensions.GetRequiredService%60%601(System.IServiceProvider)> を呼び出します。

:::code language="csharp" source="snippets/configuration/di-anti-patterns/Program.cs" range="47-53":::

非同期ガイダンスの詳細については、「[非同期プログラミング: 重要な情報とアドバイス](../../csharp/async.md#important-info-and-advice)」を参照してください。 デッドロックのデバッグの詳細については、[.NET でのデッドロックのデバッグ](../diagnostics/debug-deadlock.md)に関する記事を参照してください。

このアンチパターンを実行していてデッドロックが発生した場合は、Visual Studio の [並列スタック] ウィンドウで待機している 2 つのスレッドを確認できます。 詳細については、「[[並列スタック] ウィンドウでスレッドを表示する](/visualstudio/debugger/using-the-parallel-stacks-window)」を参照してください。

### <a name="captive-dependency"></a>キャプティブ依存関係

[Mark Seeman](https://blog.ploeh.dk/about) によって作成された ["キャプティブ依存関係"](https://blog.ploeh.dk/2014/06/02/captive-dependency) という用語は、サービスの有効期間の誤った構成により、有効期間が長いサービスによって有効期間の短いサービスが捕獲されることを意味します。

:::code language="csharp" source="snippets/configuration/di-anti-patterns/Program.cs" range="55-65":::

上のコードで、`Foo` はシングルトンとして登録され、`Bar` はスコープ指定されています。これは表面上は有効であるように見えます。 しかし、`Foo` の実装を考えてみてください。

:::code language="csharp" source="snippets/configuration/di-anti-patterns/Foo.cs" highlight="5":::

`Foo` オブジェクトには `Bar` オブジェクトが必要であり、`Foo` はシングルトンであるため、`Bar` はスコープ指定されます。これは不適切な構成です。 そのように、`Foo` は 1 回だけインスタンス化され、その有効期間にわたって `Bar` を保持します。これは、`Bar` の意図されるスコープ指定された有効期間より長くなります。 `validateScopes: true` を <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Boolean)> に渡すことによって、スコープを検証することを検討する必要があります。 スコープを検証すると、<xref:System.InvalidOperationException> と "シングルトン 'Foo' からスコープ指定されたサービス 'bar' を使用することはできません" のようなメッセージを受け取ります。

詳しくは、「[スコープの検証](dependency-injection.md#scope-validation)」をご覧ください。

### <a name="scoped-service-as-singleton"></a>シングルトンとしてのスコープ指定されたサービス

スコープ指定されたサービスを使用するとき、スコープを作成しない場合、または既存のスコープ内にいない場合は、サービスはシングルトンになります。

:::code language="csharp" source="snippets/configuration/di-anti-patterns/Program.cs" range="68-82" highlight="13-14":::

上のコードで、`Bar` は <xref:Microsoft.Extensions.DependencyInjection.IServiceScope> 内で取得されており、これは正しいことです。 アンチパターンの場合は、`Bar` はスコープの外側で取得されており、どの例の取得が正しくないかを示すため、変数には `avoid` という名前が付けられています。

## <a name="see-also"></a>関連項目

- [.NET での依存関係の挿入](dependency-injection.md)
- [チュートリアル: .NET で依存関係の挿入を使用する](dependency-injection-usage.md)
