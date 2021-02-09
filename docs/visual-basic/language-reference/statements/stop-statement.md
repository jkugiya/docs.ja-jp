---
description: '詳細情報: Stop ステートメント (Visual Basic)'
title: Stop ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.Stop
helpviewer_keywords:
- breakpoints, Stop statements
- Stop statements [Visual Basic], syntax
- Stop statements [Visual Basic]
- execution [Visual Basic], suspending
- processing, interrupting
- processes, interrupting
- execution [Visual Basic], stopping
ms.assetid: c9a9fde0-d649-4662-9bef-bd0146ebc2a7
ms.openlocfilehash: 1e25eb88d1b85f38a53023dfb7dfbc877f498e5e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741082"
---
# <a name="stop-statement-visual-basic"></a><span data-ttu-id="9c04e-103">Stop ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9c04e-103">Stop Statement (Visual Basic)</span></span>

<span data-ttu-id="9c04e-104">実行を中断します。</span><span class="sxs-lookup"><span data-stu-id="9c04e-104">Suspends execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c04e-105">構文</span><span class="sxs-lookup"><span data-stu-id="9c04e-105">Syntax</span></span>  
  
```vb  
Stop  
```  
  
## <a name="remarks"></a><span data-ttu-id="9c04e-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="9c04e-106">Remarks</span></span>  

 <span data-ttu-id="9c04e-107">プロシージャ内のどこでも `Stop` ステートメントを配置して、実行を中断できます。</span><span class="sxs-lookup"><span data-stu-id="9c04e-107">You can place `Stop` statements anywhere in procedures to suspend execution.</span></span> <span data-ttu-id="9c04e-108">`Stop` ステートメントの使用は、コードにブレークポイントを設定することと似ています。</span><span class="sxs-lookup"><span data-stu-id="9c04e-108">Using the `Stop` statement is similar to setting a breakpoint in the code.</span></span>  
  
 <span data-ttu-id="9c04e-109">`Stop` ステートメントでは実行が中断されますが、`End` とは異なり、コンパイル済みの実行可能 (.exe) ファイルで検出されていない限り、ファイルを閉じたり、変数をクリアしたりしません。</span><span class="sxs-lookup"><span data-stu-id="9c04e-109">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9c04e-110">統合開発環境 (IDE) の外部で実行されているコードで `Stop` ステートメントが検出されると、デバッガーが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="9c04e-110">If the `Stop` statement is encountered in code that is running outside of the integrated development environment (IDE), the debugger is invoked.</span></span> <span data-ttu-id="9c04e-111">これは、コードがデバッグ モードと製品版モードのどちらでコンパイルされたかに関係なく当てはまります。</span><span class="sxs-lookup"><span data-stu-id="9c04e-111">This is true regardless of whether the code was compiled in debug or retail mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c04e-112">例</span><span class="sxs-lookup"><span data-stu-id="9c04e-112">Example</span></span>  

 <span data-ttu-id="9c04e-113">この例では、`Stop` ステートメントを使用して、`For...Next` ループを通した反復ごとに実行を中断しています。</span><span class="sxs-lookup"><span data-stu-id="9c04e-113">This example uses the `Stop` statement to suspend execution for each iteration through the `For...Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#56)]  
  
## <a name="see-also"></a><span data-ttu-id="9c04e-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="9c04e-114">See also</span></span>

- [<span data-ttu-id="9c04e-115">End ステートメント</span><span class="sxs-lookup"><span data-stu-id="9c04e-115">End Statement</span></span>](end-statement.md)
