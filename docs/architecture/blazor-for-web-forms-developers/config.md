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
# <a name="app-configuration"></a><span data-ttu-id="626f4-103">アプリの構成</span><span class="sxs-lookup"><span data-stu-id="626f4-103">App configuration</span></span>

<span data-ttu-id="626f4-104">Web Forms にアプリ構成を読み込む主な方法は、*web.config* ファイルのエントリ (サーバー上または *web.config* によって参照される関連する構成ファイル) を使用することです。静的な `ConfigurationManager` オブジェクトを使用して、アプリの設定、データ リポジトリ接続文字列、およびアプリに追加されるその他の拡張構成プロバイダーとやり取りすることができます。</span><span class="sxs-lookup"><span data-stu-id="626f4-104">The primary way to load app configuration in Web Forms is with entries in the *web.config* file&mdash;either on the server or a related configuration file referenced by *web.config*. You can use the static `ConfigurationManager` object to interact with app settings, data repository connection strings, and other extended configuration providers that are added into the app.</span></span> <span data-ttu-id="626f4-105">一般的に、アプリ構成との対話は次のコードのようになります。</span><span class="sxs-lookup"><span data-stu-id="626f4-105">It's typical to see interactions with app configuration as seen in the following code:</span></span>

```csharp
var configurationValue = ConfigurationManager.AppSettings["ConfigurationSettingName"];
var connectionString = ConfigurationManager.ConnectionStrings["MyDatabaseConnectionName"].ConnectionString;
```

<span data-ttu-id="626f4-106">ASP.NET Core およびサーバー側の Blazor では、アプリが Windows IIS サーバーでホストされている場合、*web.config* ファイルが存在する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="626f4-106">With ASP.NET Core and server-side Blazor, the *web.config* file MAY be present if your app is hosted on a Windows IIS server.</span></span> <span data-ttu-id="626f4-107">ただし、この構成には `ConfigurationManager` の対話は存在せず、他の構造化されたアプリ構成を他のソースから受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="626f4-107">However, there's no `ConfigurationManager` interaction with this configuration, and you can receive more structured app configuration from other sources.</span></span> <span data-ttu-id="626f4-108">構成の収集方法と、*web.config* ファイルから構成情報にアクセスできる方法を見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="626f4-108">Let's take a look at how configuration is gathered and how you can still access configuration information from a *web.config* file.</span></span>

## <a name="configuration-sources"></a><span data-ttu-id="626f4-109">構成元</span><span class="sxs-lookup"><span data-stu-id="626f4-109">Configuration sources</span></span>

<span data-ttu-id="626f4-110">ASP.NET Core では、アプリに使用できる多くの構成ソースがあることを認識しています。</span><span class="sxs-lookup"><span data-stu-id="626f4-110">ASP.NET Core recognizes there are many configuration sources you may want to use for your app.</span></span> <span data-ttu-id="626f4-111">このフレームワークでは、既定でこれらの機能のうち最適なものをユーザーに提供しようとします。</span><span class="sxs-lookup"><span data-stu-id="626f4-111">The framework attempts to offer you the best of these features by default.</span></span> <span data-ttu-id="626f4-112">ASP.NET Core によって、これらのさまざまなソースから構成を読み取り集計します。</span><span class="sxs-lookup"><span data-stu-id="626f4-112">Configuration is read and aggregated from these various sources by ASP.NET Core.</span></span> <span data-ttu-id="626f4-113">同じ構成キーについて後から読み込まれる値が、以前の値よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="626f4-113">Later loaded values for the same configuration key take precedence over earlier values.</span></span>

<span data-ttu-id="626f4-114">ASP.NET Core は、クラウドに対応し、オペレーターと開発者の両方にとってアプリの構成が容易になるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="626f4-114">ASP.NET Core was designed to be cloud-aware and to make the configuration of apps easier for both operators and developers.</span></span> <span data-ttu-id="626f4-115">ASP.NET Core は環境を認識し、`Production` または `Development` のどちらの環境で実行されているか認識します。</span><span class="sxs-lookup"><span data-stu-id="626f4-115">ASP.NET Core is environment-aware and knows if it's running in your `Production` or `Development` environment.</span></span> <span data-ttu-id="626f4-116">環境インジケーターは、`ASPNETCORE_ENVIRONMENT` システム環境変数で設定されます。</span><span class="sxs-lookup"><span data-stu-id="626f4-116">The environment indicator is set in the `ASPNETCORE_ENVIRONMENT` system environment variable.</span></span> <span data-ttu-id="626f4-117">値が構成されていない場合、アプリは既定で `Production` 環境で実行されます。</span><span class="sxs-lookup"><span data-stu-id="626f4-117">If no value is configured, the app defaults to running in the `Production` environment.</span></span>

<span data-ttu-id="626f4-118">アプリは環境の名前に基づいて、複数のソースから構成をトリガーおよび追加できます。</span><span class="sxs-lookup"><span data-stu-id="626f4-118">Your app can trigger and add configuration from several sources based on the environment's name.</span></span> <span data-ttu-id="626f4-119">既定では、構成は次のリソースから記載されている順に読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="626f4-119">By default, the configuration is loaded from the following resources in the order listed:</span></span>

1. <span data-ttu-id="626f4-120">*appsettings.json* ファイル (存在する場合)</span><span class="sxs-lookup"><span data-stu-id="626f4-120">*appsettings.json* file, if present</span></span>
1. <span data-ttu-id="626f4-121">*appsettings.{ENVIRONMENT_NAME}.json* ファイル (存在する場合)</span><span class="sxs-lookup"><span data-stu-id="626f4-121">*appsettings.{ENVIRONMENT_NAME}.json* file, if present</span></span>
1. <span data-ttu-id="626f4-122">ディスク上のユーザー シークレット ファイル (存在する場合)</span><span class="sxs-lookup"><span data-stu-id="626f4-122">User secrets file on disk, if present</span></span>
1. <span data-ttu-id="626f4-123">環境変数</span><span class="sxs-lookup"><span data-stu-id="626f4-123">Environment variables</span></span>
1. <span data-ttu-id="626f4-124">コマンド ライン引数</span><span class="sxs-lookup"><span data-stu-id="626f4-124">Command-line arguments</span></span>

## <a name="appsettingsjson-format-and-access"></a><span data-ttu-id="626f4-125">appsettings.json 形式とアクセス</span><span class="sxs-lookup"><span data-stu-id="626f4-125">appsettings.json format and access</span></span>

<span data-ttu-id="626f4-126">*appsettings.json* ファイルは、次の JSON のように構造化された値を使用して階層化できます。</span><span class="sxs-lookup"><span data-stu-id="626f4-126">The *appsettings.json* file can be hierarchical with values structured like the following JSON:</span></span>

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

<span data-ttu-id="626f4-127">上記の JSON が提供された場合、構成システムでは子の値がフラット化され、完全修飾された階層パスが参照されます。</span><span class="sxs-lookup"><span data-stu-id="626f4-127">When presented with the preceding JSON, the configuration system flattens child values and references their fully qualified hierarchical paths.</span></span> <span data-ttu-id="626f4-128">階層内の各プロパティは、コロン (`:`) 文字で区切られます。</span><span class="sxs-lookup"><span data-stu-id="626f4-128">A colon (`:`) character separates each property in the hierarchy.</span></span> <span data-ttu-id="626f4-129">たとえば、構成キー `section1:key0` は、`section1` オブジェクト リテラルの `key0` 値にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="626f4-129">For example, the configuration key `section1:key0` accesses the `section1` object literal's `key0` value.</span></span>

## <a name="user-secrets"></a><span data-ttu-id="626f4-130">ユーザー シークレット</span><span class="sxs-lookup"><span data-stu-id="626f4-130">User secrets</span></span>

<span data-ttu-id="626f4-131">ユーザー シークレットは、次のようなものです。</span><span class="sxs-lookup"><span data-stu-id="626f4-131">User secrets are:</span></span>

* <span data-ttu-id="626f4-132">アプリ開発フォルダーの外部にある、開発者のワークステーション上の JSON ファイルに格納されている構成値。</span><span class="sxs-lookup"><span data-stu-id="626f4-132">Configuration values that are stored in a JSON file on the developer's workstation, outside of the app development folder.</span></span>
* <span data-ttu-id="626f4-133">`Development` 環境での実行時にのみ読み込まれる。</span><span class="sxs-lookup"><span data-stu-id="626f4-133">Only loaded when running in the `Development` environment.</span></span>
* <span data-ttu-id="626f4-134">特定のアプリに関連付けられる。</span><span class="sxs-lookup"><span data-stu-id="626f4-134">Associated with a specific app.</span></span>
* <span data-ttu-id="626f4-135">.NET CLI の `user-secrets` コマンドを使用して管理される。</span><span class="sxs-lookup"><span data-stu-id="626f4-135">Managed with the .NET CLI's `user-secrets` command.</span></span>

<span data-ttu-id="626f4-136">`user-secrets` コマンドを実行して、シークレット ストレージ用にアプリを構成します。</span><span class="sxs-lookup"><span data-stu-id="626f4-136">Configure your app for secrets storage by executing the `user-secrets` command:</span></span>

```dotnetcli
dotnet user-secrets init
```

<span data-ttu-id="626f4-137">上記のコマンドによって `UserSecretsId` 要素がプロジェクト ファイルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="626f4-137">The preceding command adds a `UserSecretsId` element to the project file.</span></span> <span data-ttu-id="626f4-138">要素には GUID が含まれており、これを使用してシークレットをアプリに関連付けます。</span><span class="sxs-lookup"><span data-stu-id="626f4-138">The element contains a GUID, which is used to associate secrets with the app.</span></span> <span data-ttu-id="626f4-139">その後、`set` コマンドを使用してシークレットを定義できます。</span><span class="sxs-lookup"><span data-stu-id="626f4-139">You can then define a secret with the `set` command.</span></span> <span data-ttu-id="626f4-140">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="626f4-140">For example:</span></span>

```dotnetcli
dotnet user-secrets set "Parent:ApiKey" "12345"
```

<span data-ttu-id="626f4-141">上記のコマンドによって、開発者のワークステーションで値 `12345` の `Parent:ApiKey` 構成キーが使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="626f4-141">The preceding command makes the `Parent:ApiKey` configuration key available on a developer's workstation with the value `12345`.</span></span>

<span data-ttu-id="626f4-142">ユーザー シークレットの作成、格納、および管理の詳細については、「[ASP.NET Core の開発におけるアプリ シークレットの安全な格納](/aspnet/core/security/app-secrets)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="626f4-142">For more information about creating, storing, and managing user secrets, see the [Safe storage of app secrets in development in ASP.NET Core](/aspnet/core/security/app-secrets) document.</span></span>

## <a name="environment-variables"></a><span data-ttu-id="626f4-143">環境変数</span><span class="sxs-lookup"><span data-stu-id="626f4-143">Environment variables</span></span>

<span data-ttu-id="626f4-144">アプリケーション構成に読み込まれる次の値のセットは、システムの環境変数です。</span><span class="sxs-lookup"><span data-stu-id="626f4-144">The next set of values loaded into your app configuration is the system's environment variables.</span></span> <span data-ttu-id="626f4-145">システムの環境変数のすべての設定は、構成 API を使用してアクセスできるようになりました。</span><span class="sxs-lookup"><span data-stu-id="626f4-145">All of your system's environment variable settings are now accessible to you through the configuration API.</span></span> <span data-ttu-id="626f4-146">アプリ内で読み取られるときに、階層値はフラット化され、コロン文字で区切られます。</span><span class="sxs-lookup"><span data-stu-id="626f4-146">Hierarchical values are flattened and separated by colon characters when read inside your app.</span></span> <span data-ttu-id="626f4-147">ただし、一部のオペレーティング システムではコロン文字の環境変数名を使用できません。</span><span class="sxs-lookup"><span data-stu-id="626f4-147">However, some operating systems don't allow the colon character environment variable names.</span></span> <span data-ttu-id="626f4-148">ASP.NET Core では、2 つのアンダースコア (`__`) を持つ値をアクセス時にコロンに変換することによって、この制限に対処 します。</span><span class="sxs-lookup"><span data-stu-id="626f4-148">ASP.NET Core addresses this limitation by converting values that have double-underscores (`__`) into a colon when they're accessed.</span></span> <span data-ttu-id="626f4-149">上記のユーザー シークレット セクションの `Parent:ApiKey` 値は、環境変数 `Parent__ApiKey` でオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="626f4-149">The `Parent:ApiKey` value from the user secrets section above can be overridden with the environment variable `Parent__ApiKey`.</span></span>

## <a name="command-line-arguments"></a><span data-ttu-id="626f4-150">コマンド ライン引数</span><span class="sxs-lookup"><span data-stu-id="626f4-150">Command-line arguments</span></span>

<span data-ttu-id="626f4-151">構成は、アプリを起動するときにコマンドライン引数として指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="626f4-151">Configuration can also be provided as command-line arguments when your app is started.</span></span> <span data-ttu-id="626f4-152">設定する構成値の名前と構成する値を示すには、二重ダッシュ (`--`) またはスラッシュ (`/`) 表記を使用します。</span><span class="sxs-lookup"><span data-stu-id="626f4-152">Use the double-dash (`--`) or forward-slash (`/`) notation to indicate the name of the configuration value to set and the value to be configured.</span></span> <span data-ttu-id="626f4-153">構文は次のコマンドのようになります。</span><span class="sxs-lookup"><span data-stu-id="626f4-153">The syntax resembles the following commands:</span></span>

```dotnetcli
dotnet run CommandLineKey1=value1 --CommandLineKey2=value2 /CommandLineKey3=value3
dotnet run --CommandLineKey1 value1 /CommandLineKey2 value2
dotnet run Parent:ApiKey=67890
```

## <a name="the-return-of-webconfig"></a><span data-ttu-id="626f4-154">web.config のリターン</span><span class="sxs-lookup"><span data-stu-id="626f4-154">The return of web.config</span></span>

<span data-ttu-id="626f4-155">アプリを IIS の Windows にデプロイした場合、*web.config* ファイルでは引き続き、アプリを管理するよう IIS が構成されます。</span><span class="sxs-lookup"><span data-stu-id="626f4-155">If you've deployed your app to Windows on IIS, the *web.config* file still configures IIS to manage your app.</span></span> <span data-ttu-id="626f4-156">既定では、IIS では ASP.NET Core モジュール (ANCM) への参照が追加されます。</span><span class="sxs-lookup"><span data-stu-id="626f4-156">By default, IIS adds a reference to the ASP.NET Core Module (ANCM).</span></span> <span data-ttu-id="626f4-157">ANCM は、Kestrel web サーバーの代わりにアプリをホストするネイティブ IIS モジュールです。</span><span class="sxs-lookup"><span data-stu-id="626f4-157">ANCM is a native IIS module that hosts your app in place of the Kestrel web server.</span></span> <span data-ttu-id="626f4-158">この *web.config* セクションは、次の XML マークアップのようになります。</span><span class="sxs-lookup"><span data-stu-id="626f4-158">This *web.config* section resembles the following XML markup:</span></span>

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

<span data-ttu-id="626f4-159">アプリ固有の構成は、`aspNetCore` 要素内に `environmentVariables` 要素を入れ子にすることによって定義できます。</span><span class="sxs-lookup"><span data-stu-id="626f4-159">App-specific configuration can be defined by nesting an `environmentVariables` element in the `aspNetCore` element.</span></span> <span data-ttu-id="626f4-160">このセクションで定義されている値は、環境変数として ASP.NET Core アプリに提示されます。</span><span class="sxs-lookup"><span data-stu-id="626f4-160">The values defined in this section are presented to the ASP.NET Core app as environment variables.</span></span> <span data-ttu-id="626f4-161">この環境変数は、アプリの起動のそのセグメント中に適切に読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="626f4-161">The environment variables load appropriately during that segment of app startup.</span></span>

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

## <a name="read-configuration-in-the-app"></a><span data-ttu-id="626f4-162">アプリ内の構成を読み取る</span><span class="sxs-lookup"><span data-stu-id="626f4-162">Read configuration in the app</span></span>

<span data-ttu-id="626f4-163">ASP.NET Core では <xref:Microsoft.Extensions.Configuration.IConfiguration> インターフェイスを通じてアプリ構成が提供されます。</span><span class="sxs-lookup"><span data-stu-id="626f4-163">ASP.NET Core provides app configuration through the <xref:Microsoft.Extensions.Configuration.IConfiguration> interface.</span></span> <span data-ttu-id="626f4-164">この構成インターフェイスは、Blazor コンポーネント、Blazor ページ、および構成へのアクセスを必要とするその他の ASP.NET Core マネージド クラスによって要求される必要があります。</span><span class="sxs-lookup"><span data-stu-id="626f4-164">This configuration interface should be requested by your Blazor components, Blazor pages, and any other ASP.NET Core-managed class that needs access to configuration.</span></span> <span data-ttu-id="626f4-165">ASP.NET Core フレームワークでは、以前構成した解決済みの構成がこのインターフェイスに自動的に設定されます。</span><span class="sxs-lookup"><span data-stu-id="626f4-165">The ASP.NET Core framework will automatically populate this interface with the resolved configuration configured earlier.</span></span> <span data-ttu-id="626f4-166">Blazor ページまたはコンポーネントの Razor マークアップでは、次のように *.razor* ファイルの先頭に `@inject` ディレクティブを使用して `IConfiguration` オブジェクトを挿入できます。</span><span class="sxs-lookup"><span data-stu-id="626f4-166">On a Blazor page or a component's Razor markup, you can inject the `IConfiguration` object with an `@inject` directive at the top of the *.razor* file like this:</span></span>

```razor
@inject IConfiguration Configuration
```

<span data-ttu-id="626f4-167">この前のステートメントにより、`IConfiguration` オブジェクトは Razor テンプレートの残りの部分を通じて `Configuration` 変数として使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="626f4-167">This preceding statement makes the `IConfiguration` object available as the `Configuration` variable throughout the rest of the Razor template.</span></span>

<span data-ttu-id="626f4-168">個々の構成設定は、インデクサー パラメーターとして検索される構成設定の階層を指定することで、読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="626f4-168">Individual configuration settings can be read by specifying the configuration setting hierarchy sought as an indexer parameter:</span></span>

```csharp
var mySetting = Configuration["section1:key0"];
```

<span data-ttu-id="626f4-169">前の例の section1 の構成を取得する `GetSection("section1")` と同様の構文で、特定の場所のキーのコレクションを取得する <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> メソッドを使用して、構成セクション全体を取得できます。</span><span class="sxs-lookup"><span data-stu-id="626f4-169">You can fetch entire configuration sections by using the <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> method to retrieve a collection of keys at a specific location with a syntax similar to `GetSection("section1")` to retrieve the configuration for section1 from the earlier example.</span></span>

## <a name="strongly-typed-configuration"></a><span data-ttu-id="626f4-170">厳密に型指定された構成</span><span class="sxs-lookup"><span data-stu-id="626f4-170">Strongly typed configuration</span></span>

<span data-ttu-id="626f4-171">Web Forms では、<xref:System.Configuration.ConfigurationSection> 型とそれに関連付けられている型から継承される、厳密に型指定された構成の型を作成できました。</span><span class="sxs-lookup"><span data-stu-id="626f4-171">With Web Forms, it was possible to create a strongly typed configuration type that inherited from the <xref:System.Configuration.ConfigurationSection> type and associated types.</span></span> <span data-ttu-id="626f4-172">`ConfigurationSection` では、これらの構成値に対していくつかのビジネス ルールと処理を構成できます。</span><span class="sxs-lookup"><span data-stu-id="626f4-172">A `ConfigurationSection` allowed you to configure some business rules and processing for those configuration values.</span></span>

<span data-ttu-id="626f4-173">ASP.NET Core では、構成値を受け取るクラス階層を指定できます。</span><span class="sxs-lookup"><span data-stu-id="626f4-173">In ASP.NET Core, you can specify a class hierarchy that will receive the configuration values.</span></span> <span data-ttu-id="626f4-174">これらのクラスは次のようなものです。</span><span class="sxs-lookup"><span data-stu-id="626f4-174">These classes:</span></span>

* <span data-ttu-id="626f4-175">親クラスから継承する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="626f4-175">Don't need to inherit from a parent class.</span></span>
* <span data-ttu-id="626f4-176">キャプチャする構成構造のプロパティおよび型参照に一致する `public` プロパティが含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="626f4-176">Should include `public` properties that match the properties and type references for the configuration structure you wish to capture.</span></span>

<span data-ttu-id="626f4-177">以前の *appsettings.js* サンプルでは、次のクラスを定義して値をキャプチャできます。</span><span class="sxs-lookup"><span data-stu-id="626f4-177">For the earlier *appsettings.json* sample, you could define the following classes to capture the values:</span></span>

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

<span data-ttu-id="626f4-178">このクラス階層は、`Startup.ConfigureServices` メソッドに次の行を追加することによって設定できます。</span><span class="sxs-lookup"><span data-stu-id="626f4-178">This class hierarchy can be populated by adding the following line to the `Startup.ConfigureServices` method:</span></span>

```csharp
services.Configure<MyConfig>(Configuration);
```

<span data-ttu-id="626f4-179">アプリの残りの部分では、厳密に型指定された構成設定を受け取るために、クラスに入力パラメーターを追加したり、型 `IOptions<MyConfig>` の Razor テンプレート内に `@inject` ディレクティブを追加したりできます。</span><span class="sxs-lookup"><span data-stu-id="626f4-179">In the rest of the app, you can add an input parameter to classes or an `@inject` directive in Razor templates of type `IOptions<MyConfig>` to receive the strongly typed configuration settings.</span></span> <span data-ttu-id="626f4-180">`IOptions<MyConfig>.Value` プロパティは、構成設定から設定された `MyConfig` 値を生成します。</span><span class="sxs-lookup"><span data-stu-id="626f4-180">The `IOptions<MyConfig>.Value` property will yield the `MyConfig` value populated from the configuration settings.</span></span>

```razor
@inject IOptions<MyConfig> options
@code {
    var MyConfiguration = options.Value;
    var theSetting = MyConfiguration.section1.key0;
}
```

<span data-ttu-id="626f4-181">Options 機能の詳細については、[ASP.NET Core のオプション パターン](/aspnet/core/fundamentals/configuration/options#options-interfaces)のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="626f4-181">More information about the Options feature can be found in the [Options pattern in ASP.NET Core](/aspnet/core/fundamentals/configuration/options#options-interfaces) document.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="626f4-182">[前へ](middleware.md)
>[次へ](security-authentication-authorization.md)</span><span class="sxs-lookup"><span data-stu-id="626f4-182">[Previous](middleware.md)
[Next](security-authentication-authorization.md)</span></span>
