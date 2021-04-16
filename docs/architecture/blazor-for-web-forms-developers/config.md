---
title: アプリの構成
description: ConfigurationManager を使用せずに Blazor アプリを構成する方法について説明します。
author: csharpfritz
ms.author: jefritz
no-loc:
- Blazor
ms.date: 11/20/2020
ms.openlocfilehash: 360d9077bc981a2e9875bb1f86b49c0029424d6e
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "96509794"
---
# <a name="app-configuration"></a>アプリの構成

Web Forms にアプリ構成を読み込む主な方法は、*web.config* ファイルのエントリ (サーバー上または *web.config* によって参照される関連する構成ファイル) を使用することです。静的な `ConfigurationManager` オブジェクトを使用して、アプリの設定、データ リポジトリ接続文字列、およびアプリに追加されるその他の拡張構成プロバイダーとやり取りすることができます。 一般的に、アプリ構成との対話は次のコードのようになります。

```csharp
var configurationValue = ConfigurationManager.AppSettings["ConfigurationSettingName"];
var connectionString = ConfigurationManager.ConnectionStrings["MyDatabaseConnectionName"].ConnectionString;
```

ASP.NET Core およびサーバー側の Blazor では、アプリが Windows IIS サーバーでホストされている場合、*web.config* ファイルが存在する可能性があります。 ただし、この構成には `ConfigurationManager` の対話は存在せず、他の構造化されたアプリ構成を他のソースから受け取ることができます。 構成の収集方法と、*web.config* ファイルから構成情報にアクセスできる方法を見てみましょう。

## <a name="configuration-sources"></a>構成元

ASP.NET Core では、アプリに使用できる多くの構成ソースがあることを認識しています。 このフレームワークでは、既定でこれらの機能のうち最適なものをユーザーに提供しようとします。 ASP.NET Core によって、これらのさまざまなソースから構成を読み取り集計します。 同じ構成キーについて後から読み込まれる値が、以前の値よりも優先されます。

ASP.NET Core は、クラウドに対応し、オペレーターと開発者の両方にとってアプリの構成が容易になるように設計されています。 ASP.NET Core は環境を認識し、`Production` または `Development` のどちらの環境で実行されているか認識します。 環境インジケーターは、`ASPNETCORE_ENVIRONMENT` システム環境変数で設定されます。 値が構成されていない場合、アプリは既定で `Production` 環境で実行されます。

アプリは環境の名前に基づいて、複数のソースから構成をトリガーおよび追加できます。 既定では、構成は次のリソースから記載されている順に読み込まれます。

1. *appsettings.json* ファイル (存在する場合)
1. *appsettings.{ENVIRONMENT_NAME}.json* ファイル (存在する場合)
1. ディスク上のユーザー シークレット ファイル (存在する場合)
1. 環境変数
1. コマンド ライン引数

## <a name="appsettingsjson-format-and-access"></a>appsettings.json 形式とアクセス

*appsettings.json* ファイルは、次の JSON のように構造化された値を使用して階層化できます。

```json
{
  "section0": {
    "key0": "value",
    "key1": "value"
  },
  "section1": {
    "key0": "value",
    "key1": "value"
  }
}
```

上記の JSON が提供された場合、構成システムでは子の値がフラット化され、完全修飾された階層パスが参照されます。 階層内の各プロパティは、コロン (`:`) 文字で区切られます。 たとえば、構成キー `section1:key0` は、`section1` オブジェクト リテラルの `key0` 値にアクセスします。

## <a name="user-secrets"></a>ユーザー シークレット

ユーザー シークレットは、次のようなものです。

* アプリ開発フォルダーの外部にある、開発者のワークステーション上の JSON ファイルに格納されている構成値。
* `Development` 環境での実行時にのみ読み込まれる。
* 特定のアプリに関連付けられる。
* .NET CLI の `user-secrets` コマンドを使用して管理される。

`user-secrets` コマンドを実行して、シークレット ストレージ用にアプリを構成します。

```dotnetcli
dotnet user-secrets init
```

上記のコマンドによって `UserSecretsId` 要素がプロジェクト ファイルに追加されます。 要素には GUID が含まれており、これを使用してシークレットをアプリに関連付けます。 その後、`set` コマンドを使用してシークレットを定義できます。 次に例を示します。

```dotnetcli
dotnet user-secrets set "Parent:ApiKey" "12345"
```

上記のコマンドによって、開発者のワークステーションで値 `12345` の `Parent:ApiKey` 構成キーが使用できるようになります。

ユーザー シークレットの作成、格納、および管理の詳細については、「[ASP.NET Core の開発におけるアプリ シークレットの安全な格納](/aspnet/core/security/app-secrets)」を参照してください。

## <a name="environment-variables"></a>環境変数

アプリケーション構成に読み込まれる次の値のセットは、システムの環境変数です。 システムの環境変数のすべての設定は、構成 API を使用してアクセスできるようになりました。 アプリ内で読み取られるときに、階層値はフラット化され、コロン文字で区切られます。 ただし、一部のオペレーティング システムではコロン文字の環境変数名を使用できません。 ASP.NET Core では、2 つのアンダースコア (`__`) を持つ値をアクセス時にコロンに変換することによって、この制限に対処 します。 上記のユーザー シークレット セクションの `Parent:ApiKey` 値は、環境変数 `Parent__ApiKey` でオーバーライドできます。

## <a name="command-line-arguments"></a>コマンド ライン引数

構成は、アプリを起動するときにコマンドライン引数として指定することもできます。 設定する構成値の名前と構成する値を示すには、二重ダッシュ (`--`) またはスラッシュ (`/`) 表記を使用します。 構文は次のコマンドのようになります。

```dotnetcli
dotnet run CommandLineKey1=value1 --CommandLineKey2=value2 /CommandLineKey3=value3
dotnet run --CommandLineKey1 value1 /CommandLineKey2 value2
dotnet run Parent:ApiKey=67890
```

## <a name="the-return-of-webconfig"></a>web.config のリターン

アプリを IIS の Windows にデプロイした場合、*web.config* ファイルでは引き続き、アプリを管理するよう IIS が構成されます。 既定では、IIS では ASP.NET Core モジュール (ANCM) への参照が追加されます。 ANCM は、Kestrel web サーバーの代わりにアプリをホストするネイティブ IIS モジュールです。 この *web.config* セクションは、次の XML マークアップのようになります。

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <location path="." inheritInChildApplications="false">
    <system.webServer>
      <handlers>
        <add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModuleV2" resourceType="Unspecified" />
      </handlers>
      <aspNetCore processPath=".\MyApp.exe"
                  stdoutLogEnabled="false"
                  stdoutLogFile=".\logs\stdout"
                  hostingModel="inprocess" />
    </system.webServer>
  </location>
</configuration>
```

アプリ固有の構成は、`aspNetCore` 要素内に `environmentVariables` 要素を入れ子にすることによって定義できます。 このセクションで定義されている値は、環境変数として ASP.NET Core アプリに提示されます。 この環境変数は、アプリの起動のそのセグメント中に適切に読み込まれます。

```xml
<aspNetCore processPath="dotnet"
      arguments=".\MyApp.dll"
      stdoutLogEnabled="false"
      stdoutLogFile=".\logs\stdout"
      hostingModel="inprocess">
  <environmentVariables>
    <environmentVariable name="ASPNETCORE_ENVIRONMENT" value="Development" />
    <environmentVariable name="Parent:ApiKey" value="67890" />
  </environmentVariables>
</aspNetCore>
```

## <a name="read-configuration-in-the-app"></a>アプリ内の構成を読み取る

ASP.NET Core では <xref:Microsoft.Extensions.Configuration.IConfiguration> インターフェイスを通じてアプリ構成が提供されます。 この構成インターフェイスは、Blazor コンポーネント、Blazor ページ、および構成へのアクセスを必要とするその他の ASP.NET Core マネージド クラスによって要求される必要があります。 ASP.NET Core フレームワークでは、以前構成した解決済みの構成がこのインターフェイスに自動的に設定されます。 Blazor ページまたはコンポーネントの Razor マークアップでは、次のように *.razor* ファイルの先頭に `@inject` ディレクティブを使用して `IConfiguration` オブジェクトを挿入できます。

```razor
@inject IConfiguration Configuration
```

この前のステートメントにより、`IConfiguration` オブジェクトは Razor テンプレートの残りの部分を通じて `Configuration` 変数として使用できるようになります。

個々の構成設定は、インデクサー パラメーターとして検索される構成設定の階層を指定することで、読み取ることができます。

```csharp
var mySetting = Configuration["section1:key0"];
```

前の例の section1 の構成を取得する `GetSection("section1")` と同様の構文で、特定の場所のキーのコレクションを取得する <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> メソッドを使用して、構成セクション全体を取得できます。

## <a name="strongly-typed-configuration"></a>厳密に型指定された構成

Web Forms では、<xref:System.Configuration.ConfigurationSection> 型とそれに関連付けられている型から継承される、厳密に型指定された構成の型を作成できました。 `ConfigurationSection` では、これらの構成値に対していくつかのビジネス ルールと処理を構成できます。

ASP.NET Core では、構成値を受け取るクラス階層を指定できます。 これらのクラスは次のようなものです。

* 親クラスから継承する必要はありません。
* キャプチャする構成構造のプロパティおよび型参照に一致する `public` プロパティが含まれている必要があります。

以前の *appsettings.js* サンプルでは、次のクラスを定義して値をキャプチャできます。

```csharp
public class MyConfig
{
    public MyConfigSection section0 { get; set;}

    public MyConfigSection section1 { get; set;}
}

public class MyConfigSection
{
    public string key0 { get; set; }

    public string key1 { get; set; }
}
```

このクラス階層は、`Startup.ConfigureServices` メソッドに次の行を追加することによって設定できます。

```csharp
services.Configure<MyConfig>(Configuration);
```

アプリの残りの部分では、厳密に型指定された構成設定を受け取るために、クラスに入力パラメーターを追加したり、型 `IOptions<MyConfig>` の Razor テンプレート内に `@inject` ディレクティブを追加したりできます。 `IOptions<MyConfig>.Value` プロパティは、構成設定から設定された `MyConfig` 値を生成します。

```razor
@inject IOptions<MyConfig> options
@code {
    var MyConfiguration = options.Value;
    var theSetting = MyConfiguration.section1.key0;
}
```

Options 機能の詳細については、[ASP.NET Core のオプション パターン](/aspnet/core/fundamentals/configuration/options#options-interfaces)のドキュメントを参照してください。

>[!div class="step-by-step"]
>[前へ](middleware.md)
>[次へ](security-authentication-authorization.md)
