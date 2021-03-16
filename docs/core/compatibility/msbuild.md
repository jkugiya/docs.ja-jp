---
title: MSBuild に関する破壊的変更
description: MSBuild for .NET Core 2.1 から 3.1 の破壊的変更を一覧で示します。
ms.date: 02/22/2021
ms.openlocfilehash: 03fcd9807a83c4f679dc659b009c857e351b9b2d
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105644"
---
# <a name="msbuild-breaking-changes-in-net-core-21---31"></a><span data-ttu-id="ffc10-103">.NET Core 2.1 から 3.1 の MSBuild に関する破壊的変更</span><span class="sxs-lookup"><span data-stu-id="ffc10-103">MSBuild breaking changes in .NET Core 2.1 - 3.1</span></span>

<span data-ttu-id="ffc10-104">このページでは、次の破壊的変更について説明します。</span><span class="sxs-lookup"><span data-stu-id="ffc10-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="ffc10-105">互換性に影響する変更点</span><span class="sxs-lookup"><span data-stu-id="ffc10-105">Breaking change</span></span> | <span data-ttu-id="ffc10-106">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="ffc10-106">Version introduced</span></span> |
| - | - |
| [<span data-ttu-id="ffc10-107">デザイン時のビルドから最上位のパッケージ参照のみが返される</span><span class="sxs-lookup"><span data-stu-id="ffc10-107">Design-time builds only return top-level package references</span></span>](#design-time-builds-only-return-top-level-package-references) | <span data-ttu-id="ffc10-108">3.1</span><span class="sxs-lookup"><span data-stu-id="ffc10-108">3.1</span></span> |
| [<span data-ttu-id="ffc10-109">リソース マニフェストのファイル名の変更</span><span class="sxs-lookup"><span data-stu-id="ffc10-109">Resource manifest file name change</span></span>](#resource-manifest-file-name-change) | <span data-ttu-id="ffc10-110">3.0</span><span class="sxs-lookup"><span data-stu-id="ffc10-110">3.0</span></span> |
| [<span data-ttu-id="ffc10-111">プロジェクト ツールが SDK に追加されました</span><span class="sxs-lookup"><span data-stu-id="ffc10-111">Project tools now included in SDK</span></span>](#project-tools-now-included-in-sdk) | <span data-ttu-id="ffc10-112">2.1</span><span class="sxs-lookup"><span data-stu-id="ffc10-112">2.1</span></span> |

## <a name="net-core-31"></a><span data-ttu-id="ffc10-113">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="ffc10-113">.NET Core 3.1</span></span>

[!INCLUDE [design-time-builds-return-top-level-package-refs](../../../includes/core-changes/msbuild/3.1/design-time-builds-return-top-level-package-refs.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="ffc10-114">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="ffc10-114">.NET Core 3.0</span></span>

[!INCLUDE[Resource file names](../../../includes/core-changes/msbuild/3.0/resource-manifest-name.md)]

***

## <a name="net-core-21"></a><span data-ttu-id="ffc10-115">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="ffc10-115">.NET Core 2.1</span></span>

[!INCLUDE [DotNetCliToolReference project elements removed for bundled tools](../../../includes/core-changes/msbuild/2.1/dotnetclitoolreference.md)]

***
