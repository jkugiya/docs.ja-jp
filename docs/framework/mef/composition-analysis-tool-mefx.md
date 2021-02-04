---
title: コンポジション分析ツール (Mefx)
description: .NET に Managed Extensibility Framework (MEF) パーツを含んでいる DLL ファイルと EXE ファイルを分析するコンポジション分析ツール (Mefx) について説明します。
ms.date: 03/30/2017
helpviewer_keywords:
- Composition Analysis Tool [MEF]
- MEF, Composition Analysis Tool
- Mefx [MEF], Composition Analysis Tool
ms.assetid: c48a7f93-83bb-4a06-aea0-d8e7bd1502ad
ms.openlocfilehash: a7c76bfe169a23322a5a0cdfe0d2e2e5d82f0346
ms.sourcegitcommit: 7e42488c2f8f63f6d499b5f8fb1dec5bac9ad254
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/28/2021
ms.locfileid: "98957879"
---
# <a name="composition-analysis-tool-mefx"></a><span data-ttu-id="ac021-103">コンポジション分析ツール (Mefx)</span><span class="sxs-lookup"><span data-stu-id="ac021-103">Composition Analysis Tool (Mefx)</span></span>

<span data-ttu-id="ac021-104">合成分析ツール (Mefx) は、Managed Extensibility Framework (MEF) のパートが含まれたライブラリ (.dll) ファイルとアプリケーション (.exe) ファイルを分析するコマンド ライン アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="ac021-104">The Composition Analysis Tool (Mefx) is a command-line application that analyzes library (.dll) and application (.exe) files containing Managed Extensibility Framework (MEF) parts.</span></span> <span data-ttu-id="ac021-105">Mefx の主な目的は、開発者が煩雑なトレース コードをアプリケーション自体に追加することなく、MEF アプリケーションの合成エラーを診断できるようにすることです。</span><span class="sxs-lookup"><span data-stu-id="ac021-105">The primary purpose of Mefx is to provide developers a way to diagnose composition failures in their MEF applications without the requirement to add cumbersome tracing code to the application itself.</span></span> <span data-ttu-id="ac021-106">また、Mefx は、サード パーティが提供するライブラリのパートについて理解する際にも役立ちます</span><span class="sxs-lookup"><span data-stu-id="ac021-106">It can also be useful to help understand parts from a library provided by a third party.</span></span> <span data-ttu-id="ac021-107">ここでは、Mefx の使用方法について説明し、構文のリファレンスを示します。</span><span class="sxs-lookup"><span data-stu-id="ac021-107">This topic describes how to use Mefx and provides a reference for its syntax.</span></span>  
  
<a name="getting_mefx"></a>

## <a name="getting-mefx"></a><span data-ttu-id="ac021-108">Mefx の入手</span><span class="sxs-lookup"><span data-stu-id="ac021-108">Getting Mefx</span></span>  

 <span data-ttu-id="ac021-109">Mefx は、GitHub の [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef/releases/tag/4.0) で入手できます。</span><span class="sxs-lookup"><span data-stu-id="ac021-109">Mefx is available on GitHub at [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef/releases/tag/4.0).</span></span> <span data-ttu-id="ac021-110">ツールをダウンロードして解凍してください。</span><span class="sxs-lookup"><span data-stu-id="ac021-110">Simply download and unzip the tool.</span></span>  
  
<a name="basic_syntax"></a>

## <a name="basic-syntax"></a><span data-ttu-id="ac021-111">基本構文</span><span class="sxs-lookup"><span data-stu-id="ac021-111">Basic Syntax</span></span>  

 <span data-ttu-id="ac021-112">Mefx は、次の形式でコマンド ラインから起動します。</span><span class="sxs-lookup"><span data-stu-id="ac021-112">Mefx is invoked from the command line in the following format:</span></span>  
  
```console
mefx [files and directories] [action] [options]  
```  
  
 <span data-ttu-id="ac021-113">引数の最初のセットでは、分析対象のパートの読み込み元となるファイルとディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="ac021-113">The first set of arguments specify the files and directories from which to load parts for analysis.</span></span> <span data-ttu-id="ac021-114">`/file:` スイッチを使用してファイルを指定し、 `/directory:` スイッチを使用してディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="ac021-114">Specify a file with the `/file:` switch, and a directory with the `/directory:` switch.</span></span> <span data-ttu-id="ac021-115">次の例に示すように、複数のファイルまたはディレクトリを指定できます。</span><span class="sxs-lookup"><span data-stu-id="ac021-115">You can specify multiple files or directories, as shown in the following example:</span></span>  
  
```console  
mefx /file:MyAddIn.dll /directory:Program\AddIns [action...]  
```  
  
> [!NOTE]
> <span data-ttu-id="ac021-116">各 .dll または .exe は一度だけ読み込むようにしてください。</span><span class="sxs-lookup"><span data-stu-id="ac021-116">Each .dll or .exe should only be loaded one time.</span></span> <span data-ttu-id="ac021-117">1 つのファイルを何度も読み込むと、ツールから間違った情報が返されることがあります。</span><span class="sxs-lookup"><span data-stu-id="ac021-117">If a file is loaded multiple times, the tool may return incorrect information.</span></span>  
  
 <span data-ttu-id="ac021-118">ファイルとディレクトリを指定した後、コマンドと、そのコマンドのオプションを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac021-118">After the list of files and directories, you must specify a command, and any options for that command.</span></span>  
  
<a name="listing_available_parts"></a>

## <a name="listing-available-parts"></a><span data-ttu-id="ac021-119">使用可能なパートの一覧を表示する</span><span class="sxs-lookup"><span data-stu-id="ac021-119">Listing Available Parts</span></span>  

 <span data-ttu-id="ac021-120">`/parts` アクションを使用すると、読み込んだファイルで宣言されているすべてのパートの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ac021-120">Use the `/parts` action to list all the parts declared in the files loaded.</span></span> <span data-ttu-id="ac021-121">結果は、パート名の単純なリストです。</span><span class="sxs-lookup"><span data-stu-id="ac021-121">The result is a simple list of part names.</span></span>  
  
```console
mefx /file:MyAddIn.dll /parts  
MyAddIn.AddIn  
MyAddIn.MemberPart  
```  
  
 <span data-ttu-id="ac021-122">パートの詳細を参照する場合は、 `/verbose` オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="ac021-122">For more information about the parts, use the `/verbose` option.</span></span> <span data-ttu-id="ac021-123">利用可能なすべてのパートの詳細が出力されます。</span><span class="sxs-lookup"><span data-stu-id="ac021-123">This will output more information for all available parts.</span></span> <span data-ttu-id="ac021-124">1 つのパートに関する詳細情報を入手する場合は、 `/type` アクションではなく `/parts`アクションを使用します。</span><span class="sxs-lookup"><span data-stu-id="ac021-124">To get more information about a single part, use the `/type` action instead of `/parts`.</span></span>  
  
```console  
mefx /file:MyAddIn.dll /type:MyAddIn.AddIn /verbose  
[Part] MyAddIn.MemberPart from: AssemblyCatalog (Assembly=" MyAddIn, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Export] MyAddIn.MemberPart (ContractName=" MyAddIn.MemberPart")  
```  
  
<a name="listing_imports_and_exports"></a>

## <a name="listing-imports-and-exports"></a><span data-ttu-id="ac021-125">インポートとエクスポートの一覧表示</span><span class="sxs-lookup"><span data-stu-id="ac021-125">Listing Imports and Exports</span></span>  

 <span data-ttu-id="ac021-126">`/imports` アクションと `/exports` アクションでは、インポートされたすべてのパートと、エクスポートされたすべてのパートがそれぞれ一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="ac021-126">The `/imports` and `/exports` actions will list all the imported parts and all the exported parts, respectively.</span></span> <span data-ttu-id="ac021-127">`/importers` アクションまたは `/exporters` アクションを使用して、特定の型をインポートまたはエクスポートするパートを一覧表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="ac021-127">You can also list the parts that import or export a particular type by using the `/importers` or `/exporters` actions.</span></span>  
  
```console  
mefx /file:MyAddIn.dll /importers:MyAddin.MemberPart  
MyAddin.AddIn  
```  
  
 <span data-ttu-id="ac021-128">これらのアクションに `/verbose` オプションを適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="ac021-128">You can also apply the `/verbose` option to these actions.</span></span>  
  
<a name="finding_rejected_parts"></a>

## <a name="finding-rejected-parts"></a><span data-ttu-id="ac021-129">拒否されたパートの検索</span><span class="sxs-lookup"><span data-stu-id="ac021-129">Finding Rejected Parts</span></span>  

 <span data-ttu-id="ac021-130">使用可能なパートを読み込んだ後、Mefx は MEF 合成エンジンを使用してそれらのパートを合成します。</span><span class="sxs-lookup"><span data-stu-id="ac021-130">Once it has loaded the available parts, Mefx uses the MEF composition engine to compose them.</span></span> <span data-ttu-id="ac021-131">正常に構成できないパートのことを、 *拒否された* パートと呼びます。</span><span class="sxs-lookup"><span data-stu-id="ac021-131">Parts that cannot be successfully composed are referred to as *rejected*.</span></span> <span data-ttu-id="ac021-132">拒否されたすべてのパートの一覧を表示するには、 `/rejected` アクションを使用します。</span><span class="sxs-lookup"><span data-stu-id="ac021-132">To list all the rejected parts, use the `/rejected` action.</span></span>  
  
 <span data-ttu-id="ac021-133">`/verbose` アクションで `/rejected` オプションを使用すると、拒否されたパートに関する詳細情報が出力されます。</span><span class="sxs-lookup"><span data-stu-id="ac021-133">You can use the `/verbose` option with the `/rejected` action to print detailed information about rejected parts.</span></span> <span data-ttu-id="ac021-134">次の例では、 `ClassLibrary1` という DLL に `AddIn` パートが含まれています。このパートは、 `MemberPart` パートと `ChainOne` パートをインポートします。</span><span class="sxs-lookup"><span data-stu-id="ac021-134">In the following example, the `ClassLibrary1` DLL contains the `AddIn` part, which imports the `MemberPart` and `ChainOne` parts.</span></span> <span data-ttu-id="ac021-135">`ChainOne` は `ChainTwo`をインポートしますが、 `ChainTwo` が存在しません。</span><span class="sxs-lookup"><span data-stu-id="ac021-135">`ChainOne` imports `ChainTwo`, but `ChainTwo` does not exist.</span></span> <span data-ttu-id="ac021-136">そのため、 `ChainOne` が拒否され、この拒否が原因で `AddIn` も拒否されることになります。</span><span class="sxs-lookup"><span data-stu-id="ac021-136">This means that `ChainOne` is rejected, which causes `AddIn` to be rejected.</span></span>  
  
```console  
mefx /file:ClassLibrary1.dll /rejected /verbose  
```  
  
 <span data-ttu-id="ac021-137">前のコマンドの完全な出力を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ac021-137">The following shows the complete output of the previous command:</span></span>  
  
```output
[Part] ClassLibrary1.AddIn from: AssemblyCatalog (Assembly="ClassLibrary1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Export] ClassLibrary1.AddIn (ContractName="ClassLibrary1.AddIn")  
  [Import] ClassLibrary1.AddIn.memberPart (ContractName="ClassLibrary1.MemberPart")  
    [SatisfiedBy] ClassLibrary1.MemberPart (ContractName="ClassLibrary1.MemberPart") from: ClassLibrary1.MemberPart from: AssemblyCatalog (Assembly="ClassLibrar  
y1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Import] ClassLibrary1.AddIn.chain (ContractName="ClassLibrary1.ChainOne")  
    [Exception] System.ComponentModel.Composition.ImportCardinalityMismatchException: No valid exports were found that match the constraint '((exportDefinition.ContractName == "ClassLibrary1.ChainOne") AndAlso (exportDefinition.Metadata.ContainsKey("ExportTypeIdentity") AndAlso "ClassLibrary1.ChainOne".Equals(exportDefinition.Metadata.get_Item("ExportTypeIdentity"))))', invalid exports may have been rejected.  
   at System.ComponentModel.Composition.Hosting.ExportProvider.GetExports(ImportDefinition definition, AtomicComposition atomicComposition)  
   at Microsoft.ComponentModel.Composition.Diagnostics.CompositionInfo.AnalyzeImportDefinition(ExportProvider host, IEnumerable`1 availableParts, ImportDefinition id)  
    [Unsuitable] ClassLibrary1.ChainOne (ContractName="ClassLibrary1.ChainOne")  
from: ClassLibrary1.ChainOne from: AssemblyCatalog (Assembly="ClassLibrary1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
      [Because] PartDefinitionIsRejected, The part providing the export is rejected because of other issues.  
  
[Part] ClassLibrary1.ChainOne from: AssemblyCatalog (Assembly="ClassLibrary1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Primary Rejection]  
  [Export] ClassLibrary1.ChainOne (ContractName="ClassLibrary1.ChainOne")  
  [Import] ClassLibrary1.ChainOne.chain (ContractName="ClassLibrary1.ChainTwo")  
    [Exception] System.ComponentModel.Composition.ImportCardinalityMismatchException: No valid exports were found that match the constraint '((exportDefinition.ContractName == "ClassLibrary1.ChainTwo") AndAlso (exportDefinition.Metadata.ContainsKey("ExportTypeIdentity") AndAlso "ClassLibrary1.ChainTwo".Equals(exportDefinition.Metadata.get_Item("ExportTypeIdentity"))))', invalid exports may have been rejected.  
   at System.ComponentModel.Composition.Hosting.ExportProvider.GetExports(ImportDefinition definition, AtomicComposition atomicComposition)  
   at Microsoft.ComponentModel.Composition.Diagnostics.CompositionInfo.AnalyzeImportDefinition(ExportProvider host, IEnumerable`1 availableParts, ImportDefinition id)  
```  
  
 <span data-ttu-id="ac021-138">`[Exception]` と `[Unsuitable]` の結果に、有用な情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="ac021-138">The interesting information is contained in the `[Exception]` and `[Unsuitable]` results.</span></span> <span data-ttu-id="ac021-139">`[Exception]` の結果には、パートが拒否された理由に関する情報が示されています。</span><span class="sxs-lookup"><span data-stu-id="ac021-139">The `[Exception]` result provides information about why a part was rejected.</span></span> <span data-ttu-id="ac021-140">`[Unsuitable]` の結果には、他の点では一致するパートを使用してインポートを満たせなかった理由が示されています。ここでは、インポートが見つからないために、パートそのものが拒否されたということが分かります。</span><span class="sxs-lookup"><span data-stu-id="ac021-140">The `[Unsuitable]` result indicates why an otherwise-matching part could not be used to fill an import; in this case, because that part was itself rejected for missing imports.</span></span>  
  
<a name="analyzing_primary_causes"></a>

## <a name="analyzing-primary-causes"></a><span data-ttu-id="ac021-141">主要な原因を分析する</span><span class="sxs-lookup"><span data-stu-id="ac021-141">Analyzing Primary Causes</span></span>  

 <span data-ttu-id="ac021-142">長い依存関係チェーンで複数のパートがリンクされている場合、最下位付近のパートに関係する問題によって、チェーン全体が拒否されることがあります。</span><span class="sxs-lookup"><span data-stu-id="ac021-142">If several parts are linked in a long dependency chain, a problem involving a part near the bottom may cause the entire chain to be rejected.</span></span> <span data-ttu-id="ac021-143">エラーの根本原因が必ずしも明らかであるとは限らないため、このような問題は診断が難しい場合があります。</span><span class="sxs-lookup"><span data-stu-id="ac021-143">Diagnosing these problems can be difficult because the root cause of the failure is not always obvious.</span></span> <span data-ttu-id="ac021-144">問題解決に役立てるために、 `/causes` アクションを使用できます。このアクションでは、拒否の連鎖の根本原因を見つけることを試みます。</span><span class="sxs-lookup"><span data-stu-id="ac021-144">To help with the problem, you can use the `/causes` action, which attempts to find the root cause of any cascading rejection.</span></span>  
  
 <span data-ttu-id="ac021-145">前の例で `/causes` アクションを使用すると、 `ChainOne`に関する情報だけが示されます。このパートのインポートが満たされなかったことが、 `AddIn`が拒否された根本原因であるためです。</span><span class="sxs-lookup"><span data-stu-id="ac021-145">Using the `/causes` action on the previous example would list only information for `ChainOne`, whose unfilled import is the root cause of the rejection of `AddIn`.</span></span> <span data-ttu-id="ac021-146">`/causes` アクションは、通常のオプションと `/verbose` オプションの両方で使用できます。</span><span class="sxs-lookup"><span data-stu-id="ac021-146">The `/causes` action can be used in both normal and `/verbose` options.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ac021-147">ほとんどの場合、連鎖するエラーの根本原因を Mefx で診断できます。</span><span class="sxs-lookup"><span data-stu-id="ac021-147">In most cases, Mefx will be able to diagnose the root cause of a cascading failure.</span></span> <span data-ttu-id="ac021-148">ただし、パートがプログラムによってコンテナーに追加される場合、階層コンテナーが関係している場合、またはカスタムの `ExportProvider` 実装が関係している場合には、Mefx によって原因を診断することができません</span><span class="sxs-lookup"><span data-stu-id="ac021-148">However, in cases where parts are added programmatically to a container, cases involving hierarchical containers, or cases involving custom `ExportProvider` implementations, Mefx will not be able to diagnose the cause.</span></span> <span data-ttu-id="ac021-149">これらの状況では一般にエラーの診断が難しいため、できるだけ避けることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ac021-149">In general, the previously described cases should be avoided where possible, as failures are generally difficult to diagnose.</span></span>  
  
<a name="white_lists"></a>

## <a name="allow-lists"></a><span data-ttu-id="ac021-150">許可リスト</span><span class="sxs-lookup"><span data-stu-id="ac021-150">Allow lists</span></span>

 <span data-ttu-id="ac021-151">`/whitelist` オプションでは、拒否されることが予想されるパートの一覧を示すテキスト ファイルを指定できます。</span><span class="sxs-lookup"><span data-stu-id="ac021-151">The `/whitelist` option enables you to specify a text file that lists parts that are expected to be rejected.</span></span> <span data-ttu-id="ac021-152">予期されない拒否にはフラグが設定されます。</span><span class="sxs-lookup"><span data-stu-id="ac021-152">Unexpected rejections will then be flagged.</span></span> <span data-ttu-id="ac021-153">これは、不完全なライブラリ、または一部の依存関係が欠落しているサブライブラリを分析する際に役立つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="ac021-153">This can be useful when you analyze an incomplete library, or a sublibrary that's missing some dependencies.</span></span> <span data-ttu-id="ac021-154">`/whitelist` オプションは、 `/rejected` アクションまたは `/causes` アクションに適用できます。</span><span class="sxs-lookup"><span data-stu-id="ac021-154">The `/whitelist` option can be applied to the `/rejected` or `/causes` actions.</span></span>  
  
 <span data-ttu-id="ac021-155">"ClassLibrary1.ChainOne" というテキストが含まれた test.txt という名前のファイルがあるとします。</span><span class="sxs-lookup"><span data-stu-id="ac021-155">Consider a file named test.txt that contains the text "ClassLibrary1.ChainOne".</span></span> <span data-ttu-id="ac021-156">前の例で `/rejected` アクションに `/whitelist` オプションを指定して実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ac021-156">If you run the `/rejected` action with the `/whitelist` option on the previous example, it produces the following output:</span></span>  
  
```console
mefx /file:ClassLibrary1.dll /rejected /whitelist:test.txt  
[Unexpected] ClassLibrary1.AddIn  
ClassLibrary1.ChainOne  
```
