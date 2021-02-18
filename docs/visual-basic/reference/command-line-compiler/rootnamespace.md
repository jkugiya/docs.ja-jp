---
description: '詳細情報: -rootnamespace'
title: -rootnamespace
ms.date: 03/13/2018
f1_keywords:
- /rootnamespace
- rootnamespace
helpviewer_keywords:
- /rootnamespace compiler option [Visual Basic]
- -rootnamespace compiler option [Visual Basic]
- rootnamespace compiler option [Visual Basic]
ms.assetid: e9245edf-6bef-420d-a7c7-324117752783
ms.openlocfilehash: 0e034999a65bf5294e63c8f9cec1a4ce4de39a4b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100474084"
---
# <a name="-rootnamespace"></a><span data-ttu-id="51682-103">-rootnamespace</span><span class="sxs-lookup"><span data-stu-id="51682-103">-rootnamespace</span></span>

<span data-ttu-id="51682-104">すべての型宣言に対して名前空間を指定します。</span><span class="sxs-lookup"><span data-stu-id="51682-104">Specifies a namespace for all type declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51682-105">構文</span><span class="sxs-lookup"><span data-stu-id="51682-105">Syntax</span></span>  
  
```console  
-rootnamespace:namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="51682-106">引数</span><span class="sxs-lookup"><span data-stu-id="51682-106">Arguments</span></span>  
  
|<span data-ttu-id="51682-107">用語</span><span class="sxs-lookup"><span data-stu-id="51682-107">Term</span></span>|<span data-ttu-id="51682-108">定義</span><span class="sxs-lookup"><span data-stu-id="51682-108">Definition</span></span>|  
|---|---|  
|`namespace`|<span data-ttu-id="51682-109">現在のプロジェクトのすべての型宣言を囲む名前空間の名前。</span><span class="sxs-lookup"><span data-stu-id="51682-109">The name of the namespace in which to enclose all type declarations for the current project.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51682-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="51682-110">Remarks</span></span>  

 <span data-ttu-id="51682-111">Visual Studio 統合開発環境で作成したプロジェクトをコンパイルするのに Visual studio の実行可能ファイル (Devenv.exe) を使用する場合は、`-rootnamespace` を使用して <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> プロパティの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="51682-111">If you use the Visual Studio executable file (Devenv.exe) to compile a project created in the Visual Studio integrated development environment, use `-rootnamespace` to specify the value of the <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> property.</span></span> <span data-ttu-id="51682-112">詳細については、「[Devenv コマンド ライン スイッチ](/visualstudio/ide/reference/devenv-command-line-switches)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="51682-112">See [Devenv Command Line Switches](/visualstudio/ide/reference/devenv-command-line-switches) for more information.</span></span>  
  
 <span data-ttu-id="51682-113">共通言語ランタイムの MSIL 逆アセンブラー (`Ildasm.exe`) を使用して、出力ファイル内に名前空間の名前を示します。</span><span class="sxs-lookup"><span data-stu-id="51682-113">Use the common language runtime MSIL Disassembler (`Ildasm.exe`) to view the namespace names in your output file.</span></span>  
  
|<span data-ttu-id="51682-114">Visual Studio 統合開発環境で -rootnamespace を設定するには</span><span class="sxs-lookup"><span data-stu-id="51682-114">To set -rootnamespace in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="51682-115">1.**ソリューション エクスプローラー** でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="51682-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="51682-116">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="51682-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="51682-117">2. **[アプリケーション]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="51682-117">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="51682-118">3. **[ルート名前空間]** ボックス内の値を変更します。</span><span class="sxs-lookup"><span data-stu-id="51682-118">3.  Modify the value in the **Root Namespace** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="51682-119">例</span><span class="sxs-lookup"><span data-stu-id="51682-119">Example</span></span>  

 <span data-ttu-id="51682-120">次のコードでは、`In.vb` がコンパイルされ、すべての型宣言が名前空間 `mynamespace` で囲まれます。</span><span class="sxs-lookup"><span data-stu-id="51682-120">The following code compiles `In.vb` and encloses all type declarations in the namespace `mynamespace`.</span></span>  
  
```console
vbc -rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="51682-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="51682-121">See also</span></span>

- [<span data-ttu-id="51682-122">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="51682-122">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="51682-123">Ildasm.exe (IL 逆アセンブラー)</span><span class="sxs-lookup"><span data-stu-id="51682-123">Ildasm.exe (IL Disassembler)</span></span>](../../../framework/tools/ildasm-exe-il-disassembler.md)
- [<span data-ttu-id="51682-124">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="51682-124">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
