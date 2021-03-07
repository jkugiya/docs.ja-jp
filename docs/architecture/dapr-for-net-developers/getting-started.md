---
title: Dapr を使ってみる
description: ローカル開発環境を準備し、Dapr で初めての .NET アプリケーションを構築するためのガイドです。
author: amolenk
ms.date: 02/25/2021
ms.openlocfilehash: 68b1982c7283e0717ff7e1e254e5f313cd480d7b
ms.sourcegitcommit: bdbf6472de867a0a11aaa5b9384a2506c24f27d2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2021
ms.locfileid: "102401474"
---
# <a name="get-started-with-dapr"></a><span data-ttu-id="39873-103">Dapr を使ってみる</span><span class="sxs-lookup"><span data-stu-id="39873-103">Get started with Dapr</span></span>

<span data-ttu-id="39873-104">最初の2つの章では、Dapr に関する基本的な概念を学習しました。</span><span class="sxs-lookup"><span data-stu-id="39873-104">In the first two chapters, you learned basic concepts about Dapr.</span></span> <span data-ttu-id="39873-105">それ *を体験してください。*</span><span class="sxs-lookup"><span data-stu-id="39873-105">It's time to take it for a *test drive*.</span></span> <span data-ttu-id="39873-106">この章では、ローカル開発環境を準備し、2つの Dapr .NET アプリケーションを構築する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="39873-106">This chapter will guide you through preparing your local development environment and building two Dapr .NET applications.</span></span>

## <a name="install-dapr-into-your-local-environment"></a><span data-ttu-id="39873-107">ローカル環境に Dapr をインストールする</span><span class="sxs-lookup"><span data-stu-id="39873-107">Install Dapr into your local environment</span></span>

<span data-ttu-id="39873-108">まず、開発用コンピューターに Dapr をインストールします。</span><span class="sxs-lookup"><span data-stu-id="39873-108">You'll start by installing Dapr on your development computer.</span></span> <span data-ttu-id="39873-109">完了すると、Dapr アプリケーションを [自己ホスト型モード](https://docs.dapr.io/operations/hosting/self-hosted/self-hosted-overview/)でビルドして実行できます。</span><span class="sxs-lookup"><span data-stu-id="39873-109">Once complete, you can build and run Dapr applications in [self-hosted mode](https://docs.dapr.io/operations/hosting/self-hosted/self-hosted-overview/).</span></span>

1. <span data-ttu-id="39873-110">[Dapr CLI をインストール](https://docs.dapr.io/getting-started/install-dapr-cli/)します。</span><span class="sxs-lookup"><span data-stu-id="39873-110">[Install the Dapr CLI](https://docs.dapr.io/getting-started/install-dapr-cli/).</span></span> <span data-ttu-id="39873-111">これにより、Dapr インスタンスの起動、実行、および管理を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="39873-111">It enables you to launch, run, and manage Dapr instances.</span></span> <span data-ttu-id="39873-112">また、デバッグサポートも提供します。</span><span class="sxs-lookup"><span data-stu-id="39873-112">It also provides debugging support.</span></span>

1. <span data-ttu-id="39873-113">[Docker Desktop](https://docs.docker.com/get-docker/)をインストールします。</span><span class="sxs-lookup"><span data-stu-id="39873-113">Install [Docker Desktop](https://docs.docker.com/get-docker/).</span></span> <span data-ttu-id="39873-114">Windows で実行している場合は、Linux コンテナーを使用するように **Docker Desktop For windows** が構成されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="39873-114">If you're running on Windows, make sure that **Docker Desktop for Windows** is configured to use Linux containers.</span></span>

> [!NOTE]
> <span data-ttu-id="39873-115">既定では、Dapr は Docker コンテナーを使用して、すぐに使用できる最適なエクスペリエンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="39873-115">By default, Dapr uses Docker containers to provide you the best out-of-the-box experience.</span></span> <span data-ttu-id="39873-116">Docker の外部で Dapr を実行するには、この手順をスキップして、 [*スリム* な初期化を実行](https://docs.dapr.io/operations/hosting/self-hosted/self-hosted-no-docker/)します。</span><span class="sxs-lookup"><span data-stu-id="39873-116">To run Dapr outside of Docker, you can skip this step and [execute a *slim* initialization](https://docs.dapr.io/operations/hosting/self-hosted/self-hosted-no-docker/).</span></span> <span data-ttu-id="39873-117">この章の例では、Docker コンテナーを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="39873-117">The examples in this chapter require you use Docker containers.</span></span>

1. <span data-ttu-id="39873-118">[Dapr を初期化](https://docs.dapr.io/getting-started/install-dapr/)します。</span><span class="sxs-lookup"><span data-stu-id="39873-118">[Initialize Dapr](https://docs.dapr.io/getting-started/install-dapr/).</span></span> <span data-ttu-id="39873-119">この手順では、最新の Dapr バイナリとコンテナーイメージをインストールして、開発環境を設定します。</span><span class="sxs-lookup"><span data-stu-id="39873-119">This step sets up your development environment by installing the latest Dapr binaries and container images.</span></span>

1. <span data-ttu-id="39873-120">[.NET Core 3.1 SDK をインストールします](https://dotnet.microsoft.com/download/dotnet/3.1)。</span><span class="sxs-lookup"><span data-stu-id="39873-120">Install the [.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet/3.1).</span></span>

<span data-ttu-id="39873-121">Dapr がインストールされたので、次は、最初の Dapr アプリケーションを構築します。</span><span class="sxs-lookup"><span data-stu-id="39873-121">Now that Dapr is installed, it's time to build your first Dapr application!</span></span>

## <a name="build-your-first-dapr-application"></a><span data-ttu-id="39873-122">最初の Dapr アプリケーションを構築する</span><span class="sxs-lookup"><span data-stu-id="39873-122">Build your first Dapr application</span></span>

<span data-ttu-id="39873-123">まず、 [Dapr state management](state-management.md) ビルディングブロックを使用する単純な .net コンソールアプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="39873-123">You'll start by building a simple .NET Console application that consumes the [Dapr state management](state-management.md) building block.</span></span>

### <a name="create-the-application"></a><span data-ttu-id="39873-124">アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="39873-124">Create the application</span></span>

1. <span data-ttu-id="39873-125">任意のコマンドシェルまたはターミナルを開きます。</span><span class="sxs-lookup"><span data-stu-id="39873-125">Open up the command shell or terminal of your choice.</span></span> <span data-ttu-id="39873-126">[Visual Studio Code](https://code.visualstudio.com/)のターミナル機能について考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="39873-126">You might consider the terminal capabilities in [Visual Studio Code](https://code.visualstudio.com/).</span></span> <span data-ttu-id="39873-127">アプリケーションをビルドするルートフォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="39873-127">Navigate to the root folder in which you want to build your application.</span></span> <span data-ttu-id="39873-128">次のコマンドを入力して、新しい .NET コンソールアプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="39873-128">Once there, enter the following command to create a new .NET Console application:</span></span>

    ```dotnetcli
    dotnet new console -o DaprCounter
    ```

    <span data-ttu-id="39873-129">このコマンドは、単純な "Hello World" .NET Core アプリケーションをスキャフォールディングします。</span><span class="sxs-lookup"><span data-stu-id="39873-129">The command scaffolds a simple "Hello World" .NET Core application.</span></span>

1. <span data-ttu-id="39873-130">次に、前のコマンドで作成した新しいディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="39873-130">Then, navigate into the new directory created by the previous command:</span></span>

    ```console
    cd DaprCounter
    ```

1. <span data-ttu-id="39873-131">コマンドを使用して、新しく作成したアプリケーションを実行し `dotnet run` ます。</span><span class="sxs-lookup"><span data-stu-id="39873-131">Run the newly created application using the `dotnet run` command.</span></span> <span data-ttu-id="39873-132">これにより、"Hello World!" が書き込まれる</span><span class="sxs-lookup"><span data-stu-id="39873-132">Doing so writes "Hello World!"</span></span> <span data-ttu-id="39873-133">コンソール画面を表示するには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="39873-133">to the console screen:</span></span>

    ```dotnetcli
    dotnet run
    ```

### <a name="add-dapr-state-management"></a><span data-ttu-id="39873-134">Dapr 状態管理の追加</span><span class="sxs-lookup"><span data-stu-id="39873-134">Add Dapr State Management</span></span>

<span data-ttu-id="39873-135">次に、Dapr [state management ビルディングブロック](https://docs.dapr.io/developing-applications/building-blocks/state-management/state-management-overview/) を使用して、プログラムにステートフルカウンターを実装します。</span><span class="sxs-lookup"><span data-stu-id="39873-135">Next, you'll use the Dapr [state management building block](https://docs.dapr.io/developing-applications/building-blocks/state-management/state-management-overview/) to implement a stateful counter in the program.</span></span>

<span data-ttu-id="39873-136">Dapr の HTTP および gRPC のネイティブサポートを使用して、任意の開発プラットフォームで Dapr Api を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="39873-136">You can invoke Dapr APIs across any development platform using Dapr's native support for HTTP and gRPC.</span></span> <span data-ttu-id="39873-137">ただし、.NET 開発者は、Dapr .NET SDK をより自然で直感的に見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="39873-137">However, .NET Developers will find the Dapr .NET SDK more natural and intuitive.</span></span> <span data-ttu-id="39873-138">このメソッドは、厳密に型指定された .NET クライアントを使用して Dapr Api を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="39873-138">It provides a strongly typed .NET client to call the Dapr APIs.</span></span> <span data-ttu-id="39873-139">.NET SDK も ASP.NET Core と緊密に統合されています。</span><span class="sxs-lookup"><span data-stu-id="39873-139">The .NET SDK also tightly integrates with ASP.NET Core.</span></span>

1. <span data-ttu-id="39873-140">ターミナルウィンドウで、 `Dapr.Client` NuGet パッケージをアプリケーションに追加します。</span><span class="sxs-lookup"><span data-stu-id="39873-140">From the terminal window, add the `Dapr.Client` NuGet package to your application:</span></span>

    ```dotnetcli
    dotnet add package Dapr.Client
    ```

    > [!NOTE]
    > <span data-ttu-id="39873-141">Dapr のプレリリース版を使用している場合は、必ずフラグをコマンドに追加してください `--prerelease` 。</span><span class="sxs-lookup"><span data-stu-id="39873-141">If you're working with a pre-release version of Dapr, be sure to add the `--prerelease` flag to the command.</span></span>

1. <span data-ttu-id="39873-142">お気に入りの `Program.cs` エディターでファイルを開き、その内容を次のコードに更新します。</span><span class="sxs-lookup"><span data-stu-id="39873-142">Open the `Program.cs` file in your favorite editor and update its contents to the following code:</span></span>

    ```csharp
    using System;
    using System.Threading.Tasks;
    using Dapr.Client;

    namespace DaprCounter
    {
        class Program
        {
            static async Task Main(string[] args)
            {
                const string storeName = "statestore";
                const string key = "counter";

                var daprClient = new DaprClientBuilder().Build();
                var counter = await daprClient.GetStateAsync<int>(storeName, key);

                while (true)
                {
                    Console.WriteLine($"Counter = {counter++}");

                    await daprClient.SaveStateAsync(storeName, key, counter);
                    await Task.Delay(1000);
                }
            }
        }
    }
    ```

    <span data-ttu-id="39873-143">更新されたコードは、次の手順を実装します。</span><span class="sxs-lookup"><span data-stu-id="39873-143">The updated code implements the following steps:</span></span>

    - <span data-ttu-id="39873-144">最初に、新しい `DaprClient` インスタンスがインスタンス化されます。</span><span class="sxs-lookup"><span data-stu-id="39873-144">First a new `DaprClient` instance is instantiated.</span></span> <span data-ttu-id="39873-145">このクラスを使用すると、Dapr サイドカーを操作できます。</span><span class="sxs-lookup"><span data-stu-id="39873-145">This class enables you to interact with the Dapr sidecar.</span></span>
    - <span data-ttu-id="39873-146">状態ストアから、 `DaprClient.GetStateAsync` キーの値をフェッチし `counter` ます。</span><span class="sxs-lookup"><span data-stu-id="39873-146">From the state store, `DaprClient.GetStateAsync` fetches the value for the `counter` key.</span></span> <span data-ttu-id="39873-147">キーが存在しない場合は、既定 `int` 値 ( `0` ) が返されます。</span><span class="sxs-lookup"><span data-stu-id="39873-147">If the key doesn't exist, the default `int` value (which is `0`) is returned.</span></span>
    - <span data-ttu-id="39873-148">次に、コードは反復処理を行い、値をコンソールに書き込んで、 `counter` 増分値を状態ストアに保存します。</span><span class="sxs-lookup"><span data-stu-id="39873-148">The code then iterates, writing the `counter` value to the console and saving an incremented value to the state store.</span></span>

1. <span data-ttu-id="39873-149">Dapr CLI コマンドを実行すると、 `run` アプリケーションが開始されます。</span><span class="sxs-lookup"><span data-stu-id="39873-149">The Dapr CLI `run` command starts the application.</span></span> <span data-ttu-id="39873-150">このメソッドは、基になる dapr ランタイムを呼び出し、アプリケーションと dapr サイドカーの両方を同時に実行できるようにします。</span><span class="sxs-lookup"><span data-stu-id="39873-150">It invokes the underlying Dapr runtime and enables both the application and Dapr sidecar to run together.</span></span> <span data-ttu-id="39873-151">を省略した場合 `app-id` 、dapr はアプリケーションの一意の名前を生成します。</span><span class="sxs-lookup"><span data-stu-id="39873-151">If you omit the `app-id`, Dapr will generate a unique name for the application.</span></span> <span data-ttu-id="39873-152">コマンドの最後のセグメントは、 `dotnet run` .net core アプリケーションを実行するように Dapr ランタイムに指示します。</span><span class="sxs-lookup"><span data-stu-id="39873-152">The final segment of the command, `dotnet run`, instructs the Dapr runtime to run the .NET core application.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="39873-153">状態管理のビルディングブロックを使用する場合は、常に明示的なパラメーターを渡す必要があり `app-id` ます。</span><span class="sxs-lookup"><span data-stu-id="39873-153">Care must be taken to always pass an explicit `app-id` parameter when consuming the state management building block.</span></span> <span data-ttu-id="39873-154">ブロックでは、キーと値のペアごとに、その状態キーの *プレフィックス* としてアプリケーション id の値を使用します。</span><span class="sxs-lookup"><span data-stu-id="39873-154">The block uses the application id value as a *prefix* for its state key for each key/value pair.</span></span> <span data-ttu-id="39873-155">アプリケーション id が変更されると、以前に保存された状態にアクセスできなくなります。</span><span class="sxs-lookup"><span data-stu-id="39873-155">If the application id changes, you can no longer access the previously stored state.</span></span>

    <span data-ttu-id="39873-156">ここで、次のコマンドを使用してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="39873-156">Now run the application with the following command:</span></span>

    ```console
    dapr run --app-id DaprCounter dotnet run
    ```

    <span data-ttu-id="39873-157">アプリケーションを停止して再起動してみてください。</span><span class="sxs-lookup"><span data-stu-id="39873-157">Try stopping and restarting the application.</span></span> <span data-ttu-id="39873-158">カウンターがリセットされていないことがわかります。</span><span class="sxs-lookup"><span data-stu-id="39873-158">You'll see that the counter doesn't reset.</span></span> <span data-ttu-id="39873-159">代わりに、以前に保存した状態から続行します。</span><span class="sxs-lookup"><span data-stu-id="39873-159">Instead it continues from the previously saved state.</span></span> <span data-ttu-id="39873-160">Dapr 構成ブロックは、アプリケーションをステートフルにします。</span><span class="sxs-lookup"><span data-stu-id="39873-160">The Dapr building block makes the application stateful.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="39873-161">サンプルアプリケーションは、事前に構成された状態コンポーネントと通信しますが、直接依存関係がないことを理解しておくことが重要です。</span><span class="sxs-lookup"><span data-stu-id="39873-161">It's important to understand your sample application communicates with a pre-configured state component, but has no direct dependency on it.</span></span> <span data-ttu-id="39873-162">Dapr は依存関係を抽象化します。</span><span class="sxs-lookup"><span data-stu-id="39873-162">Dapr abstracts away the dependency.</span></span> <span data-ttu-id="39873-163">すぐにわかるように、基になる状態ストアコンポーネントは、単純な構成の更新を使用して変更できます。</span><span class="sxs-lookup"><span data-stu-id="39873-163">As you'll shortly see, the underlying state store component can be changed with a simple configuration update.</span></span>

<span data-ttu-id="39873-164">実際には状態が保存されていることに疑問があるかもしれません。</span><span class="sxs-lookup"><span data-stu-id="39873-164">You might be wondering, where exactly is the state stored?</span></span>

## <a name="component-configuration-files"></a><span data-ttu-id="39873-165">コンポーネント構成ファイル</span><span class="sxs-lookup"><span data-stu-id="39873-165">Component configuration files</span></span>

<span data-ttu-id="39873-166">ローカル環境に対して Dapr を最初に初期化したときに、Redis コンテナーが自動的にプロビジョニングされます。</span><span class="sxs-lookup"><span data-stu-id="39873-166">When you first initialized Dapr for your local environment, it automatically provisioned a Redis container.</span></span> <span data-ttu-id="39873-167">Dapr は、コンポーネント構成ファイル (権利あり) を使用して、Redis コンテナーを既定の状態ストアコンポーネントとして構成しました `statestore.yaml` 。</span><span class="sxs-lookup"><span data-stu-id="39873-167">Dapr then configured the Redis container as the default state store component with a component configuration file, entitled `statestore.yaml`.</span></span> <span data-ttu-id="39873-168">その内容を見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="39873-168">Here's a look at its contents:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: statestore
spec:
  type: state.redis
  version: v1
  metadata:
  - name: redisHost
    value: localhost:6379
  - name: redisPassword
    value: ""
  - name: actorStateStore
    value: "true"
```

> [!NOTE]
> <span data-ttu-id="39873-169">既定のコンポーネント構成ファイルは、 `$HOME/.dapr/components` Linux/macOS のフォルダーと Windows 上のフォルダーに格納され `%USERPROFILE%\.dapr\components` ます。</span><span class="sxs-lookup"><span data-stu-id="39873-169">Default component configuration files are stored in the `$HOME/.dapr/components` folder on Linux/macOS, and in the `%USERPROFILE%\.dapr\components` folder on Windows.</span></span>

<span data-ttu-id="39873-170">前のコンポーネント構成ファイルの形式に注意してください。</span><span class="sxs-lookup"><span data-stu-id="39873-170">Note the format of the previous component configuration file:</span></span>

- <span data-ttu-id="39873-171">各コンポーネントには名前があります。</span><span class="sxs-lookup"><span data-stu-id="39873-171">Each component has a name.</span></span> <span data-ttu-id="39873-172">上記のサンプルでは、という名前のコンポーネントが `statestore` あります。</span><span class="sxs-lookup"><span data-stu-id="39873-172">In the sample above, the component is named `statestore`.</span></span> <span data-ttu-id="39873-173">最初のコード例では、この名前を使用して、使用するコンポーネントを Dapr に指示しています。</span><span class="sxs-lookup"><span data-stu-id="39873-173">We used that name in our first code example to tell the Dapr sidecar which component to use.</span></span>
- <span data-ttu-id="39873-174">各コンポーネント構成ファイルには `spec` セクションがあります。</span><span class="sxs-lookup"><span data-stu-id="39873-174">Each component configuration file has a `spec` section.</span></span> <span data-ttu-id="39873-175">`type`コンポーネントの種類を指定するフィールドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="39873-175">It contains a `type` field that specifies the component type.</span></span> <span data-ttu-id="39873-176">フィールドは、 `version` コンポーネントのバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="39873-176">The `version` field specifies the component version.</span></span> <span data-ttu-id="39873-177">フィールドには、 `metadata` 接続の詳細やその他の設定など、コンポーネントに必要な情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="39873-177">The `metadata` field contains information that the component requires, such as connection details and other settings.</span></span> <span data-ttu-id="39873-178">メタデータ値は、コンポーネントの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="39873-178">The metadata values will vary for the different types of components.</span></span>

<span data-ttu-id="39873-179">Dapr サイドカーは、アプリケーションで構成されているすべての dapr コンポーネントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="39873-179">A Dapr sidecar can consume any Dapr component configured in your application.</span></span> <span data-ttu-id="39873-180">しかし、コンポーネントのアクセシビリティを制限するアーキテクチャ上の理由がある場合はどうでしょうか。</span><span class="sxs-lookup"><span data-stu-id="39873-180">But, what if you had an architectural justification to limit the accessibility of a component?</span></span> <span data-ttu-id="39873-181">Redis コンポーネントを、運用環境でのみ実行される Dapr サイドカーに制限するにはどうすればよいでしょうか。</span><span class="sxs-lookup"><span data-stu-id="39873-181">How could you restrict the Redis component to Dapr sidecars running only in a production environment?</span></span>

<span data-ttu-id="39873-182">これを行うには、 `namespace` 運用環境のを定義します。</span><span class="sxs-lookup"><span data-stu-id="39873-182">To do so, you could define a `namespace` for the production environment.</span></span> <span data-ttu-id="39873-183">名前を指定することもでき `production` ます。</span><span class="sxs-lookup"><span data-stu-id="39873-183">You might name it `production`.</span></span> <span data-ttu-id="39873-184">自己ホスト型モードでは、環境変数を設定することによって dapr サイドカーの名前空間を指定し `NAMESPACE` ます。</span><span class="sxs-lookup"><span data-stu-id="39873-184">In self-hosted mode, you specify the namespace of a Dapr sidecar by setting the `NAMESPACE` environment variable.</span></span> <span data-ttu-id="39873-185">構成した場合、Dapr サイドカーは、名前空間に一致するコンポーネントのみを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="39873-185">When configured, the Dapr sidecar will only load the components that match the namespace.</span></span> <span data-ttu-id="39873-186">Kubernetes のデプロイでは、Kubernetes 名前空間によって、読み込まれるコンポーネントが決まります。</span><span class="sxs-lookup"><span data-stu-id="39873-186">For Kubernetes deployments, the Kubernetes namespace determines the components that are loaded.</span></span> <span data-ttu-id="39873-187">次の例は、名前空間に配置された Redis コンポーネントを示して `production` います。</span><span class="sxs-lookup"><span data-stu-id="39873-187">The following sample shows the Redis component placed in a `production` namespace.</span></span> <span data-ttu-id="39873-188">要素内の宣言を確認し `namespace` `metadata` ます。</span><span class="sxs-lookup"><span data-stu-id="39873-188">Note the `namespace` declaration in the `metadata` element:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: statestore
  namespace: production
spec:
  type: state.redis
  version: v1
  metadata:
  - name: redisHost
    value: localhost:6379
  - name: redisPassword
    value: ""
  - name: actorStateStore
    value: "true"
```

> [!IMPORTANT]
> <span data-ttu-id="39873-189">名前空間のコンポーネントは、同じ名前空間で実行されているアプリケーションにのみアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="39873-189">A namespaced component is only accessible to applications running in the same namespace.</span></span> <span data-ttu-id="39873-190">Dapr アプリケーションがコンポーネントの読み込みに失敗した場合は、アプリケーションの名前空間が component 名前空間と一致していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="39873-190">If your Dapr application fails to load a component, make sure that the application namespace matches the component namespace.</span></span> <span data-ttu-id="39873-191">これは、アプリケーションの名前空間が環境変数に格納される自己ホスト型のモードでは特に注意が必要です `NAMESPACE` 。</span><span class="sxs-lookup"><span data-stu-id="39873-191">This can be especially tricky in self-hosted mode where the application namespace is stored in a `NAMESPACE` environment variable.</span></span>

<span data-ttu-id="39873-192">必要に応じて、コンポーネントを特定のアプリケーションに限定することもできます。</span><span class="sxs-lookup"><span data-stu-id="39873-192">If needed, you could further restrict a component to a particular application.</span></span> <span data-ttu-id="39873-193">名前空間内で、 `production` Redis cache へのアクセスをアプリケーションのみに制限することができ `DaprCounter` ます。</span><span class="sxs-lookup"><span data-stu-id="39873-193">Within the `production` namespace, you may want to limit access of the Redis cache to only the `DaprCounter` application.</span></span> <span data-ttu-id="39873-194">これを行うには `scopes` 、コンポーネントの構成でを指定します。</span><span class="sxs-lookup"><span data-stu-id="39873-194">You do so by specifying `scopes` in the component configuration.</span></span> <span data-ttu-id="39873-195">次の例は、Redis コンポーネントへのアクセスを `statestore` 名前空間内のアプリケーションに制限する方法を示してい `DaprCounter` `production` ます。</span><span class="sxs-lookup"><span data-stu-id="39873-195">The following example shows how to restrict access to the Redis `statestore` component to the application `DaprCounter` in the `production` namespace:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: statestore
  namespace: production
spec:
  type: state.redis
  version: v1
  metadata:
  - name: redisHost
    value: localhost:6379
  - name: redisPassword
    value: ""
  - name: actorStateStore
    value: "true"
  scopes:
  - DaprCounter
```

## <a name="build-a-multi-container-dapr-application"></a><span data-ttu-id="39873-196">複数コンテナーの Dapr アプリケーションを構築する</span><span class="sxs-lookup"><span data-stu-id="39873-196">Build a multi-container Dapr application</span></span>

<span data-ttu-id="39873-197">最初の例では、Dapr サイドカーとサイドバイサイドで実行された単純な .NET コンソールアプリケーションを作成しました。</span><span class="sxs-lookup"><span data-stu-id="39873-197">In the first example, you created a simple .NET console application that ran side-by-side with a Dapr sidecar.</span></span> <span data-ttu-id="39873-198">しかし、多くの場合、最新の分散アプリケーションは多くの移動パーツで構成されています。</span><span class="sxs-lookup"><span data-stu-id="39873-198">Modern distributed applications, however, often consist of many moving parts.</span></span> <span data-ttu-id="39873-199">これらのユーザーは、独立したマイクロサービスを同時に実行できます。</span><span class="sxs-lookup"><span data-stu-id="39873-199">They can simultaneously run independent microservices.</span></span> <span data-ttu-id="39873-200">これらのモダンアプリケーションは通常、コンテナー化され、Docker Compose や Kubernetes などのコンテナーオーケストレーションツールを必要とします。</span><span class="sxs-lookup"><span data-stu-id="39873-200">These modern applications are typically containerized and require container orchestration tools such as Docker Compose or Kubernetes.</span></span>

<span data-ttu-id="39873-201">次の例では、複数コンテナーアプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="39873-201">In the next example, you'll create a multi-container application.</span></span> <span data-ttu-id="39873-202">また、 [Dapr サービスの呼び出し](service-invocation.md) の構成要素を使用して、サービス間の通信を行います。</span><span class="sxs-lookup"><span data-stu-id="39873-202">You'll also use the [Dapr service invocation](service-invocation.md) building block to communicate between services.</span></span> <span data-ttu-id="39873-203">このソリューションは、web API から天気予報を取得する web アプリケーションで構成されます。</span><span class="sxs-lookup"><span data-stu-id="39873-203">The solution will consist of a web application that retrieves weather forecasts from a web API.</span></span> <span data-ttu-id="39873-204">これらはそれぞれ、Docker コンテナーで実行されます。</span><span class="sxs-lookup"><span data-stu-id="39873-204">They will each run in a Docker container.</span></span> <span data-ttu-id="39873-205">Docker Compose を使用して、コンテナーをローカルで実行し、デバッグ機能を有効にします。</span><span class="sxs-lookup"><span data-stu-id="39873-205">You'll use Docker Compose to run the container locally and enable debugging capabilities.</span></span>

<span data-ttu-id="39873-206">Dapr 用のローカル環境を構成し、 [.Net Core 3.1 開発ツール](https://dotnet.microsoft.com/download/dotnet-core/3.1) をインストールしたことを確認します (手順については、この章の最初で説明しています)。</span><span class="sxs-lookup"><span data-stu-id="39873-206">Make sure you've configured your local environment for Dapr and installed the [.NET Core 3.1 Development Tools](https://dotnet.microsoft.com/download/dotnet-core/3.1) (instructions are available at the beginning of this chapter).</span></span>

<span data-ttu-id="39873-207">また、 **.Net Core クロスプラットフォーム開発** ワークロードがインストールされた [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)を使用して、このサンプルを完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="39873-207">Additionally, you'll need complete this sample using [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) with the **.NET Core cross-platform development** workload installed.</span></span>

### <a name="create-the-application"></a><span data-ttu-id="39873-208">アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="39873-208">Create the application</span></span>

1. <span data-ttu-id="39873-209">Visual Studio 2019 で **ASP.NET Core Web アプリ** プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="39873-209">In Visual Studio 2019, create an **ASP.NET Core Web App** project:</span></span>

    :::image type="content" source="./media/getting-started/multicontainer-createproject.png" alt-text="新しいプロジェクトの作成のスクリーンショット":::

1. <span data-ttu-id="39873-211">プロジェクト `DaprFrontEnd` とソリューションの名前を指定し `DaprMultiContainer` ます。</span><span class="sxs-lookup"><span data-stu-id="39873-211">Name your project `DaprFrontEnd` and your solution `DaprMultiContainer`:</span></span>

    :::image type="content" source="./media/getting-started/multicontainer-configureproject.png" alt-text="新しいプロジェクトの構成のスクリーンショット":::

1. <span data-ttu-id="39873-213">**[Web アプリケーション]** を選択し、Razor Pages を使用して Web アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="39873-213">Select **Web Application** to create a web application with Razor pages.</span></span> <span data-ttu-id="39873-214">[Enable Docker Support]\(Docker サポートを有効にする\) は **選択しないで** ください。</span><span class="sxs-lookup"><span data-stu-id="39873-214">Don't select **Enable Docker Support**.</span></span> <span data-ttu-id="39873-215">Docker サポートは、後で追加します。</span><span class="sxs-lookup"><span data-stu-id="39873-215">You'll add Docker support later.</span></span>

    :::image type="content" source="./media/getting-started/multicontainer-createwebapp.png" alt-text="新しい ASP.NET Core web アプリケーションの作成のスクリーンショット":::

1. <span data-ttu-id="39873-217">ASP.NET Core Web API プロジェクトを同じソリューションに追加し、 _DaprBackEnd_ という呼び出しを行います。</span><span class="sxs-lookup"><span data-stu-id="39873-217">Add a ASP.NET Core Web API project to the same solution and call it _DaprBackEnd_.</span></span> <span data-ttu-id="39873-218">プロジェクトの種類として [ **API** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="39873-218">Select **API** as the project type.</span></span> <span data-ttu-id="39873-219">既定では、dapr サイドカーは、パブリック API へのアクセスを制限するためにネットワーク境界に依存しています。</span><span class="sxs-lookup"><span data-stu-id="39873-219">By default, a Dapr sidecar relies on the network boundary to limit access to its public API.</span></span> <span data-ttu-id="39873-220">そのため、[ **HTTPS 用に構成**] のチェックボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="39873-220">So, clear the checkbox for **Configure for HTTPS**.</span></span>

    :::image type="content" source="./media/getting-started/multicontainer-createwebapi.png" alt-text="Web API の作成のスクリーンショット":::

### <a name="add-dapr-service-invocation"></a><span data-ttu-id="39873-222">Dapr サービスの呼び出しの追加</span><span class="sxs-lookup"><span data-stu-id="39873-222">Add Dapr service invocation</span></span>

<span data-ttu-id="39873-223">ここでは、Dapr [サービス呼び出し構成ブロック](https://docs.dapr.io/developing-applications/building-blocks/service-invocation/service-invocation-overview/)を使用して、サービス間の通信を構成します。</span><span class="sxs-lookup"><span data-stu-id="39873-223">Now, you'll configure communication between the services using Dapr [service invocation building block](https://docs.dapr.io/developing-applications/building-blocks/service-invocation/service-invocation-overview/).</span></span> <span data-ttu-id="39873-224">Web アプリで web API から天気予報を取得できるようにします。</span><span class="sxs-lookup"><span data-stu-id="39873-224">You'll enable the web app to retrieve weather forecasts from the web API.</span></span> <span data-ttu-id="39873-225">サービス呼び出しの構成ブロックには、多くの利点があります。</span><span class="sxs-lookup"><span data-stu-id="39873-225">The service invocation building block features many benefits.</span></span> <span data-ttu-id="39873-226">これには、サービスの検出、自動再試行、メッセージの暗号化 (mTLS を使用)、改善された可観測性が含まれます。</span><span class="sxs-lookup"><span data-stu-id="39873-226">It includes service discovery, automatic retries, message encryption (using mTLS), and improved observability.</span></span> <span data-ttu-id="39873-227">Dapr sidecar でサービス呼び出し API を呼び出すには、Dapr .NET SDK を使用します。</span><span class="sxs-lookup"><span data-stu-id="39873-227">You'll use the Dapr .NET SDK to invoke the service invocation API on the Dapr sidecar.</span></span>

1. <span data-ttu-id="39873-228">Visual Studio で、パッケージマネージャーコンソール ([**ツール > NuGet パッケージマネージャー > パッケージマネージャーコンソール**) を開き、 `DaprFrontEnd` が既定のプロジェクトであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="39873-228">In Visual Studio, open the Package Manager Console (**Tools > NuGet Package Manager > Package Manager Console**) and make sure that `DaprFrontEnd` is the default project.</span></span> <span data-ttu-id="39873-229">コンソールで、 `Dapr.AspNetCore` NuGet パッケージをプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="39873-229">From the console, add the `Dapr.AspNetCore` NuGet package to the project:</span></span>

    ```powershell
    Install-Package Dapr.AspNetCore
    ```

    > [!NOTE]
    > <span data-ttu-id="39873-230">プレリリースされているのバージョンを対象としている場合は、 `Dapr.AspNetCore` フラグを指定する必要があり `-Prerelease` ます。</span><span class="sxs-lookup"><span data-stu-id="39873-230">If you're targeting a version of `Dapr.AspNetCore` that is in prerelease, you need to specify the `-Prerelease` flag.</span></span>

1. <span data-ttu-id="39873-231">プロジェクトで `DaprFrontEnd` *Startup.cs* ファイルを開き、 `ConfigureServices` メソッドを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="39873-231">In the `DaprFrontEnd` project, open the *Startup.cs* file, and replace the `ConfigureServices` method with the following code:</span></span>

    ```csharp
    // This method gets called by the runtime. Use this method to add services to the container.
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddControllers().AddDapr();
        services.AddRazorPages();
    }
    ```

    <span data-ttu-id="39873-232">を呼び出すと、 `AddDapr` `DaprClient` ASP.NET Core 依存関係の挿入システムにクラスが登録されます。</span><span class="sxs-lookup"><span data-stu-id="39873-232">The call to `AddDapr` registers the `DaprClient` class with the ASP.NET Core dependency injection system.</span></span> <span data-ttu-id="39873-233">後で、クラスを使用して `DaprClient` Dapr sidecar と通信します。</span><span class="sxs-lookup"><span data-stu-id="39873-233">You'll use the `DaprClient` class later on to communicate with the Dapr sidecar.</span></span>

1. <span data-ttu-id="39873-234">*WeatherForecast* という名前の新しい C# クラスファイルをプロジェクトに追加し `DaprFrontEnd` ます。</span><span class="sxs-lookup"><span data-stu-id="39873-234">Add a new C# class file named *WeatherForecast* to the `DaprFrontEnd` project:</span></span>

    ```csharp
    using System;

    namespace DaprFrontEnd
    {
        public class WeatherForecast
        {
            public DateTime Date { get; set; }

            public int TemperatureC { get; set; }

            public int TemperatureF { get; set; }

            public string Summary { get; set; }
        }
    }
    ```

1. <span data-ttu-id="39873-235">*Pages* フォルダーの *Index.cshtml.cs* ファイルを開き、その内容を次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="39873-235">Open the *Index.cshtml.cs* file in the *Pages* folder, and replace its contents with the following code:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Net.Http;
    using System.Threading.Tasks;
    using Dapr.Client;
    using Microsoft.AspNetCore.Mvc.RazorPages;

    namespace DaprFrontEnd.Pages
    {
        public class IndexModel : PageModel
        {
            private readonly DaprClient _daprClient;

            public IndexModel(DaprClient daprClient)
            {
                _daprClient = daprClient ?? throw new ArgumentNullException(nameof(daprClient));
            }

            public async Task OnGet()
            {
                var forecasts = await _daprClient.InvokeMethodAsync<IEnumerable<WeatherForecast>>(
                    HttpMethod.Get,
                    "daprbackend",
                    "weatherforecast");

                ViewData["WeatherForecastData"] = forecasts;
            }
        }
    }
    ```

    <span data-ttu-id="39873-236">クラスをコンストラクターに挿入することによって、Dapr 機能を web アプリに追加し `DaprClient` `IndexModel` ます。</span><span class="sxs-lookup"><span data-stu-id="39873-236">You add Dapr capabilities into the web app by injecting the `DaprClient` class into `IndexModel` constructor.</span></span> <span data-ttu-id="39873-237">メソッドでは、 `OnGet` Dapr サービスの呼び出し構成ブロックを使用して、API サービスを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="39873-237">In the `OnGet` method, you call the API service with the Dapr service invocation building block.</span></span> <span data-ttu-id="39873-238">メソッドは、 `OnGet` ユーザーがホームページにアクセスするたびに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="39873-238">The `OnGet` method is invoked whenever a user visits the home page.</span></span> <span data-ttu-id="39873-239">`DaprClient.InvokeMethodAsync`サービスのメソッドを呼び出すには、メソッドを使用し `weatherforecast` `daprbackend` ます。</span><span class="sxs-lookup"><span data-stu-id="39873-239">You use the `DaprClient.InvokeMethodAsync` method to invoke the `weatherforecast` method of the `daprbackend` service.</span></span> <span data-ttu-id="39873-240">`daprbackend`後で Dapr で実行するように構成するときに、アプリケーション ID として使用するように WEB API を構成します。</span><span class="sxs-lookup"><span data-stu-id="39873-240">You'll configure the web API to use `daprbackend` as its application ID later on when configuring it to run with Dapr.</span></span> <span data-ttu-id="39873-241">最後に、サービス応答がビューデータに保存されます。</span><span class="sxs-lookup"><span data-stu-id="39873-241">Finally, the service response is saved in view data.</span></span>

1. <span data-ttu-id="39873-242">*Pages* フォルダー内の *Index. cshtml* ファイルの内容を次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="39873-242">Replace the contents of the *Index.cshtml* file in the *Pages* folder, with the following code.</span></span> <span data-ttu-id="39873-243">ビューデータに格納されている天気予報がユーザーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="39873-243">It displays the weather forecasts stored in the view data to the user:</span></span>

    ```razor
    @page
    @model IndexModel
    @{
        ViewData["Title"] = "Home page";
    }

    <div class="text-center">
        <h1 class="display-4">Welcome</h1>
        <p>Learn about <a href="https://docs.microsoft.com/aspnet/core">building Web apps with ASP.NET Core</a>.</p>
        @foreach (var forecast in (IEnumerable<WeatherForecast>)ViewData["WeatherForecastData"])
        {
            <p>The forecast for @forecast.Date is @forecast.Summary!</p>
        }
    </div>
    ```

### <a name="add-container-support"></a><span data-ttu-id="39873-244">コンテナー サポートを追加する</span><span class="sxs-lookup"><span data-stu-id="39873-244">Add container support</span></span>

<span data-ttu-id="39873-245">この例の最後の部分では、コンテナーのサポートを追加し、Docker Compose を使用してソリューションを実行します。</span><span class="sxs-lookup"><span data-stu-id="39873-245">In the final part of this example, you'll add container support and run the solution using Docker Compose.</span></span>

1. <span data-ttu-id="39873-246">プロジェクトを右クリック `DaprFrontEnd` し、[   >  **コンテナー Orchestrator サポート** の追加] を選択します。</span><span class="sxs-lookup"><span data-stu-id="39873-246">Right-click the `DaprFrontEnd` project, and choose **Add** > **Container Orchestrator Support**.</span></span> <span data-ttu-id="39873-247">[ **コンテナー Orchestrator サポートの追加** ] ダイアログが表示されます。</span><span class="sxs-lookup"><span data-stu-id="39873-247">The **Add Container Orchestrator Support** dialog appears:</span></span>

    :::image type="content" source="./media/getting-started/multicontainer-addorchestrator.png" alt-text="コンテナー orchestrator サポートの追加のスクリーンショット":::

    <span data-ttu-id="39873-249">**[Docker Compose]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="39873-249">Choose **Docker Compose**.</span></span>

1. <span data-ttu-id="39873-250">次のダイアログボックスで、ターゲット OS として [ **Linux** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="39873-250">In the next dialog, select **Linux** as the Target OS:</span></span>

    :::image type="content" source="./media/getting-started/multicontainer-targetos.png" alt-text="Docker ターゲット OS の選択のスクリーンショット":::

    <span data-ttu-id="39873-252">Visual Studio によって、ソリューションの **docker-作成** フォルダーに *docker-compose.yml* ファイルと *dockerignore* ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="39873-252">Visual Studio creates a *docker-compose.yml* file and a *.dockerignore* file in the **docker-compose** folder in the solution:</span></span>

    :::image type="content" source="./media/getting-started/multicontainer-dockersolution.png" alt-text="Docker 作成プロジェクトのスクリーンショット":::

    <span data-ttu-id="39873-254">*Docker-compose.yml* ファイルには、次の内容が含まれています。</span><span class="sxs-lookup"><span data-stu-id="39873-254">The *docker-compose.yml* file has the following content:</span></span>

    ```yaml
    version: "3.4"

    services:
      daprfrontend:
        image: ${DOCKER_REGISTRY-}daprfrontend
        build:
          context: .
          dockerfile: DaprFrontEnd/Dockerfile
    ```

    <span data-ttu-id="39873-255">*.dockerignore* ファイルには、Docker によってコンテナーに含める必要のないファイルの種類と拡張機能が含まれます。</span><span class="sxs-lookup"><span data-stu-id="39873-255">The *.dockerignore* file contains file types and extensions that you don't want Docker to include in the container.</span></span> <span data-ttu-id="39873-256">これらのファイルは開発環境とソース管理に関連付けられており、デプロイするアプリやサービスには関連付けられていません。</span><span class="sxs-lookup"><span data-stu-id="39873-256">These files are associated with the development environment and source control and not the app or service you're deploying.</span></span>

    <span data-ttu-id="39873-257">*DaprFrontEnd* プロジェクトディレクトリのルートに、新しい *dockerfile* が作成されました。</span><span class="sxs-lookup"><span data-stu-id="39873-257">In the root of the *DaprFrontEnd* project directory, a new *Dockerfile* was created.</span></span> <span data-ttu-id="39873-258">*Dockerfile* は、イメージをビルドするために使用される一連のコマンドです。</span><span class="sxs-lookup"><span data-stu-id="39873-258">A *Dockerfile* is a sequence of commands that are used to build an image.</span></span> <span data-ttu-id="39873-259">詳細については、「 [Dockerfile リファレンス](https://docs.docker.com/engine/reference/builder)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39873-259">For more information, see [Dockerfile reference](https://docs.docker.com/engine/reference/builder).</span></span>

    <span data-ttu-id="39873-260">*Dockerfile* には、yaml が含まれています。</span><span class="sxs-lookup"><span data-stu-id="39873-260">The *Dockerfile* contains the YAML:</span></span>

    ```yml
    FROM mcr.microsoft.com/dotnet/aspnet:3.1 AS base
    WORKDIR /app
    EXPOSE 80
    EXPOSE 443

    FROM mcr.microsoft.com/dotnet/sdk:3.1 AS build
    WORKDIR /src
    COPY ["DaprFrontEnd/DaprFrontEnd.csproj", "DaprFrontEnd/"]
    RUN dotnet restore "DaprFrontEnd/DaprFrontEnd.csproj"
    COPY . .
    WORKDIR "/src/DaprFrontEnd"
    RUN dotnet build "DaprFrontEnd.csproj" -c Release -o /app/build

    FROM build AS publish
    RUN dotnet publish "DaprFrontEnd.csproj" -c Release -o /app/publish

    FROM base AS final
    WORKDIR /app
    COPY --from=publish /app/publish .
    ENTRYPOINT ["dotnet", "DaprFrontEnd.dll"]
    ```

    <span data-ttu-id="39873-261">前の *Dockerfile* は、呼び出されると、次の手順を順番に実行します。</span><span class="sxs-lookup"><span data-stu-id="39873-261">The preceding *Dockerfile* sequentially performs the following steps when invoked:</span></span>

    1. <span data-ttu-id="39873-262">イメージを取得し、 `mcr.microsoft.com/dotnet/aspnet:3.1` 名前をに `base` します。</span><span class="sxs-lookup"><span data-stu-id="39873-262">Pulls the `mcr.microsoft.com/dotnet/aspnet:3.1` image and names it `base`.</span></span>
    1. <span data-ttu-id="39873-263">作業ディレクトリを */アプリ* に設定します。</span><span class="sxs-lookup"><span data-stu-id="39873-263">Sets the working directory to */app*.</span></span>
    1. <span data-ttu-id="39873-264">ポート `80` とを公開 `443` します。</span><span class="sxs-lookup"><span data-stu-id="39873-264">Exposes port `80` and `443`.</span></span>
    1. <span data-ttu-id="39873-265">イメージを取得し、 `mcr.microsoft.com/dotnet/sdk:3.1` 名前をに `build` します。</span><span class="sxs-lookup"><span data-stu-id="39873-265">Pulls the `mcr.microsoft.com/dotnet/sdk:3.1` image and names it `build`.</span></span>
    1. <span data-ttu-id="39873-266">作業ディレクトリを */src* に設定します。</span><span class="sxs-lookup"><span data-stu-id="39873-266">Sets the working directory to */src*.</span></span>
    1. <span data-ttu-id="39873-267">_DaprFrontEnd/DaprFrontEnd_ を *DaprFrontEnd/* という名前の新しいディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="39873-267">Copies the _DaprFrontEnd/DaprFrontEnd.csproj_ to a new directory named *DaprFrontEnd/*.</span></span>
    1. <span data-ttu-id="39873-268">[`dotnet restore`](../../core/tools/dotnet-restore.md)プロジェクトでを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="39873-268">Calls [`dotnet restore`](../../core/tools/dotnet-restore.md) on the project.</span></span>
    1. <span data-ttu-id="39873-269">ルートディレクトリからイメージのルートにすべてをコピーします。</span><span class="sxs-lookup"><span data-stu-id="39873-269">Copies everything from the root directory into the image's root.</span></span>
    1. <span data-ttu-id="39873-270">作業ディレクトリを _/src/DaprFrontEnd_ に設定します。</span><span class="sxs-lookup"><span data-stu-id="39873-270">Sets the working directory to _/src/DaprFrontEnd_.</span></span>
    1. <span data-ttu-id="39873-271">[`dotnet build`](../../core/tools/dotnet-build.md)プロジェクトでを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="39873-271">Calls [`dotnet build`](../../core/tools/dotnet-build.md) on the project.</span></span>
        - <span data-ttu-id="39873-272">**リリース** 構成をターゲットにして、 */app/build* に出力します。</span><span class="sxs-lookup"><span data-stu-id="39873-272">Targeting the **Release** configuration and outputs to */app/build*.</span></span>
    1. <span data-ttu-id="39873-273">既存の基本イメージから新しいビルドステージを初期化し、名前をに `build` `publish` します。</span><span class="sxs-lookup"><span data-stu-id="39873-273">Initializes a new build stage from the existing `build` base image and names it `publish`.</span></span>
    1. <span data-ttu-id="39873-274">`dotnet publish`プロジェクトでを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="39873-274">Calls `dotnet publish` on the project.</span></span>
        - <span data-ttu-id="39873-275">**リリース** 構成をターゲットにして、 */app/publish* に出力します。</span><span class="sxs-lookup"><span data-stu-id="39873-275">Targeting the **Release** configuration and outputs to */app/publish*.</span></span>
    1. <span data-ttu-id="39873-276">既存の基本イメージから新しいビルドステージを初期化し、名前をに `publish` `final` します。</span><span class="sxs-lookup"><span data-stu-id="39873-276">Initializes a new build stage from the existing `publish` base image and names it `final`.</span></span>
    1. <span data-ttu-id="39873-277">作業ディレクトリを */アプリ* に設定します。</span><span class="sxs-lookup"><span data-stu-id="39873-277">Sets the working directory to */app*.</span></span>
    1. <span data-ttu-id="39873-278">イメージ `/app/publish` のディレクトリを `publish` イメージのルートにコピーし `final` ます。</span><span class="sxs-lookup"><span data-stu-id="39873-278">Copies the `/app/publish` directory from the `publish` image into the root of the `final` image.</span></span>
    1. <span data-ttu-id="39873-279">エントリポイントをイメージとしてに設定 `dotnet` し、を `DaprFrontEnd.dll` arg として渡します。</span><span class="sxs-lookup"><span data-stu-id="39873-279">Sets the entry point as the image to `dotnet` and passes the `DaprFrontEnd.dll` as an arg.</span></span>

1. <span data-ttu-id="39873-280">`DaprBackEnd`Web API プロジェクトで、プロジェクトノードを右クリックし、[   >  **コンテナー Orchestrator サポート** の追加] を選択します。</span><span class="sxs-lookup"><span data-stu-id="39873-280">In the `DaprBackEnd` web API project, right-click on the project node, and choose **Add** > **Container Orchestrator Support**.</span></span> <span data-ttu-id="39873-281">[ **Docker Compose**] を選択し、ターゲット OS として [ **Linux** ] をもう一度選択します。</span><span class="sxs-lookup"><span data-stu-id="39873-281">Choose **Docker Compose**, and then select **Linux** again as the target OS.</span></span>

    <span data-ttu-id="39873-282">_DaprBackEnd_ プロジェクトディレクトリのルートに、新しい *dockerfile* が作成されました。</span><span class="sxs-lookup"><span data-stu-id="39873-282">In the root of the _DaprBackEnd_ project directory, a new *Dockerfile* was created.</span></span> <span data-ttu-id="39873-283">*Dockerfile* には、次の yaml が含まれています。</span><span class="sxs-lookup"><span data-stu-id="39873-283">The *Dockerfile* contains the following YAML:</span></span>

    ```yml
    FROM mcr.microsoft.com/dotnet/aspnet:3.1 AS base
    WORKDIR /app
    EXPOSE 80

    FROM mcr.microsoft.com/dotnet/sdk:3.1 AS build
    WORKDIR /src
    COPY ["DaprBackEnd/DaprBackEnd.csproj", "DaprBackEnd/"]
    RUN dotnet restore "DaprBackEnd/DaprBackEnd.csproj"
    COPY . .
    WORKDIR "/src/DaprBackEnd"
    RUN dotnet build "DaprBackEnd.csproj" -c Release -o /app/build

    FROM build AS publish
    RUN dotnet publish "DaprBackEnd.csproj" -c Release -o /app/publish

    FROM base AS final
    WORKDIR /app
    COPY --from=publish /app/publish .
    ENTRYPOINT ["dotnet", "DaprBackEnd.dll"]
    ```

    <span data-ttu-id="39873-284">*Docker-compose.yml* ファイルをもう一度開き、内容を確認します。</span><span class="sxs-lookup"><span data-stu-id="39873-284">Open the *docker-compose.yml* file again and examine its contents.</span></span> <span data-ttu-id="39873-285">Visual Studio によって **Docker Compose** ファイルが更新されました。</span><span class="sxs-lookup"><span data-stu-id="39873-285">Visual Studio has updated the **Docker Compose** file.</span></span> <span data-ttu-id="39873-286">2つのサービスが含まれるようになりました。</span><span class="sxs-lookup"><span data-stu-id="39873-286">Now both services are included:</span></span>

    ```yaml
    version: '3.4'

    services:
      daprfrontend:
        image: ${DOCKER_REGISTRY-}daprfrontend
        build:
          context: .
          dockerfile: DaprFrontEnd/Dockerfile

      daprbackend:
        image: ${DOCKER_REGISTRY-}daprbackend
        build:
          context: .
          dockerfile: DaprBackEnd/Dockerfile
    ```

1. <span data-ttu-id="39873-287">コンテナー化されたアプリケーション内から Dapr 構成ブロックを使用するには、作成ファイルに Dapr サイドカーコンテナーを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="39873-287">To use Dapr building blocks from inside a containerized application, you'll need to add the Dapr sidecars containers to your Compose file.</span></span> <span data-ttu-id="39873-288">次の例に一致するように、 *docker-compose.yml* ファイルの内容を慎重に更新します。</span><span class="sxs-lookup"><span data-stu-id="39873-288">Carefully update the content of the *docker-compose.yml* file to match the following example.</span></span> <span data-ttu-id="39873-289">書式設定と間隔に注意してください。タブは使用しません。</span><span class="sxs-lookup"><span data-stu-id="39873-289">Pay close attention to the formatting and spacing and don't use tabs.</span></span>

    ```yaml
    version: '3.4'
    
    services:
      daprfrontend:
        image: ${DOCKER_REGISTRY-}daprfrontend
        build:
          context: .
          dockerfile: DaprFrontEnd/Dockerfile
        ports:
          - "51000:50001"

      daprfrontend-dapr:
        image: "daprio/daprd:latest"
        command: [ "./daprd", "-app-id", "daprfrontend", "-app-port", "80" ]
        depends_on:
          - daprfrontend
        network_mode: "service:daprfrontend"

      daprbackend:
        image: ${DOCKER_REGISTRY-}daprbackend
        build:
          context: .
          dockerfile: DaprBackEnd/Dockerfile
        ports:
          - "52000:50001"

      daprbackend-dapr:
        image: "daprio/daprd:latest"
        command: [ "./daprd", "-app-id", "daprbackend", "-app-port", "80" ]
        depends_on:
          - daprfrontend
        network_mode: "service:daprbackend"
    ```

    <span data-ttu-id="39873-290">更新されたファイルでは、 `daprfrontend-dapr` `daprbackend-dapr` サービスとサービスにそれぞれ追加されて `daprfrontend` `daprbackend` います。</span><span class="sxs-lookup"><span data-stu-id="39873-290">In the updated file, we've added `daprfrontend-dapr` and `daprbackend-dapr` sidecars for the `daprfrontend` and `daprbackend` services respectively.</span></span> <span data-ttu-id="39873-291">更新されたファイルで、次の変更に注意してください。</span><span class="sxs-lookup"><span data-stu-id="39873-291">In the updated file, pay close attention to the following changes:</span></span>

    - <span data-ttu-id="39873-292">サイドカーは、コンテナーイメージを使用し `daprio/daprd:latest` ます。</span><span class="sxs-lookup"><span data-stu-id="39873-292">The sidecars use the `daprio/daprd:latest` container image.</span></span> <span data-ttu-id="39873-293">`latest`運用環境のシナリオでは、タグを使用しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="39873-293">The use of the `latest` tag isn't recommended for production scenarios.</span></span> <span data-ttu-id="39873-294">運用環境では、特定のバージョン番号を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="39873-294">For production, it's better to use a specific version number.</span></span>
    - <span data-ttu-id="39873-295">作成ファイルで定義されている各サービスには、ネットワークの分離を目的とした独自のネットワーク名前空間があります。</span><span class="sxs-lookup"><span data-stu-id="39873-295">Each service defined in the Compose file has its own network namespace for network isolation purposes.</span></span> <span data-ttu-id="39873-296">サイドカーは、 `network_mode: "service:..."` アプリケーションと同じネットワーク名前空間で実行されることを保証するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="39873-296">The sidecars use `network_mode: "service:..."` to ensure they run in the same network namespace as the application.</span></span> <span data-ttu-id="39873-297">これにより、を使用して、サイドカーとアプリケーションが通信できるように `localhost` なります。</span><span class="sxs-lookup"><span data-stu-id="39873-297">Doing so allows the sidecar and the application to communicate using `localhost`.</span></span>
    - <span data-ttu-id="39873-298">Dapr サイドカーが gRPC 通信をリッスンしているポート (既定では 50001) を公開して、sidecars が相互に通信できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="39873-298">The ports on which the Dapr sidecars are listening for gRPC communication (by default 50001) must be exposed to allow the sidecars to communicate with each other.</span></span>

1. <span data-ttu-id="39873-299">ソリューション (<kbd>F5</kbd> キーまたは <kbd>Ctrl + F5</kbd>キー) を実行して、予期したとおりに動作することを確認します。</span><span class="sxs-lookup"><span data-stu-id="39873-299">Run the solution (<kbd>F5</kbd> or <kbd>Ctrl+F5</kbd>) to verify that it works as expected.</span></span> <span data-ttu-id="39873-300">すべてが正しく構成されている場合は、天気予報データが表示されます。</span><span class="sxs-lookup"><span data-stu-id="39873-300">If everything is configured correctly, you should see the weather forecast data:</span></span>

    :::image type="content" source="./media/getting-started/multicontainer-result.png" alt-text="気象予測データを示す最後のソリューションのスクリーンショット":::

    <span data-ttu-id="39873-302">Docker Compose と Visual Studio 2019 を使用してローカルで実行すると、ブレークポイントを設定し、アプリケーションにデバッグできます。</span><span class="sxs-lookup"><span data-stu-id="39873-302">Running locally with Docker Compose and Visual Studio 2019, you can set breakpoints and debug into the application.</span></span> <span data-ttu-id="39873-303">運用環境のシナリオでは、Kubernetes でアプリケーションをホストすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="39873-303">For production scenarios, it's recommended to host your application in Kubernetes.</span></span> <span data-ttu-id="39873-304">この本には、Kubernetes にデプロイするためのスクリプトを含む、付属の参照アプリケーション [eShopOnDapr](https://github.com/dotnet-architecture/eShopOnDapr)が含まれています。</span><span class="sxs-lookup"><span data-stu-id="39873-304">This book includes an accompanying reference application, [eShopOnDapr](https://github.com/dotnet-architecture/eShopOnDapr), that contains scripts to deploy to Kubernetes.</span></span>

    <span data-ttu-id="39873-305">このチュートリアルで使用する Dapr サービス呼び出しの構成ブロックの詳細については、 [6 章](service-invocation.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39873-305">To learn more about the Dapr service invocation building block used in this walkthrough, refer to [chapter 6](service-invocation.md).</span></span>

## <a name="summary"></a><span data-ttu-id="39873-306">まとめ</span><span class="sxs-lookup"><span data-stu-id="39873-306">Summary</span></span>

<span data-ttu-id="39873-307">この章では、dapr ドライブを *テスト* する機会がありました。</span><span class="sxs-lookup"><span data-stu-id="39873-307">In this chapter, you had an opportunity to *test drive* Dapr.</span></span> <span data-ttu-id="39873-308">Dapr .NET SDK を使用して、Dapr が .NET アプリケーションプラットフォームと統合されていることを確認しました。</span><span class="sxs-lookup"><span data-stu-id="39873-308">Using the Dapr .NET SDK, you saw how Dapr integrates with the .NET application platform.</span></span>

<span data-ttu-id="39873-309">最初の例は、Dapr state management ビルディングブロックを使用した、単純なステートフルな .NET コンソールアプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="39873-309">The first example was a simple, stateful, .NET Console application that used the Dapr state management building block.</span></span>

<span data-ttu-id="39873-310">2番目の例では、Docker で実行されている複数コンテナーアプリケーションを使用しています。</span><span class="sxs-lookup"><span data-stu-id="39873-310">The second example involved a multi-container application running in Docker.</span></span> <span data-ttu-id="39873-311">Docker Compose で Visual Studio を使用することにより、すべての .NET アプリで使い慣れた *F5 デバッグエクスペリエンス* を利用できました。</span><span class="sxs-lookup"><span data-stu-id="39873-311">By using Visual Studio with Docker Compose, you experienced the familiar *F5 debugging experience* available across all .NET apps.</span></span>

<span data-ttu-id="39873-312">また、Dapr コンポーネント構成ファイルについても詳しく見ていきます。</span><span class="sxs-lookup"><span data-stu-id="39873-312">You also got a closer look at Dapr component configuration files.</span></span> <span data-ttu-id="39873-313">これらは、Dapr 構成要素によって使用される実際のインフラストラクチャ実装を構成します。</span><span class="sxs-lookup"><span data-stu-id="39873-313">They configure the actual infrastructure implementation used by the Dapr building blocks.</span></span> <span data-ttu-id="39873-314">名前空間とスコープを使用すると、特定の環境やアプリケーションへのコンポーネントアクセスを制限できます。</span><span class="sxs-lookup"><span data-stu-id="39873-314">You can use namespaces and scopes to restrict component access to particular environments and applications.</span></span>

<span data-ttu-id="39873-315">今後の章では、Dapr によって提供される構成要素について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="39873-315">In the upcoming chapters, you'll dive deep into the building blocks offered by Dapr.</span></span>

### <a name="references"></a><span data-ttu-id="39873-316">関連項目</span><span class="sxs-lookup"><span data-stu-id="39873-316">References</span></span>

- [<span data-ttu-id="39873-317">Dapr のドキュメント-概要</span><span class="sxs-lookup"><span data-stu-id="39873-317">Dapr documentation - Getting started</span></span>](https://docs.dapr.io/getting-started)
- [<span data-ttu-id="39873-318">eShopOnDapr</span><span class="sxs-lookup"><span data-stu-id="39873-318">eShopOnDapr</span></span>](https://github.com/dotnet-architecture/eShopOnDapr)

> [!div class="step-by-step"]
> <span data-ttu-id="39873-319">[前へ](dapr-at-20000-feet.md)
> [次へ](reference-application.md)</span><span class="sxs-lookup"><span data-stu-id="39873-319">[Previous](dapr-at-20000-feet.md)
[Next](reference-application.md)</span></span>
