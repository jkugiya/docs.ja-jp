---
description: 詳細については、「WorkflowIdentity とバージョン管理の使用」を参照してください。
title: WorkflowIdentity と Versioning の使用
ms.date: 03/30/2017
ms.assetid: b8451735-8046-478f-912b-40870a6c0c3a
ms.openlocfilehash: b51bce26b69d77e0be702e40a315dcd138d2fc03
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754967"
---
# <a name="using-workflowidentity-and-versioning"></a><span data-ttu-id="9ed78-103">WorkflowIdentity と Versioning の使用</span><span class="sxs-lookup"><span data-stu-id="9ed78-103">Using WorkflowIdentity and Versioning</span></span>

<span data-ttu-id="9ed78-104"><xref:System.Activities.WorkflowIdentity> を使用すると、ワークフロー アプリケーションの開発者は、名前と <xref:System.Version> をワークフロー定義に関連付け、永続化されたワークフロー インスタンスにこの情報を関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="9ed78-104"><xref:System.Activities.WorkflowIdentity> provides a way for workflow application developers to associate a name and a <xref:System.Version> with a workflow definition, and for this information to be associated with a persisted workflow instance.</span></span> <span data-ttu-id="9ed78-105">この ID 情報は、ワークフロー アプリケーションの開発者がワークフロー定義の複数のバージョンの side-by-side 実行などのシナリオを有効にするために使用できます。また、動的更新などの他の機能の基礎となります。</span><span class="sxs-lookup"><span data-stu-id="9ed78-105">This identity information can be used by workflow application developers to enable scenarios such as side-by-side execution of multiple versions of a workflow definition, and provides the cornerstone for other functionality such as dynamic update.</span></span> <span data-ttu-id="9ed78-106">このトピックでは、<xref:System.Activities.WorkflowIdentity> ホスティングでの <xref:System.Activities.WorkflowApplication> の使用の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="9ed78-106">This topic provides as overview of using <xref:System.Activities.WorkflowIdentity> with <xref:System.Activities.WorkflowApplication> hosting.</span></span> <span data-ttu-id="9ed78-107">ワークフローサービスでのワークフロー定義の side-by-side 実行の詳細については、「 [WorkflowServiceHost でのサイドバイサイドバージョン管理](../wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ed78-107">For information on side-by-side execution of workflow definitions in a workflow service, see [Side by Side Versioning in WorkflowServiceHost](../wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md).</span></span> <span data-ttu-id="9ed78-108">動的更新の詳細については、「 [動的更新](dynamic-update.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ed78-108">For information on dynamic update, see [Dynamic Update](dynamic-update.md).</span></span>

## <a name="in-this-topic"></a><span data-ttu-id="9ed78-109">このトピックの内容</span><span class="sxs-lookup"><span data-stu-id="9ed78-109">In this topic</span></span>

- [<span data-ttu-id="9ed78-110">WorkflowIdentity の使用</span><span class="sxs-lookup"><span data-stu-id="9ed78-110">Using WorkflowIdentity</span></span>](using-workflowidentity-and-versioning.md#UsingWorkflowIdentity)

  - [<span data-ttu-id="9ed78-111">WorkflowIdentity を使用した side-by-side 実行</span><span class="sxs-lookup"><span data-stu-id="9ed78-111">Side-by-side Execution using WorkflowIdentity</span></span>](using-workflowidentity-and-versioning.md#SxS)

- [<span data-ttu-id="9ed78-112">ワークフローのバージョン管理をサポートする .NET Framework 4 永続性データベースのアップグレード</span><span class="sxs-lookup"><span data-stu-id="9ed78-112">Upgrading .NET Framework 4 Persistence Databases to Support Workflow Versioning</span></span>](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases)

  - [<span data-ttu-id="9ed78-113">データベース スキーマをアップグレードするには</span><span class="sxs-lookup"><span data-stu-id="9ed78-113">To upgrade the database schema</span></span>](using-workflowidentity-and-versioning.md#ToUpgrade)

## <a name="using-workflowidentity"></a><a name="UsingWorkflowIdentity"></a> <span data-ttu-id="9ed78-114">WorkflowIdentity の使用</span><span class="sxs-lookup"><span data-stu-id="9ed78-114">Using WorkflowIdentity</span></span>

<span data-ttu-id="9ed78-115"><xref:System.Activities.WorkflowIdentity> を使用するには、インスタンスを作成および構成し、<xref:System.Activities.WorkflowApplication> インスタンスに関連付けます。</span><span class="sxs-lookup"><span data-stu-id="9ed78-115">To use <xref:System.Activities.WorkflowIdentity>, create an instance, configure it, and associate it with a <xref:System.Activities.WorkflowApplication> instance.</span></span> <span data-ttu-id="9ed78-116"><xref:System.Activities.WorkflowIdentity> インスタンスには 3 種類の識別情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="9ed78-116">A <xref:System.Activities.WorkflowIdentity> instance contains three identifying pieces of information.</span></span> <span data-ttu-id="9ed78-117"><xref:System.Activities.WorkflowIdentity.Name%2A> と <xref:System.Activities.WorkflowIdentity.Version%2A> は必須で、名前と <xref:System.Version> を表します。また、<xref:System.Activities.WorkflowIdentity.Package%2A> は省略可能で、アセンブリ名やその他の必要な情報などの情報を格納する追加文字列の指定に使用できます。</span><span class="sxs-lookup"><span data-stu-id="9ed78-117"><xref:System.Activities.WorkflowIdentity.Name%2A> and <xref:System.Activities.WorkflowIdentity.Version%2A> contain a name and a <xref:System.Version> and are required, and <xref:System.Activities.WorkflowIdentity.Package%2A> is optional and can be used to specify an additional string containing information such as assembly name or other desired information.</span></span> <span data-ttu-id="9ed78-118"><xref:System.Activities.WorkflowIdentity> は、その 3 つのプロパティのいずれかが他の <xref:System.Activities.WorkflowIdentity> と異なる場合に一意です。</span><span class="sxs-lookup"><span data-stu-id="9ed78-118">A <xref:System.Activities.WorkflowIdentity> is unique if any of its three properties are different from another <xref:System.Activities.WorkflowIdentity>.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9ed78-119"><xref:System.Activities.WorkflowIdentity> には、個人を特定できる情報 (PII) を含めないでください。</span><span class="sxs-lookup"><span data-stu-id="9ed78-119">A <xref:System.Activities.WorkflowIdentity> should not contain any personally identifiable information (PII).</span></span> <span data-ttu-id="9ed78-120">インスタンスの作成に使用される <xref:System.Activities.WorkflowIdentity> に関する情報は、ランタイムによるアクティビティ ライフ サイクルのさまざまなポイントで構成されているすべての追跡サービスに出力されます。</span><span class="sxs-lookup"><span data-stu-id="9ed78-120">Information about the <xref:System.Activities.WorkflowIdentity> used to create an instance is emitted to any configured tracking services at several different points of the activity life-cycle by the runtime.</span></span> <span data-ttu-id="9ed78-121">WF の追跡には PII (機密ユーザー データ) を非表示にするメカニズムがありません。</span><span class="sxs-lookup"><span data-stu-id="9ed78-121">WF Tracking does not have any mechanism to hide PII (sensitive user data).</span></span> <span data-ttu-id="9ed78-122">そのため、<xref:System.Activities.WorkflowIdentity> インスタンスには PII データを含めないでください。PII データは、ランタイムによって追跡レコードに出力され、追跡レコードを表示するためのアクセス権を持つユーザーに表示できます。</span><span class="sxs-lookup"><span data-stu-id="9ed78-122">Therefore, a <xref:System.Activities.WorkflowIdentity> instance should not contain any PII data as it will be emitted by the runtime in tracking records and may be visible to anyone with access to view the tracking records.</span></span>

<span data-ttu-id="9ed78-123">次の例では、<xref:System.Activities.WorkflowIdentity> を作成し、`MortgageWorkflow` のワークフロー定義を使用して作成したワークフローのインスタンスに関連付けます。</span><span class="sxs-lookup"><span data-stu-id="9ed78-123">In the following example, a <xref:System.Activities.WorkflowIdentity> is created and associated with an instance of a workflow created using a `MortgageWorkflow` workflow definition.</span></span>

```csharp
WorkflowIdentity identityV1 = new WorkflowIdentity
{
    Name = "MortgageWorkflow v1",
    Version = new Version(1, 0, 0, 0)
};

WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identity);

// Configure the WorkflowApplication with persistence and desired workflow event handlers.
ConfigureWorkflowApplication(wfApp);

// Run the workflow.
wfApp.Run();
```

<span data-ttu-id="9ed78-124">ワークフローを再読み込みして再開すると、永続化されたワークフロー インスタンスの <xref:System.Activities.WorkflowIdentity> と一致するように構成されている <xref:System.Activities.WorkflowIdentity> を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ed78-124">When reloading and resuming a workflow, a <xref:System.Activities.WorkflowIdentity> that is configured to match the <xref:System.Activities.WorkflowIdentity> of the persisted workflow instance must be used.</span></span>

```csharp
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identityV1);

// Configure the WorkflowApplication with persistence and desired workflow event handlers.
ConfigureWorkflowApplication(wfApp);

// Load the workflow.
wfApp.Load(instanceId);

// Resume the workflow...
```

<span data-ttu-id="9ed78-125">ワークフロー インスタンスの再読み込み時に使用される <xref:System.Activities.WorkflowIdentity> が永続化された <xref:System.Activities.WorkflowIdentity> と一致しない場合は、<xref:System.Activities.VersionMismatchException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="9ed78-125">If the <xref:System.Activities.WorkflowIdentity> used when reloading the workflow instance does not match the persisted <xref:System.Activities.WorkflowIdentity>, a <xref:System.Activities.VersionMismatchException> is thrown.</span></span> <span data-ttu-id="9ed78-126">次の例では、前の例で永続化された `MortgageWorkflow` インスタンスで読み込み操作が行われます。</span><span class="sxs-lookup"><span data-stu-id="9ed78-126">In the following example a load attempt is made on the `MortgageWorkflow` instance that was persisted in the previous example.</span></span> <span data-ttu-id="9ed78-127">この読み込み操作は、永続化されたインスタンスと一致しない、住宅ローン ワークフローの新しいバージョン用に構成された <xref:System.Activities.WorkflowIdentity> を使用して行われます。</span><span class="sxs-lookup"><span data-stu-id="9ed78-127">This load attempt is made using a <xref:System.Activities.WorkflowIdentity> configured for a newer version of the mortgage workflow that does not match the persisted instance.</span></span>

```csharp
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow_v2(), identityV2);

// Configure the WorkflowApplication with persistence and desired workflow event handlers.
ConfigureWorkflowApplication(wfApp);

// Attempt to load the workflow instance.
wfApp.Load(instanceId);

// Resume the workflow...
```

<span data-ttu-id="9ed78-128">前のコードが実行されると、次の <xref:System.Activities.VersionMismatchException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="9ed78-128">When the previous code is executed, the following <xref:System.Activities.VersionMismatchException> is thrown.</span></span>

```output
The WorkflowIdentity ('MortgageWorkflow v1; Version=1.0.0.0') of the loaded instance does not match the WorkflowIdentity ('MortgageWorkflow v2; Version=2.0.0.0') of the provided workflow definition. The instance can be loaded using a different definition, or updated using Dynamic Update.
```

### <a name="side-by-side-execution-using-workflowidentity"></a><a name="SxS"></a> <span data-ttu-id="9ed78-129">WorkflowIdentity を使用した side-by-side 実行</span><span class="sxs-lookup"><span data-stu-id="9ed78-129">Side-by-side Execution using WorkflowIdentity</span></span>

<span data-ttu-id="9ed78-130"><xref:System.Activities.WorkflowIdentity> を使用すると、ワークフローの複数のバージョンの side-by-side 実行を簡略化できます。</span><span class="sxs-lookup"><span data-stu-id="9ed78-130"><xref:System.Activities.WorkflowIdentity> can be used to facilitate the execution of multiple versions of a workflow side-by-side.</span></span> <span data-ttu-id="9ed78-131">たとえば、実行時間の長いワークフローのビジネス要件を変更します。</span><span class="sxs-lookup"><span data-stu-id="9ed78-131">One common scenario is changing business requirements on a long-running workflow.</span></span> <span data-ttu-id="9ed78-132">ワークフローの多くのインスタンスは、更新されたバージョンを配置すると実行できます。</span><span class="sxs-lookup"><span data-stu-id="9ed78-132">Many instances of a workflow could be running when an updated version is deployed.</span></span> <span data-ttu-id="9ed78-133">ホスト アプリケーションは、新しいインスタンスの開始時に更新されたワークフロー定義を使用するよう構成できます。また、インスタンスの再開時に適切なワークフロー定義を指定するのはホスト アプリケーションの役割です。</span><span class="sxs-lookup"><span data-stu-id="9ed78-133">The host application can be configured to use the updated workflow definition when starting new instances, and it is the responsibility of the host application to provide the correct workflow definition when resuming instances.</span></span> <span data-ttu-id="9ed78-134"><xref:System.Activities.WorkflowIdentity> を使用すると、ワークフロー インスタンスの再開時に、一致するワークフロー定義を特定して指定できます。</span><span class="sxs-lookup"><span data-stu-id="9ed78-134"><xref:System.Activities.WorkflowIdentity> can be used to identify and supply the matching workflow definition when resuming workflow instances.</span></span>

<span data-ttu-id="9ed78-135">永続化されたワークフロー インスタンスの <xref:System.Activities.WorkflowIdentity> を取得するには、<xref:System.Activities.WorkflowApplication.GetInstance%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="9ed78-135">To retrieve the <xref:System.Activities.WorkflowIdentity> of a persisted workflow instance, the <xref:System.Activities.WorkflowApplication.GetInstance%2A> method is used.</span></span> <span data-ttu-id="9ed78-136"><xref:System.Activities.WorkflowApplication.GetInstance%2A> メソッドは、永続化されたワークフロー インスタンスの <xref:System.Activities.WorkflowApplication.Id%2A>、および永続化されたインスタンスを格納する <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> を取得して、<xref:System.Activities.WorkflowApplicationInstance> を返します。</span><span class="sxs-lookup"><span data-stu-id="9ed78-136">The <xref:System.Activities.WorkflowApplication.GetInstance%2A> method takes the <xref:System.Activities.WorkflowApplication.Id%2A> of the persisted workflow instance and the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> that contains the persisted instance and returns a <xref:System.Activities.WorkflowApplicationInstance>.</span></span> <span data-ttu-id="9ed78-137"><xref:System.Activities.WorkflowApplicationInstance> には、永続化されたワークフロー インスタンスに関する情報 (関連付けられた <xref:System.Activities.WorkflowIdentity> など) が格納されます。</span><span class="sxs-lookup"><span data-stu-id="9ed78-137">A <xref:System.Activities.WorkflowApplicationInstance> contains information about a persisted workflow instance, including its associated <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="9ed78-138">この関連付けられた <xref:System.Activities.WorkflowIdentity> は、ワークフロー インスタンスを読み込んで再開するときに、適切なワークフロー定義を指定するためにホストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="9ed78-138">This associated <xref:System.Activities.WorkflowIdentity> can be used by the host to supply the correct workflow definition when loading and resuming the workflow instance.</span></span>

> [!NOTE]
> <span data-ttu-id="9ed78-139">null の <xref:System.Activities.WorkflowIdentity> は有効で、ホストで使用すると、関連付けられた <xref:System.Activities.WorkflowIdentity> がない、永続化されたインスタンスを適切なワークフロー定義にマップできます。</span><span class="sxs-lookup"><span data-stu-id="9ed78-139">A null <xref:System.Activities.WorkflowIdentity> is valid, and can be used by the host to map instances that were persisted with no associated <xref:System.Activities.WorkflowIdentity> to the proper workflow definition.</span></span> <span data-ttu-id="9ed78-140">このシナリオは、ワークフローアプリケーションがワークフローのバージョン管理を使用して最初に記述されていない場合、またはアプリケーションが .NET Framework 4 からアップグレードされた場合に発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9ed78-140">This scenario can occur when a workflow application was not initially written with workflow versioning, or when an application is upgraded from .NET Framework 4.</span></span> <span data-ttu-id="9ed78-141">詳細については、「 [.NET Framework 4 の永続性データベースのアップグレード」を](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases)参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ed78-141">For more information, see [Upgrading .NET Framework 4 Persistence Databases to Support Workflow Versioning](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases).</span></span>

<span data-ttu-id="9ed78-142">次の例では、を使用して、 `Dictionary<WorkflowIdentity, Activity>` インスタンスとそれに対応するワークフロー定義を関連付け <xref:System.Activities.WorkflowIdentity> ます。ワークフローは `MortgageWorkflow` 、に関連付けられているワークフロー定義を使用して開始され `identityV1` <xref:System.Activities.WorkflowIdentity> ます。</span><span class="sxs-lookup"><span data-stu-id="9ed78-142">In the following example a `Dictionary<WorkflowIdentity, Activity>` is used to associate <xref:System.Activities.WorkflowIdentity> instances with their matching workflow definitions, and a workflow is started using the `MortgageWorkflow` workflow definition, which is associated with the `identityV1` <xref:System.Activities.WorkflowIdentity>.</span></span>

```csharp
WorkflowIdentity identityV1 = new WorkflowIdentity
{
    Name = "MortgageWorkflow v1",
    Version = new Version(1, 0, 0, 0)
};

WorkflowIdentity identityV2 = new WorkflowIdentity
{
    Name = "MortgageWorkflow v2",
    Version = new Version(2, 0, 0, 0)
};

Dictionary<WorkflowIdentity, Activity> WorkflowVersionMap = new Dictionary<WorkflowIdentity, Activity>();
WorkflowVersionMap.Add(identityV1, new MortgageWorkflow());
WorkflowVersionMap.Add(identityV2, new MortgageWorkflow_v2());

WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identityV1);

// Configure the WorkflowApplication with persistence and desired workflow event handlers.
ConfigureWorkflowApplication(wfApp);

// Run the workflow.
wfApp.Run();
```

<span data-ttu-id="9ed78-143">次の例では、前の例の永続化されたワークフロー インスタンスに関する情報を <xref:System.Activities.WorkflowApplication.GetInstance%2A> を呼び出すことによって取得し、永続化された <xref:System.Activities.WorkflowIdentity> の情報を使用して一致するワークフロー定義を取得します。</span><span class="sxs-lookup"><span data-stu-id="9ed78-143">In the following example, information about the persisted workflow instance from the previous example is retrieved by calling <xref:System.Activities.WorkflowApplication.GetInstance%2A>, and the persisted <xref:System.Activities.WorkflowIdentity> information is used to retrieve the matching workflow definition.</span></span> <span data-ttu-id="9ed78-144">この情報を使用して <xref:System.Activities.WorkflowApplication> を構成すると、ワークフローが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="9ed78-144">This information is used to configure the <xref:System.Activities.WorkflowApplication>, and then the workflow is loaded.</span></span> <span data-ttu-id="9ed78-145"><xref:System.Activities.WorkflowApplication.Load%2A> を受け取る <xref:System.Activities.WorkflowApplicationInstance> オーバーロードが使用されるため、<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> で構成された <xref:System.Activities.WorkflowApplicationInstance> が <xref:System.Activities.WorkflowApplication> によって使用され、その結果、その <xref:System.Activities.WorkflowApplication.InstanceStore%2A> プロパティを構成する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="9ed78-145">Note that because the <xref:System.Activities.WorkflowApplication.Load%2A> overload that takes the <xref:System.Activities.WorkflowApplicationInstance> is used, the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> that was configured on the <xref:System.Activities.WorkflowApplicationInstance> is used by the <xref:System.Activities.WorkflowApplication> and therefore its <xref:System.Activities.WorkflowApplication.InstanceStore%2A> property does not need to be configured.</span></span>

> [!NOTE]
> <span data-ttu-id="9ed78-146"><xref:System.Activities.WorkflowApplication.InstanceStore%2A> プロパティを設定する場合は、<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> によって使用されるのと同じ <xref:System.Activities.WorkflowApplicationInstance> インスタンスで設定する必要があります。そうしないと、<xref:System.ArgumentException> がスローされ、"`The instance is configured with a different InstanceStore than this WorkflowApplication.`" というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9ed78-146">If the <xref:System.Activities.WorkflowApplication.InstanceStore%2A> property is set, it must be set with the same <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> instance used by the <xref:System.Activities.WorkflowApplicationInstance> or else an <xref:System.ArgumentException> will be thrown with the following message: `The instance is configured with a different InstanceStore than this WorkflowApplication.`.</span></span>

```csharp
// Get the WorkflowApplicationInstance of the desired workflow from the specified
// SqlWorkflowInstanceStore.
WorkflowApplicationInstance instance = WorkflowApplication.GetInstance(instanceId, store);

// Use the persisted WorkflowIdentity to retrieve the correct workflow
// definition from the dictionary.
Activity definition = WorkflowVersionMap[instance.DefinitionIdentity];

WorkflowApplication wfApp = new WorkflowApplication(definition, instance.DefinitionIdentity);

// Configure the WorkflowApplication with persistence and desired workflow event handlers.
ConfigureWorkflowApplication(wfApp);

// Load the persisted workflow instance.
wfApp.Load(instance);

// Resume the workflow...
```

## <a name="upgrading-net-framework-4-persistence-databases-to-support-workflow-versioning"></a><a name="UpdatingWF4PersistenceDatabases"></a> <span data-ttu-id="9ed78-147">ワークフローのバージョン管理をサポートするために .NET Framework 4 つの永続性データベースをアップグレードする</span><span class="sxs-lookup"><span data-stu-id="9ed78-147">Upgrading .NET Framework 4 Persistence Databases to Support Workflow Versioning</span></span>

<span data-ttu-id="9ed78-148">.NET Framework 4 つのデータベーススクリプトを使用して作成された永続性データベースをアップグレードするために、Sqlworkflowinstancestoreschemaupgrade.sql データベーススクリプトが用意されています。</span><span class="sxs-lookup"><span data-stu-id="9ed78-148">A SqlWorkflowInstanceStoreSchemaUpgrade.sql database script is provided to upgrade persistence databases created using the .NET Framework 4 database scripts.</span></span> <span data-ttu-id="9ed78-149">このスクリプトは、.NET Framework 4.5 で導入された新しいバージョン管理機能をサポートするようにデータベースを更新します。</span><span class="sxs-lookup"><span data-stu-id="9ed78-149">This script updates the databases to support the new versioning capabilities introduced in .NET Framework 4.5.</span></span> <span data-ttu-id="9ed78-150">データベースで永続化されたすべてのワークフロー インスタンスは、既定のバージョン番号が付与されるため、side-by-side 実行および動的更新に参加できるようになります。</span><span class="sxs-lookup"><span data-stu-id="9ed78-150">Any persisted workflow instances in the databases are given default versioning values, and can then participate in side-by-side execution and dynamic update.</span></span>

<span data-ttu-id="9ed78-151">.NET Framework 4.5 ワークフローアプリケーションが、指定されたスクリプトを使用してアップグレードされていない永続性データベースで新しいバージョン管理機能を使用する永続化操作を試みると、 <xref:System.Runtime.DurableInstancing.InstancePersistenceCommandException> 次のようなメッセージと共にがスローされます。</span><span class="sxs-lookup"><span data-stu-id="9ed78-151">If a .NET Framework 4.5 workflow application attempts any persistence operations that use the new versioning features on a persistence database which has not been upgraded using the provided script, an <xref:System.Runtime.DurableInstancing.InstancePersistenceCommandException> is thrown with a message similar to the following message.</span></span>

```output
The SqlWorkflowInstanceStore has a database version of '4.0.0.0'. InstancePersistenceCommand 'System.Activities.DurableInstancing.CreateWorkflowOwnerWithIdentityCommand' cannot be run against this database version.  Please upgrade the database to '4.5.0.0'.
```

### <a name="to-upgrade-the-database-schema"></a><a name="ToUpgrade"></a> <span data-ttu-id="9ed78-152">データベーススキーマをアップグレードするには</span><span class="sxs-lookup"><span data-stu-id="9ed78-152">To upgrade the database schema</span></span>

1. <span data-ttu-id="9ed78-153">SQL Server Management Studio を開き、 **.\SQLEXPRESS** などの永続性データベースサーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="9ed78-153">Open SQL Server Management Studio and connect to the persistence database server, for example **.\SQLEXPRESS**.</span></span>

2. <span data-ttu-id="9ed78-154">[**ファイル**] メニューの [**開く** **] をクリック** します。</span><span class="sxs-lookup"><span data-stu-id="9ed78-154">Choose **Open**, **File** from the **File** menu.</span></span> <span data-ttu-id="9ed78-155">次のフォルダーに移動します: `C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en`。</span><span class="sxs-lookup"><span data-stu-id="9ed78-155">Browse to the following folder: `C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en`</span></span>

3. <span data-ttu-id="9ed78-156">**Sqlworkflowinstancestoreschemaupgrade.sql** を選択し、[**開く**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9ed78-156">Select **SqlWorkflowInstanceStoreSchemaUpgrade.sql** and click **Open**.</span></span>

4. <span data-ttu-id="9ed78-157">[ **使用できるデータベース** ] ドロップダウンで、永続性データベースの名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="9ed78-157">Select the name of the persistence database in the **Available Databases** drop-down.</span></span>

5. <span data-ttu-id="9ed78-158">[**クエリ**] メニューの [**実行**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9ed78-158">Choose **Execute** from the **Query** menu.</span></span>

<span data-ttu-id="9ed78-159">クエリが完了すると、データベース スキーマがアップグレードされるため、必要に応じて、永続化されたワークフロー インスタンスに割り当てられた既定のワークフロー ID を確認できます。</span><span class="sxs-lookup"><span data-stu-id="9ed78-159">When the query completes, the database schema is upgraded, and if desired, you can view the default workflow identity that was assigned to the persisted workflow instances.</span></span> <span data-ttu-id="9ed78-160">**オブジェクトエクスプローラー** の [**データベース**] ノードで永続性データベースを展開し、[**ビュー** ] ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="9ed78-160">Expand your persistence database in the **Databases** node of the **Object Explorer**, and then expand the **Views** node.</span></span> <span data-ttu-id="9ed78-161">**System.activities.durableinstancing.instances** を右クリックし、[**上位1000行の選択]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="9ed78-161">Right-click **System.Activities.DurableInstancing.Instances** and choose **Select Top 1000 Rows**.</span></span> <span data-ttu-id="9ed78-162">列の最後までスクロールし、ビューに追加された6つの **列 ([** **IdentityPackage**]、[ **ビルド**]、[ **メジャー**]、[ **マイナー**]、[ **リビジョン**]) が表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="9ed78-162">Scroll to end of the columns and note that there are six additional columns added to the view: **IdentityName**, **IdentityPackage**, **Build**, **Major**, **Minor**, and **Revision**.</span></span> <span data-ttu-id="9ed78-163">永続化されたワークフローでは、null のワークフロー id を表す null 値がこれらのフィールドに対して **null** になります。</span><span class="sxs-lookup"><span data-stu-id="9ed78-163">Any persisted workflows will have a value of **NULL** for these fields, representing a null workflow identity.</span></span>
