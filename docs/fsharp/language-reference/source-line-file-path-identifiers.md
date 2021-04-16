---
title: ソース行、ファイル、およびパスの識別子
description: コード内でソースの行番号、ディレクトリ、ファイル名にアクセスできるようにする F# の組み込み識別子の値の使用方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: f22c3dfb3cb106fbe45883ffd7de01feac30db00
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216751"
---
# <a name="source-line-file-and-path-identifiers"></a><span data-ttu-id="79089-103">ソース行、ファイル、およびパスの識別子</span><span class="sxs-lookup"><span data-stu-id="79089-103">Source Line, File, and Path Identifiers</span></span>

<span data-ttu-id="79089-104">`__LINE__`、`__SOURCE_DIRECTORY__`、`__SOURCE_FILE__` の識別子は、コード内でソースの行番号、ディレクトリ、ファイル名にアクセスできるようにする組み込みの値です。</span><span class="sxs-lookup"><span data-stu-id="79089-104">The identifiers `__LINE__`, `__SOURCE_DIRECTORY__` and `__SOURCE_FILE__` are built-in values that enable you to access the source line number, directory and file name in your code.</span></span>

## <a name="syntax"></a><span data-ttu-id="79089-105">構文</span><span class="sxs-lookup"><span data-stu-id="79089-105">Syntax</span></span>

```fsharp
__LINE__
__SOURCE_DIRECTORY__
__SOURCE_FILE__
```

## <a name="remarks"></a><span data-ttu-id="79089-106">解説</span><span class="sxs-lookup"><span data-stu-id="79089-106">Remarks</span></span>

<span data-ttu-id="79089-107">これらの各値には型 `string` が指定されています。</span><span class="sxs-lookup"><span data-stu-id="79089-107">Each of these values has type `string`.</span></span>

<span data-ttu-id="79089-108">次の表は、F# で使用できるソース行、ファイル、パスの識別子をまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="79089-108">The following table summarizes the source line, file, and path identifiers that are available in F#.</span></span> <span data-ttu-id="79089-109">これらの識別子はプリプロセッサ マクロではなく、コンパイラによって認識される組み込みの値です。</span><span class="sxs-lookup"><span data-stu-id="79089-109">These identifiers are not preprocessor macros; they are built-in values that are recognized by the compiler.</span></span>

|<span data-ttu-id="79089-110">定義済み識別子</span><span class="sxs-lookup"><span data-stu-id="79089-110">Predefined identifier</span></span>|<span data-ttu-id="79089-111">説明</span><span class="sxs-lookup"><span data-stu-id="79089-111">Description</span></span>|
|---------------------|-----------|
|`__LINE__`|<span data-ttu-id="79089-112">`#line` ディレクティブを考慮して、現在の行番号として評価されます。</span><span class="sxs-lookup"><span data-stu-id="79089-112">Evaluates to the current line number, considering `#line` directives.</span></span>|
|`__SOURCE_DIRECTORY__`|<span data-ttu-id="79089-113">`#line` ディレクティブを考慮して、ソース ディレクトリの現在の完全なパスとして評価されます。</span><span class="sxs-lookup"><span data-stu-id="79089-113">Evaluates to the current full path of the source directory, considering `#line` directives.</span></span>|
|`__SOURCE_FILE__`|<span data-ttu-id="79089-114">`#line` ディレクティブを考慮して、パスを除いた現在のソース ファイル名として評価されます。</span><span class="sxs-lookup"><span data-stu-id="79089-114">Evaluates to the current source file name, without its path, considering `#line` directives.</span></span>|

<span data-ttu-id="79089-115">`#line` ディレクティブの詳細については、「[コンパイラ ディレクティブ](compiler-directives.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="79089-115">For more information about the `#line` directive, see [Compiler Directives](compiler-directives.md).</span></span>

## <a name="example"></a><span data-ttu-id="79089-116">例</span><span class="sxs-lookup"><span data-stu-id="79089-116">Example</span></span>

<span data-ttu-id="79089-117">これらの値の使用方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="79089-117">The following code example demonstrates the use of these values.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

<span data-ttu-id="79089-118">出力:</span><span class="sxs-lookup"><span data-stu-id="79089-118">Output:</span></span>

```console
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: Program.fs
```

## <a name="see-also"></a><span data-ttu-id="79089-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="79089-119">See also</span></span>

- [<span data-ttu-id="79089-120">コンパイラ ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="79089-120">Compiler Directives</span></span>](compiler-directives.md)
- [<span data-ttu-id="79089-121">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="79089-121">F# Language Reference</span></span>](index.md)
