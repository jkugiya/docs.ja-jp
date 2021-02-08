---
description: 詳細については、「ブックマーク」を参照してください。
title: ブックマーク-WF
ms.date: 03/30/2017
ms.assetid: 9b51a346-09ae-455c-a70a-e2264ddeb9e2
ms.openlocfilehash: b4f0e68e0868ecd4eb97673ff6c09ee8c806cf43
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787930"
---
# <a name="bookmarks"></a><span data-ttu-id="06b34-103">ブックマーク</span><span class="sxs-lookup"><span data-stu-id="06b34-103">Bookmarks</span></span>

<span data-ttu-id="06b34-104">ブックマークは、ワークフローのスレッド上に保持することなく、アクティビティが受動的に入力を待機できるようにする機構です。</span><span class="sxs-lookup"><span data-stu-id="06b34-104">Bookmarks are the mechanism that enables an activity to passively wait for input without holding onto a workflow thread.</span></span> <span data-ttu-id="06b34-105">アクティビティが働きかけを待機していることを示すときは、ブックマークを作成できます。</span><span class="sxs-lookup"><span data-stu-id="06b34-105">When an activity signals that it is waiting for stimulus, it can create a bookmark.</span></span> <span data-ttu-id="06b34-106">これは、現在実行中の (<xref:System.Activities.Bookmark> を作成した) メソッドから返された場合でも、アクティビティの実行が完了していると見なさないことをランタイムに対して示します。</span><span class="sxs-lookup"><span data-stu-id="06b34-106">This indicates to the runtime that the activity’s execution should not be considered complete even when the currently executing method (which created the <xref:System.Activities.Bookmark>) returns.</span></span>  
  
## <a name="bookmark-basics"></a><span data-ttu-id="06b34-107">ブックマークの基本</span><span class="sxs-lookup"><span data-stu-id="06b34-107">Bookmark Basics</span></span>  

 <span data-ttu-id="06b34-108"><xref:System.Activities.Bookmark> は、ワークフロー インスタンス内で実行を再開できるポイント (および入力を渡すことができるポイント) を表します。</span><span class="sxs-lookup"><span data-stu-id="06b34-108">A <xref:System.Activities.Bookmark> represents a point at which execution can be resumed (and through which input can be delivered) within a workflow instance.</span></span> <span data-ttu-id="06b34-109">通常、<xref:System.Activities.Bookmark> には名前が付けられ、外部 (ホストまたは拡張) コードで、関連データを含むブックマークを再開する処理を実行します。</span><span class="sxs-lookup"><span data-stu-id="06b34-109">Typically, a <xref:System.Activities.Bookmark> is given a name and external (host or extension) code is responsible for resuming the bookmark with relevant data.</span></span> <span data-ttu-id="06b34-110"><xref:System.Activities.Bookmark> を再開すると、ワークフロー ランタイムは、作成時に、その <xref:System.Activities.BookmarkCallback> と関連付けられた <xref:System.Activities.Bookmark> のデリゲートをスケジュールします。</span><span class="sxs-lookup"><span data-stu-id="06b34-110">When a <xref:System.Activities.Bookmark> is resumed, the workflow runtime schedules the <xref:System.Activities.BookmarkCallback> delegate that was associated with that <xref:System.Activities.Bookmark> at the time of its creation.</span></span>  
  
## <a name="bookmark-options"></a><span data-ttu-id="06b34-111">ブックマークのオプション</span><span class="sxs-lookup"><span data-stu-id="06b34-111">Bookmark Options</span></span>  

 <span data-ttu-id="06b34-112"><xref:System.Activities.BookmarkOptions> クラスは、作成する <xref:System.Activities.Bookmark> の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="06b34-112">The <xref:System.Activities.BookmarkOptions> class specifies the type of <xref:System.Activities.Bookmark> being created.</span></span> <span data-ttu-id="06b34-113">互いに矛盾しない値として、<xref:System.Activities.BookmarkOptions.None>、<xref:System.Activities.BookmarkOptions.MultipleResume>、および <xref:System.Activities.BookmarkOptions.NonBlocking> があります。</span><span class="sxs-lookup"><span data-stu-id="06b34-113">The possible non mutually-exclusive values are <xref:System.Activities.BookmarkOptions.None>, <xref:System.Activities.BookmarkOptions.MultipleResume>, and <xref:System.Activities.BookmarkOptions.NonBlocking>.</span></span> <span data-ttu-id="06b34-114">1 度のみ再開される想定の <xref:System.Activities.BookmarkOptions.None> を作成する場合、既定では <xref:System.Activities.Bookmark> を使用します。</span><span class="sxs-lookup"><span data-stu-id="06b34-114">Use <xref:System.Activities.BookmarkOptions.None>, the default, when creating a <xref:System.Activities.Bookmark> that is expected to be resumed exactly once.</span></span> <span data-ttu-id="06b34-115">複数回再開できる <xref:System.Activities.BookmarkOptions.MultipleResume> を作成する場合は、<xref:System.Activities.Bookmark> を使用します。</span><span class="sxs-lookup"><span data-stu-id="06b34-115">Use <xref:System.Activities.BookmarkOptions.MultipleResume> when creating a <xref:System.Activities.Bookmark> that can be resumed multiple times.</span></span> <span data-ttu-id="06b34-116">再開しない <xref:System.Activities.BookmarkOptions.NonBlocking> を作成する場合は、<xref:System.Activities.Bookmark> を使用します。</span><span class="sxs-lookup"><span data-stu-id="06b34-116">Use <xref:System.Activities.BookmarkOptions.NonBlocking> when creating a <xref:System.Activities.Bookmark> that might never be resumed.</span></span> <span data-ttu-id="06b34-117">既定の <xref:System.Activities.BookmarkOptions> を使用して作成されるブックマークとは異なり、<xref:System.Activities.BookmarkOptions.NonBlocking> ブックマークはアクティビティの完了を妨げません。</span><span class="sxs-lookup"><span data-stu-id="06b34-117">Unlike bookmarks created using the default <xref:System.Activities.BookmarkOptions>, <xref:System.Activities.BookmarkOptions.NonBlocking> bookmarks do not prevent an activity from completing.</span></span>  
  
## <a name="bookmark-resumption"></a><span data-ttu-id="06b34-118">ブックマークの再開</span><span class="sxs-lookup"><span data-stu-id="06b34-118">Bookmark Resumption</span></span>  

 <span data-ttu-id="06b34-119">ブックマークは、ワークフロー以外のコードから、<xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> オーバーロードのいずれかを使用して再開できます。</span><span class="sxs-lookup"><span data-stu-id="06b34-119">Bookmarks can be resumed by code outside of a workflow using one of the <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> overloads.</span></span> <span data-ttu-id="06b34-120">この例では、`ReadLine` アクティビティが作成されます。</span><span class="sxs-lookup"><span data-stu-id="06b34-120">In this example, a `ReadLine` activity is created.</span></span> <span data-ttu-id="06b34-121">実行されると、`ReadLine` アクティビティは <xref:System.Activities.Bookmark> を作成し、コールバックを登録してから、<xref:System.Activities.Bookmark> が再開されるのを待機します。</span><span class="sxs-lookup"><span data-stu-id="06b34-121">When executed, the `ReadLine` activity creates a <xref:System.Activities.Bookmark>, registers a callback, and then waits for the <xref:System.Activities.Bookmark> to be resumed.</span></span> <span data-ttu-id="06b34-122">再開されると、`ReadLine` アクティビティは <xref:System.Activities.Bookmark> と一緒に渡されたデータを <xref:System.Activities.Activity%601.Result%2A> 引数に代入します。</span><span class="sxs-lookup"><span data-stu-id="06b34-122">When it is resumed, the `ReadLine` activity assigns the data that was passed with the <xref:System.Activities.Bookmark> to its <xref:System.Activities.Activity%601.Result%2A> argument.</span></span>  
  
```csharp  
public sealed class ReadLine : NativeActivity<string>  
{  
    [RequiredArgument]  
    public  InArgument<string> BookmarkName { get; set; }  
  
    protected override void Execute(NativeActivityContext context)  
    {  
        // Create a Bookmark and wait for it to be resumed.  
        context.CreateBookmark(BookmarkName.Get(context),
            new BookmarkCallback(OnResumeBookmark));  
    }  
  
    // NativeActivity derived activities that do asynchronous operations by calling
    // one of the CreateBookmark overloads defined on System.Activities.NativeActivityContext
    // must override the CanInduceIdle property and return true.  
    protected override bool CanInduceIdle  
    {  
        get { return true; }  
    }  
  
    public void OnResumeBookmark(NativeActivityContext context, Bookmark bookmark, object obj)  
    {  
        // When the Bookmark is resumed, assign its value to  
        // the Result argument.  
        Result.Set(context, (string)obj);  
    }  
}  
```  
  
 <span data-ttu-id="06b34-123">次の例では、`ReadLine` アクティビティを使用してユーザー名を収集し、それをコンソール ウィンドウに表示するワークフローを作成します。</span><span class="sxs-lookup"><span data-stu-id="06b34-123">In this example, a workflow is created that uses the `ReadLine` activity to gather the user’s name and display it to the console window.</span></span> <span data-ttu-id="06b34-124">ホスト アプリケーションは入力を収集する実際の作業を実行し、<xref:System.Activities.Bookmark> を再開することでワークフローに渡します。</span><span class="sxs-lookup"><span data-stu-id="06b34-124">The host application performs the actual work of gathering the input and passes it to the workflow by resuming the <xref:System.Activities.Bookmark>.</span></span>  
  
```csharp  
Variable<string> name = new Variable<string>  
{  
    Name = "name"  
};  
  
Activity wf = new Sequence  
{  
    Variables =  
    {  
        name  
    },  
    Activities =  
    {  
        new WriteLine()  
        {  
            Text = "What is your name?"  
        },  
        new ReadLine()  
        {  
            BookmarkName = "UserName",  
            Result = name  
        },  
        new WriteLine()  
        {  
            Text = new InArgument<string>((env) => "Hello, " + name.Get(env))  
        }  
    }  
};  
  
AutoResetEvent syncEvent = new AutoResetEvent(false);  
  
// Create the WorkflowApplication using the desired  
// workflow definition.  
WorkflowApplication wfApp = new WorkflowApplication(wf);  
  
// Handle the desired lifecycle events.  
wfApp.Completed = delegate(WorkflowApplicationCompletedEventArgs e)  
{  
    // Signal the host that the workflow is complete.  
    syncEvent.Set();  
};  
  
// Start the workflow.  
wfApp.Run();  
  
// Collect the user's name and resume the bookmark.  
// Bookmark resumption only occurs when the workflow  
// is idle. If a call to ResumeBookmark is made and the workflow  
// is not idle, ResumeBookmark blocks until the workflow becomes  
// idle before resuming the bookmark.  
wfApp.ResumeBookmark("UserName", Console.ReadLine());  
  
// Wait for Completed to arrive and signal that  
// the workflow is complete.  
syncEvent.WaitOne();  
```  
  
 <span data-ttu-id="06b34-125">`ReadLine` アクティビティが実行されると、<xref:System.Activities.Bookmark> という名前の `UserName` が作成され、ブックマークが再開されるのを待機します。</span><span class="sxs-lookup"><span data-stu-id="06b34-125">When the `ReadLine` activity is executed, it creates a <xref:System.Activities.Bookmark> named `UserName` and then waits for the bookmark to be resumed.</span></span> <span data-ttu-id="06b34-126">ホストは必要なデータを収集し、<xref:System.Activities.Bookmark> を再開します。</span><span class="sxs-lookup"><span data-stu-id="06b34-126">The host collects the desired data and then resumes the <xref:System.Activities.Bookmark>.</span></span> <span data-ttu-id="06b34-127">ワークフローが再開されると名前が表示されて、完了します。</span><span class="sxs-lookup"><span data-stu-id="06b34-127">The workflow resumes, displays the name, and then completes.</span></span> <span data-ttu-id="06b34-128">ブックマークの再開に関して、同期コードは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="06b34-128">Note that no synchronization code is required with regard to resuming the bookmark.</span></span> <span data-ttu-id="06b34-129"><xref:System.Activities.Bookmark> を再開できるのは、ワークフローがアイドルの場合のみです。ワークフローがアイドルではない場合、<xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> を呼び出すと、ワークフローがアイドルになるまでブロックされます。</span><span class="sxs-lookup"><span data-stu-id="06b34-129">A <xref:System.Activities.Bookmark> can only be resumed when the workflow is idle, and if the workflow is not idle, the call to <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> blocks until the workflow becomes idle.</span></span>  
  
## <a name="bookmark-resumption-result"></a><span data-ttu-id="06b34-130">ブックマークの再開結果</span><span class="sxs-lookup"><span data-stu-id="06b34-130">Bookmark Resumption Result</span></span>  

 <span data-ttu-id="06b34-131"><xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> は、ブックマークの再開要求の結果を示す <xref:System.Activities.BookmarkResumptionResult> 列挙値を返します。</span><span class="sxs-lookup"><span data-stu-id="06b34-131"><xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> returns a <xref:System.Activities.BookmarkResumptionResult> enumeration value to indicate the results of the bookmark resumption request.</span></span> <span data-ttu-id="06b34-132">戻り値には <xref:System.Activities.BookmarkResumptionResult.Success>、<xref:System.Activities.BookmarkResumptionResult.NotReady>、および <xref:System.Activities.BookmarkResumptionResult.NotFound> があります。</span><span class="sxs-lookup"><span data-stu-id="06b34-132">The possible return values are <xref:System.Activities.BookmarkResumptionResult.Success>, <xref:System.Activities.BookmarkResumptionResult.NotReady>, and <xref:System.Activities.BookmarkResumptionResult.NotFound>.</span></span> <span data-ttu-id="06b34-133">ホストと拡張ではこの値を使用して処理の進め方を決定します。</span><span class="sxs-lookup"><span data-stu-id="06b34-133">Hosts and extensions can use this value to determine how to proceed.</span></span>
