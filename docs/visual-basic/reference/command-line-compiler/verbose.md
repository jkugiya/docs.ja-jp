---
description: '詳細情報: -verbose'
title: -verbose
ms.date: 03/13/2018
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
ms.openlocfilehash: ea222d4f284bcaf163b142269fe250a081b0ee4f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100470137"
---
# <a name="-verbose"></a><span data-ttu-id="f9ab3-103">-verbose</span><span class="sxs-lookup"><span data-stu-id="f9ab3-103">-verbose</span></span>

<span data-ttu-id="f9ab3-104">コンパイラによって詳細なステータス メッセージとエラー メッセージが生成されるようにします。</span><span class="sxs-lookup"><span data-stu-id="f9ab3-104">Causes the compiler to produce verbose status and error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9ab3-105">構文</span><span class="sxs-lookup"><span data-stu-id="f9ab3-105">Syntax</span></span>  
  
```console  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="f9ab3-106">引数</span><span class="sxs-lookup"><span data-stu-id="f9ab3-106">Arguments</span></span>  

 <span data-ttu-id="f9ab3-107">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="f9ab3-107">`+` &#124; `-`</span></span>  
 <span data-ttu-id="f9ab3-108">任意。</span><span class="sxs-lookup"><span data-stu-id="f9ab3-108">Optional.</span></span> <span data-ttu-id="f9ab3-109">`-verbose` を指定することは、`-verbose+` を指定することと同じです。これにより、コンパイラで詳細なメッセージが出力されます。</span><span class="sxs-lookup"><span data-stu-id="f9ab3-109">Specifying `-verbose` is the same as specifying `-verbose+`, which causes the compiler to emit verbose messages.</span></span> <span data-ttu-id="f9ab3-110">このオプションの既定値は `-verbose-` です。</span><span class="sxs-lookup"><span data-stu-id="f9ab3-110">The default for this option is `-verbose-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9ab3-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="f9ab3-111">Remarks</span></span>  

 <span data-ttu-id="f9ab3-112">`-verbose` オプションでは、コンパイラによって発行されたエラーの合計数に関する情報を表示し、どのアセンブリがモジュールに読み込まれているかを報告します。また、どのファイルが現在コンパイルされているかを表示します。</span><span class="sxs-lookup"><span data-stu-id="f9ab3-112">The `-verbose` option displays information about the total number of errors issued by the compiler, reports which assemblies are being loaded by a module, and displays which files are currently being compiled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f9ab3-113">`-verbose` オプションは、Visual Studio 開発環境からは利用できません。これはコマンド ラインからコンパイルするときにのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="f9ab3-113">The `-verbose` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9ab3-114">例</span><span class="sxs-lookup"><span data-stu-id="f9ab3-114">Example</span></span>  

 <span data-ttu-id="f9ab3-115">次のコードでは `In.vb` がコンパイルされ、詳細情報を表示するようにコンパイラに指示されます。</span><span class="sxs-lookup"><span data-stu-id="f9ab3-115">The following code compiles `In.vb` and directs the compiler to display verbose status information.</span></span>  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="f9ab3-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="f9ab3-116">See also</span></span>

- [<span data-ttu-id="f9ab3-117">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="f9ab3-117">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="f9ab3-118">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="f9ab3-118">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
