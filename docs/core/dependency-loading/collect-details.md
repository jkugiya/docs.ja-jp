---
title: アセンブリの読み込みに関する詳細情報の収集 - .NET Core
description: .NET Core でアセンブリの読み込み情報を収集する方法の説明
author: elinor-fung
ms.author: elfung
ms.date: 11/17/2020
ms.openlocfilehash: 505fc827021fe4d34675b2ef5a7fc5746ada1af6
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104872939"
---
# <a name="collect-detailed-assembly-loading-information"></a>アセンブリの読み込みに関する詳細情報の収集

.NET 5.0 以降、ランタイムを使用して、`EventPipe` を介して[マネージド アセンブリの読み込み](loading-managed.md)に関する詳細情報を含むイベントを発行し、アセンブリの読み込みに関する問題の診断に役立てることができるようになりました。 これらの[イベント](../../fundamentals/diagnostics/runtime-loader-binder-events.md)は、`AssemblyLoader` キーワード (`0x4`) に従い `Microsoft-Windows-DotNETRuntime` プロバイダーによって発行されます。

## <a name="prerequisites"></a>前提条件

- [.NET 5.0 SDK](https://dotnet.microsoft.com/download) 以降のバージョン
- [dotnet-trace](../diagnostics/dotnet-trace.md) ツール。

## <a name="collect-a-trace-with-assembly-loading-events"></a>アセンブリの読み込みイベントを使用してトレースを収集する

ランタイムでアセンブリの読み込みイベントを有効にし、それらのトレースを収集するには、次のコマンドで `dotnet-trace` を使用します。

```console
dotnet-trace collect --providers Microsoft-Windows-DotNETRuntime:4 --process-id <pid>
```

これにより、`Microsoft-Windows-DotNETRuntime` プロバイダーで `AssemblyLoader` イベントが有効になり、指定された `<pid>` のトレースが収集されます。 結果は `.nettrace` ファイルになります。

## <a name="view-a-trace"></a>トレースを表示する

収集されたトレース ファイルは、Windows 上で [PerfView](https://github.com/microsoft/perfview) の [Events]\(イベント\) ビューを使用して表示できます。 すべてのアセンブリの読み込みイベントには、`Microsoft-Windows-DotNETRuntime/AssemblyLoader` というプレフィックスが付きます。

## <a name="example-on-windows"></a>例 (Windows の場合)

この例では、[アセンブリの読み込み拡張ポイントのサンプル](https://docs.microsoft.com/samples/dotnet/samples/assembly-loading-extension-points/)を使用します。 このアプリケーションにより、アセンブリ `MyLibrary` (アプリケーションから参照されていないアセンブリ) の読み込みが試行されます。そのため、正常に読み込むには、アセンブリの読み込み拡張ポイントでの処理が必要です。

### <a name="collect-the-trace"></a>トレースを収集する

01. ダウンロードしたサンプルのあるディレクトリに移動します。 次を使用してアプリケーションをビルドします。

    ```console
    dotnet build
    ```

01. 一時停止する必要があることを示す引数を指定してアプリケーションを起動し、キーの押下を待機します。 再開すると、既定の `AssemblyLoadContext` でアセンブリの読み込みが試行されます。正常に読み込むために必要な処理は行われません。 出力ディレクトリに移動し、次を実行します。

    ```console
    AssemblyLoading.exe /d default
    ```

01. アプリケーションのプロセス ID を見つけます。

    ```console
    dotnet-trace ps
    ```

    出力には、使用できるプロセスが一覧表示されます。 次に例を示します。

    ```console
    35832 AssemblyLoading C:\src\AssemblyLoading\bin\Debug\net5.0\AssemblyLoading.exe
    ```

01. 実行中のアプリケーションに `dotnet-trace` をアタッチします。

    ```console
    dotnet-trace collect --providers Microsoft-Windows-DotNETRuntime:4 --process-id 35832
    ```

01. アプリケーションを実行しているウィンドウで、任意のキーを押してプログラムを続行します。 アプリケーションが終了すると、トレースは自動的に停止します。

### <a name="view-the-trace"></a>トレースを表示する

収集したトレースを [PerfView](https://github.com/microsoft/perfview) で開き、[Events]\(イベント\) ビューを開きます。 イベント一覧をフィルター処理して `Microsoft-Windows-DotNETRuntime/AssemblyLoader` イベントを表示します。

:::image type="content" source="media/collect-details/assembly-loader-filter.png" alt-text="PerfView のアセンブリ ローダーのフィルターの画像":::

トレースの開始後にアプリケーションで発生したすべてのアセンブリの読み込みが表示されます。 この例 (`MyLibrary`) の対象となるアセンブリの読み込み操作を調べるために、さらにフィルター処理を実行することができます。

### <a name="assembly-loads"></a>アセンブリの読み込み

左側のイベント一覧を使用し、ビューをフィルター処理して `Microsoft-Windows-DotNETRuntime/AssemblyLoader` 以下の [`Start`](../../fundamentals/diagnostics/runtime-loader-binder-events.md#assemblyloadstart-event) および [`Stop`](../../fundamentals/diagnostics/runtime-loader-binder-events.md#assemblyloadstop-event) イベントを表示します。 列 `AssemblyName`、`ActivityID`、および `Success` をビューに追加します。 フィルター処理して `MyLibrary` を含むイベントを表示します。

:::image type="content" source="media/collect-details/start-stop.png" alt-text="PerfView の開始および終了イベントの画像":::

| イベント名             | AssemblyName                                      | ActivityID | 成功 |
| ---------------------- | ------------------------------------------------- | ---------- | ------- |
| `AssemblyLoader/Start` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | //1/2/     |         |
| `AssemblyLoader/Stop`  | `MyLibrary, Culture=neutral, PublicKeyToken=null` | //1/2/     | False   |

`Stop` イベントに 1 つの `Start`/`Stop` ペアと `Success=False` があります。これは、読み込み操作が失敗したことを示します。 2 つのイベントのアクティビティ ID が同じであることに注意してください。 アクティビティ ID を使用すると、他のすべてのアセンブリ ローダー イベントを、この読み込み操作に対応するイベントのみにフィルター処理することができます。

### <a name="breakdown-of-attempt-to-load"></a>読み込みの試行の内訳

読み込み操作の詳細な内訳については、左側のイベント一覧を使用し、ビューをフィルター処理して `Microsoft-Windows-DotNETRuntime/AssemblyLoader` 以下の [`ResolutionAttempted` イベント](../../fundamentals/diagnostics/runtime-loader-binder-events.md#resolutionattempted-event)を表示します。 列 `AssemblyName`、`Stage`、および `Result` をビューに追加します。 フィルター処理して、`Start`/`Stop` ペアのうち、そのアクティビティ ID を持つイベントを表示します。

:::image type="content" source="media/collect-details/resolution-attempted.png" alt-text="PerfView の ResolutionAttempted イベントの画像":::

| イベント名                           | AssemblyName                                      | 段階                               | 結果             |
| ------------------------------------ | ------------------------------------------------- | ----------------------------------- | ------------------ |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `FindInLoadContext`                 | `AssemblyNotFound` |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `ApplicationAssemblies`             | `AssemblyNotFound` |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `AssemblyLoadContextResolvingEvent` | `AssemblyNotFound` |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `AppDomainAssemblyResolveEvent`     | `AssemblyNotFound` |

上記のイベントは、アセンブリ ローダーによって、現在の読み込みコンテキストが確認され、マネージド アプリケーション アセンブリの既定のプローブ ロジックが実行され、<xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> イベントのハンドラーが呼び出され、<xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> のハンドラーを呼び出されるという手順で、アセンブリの解決が試行されたことを示しています。 これらすべての手順を実行しても、アセンブリは見つかりませんでした。

### <a name="extension-points"></a>拡張ポイント

呼び出された拡張ポイントを確認するには、左側のイベント一覧を使用し、ビューをフィルター処理して `Microsoft-Windows-DotNETRuntime/AssemblyLoader` 以下の [`AssemblyLoadContextResolvingHandlerInvoked`](../../fundamentals/diagnostics/runtime-loader-binder-events.md#assemblyloadcontextresolvinghandlerinvoked-event) および [`AppDomainAssemblyResolveHandlerInvoked`](../../fundamentals/diagnostics/runtime-loader-binder-events.md#appdomainassemblyresolvehandlerinvoked-event) を表示します。 列 `AssemblyName` および `HandlerName` をビューに追加します。 フィルター処理して、`Start`/`Stop` ペアのうち、そのアクティビティ ID を持つイベントを表示します。

:::image type="content" source="media/collect-details/extension-point.png" alt-text="PerfView の拡張ポイント イベントの画像":::

| イベント名                                                  | AssemblyName                                      | HandlerName                      |
| ----------------------------------------------------------- | ------------------------------------------------- | -------------------------------- |
| `AssemblyLoader/AssemblyLoadContextResolvingHandlerInvoked` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `OnAssemblyLoadContextResolving` |
| `AssemblyLoader/AppDomainAssemblyResolveHandlerInvoked`     | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `OnAppDomainAssemblyResolve`     |

上記のイベントは、`OnAssemblyLoadContextResolving` という名前のハンドラーが <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> イベントに対して呼び出され、`OnAppDomainAssemblyResolve` という名前のハンドラーが <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> イベントに対して呼び出されたことを示しています。

### <a name="collect-another-trace"></a>別のトレースを収集する

<xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> イベントのハンドラーによって `MyLibrary` アセンブリが読み込まれるように、引数を指定してアプリケーションを実行します。

```console
AssemblyLoading /d default alc-resolving
```

[上記の手順](#collect-the-trace)を使用して、別の `.nettrace` ファイルを収集して開きます。

フィルター処理して `MyLibrary` の `Start` および `Stop` イベントをもう一度表示します。 `Start`/`Stop` のペアとその間に別の `Start`/`Stop` があります。 内側にある読み込み操作は、<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromAssemblyPath%2A?displayProperty=nameWithType> が呼び出されたときに <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> のハンドラーによってトリガーされた読み込みを表します。 今回は、`Stop` イベントに `Success=True` があります。これは読み込み操作が成功したことを示しています。 `ResultAssemblyPath` フィールドには、結果のアセンブリのパスが表示されます。

:::image type="content" source="media/collect-details/start-stop-success.png" alt-text="PerfView の成功した開始および停止イベントの画像":::

| イベント名             | AssemblyName                                                       | ActivityID | 成功 | ResultAssemblyPath                                      |
| ---------------------- | ------------------------------------------------------------------ |------------|---------| ------------------------------------------------------- |
| `AssemblyLoader/Start` |                  `MyLibrary, Culture=neutral, PublicKeyToken=null` | //1/2/     |         |                                                         |
| `AssemblyLoader/Start` | `MyLibrary, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null` | //1/2/1/   |         |                                                         |
| `AssemblyLoader/Stop`  | `MyLibrary, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null` | //1/2/1/   | True    | *C:\src\AssemblyLoading\bin\Debug\net5.0\MyLibrary.dll* |
| `AssemblyLoader/Stop`  |                  `MyLibrary, Culture=neutral, PublicKeyToken=null` | //1/2/     | True    | *C:\src\AssemblyLoading\bin\Debug\net5.0\MyLibrary.dll* |

次に、外側の読み込みのアクティビティ ID を持つ `ResolutionAttempted` イベントを調べて、アセンブリが正常に解決されたステップを判断できます。 今回のイベントでは、`AssemblyLoadContextResolvingEvent` ステージが成功したことが示されます。 `ResultAssemblyPath` フィールドには、結果のアセンブリのパスが表示されます。

:::image type="content" source="media/collect-details/resolution-attempted-success.png" alt-text="PerfView の成功した ResolutionAttempted イベントの画像":::

| イベント名                           | AssemblyName                                      | 段階                               | 結果             | ResultAssemblyPath |
| ------------------------------------ | ------------------------------------------------- | ----------------------------------- | ------------------ | ------------------ |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `FindInLoadContext`                 | `AssemblyNotFound` |                    |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `ApplicationAssemblies`             | `AssemblyNotFound` |                    |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `AssemblyLoadContextResolvingEvent` | `Success`          | *C:\src\AssemblyLoading\bin\Debug\net5.0\MyLibrary.dll* |

`AssemblyLoadContextResolvingHandlerInvoked` イベントを見ると、`OnAssemblyLoadContextResolving` という名前のハンドラーが呼び出されたことがわかります。 `ResultAssemblyPath` フィールドには、ハンドラーから返されたアセンブリのパスが表示されます。

:::image type="content" source="media/collect-details/extension-point-success.png" alt-text="PerfView の成功した拡張ポイント イベントの画像":::

| イベント名                                                  | AssemblyName                                      | HandlerName                      | ResultAssemblyPath |
| ----------------------------------------------------------- | ------------------------------------------------- | -------------------------------- | ------------------ |
| `AssemblyLoader/AssemblyLoadContextResolvingHandlerInvoked` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `OnAssemblyLoadContextResolving` | *C:\src\AssemblyLoading\bin\Debug\net5.0\MyLibrary.dll* |

<xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> イベントを発生させる読み込みアルゴリズムのステップに到達する前にアセンブリが正常に読み込まれたため、`AppDomainAssemblyResolveEvent` ステージまたは `AppDomainAssemblyResolveHandlerInvoked` イベントを伴う `ResolutionAttempted` イベントは存在しないことに注意してください。

## <a name="see-also"></a>関連項目

- [アセンブリ ローダーのイベント](../../fundamentals/diagnostics/runtime-loader-binder-events.md)
- [dotnet-トレース](../diagnostics/dotnet-trace.md)
- [PerfView](https://github.com/microsoft/perfview)
