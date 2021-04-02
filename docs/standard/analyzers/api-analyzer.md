---
title: .NET API アナライザー
description: 非推奨の API およびプラットフォームの互換性の問題を検出するのに .NET API アナライザーがどのように役立つかについて説明します。
author: oliag
ms.date: 02/20/2020
ms.openlocfilehash: 9eef1908fd6be90d31e6e26cbab65e55a26ce228
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636910"
---
# <a name="net-api-analyzer"></a><span data-ttu-id="0c306-103">.NET API アナライザー</span><span class="sxs-lookup"><span data-stu-id="0c306-103">.NET API analyzer</span></span>

<span data-ttu-id="0c306-104">.NET API アナライザーは、さまざまなプラットフォームでの C# API の互換性リスクの可能性および非推奨の API の呼び出しを検出する Roslyn アナライザーです。</span><span class="sxs-lookup"><span data-stu-id="0c306-104">The .NET API Analyzer is a Roslyn analyzer that discovers potential compatibility risks for C# APIs on different platforms and detects calls to deprecated APIs.</span></span> <span data-ttu-id="0c306-105">開発のすべての段階ですべての C# 開発者に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="0c306-105">It can be useful for all C# developers at any stage of development.</span></span>

<span data-ttu-id="0c306-106">API アナライザーは、NuGet パッケージ [Microsoft.DotNet.Analyzers.Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/) として提供されています。</span><span class="sxs-lookup"><span data-stu-id="0c306-106">API Analyzer comes as a NuGet package [Microsoft.DotNet.Analyzers.Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/).</span></span> <span data-ttu-id="0c306-107">プロジェクトでこれを参照すると、コードが自動的に監視されて、問題のある API 使用が示されます。</span><span class="sxs-lookup"><span data-stu-id="0c306-107">After you reference it in a project, it automatically monitors the code and indicates problematic API usage.</span></span> <span data-ttu-id="0c306-108">また、電球アイコンをクリックすると、考えられる修正方法の提案を得ることもできます。</span><span class="sxs-lookup"><span data-stu-id="0c306-108">You can also get suggestions on possible fixes by clicking on the light bulb.</span></span> <span data-ttu-id="0c306-109">ドロップダウン メニューには、警告を抑制するオプションが含まれます。</span><span class="sxs-lookup"><span data-stu-id="0c306-109">The drop-down menu includes an option to suppress the warnings.</span></span>

> [!NOTE]
> <span data-ttu-id="0c306-110">.NET API アナライザーは、まだプレリリース バージョンです。</span><span class="sxs-lookup"><span data-stu-id="0c306-110">The .NET API analyzer is still a pre-release version.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0c306-111">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="0c306-111">Prerequisites</span></span>

- <span data-ttu-id="0c306-112">Visual Studio 2017 以降のバージョン、または Visual Studio for Mac (すべてのバージョン)。</span><span class="sxs-lookup"><span data-stu-id="0c306-112">Visual Studio 2017 and later versions, or Visual Studio for Mac (all versions).</span></span>

## <a name="discover-deprecated-apis"></a><span data-ttu-id="0c306-113">非推奨の API を検出する</span><span class="sxs-lookup"><span data-stu-id="0c306-113">Discover deprecated APIs</span></span>

### <a name="what-are-deprecated-apis"></a><span data-ttu-id="0c306-114">非推奨の API とは</span><span class="sxs-lookup"><span data-stu-id="0c306-114">What are deprecated APIs?</span></span>

<span data-ttu-id="0c306-115">.NET ファミリは大規模な製品のセットであり、より適切に顧客のニーズに対応するため頻繁にアップグレードされています。</span><span class="sxs-lookup"><span data-stu-id="0c306-115">The .NET family is a set of large products that are constantly upgraded to better serve customer needs.</span></span> <span data-ttu-id="0c306-116">当然、API が廃止されたり新しいものに置き換えられたりすることがあります。</span><span class="sxs-lookup"><span data-stu-id="0c306-116">It's natural to deprecate some APIs and replace them with new ones.</span></span> <span data-ttu-id="0c306-117">より優れた代替 API が存在する API は、非推奨と見なされます。</span><span class="sxs-lookup"><span data-stu-id="0c306-117">An API is considered deprecated when a better alternative exists.</span></span> <span data-ttu-id="0c306-118">API が非推奨であり使ってはならないことを通知する手段の 1 つは、<xref:System.ObsoleteAttribute> 属性で API をマークすることです。</span><span class="sxs-lookup"><span data-stu-id="0c306-118">One way to inform that an API is deprecated and shouldn't be used is to mark it with the <xref:System.ObsoleteAttribute> attribute.</span></span> <span data-ttu-id="0c306-119">この方法の欠点は、すべての非推奨 API に対して診断 ID が 1 つしかないことです (C# の場合、[CS0612](../../csharp/misc/cs0612.md))。</span><span class="sxs-lookup"><span data-stu-id="0c306-119">The disadvantage of this approach is that there is only one diagnostic ID for all obsolete APIs (for C#, [CS0612](../../csharp/misc/cs0612.md)).</span></span> <span data-ttu-id="0c306-120">これによって、次のことが起こります。</span><span class="sxs-lookup"><span data-stu-id="0c306-120">This means that:</span></span>

- <span data-ttu-id="0c306-121">ケースごとに専用のドキュメントを作成できません。</span><span class="sxs-lookup"><span data-stu-id="0c306-121">It's impossible to have dedicated documents for each case.</span></span>
- <span data-ttu-id="0c306-122">特定のカテゴリの警告を抑制できません。</span><span class="sxs-lookup"><span data-stu-id="0c306-122">It's impossible to suppress certain category of warnings.</span></span> <span data-ttu-id="0c306-123">すべてを抑制するか、まったく抑制しないかです。</span><span class="sxs-lookup"><span data-stu-id="0c306-123">You can suppress either all or none of them.</span></span>
- <span data-ttu-id="0c306-124">新しい非推奨 API をユーザーに通知するには、参照されているアセンブリまたは対象のパッケージを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0c306-124">To inform users of a new deprecation, a referenced assembly or targeting package has to be updated.</span></span>

<span data-ttu-id="0c306-125">API アナライザーは、DE (Deprecation Error の略) で始まる API 固有のエラー コードを使うので、個々の警告の表示を制御できます。</span><span class="sxs-lookup"><span data-stu-id="0c306-125">The API Analyzer uses API-specific error codes that begin with DE (which stands for Deprecation Error), which allows control over the display of individual warnings.</span></span> <span data-ttu-id="0c306-126">アナライザーによって識別された非推奨の API は、[dotnet/platform-compat](https://github.com/dotnet/platform-compat) リポジトリで定義されています。</span><span class="sxs-lookup"><span data-stu-id="0c306-126">The deprecated APIs identified by the analyzer are defined in the [dotnet/platform-compat](https://github.com/dotnet/platform-compat) repo.</span></span>

### <a name="add-the-api-analyzer-to-your-project"></a><span data-ttu-id="0c306-127">API アナライザーをプロジェクトに追加する</span><span class="sxs-lookup"><span data-stu-id="0c306-127">Add the API Analyzer to your project</span></span>

1. <span data-ttu-id="0c306-128">Visual Studio を開きます。</span><span class="sxs-lookup"><span data-stu-id="0c306-128">Open Visual Studio.</span></span>
2. <span data-ttu-id="0c306-129">アナライザーを実行するプロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="0c306-129">Open the project you want to run the analyzer on.</span></span>
3. <span data-ttu-id="0c306-130">**ソリューション エクスプローラー** で、プロジェクトを右クリックし、 **[NuGet パッケージの管理]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0c306-130">In **Solution Explorer**, right-click on your project and choose **Manage NuGet Packages**.</span></span> <span data-ttu-id="0c306-131">(このオプションは、 **[プロジェクト]** メニューからも使用できます。)</span><span class="sxs-lookup"><span data-stu-id="0c306-131">(This option is also available from the **Project** menu.)</span></span>
4. <span data-ttu-id="0c306-132">[NuGet パッケージ マネージャー] タブ上で、次を実行します。</span><span class="sxs-lookup"><span data-stu-id="0c306-132">On the NuGet Package Manager tab:</span></span>
   1. <span data-ttu-id="0c306-133">[パッケージ ソース] として [nuget.org] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0c306-133">Select "nuget.org" as the Package source.</span></span>
   2. <span data-ttu-id="0c306-134">**[参照]** タブに移動します。</span><span class="sxs-lookup"><span data-stu-id="0c306-134">Go to the **Browse** tab.</span></span>
   3. <span data-ttu-id="0c306-135">**[プレリリースを含める]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0c306-135">Select **Include prerelease**.</span></span>
   4. <span data-ttu-id="0c306-136">**[Microsoft.DotNet.Analyzers.Compatibility]** を検索します。</span><span class="sxs-lookup"><span data-stu-id="0c306-136">Search for **Microsoft.DotNet.Analyzers.Compatibility**.</span></span>
   5. <span data-ttu-id="0c306-137">一覧にある該当のパッケージを選択します。</span><span class="sxs-lookup"><span data-stu-id="0c306-137">Select that package in the list.</span></span>
   6. <span data-ttu-id="0c306-138">**[インストール]** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="0c306-138">Select the **Install** button.</span></span>
   7. <span data-ttu-id="0c306-139">**[変更のプレビュー]** ダイアログの **[OK]** を選択します。表示されているパッケージのライセンス条項に同意する場合は、**[ライセンスの同意]** ダイアログの **[同意する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0c306-139">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="use-the-api-analyzer"></a><span data-ttu-id="0c306-140">API アナライザーを使用する</span><span class="sxs-lookup"><span data-stu-id="0c306-140">Use the API Analyzer</span></span>

<span data-ttu-id="0c306-141">非推奨の API (<xref:System.Net.WebClient> など) がコードで使われていると、API アナライザーは緑の波線でそれを強調します。</span><span class="sxs-lookup"><span data-stu-id="0c306-141">When a deprecated API, such as <xref:System.Net.WebClient>, is used in a code, API Analyzer highlights it with a green squiggly line.</span></span> <span data-ttu-id="0c306-142">API 呼び出しをポイントすると、次の例のように、電球アイコンと API の非推奨に関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0c306-142">When you hover over the API call, a light bulb is displayed with information about the API deprecation, as in the following example:</span></span>

![緑の波線が表示された WebClient API と左側の電球アイコンのスクリーンショット。](media/api-analyzer/green-squiggle.jpg)

<span data-ttu-id="0c306-144">**[エラー一覧]** ウィンドウには、非推奨の API ごとに一意の ID を含む警告が表示されます。次に示すのは `DE004` の例です。</span><span class="sxs-lookup"><span data-stu-id="0c306-144">The **Error List** window contains warnings with a unique ID per deprecated API, as shown in the following example (`DE004`):</span></span>

<span data-ttu-id="0c306-145">![警告の ID と説明が表示されている [エラー一覧] ウィンドウのスクリーンショット。](media/api-analyzer/warnings-id-and-descriptions.jpg "警告を含むエラー一覧ウィンドウ。")</span><span class="sxs-lookup"><span data-stu-id="0c306-145">![Screenshot of the Error List window showing warning's ID and description.](media/api-analyzer/warnings-id-and-descriptions.jpg "Error List window that includes warnings.")</span></span>

<span data-ttu-id="0c306-146">ID をクリックすると、API が非推奨になった理由に関する詳細情報と、使用できる代替 API に関する提案が表示される Web ページに移動します。</span><span class="sxs-lookup"><span data-stu-id="0c306-146">By clicking on the ID, you go to a webpage with detailed information about why the API was deprecated and suggestions regarding alternative APIs that can be used.</span></span>

<span data-ttu-id="0c306-147">強調表示されたメンバーを右クリックして **[\<diagnostic ID> の非表示]** を選ぶと、警告を抑制できます。</span><span class="sxs-lookup"><span data-stu-id="0c306-147">Any warnings can be suppressed by right-clicking on the highlighted member and selecting **Suppress \<diagnostic ID>**.</span></span> <span data-ttu-id="0c306-148">警告を抑制するには 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="0c306-148">There are two ways to suppress warnings:</span></span>

- [<span data-ttu-id="0c306-149">ローカル (ソース内)</span><span class="sxs-lookup"><span data-stu-id="0c306-149">locally (in source)</span></span>](#suppress-warnings-locally)
- <span data-ttu-id="0c306-150">[グローバル (抑制ファイル内)](#suppress-warnings-globally) - 推奨</span><span class="sxs-lookup"><span data-stu-id="0c306-150">[globally (in a suppression file)](#suppress-warnings-globally) - recommended</span></span>

### <a name="suppress-warnings-locally"></a><span data-ttu-id="0c306-151">警告をローカルに抑制する</span><span class="sxs-lookup"><span data-stu-id="0c306-151">Suppress warnings locally</span></span>

<span data-ttu-id="0c306-152">警告をローカルに抑制するには、警告を抑制するメンバーを右クリックして、 **[クイック アクションとリファクタリング]**  >  **[*診断 ID*\<diagnostic ID> の非表示]**  >  **[ソース内]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="0c306-152">To suppress warnings locally, right-click on the member you want to suppress warnings for and then select **Quick Actions and Refactorings** > **Suppress *diagnostic ID*\<diagnostic ID>** > **in Source**.</span></span> <span data-ttu-id="0c306-153">[#pragma](../../csharp/language-reference/preprocessor-directives.md#pragma-warning) 警告プリプロセッサ ディレクティブが、定義されているスコープ内のソース コードに追加されます。![#pragma warning disable が枠で囲まれたコードのスクリーンショット。](media/api-analyzer/suppress-in-source.jpg)</span><span class="sxs-lookup"><span data-stu-id="0c306-153">The [#pragma](../../csharp/language-reference/preprocessor-directives.md#pragma-warning) warning preprocessor directive is added to your source code in the scope defined: ![Screenshot of code framed with #pragma warning disable.](media/api-analyzer/suppress-in-source.jpg)</span></span>

### <a name="suppress-warnings-globally"></a><span data-ttu-id="0c306-154">警告をグローバルに抑制する</span><span class="sxs-lookup"><span data-stu-id="0c306-154">Suppress warnings globally</span></span>

<span data-ttu-id="0c306-155">警告をグローバルに抑制するには、警告を抑制するメンバーを右クリックして、 **[クイック アクションとリファクタリング]**  >  **[*診断 ID*\<diagnostic ID> の非表示]**  >  **[抑制ファイル内]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="0c306-155">To suppress warnings globally, right-click on the member you want to suppress warnings for and then select **Quick Actions and Refactorings** > **Suppress *diagnostic ID*\<diagnostic ID>** > **in Suppression File**.</span></span>

![Visual Studio の警告を抑制するオプションを示す右クリック メニューのスクリーンショット。](media/api-analyzer/suppress-in-sup-file.jpg)

<span data-ttu-id="0c306-157">最初の抑制後に、*GlobalSuppressions.cs* ファイルがプロジェクトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="0c306-157">A *GlobalSuppressions.cs* file is added to your project after the first suppression.</span></span> <span data-ttu-id="0c306-158">新しいグローバル抑制は、このファイルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="0c306-158">New global suppressions are appended to this file.</span></span>

![ソリューション エクスプローラーの GlobalSuppressions.cs ファイルのスクリーンショット。](media/api-analyzer/suppression-file.jpg)

<span data-ttu-id="0c306-160">グローバル抑制は、プロジェクト間で API 使用の一貫性を確保するのに推奨される方法です。</span><span class="sxs-lookup"><span data-stu-id="0c306-160">Global suppression is the recommended way to ensure consistency of API usage across projects.</span></span>

## <a name="discover-cross-platform-issues"></a><span data-ttu-id="0c306-161">クロスプラットフォームの問題を検出する</span><span class="sxs-lookup"><span data-stu-id="0c306-161">Discover cross-platform issues</span></span>

> [!NOTE]
> <span data-ttu-id="0c306-162">.NET 5.0 では、この機能の置き換えとして[プラットフォーム互換性アナライザー](platform-compat-analyzer.md)が導入されます。</span><span class="sxs-lookup"><span data-stu-id="0c306-162">.NET 5.0 introduces the [Platform compatibility analyzer](platform-compat-analyzer.md) as a replacement of this feature.</span></span> <span data-ttu-id="0c306-163">プラットフォーム互換性アナライザーは .NET SDK に含まれており (個別にインストールする必要はありません)、既定で有効です。</span><span class="sxs-lookup"><span data-stu-id="0c306-163">The platform compatibility analyzer is included in the .NET SDK (no need to install it separately) and is on by default.</span></span>

<span data-ttu-id="0c306-164">非推奨の API と同様に、アナライザーはクロスプラットフォームではないすべての API を識別します。</span><span class="sxs-lookup"><span data-stu-id="0c306-164">Similar to deprecated APIs, the analyzer identifies all APIs that are not cross-platform.</span></span> <span data-ttu-id="0c306-165">たとえば、<xref:System.Console.WindowWidth?displayProperty=nameWithType> は Windows では動作しますが、Linux や macOS では動作しません。</span><span class="sxs-lookup"><span data-stu-id="0c306-165">For example, <xref:System.Console.WindowWidth?displayProperty=nameWithType> works on Windows but not on Linux and macOS.</span></span> <span data-ttu-id="0c306-166">診断 ID は、 **[エラー一覧]** ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="0c306-166">The diagnostic ID is shown in the **Error List** window.</span></span> <span data-ttu-id="0c306-167">右クリックして **[クイック アクションとリファクタリング]** を選ぶことで、その警告を抑制することができます。</span><span class="sxs-lookup"><span data-stu-id="0c306-167">You can suppress that warning by right-clicking and selecting **Quick Actions and Refactorings**.</span></span> <span data-ttu-id="0c306-168">2 つのオプション (非推奨のメンバーを使い続けて警告を抑制するか、まったく使わない) がある非推奨の場合とは異なり、特定のプラットフォーム用にのみコードを開発している場合は、コードを実行する予定のない他のすべてのプラットフォームですべての警告を抑制できます。</span><span class="sxs-lookup"><span data-stu-id="0c306-168">Unlike deprecation cases where you have two options (either keep using the deprecated member and suppress warnings or not use it at all), here if you're developing your code only for certain platforms, you can suppress all warnings for all other platforms you don't plan to run your code on.</span></span> <span data-ttu-id="0c306-169">そのために必要なことは、プロジェクト ファイルを編集し、無視するすべてのプラットフォームを列記した `PlatformCompatIgnore` プロパティを追加するだけです。</span><span class="sxs-lookup"><span data-stu-id="0c306-169">To do so, you just need to edit your project file and add the `PlatformCompatIgnore` property that lists all platforms to be ignored.</span></span> <span data-ttu-id="0c306-170">指定できる値は、`Linux`、`macOS`、`Windows` です。</span><span class="sxs-lookup"><span data-stu-id="0c306-170">The accepted values are: `Linux`, `macOS`, and `Windows`.</span></span>

```xml
<PropertyGroup>
    <PlatformCompatIgnore>Linux;macOS</PlatformCompatIgnore>
</PropertyGroup>
```

<span data-ttu-id="0c306-171">コードが複数のプラットフォームを対象にしていて、一部のプラットフォームでサポートされていない API を利用したい場合は、`if` ステートメントを使ってコードのその部分を保護できます。</span><span class="sxs-lookup"><span data-stu-id="0c306-171">If your code targets multiple platforms and you want to take advantage of an API not supported on some of them, you can guard that part of the code with an `if` statement:</span></span>

```csharp
if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
{
     var w = Console.WindowWidth;
     // More code
}
```

<span data-ttu-id="0c306-172">また、対象のフレームワーク/オペレーティング システムごとに条件付きでコンパイルすることもできますが、現在は[手動で](../frameworks.md#how-to-specify-a-target-framework)行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="0c306-172">You can also conditionally compile per target framework/operating system, but you currently need to do that [manually](../frameworks.md#how-to-specify-a-target-framework).</span></span>

## <a name="supported-diagnostics"></a><span data-ttu-id="0c306-173">サポートされている診断</span><span class="sxs-lookup"><span data-stu-id="0c306-173">Supported diagnostics</span></span>

<span data-ttu-id="0c306-174">現時点では、アナライザーは次のケースを処理します。</span><span class="sxs-lookup"><span data-stu-id="0c306-174">Currently, the analyzer handles the following cases:</span></span>

- <span data-ttu-id="0c306-175"><xref:System.PlatformNotSupportedException> (PC001) をスローする .NET Standard API の使用。</span><span class="sxs-lookup"><span data-stu-id="0c306-175">Usage of a .NET Standard API that throws <xref:System.PlatformNotSupportedException> (PC001).</span></span>
- <span data-ttu-id="0c306-176">.NET Framework 4.6.1 (PC002) では利用できない .NET Standard API の使用。</span><span class="sxs-lookup"><span data-stu-id="0c306-176">Usage of a .NET Standard API that isn't available on the .NET Framework 4.6.1 (PC002).</span></span>
- <span data-ttu-id="0c306-177">UWP (PC003) に存在しないネイティブ API の使用。</span><span class="sxs-lookup"><span data-stu-id="0c306-177">Usage of a native API that doesn't exist in UWP (PC003).</span></span>
- <span data-ttu-id="0c306-178">Delegate.BeginInvoke および EndInvoke API (PC004) の使用。</span><span class="sxs-lookup"><span data-stu-id="0c306-178">Usage of Delegate.BeginInvoke and EndInvoke APIs (PC004).</span></span>
- <span data-ttu-id="0c306-179">非推奨 (DEXXXX) としてマークされている API の使用。</span><span class="sxs-lookup"><span data-stu-id="0c306-179">Usage of an API that is marked as deprecated (DEXXXX).</span></span>

## <a name="ci-machine"></a><span data-ttu-id="0c306-180">CI マシン</span><span class="sxs-lookup"><span data-stu-id="0c306-180">CI machine</span></span>

<span data-ttu-id="0c306-181">これらの診断はすべて、IDE で利用できるだけでなく、プロジェクトのビルドの一部としてコマンド ラインでも利用でき、これには CI サーバーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="0c306-181">All these diagnostics are available not only in the IDE, but also on the command line as part of building your project, which includes the CI server.</span></span>

## <a name="configuration"></a><span data-ttu-id="0c306-182">構成</span><span class="sxs-lookup"><span data-stu-id="0c306-182">Configuration</span></span>

<span data-ttu-id="0c306-183">ユーザーは、診断の処理方法を決定します (警告、エラー、提案、オフ)。</span><span class="sxs-lookup"><span data-stu-id="0c306-183">The user decides how the diagnostics should be treated: as warnings, errors, suggestions, or to be turned off.</span></span> <span data-ttu-id="0c306-184">たとえば、設計者は、互換性の問題をエラーとして扱い、一部の非推奨の API の呼び出しでは警告を生成し、それ以外については提案を生成するだけにする、といったことを決定できます。</span><span class="sxs-lookup"><span data-stu-id="0c306-184">For example, as an architect, you can decide that compatibility issues should be treated as errors, calls to some deprecated APIs generate warnings, while others only generate suggestions.</span></span> <span data-ttu-id="0c306-185">これを、診断 ID 別およびプロジェクト別に構成できます。</span><span class="sxs-lookup"><span data-stu-id="0c306-185">You can configure this separately by diagnostic ID and by project.</span></span> <span data-ttu-id="0c306-186">そのためには、**ソリューション エクスプローラー** で、プロジェクトの **[依存関係]** ノードに移動します。</span><span class="sxs-lookup"><span data-stu-id="0c306-186">To do so in **Solution Explorer**, navigate to the **Dependencies** node under your project.</span></span> <span data-ttu-id="0c306-187">ノード **[依存関係]**  >  **[アナライザー]**  >  **[Microsoft.DotNet.Analyzers.Compatibility]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="0c306-187">Expand the nodes **Dependencies** > **Analyzers** > **Microsoft.DotNet.Analyzers.Compatibility**.</span></span> <span data-ttu-id="0c306-188">診断 ID を右クリックし、 **[ルール セットの重要度を設定]** を選んで、目的のオプションを選びます。</span><span class="sxs-lookup"><span data-stu-id="0c306-188">Right-click on the diagnostic ID, select **Set Rule Set Severity**, and then pick the desired option.</span></span>

![診断とルール セットの重要度のポップアップ ダイアログが表示されているソリューション エクスプローラーのスクリーンショット。](media/api-analyzer/disable-notifications.jpg)

## <a name="see-also"></a><span data-ttu-id="0c306-190">関連項目</span><span class="sxs-lookup"><span data-stu-id="0c306-190">See also</span></span>

- <span data-ttu-id="0c306-191">「[Introducing API Analyzer](https://devblogs.microsoft.com/dotnet/introducing-api-analyzer/)」(API アナライザーの概要) のブログ投稿。</span><span class="sxs-lookup"><span data-stu-id="0c306-191">[Introducing API Analyzer](https://devblogs.microsoft.com/dotnet/introducing-api-analyzer/) blog post.</span></span>
- <span data-ttu-id="0c306-192">YouTube の「[API Analyzer](https://youtu.be/eeBEahYXGd0)」(API アナライザー) デモ ビデオ。</span><span class="sxs-lookup"><span data-stu-id="0c306-192">[API Analyzer](https://youtu.be/eeBEahYXGd0) demo video on YouTube.</span></span>
- [<span data-ttu-id="0c306-193">プラットフォーム互換性アナライザー</span><span class="sxs-lookup"><span data-stu-id="0c306-193">Platform Compatibility Analyzer</span></span>](platform-compat-analyzer.md)
