---
title: '破壊的変更: WPF アプリと WinForms アプリで OutputType が WinExe に設定されている'
description: .NET 5.0 での破壊的変更について学習します。Windows フォーム アプリで OutputType が自動的に WinExe に設定されます。
ms.date: 09/18/2020
ms.openlocfilehash: 072c5b11c8304eb540e176ce9747930789f28505
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760022"
---
# <a name="outputtype-set-to-winexe-for-wpf-and-winforms-apps"></a><span data-ttu-id="1bdee-103">WPF アプリと WinForms アプリで OutputType が WinExe に設定されている</span><span class="sxs-lookup"><span data-stu-id="1bdee-103">OutputType set to WinExe for WPF and WinForms apps</span></span>

<span data-ttu-id="1bdee-104">`OutputType` は、Windows Presentation Foundation (WPF) アプリと Windows フォーム アプリでは、自動的に `WinExe` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="1bdee-104">`OutputType` is automatically set to `WinExe` for Windows Presentation Foundation (WPF) and Windows Forms apps.</span></span> <span data-ttu-id="1bdee-105">`OutputType` が `WinExe` に設定されている場合、アプリの実行時にコンソール ウィンドウは開きません。</span><span class="sxs-lookup"><span data-stu-id="1bdee-105">When `OutputType` is set to `WinExe`, a console window doesn't open when the app is executed.</span></span>

## <a name="change-description"></a><span data-ttu-id="1bdee-106">変更内容</span><span class="sxs-lookup"><span data-stu-id="1bdee-106">Change description</span></span>

<span data-ttu-id="1bdee-107">以前のバージョンの .NET では、プロジェクト ファイルで `OutputType` に指定されている値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="1bdee-107">In previous versions of .NET, the value that's specified for `OutputType` in the project file is used.</span></span> <span data-ttu-id="1bdee-108">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="1bdee-108">For example:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="1bdee-109">.NET 5.0 以降では、WPF アプリと Windows フォーム アプリで `OutputType` が `WinExe` に自動的に設定されます。</span><span class="sxs-lookup"><span data-stu-id="1bdee-109">Starting in .NET 5.0, `OutputType` is automatically set to `WinExe` for WPF and Windows Forms apps.</span></span> <span data-ttu-id="1bdee-110">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="1bdee-110">For example:</span></span>

```xml
<PropertyGroup>
  <OutputType>WinExe</OutputType>
</PropertyGroup>
```

## <a name="reason-for-change"></a><span data-ttu-id="1bdee-111">変更理由</span><span class="sxs-lookup"><span data-stu-id="1bdee-111">Reason for change</span></span>

<span data-ttu-id="1bdee-112">WPF アプリまたは Windows フォーム アプリの実行時に、ほとんどのユーザーがコンソール ウィンドウを開かないことを前提としています。</span><span class="sxs-lookup"><span data-stu-id="1bdee-112">It's assumed that most users don't want a console window to open when a WPF or Windows Forms app is executed.</span></span> <span data-ttu-id="1bdee-113">さらに、[これらの種類のアプリケーションでは .NET SDK が使用され](sdk-and-target-framework-change.md) (Windows Desktop SDK が使用されるのではなく)、正しい既定値が設定されるようになります。</span><span class="sxs-lookup"><span data-stu-id="1bdee-113">In addition, [now that these application types use the .NET SDK](sdk-and-target-framework-change.md) instead of the Windows Desktop SDK, the correct default will be set.</span></span> <span data-ttu-id="1bdee-114">さらに、iOS と Android を対象としたサポートが追加されると、これらすべてで同じ出力の種類が使用される場合に、複数のプラットフォーム間で複数のターゲットを指定することが容易になります。</span><span class="sxs-lookup"><span data-stu-id="1bdee-114">Further, when support for targeting iOS and Android is added, it will be easier to multi-target between multiple platforms if they all use the same output type.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="1bdee-115">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="1bdee-115">Version introduced</span></span>

<span data-ttu-id="1bdee-116">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="1bdee-116">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="1bdee-117">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="1bdee-117">Recommended action</span></span>

<span data-ttu-id="1bdee-118">ユーザー側の対応は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="1bdee-118">No action is required in your part.</span></span> <span data-ttu-id="1bdee-119">ただし、以前の動作に戻す場合は、プロジェクト ファイルの `DisableWinExeOutputInference` プロパティを `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="1bdee-119">However, if you want to revert to the old behavior, set the `DisableWinExeOutputInference` property to `true` in your project file.</span></span>

```xml
<DisableWinExeOutputInference>true</DisableWinExeOutputInference>
```

## <a name="affected-apis"></a><span data-ttu-id="1bdee-120">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="1bdee-120">Affected APIs</span></span>

<span data-ttu-id="1bdee-121">API 分析では検出できません。</span><span class="sxs-lookup"><span data-stu-id="1bdee-121">Not detectable via API analysis.</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

- Windows Forms
- Windows Presentation Framework (WPF)

-->