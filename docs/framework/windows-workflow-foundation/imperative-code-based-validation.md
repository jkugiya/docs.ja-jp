---
description: 詳細については、「命令型 Code-Based 検証」を参照してください。
title: 命令型コードに基づく検証
ms.date: 03/30/2017
ms.assetid: ae12537c-455e-42b1-82f4-cea4c46c023e
ms.openlocfilehash: 36759572393be613a569c4846e3610fcbbde2a51
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792701"
---
# <a name="imperative-code-based-validation"></a><span data-ttu-id="50dfc-103">命令型コードに基づく検証</span><span class="sxs-lookup"><span data-stu-id="50dfc-103">Imperative Code-Based Validation</span></span>

<span data-ttu-id="50dfc-104">命令型コードに基づく検証は、アクティビティでアクティビティ自身に関する検証を可能にする簡単な方法を提供し、<xref:System.Activities.CodeActivity>、<xref:System.Activities.AsyncCodeActivity>、および <xref:System.Activities.NativeActivity> から派生するアクティビティで使用できます。</span><span class="sxs-lookup"><span data-stu-id="50dfc-104">Imperative code-based validation provides a simple way for an activity to provide validation about itself, and is available for activities that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, and <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="50dfc-105">検証のエラーまたは警告を判断する検証コードがアクティビティに追加されます。</span><span class="sxs-lookup"><span data-stu-id="50dfc-105">Validation code that determines any validation errors or warnings is added to the activity.</span></span>  
  
## <a name="using-code-based-validation"></a><span data-ttu-id="50dfc-106">コードに基づく検証の使用</span><span class="sxs-lookup"><span data-stu-id="50dfc-106">Using Code-Based Validation</span></span>

<span data-ttu-id="50dfc-107">コードに基づく検証は、<xref:System.Activities.CodeActivity>、<xref:System.Activities.AsyncCodeActivity>、および <xref:System.Activities.NativeActivity> から派生するアクティビティでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="50dfc-107">Code-based validation is supported by activities that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, and <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="50dfc-108">検証コードは <xref:System.Activities.CodeActivity.CacheMetadata%2A> オーバーライドに配置できます。また、検証エラーまたは警告はメタデータ引数に追加できます。</span><span class="sxs-lookup"><span data-stu-id="50dfc-108">Validation code can be placed in the <xref:System.Activities.CodeActivity.CacheMetadata%2A> override, and validation errors or warnings can be added to the metadata argument.</span></span> <span data-ttu-id="50dfc-109">次の例では、`Cost` が `Price` よりも高い場合、検証エラーがメタデータに追加されます。</span><span class="sxs-lookup"><span data-stu-id="50dfc-109">In the following example, if the `Cost` is greater than the `Price`, a validation error is added to the metadata.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="50dfc-110">`Cost` と `Price` はこのアクティビティの引数ではありませんが、デザイン時に設定されるプロパティです。</span><span class="sxs-lookup"><span data-stu-id="50dfc-110">Note that `Cost` and `Price` are not arguments to the activity, but are properties that are set at design time.</span></span> <span data-ttu-id="50dfc-111">その理由は、これらの値は <xref:System.Activities.CodeActivity.CacheMetadata%2A> オーバーライドで検証できるためです。</span><span class="sxs-lookup"><span data-stu-id="50dfc-111">That is why their values can be validated in the <xref:System.Activities.CodeActivity.CacheMetadata%2A> override.</span></span> <span data-ttu-id="50dfc-112">引数に流入するデータの値は、データが実行時まで流れないのでデザイン時には検証できません。しかし、`RequiredArgument` 属性とオーバーロード グループを使用してアクティビティの引数を検証すると、それらの引数にバインドされていることが確認できます。</span><span class="sxs-lookup"><span data-stu-id="50dfc-112">The value of the data flowing through an argument cannot be validated at design time because the data does not flow until run time, but activity arguments can be validated to ensure that they are bound by using the `RequiredArgument` attribute and overload groups.</span></span> <span data-ttu-id="50dfc-113">このコード例では、`RequiredArgument` 引数の `Description` 属性を確認します。これがバインドされていなければ、検証エラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="50dfc-113">This example code sees the `RequiredArgument` attribute for the `Description` argument, and if it is not bound then a validation error is generated.</span></span> <span data-ttu-id="50dfc-114">必須の引数につい [ては、「必須の引数とオーバーロードグループ](required-arguments-and-overload-groups.md)」を対象としています。</span><span class="sxs-lookup"><span data-stu-id="50dfc-114">Required arguments are covered in [Required Arguments and Overload Groups](required-arguments-and-overload-groups.md).</span></span>  
  
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
  
 <span data-ttu-id="50dfc-115">既定では、検証エラーがメタデータに追加されるのは、<xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> が呼び出されたときです。</span><span class="sxs-lookup"><span data-stu-id="50dfc-115">By default, a validation error is added to the metadata when <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> is called.</span></span> <span data-ttu-id="50dfc-116">検証の警告を追加するには、<xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> を受け取る <xref:System.Activities.Validation.ValidationError> オーバーロードを使用し、<xref:System.Activities.Validation.ValidationError> プロパティを設定することで <xref:System.Activities.Validation.ValidationError.IsWarning%2A> が警告を表すことを示します。</span><span class="sxs-lookup"><span data-stu-id="50dfc-116">To add a validation warning, use the <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> overload that takes a <xref:System.Activities.Validation.ValidationError>, and specify that the <xref:System.Activities.Validation.ValidationError> represents a warning by setting the <xref:System.Activities.Validation.ValidationError.IsWarning%2A> property.</span></span>  
  
 <span data-ttu-id="50dfc-117">検証が発生するのは、ワークフローがワークフロー デザイナーで修正され、検証エラーまたは警告がワークフロー デザイナーに表示されたときです。</span><span class="sxs-lookup"><span data-stu-id="50dfc-117">Validation occurs when a workflow is modified in the workflow designer and any validation errors or warnings are displayed in the workflow designer.</span></span> <span data-ttu-id="50dfc-118">ワーク フローの呼び出し時に検証も行われます。検証エラーが発生すると、既定の検証ロジックによって <xref:System.Activities.InvalidWorkflowException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="50dfc-118">Validation also occurs at run time when a workflow is invoked and if any validation errors occur, an <xref:System.Activities.InvalidWorkflowException> is thrown by the default validation logic.</span></span> <span data-ttu-id="50dfc-119">検証の呼び出しと検証の警告またはエラーへのアクセスの詳細については、「 [アクティビティ検証の呼び出し](invoking-activity-validation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="50dfc-119">For more information about invoking validation and accessing any validation warnings or errors, see [Invoking Activity Validation](invoking-activity-validation.md).</span></span>  
  
 <span data-ttu-id="50dfc-120"><xref:System.Activities.CodeActivity.CacheMetadata%2A> からスローされる例外は、検証エラーとして処理されません。</span><span class="sxs-lookup"><span data-stu-id="50dfc-120">Any exceptions that are thrown from <xref:System.Activities.CodeActivity.CacheMetadata%2A> are not treated as validation errors.</span></span> <span data-ttu-id="50dfc-121">これらの例外は、<xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> への呼び出しからエスケープされ、呼び出し元によって処理される必要があります。</span><span class="sxs-lookup"><span data-stu-id="50dfc-121">These exceptions will escape from the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> and must be handled by the caller.</span></span>  
  
 <span data-ttu-id="50dfc-122">コードに基づく検証は、コードを含み、ワークフロー内の他のアクティビティから表示できないアクティビティを検証するときに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="50dfc-122">Code-based validation is useful for validating the activity that contains the code, but it does not have visibility into the other activities in the workflow.</span></span> <span data-ttu-id="50dfc-123">宣言型制約の検証では、ワークフロー内のアクティビティと他のアクティビティとの間の関係を検証する機能が提供されます。これについては、「 [宣言型制約](declarative-constraints.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="50dfc-123">Declarative constraints validation provides the ability to validate the relationships between an activity and other activities in the workflow, and is covered in the [Declarative Constraints](declarative-constraints.md) topic.</span></span>
