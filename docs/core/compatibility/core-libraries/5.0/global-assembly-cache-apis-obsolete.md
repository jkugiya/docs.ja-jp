---
title: '破壊的変更: グローバル アセンブリ キャッシュ API は旧型式'
description: Core .NET ライブラリでの .NET 5 に関する破壊的変更について学習します。この変更により、GAC を処理する API は、失敗するか、操作が実行されません。
ms.date: 11/01/2020
ms.openlocfilehash: 39c7b092b06754a28723693c0147b7ec3a0b705e
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257480"
---
# <a name="global-assembly-cache-apis-are-obsolete"></a><span data-ttu-id="e8e1e-103">グローバル アセンブリ キャッシュ API は旧型式</span><span class="sxs-lookup"><span data-stu-id="e8e1e-103">Global assembly cache APIs are obsolete</span></span>

<span data-ttu-id="e8e1e-104">.NET Core および .NET 5 以降のバージョンでは、.NET Framework に存在していたグローバル アセンブリ キャッシュ (GAC) の概念がなくなりました。</span><span class="sxs-lookup"><span data-stu-id="e8e1e-104">.NET Core and .NET 5 and later versions eliminate the concept of the global assembly cache (GAC) that was present in .NET Framework.</span></span> <span data-ttu-id="e8e1e-105">そのため、GAC を処理するすべての .NET Core および .NET 5 以降の API は失敗するか、操作が実行されません。</span><span class="sxs-lookup"><span data-stu-id="e8e1e-105">As such, all .NET Core and .NET 5+ APIs that deal with the GAC either fail or perform no operation.</span></span>

<span data-ttu-id="e8e1e-106">開発者がこれらの API を使用しないようにするために、一部の GAC 関連の API は古いものとしてマークされており、コンパイル時に `SYSLIB0005` 警告が生成されます。</span><span class="sxs-lookup"><span data-stu-id="e8e1e-106">To help steer developers away from these APIs, some GAC-related APIs are marked as obsolete, and generate a `SYSLIB0005` warning at compile time.</span></span> <span data-ttu-id="e8e1e-107">これらの API は、将来のバージョンの .NET で削除される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e8e1e-107">These APIs may be removed in a future version of .NET.</span></span>

## <a name="change-description"></a><span data-ttu-id="e8e1e-108">変更内容</span><span class="sxs-lookup"><span data-stu-id="e8e1e-108">Change description</span></span>

<span data-ttu-id="e8e1e-109">次の API は古いものとしてマークされています。</span><span class="sxs-lookup"><span data-stu-id="e8e1e-109">The following APIs are marked obsolete.</span></span>

| <span data-ttu-id="e8e1e-110">API</span><span class="sxs-lookup"><span data-stu-id="e8e1e-110">API</span></span> | <span data-ttu-id="e8e1e-111">古いものとしてマークされる対象</span><span class="sxs-lookup"><span data-stu-id="e8e1e-111">Marked obsolete in...</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.GlobalAssemblyCache?displayProperty=nameWithType> | <span data-ttu-id="e8e1e-112">5.0 RC1</span><span class="sxs-lookup"><span data-stu-id="e8e1e-112">5.0 RC1</span></span> |

<span data-ttu-id="e8e1e-113">.NET Framework 2.x から 4.x では、クエリが実行されたアセンブリが GAC から読み込まれた場合は <xref:System.Reflection.Assembly.GlobalAssemblyCache> プロパティから `true` が返され、ディスク上の異なる場所から読み込まれた場合は `false` が返されます。</span><span class="sxs-lookup"><span data-stu-id="e8e1e-113">In .NET Framework 2.x - 4.x, the <xref:System.Reflection.Assembly.GlobalAssemblyCache> property returns `true` if the queried assembly was loaded from the GAC, and `false` if it was loaded from a different location on disk.</span></span> <span data-ttu-id="e8e1e-114">.NET Core 2.x から 3.x では、<xref:System.Reflection.Assembly.GlobalAssemblyCache> から常に `false` が返されます。これは、GAC が .NET Core に存在しないことを反映しています。</span><span class="sxs-lookup"><span data-stu-id="e8e1e-114">In .NET Core 2.x - 3.x, the <xref:System.Reflection.Assembly.GlobalAssemblyCache> always returns `false`, reflecting that the GAC does not exist in .NET Core.</span></span>

```csharp
Assembly asm = typeof(object).Assembly;
// Prints 'True' on .NET Framework, 'False' on .NET Core.
Console.WriteLine(asm.GlobalAssemblyCache);
```

<span data-ttu-id="e8e1e-115">.NET 5 以降のバージョンでは、<xref:System.Reflection.Assembly.GlobalAssemblyCache> プロパティからは引き続き、常に `false` が返されます。</span><span class="sxs-lookup"><span data-stu-id="e8e1e-115">In .NET 5 and later versions, the <xref:System.Reflection.Assembly.GlobalAssemblyCache> property continues to always return `false`.</span></span> <span data-ttu-id="e8e1e-116">しかし、プロパティ getter も、プロパティへのアクセスを停止する必要があることを呼び出し元に示すために、古いものとしてマークされています。</span><span class="sxs-lookup"><span data-stu-id="e8e1e-116">However, the property getter is also marked as obsolete to indicate to callers that they should stop accessing the property.</span></span> <span data-ttu-id="e8e1e-117">ライブラリとアプリで実行時の動作を決定するために <xref:System.Reflection.Assembly.GlobalAssemblyCache> API を使用することはできません。これは、.NET Core および .NET 5 以降のバージョンでは常に `false` が返されるためです。</span><span class="sxs-lookup"><span data-stu-id="e8e1e-117">Libraries and apps should not use the <xref:System.Reflection.Assembly.GlobalAssemblyCache> API to make determinations about run-time behavior, as it always returns `false` in .NET Core and .NET 5 and later versions.</span></span>

```csharp
Assembly asm = typeof(object).Assembly;
// Prints 'False' on .NET 5.0+; also produces warning SYSLIB0005 at compile time.
Console.WriteLine(asm.GlobalAssemblyCache);
```

<span data-ttu-id="e8e1e-118">これは、コンパイル時のみの変更です。</span><span class="sxs-lookup"><span data-stu-id="e8e1e-118">This is a compile-time only change.</span></span> <span data-ttu-id="e8e1e-119">実行時については、以前のバージョンの .NET Core からの変更はありません。</span><span class="sxs-lookup"><span data-stu-id="e8e1e-119">There is no run-time change from previous versions of .NET Core.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="e8e1e-120">変更理由</span><span class="sxs-lookup"><span data-stu-id="e8e1e-120">Reason for change</span></span>

<span data-ttu-id="e8e1e-121">.NET Core および .NET 5 以降のバージョンでは、グローバル アセンブリ キャッシュ (GAC) は概念として存在しません。</span><span class="sxs-lookup"><span data-stu-id="e8e1e-121">The global assembly cache (GAC) does not exist as a concept in .NET Core and .NET 5 and later versions.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="e8e1e-122">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="e8e1e-122">Version introduced</span></span>

<span data-ttu-id="e8e1e-123">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="e8e1e-123">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="e8e1e-124">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="e8e1e-124">Recommended action</span></span>

- <span data-ttu-id="e8e1e-125">アプリケーションによって <xref:System.Reflection.Assembly.GlobalAssemblyCache> プロパティのクエリが実行される場合は、呼び出しを削除することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="e8e1e-125">If your application queries the <xref:System.Reflection.Assembly.GlobalAssemblyCache> property, consider removing the call.</span></span> <span data-ttu-id="e8e1e-126"><xref:System.Reflection.Assembly.GlobalAssemblyCache> 値を使用して、実行時に "GAC のアセンブリ" フローと "GAC に存在しないアセンブリ" フローのどちらかを選択する場合は、フローが .NET Core または .NET 5.0 以降のアプリケーションで引き続き意味を持つかどうかを再検討してください。</span><span class="sxs-lookup"><span data-stu-id="e8e1e-126">If you use the <xref:System.Reflection.Assembly.GlobalAssemblyCache> value to choose between an "assembly in the GAC"-flow vs. an "assembly not in the GAC"-flow at run time, reconsider whether the flow still makes sense for a .NET Core or .NET 5.0+ application.</span></span>

- <span data-ttu-id="e8e1e-127">古い API を引き続き使用する必要がある場合は、コードで `SYSLIB0005` 警告を抑制することができます。</span><span class="sxs-lookup"><span data-stu-id="e8e1e-127">If you must continue to use the obsolete APIs, you can suppress the `SYSLIB0005` warning in code.</span></span>

  ```csharp
  Assembly asm = typeof(object).Assembly;
  #pragma warning disable SYSLIB0005 // Disable the warning.
  // Prints 'False' on .NET 5.0+.
  Console.WriteLine(asm.GlobalAssemblyCache);
  #pragma warning restore SYSLIB0005 // Re-enable the warning.
  ```

  <span data-ttu-id="e8e1e-128">プロジェクト ファイルで警告を抑制することもできます。これにより、プロジェクト内のすべてのソース ファイルに対して警告が無効になります。</span><span class="sxs-lookup"><span data-stu-id="e8e1e-128">You can also suppress the warning in your project file, which disables the warning for all source files in the project.</span></span>

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- NoWarn below will suppress SYSLIB0005 project-wide -->
     <NoWarn>$(NoWarn);SYSLIB0005</NoWarn>
    </PropertyGroup>
  </Project>
  ```

  <span data-ttu-id="e8e1e-129">`SYSLIB0005` を抑制すると、<xref:System.Reflection.Assembly.GlobalAssemblyCache> が旧型式であるという警告のみが無効になります。</span><span class="sxs-lookup"><span data-stu-id="e8e1e-129">Suppressing `SYSLIB0005` disables only the <xref:System.Reflection.Assembly.GlobalAssemblyCache> obsoletion warning.</span></span> <span data-ttu-id="e8e1e-130">それ以外の警告は無効になりません。</span><span class="sxs-lookup"><span data-stu-id="e8e1e-130">It does not disable any other warnings.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="e8e1e-131">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="e8e1e-131">Affected APIs</span></span>

- <xref:System.Reflection.Assembly.GlobalAssemblyCache?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Reflection.Assembly.GlobalAssemblyCache`

-->
