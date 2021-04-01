---
description: '詳細情報: データフロー ブロックのタスク スケジューラを指定する方法'
title: 方法:データフロー ブロックのタスク スケジューラを指定する
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TPL dataflow library, linking to task scheduler in TPL
- Task Parallel Library, dataflows
- task scheduler, linking from TPL
ms.assetid: 27ece374-ed5b-49ef-9cec-b20db34a65e8
ms.openlocfilehash: e3a803bfa775d8272db5b0d6974b13648136c74e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701795"
---
# <a name="how-to-specify-a-task-scheduler-in-a-dataflow-block"></a><span data-ttu-id="3c269-103">方法:データフロー ブロックのタスク スケジューラを指定する</span><span class="sxs-lookup"><span data-stu-id="3c269-103">How to: Specify a Task Scheduler in a Dataflow Block</span></span>

<span data-ttu-id="3c269-104">このドキュメントでは、アプリケーションでデータ フローを使用する場合に特定のタスク スケジューラを関連付ける方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3c269-104">This document demonstrates how to associate a specific task scheduler when you use dataflow in your application.</span></span> <span data-ttu-id="3c269-105">この例では、Windows フォーム アプリケーションの <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair?displayProperty=nameWithType> クラスを使用して、リーダー タスクがアクティブである場合と、ライター タスクがアクティブである場合を示します。</span><span class="sxs-lookup"><span data-stu-id="3c269-105">The example uses the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair?displayProperty=nameWithType> class in a Windows Forms application to show when reader tasks are active and when a writer task is active.</span></span> <span data-ttu-id="3c269-106">また、<xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> メソッドを使用してデータ フロー ブロックを有効にし、ユーザー インターフェイス スレッドで実行できるようにします。</span><span class="sxs-lookup"><span data-stu-id="3c269-106">It also uses the <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> method to enable a dataflow block to run on the user-interface thread.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="to-create-the-windows-forms-application"></a><span data-ttu-id="3c269-107">Windows フォーム アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="3c269-107">To Create the Windows Forms Application</span></span>  
  
1. <span data-ttu-id="3c269-108">Visual C# または Visual Basic の **Windows フォーム アプリケーション** プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="3c269-108">Create a Visual C# or Visual Basic **Windows Forms Application** project.</span></span> <span data-ttu-id="3c269-109">以降の手順では、プロジェクトの名前は `WriterReadersWinForms` とします。</span><span class="sxs-lookup"><span data-stu-id="3c269-109">In the following steps, the project is named `WriterReadersWinForms`.</span></span>  
  
2. <span data-ttu-id="3c269-110">メイン フォーム Form1.cs (Visual Basic の Form1.vb) のフォーム デザイナーで、4 つの <xref:System.Windows.Forms.CheckBox> コントロールを追加します。</span><span class="sxs-lookup"><span data-stu-id="3c269-110">On the form designer for the main form, Form1.cs (Form1.vb for Visual Basic), add four <xref:System.Windows.Forms.CheckBox> controls.</span></span> <span data-ttu-id="3c269-111"><xref:System.Windows.Forms.Control.Text%2A> プロパティを、`checkBox1` に対しては「**リーダー 1**」に、`checkBox2` に対しては「**リーダー 2**」に、`checkBox3` に対しては「**リーダー 3**」に、そして `checkBox4` に対しては「**ライター**」に設定します。</span><span class="sxs-lookup"><span data-stu-id="3c269-111">Set the <xref:System.Windows.Forms.Control.Text%2A> property to **Reader 1** for `checkBox1`, **Reader 2** for `checkBox2`, **Reader 3** for `checkBox3`, and **Writer** for `checkBox4`.</span></span> <span data-ttu-id="3c269-112">コントロールごとに、<xref:System.Windows.Forms.Control.Enabled%2A> プロパティを `False` に設定します。</span><span class="sxs-lookup"><span data-stu-id="3c269-112">Set the <xref:System.Windows.Forms.Control.Enabled%2A> property for each control to `False`.</span></span>  
  
3. <span data-ttu-id="3c269-113">フォームに <xref:System.Windows.Forms.Timer> コントロールを追加します。</span><span class="sxs-lookup"><span data-stu-id="3c269-113">Add a <xref:System.Windows.Forms.Timer> control to the form.</span></span> <span data-ttu-id="3c269-114"><xref:System.Windows.Forms.Timer.Interval%2A> プロパティを `2500`に設定します。</span><span class="sxs-lookup"><span data-stu-id="3c269-114">Set the <xref:System.Windows.Forms.Timer.Interval%2A> property to `2500`.</span></span>  
  
## <a name="adding-dataflow-functionality"></a><span data-ttu-id="3c269-115">データ フロー機能の追加</span><span class="sxs-lookup"><span data-stu-id="3c269-115">Adding Dataflow Functionality</span></span>  

 <span data-ttu-id="3c269-116">このセクションでは、アプリケーションに参加するデータ フロー ブロックを作成する方法と、各データ フロー ブロックをタスク スケジューラとを関連付ける方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3c269-116">This section describes how to create the dataflow blocks that participate in the application and how to associate each one with a task scheduler.</span></span>  
  
### <a name="to-add-dataflow-functionality-to-the-application"></a><span data-ttu-id="3c269-117">アプリケーションにデータ フロー機能を追加するには</span><span class="sxs-lookup"><span data-stu-id="3c269-117">To Add Dataflow Functionality to the Application</span></span>  
  
1. <span data-ttu-id="3c269-118">プロジェクトで、System.Threading.Tasks.Dataflow.dll への参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="3c269-118">In your project, add a reference to System.Threading.Tasks.Dataflow.dll.</span></span>  
  
2. <span data-ttu-id="3c269-119">Form1.cs (Visual Basic の Form1.vb) に次の `using` ステートメント (Visual Basic では `Imports`) が含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="3c269-119">Ensure that Form1.cs (Form1.vb for Visual Basic) contains the following `using` statements (`Imports` in Visual Basic).</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#1)]  
  
3. <span data-ttu-id="3c269-120"><xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> データ メンバーを `Form1` クラスに追加します。</span><span class="sxs-lookup"><span data-stu-id="3c269-120">Add a <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> data member to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#2)]  
  
4. <span data-ttu-id="3c269-121">`Form1` コンストラクターで、`InitializeComponent` の呼び出しの後に、<xref:System.Windows.Forms.CheckBox> オブジェクトの状態を切り替える <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="3c269-121">In the `Form1` constructor, after the call to `InitializeComponent`, create an <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object that toggles the state of <xref:System.Windows.Forms.CheckBox> objects.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#3)]  
  
5. <span data-ttu-id="3c269-122">`Form1` コンストラクターで、1 つの <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> オブジェクトと 4 つの <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> オブジェクト (各 <xref:System.Windows.Forms.CheckBox> オブジェクトに 1 つの <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> オブジェクト) を作成します。</span><span class="sxs-lookup"><span data-stu-id="3c269-122">In the `Form1` constructor, create a <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> object and four <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objects, one <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object for each <xref:System.Windows.Forms.CheckBox> object.</span></span> <span data-ttu-id="3c269-123">それぞれの <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> オブジェクトに対して <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> オブジェクトを指定します。このオブジェクトの <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> プロパティは、リーダーの場合は <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ConcurrentScheduler%2A> プロパティに設定し、ライターの場合は <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ExclusiveScheduler%2A> プロパティに設定します。</span><span class="sxs-lookup"><span data-stu-id="3c269-123">For each <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object, specify a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ConcurrentScheduler%2A> property for the readers, and the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ExclusiveScheduler%2A> property for the writer.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#4)]  
  
6. <span data-ttu-id="3c269-124">`Form1` コンストラクターで、<xref:System.Windows.Forms.Timer> オブジェクトを開始します。</span><span class="sxs-lookup"><span data-stu-id="3c269-124">In the `Form1` constructor, start the <xref:System.Windows.Forms.Timer> object.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#5)]  
  
7. <span data-ttu-id="3c269-125">メイン フォームのフォーム デザイナーで、タイマーの <xref:System.Windows.Forms.Timer.Tick> イベントのイベント ハンドラーを作成します。</span><span class="sxs-lookup"><span data-stu-id="3c269-125">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.Timer.Tick> event for the timer.</span></span>  
  
8. <span data-ttu-id="3c269-126">タイマーに <xref:System.Windows.Forms.Timer.Tick> イベントを実装します。</span><span class="sxs-lookup"><span data-stu-id="3c269-126">Implement the <xref:System.Windows.Forms.Timer.Tick> event for the timer.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#6)]  
  
 <span data-ttu-id="3c269-127">`toggleCheckBox` データ フロー ブロックはユーザー インターフェイスで機能するので、この操作をユーザー インターフェイス スレッドで実行することが重要です。</span><span class="sxs-lookup"><span data-stu-id="3c269-127">Because the `toggleCheckBox` dataflow block acts on the user interface, it is important that this action occur on the user-interface thread.</span></span> <span data-ttu-id="3c269-128">これを実現するため、構築時にこのオブジェクトは <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> プロパティが <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> に設定された <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> オブジェクトを提供します。</span><span class="sxs-lookup"><span data-stu-id="3c269-128">To accomplish this, during construction this object provides a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3c269-129"><xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A> メソッドは、現行の同期コンテキストで作業を実行する <xref:System.Threading.Tasks.TaskScheduler> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="3c269-129">The <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A> method creates a <xref:System.Threading.Tasks.TaskScheduler> object that performs work on the current synchronization context.</span></span> <span data-ttu-id="3c269-130">`Form1` コンストラクターはユーザー インターフェイス スレッドから呼び出されるので、`toggleCheckBox` データ フロー ブロックに対するアクションも、ユーザー インターフェイス スレッドで実行されます。</span><span class="sxs-lookup"><span data-stu-id="3c269-130">Because the `Form1` constructor is called from the user-interface thread, the action for the `toggleCheckBox` dataflow block also runs on the user-interface thread.</span></span>  
  
 <span data-ttu-id="3c269-131">この例では、<xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> クラスを使用していくつかのデータ フロー ブロックが同時に実行できるようにし、別の 1 つのデータ フロー ブロックが、同じ <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> オブジェクトで実行するその他すべてのデータ フロー ブロックに対して排他的に実行するようにします。</span><span class="sxs-lookup"><span data-stu-id="3c269-131">This example also uses the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> class to enable some dataflow blocks to act concurrently, and another dataflow block to act exclusive with respect to all other dataflow blocks that run on the same <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> object.</span></span> <span data-ttu-id="3c269-132">この手法は、複数のデータ フロー ブロックが 1 つのリソースを共有し、一部のデータ フロー ブロックがそのリソースへの排他アクセスを必要とする場合に、手動でそのリソースへのアクセスを同期する必要がなくなるため、便利です。</span><span class="sxs-lookup"><span data-stu-id="3c269-132">This technique is useful when multiple dataflow blocks share a resource and some require exclusive access to that resource, because it eliminates the requirement to manually synchronize access to that resource.</span></span> <span data-ttu-id="3c269-133">手動で同期する必要がなくなることで、コードの効率性が向上する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3c269-133">The elimination of manual synchronization can make code more efficient.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c269-134">例</span><span class="sxs-lookup"><span data-stu-id="3c269-134">Example</span></span>  

 <span data-ttu-id="3c269-135">次の例は、Form1.cs (Visual Basic の Form1.vb) のコード全体を示しています。</span><span class="sxs-lookup"><span data-stu-id="3c269-135">The following example shows the complete code for Form1.cs (Form1.vb for Visual Basic).</span></span>  
  
 [!code-csharp[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#100)]  
  
## <a name="see-also"></a><span data-ttu-id="3c269-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="3c269-136">See also</span></span>

- [<span data-ttu-id="3c269-137">データフロー</span><span class="sxs-lookup"><span data-stu-id="3c269-137">Dataflow</span></span>](dataflow-task-parallel-library.md)
