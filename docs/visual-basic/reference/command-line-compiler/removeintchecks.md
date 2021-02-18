---
description: '詳細情報: -removeintchecks'
title: -removeintchecks
ms.date: 03/13/2018
f1_keywords:
- removeintchecks
- -removeintchecks
helpviewer_keywords:
- removeintchecks compiler option [Visual Basic]
- /removeintchecks compiler option [Visual Basic]
- -removeintchecks compiler option [Visual Basic]
ms.assetid: c1835bd5-1e38-4fba-bd2f-6984774765d4
ms.openlocfilehash: 1dc484e1538718b68fe9f0cc450fa2480dc52412
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100474097"
---
# <a name="-removeintchecks"></a><span data-ttu-id="07ab2-103">-removeintchecks</span><span class="sxs-lookup"><span data-stu-id="07ab2-103">-removeintchecks</span></span>

<span data-ttu-id="07ab2-104">整数演算のオーバーフロー エラー チェックをオンまたはオフにします。</span><span class="sxs-lookup"><span data-stu-id="07ab2-104">Turns overflow-error checking for integer operations on or off.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07ab2-105">構文</span><span class="sxs-lookup"><span data-stu-id="07ab2-105">Syntax</span></span>  
  
```console  
-removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="07ab2-106">引数</span><span class="sxs-lookup"><span data-stu-id="07ab2-106">Arguments</span></span>  
  
|<span data-ttu-id="07ab2-107">用語</span><span class="sxs-lookup"><span data-stu-id="07ab2-107">Term</span></span>|<span data-ttu-id="07ab2-108">定義</span><span class="sxs-lookup"><span data-stu-id="07ab2-108">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="07ab2-109">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="07ab2-109">`+` &#124; `-`</span></span>|<span data-ttu-id="07ab2-110">任意。</span><span class="sxs-lookup"><span data-stu-id="07ab2-110">Optional.</span></span> <span data-ttu-id="07ab2-111">`-removeintchecks-` オプションを指定すると、すべての整数計算について、オーバーフロー エラーの有無がコンパイラでチェックされます。</span><span class="sxs-lookup"><span data-stu-id="07ab2-111">The `-removeintchecks-` option causes the compiler to check all integer calculations for overflow errors.</span></span> <span data-ttu-id="07ab2-112">既定値は、`-removeintchecks-` です。</span><span class="sxs-lookup"><span data-stu-id="07ab2-112">The default is `-removeintchecks-`.</span></span><br /><br /> <span data-ttu-id="07ab2-113">`-removeintchecks` または `-removeintchecks+` を指定すると、エラー チェックが行われず、整数計算を高速にすることができます。</span><span class="sxs-lookup"><span data-stu-id="07ab2-113">Specifying `-removeintchecks` or `-removeintchecks+` prevents error checking and can make integer calculations faster.</span></span> <span data-ttu-id="07ab2-114">ただし、エラー チェックが行われず、データ型の容量がオーバーフローした場合は、エラーが発生することなく誤った結果が格納される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="07ab2-114">However, without error checking, and if data type capacities are overflowed, incorrect results may be stored without raising an error.</span></span>|  
  
|<span data-ttu-id="07ab2-115">Visual Studio 統合開発環境で -removeintchecks を設定するには</span><span class="sxs-lookup"><span data-stu-id="07ab2-115">To set -removeintchecks in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="07ab2-116">1.**ソリューション エクスプローラー** でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="07ab2-116">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="07ab2-117">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="07ab2-117">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="07ab2-118">2. **[コンパイル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="07ab2-118">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="07ab2-119">3. **[詳細設定]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="07ab2-119">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="07ab2-120">4. **[整数オーバーフローのチェックを解除]** ボックスの値を変更します。</span><span class="sxs-lookup"><span data-stu-id="07ab2-120">4.  Modify the value of the **Remove integer overflow checks** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="07ab2-121">例</span><span class="sxs-lookup"><span data-stu-id="07ab2-121">Example</span></span>  

 <span data-ttu-id="07ab2-122">次のコードでは、`Test.vb` がコンパイルされ、整数オーバーフロー エラーのチェックがオフにされます。</span><span class="sxs-lookup"><span data-stu-id="07ab2-122">The following code compiles `Test.vb` and turns off integer overflow-error checking.</span></span>  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="07ab2-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="07ab2-123">See also</span></span>

- [<span data-ttu-id="07ab2-124">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="07ab2-124">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="07ab2-125">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="07ab2-125">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
