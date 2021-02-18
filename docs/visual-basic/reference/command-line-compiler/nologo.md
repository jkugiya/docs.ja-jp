---
description: '詳細情報: -nologo (Visual Basic)'
title: -nologo
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: 370889fbd5d4e499ba27ff8bee4adc16a7a71876
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100434889"
---
# <a name="-nologo-visual-basic"></a><span data-ttu-id="11bf1-103">-nologo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11bf1-103">-nologo (Visual Basic)</span></span>

<span data-ttu-id="11bf1-104">コンパイル中に著作権情報のバナーおよび情報メッセージが表示されません。</span><span class="sxs-lookup"><span data-stu-id="11bf1-104">Suppresses display of the copyright banner and informational messages during compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11bf1-105">構文</span><span class="sxs-lookup"><span data-stu-id="11bf1-105">Syntax</span></span>  
  
```console  
-nologo  
```  
  
## <a name="remarks"></a><span data-ttu-id="11bf1-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="11bf1-106">Remarks</span></span>  

 <span data-ttu-id="11bf1-107">`-nologo` を指定すると、コンパイラで著作権情報のバナーが表示されません。</span><span class="sxs-lookup"><span data-stu-id="11bf1-107">If you specify `-nologo`, the compiler does not display a copyright banner.</span></span> <span data-ttu-id="11bf1-108">既定では、`-nologo` は無効です。</span><span class="sxs-lookup"><span data-stu-id="11bf1-108">By default, `-nologo` is not in effect.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="11bf1-109">`-nologo` オプションは、Visual Studio 開発環境からは利用できません。これはコマンド ラインからコンパイルするときにのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="11bf1-109">The `-nologo` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11bf1-110">例</span><span class="sxs-lookup"><span data-stu-id="11bf1-110">Example</span></span>  

 <span data-ttu-id="11bf1-111">次のコードでは `T2.vb` がコンパイルされ、著作権のバナーは表示されません。</span><span class="sxs-lookup"><span data-stu-id="11bf1-111">The following code compiles `T2.vb` and does not display a copyright banner.</span></span>  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="11bf1-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="11bf1-112">See also</span></span>

- [<span data-ttu-id="11bf1-113">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="11bf1-113">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="11bf1-114">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="11bf1-114">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
