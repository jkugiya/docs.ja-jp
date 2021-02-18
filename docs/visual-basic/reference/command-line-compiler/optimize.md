---
description: '詳細情報: -optimize'
title: -optimize
ms.date: 07/20/2015
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
ms.openlocfilehash: 812eaa544dd874fd3871e58f366a34ee8176273a
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100426700"
---
# <a name="-optimize"></a><span data-ttu-id="d116d-103">-optimize</span><span class="sxs-lookup"><span data-stu-id="d116d-103">-optimize</span></span>

<span data-ttu-id="d116d-104">コンパイラ最適化を有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="d116d-104">Enables or disables compiler optimizations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d116d-105">構文</span><span class="sxs-lookup"><span data-stu-id="d116d-105">Syntax</span></span>  
  
```console  
-optimize[ + | - ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="d116d-106">引数</span><span class="sxs-lookup"><span data-stu-id="d116d-106">Arguments</span></span>  
  
|<span data-ttu-id="d116d-107">用語</span><span class="sxs-lookup"><span data-stu-id="d116d-107">Term</span></span>|<span data-ttu-id="d116d-108">定義</span><span class="sxs-lookup"><span data-stu-id="d116d-108">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="d116d-109">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="d116d-109">`+` &#124; `-`</span></span>|<span data-ttu-id="d116d-110">任意。</span><span class="sxs-lookup"><span data-stu-id="d116d-110">Optional.</span></span> <span data-ttu-id="d116d-111">`-optimize-` オプションにより、コンパイラ最適化が無効になります。</span><span class="sxs-lookup"><span data-stu-id="d116d-111">The `-optimize-` option disables compiler optimizations.</span></span> <span data-ttu-id="d116d-112">`-optimize+` オプションにより、最適化が有効になります。</span><span class="sxs-lookup"><span data-stu-id="d116d-112">The `-optimize+` option enables optimizations.</span></span> <span data-ttu-id="d116d-113">既定では、最適化が無効になります。</span><span class="sxs-lookup"><span data-stu-id="d116d-113">By default, optimizations are disabled.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d116d-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="d116d-114">Remarks</span></span>  

 <span data-ttu-id="d116d-115">コンパイラを最適化すると、出力ファイルのサイズが小さくなり、動作が速くなり、処理の効率が向上します。</span><span class="sxs-lookup"><span data-stu-id="d116d-115">Compiler optimizations make your output file smaller, faster, and more efficient.</span></span> <span data-ttu-id="d116d-116">ただし、最適化によって出力ファイル内のコードの配置が変更されるため、`-optimize+` を使用するとデバッグが困難になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d116d-116">However, because optimizations result in code rearrangement in the output file, `-optimize+` can make debugging difficult.</span></span>  
  
 <span data-ttu-id="d116d-117">`-target:module` で生成されるアセンブリのすべてのモジュールには、アセンブリと同じ `-optimize` 設定を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d116d-117">All modules generated with `-target:module` for an assembly must use the same `-optimize` settings as the assembly.</span></span> <span data-ttu-id="d116d-118">詳細については、「[-target (Visual Basic)](target.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d116d-118">For more information, see [-target (Visual Basic)](target.md).</span></span>  
  
 <span data-ttu-id="d116d-119">`-optimize` オプションと `-debug` オプションを組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="d116d-119">You can combine the `-optimize` and `-debug` options.</span></span>  
  
|<span data-ttu-id="d116d-120">Visual Studio 統合開発環境で -optimize を設定するには</span><span class="sxs-lookup"><span data-stu-id="d116d-120">To set -optimize in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="d116d-121">1.**ソリューション エクスプローラー** でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="d116d-121">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="d116d-122">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d116d-122">On the **Project** menu, click **Properties**.</span></span><br />     <br /><span data-ttu-id="d116d-123">2. **[コンパイル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d116d-123">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="d116d-124">3. **[詳細設定]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d116d-124">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="d116d-125">4. **[最適化を有効にする]** チェック ボックスを変更します。</span><span class="sxs-lookup"><span data-stu-id="d116d-125">4.  Modify the **Enable optimizations** check box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d116d-126">例</span><span class="sxs-lookup"><span data-stu-id="d116d-126">Example</span></span>  

 <span data-ttu-id="d116d-127">次のコードでは、`T2.vb` がコンパイルされ、コンパイラの最適化が有効になります。</span><span class="sxs-lookup"><span data-stu-id="d116d-127">The following code compiles `T2.vb` and enables compiler optimizations.</span></span>  
  
```console
vbc t2.vb -optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="d116d-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="d116d-128">See also</span></span>

- [<span data-ttu-id="d116d-129">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="d116d-129">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="d116d-130">-debug (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d116d-130">-debug (Visual Basic)</span></span>](debug.md)
- [<span data-ttu-id="d116d-131">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="d116d-131">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="d116d-132">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d116d-132">-target (Visual Basic)</span></span>](target.md)
