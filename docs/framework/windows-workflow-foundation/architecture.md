---
title: Windows Workflow のアーキテクチャ
description: Windows Workflow Foundation により、フロー制御、例外処理、およびその他の機能を備えた環境内で実行される作業単位がアクティビティとしてカプセル化されます。
ms.date: 03/30/2017
ms.assetid: 1d4c6495-d64a-46d0-896a-3a01fac90aa9
ms.openlocfilehash: 81d1414fe5c6e17871dbbd0a2dd78cd8ace21ec6
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96289140"
---
# <a name="windows-workflow-architecture"></a><span data-ttu-id="aa7b9-103">Windows Workflow のアーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="aa7b9-103">Windows Workflow Architecture</span></span>

<span data-ttu-id="aa7b9-104">Windows Workflow Foundation (WF) により、実行時間の長い対話型アプリケーションの開発における抽象化のレベルが引き上げられます。</span><span class="sxs-lookup"><span data-stu-id="aa7b9-104">Windows Workflow Foundation (WF) raises the abstraction level for developing interactive long-running applications.</span></span> <span data-ttu-id="aa7b9-105">作業単位はアクティビティとしてカプセル化されます。</span><span class="sxs-lookup"><span data-stu-id="aa7b9-105">Units of work are encapsulated as activities.</span></span> <span data-ttu-id="aa7b9-106">アクティビティが実行される環境には、フロー制御、例外処理、エラー伝達、状態データの永続化、動作中のワークフローのメモリへの読み込みやアンロード、追跡、トランザクション フローに対応する機能が備わっています。</span><span class="sxs-lookup"><span data-stu-id="aa7b9-106">Activities run in an environment that provides facilities for flow control, exception handling, fault propagation, persistence of state data, loading and unloading of in-progress workflows from memory, tracking, and transaction flow.</span></span>  
  
## <a name="activity-architecture"></a><span data-ttu-id="aa7b9-107">アクティビティのアーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="aa7b9-107">Activity Architecture</span></span>  

 <span data-ttu-id="aa7b9-108">アクティビティは、<xref:System.Activities.Activity>、<xref:System.Activities.CodeActivity>、<xref:System.Activities.AsyncCodeActivity>、または <xref:System.Activities.NativeActivity> から派生する CLR 型として開発されたり、値 <xref:System.Activities.Activity%601>、<xref:System.Activities.CodeActivity%601>、<xref:System.Activities.AsyncCodeActivity%601>、または <xref:System.Activities.NativeActivity%601> を返す CLR 型の変化形として開発されます。</span><span class="sxs-lookup"><span data-stu-id="aa7b9-108">Activities are developed as CLR types that derive from either <xref:System.Activities.Activity>, <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, or <xref:System.Activities.NativeActivity>, or their variants that return a value, <xref:System.Activities.Activity%601>, <xref:System.Activities.CodeActivity%601>, <xref:System.Activities.AsyncCodeActivity%601>, or <xref:System.Activities.NativeActivity%601>.</span></span> <span data-ttu-id="aa7b9-109"><xref:System.Activities.Activity> から派生するアクティビティを開発すると、ユーザーは既存のアクティビティを組み合わせてワークフロー環境で実行される作業単位をすばやく作成できます。</span><span class="sxs-lookup"><span data-stu-id="aa7b9-109">Developing activities that derive from <xref:System.Activities.Activity> allows the user to assemble pre-existing activities to quickly create units of work that execute in the workflow environment.</span></span> <span data-ttu-id="aa7b9-110">一方、<xref:System.Activities.CodeActivity> では、主にアクティビティ引数にアクセスするために <xref:System.Activities.CodeActivityContext> を使用してマネージド コードで作成される実行ロジックが有効になります。</span><span class="sxs-lookup"><span data-stu-id="aa7b9-110"><xref:System.Activities.CodeActivity>, on the other hand, enables execution logic to be authored in managed code using <xref:System.Activities.CodeActivityContext> primarily for access to activity arguments.</span></span> <span data-ttu-id="aa7b9-111"><xref:System.Activities.AsyncCodeActivity> は、非同期タスクを実装するために使用できること以外の点で <xref:System.Activities.CodeActivity> に似ています。</span><span class="sxs-lookup"><span data-stu-id="aa7b9-111"><xref:System.Activities.AsyncCodeActivity> is similar to <xref:System.Activities.CodeActivity> except that it can be used to implement asynchronous tasks.</span></span> <span data-ttu-id="aa7b9-112"><xref:System.Activities.NativeActivity> から派生するアクティビティを開発すると、<xref:System.Activities.NativeActivityContext> を通じてランタイムにアクセスし、子のスケジュール設定、ブックマーク作成、非同期の作業の呼び出し、トランザクションの登録などの機能を使用できます。</span><span class="sxs-lookup"><span data-stu-id="aa7b9-112">Developing activities that derive from <xref:System.Activities.NativeActivity> allows users to access the runtime through the <xref:System.Activities.NativeActivityContext> for functionality like scheduling children, creating bookmarks, invoking asynchronous work, registering transactions, and more.</span></span>  
  
 <span data-ttu-id="aa7b9-113"><xref:System.Activities.Activity> から派生するアクティビティの作成は宣言型です。また、これらのアクティビティは XAML で作成できます。</span><span class="sxs-lookup"><span data-stu-id="aa7b9-113">Authoring activities that derive from <xref:System.Activities.Activity> is declarative and these activities can be authored in XAML.</span></span> <span data-ttu-id="aa7b9-114">次の例では、`Prompt` というアクティビティが、実行の本体用に他のアクティビティを使用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="aa7b9-114">In the following example, an activity called `Prompt` is created using other activities for the execution body.</span></span>  
  
```xml  
<Activity x:Class='Prompt'  
  xmlns:x='http://schemas.microsoft.com/winfx/2006/xaml'  
    xmlns:z='http://schemas.microsoft.com/netfx/2008/xaml/schema'  
xmlns:my='clr-namespace:XAMLActivityDefinition;assembly=XAMLActivityDefinition'  
xmlns:s="clr-namespace:System;assembly=mscorlib"  
xmlns="http://schemas.microsoft.com/2009/workflow">  
<z:SchemaType.Members>  
    <z:SchemaType.SchemaProperty Name='Text' Type=' InArgument(s:String)' />  
  <z:SchemaType.SchemaProperty Name='Response' Type='OutArgument(s:String)' />  
</z:SchemaType.Members>  
  <Sequence>  
    <my:WriteLine Text='[Text]' />  
    <my:ReadLine BookmarkName='r1' Result='[Response]' />  
  </Sequence>  
</Activity>  
```  
  
## <a name="activity-context"></a><span data-ttu-id="aa7b9-115">アクティビティ コンテキスト</span><span class="sxs-lookup"><span data-stu-id="aa7b9-115">Activity Context</span></span>  

 <span data-ttu-id="aa7b9-116"><xref:System.Activities.ActivityContext> は、アクティビティ作成者のワークフロー ランタイムへのインターフェイスであり、ランタイムのさまざまな機能にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="aa7b9-116">The <xref:System.Activities.ActivityContext> is the activity author's interface to the workflow runtime and provides access to the runtime's wealth of features.</span></span> <span data-ttu-id="aa7b9-117">次の例では、ブックマーク (データをアクティビティに渡してホストが再開できる、実行の継続点をアクティビティが登録できる方法) を作成する実行コンテキストを使用するアクティビティが定義されています。</span><span class="sxs-lookup"><span data-stu-id="aa7b9-117">In the following example, an activity is defined that uses the execution context to create a bookmark (the mechanism that allows an activity to register a continuation point in its execution that can be resumed by a host passing data into the activity).</span></span>  
  
 [!code-csharp[CFX_WorkflowApplicationExample#15](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#15)]  
  
## <a name="activity-life-cycle"></a><span data-ttu-id="aa7b9-118">アクティビティ ライフ サイクル</span><span class="sxs-lookup"><span data-stu-id="aa7b9-118">Activity Life Cycle</span></span>  

 <span data-ttu-id="aa7b9-119">アクティビティのインスタンスは <xref:System.Activities.ActivityInstanceState.Executing> 状態で開始します。</span><span class="sxs-lookup"><span data-stu-id="aa7b9-119">An instance of an activity starts out in the <xref:System.Activities.ActivityInstanceState.Executing> state.</span></span> <span data-ttu-id="aa7b9-120">例外が検出された場合を除き、すべての子アクティビティが実行を終了し、他の保留中の作業 (<xref:System.Activities.Bookmark> オブジェクトなど) が完了するまでこの状態が維持されてから、<xref:System.Activities.ActivityInstanceState.Closed> 状態に移行します。</span><span class="sxs-lookup"><span data-stu-id="aa7b9-120">Unless exceptions are encountered, it remains in this state until all child activities are finished executing and any other pending work (<xref:System.Activities.Bookmark> objects, for instance) is completed, at which point it transitions to the <xref:System.Activities.ActivityInstanceState.Closed> state.</span></span> <span data-ttu-id="aa7b9-121">アクティビティ インスタンスの親は子にキャンセルを要求できます。子がキャンセル可能な場合、子は <xref:System.Activities.ActivityInstanceState.Canceled> 状態で完了します。</span><span class="sxs-lookup"><span data-stu-id="aa7b9-121">The parent of an activity instance can request a child to cancel; if the child is able to be canceled it completes in the <xref:System.Activities.ActivityInstanceState.Canceled> state.</span></span> <span data-ttu-id="aa7b9-122">実行中に例外がスローされた場合は、ランタイムはアクティビティを <xref:System.Activities.ActivityInstanceState.Faulted> 状態にし、アクティビティの親チェーンの上方向へ例外を伝達します。</span><span class="sxs-lookup"><span data-stu-id="aa7b9-122">If an exception is thrown during execution, the runtime puts the activity into the <xref:System.Activities.ActivityInstanceState.Faulted> state and propagates the exception up the parent chain of activities.</span></span> <span data-ttu-id="aa7b9-123">アクティビティの 3 つの完了状態を次に示します。</span><span class="sxs-lookup"><span data-stu-id="aa7b9-123">The following are the three completion states of an activity:</span></span>
  
- <span data-ttu-id="aa7b9-124">**Closed:** アクティビティは作業を完了し、終了しました。</span><span class="sxs-lookup"><span data-stu-id="aa7b9-124">**Closed:** The activity has completed its work and exited.</span></span>  
  
- <span data-ttu-id="aa7b9-125">**Canceled:** アクティビティは作業を正常に中断し、終了しました。</span><span class="sxs-lookup"><span data-stu-id="aa7b9-125">**Canceled:** The activity has gracefully abandoned its work and exited.</span></span> <span data-ttu-id="aa7b9-126">この状態に移行した場合、作業は明示的にロール バックされません。</span><span class="sxs-lookup"><span data-stu-id="aa7b9-126">Work is not explicitly rolled back when this state is entered.</span></span>  
  
- <span data-ttu-id="aa7b9-127">**Faulted:** アクティビティによってエラーが検出され、作業が完了されずに終了しました。</span><span class="sxs-lookup"><span data-stu-id="aa7b9-127">**Faulted:** The activity has encountered an error and has exited without completing its work.</span></span>  
  
 <span data-ttu-id="aa7b9-128">アクティビティは、永続化またはアンロードされても <xref:System.Activities.ActivityInstanceState.Executing> 状態を維持します。</span><span class="sxs-lookup"><span data-stu-id="aa7b9-128">Activities remain in the <xref:System.Activities.ActivityInstanceState.Executing> state when they are persisted or unloaded.</span></span>
