---
description: 詳細については、「アクティビティ検証の呼び出し」を参照してください。
title: アクティビティ検証の呼び出し
ms.date: 03/30/2017
ms.assetid: 22bef766-c505-4fd4-ac0f-7b363b238969
ms.openlocfilehash: dc710e76134fbd76f5217df4ea569f20e6de4445
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792662"
---
# <a name="invoking-activity-validation"></a><span data-ttu-id="5260b-103">アクティビティ検証の呼び出し</span><span class="sxs-lookup"><span data-stu-id="5260b-103">Invoking Activity Validation</span></span>

<span data-ttu-id="5260b-104">アクティビティの検証は、アクティビティを実行する前にアクティビティの構成エラーを特定および報告する手段です。</span><span class="sxs-lookup"><span data-stu-id="5260b-104">Activity validation provides a method to identify and report errors in any activity’s configuration prior to its execution.</span></span> <span data-ttu-id="5260b-105">検証が発生するのは、ワークフローがワークフロー デザイナーで修正され、検証エラーまたは警告がワークフロー デザイナーに表示されたときです。</span><span class="sxs-lookup"><span data-stu-id="5260b-105">Validation occurs when a workflow is modified in the workflow designer and any validation errors or warnings are displayed in the workflow designer.</span></span> <span data-ttu-id="5260b-106">ワーク フローの呼び出し時に検証も行われます。検証エラーが発生すると、既定の検証ロジックによって <xref:System.Activities.InvalidWorkflowException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="5260b-106">Validation also occurs at run time when a workflow is invoked and if any validation errors occur, an <xref:System.Activities.InvalidWorkflowException> is thrown by the default validation logic.</span></span> <span data-ttu-id="5260b-107">Windows Workflow Foundation (WF) は、 <xref:System.Activities.Validation.ActivityValidationServices> ワークフローアプリケーションやツールの開発者がアクティビティを明示的に検証するために使用できるクラスを提供します。</span><span class="sxs-lookup"><span data-stu-id="5260b-107">Windows Workflow Foundation (WF) provides the <xref:System.Activities.Validation.ActivityValidationServices> class that can be used by workflow application and tooling developers to explicitly validate an activity.</span></span> <span data-ttu-id="5260b-108">このトピックでは、<xref:System.Activities.Validation.ActivityValidationServices> を使用してアクティビティの検証を実行する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="5260b-108">This topic describes how to use <xref:System.Activities.Validation.ActivityValidationServices> to perform activity validation.</span></span>  
  
## <a name="using-activityvalidationservices"></a><span data-ttu-id="5260b-109">ActivityValidationServices の使用</span><span class="sxs-lookup"><span data-stu-id="5260b-109">Using ActivityValidationServices</span></span>  

 <span data-ttu-id="5260b-110"><xref:System.Activities.Validation.ActivityValidationServices> には、アクティビティの検証ロジックの呼び出しに使用される 2 つの <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> オーバーロードがあります。</span><span class="sxs-lookup"><span data-stu-id="5260b-110"><xref:System.Activities.Validation.ActivityValidationServices> has two <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> overloads that are used to invoke an activity’s validation logic.</span></span> <span data-ttu-id="5260b-111">1 つ目のオーバーロードは、検証されるルート アクティビティを受け取り、一連の検証エラーと警告を返します。</span><span class="sxs-lookup"><span data-stu-id="5260b-111">The first overload takes the root activity to be validated and returns a collection of validation errors and warnings.</span></span> <span data-ttu-id="5260b-112">次の例では、2 つの必須引数を持つカスタムの `Add` アクティビティが使用されています。</span><span class="sxs-lookup"><span data-stu-id="5260b-112">In the following example, a custom `Add` activity is used that has two required arguments.</span></span>  
  
```csharp  
public sealed class Add : CodeActivity<int>  
{  
    [RequiredArgument]  
    public InArgument<int> Operand1 { get; set; }  
  
    [RequiredArgument]  
    public InArgument<int> Operand2 { get; set; }  
  
    protected override int Execute(CodeActivityContext context)  
    {  
        return Operand1.Get(context) + Operand2.Get(context);  
    }  
}  
```  
  
 <span data-ttu-id="5260b-113">`Add` アクティビティが <xref:System.Activities.Statements.Sequence> 内で使用されていますが、次の例に示すように、その 2 つの必須引数はバインドされていません。</span><span class="sxs-lookup"><span data-stu-id="5260b-113">The `Add` activity is used inside a <xref:System.Activities.Statements.Sequence>, but its two required arguments are not bound, as shown in the following example.</span></span>  
  
```csharp  
Variable<int> Operand1 = new Variable<int>{ Default = 10 };  
Variable<int> Operand2 = new Variable<int>{ Default = 15 };  
Variable<int> Result = new Variable<int>();  
  
Activity wf = new Sequence  
{  
    Variables = { Operand1, Operand2, Result },  
    Activities =
    {  
        new Add(),  
        new WriteLine  
        {  
            Text = new InArgument<string>(env => "The result is " + Result.Get(env))  
        }  
    }  
};  
```  
  
 <span data-ttu-id="5260b-114">このワーク フローは、<xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> を呼び出して検証できます。</span><span class="sxs-lookup"><span data-stu-id="5260b-114">This workflow can be validated by calling <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="5260b-115"><xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> は、次の例に示すように、アクティビティと子に含まれる一連の検証エラーと警告を返します。</span><span class="sxs-lookup"><span data-stu-id="5260b-115"><xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> returns a collection of any validation errors or warnings contained by the activity and any children, as shown in the following example.</span></span>  
  
```csharp  
ValidationResults results = ActivityValidationServices.Validate(wf);  
  
if (results.Errors.Count == 0 && results.Warnings.Count == 0)  
{  
    Console.WriteLine("No warnings or errors");  
}  
else  
{  
    foreach (ValidationError error in results.Errors)  
    {  
        Console.WriteLine("Error: {0}", error.Message);  
    }  
    foreach (ValidationError warning in results.Warnings)  
    {  
        Console.WriteLine("Warning: {0}", warning.Message);  
    }  
}  
```  
  
 <span data-ttu-id="5260b-116">このサンプル ワークフローで <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> が呼び出されると、次の 2 つの検証エラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="5260b-116">When <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> is called on this sample workflow, two validation errors are returned.</span></span>  
  
 <span data-ttu-id="5260b-117">**エラー: 必須のアクティビティ引数 'Operand2' の値が指定されませんでした。**</span><span class="sxs-lookup"><span data-stu-id="5260b-117">**Error: Value for a required activity argument 'Operand2' was not supplied.**</span></span>  
<span data-ttu-id="5260b-118">**エラー: 必須のアクティビティ引数 ' Operand1 ' の値が指定されませんでした。**</span><span class="sxs-lookup"><span data-stu-id="5260b-118">**Error: Value for a required activity argument 'Operand1' was not supplied.**</span></span>  <span data-ttu-id="5260b-119">このワークフローが呼び出された場合、次の例に示すように、<xref:System.Activities.InvalidWorkflowException> がスローされることになります。</span><span class="sxs-lookup"><span data-stu-id="5260b-119">If this workflow was invoked, an <xref:System.Activities.InvalidWorkflowException> would be thrown, as shown in the following example.</span></span>  
  
```csharp  
try  
{  
    WorkflowInvoker.Invoke(wf);  
}  
catch (Exception ex)  
{  
    Console.WriteLine(ex);  
}  
```  
  
 <span data-ttu-id="5260b-120">**System.Activities.InvalidWorkflowException:**</span><span class="sxs-lookup"><span data-stu-id="5260b-120">**System.Activities.InvalidWorkflowException:**</span></span>  
<span data-ttu-id="5260b-121">**ワークフローツリーの処理中に次のエラーが発生しました:** 
 **' Add ': 必須のアクティビティ引数 ' Operand2 ' の値が指定されませんでした。** 
 **' Add ': 必須のアクティビティ引数 ' Operand1 ' の値が指定されませんでした。**</span><span class="sxs-lookup"><span data-stu-id="5260b-121">**The following errors were encountered while processing the workflow tree:**
 **'Add': Value for a required activity argument 'Operand2' was not supplied.**
 **'Add': Value for a required activity argument 'Operand1' was not supplied.**</span></span>  <span data-ttu-id="5260b-122">このサンプル ワークフローを有効にするには、`Add` アクティビティの 2 つの必須引数をバインドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5260b-122">For this example workflow to be valid, the two required arguments of the `Add` activity must be bound.</span></span> <span data-ttu-id="5260b-123">次の例では、2 つの必須引数と結果値がワークフロー変数にバインドされています。</span><span class="sxs-lookup"><span data-stu-id="5260b-123">In the following example, the two required arguments are bound to workflow variables along with the result value.</span></span> <span data-ttu-id="5260b-124">この例では、2 つの必須変数に加え、<xref:System.Activities.Activity%601.Result%2A> 引数がバインドされています。</span><span class="sxs-lookup"><span data-stu-id="5260b-124">In this example the <xref:System.Activities.Activity%601.Result%2A> argument is bound along with the two required arguments.</span></span> <span data-ttu-id="5260b-125"><xref:System.Activities.Activity%601.Result%2A> 引数はバインドする必要がなく、バインドされていなくても検証エラーは発生しません。</span><span class="sxs-lookup"><span data-stu-id="5260b-125">The <xref:System.Activities.Activity%601.Result%2A> argument is not required to be bound and does not cause a validation error if it is not.</span></span> <span data-ttu-id="5260b-126"><xref:System.Activities.Activity%601.Result%2A> の値がワークフローの別の場所で使用される場合、この引数のバインドはワークフローの作成者が行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="5260b-126">It is the responsibility of the workflow author to bind <xref:System.Activities.Activity%601.Result%2A> if its value is used elsewhere in the workflow.</span></span>  
  
```csharp  
new Add  
{  
    Operand1 = Operand1,  
    Operand2 = Operand2,  
    Result = Result  
}  
```  
  
### <a name="validating-required-arguments-on-the-root-activity"></a><span data-ttu-id="5260b-127">ルート アクティビティでの必須引数の検証</span><span class="sxs-lookup"><span data-stu-id="5260b-127">Validating Required Arguments on the Root Activity</span></span>  

 <span data-ttu-id="5260b-128">ワーク フローのルート アクティビティに引数がある場合、ワーク フローが呼び出され、パラメーターがワーク フローに渡されるまでこれらの引数はバインドされません。</span><span class="sxs-lookup"><span data-stu-id="5260b-128">If the root activity of a workflow has arguments, these are not bound until the workflow is invoked and parameters are passed to the workflow.</span></span> <span data-ttu-id="5260b-129">次のワーク フローは検証を渡しますが、次の例に示すように、ワーク フローが必要な引数に渡されずに呼び出されると、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="5260b-129">The following workflow passes validation, but an exception is thrown if the workflow is invoked without passing in the required arguments, as shown in the following example.</span></span>  
  
```csharp  
Activity wf = new Add();  
  
ValidationResults results = ActivityValidationServices.Validate(wf);  
// results has no errors or warnings, but when the workflow  
// is invoked, an InvalidWorkflowException is thrown.  
try  
{  
    WorkflowInvoker.Invoke(wf);  
}  
catch (Exception ex)  
{  
    Console.WriteLine(ex);  
}  
```  
  
 <span data-ttu-id="5260b-130">**System.ArgumentException: ルート アクティビティの引数の設定が正しくありません。**</span><span class="sxs-lookup"><span data-stu-id="5260b-130">**System.ArgumentException: The root activity's argument settings are incorrect.**</span></span>  
<span data-ttu-id="5260b-131">**これらのエラーを修正するには、ワークフロー定義を修正するか、入力値を指定してください。** 
 **' Add ': 必須のアクティビティ引数 ' Operand2 ' の値が指定されませんでした。** 
 **' Add ': 必須のアクティビティ引数 ' Operand1 ' の値が指定されませんでした。**</span><span class="sxs-lookup"><span data-stu-id="5260b-131">**Either fix the workflow definition or supply input values to fix these errors:**
 **'Add': Value for a required activity argument 'Operand2' was not supplied.**
 **'Add': Value for a required activity argument 'Operand1' was not supplied.**</span></span>  <span data-ttu-id="5260b-132">正しい引数が渡された後、次の例に示すように、ワークフローは正常に完了します。</span><span class="sxs-lookup"><span data-stu-id="5260b-132">After the correct arguments are passed, the workflow completes successfully, as shown in the following example.</span></span>  
  
```csharp  
Add wf = new Add();  
  
ValidationResults results = ActivityValidationServices.Validate(wf);  
// results has no errors or warnings, and the workflow completes  
// successfully because the required arguments were passed.  
try  
{  
    Dictionary<string, object> wfparams = new Dictionary<string, object>  
    {  
        { "Operand1", 10 },  
        { "Operand2", 15 }  
    };  
  
    int result = WorkflowInvoker.Invoke(wf, wfparams);  
    Console.WriteLine("Result: {0}", result);  
}  
catch (Exception ex)  
{  
    Console.WriteLine(ex);  
}  
```  
  
> [!NOTE]
> <span data-ttu-id="5260b-133">この例では、前の例の `Add` とは異なり、ルート アクティビティは `Activity` として宣言されています。</span><span class="sxs-lookup"><span data-stu-id="5260b-133">In this example, the root activity was declared as `Add` instead of `Activity` as in the previous example.</span></span> <span data-ttu-id="5260b-134">このため、`WorkflowInvoker.Invoke` メソッドは、`Add` 引数のディクショナリではなく、`out` アクティビティの結果を表す 1 つの整数を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="5260b-134">This allows the `WorkflowInvoker.Invoke` method to return a single integer that represents the results of the `Add` activity instead of a dictionary of `out` arguments.</span></span> <span data-ttu-id="5260b-135">また、変数 `wf` は `Activity<int>` として宣言することも可能です。</span><span class="sxs-lookup"><span data-stu-id="5260b-135">The variable `wf` could also have been declared as `Activity<int>`.</span></span>  
  
 <span data-ttu-id="5260b-136">ルート引数を検証する場合、ワークフローが呼び出されたときにすべての必須変数が渡されたことを確認するのはホスト アプリケーションが担当します。</span><span class="sxs-lookup"><span data-stu-id="5260b-136">When validating root arguments, it is the responsibility of the host application to ensure that all required arguments are passed when the workflow is invoked.</span></span>  
  
### <a name="invoking-imperative-code-based-validation"></a><span data-ttu-id="5260b-137">命令型コードに基づく検証の呼び出し</span><span class="sxs-lookup"><span data-stu-id="5260b-137">Invoking Imperative Code-Based Validation</span></span>

<span data-ttu-id="5260b-138">命令型コードに基づく検証は、アクティビティでアクティビティ自身に関する検証を可能にする簡単な方法を提供し、<xref:System.Activities.CodeActivity>、<xref:System.Activities.AsyncCodeActivity>、および <xref:System.Activities.NativeActivity> から派生するアクティビティで使用できます。</span><span class="sxs-lookup"><span data-stu-id="5260b-138">Imperative code-based validation provides a simple way for an activity to provide validation about itself, and is available for activities that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, and <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="5260b-139">検証のエラーまたは警告を判断する検証コードがアクティビティに追加されます。</span><span class="sxs-lookup"><span data-stu-id="5260b-139">Validation code that determines any validation errors or warnings is added to the activity.</span></span> <span data-ttu-id="5260b-140">検証がアクティビティで呼び出されると、これらの警告またはエラーは、<xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> への呼び出しで返されるコレクションに格納されます。</span><span class="sxs-lookup"><span data-stu-id="5260b-140">When validation is invoked on the activity, these warnings or errors are contained in the collection returned by the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="5260b-141">次の例では、 `CreateProduct` アクティビティを定義します。</span><span class="sxs-lookup"><span data-stu-id="5260b-141">In the following example, a `CreateProduct` activity is defined.</span></span> <span data-ttu-id="5260b-142">`Cost` が `Price` よりも高い場合、検証エラーが <xref:System.Activities.CodeActivity.CacheMetadata%2A> オーバーライドのメタデータに追加されます。</span><span class="sxs-lookup"><span data-stu-id="5260b-142">If the `Cost` is greater than the `Price`, a validation error is added to the metadata in the <xref:System.Activities.CodeActivity.CacheMetadata%2A> override.</span></span>  
  
```csharp  
public sealed class CreateProduct : CodeActivity  
{  
    public double Price { get; set; }  
    public double Cost { get; set; }  
  
    // [RequiredArgument] attribute will generate a validation error
    // if the Description argument is not set.  
    [RequiredArgument]  
    public InArgument<string> Description { get; set; }  
  
    protected override void CacheMetadata(CodeActivityMetadata metadata)  
    {  
        base.CacheMetadata(metadata);  
        // Determine when the activity has been configured in an invalid way.  
        if (this.Cost > this.Price)  
        {  
            // Add a validation error with a custom message.  
            metadata.AddValidationError("The Cost must be less than or equal to the Price.");  
        }  
    }  
  
    protected override void Execute(CodeActivityContext context)  
    {  
        // Not needed for the sample.  
    }  
}  
```  
  
 <span data-ttu-id="5260b-143">この例では、ワーク フローは `CreateProduct` のアクティビティを使用して構成されます。</span><span class="sxs-lookup"><span data-stu-id="5260b-143">In this example, a workflow is configured using the `CreateProduct` activity.</span></span> <span data-ttu-id="5260b-144">このワーク フローで、`Cost` は `Price` より大きく、必須の `Description` 引数は設定されません。</span><span class="sxs-lookup"><span data-stu-id="5260b-144">In this workflow, the `Cost` is greater than the `Price`, and the required `Description` argument is not set.</span></span> <span data-ttu-id="5260b-145">検証を呼び出すと、次のエラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="5260b-145">When validation is invoked, the following errors are returned.</span></span>  
  
```csharp  
Activity wf = new Sequence  
{  
    Activities =
    {  
        new CreateProduct  
        {  
            Cost = 75.00,  
            Price = 55.00  
            // Cost > Price and required Description argument not set.  
        },  
        new WriteLine  
        {  
            Text = "Product added."  
        }  
    }  
};  
  
ValidationResults results = ActivityValidationServices.Validate(wf);  
  
if (results.Errors.Count == 0 && results.Warnings.Count == 0)  
{  
    Console.WriteLine("No warnings or errors");  
}  
else  
{  
    foreach (ValidationError error in results.Errors)  
    {  
        Console.WriteLine("Error: {0}", error.Message);  
    }  
    foreach (ValidationError warning in results.Warnings)  
    {  
        Console.WriteLine("Warning: {0}", warning.Message);  
    }  
}  
```  
  
 <span data-ttu-id="5260b-146">**エラー: コストを価格以下する必要があります。**</span><span class="sxs-lookup"><span data-stu-id="5260b-146">**Error: The Cost must be less than or equal to the Price.**</span></span>  
<span data-ttu-id="5260b-147">**エラー: 必須のアクティビティ引数 'Description' の値が指定されませんでした。**</span><span class="sxs-lookup"><span data-stu-id="5260b-147">**Error: Value for a required activity argument 'Description' was not supplied.**</span></span>
> [!NOTE]
> <span data-ttu-id="5260b-148">カスタム アクティビティの作成者は、アクティビティの <xref:System.Activities.CodeActivity.CacheMetadata%2A> オーバーライドに検証ロジックを指定できます。</span><span class="sxs-lookup"><span data-stu-id="5260b-148">Custom activity authors can provide validation logic in an activity's <xref:System.Activities.CodeActivity.CacheMetadata%2A> override.</span></span> <span data-ttu-id="5260b-149"><xref:System.Activities.CodeActivity.CacheMetadata%2A> からスローされる例外は、検証エラーとして処理されません。</span><span class="sxs-lookup"><span data-stu-id="5260b-149">Any exceptions that are thrown from <xref:System.Activities.CodeActivity.CacheMetadata%2A> are not treated as validation errors.</span></span> <span data-ttu-id="5260b-150">これらの例外は、<xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> への呼び出しからエスケープされ、呼び出し元によって処理される必要があります。</span><span class="sxs-lookup"><span data-stu-id="5260b-150">These exceptions will escape from the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> and must be handled by the caller.</span></span>  
  
## <a name="using-validationsettings"></a><span data-ttu-id="5260b-151">ValidationSettings の使用</span><span class="sxs-lookup"><span data-stu-id="5260b-151">Using ValidationSettings</span></span>  

 <span data-ttu-id="5260b-152">既定では、アクティビティ ツリー内のすべてのアクティビティは、検証が <xref:System.Activities.Validation.ActivityValidationServices> に呼び出されたときに評価されます。</span><span class="sxs-lookup"><span data-stu-id="5260b-152">By default, all activities in the activity tree are evaluated when validation is invoked by <xref:System.Activities.Validation.ActivityValidationServices>.</span></span> <span data-ttu-id="5260b-153"><xref:System.Activities.Validation.ValidationSettings> を使用すると、その 3 つのプロパティを構成することによって、さまざまな方法で検証をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="5260b-153"><xref:System.Activities.Validation.ValidationSettings> allows the validation to be customized in several different ways by configuring its three properties.</span></span> <span data-ttu-id="5260b-154"><xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> は、バリデーターがアクティビティ ツリー全体を調べるか、指定したアクティビティにのみ検証ロジックを適用するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="5260b-154"><xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> specifies whether the validator should walk the entire activity tree or only apply validation logic to the supplied activity.</span></span> <span data-ttu-id="5260b-155">この値の既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="5260b-155">The default for this value is `false`.</span></span> <span data-ttu-id="5260b-156"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> は、型から制約のリストへの追加の制約マッピングを指定します。</span><span class="sxs-lookup"><span data-stu-id="5260b-156"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> specifies additional constraint mapping from a type to a list of constraints.</span></span> <span data-ttu-id="5260b-157">検証されているアクティビティ ツリーの各アクティビティの基本型について、<xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> への参照が行われます。</span><span class="sxs-lookup"><span data-stu-id="5260b-157">For the base type of each activity in the activity tree being validated there is a lookup into <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>.</span></span> <span data-ttu-id="5260b-158">一致する制約リストが見つかると、アクティビティについて、リストのすべての制約が評価されます。</span><span class="sxs-lookup"><span data-stu-id="5260b-158">If a matching constraint list is found, all constraints in the list are evaluated for the activity.</span></span> <span data-ttu-id="5260b-159"><xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> は、バリデーターがすべての制約を評価するか、<xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> で指定された制約のみを評価するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="5260b-159"><xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> specifies whether the validator should evaluate all constraints or only those specified in <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>.</span></span> <span data-ttu-id="5260b-160">既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="5260b-160">The default value is `false`.</span></span> <span data-ttu-id="5260b-161"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> および <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> は、FxCop のようなツールのポリシーの制約など、ワークフローの検証をワークフロー ホストの作成者がさらに追加する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="5260b-161"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> and <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> are useful for workflow host authors to add additional validation for workflows, such as policy constraints for tools such as FxCop.</span></span> <span data-ttu-id="5260b-162">制約の詳細については、「 [宣言型制約](declarative-constraints.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5260b-162">For more information about constraints, see [Declarative Constraints](declarative-constraints.md).</span></span>  
  
 <span data-ttu-id="5260b-163"><xref:System.Activities.Validation.ValidationSettings> を使用するには、必要なプロパティを構成し、<xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> の呼び出しで渡します。</span><span class="sxs-lookup"><span data-stu-id="5260b-163">To use <xref:System.Activities.Validation.ValidationSettings>, configure the desired properties, and then pass it in the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="5260b-164">この例では、カスタムの <xref:System.Activities.Statements.Sequence> アクティビティを持つ `Add` で構成されるワークフローが検証されます。</span><span class="sxs-lookup"><span data-stu-id="5260b-164">In this example, a workflow that consists of a <xref:System.Activities.Statements.Sequence> with a custom `Add` activity is validated.</span></span> <span data-ttu-id="5260b-165">この `Add` アクティビティには必須引数が 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="5260b-165">The `Add` activity has two required arguments.</span></span>  
  
```csharp  
public sealed class Add : CodeActivity<int>  
{  
    [RequiredArgument]  
    public InArgument<int> Operand1 { get; set; }  
  
    [RequiredArgument]  
    public InArgument<int> Operand2 { get; set; }  
  
    protected override int Execute(CodeActivityContext context)  
    {  
        return Operand1.Get(context) + Operand2.Get(context);  
    }  
}  
```  
  
 <span data-ttu-id="5260b-166">次の `Add` アクティビティは <xref:System.Activities.Statements.Sequence> で使用されますが、その 2 つの必須変数はバインドされていません。</span><span class="sxs-lookup"><span data-stu-id="5260b-166">The following `Add` activity is used in a <xref:System.Activities.Statements.Sequence>, but its two required arguments are not bound.</span></span>  
  
```csharp  
Variable<int> Operand1 = new Variable<int> { Default = 10 };  
Variable<int> Operand2 = new Variable<int> { Default = 15 };  
Variable<int> Result = new Variable<int>();  
  
Activity wf = new Sequence  
{  
    Variables = { Operand1, Operand2, Result },  
    Activities =
    {  
        new Add(),  
        new WriteLine  
        {  
            Text = new InArgument<string>(env => "The result is " + Result.Get(env))  
        }  
    }  
};  
```  
  
 <span data-ttu-id="5260b-167">次の例では、<xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> が `true` に設定されて検証が実行されるため、ルート アクティビティ <xref:System.Activities.Statements.Sequence> のみが検証されます。</span><span class="sxs-lookup"><span data-stu-id="5260b-167">For the following example, validation is performed with <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> set to `true`, so only the root <xref:System.Activities.Statements.Sequence> activity is validated.</span></span>  
  
```csharp  
ValidationSettings settings = new ValidationSettings  
{  
    SingleLevel = true  
};  
  
ValidationResults results = ActivityValidationServices.Validate(wf, settings);  
  
if (results.Errors.Count == 0 && results.Warnings.Count == 0)  
{  
    Console.WriteLine("No warnings or errors");  
}  
else  
{  
    foreach (ValidationError error in results.Errors)  
    {  
        Console.WriteLine("Error: {0}", error.Message);  
    }  
    foreach (ValidationError warning in results.Warnings)  
    {  
        Console.WriteLine("Warning: {0}", warning.Message);  
    }  
}  
```  
  
 <span data-ttu-id="5260b-168">このコードを実行すると、次の出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5260b-168">This code displays the following output:</span></span>  
  
 <span data-ttu-id="5260b-169">**警告またはエラーはありません** アクティビティにバインドされていない必須の引数がある場合でも、 `Add` ルートアクティビティのみが評価されるため、検証は成功します。</span><span class="sxs-lookup"><span data-stu-id="5260b-169">**No warnings or errors** Even though the `Add` activity has required arguments that are not bound, validation is successful because only the root activity is evaluated.</span></span> <span data-ttu-id="5260b-170">このタイプの検証は、デザイナーで 1 つのアクティビティのプロパティの変更を検証するなど、アクティビティ ツリーの特定の要素のみを検証する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="5260b-170">This type of validation is useful for validating only specific elements in an activity tree, such as validation of a property change of a single activity in a designer.</span></span> <span data-ttu-id="5260b-171">このワークフローが呼び出された場合、ワークフローで構成された完全な検証が評価され、<xref:System.Activities.InvalidWorkflowException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="5260b-171">Note that if this workflow is invoked, the full validation configured in the workflow is evaluated and an <xref:System.Activities.InvalidWorkflowException> would be thrown.</span></span> <span data-ttu-id="5260b-172"><xref:System.Activities.Validation.ActivityValidationServices> および <xref:System.Activities.Validation.ValidationSettings> で構成されるのは、ホストによって明示的に呼び出される検証だけであり、ワークフローが呼び出されたときに発生する検証ではありません。</span><span class="sxs-lookup"><span data-stu-id="5260b-172"><xref:System.Activities.Validation.ActivityValidationServices> and <xref:System.Activities.Validation.ValidationSettings> configure only validation explicitly invoked by the host, and not the validation that occurs when a workflow is invoked.</span></span>
