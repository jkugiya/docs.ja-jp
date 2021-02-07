---
description: '詳細情報: ストアの機能拡張'
title: ストア拡張
ms.date: 03/30/2017
ms.assetid: 7c3f4a46-4bac-4138-ae6a-a7c7ee0d28f5
ms.openlocfilehash: f04c466224aacd1c8f755e7aa60b18846d0c7180
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755227"
---
# <a name="store-extensibility"></a><span data-ttu-id="0d238-103">ストア拡張</span><span class="sxs-lookup"><span data-stu-id="0d238-103">Store Extensibility</span></span>

<span data-ttu-id="0d238-104"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> を使用して、永続性データベースのインスタンスをクエリする場合に使用できるカスタムのアプリケーション固有のプロパティを昇格できます。</span><span class="sxs-lookup"><span data-stu-id="0d238-104"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> allows users to promote custom, application-specific properties that can be used to query for instances in the persistence database.</span></span> <span data-ttu-id="0d238-105">プロパティを昇格することで、データベース内の特殊なビュー内で値が使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="0d238-105">The act of promoting a property causes the value to be available within a special view in the database.</span></span> <span data-ttu-id="0d238-106">これらの昇格したプロパティ (ユーザー クエリで使用できるプロパティ) は、単純型 (Int64、Guid、String、DateTime など) またはシリアル化されたバイナリ型 (byte[]) になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="0d238-106">These promoted properties (properties that can be used in user queries) can be of simple types such as Int64, Guid, String, and DateTime or of a serialized binary type (byte[]).</span></span>

<span data-ttu-id="0d238-107"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> クラスには <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.Promote%2A> メソッドがあり、クエリで使用できるプロパティとしてプロパティを昇格するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="0d238-107">The <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> class has the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.Promote%2A> method that you can use to promote a property as a property that can be used in queries.</span></span> <span data-ttu-id="0d238-108">次の例は、ストア拡張のエンド ツー エンドの例です。</span><span class="sxs-lookup"><span data-stu-id="0d238-108">The following example is an end-to-end example of store extensibility.</span></span>

1. <span data-ttu-id="0d238-109">この例のシナリオでは、ドキュメント処理 (DP) アプリケーションにワークフローがあり、それぞれがドキュメント処理にカスタム アクティビティを使用しています。</span><span class="sxs-lookup"><span data-stu-id="0d238-109">In this example scenario, a document processing (DP) application has workflows, each of which uses custom activities for document processing.</span></span> <span data-ttu-id="0d238-110">これらのワークフローは、エンド ユーザーから見える必要がある一連の状態変数を備えています。</span><span class="sxs-lookup"><span data-stu-id="0d238-110">These workflows have a set of state variables that need to be made visible to the end user.</span></span> <span data-ttu-id="0d238-111">これを実現するために、DP アプリケーションには <xref:System.Activities.Persistence.PersistenceParticipant> 型を持つインスタンス拡張機能があり、状態変数を提供するアクティビティによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="0d238-111">To achieve this, the DP application provides an instance extension of type <xref:System.Activities.Persistence.PersistenceParticipant>, which is used by activities to supply the state variables.</span></span>

    ```csharp
    class DocumentStatusExtension : PersistenceParticipant
    {
        public string DocumentId;
        public string ApprovalStatus;
        public string UserName;
        public DateTime LastUpdateTime;
    }
    ```

2. <span data-ttu-id="0d238-112">次に、新しい機能拡張がホストに追加されます。</span><span class="sxs-lookup"><span data-stu-id="0d238-112">The new extension is then added to the host.</span></span>

    ```csharp
    static Activity workflow = CreateWorkflow();
    WorkflowApplication application = new WorkflowApplication(workflow);
    DocumentStatusExtension documentStatusExtension = new DocumentStatusExtension ();
    application.Extensions.Add(documentStatusExtension);
    ```

     <span data-ttu-id="0d238-113">カスタムの永続参加要素を追加する方法の詳細については、 [永続参加](persistence-participants.md) 要素のサンプルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d238-113">For more details about adding a custom persistence participant, see the [Persistence Participants](persistence-participants.md) sample.</span></span>

3. <span data-ttu-id="0d238-114">DP アプリケーションのカスタムアクティビティは、 **Execute** メソッドにさまざまな状態フィールドを設定します。</span><span class="sxs-lookup"><span data-stu-id="0d238-114">The custom activities in the DP application populate various status fields in the **Execute** method.</span></span>

    ```csharp
    public override void Execute(CodeActivityContext context)
    {
        // ...
        context.GetExtension<DocumentStatusExtension>().DocumentId = Guid.NewGuid();
        context.GetExtension<DocumentStatusExtension>().UserName = "John Smith";
        context.GetExtension<DocumentStatusExtension>().ApprovalStatus = "Approved";
        context.GetExtension<DocumentStatusExtension>().LastUpdateTime = DateTime.Now();
        // ...
    }
    ```

4. <span data-ttu-id="0d238-115">ワークフローインスタンスが永続化ポイントに到達すると、 **Documentstatusextension** 永続化参加要素の **collectvalues** メソッドによって、これらのプロパティが永続性データコレクションに保存されます。</span><span class="sxs-lookup"><span data-stu-id="0d238-115">When a workflow instance reaches a persistence point, the **CollectValues** method of the **DocumentStatusExtension** persistence participant saves these properties into the persistence data collection.</span></span>

    ```csharp
    class DocumentStatusExtension : PersistenceParticipant
    {
        const XNamespace xNS = XNamespace.Get("http://contoso.com/DocumentStatus");

        protected override void CollectValues(out IDictionary<XName, object> readWriteValues, out IDictionary<XName, object> writeOnlyValues)
        {
            readWriteValues = new Dictionary<XName, object>();
            readWriteValues.Add(xNS.GetName("UserName"), this.UserName);
            readWriteValues.Add(xNS.GetName("ApprovalStatus"), this.ApprovalStatus);
            readWriteValues.Add(xNS.GetName("DocumentId"), this.DocumentId);
            readWriteValues.Add(xNS.GetName("LastModifiedTime"), this.LastUpdateTime);

            writeOnlyValues = null;
        }
        // ...
    }
    ```

    > [!NOTE]
    > <span data-ttu-id="0d238-116">これらのプロパティはすべて、 **SaveWorkflowCommand** コレクションを通じて永続化フレームワークによって **SqlWorkflowInstanceStore** に渡されます。</span><span class="sxs-lookup"><span data-stu-id="0d238-116">All these properties are passed to **SqlWorkflowInstanceStore** by the persistence framework through the **SaveWorkflowCommand.InstanceData** collection.</span></span>

5. <span data-ttu-id="0d238-117">DP アプリケーションは SQL Workflow Instance Store を初期化し、 **promote** メソッドを呼び出してこのデータを昇格させます。</span><span class="sxs-lookup"><span data-stu-id="0d238-117">The DP application initializes the SQL Workflow Instance Store and invokes the **Promote** method to promote this data.</span></span>

    ```csharp
    SqlWorkflowInstanceStore store = new SqlWorkflowInstanceStore(connectionString);

    List<XName> variantProperties = new List<XName>()
    {
        xNS.GetName("UserName"),
        xNS.GetName("ApprovalStatus"),
        xNS.GetName("DocumentId"),
        xNS.GetName("LastModifiedTime")
    };

    store.Promote("DocumentStatus", variantProperties, null);
    ```

    <span data-ttu-id="0d238-118">このプロモーション情報に基づいて、 **SqlWorkflowInstanceStore** は [InstancePromotedProperties](#InstancePromotedProperties) ビューの列にデータプロパティを配置します。</span><span class="sxs-lookup"><span data-stu-id="0d238-118">Based on this promotion information, **SqlWorkflowInstanceStore** places the data properties in the columns of the [InstancePromotedProperties](#InstancePromotedProperties) view.</span></span>

6. <span data-ttu-id="0d238-119">昇格テーブルのデータのサブセットを照会するために、DP アプリケーションによって昇格ビューの上にカスタマイズされたビューが追加されます。</span><span class="sxs-lookup"><span data-stu-id="0d238-119">To query a subset of the data from the promotion table, the DP application adds a customized view on top of the promotion view.</span></span>

    ```sql
    create view [dbo].[DocumentStatus] with schemabinding
    as
        select  P.[InstanceId] as [InstanceId],
            P.Value1 as [UserName],
            P.Value2 as [ApprovalStatus],
            P.Value3 as [DocumentId],
            P.Value4 as [LastUpdatedTime]
    from [System.Activities.DurableInstancing].[InstancePromotedProperties] as P
    where P.PromotionName = N'DocumentStatus'
    go
    ```

## <a name="systemactivitiesdurableinstancinginstancepromotedproperties-view"></a><a name="InstancePromotedProperties"></a> <span data-ttu-id="0d238-120">[System.activities.durableinstancing.instances. InstancePromotedProperties] ビュー</span><span class="sxs-lookup"><span data-stu-id="0d238-120">[System.Activities.DurableInstancing.InstancePromotedProperties] view</span></span>

|<span data-ttu-id="0d238-121">列名</span><span class="sxs-lookup"><span data-stu-id="0d238-121">Column Name</span></span>|<span data-ttu-id="0d238-122">列の型</span><span class="sxs-lookup"><span data-stu-id="0d238-122">Column Type</span></span>|<span data-ttu-id="0d238-123">説明</span><span class="sxs-lookup"><span data-stu-id="0d238-123">Description</span></span>|
|-----------------|-----------------|-----------------|
|<span data-ttu-id="0d238-124">InstanceId</span><span class="sxs-lookup"><span data-stu-id="0d238-124">InstanceId</span></span>|<span data-ttu-id="0d238-125">GUID</span><span class="sxs-lookup"><span data-stu-id="0d238-125">GUID</span></span>|<span data-ttu-id="0d238-126">この昇格が属するワークフロー インスタンス。</span><span class="sxs-lookup"><span data-stu-id="0d238-126">The workflow instance that this promotion belongs to.</span></span>|
|<span data-ttu-id="0d238-127">PromotionName</span><span class="sxs-lookup"><span data-stu-id="0d238-127">PromotionName</span></span>|<span data-ttu-id="0d238-128">nvarchar(400)</span><span class="sxs-lookup"><span data-stu-id="0d238-128">nvarchar(400)</span></span>|<span data-ttu-id="0d238-129">昇格自体の名前。</span><span class="sxs-lookup"><span data-stu-id="0d238-129">The name of the promotion itself.</span></span>|
|<span data-ttu-id="0d238-130">Value1、Value2、Value3、…Value32</span><span class="sxs-lookup"><span data-stu-id="0d238-130">Value1, Value2, Value3,..,Value32</span></span>|<span data-ttu-id="0d238-131">sql_variant</span><span class="sxs-lookup"><span data-stu-id="0d238-131">sql_variant</span></span>|<span data-ttu-id="0d238-132">昇格したプロパティ自体の値。</span><span class="sxs-lookup"><span data-stu-id="0d238-132">The value of the promoted property itself.</span></span> <span data-ttu-id="0d238-133">ほとんどの SQL プリミティブ データ型はバイナリ ブロブを除外し、長さが 8,000 バイトを超える文字列は sql_variant に合わせて短縮されます。</span><span class="sxs-lookup"><span data-stu-id="0d238-133">Most SQL primitive data types except binary blobs and strings over 8000 bytes in length can fit in sql_variant.</span></span>|
|<span data-ttu-id="0d238-134">Value33、Value34、Value35、…、Value64</span><span class="sxs-lookup"><span data-stu-id="0d238-134">Value33, Value34, Value35, …, Value64</span></span>|<span data-ttu-id="0d238-135">varbinary(max)</span><span class="sxs-lookup"><span data-stu-id="0d238-135">varbinary(max)</span></span>|<span data-ttu-id="0d238-136">varbinary(max) として明示的に宣言される昇格したプロパティの値。</span><span class="sxs-lookup"><span data-stu-id="0d238-136">The value of promoted properties that are explicitly declared as varbinary(max).</span></span>|
