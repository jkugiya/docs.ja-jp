---
description: '詳細情報: -deterministic'
title: -deterministic
ms.date: 04/11/2018
helpviewer_keywords:
- deterministic compiler option [Visual Basic]
- -deterministic compiler option [Visual Basic]
- -deterministic compiler option [Visual Basic]
ms.openlocfilehash: b339b76d4f95ba80f8e92c4961586fa390b0839a
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100461516"
---
# <a name="-deterministic"></a><span data-ttu-id="e0ca0-103">-deterministic</span><span class="sxs-lookup"><span data-stu-id="e0ca0-103">-deterministic</span></span>

<span data-ttu-id="e0ca0-104">同一の入力に対して、バイト単位の出力がコンパイル全体で同一のアセンブリをコンパイラに生成させます。</span><span class="sxs-lookup"><span data-stu-id="e0ca0-104">Causes the compiler to produce an assembly whose byte-for-byte output is identical across compilations for identical inputs.</span></span>

## <a name="syntax"></a><span data-ttu-id="e0ca0-105">構文</span><span class="sxs-lookup"><span data-stu-id="e0ca0-105">Syntax</span></span>

```console
-deterministic
```

## <a name="remarks"></a><span data-ttu-id="e0ca0-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="e0ca0-106">Remarks</span></span>

<span data-ttu-id="e0ca0-107">既定では、コンパイラはタイムスタンプと乱数から生成された GUID を追加するため、指定した入力のセットからのコンパイラの出力は固有になります。</span><span class="sxs-lookup"><span data-stu-id="e0ca0-107">By default, compiler output from a given set of inputs is unique, since the compiler adds a timestamp and a GUID that is generated from random numbers.</span></span> <span data-ttu-id="e0ca0-108">`-deterministic` オプションを使用して、*決定論的アセンブリ* を生成します。そのバイナリ コンテンツは、入力が同じである限り、コンパイル全体で同一になります。</span><span class="sxs-lookup"><span data-stu-id="e0ca0-108">You use the `-deterministic` option to produce a *deterministic assembly*, one whose binary content is identical across compilations as long as the input remains the same.</span></span>

<span data-ttu-id="e0ca0-109">コンパイラでは決定性のために次の入力が考慮されます。</span><span class="sxs-lookup"><span data-stu-id="e0ca0-109">The compiler considers the following inputs for the purpose of determinism:</span></span>

- <span data-ttu-id="e0ca0-110">コマンド ライン パラメーターのシーケンス。</span><span class="sxs-lookup"><span data-stu-id="e0ca0-110">The sequence of command-line parameters.</span></span>
- <span data-ttu-id="e0ca0-111">コンパイラの .rsp 応答ファイルの内容。</span><span class="sxs-lookup"><span data-stu-id="e0ca0-111">The contents of the compiler's .rsp response file.</span></span>
- <span data-ttu-id="e0ca0-112">使用されるコンパイラの正確なバージョン、およびその参照先のアセンブリ。</span><span class="sxs-lookup"><span data-stu-id="e0ca0-112">The precise version of the compiler used, and its referenced assemblies.</span></span>
- <span data-ttu-id="e0ca0-113">現在のディレクトリ パス。</span><span class="sxs-lookup"><span data-stu-id="e0ca0-113">The current directory path.</span></span>
- <span data-ttu-id="e0ca0-114">すべてのファイルのバイナリ コンテンツは、以下を含めて、直接または間接のいずれかでコンパイラに明示的に渡されます。</span><span class="sxs-lookup"><span data-stu-id="e0ca0-114">The binary contents of all files explicitly passed to the compiler either directly or indirectly, including:</span></span>
  - <span data-ttu-id="e0ca0-115">ソース ファイル</span><span class="sxs-lookup"><span data-stu-id="e0ca0-115">Source files</span></span>
  - <span data-ttu-id="e0ca0-116">参照アセンブリ</span><span class="sxs-lookup"><span data-stu-id="e0ca0-116">Referenced assemblies</span></span>
  - <span data-ttu-id="e0ca0-117">参照モジュール</span><span class="sxs-lookup"><span data-stu-id="e0ca0-117">Referenced modules</span></span>
  - <span data-ttu-id="e0ca0-118">リソース</span><span class="sxs-lookup"><span data-stu-id="e0ca0-118">Resources</span></span>
  - <span data-ttu-id="e0ca0-119">厳密な名前のキー ファイル</span><span class="sxs-lookup"><span data-stu-id="e0ca0-119">The strong name key file</span></span>
  - <span data-ttu-id="e0ca0-120">@ 応答ファイル</span><span class="sxs-lookup"><span data-stu-id="e0ca0-120">@ response files</span></span>
  - <span data-ttu-id="e0ca0-121">アナライザー</span><span class="sxs-lookup"><span data-stu-id="e0ca0-121">Analyzers</span></span>
  - <span data-ttu-id="e0ca0-122">ルールセット</span><span class="sxs-lookup"><span data-stu-id="e0ca0-122">Rulesets</span></span>
  - <span data-ttu-id="e0ca0-123">アナライザーによって使用される可能性がある追加のファイル</span><span class="sxs-lookup"><span data-stu-id="e0ca0-123">Additional files that may be used by analyzers</span></span>
- <span data-ttu-id="e0ca0-124">現在のカルチャ (診断と例外メッセージが生成される言語)。</span><span class="sxs-lookup"><span data-stu-id="e0ca0-124">The current culture (for the language in which diagnostics and exception messages are produced).</span></span>
- <span data-ttu-id="e0ca0-125">エンコードが指定されていない場合の既定のエンコード (または現在のコード ページ)。</span><span class="sxs-lookup"><span data-stu-id="e0ca0-125">The default encoding (or the current code page) if the encoding is not specified.</span></span>
- <span data-ttu-id="e0ca0-126">コンパイラの検索パス上のファイルの有無、および内容 (たとえば、`-lib` や `-recurse` で指定)。</span><span class="sxs-lookup"><span data-stu-id="e0ca0-126">The existence, non-existence, and contents of files on the compiler's search paths (specified, for example, by `-lib` or `-recurse`).</span></span>
- <span data-ttu-id="e0ca0-127">コンパイラが実行される CLR プラットフォーム。</span><span class="sxs-lookup"><span data-stu-id="e0ca0-127">The CLR platform on which the compiler is run.</span></span>
- <span data-ttu-id="e0ca0-128">`%LIBPATH%` の値。アナライザーの依存関係の読み込みに影響する場合があります。</span><span class="sxs-lookup"><span data-stu-id="e0ca0-128">The value of `%LIBPATH%`, which can affect analyzer dependency loading.</span></span>

<span data-ttu-id="e0ca0-129">ソースを公開用に利用できる場合、バイナリが信頼できる発行元からコンパイルされているかどうかを確立するために、決定論的コンパイルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="e0ca0-129">When sources are publicly available, deterministic compilation can be used for establishing whether a binary is compiled from a trusted source.</span></span> <span data-ttu-id="e0ca0-130">これは、バイナリへの変更に依存しているビルド ステップを実行する必要があるかどうかを決定するために、継続的なビルド システムで役立つ場合もあります。</span><span class="sxs-lookup"><span data-stu-id="e0ca0-130">It can also be useful in a continuous build system for determining whether build steps that are dependent on changes to a binary need to be executed.</span></span>

## <a name="see-also"></a><span data-ttu-id="e0ca0-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="e0ca0-131">See also</span></span>

- [<span data-ttu-id="e0ca0-132">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="e0ca0-132">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="e0ca0-133">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="e0ca0-133">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
