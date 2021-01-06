---
title: 破壊的変更:TargetFramework が netcoreapp から net に変更される
description: .NET 5.0 での破壊的変更について学習します。MSBuild TargetFramework プロパティの値が netcoreapp3.1 から net5.0 に変更されました。
ms.date: 10/17/2020
ms.openlocfilehash: c3b39a36548d58d6ed75fd8b1c84b0cccfc738f0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759399"
---
# <a name="targetframework-change-from-netcoreapp-to-net"></a><span data-ttu-id="a5811-103">TargetFramework が netcoreapp から net に変更される</span><span class="sxs-lookup"><span data-stu-id="a5811-103">TargetFramework change from netcoreapp to net</span></span>

<span data-ttu-id="a5811-104">MSBuild `TargetFramework` プロパティの値が `netcoreapp3.1` から `net5.0` に変更されました。</span><span class="sxs-lookup"><span data-stu-id="a5811-104">The value for the MSBuild `TargetFramework` property changed from `netcoreapp3.1` to `net5.0`.</span></span> <span data-ttu-id="a5811-105">それにより、`TargetFramework` の値の解析に依存するコードが破損するおそれがあります。</span><span class="sxs-lookup"><span data-stu-id="a5811-105">This can break code that relies on parsing the value of `TargetFramework`.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="a5811-106">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="a5811-106">Version introduced</span></span>

<span data-ttu-id="a5811-107">5.0</span><span class="sxs-lookup"><span data-stu-id="a5811-107">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="a5811-108">変更の説明</span><span class="sxs-lookup"><span data-stu-id="a5811-108">Change description</span></span>

<span data-ttu-id="a5811-109">.NET Core 1.0 から 3.1 では、MSBuild `TargetFramework` の値は `netcoreapp` で始まります。たとえば、.NET Core 3.1 を対象とするアプリの場合、`netcoreapp3.1` になります。</span><span class="sxs-lookup"><span data-stu-id="a5811-109">In .NET Core 1.0 - 3.1, the value for the MSBuild `TargetFramework` property starts with `netcoreapp`, for example, `netcoreapp3.1` for apps that target .NET Core 3.1.</span></span> <span data-ttu-id="a5811-110">.NET 5.0 以降、この値が簡略化され、`net` で始まります。たとえば、.NET 5.0 の場合、`net5.0` になります。</span><span class="sxs-lookup"><span data-stu-id="a5811-110">Starting in .NET 5.0, this value is simplified to just start with `net`, for example, `net5.0` for .NET 5.0.</span></span>

<span data-ttu-id="a5811-111">詳細については、「[The future of .NET Standard](https://devblogs.microsoft.com/dotnet/the-future-of-net-standard/)」 (.NET Standard の未来) と「[Target framework names in .NET 5](https://github.com/dotnet/designs/blob/main/accepted/2020/net5/net5.md)」 (.NET 5 のターゲット フレームワーク名) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5811-111">For more information, see [The future of .NET Standard](https://devblogs.microsoft.com/dotnet/the-future-of-net-standard/) and [Target framework names in .NET 5](https://github.com/dotnet/designs/blob/main/accepted/2020/net5/net5.md).</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="a5811-112">変更理由</span><span class="sxs-lookup"><span data-stu-id="a5811-112">Reason for change</span></span>

- <span data-ttu-id="a5811-113">`TargetFramework` 値を簡略化します。</span><span class="sxs-lookup"><span data-stu-id="a5811-113">Simplifies the `TargetFramework` value.</span></span>
- <span data-ttu-id="a5811-114">`TargetFramework` プロパティに `TargetPlatform` を含めることをプロジェクトで可能にします。</span><span class="sxs-lookup"><span data-stu-id="a5811-114">Enables projects to include a `TargetPlatform` in the `TargetFramework` property.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="a5811-115">推奨される操作</span><span class="sxs-lookup"><span data-stu-id="a5811-115">Recommended action</span></span>

<span data-ttu-id="a5811-116">`TargetFramework` の値を解析するロジックがある場合、それを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a5811-116">If you have logic that parses the value of `TargetFramework`, you'll need to update it.</span></span> <span data-ttu-id="a5811-117">たとえば、次の MSBuild 条件は `TargetFramework` の値に依存します。</span><span class="sxs-lookup"><span data-stu-id="a5811-117">For example, the following MSBuild condition relies on the value of `TargetFramework`.</span></span>

```xml
<PropertyGroup Condition="$(TargetFramework.StartsWith('netcoreapp'))">
```

<span data-ttu-id="a5811-118">この要件の場合、代わりにターゲット フレームワークの識別子を比較するようにコードを更新できます。</span><span class="sxs-lookup"><span data-stu-id="a5811-118">For this requirement, you can update the code to compare the target framework identifier instead.</span></span>

```xml
<PropertyGroup Condition="'$([MSBuild]::GetTargetFrameworkIdentifier('$(TargetFramework)'))' == '.NETCoreApp'">
```

## <a name="affected-apis"></a><span data-ttu-id="a5811-119">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="a5811-119">Affected APIs</span></span>

<span data-ttu-id="a5811-120">N/A</span><span class="sxs-lookup"><span data-stu-id="a5811-120">N/A</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

MSBuild

-->