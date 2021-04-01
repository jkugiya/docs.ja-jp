---
title: Windows 互換機能パックを使用してコードを移植する
description: Windows 互換機能パックについて、およびそれを使用して既存の .NET Framework コードを .NET 5 および .NET Core 3.1 に移植する方法について説明します。
author: terrajobst
ms.date: 03/04/2021
ms.openlocfilehash: 655657e38f564d84ea3e56b5374debc04b405eeb
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873641"
---
# <a name="use-the-windows-compatibility-pack-to-port-code-to-net-5"></a><span data-ttu-id="201b0-103">Windows 互換機能パックを使用してコードを .NET 5+ に移植する</span><span class="sxs-lookup"><span data-stu-id="201b0-103">Use the Windows Compatibility Pack to port code to .NET 5+</span></span>

<span data-ttu-id="201b0-104">既存のコードを .NET Framework から .NET に移植するときに発生する最も一般的な問題の一部として、.NET Framework のみに存在する API およびテクノロジへの依存があります。</span><span class="sxs-lookup"><span data-stu-id="201b0-104">Some of the most common issues found when porting existing code from .NET Framework to .NET are dependencies on APIs and technologies that are only found in .NET Framework.</span></span> <span data-ttu-id="201b0-105">"*Windows 互換機能パック*" には、このようなテクノロジの多くが用意されているので、.NET アプリケーションと .NET Standard ライブラリをはるかに簡単に構築できます。</span><span class="sxs-lookup"><span data-stu-id="201b0-105">The *Windows Compatibility Pack* provides many of these technologies, so it's much easier to build .NET applications and .NET Standard libraries.</span></span>

<span data-ttu-id="201b0-106">互換性パックは論理的な [.NET Standard 2.0 の拡張機能](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support)であり、API セットが大幅に増加します。</span><span class="sxs-lookup"><span data-stu-id="201b0-106">The compatibility pack is a logical [extension of .NET Standard 2.0](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) that significantly increases the API set.</span></span> <span data-ttu-id="201b0-107">既存のコードは、ほとんど変更されずにコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="201b0-107">Existing code compiles with almost no modifications.</span></span> <span data-ttu-id="201b0-108">"あらゆる .NET 実装で提供される API のセット" でその約束を守るために、レジストリ、Windows Management Instrumentation (WMI)、リフレクション出力 API など、すべてのプラットフォームで動作しないテクノロジは .NET Standard には含まれていません。</span><span class="sxs-lookup"><span data-stu-id="201b0-108">To keep its promise of "the set of APIs that all .NET implementations provide", .NET Standard doesn't include technologies that can't work across all platforms, such as registry, Windows Management Instrumentation (WMI), or reflection emit APIs.</span></span> <span data-ttu-id="201b0-109">Windows 互換機能パックは .NET Standard を基盤とし、これらの Windows 専用のテクノロジにアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="201b0-109">The Windows Compatibility Pack sits on top of .NET Standard and provides access to these Windows-only technologies.</span></span> <span data-ttu-id="201b0-110">.NET に移行したいが、少なくとも最初の手順で Windows に留まることを計画している顧客にとって特に便利です。</span><span class="sxs-lookup"><span data-stu-id="201b0-110">It's especially useful for customers that want to move to .NET but plan to stay on Windows, at least as a first step.</span></span> <span data-ttu-id="201b0-111">このシナリオでは、Windows 専用のテクノロジを使用して、移行の障害を取り除くことができます。</span><span class="sxs-lookup"><span data-stu-id="201b0-111">In that scenario, you can use Windows-only technologies removes the migration hurdle.</span></span>

## <a name="package-contents"></a><span data-ttu-id="201b0-112">パッケージの内容</span><span class="sxs-lookup"><span data-stu-id="201b0-112">Package contents</span></span>

<span data-ttu-id="201b0-113">Windows 互換機能パックは、[Microsoft.Windows.Compatibility NuGet パッケージ](https://www.nuget.org/packages/Microsoft.Windows.Compatibility)経由で提供され、.NET または .NET Standard をターゲットとするプロジェクトから参照できます。</span><span class="sxs-lookup"><span data-stu-id="201b0-113">The Windows Compatibility Pack is provided via the [Microsoft.Windows.Compatibility NuGet package](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) and can be referenced from projects that target .NET or .NET Standard.</span></span>

<span data-ttu-id="201b0-114">Windows 専用 API やプラットフォーム非依存 API など、約 20,000 の API を提供します。テクノロジ領域には次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="201b0-114">It provides about 20,000 APIs, including Windows-only and cross-platform APIs from the following technology areas:</span></span>

- <span data-ttu-id="201b0-115">コード ページ</span><span class="sxs-lookup"><span data-stu-id="201b0-115">Code Pages</span></span>
- <span data-ttu-id="201b0-116">CodeDom</span><span class="sxs-lookup"><span data-stu-id="201b0-116">CodeDom</span></span>
- <span data-ttu-id="201b0-117">構成</span><span class="sxs-lookup"><span data-stu-id="201b0-117">Configuration</span></span>
- <span data-ttu-id="201b0-118">ディレクトリ サービス</span><span class="sxs-lookup"><span data-stu-id="201b0-118">Directory Services</span></span>
- <span data-ttu-id="201b0-119">描画</span><span class="sxs-lookup"><span data-stu-id="201b0-119">Drawing</span></span>
- <span data-ttu-id="201b0-120">ODBC</span><span class="sxs-lookup"><span data-stu-id="201b0-120">ODBC</span></span>
- <span data-ttu-id="201b0-121">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="201b0-121">Permissions</span></span>
- <span data-ttu-id="201b0-122">Port</span><span class="sxs-lookup"><span data-stu-id="201b0-122">Ports</span></span>
- <span data-ttu-id="201b0-123">Windows アクセス制御リスト (ACL)</span><span class="sxs-lookup"><span data-stu-id="201b0-123">Windows Access Control Lists (ACL)</span></span>
- <span data-ttu-id="201b0-124">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="201b0-124">Windows Communication Foundation (WCF)</span></span>
- <span data-ttu-id="201b0-125">Windows 暗号化</span><span class="sxs-lookup"><span data-stu-id="201b0-125">Windows Cryptography</span></span>
- <span data-ttu-id="201b0-126">Windows EventLog</span><span class="sxs-lookup"><span data-stu-id="201b0-126">Windows EventLog</span></span>
- <span data-ttu-id="201b0-127">Windows Management Instrumentation (WMI)</span><span class="sxs-lookup"><span data-stu-id="201b0-127">Windows Management Instrumentation (WMI)</span></span>
- <span data-ttu-id="201b0-128">Windows パフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="201b0-128">Windows Performance Counters</span></span>
- <span data-ttu-id="201b0-129">Windows レジストリ</span><span class="sxs-lookup"><span data-stu-id="201b0-129">Windows Registry</span></span>
- <span data-ttu-id="201b0-130">Windows ランタイム キャッシュ</span><span class="sxs-lookup"><span data-stu-id="201b0-130">Windows Runtime Caching</span></span>
- <span data-ttu-id="201b0-131">Windows サービス</span><span class="sxs-lookup"><span data-stu-id="201b0-131">Windows Services</span></span>

<span data-ttu-id="201b0-132">詳細については、[互換機能パックの仕様](https://github.com/dotnet/designs/blob/main/accepted/2018/compat-pack/compat-pack.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="201b0-132">For more information, see the [specification of the compatibility pack](https://github.com/dotnet/designs/blob/main/accepted/2018/compat-pack/compat-pack.md).</span></span>

## <a name="get-started"></a><span data-ttu-id="201b0-133">はじめに</span><span class="sxs-lookup"><span data-stu-id="201b0-133">Get started</span></span>

1. <span data-ttu-id="201b0-134">移植の前に、[移植プロセス](index.md)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="201b0-134">Before porting, make sure to take a look at the [Porting process](index.md).</span></span>

2. <span data-ttu-id="201b0-135">.NET または .NET Standard に既存のコードを移植するときに、[Microsoft.Windows.Compatibility NuGet パッケージ](https://www.nuget.org/packages/Microsoft.Windows.Compatibility)をインストールします。</span><span class="sxs-lookup"><span data-stu-id="201b0-135">When porting existing code to .NET or .NET Standard, install the [Microsoft.Windows.Compatibility NuGet package](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span>

   <span data-ttu-id="201b0-136">Windows に留まる場合、すでに用意はできています。</span><span class="sxs-lookup"><span data-stu-id="201b0-136">If you want to stay on Windows, you're all set.</span></span>

3. <span data-ttu-id="201b0-137">.NET アプリケーションまたは .NET Standard ライブラリを Linux または macOS で実行する場合、[API Analyzer](../../standard/analyzers/api-analyzer.md) を使用して、クロスプラットフォームで機能しない API の使用方法を見つけます。</span><span class="sxs-lookup"><span data-stu-id="201b0-137">If you want to run the .NET application or .NET Standard library on Linux or macOS, use the [API Analyzer](../../standard/analyzers/api-analyzer.md) to find usage of APIs that won't work cross-platform.</span></span>

4. <span data-ttu-id="201b0-138">そのような API の使用を取り除くか、プラットフォーム非依存の代替で置換するか、プラットフォーム チェックで保護します (以下参照)。</span><span class="sxs-lookup"><span data-stu-id="201b0-138">Either remove the usages of those APIs, replace them with cross-platform alternatives, or guard them using a platform check, like:</span></span>

    ```csharp
    private static string GetLoggingPath()
    {
        // Verify the code is running on Windows.
        if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
        {
            using (var key = Registry.CurrentUser.OpenSubKey(@"Software\Fabrikam\AssetManagement"))
            {
                if (key?.GetValue("LoggingDirectoryPath") is string configuredPath)
                    return configuredPath;
            }
        }

        // This is either not running on Windows or no logging path was configured,
        // so just use the path for non-roaming user-specific data files.
        var appDataPath = Environment.GetFolderPath(Environment.SpecialFolder.LocalApplicationData);
        return Path.Combine(appDataPath, "Fabrikam", "AssetManagement", "Logging");
    }
    ```

<span data-ttu-id="201b0-139">デモについては、[Windows 互換機能パックの Channel 9 動画](https://channel9.msdn.com/Events/Connect/2017/T123)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="201b0-139">For a demo, check out the [Channel 9 video of the Windows Compatibility Pack](https://channel9.msdn.com/Events/Connect/2017/T123).</span></span>

## <a name="see-also"></a><span data-ttu-id="201b0-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="201b0-140">See also</span></span>

- [<span data-ttu-id="201b0-141">.NET Framework から .NET への移植の概要</span><span class="sxs-lookup"><span data-stu-id="201b0-141">Overview of porting from .NET Framework to .NET</span></span>](index.md)
- [<span data-ttu-id="201b0-142">ASP.NET から ASP.NET Core への移行</span><span class="sxs-lookup"><span data-stu-id="201b0-142">ASP.NET to ASP.NET Core migration</span></span>](/aspnet/core/migration/proper-to-2x)
- [<span data-ttu-id="201b0-143">.NET Framework WPF アプリを .NET に移行する</span><span class="sxs-lookup"><span data-stu-id="201b0-143">Migrate .NET Framework WPF apps to .NET</span></span>](/dotnet/desktop/wpf/migration/convert-project-from-net-framework?view=netdesktop-5.0&preserve-view=true)
- [<span data-ttu-id="201b0-144">.NET Framework Windows フォーム アプリを .NET に移行する</span><span class="sxs-lookup"><span data-stu-id="201b0-144">Migrate .NET Framework Windows Forms apps to .NET</span></span>](/dotnet/desktop/winforms/migration/?view=netdesktop-5.0&preserve-view=true)
- [<span data-ttu-id="201b0-145">.NET Framework ライブラリを .NET に移植する</span><span class="sxs-lookup"><span data-stu-id="201b0-145">Port .NET Framework libraries to .NET</span></span>](libraries.md)
