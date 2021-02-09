---
description: '詳細情報: 方法:アプリケーションの起動時または終了時にメッセージをログに記録する (Visual Basic)'
title: '方法: アプリケーションの起動時または終了時にメッセージをログに記録する'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, shutdown
- My.Application.Log object, logging
- Startup event [Visual Basic]
- event logs, startup
- Shutdown event [Visual Basic]
- My.Log object, logging
ms.assetid: 67624d05-cddf-48b7-8c36-5c99baa4c621
ms.openlocfilehash: 545a57c3666aa12e3763961d05067face9fe324a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775189"
---
# <a name="how-to-log-messages-when-the-application-starts-or-shuts-down-visual-basic"></a><span data-ttu-id="7ccdc-103">方法: アプリケーションの起動時または終了時にメッセージをログに記録する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ccdc-103">How to: Log Messages When the Application Starts or Shuts Down (Visual Basic)</span></span>

<span data-ttu-id="7ccdc-104">`My.Application.Log` オブジェクトおよび `My.Log` オブジェクトを使用すると、アプリケーション内で発生したイベントに関する情報をログに記録できます。</span><span class="sxs-lookup"><span data-stu-id="7ccdc-104">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="7ccdc-105">この例では、 `My.Application.Log.WriteEntry` イベントおよび `Startup` イベントで `Shutdown` メソッドを使用してトレース情報を書き込む方法を示します。</span><span class="sxs-lookup"><span data-stu-id="7ccdc-105">This example shows how to use the `My.Application.Log.WriteEntry` method with the `Startup` and `Shutdown` events to write tracing information.</span></span>  
  
### <a name="to-access-the-applications-event-handler-code"></a><span data-ttu-id="7ccdc-106">アプリケーションのイベント ハンドラー コードにアクセスするには</span><span class="sxs-lookup"><span data-stu-id="7ccdc-106">To access the application's event-handler code</span></span>  
  
1. <span data-ttu-id="7ccdc-107">**ソリューション エクスプローラー** でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="7ccdc-107">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="7ccdc-108">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7ccdc-108">On the **Project** menu, choose **Properties**.</span></span>  
  
2. <span data-ttu-id="7ccdc-109">**[アプリケーション]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="7ccdc-109">Click the **Application** tab.</span></span>  
  
3. <span data-ttu-id="7ccdc-110">**[アプリケーション イベントの表示]** をクリックしてコード エディターを開きます。</span><span class="sxs-lookup"><span data-stu-id="7ccdc-110">Click the **View Application Events** button to open the Code Editor.</span></span>  
  
     <span data-ttu-id="7ccdc-111">ApplicationEvents.vb ファイルが開かれます。</span><span class="sxs-lookup"><span data-stu-id="7ccdc-111">This opens the ApplicationEvents.vb file.</span></span>  
  
### <a name="to-log-messages-when-the-application-starts"></a><span data-ttu-id="7ccdc-112">アプリケーションの起動時にメッセージをログに記録するには</span><span class="sxs-lookup"><span data-stu-id="7ccdc-112">To log messages when the application starts</span></span>  
  
1. <span data-ttu-id="7ccdc-113">コード エディターで ApplicationEvents.vb ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="7ccdc-113">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="7ccdc-114">**[全般]** メニューの **[MyApplication イベント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7ccdc-114">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
2. <span data-ttu-id="7ccdc-115">**[宣言]** メニューの **[スタートアップ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7ccdc-115">On the **Declarations** menu, choose **Startup**.</span></span>  
  
     <span data-ttu-id="7ccdc-116">アプリケーションでは、メイン アプリケーションの実行前に <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="7ccdc-116">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> event before the main application runs.</span></span>  
  
3. <span data-ttu-id="7ccdc-117">`My.Application.Log.WriteEntry` イベント ハンドラーに `Startup` メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="7ccdc-117">Add the `My.Application.Log.WriteEntry` method to the `Startup` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#1)]  
  
### <a name="to-log-messages-when-the-application-shuts-down"></a><span data-ttu-id="7ccdc-118">アプリケーションの終了時にメッセージをログに記録するには</span><span class="sxs-lookup"><span data-stu-id="7ccdc-118">To log messages when the application shuts down</span></span>  
  
1. <span data-ttu-id="7ccdc-119">コード エディターで ApplicationEvents.vb ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="7ccdc-119">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="7ccdc-120">**[全般]** メニューの **[MyApplication イベント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7ccdc-120">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
2. <span data-ttu-id="7ccdc-121">**[宣言]** メニューの **[シャットダウン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7ccdc-121">On the **Declarations** menu, choose **Shutdown**.</span></span>  
  
     <span data-ttu-id="7ccdc-122">アプリケーションでは、メイン アプリケーションが実行された後、終了前に <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="7ccdc-122">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> event after the main application runs, but before it shuts down.</span></span>  
  
3. <span data-ttu-id="7ccdc-123">`My.Application.Log.WriteEntry` イベント ハンドラーに `Shutdown` メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="7ccdc-123">Add the `My.Application.Log.WriteEntry` method to the `Shutdown` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="7ccdc-124">例</span><span class="sxs-lookup"><span data-stu-id="7ccdc-124">Example</span></span>  

 <span data-ttu-id="7ccdc-125">**プロジェクト デザイナー** を使用して、コード エディターでアプリケーション イベントにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="7ccdc-125">You can use the **Project Designer** to access the application events in the Code Editor.</span></span> <span data-ttu-id="7ccdc-126">詳細については、「[[アプリケーション] ページ (プロジェクト デザイナー) (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ccdc-126">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
 [!code-vb[VbVbalrMyApplicationLog#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="7ccdc-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="7ccdc-127">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- <span data-ttu-id="7ccdc-128">[[アプリケーション] ページ (プロジェクト デザイナー)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)</span><span class="sxs-lookup"><span data-stu-id="7ccdc-128">[Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)</span></span>
- [<span data-ttu-id="7ccdc-129">アプリケーション ログの使用</span><span class="sxs-lookup"><span data-stu-id="7ccdc-129">Working with Application Logs</span></span>](working-with-application-logs.md)
