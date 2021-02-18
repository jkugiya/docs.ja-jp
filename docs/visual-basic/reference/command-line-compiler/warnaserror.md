---
description: '詳細情報: -warnaserror (Visual Basic)'
title: -warnaserror
ms.date: 03/13/2018
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
ms.openlocfilehash: 38fc2d70f95228c715ef5ac4bfc9b4fdb6f67c0e
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100470098"
---
# <a name="-warnaserror-visual-basic"></a><span data-ttu-id="323fd-103">-warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="323fd-103">-warnaserror (Visual Basic)</span></span>

<span data-ttu-id="323fd-104">コンパイラで、最初に発生した警告がエラーとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="323fd-104">Causes the compiler to treat the first occurrence of a warning as an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="323fd-105">構文</span><span class="sxs-lookup"><span data-stu-id="323fd-105">Syntax</span></span>  
  
```console  
-warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a><span data-ttu-id="323fd-106">引数</span><span class="sxs-lookup"><span data-stu-id="323fd-106">Arguments</span></span>  
  
|<span data-ttu-id="323fd-107">用語</span><span class="sxs-lookup"><span data-stu-id="323fd-107">Term</span></span>|<span data-ttu-id="323fd-108">定義</span><span class="sxs-lookup"><span data-stu-id="323fd-108">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="323fd-109">+ &#124; -</span><span class="sxs-lookup"><span data-stu-id="323fd-109">+ &#124; -</span></span>|<span data-ttu-id="323fd-110">任意。</span><span class="sxs-lookup"><span data-stu-id="323fd-110">Optional.</span></span> <span data-ttu-id="323fd-111">既定では `-warnaserror-` は有効です。警告が発生しても、コンパイラは出力ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="323fd-111">By default, `-warnaserror-` is in effect; warnings do not prevent the compiler from producing an output file.</span></span> <span data-ttu-id="323fd-112">`-warnaserror` オプションは `-warnaserror+` と同じで、警告がエラーとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="323fd-112">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>|  
|`numberList`|<span data-ttu-id="323fd-113">任意。</span><span class="sxs-lookup"><span data-stu-id="323fd-113">Optional.</span></span> <span data-ttu-id="323fd-114">`-warnaserror` オプションを適用する、警告 ID 番号のコンマ区切りのリスト。</span><span class="sxs-lookup"><span data-stu-id="323fd-114">Comma-delimited list of the warning ID numbers to which the `-warnaserror` option applies.</span></span> <span data-ttu-id="323fd-115">警告 ID が指定されていない場合、`-warnaserror`オプションはすべての警告に適用されます。</span><span class="sxs-lookup"><span data-stu-id="323fd-115">If no warning ID is specified, the `-warnaserror` option applies to all warnings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="323fd-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="323fd-116">Remarks</span></span>  

 <span data-ttu-id="323fd-117">`-warnaserror` オプションで、すべての警告がエラーとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="323fd-117">The `-warnaserror` option treats all warnings as errors.</span></span> <span data-ttu-id="323fd-118">通常は警告として報告されるすべてのメッセージが、代わりにエラーとして報告されます。</span><span class="sxs-lookup"><span data-stu-id="323fd-118">Any messages that would ordinarily be reported as warnings are instead reported as errors.</span></span> <span data-ttu-id="323fd-119">コンパイラは、後続の同じ警告の発生を警告として報告します。</span><span class="sxs-lookup"><span data-stu-id="323fd-119">The compiler reports subsequent occurrences of the same warning as warnings.</span></span>  
  
 <span data-ttu-id="323fd-120">既定では `-warnaserror-` が有効であり、警告は情報提供のみになります。</span><span class="sxs-lookup"><span data-stu-id="323fd-120">By default, `-warnaserror-` is in effect, which causes the warnings to be informational only.</span></span> <span data-ttu-id="323fd-121">`-warnaserror` オプションは `-warnaserror+` と同じで、警告がエラーとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="323fd-121">The `-warnaserror` option, which is the same as `-warnaserror+`, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="323fd-122">いくつかの特定の警告のみをエラーとして扱う場合は、エラーとして扱う警告番号のコンマ区切りのリストを指定できます。</span><span class="sxs-lookup"><span data-stu-id="323fd-122">If you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="323fd-123">`-warnaserror` オプションでは、警告の表示方法は制御されません。</span><span class="sxs-lookup"><span data-stu-id="323fd-123">The `-warnaserror` option does not control how warnings are displayed.</span></span> <span data-ttu-id="323fd-124">[-nowarn](nowarn.md) オプションを使用して警告を無効にします。</span><span class="sxs-lookup"><span data-stu-id="323fd-124">Use the [-nowarn](nowarn.md) option to disable warnings.</span></span>  
  
|<span data-ttu-id="323fd-125">-warnaserror を設定し、Visual Studio IDE ですべての警告をエラーとして扱う</span><span class="sxs-lookup"><span data-stu-id="323fd-125">To set -warnaserror to treat all warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="323fd-126">1.**ソリューション エクスプローラー** でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="323fd-126">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="323fd-127">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="323fd-127">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="323fd-128">2. **[コンパイル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="323fd-128">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="323fd-129">3. **[すべての警告を表示しない]** チェック ボックスがオフになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="323fd-129">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="323fd-130">4. **[すべての警告をエラーとして扱う]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="323fd-130">4.  Check the **Treat all warnings as errors** check box.</span></span>|  
  
|<span data-ttu-id="323fd-131">-warnaserror を設定し、Visual Studio IDE で特定の警告をエラーとして扱う</span><span class="sxs-lookup"><span data-stu-id="323fd-131">To set -warnaserror to treat specific warnings as errors in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="323fd-132">1.**ソリューション エクスプローラー** でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="323fd-132">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="323fd-133">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="323fd-133">On the **Project** menu, click **Properties**.</span></span><br /><span data-ttu-id="323fd-134">2. **[コンパイル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="323fd-134">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="323fd-135">3. **[すべての警告を表示しない]** チェック ボックスがオフになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="323fd-135">3.  Make sure the **Disable all warnings** check box is unchecked.</span></span><br /><span data-ttu-id="323fd-136">4. **[すべての警告をエラーとして扱う]** チェック ボックスがオフになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="323fd-136">4.  Make sure the **Treat all warnings as errors** check box is unchecked.</span></span><br /><span data-ttu-id="323fd-137">5.エラーとして扱う警告の隣にある **[通知]** 列から、 **[エラー]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="323fd-137">5.  Select **Error** from the **Notification** column adjacent to the warning that should be treated as an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="323fd-138">例</span><span class="sxs-lookup"><span data-stu-id="323fd-138">Example</span></span>  

 <span data-ttu-id="323fd-139">次のコードは `In.vb` をコンパイルし、最初に見つけたすべての警告をエラーとして表示するようにコンパイラに指示します。</span><span class="sxs-lookup"><span data-stu-id="323fd-139">The following code compiles `In.vb` and directs the compiler to display an error for the first occurrence of every warning it finds.</span></span>  
  
```console
vbc -warnaserror in.vb  
```  
  
## <a name="example"></a><span data-ttu-id="323fd-140">例</span><span class="sxs-lookup"><span data-stu-id="323fd-140">Example</span></span>  

 <span data-ttu-id="323fd-141">次のコードは `T2.vb` をコンパイルし、使用されていないローカル変数 (42024) に向けた警告のみをエラーとして扱います。</span><span class="sxs-lookup"><span data-stu-id="323fd-141">The following code compiles `T2.vb` and treats only the warning for unused local variables (42024) as an error.</span></span>  
  
```console
vbc -warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="323fd-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="323fd-142">See also</span></span>

- [<span data-ttu-id="323fd-143">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="323fd-143">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="323fd-144">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="323fd-144">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="323fd-145">Configuring Warnings in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="323fd-145">Configuring Warnings in Visual Basic</span></span>](/visualstudio/ide/configuring-warnings-in-visual-basic)
