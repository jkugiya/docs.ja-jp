---
description: '詳細情報: #Region ディレクティブ'
title: '#Region ディレクティブ'
ms.date: 07/20/2015
f1_keywords:
- vb.Region
- vb.#Region
helpviewer_keywords:
- Visual Basic compiler, compiler directives
- '#region directive'
- region directive (#region)
- '#Region keyword [Visual Basic]'
ms.assetid: 90a6a104-3cbf-47d0-bdc4-b585d0921b87
ms.openlocfilehash: 4ba1645cfc51a69d39e6a60b5ea236dd65883e1c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797225"
---
# <a name="region-directive"></a><span data-ttu-id="4c6a4-103">#Region ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="4c6a4-103">#Region Directive</span></span>

<span data-ttu-id="4c6a4-104">Visual Basic ファイルのコードのセクションを折りたたんで非表示にします。</span><span class="sxs-lookup"><span data-stu-id="4c6a4-104">Collapses and hides sections of code in Visual Basic files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c6a4-105">構文</span><span class="sxs-lookup"><span data-stu-id="4c6a4-105">Syntax</span></span>  

```vb
#Region "identifier_string"  
#End Region  
```  
  
## <a name="parts"></a><span data-ttu-id="4c6a4-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="4c6a4-106">Parts</span></span>  
  
|<span data-ttu-id="4c6a4-107">用語</span><span class="sxs-lookup"><span data-stu-id="4c6a4-107">Term</span></span>|<span data-ttu-id="4c6a4-108">定義</span><span class="sxs-lookup"><span data-stu-id="4c6a4-108">Definition</span></span>|  
|---|---|  
|`identifier_string`|<span data-ttu-id="4c6a4-109">必須です。</span><span class="sxs-lookup"><span data-stu-id="4c6a4-109">Required.</span></span> <span data-ttu-id="4c6a4-110">領域が折りたたまれたときにその領域のタイトルとして機能する文字列です。</span><span class="sxs-lookup"><span data-stu-id="4c6a4-110">String that acts as the title of a region when it is collapsed.</span></span> <span data-ttu-id="4c6a4-111">既定では、領域は折りたたまれています。</span><span class="sxs-lookup"><span data-stu-id="4c6a4-111">Regions are collapsed by default.</span></span>|  
|`#End Region`|<span data-ttu-id="4c6a4-112">`#Region` ブロックを終了します。</span><span class="sxs-lookup"><span data-stu-id="4c6a4-112">Terminates the `#Region` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c6a4-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="4c6a4-113">Remarks</span></span>  

 <span data-ttu-id="4c6a4-114">Visual Studio Code エディターのアウトライン機能を使うときに展開または折りたたみの対象となるコード ブロックを指定するには、`#Region` ディレクティブを使用します。</span><span class="sxs-lookup"><span data-stu-id="4c6a4-114">Use the `#Region` directive to specify a block of code to expand or collapse when using the outlining feature of the Visual Studio Code Editor.</span></span> <span data-ttu-id="4c6a4-115">類似した領域をグループ化するために、他の領域内に領域を配置する ("*入れ子にする*") ことができます。</span><span class="sxs-lookup"><span data-stu-id="4c6a4-115">You can place, or *nest*, regions within other regions to group similar regions together.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c6a4-116">例</span><span class="sxs-lookup"><span data-stu-id="4c6a4-116">Example</span></span>  

 <span data-ttu-id="4c6a4-117">`#Region` ディレクティブの使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4c6a4-117">This example uses the `#Region` directive.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="4c6a4-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="4c6a4-118">See also</span></span>

- [<span data-ttu-id="4c6a4-119">#If...Then...#Else ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="4c6a4-119">#If...Then...#Else Directives</span></span>](if-then-else-directives.md)
- [<span data-ttu-id="4c6a4-120">アウトライン</span><span class="sxs-lookup"><span data-stu-id="4c6a4-120">Outlining</span></span>](/visualstudio/ide/outlining)
- [<span data-ttu-id="4c6a4-121">方法: コードのセクションを折りたたんで非表示にする</span><span class="sxs-lookup"><span data-stu-id="4c6a4-121">How to: Collapse and Hide Sections of Code</span></span>](../../programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)
