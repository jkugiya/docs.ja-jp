---
title: 'NETSDK1004: 資産ファイルが見つかりません'
description: .NET SDK エラー NETSDK1004 について学習します。これは、project.assets.json ファイルが見つからない場合に発生します。
ms.topic: error-reference
ms.date: 01/29/2021
f1_keywords:
- NETSDK1004
ms.openlocfilehash: 8416063fe318106cbcb4dbccacef3ecaaff5bba2
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2021
ms.locfileid: "99216436"
---
# <a name="netsdk1004-assets-file-not-found"></a><span data-ttu-id="7b24a-103">NETSDK1004: 資産ファイルが見つかりません</span><span class="sxs-lookup"><span data-stu-id="7b24a-103">NETSDK1004: Assets file not found</span></span>

<span data-ttu-id="7b24a-104">**この記事の対象:** ✔️ .NET Core 2.1.100 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="7b24a-104">**This article applies to:** ✔️ .NET Core 2.1.100 SDK and later versions</span></span>

<span data-ttu-id="7b24a-105">NuGet によって、*project.assets.json* という名前のファイルが *obj* フォルダーに書き込まれます。これはコンパイラに渡すパッケージに関する情報を取得するために .NET SDK によって使用されます。</span><span class="sxs-lookup"><span data-stu-id="7b24a-105">NuGet writes a file named *project.assets.json* in the *obj* folder, and the .NET SDK uses it to get information about packages to pass into the compiler.</span></span> <span data-ttu-id="7b24a-106">このエラーが発生するのは、資産ファイル *project.assets.json* がビルド中に見つからない場合です。</span><span class="sxs-lookup"><span data-stu-id="7b24a-106">This error occurs when the assets file *project.assets.json* is not found during build.</span></span> <span data-ttu-id="7b24a-107">完全なエラー メッセージは、次の例のようになります。</span><span class="sxs-lookup"><span data-stu-id="7b24a-107">The full error message is similar to the following example:</span></span>

<span data-ttu-id="7b24a-108">**NETSDK1004: 資産ファイル 'C:\path\to\project.assets.json' が見つかりません。このファイルを生成するには、NuGet パッケージの復元を実行します。**</span><span class="sxs-lookup"><span data-stu-id="7b24a-108">**NETSDK1004: Assets file 'C:\path\to\project.assets.json' not found. Run a NuGet package restore to generate this file.**</span></span>

<span data-ttu-id="7b24a-109">このエラーの原因として考えられるものをいくつか以下に示します。</span><span class="sxs-lookup"><span data-stu-id="7b24a-109">Here are some possible causes of the error:</span></span>

* <span data-ttu-id="7b24a-110">`%` 文字を含むディレクトリ パスから `dotnet build` コマンドを実行している。</span><span class="sxs-lookup"><span data-stu-id="7b24a-110">You are running the `dotnet build` command from a directory path that contains a `%` character.</span></span> <span data-ttu-id="7b24a-111">このエラーを解決するには、フォルダー名から `%` を削除し、`dotnet build` を再実行します。</span><span class="sxs-lookup"><span data-stu-id="7b24a-111">To resolve the error, remove the `%` from the folder name, and rerun `dotnet build`.</span></span>
* <span data-ttu-id="7b24a-112">プロジェクト ファイルに対する変更が、プロジェクト システムによって自動的に検出および復元されなかった。</span><span class="sxs-lookup"><span data-stu-id="7b24a-112">A change to the project file wasn't automatically detected and restored by the project system.</span></span> <span data-ttu-id="7b24a-113">このエラーを解決するには、コマンド プロンプトを開き、プロジェクトで `dotnet restore` を実行します。</span><span class="sxs-lookup"><span data-stu-id="7b24a-113">To resolve the error, open a command prompt and run `dotnet restore` on the project.</span></span>
* <span data-ttu-id="7b24a-114">プロジェクトが、古いバージョンの Nuget.exe によって個別に復元された。</span><span class="sxs-lookup"><span data-stu-id="7b24a-114">A project was restored separately by an older version of Nuget.exe.</span></span> <span data-ttu-id="7b24a-115">このエラーを解決するには、コマンド プロンプトを開き、プロジェクトで `dotnet restore` を実行します。</span><span class="sxs-lookup"><span data-stu-id="7b24a-115">To resolve the error, open a command prompt and run `dotnet restore` on the project.</span></span>
* <span data-ttu-id="7b24a-116">NETSDK1045 (使用している SDK のバージョンでプロジェクトのターゲット フレームワークがサポートされていない) などの以前のエラーにより、NuGet でプロジェクト資産ファイルが作成されなかった。</span><span class="sxs-lookup"><span data-stu-id="7b24a-116">An earlier error, such as NETSDK1045 (the version of the SDK you're using doesn't support the project's target framework), prevented NuGet from creating the project assets file.</span></span> <span data-ttu-id="7b24a-117">NETSDK1004 エラーを解決するには、以前のエラーを解決してから、プロジェクトで `dotnet restore` を実行します。</span><span class="sxs-lookup"><span data-stu-id="7b24a-117">To resolve the NETSDK1004 error, resolve the earlier error, and then run `dotnet restore` on the project.</span></span>
* <span data-ttu-id="7b24a-118">App Center CI で、NuGet にはない外部アセンブリを含むプロジェクトがビルドされている。</span><span class="sxs-lookup"><span data-stu-id="7b24a-118">App Center CI is building a project that has an external assembly that is not in NuGet.</span></span> <span data-ttu-id="7b24a-119">このエラーを解決するには、アセンブリの NuGet パッケージを使用します。</span><span class="sxs-lookup"><span data-stu-id="7b24a-119">To resolve the error, use a NuGet package for the assembly.</span></span>
