---
description: '詳細情報: スタック領域が不足しています。(Visual Basic)'
title: スタック領域が不足しています。
ms.date: 07/20/2015
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
ms.openlocfilehash: a32ca0d2becade33177596501b7eabde4251e0a9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795489"
---
# <a name="out-of-stack-space-visual-basic"></a><span data-ttu-id="ef8e8-103">スタック領域が不足しています。(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ef8e8-103">Out of stack space (Visual Basic)</span></span>

<span data-ttu-id="ef8e8-104">スタックは、実行中のプログラムの要求に応じて、動的に拡張および縮小されるメモリの作業領域です。</span><span class="sxs-lookup"><span data-stu-id="ef8e8-104">The stack is a working area of memory that grows and shrinks dynamically with the demands of your executing program.</span></span> <span data-ttu-id="ef8e8-105">その制限を超えました。</span><span class="sxs-lookup"><span data-stu-id="ef8e8-105">Its limits have been exceeded.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ef8e8-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="ef8e8-106">To correct this error</span></span>  
  
1. <span data-ttu-id="ef8e8-107">プロシージャの入れ子が深すぎないことをチェックします。</span><span class="sxs-lookup"><span data-stu-id="ef8e8-107">Check that procedures are not nested too deeply.</span></span>  
  
2. <span data-ttu-id="ef8e8-108">再帰プロシージャが正常に終了することを確認します。</span><span class="sxs-lookup"><span data-stu-id="ef8e8-108">Make sure recursive procedures terminate properly.</span></span>  
  
3. <span data-ttu-id="ef8e8-109">ローカル変数で、使用可能な量よりも多くのローカル変数領域が必要な場合は、一部の変数をモジュール レベルで宣言してみてください。</span><span class="sxs-lookup"><span data-stu-id="ef8e8-109">If local variables require more local variable space than is available, try declaring some variables at the module level.</span></span> <span data-ttu-id="ef8e8-110">また、`Static` を `Property`、`Sub`、または `Function` キーワードの前に付けて、プロシージャ内のすべての変数を静的に宣言することもできます。</span><span class="sxs-lookup"><span data-stu-id="ef8e8-110">You can also declare all variables in the procedure static by preceding the `Property`, `Sub`, or `Function` keyword with `Static`.</span></span> <span data-ttu-id="ef8e8-111">または、`Static` ステートメントを使用して、プロシージャ内で個々の静的変数を宣言することもできます。</span><span class="sxs-lookup"><span data-stu-id="ef8e8-111">Or you can use the `Static` statement to declare individual static variables within procedures.</span></span>  
  
4. <span data-ttu-id="ef8e8-112">固定長文字列は可変長文字列よりも多くのスタック領域を使用するため、一部の固定長文字列を可変長文字列として再定義します。</span><span class="sxs-lookup"><span data-stu-id="ef8e8-112">Redefine some of your fixed-length strings as variable-length strings, as fixed-length strings use more stack space than variable-length strings.</span></span> <span data-ttu-id="ef8e8-113">スタック領域を必要としない、モジュール レベルで文字列を定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="ef8e8-113">You can also define the string at module level where it requires no stack space.</span></span>  
  
5. <span data-ttu-id="ef8e8-114">`Calls` ダイアログ ボックスを使用して、スタック上でアクティブになっているプロシージャを表示して、入れ子になった `DoEvents` 関数呼び出しの数をチェックします。</span><span class="sxs-lookup"><span data-stu-id="ef8e8-114">Check the number of nested `DoEvents` function calls, by using the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
6. <span data-ttu-id="ef8e8-115">既にスタックにあるイベント プロシージャを呼び出すイベントをトリガーすることによって、"イベントのカスケード" が発生していないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="ef8e8-115">Make sure you did not cause an "event cascade" by triggering an event that calls an event procedure already on the stack.</span></span> <span data-ttu-id="ef8e8-116">イベントのカスケードは、未終了の再帰プロシージャ呼び出しに似ていますが、コード内の明示的な呼び出しではなく Visual Basic によって呼び出しが行われるため、目立ちません。</span><span class="sxs-lookup"><span data-stu-id="ef8e8-116">An event cascade is similar to an unterminated recursive procedure call, but it is less obvious, since the call is made by Visual Basic rather than an explicit call in the code.</span></span> <span data-ttu-id="ef8e8-117">`Calls` ダイアログ ボックスを使用すると、スタック上でアクティブになっているプロシージャが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ef8e8-117">Use the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef8e8-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="ef8e8-118">See also</span></span>

- <span data-ttu-id="ef8e8-119">[[メモリ] ウィンドウ](/visualstudio/debugger/memory-windows)</span><span class="sxs-lookup"><span data-stu-id="ef8e8-119">[Memory Windows](/visualstudio/debugger/memory-windows)</span></span>
