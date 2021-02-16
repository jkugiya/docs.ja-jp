---
description: '詳細情報: 方法:値を返さないプロシージャを呼び出す (Visual Basic)'
title: '方法: 値を返さないプロシージャを呼び出す'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
ms.openlocfilehash: 3aaa6b4358f0585323e6c8321eea7dbaa4906a44
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466771"
---
# <a name="how-to-call-a-procedure-that-does-not-return-a-value-visual-basic"></a><span data-ttu-id="a9f6d-103">方法: 値を返さないプロシージャを呼び出す (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a9f6d-103">How to: Call a Procedure that Does Not Return a Value (Visual Basic)</span></span>

<span data-ttu-id="a9f6d-104">`Sub` プロシージャから呼び出し元コードに対しては値が返されません。</span><span class="sxs-lookup"><span data-stu-id="a9f6d-104">A `Sub` procedure does not return a value to the calling code.</span></span> <span data-ttu-id="a9f6d-105">これは、スタンドアロンの呼び出し元ステートメントを使用して明示的に呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a9f6d-105">You call it explicitly with a stand-alone calling statement.</span></span> <span data-ttu-id="a9f6d-106">式内でその名前を使用するだけでは呼び出せません。</span><span class="sxs-lookup"><span data-stu-id="a9f6d-106">You cannot call it by simply using its name within an expression.</span></span>  
  
### <a name="to-call-a-sub-procedure"></a><span data-ttu-id="a9f6d-107">Sub プロシージャを呼び出すには</span><span class="sxs-lookup"><span data-stu-id="a9f6d-107">To call a Sub procedure</span></span>  
  
1. <span data-ttu-id="a9f6d-108">`Sub` プロシージャの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="a9f6d-108">Specify the name of the `Sub` procedure.</span></span>  
  
2. <span data-ttu-id="a9f6d-109">プロシージャ名の後にかっこを使用して引数リストを囲みます。</span><span class="sxs-lookup"><span data-stu-id="a9f6d-109">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="a9f6d-110">引数がない場合は、必要に応じてかっこを省略できます。</span><span class="sxs-lookup"><span data-stu-id="a9f6d-110">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="a9f6d-111">ただし、かっこを使用すると、コードが読みやすくなります。</span><span class="sxs-lookup"><span data-stu-id="a9f6d-111">However, using the parentheses makes your code easier to read.</span></span>  
  
3. <span data-ttu-id="a9f6d-112">引数リストの引数をコンマで区切ってかっこ内に配置します。</span><span class="sxs-lookup"><span data-stu-id="a9f6d-112">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="a9f6d-113">引数の指定は必ず、`Sub` プロシージャで定義されている対応するパラメーターと同じ順序で行ってください。</span><span class="sxs-lookup"><span data-stu-id="a9f6d-113">Be sure you supply the arguments in the same order that the `Sub` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="a9f6d-114">次の例では、Visual Basic <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> 関数を呼び出して、アプリケーション ウィンドウをアクティブにします。</span><span class="sxs-lookup"><span data-stu-id="a9f6d-114">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> function to activate an application window.</span></span> <span data-ttu-id="a9f6d-115"><xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> は、ウィンドウ タイトルを唯一の引数として受け取ります。</span><span class="sxs-lookup"><span data-stu-id="a9f6d-115"><xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> takes the window title as its sole argument.</span></span> <span data-ttu-id="a9f6d-116">呼び出し元のコードには値が返されません。</span><span class="sxs-lookup"><span data-stu-id="a9f6d-116">It does not return a value to the calling code.</span></span> <span data-ttu-id="a9f6d-117">メモ帳プロセスが実行されていない場合、この例では <xref:System.ArgumentException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="a9f6d-117">If a Notepad process is not running, the example throws an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="a9f6d-118">`Shell` プロシージャでは、アプリケーションが指定されたパスにあることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="a9f6d-118">The `Shell` procedure assumes the applications are in the paths specified.</span></span>  
  
     [!code-vb[VbVbalrCatRef#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCatRef/VB/Class1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="a9f6d-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="a9f6d-119">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:System.ArgumentException>
- [<span data-ttu-id="a9f6d-120">手順</span><span class="sxs-lookup"><span data-stu-id="a9f6d-120">Procedures</span></span>](./index.md)
- [<span data-ttu-id="a9f6d-121">Sub プロシージャ</span><span class="sxs-lookup"><span data-stu-id="a9f6d-121">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="a9f6d-122">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="a9f6d-122">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="a9f6d-123">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="a9f6d-123">Sub Statement</span></span>](../../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="a9f6d-124">方法: プロシージャを作成する</span><span class="sxs-lookup"><span data-stu-id="a9f6d-124">How to: Create a Procedure</span></span>](./how-to-create-a-procedure.md)
- [<span data-ttu-id="a9f6d-125">方法: 値を返すプロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="a9f6d-125">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="a9f6d-126">方法: Visual Basic でイベント ハンドラーを呼び出す</span><span class="sxs-lookup"><span data-stu-id="a9f6d-126">How to: Call an Event Handler in Visual Basic</span></span>](./how-to-call-an-event-handler.md)
