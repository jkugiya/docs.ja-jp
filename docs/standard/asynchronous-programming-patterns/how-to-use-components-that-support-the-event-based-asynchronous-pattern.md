---
description: '詳細情報: イベントベースの非同期パターンをサポートするコンポーネントを使用する方法'
title: '方法: イベントベースの非同期パターンをサポートするコンポーネントを使用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET], asynchronous features
- components [.NET], asynchronous
- AsyncOperation class
- threading [Windows Forms], asynchronous features
- AsyncCompletedEventArgs class
ms.assetid: 35e9549c-1568-4768-ad07-17cc6dff11e1
ms.openlocfilehash: 78c5df143e687333689e7805dfc89b4cf0f5e98a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702965"
---
# <a name="how-to-use-components-that-support-the-event-based-asynchronous-pattern"></a><span data-ttu-id="58c7f-103">方法: イベントベースの非同期パターンをサポートするコンポーネントを使用する</span><span class="sxs-lookup"><span data-stu-id="58c7f-103">How to: Use Components That Support the Event-based Asynchronous Pattern</span></span>

<span data-ttu-id="58c7f-104">多くのコンポーネントでは、非同期的に作業を実行するオプションが提供されます。</span><span class="sxs-lookup"><span data-stu-id="58c7f-104">Many components provide you with the option of performing their work asynchronously.</span></span> <span data-ttu-id="58c7f-105">たとえば、<xref:System.Media.SoundPlayer> と <xref:System.Windows.Forms.PictureBox> コンポーネントでは、メイン スレッドが中断されることなく、実行され続ける間に、"バックグラウンドで" 音声とイメージを読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="58c7f-105">The <xref:System.Media.SoundPlayer> and <xref:System.Windows.Forms.PictureBox> components, for example, enable you to load sounds and images "in the background" while your main thread continues running without interruption.</span></span>  
  
 <span data-ttu-id="58c7f-106">[イベントベースの非同期パターンの概要](event-based-asynchronous-pattern-overview.md)をサポートするクラスで非同期メソッドを使用することは、別のイベントに対して行うように、イベント ハンドラーをコンポーネントの _MethodName_**Completed** イベントにアタッチするのと同じくらい単純です。</span><span class="sxs-lookup"><span data-stu-id="58c7f-106">Using asynchronous methods on a class that supports the [Event-based Asynchronous Pattern Overview](event-based-asynchronous-pattern-overview.md) can be as simple as attaching an event handler to the component's _MethodName_**Completed** event, just as you would for any other event.</span></span> <span data-ttu-id="58c7f-107">_MethodName_**Async** メソッドを呼び出すと、_MethodName_**Completed** イベントが発生するまで、アプリケーションは中断されることなく実行され続けます。</span><span class="sxs-lookup"><span data-stu-id="58c7f-107">When you call the _MethodName_**Async** method, your application will continue running without interruption until the _MethodName_**Completed** event is raised.</span></span> <span data-ttu-id="58c7f-108">イベント ハンドラーで、非同期操作が正常に完了するか、キャンセルされたかどうかを判断するには、<xref:System.ComponentModel.AsyncCompletedEventArgs> パラメーターを調べることができます。</span><span class="sxs-lookup"><span data-stu-id="58c7f-108">In your event handler, you can examine the <xref:System.ComponentModel.AsyncCompletedEventArgs> parameter to determine if the asynchronous operation successfully completed or if it was canceled.</span></span>  
  
 <span data-ttu-id="58c7f-109">イベント ハンドラーの使用に関する詳細については、「[イベント ハンドラーの概要](/dotnet/desktop/winforms/event-handlers-overview-windows-forms)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58c7f-109">For more information about using event handlers, see [Event Handlers Overview](/dotnet/desktop/winforms/event-handlers-overview-windows-forms).</span></span>  
  
 <span data-ttu-id="58c7f-110">次の手順は、<xref:System.Windows.Forms.PictureBox> コントロールの非同期イメージ読み込み機能を使用する方法について示しています。</span><span class="sxs-lookup"><span data-stu-id="58c7f-110">The following procedure shows how to use the asynchronous image-loading capability of a <xref:System.Windows.Forms.PictureBox> control.</span></span>  
  
### <a name="to-enable-a-picturebox-control-to-asynchronously-load-an-image"></a><span data-ttu-id="58c7f-111">イメージを非同期的に読み込むために PictureBox コントロールを有効にするには</span><span class="sxs-lookup"><span data-stu-id="58c7f-111">To enable a PictureBox control to asynchronously load an image</span></span>  
  
1. <span data-ttu-id="58c7f-112">フォームで <xref:System.Windows.Forms.PictureBox> コンポーネントのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="58c7f-112">Create an instance of the <xref:System.Windows.Forms.PictureBox> component in your form.</span></span>  
  
2. <span data-ttu-id="58c7f-113">イベント ハンドラーを <xref:System.Windows.Forms.PictureBox.LoadCompleted> イベントに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="58c7f-113">Assign an event handler to the <xref:System.Windows.Forms.PictureBox.LoadCompleted> event.</span></span>  
  
     <span data-ttu-id="58c7f-114">非同期ダウンロード中に発生する可能性があるエラーをここで確認してください。</span><span class="sxs-lookup"><span data-stu-id="58c7f-114">Check for any errors that may have occurred during the asynchronous download here.</span></span> <span data-ttu-id="58c7f-115">また、ここはキャンセルを確認するための場所でもあります。</span><span class="sxs-lookup"><span data-stu-id="58c7f-115">This is also where you check for cancellation.</span></span>  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#2](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#2](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/Form1.vb#2)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#5](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#5](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/Form1.vb#5)]  
  
3. <span data-ttu-id="58c7f-116">`loadButton` と `cancelLoadButton` と呼ばれる 2 つのボタンをフォームに追加します。</span><span class="sxs-lookup"><span data-stu-id="58c7f-116">Add two buttons, called `loadButton` and `cancelLoadButton`, to your form.</span></span> <span data-ttu-id="58c7f-117">ダウンロードの開始とキャンセルを行うために、<xref:System.Windows.Forms.Control.Click> イベント ハンドラーを追加します。</span><span class="sxs-lookup"><span data-stu-id="58c7f-117">Add <xref:System.Windows.Forms.Control.Click> event handlers to start and cancel the download.</span></span>  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#3](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#3](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#4](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#4](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/Form1.vb#4)]  
  
4. <span data-ttu-id="58c7f-118">アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="58c7f-118">Run your application.</span></span>  
  
     <span data-ttu-id="58c7f-119">イメージのダウンロードを進めるときに、フォームを自由に移動したり、最小化や最大化を行ったりすることができます。</span><span class="sxs-lookup"><span data-stu-id="58c7f-119">As the image download proceeds, you can move the form freely, minimize it, and maximize it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58c7f-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="58c7f-120">See also</span></span>

- [<span data-ttu-id="58c7f-121">方法: バックグラウンドで操作を実行する</span><span class="sxs-lookup"><span data-stu-id="58c7f-121">How to: Run an Operation in the Background</span></span>](/dotnet/desktop/winforms/controls/how-to-run-an-operation-in-the-background)
- [<span data-ttu-id="58c7f-122">イベントベースの非同期パターンの概要</span><span class="sxs-lookup"><span data-stu-id="58c7f-122">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)
