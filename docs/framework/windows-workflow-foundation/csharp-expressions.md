---
description: '詳細情報: C# の式'
title: C# の式
ms.date: 03/30/2017
ms.assetid: 29110be7-f4e3-407e-8dbe-78102eb21115
ms.openlocfilehash: ce918bb96164643f1adbc73f749d2b5f88f4eb3e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742811"
---
# <a name="c-expressions"></a><span data-ttu-id="9aceb-103">C# の式</span><span class="sxs-lookup"><span data-stu-id="9aceb-103">C# Expressions</span></span>

<span data-ttu-id="9aceb-104">.NET Framework 4.5 以降では、Windows Workflow Foundation (WF) で C# 式がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="9aceb-104">Starting with .NET Framework 4.5, C# expressions are supported in Windows Workflow Foundation (WF).</span></span> <span data-ttu-id="9aceb-105">Visual Studio 2012 で作成され、.NET Framework 4.5 を対象とする新しい C# ワークフロープロジェクトは C# 式を使用し、Visual Basic ワークフロープロジェクトは Visual Basic 式を使用します。</span><span class="sxs-lookup"><span data-stu-id="9aceb-105">New C# workflow projects created in Visual Studio 2012 that target .NET Framework 4.5 use C# expressions, and Visual Basic workflow projects use Visual Basic expressions.</span></span> <span data-ttu-id="9aceb-106">Visual Basic 式を使用する既存の .NET Framework 4 ワークフロープロジェクトは [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 、プロジェクトの言語に関係なく、に移行できます。また、サポートされています。</span><span class="sxs-lookup"><span data-stu-id="9aceb-106">Existing .NET Framework 4 workflow projects that use Visual Basic expressions can be migrated to [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] regardless of the project language and are supported.</span></span> <span data-ttu-id="9aceb-107">ここでは、[!INCLUDE[wf1](../../../includes/wf1-md.md)] での C# 式の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="9aceb-107">This topic provides an overview of C# expressions in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span>

## <a name="using-c-expressions-in-workflows"></a><span data-ttu-id="9aceb-108">ワークフローでの C# 式の使用</span><span class="sxs-lookup"><span data-stu-id="9aceb-108">Using C# expressions in workflows</span></span>

- [<span data-ttu-id="9aceb-109">ワークフロー デザイナーでの C# 式の使用</span><span class="sxs-lookup"><span data-stu-id="9aceb-109">Using C# expressions in the Workflow Designer</span></span>](csharp-expressions.md#WFDesigner)

  - [<span data-ttu-id="9aceb-110">下位互換性</span><span class="sxs-lookup"><span data-stu-id="9aceb-110">Backwards compatibility</span></span>](csharp-expressions.md#BackwardCompat)

- [<span data-ttu-id="9aceb-111">コード ワークフローでの C# 式の使用</span><span class="sxs-lookup"><span data-stu-id="9aceb-111">Using C# expressions in code workflows</span></span>](csharp-expressions.md#CodeWorkflows)

- [<span data-ttu-id="9aceb-112">XAML ワークフローでの C# 式の使用</span><span class="sxs-lookup"><span data-stu-id="9aceb-112">Using C# expressions in XAML workflows</span></span>](csharp-expressions.md#XamlWorkflows)

  - [<span data-ttu-id="9aceb-113">コンパイルされた Xaml</span><span class="sxs-lookup"><span data-stu-id="9aceb-113">Compiled Xaml</span></span>](csharp-expressions.md#CompiledXaml)

  - [<span data-ttu-id="9aceb-114">ルース Xaml</span><span class="sxs-lookup"><span data-stu-id="9aceb-114">Loose Xaml</span></span>](csharp-expressions.md#LooseXaml)

- [<span data-ttu-id="9aceb-115">XAMLX ワークフロー サービスでの C# 式の使用</span><span class="sxs-lookup"><span data-stu-id="9aceb-115">Using C# expressions in XAMLX workflow services</span></span>](csharp-expressions.md#WFServices)

### <a name="using-c-expressions-in-the-workflow-designer"></a><a name="WFDesigner"></a> <span data-ttu-id="9aceb-116">ワークフローデザイナーでの C# 式の使用</span><span class="sxs-lookup"><span data-stu-id="9aceb-116">Using C# expressions in the Workflow Designer</span></span>

<span data-ttu-id="9aceb-117">.NET Framework 4.5 以降では、Windows Workflow Foundation (WF) で C# 式がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="9aceb-117">Starting with .NET Framework 4.5, C# expressions are supported in Windows Workflow Foundation (WF).</span></span> <span data-ttu-id="9aceb-118">Visual Studio 2012 で作成され .NET Framework 4.5 を対象とする c# ワークフロープロジェクトでは C# 式を使用しますが、Visual Basic ワークフロープロジェクトでは Visual Basic 式を使用します。</span><span class="sxs-lookup"><span data-stu-id="9aceb-118">C# workflow projects created in Visual Studio 2012 that target .NET Framework 4.5 use C# expressions, while Visual Basic workflow projects use Visual Basic expressions.</span></span> <span data-ttu-id="9aceb-119">目的の C# 式を指定するには、[ **c# の式を入力** してください] というラベルの付いたボックスに入力します。</span><span class="sxs-lookup"><span data-stu-id="9aceb-119">To specify the desired C# expression, type it into the box labeled **Enter a C# expression**.</span></span> <span data-ttu-id="9aceb-120">このラベルは、プロパティ ウィンドウ (デザイナーでアクティビティを選択した場合) またはワークフロー デザイナーのアクティビティに表示されます。</span><span class="sxs-lookup"><span data-stu-id="9aceb-120">This label is displayed in the properties window when the activity is selected in the designer, or on the activity in the workflow designer.</span></span> <span data-ttu-id="9aceb-121">次の例では、2 つの `WriteLine` アクティビティが `Sequence` の中で `NoPersistScope` 内に含まれています。</span><span class="sxs-lookup"><span data-stu-id="9aceb-121">In the following example, two `WriteLine` activities are contained within a `Sequence` inside a `NoPersistScope`.</span></span>

![自動的に作成された sequence アクティビティを示すスクリーンショット。](./media/csharp-expressions/auto-surround-sequence-activity.png)

> [!NOTE]
> <span data-ttu-id="9aceb-123">C# の式は、Visual Studio でのみサポートされており、再ホストされたワークフローデザイナーではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="9aceb-123">C# expressions are supported only in Visual Studio, and are not supported in the re-hosted workflow designer.</span></span> <span data-ttu-id="9aceb-124">再ホストされたデザイナーでサポートされている新しい WF45 機能の詳細については、「 [rehosted ワークフローデザイナーでの新しい Workflow Foundation 4.5 機能のサポート](wf-features-in-the-rehosted-workflow-designer.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9aceb-124">For more information about new WF45 features supported in the re-hosted designer, see [Support for New Workflow Foundation 4.5 Features in the Rehosted Workflow Designer](wf-features-in-the-rehosted-workflow-designer.md).</span></span>

#### <a name="backwards-compatibility"></a><a name="BackwardCompat"></a> <span data-ttu-id="9aceb-125">旧バージョンとの互換性</span><span class="sxs-lookup"><span data-stu-id="9aceb-125">Backwards compatibility</span></span>

<span data-ttu-id="9aceb-126">に移行された既存の .NET Framework 4 つの C# ワークフロープロジェクトの Visual Basic 式 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="9aceb-126">Visual Basic expressions in existing .NET Framework 4 C# workflow projects that have been migrated to [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] are supported.</span></span> <span data-ttu-id="9aceb-127">Visual Basic 式がワークフローデザイナーで表示されると、Visual Basic 式が有効な C# 構文でない限り、既存の Visual Basic 式のテキストが **XAML で設定された値** に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="9aceb-127">When the Visual Basic expressions are viewed in the workflow designer, the text of the existing Visual Basic expression is replaced with **Value was set in XAML**, unless the Visual Basic expression is valid C# syntax.</span></span> <span data-ttu-id="9aceb-128">Visual Basic 式が有効な C# 構文である場合は、式が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9aceb-128">If the Visual Basic expression is valid C# syntax, then the expression is displayed.</span></span> <span data-ttu-id="9aceb-129">Visual Basic 式を C# に更新するには、ワークフロー デザイナーでその式を編集して、対応する C# 式を指定します。</span><span class="sxs-lookup"><span data-stu-id="9aceb-129">To update the Visual Basic expressions to C#, you can edit them in the workflow designer and specify the equivalent C# expression.</span></span> <span data-ttu-id="9aceb-130">Visual Basic 式を C# に更新する必要はありませんが、ワークフロー デザイナーで式を更新すると、式は C# に変換され、Visual Basic に戻すことができなくなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="9aceb-130">It is not required to update the Visual Basic expressions to C#, but once the expressions are updated in the workflow designer they are converted to C# and may not be reverted to Visual Basic.</span></span>

### <a name="using-c-expressions-in-code-workflows"></a><a name="CodeWorkflows"></a> <span data-ttu-id="9aceb-131">コードワークフローでの C# 式の使用</span><span class="sxs-lookup"><span data-stu-id="9aceb-131">Using C# expressions in code workflows</span></span>

<span data-ttu-id="9aceb-132">C# 式は、[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] コードベースのワークフローでサポートされていますが、ワークフローを呼び出す前に、<xref:System.Activities.XamlIntegration.TextExpressionCompiler.Compile%2A?displayProperty=nameWithType> を使用して C# 式をコンパイルする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9aceb-132">C# expressions are supported in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] code based workflows, but before the workflow can be invoked the C# expressions must be compiled using <xref:System.Activities.XamlIntegration.TextExpressionCompiler.Compile%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9aceb-133">ワークフローの作成者は、`CSharpValue` を使用して式の右辺値を表し、`CSharpReference` を使用して式の左辺値を表すことができます。</span><span class="sxs-lookup"><span data-stu-id="9aceb-133">Workflow authors can use `CSharpValue` to represent the r-value of an expression, and `CSharpReference` to represent the l-value of an expression.</span></span> <span data-ttu-id="9aceb-134">次の例では、`Assign` アクティビティに含まれる `WriteLine` アクティビティと `Sequence` アクティビティを使用してワークフローを作成します。</span><span class="sxs-lookup"><span data-stu-id="9aceb-134">In the following example, a workflow is created with an `Assign` activity and a `WriteLine` activity contained in a `Sequence` activity.</span></span> <span data-ttu-id="9aceb-135">`CSharpReference` は `Assign` の `To` 引数として指定され、式の左辺値を表します。</span><span class="sxs-lookup"><span data-stu-id="9aceb-135">A `CSharpReference` is specified for the `To` argument of the `Assign`, and represents the l-value of the expression.</span></span> <span data-ttu-id="9aceb-136">`CSharpValue` は `Assign` の `Value` 引数、および `WriteLine` の `Text` 引数として指定され、2 つの式の右辺値を表します。</span><span class="sxs-lookup"><span data-stu-id="9aceb-136">A `CSharpValue` is specified for the `Value` argument of the `Assign`, and for the `Text` argument of the `WriteLine`, and represents the r-value for those two expressions.</span></span>

```csharp
Variable<int> n = new Variable<int>
{
    Name = "n"
};

Activity wf = new Sequence
{
    Variables = { n },
    Activities =
    {
        new Assign<int>
        {
            To = new CSharpReference<int>("n"),
            Value = new CSharpValue<int>("new Random().Next(1, 101)")
        },
        new WriteLine
        {
            Text = new CSharpValue<string>("\"The number is \" + n")
        }
    }
};

CompileExpressions(wf);

WorkflowInvoker.Invoke(wf);
```

<span data-ttu-id="9aceb-137">ワークフローが作成されると、`CompileExpressions` ヘルパー メソッドを呼び出して C# 式がコンパイルされ、ワークフローが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="9aceb-137">After the workflow is constructed, the C# expressions are compiled by calling the `CompileExpressions` helper method and then the workflow is invoked.</span></span> <span data-ttu-id="9aceb-138">次の例は、`CompileExpressions` メソッドです。</span><span class="sxs-lookup"><span data-stu-id="9aceb-138">The following example is the `CompileExpressions` method.</span></span>

```csharp
static void CompileExpressions(Activity activity)
{
    // activityName is the Namespace.Type of the activity that contains the
    // C# expressions.
    string activityName = activity.GetType().ToString();

    // Split activityName into Namespace and Type.Append _CompiledExpressionRoot to the type name
    // to represent the new type that represents the compiled expressions.
    // Take everything after the last . for the type name.
    string activityType = activityName.Split('.').Last() + "_CompiledExpressionRoot";
    // Take everything before the last . for the namespace.
    string activityNamespace = string.Join(".", activityName.Split('.').Reverse().Skip(1).Reverse());

    // Create a TextExpressionCompilerSettings.
    TextExpressionCompilerSettings settings = new TextExpressionCompilerSettings
    {
        Activity = activity,
        Language = "C#",
        ActivityName = activityType,
        ActivityNamespace = activityNamespace,
        RootNamespace = null,
        GenerateAsPartialClass = false,
        AlwaysGenerateSource = true,
        ForImplementation = false
    };

    // Compile the C# expression.
    TextExpressionCompilerResults results =
        new TextExpressionCompiler(settings).Compile();

    // Any compilation errors are contained in the CompilerMessages.
    if (results.HasErrors)
    {
        throw new Exception("Compilation failed.");
    }

    // Create an instance of the new compiled expression type.
    ICompiledExpressionRoot compiledExpressionRoot =
        Activator.CreateInstance(results.ResultType,
            new object[] { activity }) as ICompiledExpressionRoot;

    // Attach it to the activity.
    CompiledExpressionInvoker.SetCompiledExpressionRoot(
        activity, compiledExpressionRoot);
}
```

> [!NOTE]
> <span data-ttu-id="9aceb-139">C# の式がコンパイルされていない場合は、 <xref:System.NotSupportedException> 次のようなメッセージを使用してワークフローが呼び出されると、がスローされます。 `Expression Activity type 'CSharpValue` 1 ' を実行するには、コンパイルが必要です。</span><span class="sxs-lookup"><span data-stu-id="9aceb-139">If the C# expressions are not compiled, a <xref:System.NotSupportedException> is thrown when the workflow is invoked with a message similar to the following: `Expression Activity type 'CSharpValue`1' requires compilation in order to run.</span></span>  <span data-ttu-id="9aceb-140">ワークフローがコンパイルされていることを確認してください。 '</span><span class="sxs-lookup"><span data-stu-id="9aceb-140">Please ensure that the workflow has been compiled.\`</span></span>

<span data-ttu-id="9aceb-141">カスタムのコードベースのワークフローで `DynamicActivity` を使用する場合は、次のコード例に示すように、`CompileExpressions` メソッドに変更を加える必要があります。</span><span class="sxs-lookup"><span data-stu-id="9aceb-141">If your custom code based workflow uses `DynamicActivity`, then some changes to the `CompileExpressions` method are required, as demonstrated in the following code example.</span></span>

```csharp
static void CompileExpressions(DynamicActivity dynamicActivity)
{
    // activityName is the Namespace.Type of the activity that contains the
    // C# expressions. For Dynamic Activities this can be retrieved using the
    // name property , which must be in the form Namespace.Type.
    string activityName = dynamicActivity.Name;

    // Split activityName into Namespace and Type.Append _CompiledExpressionRoot to the type name
    // to represent the new type that represents the compiled expressions.
    // Take everything after the last . for the type name.
    string activityType = activityName.Split('.').Last() + "_CompiledExpressionRoot";
    // Take everything before the last . for the namespace.
    string activityNamespace = string.Join(".", activityName.Split('.').Reverse().Skip(1).Reverse());

    // Create a TextExpressionCompilerSettings.
    TextExpressionCompilerSettings settings = new TextExpressionCompilerSettings
    {
        Activity = dynamicActivity,
        Language = "C#",
        ActivityName = activityType,
        ActivityNamespace = activityNamespace,
        RootNamespace = null,
        GenerateAsPartialClass = false,
        AlwaysGenerateSource = true,
        ForImplementation = true
    };

    // Compile the C# expression.
    TextExpressionCompilerResults results =
        new TextExpressionCompiler(settings).Compile();

    // Any compilation errors are contained in the CompilerMessages.
    if (results.HasErrors)
    {
        throw new Exception("Compilation failed.");
    }

    // Create an instance of the new compiled expression type.
    ICompiledExpressionRoot compiledExpressionRoot =
        Activator.CreateInstance(results.ResultType,
            new object[] { dynamicActivity }) as ICompiledExpressionRoot;

    // Attach it to the activity.
    CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation(
        dynamicActivity, compiledExpressionRoot);
}
```

<span data-ttu-id="9aceb-142">動的アクティビティで C# 式をコンパイルする `CompileExpressions` オーバーロードには、いくつかの相違点があります。</span><span class="sxs-lookup"><span data-stu-id="9aceb-142">There are several differences in the `CompileExpressions` overload that compiles the C# expressions in a dynamic activity.</span></span>

- <span data-ttu-id="9aceb-143">`CompileExpressions` のパラメーターが `DynamicActivity` です。</span><span class="sxs-lookup"><span data-stu-id="9aceb-143">The parameter to `CompileExpressions` is a `DynamicActivity`.</span></span>

- <span data-ttu-id="9aceb-144">型名および名前空間の取得に `DynamicActivity.Name` プロパティが使用されます。</span><span class="sxs-lookup"><span data-stu-id="9aceb-144">The type name and namespace are retrieved using the `DynamicActivity.Name` property.</span></span>

- <span data-ttu-id="9aceb-145">`TextExpressionCompilerSettings.ForImplementation` は `true` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="9aceb-145">`TextExpressionCompilerSettings.ForImplementation` is set to `true`.</span></span>

- <span data-ttu-id="9aceb-146">`CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation` の代わりに `CompiledExpressionInvoker.SetCompiledExpressionRoot` が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="9aceb-146">`CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation` is called instead of `CompiledExpressionInvoker.SetCompiledExpressionRoot`.</span></span>

<span data-ttu-id="9aceb-147">コードで式を使用する方法の詳細については、「 [命令型コードを使用したワークフロー、アクティビティ、および式の作成](authoring-workflows-activities-and-expressions-using-imperative-code.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9aceb-147">For more information about working with expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>

### <a name="using-c-expressions-in-xaml-workflows"></a><a name="XamlWorkflows"></a> <span data-ttu-id="9aceb-148">XAML ワークフローでの C# 式の使用</span><span class="sxs-lookup"><span data-stu-id="9aceb-148">Using C# expressions in XAML workflows</span></span>

<span data-ttu-id="9aceb-149">C# 式は XAML ワークフローでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="9aceb-149">C# expressions are supported in XAML workflows.</span></span> <span data-ttu-id="9aceb-150">コンパイルされた XAML ワークフローは型にコンパイルされ、Loose XAML ワークフローはランタイムによって読み込まれ、ワークフローの実行時にアクティビティ ツリーにコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="9aceb-150">Compiled XAML workflows are compiled into a type, and loose XAML workflows are loaded by the runtime and compiled into an activity tree when the workflow is executed.</span></span>

- [<span data-ttu-id="9aceb-151">コンパイルされた Xaml</span><span class="sxs-lookup"><span data-stu-id="9aceb-151">Compiled Xaml</span></span>](csharp-expressions.md#CompiledXaml)

- [<span data-ttu-id="9aceb-152">ルース Xaml</span><span class="sxs-lookup"><span data-stu-id="9aceb-152">Loose Xaml</span></span>](csharp-expressions.md#LooseXaml)

#### <a name="compiled-xaml"></a><a name="CompiledXaml"></a> <span data-ttu-id="9aceb-153">コンパイルされた Xaml</span><span class="sxs-lookup"><span data-stu-id="9aceb-153">Compiled Xaml</span></span>

<span data-ttu-id="9aceb-154">C# 式は、コンパイルされた XAML ワークフローでサポートされており、[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] を対象とする C# ワークフロー プロジェクトの一部として型にコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="9aceb-154">C# expressions are supported in compiled XAML workflows that are compiled to a type as part of a C# workflow project that targets [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)].</span></span> <span data-ttu-id="9aceb-155">コンパイルされた XAML は、Visual Studio でのワークフロー作成の既定の種類であり、Visual Studio で作成され、ターゲットとする C# ワークフロープロジェクトは [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] C# 式を使用します。</span><span class="sxs-lookup"><span data-stu-id="9aceb-155">Compiled XAML is the default type of workflow authoring in Visual Studio, and C# workflow projects created in Visual Studio that target [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] use C# expressions.</span></span>

#### <a name="loose-xaml"></a><a name="LooseXaml"></a> <span data-ttu-id="9aceb-156">ルース Xaml</span><span class="sxs-lookup"><span data-stu-id="9aceb-156">Loose Xaml</span></span>

<span data-ttu-id="9aceb-157">C# 式は Loose XAML ワークフローでがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="9aceb-157">C# expressions are supported in loose XAML workflows.</span></span> <span data-ttu-id="9aceb-158">Loose XAML ワークフローを読み込んで呼び出すワークフロー ホスト プログラムは、[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] を対象としている必要があります。また、<xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> は `true` (既定値は `false`) に設定する必要がります。</span><span class="sxs-lookup"><span data-stu-id="9aceb-158">The workflow host program that loads and invokes the loose XAML workflow must target [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], and <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> must be set to `true` (the default is `false`).</span></span> <span data-ttu-id="9aceb-159"><xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> を `true` に設定するには、<xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> プロパティが <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> に設定されている `true` インスタンスを作成し、そのインスタンスを <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType> へパラメーターとして渡します。</span><span class="sxs-lookup"><span data-stu-id="9aceb-159">To set <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> to `true`, create an <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> instance with its <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> property set to `true`, and pass it as a parameter to <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9aceb-160">`CompileExpressions`がに設定されていない場合、が `true` <xref:System.NotSupportedException> スローされ、次のようなメッセージが表示されます。 `Expression Activity type 'CSharpValue` 1 ' を実行するには、コンパイルが必要です。</span><span class="sxs-lookup"><span data-stu-id="9aceb-160">If `CompileExpressions` Is not set to `true`, a <xref:System.NotSupportedException> will be thrown with a message similar to the following: `Expression Activity type 'CSharpValue`1' requires compilation in order to run.</span></span>  <span data-ttu-id="9aceb-161">ワークフローがコンパイルされていることを確認してください。 '</span><span class="sxs-lookup"><span data-stu-id="9aceb-161">Please ensure that the workflow has been compiled.\`</span></span>

```csharp
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings
{
    CompileExpressions = true
};

DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;
```

<span data-ttu-id="9aceb-162">XAML ワークフローの操作の詳細については、「 [xaml との間でのワークフローとアクティビティのシリアル](serializing-workflows-and-activities-to-and-from-xaml.md)化」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9aceb-162">For more information about working with XAML workflows, see [Serializing Workflows and Activities to and from XAML](serializing-workflows-and-activities-to-and-from-xaml.md).</span></span>

### <a name="using-c-expressions-in-xamlx-workflow-services"></a><a name="WFServices"></a> <span data-ttu-id="9aceb-163">.XAMLX workflow services での C# 式の使用</span><span class="sxs-lookup"><span data-stu-id="9aceb-163">Using C# expressions in XAMLX workflow services</span></span>

<span data-ttu-id="9aceb-164">C# 式は XAMLX ワークフロー サービスでがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="9aceb-164">C# expressions are supported in XAMLX workflow services.</span></span> <span data-ttu-id="9aceb-165">ワークフロー サービスが IIS または WAS でホストされている場合、追加の手順は必要ありません。ただし、XAML ワークフロー サービスが自己ホスト型サービスの場合は、C# 式をコンパイルする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9aceb-165">When a workflow service is hosted in IIS or WAS then no additional steps are required, but if the XAML workflow service is self-hosted, then the C# expressions must be compiled.</span></span> <span data-ttu-id="9aceb-166">自己ホスト型の .XAMLX workflow サービスで C# の式をコンパイルするには、最初に .XAMLX ファイルをに読み込み、 `WorkflowService` 次に `Body` 、 `WorkflowService` `CompileExpressions` 「 [コードワークフローでの c# 式の使用](csharp-expressions.md#CodeWorkflows) 」セクションで説明したメソッドにのを渡します。</span><span class="sxs-lookup"><span data-stu-id="9aceb-166">To compile the C# expressions in a self-hosted XAMLX workflow service, first load the XAMLX file into a `WorkflowService`, and then pass the `Body` of the `WorkflowService` to the `CompileExpressions` method described in the previous [Using C# expressions in code workflows](csharp-expressions.md#CodeWorkflows) section.</span></span> <span data-ttu-id="9aceb-167">次の例では、XAMLX ワークフロー サービスが読み込まれ、C# 式がコンパイルされた後、ワークフロー サービスが開かれて要求を待機します。</span><span class="sxs-lookup"><span data-stu-id="9aceb-167">In the following example, a XAMLX workflow service is loaded, the C# expressions are compiled, and then the workflow service is opened and waits for requests.</span></span>

```csharp
// Load the XAMLX workflow service.
WorkflowService workflow1 =
    (WorkflowService)XamlServices.Load(xamlxPath);

// Compile the C# expressions in the workflow by passing the Body to CompileExpressions.
CompileExpressions(workflow1.Body);

// Initialize the WorkflowServiceHost.
var host = new WorkflowServiceHost(workflow1, new Uri("http://localhost:8293/Service1.xamlx"));

// Enable Metadata publishing/
ServiceMetadataBehavior smb = new ServiceMetadataBehavior();
smb.HttpGetEnabled = true;
smb.MetadataExporter.PolicyVersion = PolicyVersion.Policy15;
host.Description.Behaviors.Add(smb);

// Open the WorkflowServiceHost and wait for requests.
host.Open();
Console.WriteLine("Press enter to quit");
Console.ReadLine();
```

<span data-ttu-id="9aceb-168">C# 式がコンパイルされないと、`Open` の処理は成功しますが、ワークフローは呼び出し時に失敗します。</span><span class="sxs-lookup"><span data-stu-id="9aceb-168">If the C# expressions are not compiled, the `Open` operation succeeds but the workflow will fail when it is invoked.</span></span> <span data-ttu-id="9aceb-169">次の `CompileExpressions` メソッドは、前の「 [コードワークフローでの C# 式の使用](csharp-expressions.md#CodeWorkflows) 」セクションのメソッドと同じです。</span><span class="sxs-lookup"><span data-stu-id="9aceb-169">The following `CompileExpressions` method is the same as the method from the previous [Using C# expressions in code workflows](csharp-expressions.md#CodeWorkflows) section.</span></span>

```csharp
static void CompileExpressions(Activity activity)
{
    // activityName is the Namespace.Type of the activity that contains the
    // C# expressions.
    string activityName = activity.GetType().ToString();

    // Split activityName into Namespace and Type.Append _CompiledExpressionRoot to the type name
    // to represent the new type that represents the compiled expressions.
    // Take everything after the last . for the type name.
    string activityType = activityName.Split('.').Last() + "_CompiledExpressionRoot";
    // Take everything before the last . for the namespace.
    string activityNamespace = string.Join(".", activityName.Split('.').Reverse().Skip(1).Reverse());

    // Create a TextExpressionCompilerSettings.
    TextExpressionCompilerSettings settings = new TextExpressionCompilerSettings
    {
        Activity = activity,
        Language = "C#",
        ActivityName = activityType,
        ActivityNamespace = activityNamespace,
        RootNamespace = null,
        GenerateAsPartialClass = false,
        AlwaysGenerateSource = true,
        ForImplementation = false
    };

    // Compile the C# expression.
    TextExpressionCompilerResults results =
        new TextExpressionCompiler(settings).Compile();

    // Any compilation errors are contained in the CompilerMessages.
    if (results.HasErrors)
    {
        throw new Exception("Compilation failed.");
    }

    // Create an instance of the new compiled expression type.
    ICompiledExpressionRoot compiledExpressionRoot =
        Activator.CreateInstance(results.ResultType,
            new object[] { activity }) as ICompiledExpressionRoot;

    // Attach it to the activity.
    CompiledExpressionInvoker.SetCompiledExpressionRoot(
        activity, compiledExpressionRoot);
}
```
