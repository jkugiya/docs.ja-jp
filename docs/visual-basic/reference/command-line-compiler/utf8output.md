---
description: '詳細情報: -utf8output (Visual Basic)'
title: -utf8output
ms.date: 07/20/2015
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
ms.openlocfilehash: 317c1be3f18150ae88bb8e95927d9f5faf0e4f3c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100461893"
---
# <a name="-utf8output-visual-basic"></a><span data-ttu-id="a6ec9-103">-utf8output (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a6ec9-103">-utf8output (Visual Basic)</span></span>

<span data-ttu-id="a6ec9-104">UTF-8 エンコードを使用してコンパイラ出力を表示します。</span><span class="sxs-lookup"><span data-stu-id="a6ec9-104">Displays compiler output using UTF-8 encoding.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6ec9-105">構文</span><span class="sxs-lookup"><span data-stu-id="a6ec9-105">Syntax</span></span>  
  
```console  
-utf8output[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="a6ec9-106">引数</span><span class="sxs-lookup"><span data-stu-id="a6ec9-106">Arguments</span></span>  

 <span data-ttu-id="a6ec9-107">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="a6ec9-107">`+` &#124; `-`</span></span>  
 <span data-ttu-id="a6ec9-108">任意。</span><span class="sxs-lookup"><span data-stu-id="a6ec9-108">Optional.</span></span> <span data-ttu-id="a6ec9-109">このオプションの既定値は `-utf8output-` です。これは、コンパイラ出力で UTF-8 エンコードが使用されないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="a6ec9-109">The default for this option is `-utf8output-`, which means compiler output does not use UTF-8 encoding.</span></span> <span data-ttu-id="a6ec9-110">`-utf8output` を指定することは、`-utf8output+` を指定することと同じです。</span><span class="sxs-lookup"><span data-stu-id="a6ec9-110">Specifying `-utf8output` is the same as specifying `-utf8output+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6ec9-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="a6ec9-111">Remarks</span></span>  

 <span data-ttu-id="a6ec9-112">地域と言語の構成によっては、コンパイラ出力をコンソールに正しく表示できない場合があります。</span><span class="sxs-lookup"><span data-stu-id="a6ec9-112">In some international configurations, compiler output cannot be displayed correctly in the console.</span></span> <span data-ttu-id="a6ec9-113">このような場合は、`-utf8output` を使用して、コンパイラ出力をファイルにリダイレクトします。</span><span class="sxs-lookup"><span data-stu-id="a6ec9-113">In such situations, use `-utf8output` and redirect compiler output to a file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a6ec9-114">`-utf8output` オプションは、Visual Studio 開発環境内からは利用できません。これはコマンド ラインからコンパイルするときにのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="a6ec9-114">The `-utf8output` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6ec9-115">例</span><span class="sxs-lookup"><span data-stu-id="a6ec9-115">Example</span></span>  

 <span data-ttu-id="a6ec9-116">次のコードでは `In.vb` をコンパイルし、UTF-8 エンコードを使用して出力を表示するようにコンパイラに指示します。</span><span class="sxs-lookup"><span data-stu-id="a6ec9-116">The following code compiles `In.vb` and directs the compiler to display output using UTF-8 encoding.</span></span>  
  
```console  
vbc -utf8output in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="a6ec9-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="a6ec9-117">See also</span></span>

- [<span data-ttu-id="a6ec9-118">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="a6ec9-118">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="a6ec9-119">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="a6ec9-119">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
