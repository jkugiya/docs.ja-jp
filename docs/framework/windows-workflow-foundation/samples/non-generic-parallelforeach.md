---
description: 詳細については、「非汎用 ParallelForEach」を参照してください。
title: 非ジェネリック ParallelForEach
ms.date: 03/30/2017
ms.assetid: de17e7a2-257b-48b3-91a1-860e2e9bf6e6
ms.openlocfilehash: 9eaa4ed565fa00a0479f21d907fe5433317d88f8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741940"
---
# <a name="non-generic-parallelforeach"></a><span data-ttu-id="b5083-103">非ジェネリック ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="b5083-103">Non-generic ParallelForEach</span></span>

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] <span data-ttu-id="b5083-104">のツールボックスには、制御フロー アクティビティのセットが用意されています。これには、<xref:System.Activities.Statements.ParallelForEach%601> コレクションを反復処理できる <xref:System.Collections.Generic.IEnumerable%601> が含まれています。</span><span class="sxs-lookup"><span data-stu-id="b5083-104">ships in its toolbox a set of Control Flow activities, including <xref:System.Activities.Statements.ParallelForEach%601>, which allows iterating through <xref:System.Collections.Generic.IEnumerable%601> collections.</span></span>

<span data-ttu-id="b5083-105"><xref:System.Activities.Statements.ParallelForEach%601> プロパティが <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> 型である必要があり  <xref:System.Collections.Generic.IEnumerable%601> ます。</span><span class="sxs-lookup"><span data-stu-id="b5083-105"><xref:System.Activities.Statements.ParallelForEach%601> requires its <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> property to be of type  <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="b5083-106">このため、ユーザーは、<xref:System.Collections.Generic.IEnumerable%601> インターフェイス (<xref:System.Collections.ArrayList> など) を実装するデータ構造を反復処理できません。</span><span class="sxs-lookup"><span data-stu-id="b5083-106">This precludes users from iterating over data structures that implement <xref:System.Collections.Generic.IEnumerable%601> interface (for example, <xref:System.Collections.ArrayList>).</span></span> <span data-ttu-id="b5083-107"><xref:System.Activities.Statements.ParallelForEach%601> の非ジェネリック バージョンにはこの要件はありませんが、コレクション内の値の型の互換性を確保するために実行時の複雑さが増します。</span><span class="sxs-lookup"><span data-stu-id="b5083-107">The non-generic version of <xref:System.Activities.Statements.ParallelForEach%601> overcomes this requirement, at the expense of more run-time complexity for ensuring the compatibility of the types of the values in the collection.</span></span>

<span data-ttu-id="b5083-108">このサンプルでは、非ジェネリックの <xref:System.Activities.Statements.ParallelForEach%601> アクティビティとそのデザイナーを実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b5083-108">This sample shows how to implement a non-generic <xref:System.Activities.Statements.ParallelForEach%601> activity and its designer.</span></span> <span data-ttu-id="b5083-109">このアクティビティは、<xref:System.Collections.ArrayList> の反復処理に使用できます。</span><span class="sxs-lookup"><span data-stu-id="b5083-109">This activity can be used to iterate through <xref:System.Collections.ArrayList>.</span></span>

## <a name="parallelforeach-activity"></a><span data-ttu-id="b5083-110">ParallelForEach アクティビティ</span><span class="sxs-lookup"><span data-stu-id="b5083-110">ParallelForEach activity</span></span>

<span data-ttu-id="b5083-111">C#/Visual Basic のステートメントは、コレクションの要素を `foreach` 列挙し、コレクションの各要素に対して埋め込みステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="b5083-111">The C#/Visual Basic `foreach` statement enumerates the elements of a collection, executing an embedded statement for each element of the collection.</span></span> <span data-ttu-id="b5083-112">このステートメントに相当する [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のアクティビティは、<xref:System.Activities.Statements.ForEach%601> および <xref:System.Activities.Statements.ParallelForEach%601> です。</span><span class="sxs-lookup"><span data-stu-id="b5083-112">The [!INCLUDE[wf1](../../../../includes/wf1-md.md)] equivalent activities are <xref:System.Activities.Statements.ForEach%601> and <xref:System.Activities.Statements.ParallelForEach%601>.</span></span> <span data-ttu-id="b5083-113"><xref:System.Activities.Statements.ForEach%601> アクティビティには、値のリストと本体が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b5083-113">The <xref:System.Activities.Statements.ForEach%601> activity contains a list of values and a body.</span></span> <span data-ttu-id="b5083-114">実行時に、リストが反復処理されて、リスト内の値ごとに本体が実行されます。</span><span class="sxs-lookup"><span data-stu-id="b5083-114">At runtime, the list is iterated and the body is executed for each value in the list.</span></span>

<span data-ttu-id="b5083-115"><xref:System.Activities.Statements.ParallelForEach%601> には <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> があります。そのため、<xref:System.Activities.Statements.ParallelForEach%601> の評価が <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> を返した場合、`true` アクティビティは早期に完了することがあります。</span><span class="sxs-lookup"><span data-stu-id="b5083-115"><xref:System.Activities.Statements.ParallelForEach%601> has a <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>, so that the <xref:System.Activities.Statements.ParallelForEach%601> activity could complete early if the evaluation of the <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> returns `true`.</span></span> <span data-ttu-id="b5083-116"><xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> は、各イテレーションの完了後に評価されます。</span><span class="sxs-lookup"><span data-stu-id="b5083-116">The <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> is evaluated after each iteration is completed.</span></span>

<span data-ttu-id="b5083-117">ほとんどの場合、ジェネリック バージョンのアクティビティを使用することをお勧めします。ジェネリック バージョンのアクティビティは、そのアクティビティを使用するシナリオの大半に対応し、コンパイル時の型チェックを提供するためです。</span><span class="sxs-lookup"><span data-stu-id="b5083-117">For most cases, the generic version of the activity should be the preferred solution, because it covers most of the scenarios in which it is used and provides type checking at compile time.</span></span> <span data-ttu-id="b5083-118">非ジェネリック バージョンは、非ジェネリックの <xref:System.Collections.IEnumerable> インターフェイスを実装する型を反復処理するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="b5083-118">The non-generic version can be used for iterating through types that implement the non-generic <xref:System.Collections.IEnumerable> interface.</span></span>

## <a name="class-definition"></a><span data-ttu-id="b5083-119">クラス定義</span><span class="sxs-lookup"><span data-stu-id="b5083-119">Class definition</span></span>

<span data-ttu-id="b5083-120">次のコード例は、非ジェネリックの `ParallelForEach` アクティビティの定義を示しています。</span><span class="sxs-lookup"><span data-stu-id="b5083-120">The following code example shows the definition of a non-generic `ParallelForEach` activity is.</span></span>

```csharp
[ContentProperty("Body")]
public class ParallelForEach : NativeActivity
{
    [RequiredArgument]
    [DefaultValue(null)]
    InArgument<IEnumerable> Values { get; set; }

    [DefaultValue(null)]
    [DependsOn("Values")]
    public Activity<bool> CompletionCondition
    [DefaultValue(null)]
    [DependsOn("CompletionCondition")]
    ActivityAction<object> Body { get; set; }
}
```

<span data-ttu-id="b5083-121">本文 (オプション) </span><span class="sxs-lookup"><span data-stu-id="b5083-121">Body (optional)</span></span>\
<span data-ttu-id="b5083-122">コレクション内の要素ごとに実行される <xref:System.Activities.ActivityAction> 型の <xref:System.Object>。</span><span class="sxs-lookup"><span data-stu-id="b5083-122">The <xref:System.Activities.ActivityAction> of type <xref:System.Object>, which is executed for each element in the collection.</span></span> <span data-ttu-id="b5083-123">各要素は、Argument プロパティを使用して Body に渡されます。</span><span class="sxs-lookup"><span data-stu-id="b5083-123">Each individual element is passed into the Body through its Argument property.</span></span>

<span data-ttu-id="b5083-124">値 (省略可能) </span><span class="sxs-lookup"><span data-stu-id="b5083-124">Values (optional)</span></span>\
<span data-ttu-id="b5083-125">反復処理される要素のコレクション。</span><span class="sxs-lookup"><span data-stu-id="b5083-125">The collection of elements that are iterated over.</span></span> <span data-ttu-id="b5083-126">コレクションのすべての要素の型が互換性のある型であることが実行時に確認されます。</span><span class="sxs-lookup"><span data-stu-id="b5083-126">Ensuring that all elements of the collection are of compatible types is done at run-time.</span></span>

<span data-ttu-id="b5083-127">補完条件 (省略可能) </span><span class="sxs-lookup"><span data-stu-id="b5083-127">CompletionCondition (optional)</span></span>\
<span data-ttu-id="b5083-128"><xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> プロパティは、イテレーションの完了後に評価されます。</span><span class="sxs-lookup"><span data-stu-id="b5083-128">The <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> property is evaluated after any iteration completes.</span></span> <span data-ttu-id="b5083-129">`true` であると評価する場合、スケジュールされた保留イテレーションはキャンセルされます。</span><span class="sxs-lookup"><span data-stu-id="b5083-129">If it evaluates to `true`, then the scheduled pending iterations are canceled.</span></span> <span data-ttu-id="b5083-130">このプロパティが設定されていない場合、分岐コレクション内のすべてのアクティビティは完了するまで実行されます。</span><span class="sxs-lookup"><span data-stu-id="b5083-130">If this property is not set, all activities in the Branches collection execute until completion.</span></span>

## <a name="example-of-using-parallelforeach"></a><span data-ttu-id="b5083-131">ParallelForEach の使用例</span><span class="sxs-lookup"><span data-stu-id="b5083-131">Example of using ParallelForEach</span></span>

<span data-ttu-id="b5083-132">アプリケーションでの ParallelForEach アクティビティの使用方法を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="b5083-132">The following code demonstrates how to use the ParallelForEach activity in an application.</span></span>

```csharp
string[] names = { "bill", "steve", "ray" };

DelegateInArgument<object> iterationVariable = new DelegateInArgument<object>() { Name = "iterationVariable" };

Activity sampleUsage =
    new ParallelForEach
    {
       Values = new InArgument<IEnumerable>(c=> names),
       Body = new ActivityAction<object>
       {
           Argument = iterationVariable,
           Handler = new WriteLine
           {
               Text = new InArgument<string>(env => string.Format("Hello {0}",                                                               iterationVariable.Get(env)))
           }
       }
   };
```

## <a name="parallelforeach-designer"></a><span data-ttu-id="b5083-133">ParallelForEach デザイナー</span><span class="sxs-lookup"><span data-stu-id="b5083-133">ParallelForEach designer</span></span>

<span data-ttu-id="b5083-134">サンプルのアクティビティ デザイナーは、組み込みの <xref:System.Activities.Statements.ParallelForEach%601> アクティビティ用に提供されているデザイナーに外観が似ています。</span><span class="sxs-lookup"><span data-stu-id="b5083-134">The activity designer for the sample is similar in appearance to the designer provided for the built-in <xref:System.Activities.Statements.ParallelForEach%601> activity.</span></span> <span data-ttu-id="b5083-135">デザイナーは、[ **サンプル** の **非ジェネリックアクティビティ** ] カテゴリの [ツールボックス] に表示されます。</span><span class="sxs-lookup"><span data-stu-id="b5083-135">The designer appears in the toolbox in the **Samples**, **Non-Generic Activities** category.</span></span> <span data-ttu-id="b5083-136">デザイナーのツールボックスには **ParallelForEachWithBodyFactory** という名前が付けられます。これは、アクティビティが、 <xref:System.Activities.Presentation.IActivityTemplateFactory> 適切に構成されたを持つアクティビティを作成するツールボックスでを公開するためです <xref:System.Activities.ActivityAction> 。</span><span class="sxs-lookup"><span data-stu-id="b5083-136">The designer is named **ParallelForEachWithBodyFactory** in the toolbox, because the activity exposes an <xref:System.Activities.Presentation.IActivityTemplateFactory> in the toolbox that creates the activity with a properly configured <xref:System.Activities.ActivityAction>.</span></span>

```csharp
public sealed class ParallelForEachWithBodyFactory : IActivityTemplateFactory
{
    public Activity Create(DependencyObject target)
    {
        return new Microsoft.Samples.Activities.Statements.ParallelForEach()
        {
            Body = new ActivityAction<object>()
            {
                Argument = new DelegateInArgument<object>()
                {
                    Name = "item"
                }
            }
        };
    }
}
```

## <a name="to-run-the-sample"></a><span data-ttu-id="b5083-137">サンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="b5083-137">To run the sample</span></span>

1. <span data-ttu-id="b5083-138">選択したプロジェクトをソリューションのスタートアップ プロジェクトに設定します。</span><span class="sxs-lookup"><span data-stu-id="b5083-138">Set the project of your choice as the startup project of the solution.</span></span>

    1. <span data-ttu-id="b5083-139">**Codetestclient** は、コードを使用してアクティビティを使用する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="b5083-139">**CodeTestClient** shows how to use the activity using code.</span></span>

    2. <span data-ttu-id="b5083-140">**デザイナ Testclient** デザイナー内でアクティビティを使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b5083-140">**DesignerTestClient** shows how to use the activity within the designer.</span></span>

2. <span data-ttu-id="b5083-141">プロジェクトをビルドして実行します。</span><span class="sxs-lookup"><span data-stu-id="b5083-141">Build and run the project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b5083-142">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="b5083-142">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b5083-143">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="b5083-143">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="b5083-144">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="b5083-144">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b5083-145">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="b5083-145">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericParallelForEach`
