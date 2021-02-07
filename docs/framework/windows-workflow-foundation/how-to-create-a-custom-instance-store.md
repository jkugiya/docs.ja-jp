---
description: '詳細については、「方法: カスタムインスタンスストアを作成する」を参照してください。'
title: '方法: カスタム インスタンス ストアを作成する'
ms.date: 03/30/2017
ms.assetid: 593c4e9d-8a49-4e12-8257-cee5e6b4c075
ms.openlocfilehash: 3a1a511e6a97dffe510c839aceec8c9d91a77ec1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742135"
---
# <a name="how-to-create-a-custom-instance-store"></a><span data-ttu-id="16499-103">方法: カスタム インスタンス ストアを作成する</span><span class="sxs-lookup"><span data-stu-id="16499-103">How to: Create a Custom Instance Store</span></span>

[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] <span data-ttu-id="16499-104">には、<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> という、SQL Server を使用してワークフロー データの永続化を行うインスタンス ストアが含まれています。</span><span class="sxs-lookup"><span data-stu-id="16499-104">contains <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, an instance store that uses SQL Server to persist workflow data.</span></span> <span data-ttu-id="16499-105">ワークフロー データの永続化を別のメディアで行う、つまり、別のデータベースやファイル システムなどを使用して行う必要があるアプリケーションの場合は、カスタム インスタンス ストアを実装できます。</span><span class="sxs-lookup"><span data-stu-id="16499-105">If your application is required to persist workflow data to another medium, such as a different database or a file system, you can implement a custom instance store.</span></span> <span data-ttu-id="16499-106">カスタム インスタンス ストアを作成するには、抽象 <xref:System.Runtime.DurableInstancing.InstanceStore> クラスを拡張し、その実装に必要なメソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="16499-106">A custom instance store is created by extending the abstract <xref:System.Runtime.DurableInstancing.InstanceStore> class and implementing the methods that are required for the implementation.</span></span> <span data-ttu-id="16499-107">カスタムインスタンスストアの完全な実装については、「 [企業の購入プロセス](./samples/corporate-purchase-process.md) 」のサンプルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="16499-107">For a complete implementation of a custom instance store, see the [Corporate Purchase Process](./samples/corporate-purchase-process.md) sample.</span></span>

## <a name="implementing-the-begintrycommand-method"></a><span data-ttu-id="16499-108">BeginTryCommand メソッドの実装</span><span class="sxs-lookup"><span data-stu-id="16499-108">Implementing the BeginTryCommand method</span></span>

<span data-ttu-id="16499-109"><xref:System.Runtime.DurableInstancing.InstanceStore.BeginTryCommand%2A> は永続化エンジンによってインスタンス ストアに送信されます。</span><span class="sxs-lookup"><span data-stu-id="16499-109">The <xref:System.Runtime.DurableInstancing.InstanceStore.BeginTryCommand%2A> is sent to the instance store by the persistence engine.</span></span> <span data-ttu-id="16499-110">`command` パラメーターの型は、どのコマンドを実行するかを示します。このパラメーターは次のいずれかになります:</span><span class="sxs-lookup"><span data-stu-id="16499-110">The type of the `command` parameter indicates which command is being executed; this parameter can be of the following types:</span></span>

- <span data-ttu-id="16499-111"><xref:System.Activities.DurableInstancing.SaveWorkflowCommand>: ワークフローをストレージ メディアに永続化する場合は、永続化エンジンがこのコマンドをインスタンス ストアに送信します。</span><span class="sxs-lookup"><span data-stu-id="16499-111"><xref:System.Activities.DurableInstancing.SaveWorkflowCommand>: The persistence engine sends this command to the instance store when a workflow is to be persisted to the storage medium.</span></span> <span data-ttu-id="16499-112">ワーク フローの永続性データは、<xref:System.Activities.DurableInstancing.SaveWorkflowCommand.InstanceData%2A> パラメーターの `command` メンバー内のメソッドに提供されます。</span><span class="sxs-lookup"><span data-stu-id="16499-112">The workflow persistence data is provided to the method in the <xref:System.Activities.DurableInstancing.SaveWorkflowCommand.InstanceData%2A> member of the `command` parameter.</span></span>

- <span data-ttu-id="16499-113"><xref:System.Activities.DurableInstancing.LoadWorkflowCommand>: ワークフローをストレージ メディアから読み込む場合は、永続化エンジンがこのコマンドをインスタンス ストアに送信します。</span><span class="sxs-lookup"><span data-stu-id="16499-113"><xref:System.Activities.DurableInstancing.LoadWorkflowCommand>: The persistence engine sends this command to the instance store when a workflow is to be loaded from the storage medium.</span></span> <span data-ttu-id="16499-114">読み込むワークフローのインスタンス ID は、`instanceId` パラメーターの <xref:System.Runtime.DurableInstancing.InstancePersistenceContext.InstanceView%2A> プロパティの `context` パラメーター内のメソッドに提供されます。</span><span class="sxs-lookup"><span data-stu-id="16499-114">The instance ID of the workflow to be loaded is provided to the method in the `instanceId` parameter of the <xref:System.Runtime.DurableInstancing.InstancePersistenceContext.InstanceView%2A> property of the `context` parameter.</span></span>

- <span data-ttu-id="16499-115"><xref:System.Activities.DurableInstancing.CreateWorkflowOwnerCommand>: <xref:System.ServiceModel.Activities.WorkflowServiceHost> をロック所有者として登録する必要がある場合は、永続化エンジンがこのコマンドをインスタンス ストアに送信します。</span><span class="sxs-lookup"><span data-stu-id="16499-115"><xref:System.Activities.DurableInstancing.CreateWorkflowOwnerCommand>: The persistence engine sends this command to the instance store when a <xref:System.ServiceModel.Activities.WorkflowServiceHost> must be registered as a lock owner.</span></span> <span data-ttu-id="16499-116">現在のワーク フローのインスタンス ID を、<xref:System.Runtime.DurableInstancing.InstancePersistenceContext.BindInstanceOwner%2A> パラメーターの `context` メソッドを使用してインスタンス ストアに提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="16499-116">The instance ID of the current workflow should be provided to the instance store using <xref:System.Runtime.DurableInstancing.InstancePersistenceContext.BindInstanceOwner%2A> method of the `context` parameter.</span></span>

     <span data-ttu-id="16499-117">次のコード スニペットは、CreateWorkflowOwner コマンドを実装して明示的なロック所有者を割り当てる方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="16499-117">The following code snippet demonstrates how to implement the CreateWorkflowOwner command to assign an explicit lock owner.</span></span>

    ```csharp
    XName WFInstanceScopeName = XName.Get(scopeName, "<namespace>");
    ...
    CreateWorkflowOwnerCommand createCommand = new CreateWorkflowOwnerCommand()
    {
        InstanceOwnerMetadata =
        {
            { WorkflowHostTypeName, new InstanceValue(WFInstanceScopeName) },
        }
    };
    InstanceHandle ownerHandle = store.CreateInstanceHandle();
    store.DefaultInstanceOwner = store.Execute(
                                   ownerHandle,
                                   createCommand,
                                   TimeSpan.FromSeconds(30)).InstanceOwner;
    childInstance.AddInitialInstanceValues(new Dictionary<XName, object>() { { WorkflowHostTypeName, WFInstanceScopeName } });
    ```

- <span data-ttu-id="16499-118"><xref:System.Activities.DurableInstancing.DeleteWorkflowOwnerCommand>: ロック所有者のインスタンス ID をインスタンス ストアから削除してよい場合は、永続化エンジンがこのコマンドをインスタンス ストアに送信します。</span><span class="sxs-lookup"><span data-stu-id="16499-118"><xref:System.Activities.DurableInstancing.DeleteWorkflowOwnerCommand>: The persistence engine sends this command to the instance store when the instance ID of a lock owner can be removed from the instance store.</span></span> <span data-ttu-id="16499-119"><xref:System.Activities.DurableInstancing.CreateWorkflowOwnerCommand> と同様に、アプリケーションがロック所有者の ID を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="16499-119">As with <xref:System.Activities.DurableInstancing.CreateWorkflowOwnerCommand>, the ID of the lock owner should be provided by the application.</span></span>

     <span data-ttu-id="16499-120">次のコード スニペットは、<xref:System.Activities.DurableInstancing.DeleteWorkflowOwnerCommand> を使用してロックを解除する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="16499-120">The following code snippet demonstrates how to release a lock using <xref:System.Activities.DurableInstancing.DeleteWorkflowOwnerCommand>.</span></span>

    ```csharp
    static void FreeHandleAndDeleteOwner(InstanceStore store, InstanceHandle handle)
    {
        handle.Free();
        handle = store.CreateInstanceHandle(store.DefaultInstanceOwner);
        try
        {
            // We need this sleep so that we dont prematurely delete the owner, we need time to update the database.
            Thread.Sleep(10000);
            store.Execute(handle, new DeleteWorkflowOwnerCommand(), TimeSpan.FromSeconds(10));
        }
        catch (InstancePersistenceCommandException ex) { Log.Inform(ex.Message); }
        catch (InstanceOwnerException ex) { Log.Inform(ex.Message); }
        catch (OperationCanceledException ex) { Log.Inform(ex.Message); }
        catch (Exception ex) { Log.Inform(ex.Message); }
        finally
        {
            handle.Free();
            store.DefaultInstanceOwner = null;
        }
    }
    ```

     <span data-ttu-id="16499-121">上のメソッドは、子インスタンスが実行されているときに Try ～ Catch ブロック内から呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="16499-121">The above method should be called in a Try/Catch block when a child instance is run.</span></span>

    ```csharp
    try
    {
        childInstance.Run();
    }
    catch (Exception)
    {
        throw ;
    }
    finally
    {
        FreeHandleAndDeleteOwner(store, ownerHandle);
    }
    ```

- <span data-ttu-id="16499-122"><xref:System.Activities.DurableInstancing.LoadWorkflowByInstanceKeyCommand>: ワークフローのインスタンス キーを使用してワークフローのインスタンスを読み込む場合は、永続化エンジンがこのコマンドをインスタンス ストアに送信します。</span><span class="sxs-lookup"><span data-stu-id="16499-122"><xref:System.Activities.DurableInstancing.LoadWorkflowByInstanceKeyCommand>: The persistence engine sends this command to the instance store when a workflow instance is to be loaded using the workflow’s instance key.</span></span> <span data-ttu-id="16499-123">インスタンス キーの ID は、このコマンドの <xref:System.Activities.DurableInstancing.LoadWorkflowByInstanceKeyCommand.LookupInstanceKey%2A> パラメーターを使用して確認できます。</span><span class="sxs-lookup"><span data-stu-id="16499-123">The ID of the instance key can be determined by using the <xref:System.Activities.DurableInstancing.LoadWorkflowByInstanceKeyCommand.LookupInstanceKey%2A> parameter of the command.</span></span>

- <span data-ttu-id="16499-124"><xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand>: ワークフローを読み込むワークフロー ホストを作成するために永続化ワークフローのアクティベーション パラメーターを取得する場合は、永続化エンジンがこのコマンドをインスタンス ストアに送信します。</span><span class="sxs-lookup"><span data-stu-id="16499-124"><xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand>: The persistence engine sends this command to the instance store to retrieve activation parameters for persisted workflows in order to create a workflow host that can then load workflows.</span></span> <span data-ttu-id="16499-125">このコマンドは、インスタンス ストアがアクティブ化できるインスタンスを見つけて、ホストに <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent> を発生させたとき、それに対する応答としてエンジンにより送信されます。</span><span class="sxs-lookup"><span data-stu-id="16499-125">This command is sent by the engine in response to the instance store raising the <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent> to the host when it locates an instance that can be activated.</span></span> <span data-ttu-id="16499-126">アクティブ化できるワーク フローがあるかどうかを判別するには、インスタンス ストアをポーリングする必要があります。</span><span class="sxs-lookup"><span data-stu-id="16499-126">The instance store should be polled to determine if there are workflows that can be activated.</span></span>

- <span data-ttu-id="16499-127"><xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand>: 実行可能なワークフロー インスタンスを読み込む場合、永続化エンジンがインスタンス ストアにこのコマンドを送信します。</span><span class="sxs-lookup"><span data-stu-id="16499-127"><xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand>: The persistence engine sends this command to the instance store to load runnable workflow instances.</span></span> <span data-ttu-id="16499-128">このコマンドは、インスタンス ストアが実行できるインスタンスを見つけて、ホストに <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> を発生させたとき、それに対する応答としてエンジンにより送信されます。</span><span class="sxs-lookup"><span data-stu-id="16499-128">This command is sent by the engine in response to the instance store raising the <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> to the host when it locates an instance that can be run.</span></span> <span data-ttu-id="16499-129">実行できるワークフローを見つけるには、インスタンス ストアをポーリングする必要があります。</span><span class="sxs-lookup"><span data-stu-id="16499-129">The instance store should poll for workflows that can be run.</span></span> <span data-ttu-id="16499-130">次のコード スニペットは、実行またはアクティブ化できるワークフローのために、インスタンス ストアのポーリングを行う方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="16499-130">The following code snippet demonstrates polling an instance store for workflows that can be run or activated.</span></span>

    ```csharp
    public void PollForEvents()
    {
        InstanceOwner[] storeOwners = this.GetInstanceOwners();

        foreach (InstanceOwner owner in storeOwners)
        {
            foreach (InstancePersistenceEvent ppEvent in this.GetEvents(owner))
            {
                if (ppEvent.Equals(HasRunnableWorkflowEvent.Value))
                {
                    bool hasRunnable = GetRunnableEvents(this.StoreId, owner.InstanceOwnerId, isActivatable);
                    if (hasRunnable)
                    {
                        this.SignalEvent(ppEvent, owner);
                    }
                    else
                    {
                        this.ResetEvent(ppEvent, owner);
                    }
                }
                else if(ppEvent.Equals(HasActivatableWorkflowEvent.Value))
                {
                   bool hasActivatable = GetActivatableEvents(this.StoreId, owner.InstanceOwnerId);
                   if (hasActivatable)
                    {
                        this.SignalEvent(ppEvent, owner);
                    }
                    else
                    {
                        this.ResetEvent(ppEvent, owner);
                    }
                }
            }
        }
    }
    ```

     <span data-ttu-id="16499-131">上のコード スニペットでは、インスタンス ストアが、使用できるイベントを探し、各イベントが <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> イベントであるかどうかを判断しています。</span><span class="sxs-lookup"><span data-stu-id="16499-131">In the above code snippet, the instance store queries the events available and examines each one to determine if it is a <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> event.</span></span> <span data-ttu-id="16499-132">使用できるイベントが見つかると、<xref:System.Runtime.DurableInstancing.InstanceStore.SignalEvent%2A> が呼び出され、インスタンス ストアにコマンドを送信することを指示する通知がホストに送信されます。</span><span class="sxs-lookup"><span data-stu-id="16499-132">If one is found, <xref:System.Runtime.DurableInstancing.InstanceStore.SignalEvent%2A> is called to signal the host to send a command to the instance store.</span></span> <span data-ttu-id="16499-133">次のコード スニペットはこのコマンドのハンドラーの実装を示します。</span><span class="sxs-lookup"><span data-stu-id="16499-133">The following code snippet demonstrates an implementation of a handler for this command.</span></span>

    ```csharp
    If (command is TryLoadRunnableWorkflowCommand)
    {
        Owner owner;
        CheckOwner(context, command.Name, out owner);
        // Checking instance.Owner is like an InstanceLockQueryResult.
        context.QueriedInstanceStore(new InstanceLockQueryResult(context.InstanceView.InstanceId, context.InstanceView.InstanceOwner.InstanceOwnerId));

        XName ownerService = null;
        InstanceValue value;
        Instance runnableInstance = default(Instance);
        bool foundRunnableInstance = false;

        value = QueryPropertyBag(WorkflowNamespace.WorkflowHostType, owner.Data);
        if (value != null && value.Value is XName)
        {
            ownerService = (XName)value.Value;
        }

        foreach (KeyValuePair<Guid, Instance> instance in MemoryStore.instances)
        {
            if (instance.Value.Owner != Guid.Empty || instance.Value.Completed)
            {
                continue;
            }

            if (ownerService != null)
            {
                value = QueryPropertyBag(WorkflowNamespace.WorkflowHostType, instance.Value.Metadata);
                if (value == null || ((XName)value.Value) != ownerService)
                {
                    continue;
                }
            }

            value = QueryPropertyBag(WorkflowServiceNamespace.SuspendReason, instance.Value.Metadata);
            if (value != null && value.Value != null && value.Value is string)
            {
                continue;
            }

            value = QueryPropertyBag(WorkflowNamespace.Status, instance.Value.Data);
            if (value != null && value.Value is string && ((string)value.Value) == "Executing")
            {
                runnableInstance = instance.Value;
                foundRunnableInstance = true;
            }

            if (!foundRunnableInstance)
            {
                value = QueryPropertyBag(XNamespace.Get("urn:schemas-microsoft-com:System.Activities/4.0/properties").GetName("TimerExpirationTime"), instance.Value.Data);
                if (value != null && value.Value is DateTime && ((DateTime)value.Value) <= DateTime.UtcNow)
                {
                    runnableInstance = instance.Value;
                    foundRunnableInstance = true;
                }
            }

            if (foundRunnableInstance)
            {
                runnableInstance.LockVersion++;
                runnableInstance.Owner = context.InstanceView.InstanceOwner.InstanceOwnerId;
                MemoryStore.instances[instance.Key] = runnableInstance;
                context.BindInstance(instance.Key);
                context.BindAcquiredLock(runnableInstance.LockVersion);

                Dictionary<Guid, IDictionary<XName, InstanceValue>> associatedKeys = new Dictionary<Guid, IDictionary<XName, InstanceValue>>();
                Dictionary<Guid, IDictionary<XName, InstanceValue>> completedKeys = new Dictionary<Guid, IDictionary<XName, InstanceValue>>();
                foreach (KeyValuePair<Guid, Key> keyEntry in MemoryStore.keys)
                {
                if (keyEntry.Value.Instance == context.InstanceView.InstanceId)
                {
                    if (keyEntry.Value.Completed)
                    {
                        completedKeys.Add(keyEntry.Key, DeserializePropertyBag(keyEntry.Value.Metadata));
                    }
                    else
                    {
                        associatedKeys.Add(keyEntry.Key, DeserializePropertyBag(keyEntry.Value.Metadata));
                    }
                }
            }

            context.LoadedInstance(InstanceState.Initialized, DeserializePropertyBag(runnableInstance.Data), DeserializePropertyBag(runnableInstance.Metadata), associatedKeys, completedKeys);
            break;
        }
    }
    ```

    <span data-ttu-id="16499-134">上のコード スニペットでは、インスタンス ストアは実行可能なインスタンスを検索します。</span><span class="sxs-lookup"><span data-stu-id="16499-134">In the above code snippet, the instance store searches for runnable instances.</span></span> <span data-ttu-id="16499-135">インスタンスが見つかると、そのインスタンスが実行コンテキストにバインドされ、読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="16499-135">If an instance is found, it is bound to the execution context and loaded.</span></span>

## <a name="using-a-custom-instance-store"></a><span data-ttu-id="16499-136">カスタム インスタンス ストアの使用</span><span class="sxs-lookup"><span data-stu-id="16499-136">Using a custom instance store</span></span>

<span data-ttu-id="16499-137">カスタム インスタンス ストアを実装するには、インスタンス ストアのインスタンスを <xref:System.Activities.WorkflowApplication.InstanceStore%2A> に割り当て、<xref:System.Activities.WorkflowApplication.PersistableIdle%2A> メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="16499-137">To implement a custom instance store, assign an instance of the instance store to the <xref:System.Activities.WorkflowApplication.InstanceStore%2A>, and implement the <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> method.</span></span> <span data-ttu-id="16499-138">詳細については、「 [方法: 実行時間の長いワークフローを作成および実行](how-to-create-and-run-a-long-running-workflow.md) する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="16499-138">See the [How to: Create and Run a Long Running Workflow](how-to-create-and-run-a-long-running-workflow.md) tutorial for specifics.</span></span>

## <a name="a-sample-instance-store"></a><span data-ttu-id="16499-139">サンプル インスタンス ストア</span><span class="sxs-lookup"><span data-stu-id="16499-139">A sample instance store</span></span>

<span data-ttu-id="16499-140">次のコードサンプルは、 [企業の購入プロセス](./samples/corporate-purchase-process.md) サンプルから取得した完全なインスタンスストアの実装です。</span><span class="sxs-lookup"><span data-stu-id="16499-140">The following code sample is a complete instance store implementation, taken from the [Corporate Purchase Process](./samples/corporate-purchase-process.md) sample.</span></span> <span data-ttu-id="16499-141">このインスタンス ストアは、XML を使用してファイルにワークフロー データを永続化します。</span><span class="sxs-lookup"><span data-stu-id="16499-141">This instance store persists workflow data to a file using XML.</span></span>

```csharp
using System;
using System.Activities.DurableInstancing;
using System.Collections.Generic;
using System.IO;
using System.Runtime.DurableInstancing;
using System.Runtime.Serialization;
using System.ServiceModel.Persistence;
using System.Xml;
using System.Xml.Linq;

namespace Microsoft.Samples.WF.PurchaseProcess
{

    public class XmlWorkflowInstanceStore : InstanceStore
    {
        Guid ownerInstanceID;

        public XmlWorkflowInstanceStore() : this(Guid.NewGuid())
        {

        }

        public XmlWorkflowInstanceStore(Guid id)
        {
            ownerInstanceID = id;
        }

        //Synchronous version of the Begin/EndTryCommand functions
        protected override bool TryCommand(InstancePersistenceContext context, InstancePersistenceCommand command, TimeSpan timeout)
        {
            return EndTryCommand(BeginTryCommand(context, command, timeout, null, null));
        }

        //The persistence engine will send a variety of commands to the configured InstanceStore,
        //such as CreateWorkflowOwnerCommand, SaveWorkflowCommand, and LoadWorkflowCommand.
        //This method is where we will handle those commands
        protected override IAsyncResult BeginTryCommand(InstancePersistenceContext context, InstancePersistenceCommand command, TimeSpan timeout, AsyncCallback callback, object state)
        {
            IDictionary<XName, InstanceValue> data = null;

            //The CreateWorkflowOwner command instructs the instance store to create a new instance owner bound to the instanace handle
            if (command is CreateWorkflowOwnerCommand)
            {
                context.BindInstanceOwner(ownerInstanceID, Guid.NewGuid());
            }
            //The SaveWorkflow command instructs the instance store to modify the instance bound to the instance handle or an instance key
            else if (command is SaveWorkflowCommand)
            {
                SaveWorkflowCommand saveCommand = (SaveWorkflowCommand)command;
                data = saveCommand.InstanceData;

                Save(data);
            }
            //The LoadWorkflow command instructs the instance store to lock and load the instance bound to the identifier in the instance handle
            else if (command is LoadWorkflowCommand)
            {
                string fileName = IOHelper.GetFileName(this.ownerInstanceID);

                try
                {
                    using (FileStream inputStream = new FileStream(fileName, FileMode.Open))
                    {
                        data = LoadInstanceDataFromFile(inputStream);
                        //load the data into the persistence Context
                        context.LoadedInstance(InstanceState.Initialized, data, null, null, null);
                    }
                }
                catch (Exception exception)
                {
                    throw new PersistenceException(exception.Message);
                }
            }

            return new CompletedAsyncResult<bool>(true, callback, state);
        }

        protected override bool EndTryCommand(IAsyncResult result)
        {
            return CompletedAsyncResult<bool>.End(result);
        }

        //Reads data from xml file and creates a dictionary based off of that.
        IDictionary<XName, InstanceValue> LoadInstanceDataFromFile(Stream inputStream)
        {
            IDictionary<XName, InstanceValue> data = new Dictionary<XName, InstanceValue>();

            NetDataContractSerializer s = new NetDataContractSerializer();

            XmlReader rdr = XmlReader.Create(inputStream);
            XmlDocument doc = new XmlDocument();
            doc.Load(rdr);

            XmlNodeList instances = doc.GetElementsByTagName("InstanceValue");
            foreach (XmlElement instanceElement in instances)
            {
                XmlElement keyElement = (XmlElement)instanceElement.SelectSingleNode("descendant::key");
                XName key = (XName)DeserializeObject(s, keyElement);

                XmlElement valueElement = (XmlElement)instanceElement.SelectSingleNode("descendant::value");
                object value = DeserializeObject(s, valueElement);
                InstanceValue instVal = new InstanceValue(value);

                data.Add(key, instVal);
            }

            return data;
        }

        object DeserializeObject(NetDataContractSerializer serializer, XmlElement element)
        {
            object deserializedObject = null;

            MemoryStream stm = new MemoryStream();
            XmlDictionaryWriter wtr = XmlDictionaryWriter.CreateTextWriter(stm);
            element.WriteContentTo(wtr);
            wtr.Flush();
            stm.Position = 0;

            deserializedObject = serializer.Deserialize(stm);

            return deserializedObject;
        }

        //Saves the persistence data to an xml file.
        void Save(IDictionary<XName, InstanceValue> instanceData)
        {
            string fileName = IOHelper.GetFileName(this.ownerInstanceID);
            XmlDocument doc = new XmlDocument();
            doc.LoadXml("<InstanceValues/>");

            foreach (KeyValuePair<XName,InstanceValue> valPair in instanceData)
            {
                XmlElement newInstance = doc.CreateElement("InstanceValue");

                XmlElement newKey = SerializeObject("key", valPair.Key, doc);
                newInstance.AppendChild(newKey);

                XmlElement newValue = SerializeObject("value", valPair.Value.Value, doc);
                newInstance.AppendChild(newValue);

                doc.DocumentElement.AppendChild(newInstance);
            }
            doc.Save(fileName);
       }

        XmlElement SerializeObject(string elementName, object o, XmlDocument doc)
        {
            NetDataContractSerializer s = new NetDataContractSerializer();
            XmlElement newElement = doc.CreateElement(elementName);
            MemoryStream stm = new MemoryStream();

            s.Serialize(stm, o);
            stm.Position = 0;
            StreamReader rdr = new StreamReader(stm);
            newElement.InnerXml = rdr.ReadToEnd();

            return newElement;
        }
    }
}
```
