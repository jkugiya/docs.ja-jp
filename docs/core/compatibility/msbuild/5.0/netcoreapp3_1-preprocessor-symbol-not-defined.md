---
title: 破壊的変更:.NET 5 を対象とする場合の NETCOREAPP3_1 プリプロセッサ シンボルが定義されていない
description: .NET 5 での破壊的変更について学習します。プロジェクトでのプリプロセッサ シンボルの定義は以前のバージョンに対しては行われなくなります。
ms.date: 09/17/2020
ms.openlocfilehash: 390c8f5af97510db4652f3f42db577e6de158020
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256531"
---
# <a name="netcoreapp3_1-preprocessor-symbol-is-not-defined-when-targeting-net-5"></a><span data-ttu-id="a975c-103">.NET 5 を対象とする場合の NETCOREAPP3_1 プリプロセッサ シンボルが定義されていない</span><span class="sxs-lookup"><span data-stu-id="a975c-103">NETCOREAPP3_1 preprocessor symbol is not defined when targeting .NET 5</span></span>

<span data-ttu-id="a975c-104">.NET 5 RC2 以降のバージョンでは、プロジェクトでのプリプロセッサ シンボルの定義は対象とするバージョンに対してのみ行われ、以前のバージョンでは行われなくなります。</span><span class="sxs-lookup"><span data-stu-id="a975c-104">In .NET 5 RC2 and later versions, projects no longer define preprocessor symbols for earlier versions, but only for the version that they target.</span></span> <span data-ttu-id="a975c-105">これは、.NET Core 1.0 - 3.1 と同じ動作です。</span><span class="sxs-lookup"><span data-stu-id="a975c-105">This is the same behavior as .NET Core 1.0 - 3.1.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="a975c-106">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="a975c-106">Version introduced</span></span>

<span data-ttu-id="a975c-107">5.0 RC2</span><span class="sxs-lookup"><span data-stu-id="a975c-107">5.0 RC2</span></span>

## <a name="change-description"></a><span data-ttu-id="a975c-108">変更内容</span><span class="sxs-lookup"><span data-stu-id="a975c-108">Change description</span></span>

<span data-ttu-id="a975c-109">.NET 5 Preview 7 から RC1 では、`net5.0` を対象とするプロジェクトで `NETCOREAPP3_1` と `NET5_0` の両方のプリプロセッサ シンボルが定義されます。</span><span class="sxs-lookup"><span data-stu-id="a975c-109">In .NET 5 preview 7 through RC1, projects that target `net5.0` define both `NETCOREAPP3_1` and `NET5_0` preprocessor symbols.</span></span> <span data-ttu-id="a975c-110">この動作変更は、.NET 5 以降で、条件付きコンパイルの[シンボルが累積になる](https://github.com/dotnet/designs/blob/main/accepted/2020/net5/net5.md#preprocessor-symbols)ことを意図したものでした。</span><span class="sxs-lookup"><span data-stu-id="a975c-110">The intent behind this behavior change was that starting with .NET 5, conditional compilation [symbols would be cumulative](https://github.com/dotnet/designs/blob/main/accepted/2020/net5/net5.md#preprocessor-symbols).</span></span>

<span data-ttu-id="a975c-111">.NET 5 RC2 以降では、プロジェクトは、以前のバージョンではなく、対象となるターゲット フレームワーク モニカー (TFM) のみに対するシンボルを定義します。</span><span class="sxs-lookup"><span data-stu-id="a975c-111">In .NET 5 RC2 and later, projects only define symbols for the target framework monikers (TFM) that it targets and not for any earlier versions.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="a975c-112">変更理由</span><span class="sxs-lookup"><span data-stu-id="a975c-112">Reason for change</span></span>

<span data-ttu-id="a975c-113">Preview 7 からの変更は、お客様からのフィードバックにより元に戻されました。</span><span class="sxs-lookup"><span data-stu-id="a975c-113">The change from preview 7 was reverted due to customer feedback.</span></span> <span data-ttu-id="a975c-114">以前のバージョンのシンボルの定義はお客様を驚かせ、混乱させました。C# のコンパイラにバグがあったと考えたお客様もいました。</span><span class="sxs-lookup"><span data-stu-id="a975c-114">Defining symbols for earlier versions surprised and confused customers, and some assumed it was a bug in the C# compiler.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="a975c-115">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="a975c-115">Recommended action</span></span>

<span data-ttu-id="a975c-116">プロジェクトが `net5.0` 以上を対象とするときに `NETCOREAPP3_1` が定義されていることを `#if` ロジックで前提としていないことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="a975c-116">Make sure that your `#if` logic doesn't assume that `NETCOREAPP3_1` is defined when the project targets `net5.0` or higher.</span></span> <span data-ttu-id="a975c-117">代わりに、プロジェクトが `netcoreapp3.1` を明示的に対象としている場合は `NETCOREAPP3_1` のみが定義されることを前提としてください。</span><span class="sxs-lookup"><span data-stu-id="a975c-117">Instead, assume that `NETCOREAPP3_1` is only defined when the project explicitly targets `netcoreapp3.1`.</span></span>

<span data-ttu-id="a975c-118">たとえば、プロジェクトが .NET Core 2.1 および .NET Core 3.1 のマルチターゲットで、.NET Core 3.1 で導入された API を呼び出す場合、`#if` ロジックは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="a975c-118">For example, if your project multitargets for .NET Core 2.1 and .NET Core 3.1 and you call APIs that were introduced in .NET Core 3.1, your `#if` logic should look as follows:</span></span>

```csharp
#if NETCOREAPP2_1 || NETCOREAPP3_0
    // Fallback behavior for old versions.
#elif NETCOREAPP
    // Behavior for .NET Core 3.1 and later.
#endif
```

## <a name="affected-apis"></a><span data-ttu-id="a975c-119">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="a975c-119">Affected APIs</span></span>

<span data-ttu-id="a975c-120">N/A</span><span class="sxs-lookup"><span data-stu-id="a975c-120">N/A</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

MSBuild

-->
