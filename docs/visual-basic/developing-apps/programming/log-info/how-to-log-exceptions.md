---
description: '詳細情報: 方法:Visual Basic で例外をログに記録する'
title: '方法: 例外をログに記録する'
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions, logging
- exceptions, tracking
ms.assetid: a26c60e2-ae39-444a-aebb-33eccadc0eeb
ms.openlocfilehash: a4155de4e73c632edf071256976161cfdbffba77
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775215"
---
# <a name="how-to-log-exceptions-in-visual-basic"></a><span data-ttu-id="63fed-103">方法: Visual Basic で例外をログに記録する</span><span class="sxs-lookup"><span data-stu-id="63fed-103">How to: Log Exceptions in Visual Basic</span></span>

<span data-ttu-id="63fed-104">`My.Application.Log` オブジェクトおよび `My.Log` オブジェクトを使用すると、アプリケーション内で発生した例外に関する情報をログに記録できます。</span><span class="sxs-lookup"><span data-stu-id="63fed-104">You can use the `My.Application.Log` and `My.Log` objects to log information about exceptions that occur in your application.</span></span> <span data-ttu-id="63fed-105">以下の例では、`My.Application.Log.WriteException` メソッドを使用して、明示的にキャッチした例外および未処理の例外をログに記録する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="63fed-105">These examples show how to use the `My.Application.Log.WriteException` method to log exceptions that you catch explicitly and exceptions that are unhandled.</span></span>  
  
 <span data-ttu-id="63fed-106">トレース情報をログに記録するには、`My.Application.Log.WriteEntry` メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="63fed-106">For logging tracing information, use the `My.Application.Log.WriteEntry` method.</span></span> <span data-ttu-id="63fed-107">詳細については、<xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> を参照してください。</span><span class="sxs-lookup"><span data-stu-id="63fed-107">For more information, see <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A></span></span>  
  
### <a name="to-log-a-handled-exception"></a><span data-ttu-id="63fed-108">処理した例外をログに記録するには</span><span class="sxs-lookup"><span data-stu-id="63fed-108">To log a handled exception</span></span>  
  
1. <span data-ttu-id="63fed-109">例外情報を生成するメソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="63fed-109">Create the method that will generate the exception information.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#9)]  
  
2. <span data-ttu-id="63fed-110">`Try...Catch` ブロックを使用して例外をキャッチします。</span><span class="sxs-lookup"><span data-stu-id="63fed-110">Use a `Try...Catch` block to catch the exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#6)]  
  
3. <span data-ttu-id="63fed-111">例外が発生する可能性のあるコードを `Try` ブロックに記述します。</span><span class="sxs-lookup"><span data-stu-id="63fed-111">Put the code that could generate an exception in the `Try` block.</span></span>  
  
     <span data-ttu-id="63fed-112">`Dim` 行と `MsgBox` 行のコメントを解除すると、<xref:System.NullReferenceException> 例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="63fed-112">Uncomment the `Dim` and `MsgBox` lines to cause a <xref:System.NullReferenceException> exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#7)]  
  
4. <span data-ttu-id="63fed-113">`Catch` ブロックで、`My.Application.Log.WriteException` メソッドを使用して例外情報を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="63fed-113">In the `Catch` block, use the `My.Application.Log.WriteException` method to write the exception information.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#8)]  
  
     <span data-ttu-id="63fed-114">次の例は、処理した例外をログに記録するコード全体を示しています。</span><span class="sxs-lookup"><span data-stu-id="63fed-114">The following example shows the complete code for logging a handled exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#10)]  
  
### <a name="to-log-an-unhandled-exception"></a><span data-ttu-id="63fed-115">未処理の例外をログに記録するには</span><span class="sxs-lookup"><span data-stu-id="63fed-115">To log an unhandled exception</span></span>  
  
1. <span data-ttu-id="63fed-116">**ソリューション エクスプローラー** でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="63fed-116">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="63fed-117">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="63fed-117">On the **Project** menu, choose **Properties**.</span></span>  
  
2. <span data-ttu-id="63fed-118">**[アプリケーション]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="63fed-118">Click the **Application** tab.</span></span>  
  
3. <span data-ttu-id="63fed-119">**[アプリケーション イベントの表示]** をクリックしてコード エディターを開きます。</span><span class="sxs-lookup"><span data-stu-id="63fed-119">Click the **View Application Events** button to open the Code Editor.</span></span>  
  
     <span data-ttu-id="63fed-120">ApplicationEvents.vb ファイルが開かれます。</span><span class="sxs-lookup"><span data-stu-id="63fed-120">This opens the ApplicationEvents.vb file.</span></span>  
  
4. <span data-ttu-id="63fed-121">コード エディターで ApplicationEvents.vb ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="63fed-121">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="63fed-122">**[全般]** メニューの **[MyApplication イベント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="63fed-122">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
5. <span data-ttu-id="63fed-123">**[宣言]** メニューの **[UnhandledException]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="63fed-123">On the **Declarations** menu, choose **UnhandledException**.</span></span>  
  
     <span data-ttu-id="63fed-124">アプリケーションでは、メイン アプリケーションの実行前に <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="63fed-124">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> event before the main application runs.</span></span>  
  
6. <span data-ttu-id="63fed-125">`My.Application.Log.WriteException` イベント ハンドラーに `UnhandledException` メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="63fed-125">Add the `My.Application.Log.WriteException` method to the `UnhandledException` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#4)]  
  
     <span data-ttu-id="63fed-126">次の例は、未処理の例外をログに記録するためのコード全体を示しています。</span><span class="sxs-lookup"><span data-stu-id="63fed-126">The following example shows the complete code for logging an unhandled exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="63fed-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="63fed-127">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="63fed-128">アプリケーション ログの使用</span><span class="sxs-lookup"><span data-stu-id="63fed-128">Working with Application Logs</span></span>](working-with-application-logs.md)
- [<span data-ttu-id="63fed-129">方法: ログ メッセージを書き込む</span><span class="sxs-lookup"><span data-stu-id="63fed-129">How to: Write Log Messages</span></span>](how-to-write-log-messages.md)
- [<span data-ttu-id="63fed-130">チュートリアル : My.Application.Log による情報の書き込み先の確認</span><span class="sxs-lookup"><span data-stu-id="63fed-130">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](walkthrough-determining-where-my-application-log-writes-information.md)
- [<span data-ttu-id="63fed-131">チュートリアル: My.Application.Log による情報の書き込み先の変更</span><span class="sxs-lookup"><span data-stu-id="63fed-131">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](walkthrough-changing-where-my-application-log-writes-information.md)
