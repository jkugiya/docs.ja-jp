---
description: '詳細情報: -noconfig'
title: -noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: e97d44427b537e73a404a47d30db202e2c3b1f41
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100481689"
---
# <a name="-noconfig"></a><span data-ttu-id="a73de-103">-noconfig</span><span class="sxs-lookup"><span data-stu-id="a73de-103">-noconfig</span></span>

<span data-ttu-id="a73de-104">コンパイラにより、一般的に使用される .NET Framework アセンブリが自動的に参照されたり、`System` と `Microsoft.VisualBasic` 名前空間がインポートされたりしないように指定します。</span><span class="sxs-lookup"><span data-stu-id="a73de-104">Specifies that the compiler should not automatically reference the commonly used .NET Framework assemblies or import the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a73de-105">構文</span><span class="sxs-lookup"><span data-stu-id="a73de-105">Syntax</span></span>  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="a73de-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="a73de-106">Remarks</span></span>  

 <span data-ttu-id="a73de-107">`-noconfig` オプションでは、Vbc.exe ファイルと同じディレクトリにある Vbc.rsp ファイルを使用してコンパイルが実行されないように、コンパイラに指定できます。</span><span class="sxs-lookup"><span data-stu-id="a73de-107">The `-noconfig` option tells the compiler not to compile with the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="a73de-108">Vbc.rsp ファイルは、一般的に使用される .NET Framework アセンブリを参照し、`System` と `Microsoft.VisualBasic` の名前空間をインポートします。</span><span class="sxs-lookup"><span data-stu-id="a73de-108">The Vbc.rsp file references the commonly used .NET Framework assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span> <span data-ttu-id="a73de-109">コンパイラでは、`-nostdlib` オプションを指定しない限り、System.dll アセンブリが暗黙的に参照されます。</span><span class="sxs-lookup"><span data-stu-id="a73de-109">The compiler implicitly references the System.dll assembly unless the `-nostdlib` option is specified.</span></span> <span data-ttu-id="a73de-110">`-nostdlib` オプションでは、Vbc.rsp を使用してコンパイルされないように、または自動的に System.dll アセンブリが参照されないように、コンパイラに指定できます。</span><span class="sxs-lookup"><span data-stu-id="a73de-110">The `-nostdlib` option tells the compiler not to compile with Vbc.rsp or automatically reference the System.dll assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a73de-111">Mscorlib.dll アセンブリおよび Microsoft.VisualBasic.dll アセンブリは常に参照されます。</span><span class="sxs-lookup"><span data-stu-id="a73de-111">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
 <span data-ttu-id="a73de-112">Vbc.rsp ファイルを変更すると、(`-noconfig` オプションを指定した場合を除き) Vbc.exe のすべてのコンパイルに含めるコンパイラ オプションを追加指定できます。</span><span class="sxs-lookup"><span data-stu-id="a73de-112">You can modify the Vbc.rsp file to specify additional compiler options that should be included in every Vbc.exe compilation (except when specifying the `-noconfig` option).</span></span> <span data-ttu-id="a73de-113">詳しくは、「[@ (応答ファイルの指定)](specify-response-file.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a73de-113">For more information, see [@ (Specify Response File)](specify-response-file.md).</span></span>  
  
 <span data-ttu-id="a73de-114">コンパイラでは、`vbc` コマンドに渡されるオプションが最後に処理されます。</span><span class="sxs-lookup"><span data-stu-id="a73de-114">The compiler processes the options passed to the `vbc` command last.</span></span> <span data-ttu-id="a73de-115">そのため、コマンド ラインでオプションが指定されている場合、Vbc.rsp ファイル内の同じオプション設定がオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="a73de-115">Therefore, any option on the command line overrides the setting of the same option in the Vbc.rsp file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a73de-116">`-noconfig` オプションは、Visual Studio 開発環境からは利用できません。これはコマンド ラインからコンパイルするときにのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="a73de-116">The `-noconfig` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a73de-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="a73de-117">See also</span></span>

- [<span data-ttu-id="a73de-118">-nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a73de-118">-nostdlib (Visual Basic)</span></span>](nostdlib.md)
- [<span data-ttu-id="a73de-119">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="a73de-119">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="a73de-120">@ (応答ファイルの指定)</span><span class="sxs-lookup"><span data-stu-id="a73de-120">@ (Specify Response File)</span></span>](specify-response-file.md)
- [<span data-ttu-id="a73de-121">-reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a73de-121">-reference (Visual Basic)</span></span>](reference.md)
