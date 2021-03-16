---
ms.openlocfilehash: d9489df1ba096109e60d663e3a3f4442d30b2bb1
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105469"
---
### <a name="project-tools-now-included-in-sdk"></a><span data-ttu-id="daa15-101">プロジェクト ツールが SDK に追加されました</span><span class="sxs-lookup"><span data-stu-id="daa15-101">Project tools now included in SDK</span></span>

<span data-ttu-id="daa15-102">.NET Core 2.1 SDK に一般的な CLI ツールが追加されました。これらのツールをプロジェクトから参照する必要がなくなりました。</span><span class="sxs-lookup"><span data-stu-id="daa15-102">The .NET Core 2.1 SDK now includes common CLI tooling, and you no longer need to reference these tools from the project.</span></span>

#### <a name="change-description"></a><span data-ttu-id="daa15-103">変更内容</span><span class="sxs-lookup"><span data-stu-id="daa15-103">Change description</span></span>

<span data-ttu-id="daa15-104">.NET Core 2.0 では、`<DotNetCliToolReference>` プロジェクト設定で外部 .NET ツールがプロジェクトによって参照されます。</span><span class="sxs-lookup"><span data-stu-id="daa15-104">In .NET Core 2.0, projects reference external .NET tools with the `<DotNetCliToolReference>` project setting.</span></span> <span data-ttu-id="daa15-105">.NET Core 2.1 では、これらのツールの一部が .NET Core SDK に付属します。この設定は不要になりました。</span><span class="sxs-lookup"><span data-stu-id="daa15-105">In .NET Core 2.1, some of these tools are included with the .NET Core SDK, and the setting is no longer needed.</span></span> <span data-ttu-id="daa15-106">プロジェクトにこれらのツールへの参照を含めると、"**ツール 'Microsoft.EntityFrameworkCore.Tools.DotNet' は .NET Core SDK に付属するようになりました**" のようなエラーが届きます。</span><span class="sxs-lookup"><span data-stu-id="daa15-106">If you include references to these tools in your project, you'll receive an error similar to the following: **The tool 'Microsoft.EntityFrameworkCore.Tools.DotNet' is now included in the .NET Core SDK.**</span></span>

<span data-ttu-id="daa15-107">.NET Core 2.1 SDK に追加されたツール:</span><span class="sxs-lookup"><span data-stu-id="daa15-107">Tools now included in .NET Core 2.1 SDK:</span></span>

| <span data-ttu-id="daa15-108">\<DotNetCliToolReference> 値</span><span class="sxs-lookup"><span data-stu-id="daa15-108">\<DotNetCliToolReference> value</span></span>                   | <span data-ttu-id="daa15-109">ツール</span><span class="sxs-lookup"><span data-stu-id="daa15-109">Tool</span></span>                                                                                                            |
|------------------------------------------------|-----------------------------------------------------------------------------------------------------------------|
| `Microsoft.DotNet.Watcher.Tools`               | [<span data-ttu-id="daa15-110">dotnet-watch</span><span class="sxs-lookup"><span data-stu-id="daa15-110">dotnet-watch</span></span>](https://github.com/dotnet/aspnetcore/blob/master/src/Tools/dotnet-watch/README.md)               |
| `Microsoft.Extensions.SecretManager.Tools`     | [<span data-ttu-id="daa15-111">dotnet-user-secrets</span><span class="sxs-lookup"><span data-stu-id="daa15-111">dotnet-user-secrets</span></span>](https://github.com/dotnet/aspnetcore/blob/master/src/Tools/dotnet-user-secrets/README.md) |
| `Microsoft.Extensions.Caching.SqlConfig.Tools` | [<span data-ttu-id="daa15-112">dotnet-sql-cache</span><span class="sxs-lookup"><span data-stu-id="daa15-112">dotnet-sql-cache</span></span>](https://github.com/dotnet/aspnetcore/blob/master/src/Tools/dotnet-sql-cache/README.md)       |
| `Microsoft.EntityFrameworkCore.Tools.DotNet`   | [<span data-ttu-id="daa15-113">dotnet-ef</span><span class="sxs-lookup"><span data-stu-id="daa15-113">dotnet-ef</span></span>](/ef/core/miscellaneous/cli/dotnet)                                                                  |

#### <a name="version-introduced"></a><span data-ttu-id="daa15-114">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="daa15-114">Version introduced</span></span>

<span data-ttu-id="daa15-115">.NET Core SDK 2.1.300</span><span class="sxs-lookup"><span data-stu-id="daa15-115">.NET Core SDK 2.1.300</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="daa15-116">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="daa15-116">Recommended action</span></span>

<span data-ttu-id="daa15-117">プロジェクトから `<DotNetCliToolReference>` 設定を削除します。</span><span class="sxs-lookup"><span data-stu-id="daa15-117">Remove the `<DotNetCliToolReference>` setting from your project.</span></span>

#### <a name="category"></a><span data-ttu-id="daa15-118">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="daa15-118">Category</span></span>

<span data-ttu-id="daa15-119">MSBuild</span><span class="sxs-lookup"><span data-stu-id="daa15-119">MSBuild</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="daa15-120">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="daa15-120">Affected APIs</span></span>

<span data-ttu-id="daa15-121">N/A</span><span class="sxs-lookup"><span data-stu-id="daa15-121">N/A</span></span>
