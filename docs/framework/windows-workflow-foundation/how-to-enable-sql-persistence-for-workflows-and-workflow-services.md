---
description: '詳細については、「方法: ワークフローとワークフローサービスの SQL 永続化を有効にする」を参照してください。'
title: '方法: ワークフローとワークフロー サービスの SQL 永続性を有効にする'
ms.date: 03/30/2017
ms.assetid: ca7bf77f-3e5d-4b23-b17a-d0b60f46411d
ms.openlocfilehash: 5c124c4ec1d75d4b3b24468c04a4fb82236aa29a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99777724"
---
# <a name="how-to-enable-sql-persistence-for-workflows-and-workflow-services"></a><span data-ttu-id="51fab-103">方法: ワークフローとワークフロー サービスの SQL 永続性を有効にする</span><span class="sxs-lookup"><span data-stu-id="51fab-103">How to: Enable SQL Persistence for Workflows and Workflow Services</span></span>

<span data-ttu-id="51fab-104">このトピックでは、ワークフローとワークフロー サービスの永続性をプログラムと構成ファイルの両方から使用して有効にできるように、SQL Workflow Instance Store の機能を構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="51fab-104">This topic describes how to configure the SQL Workflow Instance Store feature to enable persistence for your workflows and workflow services both programmatically and by using a configuration file.</span></span>

<span data-ttu-id="51fab-105">Windows Server App Fabric を使用すると、永続化の構成のプロセスを簡潔化できます。</span><span class="sxs-lookup"><span data-stu-id="51fab-105">Windows Server App Fabric simplifies the process of configuring persistence.</span></span> <span data-ttu-id="51fab-106">詳細については、「 [App Fabric の永続](/previous-versions/appfabric/ee790848(v=azure.10))化の構成」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="51fab-106">For more information, see [App Fabric Persistence Configuration](/previous-versions/appfabric/ee790848(v=azure.10)).</span></span>

<span data-ttu-id="51fab-107">SQL Workflow Instance Store 機能を使用する前に、この機能においてワークフロー インスタンスの永続化に使用するデータベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="51fab-107">Before using the SQL Workflow Instance Store feature, create a database that the feature uses to persist workflow instances.</span></span> <span data-ttu-id="51fab-108">[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] セットアップ プログラムによって、SQL Workflow Instance Store 機能に関連する SQL スクリプト ファイルが %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN フォルダーにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="51fab-108">The [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] set-up program copies SQL script files associated with the SQL Workflow Instance Store feature to the %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN folder.</span></span> <span data-ttu-id="51fab-109">これらのスクリプト ファイルは、SQL Workflow Instance Store がワークフロー インスタンスの永続化に使用する SQL Server 2005 または SQL Server 2008 のデータベースに対して実行します。</span><span class="sxs-lookup"><span data-stu-id="51fab-109">Run these script files against a SQL Server 2005 or SQL Server 2008 database that you want the SQL Workflow Instance Store to use to persist workflow instances.</span></span> <span data-ttu-id="51fab-110">最初に SqlWorkflowInstanceStoreSchema.sql ファイルを実行してから、SqlWorkflowInstanceStoreLogic.sql ファイルを実行します。</span><span class="sxs-lookup"><span data-stu-id="51fab-110">Run the SqlWorkflowInstanceStoreSchema.sql file first and then run the SqlWorkflowInstanceStoreLogic.sql file.</span></span>

> [!NOTE]
> <span data-ttu-id="51fab-111">永続性データベースをクリーンアップして新しいデータベースにするには、%WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN にあるスクリプトを次の順序で実行します。</span><span class="sxs-lookup"><span data-stu-id="51fab-111">To clean up the persistence database to have a fresh database, run the scripts in %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN in the following order.</span></span>
>
> 1. <span data-ttu-id="51fab-112">SqlWorkflowInstanceStoreSchema.sql</span><span class="sxs-lookup"><span data-stu-id="51fab-112">SqlWorkflowInstanceStoreSchema.sql</span></span>
> 2. <span data-ttu-id="51fab-113">SqlWorkflowInstanceStoreLogic.sql</span><span class="sxs-lookup"><span data-stu-id="51fab-113">SqlWorkflowInstanceStoreLogic.sql</span></span>

> [!IMPORTANT]
> <span data-ttu-id="51fab-114">永続性データベースを作成しない場合、ホストがワークフローを永続化しようとしたときに、SQL Workflow Instance Store 機能によって次のような例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="51fab-114">If you do not create a persistence database, the SQL Workflow Instance Store feature throws an exception similar to the following one when a host tries to persist workflows.</span></span>
>
> <span data-ttu-id="51fab-115">System.Data.SqlClient.SqlException: ストアド プロシージャ 'System.Activities.DurableInstancing.CreateLockOwner' が見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="51fab-115">System.Data.SqlClient.SqlException: Could not find stored procedure 'System.Activities.DurableInstancing.CreateLockOwner'</span></span>

<span data-ttu-id="51fab-116">以下のセクションでは、SQL Workflow Instance Store を使用してワークフローとワークフロー サービスの永続性を有効にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="51fab-116">The following sections describe how to enable persistence for workflows and workflow services using the SQL Workflow Instance Store.</span></span> <span data-ttu-id="51fab-117">SQL Workflow Instance Store のプロパティの詳細については、「 [Sql Workflow Instance store のプロパティ](properties-of-sql-workflow-instance-store.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="51fab-117">For more information about properties of the SQL Workflow Instance Store, see [Properties of SQL Workflow Instance Store](properties-of-sql-workflow-instance-store.md).</span></span>

## <a name="enabling-persistence-for-self-hosted-workflows-that-use-workflowapplication"></a><span data-ttu-id="51fab-118">WorkflowApplication を使用する自己ホスト型ワークフローの永続化の有効化</span><span class="sxs-lookup"><span data-stu-id="51fab-118">Enabling Persistence for Self-Hosted Workflows that use WorkflowApplication</span></span>

<span data-ttu-id="51fab-119"><xref:System.Activities.WorkflowApplication> オブジェクト モデルを使用して、プログラムから <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> を使用する自己ホスト型ワークフローの永続化を有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="51fab-119">You can enable persistence for self-hosted workflows that use <xref:System.Activities.WorkflowApplication> programmatically by using the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> object model.</span></span> <span data-ttu-id="51fab-120">これを行う手順を次に示します。</span><span class="sxs-lookup"><span data-stu-id="51fab-120">The following procedure contains steps to do this.</span></span>

#### <a name="to-enable-persistence-for-self-hosted-workflows"></a><span data-ttu-id="51fab-121">自己ホスト型ワークフローの永続化を有効にするには</span><span class="sxs-lookup"><span data-stu-id="51fab-121">To enable persistence for self-hosted workflows</span></span>

1. <span data-ttu-id="51fab-122">System.Activities.DurableInstancing.dll への参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="51fab-122">Add a reference to System.Activities.DurableInstancing.dll.</span></span>

2. <span data-ttu-id="51fab-123">ソース ファイルの先頭にある既存の "using" ステートメントの後に、次のステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="51fab-123">Add the following statement at the top of the source file after the existing "using" statements.</span></span>

    ```csharp
    using System.Activities.DurableInstancing;
    ```

3. <span data-ttu-id="51fab-124">次のコード例に示すように、<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> を構築して <xref:System.Activities.WorkflowApplication.InstanceStore%2A> の <xref:System.Activities.WorkflowApplication> に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="51fab-124">Construct a <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> and assign it to the <xref:System.Activities.WorkflowApplication.InstanceStore%2A> of the <xref:System.Activities.WorkflowApplication> as shown in the following code example.</span></span>

    ```csharp
    SqlWorkflowInstanceStore store =
        new SqlWorkflowInstanceStore("Server=.\\SQLEXPRESS;Initial Catalog=Persistence;Integrated Security=SSPI");

    WorkflowApplication wfApp =
        new WorkflowApplication(new Workflow1());

    wfApp.InstanceStore = store;
    ```

   > [!NOTE]
   > <span data-ttu-id="51fab-125">使用している SQL Server のエディションによって、接続文字列のサーバー名は異なる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="51fab-125">Depending on your edition of SQL Server, the connection string server name may be different.</span></span>

4. <span data-ttu-id="51fab-126"><xref:System.Activities.WorkflowApplication.Persist%2A> オブジェクトの <xref:System.Activities.WorkflowApplication> メソッドを呼び出してワークフローを永続化するか、<xref:System.Activities.WorkflowApplication.Unload%2A> メソッドを呼び出してワークフローを永続化およびアンロードします。</span><span class="sxs-lookup"><span data-stu-id="51fab-126">Invoke the <xref:System.Activities.WorkflowApplication.Persist%2A> method on the <xref:System.Activities.WorkflowApplication> object to persist a workflow, or <xref:System.Activities.WorkflowApplication.Unload%2A> method to persist and unload a workflow.</span></span> <span data-ttu-id="51fab-127">また、<xref:System.Activities.WorkflowApplication.PersistableIdle%2A> オブジェクトによって発生した <xref:System.Activities.WorkflowApplication> イベントを処理して、<xref:System.Activities.PersistableIdleAction.Persist> の適切なメンバー (<xref:System.Activities.PersistableIdleAction.Unload> または <xref:System.Activities.PersistableIdleAction>) を返すこともできます。</span><span class="sxs-lookup"><span data-stu-id="51fab-127">You can also handle the <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> event raised by the <xref:System.Activities.WorkflowApplication> object and return appropriate (<xref:System.Activities.PersistableIdleAction.Persist> or <xref:System.Activities.PersistableIdleAction.Unload>) member of <xref:System.Activities.PersistableIdleAction>.</span></span>

   ```csharp
   wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)
   {
       return PersistableIdleAction.Persist;
   };
   ```

> [!NOTE]
> <span data-ttu-id="51fab-128">詳細な手順については、[はじめにチュートリアル](getting-started-tutorial.md)の「[方法: 実行時間の長いワークフローの作成と実行](how-to-create-and-run-a-long-running-workflow.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="51fab-128">See the [How to: Create and Run a Long Running Workflow](how-to-create-and-run-a-long-running-workflow.md) step of the [Getting Started Tutorial](getting-started-tutorial.md) for step by step instructions.</span></span>

## <a name="enabling-persistence-for-self-hosted-workflow-services-that-use-the-workflowservicehost"></a><span data-ttu-id="51fab-129">WorkflowServiceHost を使用する自己ホスト型ワークフロー サービスの永続化の有効化</span><span class="sxs-lookup"><span data-stu-id="51fab-129">Enabling Persistence for Self-Hosted Workflow Services that use the WorkflowServiceHost</span></span>

<span data-ttu-id="51fab-130"><xref:System.ServiceModel.WorkflowServiceHost> クラスまたは <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> クラスを使用して、プログラムから <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> を使用する自己ホスト型ワークフロー サービスの永続化を有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="51fab-130">You can enable persistence for self-hosted workflow services that use <xref:System.ServiceModel.WorkflowServiceHost> programmatically by using the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> class or the <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> class.</span></span>

### <a name="using-the-sqlworkflowinstancestorebehavior-class"></a><span data-ttu-id="51fab-131">SqlWorkflowInstanceStoreBehavior クラスの使用</span><span class="sxs-lookup"><span data-stu-id="51fab-131">Using the SqlWorkflowInstanceStoreBehavior Class</span></span>

<span data-ttu-id="51fab-132"><xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> クラスを使用して、自己ホスト型ワークフロー サービスの永続化を有効にする手順を次に示します。</span><span class="sxs-lookup"><span data-stu-id="51fab-132">The following procedure contains steps to use the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> class to enable persistence for self-hosted workflow services.</span></span>

#### <a name="to-enable-persistence-using-sqlworkflowinstancestorebehavior"></a><span data-ttu-id="51fab-133">SqlWorkflowInstanceStoreBehavior を使用して永続化を有効にするには</span><span class="sxs-lookup"><span data-stu-id="51fab-133">To enable persistence using SqlWorkflowInstanceStoreBehavior</span></span>

1. <span data-ttu-id="51fab-134">System.ServiceModel.dll への参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="51fab-134">Add a reference to the System.ServiceModel.dll.</span></span>

2. <span data-ttu-id="51fab-135">ソース ファイルの先頭にある既存の "using" ステートメントの後に、次のステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="51fab-135">Add the following statement at the top of the source file after the existing "using" statements.</span></span>

    ```csharp
    using System.ServiceModel.Activities.Description;
    ```

3. <span data-ttu-id="51fab-136">`WorkflowServiceHost` のインスタンスを作成し、ワークフロー サービスのエンドポイントを追加します。</span><span class="sxs-lookup"><span data-stu-id="51fab-136">Create an instance of the `WorkflowServiceHost` and add endpoints for the workflow service.</span></span>

    ```csharp
    WorkflowServiceHost host = new WorkflowServiceHost(new CountingWorkflow(), new Uri(hostBaseAddress));
    host.AddServiceEndpoint("ICountingWorkflow", new BasicHttpBinding(), "");
    ```

4. <span data-ttu-id="51fab-137">`SqlWorkflowInstanceStoreBehavior` オブジェクトを作成して、動作オブジェクトのプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="51fab-137">Construct a `SqlWorkflowInstanceStoreBehavior` object and to set properties of the behavior object.</span></span>

    ```csharp
    SqlWorkflowInstanceStoreBehavior instanceStoreBehavior = new SqlWorkflowInstanceStoreBehavior(connectionString);
    instanceStoreBehavior.HostLockRenewalPeriod = new TimeSpan(0, 0, 5);
    instanceStoreBehavior.InstanceCompletionAction = InstanceCompletionAction.DeleteAll;
    instanceStoreBehavior.InstanceLockedExceptionAction = InstanceLockedExceptionAction.AggressiveRetry;
    instanceStoreBehavior.InstanceEncodingOption = InstanceEncodingOption.GZip;
    instanceStoreBehavior.RunnableInstancesDetectionPeriod = new TimeSpan("00:00:02");
    host.Description.Behaviors.Add(instanceStoreBehavior);
    ```

5. <span data-ttu-id="51fab-138">ワークフロー サービス ホストを開きます。</span><span class="sxs-lookup"><span data-stu-id="51fab-138">Open the workflow service host.</span></span>

    ```csharp
    host.Open();
    ```

### <a name="using-the-durableinstancingoptions-property"></a><span data-ttu-id="51fab-139">DurableInstancingOptions プロパティの使用</span><span class="sxs-lookup"><span data-stu-id="51fab-139">Using the DurableInstancingOptions Property</span></span>

<span data-ttu-id="51fab-140">`SqlWorkflowInstanceStoreBehavior` が適用される場合、`DurableInstancingOptions.InstanceStore` の `WorkflowServiceHost` は構成値を使用して作成された `SqlWorkflowInstanceStore` オブジェクトに設定されます。</span><span class="sxs-lookup"><span data-stu-id="51fab-140">When the `SqlWorkflowInstanceStoreBehavior` is applied, the `DurableInstancingOptions.InstanceStore` on the `WorkflowServiceHost` is set to the `SqlWorkflowInstanceStore` object created using the configuration values.</span></span> <span data-ttu-id="51fab-141">同じ内容をプログラムから実行するには、次のコード例に示すように、<xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> クラスを使用せずに `WorkflowServiceHost` の `SqlWorkflowInstanceStoreBehavior` プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="51fab-141">You can do the same programmatically to set the <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> property of the `WorkflowServiceHost` without using the `SqlWorkflowInstanceStoreBehavior` class as shown in the following code example.</span></span>

```csharp
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;
```

## <a name="enabling-persistence-for-was-hosted-workflow-services-that-use-the-workflowservicehost-using-a-configuration-file"></a><span data-ttu-id="51fab-142">WorkflowServiceHost を使用する WAS でホストされるワークフロー サービスの構成ファイルを使用した永続化の有効化</span><span class="sxs-lookup"><span data-stu-id="51fab-142">Enabling Persistence for WAS-Hosted Workflow Services that use the WorkflowServiceHost using a Configuration File</span></span>

<span data-ttu-id="51fab-143">構成ファイルを使用することで、自己ホスト型または Windows プロセス アクティブ化サービス (WAS) でホストされるワークフロー サービスの永続化を有効にできます。</span><span class="sxs-lookup"><span data-stu-id="51fab-143">You can enable persistence for self-hosted or Windows Process Activation Service (WAS)-hosted workflow services by using a configuration file.</span></span> <span data-ttu-id="51fab-144">WAS でホストされるワークフロー サービスは、自己ホスト型ワークフローのように WorkflowServiceHost を使用します。</span><span class="sxs-lookup"><span data-stu-id="51fab-144">A WAS-hosted workflow service uses the WorkflowServiceHost as the self-hosted workflow services do.</span></span>

<span data-ttu-id="51fab-145">`SqlWorkflowInstanceStoreBehavior`。 XML 構成を使用して[SQL Workflow Instance Store](sql-workflow-instance-store.md)のプロパティを簡単に変更できるようにするサービス動作。</span><span class="sxs-lookup"><span data-stu-id="51fab-145">The `SqlWorkflowInstanceStoreBehavior`, a service behavior that allows you to conveniently change the [SQL Workflow Instance Store](sql-workflow-instance-store.md) properties through XML configuration.</span></span> <span data-ttu-id="51fab-146">WAS でホストされるワークフロー サービスの場合は、Web.config ファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="51fab-146">For WAS-hosted workflow services, use the Web.config file.</span></span> <span data-ttu-id="51fab-147">次の構成例では、構成ファイルで `sqlWorkflowInstanceStore` という動作要素を使用して SQL Workflow Instance Store を構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="51fab-147">The following configuration example shows how to configure the SQL Workflow Instance Store by using the `sqlWorkflowInstanceStore` behavior element in a configuration file.</span></span>

```xml
<serviceBehaviors>
    <behavior name="">
        <sqlWorkflowInstanceStore
                    connectionString="Data Source=(local);Initial Catalog=DefaultPersistenceProviderDb;Integrated Security=True;Async=true"
                    instanceEncodingOption="GZip | None"
                    instanceCompletionAction="DeleteAll | DeleteNothing"
                    instanceLockedExceptionAction="NoRetry | BasicRetry |AggressiveRetry"
                    hostLockRenewalPeriod="00:00:30"
                    runnableInstancesDetectionPeriod="00:00:05" />

    </behavior>
</serviceBehaviors>
```

<span data-ttu-id="51fab-148">`connectionString` または `connectionStringName` プロパティの値が設定されていない場合、SQL Workflow Instance Store は既定の名前付き接続文字列 `DefaultSqlWorkflowInstanceStoreConnectionString` を使用します。</span><span class="sxs-lookup"><span data-stu-id="51fab-148">If you do not set values for the `connectionString` or the `connectionStringName` property, the SQL Workflow Instance Store uses the default named connection string `DefaultSqlWorkflowInstanceStoreConnectionString`.</span></span>

<span data-ttu-id="51fab-149">`SqlWorkflowInstanceStoreBehavior` が適用される場合、`DurableInstancingOptions.InstanceStore` の `WorkflowServiceHost` は構成値を使用して作成された `SqlWorkflowInstanceStore` オブジェクトに設定されます。</span><span class="sxs-lookup"><span data-stu-id="51fab-149">When the `SqlWorkflowInstanceStoreBehavior` is applied, the `DurableInstancingOptions.InstanceStore` on the `WorkflowServiceHost` is set to the `SqlWorkflowInstanceStore` object created using the configuration values.</span></span> <span data-ttu-id="51fab-150">同じ内容をプログラムから実行するには、サービスの動作要素を使用せずに `SqlWorkflowInstanceStore` を `WorkflowServiceHost` と一緒に使用します。</span><span class="sxs-lookup"><span data-stu-id="51fab-150">You can do the same programmatically to use the `SqlWorkflowInstanceStore` with `WorkflowServiceHost` without using the service behavior element.</span></span>

```csharp
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;
```

> [!IMPORTANT]
> <span data-ttu-id="51fab-151">ユーザー名やパスワードなどの機密情報は、Web.config ファイルに保存しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="51fab-151">It is recommended that you do not store sensitive information such as user names and passwords in the Web.config file.</span></span> <span data-ttu-id="51fab-152">Web.config ファイルに機密情報を保存する場合は、ファイル システムのアクセス制御リスト (ACL) を使用して、Web.config ファイルへのアクセスをセキュリティで保護する必要があります。</span><span class="sxs-lookup"><span data-stu-id="51fab-152">If you do store sensitive information in the Web.config file, you should secure access to the Web.config file by using file system Access Control Lists (ACLs).</span></span> <span data-ttu-id="51fab-153">さらに、「 [保護された構成を使用した構成情報の暗号化](/previous-versions/aspnet/53tyfkaw(v=vs.100))」で説明されているように、構成ファイル内の構成値をセキュリティで保護することもできます。</span><span class="sxs-lookup"><span data-stu-id="51fab-153">In addition, you can also secure the configuration values within a configuration file as mentioned in [Encrypting Configuration Information Using Protected Configuration](/previous-versions/aspnet/53tyfkaw(v=vs.100)).</span></span>

### <a name="machineconfig-elements-related-to-the-sql-workflow-instance-store-feature"></a><span data-ttu-id="51fab-154">SQL Workflow Instance Store 機能に関連する Machine.config の要素</span><span class="sxs-lookup"><span data-stu-id="51fab-154">Machine.config Elements Related to the SQL Workflow Instance Store Feature</span></span>

<span data-ttu-id="51fab-155">[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] のインストールでは、SQL Workflow Instance Store 機能に関連する次の要素が Machine.config ファイルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="51fab-155">The [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] installation adds the following elements related to the SQL Workflow Instance Store feature to the Machine.config file:</span></span>

- <span data-ttu-id="51fab-156">構成ファイルのサービス動作要素を使用してサービスの永続化を構成できるように、Machine.config ファイルに次の動作拡張要素を追加し \<sqlWorkflowInstanceStore> ます。</span><span class="sxs-lookup"><span data-stu-id="51fab-156">Adds the following behavior extension element to the Machine.config file so that you can use the \<sqlWorkflowInstanceStore> service behavior element in the configuration file to configure persistence for your services.</span></span>

    ```xml
    <configuration>
        <system.serviceModel>
            <extensions>
                <behaviorExtensions>
                    <add name="sqlWorkflowInstanceStore" type="System.Activities.DurableInstancing.SqlWorkflowInstanceStoreElement, System.Activities.DurableInstancing, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />
                </behaviorExtensions>
            </extensions>
        </system.serviceModel>
    </configuration>
    ```
