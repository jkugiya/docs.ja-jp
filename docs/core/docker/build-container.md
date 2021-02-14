---
title: Docker を使用してアプリをコンテナー化するチュートリアル
description: このチュートリアルでは、Docker を使って .NET Core アプリケーションをコンテナー化する方法を学習します。
ms.date: 04/27/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: c92f5823f56f74941afdd28638d30e759b2c51c9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740757"
---
# <a name="tutorial-containerize-a-net-core-app"></a><span data-ttu-id="75716-103">チュートリアル: NET Core アプリのコンテナー化</span><span class="sxs-lookup"><span data-stu-id="75716-103">Tutorial: Containerize a .NET Core app</span></span>

<span data-ttu-id="75716-104">このチュートリアルでは、Docker を使って .NET Core アプリケーションをコンテナー化する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="75716-104">In this tutorial, you'll learn how to containerize a .NET Core application with Docker.</span></span> <span data-ttu-id="75716-105">コンテナーには、変更できないインフラストラクチャになったり、移植可能なアーキテクチャを提供したり、スケーラビリティを可能にしたりといった、さまざまな特徴とベネフィットがあります。</span><span class="sxs-lookup"><span data-stu-id="75716-105">Containers have many features and benefits, such as being an immutable infrastructure, providing a portable architecture, and enabling scalability.</span></span> <span data-ttu-id="75716-106">そのイメージを使って、ローカル開発環境、プライベート クラウド、またはパブリック クラウド用にコンテナーを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="75716-106">The image can be used to create containers for your local development environment, private cloud, or public cloud.</span></span>

<span data-ttu-id="75716-107">このチュートリアルでは、次の作業を行いました。</span><span class="sxs-lookup"><span data-stu-id="75716-107">In this tutorial, you:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="75716-108">簡単な .NET Core アプリを作成して発行する</span><span class="sxs-lookup"><span data-stu-id="75716-108">Create and publish a simple .NET Core app</span></span>
> - <span data-ttu-id="75716-109">.NET Core 用の Dockerfile を作成して構成する</span><span class="sxs-lookup"><span data-stu-id="75716-109">Create and configure a Dockerfile for .NET Core</span></span>
> - <span data-ttu-id="75716-110">Docker イメージの構築</span><span class="sxs-lookup"><span data-stu-id="75716-110">Build a Docker image</span></span>
> - <span data-ttu-id="75716-111">Docker コンテナーを作成して実行する</span><span class="sxs-lookup"><span data-stu-id="75716-111">Create and run a Docker container</span></span>

<span data-ttu-id="75716-112">.NET Core アプリケーション用に Docker コンテナーを構築してデプロイするタスクを理解できます。</span><span class="sxs-lookup"><span data-stu-id="75716-112">You'll understand the Docker container build and deploy tasks for a .NET Core application.</span></span> <span data-ttu-id="75716-113">"*Docker プラットフォーム*" では、"*Docker エンジン*" を使用して、すばやくアプリがビルドされ、"*Docker イメージ*" としてパッケージ化されます。</span><span class="sxs-lookup"><span data-stu-id="75716-113">The *Docker platform* uses the *Docker engine* to quickly build and package apps as *Docker images*.</span></span> <span data-ttu-id="75716-114">これらのイメージは、階層型コンテナーに展開されて実行される *Dockerfile* 形式で記述されています。</span><span class="sxs-lookup"><span data-stu-id="75716-114">These images are written in the *Dockerfile* format to be deployed and run in a layered container.</span></span>

> [!NOTE]
> <span data-ttu-id="75716-115">このチュートリアルは ASP.NET Core アプリ向けのものでは **ありません**。</span><span class="sxs-lookup"><span data-stu-id="75716-115">This tutorial **is not** for ASP.NET Core apps.</span></span> <span data-ttu-id="75716-116">ASP.NET Core を使用している場合は、[ASP.NET Core アプリケーションをコンテナー化する方法](/aspnet/core/host-and-deploy/docker/building-net-docker-images)に関するチュートリアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="75716-116">If you're using ASP.NET Core, see the [Learn how to containerize an ASP.NET Core application](/aspnet/core/host-and-deploy/docker/building-net-docker-images) tutorial.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="75716-117">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="75716-117">Prerequisites</span></span>

<span data-ttu-id="75716-118">次の前提条件をインストールします。</span><span class="sxs-lookup"><span data-stu-id="75716-118">Install the following prerequisites:</span></span>

- <span data-ttu-id="75716-119">[.NET Core 5.0 SDK](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="75716-119">[.NET Core 5.0 SDK](https://dotnet.microsoft.com/download)</span></span>\
<span data-ttu-id="75716-120">.NET Core をインストールしてある場合、どの SDK を使っているか確認するには、`dotnet --info` コマンドを使います。</span><span class="sxs-lookup"><span data-stu-id="75716-120">If you have .NET Core installed, use the `dotnet --info` command to determine which SDK you're using.</span></span>
- [<span data-ttu-id="75716-121">Docker Community Edition</span><span class="sxs-lookup"><span data-stu-id="75716-121">Docker Community Edition</span></span>](https://www.docker.com/products/docker-desktop)
- <span data-ttu-id="75716-122">*Dockerfile* と .NET Core サンプル アプリ用の一時作業フォルダー。</span><span class="sxs-lookup"><span data-stu-id="75716-122">A temporary working folder for the *Dockerfile* and .NET Core example app.</span></span> <span data-ttu-id="75716-123">このチュートリアルでは、作業フォルダーに *docker-working* の名前が使用されます。</span><span class="sxs-lookup"><span data-stu-id="75716-123">In this tutorial, the name *docker-working* is used as the working folder.</span></span>

## <a name="create-net-core-app"></a><span data-ttu-id="75716-124">.NET Core アプリを作成する</span><span class="sxs-lookup"><span data-stu-id="75716-124">Create .NET Core app</span></span>

<span data-ttu-id="75716-125">Docker コンテナーで実行される .NET Core アプリが必要です。</span><span class="sxs-lookup"><span data-stu-id="75716-125">You need a .NET Core app that the Docker container will run.</span></span> <span data-ttu-id="75716-126">ターミナルを開き、作業フォルダーがまだない場合は作成して、移動します。</span><span class="sxs-lookup"><span data-stu-id="75716-126">Open your terminal, create a working folder if you haven't already, and enter it.</span></span> <span data-ttu-id="75716-127">作業フォルダーで次のコマンドを実行し、*app* という名前のサブディレクトリに新しいプロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="75716-127">In the working folder, run the following command to create a new project in a subdirectory named *app*:</span></span>

```dotnetcli
dotnet new console -o App -n NetCore.Docker
```

<span data-ttu-id="75716-128">フォルダー ツリーは次のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="75716-128">Your folder tree will look like the following:</span></span>

```
docker-working
    └──App
        ├──NetCore.Docker.csproj
        ├──Program.cs
        └──obj
            ├──NetCore.Docker.csproj.nuget.dgspec.json
            ├──NetCore.Docker.csproj.nuget.g.props
            ├──NetCore.Docker.csproj.nuget.g.targets
            ├──project.assets.json
            └──project.nuget.cache
```

<span data-ttu-id="75716-129">`dotnet new` コマンドでは、"*App*" という名前の新しいフォルダーが作成され、"Hello World" コンソール アプリケーションが生成されます。</span><span class="sxs-lookup"><span data-stu-id="75716-129">The `dotnet new` command creates a new folder named *App* and generates a "Hello World" console application.</span></span> <span data-ttu-id="75716-130">ディレクトリを変更し、ターミナル セッションから "*App*" フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="75716-130">Change directories and navigate into the *App* folder, from your terminal session.</span></span> <span data-ttu-id="75716-131">`dotnet run` コマンドを使用してアプリを起動します。</span><span class="sxs-lookup"><span data-stu-id="75716-131">Use the `dotnet run` command to start the app.</span></span> <span data-ttu-id="75716-132">アプリケーションが実行され、コマンドの下に `Hello World!` が出力されます。</span><span class="sxs-lookup"><span data-stu-id="75716-132">The application will run, and print `Hello World!` below the command:</span></span>

```dotnetcli
dotnet run
Hello World!
```

<span data-ttu-id="75716-133">既定のテンプレートでは、ターミナルに出力した後、すぐに終了するアプリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="75716-133">The default template creates an app that prints to the terminal and then immediately terminates.</span></span> <span data-ttu-id="75716-134">このチュートリアルでは、無限にループするアプリを使います。</span><span class="sxs-lookup"><span data-stu-id="75716-134">For this tutorial, you'll use an app that loops indefinitely.</span></span> <span data-ttu-id="75716-135">テキスト エディターで *Program.cs* ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="75716-135">Open the *Program.cs* file in a text editor.</span></span>

> [!TIP]
> <span data-ttu-id="75716-136">Visual Studio Code を使用している場合は、前のターミナル セッションで次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="75716-136">If you're using Visual Studio Code, from the previous terminal session type the following command:</span></span>
>
> ```console
> code .
> ```
>
> <span data-ttu-id="75716-137">これにより、Visual Studio Code のプロジェクトを含む "*App*" フォルダーが開きます。</span><span class="sxs-lookup"><span data-stu-id="75716-137">This will open the *App* folder that contains the project in Visual Studio Code.</span></span>

<span data-ttu-id="75716-138">"*Program.cs*" は次のような C# コードになります。</span><span class="sxs-lookup"><span data-stu-id="75716-138">The *Program.cs* should look like the following C# code:</span></span>

```csharp
using System;

namespace NetCore.Docker
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

<span data-ttu-id="75716-139">1 秒ごとに数をカウントする次のコードにファイルを置き換えます。</span><span class="sxs-lookup"><span data-stu-id="75716-139">Replace the file with the following code that counts numbers every second:</span></span>

```csharp
using System;
using System.Threading.Tasks;

namespace NetCore.Docker
{
    class Program
    {
        static async Task Main(string[] args)
        {
            var counter = 0;
            var max = args.Length != 0 ? Convert.ToInt32(args[0]) : -1;
            while (max == -1 || counter < max)
            {
                Console.WriteLine($"Counter: {++counter}");
                await Task.Delay(1000);
            }
        }
    }
}
```

<span data-ttu-id="75716-140">ファイルを保存し、`dotnet run` で再びプログラムをテストします。</span><span class="sxs-lookup"><span data-stu-id="75716-140">Save the file and test the program again with `dotnet run`.</span></span> <span data-ttu-id="75716-141">このアプリは無限に実行されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="75716-141">Remember that this app runs indefinitely.</span></span> <span data-ttu-id="75716-142">停止するにはキャンセル コマンド <kbd>Ctrl + C</kbd> を使用します。</span><span class="sxs-lookup"><span data-stu-id="75716-142">Use the cancel command <kbd>Ctrl+C</kbd> to stop it.</span></span> <span data-ttu-id="75716-143">次に出力例を示します。</span><span class="sxs-lookup"><span data-stu-id="75716-143">The following is an example output:</span></span>

```dotnetcli
dotnet run
Counter: 1
Counter: 2
Counter: 3
Counter: 4
^C
```

<span data-ttu-id="75716-144">コマンド ラインでアプリに数値を渡すと、アプリはその値までカウント アップしただけで終了します。</span><span class="sxs-lookup"><span data-stu-id="75716-144">If you pass a number on the command line to the app, it will only count up to that amount and then exit.</span></span> <span data-ttu-id="75716-145">`dotnet run -- 5` で 5 までカウントしてみてください。</span><span class="sxs-lookup"><span data-stu-id="75716-145">Try it with `dotnet run -- 5` to count to five.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="75716-146">`--` より後のパラメーターは `dotnet run` コマンドに渡されず、代わりにアプリケーションに渡されます。</span><span class="sxs-lookup"><span data-stu-id="75716-146">Any parameters after `--` are not passed to the `dotnet run` command and instead are passed to your application.</span></span>

## <a name="publish-net-core-app"></a><span data-ttu-id="75716-147">.NET Core アプリを発行する</span><span class="sxs-lookup"><span data-stu-id="75716-147">Publish .NET Core app</span></span>

<span data-ttu-id="75716-148">.NET Core アプリを Docker イメージに追加するには、まず発行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="75716-148">Before adding the .NET Core app to the Docker image, first it must be published.</span></span> <span data-ttu-id="75716-149">アプリの発行済みバージョンをコンテナーで実行することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="75716-149">It is best to have the container run the published version of the app.</span></span> <span data-ttu-id="75716-150">アプリを発行するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="75716-150">To publish the app, run the following command:</span></span>

```dotnetcli
dotnet publish -c Release
```

<span data-ttu-id="75716-151">このコマンドでは、*publish* フォルダーにアプリがコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="75716-151">This command compiles your app to the *publish* folder.</span></span> <span data-ttu-id="75716-152">作業フォルダーから *publish* フォルダーへのパスは `.\App\bin\Release\net5.0\publish\` です</span><span class="sxs-lookup"><span data-stu-id="75716-152">The path to the *publish* folder from the working folder should be `.\App\bin\Release\net5.0\publish\`</span></span>

#### <a name="windows"></a>[<span data-ttu-id="75716-153">Windows</span><span class="sxs-lookup"><span data-stu-id="75716-153">Windows</span></span>](#tab/windows)

<span data-ttu-id="75716-154">"*App*" フォルダーから、publish フォルダーのディレクトリ一覧を表示し、"*NetCore.Docker.dll*" ファイルが作成されたことを確認します。</span><span class="sxs-lookup"><span data-stu-id="75716-154">From the *App* folder, get a directory listing of the publish folder to verify that the *NetCore.Docker.dll* file was created.</span></span>

```powershell
dir .\bin\Release\net5.0\publish\

    Directory: C:\Users\dapine\App\bin\Release\net5.0\publish

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        4/27/2020   8:27 AM            434 NetCore.Docker.deps.json
-a----        4/27/2020   8:27 AM           6144 NetCore.Docker.dll
-a----        4/27/2020   8:27 AM         171520 NetCore.Docker.exe
-a----        4/27/2020   8:27 AM            860 NetCore.Docker.pdb
-a----        4/27/2020   8:27 AM            154 NetCore.Docker.runtimeconfig.json
```

#### <a name="linux"></a>[<span data-ttu-id="75716-155">Linux</span><span class="sxs-lookup"><span data-stu-id="75716-155">Linux</span></span>](#tab/linux)

<span data-ttu-id="75716-156">`ls` コマンドを使用してディレクトリ一覧を表示し、"*NetCore.Docker.dll*" ファイルが作成されたことを確認します。</span><span class="sxs-lookup"><span data-stu-id="75716-156">Use the `ls` command to get a directory listing and verify that the *NetCore.Docker.dll* file was created.</span></span>

```bash
me@DESKTOP:/docker-working/app$ ls bin/Release/net5.0/publish
NetCore.Docker.deps.json  NetCore.Docker.dll  NetCore.Docker.pdb  NetCore.Docker.runtimeconfig.json
```

---

## <a name="create-the-dockerfile"></a><span data-ttu-id="75716-157">Dockerfile を作成する</span><span class="sxs-lookup"><span data-stu-id="75716-157">Create the Dockerfile</span></span>

<span data-ttu-id="75716-158">*Dockerfile* ファイルは、コンテナー イメージを作成するために `docker build` コマンドによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="75716-158">The *Dockerfile* file is used by the `docker build` command to create a container image.</span></span> <span data-ttu-id="75716-159">このファイルは *Dockerfile* という名前のテキスト ファイルで、拡張子はありません。</span><span class="sxs-lookup"><span data-stu-id="75716-159">This file is a text file named *Dockerfile* that doesn't have an extension.</span></span>

<span data-ttu-id="75716-160">" *.csproj*" が含まれるディレクトリに "*Dockerfile*" という名前のファイルを作成し、テキスト エディターで開きます。</span><span class="sxs-lookup"><span data-stu-id="75716-160">Create a file named *Dockerfile* in directory containing the *.csproj* and open it in a text editor.</span></span> <span data-ttu-id="75716-161">このチュートリアルでは、(.NET Core ランタイム イメージを含む) ASP.NET Core ランタイム イメージを使用して、.NET Core コンソール アプリケーションに対応します。</span><span class="sxs-lookup"><span data-stu-id="75716-161">This tutorial will use the ASP.NET Core runtime image (which contains the .NET Core runtime image) and corresponds with the .NET Core console application.</span></span>

```dockerfile
FROM mcr.microsoft.com/dotnet/aspnet:5.0
```

> [!NOTE]
> <span data-ttu-id="75716-162">`mcr.microsoft.com/dotnet/runtime:5.0` イメージが使用されている可能性もありますが、ここでは ASP.NET Core ランタイム イメージを意図的に使用します。</span><span class="sxs-lookup"><span data-stu-id="75716-162">The ASP.NET Core runtime image is used intentionally here, although the `mcr.microsoft.com/dotnet/runtime:5.0` image could have been used.</span></span>

<span data-ttu-id="75716-163">`FROM` キーワードには、完全修飾 Docker コンテナー イメージ名が必要です。</span><span class="sxs-lookup"><span data-stu-id="75716-163">The `FROM` keyword requires a fully qualified Docker container image name.</span></span> <span data-ttu-id="75716-164">Microsoft Container Registry (MCR、mcr.microsoft.com) は、パブリック アクセスが可能なコンテナーをホストする Docker Hub のシンジケートです。</span><span class="sxs-lookup"><span data-stu-id="75716-164">The Microsoft Container Registry (MCR, mcr.microsoft.com) is a syndicate of Docker Hub - which hosts publicly accessible containers.</span></span> <span data-ttu-id="75716-165">`dotnet/core` セグメントはコンテナー リポジトリで、`aspnet` セグメントはコンテナー イメージの名前です。</span><span class="sxs-lookup"><span data-stu-id="75716-165">The `dotnet/core` segment is the container repository, where as the `aspnet` segment is the container image name.</span></span> <span data-ttu-id="75716-166">イメージには `5.0` のタグが付けられ、バージョン管理に使用されます。</span><span class="sxs-lookup"><span data-stu-id="75716-166">The image is tagged with `5.0`, which is used for versioning.</span></span> <span data-ttu-id="75716-167">このため、`mcr.microsoft.com/dotnet/aspnet:5.0` は .NET Core 5.0 ランタイムです。</span><span class="sxs-lookup"><span data-stu-id="75716-167">Thus, `mcr.microsoft.com/dotnet/aspnet:5.0` is the .NET Core 5.0 runtime.</span></span> <span data-ttu-id="75716-168">必ず、SDK のターゲットのランタイムと一致するランタイム バージョンをプルしてください。</span><span class="sxs-lookup"><span data-stu-id="75716-168">Make sure that you pull the runtime version that matches the runtime targeted by your SDK.</span></span> <span data-ttu-id="75716-169">たとえば、前のセクションで作成したアプリでは .NET Core 5.0 SDK が使用されているため、*Dockerfile* で参照される基本イメージは **5.0** でタグ付けされます。</span><span class="sxs-lookup"><span data-stu-id="75716-169">For example, the app created in the previous section used the .NET Core 5.0 SDK and the base image referred to in the *Dockerfile* is tagged with **5.0**.</span></span>

<span data-ttu-id="75716-170">*Dockerfile* ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="75716-170">Save the *Dockerfile* file.</span></span> <span data-ttu-id="75716-171">作業フォルダーのディレクトリ構造は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="75716-171">The directory structure of the working folder should look like the following.</span></span> <span data-ttu-id="75716-172">一部のより深いレベルのファイルとフォルダーは、スペース削減のためこの記事では省略されています。</span><span class="sxs-lookup"><span data-stu-id="75716-172">Some of the deeper-level files and folders have been omitted to save space in the article:</span></span>

```
docker-working
    └──App
        ├──Dockerfile
        ├──NetCore.Docker.csproj
        ├──Program.cs
        ├──bin
        │   └──Release
        │       └──net5.0
        │           └──publish
        │               ├──NetCore.Docker.deps.json
        │               ├──NetCore.Docker.exe
        │               ├──NetCore.Docker.dll
        │               ├──NetCore.Docker.pdb
        │               └──NetCore.Docker.runtimeconfig.json
        └──obj
            └──...
```

<span data-ttu-id="75716-173">ターミナルから、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="75716-173">From your terminal, run the following command:</span></span>

```console
docker build -t counter-image -f Dockerfile .
```

<span data-ttu-id="75716-174">Docker により *Dockerfile* 内の各行が処理されます。</span><span class="sxs-lookup"><span data-stu-id="75716-174">Docker will process each line in the *Dockerfile*.</span></span> <span data-ttu-id="75716-175">`docker build` コマンドの `.` は、現在のフォルダーで *Dockerfile* を検索するよう Docker に指示します。</span><span class="sxs-lookup"><span data-stu-id="75716-175">The `.` in the `docker build` command tells Docker to use the current folder to find a *Dockerfile*.</span></span> <span data-ttu-id="75716-176">このコマンドでは、イメージがビルドされて、そのイメージを指す **counter-image** という名前のローカル リポジトリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="75716-176">This command builds the image and creates a local repository named **counter-image** that points to that image.</span></span> <span data-ttu-id="75716-177">このコマンドが終了したら、`docker images` を実行し、インストールされているイメージの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="75716-177">After this command finishes, run `docker images` to see a list of images installed:</span></span>

```console
docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
counter-image                           latest              e6780479db63        4 days ago          190MB
mcr.microsoft.com/dotnet/aspnet         5.0                 e6780479db63        4 days ago          190MB
```

<span data-ttu-id="75716-178">2 つのイメージで同じ **IMAGE ID** 値が共有されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="75716-178">Notice that the two images share the same **IMAGE ID** value.</span></span> <span data-ttu-id="75716-179">*Dockerfile* での唯一のコマンドが既存のイメージを新しいイメージの基にするものであったため、両方のイメージで値が同じになっています。</span><span class="sxs-lookup"><span data-stu-id="75716-179">The value is the same between both images because the only command in the *Dockerfile* was to base the new image on an existing image.</span></span> <span data-ttu-id="75716-180">3 つのコマンドを "*Dockerfile*" に追加してみましょう。</span><span class="sxs-lookup"><span data-stu-id="75716-180">Let's add three commands to the *Dockerfile*.</span></span> <span data-ttu-id="75716-181">各コマンドでは、**counter-image** リポジトリ エントリが指し示すイメージを表す最後のコマンドで新しいイメージ レイヤーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="75716-181">Each command creates a new image layer with the final command representing the **counter-image** repository entry points to.</span></span>

```dockerfile
COPY bin/Release/net5.0/publish/ App/
WORKDIR /App
ENTRYPOINT ["dotnet", "NetCore.Docker.dll"]
```

<span data-ttu-id="75716-182">`COPY` コマンドは、自分のコンピューターの指定したフォルダーをコンテナー内のフォルダーにコピーするよう Docker に指示します。</span><span class="sxs-lookup"><span data-stu-id="75716-182">The `COPY` command tells Docker to copy the specified folder on your computer to a folder in the container.</span></span> <span data-ttu-id="75716-183">この例では、"*publish*" フォルダーが、コンテナーの "*App*" という名前のフォルダーにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="75716-183">In this example, the *publish* folder is copied to a folder named *App* in the container.</span></span>

<span data-ttu-id="75716-184">`WORKDIR` コマンドでは、コンテナー内の **現在のディレクトリ** が、"*App*" に変更されます。</span><span class="sxs-lookup"><span data-stu-id="75716-184">The `WORKDIR` command changes the **current directory** inside of the container to *App*.</span></span>

<span data-ttu-id="75716-185">次のコマンド `ENTRYPOINT` は、実行可能ファイルとして実行するためにコンテナーを構成するよう Docker に指示します。</span><span class="sxs-lookup"><span data-stu-id="75716-185">The next command, `ENTRYPOINT`, tells Docker to configure the container to run as an executable.</span></span> <span data-ttu-id="75716-186">コンテナーの起動時に、`ENTRYPOINT` コマンドが実行されます。</span><span class="sxs-lookup"><span data-stu-id="75716-186">When the container starts, the `ENTRYPOINT` command runs.</span></span> <span data-ttu-id="75716-187">このコマンドが終了すると、コンテナーは自動的に停止します。</span><span class="sxs-lookup"><span data-stu-id="75716-187">When this command ends, the container will automatically stop.</span></span>

<span data-ttu-id="75716-188">端末から `docker build -t counter-image -f Dockerfile .` を実行し、そのコマンドが終了したら `docker images` を実行します。</span><span class="sxs-lookup"><span data-stu-id="75716-188">From your terminal, run `docker build -t counter-image -f Dockerfile .` and when that command finishes, run `docker images`.</span></span>

```console
docker build -t counter-image -f Dockerfile .
Sending build context to Docker daemon  1.117MB
Step 1/4 : FROM mcr.microsoft.com/dotnet/aspnet:5.0
 ---> e6780479db63
Step 2/4 : COPY bin/Release/net5.0/publish/ App/
 ---> d1732740eed2
Step 3/4 : WORKDIR /App
 ---> Running in b1701a42f3ff
Removing intermediate container b1701a42f3ff
 ---> 919aab5b95e3
Step 4/4 : ENTRYPOINT ["dotnet", "NetCore.Docker.dll"]
 ---> Running in c12aebd26ced
Removing intermediate container c12aebd26ced
 ---> cd11c3df9b19
Successfully built cd11c3df9b19
Successfully tagged counter-image:latest

docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
counter-image                           latest              cd11c3df9b19        41 seconds ago      190MB
mcr.microsoft.com/dotnet/aspnet         5.0                 e6780479db63        4 days ago          190MB
```

<span data-ttu-id="75716-189">*Dockerfile* 内の各コマンドによってレイヤーが生成され、**IMAGE ID** が作成されます。</span><span class="sxs-lookup"><span data-stu-id="75716-189">Each command in the *Dockerfile* generated a layer and created an **IMAGE ID**.</span></span> <span data-ttu-id="75716-190">最後の **IMAGE ID** は **cd11c3df9b19** であり (個々に異なります)、次にこのイメージを基にしてコンテナーを作成します。</span><span class="sxs-lookup"><span data-stu-id="75716-190">The final **IMAGE ID** (yours will be different) is **cd11c3df9b19** and next you'll create a container based on this image.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="75716-191">コンテナーの作成</span><span class="sxs-lookup"><span data-stu-id="75716-191">Create a container</span></span>

<span data-ttu-id="75716-192">アプリを含むイメージができたので、コンテナーを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="75716-192">Now that you have an image that contains your app, you can create a container.</span></span> <span data-ttu-id="75716-193">2 つの方法でコンテナーを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="75716-193">You can create a container in two ways.</span></span> <span data-ttu-id="75716-194">最初に、停止している新しいコンテナーを作成します。</span><span class="sxs-lookup"><span data-stu-id="75716-194">First, create a new container that is stopped.</span></span>

```console
docker create --name core-counter counter-image
0f281cb3af994fba5d962cc7d482828484ea14ead6bfe386a35e5088c0058851
```

<span data-ttu-id="75716-195">上の `docker create` コマンドでは、**counter-image** イメージに基づくコンテナーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="75716-195">The `docker create` command from above will create a container based on the **counter-image** image.</span></span> <span data-ttu-id="75716-196">そのコマンドの出力では、作成されたコンテナーの **CONTAINER ID** (個々に異なります) が示されます。</span><span class="sxs-lookup"><span data-stu-id="75716-196">The output of that command shows you the **CONTAINER ID** (yours will be different) of the created container.</span></span> <span data-ttu-id="75716-197">"*すべて*" のコンテナーの一覧を表示するには、`docker ps -a` コマンドを使います。</span><span class="sxs-lookup"><span data-stu-id="75716-197">To see a list of *all* containers, use the `docker ps -a` command:</span></span>

```console
docker ps -a
CONTAINER ID    IMAGE            COMMAND                   CREATED           STATUS     PORTS    NAMES
0f281cb3af99    counter-image    "dotnet NetCore.Dock…"    40 seconds ago    Created             core-counter
```

### <a name="manage-the-container"></a><span data-ttu-id="75716-198">コンテナーを管理する</span><span class="sxs-lookup"><span data-stu-id="75716-198">Manage the container</span></span>

<span data-ttu-id="75716-199">コンテナーが特定の名前 `core-counter` で作成されました。この名前を使用してコンテナーを管理します。</span><span class="sxs-lookup"><span data-stu-id="75716-199">The container was created with a specific name `core-counter`, this name is used to manage the container.</span></span> <span data-ttu-id="75716-200">次の例では、`docker start` コマンドを使ってコンテナーを起動した後、`docker ps` コマンドを使って、実行されているコンテナーのみを表示します。</span><span class="sxs-lookup"><span data-stu-id="75716-200">The following example uses the `docker start` command to start the container, and then uses the `docker ps` command to only show containers that are running:</span></span>

```console
docker start core-counter
core-counter

docker ps
CONTAINER ID    IMAGE            COMMAND                   CREATED          STATUS          PORTS    NAMES
2f6424a7ddce    counter-image    "dotnet NetCore.Dock…"    2 minutes ago    Up 11 seconds            core-counter
```

<span data-ttu-id="75716-201">同様に、`docker stop` コマンドではコンテナーが停止されます。</span><span class="sxs-lookup"><span data-stu-id="75716-201">Similarly, the `docker stop` command will stop the container.</span></span> <span data-ttu-id="75716-202">次の例では、`docker stop` コマンドを使ってコンテナーを停止した後、`docker ps` コマンドを使って、実行されているコンテナーがないことを示します。</span><span class="sxs-lookup"><span data-stu-id="75716-202">The following example uses the `docker stop` command to stop the container, and then uses the `docker ps` command to show that no containers are running:</span></span>

```console
docker stop core-counter
core-counter

docker ps
CONTAINER ID    IMAGE    COMMAND    CREATED    STATUS    PORTS    NAMES
```

### <a name="connect-to-a-container"></a><span data-ttu-id="75716-203">コンテナーへの接続</span><span class="sxs-lookup"><span data-stu-id="75716-203">Connect to a container</span></span>

<span data-ttu-id="75716-204">コンテナーが実行状態になった後、それに接続して出力を確認できます。</span><span class="sxs-lookup"><span data-stu-id="75716-204">After a container is running, you can connect to it to see the output.</span></span> <span data-ttu-id="75716-205">`docker start` コマンドを使ってコンテナーを起動し、`docker attach` コマンドを使って出力ストリームを表示します。</span><span class="sxs-lookup"><span data-stu-id="75716-205">Use the `docker start` and `docker attach` commands to start the container and peek at the output stream.</span></span> <span data-ttu-id="75716-206">この例では、<kbd>Ctrl+C</kbd> キー入力を使用して、実行中のコンテナーからデタッチします。</span><span class="sxs-lookup"><span data-stu-id="75716-206">In this example, the <kbd>Ctrl+C</kbd> keystroke is used to detach from the running container.</span></span> <span data-ttu-id="75716-207">このキー入力では、コンテナーを停止するように指定されている場合を除き、コンテナー内のプロセスが終了します。</span><span class="sxs-lookup"><span data-stu-id="75716-207">This keystroke will end the process in the container unless otherwise specified, which would stop the container.</span></span> <span data-ttu-id="75716-208">`--sig-proxy=false` パラメーターを指定すると、<kbd>Ctrl+C</kbd> キーを押してもコンテナー内のプロセスが停止しないことが保証されます。</span><span class="sxs-lookup"><span data-stu-id="75716-208">The `--sig-proxy=false` parameter ensures that <kbd>Ctrl+C</kbd> will not stop the process in the container.</span></span>

<span data-ttu-id="75716-209">コンテナーからデタッチした後、再アタッチして、まだ実行されていてカウントが行われていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="75716-209">After you detach from the container, reattach to verify that it's still running and counting.</span></span>

```console
docker start core-counter
core-counter

docker attach --sig-proxy=false core-counter
Counter: 7
Counter: 8
Counter: 9
^C

docker attach --sig-proxy=false core-counter
Counter: 17
Counter: 18
Counter: 19
^C
```

### <a name="delete-a-container"></a><span data-ttu-id="75716-210">コンテナーを削除する</span><span class="sxs-lookup"><span data-stu-id="75716-210">Delete a container</span></span>

<span data-ttu-id="75716-211">この記事の目的では、何も行っていないコンテナーをそのままにするのは望ましくありません。</span><span class="sxs-lookup"><span data-stu-id="75716-211">For the purposes of this article you don't want containers just hanging around doing nothing.</span></span> <span data-ttu-id="75716-212">前に作成したコンテナーを削除します。</span><span class="sxs-lookup"><span data-stu-id="75716-212">Delete the container you previously created.</span></span> <span data-ttu-id="75716-213">コンテナーが実行されている場合は、それを停止します。</span><span class="sxs-lookup"><span data-stu-id="75716-213">If the container is running, stop it.</span></span>

```console
docker stop core-counter
```

<span data-ttu-id="75716-214">次の例では、すべてのコンテナーを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="75716-214">The following example lists all containers.</span></span> <span data-ttu-id="75716-215">次に、`docker rm` コマンドを使ってコンテナーを削除した後、もう一度実行中のコンテナーを確認します。</span><span class="sxs-lookup"><span data-stu-id="75716-215">It then uses the `docker rm` command to delete the container, and then checks a second time for any running containers.</span></span>

```console
docker ps -a
CONTAINER ID    IMAGE            COMMAND                   CREATED          STATUS                        PORTS    NAMES
2f6424a7ddce    counter-image    "dotnet NetCore.Dock…"    7 minutes ago    Exited (143) 20 seconds ago            core-counter

docker rm core-counter
core-counter

docker ps -a
CONTAINER ID    IMAGE    COMMAND    CREATED    STATUS    PORTS    NAMES
```

### <a name="single-run"></a><span data-ttu-id="75716-216">単一実行</span><span class="sxs-lookup"><span data-stu-id="75716-216">Single run</span></span>

<span data-ttu-id="75716-217">Docker では、1 つのコマンドとしてコンテナーを作成して実行するための `docker run` コマンドが提供されています。</span><span class="sxs-lookup"><span data-stu-id="75716-217">Docker provides the `docker run` command to create and run the container as a single command.</span></span> <span data-ttu-id="75716-218">このコマンドでは、`docker create` を実行してから `docker start` を実行する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="75716-218">This command eliminates the need to run `docker create` and then `docker start`.</span></span> <span data-ttu-id="75716-219">コンテナーが停止したら自動的にコンテナーを削除するように、このコマンドを設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="75716-219">You can also set this command to automatically delete the container when the container stops.</span></span> <span data-ttu-id="75716-220">たとえば、`docker run -it --rm` を使うと 2 つのことが行われます。つまり、最初に現在の端末を使ってコンテナーに自動的に接続し、次にコンテナーが終了したらそれを削除します。</span><span class="sxs-lookup"><span data-stu-id="75716-220">For example, use `docker run -it --rm` to do two things, first, automatically use the current terminal to connect to the container, and then when the container finishes, remove it:</span></span>

```console
docker run -it --rm counter-image
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
^C
```

<span data-ttu-id="75716-221">また、コンテナーは .NET Core アプリの実行にパラメーターを渡します。</span><span class="sxs-lookup"><span data-stu-id="75716-221">The container also passes parameters into the execution of the .NET Core app.</span></span> <span data-ttu-id="75716-222">.NET Core アプリに対して 3 つまでしかカウントしないように指示するには、3 を渡します。</span><span class="sxs-lookup"><span data-stu-id="75716-222">To instruct the .NET Core app to count only to 3 pass in 3.</span></span>

```console
docker run -it --rm counter-image 3
Counter: 1
Counter: 2
Counter: 3
```

<span data-ttu-id="75716-223">`docker run -it` では、<kbd>Ctrl+C</kbd> キーを押すと、コンテナーで実行されているプロセスが停止し、さらにコンテナーが停止されます。</span><span class="sxs-lookup"><span data-stu-id="75716-223">With `docker run -it`, the <kbd>Ctrl+C</kbd> command will stop process that is running in the container, which in turn, stops the container.</span></span> <span data-ttu-id="75716-224">`--rm` パラメーターを指定したので、プロセスが停止するとコンテナーは自動的に削除されます。</span><span class="sxs-lookup"><span data-stu-id="75716-224">Since the `--rm` parameter was provided, the container is automatically deleted when the process is stopped.</span></span> <span data-ttu-id="75716-225">それが存在しないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="75716-225">Verify that it doesn't exist:</span></span>

```console
docker ps -a
CONTAINER ID    IMAGE    COMMAND    CREATED    STATUS    PORTS    NAMES
```

### <a name="change-the-entrypoint"></a><span data-ttu-id="75716-226">ENTRYPOINT を変更する</span><span class="sxs-lookup"><span data-stu-id="75716-226">Change the ENTRYPOINT</span></span>

<span data-ttu-id="75716-227">`docker run` コマンドでは、*Dockerfile* から `ENTRYPOINT` コマンドを変更し、そのコンテナーに対してのみ何か他のことを実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="75716-227">The `docker run` command also lets you modify the `ENTRYPOINT` command from the *Dockerfile* and run something else, but only for that container.</span></span> <span data-ttu-id="75716-228">たとえば、次のコマンドを使うと `bash` または `cmd.exe` を実行できます。</span><span class="sxs-lookup"><span data-stu-id="75716-228">For example, use the following command to run `bash` or `cmd.exe`.</span></span> <span data-ttu-id="75716-229">必要に応じて、コマンドを編集します。</span><span class="sxs-lookup"><span data-stu-id="75716-229">Edit the command as necessary.</span></span>

#### <a name="windows"></a>[<span data-ttu-id="75716-230">Windows</span><span class="sxs-lookup"><span data-stu-id="75716-230">Windows</span></span>](#tab/windows)

<span data-ttu-id="75716-231">この例では、`ENTRYPOINT` が `cmd.exe` に変更されています。</span><span class="sxs-lookup"><span data-stu-id="75716-231">In this example, `ENTRYPOINT` is changed to `cmd.exe`.</span></span> <span data-ttu-id="75716-232">プロセスを終了してコンテナーを停止するには、<kbd>Ctrl+C</kbd> キーを押します。</span><span class="sxs-lookup"><span data-stu-id="75716-232"><kbd>Ctrl+C</kbd> is pressed to end the process and stop the container.</span></span>

```console
docker run -it --rm --entrypoint "cmd.exe" counter-image

Microsoft Windows [Version 10.0.17763.379]
(c) 2018 Microsoft Corporation. All rights reserved.

C:\>dir
 Volume in drive C has no label.
 Volume Serial Number is 3005-1E84

 Directory of C:\

04/09/2019  08:46 AM    <DIR>          app
03/07/2019  10:25 AM             5,510 License.txt
04/02/2019  01:35 PM    <DIR>          Program Files
04/09/2019  01:06 PM    <DIR>          Users
04/02/2019  01:35 PM    <DIR>          Windows
               1 File(s)          5,510 bytes
               4 Dir(s)  21,246,517,248 bytes free

C:\>^C
```

#### <a name="linux"></a>[<span data-ttu-id="75716-233">Linux</span><span class="sxs-lookup"><span data-stu-id="75716-233">Linux</span></span>](#tab/linux)

<span data-ttu-id="75716-234">この例では、`ENTRYPOINT` が `bash` に変更されています。</span><span class="sxs-lookup"><span data-stu-id="75716-234">In this example, `ENTRYPOINT` is changed to `bash`.</span></span> <span data-ttu-id="75716-235">`exit` コマンドが実行されると、プロセスが終了してコンテナーが停止されます。</span><span class="sxs-lookup"><span data-stu-id="75716-235">The `exit` command is run which ends the process and stop the container.</span></span>

```bash
docker run -it --rm --entrypoint "bash" counter-image
root@b735b9799abf:/App# ls
NetCore.Docker.deps.json  NetCore.Docker.dll  NetCore.Docker.exe  NetCore.Docker.pdb  NetCore.Docker.runtimeconfig.json
root@b735b9799abf:/App# dotnet NetCore.Docker.dll 3
Counter: 1
Counter: 2
Counter: 3
root@b735b9799abf:/App# exit
exit
```

---

## <a name="essential-commands"></a><span data-ttu-id="75716-236">重要なコマンド</span><span class="sxs-lookup"><span data-stu-id="75716-236">Essential commands</span></span>

<span data-ttu-id="75716-237">Docker には、コンテナーとイメージを作成、管理、操作するさまざまなコマンドが用意されています。</span><span class="sxs-lookup"><span data-stu-id="75716-237">Docker has many different commands that create, manage, and interact with containers and images.</span></span> <span data-ttu-id="75716-238">コンテナーの管理に不可欠な Docker コマンドは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="75716-238">These Docker commands are essential to managing your containers:</span></span>

- [<span data-ttu-id="75716-239">docker build</span><span class="sxs-lookup"><span data-stu-id="75716-239">docker build</span></span>](https://docs.docker.com/engine/reference/commandline/build/)
- [<span data-ttu-id="75716-240">docker run</span><span class="sxs-lookup"><span data-stu-id="75716-240">docker run</span></span>](https://docs.docker.com/engine/reference/commandline/run/)
- [<span data-ttu-id="75716-241">docker ps</span><span class="sxs-lookup"><span data-stu-id="75716-241">docker ps</span></span>](https://docs.docker.com/engine/reference/commandline/ps/)
- [<span data-ttu-id="75716-242">docker stop</span><span class="sxs-lookup"><span data-stu-id="75716-242">docker stop</span></span>](https://docs.docker.com/engine/reference/commandline/stop/)
- [<span data-ttu-id="75716-243">docker rm</span><span class="sxs-lookup"><span data-stu-id="75716-243">docker rm</span></span>](https://docs.docker.com/engine/reference/commandline/rm/)
- [<span data-ttu-id="75716-244">docker rmi</span><span class="sxs-lookup"><span data-stu-id="75716-244">docker rmi</span></span>](https://docs.docker.com/engine/reference/commandline/rmi/)
- [<span data-ttu-id="75716-245">docker image</span><span class="sxs-lookup"><span data-stu-id="75716-245">docker image</span></span>](https://docs.docker.com/engine/reference/commandline/image/)

## <a name="clean-up-resources"></a><span data-ttu-id="75716-246">リソースをクリーンアップする</span><span class="sxs-lookup"><span data-stu-id="75716-246">Clean up resources</span></span>

<span data-ttu-id="75716-247">このチュートリアルでは、コンテナーとイメージを作成しました。</span><span class="sxs-lookup"><span data-stu-id="75716-247">During this tutorial, you created containers and images.</span></span> <span data-ttu-id="75716-248">必要な場合は、これらのリソースを削除します。</span><span class="sxs-lookup"><span data-stu-id="75716-248">If you want, delete these resources.</span></span> <span data-ttu-id="75716-249">次のコマンドを使います</span><span class="sxs-lookup"><span data-stu-id="75716-249">Use the following commands to</span></span>

01. <span data-ttu-id="75716-250">すべてのコンテナーを一覧表示します</span><span class="sxs-lookup"><span data-stu-id="75716-250">List all containers</span></span>

    ```console
    docker ps -a
    ```

02. <span data-ttu-id="75716-251">実行しているコンテナーを名前で選んで停止します。</span><span class="sxs-lookup"><span data-stu-id="75716-251">Stop containers that are running by their name.</span></span>

    ```console
    docker stop counter-image
    ```

03. <span data-ttu-id="75716-252">コンテナーを削除します</span><span class="sxs-lookup"><span data-stu-id="75716-252">Delete the container</span></span>

    ```console
    docker rm counter-image
    ```

<span data-ttu-id="75716-253">次に、コンピューターに残しておきたくないイメージを削除します。</span><span class="sxs-lookup"><span data-stu-id="75716-253">Next, delete any images that you no longer want on your machine.</span></span> <span data-ttu-id="75716-254">*Dockerfile* によって作成されたイメージを削除した後、*Dockerfile* が基にした .NET Core イメージを削除します。</span><span class="sxs-lookup"><span data-stu-id="75716-254">Delete the image created by your *Dockerfile* and then delete the .NET Core image the *Dockerfile* was based on.</span></span> <span data-ttu-id="75716-255">**IMAGE ID** または **REPOSITORY:TAG** の書式に設定された文字列を使うことができます。</span><span class="sxs-lookup"><span data-stu-id="75716-255">You can use the **IMAGE ID** or the **REPOSITORY:TAG** formatted string.</span></span>

```console
docker rmi counter-image:latest
docker rmi mcr.microsoft.com/dotnet/aspnet:5.0
```

<span data-ttu-id="75716-256">インストールされているイメージの一覧を表示するには、`docker images` コマンドを使います。</span><span class="sxs-lookup"><span data-stu-id="75716-256">Use the `docker images` command to see a list of images installed.</span></span>

> [!TIP]
> <span data-ttu-id="75716-257">イメージ ファイルは大きくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="75716-257">Image files can be large.</span></span> <span data-ttu-id="75716-258">普通、アプリのテスト中および開発中に作成した一時的なコンテナーは削除します。</span><span class="sxs-lookup"><span data-stu-id="75716-258">Typically, you would remove temporary containers you created while testing and developing your app.</span></span> <span data-ttu-id="75716-259">通常、ランタイムがインストールされた基本イメージは、そのランタイムを基にして他のイメージをビルドする予定がある場合は、残しておきます。</span><span class="sxs-lookup"><span data-stu-id="75716-259">You usually keep the base images with the runtime installed if you plan on building other images based on that runtime.</span></span>

## <a name="next-steps"></a><span data-ttu-id="75716-260">次の手順</span><span class="sxs-lookup"><span data-stu-id="75716-260">Next steps</span></span>

- [<span data-ttu-id="75716-261">ASP.NET Core アプリケーションをコンテナー化する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="75716-261">Learn how to containerize an ASP.NET Core application.</span></span>](/aspnet/core/host-and-deploy/docker/building-net-docker-images)
- [<span data-ttu-id="75716-262">ASP.NET Core マイクロサービスのチュートリアルを試します。</span><span class="sxs-lookup"><span data-stu-id="75716-262">Try the ASP.NET Core Microservice Tutorial.</span></span>](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
- [<span data-ttu-id="75716-263">コンテナーをサポートする Azure サービスを確認します。</span><span class="sxs-lookup"><span data-stu-id="75716-263">Review the Azure services that support containers.</span></span>](https://azure.microsoft.com/overview/containers/)
- [<span data-ttu-id="75716-264">Dockerfile のコマンドについて読みます。</span><span class="sxs-lookup"><span data-stu-id="75716-264">Read about Dockerfile commands.</span></span>](https://docs.docker.com/engine/reference/builder/)
- [<span data-ttu-id="75716-265">Visual Studio 向けのコンテナー ツールを調べます</span><span class="sxs-lookup"><span data-stu-id="75716-265">Explore the Container Tools for Visual Studio</span></span>](/visualstudio/containers/overview)
