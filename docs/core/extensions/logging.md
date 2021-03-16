---
title: .NET でのログの記録
author: IEvangelist
description: Microsoft.Extensions.Logging NuGet パッケージで提供されるログ記録フレームワークの使用方法について説明します。
ms.author: dapine
ms.date: 02/19/2021
ms.openlocfilehash: 834331b9e103138012bbe91586d0d5a7c08654ce
ms.sourcegitcommit: bdbf6472de867a0a11aaa5b9384a2506c24f27d2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2021
ms.locfileid: "102402167"
---
# <a name="logging-in-net"></a>.NET でのログの記録

.NET では、組み込みやサード パーティ製のさまざまなログ プロバイダーと連携するログ API がサポートされています。 この記事では、組み込みプロバイダーと共にログ API を使用する方法について説明します。 この記事に示されているほとんどのコード例は、[汎用ホスト](generic-host.md)を使用する任意の .NET アプリに適用されます。 汎用ホストを使用しないアプリについては、「[ホスト コンソール以外のアプリ](#non-host-console-app)」を参照してください。

## <a name="create-logs"></a>ログを作成する

ログを作成するには、[依存関係の挿入 (DI)](dependency-injection.md) から <xref:Microsoft.Extensions.Logging.ILogger%601> オブジェクトを使用します。

次のような例です。

- `Worker` 型の完全修飾名のログ "*カテゴリ*" を使用する、ロガー `ILogger<Worker>` を作成します。 ログのカテゴリは、各ログに関連付けられている文字列です。
- <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogInformation%2A> を呼び出して、`Information` レベルでログを記録します。 ログの "*レベル*" は、ログに記録されるイベントの重大度を示します。

:::code language="csharp" source="snippets/configuration/worker-service/Worker.cs" range="9-24" highlight="12":::

[レベル](#log-level)と[カテゴリ](#log-category)の詳細については、この記事で後ほど説明します。

## <a name="configure-logging"></a>ログの構成

一般的に、ログの構成は *appsettings*.`{Environment}` *.json* ファイルの `Logging` セクションで指定されます。 次の *appsettings.Development.json* ファイルは、.NET Worker サービス テンプレートによって生成されます。

:::code language="json" source="snippets/configuration/worker-service/appsettings.Development.json":::

上記の JSON では、次のように指定されています。

- `"Default"`、`"Microsoft"`、および `"Microsoft.Hosting.Lifetime"` の各カテゴリが指定されています。
- `"Microsoft"` カテゴリは、`"Microsoft"` で始まるすべてのカテゴリに適用されます。
- `"Microsoft"` カテゴリでは、ログ レベルが `Warning` 以上のログが記録されます。
- `"Microsoft.Hosting.Lifetime"` カテゴリは `"Microsoft"` カテゴリよりも詳細なので、`"Microsoft.Hosting.Lifetime"` カテゴリではログ レベルが "情報" 以上のログが記録されます。
- 特定のログ プロバイダーが指定されていないため、`LogLevel` は、[Windows EventLog](logging-providers.md#windows-eventlog) を除くすべての有効なログ プロバイダーに適用されます。

`Logging` プロパティには <xref:Microsoft.Extensions.Logging.LogLevel> およびログ プロバイダーのプロパティを含めることができます。 `LogLevel` により、選択したカテゴリに対するログの最小[レベル](#log-level)が指定されます。 上記の JSON では、`Information` と `Warning` のログ レベルが指定されています。 `LogLevel` はログの重大度を 0 - 6 の範囲で示します。

`Trace` = 0、`Debug` = 1、`Information` = 2、`Warning` = 3、`Error` = 4、`Critical` = 5、`None` = 6。

`LogLevel` を指定すると、指定したレベル以上のメッセージに対してログが有効になります。 上記の JSON では、`Default` カテゴリは `Information` 以上に対してのみログに記録されます。 たとえば、`Information`、`Warning`、`Error`、`Critical` のメッセージがログに記録されます。 `LogLevel` が指定されていない場合、ログは既定で `Information` レベルになります。 詳細については、「[ログ レベル](#log-level)」を参照してください。

プロバイダー プロパティで `LogLevel` プロパティを指定できます。 プロバイダーの下の `LogLevel` によって、そのプロバイダーのログに記録するレベルが指定され、プロバイダー以外のログ設定がオーバーライドされます。 以下の *appsettings.json* ファイルについて考えます:

:::code language="json" source="snippets/configuration/worker-service/appsettings.Staging.json":::

`Logging.{ProviderName}.LogLevel` の設定により `Logging.LogLevel` の設定がオーバーライドされます。 上記の JSON では、`Debug` プロバイダーの既定のログ レベルは `Information` に設定されています。

`Logging:Debug:LogLevel:Default:Information`

上記の設定により、`Microsoft.Hosting` 以外のすべての `Logging:Debug:` カテゴリに `Information` ログ レベルが指定されます。 特定のカテゴリが一覧表示されると、特定のカテゴリによって既定のカテゴリがオーバーライドされます。 上記の JSON では、`Logging:Debug:LogLevel` カテゴリ `"Microsoft.Hosting"` と `"Default"` によって、`Logging:LogLevel` の設定がオーバーライドされます。

最小ログ レベルは、次のいずれかに指定できます。

- 特定のプロバイダー: たとえば、`Logging:EventSource:LogLevel:Default:Information`
- 特定のカテゴリ: たとえば、`Logging:LogLevel:Microsoft:Warning`
- すべてのプロバイダーとすべてのカテゴリ: `Logging:LogLevel:Default:Warning`

最小レベルを下回るログは、次のことが "***行われません***"。

- プロバイダーに渡される。
- ログに記録または表示される。

すべてのログを抑制するには、[LogLevel.None](xref:Microsoft.Extensions.Logging.LogLevel) を指定します。 `LogLevel.None` の値は、`LogLevel.Critical` (5) より大きい 6 です。

プロバイダーで[ログのスコープ](#log-scopes)がサポートされている場合、`IncludeScopes` によってそれを有効にするかどうかが指定されます。 詳細については、「[ログ スコープ](#log-scopes)」を参照してください。

次の *appsettings.json* ファイルには、すべての組み込みプロバイダー用の設定が含まれています。

:::code language="json" source="snippets/configuration/worker-service/appsettings.Production.json":::

上記のサンプルについて:

- カテゴリとレベルは推奨値ではありません。 このサンプルは、すべての既定のプロバイダーを表示するために提供されています。
- `Logging.{ProviderName}.LogLevel` の設定により `Logging.LogLevel` の設定がオーバーライドされます。 たとえば、`Debug.LogLevel.Default` のレベルにより `LogLevel.Default` のレベルがオーバーライドされます。
- 各プロバイダーの "*エイリアス*" が使用されています。 各プロバイダーでは "*エイリアス*" が定義されます。これは構成で完全修飾型名の代わりに使用できます。 組み込みプロバイダーのエイリアスは次のとおりです。
  - コンソール
  - デバッグ
  - EventSource
  - EventLog
  - AzureAppServicesFile
  - AzureAppServicesBlob
  - ApplicationInsights

### <a name="set-log-level-by-command-line-environment-variables-and-other-configuration"></a>コマンド ライン、環境変数、およびその他の構成でログ レベルを設定する

ログ レベルは、いずれかの[構成プロバイダー](configuration-providers.md)で設定できます。 たとえば、名前が `Logging:LogLevel:Microsoft` で値が `Information` の永続化された環境変数を作成できます。

## <a name="command-line"></a>[コマンド ライン](#tab/command-line)

ログ レベルの値が代入された、永続化された環境変数を作成します。

```CMD
:: Assigns the env var to the value
setx "Logging__LogLevel__Microsoft" "Information" /M
```

**コマンド プロンプト** の "*新しい*" インスタンスで、環境変数を読み取ります。

```CMD
:: Prints the env var value
echo %Logging__LogLevel__Microsoft%
```

## <a name="powershell"></a>[PowerShell](#tab/powershell)

ログ レベルの値が代入された、永続化された環境変数を作成します。

```powershell
# Assigns the env var to the value
[System.Environment]::SetEnvironmentVariable(
    "Logging__LogLevel__Microsoft", "Information", "Machine")
```

**PowerShell** の "*新しい*" インスタンスで、環境変数を読み取ります。

```powershell
# Prints the env var value
[System.Environment]::GetEnvironmentVariable(
    "Logging__LogLevel__Microsoft", "Machine")
```

## <a name="bash"></a>[Bash](#tab/bash)

ログ レベルの値が代入された、永続化された環境変数を作成します。

```Bash
# Assigns the env var to the value, persists it across sessions
echo export Logging__LogLevel__Microsoft="Information" >> ~/.bashrc && source ~/.bashrc
```

環境変数を読み取ります。

```Bash
# Prints the env var value
echo $Logging__LogLevel__Microsoft

# Or use printenv:
# printenv Logging__LogLevel__Microsoft
```

> [!NOTE]
> `.` (ピリオド) を含む名前で環境変数を構成する場合は、**Stack Exchange** の「ドット (.) が含まれる変数のエクスポート」という質問と、それに対して[受け入れられた回答](https://unix.stackexchange.com/a/93533)を考慮してください。

---

上記の環境設定は、環境内に保持されます。 .NET Worker サービス テンプレートで作成されたアプリを使用して設定をテストするには、環境変数に代入した後、プロジェクト ディレクトリ内で `dotnet run` コマンドを使用します。

```dotnetcli
dotnet run
```

> [!TIP]
> 環境変数を設定した後、統合開発環境 (IDE) を再起動して、新しく追加した環境変数を使用できることを確認します。

[Azure App Service](https://azure.microsoft.com/services/app-service/) で、 **設定 > 構成** ページの **新しいアプリケーション設定** を選択します。 Azure App Service アプリケーションの設定は：

- 保存時に暗号化され、暗号化されたチャネルで送信されます。
- 環境変数として公開されます。

環境変数を使用して .NET 構成値を設定する方法の詳細については、[環境変数](configuration-providers.md#environment-variable-configuration-provider)に関する記事を参照してください。

## <a name="how-filtering-rules-are-applied"></a>フィルター規則を適用する方法

<xref:Microsoft.Extensions.Logging.ILogger%601> オブジェクトを作成すると、<xref:Microsoft.Extensions.Logging.ILoggerFactory> オブジェクトによって、そのロガーに適用するプロバイダーごとに 1 つの規則が選択されます。 `ILogger` インスタンスによって書き込まれるすべてのメッセージは、選択した規則に基づいてフィルター処理されます。 使用できる規則から、各プロバイダーとカテゴリのペアごとに最も明確な規則が選択されます。

特定のカテゴリに `ILogger` が作成されるときに、各プロバイダーに次のアルゴリズムが使用されます。

- プロバイダーとそのエイリアスと一致するすべての規則が選択されます。 一致が見つからない場合は、空のプロバイダーですべての規則が選択されます。
- 前の手順の結果、最も長いカテゴリのプレフィックスが一致する規則が選択されます。 一致が見つからない場合は、カテゴリを指定しないすべての規則が選択されます。
- 複数の規則が選択されている場合は、**最後** の 1 つが使用されます。
- 規則が選択されていない場合は、<xref:Microsoft.Extensions.Logging.LoggingBuilderExtensions.SetMinimumLevel(Microsoft.Extensions.Logging.ILoggingBuilder,Microsoft.Extensions.Logging.LogLevel)?displayProperty=nameWithType> を使用して最小ログ記録レベルを指定します。

## <a name="log-category"></a>ログのカテゴリ

`ILogger` オブジェクトが作成されるときに、"*カテゴリ*" が指定されます。 このカテゴリは、`ILogger` のインスタンスによって作成される各ログ メッセージと共に含められます。 カテゴリ文字列は任意ですが、規則ではクラス名を使用します。 たとえば、サービスが次のオブジェクトように定義されているアプリケーションでは、カテゴリは `"Example.DefaultService"` のようになります。

```csharp
namespace Example
{
    public class DefaultService : IService
    {
        private readonly ILogger<DefaultService> _logger;

        public DefaultService(ILogger<DefaultService> logger) =>
            _logger = logger;

        // ...
    }
}
```

カテゴリを明示的に指定するには、<xref:Microsoft.Extensions.Logging.LoggerFactory.CreateLogger%2A?displayProperty=nameWithType> を呼び出します。

```csharp
namespace Example
{
    public class DefaultService : IService
    {
        private readonly ILogger _logger;

        public DefaultService(ILoggerFactory loggerFactory) =>
            _logger = loggerFactory.CreateLogger("CustomCategory");

        // ...
    }
}
```

複数のクラスや型で使用する場合、固定名を使用して `CreateLogger` を呼び出すと、イベントをカテゴリ別に分類できるので便利です。

`ILogger<T>` は、`T` の完全修飾型名を使用した `CreateLogger` の呼び出しと同じです。

## <a name="log-level"></a>ログ レベル

次の表に、<xref:Microsoft.Extensions.Logging.LogLevel> 値、便利な `Log{LogLevel}` 拡張メソッド、推奨される使用法を示します。

| LogLevel | [値] | Method | 説明 |
|--|--|--|--|
| [トレース](xref:Microsoft.Extensions.Logging.LogLevel) | 0 | <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogTrace%2A> | 最も詳細なメッセージが含まれます。 これらのメッセージには、機密性の高いアプリ データが含まれる場合があります。 これらのメッセージは既定で無効になっているため、運用環境では有効に "***しないでください***"。 |
| [デバッグ](xref:Microsoft.Extensions.Logging.LogLevel) | 1 | <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogDebug%2A> | デバッグと開発用。 量が多いため、運用環境では慎重に使用してください。 |
| [情報](xref:Microsoft.Extensions.Logging.LogLevel) | 2 | <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogInformation%2A> | アプリの一般的なフローを追跡します。 長期的な値が含まれている可能性があります。 |
| [警告](xref:Microsoft.Extensions.Logging.LogLevel) | 3 | <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogWarning%2A> | 異常なイベントや予期しないイベント用。 通常、アプリが失敗する原因にならないエラーや条件が含まれます。 |
| [エラー](xref:Microsoft.Extensions.Logging.LogLevel) | 4 | <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogError%2A> | 処理できないエラーと例外の場合。 これらのメッセージは、アプリ全体のエラーではなく、現在の操作や要求における失敗を示します。 |
| [重大](xref:Microsoft.Extensions.Logging.LogLevel) | 5 | <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogCritical%2A> | 即時の注意が必要なエラーの場合。 例: データ損失のシナリオ、ディスク領域不足。 |
| [None](xref:Microsoft.Extensions.Logging.LogLevel) | 6 |  | メッセージを書き込む必要がないことを指定します。 |

前の表では、重大度が最も低い方から高い方に `LogLevel` が一覧表示されています。

[Log](xref:Microsoft.Extensions.Logging.LoggerExtensions) メソッドの最初のパラメーター <xref:Microsoft.Extensions.Logging.LogLevel> は、ログの重大度を示します。 ほとんどの開発者は、`Log(LogLevel, ...)` を呼び出すのではなく、[Log{LogLevel}](xref:Microsoft.Extensions.Logging.LoggerExtensions) 拡張メソッドを呼び出します。 `Log{LogLevel}` 拡張メソッドによって、[Log メソッドが呼び出され、LogLevel が指定されます](https://github.com/dotnet/extensions/blob/release/3.1/src/Logging/Logging.Abstractions/src/LoggerExtensions.cs)。 たとえば、次の 2 つのログ呼び出しは、機能的に同等で、同じログが生成されます。

```csharp
public void LogDetails()
{
    var logMessage = "Details for log.";

    _logger.Log(LogLevel.Information, AppLogEvents.Details, logMessage);
    _logger.LogInformation(AppLogEvents.Details, logMessage);
}
```

`AppLogEvents.Details` はイベント ID であり、暗黙的に <xref:System.Int32> 定数値によって表されます。 `AppLogEvents` はさまざまな名前付き識別子定数を公開するクラスであり、[ログ イベント ID](#log-event-id) セクションに表示されます。

`Information` および `Warning` ログを作成するコードを次に示します。

```csharp
public async Task<T> GetAsync<T>(string id)
{
    _logger.LogInformation(AppLogEvents.Read, "Reading value for {Id}", id);

    var result = await _repository.GetAsync(id);
    if (result is null)
    {
        _logger.LogWarning(AppLogEvents.ReadNotFound, "GetAsync({Id}) not found", id);
    }

    return result;
}
```

上記のコードでは、最初の `Log{LogLevel}` パラメーター `AppLogEvents.Read` は、[ログ イベント ID](#log-event-id) です。 2 つ目のパラメーターは、他のメソッド パラメーターによって提供される引数値のプレースホルダーを含むメッセージ テンプレートです。 メソッド パラメーターについては、この記事の後半の[メッセージ テンプレート](#log-message-template)に関するセクションで説明します。

適切なログ レベルを構成し、適切な `Log{LogLevel}` メソッドを呼び出して、特定のストレージ メディアに書き込むログ出力の量を制御します。 次に例を示します。

- 運用環境:
  - `Trace` または `Information` のレベルでログを記録すると、詳細なログ メッセージが大量に生成されます。 コストを制御し、データ ストレージの上限を超えないようにするには、`Trace` および `Information` のレベルのメッセージを、大容量の低コストのデータ ストアに記録します。 `Trace` と `Information` を特定のカテゴリに制限することを検討してください。
  - `Warning` から `Critical` のレベルでログを記録しても、ログ メッセージはほとんど生成されません。
    - 通常、コストとストレージの制限は考慮されません。
    - ログの数が少ないほど、データ ストアをより柔軟に選択できるようになります。
- 開発中:
  - `Warning` を設定します。
  - トラブルシューティングの際に `Trace` または `Information` のメッセージを追加します。 出力を制限するには、調査中のカテゴリに対してのみ `Trace` または `Information` を設定します。

次の JSON は `Logging:Console:LogLevel:Microsoft:Information` を設定します。

:::code language="json" source="snippets/configuration/worker-service/appsettings.MSFT.json":::

## <a name="log-event-id"></a>ログ イベント ID

各ログでは、"*イベント識別子*" を指定できます。<xref:Microsoft.Extensions.Logging.EventId> は、`Id` および省略可能な `Name` 読み取り専用プロパティを持つ構造体です。 サンプル ソース コードでは、`AppLogEvents` クラスを使用してイベント ID を定義しています。

```csharp
internal static class AppLogEvents
{
    internal const int Create = 1000;
    internal const int Read = 1001;
    internal const int Update = 1002;
    internal const int Delete = 1003;

    internal const int Details = 3000;
    internal const int Error = 3001;

    internal const int ReadNotFound = 4000;
    internal const int UpdateNotFound = 4001;

    // ...
}
```

イベント ID によって一連のイベントが関連付けられます。 たとえば、リポジトリからの値の読み取りに関連するすべてのログを `1001` にすることができます。

ログ プロバイダーでは、ID フィールドやログ メッセージにイベント ID が記録されたり、またはまったく記録されなかったりする場合があります。 Debug プロバイダーでイベント ID が表示されることはありません。 Console プロバイダーでは、カテゴリの後のブラケット内にイベント ID が表示されます。

```console
info: Example.DefaultService.GetAsync[1001]
      Reading value for a1b2c3
warn: Example.DefaultService.GetAsync[4000]
      GetAsync(a1b2c3) not found
```

一部のログ プロバイダーでは、イベント ID がフィールドに格納されます。これにより、ID に対するフィルター処理が可能になります。

## <a name="log-message-template"></a>ログ メッセージ テンプレート

各ログ API では、メッセージ テンプレートが使用されます。 メッセージ テンプレートには、指定される引数のためのプレースホルダーを含めることができます。 プレースホルダーには、数値ではなく名前を使用します。 プレースホルダーの名前ではなく、プレースホルダーの順序によって、値の指定に使用されるパラメーターが決まります。 次のコードでは、パラメーター名がメッセージ テンプレート内のシーケンスの外にあります。

```csharp
string p1 = "param1";
string p2 = "param2";
_logger.LogInformation("Parameter values: {p2}, {p1}", p1, p2);
```

上記のコードでは、シーケンス内のパラメーター値を含むログ メッセージが作成されます。

```text
Parameter values: param1, param2
```

この方法により、ログ プロバイダーが [セマンティック ログまたは構造化ログ](https://github.com/NLog/NLog/wiki/How-to-use-structured-logging)を実装できるようになります。 書式設定されたメッセージ テンプレートだけでなく、引数自体がログ システムに渡されます。 これにより、ログ プロバイダーはフィールドとしてパラメーター値を格納することができます。 次のロガー メソッドについて考えてみます。

```csharp
_logger.LogInformation("Getting item {Id} at {RunTime}", id, DateTime.Now);
```

たとえば、Azure Table Storage にログを記録する場合:

- 各 Azure Table エンティティには、`ID` プロパティと `RunTime` プロパティを含めることができます。
- プロパティを持つテーブルによって、ログに記録されたデータに対するクエリが簡略化されます。 たとえば、クエリによって、特定の `RunTime` の範囲内のすべてのログを検索できます。テキスト メッセージから時間を解析する必要はありません。

## <a name="log-exceptions"></a>例外をログに記録する

ロガー メソッドには、例外パラメーターを受け取るオーバーロードがあります。

```csharp
public void Test(string id)
{
    try
    {
        if (id == "none")
        {
            throw new Exception("Default Id detected.");
        }
    }
    catch (Exception ex)
    {
        _logger.LogWarning(
            AppLogEvents.Error, ex,
            "Failed to process iteration: {Id}", id)
    }
}
```

例外ログはプロバイダー固有です。

### <a name="default-log-level"></a>既定のログ レベル

既定のログ レベルが設定されていない場合、既定のログ レベル値は `Information` になります。

たとえば、次のようなワーカー サービス アプリについて考えてみます。

- .NET Worker テンプレートを使用して作成された。
- *appsettings.json* と *appsettings.Development.json* が削除または名前が変更された。

上記の設定で、プライバシー ページまたはホーム ページに移動すると、カテゴリ名に `Microsoft` が含まれる多くの`Trace`、`Debug`、`Information` のメッセージが生成されます。

次のコードは、既定のログ レベルが構成で設定されていない場合に、既定のログ レベルを設定します。

```csharp
class Program
{
    static Task Main(string[] args) =>
        CreateHostBuilder(args).Build().RunAsync();

    static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureLogging(logging => logging.SetMinimumLevel(LogLevel.Warning));
}
```

### <a name="filter-function"></a>フィルター関数

フィルター関数は、構成またはコードによって規則が割り当てられていないすべてのプロバイダーとカテゴリに対して呼び出されます。

```csharp
class Program
{
    static Task Main(string[] args) =>
        CreateHostBuilder(args).Build().RunAsync();

    static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureLogging(logging =>
                logging.AddFilter((provider, category, logLevel) =>
                {
                    return provider.Contains("ConsoleLoggerProvider")
                        && (category.Contains("Example") || category.Contains("Microsoft"))
                        && logLevel >= LogLevel.Information;
                }));
}
```

上記のコードでは、カテゴリに `Example` または `Microsoft` が含まれ、ログ レベルが `Information` 以上の場合にコンソール ログが表示されます。

## <a name="log-scopes"></a>ログのスコープ

 "*スコープ*" では、論理操作のセットをグループ化できます。 このグループ化を使用して、セットの一部として作成される各ログに同じデータをアタッチすることができます。 たとえば、トランザクション処理の一部として作成されるすべてのログに、トランザクション ID を含めることができます。

スコープは:

- <xref:Microsoft.Extensions.Logging.ILogger.BeginScope%2A> メソッドによって返される <xref:System.IDisposable> 型です。
- 破棄されるまで継続します。

次のプロバイダーではスコープがサポートされています。

- `Console`
- [AzureAppServicesFile と AzureAppServicesBlob](xref:Microsoft.Extensions.Logging.AzureAppServices.BatchingLoggerOptions.IncludeScopes)

ロガーの呼び出しを `using` ブロックでラップすることによって、スコープを使用します。

```csharp
public async Task<T> GetAsync<T>(string id)
{
    T result;

    using (_logger.BeginScope("using block message"))
    {
        _logger.LogInformation(
            AppLogEvents.Read, "Reading value for {Id}", id);

        var result = await _repository.GetAsync(id);
        if (result is null)
        {
            _logger.LogWarning(
                AppLogEvents.ReadNotFound, "GetAsync({Id}) not found", id);
        }
    }

    return result;
}
```

次の JSON では、Console プロバイダーのスコープを有効にしています。

:::code language="json" source="snippets/configuration/worker-service/appsettings.IncludeScopes.json" highlight="9":::

次のコードでは、Console プロバイダーのスコープを有効にしています。

```csharp
class Program
{
    static Task Main(string[] args) =>
        CreateHostBuilder(args).Build().RunAsync();

    static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureLogging((_, logging) =>
                logging.ClearProviders()
                    .AddConsole(options => options.IncludeScopes = true));
}
```

## <a name="non-host-console-app"></a>ホスト コンソール以外のアプリ

[汎用ホスト](generic-host.md)を使用しないアプリのログ記録コードは、[プロバイダーの追加方法](logging-providers.md#built-in-logging-providers)と[ロガーの作成方法](#create-logs)が異なります。 ホスト コンソール以外のアプリでは、`LoggerFactory` を作成するときにプロバイダーの `Add{provider name}` 拡張メソッドを呼び出します。

```csharp
class Program
{
    static void Main(string[] args)
    {
        using var loggerFactory = LoggerFactory.Create(builder =>
        {
            builder
                .AddFilter("Microsoft", LogLevel.Warning)
                .AddFilter("System", LogLevel.Warning)
                .AddFilter("LoggingConsoleApp.Program", LogLevel.Debug)
                .AddConsole();
        });

        ILogger logger = loggerFactory.CreateLogger<Program>();
        logger.LogInformation("Example log message");
    }
}
```

`loggerFactory` オブジェクトは、<xref:Microsoft.Extensions.Logging.ILogger> インスタンスを作成するために使用されます。

## <a name="create-logs-in-main"></a>Main でログを作成する

次のコードでは、ホストを構築した後に DI から `ILogger` インスタンスを取得することによって `Main` でログを記録します。

```csharp
using System;
using System.Threading.Tasks;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Hosting;
using Microsoft.Extensions.Logging;

class Program
{
    static Task Main(string[] args)
    {
        IHost host = Host.CreateDefaultBuilder(args).Build();

        var logger = host.Services.GetRequiredService<ILogger<Program>>();
        logger.LogInformation("Host created.");

        return host.RunAsync();
    }
}
```

### <a name="no-asynchronous-logger-methods"></a>非同期でないロガー メソッド

ログ記録は高速に実行され、非同期コードのパフォーマンス コストを下回る必要があります。 ログ データ ストアが低速の場合は、そこへ直接書き込まないでください。 まずログ メッセージを高速なストアに書き込んでから、後で低速なストアに移動することを検討してください。 たとえば、SQL Server にログを記録する場合、`Log` メソッドは同期しているため、`Log` メソッドで直接それを行わないでください。 代わりに、ログ メッセージをインメモリ キューに同期的に追加し、バックグラウンド ワーカーにキューからメッセージをプルさせて、SQL Server にデータをプッシュする非同期処理を実行させます。

## <a name="change-log-levels-in-a-running-app"></a>実行中のアプリのログ レベルを変更する

ログ API には、アプリの実行中にログ レベルを変更するシナリオは含まれていません。 ただし、一部の構成プロバイダーは構成を再読み込みすることができ、ログ構成に直ちに影響します。 たとえば、[ファイル構成プロバイダー](configuration-providers.md#file-configuration-provider)では、既定でログ構成が再度読み込まれます。 アプリの実行中にコードの構成が変更された場合、アプリは [IConfigurationRoot.Reload](xref:Microsoft.Extensions.Configuration.IConfigurationRoot.Reload%2A) を呼び出して、アプリのログ構成を更新できます。

## <a name="nuget-packages"></a>NuGet パッケージ

<xref:Microsoft.Extensions.Logging.ILogger%601> と <xref:Microsoft.Extensions.Logging.ILoggerFactory> のインターフェイスと実装は .NET Core SDK に含まれています。 これらは、次の NuGet パッケージでも入手できます。

- インターフェイスは、[Microsoft.Extensions.Logging.Abstractions](https://www.nuget.org/packages/Microsoft.Extensions.Logging.Abstractions) にあります。
- 既定の実装は、[Microsoft.Extensions.Logging](https://www.nuget.org/packages/microsoft.extensions.logging) にあります。

## <a name="apply-log-filter-rules-in-code"></a>コードでログ フィルター規則を適用する

ログ フィルター規則を設定するには、[構成](configuration.md)を使用することをお勧めします。

コードにフィルター規則を登録する方法を次の例に示します。

```csharp
class Program
{
    static Task Main(string[] args) =>
        CreateHostBuilder(args).Build().RunAsync();

    static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureLogging(logging =>
               logging.AddFilter("System", LogLevel.Debug)
                  .AddFilter<DebugLoggerProvider>("Microsoft", LogLevel.Information)
                  .AddFilter<ConsoleLoggerProvider>("Microsoft", LogLevel.Trace));
}
```

`logging.AddFilter("System", LogLevel.Debug)` は `System` カテゴリとログ レベル `Debug` を指定します。 特定のプロバイダーが構成されていないため、フィルターはすべてのプロバイダーに適用されます。

`AddFilter<DebugLoggerProvider>("Microsoft", LogLevel.Information)` は以下を指定します。

- `Debug` ログ プロバイダー。
- ログ レベル `Information` 以上。
- `"Microsoft"` で始まるすべてのカテゴリ。

## <a name="see-also"></a>関連項目

- [.NET でのログ プロバイダー](logging-providers.md)
- [.NET にカスタム ログ プロバイダーを実装する](custom-logging-provider.md)
- [コンソール ログの書式設定](console-log-formatter.md)
- [.NET での高パフォーマンスのログ](high-performance-logging.md)
- ログに関するバグは [github.com/dotnet/extensions](https://github.com/dotnet/extensions/issues) リポジトリに作成する必要があります
