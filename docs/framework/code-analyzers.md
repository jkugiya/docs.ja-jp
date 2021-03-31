---
title: .NET Framework 用のコード アナライザー
titleSuffix: ''
description: .NET Framework Analyzers パッケージ内のアナライザーを使用し、コードの問題を見つけて対処する方法について学習します。
author: billwagner
ms.author: wiwagn
ms.date: 10/23/2020
ms.openlocfilehash: 69dfbc9f9645c7f602ffbce46308b241c119fd96
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2020
ms.locfileid: "103412164"
---
# <a name="code-analysis"></a><span data-ttu-id="4c620-103">コード分析</span><span class="sxs-lookup"><span data-stu-id="4c620-103">Code analysis</span></span>

<span data-ttu-id="4c620-104">コード アナライザーを使用すると、.NET Framework アプリケーション コードの潜在的な問題を見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="4c620-104">You can use code analyzers to find potential issues in your .NET Framework application code.</span></span> <span data-ttu-id="4c620-105">アナライザーによって、潜在的な問題が検出され、その修正が提案されます。</span><span class="sxs-lookup"><span data-stu-id="4c620-105">The analyzers find potential issues and suggest fixes for them.</span></span>

<span data-ttu-id="4c620-106">コードを書くとき、あるいは CI ビルドの一部として、Roslyn ベースのコード アナライザーは、Visual Studio で対話的に動作します。</span><span class="sxs-lookup"><span data-stu-id="4c620-106">Roslyn-based code analyzers run interactively in Visual Studio as you write your code or as part of a CI build.</span></span> <span data-ttu-id="4c620-107">開発サイクルのできるだけ早い段階で、プロジェクトにアナライザーを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c620-107">You should add the analyzers to your project as early as possible in the development cycle.</span></span> <span data-ttu-id="4c620-108">コードに潜む問題を見つけるのが早ければ早いほど、修正が簡単になります。</span><span class="sxs-lookup"><span data-stu-id="4c620-108">The sooner you find any potential issues in your code, the easier they are to fix.</span></span> <span data-ttu-id="4c620-109">アナライザーによって、既存のコードの問題にフラグが設定され、開発を続けると、新しい問題に関する警告が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4c620-109">The analyzers flag issues in existing code and warn about new issues as you continue development.</span></span>

## <a name="install-and-configure-analyzers"></a><span data-ttu-id="4c620-110">アナライザーのインストールと構成</span><span class="sxs-lookup"><span data-stu-id="4c620-110">Install and configure analyzers</span></span>

<span data-ttu-id="4c620-111">.NET Framework Analyzer は [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) NuGet パッケージで配布されます。</span><span class="sxs-lookup"><span data-stu-id="4c620-111">The .NET Framework Analyzer is delivered in the [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) NuGet package.</span></span> <span data-ttu-id="4c620-112">このパッケージには、.NET Framework API に固有のアナライザーが用意されており、これにはセキュリティ アナライザーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="4c620-112">This package provides analyzers that are specific to .NET Framework APIs, which includes security analyzers.</span></span> <span data-ttu-id="4c620-113">このパッケージは [Microsoft.CodeAnalysis.FxCopAnalyzers パッケージ](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers)に含まれているので、パッケージをインストールする場合は、.NET Framework アナライザーを個別にインストールする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="4c620-113">The package is included with the [Microsoft.CodeAnalysis.FxCopAnalyzers package](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers), so if you install that package, there's no need to install the .NET Framework analyzers separately.</span></span>

<span data-ttu-id="4c620-114">アナライザーを実行するすべてのプロジェクトに NuGet パッケージをインストールします。</span><span class="sxs-lookup"><span data-stu-id="4c620-114">Install the NuGet package on every project where you want the analyzers to run.</span></span> <span data-ttu-id="4c620-115">1 人の開発者がそれをプロジェクトに追加すれば十分です。</span><span class="sxs-lookup"><span data-stu-id="4c620-115">Only one developer needs to add them to the project.</span></span> <span data-ttu-id="4c620-116">アナライザー パッケージはプロジェクト依存関係であり、更新済みのソリューションが与えられると、あらゆる開発者のコンピューターで実行されます。</span><span class="sxs-lookup"><span data-stu-id="4c620-116">The analyzer package is a project dependency and will run on every developer's machine once it has the updated solution.</span></span>

<span data-ttu-id="4c620-117">このパッケージをインストールするには、プロジェクトを右クリックし、[依存関係の管理] を選択します。</span><span class="sxs-lookup"><span data-stu-id="4c620-117">To install the package, right-click on the project, and select "Manage Dependencies".</span></span> <span data-ttu-id="4c620-118">NuGet エクスプローラーで、"Microsoft.NetFramework.Analyzers" を検索します。</span><span class="sxs-lookup"><span data-stu-id="4c620-118">From the NuGet explorer, search for "Microsoft.NetFramework.Analyzers".</span></span> <span data-ttu-id="4c620-119">ソリューションのすべてのプロジェクトで安定した最新のバージョンをインストールします。</span><span class="sxs-lookup"><span data-stu-id="4c620-119">Install the latest stable version in all projects in your solution.</span></span>

## <a name="use-the-analyzers"></a><span data-ttu-id="4c620-120">アナライザーの使用</span><span class="sxs-lookup"><span data-stu-id="4c620-120">Use the analyzers</span></span>

<span data-ttu-id="4c620-121">NuGet パッケージがインストールされたら、ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="4c620-121">Once the NuGet package is installed, build your solution.</span></span> <span data-ttu-id="4c620-122">アナライザーは、コードベースで見つかった問題を報告します。</span><span class="sxs-lookup"><span data-stu-id="4c620-122">The analyzer will report any issues it locates in your codebase.</span></span> <span data-ttu-id="4c620-123">問題は Visual Studio の [エラー一覧] ウィンドウに警告として表示されます。次の画像をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4c620-123">The issues are reported as warnings in the Visual Studio Error List window, as shown in the following image:</span></span>

![.NET Framework アナライザーによって報告される問題](./media/framework-analyzers-2.png)

<span data-ttu-id="4c620-125">コードを記述しているとき、コードに潜在的な問題があれば、その部分に波線が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4c620-125">As you write code, you see squiggles underneath any potential issue in your code.</span></span>
<span data-ttu-id="4c620-126">次の画像に示すように、問題をポイントすると、詳細情報が表示され、考えられる修正候補が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4c620-126">Hover over any issue to get more information and see suggestions for any possible fix, as shown in the following image:</span></span>

![コード アナライザーによって検出された問題の対話型レポート。](./media/framework-analyzers-1.png)

<span data-ttu-id="4c620-128">詳細については、[Visual Studio のコード分析](/visualstudio/code-quality/roslyn-analyzers-overview)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c620-128">For more information, see [Code analysis in Visual Studio](/visualstudio/code-quality/roslyn-analyzers-overview).</span></span>

## <a name="types-of-rules"></a><span data-ttu-id="4c620-129">規則の種類</span><span class="sxs-lookup"><span data-stu-id="4c620-129">Types of rules</span></span>

<span data-ttu-id="4c620-130">アナライザーによって、ソリューション内のコードが検査され、`CA` プレフィックスと共に警告が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4c620-130">The analyzers examine the code in your solution and surface warnings with a `CA` prefix.</span></span> <span data-ttu-id="4c620-131">可能性のあるすべての警告の一覧については、「[コード品質規則](../fundamentals/code-analysis/quality-rules/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c620-131">For a list of all possible warnings, see [Code quality rules](../fundamentals/code-analysis/quality-rules/index.md).</span></span> <span data-ttu-id="4c620-132">.NET Framework の API に適用されるのは、次のような一部の警告のみです。</span><span class="sxs-lookup"><span data-stu-id="4c620-132">Only some of these warnings apply to .NET Framework APIS, including:</span></span>

- [<span data-ttu-id="4c620-133">CA1058:型は、一定の基本型を拡張することはできません</span><span class="sxs-lookup"><span data-stu-id="4c620-133">CA1058: Types should not extend certain base types</span></span>](../fundamentals/code-analysis/quality-rules/ca1058.md)

- [<span data-ttu-id="4c620-134">CA2153: 破損状態例外はキャッチしないでください</span><span class="sxs-lookup"><span data-stu-id="4c620-134">CA2153: Do not catch corrupted state exceptions</span></span>](../fundamentals/code-analysis/quality-rules/ca2153.md)

- [<span data-ttu-id="4c620-135">CA2229:シリアル化コンストラクターを実装します</span><span class="sxs-lookup"><span data-stu-id="4c620-135">CA2229: Implement serialization constructors</span></span>](../fundamentals/code-analysis/quality-rules/ca2229.md)

- [<span data-ttu-id="4c620-136">CA2235:すべてのシリアル化不可能なフィールドを設定します</span><span class="sxs-lookup"><span data-stu-id="4c620-136">CA2235: Mark all non-serializable fields</span></span>](../fundamentals/code-analysis/quality-rules/ca2235.md)

- [<span data-ttu-id="4c620-137">CA2237: ISerializable 型を Serializable に設定します</span><span class="sxs-lookup"><span data-stu-id="4c620-137">CA2237: Mark ISerializable types with serializable</span></span>](../fundamentals/code-analysis/quality-rules/ca2237.md)

- [<span data-ttu-id="4c620-138">CA3075: XML の安全ではない DTD の処理</span><span class="sxs-lookup"><span data-stu-id="4c620-138">CA3075: Insecure DTD processing in XML</span></span>](../fundamentals/code-analysis/quality-rules/ca3075.md)

- [<span data-ttu-id="4c620-139">CA5350: 脆弱な暗号アルゴリズムを使用しないでください</span><span class="sxs-lookup"><span data-stu-id="4c620-139">CA5350: Do not use weak cryptographic algorithms</span></span>](../fundamentals/code-analysis/quality-rules/ca5350.md)

- [<span data-ttu-id="4c620-140">CA5351 破られた暗号アルゴリズムを使用しないでください</span><span class="sxs-lookup"><span data-stu-id="4c620-140">CA5351 Do not use broken cryptographic algorithms</span></span>](../fundamentals/code-analysis/quality-rules/ca5351.md)

## <a name="see-also"></a><span data-ttu-id="4c620-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="4c620-141">See also</span></span>

- [<span data-ttu-id="4c620-142">Visual Studio でのコード分析</span><span class="sxs-lookup"><span data-stu-id="4c620-142">Code analysis in Visual Studio</span></span>](/visualstudio/code-quality/roslyn-analyzers-overview)
- [<span data-ttu-id="4c620-143">.NET SDK でのコード分析</span><span class="sxs-lookup"><span data-stu-id="4c620-143">Code analysis in the .NET SDK</span></span>](../fundamentals/code-analysis/overview.md)
