---
description: -langversion (C# コンパイラ オプション)
title: -langversion (C# コンパイラ オプション)
ms.date: 05/20/2020
f1_keywords:
- /langversion
helpviewer_keywords:
- /langversion compiler option [C#]
- -langversion compiler option [C#]
- langversion compiler option [C#]
ms.custom: updateeachrelease
ms.assetid: 3fb00b05-a0ff-4782-b313-13a4c0f62d94
ms.openlocfilehash: 987177cc203b4c6202e8c14d8a9f4b41721e836f
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102104875"
---
# <a name="-langversion-c-compiler-options"></a><span data-ttu-id="70aaa-103">-langversion (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="70aaa-103">-langversion (C# Compiler Options)</span></span>

<span data-ttu-id="70aaa-104">コンパイラが、選択した C# 言語仕様に含まれている構文のみを受け入れるようにします。</span><span class="sxs-lookup"><span data-stu-id="70aaa-104">Causes the compiler to accept only syntax that is included in the chosen C# language specification.</span></span>

## <a name="syntax"></a><span data-ttu-id="70aaa-105">構文</span><span class="sxs-lookup"><span data-stu-id="70aaa-105">Syntax</span></span>

```console
-langversion:option
```

## <a name="arguments"></a><span data-ttu-id="70aaa-106">引数</span><span class="sxs-lookup"><span data-stu-id="70aaa-106">Arguments</span></span>

`option`

<span data-ttu-id="70aaa-107">有効な値は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="70aaa-107">The following values are valid:</span></span>

[!INCLUDE [lang-versions-table](../includes/langversion-table.md)]

<span data-ttu-id="70aaa-108">既定の言語バージョンは、アプリケーションのターゲット フレームワークやインストールされている SDK または Visual Studio のバージョンに依存します。</span><span class="sxs-lookup"><span data-stu-id="70aaa-108">The default language version depends on the target framework for your application and the version of the SDK or Visual Studio installed.</span></span> <span data-ttu-id="70aaa-109">これらの規則は、[言語バージョンの構成](../configure-language-version.md#defaults)に関する記事の中で定義されています。</span><span class="sxs-lookup"><span data-stu-id="70aaa-109">Those rules are defined in the [configuring the language version](../configure-language-version.md#defaults) article.</span></span>

## <a name="remarks"></a><span data-ttu-id="70aaa-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="70aaa-110">Remarks</span></span>

<span data-ttu-id="70aaa-111">C# アプリケーションで参照されるメタデータは、 **-langversion** コンパイラ オプションの対象になりません。</span><span class="sxs-lookup"><span data-stu-id="70aaa-111">Metadata referenced by your C# application is not subject to **-langversion** compiler option.</span></span>

<span data-ttu-id="70aaa-112">C# コンパイラのバージョンごとに言語仕様の拡張機能が含まれているため、 **-langversion** は、コンパイラの以前のバージョンと同じ機能を提供しません。</span><span class="sxs-lookup"><span data-stu-id="70aaa-112">Because each version of the C# compiler contains extensions to the language specification, **-langversion** does not give you the equivalent functionality of an earlier version of the compiler.</span></span>

<span data-ttu-id="70aaa-113">さらに、C# バージョンの更新は、一般的に主要な .NET Framework のリリースと一致しますが、新しい構文および機能は必ずしも特定のフレームワーク バージョンに関連付けられていません。</span><span class="sxs-lookup"><span data-stu-id="70aaa-113">Additionally, while C# version updates generally coincide with major .NET Framework releases, the new syntax and features are not necessarily tied to that specific framework version.</span></span> <span data-ttu-id="70aaa-114">新機能では、C# リビジョンと共にリリースされる新しいコンパイラの更新プログラムを確実に必要としますが、各特定機能には、独自の最小の .NET API または共通言語ランタイムの要件があり、この要件によって、NuGet パッケージやその他のライブラリを含めることで下位レベルのフレームワークで実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="70aaa-114">While the new features definitely require a new compiler update that is also released alongside the C# revision, each specific feature has its own minimum .NET API or common language runtime requirements that may allow it to run on downlevel frameworks by including NuGet packages or other libraries.</span></span>

<span data-ttu-id="70aaa-115">使用する **-langversion** の設定に関係なく、現在のバージョンの共通言語ランタイムを使用して .exe や .dll を作成します。</span><span class="sxs-lookup"><span data-stu-id="70aaa-115">Regardless of which **-langversion** setting you use, use the current version of the common language runtime to create your .exe or .dll.</span></span> <span data-ttu-id="70aaa-116">1 つの例外は、 **-langversion:ISO-1** の下で機能する、フレンド アセンブリと [-moduleassemblyname (C# コンパイラ オプション)](./moduleassemblyname-compiler-option.md) です。</span><span class="sxs-lookup"><span data-stu-id="70aaa-116">One exception is friend assemblies and [-moduleassemblyname (C# Compiler Option)](./moduleassemblyname-compiler-option.md), which work under **-langversion:ISO-1**.</span></span>

<span data-ttu-id="70aaa-117">C# 言語バージョンを指定するその他の方法については、[C# 言語のバージョンの選択](../configure-language-version.md)に関するトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="70aaa-117">For other ways to specify the C# language version, see the [Select the C# language version](../configure-language-version.md) article.</span></span>

<span data-ttu-id="70aaa-118">このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="70aaa-118">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="70aaa-119">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="70aaa-119">C# language specification</span></span>

| <span data-ttu-id="70aaa-120">バージョン</span><span class="sxs-lookup"><span data-stu-id="70aaa-120">Version</span></span>          | <span data-ttu-id="70aaa-121">Link</span><span class="sxs-lookup"><span data-stu-id="70aaa-121">Link</span></span>                       | <span data-ttu-id="70aaa-122">説明</span><span class="sxs-lookup"><span data-stu-id="70aaa-122">Description</span></span>                                                             |
|------------------|----------------------------|-------------------------------------------------------------------------|
| <span data-ttu-id="70aaa-123">C# 7.0 以降</span><span class="sxs-lookup"><span data-stu-id="70aaa-123">C# 7.0 and later</span></span> |                            | <span data-ttu-id="70aaa-124">現在、利用できません</span><span class="sxs-lookup"><span data-stu-id="70aaa-124">Not currently available</span></span>                                                 |
| <span data-ttu-id="70aaa-125">C# 6.0</span><span class="sxs-lookup"><span data-stu-id="70aaa-125">C# 6.0</span></span>           | <span data-ttu-id="70aaa-126">[リンク][csharp-6]</span><span class="sxs-lookup"><span data-stu-id="70aaa-126">[Link][csharp-6]</span></span>           | <span data-ttu-id="70aaa-127">C# 言語仕様バージョン 6 - 非公式ドラフト: .NET Foundation</span><span class="sxs-lookup"><span data-stu-id="70aaa-127">C# Language Specification Version 6 - Unofficial Draft: .NET Foundation</span></span> |
| <span data-ttu-id="70aaa-128">C# 5.0</span><span class="sxs-lookup"><span data-stu-id="70aaa-128">C# 5.0</span></span>           | <span data-ttu-id="70aaa-129">[PDF のダウンロード][csharp-5]</span><span class="sxs-lookup"><span data-stu-id="70aaa-129">[Download PDF][csharp-5]</span></span>   | <span data-ttu-id="70aaa-130">Standard ECMA-334 5th Edition</span><span class="sxs-lookup"><span data-stu-id="70aaa-130">Standard ECMA-334 5th Edition</span></span>                                           |
| <span data-ttu-id="70aaa-131">C# 3.0</span><span class="sxs-lookup"><span data-stu-id="70aaa-131">C# 3.0</span></span>           | <span data-ttu-id="70aaa-132">[DOC のダウンロード][csharp-3]</span><span class="sxs-lookup"><span data-stu-id="70aaa-132">[Download DOC][csharp-3]</span></span>   | <span data-ttu-id="70aaa-133">C# 言語仕様バージョン 3.0:Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="70aaa-133">C# Language Specification Version 3.0: Microsoft Corporation</span></span>            |
| <span data-ttu-id="70aaa-134">C# 2.0</span><span class="sxs-lookup"><span data-stu-id="70aaa-134">C# 2.0</span></span>           | <span data-ttu-id="70aaa-135">[PDF のダウンロード][csharp-2]</span><span class="sxs-lookup"><span data-stu-id="70aaa-135">[Download PDF][csharp-2]</span></span>   | <span data-ttu-id="70aaa-136">Standard ECMA-334 4th Edition</span><span class="sxs-lookup"><span data-stu-id="70aaa-136">Standard ECMA-334 4th Edition</span></span>                                           |
| <span data-ttu-id="70aaa-137">C# 1.2</span><span class="sxs-lookup"><span data-stu-id="70aaa-137">C# 1.2</span></span>           | <span data-ttu-id="70aaa-138">[DOC のダウンロード][csharp-1.2]</span><span class="sxs-lookup"><span data-stu-id="70aaa-138">[Download DOC][csharp-1.2]</span></span> | <span data-ttu-id="70aaa-139">C# 言語仕様バージョン 1.2:Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="70aaa-139">C# Language Specification Version 1.2: Microsoft Corporation</span></span>            |
| <span data-ttu-id="70aaa-140">C# 1.0</span><span class="sxs-lookup"><span data-stu-id="70aaa-140">C# 1.0</span></span>           | <span data-ttu-id="70aaa-141">[DOC のダウンロード][csharp-1]</span><span class="sxs-lookup"><span data-stu-id="70aaa-141">[Download DOC][csharp-1]</span></span>   | <span data-ttu-id="70aaa-142">C# 言語仕様バージョン 1.0:Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="70aaa-142">C# Language Specification Version 1.0: Microsoft Corporation</span></span>            |

[csharp-6]: /dotnet/csharp/language-reference/language-specification/introduction
[csharp-5]: https://www.ecma-international.org/wp-content/uploads/ECMA-334_5th_edition_december_2017.pdf
[csharp-3]: https://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc
[csharp-2]: https://www.ecma-international.org/wp-content/uploads/ECMA-334_4th_edition_june_2006.pdf
[csharp-1.2]: https://www.ecma-international.org/wp-content/uploads/ECMA-334_2nd_edition_december_2002.pdf
[csharp-1]: https://www.ecma-international.org/wp-content/uploads/ECMA-334_1st_edition_december_2001.pdf

## <a name="minimum-sdk-version-needed-to-support-all-language-features"></a><span data-ttu-id="70aaa-143">すべての言語機能をサポートするために必要な SDK の最小バージョン</span><span class="sxs-lookup"><span data-stu-id="70aaa-143">Minimum SDK version needed to support all language features</span></span>

<span data-ttu-id="70aaa-144">次の表は、SDK の最小バージョンに対応する言語バージョンをサポートする C# コンパイラを示しています。</span><span class="sxs-lookup"><span data-stu-id="70aaa-144">The following table lists the minimum versions of the SDK with the C# compiler that supports the corresponding language version:</span></span>

| <span data-ttu-id="70aaa-145">C# バージョン</span><span class="sxs-lookup"><span data-stu-id="70aaa-145">C# version</span></span> | <span data-ttu-id="70aaa-146">SDK の最小バージョン</span><span class="sxs-lookup"><span data-stu-id="70aaa-146">Minimum SDK version</span></span>                                                                  |
|------------|--------------------------------------------------------------------------------------|
| <span data-ttu-id="70aaa-147">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="70aaa-147">C# 8.0</span></span>     | <span data-ttu-id="70aaa-148">Microsoft Visual Studio/Build Tools 2019、バージョン 16.3 または .NET Core 3.0 SDK</span><span class="sxs-lookup"><span data-stu-id="70aaa-148">Microsoft Visual Studio/Build Tools 2019, version 16.3, or .NET Core 3.0 SDK</span></span>         |
| <span data-ttu-id="70aaa-149">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="70aaa-149">C# 7.3</span></span>     | <span data-ttu-id="70aaa-150">Microsoft Visual Studio/Build Tools 2017、バージョン 15.7</span><span class="sxs-lookup"><span data-stu-id="70aaa-150">Microsoft Visual Studio/Build Tools 2017, version 15.7</span></span>                               |
| <span data-ttu-id="70aaa-151">C# 7.2</span><span class="sxs-lookup"><span data-stu-id="70aaa-151">C# 7.2</span></span>     | <span data-ttu-id="70aaa-152">Microsoft Visual Studio/Build Tools 2017、バージョン 15.5</span><span class="sxs-lookup"><span data-stu-id="70aaa-152">Microsoft Visual Studio/Build Tools 2017, version 15.5</span></span>                               |
| <span data-ttu-id="70aaa-153">C# 7.1</span><span class="sxs-lookup"><span data-stu-id="70aaa-153">C# 7.1</span></span>     | <span data-ttu-id="70aaa-154">Microsoft Visual Studio/Build Tools 2017、バージョン 15.3</span><span class="sxs-lookup"><span data-stu-id="70aaa-154">Microsoft Visual Studio/Build Tools 2017, version 15.3</span></span>                               |
| <span data-ttu-id="70aaa-155">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="70aaa-155">C# 7.0</span></span>     | <span data-ttu-id="70aaa-156">Microsoft Visual Studio/Build Tools 2017</span><span class="sxs-lookup"><span data-stu-id="70aaa-156">Microsoft Visual Studio/Build Tools 2017</span></span>                                             |
| <span data-ttu-id="70aaa-157">C# 6</span><span class="sxs-lookup"><span data-stu-id="70aaa-157">C# 6</span></span>       | <span data-ttu-id="70aaa-158">Microsoft Visual Studio/Build Tools 2015</span><span class="sxs-lookup"><span data-stu-id="70aaa-158">Microsoft Visual Studio/Build Tools 2015</span></span>                                             |
| <span data-ttu-id="70aaa-159">C# 5</span><span class="sxs-lookup"><span data-stu-id="70aaa-159">C# 5</span></span>       | <span data-ttu-id="70aaa-160">Microsoft Visual Studio/Build Tools 2012、またはバンドルされている .Net Framework 4.5 コンパイラ</span><span class="sxs-lookup"><span data-stu-id="70aaa-160">Microsoft Visual Studio/Build Tools 2012 or bundled .NET Framework 4.5 compiler</span></span>      |
| <span data-ttu-id="70aaa-161">C# 4</span><span class="sxs-lookup"><span data-stu-id="70aaa-161">C# 4</span></span>       | <span data-ttu-id="70aaa-162">Microsoft Visual Studio/Build Tools 2010、またはバンドルされている .Net Framework 4.0 コンパイラ</span><span class="sxs-lookup"><span data-stu-id="70aaa-162">Microsoft Visual Studio/Build Tools 2010 or bundled .NET Framework 4.0 compiler</span></span>      |
| <span data-ttu-id="70aaa-163">C# 3</span><span class="sxs-lookup"><span data-stu-id="70aaa-163">C# 3</span></span>       | <span data-ttu-id="70aaa-164">Microsoft Visual Studio/Build Tools 2008、またはバンドルされている .Net Framework 3.5 コンパイラ</span><span class="sxs-lookup"><span data-stu-id="70aaa-164">Microsoft Visual Studio/Build Tools 2008 or bundled .NET Framework 3.5 compiler</span></span>      |
| <span data-ttu-id="70aaa-165">C# 2</span><span class="sxs-lookup"><span data-stu-id="70aaa-165">C# 2</span></span>       | <span data-ttu-id="70aaa-166">Microsoft Visual Studio/Build Tools 2005、またはバンドルされている .Net Framework 2.0 コンパイラ</span><span class="sxs-lookup"><span data-stu-id="70aaa-166">Microsoft Visual Studio/Build Tools 2005 or bundled .NET Framework 2.0 compiler</span></span>      |
| <span data-ttu-id="70aaa-167">C# 1.0/1.2</span><span class="sxs-lookup"><span data-stu-id="70aaa-167">C# 1.0/1.2</span></span> | <span data-ttu-id="70aaa-168">Microsoft Visual Studio/Build Tools .NET 2002 またはバンドルされている .NET Framework 1.0 コンパイラ</span><span class="sxs-lookup"><span data-stu-id="70aaa-168">Microsoft Visual Studio/Build Tools .NET 2002 or bundled .NET Framework 1.0 compiler</span></span> |

## <a name="see-also"></a><span data-ttu-id="70aaa-169">関連項目</span><span class="sxs-lookup"><span data-stu-id="70aaa-169">See also</span></span>

- [<span data-ttu-id="70aaa-170">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="70aaa-170">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="70aaa-171">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="70aaa-171">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
