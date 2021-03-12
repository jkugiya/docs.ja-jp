---
title: Dapr シークレットの構成ブロック
description: シークレットの構成ブロックの説明、その機能、利点、適用方法
author: edwinvw
ms.date: 02/07/2021
ms.openlocfilehash: 94942b396af947b2a3e49b918b2b082c15f4bb08
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401438"
---
# <a name="the-dapr-secrets-building-block"></a><span data-ttu-id="048ef-103">Dapr シークレットの構成ブロック</span><span class="sxs-lookup"><span data-stu-id="048ef-103">The Dapr secrets building block</span></span>

<span data-ttu-id="048ef-104">エンタープライズアプリケーションにはシークレットが必要です。</span><span class="sxs-lookup"><span data-stu-id="048ef-104">Enterprise applications require secrets.</span></span> <span data-ttu-id="048ef-105">たとえば、次のような場合です。</span><span class="sxs-lookup"><span data-stu-id="048ef-105">Common examples include:</span></span>

- <span data-ttu-id="048ef-106">ユーザー名とパスワードを含むデータベース接続文字列。</span><span class="sxs-lookup"><span data-stu-id="048ef-106">A database connection string that contains a username and password.</span></span>
- <span data-ttu-id="048ef-107">外部 web API を呼び出すための API キー。</span><span class="sxs-lookup"><span data-stu-id="048ef-107">An API key for calling an external web API.</span></span>
- <span data-ttu-id="048ef-108">外部システムに対して認証を行うためのクライアント証明書。</span><span class="sxs-lookup"><span data-stu-id="048ef-108">A client certificate for authenticating to an external system.</span></span>

<span data-ttu-id="048ef-109">シークレットは、アプリケーションの外部に公開されないように、慎重に管理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="048ef-109">Secrets must be carefully managed so that they're never disclosed outside of the application.</span></span>

<span data-ttu-id="048ef-110">アプリケーションのシークレットは、アプリケーションコードベース内の構成ファイルに保存するのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="048ef-110">Not long ago, it was popular to store application secrets in a configuration file inside the application codebase.</span></span> <span data-ttu-id="048ef-111">.NET 開発者は、 *web.config* ファイルを fondly に再呼び出します。</span><span class="sxs-lookup"><span data-stu-id="048ef-111">.NET developers will fondly recall the *web.config* file.</span></span> <span data-ttu-id="048ef-112">実装するのは簡単ですが、シークレットとコードを統合することは安全ではありませんでした。</span><span class="sxs-lookup"><span data-stu-id="048ef-112">While simple to implement, integrating secrets to along with code was far from secure.</span></span> <span data-ttu-id="048ef-113">一般的な誤った手順は、パブリック GIT リポジトリにプッシュするときにファイルを含めて、世界にシークレットを公開することでした。</span><span class="sxs-lookup"><span data-stu-id="048ef-113">A common misstep was to include the file when pushing to a public GIT repository, exposing the secrets to the world.</span></span>

<span data-ttu-id="048ef-114">最新の分散アプリケーションを構築するために広く受け入れられている方法として、 [Twelve-Factor アプリ](https://12factor.net/)があります。</span><span class="sxs-lookup"><span data-stu-id="048ef-114">A widely accepted methodology for constructing modern distributed applications is [The Twelve-Factor App](https://12factor.net/).</span></span> <span data-ttu-id="048ef-115">ここでは、一連の原則とベストプラクティスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="048ef-115">It describes a set of principles and best practices.</span></span> <span data-ttu-id="048ef-116">3番目の要素 *は、構成とシークレットがコードベースの外部で外部化さ* れることを規定します。</span><span class="sxs-lookup"><span data-stu-id="048ef-116">Its third factor prescribes that *configuration and secrets be externalized outside of the code base.*</span></span>

<span data-ttu-id="048ef-117">この問題に対処するために、.NET Core プラットフォームには、機密データをプロジェクトツリーの外部の物理的なフォルダーに格納する [Secret Manager](/aspnet/core/security/app-secrets#secret-manager) 機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="048ef-117">To address this concern, the .NET Core platform includes a [Secret Manager](/aspnet/core/security/app-secrets#secret-manager) feature that stores sensitive data in a physical folder outside of the project tree.</span></span> <span data-ttu-id="048ef-118">シークレットはソース管理の対象外ですが、この機能はデータを暗号化しません。</span><span class="sxs-lookup"><span data-stu-id="048ef-118">While secrets are outside of source control, this feature doesn't encrypt data.</span></span> <span data-ttu-id="048ef-119">**開発目的** のためだけに設計されています。</span><span class="sxs-lookup"><span data-stu-id="048ef-119">It's designed for **development purposes** only.</span></span>

<span data-ttu-id="048ef-120">より新しい安全な方法は、 **Hashicorp Vault** や **Azure Key Vault** などのシークレット管理ツールでシークレットを分離することです。</span><span class="sxs-lookup"><span data-stu-id="048ef-120">A more modern and secure practice is to isolate secrets in a secrets management tool like **Hashicorp Vault** or **Azure Key Vault**.</span></span>  <span data-ttu-id="048ef-121">これらのツールを使用すると、シークレットを外部に格納し、環境間で資格情報を変更して、アプリケーションコードから参照できます。</span><span class="sxs-lookup"><span data-stu-id="048ef-121">These tools enable you to store secrets externally, vary credentials across environments, and reference them from application code.</span></span> <span data-ttu-id="048ef-122">ただし、各ツールには複雑で学習曲線があります。</span><span class="sxs-lookup"><span data-stu-id="048ef-122">However, each tool has its complexities and learning curve.</span></span>

<span data-ttu-id="048ef-123">Dapr は、シークレットの管理を簡略化するビルディングブロックを提供します。</span><span class="sxs-lookup"><span data-stu-id="048ef-123">Dapr offers a building block that simplifies managing secrets.</span></span>

## <a name="what-it-solves"></a><span data-ttu-id="048ef-124">解決方法</span><span class="sxs-lookup"><span data-stu-id="048ef-124">What it solves</span></span>

<span data-ttu-id="048ef-125">Dapr secret [ビルディングブロック](https://docs.dapr.io/developing-applications/building-blocks/secrets/secrets-overview/) は、シークレットとシークレット管理ツールの操作の複雑さを解消します。</span><span class="sxs-lookup"><span data-stu-id="048ef-125">The Dapr [secrets building block](https://docs.dapr.io/developing-applications/building-blocks/secrets/secrets-overview/) abstracts away the complexity of working with secrets and secret management tools.</span></span>

- <span data-ttu-id="048ef-126">これにより、基になるプラミングが統合インターフェイスで非表示になります。</span><span class="sxs-lookup"><span data-stu-id="048ef-126">It hides the underlying plumbing through a unified interface.</span></span>
- <span data-ttu-id="048ef-127">これは、開発と運用の間で異なる可能性がある、 *プラグ* 可能なさまざまなシークレットストアコンポーネントをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="048ef-127">It supports various *pluggable* secret store components, which can vary between development and production.</span></span>
- <span data-ttu-id="048ef-128">アプリケーションでは、シークレットストアライブラリに直接依存する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="048ef-128">Applications don't require direct dependencies on secret store libraries.</span></span>
- <span data-ttu-id="048ef-129">開発者は、各シークレットストアに関する詳細な知識を必要としません。</span><span class="sxs-lookup"><span data-stu-id="048ef-129">Developers don't require detailed knowledge of each secret store.</span></span>

<span data-ttu-id="048ef-130">Dapr は、上記のすべての懸念事項を処理します。</span><span class="sxs-lookup"><span data-stu-id="048ef-130">Dapr handles all of the above concerns.</span></span>

<span data-ttu-id="048ef-131">シークレットへのアクセスは、認証と承認によって保護されます。</span><span class="sxs-lookup"><span data-stu-id="048ef-131">Access to the secrets is secured through authentication and authorization.</span></span> <span data-ttu-id="048ef-132">十分な権限を持つアプリケーションのみがシークレットにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="048ef-132">Only an application with sufficient rights can access secrets.</span></span> <span data-ttu-id="048ef-133">Kubernetes で実行されているアプリケーションは、組み込みのシークレット管理メカニズムを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="048ef-133">Applications running in Kubernetes can also use its built-in secrets management mechanism.</span></span>

## <a name="how-it-works"></a><span data-ttu-id="048ef-134">しくみ</span><span class="sxs-lookup"><span data-stu-id="048ef-134">How it works</span></span>

<span data-ttu-id="048ef-135">アプリケーションでは、次の2つの方法でシークレット構成ブロックを使用します。</span><span class="sxs-lookup"><span data-stu-id="048ef-135">Applications use the secrets building block in two ways:</span></span>

- <span data-ttu-id="048ef-136">アプリケーションブロックからシークレットを直接取得します。</span><span class="sxs-lookup"><span data-stu-id="048ef-136">Retrieve a secret directly from the application block.</span></span>
- <span data-ttu-id="048ef-137">Dapr コンポーネント構成から間接的にシークレットを参照します。</span><span class="sxs-lookup"><span data-stu-id="048ef-137">Reference a secret indirectly from a Dapr component configuration.</span></span>

<span data-ttu-id="048ef-138">シークレットを直接取得する方法については、最初に説明します。</span><span class="sxs-lookup"><span data-stu-id="048ef-138">Retrieving secrets directly is covered first.</span></span> <span data-ttu-id="048ef-139">Dapr コンポーネント構成ファイルからシークレットを参照する方法については、後のセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="048ef-139">Referencing a secret from a Dapr component configuration file is addressed in a later section.</span></span>

<span data-ttu-id="048ef-140">アプリケーションは、シークレットの構成ブロックを使用しているときに dapr サイドカーと対話します。</span><span class="sxs-lookup"><span data-stu-id="048ef-140">The application interacts with a Dapr sidecar when using the secrets building block.</span></span> <span data-ttu-id="048ef-141">サイドカーは、シークレット API を公開しています。</span><span class="sxs-lookup"><span data-stu-id="048ef-141">The sidecar exposes the secrets API.</span></span> <span data-ttu-id="048ef-142">API は、HTTP または gRPC を使用して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="048ef-142">The API can be called with either HTTP or gRPC.</span></span> <span data-ttu-id="048ef-143">次の URL を使用して HTTP API を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="048ef-143">Use the following URL to call the HTTP API:</span></span>

```http
http://localhost:<dapr-port>/v1.0/secrets/<store-name>/<name>?<metadata>
```

<span data-ttu-id="048ef-144">URL には、次のセグメントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="048ef-144">The URL contains the following segments:</span></span>

- <span data-ttu-id="048ef-145">`<dapr-port>` dapr サイドカーがリッスンするポート番号を指定します。</span><span class="sxs-lookup"><span data-stu-id="048ef-145">`<dapr-port>` specifies the port number upon which the Dapr sidecar is listening.</span></span>
- <span data-ttu-id="048ef-146">`<store-name>` Dapr シークレットストアの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="048ef-146">`<store-name>` specifies the name of the Dapr secret store.</span></span>
- <span data-ttu-id="048ef-147">`<name>` 取得するシークレットの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="048ef-147">`<name>` specifies  the name of the secret to retrieve.</span></span>
- <span data-ttu-id="048ef-148">`<metadata>` シークレットに関する追加情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="048ef-148">`<metadata>` provides additional information for the secret.</span></span> <span data-ttu-id="048ef-149">このセグメントは省略可能であり、メタデータのプロパティはシークレットストアごとに異なります。</span><span class="sxs-lookup"><span data-stu-id="048ef-149">This segment is optional and metadata properties differ per secret store.</span></span> <span data-ttu-id="048ef-150">メタデータプロパティの詳細については、「 [シークレット API リファレンス]([Secrets API reference | Dapr Docs](https://docs.dapr.io/reference/api/secrets_api/))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="048ef-150">For more information on metadata properties, see the [secrets API reference]([Secrets API reference | Dapr Docs](https://docs.dapr.io/reference/api/secrets_api/)).</span></span>

 > [!NOTE]
 > <span data-ttu-id="048ef-151">上記の URL は、HTTP または gRPC をサポートするすべての開発プラットフォームで使用できるネイティブな Dapr API 呼び出しを表します。</span><span class="sxs-lookup"><span data-stu-id="048ef-151">The above URL represents the native Dapr API call available to any development platform that supports HTTP or gRPC.</span></span> <span data-ttu-id="048ef-152">.NET、Java、およびゴーなどの一般的なプラットフォームには、独自のカスタム Api があります。</span><span class="sxs-lookup"><span data-stu-id="048ef-152">Popular platforms like .NET, Java, and Go have their own custom APIs.</span></span>

<span data-ttu-id="048ef-153">JSON 応答には、シークレットのキーと値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="048ef-153">The JSON response contains the key and value of the secret.</span></span>

<span data-ttu-id="048ef-154">図10-1 は、Dapr がシークレット API の要求を処理する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="048ef-154">Figure 10-1 shows how Dapr handles a request for the secrets API:</span></span>

![Dapr シークレット API を使用してシークレットを取得する方法の図。](media/secrets/secrets-flow.png)

<span data-ttu-id="048ef-156">**図 10-1**.</span><span class="sxs-lookup"><span data-stu-id="048ef-156">**Figure 10-1**.</span></span> <span data-ttu-id="048ef-157">Dapr secret API を使用してシークレットを取得する。</span><span class="sxs-lookup"><span data-stu-id="048ef-157">Retrieving a secret with the Dapr secrets API.</span></span>

1. <span data-ttu-id="048ef-158">サービスは、Dapr シークレット API と、シークレットストアの名前、および取得するシークレットを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="048ef-158">The service calls the Dapr secrets API, along with the name of the secret store, and secret to retrieve.</span></span>
1. <span data-ttu-id="048ef-159">Dapr サイドカーは、指定されたシークレットをシークレットストアから取得します。</span><span class="sxs-lookup"><span data-stu-id="048ef-159">The Dapr sidecar retrieves the specified secret from the secret store.</span></span>
1. <span data-ttu-id="048ef-160">Dapr サイドカーは、秘密情報をサービスに返します。</span><span class="sxs-lookup"><span data-stu-id="048ef-160">The Dapr sidecar returns the secret information back to the service.</span></span>

<span data-ttu-id="048ef-161">一部のシークレットストアでは、複数のキー/値ペアを1つのシークレットに格納することがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="048ef-161">Some secret stores support storing multiple key/value pairs in a single secret.</span></span> <span data-ttu-id="048ef-162">これらのシナリオでは、次の例に示すように、応答には1つの JSON 応答に複数のキー/値ペアが含まれます。</span><span class="sxs-lookup"><span data-stu-id="048ef-162">For those scenarios, the response would contain multiple key/value pairs in a single JSON response as in the following example:</span></span>

```http
GET http://localhost:3500/v1.0/secrets/secret-store/interestRates?metadata.version_id=3
```

```json
{
  "tier1-percentage": "2.5",
  "tier2-percentage": "3.8",
  "tier3-percentage": "5.1"
}
```

<span data-ttu-id="048ef-163">Dapr シークレット API は、アプリケーションがアクセスできるすべてのシークレットを取得する操作も提供します。</span><span class="sxs-lookup"><span data-stu-id="048ef-163">The Dapr secrets API also offers an operation to retrieve all the secrets the application has access to:</span></span>

```http
http://localhost:<dapr-port>/v1.0/secrets/<store-name>/bulk
```

## <a name="use-the-dapr-net-sdk"></a><span data-ttu-id="048ef-164">Dapr .NET SDK を使用する</span><span class="sxs-lookup"><span data-stu-id="048ef-164">Use the Dapr .NET SDK</span></span>

<span data-ttu-id="048ef-165">.NET 開発者の場合、Dapr .NET SDK を使用すると、Dapr のシークレット管理が効率化されます。</span><span class="sxs-lookup"><span data-stu-id="048ef-165">For .NET developers, the Dapr .NET SDK streamlines Dapr secret management.</span></span> <span data-ttu-id="048ef-166">メソッドについて考えてみましょう `DaprClient.GetSecretAsync` 。</span><span class="sxs-lookup"><span data-stu-id="048ef-166">Consider the `DaprClient.GetSecretAsync` method.</span></span> <span data-ttu-id="048ef-167">これにより、最小限の労力で、任意の Dapr シークレットストアからシークレットを直接取得できます。</span><span class="sxs-lookup"><span data-stu-id="048ef-167">It enables you to retrieve a secret directly from any Dapr secret store with minimal effort.</span></span> <span data-ttu-id="048ef-168">SQL Server データベースの接続文字列シークレットを取得する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="048ef-168">Here's an example of fetching a connection string secret for a SQL Server database:</span></span>

```csharp
var metadata = new Dictionary<string, string> { ["version_id"] = "3" };
Dictionary<string, string> secrets = await daprClient.GetSecretAsync("secret-store", "eshopsecrets", metadata);
string connectionString = secrets["customerdb"];
```

<span data-ttu-id="048ef-169">メソッドの引数 `GetSecretAsync` は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="048ef-169">Arguments for the `GetSecretAsync` method include:</span></span>

- <span data-ttu-id="048ef-170">Dapr シークレットストアコンポーネント (' secret ストア ') の名前</span><span class="sxs-lookup"><span data-stu-id="048ef-170">The name of the Dapr secret store component ('secret-store')</span></span>
- <span data-ttu-id="048ef-171">取得するシークレット (' eshopsecrets ')</span><span class="sxs-lookup"><span data-stu-id="048ef-171">The secret to retrieve ('eshopsecrets')</span></span>
- <span data-ttu-id="048ef-172">省略可能なメタデータのキーと値のペア (' version_id = 3 ')</span><span class="sxs-lookup"><span data-stu-id="048ef-172">Optional metadata key/value pairs ('version_id=3')</span></span>

<span data-ttu-id="048ef-173">シークレットには複数のキーと値のペアを含めることができるため、メソッドはディクショナリオブジェクトで応答します。</span><span class="sxs-lookup"><span data-stu-id="048ef-173">The method responds with a dictionary object as a secret can contain multiple key/value pairs.</span></span> <span data-ttu-id="048ef-174">上の例では、という名前のシークレット `customerdb` がコレクションから参照され、接続文字列が返されます。</span><span class="sxs-lookup"><span data-stu-id="048ef-174">In the example above, the secret named `customerdb` is referenced from the collection to return a connection string.</span></span>

<span data-ttu-id="048ef-175">Dapr .NET SDK には、.NET 構成プロバイダーも用意されています。</span><span class="sxs-lookup"><span data-stu-id="048ef-175">The Dapr .NET SDK also features a .NET configuration provider.</span></span> <span data-ttu-id="048ef-176">指定されたシークレットを、基になる [.Net Core 構成 API](../../core/extensions/configuration.md)に読み込みます。</span><span class="sxs-lookup"><span data-stu-id="048ef-176">It loads specified secrets into the underlying [.NET Core configuration API](../../core/extensions/configuration.md).</span></span> <span data-ttu-id="048ef-177">実行中のアプリケーションは、 `IConfiguration` ASP.NET Core 依存関係の挿入に登録されているディクショナリからシークレットを参照できます。</span><span class="sxs-lookup"><span data-stu-id="048ef-177">The running application can then reference secrets from the `IConfiguration` dictionary that is registered in ASP.NET Core dependency injection.</span></span>

<span data-ttu-id="048ef-178">シークレット構成プロバイダーは、 [Dapr.Extensions.Configuration](https://www.nuget.org/packages/Dapr.Extensions.Configuration) NuGet パッケージから入手できます。</span><span class="sxs-lookup"><span data-stu-id="048ef-178">The secrets configuration provider is available from the [Dapr.Extensions.Configuration](https://www.nuget.org/packages/Dapr.Extensions.Configuration) NuGet package.</span></span> <span data-ttu-id="048ef-179">プロバイダーは、 `Program.cs` ASP.NET Web API アプリケーションのに登録できます。</span><span class="sxs-lookup"><span data-stu-id="048ef-179">The provider can be registered in the `Program.cs` of an ASP.NET Web API application:</span></span>  

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureAppConfiguration(config =>
        {
            var daprClient = new DaprClientBuilder().Build();
            var secretDescriptors = new List<DaprSecretDescriptor>
            {
                new DaprSecretDescriptor("eshopsecrets")
            };
            config.AddDaprSecretStore("secret-store", secretDescriptors, daprClient);
        })
        .ConfigureWebHostDefaults(webBuilder =>
        {
            webBuilder.UseStartup<Startup>();
        });
```

<span data-ttu-id="048ef-180">上の例では、 `eshopsecrets` 起動時に、.net 構成システムにシークレットコレクションを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="048ef-180">The above example loads the `eshopsecrets` secrets collection into the .NET configuration system at startup.</span></span> <span data-ttu-id="048ef-181">プロバイダーを登録するには、 `DaprClient` Dapr sidecar でシークレット API を呼び出すために、のインスタンスが必要です。</span><span class="sxs-lookup"><span data-stu-id="048ef-181">Registering the provider requires an instance of `DaprClient` to invoke the secrets API on the Dapr sidecar.</span></span> <span data-ttu-id="048ef-182">その他の引数には、シークレットストアの名前、および `DaprSecretDescriptor` シークレットの名前を含むオブジェクトが含まれます。</span><span class="sxs-lookup"><span data-stu-id="048ef-182">The other arguments include the name of the secret store and a `DaprSecretDescriptor` object with the name of the secret.</span></span>

<span data-ttu-id="048ef-183">読み込みが完了すると、アプリケーションコードから直接シークレットを取得できます。</span><span class="sxs-lookup"><span data-stu-id="048ef-183">Once loaded, you can retrieve secrets directly from application code:</span></span>

```csharp
public void GetCustomer(IConfiguration config)
{
    var connectionString = config["eshopsecrets"]["customerdb"];
}
```

## <a name="secret-store-components"></a><span data-ttu-id="048ef-184">シークレットストアのコンポーネント</span><span class="sxs-lookup"><span data-stu-id="048ef-184">Secret store components</span></span>

<span data-ttu-id="048ef-185">シークレットの構成ブロックでは、複数のシークレットストアコンポーネントがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="048ef-185">The secrets building block supports several secret store components.</span></span> <span data-ttu-id="048ef-186">作成時には、次のシークレットストアを使用できます。</span><span class="sxs-lookup"><span data-stu-id="048ef-186">At the time of writing, the following secret stores are available:</span></span>

- <span data-ttu-id="048ef-187">環境変数</span><span class="sxs-lookup"><span data-stu-id="048ef-187">Environment Variables</span></span>
- <span data-ttu-id="048ef-188">ローカル ファイル</span><span class="sxs-lookup"><span data-stu-id="048ef-188">Local file</span></span>
- <span data-ttu-id="048ef-189">Kubernetes シークレット</span><span class="sxs-lookup"><span data-stu-id="048ef-189">Kubernetes secrets</span></span>
- <span data-ttu-id="048ef-190">AWS シークレットマネージャー</span><span class="sxs-lookup"><span data-stu-id="048ef-190">AWS Secrets Manager</span></span>
- <span data-ttu-id="048ef-191">Azure Key Vault</span><span class="sxs-lookup"><span data-stu-id="048ef-191">Azure Key Vault</span></span>
- <span data-ttu-id="048ef-192">GCP シークレットマネージャー</span><span class="sxs-lookup"><span data-stu-id="048ef-192">GCP Secret Manager</span></span>
- <span data-ttu-id="048ef-193">HashiCorp コンテナー</span><span class="sxs-lookup"><span data-stu-id="048ef-193">HashiCorp Vault</span></span>

> [!IMPORTANT]
> <span data-ttu-id="048ef-194">環境変数とローカルファイルコンポーネントは、開発ワークロード専用に設計されています。</span><span class="sxs-lookup"><span data-stu-id="048ef-194">The environment variables and local file components are designed for development workloads only.</span></span>

<span data-ttu-id="048ef-195">次のセクションでは、シークレットストアを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="048ef-195">The following sections show how to configure a secret store.</span></span>

### <a name="configuration"></a><span data-ttu-id="048ef-196">構成</span><span class="sxs-lookup"><span data-stu-id="048ef-196">Configuration</span></span>

<span data-ttu-id="048ef-197">共有ストアは、Dapr コンポーネント構成ファイルを使用して構成します。</span><span class="sxs-lookup"><span data-stu-id="048ef-197">You configure a secret store using a Dapr component configuration file.</span></span> <span data-ttu-id="048ef-198">ファイルの一般的な構造を次に示します。</span><span class="sxs-lookup"><span data-stu-id="048ef-198">The typical structure of the file is shown below:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: [component name]
  namespace: [namespace]
spec:
  type: secretstores.[secret store type]
  version: [secret store version]
  metadata:
  - name: [property name]
    value: [property value]
```

<span data-ttu-id="048ef-199">すべての Dapr コンポーネント構成ファイルは、 `name` オプションの値と共にを必要と `namespace` します。</span><span class="sxs-lookup"><span data-stu-id="048ef-199">All Dapr component configuration files require a `name` along with an optional `namespace` value.</span></span> <span data-ttu-id="048ef-200">また、セクションのフィールドは、 `type` `spec` シークレットストアコンポーネントの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="048ef-200">Additionally, the `type` field in the `spec` section specifies the type of secret store component.</span></span> <span data-ttu-id="048ef-201">セクションのプロパティは、 `metadata` シークレットストアごとに異なります。</span><span class="sxs-lookup"><span data-stu-id="048ef-201">The properties in the `metadata` section differ per secret store.</span></span>

### <a name="indirectly-consume-dapr-secrets"></a><span data-ttu-id="048ef-202">Dapr シークレットを間接的に使用する</span><span class="sxs-lookup"><span data-stu-id="048ef-202">Indirectly consume Dapr secrets</span></span>

<span data-ttu-id="048ef-203">この章で既に説明したように、アプリケーションでは、コンポーネント構成ファイルでシークレットを参照することによってシークレットを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="048ef-203">As mentioned earlier in this chapter, applications can also consume secrets by referencing them in component configuration files.</span></span> <span data-ttu-id="048ef-204">状態を格納するために Redis cache を使用する [状態管理コンポーネント](state-management.md) を考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="048ef-204">Consider a [state management component](state-management.md) that uses Redis cache for storing state:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: eshop-basket-statestore
  namespace: eshop
spec:
  type: state.redis
  version: v1
  metadata:
  - name: redisHost
    value: localhost:6379
  - name: redisPassword
    value: e$h0p0nD@pr
```

<span data-ttu-id="048ef-205">上記の構成ファイルには、Redis サーバーに接続するための **クリアテキスト** パスワードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="048ef-205">The above configuration file contains a **clear-text** password for connecting to the Redis server.</span></span> <span data-ttu-id="048ef-206">**ハードコーディング** されたパスワードは、常に不適切なアイデアです。</span><span class="sxs-lookup"><span data-stu-id="048ef-206">**Hardcoded** passwords are always a bad idea.</span></span> <span data-ttu-id="048ef-207">この構成ファイルをパブリックリポジトリにプッシュすると、パスワードが公開されます。</span><span class="sxs-lookup"><span data-stu-id="048ef-207">Pushing this configuration file to a public repository would expose the password.</span></span> <span data-ttu-id="048ef-208">シークレットストアにパスワードを格納すると、このシナリオが大幅に改善されます。</span><span class="sxs-lookup"><span data-stu-id="048ef-208">Storing the password in a secret store would dramatically improve this scenario.</span></span>

<span data-ttu-id="048ef-209">次の例では、いくつかの異なるシークレットストアを使用してこれを示します。</span><span class="sxs-lookup"><span data-stu-id="048ef-209">The following examples demonstrate this using several different secret stores.</span></span>

### <a name="local-file"></a><span data-ttu-id="048ef-210">ローカル ファイル</span><span class="sxs-lookup"><span data-stu-id="048ef-210">Local file</span></span>

<span data-ttu-id="048ef-211">ローカルファイルコンポーネントは、開発シナリオ向けに設計されています。</span><span class="sxs-lookup"><span data-stu-id="048ef-211">The local file component is designed for development scenarios.</span></span> <span data-ttu-id="048ef-212">JSON ファイル内のローカルファイルシステムにシークレットを格納します。</span><span class="sxs-lookup"><span data-stu-id="048ef-212">It stores secrets on the local filesystem inside a JSON file.</span></span> <span data-ttu-id="048ef-213">という名前の例を次に示し `eshop-secrets.json` ます。</span><span class="sxs-lookup"><span data-stu-id="048ef-213">Here's an example named `eshop-secrets.json`.</span></span> <span data-ttu-id="048ef-214">これには、Redis のパスワードという1つの秘密が含まれます。</span><span class="sxs-lookup"><span data-stu-id="048ef-214">It contains a single secret - a password for Redis:</span></span>

```json
{
  "eShopRedisPassword": "e$h0p0nD@pr"
}
```

<span data-ttu-id="048ef-215">このファイルは、 `components` Dapr アプリケーションの実行時に指定したフォルダーに配置します。</span><span class="sxs-lookup"><span data-stu-id="048ef-215">You place this file in a `components` folder that you specify when running the Dapr application.</span></span>

<span data-ttu-id="048ef-216">次のシークレットストア構成ファイルは、シークレットストアとして JSON ファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="048ef-216">The following secret store configuration file consumes the JSON file as a secret store.</span></span> <span data-ttu-id="048ef-217">次のフォルダーにも配置され `components` ます。</span><span class="sxs-lookup"><span data-stu-id="048ef-217">It's also placed in the `components` folder:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: eshop-local-secret-store
  namespace: eshop
spec:
  type: secretstores.local.file
  version: v1
  metadata:
  - name: secretsFile
    value: ./components/eshop-secrets.json
  - name: nestedSeparator
    value: ":"
```

<span data-ttu-id="048ef-218">コンポーネントの種類が `secretstore.local.file` です。</span><span class="sxs-lookup"><span data-stu-id="048ef-218">The component type is `secretstore.local.file`.</span></span> <span data-ttu-id="048ef-219">`secretsFile`メタデータ要素は、シークレットファイルへのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="048ef-219">The `secretsFile` metadata element specifies the path to the secrets file.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="048ef-220">シークレットファイルへのパスには、絶対パスまたは相対パスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="048ef-220">The path to a secrets file can be a absolute or relative path.</span></span> <span data-ttu-id="048ef-221">相対パスは、アプリケーションを起動するフォルダーに基づいています。</span><span class="sxs-lookup"><span data-stu-id="048ef-221">The relative path is based on the folder in which the application starts.</span></span> <span data-ttu-id="048ef-222">この例では、 `components` フォルダーは、.net アプリケーションが格納されているディレクトリのサブフォルダーです。</span><span class="sxs-lookup"><span data-stu-id="048ef-222">In the example, the `components` folder is a sub-folder of the directory that contains the .NET application.</span></span>

<span data-ttu-id="048ef-223">アプリケーションフォルダーから、 `components` コマンドライン引数としてパスを指定して Dapr アプリケーションを開始します。</span><span class="sxs-lookup"><span data-stu-id="048ef-223">From the application folder, start the Dapr application specifying the `components` path as a command-line argument:</span></span>

```console
dapr run --app-id basket-api --components-path ./components dotnet run
```

> [!NOTE]
> <span data-ttu-id="048ef-224">上記の例は、自己ホスト型モードでの Dapr の実行に適用されます。</span><span class="sxs-lookup"><span data-stu-id="048ef-224">This above example applies to running Dapr in self-hosted mode.</span></span> <span data-ttu-id="048ef-225">Kubernetes をホストする場合は、ボリュームマウントの使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="048ef-225">For Kubernetes hosting, consider using volume mounts.</span></span>

<span data-ttu-id="048ef-226">`nestedSeparator`Dapr 構成ファイルのは、JSON 階層を *平坦* 化する文字を指定します。</span><span class="sxs-lookup"><span data-stu-id="048ef-226">The `nestedSeparator` in a Dapr configuration file specifies a character to *flatten* a JSON hierarchy.</span></span> <span data-ttu-id="048ef-227">次のスニペットを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="048ef-227">Consider the following snippet:</span></span>

```json
{
    "redisPassword": "some password",
    "connectionStrings": {
        "customerdb": "some connection string",
        "productdb": "some connection string"
    }
}
```

<span data-ttu-id="048ef-228">区切り記号としてコロンを使用すると、 `customerdb` キーを使用して接続文字列を取得でき `connectionStrings:customerdb` ます。</span><span class="sxs-lookup"><span data-stu-id="048ef-228">Using a colon as a separator, you can retrieve the `customerdb` connection-string using the key `connectionStrings:customerdb`.</span></span>

> [!NOTE]
> <span data-ttu-id="048ef-229">`:`既定の区切り記号の値は、コロンです。</span><span class="sxs-lookup"><span data-stu-id="048ef-229">The colon `:` is the default separator value.</span></span>

<span data-ttu-id="048ef-230">次の例では、状態管理構成ファイルがローカルシークレットストアコンポーネントを参照し、Redis サーバーに接続するためのパスワードを取得します。</span><span class="sxs-lookup"><span data-stu-id="048ef-230">In the next example, a state management configuration file references the local secret store component to obtain the password for connecting to the Redis server:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: eshop-basket-statestore
  namespace: eshop
spec:
  type: state.redis
  version: v1
  metadata:
  - name: redisHost
    value: localhost:6379
  - name: redisPassword
    secretKeyRef:
      name: eShopRedisPassword
      key: eShopRedisPassword
auth:
  secretStore: eshop-local-secret-store
```

<span data-ttu-id="048ef-231">要素は、 `secretKeyRef` パスワードを含むシークレットを参照します。</span><span class="sxs-lookup"><span data-stu-id="048ef-231">The `secretKeyRef` element references the secret containing the password.</span></span> <span data-ttu-id="048ef-232">これは、以前の *クリアテキスト* の値を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="048ef-232">It replaces the earlier *clear-text* value.</span></span> <span data-ttu-id="048ef-233">シークレット名とキー名は、 `eShopRedisPassword` シークレットを参照します。</span><span class="sxs-lookup"><span data-stu-id="048ef-233">The secret name and the key name, `eShopRedisPassword`, reference the secret.</span></span> <span data-ttu-id="048ef-234">シークレット管理コンポーネントの名前は、 `eshop-local-secret-store` `auth` メタデータ要素にあります。</span><span class="sxs-lookup"><span data-stu-id="048ef-234">The name of the secret management component `eshop-local-secret-store` is found in the `auth` metadata element.</span></span>

<span data-ttu-id="048ef-235">`eShopRedisPassword`シークレット参照の名前とキーの両方でが同一であることが不思議に思われるかもしれません。</span><span class="sxs-lookup"><span data-stu-id="048ef-235">You might wonder why `eShopRedisPassword` is identical for both the name and key in the secret reference.</span></span> <span data-ttu-id="048ef-236">ローカルファイルシークレットストアでは、シークレットは別の名前で識別されません。</span><span class="sxs-lookup"><span data-stu-id="048ef-236">In the local file secret store, secrets aren't identified with a separate name.</span></span> <span data-ttu-id="048ef-237">このシナリオは、Kubernetes シークレットを使用した次の例では異なります。</span><span class="sxs-lookup"><span data-stu-id="048ef-237">The scenario will be different in the next example using Kubernetes secrets.</span></span>

### <a name="kubernetes-secret"></a><span data-ttu-id="048ef-238">Kubernetes シークレット</span><span class="sxs-lookup"><span data-stu-id="048ef-238">Kubernetes secret</span></span>

<span data-ttu-id="048ef-239">この2番目の例では、Kubernetes で実行されている Dapr アプリケーションに焦点を当てています。</span><span class="sxs-lookup"><span data-stu-id="048ef-239">This second example focuses on a Dapr application running in Kubernetes.</span></span> <span data-ttu-id="048ef-240">Kubernetes が提供する標準のシークレット機構を使用します。</span><span class="sxs-lookup"><span data-stu-id="048ef-240">It uses the standard secrets mechanism that Kubernetes offers.</span></span> <span data-ttu-id="048ef-241">Kubernetes CLI ( `kubectl` ) を使用して、パスワードを含むという名前のシークレットを作成し `eshop-redis-secret` ます。</span><span class="sxs-lookup"><span data-stu-id="048ef-241">Use the Kubernetes CLI (`kubectl`) to create a secret named `eshop-redis-secret` that contains the password:</span></span>

```console
kubectl create secret generic eshopsecrets --from-literal=redisPassword=e$h0p0nD@pr -n eshop
```

<span data-ttu-id="048ef-242">作成後は、状態管理のコンポーネント構成ファイルでシークレットを参照できます。</span><span class="sxs-lookup"><span data-stu-id="048ef-242">Once created, you can reference the secret in the component configuration file for state management:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: eshop-basket-statestore
  namespace: eshop
spec:
  type: state.redis
  version: v1
  metadata:
  - name: redisHost
    value: redis:6379
  - name: redisPassword
    secretKeyRef:
      name: eshopsecrets
      key: redisPassword
auth:
  secretStore: kubernetes
```

<span data-ttu-id="048ef-243">要素は、 `secretKeyRef` Kubernetes シークレットの名前とシークレットのキー、およびをそれぞれ指定し `eshopsecrets` `redisPassword` ます。</span><span class="sxs-lookup"><span data-stu-id="048ef-243">The `secretKeyRef` element specifies the name of the Kubernetes secret and the secret's key, `eshopsecrets`, and `redisPassword` respectively.</span></span> <span data-ttu-id="048ef-244">`auth`メタデータセクションは、Kubernetes シークレット管理コンポーネントを使用するように Dapr に指示します。</span><span class="sxs-lookup"><span data-stu-id="048ef-244">The `auth` metadata section instructs Dapr to use the Kubernetes secrets management component.</span></span>

> [!NOTE]
> <span data-ttu-id="048ef-245">Kubernetes シークレットを使用する場合、Auth が既定値となります。これは省略できます。</span><span class="sxs-lookup"><span data-stu-id="048ef-245">Auth is the default value when using Kubernetes secrets and can be omitted.</span></span>

<span data-ttu-id="048ef-246">運用環境の設定では、通常、シークレットは自動 CI/CD パイプラインの一部として作成されます。</span><span class="sxs-lookup"><span data-stu-id="048ef-246">In a production setting, secrets are typically created as part of an automated CI/CD pipeline.</span></span> <span data-ttu-id="048ef-247">これにより、十分なアクセス許可を持つ方だけがシークレットにアクセスして変更できるようになります。</span><span class="sxs-lookup"><span data-stu-id="048ef-247">Doing so ensures only people with sufficient permissions can access and change the secrets.</span></span> <span data-ttu-id="048ef-248">開発者は、シークレットの実際の値を知らずに構成ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="048ef-248">Developers create configuration files without knowing the actual value of the secrets.</span></span>

### <a name="azure-key-vault"></a><span data-ttu-id="048ef-249">Azure Key Vault</span><span class="sxs-lookup"><span data-stu-id="048ef-249">Azure Key Vault</span></span>

<span data-ttu-id="048ef-250">次の例は、実稼働環境のシナリオを対象としています。</span><span class="sxs-lookup"><span data-stu-id="048ef-250">The next example is geared toward a real-world production scenario.</span></span> <span data-ttu-id="048ef-251">シークレットストアとして **Azure Key Vault** を使用します。</span><span class="sxs-lookup"><span data-stu-id="048ef-251">It uses **Azure Key Vault** as the secret store.</span></span> <span data-ttu-id="048ef-252">Azure Key Vault は、シークレットをクラウドに安全に格納できるようにする、管理された Azure サービスです。</span><span class="sxs-lookup"><span data-stu-id="048ef-252">Azure Key Vault is a managed Azure service that enables secrets to be stored securely in the cloud.</span></span>

<span data-ttu-id="048ef-253">この例を使用するには、次の前提条件を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="048ef-253">For this example to work, the following prerequisites must be satisfied:</span></span>

- <span data-ttu-id="048ef-254">Azure サブスクリプションへの管理アクセスをセキュリティで保護しました。</span><span class="sxs-lookup"><span data-stu-id="048ef-254">You've secured administrative access to an Azure subscription.</span></span>
- <span data-ttu-id="048ef-255">`eshopkv` `redisPassword` Redis サーバーに接続するためのパスワードを含むという名前のシークレットを保持するという名前の Azure Key Vault をプロビジョニングしました。</span><span class="sxs-lookup"><span data-stu-id="048ef-255">You've provisioned an Azure Key Vault named `eshopkv` that holds a secret named `redisPassword` that contains the password for connecting to the Redis server.</span></span>
- <span data-ttu-id="048ef-256">Azure Active Directory で [サービスプリンシパル](/azure/active-directory/develop/howto-create-service-principal-portal) が作成されました。</span><span class="sxs-lookup"><span data-stu-id="048ef-256">You've created [service principal](/azure/active-directory/develop/howto-create-service-principal-portal) in Azure Active Directory.</span></span>
- <span data-ttu-id="048ef-257">このサービスプリンシパル (公開キーと秘密キーの両方を含む) の X509 証明書をローカルファイルシステムにインストールしました。</span><span class="sxs-lookup"><span data-stu-id="048ef-257">You've installed an X509 certificate for this service principal (containing both the public and private key) on the local filesystem.</span></span>

> [!NOTE]
> <span data-ttu-id="048ef-258">サービスプリンシパルは、アプリケーションが Azure サービスを認証するために使用できる id です。</span><span class="sxs-lookup"><span data-stu-id="048ef-258">A service principal is an identity that can be used by an application to authenticate an Azure service.</span></span> <span data-ttu-id="048ef-259">サービスプリンシパルは、X509 証明書を使用します。</span><span class="sxs-lookup"><span data-stu-id="048ef-259">The service principal uses a X509 certificate.</span></span> <span data-ttu-id="048ef-260">アプリケーションは、資格情報としてこの証明書を使用して自身を認証します。</span><span class="sxs-lookup"><span data-stu-id="048ef-260">The application uses this certificate as a credential to authenticate itself.</span></span>

<span data-ttu-id="048ef-261">[Dapr Azure Key Vault シークレットストアのドキュメント](https://docs.dapr.io/operations/components/setup-secret-store/supported-secret-stores/azure-keyvault/)では、Key Vault 環境を作成および構成するための詳細な手順について説明しています。</span><span class="sxs-lookup"><span data-stu-id="048ef-261">The [Dapr Azure Key Vault secret store documentation](https://docs.dapr.io/operations/components/setup-secret-store/supported-secret-stores/azure-keyvault/) provides step-by-step instructions to create and configure a Key Vault environment.</span></span>

#### <a name="use-key-vault-when-running-in-self-hosted-mode"></a><span data-ttu-id="048ef-262">自己ホスト型モードで実行する場合は Key Vault を使用する</span><span class="sxs-lookup"><span data-stu-id="048ef-262">Use Key Vault when running in self-hosted mode</span></span>

<span data-ttu-id="048ef-263">Dapr の自己ホスト型モードで Azure Key Vault を使用するには、次の構成ファイルが必要です。</span><span class="sxs-lookup"><span data-stu-id="048ef-263">Consuming Azure Key Vault in Dapr self-hosted mode requires the following configuration file:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: eshop-azurekv-secret-store
  namespace: eshop
spec:
  type: secretstores.azure.keyvault
  version: v1
  metadata:
  - name: vaultName
    value: eshopkv
  - name: spnTenantId
    value: "619926af-a7c3-4e95-93ed-4ecc4e3e652b"
  - name: spnClientId
    value: "6cf48032-6c38-43be-9d6f-2a43ce736b09"
  - name: spnCertificateFile
    value : "azurekv-spn-cert.pfx"
```

<span data-ttu-id="048ef-264">シークレットストアの種類は `secretstores.azure.keyvault` です。</span><span class="sxs-lookup"><span data-stu-id="048ef-264">The secret store type is `secretstores.azure.keyvault`.</span></span> <span data-ttu-id="048ef-265">`metadata`Key Vault へのアクセスを構成する要素には、次のプロパティが必要です。</span><span class="sxs-lookup"><span data-stu-id="048ef-265">The `metadata` element to configure access to Key Vault requires the following properties:</span></span>

- <span data-ttu-id="048ef-266">には、 `vaultName` Azure Key Vault の名前が含まれています。</span><span class="sxs-lookup"><span data-stu-id="048ef-266">The `vaultName` contains the name of the Azure Key Vault.</span></span>
- <span data-ttu-id="048ef-267">には、 `spnTenantId` Key Vault に対する認証に使用されるサービスプリンシパルの *テナント ID* が含まれています。</span><span class="sxs-lookup"><span data-stu-id="048ef-267">The `spnTenantId` contains the *tenant ID* of the service principal used to authenticate against the Key Vault.</span></span>
- <span data-ttu-id="048ef-268">には、 `spnClientId` Key Vault に対する認証に使用されるサービスプリンシパルの *アプリ ID* が格納されます。</span><span class="sxs-lookup"><span data-stu-id="048ef-268">The `spnClientId` contains the *app ID* of the service principal used to authenticate against the Key Vault.</span></span>
- <span data-ttu-id="048ef-269">には、 `spnCertificateFile` サービスプリンシパルが Key Vault に対して認証を行うための証明書ファイルへのパスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="048ef-269">The `spnCertificateFile` contains the path to the certificate file for the service principal to authenticate against the Key Vault.</span></span>

> [!TIP]
> <span data-ttu-id="048ef-270">サービスプリンシパル情報は、Azure portal または Azure CLI からコピーできます。</span><span class="sxs-lookup"><span data-stu-id="048ef-270">You can copy the service principal information from the Azure portal or Azure CLI .</span></span>

<span data-ttu-id="048ef-271">これで、アプリケーションは Azure Key Vault から Redis パスワードを取得できるようになります。</span><span class="sxs-lookup"><span data-stu-id="048ef-271">Now the application can retrieve the Redis password from the Azure Key Vault.</span></span>

#### <a name="use-key-vault-when-running-on-kubernetes"></a><span data-ttu-id="048ef-272">Kubernetes で実行する場合は Key Vault を使用する</span><span class="sxs-lookup"><span data-stu-id="048ef-272">Use Key Vault when running on Kubernetes</span></span>

<span data-ttu-id="048ef-273">Dapr と Kubernetes で Azure Key Vault を使用するには、Azure Key Vault に対して認証するためのサービスプリンシパルも必要です。</span><span class="sxs-lookup"><span data-stu-id="048ef-273">Consuming Azure Key Vault with Dapr and Kubernetes also requires a service principal to authenticate against the Azure Key Vault.</span></span>

<span data-ttu-id="048ef-274">まず、kubectl CLI ツールを使用して証明書ファイルを含む *Kubernetes シークレット* を作成します。</span><span class="sxs-lookup"><span data-stu-id="048ef-274">First, create a *Kubernetes secret* that contains a certificate file using the kubectl CLI tool:</span></span>

```console
kubectl create secret generic [k8s_spn_secret_name] --from-file=[pfx_certificate_file_local_path] -n eshop
```

<span data-ttu-id="048ef-275">コマンドには、次の2つのコマンドライン引数が必要です。</span><span class="sxs-lookup"><span data-stu-id="048ef-275">The command requires two command-line arguments:</span></span>

- <span data-ttu-id="048ef-276">`[k8s_spn_secret_name]` Kubernetes secret ストアのシークレット名を指定します。</span><span class="sxs-lookup"><span data-stu-id="048ef-276">`[k8s_spn_secret_name]` is the secret name in Kubernetes secret store.</span></span>
- <span data-ttu-id="048ef-277">`[pfx_certificate_file_local_path]` は、X509 証明書ファイルのパスです。</span><span class="sxs-lookup"><span data-stu-id="048ef-277">`[pfx_certificate_file_local_path]` is the path of X509 certificate file.</span></span>

<span data-ttu-id="048ef-278">作成したら、シークレットストアのコンポーネント構成ファイルで Kubernetes シークレットを参照できます。</span><span class="sxs-lookup"><span data-stu-id="048ef-278">Once created, you can reference the Kubernetes secret in the secret store component configuration file:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: eshop-azurekv-secret-store
  namespace: eshop
spec:
  type: secretstores.azure.keyvault
  version: v1
  metadata:
  - name: vaultName
    value: [your_keyvault_name]
  - name: spnTenantId
    value: "619926af-a7c3-4e95-93ed-4ecc4e3e652b"
  - name: spnClientId
    value: "6cf48032-6c38-43be-9d6f-2a43ce736b09"
  - name: spnCertificate
    secretKeyRef:
      name: [k8s_spn_secret_name]
      key: [pfx_certificate_file_local_name]
auth:
    secretStore: kubernetes
```

<span data-ttu-id="048ef-279">この時点で、Kubernetes で実行されているアプリケーションは、Azure Key Vault から Redis パスワードを取得できます。</span><span class="sxs-lookup"><span data-stu-id="048ef-279">At this point, an application running in Kubernetes can retrieve the Redis password from the Azure Key Vault.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="048ef-280">サービスプリンシパルの X509 証明書ファイルを安全な場所に保管することが重要です。</span><span class="sxs-lookup"><span data-stu-id="048ef-280">It's critical to keep the X509 certificate file for the service principal in a safe place.</span></span> <span data-ttu-id="048ef-281">ソースコードリポジトリの外部にあるよく知られたフォルダーに配置することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="048ef-281">It's best to place it in a well-known folder outside the source-code repository.</span></span> <span data-ttu-id="048ef-282">構成ファイルは、この既知のフォルダーから証明書ファイルを参照できます。</span><span class="sxs-lookup"><span data-stu-id="048ef-282">The configuration file can then reference the certificate file from this well-known folder.</span></span> <span data-ttu-id="048ef-283">ローカルの開発用コンピューターでは、証明書をフォルダーにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="048ef-283">On a local development machine, you're responsible for copying the certificate to the folder.</span></span> <span data-ttu-id="048ef-284">自動デプロイの場合、パイプラインはアプリケーションが配置されているコンピューターに証明書をコピーします。</span><span class="sxs-lookup"><span data-stu-id="048ef-284">For automated deployments, the pipeline will copy the certificate to the machine where the application is deployed.</span></span> <span data-ttu-id="048ef-285">ベストプラクティスとして、環境ごとに異なるサービスプリンシパルを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="048ef-285">It's a best practice to use a different service principal per environment.</span></span> <span data-ttu-id="048ef-286">これにより、開発環境のサービスプリンシパルが運用環境のシークレットにアクセスできなくなります。</span><span class="sxs-lookup"><span data-stu-id="048ef-286">Doing so prevents the service principal from a DEVELOPMENT environment to access secrets in a PRODUCTION environment.</span></span>

<span data-ttu-id="048ef-287">Azure Kubernetes Service (AKS) で実行する場合は、Azure Key Vault に対して認証を行うために [Azure マネージ id](/azure/active-directory/managed-identities-azure-resources/overview) を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="048ef-287">When running in  Azure Kubernetes Service (AKS), it's preferable to use an [Azure Managed Identity](/azure/active-directory/managed-identities-azure-resources/overview) for authenticating against Azure Key Vault.</span></span> <span data-ttu-id="048ef-288">マネージド id はこの書籍の範囲外ですが、 [管理対象 id に](https://docs.dapr.io/operations/components/setup-secret-store/supported-secret-stores/azure-keyvault-managed-identity/) 関するドキュメントの Azure Key Vault で説明されています。</span><span class="sxs-lookup"><span data-stu-id="048ef-288">Managed identities are outside of the scope of this book, but explained in the [Azure Key Vault with managed identities](https://docs.dapr.io/operations/components/setup-secret-store/supported-secret-stores/azure-keyvault-managed-identity/) documentation.</span></span>

### <a name="scope-secrets"></a><span data-ttu-id="048ef-289">シークレットのスコープを適用する</span><span class="sxs-lookup"><span data-stu-id="048ef-289">Scope secrets</span></span>

<span data-ttu-id="048ef-290">シークレットスコープを使用すると、アプリケーションがアクセスできるシークレットを制御できます。</span><span class="sxs-lookup"><span data-stu-id="048ef-290">Secret scopes allow you to control which secrets your application can access.</span></span> <span data-ttu-id="048ef-291">スコープは、dapr サイドカー構成ファイルで構成します。</span><span class="sxs-lookup"><span data-stu-id="048ef-291">You configure scopes in a Dapr sidecar configuration file.</span></span> <span data-ttu-id="048ef-292">[Dapr 構成ドキュメント](https://docs.dapr.io/operations/configuration/configuration-overview/)では、シークレットのスコープを設定する方法を説明しています。</span><span class="sxs-lookup"><span data-stu-id="048ef-292">The [Dapr configuration documentation](https://docs.dapr.io/operations/configuration/configuration-overview/) provides instructions for scoping secrets.</span></span>

<span data-ttu-id="048ef-293">次に、秘密のスコープを含む dapr サイドカー構成ファイルの例を示します。</span><span class="sxs-lookup"><span data-stu-id="048ef-293">Here's an example of a Dapr sidecar configuration file that contains secret scopes:</span></span>

```yml
apiVersion: dapr.io/v1alpha1
kind: Configuration
metadata:
  name: dapr-config
  namespace: eshop
spec:
  tracing:
    samplingRate: "1"
  secrets:
    scopes:
      - storeName: eshop-azurekv-secret-store
        defaultAccess: allow
        deniedSecrets: ["redisPassword", "apiKey"]
```

<span data-ttu-id="048ef-294">シークレットストアごとにスコープを指定します。</span><span class="sxs-lookup"><span data-stu-id="048ef-294">You specify scopes per secret store.</span></span> <span data-ttu-id="048ef-295">上の例では、シークレットストアにという名前が付けられて `eshop-azurekv-secret-store` います。</span><span class="sxs-lookup"><span data-stu-id="048ef-295">In the above example, the secret store is named `eshop-azurekv-secret-store`.</span></span> <span data-ttu-id="048ef-296">シークレットへのアクセスを構成するには、次のプロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="048ef-296">You configure access to secrets using the following properties:</span></span>

| <span data-ttu-id="048ef-297">プロパティ</span><span class="sxs-lookup"><span data-stu-id="048ef-297">Property</span></span>         | <span data-ttu-id="048ef-298">値</span><span class="sxs-lookup"><span data-stu-id="048ef-298">Value</span></span>               | <span data-ttu-id="048ef-299">説明</span><span class="sxs-lookup"><span data-stu-id="048ef-299">Description</span></span>                                                                                                                       |
|------------------|---------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| `defaultAccess`  | <span data-ttu-id="048ef-300">`allow` または `deny`</span><span class="sxs-lookup"><span data-stu-id="048ef-300">`allow` or `deny`</span></span>   | <span data-ttu-id="048ef-301">指定したシークレットストア内の *すべて* のシークレットへのアクセスを許可または拒否します。</span><span class="sxs-lookup"><span data-stu-id="048ef-301">Allows or denies access to *all* secrets in the specified secret store.</span></span> <span data-ttu-id="048ef-302">このプロパティは省略可能で、既定値は `allow` です。</span><span class="sxs-lookup"><span data-stu-id="048ef-302">This property is optional with a default value of `allow`.</span></span> |
| `allowedSecrets` | <span data-ttu-id="048ef-303">秘密キーの一覧</span><span class="sxs-lookup"><span data-stu-id="048ef-303">List of secret keys</span></span> | <span data-ttu-id="048ef-304">配列に指定されたシークレットにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="048ef-304">Secrets specified in the array will be accessible.</span></span> <span data-ttu-id="048ef-305">このプロパティは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="048ef-305">This property is optional.</span></span>                                                     |
| `deniedSecrets`  | <span data-ttu-id="048ef-306">秘密キーの一覧</span><span class="sxs-lookup"><span data-stu-id="048ef-306">List of secret keys</span></span> | <span data-ttu-id="048ef-307">配列に指定されたシークレットにアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="048ef-307">Secrets specified in the array will NOT be accessible.</span></span> <span data-ttu-id="048ef-308">このプロパティは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="048ef-308">This property is optional.</span></span>                                                 |

<span data-ttu-id="048ef-309">`allowedSecrets`プロパティと `deniedSecrets` プロパティは、プロパティよりも優先され `defaultAccess` ます。</span><span class="sxs-lookup"><span data-stu-id="048ef-309">The `allowedSecrets` and `deniedSecrets` properties take precedence over the `defaultAccess` property.</span></span> <span data-ttu-id="048ef-310">とリストを指定することを想像 `defaultAccess: allowed` `allowedSecrets` してください。</span><span class="sxs-lookup"><span data-stu-id="048ef-310">Imagine specifying `defaultAccess: allowed` and an `allowedSecrets` list.</span></span> <span data-ttu-id="048ef-311">この場合、アプリケーションからアクセスできるのはリスト内のシークレットだけ `allowedSecrets` です。</span><span class="sxs-lookup"><span data-stu-id="048ef-311">In this case, only the secrets in the `allowedSecrets` list would be accessible by the application.</span></span>

## <a name="reference-application-eshopondapr"></a><span data-ttu-id="048ef-312">参照アプリケーション: eShopOnDapr</span><span class="sxs-lookup"><span data-stu-id="048ef-312">Reference application: eShopOnDapr</span></span>

<span data-ttu-id="048ef-313">EShopOnDapr 参照アプリケーションは、次の2つのシークレットに対してシークレットの構成ブロックを使用します。</span><span class="sxs-lookup"><span data-stu-id="048ef-313">The eShopOnDapr reference application uses the secrets building block for two secrets:</span></span>

- <span data-ttu-id="048ef-314">Redis cache に接続するためのパスワード。</span><span class="sxs-lookup"><span data-stu-id="048ef-314">The password for connecting to the Redis cache.</span></span>
- <span data-ttu-id="048ef-315">Twilio Sendgrid API を使用するための API キー。</span><span class="sxs-lookup"><span data-stu-id="048ef-315">The API-key for using the Twilio Sendgrid API.</span></span> <span data-ttu-id="048ef-316">アプリケーションは、Twillio を使用して、Dapr 出力バインドを使用して電子メールを送信します (「binding [ビルディングブロック](bindings.md)」の章を参照)。</span><span class="sxs-lookup"><span data-stu-id="048ef-316">The application uses Twillio to send emails using a Dapr output binding (as described in the [bindings building block chapter](bindings.md)).</span></span>

<span data-ttu-id="048ef-317">Docker Compose を使用してアプリケーションを実行すると、 **ローカルファイル** シークレットストアが使用されます。</span><span class="sxs-lookup"><span data-stu-id="048ef-317">When running the application using Docker Compose, the **local file** secret store is used.</span></span> <span data-ttu-id="048ef-318">コンポーネント構成ファイル `eshop-secretstore.yaml` は、 `dapr/components` eShopOnDapr リポジトリのフォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="048ef-318">The component configuration file `eshop-secretstore.yaml` is found in the `dapr/components` folder of the eShopOnDapr repository:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: eshop-secretstore
  namespace: eshop
spec:
  type: secretstores.local.file
  version: v1
  metadata:
  - name: secretsFile
    value: ./components/eshop-secretstore.json
```

<span data-ttu-id="048ef-319">構成ファイルは、同じフォルダーにあるローカルストアファイルを参照し `eshop-secretstore.json` ます。</span><span class="sxs-lookup"><span data-stu-id="048ef-319">The configuration file references the local store file `eshop-secretstore.json` located in the same folder:</span></span>

```json
{
    "redisPassword": "**********",
    "sendgridAPIKey": "**********"
}
```

<span data-ttu-id="048ef-320">この `components` フォルダーはコマンドラインで指定され、dapr サイドカーコンテナー内にローカルフォルダーとしてマウントされます。</span><span class="sxs-lookup"><span data-stu-id="048ef-320">The `components` folder is specified in the command-line and mounted as a local folder inside the Dapr sidecar container.</span></span> <span data-ttu-id="048ef-321">`docker-compose.override.yml`ボリュームのマウントを指定するリポジトリルート内のファイルのスニペットを次に示します。</span><span class="sxs-lookup"><span data-stu-id="048ef-321">Here's a snippet from the `docker-compose.override.yml` file in the repository root that specifies the volume mount:</span></span>

```yaml
  ordering-backgroundtasks-dapr:
    command: ["./daprd",
      "-app-id", "ordering-backgroundtasks",
      "-app-port", "80",
      "-dapr-grpc-port", "50004",
      "-components-path", "/components",
      "-config", "/configuration/eshop-config.yaml"
      ]
    volumes:
      - "./dapr/components/:/components"
      - "./dapr/configuration/:/configuration"
```

> [!NOTE]
> <span data-ttu-id="048ef-322">Docker Compose 上書きファイルには、環境固有の構成値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="048ef-322">The Docker Compose override file contains environmental specific configuration values.</span></span>

<span data-ttu-id="048ef-323">`/components`ボリュームマウントと `--components-path` コマンドライン引数は、スタートアップコマンドに渡され `daprd` ます。</span><span class="sxs-lookup"><span data-stu-id="048ef-323">The `/components` volume mount and `--components-path` command-line argument are passed into the `daprd` startup command.</span></span>

<span data-ttu-id="048ef-324">構成が完了すると、他のコンポーネント構成ファイルでもシークレットを参照できます。</span><span class="sxs-lookup"><span data-stu-id="048ef-324">Once configured, other component configuration files can also reference the secrets.</span></span> <span data-ttu-id="048ef-325">次に、公開/サブスクライブコンポーネント構成でシークレットを使用する例を示します。</span><span class="sxs-lookup"><span data-stu-id="048ef-325">Here's an example of the Publish/Subscribe component configuration consuming secrets:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: pubsub
  namespace: eshop
spec:
  type: pubsub.redis
  version: v1
  metadata:
  - name: redisHost
    value: redis:6379
  - name: redisPassword
    secretKeyRef:
      name: redisPassword
auth:
  secretStore: eshop-secretstore
```

<span data-ttu-id="048ef-326">前の例では、シークレットを参照するためにローカル Redis ストアが使用されています。</span><span class="sxs-lookup"><span data-stu-id="048ef-326">In the preceding example, the local Redis store is used to reference secrets.</span></span>

## <a name="summary"></a><span data-ttu-id="048ef-327">まとめ</span><span class="sxs-lookup"><span data-stu-id="048ef-327">Summary</span></span>

<span data-ttu-id="048ef-328">Dapr シークレットの構成ブロックには、パスワードや接続文字列などの機密構成設定を格納および取得する機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="048ef-328">The Dapr secrets building block provides capabilities for storing and retrieving sensitive configuration settings like passwords and connection-strings.</span></span> <span data-ttu-id="048ef-329">シークレットはプライベートに保持され、誤って開示されることはありません。</span><span class="sxs-lookup"><span data-stu-id="048ef-329">It keeps secrets private and prevents them from being accidentally disclosed.</span></span>

<span data-ttu-id="048ef-330">ビルディングブロックでは、いくつかの異なるシークレットストアがサポートされており、Dapr シークレット API での複雑さが隠蔽されています。</span><span class="sxs-lookup"><span data-stu-id="048ef-330">The building block supports several different secret stores and hides their complexity with the Dapr secrets API.</span></span>

<span data-ttu-id="048ef-331">Dapr .NET SDK には、 `DaprClient` シークレットを取得するためのオブジェクトが用意されています。</span><span class="sxs-lookup"><span data-stu-id="048ef-331">The Dapr .NET SDK provides a `DaprClient` object to retrieve secrets.</span></span> <span data-ttu-id="048ef-332">また、.net Core 構成システムにシークレットを追加する .NET 構成プロバイダーも含まれています。</span><span class="sxs-lookup"><span data-stu-id="048ef-332">It also includes a .NET configuration provider that adds secrets to the .NET Core configuration system.</span></span> <span data-ttu-id="048ef-333">読み込んだ後は、これらのシークレットを .NET コードで使用できます。</span><span class="sxs-lookup"><span data-stu-id="048ef-333">Once loaded, you can consume these secrets in your .NET code.</span></span>

<span data-ttu-id="048ef-334">シークレットスコープを使用して、特定のシークレットへのアクセスを制御することができます。</span><span class="sxs-lookup"><span data-stu-id="048ef-334">You can use secret scopes to control access to specific secrets.</span></span>

## <a name="references"></a><span data-ttu-id="048ef-335">参照設定</span><span class="sxs-lookup"><span data-stu-id="048ef-335">References</span></span>

- [<span data-ttu-id="048ef-336">Twelve-Factor アプリケーション以外</span><span class="sxs-lookup"><span data-stu-id="048ef-336">Beyond the Twelve-Factor Application</span></span>](https://tanzu.vmware.com/content/blog/beyond-the-twelve-factor-app)

>[!div class="step-by-step"]
><span data-ttu-id="048ef-337">[前へ](observability.md)
>[次へ](summary.md)</span><span class="sxs-lookup"><span data-stu-id="048ef-337">[Previous](observability.md)
[Next](summary.md)</span></span>
