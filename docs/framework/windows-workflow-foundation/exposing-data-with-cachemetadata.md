---
description: '詳細情報: CacheMetadata を使用したデータの公開'
title: CacheMetadata を使用したデータの公開
ms.date: 03/30/2017
ms.assetid: 34832f23-e93b-40e6-a80b-606a855a00d9
ms.openlocfilehash: ac4623881ebd76270f773a3b7acfe205ad365118
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742343"
---
# <a name="exposing-data-with-cachemetadata"></a><span data-ttu-id="a7a0b-103">CacheMetadata を使用したデータの公開</span><span class="sxs-lookup"><span data-stu-id="a7a0b-103">Exposing data with CacheMetadata</span></span>

<span data-ttu-id="a7a0b-104">アクティビティを実行する前に、ワークフロー ランタイムは実行を維持するために必要なアクティビティに関するすべての情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="a7a0b-104">Before executing an activity, the workflow runtime obtains all of the information about the activity that it needs in order to maintain its execution.</span></span> <span data-ttu-id="a7a0b-105">ワークフロー ランタイムは <xref:System.Activities.Activity.CacheMetadata%2A> メソッドの実行時にこの情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="a7a0b-105">The workflow runtime gets this information during the execution of the <xref:System.Activities.Activity.CacheMetadata%2A> method.</span></span> <span data-ttu-id="a7a0b-106">このメソッドの既定の実装は、アクティビティによって公開されたすべてのパブリック引数、変数、子アクティビティを実行時にランタイムに提供します。アクティビティがランタイムにその他の情報 (プライベート メンバーやアクティビティによってスケジュールされるアクティビティなど) を提供する必要がある場合、このメソッドをオーバーライドして情報を提供できます。</span><span class="sxs-lookup"><span data-stu-id="a7a0b-106">The default implementation of this method provides the runtime with all of the public arguments, variables, and child activities exposed by the activity at the time it is executed; if the activity needs to give more information to the runtime than this (such as private members, or activities to be scheduled by the activity), this method can be overridden to provide it.</span></span>

## <a name="default-cachemetadata-behavior"></a><span data-ttu-id="a7a0b-107">CacheMetadata の既定の動作</span><span class="sxs-lookup"><span data-stu-id="a7a0b-107">Default CacheMetadata behavior</span></span>

<span data-ttu-id="a7a0b-108"><xref:System.Activities.NativeActivity.CacheMetadata%2A> から派生したアクティビティの <xref:System.Activities.NativeActivity> の既定の実装は、次のメソッド型を以下の方法で処理します。</span><span class="sxs-lookup"><span data-stu-id="a7a0b-108">The default implementation of <xref:System.Activities.NativeActivity.CacheMetadata%2A> for activities that derive from <xref:System.Activities.NativeActivity> processes the following method types in the following ways:</span></span>

- <span data-ttu-id="a7a0b-109"><xref:System.Activities.InArgument%601>、<xref:System.Activities.OutArgument%601>、または <xref:System.Activities.InOutArgument%601> (ジェネリック引数): これらの引数は公開されたプロパティと同じ名前、データ型、引数の方向、および検証データで引数としてランタイムに公開されます。</span><span class="sxs-lookup"><span data-stu-id="a7a0b-109"><xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, or <xref:System.Activities.InOutArgument%601> (generic arguments): These arguments are exposed to the runtime as arguments with a name and type equal to the exposed property name and type, the appropriate argument direction, and some validation data.</span></span>

- <span data-ttu-id="a7a0b-110"><xref:System.Activities.Variable> またはそのサブクラス: これらのメンバーはパブリック変数としてランタイムに公開されます。</span><span class="sxs-lookup"><span data-stu-id="a7a0b-110"><xref:System.Activities.Variable> or any subclass thereof: These members are exposed to the runtime as public variables.</span></span>

- <span data-ttu-id="a7a0b-111"><xref:System.Activities.Activity> またはそのサブクラス: これらのメンバーはパブリック子アクティビティとしてランタイムに公開されます。</span><span class="sxs-lookup"><span data-stu-id="a7a0b-111"><xref:System.Activities.Activity> or any subclass thereof: These members are exposed to the runtime as public child activities.</span></span> <span data-ttu-id="a7a0b-112">既定の動作は、を呼び出して子アクティビティを渡すことによって、明示的に実装でき <xref:System.Activities.ActivityMetadata.AddImportedChild%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="a7a0b-112">The default behavior can be implemented explicitly by calling <xref:System.Activities.ActivityMetadata.AddImportedChild%2A>, passing in the child activity.</span></span>

- <span data-ttu-id="a7a0b-113"><xref:System.Activities.ActivityDelegate> またはそのサブクラス: これらのメンバーはパブリック デリゲートとしてランタイムに公開されます。</span><span class="sxs-lookup"><span data-stu-id="a7a0b-113"><xref:System.Activities.ActivityDelegate> or any subclass thereof: These members are exposed to the runtime as public delegates.</span></span>

- <span data-ttu-id="a7a0b-114"><xref:System.Activities.Variable> 型の <xref:System.Collections.ICollection>: コレクション内のすべての要素がパブリック変数としてランタイムに公開されます。</span><span class="sxs-lookup"><span data-stu-id="a7a0b-114"><xref:System.Collections.ICollection> of type <xref:System.Activities.Variable>: All elements in the collection are exposed to the runtime as public variables.</span></span>

- <span data-ttu-id="a7a0b-115"><xref:System.Collections.ICollection> 型の <xref:System.Activities.Activity>: コレクション内のすべての要素がパブリック子としてランタイムに公開されます。</span><span class="sxs-lookup"><span data-stu-id="a7a0b-115"><xref:System.Collections.ICollection> of type <xref:System.Activities.Activity>: All elements in the collection are exposed to the runtime as public children.</span></span>

- <span data-ttu-id="a7a0b-116"><xref:System.Activities.ActivityDelegate> 型の <xref:System.Collections.ICollection>: コレクション内のすべての要素がパブリック デリゲートとしてランタイムに公開されます。</span><span class="sxs-lookup"><span data-stu-id="a7a0b-116"><xref:System.Collections.ICollection> of type <xref:System.Activities.ActivityDelegate>: All elements in the collection are exposed to the runtime as public delegates.</span></span>

<span data-ttu-id="a7a0b-117"><xref:System.Activities.Activity.CacheMetadata%2A>、<xref:System.Activities.Activity>、および <xref:System.Workflow.Activities.CodeActivity> から派生したアクティビティの <xref:System.Activities.AsyncCodeActivity> も次の相違点を除いて前述と同様に機能します。</span><span class="sxs-lookup"><span data-stu-id="a7a0b-117">The <xref:System.Activities.Activity.CacheMetadata%2A> for activities that derive from <xref:System.Activities.Activity>, <xref:System.Workflow.Activities.CodeActivity>, and <xref:System.Activities.AsyncCodeActivity> also function as above, except for the following differences:</span></span>

- <span data-ttu-id="a7a0b-118"><xref:System.Activities.Activity> から派生したクラスは子アクティビティまたはデリゲートをスケジュールできないため、これらのメンバーはインポートされた子およびデリゲートとして公開されます。</span><span class="sxs-lookup"><span data-stu-id="a7a0b-118">Classes that derive from <xref:System.Activities.Activity> cannot schedule child activities or delegates, so such members are exposed as imported children and delegates; the</span></span>

- <span data-ttu-id="a7a0b-119"><xref:System.Activities.CodeActivity> および <xref:System.Activities.AsyncCodeActivity> から派生したクラスは変数、子、またはデリゲートをサポートしないため、引数のみが公開されます。</span><span class="sxs-lookup"><span data-stu-id="a7a0b-119">Classes that derive from <xref:System.Activities.CodeActivity> and <xref:System.Activities.AsyncCodeActivity> do not support variables, children, or delegates, so only arguments will be exposed.</span></span>

## <a name="overriding-cachemetadata-to-provide-information-to-the-runtime"></a><span data-ttu-id="a7a0b-120">CacheMetadata をオーバーライドしてランタイムに情報を提供する</span><span class="sxs-lookup"><span data-stu-id="a7a0b-120">Overriding CacheMetadata to provide information to the runtime</span></span>

<span data-ttu-id="a7a0b-121">次のコード スニペットは、<xref:System.Activities.Activity.CacheMetadata%2A> メソッドの実行時にメンバーに関する情報をアクティビティのメタデータに追加する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="a7a0b-121">The following code snippet demonstrates how to add information about members to an activity’s metadata during the execution of the <xref:System.Activities.Activity.CacheMetadata%2A> method.</span></span> <span data-ttu-id="a7a0b-122">メソッドの base を呼び出して、アクティビティに関するすべてのパブリック データをキャッシュしています。</span><span class="sxs-lookup"><span data-stu-id="a7a0b-122">Note that the base of the method is called to cache all public data about the activity.</span></span>

```csharp
protected override void CacheMetadata(NativeActivityMetadata metadata)
{
    base.CacheMetadata(metadata);
    metadata.AddImplementationChild(this._writeLine);
    metadata.AddVariable(this._myVariable);
    metadata.AddImplementationVariable(this._myImplementationVariable);

    RuntimeArgument argument = new RuntimeArgument("MyArgument", ArgumentDirection.In, typeof(SomeType));
    metadata.Bind(argument, this.SomeName);
    metadata.AddArgument(argument);
}
```

## <a name="using-cachemetadata-to-expose-implementation-children"></a><span data-ttu-id="a7a0b-123">CacheMetadata を使用して実装の子を公開する</span><span class="sxs-lookup"><span data-stu-id="a7a0b-123">Using CacheMetadata to expose implementation children</span></span>

<span data-ttu-id="a7a0b-124">アクティビティによってスケジュールされる子アクティビティに変数を使用してデータを渡すには、変数を実装変数として追加する必要があります。パブリック変数ではこの方法で値を設定することはできません。</span><span class="sxs-lookup"><span data-stu-id="a7a0b-124">In order to pass data to child activities that are to be scheduled by an activity using variables, it is necessary to add the variables as implementation variables; public variables cannot have their values set this way.</span></span> <span data-ttu-id="a7a0b-125">その理由は、アクティビティはカプセル化されたクラス (プロパティを持つ) としてよりも、関数 (パラメーターを持つ) の実装として実行することを目的としているためです。</span><span class="sxs-lookup"><span data-stu-id="a7a0b-125">The reason for this is that activities are intended to be executed more as implementations of functions (which have parameters), rather than encapsulated classes (which have properties).</span></span> <span data-ttu-id="a7a0b-126">ただし、場合によっては引数を明示的に設定する必要があります。たとえば、スケジュールされたアクティビティは親アクティビティの引数に子アクティビティと同じ方法でアクセスすることはできないため、<xref:System.Activities.NativeActivityContext.ScheduleActivity%2A> を使用する場合には引数の明示的な設定が必要です。</span><span class="sxs-lookup"><span data-stu-id="a7a0b-126">However, there are situations in which the arguments must be explicitly set, such as when using <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>, since the scheduled activity doesn't have access to the parent activity's arguments in the way a child activity would.</span></span>

<span data-ttu-id="a7a0b-127">次のコード スニペットは、<xref:System.Activities.Activity.CacheMetadata%2A> を使用してネイティブ アクティビティからスケジュールされたアクティビティに引数を渡す方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="a7a0b-127">The following code snippet demonstrates how to pass an argument form a native activity into a scheduled activity using <xref:System.Activities.Activity.CacheMetadata%2A>.</span></span>

```csharp
public sealed class ChildActivity : NativeActivity
{
    public WriteLine _writeLine;
    public InArgument<string> Message { get; set; }
    private Variable<string> MessageVariable { get; set; }
    public ChildActivity()
    {
        MessageVariable = new Variable<string>();
        _writeLine = new WriteLine
        {
            Text = new InArgument<string>(MessageVariable),
        };
    }
    protected override void CacheMetadata(NativeActivityMetadata metadata)
    {
        base.CacheMetadata(metadata);
        metadata.AddImplementationVariable(this.MessageVariable);
        metadata.AddImplementationChild(this._writeLine);
    }
    protected override void Execute(NativeActivityContext context)
    {
        string configuredMessage = context.GetValue(Message);
        context.SetValue(MessageVariable, configuredMessage);
        context.ScheduleActivity(this._writeLine);
    }
}
```
