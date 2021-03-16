---
title: 破壊的変更:Directory.Packages.props ファイルが既定でインポートされる
description: .NET 5 での破壊的変更について学習します。Directory.Packages.props という名前のファイルがプロジェクト フォルダーに含まれている場合、NuGet の .props ファイルによってそのファイルのインポートが自動的に行われます。
ms.date: 09/17/2020
ms.openlocfilehash: a031d9b2bd832be06dedb20495c24075d1239b02
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256583"
---
# <a name="directorypackagesprops-files-is-imported-by-default"></a><span data-ttu-id="39665-103">Directory.Packages.props ファイルが既定でインポートされる</span><span class="sxs-lookup"><span data-stu-id="39665-103">Directory.Packages.props files is imported by default</span></span>

<span data-ttu-id="39665-104">NuGet の *.props* ファイルでは、*Directory.Packages.props* という名前のファイルがプロジェクト フォルダーまたはその先祖に含まれている場合は、そのファイルのインポートが自動的に行われます。</span><span class="sxs-lookup"><span data-stu-id="39665-104">NuGet's *.props* files automatically import a file named *Directory.Packages.props* if it's found in the project folder or any of its ancestors.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="39665-105">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="39665-105">Version introduced</span></span>

<span data-ttu-id="39665-106">5.0</span><span class="sxs-lookup"><span data-stu-id="39665-106">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="39665-107">変更の説明</span><span class="sxs-lookup"><span data-stu-id="39665-107">Change description</span></span>

<span data-ttu-id="39665-108">以前の .NET バージョンでは、*Directory.Packages.props* という名前のファイルをプロジェクト ファイルに含めることができ、ビルド時に NuGet の *.props* によって自動的にインポートされることはありませんでした。</span><span class="sxs-lookup"><span data-stu-id="39665-108">In previous .NET versions, you could have a file named *Directory.Packages.props* in your project file and it wouldn't be automatically imported by NuGet's *.props* file at build time.</span></span>

<span data-ttu-id="39665-109">.NET 5 以降では、このようなファイルがプロジェクト フォルダーまたはその先祖に存在している場合は、そのファイルのインポートが自動的に "*行われます*"。</span><span class="sxs-lookup"><span data-stu-id="39665-109">Starting in .NET 5, such a file *is* automatically imported if it exists in the project folder or any of its ancestors.</span></span> <span data-ttu-id="39665-110">この名前のファイルがプロジェクト フォルダーにある場合は、この自動インポート機能によってビルドの動作が変わる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="39665-110">If you have a file with this name in your project folder, this automatic import could change behavior of the build.</span></span> <span data-ttu-id="39665-111">たとえば、そのファイルは今後インポートされるものの以前はインポートされていなかったか、明示的にインポートした場合にインポートされる順序が変わるなどします。</span><span class="sxs-lookup"><span data-stu-id="39665-111">For example, the file will be imported but it wasn't before, or the order of when it's imported could change if you specifically import it.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="39665-112">変更理由</span><span class="sxs-lookup"><span data-stu-id="39665-112">Reason for change</span></span>

<span data-ttu-id="39665-113">この変更は、NuGet を対象とした[パッケージのバージョン集中管理](https://github.com/NuGet/Home/wiki/Centrally-managing-NuGet-package-versions)をサポートするために行われました。</span><span class="sxs-lookup"><span data-stu-id="39665-113">This change was made in order to support [central package versioning](https://github.com/NuGet/Home/wiki/Centrally-managing-NuGet-package-versions) for NuGet.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="39665-114">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="39665-114">Recommended action</span></span>

<span data-ttu-id="39665-115">既存の *Directory.Packages.props* ファイルが自動的にインポートされないようにする場合は、そのファイルの名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="39665-115">Rename the existing *Directory.Packages.props* file if it should not be imported automatically.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="39665-116">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="39665-116">Affected APIs</span></span>

<span data-ttu-id="39665-117">N/A</span><span class="sxs-lookup"><span data-stu-id="39665-117">N/A</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

MSBuild

-->
