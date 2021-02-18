---
description: '詳細情報: -nowarn'
title: -nowarn
ms.date: 07/20/2015
helpviewer_keywords:
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
ms.openlocfilehash: 4fb7d39aef48ff1443c342367f9e20bb37f9c5e0
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100434863"
---
# <a name="-nowarn"></a><span data-ttu-id="c3680-103">-nowarn</span><span class="sxs-lookup"><span data-stu-id="c3680-103">-nowarn</span></span>

<span data-ttu-id="c3680-104">警告を生成するコンパイラの機能を無効にします。</span><span class="sxs-lookup"><span data-stu-id="c3680-104">Suppresses the compiler's ability to generate warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3680-105">構文</span><span class="sxs-lookup"><span data-stu-id="c3680-105">Syntax</span></span>  
  
```console  
-nowarn[:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="c3680-106">引数</span><span class="sxs-lookup"><span data-stu-id="c3680-106">Arguments</span></span>  
  
|<span data-ttu-id="c3680-107">用語</span><span class="sxs-lookup"><span data-stu-id="c3680-107">Term</span></span>|<span data-ttu-id="c3680-108">定義</span><span class="sxs-lookup"><span data-stu-id="c3680-108">Definition</span></span>|  
|---|---|  
|`numberList`|<span data-ttu-id="c3680-109">任意。</span><span class="sxs-lookup"><span data-stu-id="c3680-109">Optional.</span></span> <span data-ttu-id="c3680-110">コンパイラにより非表示にされるべき警告 ID 番号のコンマ区切りの一覧。</span><span class="sxs-lookup"><span data-stu-id="c3680-110">Comma-delimited list of the warning ID numbers that the compiler should suppress.</span></span> <span data-ttu-id="c3680-111">警告 ID が指定されていない場合、すべての警告は非表示になります。</span><span class="sxs-lookup"><span data-stu-id="c3680-111">If the warning IDs are not specified, all warnings are suppressed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3680-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="c3680-112">Remarks</span></span>  

 <span data-ttu-id="c3680-113">`-nowarn` オプションを指定すると、コンパイラにより警告が生成されなくなります。</span><span class="sxs-lookup"><span data-stu-id="c3680-113">The `-nowarn` option causes the compiler to not generate warnings.</span></span> <span data-ttu-id="c3680-114">個々の警告を非表示にするには、`-nowarn` オプションの後にコロンを追加し、警告 ID を指定します。</span><span class="sxs-lookup"><span data-stu-id="c3680-114">To suppress an individual warning, supply the warning ID to the `-nowarn` option following the colon.</span></span> <span data-ttu-id="c3680-115">警告が複数ある場合は、番号をコンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="c3680-115">Separate multiple warning numbers with commas.</span></span>  
  
 <span data-ttu-id="c3680-116">警告 ID は、数値部分のみを指定します。</span><span class="sxs-lookup"><span data-stu-id="c3680-116">You need to specify only the numeric part of the warning identifier.</span></span> <span data-ttu-id="c3680-117">たとえば、BC42024 を非表示にする場合は、使用されていないローカル変数の警告に、`-nowarn:42024` を指定します。</span><span class="sxs-lookup"><span data-stu-id="c3680-117">For example, if you want to suppress BC42024, the warning for unused local variables, specify `-nowarn:42024`.</span></span>  
  
 <span data-ttu-id="c3680-118">警告 ID の番号の詳細については、「[Visual Basic での警告の構成](/visualstudio/ide/configuring-warnings-in-visual-basic)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c3680-118">For more information on the warning ID numbers, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
|<span data-ttu-id="c3680-119">Visual Studio 統合開発環境で -nowarn を設定するには</span><span class="sxs-lookup"><span data-stu-id="c3680-119">To set -nowarn in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="c3680-120">1.**ソリューション エクスプローラー** でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="c3680-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="c3680-121">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c3680-121">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="c3680-122">2. **[コンパイル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="c3680-122">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="c3680-123">3.警告をすべて無効にするには、 **[すべての警告を表示しない]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="c3680-123">3.  Select the **Disable all warnings** check box to disable all warnings.</span></span><br />     <span data-ttu-id="c3680-124">または</span><span class="sxs-lookup"><span data-stu-id="c3680-124">- or -</span></span><br />     <span data-ttu-id="c3680-125">特定の警告を無効にするには、その警告の隣のドロップダウン リストから **[なし]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c3680-125">To disable a particular warning, click **None** from the drop-down list adjacent to the warning.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c3680-126">例</span><span class="sxs-lookup"><span data-stu-id="c3680-126">Example</span></span>  

 <span data-ttu-id="c3680-127">次のコードでは `T2.vb` がコンパイルされ、警告が表示されません。</span><span class="sxs-lookup"><span data-stu-id="c3680-127">The following code compiles `T2.vb` and does not display any warnings.</span></span>  
  
```console
vbc -nowarn t2.vb  
```  
  
## <a name="example"></a><span data-ttu-id="c3680-128">例</span><span class="sxs-lookup"><span data-stu-id="c3680-128">Example</span></span>  

 <span data-ttu-id="c3680-129">次のコードでは `T2.vb` がコンパイルされ、使用されていないローカル変数 (42024) の警告が表示されません。</span><span class="sxs-lookup"><span data-stu-id="c3680-129">The following code compiles `T2.vb` and does not display the warnings for unused local variables (42024).</span></span>  
  
```console
vbc -nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="c3680-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="c3680-130">See also</span></span>

- [<span data-ttu-id="c3680-131">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="c3680-131">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="c3680-132">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="c3680-132">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="c3680-133">Configuring Warnings in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c3680-133">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
