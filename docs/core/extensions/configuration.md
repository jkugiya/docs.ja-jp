---
title: .NET での構成
description: 構成 API を使用して、.NET アプリケーションを構成する方法を説明します。
author: IEvangelist
ms.author: dapine
ms.date: 09/16/2020
ms.topic: overview
ms.openlocfilehash: 5955e46c2f5acb6776ada4e3fd6a65507d3faa1f
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2020
ms.locfileid: "102402024"
---
# <a name="configuration-in-net"></a><span data-ttu-id="c2802-103">.NET での構成</span><span class="sxs-lookup"><span data-stu-id="c2802-103">Configuration in .NET</span></span>

<span data-ttu-id="c2802-104">.NET での構成は、1 つまたは複数の[構成プロバイダー](#configuration-providers)を使用して実行されます。</span><span class="sxs-lookup"><span data-stu-id="c2802-104">Configuration in .NET is performed using one or more [configuration providers](#configuration-providers).</span></span> <span data-ttu-id="c2802-105">構成プロバイダーは、以下のようなさまざまな構成ソースを使用して、キーと値のペアから構成データを読み取ります:</span><span class="sxs-lookup"><span data-stu-id="c2802-105">Configuration providers read configuration data from key-value pairs using a variety of configuration sources:</span></span>

- <span data-ttu-id="c2802-106">*appsettings.json* などの設定ファイル</span><span class="sxs-lookup"><span data-stu-id="c2802-106">Settings files, such as *appsettings.json*</span></span>
- <span data-ttu-id="c2802-107">環境変数</span><span class="sxs-lookup"><span data-stu-id="c2802-107">Environment variables</span></span>
- [<span data-ttu-id="c2802-108">Azure Key Vault</span><span class="sxs-lookup"><span data-stu-id="c2802-108">Azure Key Vault</span></span>](/azure/key-vault/general/overview)
- [<span data-ttu-id="c2802-109">Azure App Configuration</span><span class="sxs-lookup"><span data-stu-id="c2802-109">Azure App Configuration</span></span>](/azure/azure-app-configuration/overview)
- <span data-ttu-id="c2802-110">コマンド ライン引数</span><span class="sxs-lookup"><span data-stu-id="c2802-110">Command-line arguments</span></span>
- <span data-ttu-id="c2802-111">インストール済みまたは作成済みのカスタム プロバイダー</span><span class="sxs-lookup"><span data-stu-id="c2802-111">Custom providers, installed or created</span></span>
- <span data-ttu-id="c2802-112">ディレクトリ ファイル</span><span class="sxs-lookup"><span data-stu-id="c2802-112">Directory files</span></span>
- <span data-ttu-id="c2802-113">メモリ内 .NET オブジェクト</span><span class="sxs-lookup"><span data-stu-id="c2802-113">In-memory .NET objects</span></span>

## <a name="configure-console-apps"></a><span data-ttu-id="c2802-114">コンソール アプリの構成</span><span class="sxs-lookup"><span data-stu-id="c2802-114">Configure console apps</span></span>

<span data-ttu-id="c2802-115">既定で [dotnet new](../tools/dotnet-new.md) または Visual Studio を使用して作成された新しい .NET コンソール アプリケーションでは、構成機能は公開 "*されません*"。</span><span class="sxs-lookup"><span data-stu-id="c2802-115">New .NET console applications created using [dotnet new](../tools/dotnet-new.md) or Visual Studio by default *do not* expose configuration capabilities.</span></span> <span data-ttu-id="c2802-116">新しい .NET コンソール アプリケーションで構成を追加するには、`Microsoft.Extensions.Hosting` に[パッケージ参照を追加](../tools/dotnet-add-package.md)します。</span><span class="sxs-lookup"><span data-stu-id="c2802-116">To add configuration in a new .NET console application, [add a package reference](../tools/dotnet-add-package.md) to `Microsoft.Extensions.Hosting`.</span></span> <span data-ttu-id="c2802-117">*Program.cs* ファイルを次のコードに一致するように変更します。</span><span class="sxs-lookup"><span data-stu-id="c2802-117">Modify the *Program.cs* file to match the following code:</span></span>

:::code language="csharp" source="snippets/configuration/console/Program.cs" highlight="18":::

<span data-ttu-id="c2802-118"><xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder(System.String[])?displayProperty=nameWithType> メソッドにより、次の順序でアプリの既定の構成が提供されます。</span><span class="sxs-lookup"><span data-stu-id="c2802-118">The <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder(System.String[])?displayProperty=nameWithType> method provides default configuration for the app in the following order:</span></span>

1. <span data-ttu-id="c2802-119">[ChainedConfigurationProvider](xref:Microsoft.Extensions.Configuration.ChainedConfigurationSource): 既存の `IConfiguration` をソースとして追加します。</span><span class="sxs-lookup"><span data-stu-id="c2802-119">[ChainedConfigurationProvider](xref:Microsoft.Extensions.Configuration.ChainedConfigurationSource) : Adds an existing `IConfiguration` as a source.</span></span>
1. <span data-ttu-id="c2802-120">[JSON 構成プロバイダー](configuration-providers.md#file-configuration-provider)を使用する *appsettings.json*。</span><span class="sxs-lookup"><span data-stu-id="c2802-120">*appsettings.json* using the [JSON configuration provider](configuration-providers.md#file-configuration-provider).</span></span>
1. <span data-ttu-id="c2802-121">[JSON 構成プロバイダー](configuration-providers.md#file-configuration-provider)を使用する *appsettings.* `Environment`*json*。</span><span class="sxs-lookup"><span data-stu-id="c2802-121">*appsettings.*`Environment`*.json* using the [JSON configuration provider](configuration-providers.md#file-configuration-provider).</span></span> <span data-ttu-id="c2802-122">たとえば、*appsettings*.***Production\*\*_._json* および *appsettings*.\*\*\*Development** _._json\*。</span><span class="sxs-lookup"><span data-stu-id="c2802-122">For example, *appsettings*.***Production\*\*_._json* and *appsettings*.\*\*\*Development** _._json\*.</span></span>
1. <span data-ttu-id="c2802-123">`Development` 環境でアプリが実行される際の App シークレット。</span><span class="sxs-lookup"><span data-stu-id="c2802-123">App secrets when the app runs in the `Development` environment.</span></span>
1. <span data-ttu-id="c2802-124">[環境変数構成プロバイダー](configuration-providers.md#environment-variable-configuration-provider)を使用する環境変数。</span><span class="sxs-lookup"><span data-stu-id="c2802-124">Environment variables using the [Environment Variables configuration provider](configuration-providers.md#environment-variable-configuration-provider).</span></span>
1. <span data-ttu-id="c2802-125">[コマンドライン構成プロバイダー](configuration-providers.md#command-line-configuration-provider)を使用するコマンドライン引数。</span><span class="sxs-lookup"><span data-stu-id="c2802-125">Command-line arguments using the [Command-line configuration provider](configuration-providers.md#command-line-configuration-provider).</span></span>

<span data-ttu-id="c2802-126">後から追加される構成プロバイダーは、それ以前のキー設定をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="c2802-126">Configuration providers that are added later override previous key settings.</span></span> <span data-ttu-id="c2802-127">たとえば、`SomeKey` が *appsettings.json* と環境の両方で設定されている場合、環境の値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="c2802-127">For example, if `SomeKey` is set in both *appsettings.json* and the environment, the environment value is used.</span></span> <span data-ttu-id="c2802-128">既定の構成プロバイダーを使用すると、[コマンドライン構成プロバイダー](configuration-providers.md#command-line-configuration-provider)によって他のすべてのプロバイダーがオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="c2802-128">Using the default configuration providers, the [Command-line configuration provider](configuration-providers.md#command-line-configuration-provider) overrides all other providers.</span></span>

### <a name="binding"></a><span data-ttu-id="c2802-129">バインド</span><span class="sxs-lookup"><span data-stu-id="c2802-129">Binding</span></span>

<span data-ttu-id="c2802-130">.NET での構成の主な利点の 1 つは、構成値を .NET オブジェクトのインスタンスにバインドする機能です。</span><span class="sxs-lookup"><span data-stu-id="c2802-130">One of the key advantages to configuration in .NET is the ability to bind configuration values to instances of .NET objects.</span></span> <span data-ttu-id="c2802-131">たとえば、JSON 構成プロバイダーは、*appsettings.json* ファイルを .NET オブジェクトにマップするのに使用でき、依存関係の挿入で使用されます。</span><span class="sxs-lookup"><span data-stu-id="c2802-131">For example, the JSON configuration provider can be used to map *appsettings.json* files to .NET objects and is used with dependency injection.</span></span> <span data-ttu-id="c2802-132">これによりオプション パターンが有効になります。オプション パターンは、クラスを使用して、関連する設定のグループに厳密に型指定されたアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="c2802-132">This enables the options pattern, the options pattern uses classes to provide strongly typed access to groups of related settings.</span></span>

## <a name="configuration-providers"></a><span data-ttu-id="c2802-133">構成プロバイダー</span><span class="sxs-lookup"><span data-stu-id="c2802-133">Configuration providers</span></span>

<span data-ttu-id="c2802-134">.NET Core アプリで使用できる構成プロバイダーを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="c2802-134">The following table shows the configuration providers available to .NET Core apps.</span></span>

| <span data-ttu-id="c2802-135">プロバイダー</span><span class="sxs-lookup"><span data-stu-id="c2802-135">Provider</span></span>                                                                                                               | <span data-ttu-id="c2802-136">以下から構成を提供します</span><span class="sxs-lookup"><span data-stu-id="c2802-136">Provides configuration from</span></span>        |
|------------------------------------------------------------------------------------------------------------------------|------------------------------------|
| [<span data-ttu-id="c2802-137">Azure App Configuration プロバイダー</span><span class="sxs-lookup"><span data-stu-id="c2802-137">Azure App configuration provider</span></span>](/azure/azure-app-configuration/quickstart-aspnet-core-app)                          | <span data-ttu-id="c2802-138">Azure App Configuration</span><span class="sxs-lookup"><span data-stu-id="c2802-138">Azure App Configuration</span></span>            |
| [<span data-ttu-id="c2802-139">Azure Key Vault 構成プロバイダー</span><span class="sxs-lookup"><span data-stu-id="c2802-139">Azure Key Vault configuration provider</span></span>](/azure/key-vault/general/tutorial-net-virtual-machine)                        | <span data-ttu-id="c2802-140">Azure Key Vault</span><span class="sxs-lookup"><span data-stu-id="c2802-140">Azure Key Vault</span></span>                    |
| [<span data-ttu-id="c2802-141">コマンド ライン構成プロバイダー</span><span class="sxs-lookup"><span data-stu-id="c2802-141">Command-line configuration provider</span></span>](configuration-providers.md#command-line-configuration-provider)                  | <span data-ttu-id="c2802-142">コマンド ライン パラメーター</span><span class="sxs-lookup"><span data-stu-id="c2802-142">Command-line parameters</span></span>            |
| [<span data-ttu-id="c2802-143">カスタム構成プロバイダー</span><span class="sxs-lookup"><span data-stu-id="c2802-143">Custom configuration provider</span></span>](custom-configuration-provider.md)                                                      | <span data-ttu-id="c2802-144">カスタム ソース</span><span class="sxs-lookup"><span data-stu-id="c2802-144">Custom source</span></span>                      |
| [<span data-ttu-id="c2802-145">環境変数構成プロバイダー</span><span class="sxs-lookup"><span data-stu-id="c2802-145">Environment Variables configuration provider</span></span>](configuration-providers.md#environment-variable-configuration-provider) | <span data-ttu-id="c2802-146">環境変数</span><span class="sxs-lookup"><span data-stu-id="c2802-146">Environment variables</span></span>              |
| [<span data-ttu-id="c2802-147">ファイル構成プロバイダー</span><span class="sxs-lookup"><span data-stu-id="c2802-147">File configuration provider</span></span>](configuration-providers.md#file-configuration-provider)                                  | <span data-ttu-id="c2802-148">JSON、XML、および INI ファイル</span><span class="sxs-lookup"><span data-stu-id="c2802-148">JSON, XML, and INI files</span></span>           |
| [<span data-ttu-id="c2802-149">ファイルごとのキーの構成プロバイダー</span><span class="sxs-lookup"><span data-stu-id="c2802-149">Key-per-file configuration provider</span></span>](configuration-providers.md#key-per-file-configuration-provider)                  | <span data-ttu-id="c2802-150">ディレクトリ ファイル</span><span class="sxs-lookup"><span data-stu-id="c2802-150">Directory files</span></span>                    |
| [<span data-ttu-id="c2802-151">メモリ構成プロバイダー</span><span class="sxs-lookup"><span data-stu-id="c2802-151">Memory configuration provider</span></span>](configuration-providers.md#memory-configuration-provider)                              | <span data-ttu-id="c2802-152">メモリ内コレクション</span><span class="sxs-lookup"><span data-stu-id="c2802-152">In-memory collections</span></span>              |
| [<span data-ttu-id="c2802-153">アプリのシークレット (Secret Manager)</span><span class="sxs-lookup"><span data-stu-id="c2802-153">App secrets (Secret Manager)</span></span>](/aspnet/core/security/app-secrets)                                                      | <span data-ttu-id="c2802-154">ユーザー プロファイル ディレクトリ内のファイル</span><span class="sxs-lookup"><span data-stu-id="c2802-154">File in the user profile directory</span></span> |

<span data-ttu-id="c2802-155">さまざまな構成プロバイダーの詳細については、「[.NET の構成プロバイダー](configuration-providers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c2802-155">For more information on various configuration providers, see [Configuration providers in .NET](configuration-providers.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c2802-156">関連項目</span><span class="sxs-lookup"><span data-stu-id="c2802-156">See also</span></span>

- [<span data-ttu-id="c2802-157">.NET の構成プロバイダー</span><span class="sxs-lookup"><span data-stu-id="c2802-157">Configuration providers in .NET</span></span>](configuration-providers.md)
- [<span data-ttu-id="c2802-158">カスタム構成プロバイダーを実装する</span><span class="sxs-lookup"><span data-stu-id="c2802-158">Implement a custom configuration provider</span></span>](custom-configuration-provider.md)
- <span data-ttu-id="c2802-159">構成のバグは、[github.com/dotnet/extensions](https://github.com/dotnet/extensions/issues) リポジトリに作成する必要がある</span><span class="sxs-lookup"><span data-stu-id="c2802-159">Configuration bugs should be created in the [github.com/dotnet/extensions](https://github.com/dotnet/extensions/issues) repo</span></span>
