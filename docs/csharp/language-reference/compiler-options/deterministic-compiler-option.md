---
description: -deterministic (C# コンパイラ オプション)
title: -deterministic (C# コンパイラ オプション)
ms.date: 04/12/2018
f1_keywords:
- /deterministic
helpviewer_keywords:
- -deterministic compiler option [C#]
- deterministic compiler option [C#]
- /deterministic compiler option [C#]
ms.openlocfilehash: d64f4d4b0d4e9b5ed2cc1ee40662dc669fc6660d
ms.sourcegitcommit: 4f5f1855849cb02c3b610c7006ac21d7429f3348
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/15/2021
ms.locfileid: "98235327"
---
# <a name="-deterministic"></a><span data-ttu-id="5f1d6-103">-deterministic</span><span class="sxs-lookup"><span data-stu-id="5f1d6-103">-deterministic</span></span>

<span data-ttu-id="5f1d6-104">同一の入力に対して、バイト単位の出力がコンパイル全体で同一のアセンブリをコンパイラに生成させます。</span><span class="sxs-lookup"><span data-stu-id="5f1d6-104">Causes the compiler to produce an assembly whose byte-for-byte output is identical across compilations for identical inputs.</span></span>

## <a name="syntax"></a><span data-ttu-id="5f1d6-105">構文</span><span class="sxs-lookup"><span data-stu-id="5f1d6-105">Syntax</span></span>

```console
-deterministic
```

## <a name="remarks"></a><span data-ttu-id="5f1d6-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="5f1d6-106">Remarks</span></span>

<span data-ttu-id="5f1d6-107">既定では、コンパイラはタイムスタンプと乱数から生成された MVID を追加するため、指定した入力のセットからのコンパイラの出力は固有になります。</span><span class="sxs-lookup"><span data-stu-id="5f1d6-107">By default, compiler output from a given set of inputs is unique, since the compiler adds a timestamp and a MVID that is generated from random numbers.</span></span> <span data-ttu-id="5f1d6-108">`-deterministic` オプションを使用して、*決定論的アセンブリ* を生成します。そのバイナリ コンテンツは、入力が同じである限り、コンパイル全体で同一になります。</span><span class="sxs-lookup"><span data-stu-id="5f1d6-108">You use the `-deterministic` option to produce a *deterministic assembly*, one whose binary content is identical across compilations as long as the input remains the same.</span></span> <span data-ttu-id="5f1d6-109">このようなビルドでは、タイムスタンプおよび MVID フィールドは、すべてのコンパイル入力のハッシュから派生した値に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="5f1d6-109">In such a build, the timestamp and MVID fields will be replaced with values derived from a hash of all the compilation inputs.</span></span>

<span data-ttu-id="5f1d6-110">コンパイラでは決定性のために次の入力が考慮されます。</span><span class="sxs-lookup"><span data-stu-id="5f1d6-110">The compiler considers the following inputs for the purpose of determinism:</span></span>

- <span data-ttu-id="5f1d6-111">コマンド ライン パラメーターのシーケンス。</span><span class="sxs-lookup"><span data-stu-id="5f1d6-111">The sequence of command-line parameters.</span></span>
- <span data-ttu-id="5f1d6-112">コンパイラの .rsp 応答ファイルの内容。</span><span class="sxs-lookup"><span data-stu-id="5f1d6-112">The contents of the compiler's .rsp response file.</span></span>
- <span data-ttu-id="5f1d6-113">使用されるコンパイラの正確なバージョン、およびその参照先のアセンブリ。</span><span class="sxs-lookup"><span data-stu-id="5f1d6-113">The precise version of the compiler used, and its referenced assemblies.</span></span>
- <span data-ttu-id="5f1d6-114">現在のディレクトリ パス。</span><span class="sxs-lookup"><span data-stu-id="5f1d6-114">The current directory path.</span></span>
- <span data-ttu-id="5f1d6-115">すべてのファイルのバイナリ コンテンツは、以下を含めて、直接または間接のいずれかでコンパイラに明示的に渡されます。</span><span class="sxs-lookup"><span data-stu-id="5f1d6-115">The binary contents of all files explicitly passed to the compiler either directly or indirectly, including:</span></span>
  - <span data-ttu-id="5f1d6-116">ソース ファイル</span><span class="sxs-lookup"><span data-stu-id="5f1d6-116">Source files</span></span>
  - <span data-ttu-id="5f1d6-117">参照アセンブリ</span><span class="sxs-lookup"><span data-stu-id="5f1d6-117">Referenced assemblies</span></span>
  - <span data-ttu-id="5f1d6-118">参照モジュール</span><span class="sxs-lookup"><span data-stu-id="5f1d6-118">Referenced modules</span></span>
  - <span data-ttu-id="5f1d6-119">リソース</span><span class="sxs-lookup"><span data-stu-id="5f1d6-119">Resources</span></span>
  - <span data-ttu-id="5f1d6-120">厳密な名前のキー ファイル</span><span class="sxs-lookup"><span data-stu-id="5f1d6-120">The strong name key file</span></span>
  - <span data-ttu-id="5f1d6-121">@ 応答ファイル</span><span class="sxs-lookup"><span data-stu-id="5f1d6-121">@ response files</span></span>
  - <span data-ttu-id="5f1d6-122">アナライザー</span><span class="sxs-lookup"><span data-stu-id="5f1d6-122">Analyzers</span></span>
  - <span data-ttu-id="5f1d6-123">ルールセット</span><span class="sxs-lookup"><span data-stu-id="5f1d6-123">Rulesets</span></span>
  - <span data-ttu-id="5f1d6-124">アナライザーによって使用される可能性がある追加のファイル</span><span class="sxs-lookup"><span data-stu-id="5f1d6-124">Additional files that may be used by analyzers</span></span>
- <span data-ttu-id="5f1d6-125">現在のカルチャ (診断と例外メッセージが生成される言語)。</span><span class="sxs-lookup"><span data-stu-id="5f1d6-125">The current culture (for the language in which diagnostics and exception messages are produced).</span></span>
- <span data-ttu-id="5f1d6-126">エンコードが指定されていない場合の既定のエンコード (または現在のコード ページ)。</span><span class="sxs-lookup"><span data-stu-id="5f1d6-126">The default encoding (or the current code page) if the encoding is not specified.</span></span>
- <span data-ttu-id="5f1d6-127">コンパイラの検索パス上のファイルの有無、および内容 (たとえば、`-lib` や `-recurse` で指定)。</span><span class="sxs-lookup"><span data-stu-id="5f1d6-127">The existence, non-existence, and contents of files on the compiler's search paths (specified, for example, by `-lib` or `-recurse`).</span></span>
- <span data-ttu-id="5f1d6-128">コンパイラが実行される CLR プラットフォーム。</span><span class="sxs-lookup"><span data-stu-id="5f1d6-128">The CLR platform on which the compiler is run.</span></span>
- <span data-ttu-id="5f1d6-129">`%LIBPATH%` の値。アナライザーの依存関係の読み込みに影響する場合があります。</span><span class="sxs-lookup"><span data-stu-id="5f1d6-129">The value of `%LIBPATH%`, which can affect analyzer dependency loading.</span></span>

<span data-ttu-id="5f1d6-130">ソースを公開用に利用できる場合、バイナリが信頼できる発行元からコンパイルされているかどうかを確立するために、決定論的コンパイルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="5f1d6-130">When sources are publicly available, deterministic compilation can be used for establishing whether a binary is compiled from a trusted source.</span></span> <span data-ttu-id="5f1d6-131">これは、バイナリへの変更に依存しているビルド ステップを実行する必要があるかどうかを決定するために、継続的なビルド システムで役立つ場合もあります。</span><span class="sxs-lookup"><span data-stu-id="5f1d6-131">It can also be useful in a continuous build system for determining whether build steps that are dependent on changes to a binary need to be executed.</span></span>

## <a name="see-also"></a><span data-ttu-id="5f1d6-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="5f1d6-132">See also</span></span>

- [<span data-ttu-id="5f1d6-133">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="5f1d6-133">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="5f1d6-134">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="5f1d6-134">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
