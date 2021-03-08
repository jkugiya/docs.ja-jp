---
title: '破壊的変更: WPF アプリと WinForms アプリで OutputType が WinExe に設定されている'
description: .NET SDK 5.0.100 での破壊的変更について学習します。Windows フォーム アプリで OutputType が自動的に WinExe に設定されます。
ms.date: 02/08/2021
ms.openlocfilehash: 565007e9ce6be289456afc9facbd4c555a1110bd
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256180"
---
# <a name="outputtype-set-to-winexe-for-wpf-and-winforms-apps"></a><span data-ttu-id="4b7fe-103">WPF アプリと WinForms アプリで OutputType が WinExe に設定されている</span><span class="sxs-lookup"><span data-stu-id="4b7fe-103">OutputType set to WinExe for WPF and WinForms apps</span></span>

<span data-ttu-id="4b7fe-104">`OutputType` は、Windows Presentation Foundation (WPF) アプリと Windows フォーム アプリでは、自動的に `WinExe` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="4b7fe-104">`OutputType` is automatically set to `WinExe` for Windows Presentation Foundation (WPF) and Windows Forms apps.</span></span> <span data-ttu-id="4b7fe-105">`OutputType` が `WinExe` に設定されている場合、アプリの実行時にコンソール ウィンドウは開きません。</span><span class="sxs-lookup"><span data-stu-id="4b7fe-105">When `OutputType` is set to `WinExe`, a console window doesn't open when the app is executed.</span></span>

## <a name="change-description"></a><span data-ttu-id="4b7fe-106">変更内容</span><span class="sxs-lookup"><span data-stu-id="4b7fe-106">Change description</span></span>

<span data-ttu-id="4b7fe-107">以前のバージョンの .NET SDK では、プロジェクト ファイルで `OutputType` に指定されている値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="4b7fe-107">In previous versions of the .NET SDK, the value that's specified for `OutputType` in the project file is used.</span></span> <span data-ttu-id="4b7fe-108">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="4b7fe-108">For example:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="4b7fe-109">.NET SDK の 5.0.100 バージョンからは、`OutputType` を `Exe` に設定すると、.NET Framework を含むあらゆるフレームワーク バージョンを対象にする WPF アプリと Windows フォーム アプリの場合、自動的に `WinExe` に変更されます。</span><span class="sxs-lookup"><span data-stu-id="4b7fe-109">Starting in the 5.0.100 version of the .NET SDK, when `OutputType` is set to `Exe`, it is automatically changed to `WinExe` for WPF and Windows Forms apps that target any framework version, including .NET Framework.</span></span>

```xml
<PropertyGroup>
  <OutputType>WinExe</OutputType>
</PropertyGroup>
```

 <span data-ttu-id="4b7fe-110">`OutputType` がプロジェクト ファイルで指定されていない場合は、既定値の `Library` になり、その値は変更されません。</span><span class="sxs-lookup"><span data-stu-id="4b7fe-110">If `OutputType` is not specified in the project file, it defaults to `Library` and that value doesn't change.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="4b7fe-111">変更理由</span><span class="sxs-lookup"><span data-stu-id="4b7fe-111">Reason for change</span></span>

<span data-ttu-id="4b7fe-112">WPF アプリまたは Windows フォーム アプリの実行時に、ほとんどのユーザーがコンソール ウィンドウを開かないことを前提としています。</span><span class="sxs-lookup"><span data-stu-id="4b7fe-112">It's assumed that most users don't want a console window to open when a WPF or Windows Forms app is executed.</span></span> <span data-ttu-id="4b7fe-113">さらに、[これらの種類のアプリケーションでは .NET SDK が使用され](sdk-and-target-framework-change.md) (Windows Desktop SDK が使用されるのではなく)、正しい既定値が設定されるようになります。</span><span class="sxs-lookup"><span data-stu-id="4b7fe-113">In addition, [now that these application types use the .NET SDK](sdk-and-target-framework-change.md) instead of the Windows Desktop SDK, the correct default will be set.</span></span> <span data-ttu-id="4b7fe-114">さらに、iOS と Android を対象としたサポートが追加されると、これらすべてで同じ出力の種類が使用される場合に、複数のプラットフォーム間で複数のターゲットを指定することが容易になります。</span><span class="sxs-lookup"><span data-stu-id="4b7fe-114">Further, when support for targeting iOS and Android is added, it will be easier to multi-target between multiple platforms if they all use the same output type.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="4b7fe-115">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="4b7fe-115">Version introduced</span></span>

<span data-ttu-id="4b7fe-116">.NET 5.0.100</span><span class="sxs-lookup"><span data-stu-id="4b7fe-116">.NET 5.0.100</span></span>

## <a name="recommended-action"></a><span data-ttu-id="4b7fe-117">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="4b7fe-117">Recommended action</span></span>

<span data-ttu-id="4b7fe-118">ユーザー側の対応は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="4b7fe-118">No action is required in your part.</span></span> <span data-ttu-id="4b7fe-119">ただし、以前の動作に戻す場合は、プロジェクト ファイルの `DisableWinExeOutputInference` プロパティを `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="4b7fe-119">However, if you want to revert to the old behavior, set the `DisableWinExeOutputInference` property to `true` in your project file.</span></span>

```xml
<DisableWinExeOutputInference>true</DisableWinExeOutputInference>
```

## <a name="affected-apis"></a><span data-ttu-id="4b7fe-120">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="4b7fe-120">Affected APIs</span></span>

<span data-ttu-id="4b7fe-121">API 分析では検出できません。</span><span class="sxs-lookup"><span data-stu-id="4b7fe-121">Not detectable via API analysis.</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

- Windows Forms
- Windows Presentation Framework (WPF)

-->
