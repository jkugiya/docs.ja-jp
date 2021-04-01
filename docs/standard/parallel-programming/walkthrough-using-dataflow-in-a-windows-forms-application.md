---
description: '詳細情報: Windows フォーム アプリケーションでのデータフローの使用に関するチュートリアル'
title: チュートリアル:Windows フォーム アプリケーションでのデータフローの使用
ms.date: 03/30/2017
helpviewer_keywords:
- TPL dataflow library, in Windows Forms
- Task Parallel Library, dataflows
- Windows Forms, and TPL
ms.assetid: 9c65cdf7-660c-409f-89ea-59d7ec8e127c
ms.openlocfilehash: 761f47b3250827a8d5cbee8bb444d172e9ae950f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798044"
---
# <a name="walkthrough-using-dataflow-in-a-windows-forms-application"></a><span data-ttu-id="a67e6-103">チュートリアル:Windows フォーム アプリケーションでのデータフローの使用</span><span class="sxs-lookup"><span data-stu-id="a67e6-103">Walkthrough: Using Dataflow in a Windows Forms Application</span></span>

<span data-ttu-id="a67e6-104">このドキュメントでは、Windows フォーム アプリケーションでイメージ処理を実行する、データフロー ブロックのネットワークを作成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="a67e6-104">This document demonstrates how to create a network of dataflow blocks that perform image processing in a Windows Forms application.</span></span>  
  
 <span data-ttu-id="a67e6-105">この例では、指定したフォルダーからイメージ ファイルを読み込み、複合イメージを作成して、結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="a67e6-105">This example loads image files from the specified folder, creates a composite image, and displays the result.</span></span> <span data-ttu-id="a67e6-106">例では、ネットワーク経由でイメージをルーティングするために、データフロー モデルを使用します。</span><span class="sxs-lookup"><span data-stu-id="a67e6-106">The example uses the dataflow model to route images through the network.</span></span> <span data-ttu-id="a67e6-107">このデータフロー モデルでは、プログラム内の独立したコンポーネント同士が、メッセージを送信することによって相互に通信します。</span><span class="sxs-lookup"><span data-stu-id="a67e6-107">In the dataflow model, independent components of a program communicate with one another by sending messages.</span></span> <span data-ttu-id="a67e6-108">1 つのコンポーネントがメッセージを受信すると、何らかのアクションを実行した後に、結果を別のコンポーネントに渡します。</span><span class="sxs-lookup"><span data-stu-id="a67e6-108">When a component receives a message, it performs some action and then passes the result to another component.</span></span> <span data-ttu-id="a67e6-109">このモデルと制御フロー モデルを比較してください。制御フロー モデルでは、アプリケーションは制御構造 (条件付きステートメントやループなど) を使用してプログラムでの操作順序を制御します。</span><span class="sxs-lookup"><span data-stu-id="a67e6-109">Compare this with the control flow model, in which an application uses control structures, for example, conditional statements, loops, and so on, to control the order of operations in a program.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a67e6-110">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="a67e6-110">Prerequisites</span></span>  

 <span data-ttu-id="a67e6-111">このチュートリアルを開始する前に、「[Dataflow (データフロー)](dataflow-task-parallel-library.md)」をお読みください。</span><span class="sxs-lookup"><span data-stu-id="a67e6-111">Read [Dataflow](dataflow-task-parallel-library.md) before you start this walkthrough.</span></span>  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="sections"></a><span data-ttu-id="a67e6-112">セクション</span><span class="sxs-lookup"><span data-stu-id="a67e6-112">Sections</span></span>  

 <span data-ttu-id="a67e6-113">このチュートリアルは、次のセクションで構成されています。</span><span class="sxs-lookup"><span data-stu-id="a67e6-113">This walkthrough contains the following sections:</span></span>  
  
- [<span data-ttu-id="a67e6-114">Windows フォーム アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="a67e6-114">Creating the Windows Forms Application</span></span>](#winforms)  
  
- [<span data-ttu-id="a67e6-115">データフロー ネットワークの作成</span><span class="sxs-lookup"><span data-stu-id="a67e6-115">Creating the Dataflow Network</span></span>](#network)  
  
- [<span data-ttu-id="a67e6-116">ユーザー インターフェイスへのデータフロー ネットワークの接続</span><span class="sxs-lookup"><span data-stu-id="a67e6-116">Connecting the Dataflow Network to the User Interface</span></span>](#ui)  
  
- [<span data-ttu-id="a67e6-117">完全な例</span><span class="sxs-lookup"><span data-stu-id="a67e6-117">The Complete Example</span></span>](#complete)  
  
<a name="winforms"></a>

## <a name="creating-the-windows-forms-application"></a><span data-ttu-id="a67e6-118">Windows フォーム アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="a67e6-118">Creating the Windows Forms Application</span></span>  

 <span data-ttu-id="a67e6-119">このセクションでは、基本的な Windows フォーム アプリケーションを作成し、メイン フォームにコントロールを追加する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="a67e6-119">This section describes how to create the basic Windows Forms application and add controls to the main form.</span></span>  
  
### <a name="to-create-the-windows-forms-application"></a><span data-ttu-id="a67e6-120">Windows フォーム アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="a67e6-120">To Create the Windows Forms Application</span></span>  
  
1. <span data-ttu-id="a67e6-121">Visual Studio で、Visual C# または Visual Basic **Windows フォーム アプリケーション** プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="a67e6-121">In Visual Studio, create a Visual C# or Visual Basic **Windows Forms Application** project.</span></span> <span data-ttu-id="a67e6-122">このドキュメントでは、プロジェクトの名前を `CompositeImages` とします。</span><span class="sxs-lookup"><span data-stu-id="a67e6-122">In this document, the project is named `CompositeImages`.</span></span>  
  
2. <span data-ttu-id="a67e6-123">メイン フォーム Form1.cs (Visual Basic の Form1.vb) のフォーム デザイナーで、<xref:System.Windows.Forms.ToolStrip> コントロールを追加します。</span><span class="sxs-lookup"><span data-stu-id="a67e6-123">On the form designer for the main form, Form1.cs (Form1.vb for Visual Basic), add a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
3. <span data-ttu-id="a67e6-124"><xref:System.Windows.Forms.ToolStrip> コントロールに <xref:System.Windows.Forms.ToolStripButton> コントロールを追加します。</span><span class="sxs-lookup"><span data-stu-id="a67e6-124">Add a <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="a67e6-125"><xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> プロパティを <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> に設定し、<xref:System.Windows.Forms.ToolStripItem.Text%2A> プロパティを「**フォルダーの選択**」に設定します。</span><span class="sxs-lookup"><span data-stu-id="a67e6-125">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> and the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Choose Folder**.</span></span>  
  
4. <span data-ttu-id="a67e6-126"><xref:System.Windows.Forms.ToolStrip> コントロールに 2 つ目の <xref:System.Windows.Forms.ToolStripButton> コントロールを追加します。</span><span class="sxs-lookup"><span data-stu-id="a67e6-126">Add a second <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="a67e6-127"><xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> プロパティを <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> に、<xref:System.Windows.Forms.ToolStripItem.Text%2A> プロパティを「**キャンセル**」に、<xref:System.Windows.Forms.ToolStripItem.Enabled%2A> プロパティを `False` に設定します。</span><span class="sxs-lookup"><span data-stu-id="a67e6-127">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Cancel**, and the <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> property to `False`.</span></span>  
  
5. <span data-ttu-id="a67e6-128"><xref:System.Windows.Forms.PictureBox> オブジェクトをメイン フォームに追加します。</span><span class="sxs-lookup"><span data-stu-id="a67e6-128">Add a <xref:System.Windows.Forms.PictureBox> object to the main form.</span></span> <span data-ttu-id="a67e6-129"><xref:System.Windows.Forms.Control.Dock%2A> プロパティを <xref:System.Windows.Forms.DockStyle.Fill>に設定します。</span><span class="sxs-lookup"><span data-stu-id="a67e6-129">Set the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
<a name="network"></a>

## <a name="creating-the-dataflow-network"></a><span data-ttu-id="a67e6-130">データフロー ネットワークの作成</span><span class="sxs-lookup"><span data-stu-id="a67e6-130">Creating the Dataflow Network</span></span>  

 <span data-ttu-id="a67e6-131">このセクションでは、イメージ処理を実行するデータフロー ネットワークを作成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="a67e6-131">This section describes how to create the dataflow network that performs image processing.</span></span>  
  
### <a name="to-create-the-dataflow-network"></a><span data-ttu-id="a67e6-132">データフロー ネットワークを作成するには</span><span class="sxs-lookup"><span data-stu-id="a67e6-132">To Create the Dataflow Network</span></span>  
  
1. <span data-ttu-id="a67e6-133">System.Threading.Tasks.Dataflow.dll への参照をプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="a67e6-133">Add a reference to System.Threading.Tasks.Dataflow.dll to your project.</span></span>  
  
2. <span data-ttu-id="a67e6-134">Form1.cs (Visual Basic の Form1.vb) に次の `using` (Visual Basic では `Using`) ステートメントが含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="a67e6-134">Ensure that Form1.cs (Form1.vb for Visual Basic) contains the following `using` (`Using` in Visual Basic) statements:</span></span>  
  
     [!code-csharp[TPLDataflow_CompositeImages#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#1)]  
  
3. <span data-ttu-id="a67e6-135">`Form1` クラスに次のデータ メンバーを追加します。</span><span class="sxs-lookup"><span data-stu-id="a67e6-135">Add the following data members to the `Form1` class:</span></span>  
  
     [!code-csharp[TPLDataflow_CompositeImages#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#2)]  
  
4. <span data-ttu-id="a67e6-136">次の `CreateImageProcessingNetwork` メソッドを `Form1` クラスに追加します。</span><span class="sxs-lookup"><span data-stu-id="a67e6-136">Add the following method, `CreateImageProcessingNetwork`, to the `Form1` class.</span></span> <span data-ttu-id="a67e6-137">このメソッドによって、イメージ処理ネットワークが作成されます。</span><span class="sxs-lookup"><span data-stu-id="a67e6-137">This method creates the image processing network.</span></span>  
  
     [!code-csharp[TPLDataflow_CompositeImages#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#3)]  
  
5. <span data-ttu-id="a67e6-138">`LoadBitmaps` メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="a67e6-138">Implement the `LoadBitmaps` method.</span></span>  
  
     [!code-csharp[TPLDataflow_CompositeImages#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#4)]  
  
6. <span data-ttu-id="a67e6-139">`CreateCompositeBitmap` メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="a67e6-139">Implement the `CreateCompositeBitmap` method.</span></span>  
  
     [!code-csharp[TPLDataflow_CompositeImages#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#5)]  
  
    > [!NOTE]
    > <span data-ttu-id="a67e6-140">`CreateCompositeBitmap` メソッドの C# バージョンでは、ポインターを使って、<xref:System.Drawing.Bitmap?displayProperty=nameWithType> オブジェクトの効率的な処理を実現します。</span><span class="sxs-lookup"><span data-stu-id="a67e6-140">The C# version of the `CreateCompositeBitmap` method uses pointers to enable efficient processing of the <xref:System.Drawing.Bitmap?displayProperty=nameWithType> objects.</span></span> <span data-ttu-id="a67e6-141">したがって、[unsafe](../../csharp/language-reference/keywords/unsafe.md) キーワードを使用するために、プロジェクト内の **[アンセーフ コードの許可]** オプションを有効にしてください。</span><span class="sxs-lookup"><span data-stu-id="a67e6-141">Therefore, you must enable the **Allow unsafe code** option in your project in order to use the [unsafe](../../csharp/language-reference/keywords/unsafe.md) keyword.</span></span> <span data-ttu-id="a67e6-142">Visual C# プロジェクトでアンセーフ コードを有効にする方法については、「[[ビルド] ページ (プロジェクト デザイナー) (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a67e6-142">For more information about how to enable unsafe code in a Visual C# project, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
 <span data-ttu-id="a67e6-143">ネットワークのメンバーを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="a67e6-143">The following table describes the members of the network.</span></span>  
  
|<span data-ttu-id="a67e6-144">メンバー</span><span class="sxs-lookup"><span data-stu-id="a67e6-144">Member</span></span>|<span data-ttu-id="a67e6-145">種類</span><span class="sxs-lookup"><span data-stu-id="a67e6-145">Type</span></span>|<span data-ttu-id="a67e6-146">説明</span><span class="sxs-lookup"><span data-stu-id="a67e6-146">Description</span></span>|  
|------------|----------|-----------------|  
|`loadBitmaps`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|<span data-ttu-id="a67e6-147">フォルダーのパスを入力として取得し、<xref:System.Drawing.Bitmap> オブジェクトのコレクションを出力として生成します。</span><span class="sxs-lookup"><span data-stu-id="a67e6-147">Takes a folder path as input and produces a collection of <xref:System.Drawing.Bitmap> objects as output.</span></span>|  
|`createCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|<span data-ttu-id="a67e6-148"><xref:System.Drawing.Bitmap> オブジェクトのコレクションを入力として取得し、複合ビットマップを出力として生成します。</span><span class="sxs-lookup"><span data-stu-id="a67e6-148">Takes a collection of <xref:System.Drawing.Bitmap> objects as input and produces a composite bitmap as output.</span></span>|  
|`displayCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|<span data-ttu-id="a67e6-149">フォーム上に複合ビットマップを表示します。</span><span class="sxs-lookup"><span data-stu-id="a67e6-149">Displays the composite bitmap on the form.</span></span>|  
|`operationCancelled`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|<span data-ttu-id="a67e6-150">操作が取り消されたことを示すためにイメージを表示し、ユーザーが別のフォルダーを選択できるようにします。</span><span class="sxs-lookup"><span data-stu-id="a67e6-150">Displays an image to indicate that the operation is canceled and enables the user to select another folder.</span></span>|  
  
 <span data-ttu-id="a67e6-151">データフロー ブロックを接続してネットワークを形成するため、この例では <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> メソッドを使います。</span><span class="sxs-lookup"><span data-stu-id="a67e6-151">To connect the dataflow blocks to form a network, this example uses the <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> method.</span></span> <span data-ttu-id="a67e6-152"><xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> メソッドには、ターゲット ブロックがメッセージを受け入れるか拒否するかを決定する <xref:System.Predicate%601> オブジェクトを受け取るオーバーロード バージョンが含まれます。</span><span class="sxs-lookup"><span data-stu-id="a67e6-152">The <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> method contains an overloaded version that takes a <xref:System.Predicate%601> object that determines whether the target block accepts or rejects a message.</span></span> <span data-ttu-id="a67e6-153">このフィルターのしくみによって、メッセージ ブロックは特定の値のみを受信できます。</span><span class="sxs-lookup"><span data-stu-id="a67e6-153">This filtering mechanism enables message blocks to receive only certain values.</span></span> <span data-ttu-id="a67e6-154">この例では、ネットワークが、2 つに分岐します。</span><span class="sxs-lookup"><span data-stu-id="a67e6-154">In this example, the network can branch in one of two ways.</span></span> <span data-ttu-id="a67e6-155">メイン分岐は、ディスクからイメージを読み込み、複合イメージを作成し、フォームにそのイメージを表示します。</span><span class="sxs-lookup"><span data-stu-id="a67e6-155">The main branch loads the images from disk, creates the composite image, and displays that image on the form.</span></span> <span data-ttu-id="a67e6-156">もう 1 つの分岐では、現在の操作がキャンセルされます。</span><span class="sxs-lookup"><span data-stu-id="a67e6-156">The alternate branch cancels the current operation.</span></span> <span data-ttu-id="a67e6-157"><xref:System.Predicate%601> オブジェクトは、メイン分岐に沿ったデータフロー ブロックで、特定のメッセージを拒否することによって、もう 1 つの分岐に切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="a67e6-157">The <xref:System.Predicate%601> objects enable the dataflow blocks along the main branch to switch to the alternative branch by rejecting certain messages.</span></span> <span data-ttu-id="a67e6-158">たとえば、ユーザーが操作をキャンセルした場合、データフロー ブロック `createCompositeBitmap` で、`null` (Visual Basic では `Nothing`) が出力として生成されます。</span><span class="sxs-lookup"><span data-stu-id="a67e6-158">For example, if the user cancels the operation, the dataflow block `createCompositeBitmap` produces `null` (`Nothing` in Visual Basic) as its output.</span></span> <span data-ttu-id="a67e6-159">データフロー ブロック `displayCompositeBitmap` では、`null` 入力値が拒否されるため、メッセージが `operationCancelled` に提供されます。</span><span class="sxs-lookup"><span data-stu-id="a67e6-159">The dataflow block `displayCompositeBitmap` rejects `null` input values, and therefore, the message is offered to `operationCancelled`.</span></span> <span data-ttu-id="a67e6-160">データフロー ブロック `operationCancelled` はすべてのメッセージを受け入れるため、操作が取り消されたことを示すためにイメージを表示します。</span><span class="sxs-lookup"><span data-stu-id="a67e6-160">The dataflow block `operationCancelled` accepts all messages and therefore, displays an image to indicate that the operation is canceled.</span></span>  
  
 <span data-ttu-id="a67e6-161">次の図は、イメージ処理ネットワークを示しています。</span><span class="sxs-lookup"><span data-stu-id="a67e6-161">The following illustration shows the image processing network:</span></span>  
  
 ![イメージ処理ネットワークを示す図。](./media/walkthrough-using-dataflow-in-a-windows-forms-application/dataflow-winforms-image-processing.png)  
  
 <span data-ttu-id="a67e6-163">`displayCompositeBitmap` と `operationCancelled` のデータフロー ブロックはユーザー インターフェイスで機能するので、これらの操作をユーザー インターフェイス スレッドで実行することが重要です。</span><span class="sxs-lookup"><span data-stu-id="a67e6-163">Because the `displayCompositeBitmap` and `operationCancelled` dataflow blocks act on the user interface, it is important that these actions occur on the user-interface thread.</span></span> <span data-ttu-id="a67e6-164">これを実現するため、構築時にこれらのオブジェクトは <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> プロパティが <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> に設定された <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> オブジェクトを提供します。</span><span class="sxs-lookup"><span data-stu-id="a67e6-164">To accomplish this, during construction, these objects each provide a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a67e6-165"><xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> メソッドは、現行の同期コンテキストで作業を実行する <xref:System.Threading.Tasks.TaskScheduler> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="a67e6-165">The <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> method creates a <xref:System.Threading.Tasks.TaskScheduler> object that performs work on the current synchronization context.</span></span> <span data-ttu-id="a67e6-166">ユーザー インターフェイス スレッドで実行される`CreateImageProcessingNetwork` メソッドは、**[フォルダーの選択]** ボタンのハンドラーから呼び出されるため、`displayCompositeBitmap` と`operationCancelled` のデータフロー ブロックのアクションも、ユーザー インターフェイス スレッドで実行されます。</span><span class="sxs-lookup"><span data-stu-id="a67e6-166">Because the `CreateImageProcessingNetwork` method is called from the handler of the **Choose Folder** button, which runs on the user-interface thread, the actions for the `displayCompositeBitmap` and `operationCancelled` dataflow blocks also run on the user-interface thread.</span></span>  
  
 <span data-ttu-id="a67e6-167"><xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> プロパティはデータフロー ブロックの実行を完全にキャンセルするので、この例では、<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> プロパティを設定する代わりに、共有キャンセル トークンを使います。</span><span class="sxs-lookup"><span data-stu-id="a67e6-167">This example uses a shared cancellation token instead of setting the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property because the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property permanently cancels dataflow block execution.</span></span> <span data-ttu-id="a67e6-168">キャンセル トークンによって、この例では、ユーザーが 1 つまたは複数の操作をキャンセルしたときにも、同じデータフロー ネットワークを複数回再利用できます。</span><span class="sxs-lookup"><span data-stu-id="a67e6-168">A cancellation token enables this example to reuse the same dataflow network multiple times, even when the user cancels one or more operations.</span></span> <span data-ttu-id="a67e6-169"><xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> を使ってデータフロー ブロックの実行を完全に取り消す例については、「[方法: データフロー ブロックをキャンセルする](how-to-cancel-a-dataflow-block.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a67e6-169">For an example that uses <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> to permanently cancel the execution of a dataflow block, see [How to: Cancel a Dataflow Block](how-to-cancel-a-dataflow-block.md).</span></span>  
  
<a name="ui"></a>

## <a name="connecting-the-dataflow-network-to-the-user-interface"></a><span data-ttu-id="a67e6-170">ユーザー インターフェイスへのデータフロー ネットワークの接続</span><span class="sxs-lookup"><span data-stu-id="a67e6-170">Connecting the Dataflow Network to the User Interface</span></span>  

 <span data-ttu-id="a67e6-171">このセクションでは、ユーザー インターフェイスにデータフロー ネットワークを接続する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="a67e6-171">This section describes how to connect the dataflow network to the user interface.</span></span> <span data-ttu-id="a67e6-172">複合イメージの作成と、操作のキャンセルは、**[フォルダーの選択]** と **[キャンセル]** の各ボタンから開始されます。</span><span class="sxs-lookup"><span data-stu-id="a67e6-172">The creation of the composite image and cancellation of the operation are initiated from the **Choose Folder** and **Cancel** buttons.</span></span> <span data-ttu-id="a67e6-173">ユーザーがこのいずれかのボタンを選択すると、適切な操作が非同期的に開始されます。</span><span class="sxs-lookup"><span data-stu-id="a67e6-173">When the user chooses either of these buttons, the appropriate action is initiated in an asynchronous manner.</span></span>  
  
### <a name="to-connect-the-dataflow-network-to-the-user-interface"></a><span data-ttu-id="a67e6-174">ユーザー インターフェイスにデータフロー ネットワークを接続するには</span><span class="sxs-lookup"><span data-stu-id="a67e6-174">To Connect the Dataflow Network to the User Interface</span></span>  
  
1. <span data-ttu-id="a67e6-175">メイン フォームのフォーム デザイナーで、**[フォルダーの選択]** ボタンの <xref:System.Windows.Forms.ToolStripItem.Click> イベントのイベント ハンドラーを作成します。</span><span class="sxs-lookup"><span data-stu-id="a67e6-175">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Choose Folder** button.</span></span>  
  
2. <span data-ttu-id="a67e6-176">**[フォルダーの選択]** ボタンの <xref:System.Windows.Forms.ToolStripItem.Click> イベントを実装します。</span><span class="sxs-lookup"><span data-stu-id="a67e6-176">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Choose Folder** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CompositeImages#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#6)]  
  
3. <span data-ttu-id="a67e6-177">メイン フォームのフォーム デザイナーで、**[キャンセル]** ボタンの <xref:System.Windows.Forms.ToolStripItem.Click> イベントのイベント ハンドラーを作成します。</span><span class="sxs-lookup"><span data-stu-id="a67e6-177">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Cancel** button.</span></span>  
  
4. <span data-ttu-id="a67e6-178">**[キャンセル]** ボタンの <xref:System.Windows.Forms.ToolStripItem.Click> イベントを実装します。</span><span class="sxs-lookup"><span data-stu-id="a67e6-178">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Cancel** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CompositeImages#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#7)]  
  
<a name="complete"></a>

## <a name="the-complete-example"></a><span data-ttu-id="a67e6-179">完全な例</span><span class="sxs-lookup"><span data-stu-id="a67e6-179">The Complete Example</span></span>  

 <span data-ttu-id="a67e6-180">次の例は、このチュートリアルのコード全体を示しています。</span><span class="sxs-lookup"><span data-stu-id="a67e6-180">The following example shows the complete code for this walkthrough.</span></span>  
  
 [!code-csharp[TPLDataflow_CompositeImages#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#100)]  
  
 <span data-ttu-id="a67e6-181">次の図は、一般的な \Sample Pictures\ フォルダーの典型的な出力を示しています。</span><span class="sxs-lookup"><span data-stu-id="a67e6-181">The following illustration shows typical output for the common \Sample Pictures\ folder.</span></span>  
  
 <span data-ttu-id="a67e6-182">![Windows フォーム アプリケーション](media/tpldataflow-compositeimages.gif "TPLDataflow_CompositeImages")</span><span class="sxs-lookup"><span data-stu-id="a67e6-182">![The Windows Forms Application](media/tpldataflow-compositeimages.gif "TPLDataflow_CompositeImages")</span></span>  

## <a name="see-also"></a><span data-ttu-id="a67e6-183">関連項目</span><span class="sxs-lookup"><span data-stu-id="a67e6-183">See also</span></span>

- [<span data-ttu-id="a67e6-184">データフロー</span><span class="sxs-lookup"><span data-stu-id="a67e6-184">Dataflow</span></span>](dataflow-task-parallel-library.md)
