---
ms.openlocfilehash: 49aa98edec8ed1ce35dd501c57aa82e4ca4cf286
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104879778"
---
### <a name="project-tools-now-included-in-sdk"></a><span data-ttu-id="2e742-101">プロジェクト ツールが SDK に追加されました</span><span class="sxs-lookup"><span data-stu-id="2e742-101">Project tools now included in SDK</span></span>

<span data-ttu-id="2e742-102">.NET Core 2.1 SDK に一般的な CLI ツールが追加されました。これらのツールをプロジェクトから参照する必要がなくなりました。</span><span class="sxs-lookup"><span data-stu-id="2e742-102">The .NET Core 2.1 SDK now includes common CLI tooling, and you no longer need to reference these tools from the project.</span></span>

#### <a name="change-description"></a><span data-ttu-id="2e742-103">変更内容</span><span class="sxs-lookup"><span data-stu-id="2e742-103">Change description</span></span>

<span data-ttu-id="2e742-104">.NET Core 2.0 では、`<DotNetCliToolReference>` プロジェクト設定で外部 .NET ツールがプロジェクトによって参照されます。</span><span class="sxs-lookup"><span data-stu-id="2e742-104">In .NET Core 2.0, projects reference external .NET tools with the `<DotNetCliToolReference>` project setting.</span></span> <span data-ttu-id="2e742-105">.NET Core 2.1 では、これらのツールの一部が .NET Core SDK に付属します。この設定は不要になりました。</span><span class="sxs-lookup"><span data-stu-id="2e742-105">In .NET Core 2.1, some of these tools are included with the .NET Core SDK, and the setting is no longer needed.</span></span> <span data-ttu-id="2e742-106">プロジェクトにこれらのツールへの参照を含めると、"**ツール 'Microsoft.EntityFrameworkCore.Tools.DotNet' は .NET Core SDK に付属するようになりました**" のようなエラーが届きます。</span><span class="sxs-lookup"><span data-stu-id="2e742-106">If you include references to these tools in your project, you'll receive an error similar to the following: **The tool 'Microsoft.EntityFrameworkCore.Tools.DotNet' is now included in the .NET Core SDK.**</span></span>

<span data-ttu-id="2e742-107">.NET Core 2.1 SDK に追加されたツール:</span><span class="sxs-lookup"><span data-stu-id="2e742-107">Tools now included in .NET Core 2.1 SDK:</span></span>

| <span data-ttu-id="2e742-108">\<DotNetCliToolReference> 値</span><span class="sxs-lookup"><span data-stu-id="2e742-108">\<DotNetCliToolReference> value</span></span>                   | <span data-ttu-id="2e742-109">ツール</span><span class="sxs-lookup"><span data-stu-id="2e742-109">Tool</span></span>                                                                                                            |
|------------------------------------------------|-----------------------------------------------------------------------------------------------------------------|
| `Microsoft.DotNet.Watcher.Tools`               | `dotnet-watch`               |
| `Microsoft.Extensions.SecretManager.Tools`     | [<span data-ttu-id="2e742-110">dotnet-user-secrets</span><span class="sxs-lookup"><span data-stu-id="2e742-110">dotnet-user-secrets</span></span>](https://github.com/dotnet/aspnetcore/blob/main/src/Tools/dotnet-user-secrets/README.md) |
| `Microsoft.Extensions.Caching.SqlConfig.Tools` | [<span data-ttu-id="2e742-111">dotnet-sql-cache</span><span class="sxs-lookup"><span data-stu-id="2e742-111">dotnet-sql-cache</span></span>](https://github.com/dotnet/aspnetcore/blob/main/src/Tools/dotnet-sql-cache/README.md)       |
| `Microsoft.EntityFrameworkCore.Tools.DotNet`   | [<span data-ttu-id="2e742-112">dotnet-ef</span><span class="sxs-lookup"><span data-stu-id="2e742-112">dotnet-ef</span></span>](/ef/core/miscellaneous/cli/dotnet)                                                                  |

#### <a name="version-introduced"></a><span data-ttu-id="2e742-113">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="2e742-113">Version introduced</span></span>

<span data-ttu-id="2e742-114">.NET Core SDK 2.1.300</span><span class="sxs-lookup"><span data-stu-id="2e742-114">.NET Core SDK 2.1.300</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2e742-115">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="2e742-115">Recommended action</span></span>

<span data-ttu-id="2e742-116">プロジェクトから `<DotNetCliToolReference>` 設定を削除します。</span><span class="sxs-lookup"><span data-stu-id="2e742-116">Remove the `<DotNetCliToolReference>` setting from your project.</span></span>

#### <a name="category"></a><span data-ttu-id="2e742-117">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="2e742-117">Category</span></span>

<span data-ttu-id="2e742-118">MSBuild</span><span class="sxs-lookup"><span data-stu-id="2e742-118">MSBuild</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2e742-119">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="2e742-119">Affected APIs</span></span>

<span data-ttu-id="2e742-120">N/A</span><span class="sxs-lookup"><span data-stu-id="2e742-120">N/A</span></span>
