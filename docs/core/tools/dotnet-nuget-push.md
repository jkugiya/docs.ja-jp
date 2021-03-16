---
title: dotnet nuget push コマンド
description: dotnet nuget push コマンドでは、パッケージをサーバーにプッシュして発行します。
author: karann-msft
ms.date: 02/14/2020
ms.openlocfilehash: 92e2593633343bda6990ca51d593455ff13f0df7
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2021
ms.locfileid: "103478190"
---
# <a name="dotnet-nuget-push"></a><span data-ttu-id="708e3-103">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="708e3-103">dotnet nuget push</span></span>

<span data-ttu-id="708e3-104">**この記事の対象:** ✔️ .NET Core 2.x SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="708e3-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="708e3-105">名前</span><span class="sxs-lookup"><span data-stu-id="708e3-105">Name</span></span>

<span data-ttu-id="708e3-106">`dotnet nuget push` - パッケージをサーバーにプッシュして発行します。</span><span class="sxs-lookup"><span data-stu-id="708e3-106">`dotnet nuget push` - Pushes a package to the server and publishes it.</span></span>

## <a name="synopsis"></a><span data-ttu-id="708e3-107">構文</span><span class="sxs-lookup"><span data-stu-id="708e3-107">Synopsis</span></span>

```dotnetcli
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output]
    [--interactive] [-k|--api-key <API_KEY>] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source <SOURCE>] [--skip-duplicate]
    [-sk|--symbol-api-key <API_KEY>] [-ss|--symbol-source <SOURCE>]
    [-t|--timeout <TIMEOUT>]

dotnet nuget push -h|--help
```

## <a name="description"></a><span data-ttu-id="708e3-108">説明</span><span class="sxs-lookup"><span data-stu-id="708e3-108">Description</span></span>

<span data-ttu-id="708e3-109">`dotnet nuget push` コマンドは、パッケージをサーバーにプッシュして発行します。</span><span class="sxs-lookup"><span data-stu-id="708e3-109">The `dotnet nuget push` command pushes a package to the server and publishes it.</span></span> <span data-ttu-id="708e3-110">プッシュ コマンドでは、システムの NuGet 構成ファイル、または構成ファイルのチェーンで検出されたサーバーと資格情報の詳細を使用します。</span><span class="sxs-lookup"><span data-stu-id="708e3-110">The push command uses server and credential details found in the system's NuGet config file or chain of config files.</span></span> <span data-ttu-id="708e3-111">構成ファイルの詳細については、「[Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior)」 (NuGet 動作を構成する) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="708e3-111">For more information on config files, see [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior).</span></span> <span data-ttu-id="708e3-112">NuGet の既定の構成は、 *%AppData%\NuGet\NuGet.config* (Windows) または *$HOME/.local/share* (Linux/macOS) を読み込み、次にドライブのルートから開始され、現在のディレクトリで終わる、任意の *nuget.config* または *.nuget\nuget.config* を読み込むことによって取得されます。</span><span class="sxs-lookup"><span data-stu-id="708e3-112">NuGet's default configuration is obtained by loading *%AppData%\NuGet\NuGet.config* (Windows) or *$HOME/.local/share* (Linux/macOS), then loading any *nuget.config* or *.nuget\nuget.config* starting from the root of drive and ending in the current directory.</span></span>

<span data-ttu-id="708e3-113">このコマンドにより、既存のパッケージがプッシュされます。</span><span class="sxs-lookup"><span data-stu-id="708e3-113">The command pushes an existing package.</span></span> <span data-ttu-id="708e3-114">パッケージは作成されません。</span><span class="sxs-lookup"><span data-stu-id="708e3-114">It doesn't create a package.</span></span> <span data-ttu-id="708e3-115">パッケージを作成するには、[`dotnet pack`](dotnet-pack.md) を使用します。</span><span class="sxs-lookup"><span data-stu-id="708e3-115">To create a package, use [`dotnet pack`](dotnet-pack.md).</span></span>

## <a name="arguments"></a><span data-ttu-id="708e3-116">引数</span><span class="sxs-lookup"><span data-stu-id="708e3-116">Arguments</span></span>

- **`ROOT`**

  <span data-ttu-id="708e3-117">プッシュされるパッケージのファイル パスを指定します。</span><span class="sxs-lookup"><span data-stu-id="708e3-117">Specifies the file path to the package to be pushed.</span></span>

## <a name="options"></a><span data-ttu-id="708e3-118">オプション</span><span class="sxs-lookup"><span data-stu-id="708e3-118">Options</span></span>

- **`-d|--disable-buffering`**

  <span data-ttu-id="708e3-119">メモリ使用量を削減するために、HTTP(S) サーバーにプッシュするときのバッファリングを無効にします。</span><span class="sxs-lookup"><span data-stu-id="708e3-119">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

- **`--force-english-output`**

  <span data-ttu-id="708e3-120">インバリアントの英語ベースのカルチャを使用して、アプリケーションの実行を強制します。</span><span class="sxs-lookup"><span data-stu-id="708e3-120">Forces the application to run using an invariant, English-based culture.</span></span>

- **`-h|--help`**

  <span data-ttu-id="708e3-121">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="708e3-121">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="708e3-122">コマンドが認証などの操作をブロックして、手動アクションを要求することを許可します。</span><span class="sxs-lookup"><span data-stu-id="708e3-122">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="708e3-123">.NET Core 2.2 SDK 以降、使用できるオプションです。</span><span class="sxs-lookup"><span data-stu-id="708e3-123">Option available since .NET Core 2.2 SDK.</span></span>

- **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="708e3-124">サーバーの API キーです。</span><span class="sxs-lookup"><span data-stu-id="708e3-124">The API key for the server.</span></span>

- **`-n|--no-symbols`**

  <span data-ttu-id="708e3-125">シンボルをプッシュしません (存在する場合でも)。</span><span class="sxs-lookup"><span data-stu-id="708e3-125">Doesn't push symbols (even if present).</span></span>

- **`--no-service-endpoint`**

  <span data-ttu-id="708e3-126">ソース URL に "api/v2/package" を追加しません。</span><span class="sxs-lookup"><span data-stu-id="708e3-126">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="708e3-127">.NET Core 2.1 SDK 以降、使用できるオプションです。</span><span class="sxs-lookup"><span data-stu-id="708e3-127">Option available since .NET Core 2.1 SDK.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="708e3-128">サーバー URL を指定します。</span><span class="sxs-lookup"><span data-stu-id="708e3-128">Specifies the server URL.</span></span> <span data-ttu-id="708e3-129">NuGet によって UNC またはローカル フォルダー ソースが識別され、HTTP を使用してファイルがプッシュされるのではなく、単にそこにファイルがコピーされます。</span><span class="sxs-lookup"><span data-stu-id="708e3-129">NuGet identifies a UNC or local folder source and simply copies the file there instead of pushing it using HTTP.</span></span>
  > [!IMPORTANT]
  > <span data-ttu-id="708e3-130">NuGet 3.4.2 以降では、NuGet 構成ファイルで `DefaultPushSource` 値が指定されていない限り、これは必須パラメーターです。</span><span class="sxs-lookup"><span data-stu-id="708e3-130">Starting with NuGet 3.4.2, this is a mandatory parameter unless the NuGet config file specifies a `DefaultPushSource` value.</span></span> <span data-ttu-id="708e3-131">詳しくは、「[NuGet の動作の構成](/nuget/consume-packages/configuring-nuget-behavior)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="708e3-131">For more information, see [Configuring NuGet behavior](/nuget/consume-packages/configuring-nuget-behavior).</span></span>

- **`--skip-duplicate`**

  <span data-ttu-id="708e3-132">複数のパッケージを HTTP(S) サーバーにプッシュする場合は、すべての 409 競合応答を警告として処理して、プッシュを続行できるようにします。</span><span class="sxs-lookup"><span data-stu-id="708e3-132">When pushing multiple packages to an HTTP(S) server, treats any 409 Conflict response as a warning so that the push can continue.</span></span> <span data-ttu-id="708e3-133">.NET Core 3.1 SDK 以降で利用できます。</span><span class="sxs-lookup"><span data-stu-id="708e3-133">Available since .NET Core 3.1 SDK.</span></span>

- **`-sk|--symbol-api-key <API_KEY>`**

  <span data-ttu-id="708e3-134">シンボル サーバーの API キーです。</span><span class="sxs-lookup"><span data-stu-id="708e3-134">The API key for the symbol server.</span></span>

- **`-ss|--symbol-source <SOURCE>`**

  <span data-ttu-id="708e3-135">シンボル サーバーの URL を指定します。</span><span class="sxs-lookup"><span data-stu-id="708e3-135">Specifies the symbol server URL.</span></span>

- **`-t|--timeout <TIMEOUT>`**

  <span data-ttu-id="708e3-136">秒単位でサーバーにプッシュする場合のタイムアウトを指定します。</span><span class="sxs-lookup"><span data-stu-id="708e3-136">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="708e3-137">既定値は 300 秒 (5 分) です。</span><span class="sxs-lookup"><span data-stu-id="708e3-137">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="708e3-138">0 (0 秒) を指定すると、既定値が適用されます。</span><span class="sxs-lookup"><span data-stu-id="708e3-138">Specifying 0 (zero seconds) applies the default value.</span></span>

## <a name="examples"></a><span data-ttu-id="708e3-139">使用例</span><span class="sxs-lookup"><span data-stu-id="708e3-139">Examples</span></span>

- <span data-ttu-id="708e3-140">API キーを使用して、NuGet 構成ファイルで指定されている既定のプッシュ ソースに *foo.nupkg* をプッシュします。</span><span class="sxs-lookup"><span data-stu-id="708e3-140">Push *foo.nupkg* to the default push source specified in the NuGet config file, using an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a
  ```

- <span data-ttu-id="708e3-141">API キーを指定して、公式 NuGet サーバーに *foo.nupkg* をプッシュします。</span><span class="sxs-lookup"><span data-stu-id="708e3-141">Push *foo.nupkg* to the official NuGet server, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://api.nuget.org/v3/index.json
  ```
  
  * <span data-ttu-id="708e3-142">API キーを指定して、カスタム プッシュ ソース `https://customsource` に *foo.nupkg* をプッシュします。</span><span class="sxs-lookup"><span data-stu-id="708e3-142">Push *foo.nupkg* to the custom push source `https://customsource`, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://customsource/
  ```

- <span data-ttu-id="708e3-143">NuGet 構成ファイルで指定されている既定のプッシュ ソースに *foo.nupkg* をプッシュします。</span><span class="sxs-lookup"><span data-stu-id="708e3-143">Push *foo.nupkg* to the default push source specified in the NuGet config file:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg
  ```

- <span data-ttu-id="708e3-144">既定のシンボル ソースに *foo.symbols.nupkg* をプッシュします。</span><span class="sxs-lookup"><span data-stu-id="708e3-144">Push *foo.symbols.nupkg* to the default symbols source:</span></span>

  ```dotnetcli
  dotnet nuget push foo.symbols.nupkg
  ```

- <span data-ttu-id="708e3-145">NuGet 構成ファイルで指定されている既定のプッシュ ソースに *foo.nupkg* を 360 秒のタイムアウトでプッシュします。</span><span class="sxs-lookup"><span data-stu-id="708e3-145">Push *foo.nupkg* to the default push source specified in the NuGet config file, with a 360-second timeout:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg --timeout 360
  ```

- <span data-ttu-id="708e3-146">NuGet 構成ファイルで指定されている既定のプッシュ ソースに、現在のディレクトリにあるすべての *.nupkg* ファイルをプッシュします。</span><span class="sxs-lookup"><span data-stu-id="708e3-146">Push all *.nupkg* files in the current directory to the default push source specified in the NuGet config file:</span></span>

  ```dotnetcli
  dotnet nuget push "*.nupkg"
  ```

  > [!NOTE]
  > <span data-ttu-id="708e3-147">このコマンドがうまくいかない場合は、古いバージョンの SDK (.NET Core 2.1 SDK 以前のバージョン) に存在したバグが原因である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="708e3-147">If this command doesn't work, it might be due to a bug that existed in older versions of the SDK (.NET Core 2.1 SDK and earlier versions).</span></span>
  > <span data-ttu-id="708e3-148">これを解決するには、SDK のバージョンをアップグレードするか、代わりに次のコマンドを実行します: `dotnet nuget push "**/*.nupkg"`</span><span class="sxs-lookup"><span data-stu-id="708e3-148">To fix this, upgrade your SDK version or run the following command instead: `dotnet nuget push "**/*.nupkg"`</span></span>
  
  > [!NOTE]
  > <span data-ttu-id="708e3-149">ファイル グロビングを実行する bash など、シェルには引用符が必須です。</span><span class="sxs-lookup"><span data-stu-id="708e3-149">The enclosing quotes are required for shells such as bash that perform file globbing.</span></span> <span data-ttu-id="708e3-150">詳細については、[NuGet/Home#4393](https://github.com/NuGet/Home/issues/4393#issuecomment-667618120) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="708e3-150">For more information, see [NuGet/Home#4393](https://github.com/NuGet/Home/issues/4393#issuecomment-667618120).</span></span>

- <span data-ttu-id="708e3-151">HTTP(S) サーバーによって競合応答 409 が返された場合でも、NuGet 構成ファイルで指定されている既定のプッシュ ソースにすべての *.nupkg* ファイルをプッシュします。</span><span class="sxs-lookup"><span data-stu-id="708e3-151">Push all *.nupkg* files to the default push source specified in the NuGet config file, even if a 409 Conflict response is returned by an HTTP(S) server:</span></span>

  ```dotnetcli
  dotnet nuget push "*.nupkg" --skip-duplicate
  ```

- <span data-ttu-id="708e3-152">ローカル フィード ディレクトリに現在のディレクトリ内のすべての *.nupkg* ファイルをプッシュします。</span><span class="sxs-lookup"><span data-stu-id="708e3-152">Push all *.nupkg* files in the current directory to a local feed directory:</span></span>

  ```dotnetcli
  dotnet nuget push "*.nupkg" -s c:\mydir
  ```

  <span data-ttu-id="708e3-153">このコマンドでは、パッケージが階層フォルダー構造に格納されないため、パフォーマンスを最適化することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="708e3-153">This command doesn't store packages in a hierarchical folder structure, which is recommended to optimize performance.</span></span> <span data-ttu-id="708e3-154">詳細については、[ローカル フィード](/nuget/hosting-packages/local-feeds)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="708e3-154">For more information, see [Local feeds](/nuget/hosting-packages/local-feeds).</span></span>  
