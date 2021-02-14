---
description: '詳細情報: #ExternalSource ディレクティブ'
title: '#ExternalSource ディレクティブ'
ms.date: 07/20/2015
f1_keywords:
- '#Externalsource'
- '#ExternalSource'
- vb.ExternalSource
- Externalsource
- vb.#ExternalSource
- ExternalSource
helpviewer_keywords:
- ExternalSource directive (#ExternalSource)
- '#ExternalSource directive'
ms.assetid: 243bc6a2-34c3-4eeb-a776-9fd2bf988149
ms.openlocfilehash: 1f2e73aa152fbe2d97edcde912626696faacd5af
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797238"
---
# <a name="externalsource-directive"></a><span data-ttu-id="3d4ed-103">#ExternalSource ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="3d4ed-103">#ExternalSource Directive</span></span>

<span data-ttu-id="3d4ed-104">ソース コードの特定の行と、ソースの外部のテキストとの間のマッピングを示します。</span><span class="sxs-lookup"><span data-stu-id="3d4ed-104">Indicates a mapping between specific lines of source code and text external to the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d4ed-105">構文</span><span class="sxs-lookup"><span data-stu-id="3d4ed-105">Syntax</span></span>  
  
```vb  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a><span data-ttu-id="3d4ed-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="3d4ed-106">Parts</span></span>  

 `StringLiteral`  
 <span data-ttu-id="3d4ed-107">外部ソースへのパスです。</span><span class="sxs-lookup"><span data-stu-id="3d4ed-107">The path to the external source.</span></span>  
  
 `IntLiteral`  
 <span data-ttu-id="3d4ed-108">外部ソースの最初の行の行番号です。</span><span class="sxs-lookup"><span data-stu-id="3d4ed-108">The line number of the first line of the external source.</span></span>  
  
 `LogicalLine`  
 <span data-ttu-id="3d4ed-109">外部ソースでエラーが発生した行です。</span><span class="sxs-lookup"><span data-stu-id="3d4ed-109">The line where the error occurs in the external source.</span></span>  
  
 `#End ExternalSource`  
 <span data-ttu-id="3d4ed-110">`#ExternalSource` ブロックを終了します。</span><span class="sxs-lookup"><span data-stu-id="3d4ed-110">Terminates the `#ExternalSource` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d4ed-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="3d4ed-111">Remarks</span></span>  

 <span data-ttu-id="3d4ed-112">このディレクティブは、コンパイラとデバッガーによってのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="3d4ed-112">This directive is used only by the compiler and the debugger.</span></span>  
  
 <span data-ttu-id="3d4ed-113">ソース ファイルには、外部ソース ディレクティブを含めることができます。これは、ソース ファイル内の特定のコード行と、.aspx ファイルなどのソースの外部のテキストとの間のマッピングを示します。</span><span class="sxs-lookup"><span data-stu-id="3d4ed-113">A source file may include external source directives, which indicate a mapping between specific lines of code in the source file and text external to the source, such as an .aspx file.</span></span> <span data-ttu-id="3d4ed-114">コンパイル時に指定されたソース コードでエラーが発生した場合、外部ソースからのものとして識別されます。</span><span class="sxs-lookup"><span data-stu-id="3d4ed-114">If errors are encountered in the designated source code during compilation, they are identified as coming from the external source.</span></span>  
  
 <span data-ttu-id="3d4ed-115">外部ソース ディレクティブはコンパイルには影響しません。また、入れ子にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="3d4ed-115">External source directives have no effect on compilation and cannot be nested.</span></span> <span data-ttu-id="3d4ed-116">これらはアプリケーションによる内部使用のみを目的としています。</span><span class="sxs-lookup"><span data-stu-id="3d4ed-116">They are intended for internal use by the application only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d4ed-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="3d4ed-117">See also</span></span>

- [<span data-ttu-id="3d4ed-118">条件付きコンパイル</span><span class="sxs-lookup"><span data-stu-id="3d4ed-118">Conditional Compilation</span></span>](../../programming-guide/program-structure/conditional-compilation.md)
