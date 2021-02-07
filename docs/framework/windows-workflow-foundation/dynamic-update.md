---
description: '詳細情報: 動的更新'
title: 動的な更新
ms.date: 03/30/2017
ms.assetid: 8b6ef19b-9691-4b4b-824c-3c651a9db96e
ms.openlocfilehash: 925212d94dc90a2e29397370746c7191a403c984
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742421"
---
# <a name="dynamic-update"></a><span data-ttu-id="c080f-103">動的な更新</span><span class="sxs-lookup"><span data-stu-id="c080f-103">Dynamic Update</span></span>

<span data-ttu-id="c080f-104">動的更新は、ワークフロー アプリケーションの開発者が永続化されたワークフロー インスタンスのワークフロー定義を更新するためのメカニズムを提供します。</span><span class="sxs-lookup"><span data-stu-id="c080f-104">Dynamic update provides a mechanism for workflow application developers to update the workflow definition of a persisted workflow instance.</span></span> <span data-ttu-id="c080f-105">これには、バグ修正の実装、新しい要件の実装、または予期しない変更への対応があります。</span><span class="sxs-lookup"><span data-stu-id="c080f-105">This can be to implement a bug fix, new requirements, or to accommodate unexpected changes.</span></span> <span data-ttu-id="c080f-106">このトピックでは、.NET Framework 4.5 で導入された動的更新機能の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="c080f-106">This topic provides an overview of the dynamic update functionality introduced in .NET Framework 4.5.</span></span>

## <a name="dynamic-update"></a><span data-ttu-id="c080f-107">動的な更新</span><span class="sxs-lookup"><span data-stu-id="c080f-107">Dynamic Update</span></span>

<span data-ttu-id="c080f-108">永続化されたワークフロー インスタンスに動的更新を適用するには、必要な変更を反映するよう永続化されたワークフロー インスタンスを変更する方法を説明した指示をランタイム用に含む <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> を作成します。</span><span class="sxs-lookup"><span data-stu-id="c080f-108">To apply dynamic updates to a persisted workflow instance, a <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> is created that contains instructions for the runtime that describe how to modify the persisted workflow instance to reflect the desired changes.</span></span> <span data-ttu-id="c080f-109">更新マップが作成されると、対象の永続化されたワークフロー インスタンスに適用されます。</span><span class="sxs-lookup"><span data-stu-id="c080f-109">Once the update map is created, it is applied to the desired persisted workflow instances.</span></span> <span data-ttu-id="c080f-110">動的更新が適用されると、更新された新しいワークフロー定義を使用して、ワークフロー インスタンスが再開される場合があります。</span><span class="sxs-lookup"><span data-stu-id="c080f-110">Once the dynamic update is applied, the workflow instance may be resumed using the new updated workflow definition.</span></span> <span data-ttu-id="c080f-111">更新マップを作成して適用する際に必要な手順は 4 つあります。</span><span class="sxs-lookup"><span data-stu-id="c080f-111">There are four steps required to create and apply an update map.</span></span>

1. [<span data-ttu-id="c080f-112">動的更新用のワークフロー定義を準備します。</span><span class="sxs-lookup"><span data-stu-id="c080f-112">Prepare the workflow definition for dynamic update</span></span>](dynamic-update.md#Prepare)

2. [<span data-ttu-id="c080f-113">必要な変更を反映するようにワークフロー定義を更新します。</span><span class="sxs-lookup"><span data-stu-id="c080f-113">Update the workflow definition to reflect the desired changes</span></span>](dynamic-update.md#Update)

3. [<span data-ttu-id="c080f-114">更新マップを作成します。</span><span class="sxs-lookup"><span data-stu-id="c080f-114">Create the update map</span></span>](dynamic-update.md#Create)

4. [<span data-ttu-id="c080f-115">目的の永続化されたワークフロー インスタンスに更新マップを適用します。</span><span class="sxs-lookup"><span data-stu-id="c080f-115">Apply the update map to the desired persisted workflow instances</span></span>](dynamic-update.md#Apply)

> [!NOTE]
> <span data-ttu-id="c080f-116">更新マップの作成に対応する手順 1. ～ 3. は、更新の適用とは関係なく実行できます。</span><span class="sxs-lookup"><span data-stu-id="c080f-116">Note that steps 1 through 3, which cover the creation of the update map, may be performed independently of applying the update.</span></span> <span data-ttu-id="c080f-117">ワークフロー開発者が更新マップをオフラインで作成する一般的なシナリオでは、管理者が後で更新プログラムを適用します。</span><span class="sxs-lookup"><span data-stu-id="c080f-117">A common scenario that the workflow developer will create the update map offline, and then an administrator will apply the update at a later time.</span></span>

<span data-ttu-id="c080f-118">このトピックでは、コンパイルされた XAML ワークフローの永続インスタンスに新しいアクティビティを追加するという動的更新プロセスの概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="c080f-118">This topic provides an overview of the dynamic update process of adding a new activity to a persisted instance of a compiled Xaml workflow.</span></span>

### <a name="prepare-the-workflow-definition-for-dynamic-update"></a><a name="Prepare"></a> <span data-ttu-id="c080f-119">動的更新のワークフロー定義を準備する</span><span class="sxs-lookup"><span data-stu-id="c080f-119">Prepare the workflow definition for dynamic update</span></span>

<span data-ttu-id="c080f-120">動的更新プロセスでは、最初に、更新に必要なワークフロー定義を準備します。</span><span class="sxs-lookup"><span data-stu-id="c080f-120">The first step in the dynamic update process is to prepare the desired workflow definition for update.</span></span> <span data-ttu-id="c080f-121">これを行うには、<xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> メソッドを呼び出し、変更するワークフロー定義を渡します。</span><span class="sxs-lookup"><span data-stu-id="c080f-121">This is done by calling the <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> method and passing in the workflow definition to modify.</span></span> <span data-ttu-id="c080f-122">このメソッドは、ワークフロー ツリーを検証して、変更後のワークフロー定義と後で比較できるようにタグ付けを必要とする、パブリック アクティビティやパブリック変数などのすべてのオブジェクトを特定します。</span><span class="sxs-lookup"><span data-stu-id="c080f-122">This method validates and then walks the workflow tree to identify all of the objects such as public activities and variables that need to be tagged so they can be compared later with the modified workflow definition.</span></span> <span data-ttu-id="c080f-123">この処理が完了すると、ワークフロー ツリーは複製され、元のワークフロー定義にアタッチされます。</span><span class="sxs-lookup"><span data-stu-id="c080f-123">When this is complete, the workflow tree is cloned and attached to the original workflow definition.</span></span> <span data-ttu-id="c080f-124">更新マップを作成すると、ワークフロー定義の更新後のバージョンが元のワークフロー定義と比較され、その相違点に基づいて更新マップが生成されます。</span><span class="sxs-lookup"><span data-stu-id="c080f-124">When the update map is created, the updated version of the workflow definition is compared with the original workflow definition and the update map is generated based on the differences.</span></span>

<span data-ttu-id="c080f-125">動的更新用に XAML ワークフローを準備するために、XAML ワークフローが <xref:System.Activities.ActivityBuilder> に読み込まれた後、<xref:System.Activities.ActivityBuilder> が <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> に渡される場合があります。</span><span class="sxs-lookup"><span data-stu-id="c080f-125">To prepare a Xaml workflow for dynamic update it may be loaded into an <xref:System.Activities.ActivityBuilder>, and then the <xref:System.Activities.ActivityBuilder> is passed into <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType>.</span></span>

> [!NOTE]
> <span data-ttu-id="c080f-126">シリアル化されたワークフローの操作の詳細について <xref:System.Activities.ActivityBuilder> は、「 [XAML との間でのワークフローとアクティビティのシリアル](serializing-workflows-and-activities-to-and-from-xaml.md)化」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c080f-126">For more information about working with serialized workflows and <xref:System.Activities.ActivityBuilder>, see [Serializing Workflows and Activities to and from XAML](serializing-workflows-and-activities-to-and-from-xaml.md).</span></span>

<span data-ttu-id="c080f-127">次の例では、(複数の子アクティビティを持つ `MortgageWorkflow` で構成される) <xref:System.Activities.Statements.Sequence> の定義が <xref:System.Activities.ActivityBuilder> に読み込まれ、動的更新用に準備されます。</span><span class="sxs-lookup"><span data-stu-id="c080f-127">In the following example, a `MortgageWorkflow` definition (that consists of a <xref:System.Activities.Statements.Sequence> with several child activities) is loaded into an <xref:System.Activities.ActivityBuilder>, and then prepared for dynamic update.</span></span> <span data-ttu-id="c080f-128">メソッドから制御が戻ると、<xref:System.Activities.ActivityBuilder> には元のワークフロー定義とコピーが格納されます。</span><span class="sxs-lookup"><span data-stu-id="c080f-128">After the method returns, the <xref:System.Activities.ActivityBuilder> contains the original workflow definition as well as a copy.</span></span>

```csharp
// Load the MortgageWorkflow definition from Xaml into
// an ActivityBuilder.
XamlXmlReaderSettings readerSettings = new XamlXmlReaderSettings()
{
    LocalAssembly = Assembly.GetExecutingAssembly()
};

XamlXmlReader xamlReader = new XamlXmlReader(@"C:\WorkflowDefinitions\MortgageWorkflow.xaml",
    readerSettings);

ActivityBuilder ab = XamlServices.Load(
    ActivityXamlServices.CreateBuilderReader(xamlReader)) as ActivityBuilder;

// Prepare the workflow definition for dynamic update.
DynamicUpdateServices.PrepareForUpdate(ab);
```

### <a name="update-the-workflow-definition-to-reflect-the-desired-changes"></a><a name="Update"></a> <span data-ttu-id="c080f-129">必要な変更を反映するようにワークフロー定義を更新する</span><span class="sxs-lookup"><span data-stu-id="c080f-129">Update the workflow definition to reflect the desired changes</span></span>

<span data-ttu-id="c080f-130">ワークフロー定義を更新するための準備が完了したら、必要な変更を加えることができます。</span><span class="sxs-lookup"><span data-stu-id="c080f-130">Once the workflow definition has been prepared for updating, the desired changes can be made.</span></span> <span data-ttu-id="c080f-131">アクティビティの追加または削除、パブリック変数の追加、移動、または削除、引数の追加または削除、およびアクティビティ デリゲートのシグネチャの変更を実行できます。</span><span class="sxs-lookup"><span data-stu-id="c080f-131">You can add or remove activities, add, move or delete public variables, add or remove arguments, and make changes to the signature of activity delegates.</span></span> <span data-ttu-id="c080f-132">実行中のアクティビティを削除したり、実行中のデリゲートのシグネチャを変更したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="c080f-132">You cannot remove a running activity or change the signature of a running delegate.</span></span> <span data-ttu-id="c080f-133">これらの変更は、コードを使用して行うか、再ホストされたワークフロー デザイナーで行うことができます。</span><span class="sxs-lookup"><span data-stu-id="c080f-133">These changes may be made using code, or in a re-hosted workflow designer.</span></span> <span data-ttu-id="c080f-134">次の例では、カスタムの `VerifyAppraisal` アクティビティが、前の例の `MortgageWorkflow` の本体を構成する Sequence に追加されます。</span><span class="sxs-lookup"><span data-stu-id="c080f-134">In the following example, a custom `VerifyAppraisal` activity is added to the Sequence that makes up the body of the `MortgageWorkflow` from the previous example.</span></span>

```csharp
// Make desired changes to the definition. In this example, we are
// inserting a new VerifyAppraisal activity as the 3rd child of the root Sequence.
VerifyAppraisal va = new VerifyAppraisal
{
    Result = new VisualBasicReference<bool>("LoanCriteria")
};

// Get the Sequence that makes up the body of the workflow.
Sequence s = ab.Implementation as Sequence;

// Insert the new activity into the Sequence.
s.Activities.Insert(2, va);
```

### <a name="create-the-update-map"></a><a name="Create"></a> <span data-ttu-id="c080f-135">更新マップを作成する</span><span class="sxs-lookup"><span data-stu-id="c080f-135">Create the update map</span></span>

<span data-ttu-id="c080f-136">更新用に準備されたワークフロー定義を変更すると、更新マップを作成できます。</span><span class="sxs-lookup"><span data-stu-id="c080f-136">Once the workflow definition that was prepared for update has been modified, the update map can be created.</span></span> <span data-ttu-id="c080f-137">動的更新マップを作成するには、<xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="c080f-137">To create a dynamic update map, the <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> method is invoked.</span></span> <span data-ttu-id="c080f-138">これにより、永続化されたワークフロー インスタンスを新しいワークフロー定義で読み込んで再開できるように変更するためにランタイムに必要な情報を含む <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> が返されます。</span><span class="sxs-lookup"><span data-stu-id="c080f-138">This returns a <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> that contains the information the runtime needs to modify a persisted workflow instance so that it may be loaded and resumed with the new workflow definition.</span></span> <span data-ttu-id="c080f-139">次の例では、前の例で変更した `MortgageWorkflow` 定義に対して動的マップが作成されます。</span><span class="sxs-lookup"><span data-stu-id="c080f-139">In the following example, a dynamic map is created for the modified `MortgageWorkflow` definition from the previous example.</span></span>

```csharp
// Create the update map.
DynamicUpdateMap map = DynamicUpdateServices.CreateUpdateMap(ab);
```

<span data-ttu-id="c080f-140">この更新マップは、永続化されたワークフロー インスタンスを変更するためにすぐに使用できますが、通常は、後で更新が適用されるように保存できます。</span><span class="sxs-lookup"><span data-stu-id="c080f-140">This update map can immediately be used to modify persisted workflow instances, or more typically it can be saved and the updates applied later.</span></span> <span data-ttu-id="c080f-141">更新マップを保存する 1 つの方法として、次の例に示すように、更新マップをファイルにシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="c080f-141">One way to save the update map is to serialize it to a file, as shown in the following example.</span></span>

```csharp
// Serialize the update map to a file.
DataContractSerializer serializer = new DataContractSerializer(typeof(DynamicUpdateMap));
using (FileStream fs = System.IO.File.Open(@"C:\WorkflowDefinitions\MortgageWorkflow.map", FileMode.Create))
{
    serializer.WriteObject(fs, map);
}
```

<span data-ttu-id="c080f-142"><xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> 空制御が戻ると、<xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> の呼び出し時に追加された、複製されたワークフロー定義とその他の動的更新情報が削除され、更新されたワークフロー インスタンスを後で再開するときに使用できるように変更後のワークフロー定義を保存できるようになります。</span><span class="sxs-lookup"><span data-stu-id="c080f-142">When <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> returns, the cloned workflow definition and other dynamic update information that was added in the call to <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> is removed, and the modified workflow definition is ready to be saved so that it can be used later when resuming updated workflow instances.</span></span> <span data-ttu-id="c080f-143">次の例では、変更後のワークフロー定義が `MortgageWorkflow_v1.1.xaml` に保存されます。</span><span class="sxs-lookup"><span data-stu-id="c080f-143">In the following example, the modified workflow definition is saved to `MortgageWorkflow_v1.1.xaml`.</span></span>

```csharp
// Save the modified workflow definition.
StreamWriter sw = File.CreateText(@"C:\WorkflowDefinitions\MortgageWorkflow_v1.1.xaml");
XamlWriter xw = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(sw, new XamlSchemaContext()));
XamlServices.Save(xw, ab);
sw.Close();
```

### <a name="apply-the-update-map-to-the-desired-persisted-workflow-instances"></a><a name="Apply"></a> <span data-ttu-id="c080f-144">目的の永続化されたワークフローインスタンスに更新マップを適用する</span><span class="sxs-lookup"><span data-stu-id="c080f-144">Apply the update map to the desired persisted workflow instances</span></span>

<span data-ttu-id="c080f-145">更新マップは作成後にいつでも適用できます。</span><span class="sxs-lookup"><span data-stu-id="c080f-145">Applying the update map can be done at any time after creating it.</span></span> <span data-ttu-id="c080f-146">これは、<xref:System.Activities.DynamicUpdate.DynamicUpdateMap> によって返された <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> インスタンスを使用してすぐに実行することも、更新マップの保存したコピーを使用して後で実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="c080f-146">It can be done right away using the <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> instance that was returned by <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType>, or it can be done later using a saved copy of the update map.</span></span> <span data-ttu-id="c080f-147">ワークフロー インスタンスを更新するには、<xref:System.Activities.WorkflowApplicationInstance> を使用して、そのワークフロー インスタンスを <xref:System.Activities.WorkflowApplication.GetInstance%2A?displayProperty=nameWithType> に読み込みます。</span><span class="sxs-lookup"><span data-stu-id="c080f-147">To update a workflow instance, load it into a <xref:System.Activities.WorkflowApplicationInstance> using <xref:System.Activities.WorkflowApplication.GetInstance%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c080f-148">次に、更新されたワークフロー定義と必要な <xref:System.Activities.WorkflowApplication> を使用して、<xref:System.Activities.WorkflowIdentity> を作成します。</span><span class="sxs-lookup"><span data-stu-id="c080f-148">Next, create a <xref:System.Activities.WorkflowApplication> using the updated workflow definition, and the desired <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="c080f-149">この <xref:System.Activities.WorkflowIdentity> は、元のワークフローの永続化に使用されたものとは異なる場合があるため、通常は、永続化されたインスタンスが変更されていることを示すために使用されます。</span><span class="sxs-lookup"><span data-stu-id="c080f-149">This <xref:System.Activities.WorkflowIdentity> may be different than the one that was used to persist the original workflow, and typically is in order to reflect that the persisted instance has been modified.</span></span> <span data-ttu-id="c080f-150"><xref:System.Activities.WorkflowApplication> は、作成されると、<xref:System.Activities.WorkflowApplication.Load%2A?displayProperty=nameWithType> を取得する <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> のオーバーロードを使用して読み込まれ、<xref:System.Activities.WorkflowApplication.Unload%2A?displayProperty=nameWithType> の呼び出しを使用してアンロードされます。</span><span class="sxs-lookup"><span data-stu-id="c080f-150">Once the <xref:System.Activities.WorkflowApplication> is created, it is loaded using the overload of <xref:System.Activities.WorkflowApplication.Load%2A?displayProperty=nameWithType> that takes a <xref:System.Activities.DynamicUpdate.DynamicUpdateMap>, and then unloaded with a call to <xref:System.Activities.WorkflowApplication.Unload%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c080f-151">これにより、動的更新が適用され、更新されたワークフロー インスタンスが永続化されます。</span><span class="sxs-lookup"><span data-stu-id="c080f-151">This applies the dynamic update and persists the updated workflow instance.</span></span>

```csharp
// Load the serialized update map.
DynamicUpdateMap map;
using (FileStream fs = File.Open(@"C:\WorkflowDefinitions\MortgageWorkflow.map", FileMode.Open))
{
    DataContractSerializer serializer = new DataContractSerializer(typeof(DynamicUpdateMap));
    object updateMap = serializer.ReadObject(fs);
    if (updateMap == null)
    {
        throw new ApplicationException("DynamicUpdateMap is null.");
    }

    map = (DynamicUpdateMap)updateMap;
}

// Retrieve a list of workflow instance ids that corresponds to the
// workflow instances to update. This step is the responsibility of
// the application developer.
List<Guid> ids = GetPersistedWorkflowIds();
foreach (Guid id in ids)
{
    // Get a proxy to the persisted workflow instance.
    SqlWorkflowInstanceStore store = new SqlWorkflowInstanceStore(connectionString);
    WorkflowApplicationInstance instance = WorkflowApplication.GetInstance(id, store);

    // If desired, you can inspect the WorkflowIdentity of the instance
    // using the DefinitionIdentity property to determine whether to apply
    // the update.
    Console.WriteLine(instance.DefinitionIdentity);

    // Create a workflow application. You must specify the updated workflow definition, and
    // you may provide an updated WorkflowIdentity if desired to reflect the update.
    WorkflowIdentity identity = new WorkflowIdentity
    {
        Name = "MortgageWorkflow v1.1",
        Version = new Version(1, 1, 0, 0)
    };

    // Load the persisted workflow instance using the updated workflow definition
    // and with an updated WorkflowIdentity. In this example the MortgageWorkflow class
    // contains the updated definition.
    WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identity);

    // Apply the dynamic update on the loaded instance.
    wfApp.Load(instance, map);

    // Unload the updated instance.
    wfApp.Unload();
}
```

### <a name="resuming-an-updated-workflow-instance"></a><span data-ttu-id="c080f-152">更新されたワークフロー インスタンスの再開</span><span class="sxs-lookup"><span data-stu-id="c080f-152">Resuming an Updated Workflow Instance</span></span>

<span data-ttu-id="c080f-153">動的更新が適用されると、ワークフロー インスタンスが再開される場合があります。</span><span class="sxs-lookup"><span data-stu-id="c080f-153">Once dynamic update has been applied, the workflow instance may be resumed.</span></span> <span data-ttu-id="c080f-154">更新された新しい定義と <xref:System.Activities.WorkflowIdentity> を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c080f-154">Note that the new updated definition and <xref:System.Activities.WorkflowIdentity> must be used.</span></span>

> [!NOTE]
> <span data-ttu-id="c080f-155">との使用の詳細について <xref:System.Activities.WorkflowApplication> <xref:System.Activities.WorkflowIdentity> は、「 [WorkflowIdentity とバージョン管理の使用](using-workflowidentity-and-versioning.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c080f-155">For more information about working with <xref:System.Activities.WorkflowApplication> and <xref:System.Activities.WorkflowIdentity>, see [Using WorkflowIdentity and Versioning](using-workflowidentity-and-versioning.md).</span></span>

<span data-ttu-id="c080f-156">次の例では、前の例の `MortgageWorkflow_v1.1.xaml` ワークフローがコンパイルされ、更新されたワークフロー定義を使用して読み込まれ、再開されます。</span><span class="sxs-lookup"><span data-stu-id="c080f-156">In the following example, the `MortgageWorkflow_v1.1.xaml` workflow from the previous example has been compiled, and is loaded and resumed using the updated workflow definition.</span></span>

```csharp
// Load the persisted workflow instance using the updated workflow definition
// and updated WorkflowIdentity.
WorkflowIdentity identity = new WorkflowIdentity
{
    Name = "MortgageWorkflow v1.1",
    Version = new Version(1, 1, 0, 0)
};

WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identity);

// Configure persistence and desired workflow event handlers.
// (Omitted for brevity.)
ConfigureWorkflowApplication(wfApp);

// Load the persisted workflow instance.
wfApp.Load(InstanceId);

// Resume the workflow.
// wfApp.ResumeBookmark(...);
```
