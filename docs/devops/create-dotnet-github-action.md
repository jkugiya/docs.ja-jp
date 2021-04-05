---
title: 'チュートリアル: .NET を使用して GitHub アクションを作成する'
description: コンテナー化された .NET アプリを使用して GitHub アクションを作成する方法について説明します。
author: IEvangelist
ms.author: dapine
ms.date: 03/23/2021
ms.topic: tutorial
ms.openlocfilehash: 58b4ee07bd3809dd1bb2e1e2d3fc33cecfc3f4d6
ms.sourcegitcommit: 5ce37699c2a51ed173171813be68ef7577b1aba5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104881074"
---
# <a name="tutorial-create-a-github-action-with-net"></a><span data-ttu-id="91b0c-103">チュートリアル: .NET を使用して GitHub アクションを作成する</span><span class="sxs-lookup"><span data-stu-id="91b0c-103">Tutorial: Create a GitHub Action with .NET</span></span>

<span data-ttu-id="91b0c-104">GitHub アクションとして使用できる .NET アプリを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="91b0c-104">Learn how to create a .NET app that can be used as a GitHub Action.</span></span> <span data-ttu-id="91b0c-105">[GitHub Actions](https://github.com/features/actions) により、ワークフローの自動化と構成が可能になります。</span><span class="sxs-lookup"><span data-stu-id="91b0c-105">[GitHub Actions](https://github.com/features/actions) enable workflow automation and composition.</span></span> <span data-ttu-id="91b0c-106">GitHub Actions を使用すると、GitHub からソース コードをビルド、テスト、デプロイできます。</span><span class="sxs-lookup"><span data-stu-id="91b0c-106">With GitHub Actions, you can build, test, and deploy source code from GitHub.</span></span> <span data-ttu-id="91b0c-107">さらに、アクションによって、プログラムで問題を操作したり、プル要求を作成したり、コード レビューを実行したり、ブランチを管理したりする機能が公開されます。</span><span class="sxs-lookup"><span data-stu-id="91b0c-107">Additionally, actions expose the ability to programmatically interact with issues, create pull requests, perform code reviews, and manage branches.</span></span> <span data-ttu-id="91b0c-108">GitHub Actions を使用した継続的インテグレーションの詳細については、[.NET のビルドとテスト](https://docs.github.com/actions/guides/building-and-testing-net)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="91b0c-108">For more information on continuous integration with GitHub Actions, see [Building and testing .NET](https://docs.github.com/actions/guides/building-and-testing-net).</span></span>

<span data-ttu-id="91b0c-109">このチュートリアルでは、次の作業を行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="91b0c-109">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="91b0c-110">.NET アプリを GitHub Actions 用に準備する</span><span class="sxs-lookup"><span data-stu-id="91b0c-110">Prepare a .NET app for GitHub Actions</span></span>
> - <span data-ttu-id="91b0c-111">アクションの入力と出力を定義する</span><span class="sxs-lookup"><span data-stu-id="91b0c-111">Define action inputs and outputs</span></span>
> - <span data-ttu-id="91b0c-112">ワークフローを構成する</span><span class="sxs-lookup"><span data-stu-id="91b0c-112">Compose a workflow</span></span>

## <a name="prerequisites"></a><span data-ttu-id="91b0c-113">前提条件</span><span class="sxs-lookup"><span data-stu-id="91b0c-113">Prerequisites</span></span>

- <span data-ttu-id="91b0c-114">[GitHub アカウント](https://github.com/join)</span><span class="sxs-lookup"><span data-stu-id="91b0c-114">A [GitHub account](https://github.com/join)</span></span>
- <span data-ttu-id="91b0c-115">[.NET 5.0 SDK 以降](https://dotnet.microsoft.com/download/dotnet)</span><span class="sxs-lookup"><span data-stu-id="91b0c-115">The [.NET 5.0 SDK or later](https://dotnet.microsoft.com/download/dotnet)</span></span>
- <span data-ttu-id="91b0c-116">.NET 統合開発環境 (IDE)</span><span class="sxs-lookup"><span data-stu-id="91b0c-116">A .NET integrated development environment (IDE)</span></span>
  - <span data-ttu-id="91b0c-117">[Visual Studio IDE](https://visualstudio.microsoft.com) を自由に使用可能</span><span class="sxs-lookup"><span data-stu-id="91b0c-117">Feel free to use the [Visual Studio IDE](https://visualstudio.microsoft.com)</span></span>

## <a name="the-intent-of-the-app"></a><span data-ttu-id="91b0c-118">アプリの意図</span><span class="sxs-lookup"><span data-stu-id="91b0c-118">The intent of the app</span></span>

<span data-ttu-id="91b0c-119">このチュートリアルのアプリでは、次の操作を行うことによってコード メトリック分析を実行します。</span><span class="sxs-lookup"><span data-stu-id="91b0c-119">The app in this tutorial performs code metric analysis by:</span></span>

- <span data-ttu-id="91b0c-120">*\*.csproj* および *\*.vbproj* プロジェクト ファイルのスキャンと検出。</span><span class="sxs-lookup"><span data-stu-id="91b0c-120">Scanning and discovering *\*.csproj* and *\*.vbproj* project files.</span></span>
- <span data-ttu-id="91b0c-121">これらのプロジェクト内の検出されたソース コードの次の点に関する分析。</span><span class="sxs-lookup"><span data-stu-id="91b0c-121">Analyzing the discovered source code within these projects for:</span></span>

  - <span data-ttu-id="91b0c-122">サイクロマティック複雑度</span><span class="sxs-lookup"><span data-stu-id="91b0c-122">Cyclomatic complexity</span></span>
  - <span data-ttu-id="91b0c-123">保守容易性指数</span><span class="sxs-lookup"><span data-stu-id="91b0c-123">Maintainability index</span></span>
  - <span data-ttu-id="91b0c-124">継承の深さ</span><span class="sxs-lookup"><span data-stu-id="91b0c-124">Depth of inheritance</span></span>
  - <span data-ttu-id="91b0c-125">クラス結合</span><span class="sxs-lookup"><span data-stu-id="91b0c-125">Class coupling</span></span>
  - <span data-ttu-id="91b0c-126">ソース コードの行数</span><span class="sxs-lookup"><span data-stu-id="91b0c-126">Number of lines of source code</span></span>
  - <span data-ttu-id="91b0c-127">実行可能コードの見積もられた行数</span><span class="sxs-lookup"><span data-stu-id="91b0c-127">Approximated lines of executable code</span></span>

- <span data-ttu-id="91b0c-128">*CODE_METRICS.md* ファイルの作成 (または更新)。</span><span class="sxs-lookup"><span data-stu-id="91b0c-128">Creating (or updating) a *CODE_METRICS.md* file.</span></span>

<span data-ttu-id="91b0c-129">このアプリは、*CODE_METRICS.md* ファイルの変更によりプル要求を作成する役割を果たし "*ません*"。</span><span class="sxs-lookup"><span data-stu-id="91b0c-129">The app is *not* responsible for creating a pull request with the changes to the *CODE_METRICS.md* file.</span></span> <span data-ttu-id="91b0c-130">これらの変更は、[ワークフローの構成](#workflow-composition)の一部として管理されます。</span><span class="sxs-lookup"><span data-stu-id="91b0c-130">These changes are managed as part of the [workflow composition](#workflow-composition).</span></span>

<span data-ttu-id="91b0c-131">このチュートリアルでのソース コードの参照には、簡潔にするために省略されたアプリの部分が含まれています。</span><span class="sxs-lookup"><span data-stu-id="91b0c-131">References to the source code in this tutorial have portions of the app omitted for brevity.</span></span> <span data-ttu-id="91b0c-132">完全なアプリ コードは、[GitHub で入手できます](https://github.com/dotnet/samples/tree/main/github-actions/DotNet.GitHubAction)。</span><span class="sxs-lookup"><span data-stu-id="91b0c-132">The complete app code is [available on GitHub](https://github.com/dotnet/samples/tree/main/github-actions/DotNet.GitHubAction).</span></span>

### <a name="explore-the-app"></a><span data-ttu-id="91b0c-133">アプリを探索する</span><span class="sxs-lookup"><span data-stu-id="91b0c-133">Explore the app</span></span>

<span data-ttu-id="91b0c-134">.NET コンソール アプリでは、[`CommandLineParser` NuGet](https://www.nuget.org/packages/CommandLineParser/) パッケージを使用して引数を `ActionInputs` オブジェクトに解析します。</span><span class="sxs-lookup"><span data-stu-id="91b0c-134">The .NET console app uses the [`CommandLineParser` NuGet](https://www.nuget.org/packages/CommandLineParser/) package to parse arguments into the `ActionInputs` object.</span></span>

:::code language="csharp" source="snippets/DotNet.GitHubAction/ActionInputs.cs":::

<span data-ttu-id="91b0c-135">前のアクション入力クラスでは、このアプリを正常に実行するために必要ないくつかの入力を定義します。</span><span class="sxs-lookup"><span data-stu-id="91b0c-135">The preceding action inputs class defines several required inputs for the app to run successfully.</span></span> <span data-ttu-id="91b0c-136">コンストラクターでは、`"GREETINGS"` 環境変数の値を書き込みます (この値が現在の実行環境で使用可能な場合)。</span><span class="sxs-lookup"><span data-stu-id="91b0c-136">The constructor will write the `"GREETINGS"` environment variable value, if one is available in the current execution environment.</span></span> <span data-ttu-id="91b0c-137">`Name` および `Branch` プロパティが解析され、`"/"` で区切られた文字列の最後のセグメントから割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="91b0c-137">The `Name` and `Branch` properties are parsed and assigned from the last segment of a `"/"` delimited string.</span></span>

<span data-ttu-id="91b0c-138">定義されたアクション入力クラスを使用して、*Program.cs* ファイルに焦点を絞ります。</span><span class="sxs-lookup"><span data-stu-id="91b0c-138">With the defined action inputs class, focus on the *Program.cs* file.</span></span>

:::code language="csharp" source="snippets/DotNet.GitHubAction/Program.cs":::

<span data-ttu-id="91b0c-139">`Program` ファイルは、簡潔にするために簡略化されています。完全なサンプル ソースを調べるには、[*Program.cs*](https://github.com/dotnet/samples/blob/main/github-actions/DotNet.GitHubAction/DotNet.GitHubAction/Program.cs) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="91b0c-139">The `Program` file is simplified for brevity, to explore the full sample source, see [*Program.cs*](https://github.com/dotnet/samples/blob/main/github-actions/DotNet.GitHubAction/DotNet.GitHubAction/Program.cs).</span></span> <span data-ttu-id="91b0c-140">ここに表示されているしくみは、次のものを使用するために必要な定型コードを示しています。</span><span class="sxs-lookup"><span data-stu-id="91b0c-140">The mechanics in place demonstrate the boilerplate code required to use:</span></span>

- [<span data-ttu-id="91b0c-141">最上位レベルのステートメント</span><span class="sxs-lookup"><span data-stu-id="91b0c-141">Top-level statements</span></span>](../csharp/whats-new/tutorials/top-level-statements.md)
- [<span data-ttu-id="91b0c-142">汎用ホスト</span><span class="sxs-lookup"><span data-stu-id="91b0c-142">Generic Host</span></span>](../core/extensions/generic-host.md)
- [<span data-ttu-id="91b0c-143">依存関係の挿入</span><span class="sxs-lookup"><span data-stu-id="91b0c-143">Dependency injection</span></span>](../core/extensions/dependency-injection.md)

<span data-ttu-id="91b0c-144">外部のプロジェクトまたはパッケージ参照を使用して、依存関係の挿入に登録できます。</span><span class="sxs-lookup"><span data-stu-id="91b0c-144">External project or package references can be used, and registered with dependency injection.</span></span> <span data-ttu-id="91b0c-145">`Get<TService>` は、`IHost` インスタンスを必要とする静的ローカル関数であり、必要なサービスを解決するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="91b0c-145">The `Get<TService>` is a static local function, which requires the `IHost` instance, and is used to resolve required services.</span></span> <span data-ttu-id="91b0c-146">`CommandLine.Parser.Default` シングルトンでは、このアプリは `args` から `parser` インスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="91b0c-146">With the `CommandLine.Parser.Default` singleton, the app gets a `parser` instance from the `args`.</span></span> <span data-ttu-id="91b0c-147">これらの引数を解析できない場合、このアプリは 0 以外の終了コードで終了します。</span><span class="sxs-lookup"><span data-stu-id="91b0c-147">When the arguments are unable to be parsed, the app exits with a non-zero exit code.</span></span> <span data-ttu-id="91b0c-148">詳細については、[アクションの終了コードの設定](https://docs.github.com/actions/creating-actions/setting-exit-codes-for-actions)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="91b0c-148">For more information, see [Setting exit codes for actions](https://docs.github.com/actions/creating-actions/setting-exit-codes-for-actions).</span></span>

<span data-ttu-id="91b0c-149">引数が正常に解析された場合、このアプリは、必要な入力で正しく呼び出されました。</span><span class="sxs-lookup"><span data-stu-id="91b0c-149">When the args are successfully parsed, the app was called correctly with the required inputs.</span></span> <span data-ttu-id="91b0c-150">この場合は、主要な機能 `StartAnalysisAsync` への呼び出しが行われます。</span><span class="sxs-lookup"><span data-stu-id="91b0c-150">In this case, a call to the primary functionality `StartAnalysisAsync` is made.</span></span>

<span data-ttu-id="91b0c-151">出力値を書き込むには、[GitHub Actions: 出力パラメーターの設定](https://docs.github.com/actions/reference/workflow-commands-for-github-actions#setting-an-output-parameter)によって認識される形式に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="91b0c-151">To write output values, you must follow the format recognized by [GitHub Actions: Setting an output parameter](https://docs.github.com/actions/reference/workflow-commands-for-github-actions#setting-an-output-parameter).</span></span>

## <a name="prepare-the-net-app-for-github-actions"></a><span data-ttu-id="91b0c-152">.NET アプリを GitHub Actions 用に準備する</span><span class="sxs-lookup"><span data-stu-id="91b0c-152">Prepare the .NET app for GitHub Actions</span></span>

<span data-ttu-id="91b0c-153">GitHub Actions では、アプリ開発として次の 2 つのバリエーションをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="91b0c-153">GitHub Actions support two variations of app development, either</span></span>

- <span data-ttu-id="91b0c-154">JavaScript (オプションで [TypeScript](https://www.typescriptlang.org))</span><span class="sxs-lookup"><span data-stu-id="91b0c-154">JavaScript (optionally [TypeScript](https://www.typescriptlang.org))</span></span>
- <span data-ttu-id="91b0c-155">Docker コンテナー ([Docker](https://docs.github.com/actions/creating-actions/creating-a-docker-container-action) 上で実行される任意のアプリ)</span><span class="sxs-lookup"><span data-stu-id="91b0c-155">Docker container (any app that runs on [Docker](https://docs.github.com/actions/creating-actions/creating-a-docker-container-action))</span></span>

<span data-ttu-id="91b0c-156">.NET は GitHub Actions でネイティブにサポートされ "*いない*" ため、.NET アプリをコンテナー化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="91b0c-156">Since .NET is *not* natively supported by GitHub Actions, the .NET app needs to be containerized.</span></span> <span data-ttu-id="91b0c-157">詳細については、[.NET アプリのコンテナー化](../core/docker/build-container.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="91b0c-157">For more information, see [Containerize a .NET app](../core/docker/build-container.md).</span></span>

### <a name="the-dockerfile"></a><span data-ttu-id="91b0c-158">Dockerfile</span><span class="sxs-lookup"><span data-stu-id="91b0c-158">The Dockerfile</span></span>

<span data-ttu-id="91b0c-159">[*Dockerfile*](https://docs.docker.com/engine/reference/builder) は、イメージをビルドするための一連の手順です。</span><span class="sxs-lookup"><span data-stu-id="91b0c-159">A [*Dockerfile*](https://docs.docker.com/engine/reference/builder) is a set of instructions to build an image.</span></span> <span data-ttu-id="91b0c-160">.NET アプリケーションの場合、*Dockerfile* は通常、ソリューション ファイルの隣にあるディレクトリのルートに存在します。</span><span class="sxs-lookup"><span data-stu-id="91b0c-160">For .NET applications, the *Dockerfile* usually sits in the root of the directory next to a solution file.</span></span>

:::code language="dockerfile" source="snippets/Dockerfile" highlight="23":::

> [!NOTE]
> <span data-ttu-id="91b0c-161">このチュートリアルの .NET アプリは、その機能の一部として .NET SDK に依存しているため、強調表示されている行によって .NET SDK がビルド出力で改めて再階層化されます。</span><span class="sxs-lookup"><span data-stu-id="91b0c-161">The .NET app in this tutorial relies on the .NET SDK as part of its functionality, as such, the highlighted line relayers the .NET SDK anew with the build output.</span></span> <span data-ttu-id="91b0c-162">その機能の一部として .NET SDK を必要と "***しない***" アプリケーションの場合は、代わりに .NET ランタイムのみに依存します。</span><span class="sxs-lookup"><span data-stu-id="91b0c-162">For applications that ***do not*** require the .NET SDK as part of their functionality, they should rely on just the .NET Runtime instead.</span></span> <span data-ttu-id="91b0c-163">これにより、イメージのサイズが大幅に削減されます。</span><span class="sxs-lookup"><span data-stu-id="91b0c-163">This greatly reduces the size of the image.</span></span>
>
> ```dockerfile
> FROM mcr.microsoft.com/dotnet/runtime:5.0
> ```

<span data-ttu-id="91b0c-164">前の *Dockerfile* のステップには、次のものが含まれます。</span><span class="sxs-lookup"><span data-stu-id="91b0c-164">The preceding *Dockerfile* steps include:</span></span>

- <span data-ttu-id="91b0c-165">`mcr.microsoft.com/dotnet/sdk:5.0` の基本イメージのエイリアス `build-env` としての設定。</span><span class="sxs-lookup"><span data-stu-id="91b0c-165">Setting the base image from `mcr.microsoft.com/dotnet/sdk:5.0` as the alias `build-env`.</span></span>
- <span data-ttu-id="91b0c-166">コンテンツのコピーと .NET アプリの発行。</span><span class="sxs-lookup"><span data-stu-id="91b0c-166">Copying the contents and publishing the .NET app:</span></span>
  - <span data-ttu-id="91b0c-167">このアプリは、[`dotnet publish`](../core/tools/dotnet-publish.md) コマンドを使用して発行されます。</span><span class="sxs-lookup"><span data-stu-id="91b0c-167">The app is published using the [`dotnet publish`](../core/tools/dotnet-publish.md) command.</span></span>
- <span data-ttu-id="91b0c-168">コンテナーへのラベルの適用。</span><span class="sxs-lookup"><span data-stu-id="91b0c-168">Applying labels to the container.</span></span>
- <span data-ttu-id="91b0c-169">`mcr.microsoft.com/dotnet/sdk:5.0` の .NET SDK イメージの再階層化。</span><span class="sxs-lookup"><span data-stu-id="91b0c-169">Relayering the .NET SDK image from `mcr.microsoft.com/dotnet/sdk:5.0`</span></span>
- <span data-ttu-id="91b0c-170">発行されたビルド出力の `build-env` からのコピー。</span><span class="sxs-lookup"><span data-stu-id="91b0c-170">Copying the published build output from the `build-env`.</span></span>
- <span data-ttu-id="91b0c-171">[`dotnet /DotNet.GitHubAction.dll`](../core/tools/dotnet.md) に委任されるエントリ ポイントの定義。</span><span class="sxs-lookup"><span data-stu-id="91b0c-171">Defining the entry point, which delegates to [`dotnet /DotNet.GitHubAction.dll`](../core/tools/dotnet.md).</span></span>

> [!TIP]
> <span data-ttu-id="91b0c-172">`mcr.microsoft.com` の MCR は "Microsoft Container Registry" を表し、公式の Docker Hub の Microsoft のシンジケート化されたコンテナー カタログです。</span><span class="sxs-lookup"><span data-stu-id="91b0c-172">The MCR in `mcr.microsoft.com` stands for "Microsoft Container Registry", and is Microsoft's syndicated container catalog from the official Docker hub.</span></span> <span data-ttu-id="91b0c-173">詳細については、[Microsoft によるコンテナー カタログのシンジケート化](https://azure.microsoft.com/blog/microsoft-syndicates-container-catalog/)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="91b0c-173">For more information, see [Microsoft syndicates container catalog](https://azure.microsoft.com/blog/microsoft-syndicates-container-catalog/).</span></span>

## <a name="define-action-inputs-and-outputs"></a><span data-ttu-id="91b0c-174">アクションの入力と出力を定義する</span><span class="sxs-lookup"><span data-stu-id="91b0c-174">Define action inputs and outputs</span></span>

<span data-ttu-id="91b0c-175">「[アプリを探索する](#explore-the-app)」のセクションでは、`ActionInputs` クラスについて学習しました。</span><span class="sxs-lookup"><span data-stu-id="91b0c-175">In the [Explore the app](#explore-the-app) section, you learned about the `ActionInputs` class.</span></span> <span data-ttu-id="91b0c-176">このオブジェクトは、GitHub アクションの入力を表します。</span><span class="sxs-lookup"><span data-stu-id="91b0c-176">This object represents the inputs for the GitHub Action.</span></span> <span data-ttu-id="91b0c-177">GitHub でリポジトリが GitHub アクションであることを認識できるようにするには、そのリポジトリのルートに *action.yml* ファイルが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="91b0c-177">For GitHub to recognize that the repository is a GitHub Action, you need to have an *action.yml* file at the root of the repository.</span></span>

:::code language="yml" source="snippets/action.yml":::

<span data-ttu-id="91b0c-178">前の *action.yml* ファイルでは、次のものを定義します。</span><span class="sxs-lookup"><span data-stu-id="91b0c-178">The preceding *action.yml* file defines:</span></span>

- <span data-ttu-id="91b0c-179">GitHub アクションの `name` と `description`。</span><span class="sxs-lookup"><span data-stu-id="91b0c-179">The `name` and `description` of the GitHub Action</span></span>
- <span data-ttu-id="91b0c-180">`branding`。これは、アクションをより一意に識別しやすくするために [GitHub Marketplace](https://github.com/marketplace?type=actions) で使用されます。</span><span class="sxs-lookup"><span data-stu-id="91b0c-180">The `branding`, which is used in the [GitHub Marketplace](https://github.com/marketplace?type=actions) to help more uniquely identify your action</span></span>
- <span data-ttu-id="91b0c-181">`inputs`。これは、`ActionInputs` クラスに 1 対 1 でマップします。</span><span class="sxs-lookup"><span data-stu-id="91b0c-181">The `inputs`, which maps one-to-one with the `ActionInputs` class</span></span>
- <span data-ttu-id="91b0c-182">`outputs`。これは、`Program` で[ワークフローの構成](#workflow-composition)に書き込まれ、その一部として使用されます。</span><span class="sxs-lookup"><span data-stu-id="91b0c-182">The `outputs`, which is written to in the `Program` and used as part of [Workflow composition](#workflow-composition)</span></span>
- <span data-ttu-id="91b0c-183">`runs` ノード。これは、そのアプリが `docker` アプリケーションであり、それにどのような引数を渡すかを GitHub に通知します。</span><span class="sxs-lookup"><span data-stu-id="91b0c-183">The `runs` node, which tells GitHub that the app is a `docker` application and what arguments to pass to it</span></span>

<span data-ttu-id="91b0c-184">詳細については、「[GitHub Actions のメタデータ構文](https://docs.github.com/actions/creating-actions/metadata-syntax-for-github-actions)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="91b0c-184">For more information, see [Metadata syntax for GitHub Actions](https://docs.github.com/actions/creating-actions/metadata-syntax-for-github-actions).</span></span>

## <a name="workflow-composition"></a><span data-ttu-id="91b0c-185">ワークフローの構成</span><span class="sxs-lookup"><span data-stu-id="91b0c-185">Workflow composition</span></span>

<span data-ttu-id="91b0c-186">[.NET アプリがコンテナー化](#prepare-the-net-app-for-github-actions)され、[アクションの入力と出力](#define-action-inputs-and-outputs)が定義されると、アクションを使用する準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="91b0c-186">With the [.NET app containerized](#prepare-the-net-app-for-github-actions), and the [action inputs and outputs](#define-action-inputs-and-outputs) defined, you're ready to consume the action.</span></span> <span data-ttu-id="91b0c-187">GitHub Actions は、使用するために GitHub Marketplace で発行する必要は "*ありません*"。</span><span class="sxs-lookup"><span data-stu-id="91b0c-187">GitHub Actions are *not* required to be published in the GitHub Marketplace to be used.</span></span> <span data-ttu-id="91b0c-188">ワークフローは、リポジトリの *.github/workflows* ディレクトリで YAML ファイルとして定義されます。</span><span class="sxs-lookup"><span data-stu-id="91b0c-188">Workflows are defined in the *.github/workflows* directory of a repository as YAML files.</span></span>

:::code language="yml" source="snippets/workflow.yml":::

<span data-ttu-id="91b0c-189">前のワークフロー YAML ファイルでは、次の 3 つのプライマリ ノードを定義します。</span><span class="sxs-lookup"><span data-stu-id="91b0c-189">The preceding workflow YAML file defines three primary nodes:</span></span>

- <span data-ttu-id="91b0c-190">ワークフローの `name`。</span><span class="sxs-lookup"><span data-stu-id="91b0c-190">The `name` of the workflow.</span></span> <span data-ttu-id="91b0c-191">この名前はまた、[ワークフロー状態バッジ](https://docs.github.com/actions/managing-workflow-runs/adding-a-workflow-status-badge)を作成するときに使用される名前でもあります。</span><span class="sxs-lookup"><span data-stu-id="91b0c-191">This name is also what's used when creating a [workflow status badge](https://docs.github.com/actions/managing-workflow-runs/adding-a-workflow-status-badge).</span></span>
- <span data-ttu-id="91b0c-192">`on` ノードは、アクションがいつ、どのようにトリガーされるかを定義します。</span><span class="sxs-lookup"><span data-stu-id="91b0c-192">The `on` node defines when and how the action is triggered.</span></span>
- <span data-ttu-id="91b0c-193">`jobs` ノードは、さまざまなジョブと、各ジョブ内のステップの概要を示します。</span><span class="sxs-lookup"><span data-stu-id="91b0c-193">The `jobs` node outlines the various jobs and steps within each job.</span></span> <span data-ttu-id="91b0c-194">個々のステップで GitHub Actions を使用します。</span><span class="sxs-lookup"><span data-stu-id="91b0c-194">Individual steps consume GitHub Actions.</span></span>

<span data-ttu-id="91b0c-195">詳細については、[最初のワークフローの作成](https://docs.github.com/actions/quickstart#creating-your-first-workflow)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="91b0c-195">For more information, see [Creating your first workflow](https://docs.github.com/actions/quickstart#creating-your-first-workflow).</span></span>

<span data-ttu-id="91b0c-196">`steps` ノードに焦点を絞ると、構成がよりわかりやすくなります。</span><span class="sxs-lookup"><span data-stu-id="91b0c-196">Focusing on the `steps` node, the composition is more obvious:</span></span>

:::code language="yml" source="snippets/workflow.yml" range="22-47":::

<span data-ttu-id="91b0c-197">`jobs/steps` は、*ワークフローの構成* を表します。</span><span class="sxs-lookup"><span data-stu-id="91b0c-197">The `jobs/steps` represents the *workflow composition*.</span></span> <span data-ttu-id="91b0c-198">ステップは、それがシーケンシャルで、通信機能を持ち、かつ構成可能であるように調整されます。</span><span class="sxs-lookup"><span data-stu-id="91b0c-198">Steps are orchestrated such that they're sequential, communicative, and composable.</span></span> <span data-ttu-id="91b0c-199">ステップを表すさまざまな GitHub Actions (それぞれに入力と出力があります) を使用してワークフローを構成できます。</span><span class="sxs-lookup"><span data-stu-id="91b0c-199">With various GitHub Actions representing steps, each having inputs and outputs, workflows can be composed.</span></span>

<span data-ttu-id="91b0c-200">前のステップでは、次のことを観察できます。</span><span class="sxs-lookup"><span data-stu-id="91b0c-200">In the preceding steps, you can observe:</span></span>

1. <span data-ttu-id="91b0c-201">リポジトリが[チェックアウト](https://github.com/actions/checkout)されます。</span><span class="sxs-lookup"><span data-stu-id="91b0c-201">The repository is [checked out](https://github.com/actions/checkout).</span></span>
1. <span data-ttu-id="91b0c-202">[手動で実行](https://github.blog/changelog/2020-07-06-github-actions-manual-triggers-with-workflow_dispatch)されると、メッセージがワークフロー ログに出力されます。</span><span class="sxs-lookup"><span data-stu-id="91b0c-202">A message is printed to the workflow log, when [manually ran](https://github.blog/changelog/2020-07-06-github-actions-manual-triggers-with-workflow_dispatch).</span></span>
1. <span data-ttu-id="91b0c-203">`dotnet-code-metrics` として識別されたステップ:</span><span class="sxs-lookup"><span data-stu-id="91b0c-203">A step identified as `dotnet-code-metrics`:</span></span>

    - <span data-ttu-id="91b0c-204">`uses: dotnet/samples/github-actions/DotNet.GitHubAction@main` は、このチュートリアルのコンテナー化された .NET アプリの場所です。</span><span class="sxs-lookup"><span data-stu-id="91b0c-204">`uses: dotnet/samples/github-actions/DotNet.GitHubAction@main` is the location of the containerized .NET app in this tutorial.</span></span>
    - <span data-ttu-id="91b0c-205">`env` は、このアプリの実行で出力される環境変数 `"GREETING"` を作成します。</span><span class="sxs-lookup"><span data-stu-id="91b0c-205">`env` creates an environment variable `"GREETING"`, which is printed in the execution of the app.</span></span>
    - <span data-ttu-id="91b0c-206">`with` は、必要な各アクション入力を指定します。</span><span class="sxs-lookup"><span data-stu-id="91b0c-206">`with` specifies each of the required action inputs.</span></span>

1. <span data-ttu-id="91b0c-207">`dotnet-code-metrics` ステップで `true` の値を持つ `updated-metrics` の出力パラメーターが指定されると、`Create pull request` という名前の条件付きステップが実行されます。</span><span class="sxs-lookup"><span data-stu-id="91b0c-207">A conditional step, named `Create pull request` runs when the `dotnet-code-metrics` step specifies an output parameter of `updated-metrics` with a value of `true`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="91b0c-208">GitHub では、[暗号化されたシークレット](https://docs.github.com/actions/reference/encrypted-secrets)の作成が許可されます。</span><span class="sxs-lookup"><span data-stu-id="91b0c-208">GitHub allows for the creation of [encrypted secrets](https://docs.github.com/actions/reference/encrypted-secrets).</span></span> <span data-ttu-id="91b0c-209">シークレットは、`${{ secrets.SECRET_NAME }}` 構文を使用して、ワークフローの構成内で使用できます。</span><span class="sxs-lookup"><span data-stu-id="91b0c-209">Secrets can be used within workflow composition, using the `${{ secrets.SECRET_NAME }}` syntax.</span></span> <span data-ttu-id="91b0c-210">GitHub アクションのコンテキストには、既定値 `${{ secrets.GITHUB_TOKEN }}` が自動的に設定される GitHub トークンが存在します。</span><span class="sxs-lookup"><span data-stu-id="91b0c-210">In the context of a GitHub Action, there is a GitHub token that is automatically populated by default: `${{ secrets.GITHUB_TOKEN }}`.</span></span> <span data-ttu-id="91b0c-211">詳細については、[GitHub Actions のコンテキストと式の構文](https://docs.github.com/actions/reference/context-and-expression-syntax-for-github-actions)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="91b0c-211">For more information, see [Context and expression syntax for GitHub Actions](https://docs.github.com/actions/reference/context-and-expression-syntax-for-github-actions).</span></span>

## <a name="put-it-all-together"></a><span data-ttu-id="91b0c-212">すべてをまとめた配置</span><span class="sxs-lookup"><span data-stu-id="91b0c-212">Put it all together</span></span>

<span data-ttu-id="91b0c-213">[dotnet/samples](https://github.com/dotnet/samples) GitHub リポジトリには、このチュートリアルのアプリを含む多数の .NET サンプル ソース コード プロジェクトがあります。</span><span class="sxs-lookup"><span data-stu-id="91b0c-213">The [dotnet/samples](https://github.com/dotnet/samples) GitHub repository is home to many .NET sample source code projects, including the app in this tutorial.</span></span>

- <span data-ttu-id="91b0c-214">このアプリは、[サンプル ブラウザー](/samples/dotnet/samples/create-dotnet-github-action)で入手できます。</span><span class="sxs-lookup"><span data-stu-id="91b0c-214">The app is available in the [samples browser](/samples/dotnet/samples/create-dotnet-github-action).</span></span>
- <span data-ttu-id="91b0c-215">生成された [*CODE_METRICS.md*](https://github.com/dotnet/samples/blob/main/github-actions/DotNet.GitHubAction/CODE_METRICS.md) ファイルはナビゲート可能です。</span><span class="sxs-lookup"><span data-stu-id="91b0c-215">The generated [*CODE_METRICS.md*](https://github.com/dotnet/samples/blob/main/github-actions/DotNet.GitHubAction/CODE_METRICS.md) file is navigable.</span></span>

<span data-ttu-id="91b0c-216">*CODE_METRICS.md* ファイルは、分析されたプロジェクトの階層を表します。</span><span class="sxs-lookup"><span data-stu-id="91b0c-216">The *CODE_METRICS.md* file represents the hierarchy of the projects it analyzed.</span></span> <span data-ttu-id="91b0c-217">各プロジェクトには最上位のセクションがあり、絵文字は、入れ子になったオブジェクトの最も高いサイクロマティック複雑度の全体的な状態を表します。</span><span class="sxs-lookup"><span data-stu-id="91b0c-217">Each project has a top-level section, and an emoji the represents the overall status of the highest cyclomatic complexity for nested objects.</span></span> <span data-ttu-id="91b0c-218">ファイル内を移動すると、各セクションでは、各領域の概要と共にドリル ダウンの機会が提供されます。</span><span class="sxs-lookup"><span data-stu-id="91b0c-218">As you navigate the file, each section exposes drill-down opportunities with a summary of each area.</span></span> <span data-ttu-id="91b0c-219">マークダウンには、利便性の向上として折りたたみ可能なセクションがあります。</span><span class="sxs-lookup"><span data-stu-id="91b0c-219">The markdown has collapsible sections as an added convenience.</span></span>

<span data-ttu-id="91b0c-220">この階層は、次のように進行します。</span><span class="sxs-lookup"><span data-stu-id="91b0c-220">The hierarchy progresses from:</span></span>

- <span data-ttu-id="91b0c-221">プロジェクト ファイルからアセンブリへ</span><span class="sxs-lookup"><span data-stu-id="91b0c-221">Project file to assembly</span></span>
- <span data-ttu-id="91b0c-222">アセンブリから名前空間へ</span><span class="sxs-lookup"><span data-stu-id="91b0c-222">Assembly to namespace</span></span>
- <span data-ttu-id="91b0c-223">名前空間から名前付き型へ</span><span class="sxs-lookup"><span data-stu-id="91b0c-223">Namespace to named-type</span></span>
- <span data-ttu-id="91b0c-224">各名前付き型にはテーブルがあり、各テーブルには次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="91b0c-224">Each named-type has a table, and each table has:</span></span>
  - <span data-ttu-id="91b0c-225">フィールド、メソッド、プロパティの行番号へのリンク</span><span class="sxs-lookup"><span data-stu-id="91b0c-225">Links to line numbers for fields, methods, and properties</span></span>
  - <span data-ttu-id="91b0c-226">コード メトリックに関する個々の評価</span><span class="sxs-lookup"><span data-stu-id="91b0c-226">Individual ratings for code metrics</span></span>

### <a name="in-action"></a><span data-ttu-id="91b0c-227">操作の実例</span><span class="sxs-lookup"><span data-stu-id="91b0c-227">In action</span></span>

<span data-ttu-id="91b0c-228">このワークフローは、`main` ブランチへの `push` に関する `on` 操作によって、アクションの実行がトリガーされることを指定します。</span><span class="sxs-lookup"><span data-stu-id="91b0c-228">The workflow specifies that `on` a `push` to the `main` branch, the action is triggered to run.</span></span> <span data-ttu-id="91b0c-229">これが実行されると、GitHub の **[アクション]** タブによって、その実行のライブ ログ ストリームが報告されます。</span><span class="sxs-lookup"><span data-stu-id="91b0c-229">When it runs, the **Actions** tab in GitHub will report the live log stream of its execution.</span></span> <span data-ttu-id="91b0c-230">`.NET code metrics` 実行のログの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="91b0c-230">Here is an example log from the `.NET code metrics` run:</span></span>

:::image type="content" source="media/action-log.png" lightbox="media/action-log.png" border="true" alt-text=".NET のコード メトリック - GitHub アクションのログ":::

## <a name="see-also"></a><span data-ttu-id="91b0c-232">関連項目</span><span class="sxs-lookup"><span data-stu-id="91b0c-232">See also</span></span>

<!-- TODO: Add DevOps eBook link when published -->

- [<span data-ttu-id="91b0c-233">.NET での汎用ホスト</span><span class="sxs-lookup"><span data-stu-id="91b0c-233">.NET Generic Host</span></span>](../core/extensions/generic-host.md)
- [<span data-ttu-id="91b0c-234">.NET での依存関係の挿入</span><span class="sxs-lookup"><span data-stu-id="91b0c-234">Dependency injection in .NET</span></span>](../core/extensions/dependency-injection.md)
- [<span data-ttu-id="91b0c-235">コード メトリック値</span><span class="sxs-lookup"><span data-stu-id="91b0c-235">Code metrics values</span></span>](/visualstudio/code-quality/code-metrics-values)

## <a name="next-steps"></a><span data-ttu-id="91b0c-236">次のステップ</span><span class="sxs-lookup"><span data-stu-id="91b0c-236">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="91b0c-237">.NET GitHub アクションのサンプル コード</span><span class="sxs-lookup"><span data-stu-id="91b0c-237">.NET GitHub Action sample code</span></span>](/samples/dotnet/samples/create-dotnet-github-action)
