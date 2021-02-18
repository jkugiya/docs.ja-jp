---
description: '詳細情報: @ (応答ファイルの指定) (Visual Basic)'
title: '@ (応答ファイルの指定)'
ms.date: 03/13/2018
helpviewer_keywords:
- '@ (Specify Response File) compiler option [Visual Basic]'
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
ms.openlocfilehash: 7a28be0d0bf6da177d9cfe85ecdb40eccf8a339f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100473915"
---
# <a name="-specify-response-file-visual-basic"></a><span data-ttu-id="82df6-103">@ (応答ファイルの指定) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82df6-103">@ (Specify Response File) (Visual Basic)</span></span>

<span data-ttu-id="82df6-104">コンパイラ オプションおよびコンパイルするソース コード ファイルを含むファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="82df6-104">Specifies a file that contains compiler options and source-code files to compile.</span></span>

## <a name="syntax"></a><span data-ttu-id="82df6-105">構文</span><span class="sxs-lookup"><span data-stu-id="82df6-105">Syntax</span></span>

```console
@response_file
```

## <a name="arguments"></a><span data-ttu-id="82df6-106">引数</span><span class="sxs-lookup"><span data-stu-id="82df6-106">Arguments</span></span>

`response_file`  
<span data-ttu-id="82df6-107">必須です。</span><span class="sxs-lookup"><span data-stu-id="82df6-107">Required.</span></span> <span data-ttu-id="82df6-108">コンパイラ オプションやコンパイルするソース コード ファイルの一覧を含むファイルです。</span><span class="sxs-lookup"><span data-stu-id="82df6-108">A file that lists compiler options or source-code files to compile.</span></span> <span data-ttu-id="82df6-109">ファイル名に空白が含まれている場合は、名前を二重引用符 (" ") で囲みます。</span><span class="sxs-lookup"><span data-stu-id="82df6-109">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>

## <a name="remarks"></a><span data-ttu-id="82df6-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="82df6-110">Remarks</span></span>

<span data-ttu-id="82df6-111">コンパイラでは、応答ファイルで指定されたコンパイラ オプションとソースコード ファイルが、コマンド ラインで指定した場合と同じように処理されます。</span><span class="sxs-lookup"><span data-stu-id="82df6-111">The compiler processes the compiler options and source-code files specified in a response file as if they had been specified on the command line.</span></span>

<span data-ttu-id="82df6-112">コンパイル時に複数の応答ファイルを指定するには、次のように複数の応答ファイル オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="82df6-112">To specify more than one response file in a compilation, specify multiple response-file options, such as the following.</span></span>

```console
@file1.rsp @file2.rsp
```

<span data-ttu-id="82df6-113">応答ファイルでは、複数のコンパイラ オプションとソース コード ファイルを 1 行に表示されます。</span><span class="sxs-lookup"><span data-stu-id="82df6-113">In a response file, multiple compiler options and source-code files can appear on one line.</span></span> <span data-ttu-id="82df6-114">1 つのコンパイラ オプションは 1 行に表示される必要があります (複数行にまたがることはできません)。</span><span class="sxs-lookup"><span data-stu-id="82df6-114">A single compiler-option specification must appear on one line (cannot span multiple lines).</span></span> <span data-ttu-id="82df6-115">応答ファイルには、`#` 記号で始まるコメントを記述できます。</span><span class="sxs-lookup"><span data-stu-id="82df6-115">Response files can have comments that begin with the `#` symbol.</span></span>

<span data-ttu-id="82df6-116">コマンド ラインで指定されたオプションと、1 つ以上の応答ファイルで指定されたオプションを組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="82df6-116">You can combine options specified on the command line with options specified in one or more response files.</span></span> <span data-ttu-id="82df6-117">コンパイラでは、検出した順にコマンド オプションが処理されます。</span><span class="sxs-lookup"><span data-stu-id="82df6-117">The compiler processes the command options as it encounters them.</span></span> <span data-ttu-id="82df6-118">このため、コマンド ライン引数によって、応答ファイルで先に指定したオプションをオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="82df6-118">Therefore, command-line arguments can override previously listed options in response files.</span></span> <span data-ttu-id="82df6-119">反対に、応答ファイルのオプションにより、コマンド ラインや他の応答ファイルで先に指定したオプションがオーバーライドされることもあります。</span><span class="sxs-lookup"><span data-stu-id="82df6-119">Conversely, options in a response file override options listed previously on the command line or in other response files.</span></span>

<span data-ttu-id="82df6-120">Visual Basic では、Vbc.exe ファイルと同じディレクトリに Vbc.rsp ファイルが提供されます。</span><span class="sxs-lookup"><span data-stu-id="82df6-120">Visual Basic provides the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="82df6-121">`-noconfig` オプションを使用しない限り、Vbc.rsp ファイルは既定で含まれます。</span><span class="sxs-lookup"><span data-stu-id="82df6-121">The Vbc.rsp file is included by default unless the `-noconfig` option is used.</span></span> <span data-ttu-id="82df6-122">詳細については、「[-noconfig](noconfig.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="82df6-122">For more information, see [-noconfig](noconfig.md).</span></span>

> [!NOTE]
> <span data-ttu-id="82df6-123">`@` オプションは、Visual Studio 開発環境からは利用できません。これはコマンド ラインからコンパイルするときにのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="82df6-123">The `@` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="82df6-124">例</span><span class="sxs-lookup"><span data-stu-id="82df6-124">Example</span></span>

<span data-ttu-id="82df6-125">次の行は、サンプルの応答ファイルの一部です。</span><span class="sxs-lookup"><span data-stu-id="82df6-125">The following lines are from a sample response file.</span></span>

```console
# build the first output file
-target:exe
-out:MyExe.exe
source1.vb
source2.vb
```

## <a name="example"></a><span data-ttu-id="82df6-126">例</span><span class="sxs-lookup"><span data-stu-id="82df6-126">Example</span></span>

<span data-ttu-id="82df6-127">次の例では、`@` オプションを `File1.rsp` という名前の応答ファイルと共に使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="82df6-127">The following example demonstrates how to use the `@` option with the response file named `File1.rsp`.</span></span>

```console
vbc @file1.rsp
```

## <a name="see-also"></a><span data-ttu-id="82df6-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="82df6-128">See also</span></span>

- [<span data-ttu-id="82df6-129">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="82df6-129">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="82df6-130">-noconfig</span><span class="sxs-lookup"><span data-stu-id="82df6-130">-noconfig</span></span>](noconfig.md)
- [<span data-ttu-id="82df6-131">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="82df6-131">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
