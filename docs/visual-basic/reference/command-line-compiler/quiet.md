---
description: '詳細情報: -quiet'
title: -quiet
ms.date: 07/20/2015
f1_keywords:
- -quiet
- quiet
helpviewer_keywords:
- -quiet compiler option [Visual Basic]
- /quiet compiler option [Visual Basic]
- quiet compiler option [Visual Basic]
ms.assetid: 5d77fa23-4c50-4708-8535-649912b098e8
ms.openlocfilehash: 23e1b6472e80ac6ca2ecea5c4390b43722ccebb6
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100432729"
---
# <a name="-quiet"></a><span data-ttu-id="2eb5a-103">-quiet</span><span class="sxs-lookup"><span data-stu-id="2eb5a-103">-quiet</span></span>

<span data-ttu-id="2eb5a-104">コンパイラで構文関連のエラーと警告のコードが表示されないようにします。</span><span class="sxs-lookup"><span data-stu-id="2eb5a-104">Prevents the compiler from displaying code for syntax-related errors and warnings.</span></span>

## <a name="syntax"></a><span data-ttu-id="2eb5a-105">構文</span><span class="sxs-lookup"><span data-stu-id="2eb5a-105">Syntax</span></span>

```console
-quiet
```

## <a name="remarks"></a><span data-ttu-id="2eb5a-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="2eb5a-106">Remarks</span></span>

<span data-ttu-id="2eb5a-107">既定では、`-quiet` は無効です。</span><span class="sxs-lookup"><span data-stu-id="2eb5a-107">By default, `-quiet` is not in effect.</span></span> <span data-ttu-id="2eb5a-108">コンパイラで構文に関連するエラーまたは警告が報告されるときに、ソース コードの行も出力されます。</span><span class="sxs-lookup"><span data-stu-id="2eb5a-108">When the compiler reports a syntax-related error or warning, it also outputs the line from source code.</span></span> <span data-ttu-id="2eb5a-109">コンパイラの出力を解析するアプリケーションでは、コンパイラで診断テキストのみが出力される方が便利な場合があります。</span><span class="sxs-lookup"><span data-stu-id="2eb5a-109">For applications that parse compiler output, it may be more convenient for the compiler to output only the text of the diagnostic.</span></span>

<span data-ttu-id="2eb5a-110">次の例の `Module1` では、`-quiet` を使用せずにコンパイルされた場合に、ソース コードを含むエラーが出力されます。</span><span class="sxs-lookup"><span data-stu-id="2eb5a-110">In the following example, `Module1` outputs an error that includes source code when compiled without `-quiet`.</span></span>

```vb
Module Module1
    Sub Main()
        x()
    End Sub
End Module
```

<span data-ttu-id="2eb5a-111">Output:</span><span class="sxs-lookup"><span data-stu-id="2eb5a-111">Output:</span></span>

```console
C:\projects\vb2.vb(3) : error BC30451: 'x' is not declared. It may be inaccessible due to its protection level.

        x()
        ~
```

<span data-ttu-id="2eb5a-112">`-quiet` を使用してコンパイルすると、コンパイラからは次のものだけが出力されます。</span><span class="sxs-lookup"><span data-stu-id="2eb5a-112">Compiled with `-quiet`, the compiler outputs only the following:</span></span>

```console
E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.
```

> [!NOTE]
> <span data-ttu-id="2eb5a-113">`-quiet` オプションは、Visual Studio 開発環境からは利用できません。これはコマンド ラインからコンパイルするときにのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="2eb5a-113">The `-quiet` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="2eb5a-114">例</span><span class="sxs-lookup"><span data-stu-id="2eb5a-114">Example</span></span>

<span data-ttu-id="2eb5a-115">次のコードでは `T2.vb` がコンパイルされ、構文に関連するコンパイラ診断のコードが表示されません。</span><span class="sxs-lookup"><span data-stu-id="2eb5a-115">The following code compiles `T2.vb` and does not display code for syntax-related compiler diagnostics:</span></span>

```console
vbc -quiet t2.vb
```

## <a name="see-also"></a><span data-ttu-id="2eb5a-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="2eb5a-116">See also</span></span>

- [<span data-ttu-id="2eb5a-117">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="2eb5a-117">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="2eb5a-118">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="2eb5a-118">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
