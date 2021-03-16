---
title: .NET でのシンボル
description: .NET でのシンボルとポータブル PDB の概要
ms.date: 02/08/2021
ms.openlocfilehash: da59a07166cd1f73160da8d9ac53b5823bf13e7b
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102108270"
---
# <a name="symbols"></a><span data-ttu-id="7f5e1-103">Symbols</span><span class="sxs-lookup"><span data-stu-id="7f5e1-103">Symbols</span></span>

<span data-ttu-id="7f5e1-104">シンボルは、デバッグや他の診断ツールに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="7f5e1-104">Symbols are useful for debugging and other diagnostic tools.</span></span> <span data-ttu-id="7f5e1-105">シンボル ファイルの内容は、言語、コンパイラ、およびプラットフォームによって異なります。</span><span class="sxs-lookup"><span data-stu-id="7f5e1-105">The contents of symbol files vary between languages, compilers, and platforms.</span></span> <span data-ttu-id="7f5e1-106">非常に高いレベルのシンボルは、ソース コードとコンパイラによって生成されるバイナリとの間のマッピングです。</span><span class="sxs-lookup"><span data-stu-id="7f5e1-106">At a very high level symbols are a mapping between the source code and the binary produced by the compiler.</span></span> <span data-ttu-id="7f5e1-107">これらのマッピングは、[Visual Studio](/visualstudio/debugger/what-is-debugging) や [Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging) などのツールによって、ソースの行番号の情報またはローカル変数名を解決するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="7f5e1-107">These mappings are used by tools like [Visual Studio](/visualstudio/debugger/what-is-debugging) and [Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging) to resolve source line number information or local variable names.</span></span>

<span data-ttu-id="7f5e1-108">[シンボルに関する Windows のドキュメント](/windows/win32/dxtecharts/debugging-with-symbols)には、Windows のシンボルに関する詳細な情報が含まれていますが、多くの概念は他のプラットフォームにも当てはまります。</span><span class="sxs-lookup"><span data-stu-id="7f5e1-108">The [Windows documentation on symbols](/windows/win32/dxtecharts/debugging-with-symbols) contain more detailed information on symbols for Windows, although many of the concepts apply to other platforms as well.</span></span>

## <a name="learn-about-nets-portable-pdb-format"></a><span data-ttu-id="7f5e1-109">.NET のポータブル PDB 形式について学習する</span><span class="sxs-lookup"><span data-stu-id="7f5e1-109">Learn about .NET's Portable PDB format</span></span>

<span data-ttu-id="7f5e1-110">.NET Core には、新しいシンボル ファイル (PDB) の形式であるポータブル PDB が導入されています。</span><span class="sxs-lookup"><span data-stu-id="7f5e1-110">.NET Core introduces a new symbol file (PDB) format - the portable PDB.</span></span> <span data-ttu-id="7f5e1-111">Windows 専用である従来の PDB とは異なり、ポータブル PDB を作成すると、すべてのプラットフォームで読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="7f5e1-111">Unlike traditional PDBs which are Windows-only, portable PDBs can be created and read on all platforms.</span></span>

### <a name="what-is-a-pdb"></a><span data-ttu-id="7f5e1-112">PDB とは</span><span class="sxs-lookup"><span data-stu-id="7f5e1-112">What is a PDB?</span></span>

<span data-ttu-id="7f5e1-113">PDB ファイルは、コンパイラによって生成される補助ファイルであり、他のツール (特にデバッガー) に、メインの実行可能ファイルの内容、およびその生成方法に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="7f5e1-113">A PDB file is an auxiliary file produced by a compiler to provide other tools, especially debuggers, information about what is in the main executable file and how it was produced.</span></span> <span data-ttu-id="7f5e1-114">たとえば、デバッガーによって PDB が読み取られ、foo.cs の 12 行目が実行可能ファイルの適切な場所にマップされて、ブレークポイントを設定できるようになります。</span><span class="sxs-lookup"><span data-stu-id="7f5e1-114">For example, a debugger reads a PDB to map foo.cs line 12 to the right executable location so that it can set a breakpoint.</span></span> <span data-ttu-id="7f5e1-115">Windows PDB 形式はかなり長い時間が経過しており、さらに古い他のネイティブ デバッグ シンボル形式から進化したものです。</span><span class="sxs-lookup"><span data-stu-id="7f5e1-115">The Windows PDB format has been around a long time, and it evolved from other native debugging symbol formats which were even older.</span></span> <span data-ttu-id="7f5e1-116">最初は、ネイティブ (C/C++) プログラム用の形式でした。</span><span class="sxs-lookup"><span data-stu-id="7f5e1-116">It started out its life as a format for native (C/C++) programs.</span></span> <span data-ttu-id="7f5e1-117">.NET Framework の最初のリリースで、Windows PDB 形式は .NET をサポートするように拡張されました。</span><span class="sxs-lookup"><span data-stu-id="7f5e1-117">For the first release of the .NET Framework, the Windows PDB format was extended to support .NET.</span></span>

## <a name="use-the-correct-pdb-format-for-your-scenario"></a><span data-ttu-id="7f5e1-118">シナリオに適した PDB 形式を使用する</span><span class="sxs-lookup"><span data-stu-id="7f5e1-118">Use the correct PDB format for your scenario</span></span>

<span data-ttu-id="7f5e1-119">ポータブル PDB も Windows PDB も、すべての場所でサポートされているわけではないため、使用する形式を決定するには、プロジェクトを使用およびデバッグする場所を検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7f5e1-119">Neither portable PDBs nor Windows PDBs are supported everywhere, so you need to consider where your project will want to be used and debugged to decide which format to use.</span></span> <span data-ttu-id="7f5e1-120">両方の形式で使用およびデバッグできるようにしたいプロジェクトがある場合は、異なるビルド構成を使用して、プロジェクトを 2 回ビルドし、両方の種類のコンシューマーをサポートできます。</span><span class="sxs-lookup"><span data-stu-id="7f5e1-120">If you have a project that you want to be able to use and debug in both formats, you can use different build configurations and build the project twice to support both types of consumer.</span></span>

### <a name="support-for-portable-pdbs"></a><span data-ttu-id="7f5e1-121">ポータブル PDB のサポート</span><span class="sxs-lookup"><span data-stu-id="7f5e1-121">Support for Portable PDBs</span></span>

<span data-ttu-id="7f5e1-122">ポータブル PDB は、どのオペレーティング システムでも読み取ることができ、マネージド コードで推奨されるシンボル形式ですが、それがサポートされていないレガシ ツールとアプリケーションがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="7f5e1-122">Portable PDBs can be read on any operating systems and is the recommended symbol format for managed code, but there are a number of legacy tools and applications where they aren't supported:</span></span>

* <span data-ttu-id="7f5e1-123">.NET Framework 4.7.1 以前を対象とするアプリケーション: 行番号に戻るマッピングが含まれるスタック トレースの出力 (ASP.NET のエラー ページなど)。</span><span class="sxs-lookup"><span data-stu-id="7f5e1-123">Applications targeting .NET Framework 4.7.1 or earlier: printing stack traces with mappings back to line numbers (such as in an ASP.NET error page).</span></span> <span data-ttu-id="7f5e1-124">メソッドの名前は影響を受けません。ソース ファイル名と行番号のみがサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="7f5e1-124">The name of methods is unaffected, only the source file names and line numbers are unsupported.</span></span>

* <span data-ttu-id="7f5e1-125">ildasm や .NET Reflector などの .NET 逆コンパイラを使用して、ソース行マッピングまたはローカル パラメーター名の表示を予想します。</span><span class="sxs-lookup"><span data-stu-id="7f5e1-125">Using .NET decompilers such as ildasm or .NET reflector and expecting to see source line mappings or local parameter names.</span></span>

* <span data-ttu-id="7f5e1-126">最新バージョンの [DIA](/visualstudio/debugger/debug-interface-access/debug-interface-access-sdk) と、シンボルの読み取りにそれを使用するツール (WinDBG など) ではポータブル PDB がサポートされますが、古いバージョンではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="7f5e1-126">The latest versions of [DIA](/visualstudio/debugger/debug-interface-access/debug-interface-access-sdk) and tools using it for reading symbols, such as WinDBG support Portable PDBs, but older version do not.</span></span>

* <span data-ttu-id="7f5e1-127">古いバージョンのプロファイラーで、ポータブル PDB がサポートされていない場合があります。</span><span class="sxs-lookup"><span data-stu-id="7f5e1-127">There may be older versions of profilers that do not support portable PDBs.</span></span>

<span data-ttu-id="7f5e1-128">ポータブル PDB をサポートしていないツールでそれを使用するには、ポータブル PDB と Windows PDB を変換する Pdb2Pdb[https://github.com/dotnet/symreader-converter#pdb2pdb ] を使用してみることができます。</span><span class="sxs-lookup"><span data-stu-id="7f5e1-128">To use portable PDBs on tools that do not support them, you can try using Pdb2Pdb[https://github.com/dotnet/symreader-converter#pdb2pdb] which converts between Portable PDBs and Windows PDBs.</span></span>

### <a name="support-for-windows-pdbs"></a><span data-ttu-id="7f5e1-129">Windows PDB のサポート</span><span class="sxs-lookup"><span data-stu-id="7f5e1-129">Support for Windows PDBs</span></span>

<span data-ttu-id="7f5e1-130">Windows PDB の書き込みまたは読み取りは、Windows 上でのみ可能です。</span><span class="sxs-lookup"><span data-stu-id="7f5e1-130">Windows PDBs can only be written or read on Windows.</span></span> <span data-ttu-id="7f5e1-131">マネージド コードへの Windows PDB の使用は廃止されており、レガシ ツールでのみ必要です。</span><span class="sxs-lookup"><span data-stu-id="7f5e1-131">Using Windows PDBs for managed code is obsolete and is only needed for legacy tools.</span></span> <span data-ttu-id="7f5e1-132">一部の新しいコンパイラ機能はポータブル PDB 専用に実装されているので、Windows PDB ではなくポータブル PDB を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7f5e1-132">It is recommended that you use portable PDBs instead of Windows PDBs as some newer compiler features that are implemented for only portable PDBs.</span></span>

## <a name="see-also"></a><span data-ttu-id="7f5e1-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="7f5e1-133">See also</span></span>

* <span data-ttu-id="7f5e1-134">[dotnet-symbol](./dotnet-symbol.md) を使用して、フレームワーク バイナリ用のシンボル ファイルをダウンロードできます</span><span class="sxs-lookup"><span data-stu-id="7f5e1-134">[dotnet-symbol](./dotnet-symbol.md) can be used to download symbol files for framework binaries</span></span>

* [<span data-ttu-id="7f5e1-135">シンボルに関する Windows のドキュメント</span><span class="sxs-lookup"><span data-stu-id="7f5e1-135">Windows documentation on symbols</span></span>](/windows/win32/dxtecharts/debugging-with-symbols)
