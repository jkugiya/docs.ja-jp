---
title: dotnet nuget add source コマンド
description: dotnet nuget add source コマンドを使うと、NuGet 構成ファイルに新しいパッケージ ソースを追加できます。
ms.date: 03/20/2020
ms.openlocfilehash: df31a2eaba997d0e9fe4f4c2666052fd7c7c2f03
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105052"
---
# <a name="dotnet-nuget-add-source"></a><span data-ttu-id="726cf-103">dotnet nuget add source</span><span class="sxs-lookup"><span data-stu-id="726cf-103">dotnet nuget add source</span></span>

<span data-ttu-id="726cf-104">**この記事の対象:** ✔️ .NET Core 3.1.200 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="726cf-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="726cf-105">名前</span><span class="sxs-lookup"><span data-stu-id="726cf-105">Name</span></span>

<span data-ttu-id="726cf-106">`dotnet nuget add source` - NuGet ソースを追加にします。</span><span class="sxs-lookup"><span data-stu-id="726cf-106">`dotnet nuget add source` - Add a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="726cf-107">構文</span><span class="sxs-lookup"><span data-stu-id="726cf-107">Synopsis</span></span>

```dotnetcli
dotnet nuget add source <PACKAGE_SOURCE_PATH> [--name <SOURCE_NAME>] [--username <USER>]
    [--password <PASSWORD>] [--store-password-in-clear-text]
    [--valid-authentication-types <TYPES>] [--configfile <FILE>]

dotnet nuget add source -h|--help
```

## <a name="description"></a><span data-ttu-id="726cf-108">説明</span><span class="sxs-lookup"><span data-stu-id="726cf-108">Description</span></span>

<span data-ttu-id="726cf-109">`dotnet nuget add source` コマンドを使うと、NuGet 構成ファイルに新しいパッケージ ソースを追加できます。</span><span class="sxs-lookup"><span data-stu-id="726cf-109">The `dotnet nuget add source` command adds a new package source to your NuGet configuration files.</span></span>

> [!WARNING]
> <span data-ttu-id="726cf-110">複数のパッケージ ソースを追加するとき、[依存関係かく乱脆弱性](https://aka.ms/pkg-sec-wp)を持ち込まないようにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="726cf-110">When adding multiple package sources, be careful not to introduce a [dependency confusion vulnerability](https://aka.ms/pkg-sec-wp).</span></span>

## <a name="arguments"></a><span data-ttu-id="726cf-111">引数</span><span class="sxs-lookup"><span data-stu-id="726cf-111">Arguments</span></span>

- **`PACKAGE_SOURCE_PATH`**

  <span data-ttu-id="726cf-112">パッケージ ソースへのパス。</span><span class="sxs-lookup"><span data-stu-id="726cf-112">Path to the package source.</span></span>

## <a name="options"></a><span data-ttu-id="726cf-113">オプション</span><span class="sxs-lookup"><span data-stu-id="726cf-113">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="726cf-114">NuGet 構成ファイル。</span><span class="sxs-lookup"><span data-stu-id="726cf-114">The NuGet configuration file.</span></span> <span data-ttu-id="726cf-115">指定した場合、このファイルの設定のみが使用されます。</span><span class="sxs-lookup"><span data-stu-id="726cf-115">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="726cf-116">指定しない場合、現在のディレクトリからの構成ファイルの階層が使用されます。</span><span class="sxs-lookup"><span data-stu-id="726cf-116">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="726cf-117">詳細については、「[一般的な NuGet 構成](/nuget/consume-packages/configuring-nuget-behavior)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="726cf-117">For more information, see [Common NuGet Configurations](/nuget/consume-packages/configuring-nuget-behavior).</span></span>

- **`-n|--name <SOURCE_NAME>`**

  <span data-ttu-id="726cf-118">ソースの名前。</span><span class="sxs-lookup"><span data-stu-id="726cf-118">Name of the source.</span></span>

- **`-p|--password <PASSWORD>`**

  <span data-ttu-id="726cf-119">認証済みソースに接続するときに使用するパスワード。</span><span class="sxs-lookup"><span data-stu-id="726cf-119">Password to be used when connecting to an authenticated source.</span></span>

- **`--store-password-in-clear-text`**

  <span data-ttu-id="726cf-120">パスワードの暗号化を無効にすることで、ポータブル パッケージ ソースの資格情報を保存できるようにします。</span><span class="sxs-lookup"><span data-stu-id="726cf-120">Enables storing portable package source credentials by disabling password encryption.</span></span>

- **`-u|--username <USER>`**

  <span data-ttu-id="726cf-121">認証済みソースに接続するときに使用するユーザー名。</span><span class="sxs-lookup"><span data-stu-id="726cf-121">Username to be used when connecting to an authenticated source.</span></span>

- **`--valid-authentication-types <TYPES>`**

  <span data-ttu-id="726cf-122">このソースに対して有効な認証の種類のコンマ区切りのリスト。</span><span class="sxs-lookup"><span data-stu-id="726cf-122">Comma-separated list of valid authentication types for this source.</span></span> <span data-ttu-id="726cf-123">サーバーによって NTLM または Negotiate がアドバタイズされていて、基本メカニズムを使用して資格情報を送信する必要がある場合は、これを `basic` に設定します。たとえば、オンプレミスの Azure DevOps Server で PAT を使用する場合などです。</span><span class="sxs-lookup"><span data-stu-id="726cf-123">Set this to `basic` if the server advertises NTLM or Negotiate and your credentials must be sent using the Basic mechanism, for instance when using a PAT with on-premises Azure DevOps Server.</span></span> <span data-ttu-id="726cf-124">その他の有効な値には、`negotiate`、`kerberos`、`ntlm`、`digest` などがありますが、これらの値は役に立たない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="726cf-124">Other valid values include `negotiate`, `kerberos`, `ntlm`, and `digest`, but these values are unlikely to be useful.</span></span>

## <a name="examples"></a><span data-ttu-id="726cf-125">使用例</span><span class="sxs-lookup"><span data-stu-id="726cf-125">Examples</span></span>

- <span data-ttu-id="726cf-126">`nuget.org` をソースとして追加します。</span><span class="sxs-lookup"><span data-stu-id="726cf-126">Add `nuget.org` as a source:</span></span>

  ```dotnetcli
  dotnet nuget add source https://api.nuget.org/v3/index.json -n nuget.org
  ```

- <span data-ttu-id="726cf-127">`c:\packages` をローカル ソースとして追加します。</span><span class="sxs-lookup"><span data-stu-id="726cf-127">Add `c:\packages` as a local source:</span></span>

  ```dotnetcli
  dotnet nuget add source c:\packages
  ```

- <span data-ttu-id="726cf-128">認証が必要なソースを追加します。</span><span class="sxs-lookup"><span data-stu-id="726cf-128">Add a source that needs authentication:</span></span>

  ```dotnetcli
  dotnet nuget add source https://someServer/myTeam -n myTeam -u myUsername -p myPassword --store-password-in-clear-text
  ```

- <span data-ttu-id="726cf-129">認証が必要なソースを追加します (その後資格情報プロバイダーをインストールします)。</span><span class="sxs-lookup"><span data-stu-id="726cf-129">Add a source that needs authentication (then go install credential provider):</span></span>

  ```dotnetcli
  dotnet nuget add source https://azureartifacts.microsoft.com/myTeam -n myTeam
  ```

## <a name="see-also"></a><span data-ttu-id="726cf-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="726cf-130">See also</span></span>

- [<span data-ttu-id="726cf-131">NuGet.config ファイルのパッケージ ソース セクション</span><span class="sxs-lookup"><span data-stu-id="726cf-131">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="726cf-132">sources コマンド (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="726cf-132">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
