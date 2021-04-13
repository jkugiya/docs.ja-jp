---
title: Dapr のシークレット ビルディング ブロック
description: シークレット ビルディング ブロック、その機能、利点、適用方法の説明
author: edwinvw
ms.date: 02/17/2021
ms.openlocfilehash: 52b899b4d496aab6762f69bbee99faecfcd23d59
ms.sourcegitcommit: d623f686701b94bef905ec5e93d8b55d031c5d6f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/17/2021
ms.locfileid: "103623747"
---
# <a name="the-dapr-secrets-building-block"></a><span data-ttu-id="40adf-103">Dapr のシークレット ビルディング ブロック</span><span class="sxs-lookup"><span data-stu-id="40adf-103">The Dapr secrets building block</span></span>

<span data-ttu-id="40adf-104">エンタープライズ アプリケーションにはシークレットが必要です。</span><span class="sxs-lookup"><span data-stu-id="40adf-104">Enterprise applications require secrets.</span></span> <span data-ttu-id="40adf-105">たとえば、次のような場合です。</span><span class="sxs-lookup"><span data-stu-id="40adf-105">Common examples include:</span></span>

- <span data-ttu-id="40adf-106">ユーザー名とパスワードを含むデータベース接続文字列。</span><span class="sxs-lookup"><span data-stu-id="40adf-106">A database connection string that contains a username and password.</span></span>
- <span data-ttu-id="40adf-107">外部 Web API を呼び出すための API キー。</span><span class="sxs-lookup"><span data-stu-id="40adf-107">An API key for calling an external web API.</span></span>
- <span data-ttu-id="40adf-108">外部システムに対して認証を行うためのクライアント証明書。</span><span class="sxs-lookup"><span data-stu-id="40adf-108">A client certificate for authenticating to an external system.</span></span>

<span data-ttu-id="40adf-109">シークレットは、アプリケーションの外部に公開されないように慎重に管理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="40adf-109">Secrets must be carefully managed so that they're never disclosed outside of the application.</span></span>

<span data-ttu-id="40adf-110">最近までは、アプリケーションのシークレットをアプリケーション コードベース内の構成ファイルに格納するのが一般的でした。</span><span class="sxs-lookup"><span data-stu-id="40adf-110">Not long ago, it was popular to store application secrets in a configuration file inside the application codebase.</span></span> <span data-ttu-id="40adf-111">.NET 開発者は、*web.config* ファイルを呼び戻すでしょう。</span><span class="sxs-lookup"><span data-stu-id="40adf-111">.NET developers will fondly recall the *web.config* file.</span></span> <span data-ttu-id="40adf-112">実装するのは簡単ですが、シークレットとコードの統合は決して安全なものではありませんでした。</span><span class="sxs-lookup"><span data-stu-id="40adf-112">While simple to implement, integrating secrets to along with code was far from secure.</span></span> <span data-ttu-id="40adf-113">よくある間違いは、パブリック Git リポジトリへのプッシュ時にファイルを追加し、世界中にシークレットを公開してしまうことでした。</span><span class="sxs-lookup"><span data-stu-id="40adf-113">A common misstep was to include the file when pushing to a public GIT repository, exposing the secrets to the world.</span></span>

<span data-ttu-id="40adf-114">最新の分散型アプリケーションの構築方法として広く受け入れられているのが [The Twelve-Factor App](https://12factor.net/) です。</span><span class="sxs-lookup"><span data-stu-id="40adf-114">A widely accepted methodology for constructing modern distributed applications is [The Twelve-Factor App](https://12factor.net/).</span></span> <span data-ttu-id="40adf-115">これには一連の原則とベスト プラクティスが記述されています。</span><span class="sxs-lookup"><span data-stu-id="40adf-115">It describes a set of principles and best practices.</span></span> <span data-ttu-id="40adf-116">3 番目の要素では、"*構成とシークレットはコードベース外に外部化される*" と規定しています。</span><span class="sxs-lookup"><span data-stu-id="40adf-116">Its third factor prescribes that *configuration and secrets be externalized outside of the code base.*</span></span>

<span data-ttu-id="40adf-117">この問題に対処するために、.NET Core プラットフォームには、プロジェクト ツリーの外部にある物理フォルダーに機密データを格納する[シークレット マネージャー](/aspnet/core/security/app-secrets#secret-manager)機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="40adf-117">To address this concern, the .NET Core platform includes a [Secret Manager](/aspnet/core/security/app-secrets#secret-manager) feature that stores sensitive data in a physical folder outside of the project tree.</span></span> <span data-ttu-id="40adf-118">シークレットはソース管理の対象外ですが、この機能ではデータを暗号化しません。</span><span class="sxs-lookup"><span data-stu-id="40adf-118">While secrets are outside of source control, this feature doesn't encrypt data.</span></span> <span data-ttu-id="40adf-119">**開発** のみを目的として設計されています。</span><span class="sxs-lookup"><span data-stu-id="40adf-119">It's designed for **development purposes** only.</span></span>

<span data-ttu-id="40adf-120">より安全性に優れた最新の方法としては、**Hashicorp Vault** や **Azure Key Vault** などのシークレット管理ツールでシークレットを分離します。</span><span class="sxs-lookup"><span data-stu-id="40adf-120">A more modern and secure practice is to isolate secrets in a secrets management tool like **Hashicorp Vault** or **Azure Key Vault**.</span></span>  <span data-ttu-id="40adf-121">これらのツールを使用すると、シークレットを外部に格納し、環境間で資格情報を変更して、アプリケーション コードから参照できます。</span><span class="sxs-lookup"><span data-stu-id="40adf-121">These tools enable you to store secrets externally, vary credentials across environments, and reference them from application code.</span></span> <span data-ttu-id="40adf-122">ただし、各ツールにはそれぞれ複雑な点と学習曲線があります。</span><span class="sxs-lookup"><span data-stu-id="40adf-122">However, each tool has its complexities and learning curve.</span></span>

<span data-ttu-id="40adf-123">Dapr は、シークレットの管理を簡略化するビルディング ブロックを提供します。</span><span class="sxs-lookup"><span data-stu-id="40adf-123">Dapr offers a building block that simplifies managing secrets.</span></span>

## <a name="what-it-solves"></a><span data-ttu-id="40adf-124">解決される内容</span><span class="sxs-lookup"><span data-stu-id="40adf-124">What it solves</span></span>

<span data-ttu-id="40adf-125">Dapr の[シークレット ビルディング ブロック](https://docs.dapr.io/developing-applications/building-blocks/secrets/secrets-overview/)は、シークレットとシークレット管理ツールの操作の複雑さを解消します。</span><span class="sxs-lookup"><span data-stu-id="40adf-125">The Dapr [secrets building block](https://docs.dapr.io/developing-applications/building-blocks/secrets/secrets-overview/) abstracts away the complexity of working with secrets and secret management tools.</span></span>

- <span data-ttu-id="40adf-126">統合インターフェイスを使用して、基になるプラミングを非表示にします。</span><span class="sxs-lookup"><span data-stu-id="40adf-126">It hides the underlying plumbing through a unified interface.</span></span>
- <span data-ttu-id="40adf-127">開発と運用の間で異なる可能性のある、"*プラグ可能な*" さまざまなシークレット ストア コンポーネントがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="40adf-127">It supports various *pluggable* secret store components, which can vary between development and production.</span></span>
- <span data-ttu-id="40adf-128">アプリケーションには、シークレット ストア ライブラリへの直接的な依存関係は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="40adf-128">Applications don't require direct dependencies on secret store libraries.</span></span>
- <span data-ttu-id="40adf-129">開発者には、各シークレット ストアに関する詳細な知識は不要です。</span><span class="sxs-lookup"><span data-stu-id="40adf-129">Developers don't require detailed knowledge of each secret store.</span></span>

<span data-ttu-id="40adf-130">Dapr は上記のすべての懸念事項に対処します。</span><span class="sxs-lookup"><span data-stu-id="40adf-130">Dapr handles all of the above concerns.</span></span>

<span data-ttu-id="40adf-131">シークレットへのアクセスは、認証と認可によって保護されます。</span><span class="sxs-lookup"><span data-stu-id="40adf-131">Access to the secrets is secured through authentication and authorization.</span></span> <span data-ttu-id="40adf-132">十分な権限を持つアプリケーションのみシークレットにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="40adf-132">Only an application with sufficient rights can access secrets.</span></span> <span data-ttu-id="40adf-133">Kubernetes で実行されているアプリケーションでは、組み込みのシークレット管理メカニズムを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="40adf-133">Applications running in Kubernetes can also use its built-in secrets management mechanism.</span></span>

## <a name="how-it-works"></a><span data-ttu-id="40adf-134">しくみ</span><span class="sxs-lookup"><span data-stu-id="40adf-134">How it works</span></span>

<span data-ttu-id="40adf-135">アプリケーションでは、次の 2 つの方法でシークレット ビルディング ブロックを使用します。</span><span class="sxs-lookup"><span data-stu-id="40adf-135">Applications use the secrets building block in two ways:</span></span>

- <span data-ttu-id="40adf-136">アプリケーション ブロックから直接シークレットを取得する。</span><span class="sxs-lookup"><span data-stu-id="40adf-136">Retrieve a secret directly from the application block.</span></span>
- <span data-ttu-id="40adf-137">Dapr コンポーネント構成から間接的にシークレットを参照する。</span><span class="sxs-lookup"><span data-stu-id="40adf-137">Reference a secret indirectly from a Dapr component configuration.</span></span>

<span data-ttu-id="40adf-138">直接シークレットを取得する方法について最初に説明します。</span><span class="sxs-lookup"><span data-stu-id="40adf-138">Retrieving secrets directly is covered first.</span></span> <span data-ttu-id="40adf-139">Dapr コンポーネント構成ファイルからシークレットを参照する方法については、後のセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="40adf-139">Referencing a secret from a Dapr component configuration file is addressed in a later section.</span></span>

<span data-ttu-id="40adf-140">アプリケーションは、シークレット ビルディング ブロックの使用時に Dapr サイドカーと対話します。</span><span class="sxs-lookup"><span data-stu-id="40adf-140">The application interacts with a Dapr sidecar when using the secrets building block.</span></span> <span data-ttu-id="40adf-141">サイドカーは、シークレット API を公開しています。</span><span class="sxs-lookup"><span data-stu-id="40adf-141">The sidecar exposes the secrets API.</span></span> <span data-ttu-id="40adf-142">この API は、HTTP または gRPC を使用して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="40adf-142">The API can be called with either HTTP or gRPC.</span></span> <span data-ttu-id="40adf-143">次の URL を使用して HTTP API を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="40adf-143">Use the following URL to call the HTTP API:</span></span>

```http
http://localhost:<dapr-port>/v1.0/secrets/<store-name>/<name>?<metadata>
```

<span data-ttu-id="40adf-144">この URL に含まれるセグメントは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="40adf-144">The URL contains the following segments:</span></span>

- <span data-ttu-id="40adf-145">`<dapr-port>` は、Dapr サイドカーがリッスンするポート番号を指定します。</span><span class="sxs-lookup"><span data-stu-id="40adf-145">`<dapr-port>` specifies the port number upon which the Dapr sidecar is listening.</span></span>
- <span data-ttu-id="40adf-146">`<store-name>` は、Dapr シークレット ストアの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="40adf-146">`<store-name>` specifies the name of the Dapr secret store.</span></span>
- <span data-ttu-id="40adf-147">`<name>` は、取得するシークレットの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="40adf-147">`<name>` specifies  the name of the secret to retrieve.</span></span>
- <span data-ttu-id="40adf-148">`<metadata>` は、シークレットの追加情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="40adf-148">`<metadata>` provides additional information for the secret.</span></span> <span data-ttu-id="40adf-149">このセグメントは省略可能であり、メタデータ プロパティはシークレット ストアごとに異なります。</span><span class="sxs-lookup"><span data-stu-id="40adf-149">This segment is optional and metadata properties differ per secret store.</span></span> <span data-ttu-id="40adf-150">メタデータ プロパティの詳細については、[シークレット API リファレンス]([Secrets API reference | Dapr Docs](https://docs.dapr.io/reference/api/secrets_api/))を参照してください。</span><span class="sxs-lookup"><span data-stu-id="40adf-150">For more information on metadata properties, see the [secrets API reference]([Secrets API reference | Dapr Docs](https://docs.dapr.io/reference/api/secrets_api/)).</span></span>

 > [!NOTE]
 > <span data-ttu-id="40adf-151">上記の URL は、HTTP または gRPC をサポートするすべての開発プラットフォームで使用可能なネイティブの Dapr API 呼び出しを表します。</span><span class="sxs-lookup"><span data-stu-id="40adf-151">The above URL represents the native Dapr API call available to any development platform that supports HTTP or gRPC.</span></span> <span data-ttu-id="40adf-152">.NET、Java、Go などの一般的なプラットフォームには独自のカスタム API があります。</span><span class="sxs-lookup"><span data-stu-id="40adf-152">Popular platforms like .NET, Java, and Go have their own custom APIs.</span></span>

<span data-ttu-id="40adf-153">JSON 応答には、シークレットのキーと値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="40adf-153">The JSON response contains the key and value of the secret.</span></span>

<span data-ttu-id="40adf-154">図 10-1 は、Dapr がシークレット API の要求を処理する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="40adf-154">Figure 10-1 shows how Dapr handles a request for the secrets API:</span></span>

![Dapr シークレット API を使用したシークレットの取得を示す図。](media/secrets/secrets-flow.png)

<span data-ttu-id="40adf-156">**図 10-1**</span><span class="sxs-lookup"><span data-stu-id="40adf-156">**Figure 10-1**.</span></span> <span data-ttu-id="40adf-157">Dapr シークレット API を使用したシークレットの取得。</span><span class="sxs-lookup"><span data-stu-id="40adf-157">Retrieving a secret with the Dapr secrets API.</span></span>

1. <span data-ttu-id="40adf-158">サービスが、Dapr シークレット API、シークレット ストアの名前、取得するシークレットを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="40adf-158">The service calls the Dapr secrets API, along with the name of the secret store, and secret to retrieve.</span></span>
1. <span data-ttu-id="40adf-159">Dapr サイドカーが、指定されたシークレットをシークレット ストアから取得します。</span><span class="sxs-lookup"><span data-stu-id="40adf-159">The Dapr sidecar retrieves the specified secret from the secret store.</span></span>
1. <span data-ttu-id="40adf-160">Dapr サイドカーが、シークレット情報をサービスに返します。</span><span class="sxs-lookup"><span data-stu-id="40adf-160">The Dapr sidecar returns the secret information back to the service.</span></span>

<span data-ttu-id="40adf-161">一部のシークレット ストアでは、複数のキー/値のペアを 1 つのシークレットに格納できます。</span><span class="sxs-lookup"><span data-stu-id="40adf-161">Some secret stores support storing multiple key/value pairs in a single secret.</span></span> <span data-ttu-id="40adf-162">これらのシナリオでは、次の例に示すように、1 つの JSON 応答に複数のキー/値のペアが含まれます。</span><span class="sxs-lookup"><span data-stu-id="40adf-162">For those scenarios, the response would contain multiple key/value pairs in a single JSON response as in the following example:</span></span>

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

<span data-ttu-id="40adf-163">Dapr シークレット API は、アプリケーションがアクセスできるすべてのシークレットを取得する操作も提供します。</span><span class="sxs-lookup"><span data-stu-id="40adf-163">The Dapr secrets API also offers an operation to retrieve all the secrets the application has access to:</span></span>

```http
http://localhost:<dapr-port>/v1.0/secrets/<store-name>/bulk
```

## <a name="use-the-dapr-net-sdk"></a><span data-ttu-id="40adf-164">Dapr .NET SDK を使用する</span><span class="sxs-lookup"><span data-stu-id="40adf-164">Use the Dapr .NET SDK</span></span>

<span data-ttu-id="40adf-165">.NET 開発者が Dapr .NET SDK を使用すると、Dapr のシークレット管理が効率化されます。</span><span class="sxs-lookup"><span data-stu-id="40adf-165">For .NET developers, the Dapr .NET SDK streamlines Dapr secret management.</span></span> <span data-ttu-id="40adf-166">たとえば、`DaprClient.GetSecretAsync` メソッドがあるとします。</span><span class="sxs-lookup"><span data-stu-id="40adf-166">Consider the `DaprClient.GetSecretAsync` method.</span></span> <span data-ttu-id="40adf-167">これにより、最小限の作業で、任意の Dapr シークレット ストアから直接シークレットを取得できます。</span><span class="sxs-lookup"><span data-stu-id="40adf-167">It enables you to retrieve a secret directly from any Dapr secret store with minimal effort.</span></span> <span data-ttu-id="40adf-168">SQL Server データベースの接続文字列シークレットを取り込む例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="40adf-168">Here's an example of fetching a connection string secret for a SQL Server database:</span></span>

```csharp
var metadata = new Dictionary<string, string> { ["version_id"] = "3" };
Dictionary<string, string> secrets = await daprClient.GetSecretAsync("secret-store", "eshopsecrets", metadata);
string connectionString = secrets["customerdb"];
```

<span data-ttu-id="40adf-169">`GetSecretAsync` メソッドの引数は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="40adf-169">Arguments for the `GetSecretAsync` method include:</span></span>

- <span data-ttu-id="40adf-170">Dapr シークレット ストア コンポーネントの名前 ("secret-store")</span><span class="sxs-lookup"><span data-stu-id="40adf-170">The name of the Dapr secret store component ('secret-store')</span></span>
- <span data-ttu-id="40adf-171">取得するシークレット ("eshopsecrets")</span><span class="sxs-lookup"><span data-stu-id="40adf-171">The secret to retrieve ('eshopsecrets')</span></span>
- <span data-ttu-id="40adf-172">(省略可能) メタデータのキーと値のペア ("version_id=3")</span><span class="sxs-lookup"><span data-stu-id="40adf-172">Optional metadata key/value pairs ('version_id=3')</span></span>

<span data-ttu-id="40adf-173">シークレットには複数のキーと値のペアを含めることができるため、このメソッドは辞書オブジェクトで応答します。</span><span class="sxs-lookup"><span data-stu-id="40adf-173">The method responds with a dictionary object as a secret can contain multiple key/value pairs.</span></span> <span data-ttu-id="40adf-174">上の例では、`customerdb` という名前のシークレットがコレクションから参照され、接続文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="40adf-174">In the example above, the secret named `customerdb` is referenced from the collection to return a connection string.</span></span>

<span data-ttu-id="40adf-175">Dapr .NET SDK には .NET 構成プロバイダーも用意されています。</span><span class="sxs-lookup"><span data-stu-id="40adf-175">The Dapr .NET SDK also features a .NET configuration provider.</span></span> <span data-ttu-id="40adf-176">これは、指定されたシークレットを、基になる [.NET Core 構成 API](../../core/extensions/configuration.md) に読み込みます。</span><span class="sxs-lookup"><span data-stu-id="40adf-176">It loads specified secrets into the underlying [.NET Core configuration API](../../core/extensions/configuration.md).</span></span> <span data-ttu-id="40adf-177">これで、実行中のアプリケーションは、ASP.NET Core 依存関係の挿入で登録される `IConfiguration` 辞書からシークレットを参照できます。</span><span class="sxs-lookup"><span data-stu-id="40adf-177">The running application can then reference secrets from the `IConfiguration` dictionary that is registered in ASP.NET Core dependency injection.</span></span>

<span data-ttu-id="40adf-178">シークレット構成プロバイダーは、[Dapr.Extensions.Configuration](https://www.nuget.org/packages/Dapr.Extensions.Configuration) NuGet パッケージから入手できます。</span><span class="sxs-lookup"><span data-stu-id="40adf-178">The secrets configuration provider is available from the [Dapr.Extensions.Configuration](https://www.nuget.org/packages/Dapr.Extensions.Configuration) NuGet package.</span></span> <span data-ttu-id="40adf-179">このプロバイダーは、ASP.NET Web API アプリケーションの `Program.cs` で登録できます。</span><span class="sxs-lookup"><span data-stu-id="40adf-179">The provider can be registered in the `Program.cs` of an ASP.NET Web API application:</span></span>  

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

<span data-ttu-id="40adf-180">上の例では、起動時に `eshopsecrets` シークレット コレクションを .NET 構成システムに読み込みます。</span><span class="sxs-lookup"><span data-stu-id="40adf-180">The above example loads the `eshopsecrets` secrets collection into the .NET configuration system at startup.</span></span> <span data-ttu-id="40adf-181">プロバイダーを登録するには、Dapr サイドカーでシークレット API を呼び出すための `DaprClient` のインスタンスが必要です。</span><span class="sxs-lookup"><span data-stu-id="40adf-181">Registering the provider requires an instance of `DaprClient` to invoke the secrets API on the Dapr sidecar.</span></span> <span data-ttu-id="40adf-182">その他の引数には、シークレット ストアの名前、およびシークレットの名前を含む `DaprSecretDescriptor` オブジェクトがあります。</span><span class="sxs-lookup"><span data-stu-id="40adf-182">The other arguments include the name of the secret store and a `DaprSecretDescriptor` object with the name of the secret.</span></span>

<span data-ttu-id="40adf-183">読み込みが完了すると、アプリケーション コードから直接シークレットを取得できます。</span><span class="sxs-lookup"><span data-stu-id="40adf-183">Once loaded, you can retrieve secrets directly from application code:</span></span>

```csharp
public void GetCustomer(IConfiguration config)
{
    var connectionString = config["eshopsecrets"]["customerdb"];
}
```

## <a name="secret-store-components"></a><span data-ttu-id="40adf-184">シークレット ストア コンポーネント</span><span class="sxs-lookup"><span data-stu-id="40adf-184">Secret store components</span></span>

<span data-ttu-id="40adf-185">シークレット ビルディング ブロックでは、複数のシークレット ストア コンポーネントがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="40adf-185">The secrets building block supports several secret store components.</span></span> <span data-ttu-id="40adf-186">この記事の執筆時点では、次のシークレット ストアを使用できます。</span><span class="sxs-lookup"><span data-stu-id="40adf-186">At the time of writing, the following secret stores are available:</span></span>

- <span data-ttu-id="40adf-187">環境変数</span><span class="sxs-lookup"><span data-stu-id="40adf-187">Environment Variables</span></span>
- <span data-ttu-id="40adf-188">ローカル ファイル</span><span class="sxs-lookup"><span data-stu-id="40adf-188">Local file</span></span>
- <span data-ttu-id="40adf-189">Kubernetes シークレット</span><span class="sxs-lookup"><span data-stu-id="40adf-189">Kubernetes secrets</span></span>
- <span data-ttu-id="40adf-190">AWS Secrets Manager</span><span class="sxs-lookup"><span data-stu-id="40adf-190">AWS Secrets Manager</span></span>
- <span data-ttu-id="40adf-191">Azure Key Vault</span><span class="sxs-lookup"><span data-stu-id="40adf-191">Azure Key Vault</span></span>
- <span data-ttu-id="40adf-192">GCP Secret Manager</span><span class="sxs-lookup"><span data-stu-id="40adf-192">GCP Secret Manager</span></span>
- <span data-ttu-id="40adf-193">HashiCorp Vault</span><span class="sxs-lookup"><span data-stu-id="40adf-193">HashiCorp Vault</span></span>

> [!IMPORTANT]
> <span data-ttu-id="40adf-194">環境変数とローカル ファイル コンポーネントは、開発ワークロード専用に設計されています。</span><span class="sxs-lookup"><span data-stu-id="40adf-194">The environment variables and local file components are designed for development workloads only.</span></span>

<span data-ttu-id="40adf-195">次のセクションでは、シークレット ストアを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="40adf-195">The following sections show how to configure a secret store.</span></span>

### <a name="configuration"></a><span data-ttu-id="40adf-196">構成</span><span class="sxs-lookup"><span data-stu-id="40adf-196">Configuration</span></span>

<span data-ttu-id="40adf-197">シークレット ストアは、Dapr コンポーネント構成ファイルを使用して構成します。</span><span class="sxs-lookup"><span data-stu-id="40adf-197">You configure a secret store using a Dapr component configuration file.</span></span> <span data-ttu-id="40adf-198">ファイルの一般的な構造を次に示します。</span><span class="sxs-lookup"><span data-stu-id="40adf-198">The typical structure of the file is shown below:</span></span>

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

<span data-ttu-id="40adf-199">すべての Dapr コンポーネント構成ファイルには、`name` とオプションの `namespace` 値が必要です。</span><span class="sxs-lookup"><span data-stu-id="40adf-199">All Dapr component configuration files require a `name` along with an optional `namespace` value.</span></span> <span data-ttu-id="40adf-200">また、`spec` セクションの `type` フィールドでは、シークレット ストア コンポーネントの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="40adf-200">Additionally, the `type` field in the `spec` section specifies the type of secret store component.</span></span> <span data-ttu-id="40adf-201">`metadata` セクションのプロパティは、シークレット ストアごとに異なります。</span><span class="sxs-lookup"><span data-stu-id="40adf-201">The properties in the `metadata` section differ per secret store.</span></span>

### <a name="indirectly-consume-dapr-secrets"></a><span data-ttu-id="40adf-202">Dapr シークレットを間接的に使用する</span><span class="sxs-lookup"><span data-stu-id="40adf-202">Indirectly consume Dapr secrets</span></span>

<span data-ttu-id="40adf-203">この章で既に説明したとおり、アプリケーションでシークレットを使用する方法として、コンポーネント構成ファイルでシークレットを参照することもできます。</span><span class="sxs-lookup"><span data-stu-id="40adf-203">As mentioned earlier in this chapter, applications can also consume secrets by referencing them in component configuration files.</span></span> <span data-ttu-id="40adf-204">Redis キャッシュを使用して状態を格納する[状態管理コンポーネント](state-management.md)について考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="40adf-204">Consider a [state management component](state-management.md) that uses Redis cache for storing state:</span></span>

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

<span data-ttu-id="40adf-205">上の構成ファイルには、Redis サーバーに接続するための **クリア テキスト** のパスワードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="40adf-205">The above configuration file contains a **clear-text** password for connecting to the Redis server.</span></span> <span data-ttu-id="40adf-206">**ハードコードされた** パスワードは常に不適切なアイデアです。</span><span class="sxs-lookup"><span data-stu-id="40adf-206">**Hardcoded** passwords are always a bad idea.</span></span> <span data-ttu-id="40adf-207">この構成ファイルをパブリック リポジトリにプッシュすると、パスワードが公開されます。</span><span class="sxs-lookup"><span data-stu-id="40adf-207">Pushing this configuration file to a public repository would expose the password.</span></span> <span data-ttu-id="40adf-208">シークレット ストアにパスワードを格納すると、このシナリオが大幅に改善されます。</span><span class="sxs-lookup"><span data-stu-id="40adf-208">Storing the password in a secret store would dramatically improve this scenario.</span></span>

<span data-ttu-id="40adf-209">次の例では、異なるいくつかのシークレット ストアを使用してこのことを実証します。</span><span class="sxs-lookup"><span data-stu-id="40adf-209">The following examples demonstrate this using several different secret stores.</span></span>

### <a name="local-file"></a><span data-ttu-id="40adf-210">ローカル ファイル</span><span class="sxs-lookup"><span data-stu-id="40adf-210">Local file</span></span>

<span data-ttu-id="40adf-211">ローカル ファイル コンポーネントは、開発シナリオ用に設計されています。</span><span class="sxs-lookup"><span data-stu-id="40adf-211">The local file component is designed for development scenarios.</span></span> <span data-ttu-id="40adf-212">これは、JSON ファイル内のローカル ファイル システムにシークレットを格納します。</span><span class="sxs-lookup"><span data-stu-id="40adf-212">It stores secrets on the local filesystem inside a JSON file.</span></span> <span data-ttu-id="40adf-213">`eshop-secrets.json` という名前のサンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="40adf-213">Here's an example named `eshop-secrets.json`.</span></span> <span data-ttu-id="40adf-214">これには、シークレットが 1 つ (Redis のパスワード) 含まれています。</span><span class="sxs-lookup"><span data-stu-id="40adf-214">It contains a single secret - a password for Redis:</span></span>

```json
{
  "eShopRedisPassword": "e$h0p0nD@pr"
}
```

<span data-ttu-id="40adf-215">このファイルは、Dapr アプリケーションの実行時に指定する `components` フォルダーに配置します。</span><span class="sxs-lookup"><span data-stu-id="40adf-215">You place this file in a `components` folder that you specify when running the Dapr application.</span></span>

<span data-ttu-id="40adf-216">次のシークレット ストア構成ファイルでは、シークレット ストアとして JSON ファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="40adf-216">The following secret store configuration file consumes the JSON file as a secret store.</span></span> <span data-ttu-id="40adf-217">これは `components` フォルダーにも配置されます。</span><span class="sxs-lookup"><span data-stu-id="40adf-217">It's also placed in the `components` folder:</span></span>

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

<span data-ttu-id="40adf-218">コンポーネントの種類は `secretstore.local.file` です。</span><span class="sxs-lookup"><span data-stu-id="40adf-218">The component type is `secretstore.local.file`.</span></span> <span data-ttu-id="40adf-219">`secretsFile` メタデータ要素は、シークレット ファイルへのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="40adf-219">The `secretsFile` metadata element specifies the path to the secrets file.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="40adf-220">シークレット ファイルへのパスとして、絶対パスまたは相対パスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="40adf-220">The path to a secrets file can be a absolute or relative path.</span></span> <span data-ttu-id="40adf-221">相対パスは、アプリケーションを起動するフォルダーを基準としています。</span><span class="sxs-lookup"><span data-stu-id="40adf-221">The relative path is based on the folder in which the application starts.</span></span> <span data-ttu-id="40adf-222">この例では、`components` フォルダーは、.NET アプリケーションが格納されているディレクトリのサブフォルダーです。</span><span class="sxs-lookup"><span data-stu-id="40adf-222">In the example, the `components` folder is a sub-folder of the directory that contains the .NET application.</span></span>

<span data-ttu-id="40adf-223">アプリケーション フォルダーから、コマンド ライン引数として `components` パスを指定して Dapr アプリケーションを起動します。</span><span class="sxs-lookup"><span data-stu-id="40adf-223">From the application folder, start the Dapr application specifying the `components` path as a command-line argument:</span></span>

```console
dapr run --app-id basket-api --components-path ./components dotnet run
```

> [!NOTE]
> <span data-ttu-id="40adf-224">上の例は、セルフホステッド モードでの Dapr の実行に適用されます。</span><span class="sxs-lookup"><span data-stu-id="40adf-224">This above example applies to running Dapr in self-hosted mode.</span></span> <span data-ttu-id="40adf-225">Kubernetes ホスティングの場合は、ボリューム マウントの使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="40adf-225">For Kubernetes hosting, consider using volume mounts.</span></span>

<span data-ttu-id="40adf-226">Dapr 構成ファイルの `nestedSeparator` は、JSON 階層を "*フラット化*" する文字を指定します。</span><span class="sxs-lookup"><span data-stu-id="40adf-226">The `nestedSeparator` in a Dapr configuration file specifies a character to *flatten* a JSON hierarchy.</span></span> <span data-ttu-id="40adf-227">次のスニペットについて考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="40adf-227">Consider the following snippet:</span></span>

```json
{
    "redisPassword": "some password",
    "connectionStrings": {
        "customerdb": "some connection string",
        "productdb": "some connection string"
    }
}
```

<span data-ttu-id="40adf-228">区切り記号としてコロンを使用すると、キー `connectionStrings:customerdb` を使用して `customerdb` 接続文字列を取得できます。</span><span class="sxs-lookup"><span data-stu-id="40adf-228">Using a colon as a separator, you can retrieve the `customerdb` connection-string using the key `connectionStrings:customerdb`.</span></span>

> [!NOTE]
> <span data-ttu-id="40adf-229">既定の区切り記号値はコロン (`:`) です。</span><span class="sxs-lookup"><span data-stu-id="40adf-229">The colon `:` is the default separator value.</span></span>

<span data-ttu-id="40adf-230">次の例では、状態管理構成ファイルがローカル シークレット ストア コンポーネントを参照し、Redis サーバーに接続するためのパスワードを取得します。</span><span class="sxs-lookup"><span data-stu-id="40adf-230">In the next example, a state management configuration file references the local secret store component to obtain the password for connecting to the Redis server:</span></span>

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

<span data-ttu-id="40adf-231">`secretKeyRef` 要素は、パスワードを含むシークレットを参照します。</span><span class="sxs-lookup"><span data-stu-id="40adf-231">The `secretKeyRef` element references the secret containing the password.</span></span> <span data-ttu-id="40adf-232">これにより、以前の "*クリア テキスト*" 値が置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="40adf-232">It replaces the earlier *clear-text* value.</span></span> <span data-ttu-id="40adf-233">シークレット名とキー名 (`eShopRedisPassword`) はシークレットを参照します。</span><span class="sxs-lookup"><span data-stu-id="40adf-233">The secret name and the key name, `eShopRedisPassword`, reference the secret.</span></span> <span data-ttu-id="40adf-234">シークレット管理コンポーネントの名前 (`eshop-local-secret-store`) は `auth` メタデータ要素にあります。</span><span class="sxs-lookup"><span data-stu-id="40adf-234">The name of the secret management component `eshop-local-secret-store` is found in the `auth` metadata element.</span></span>

<span data-ttu-id="40adf-235">シークレット参照の名前とキーがなぜ両方とも `eShopRedisPassword` であるかを不思議に思うかもしれません。</span><span class="sxs-lookup"><span data-stu-id="40adf-235">You might wonder why `eShopRedisPassword` is identical for both the name and key in the secret reference.</span></span> <span data-ttu-id="40adf-236">ローカル ファイル シークレット ストアでは、複数のシークレットが個別の名前で識別されません。</span><span class="sxs-lookup"><span data-stu-id="40adf-236">In the local file secret store, secrets aren't identified with a separate name.</span></span> <span data-ttu-id="40adf-237">このシナリオは、Kubernetes シークレットを使用する次の例では異なります。</span><span class="sxs-lookup"><span data-stu-id="40adf-237">The scenario will be different in the next example using Kubernetes secrets.</span></span>

### <a name="kubernetes-secret"></a><span data-ttu-id="40adf-238">Kubernetes シークレット</span><span class="sxs-lookup"><span data-stu-id="40adf-238">Kubernetes secret</span></span>

<span data-ttu-id="40adf-239">この 2 番目の例では、Kubernetes で実行される Dapr アプリケーションに焦点を当てています。</span><span class="sxs-lookup"><span data-stu-id="40adf-239">This second example focuses on a Dapr application running in Kubernetes.</span></span> <span data-ttu-id="40adf-240">この場合、Kubernetes が提供する標準のシークレット メカニズムが使用されます。</span><span class="sxs-lookup"><span data-stu-id="40adf-240">It uses the standard secrets mechanism that Kubernetes offers.</span></span> <span data-ttu-id="40adf-241">Kubernetes CLI (`kubectl`) を使用して、パスワードを含む `eshop-redis-secret` という名前のシークレットを作成します。</span><span class="sxs-lookup"><span data-stu-id="40adf-241">Use the Kubernetes CLI (`kubectl`) to create a secret named `eshop-redis-secret` that contains the password:</span></span>

```console
kubectl create secret generic eshopsecrets --from-literal=redisPassword=e$h0p0nD@pr -n eshop
```

<span data-ttu-id="40adf-242">作成が完了すると、状態管理用のコンポーネント構成ファイルでシークレットを参照できます。</span><span class="sxs-lookup"><span data-stu-id="40adf-242">Once created, you can reference the secret in the component configuration file for state management:</span></span>

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

<span data-ttu-id="40adf-243">`secretKeyRef` 要素は、Kubernetes シークレットの名前 (`eshopsecrets`) とシークレットのキー (`redisPassword`) をそれぞれ指定します。</span><span class="sxs-lookup"><span data-stu-id="40adf-243">The `secretKeyRef` element specifies the name of the Kubernetes secret and the secret's key, `eshopsecrets`, and `redisPassword` respectively.</span></span> <span data-ttu-id="40adf-244">`auth` メタデータ セクションでは、Kubernetes シークレット管理コンポーネントを使用するように Dapr に指示します。</span><span class="sxs-lookup"><span data-stu-id="40adf-244">The `auth` metadata section instructs Dapr to use the Kubernetes secrets management component.</span></span>

> [!NOTE]
> <span data-ttu-id="40adf-245">Kubernetes シークレットを使用する場合は、auth が既定値です。この値は省略できます。</span><span class="sxs-lookup"><span data-stu-id="40adf-245">Auth is the default value when using Kubernetes secrets and can be omitted.</span></span>

<span data-ttu-id="40adf-246">運用環境の設定では、通常、シークレットは自動 CI/CD パイプラインの一部として作成されます。</span><span class="sxs-lookup"><span data-stu-id="40adf-246">In a production setting, secrets are typically created as part of an automated CI/CD pipeline.</span></span> <span data-ttu-id="40adf-247">これで、十分なアクセス許可を持つユーザーだけがシークレットにアクセスしたり、シークレットを変更したりできるようになります。</span><span class="sxs-lookup"><span data-stu-id="40adf-247">Doing so ensures only people with sufficient permissions can access and change the secrets.</span></span> <span data-ttu-id="40adf-248">開発者は、シークレットの実際の値を把握せずに構成ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="40adf-248">Developers create configuration files without knowing the actual value of the secrets.</span></span>

### <a name="azure-key-vault"></a><span data-ttu-id="40adf-249">Azure Key Vault</span><span class="sxs-lookup"><span data-stu-id="40adf-249">Azure Key Vault</span></span>

<span data-ttu-id="40adf-250">次の例は、実際の運用環境のシナリオを対象としています。</span><span class="sxs-lookup"><span data-stu-id="40adf-250">The next example is geared toward a real-world production scenario.</span></span> <span data-ttu-id="40adf-251">シークレット ストアとして **Azure Key Vault** が使用されます。</span><span class="sxs-lookup"><span data-stu-id="40adf-251">It uses **Azure Key Vault** as the secret store.</span></span> <span data-ttu-id="40adf-252">Azure Key Vault は、シークレットを安全にクラウドに格納できるようにするマネージド Azure サービスです。</span><span class="sxs-lookup"><span data-stu-id="40adf-252">Azure Key Vault is a managed Azure service that enables secrets to be stored securely in the cloud.</span></span>

<span data-ttu-id="40adf-253">この例を使用するには、次の前提条件を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="40adf-253">For this example to work, the following prerequisites must be satisfied:</span></span>

- <span data-ttu-id="40adf-254">Azure サブスクリプションへの管理アクセスがセキュリティで保護されている。</span><span class="sxs-lookup"><span data-stu-id="40adf-254">You've secured administrative access to an Azure subscription.</span></span>
- <span data-ttu-id="40adf-255">Redis サーバーに接続するためのパスワードを含むシークレット (`redisPassword`) を保持する Azure Key Vault (`eshopkv`) がプロビジョニングされている。</span><span class="sxs-lookup"><span data-stu-id="40adf-255">You've provisioned an Azure Key Vault named `eshopkv` that holds a secret named `redisPassword` that contains the password for connecting to the Redis server.</span></span>
- <span data-ttu-id="40adf-256">Azure Active Directory で[サービス プリンシパル](/azure/active-directory/develop/howto-create-service-principal-portal)が作成されている。</span><span class="sxs-lookup"><span data-stu-id="40adf-256">You've created [service principal](/azure/active-directory/develop/howto-create-service-principal-portal) in Azure Active Directory.</span></span>
- <span data-ttu-id="40adf-257">このサービス プリンシパルの X509 証明書 (公開キーと秘密キーの両方を含む) がローカル ファイル システムにインストールされている。</span><span class="sxs-lookup"><span data-stu-id="40adf-257">You've installed an X509 certificate for this service principal (containing both the public and private key) on the local filesystem.</span></span>

> [!NOTE]
> <span data-ttu-id="40adf-258">サービス プリンシパルは、アプリケーションが Azure サービスを認証するために使用できる ID です。</span><span class="sxs-lookup"><span data-stu-id="40adf-258">A service principal is an identity that can be used by an application to authenticate an Azure service.</span></span> <span data-ttu-id="40adf-259">サービス プリンシパルでは X509 証明書を使用します。</span><span class="sxs-lookup"><span data-stu-id="40adf-259">The service principal uses a X509 certificate.</span></span> <span data-ttu-id="40adf-260">アプリケーションでは、資格情報としてこの証明書を使用して自身を認証します。</span><span class="sxs-lookup"><span data-stu-id="40adf-260">The application uses this certificate as a credential to authenticate itself.</span></span>

<span data-ttu-id="40adf-261">[Dapr Azure Key Vault シークレット ストアのドキュメント](https://docs.dapr.io/operations/components/setup-secret-store/supported-secret-stores/azure-keyvault/)では、Key Vault 環境を作成および構成するための詳細な手順について説明しています。</span><span class="sxs-lookup"><span data-stu-id="40adf-261">The [Dapr Azure Key Vault secret store documentation](https://docs.dapr.io/operations/components/setup-secret-store/supported-secret-stores/azure-keyvault/) provides step-by-step instructions to create and configure a Key Vault environment.</span></span>

#### <a name="use-key-vault-when-running-in-self-hosted-mode"></a><span data-ttu-id="40adf-262">セルフホステッド モードでの実行時に Key Vault を使用する</span><span class="sxs-lookup"><span data-stu-id="40adf-262">Use Key Vault when running in self-hosted mode</span></span>

<span data-ttu-id="40adf-263">Dapr のセルフホステッド モードで Azure Key Vault を使用するには、次の構成ファイルが必要です。</span><span class="sxs-lookup"><span data-stu-id="40adf-263">Consuming Azure Key Vault in Dapr self-hosted mode requires the following configuration file:</span></span>

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

<span data-ttu-id="40adf-264">シークレット ストアの種類は `secretstores.azure.keyvault` です。</span><span class="sxs-lookup"><span data-stu-id="40adf-264">The secret store type is `secretstores.azure.keyvault`.</span></span> <span data-ttu-id="40adf-265">Key Vault へのアクセスを構成する `metadata` 要素には次のプロパティが必要です。</span><span class="sxs-lookup"><span data-stu-id="40adf-265">The `metadata` element to configure access to Key Vault requires the following properties:</span></span>

- <span data-ttu-id="40adf-266">`vaultName` には、Azure Key Vault の名前が含まれています。</span><span class="sxs-lookup"><span data-stu-id="40adf-266">The `vaultName` contains the name of the Azure Key Vault.</span></span>
- <span data-ttu-id="40adf-267">`spnTenantId` には、Key Vault に対する認証に使用されるサービス プリンシパルの "*テナント ID*" が含まれています。</span><span class="sxs-lookup"><span data-stu-id="40adf-267">The `spnTenantId` contains the *tenant ID* of the service principal used to authenticate against the Key Vault.</span></span>
- <span data-ttu-id="40adf-268">`spnClientId` には、Key Vault に対する認証に使用されるサービス プリンシパルの "*アプリ ID*" が含まれています。</span><span class="sxs-lookup"><span data-stu-id="40adf-268">The `spnClientId` contains the *app ID* of the service principal used to authenticate against the Key Vault.</span></span>
- <span data-ttu-id="40adf-269">`spnCertificateFile` には、Key Vault に対する認証のためのサービス プリンシパルの証明書ファイル名へのパスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="40adf-269">The `spnCertificateFile` contains the path to the certificate file for the service principal to authenticate against the Key Vault.</span></span>

> [!TIP]
> <span data-ttu-id="40adf-270">サービス プリンシパル情報は、Azure portal または Azure CLI からコピーできます。</span><span class="sxs-lookup"><span data-stu-id="40adf-270">You can copy the service principal information from the Azure portal or Azure CLI .</span></span>

<span data-ttu-id="40adf-271">これで、アプリケーションが Azure Key Vault から Redis パスワードを取得できます。</span><span class="sxs-lookup"><span data-stu-id="40adf-271">Now the application can retrieve the Redis password from the Azure Key Vault.</span></span>

#### <a name="use-key-vault-when-running-on-kubernetes"></a><span data-ttu-id="40adf-272">Kubernetes での実行時に Key Vault を使用する</span><span class="sxs-lookup"><span data-stu-id="40adf-272">Use Key Vault when running on Kubernetes</span></span>

<span data-ttu-id="40adf-273">Azure Key Vault を Dapr と Kubernetes で使用するには、Azure Key Vault に対する認証のためのサービス プリンシパルも必要です。</span><span class="sxs-lookup"><span data-stu-id="40adf-273">Consuming Azure Key Vault with Dapr and Kubernetes also requires a service principal to authenticate against the Azure Key Vault.</span></span>

<span data-ttu-id="40adf-274">最初に、kubectl CLI ツールを使用して証明書ファイルを含む "*Kubernetes シークレット*" を作成します。</span><span class="sxs-lookup"><span data-stu-id="40adf-274">First, create a *Kubernetes secret* that contains a certificate file using the kubectl CLI tool:</span></span>

```console
kubectl create secret generic [k8s_spn_secret_name] --from-file=[pfx_certificate_file_local_path] -n eshop
```

<span data-ttu-id="40adf-275">このコマンドには、次の 2 つのコマンド ライン引数が必要です。</span><span class="sxs-lookup"><span data-stu-id="40adf-275">The command requires two command-line arguments:</span></span>

- <span data-ttu-id="40adf-276">`[k8s_spn_secret_name]` は、Kubernetes シークレット ストア内のシークレット名です。</span><span class="sxs-lookup"><span data-stu-id="40adf-276">`[k8s_spn_secret_name]` is the secret name in Kubernetes secret store.</span></span>
- <span data-ttu-id="40adf-277">`[pfx_certificate_file_local_path]` は、X509 証明書ファイルのパスです。</span><span class="sxs-lookup"><span data-stu-id="40adf-277">`[pfx_certificate_file_local_path]` is the path of X509 certificate file.</span></span>

<span data-ttu-id="40adf-278">作成が完了すると、シークレット ストア コンポーネント構成ファイルで Kubernetes シークレットを参照できます。</span><span class="sxs-lookup"><span data-stu-id="40adf-278">Once created, you can reference the Kubernetes secret in the secret store component configuration file:</span></span>

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

<span data-ttu-id="40adf-279">この時点で、Kubernetes で実行されているアプリケーションは、Azure Key Vault から Redis パスワードを取得できます。</span><span class="sxs-lookup"><span data-stu-id="40adf-279">At this point, an application running in Kubernetes can retrieve the Redis password from the Azure Key Vault.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="40adf-280">サービス プリンシパルの X509 証明書ファイルを安全な場所に保管することが重要です。</span><span class="sxs-lookup"><span data-stu-id="40adf-280">It's critical to keep the X509 certificate file for the service principal in a safe place.</span></span> <span data-ttu-id="40adf-281">ソース コード リポジトリの外部にある既知のフォルダーに配置することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="40adf-281">It's best to place it in a well-known folder outside the source-code repository.</span></span> <span data-ttu-id="40adf-282">これで、構成ファイルがこの既知のフォルダーから証明書ファイルを参照できます。</span><span class="sxs-lookup"><span data-stu-id="40adf-282">The configuration file can then reference the certificate file from this well-known folder.</span></span> <span data-ttu-id="40adf-283">ローカルの開発マシンでは、ユーザーが証明書をこのフォルダーにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="40adf-283">On a local development machine, you're responsible for copying the certificate to the folder.</span></span> <span data-ttu-id="40adf-284">自動デプロイの場合は、パイプラインによって、アプリケーションがデプロイされているマシンに証明書がコピーされます。</span><span class="sxs-lookup"><span data-stu-id="40adf-284">For automated deployments, the pipeline will copy the certificate to the machine where the application is deployed.</span></span> <span data-ttu-id="40adf-285">環境ごとに異なるサービス プリンシパルを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="40adf-285">It's a best practice to use a different service principal per environment.</span></span> <span data-ttu-id="40adf-286">これにより、開発環境のサービス プリンシパルが運用環境のシークレットにアクセスできなくなります。</span><span class="sxs-lookup"><span data-stu-id="40adf-286">Doing so prevents the service principal from a DEVELOPMENT environment to access secrets in a PRODUCTION environment.</span></span>

<span data-ttu-id="40adf-287">Azure Kubernetes Service (AKS) での実行時には、[Azure マネージド ID](/azure/active-directory/managed-identities-azure-resources/overview) を使用して Azure Key Vault に対する認証を行うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="40adf-287">When running in  Azure Kubernetes Service (AKS), it's preferable to use an [Azure Managed Identity](/azure/active-directory/managed-identities-azure-resources/overview) for authenticating against Azure Key Vault.</span></span> <span data-ttu-id="40adf-288">マネージド ID については本書では説明しません。[Azure Key Vault でマネージド ID を使用する方法](https://docs.dapr.io/operations/components/setup-secret-store/supported-secret-stores/azure-keyvault-managed-identity/)に関するドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="40adf-288">Managed identities are outside of the scope of this book, but explained in the [Azure Key Vault with managed identities](https://docs.dapr.io/operations/components/setup-secret-store/supported-secret-stores/azure-keyvault-managed-identity/) documentation.</span></span>

### <a name="scope-secrets"></a><span data-ttu-id="40adf-289">シークレットのスコープを指定する</span><span class="sxs-lookup"><span data-stu-id="40adf-289">Scope secrets</span></span>

<span data-ttu-id="40adf-290">シークレットのスコープを使用すると、アプリケーションがアクセスできるシークレットを制御できます。</span><span class="sxs-lookup"><span data-stu-id="40adf-290">Secret scopes allow you to control which secrets your application can access.</span></span> <span data-ttu-id="40adf-291">スコープは、Dapr サイドカー構成ファイルで構成します。</span><span class="sxs-lookup"><span data-stu-id="40adf-291">You configure scopes in a Dapr sidecar configuration file.</span></span> <span data-ttu-id="40adf-292">[Dapr の構成に関するドキュメント](https://docs.dapr.io/operations/configuration/configuration-overview/)では、シークレットのスコープを指定する手順について説明しています。</span><span class="sxs-lookup"><span data-stu-id="40adf-292">The [Dapr configuration documentation](https://docs.dapr.io/operations/configuration/configuration-overview/) provides instructions for scoping secrets.</span></span>

<span data-ttu-id="40adf-293">シークレットのスコープを含む Dapr サイドカー構成ファイルの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="40adf-293">Here's an example of a Dapr sidecar configuration file that contains secret scopes:</span></span>

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

<span data-ttu-id="40adf-294">スコープはシークレット ストアごとに指定します。</span><span class="sxs-lookup"><span data-stu-id="40adf-294">You specify scopes per secret store.</span></span> <span data-ttu-id="40adf-295">上の例では、シークレット ストアに `eshop-azurekv-secret-store` という名前が付けられています。</span><span class="sxs-lookup"><span data-stu-id="40adf-295">In the above example, the secret store is named `eshop-azurekv-secret-store`.</span></span> <span data-ttu-id="40adf-296">シークレットへのアクセスを構成するには、次のプロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="40adf-296">You configure access to secrets using the following properties:</span></span>

| <span data-ttu-id="40adf-297">プロパティ</span><span class="sxs-lookup"><span data-stu-id="40adf-297">Property</span></span>         | <span data-ttu-id="40adf-298">値</span><span class="sxs-lookup"><span data-stu-id="40adf-298">Value</span></span>               | <span data-ttu-id="40adf-299">説明</span><span class="sxs-lookup"><span data-stu-id="40adf-299">Description</span></span>                                                                                                                       |
|------------------|---------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| `defaultAccess`  | <span data-ttu-id="40adf-300">`allow` または `deny`</span><span class="sxs-lookup"><span data-stu-id="40adf-300">`allow` or `deny`</span></span>   | <span data-ttu-id="40adf-301">指定されたシークレット ストア内の "*すべて*" のシークレットへのアクセスを許可または拒否します。</span><span class="sxs-lookup"><span data-stu-id="40adf-301">Allows or denies access to *all* secrets in the specified secret store.</span></span> <span data-ttu-id="40adf-302">このプロパティは省略可能であり、既定値は `allow` です。</span><span class="sxs-lookup"><span data-stu-id="40adf-302">This property is optional with a default value of `allow`.</span></span> |
| `allowedSecrets` | <span data-ttu-id="40adf-303">シークレット キーのリスト</span><span class="sxs-lookup"><span data-stu-id="40adf-303">List of secret keys</span></span> | <span data-ttu-id="40adf-304">配列に指定されたシークレットにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="40adf-304">Secrets specified in the array will be accessible.</span></span> <span data-ttu-id="40adf-305">このプロパティは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="40adf-305">This property is optional.</span></span>                                                     |
| `deniedSecrets`  | <span data-ttu-id="40adf-306">シークレット キーのリスト</span><span class="sxs-lookup"><span data-stu-id="40adf-306">List of secret keys</span></span> | <span data-ttu-id="40adf-307">配列に指定されたシークレットにはアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="40adf-307">Secrets specified in the array will NOT be accessible.</span></span> <span data-ttu-id="40adf-308">このプロパティは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="40adf-308">This property is optional.</span></span>                                                 |

<span data-ttu-id="40adf-309">`allowedSecrets` プロパティと `deniedSecrets` プロパティは `defaultAccess` プロパティよりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="40adf-309">The `allowedSecrets` and `deniedSecrets` properties take precedence over the `defaultAccess` property.</span></span> <span data-ttu-id="40adf-310">`defaultAccess: allowed` と `allowedSecrets` リストを指定すると想像してください。</span><span class="sxs-lookup"><span data-stu-id="40adf-310">Imagine specifying `defaultAccess: allowed` and an `allowedSecrets` list.</span></span> <span data-ttu-id="40adf-311">この場合、アプリケーションからアクセスできるのは `allowedSecrets` リスト内のシークレットだけです。</span><span class="sxs-lookup"><span data-stu-id="40adf-311">In this case, only the secrets in the `allowedSecrets` list would be accessible by the application.</span></span>

## <a name="reference-application-eshopondapr"></a><span data-ttu-id="40adf-312">参照アプリケーション: eShopOnDapr</span><span class="sxs-lookup"><span data-stu-id="40adf-312">Reference application: eShopOnDapr</span></span>

<span data-ttu-id="40adf-313">eShopOnDapr 参照アプリケーションでは、次に示す 2 つのシークレットに対してシークレット ビルディング ブロックを使用します。</span><span class="sxs-lookup"><span data-stu-id="40adf-313">The eShopOnDapr reference application uses the secrets building block for two secrets:</span></span>

- <span data-ttu-id="40adf-314">Redis キャッシュに接続するためのパスワード。</span><span class="sxs-lookup"><span data-stu-id="40adf-314">The password for connecting to the Redis cache.</span></span>
- <span data-ttu-id="40adf-315">Twilio Sendgrid API を使用するための API キー。</span><span class="sxs-lookup"><span data-stu-id="40adf-315">The API-key for using the Twilio Sendgrid API.</span></span> <span data-ttu-id="40adf-316">このアプリケーションでは、Twilio を使用して、Dapr 出力バインディングによって電子メールを送信します ([バインディング ビルディング ブロックに関する章](bindings.md)を参照)。</span><span class="sxs-lookup"><span data-stu-id="40adf-316">The application uses Twillio to send emails using a Dapr output binding (as described in the [bindings building block chapter](bindings.md)).</span></span>

<span data-ttu-id="40adf-317">Docker Compose を使用してアプリケーションを実行する場合は、**ローカル ファイル** シークレット ストアが使用されます。</span><span class="sxs-lookup"><span data-stu-id="40adf-317">When running the application using Docker Compose, the **local file** secret store is used.</span></span> <span data-ttu-id="40adf-318">コンポーネント構成ファイル `eshop-secretstore.yaml` は、eShopOnDapr リポジトリの `dapr/components` フォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="40adf-318">The component configuration file `eshop-secretstore.yaml` is found in the `dapr/components` folder of the eShopOnDapr repository:</span></span>

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

<span data-ttu-id="40adf-319">この構成ファイルは、同じフォルダーにあるローカル ストア ファイル `eshop-secretstore.json` を参照します。</span><span class="sxs-lookup"><span data-stu-id="40adf-319">The configuration file references the local store file `eshop-secretstore.json` located in the same folder:</span></span>

```json
{
    "redisPassword": "**********",
    "sendgridAPIKey": "**********"
}
```

<span data-ttu-id="40adf-320">`components` フォルダーはコマンド ラインで指定され、Dapr サイドカー コンテナー内にローカル フォルダーとしてマウントされます。</span><span class="sxs-lookup"><span data-stu-id="40adf-320">The `components` folder is specified in the command-line and mounted as a local folder inside the Dapr sidecar container.</span></span> <span data-ttu-id="40adf-321">ボリューム マウントを指定するリポジトリ ルート内の `docker-compose.override.yml` ファイルのスニペットを次に示します。</span><span class="sxs-lookup"><span data-stu-id="40adf-321">Here's a snippet from the `docker-compose.override.yml` file in the repository root that specifies the volume mount:</span></span>

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
> <span data-ttu-id="40adf-322">Docker Compose オーバーライド ファイルには、環境固有の構成値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="40adf-322">The Docker Compose override file contains environmental specific configuration values.</span></span>

<span data-ttu-id="40adf-323">`/components` ボリューム マウントと `--components-path` コマンド ライン引数は、`daprd` スタートアップ コマンドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="40adf-323">The `/components` volume mount and `--components-path` command-line argument are passed into the `daprd` startup command.</span></span>

<span data-ttu-id="40adf-324">構成が完了すると、他のコンポーネント構成ファイルでもシークレットを参照できます。</span><span class="sxs-lookup"><span data-stu-id="40adf-324">Once configured, other component configuration files can also reference the secrets.</span></span> <span data-ttu-id="40adf-325">シークレットを使用するパブリッシュ/サブスクライブ コンポーネント構成の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="40adf-325">Here's an example of the Publish/Subscribe component configuration consuming secrets:</span></span>

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

<span data-ttu-id="40adf-326">上の例では、シークレットを参照するためにローカルの Redis ストアが使用されます。</span><span class="sxs-lookup"><span data-stu-id="40adf-326">In the preceding example, the local Redis store is used to reference secrets.</span></span>

## <a name="summary"></a><span data-ttu-id="40adf-327">まとめ</span><span class="sxs-lookup"><span data-stu-id="40adf-327">Summary</span></span>

<span data-ttu-id="40adf-328">Dapr シークレット ビルディング ブロックは、パスワードや接続文字列などの機密構成設定を格納および取得する機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="40adf-328">The Dapr secrets building block provides capabilities for storing and retrieving sensitive configuration settings like passwords and connection-strings.</span></span> <span data-ttu-id="40adf-329">シークレットは機密として扱われ、誤って公開されることはありません。</span><span class="sxs-lookup"><span data-stu-id="40adf-329">It keeps secrets private and prevents them from being accidentally disclosed.</span></span>

<span data-ttu-id="40adf-330">このビルディング ブロックでは、異なるいくつかのシークレット ストアがサポートされており、Dapr シークレット API によってその複雑さが隠されています。</span><span class="sxs-lookup"><span data-stu-id="40adf-330">The building block supports several different secret stores and hides their complexity with the Dapr secrets API.</span></span>

<span data-ttu-id="40adf-331">Dapr .NET SDK には、シークレットを取得するための `DaprClient` オブジェクトが用意されています。</span><span class="sxs-lookup"><span data-stu-id="40adf-331">The Dapr .NET SDK provides a `DaprClient` object to retrieve secrets.</span></span> <span data-ttu-id="40adf-332">また、.NET Core 構成システムにシークレットを追加する .NET 構成プロバイダーも含まれています。</span><span class="sxs-lookup"><span data-stu-id="40adf-332">It also includes a .NET configuration provider that adds secrets to the .NET Core configuration system.</span></span> <span data-ttu-id="40adf-333">読み込みが完了すると、これらのシークレットを .NET コードで使用できます。</span><span class="sxs-lookup"><span data-stu-id="40adf-333">Once loaded, you can consume these secrets in your .NET code.</span></span>

<span data-ttu-id="40adf-334">シークレットのスコープを使用すると、特定のシークレットへのアクセスを制御できます。</span><span class="sxs-lookup"><span data-stu-id="40adf-334">You can use secret scopes to control access to specific secrets.</span></span>

## <a name="references"></a><span data-ttu-id="40adf-335">リファレンス</span><span class="sxs-lookup"><span data-stu-id="40adf-335">References</span></span>

- [<span data-ttu-id="40adf-336">Beyond the Twelve-Factor Application (Beyond the Twelve-Factor App)</span><span class="sxs-lookup"><span data-stu-id="40adf-336">Beyond the Twelve-Factor Application</span></span>](https://tanzu.vmware.com/content/blog/beyond-the-twelve-factor-app)

>[!div class="step-by-step"]
><span data-ttu-id="40adf-337">[前へ](observability.md)
>[次へ](summary.md)</span><span class="sxs-lookup"><span data-stu-id="40adf-337">[Previous](observability.md)
[Next](summary.md)</span></span>
