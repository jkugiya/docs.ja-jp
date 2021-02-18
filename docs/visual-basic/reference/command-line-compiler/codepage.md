---
description: '詳細情報: -codepage (Visual Basic)'
title: -codepage
ms.date: 03/09/2018
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
ms.openlocfilehash: 8bc68263bda298787a48dc06729ea17c5adfcfa5
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100468279"
---
# <a name="-codepage-visual-basic"></a><span data-ttu-id="b857c-103">-codepage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b857c-103">-codepage (Visual Basic)</span></span>

<span data-ttu-id="b857c-104">コンパイルですべてのソース コード ファイルに使用するコード ページを指定します。</span><span class="sxs-lookup"><span data-stu-id="b857c-104">Specifies the code page to use for all source-code files in the compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b857c-105">構文</span><span class="sxs-lookup"><span data-stu-id="b857c-105">Syntax</span></span>  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="b857c-106">引数</span><span class="sxs-lookup"><span data-stu-id="b857c-106">Arguments</span></span>  
  
|<span data-ttu-id="b857c-107">用語</span><span class="sxs-lookup"><span data-stu-id="b857c-107">Term</span></span>|<span data-ttu-id="b857c-108">定義</span><span class="sxs-lookup"><span data-stu-id="b857c-108">Definition</span></span>|  
|---|---|  
|`id`|<span data-ttu-id="b857c-109">必須です。</span><span class="sxs-lookup"><span data-stu-id="b857c-109">Required.</span></span> <span data-ttu-id="b857c-110">コンパイラは、`id` で指定されたコード ページを使用して、ソース ファイルのエンコードを解釈します。</span><span class="sxs-lookup"><span data-stu-id="b857c-110">The compiler uses the code page specified by `id` to interpret the encoding of the source files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b857c-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="b857c-111">Remarks</span></span>  

 <span data-ttu-id="b857c-112">特定のエンコードを使用して保存されたソース コードをコンパイルするには、`-codepage` を使用して、使用するコード ページを指定します。</span><span class="sxs-lookup"><span data-stu-id="b857c-112">To compile source code saved with a specific encoding, you can use `-codepage` to specify which code page should be used.</span></span> <span data-ttu-id="b857c-113">`-codepage` オプションは、コンパイル時にすべてのソース コード ファイルに適用されます。</span><span class="sxs-lookup"><span data-stu-id="b857c-113">The `-codepage` option applies to all source-code files in your compilation.</span></span> <span data-ttu-id="b857c-114">詳細については、[.NET Framework での文字エンコード](../../../standard/base-types/character-encoding.md)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b857c-114">For more information, see [Character Encoding in the .NET Framework](../../../standard/base-types/character-encoding.md).</span></span>  
  
 <span data-ttu-id="b857c-115">ソース コード ファイルが現在の ANSI コード ページ、Unicode、または UTF-8 を使用して保存されている場合、`-codepage` オプションは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="b857c-115">The `-codepage` option is not needed if the source-code files were saved using the current ANSI code page, Unicode, or UTF-8 with a signature.</span></span> <span data-ttu-id="b857c-116">Visual Studio では、ユーザーが **[エンコード]** ダイアログ ボックスで別のエンコードを指定しない限り、既定ですべてのソース コード ファイルが現在の ANSI コード ページで保存されます。</span><span class="sxs-lookup"><span data-stu-id="b857c-116">Visual Studio saves all source-code files with the current ANSI code page by default, unless the user specifies another encoding in the **Encoding** dialog box.</span></span> <span data-ttu-id="b857c-117">Visual Studio では、 **[エンコード]** ダイアログ ボックスを使用して、別のコード ページで保存されたソースコード ファイルが開かれます。</span><span class="sxs-lookup"><span data-stu-id="b857c-117">Visual Studio uses the **Encoding** dialog box to open source-code files saved with a different code page.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b857c-118">`-codepage` オプションは、Visual Studio 開発環境からは利用できません。これはコマンド ラインからコンパイルするときにのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="b857c-118">The `-codepage` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b857c-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="b857c-119">See also</span></span>

- [<span data-ttu-id="b857c-120">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="b857c-120">Visual Basic Command-Line Compiler</span></span>](index.md)
